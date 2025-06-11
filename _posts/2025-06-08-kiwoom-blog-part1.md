---
title: "Bridging Legacy and Modern: Integrating Kiwoom API with Modern Web Architecture"  
date: 2025-06-11  
layout: single  
tags:  
  - project  

excerpt: "I faced the challenge of integrating a Windows-only desktop API into a modern web application, requiring innovative solutions to bridge completely different architectural paradigms."  
---

## Why I studied this  

I wanted to build a real-time stock volume ranking service using Korean market data from Kiwoom Securities. What seemed like a straightforward API integration project quickly became a complex architectural challenge when I discovered that Kiwoom's API is fundamentally incompatible with modern web development practices. This forced me to think creatively about bridging legacy desktop applications with contemporary web architecture.  

---

## What I did  

### Understanding the Fundamental Problem  

The Kiwoom API presented unique constraints that challenged conventional web development approaches:  

#### The Desktop-Only Limitation  
Kiwoom API operates exclusively in a Windows environment using COM (ActiveX) technology, requiring PyQt5 for GUI integration. This means:  
- No server deployment capability  
- No headless environment support  
- No cloud hosting compatibility  
- Mandatory GUI thread requirements  

#### My Initial Approach  
I first attempted to integrate the API directly into a FastAPI backend, thinking I could run it as a standard web service:  

```python
# This approach failed completely  
from fastapi import FastAPI  
from kiwoom_api import KiwoomAPI  # This won't work in server environment  

app = FastAPI()  
kiwoom = KiwoomAPI()  # Requires Windows GUI  

@app.get("/volume-ranking")  
async def get_volume_ranking():  
    return kiwoom.get_data()  # Fails without PyQt5 event loop  
```

This approach was fundamentally flawed because I was trying to force a desktop application into a server paradigm.  

### Designing the Bridge Architecture  

After understanding the constraints, I developed a middleware solution that acts as a bridge between the desktop API and web application:  

#### The Middleware Concept  
I created a PyQt5 application that serves as a local data broker, running alongside the web application and communicating through HTTP endpoints:  

```python
# kiwoom_middleware.py  
import sys  
from PyQt5.QtWidgets import QApplication  
from PyQt5.QAxContainer import QAxWidget  
import threading  
import asyncio  
from fastapi import FastAPI  
import uvicorn  

class KiwoomMiddleware:  
    def __init__(self):  
        self.app = QApplication(sys.argv)  
        self.kiwoom = QAxWidget("KHOPENAPI.KHOpenAPICtrl.1")  
        self.data_cache = {}  
        self.setup_api_events()  
    
    def setup_api_events(self):  
        self.kiwoom.OnEventConnect.connect(self.on_event_connect)  
        self.kiwoom.OnReceiveTrData.connect(self.on_receive_tr_data)  
    
    def on_event_connect(self, err_code):  
        if err_code == 0:  
            print("Kiwoom API connected successfully")  
            self.fetch_volume_ranking()  
    
    def on_receive_tr_data(self, screen_no, rqname, trcode, record_name, prev_next):  
        # Process and cache the received data  
        self.process_volume_data(rqname, trcode)  
    
    def fetch_volume_ranking(self):  
        self.kiwoom.SetInputValue("시장구분", "001")  # KOSPI  
        self.kiwoom.CommRqData("volume_rank", "opt10023", 0, "0101")  

# FastAPI component running in separate thread  
api_app = FastAPI()  

@api_app.get("/api/volume-ranking")  
async def get_volume_ranking():  
    return middleware.get_cached_data()  

def run_fastapi():  
    uvicorn.run(api_app, host="127.0.0.1", port=8000)  

if __name__ == "__main__":  
    middleware = KiwoomMiddleware()  
    
    # Run FastAPI in separate thread  
    api_thread = threading.Thread(target=run_fastapi, daemon=True)  
    api_thread.start()  
    
    # Run PyQt5 main loop  
    middleware.app.exec_()  
```

#### Solving the Threading Challenge  

The most complex aspect was managing two different event loops simultaneously:  

**Challenge**: PyQt5 requires the main thread for GUI operations, while FastAPI needs to run its async event loop.  

**Solution**: I implemented a thread-safe communication system:  

```python
import asyncio  
import threading  
from queue import Queue  
from typing import Dict, Any  

class ThreadSafeDataBridge:  
    def __init__(self):  
        self.data_queue = Queue()  
        self.latest_data: Dict[str, Any] = {}  
        self.data_lock = threading.Lock()  
    
    def update_data_from_kiwoom(self, data: Dict[str, Any]):  
        """Called from PyQt5 thread"""  
        with self.data_lock:  
            self.latest_data.update(data)  
            self.data_queue.put(data)  
    
    async def get_latest_data(self) -> Dict[str, Any]:  
        """Called from FastAPI async context"""  
        with self.data_lock:  
            return self.latest_data.copy()  
    
    def has_new_data(self) -> bool:  
        return not self.data_queue.empty()  
```

### Implementing Real-Time Data Flow  

The architecture needed to handle real-time market data updates efficiently:  

#### Data Caching Strategy  
```python
class VolumeRankingCache:  
    def __init__(self):  
        self.cache = {}  
        self.last_update = None  
        self.update_interval = 60  # seconds  
    
    def should_refresh(self) -> bool:  
        if not self.last_update:  
            return True  
        return (datetime.now() - self.last_update).seconds > self.update_interval  
    
    def update_cache(self, ranking_data: List[Dict]):  
        self.cache['volume_ranking'] = ranking_data  
        self.cache['market_status'] = self.get_market_status()  
        self.last_update = datetime.now()  
    
    def get_cached_data(self) -> Dict:  
        return {  
            'data': self.cache.get('volume_ranking', []),  
            'last_update': self.last_update.isoformat() if self.last_update else None,  
            'market_open': self.cache.get('market_status', False)  
        }  
```

---

## What I learned  

This project taught me several crucial lessons about system integration and architectural thinking:  

- **Legacy system constraints drive architecture**: Sometimes you can't force modern patterns onto legacy systems - you need to build bridges instead  
- **Threading complexity in desktop-web hybrids**: Managing multiple event loops requires careful coordination and thread-safe communication patterns  
- **The value of middleware patterns**: When direct integration isn't possible, middleware can provide elegant abstraction layers  
- **Real-time data challenges**: Desktop APIs often weren't designed for web-scale concurrent access, requiring careful caching strategies  

The most important insight was that successful integration often requires abandoning ideal architectures in favor of practical solutions that work within existing constraints.  

---

## What I want to do next  

- Implement WebSocket connections for real-time frontend updates  
- Add comprehensive error handling and recovery mechanisms  
- Design a configuration system for different market data requirements  
- Create monitoring and logging systems for the middleware  
- Explore containerization strategies for the complete system  

---
---
title: "Real-Time Data Synchronization: Solving Market Data Freshness and UI Consistency"  
date: 2025-06-11  
layout: single  
tags:  
  - project  

excerpt: "Building a reliable real-time stock ranking system required solving complex data synchronization challenges between market API constraints and user interface requirements."  
---

## Why I studied this  

After establishing the basic architecture bridge between Kiwoom API and my web application, I faced new challenges around data freshness and frontend reliability. Market data is inherently time-sensitive, and users expect accurate, up-to-date information. However, the Kiwoom API has specific timing constraints and data delivery patterns that don't align with typical web application expectations.  

---

## What I did  

### Challenge 1: Market Data Timing and Freshness  

The Kiwoom API presents unique data availability patterns that required sophisticated handling:  

#### Understanding Market Data Constraints  
- Market data is only available during trading hours (9:00 AM - 3:30 PM KST)  
- API responses can be cached or delayed during high-traffic periods  
- Data requests before market open return stale information  
- Rate limiting prevents excessive API calls  

#### Implementing Intelligent Data Scheduling  

I developed a scheduling system that adapts to market conditions:  

```python
from apscheduler.schedulers.asyncio import AsyncIOScheduler  
from apscheduler.triggers.cron import CronTrigger  
from datetime import datetime, time  
import pytz  

class MarketDataScheduler:  
    def __init__(self, kiwoom_bridge):  
        self.scheduler = AsyncIOScheduler()  
        self.kiwoom_bridge = kiwoom_bridge  
        self.seoul_tz = pytz.timezone('Asia/Seoul')  
        self.setup_market_schedule()  
    
    def setup_market_schedule(self):  
        # High-frequency updates during market hours  
        self.scheduler.add_job(  
            func=self.fetch_volume_ranking,  
            trigger=CronTrigger(  
                day_of_week='mon-fri',  
                hour='9-15',  
                minute='*/2',  # Every 2 minutes during trading  
                timezone=self.seoul_tz  
            ),  
            id='market_hours_update'  
        )  
        
        # Pre-market preparation  
        self.scheduler.add_job(  
            func=self.prepare_market_data,  
            trigger=CronTrigger(  
                day_of_week='mon-fri',  
                hour=8,  
                minute=50,  
                timezone=self.seoul_tz  
            ),  
            id='pre_market_prep'  
        )  
        
        # Post-market cleanup  
        self.scheduler.add_job(  
            func=self.finalize_daily_data,  
            trigger=CronTrigger(  
                day_of_week='mon-fri',  
                hour=16,  
                minute=0,  
                timezone=self.seoul_tz  
            ),  
            id='post_market_cleanup'  
        )  
    
    async def fetch_volume_ranking(self):  
        """Intelligent data fetching with freshness validation"""  
        try:  
            current_time = datetime.now(self.seoul_tz)  
            
            # Check if market is actually open  
            if not self.is_market_open(current_time):  
                return  
            
            # Request fresh data from Kiwoom  
            new_data = await self.kiwoom_bridge.request_volume_data()  
            
            # Validate data freshness  
            if self.is_data_fresh(new_data):  
                await self.update_cache_and_notify(new_data)  
            else:  
                # Implement exponential backoff for stale data  
                await self.handle_stale_data()  
                
        except Exception as e:  
            await self.handle_fetch_error(e)  
    
    def is_data_fresh(self, data) -> bool:  
        """Validate if received data is actually fresh"""  
        if not data or 'timestamp' not in data:  
            return False  
        
        data_time = datetime.fromisoformat(data['timestamp'])  
        current_time = datetime.now(self.seoul_tz)  
        
        # Data should be no older than 5 minutes during market hours  
        time_diff = (current_time - data_time).total_seconds()  
        return time_diff < 300  # 5 minutes  
    
    async def handle_stale_data(self):  
        """Implement intelligent retry strategy"""  
        retry_count = getattr(self, 'retry_count', 0)  
        max_retries = 3  
        
        if retry_count < max_retries:  
            self.retry_count = retry_count + 1  
            # Exponential backoff: 30s, 60s, 120s  
            delay = 30 * (2 ** retry_count)  
            
            self.scheduler.add_job(  
                func=self.fetch_volume_ranking,  
                trigger='date',  
                run_date=datetime.now() + timedelta(seconds=delay),  
                id=f'retry_fetch_{retry_count}'  
            )  
        else:  
            # Reset retry count and log issue  
            self.retry_count = 0  
            logger.warning("Max retries reached for data fetch")  
```

### Challenge 2: React Frontend Data Synchronization  

The frontend needed to handle dynamic data updates without performance degradation or visual artifacts:  

#### Solving Table Rendering Issues  

The initial implementation suffered from duplicate rows, flickering, and inconsistent updates:  

```javascript
// Problematic initial approach  
function VolumeRankingTable({ data }) {  
  const [rankings, setRankings] = useState([]);  
  
  // This caused duplicates and flickering  
  useEffect(() => {  
    setRankings([...rankings, ...data]); // Wrong: accumulating data  
  }, [data]);  
  
  return (  
    <table>
      {rankings.map((stock, index) => (  
        <tr key={index}> // Wrong: using array index as key  
          <td>{stock.name}</td>
          <td>{stock.volume}</td>
        </tr>
      ))}  
    </table>
  );  
}  
```

#### Implementing Robust State Management  

I redesigned the component with proper state management and efficient rendering:  

```javascript
import { useState, useEffect, useCallback, useMemo } from 'react';  

function VolumeRankingTable() {  
  const [rankings, setRankings] = useState([]);  
  const [lastUpdate, setLastUpdate] = useState(null);  
  const [isLoading, setIsLoading] = useState(false);  
  const [error, setError] = useState(null);  
  
  // Memoized data processing to prevent unnecessary re-renders  
  const processedRankings = useMemo(() => {  
    return rankings.map((stock, index) => ({  
      ...stock,  
      rank: index + 1,  
      id: stock.code, // Use stock code as stable identifier  
      volumeFormatted: formatVolume(stock.volume),  
      changePercent: calculateChange(stock.current_price, stock.prev_price)  
    }));  
  }, [rankings]);  
  
  // Stable fetch function with error handling  
  const fetchRankings = useCallback(async () => {  
    try {  
      setIsLoading(true);  
      setError(null);  
      
      const response = await fetch('/api/volume-ranking');  
      const result = await response.json();  
      
      if (!response.ok) {  
        throw new Error(result.message || 'Failed to fetch data');  
      }  
      
      // Validate data structure before updating state  
      if (validateRankingData(result.data)) {  
        setRankings(result.data);  
        setLastUpdate(new Date(result.last_update));  
      } else {  
        throw new Error('Invalid data structure received');  
      }  
      
    } catch (err) {  
      setError(err.message);  
      console.error('Fetch error:', err);  
    } finally {  
      setIsLoading(false);  
    }  
  }, []);  
  
  // Intelligent update polling  
  useEffect(() => {  
    fetchRankings(); // Initial fetch  
    
    const interval = setInterval(() => {  
      // Only fetch if tab is visible and market is open  
      if (!document.hidden && isMarketOpen()) {  
        fetchRankings();  
      }  
    }, 120000); // 2 minutes  
    
    // Cleanup interval on unmount  
    return () => clearInterval(interval);  
  }, [fetchRankings]);  
  
  // Handle visibility change to pause/resume updates  
  useEffect(() => {  
    const handleVisibilityChange = () => {  
      if (!document.hidden) {  
        fetchRankings(); // Refresh when tab becomes visible  
      }  
    };  
    
    document.addEventListener('visibilitychange', handleVisibilityChange);  
    return () => document.removeEventListener('visibilitychange', handleVisibilityChange);  
  }, [fetchRankings]);  
  
  if (error) {  
    return (  
      <div className="error-container">
        <p>Error loading data: {error}</p>
        <button onClick={fetchRankings}>Retry</button>
      </div>
    );  
  }  
  
  return (  
    <div className="ranking-table-container">
      <div className="table-header">
        <h2>Volume Rankings</h2>
        {lastUpdate && (  
          <span className="last-update">
            Last updated: {lastUpdate.toLocaleTimeString()}  
          </span>
        )}  
        {isLoading && <span className="loading-indicator">Updating...</span>}  
      </div>
      
      <table className="ranking-table">
        <thead>
          <tr>
            <th>Rank</th>
            <th>Stock Name</th>
            <th>Code</th>
            <th>Volume</th>
            <th>Price</th>
            <th>Change %</th>
          </tr>
        </thead>
        <tbody>
          {processedRankings.map((stock) => (  
            <tr  
              key={stock.id} // Stable key using stock code  
              className={`ranking-row ${stock.changePercent > 0 ? 'positive' : 'negative'}`}  
            >  
              <td className="rank">{stock.rank}</td>
              <td className="stock-name">{stock.name}</td>
              <td className="stock-code">{stock.code}</td>
              <td className="volume">{stock.volumeFormatted}</td>
              <td className="price">{stock.current_price.toLocaleString()}</td>
              <td className={`change ${stock.changePercent > 0 ? 'positive' : 'negative'}`}>
                {stock.changePercent > 0 ? '+' : ''}{stock.changePercent.toFixed(2)}%  
              </td>
            </tr>
          ))}  
        </tbody>
      </table>
    </div>
  );  
}  

// Utility functions  
function validateRankingData(data) {  
  return Array.isArray(data) &&  
         data.every(stock =>  
           stock.hasOwnProperty('code') &&  
           stock.hasOwnProperty('name') &&  
           stock.hasOwnProperty('volume')  
         );  
}  

function formatVolume(volume) {  
  if (volume >= 1000000) {  
    return `${(volume / 1000000).toFixed(1)}M`;  
  } else if (volume >= 1000) {  
    return `${(volume / 1000).toFixed(1)}K`;  
  }  
  return volume.toLocaleString();  
}  

function isMarketOpen() {  
  const now = new Date();  
  const koreanTime = new Date(now.toLocaleString("en-US", {timeZone: "Asia/Seoul"}));  
  const hour = koreanTime.getHours();  
  const day = koreanTime.getDay();  
  
  // Market open: Monday-Friday, 9 AM - 3:30 PM KST  
  return day >= 1 && day <= 5 && hour >= 9 && hour < 15.5;  
}  
```

---

## What I learned  

This phase of the project taught me sophisticated lessons about real-time data management:  

- **Market data has inherent timing constraints** that must be respected in system design  
- **Frontend performance optimization** requires careful state management and intelligent re-rendering strategies  
- **Data validation and error handling** become critical when dealing with external APIs that may return inconsistent data  
- **User experience considerations** like visibility-based polling and loading states significantly impact application usability  

The most valuable insight was understanding that real-time doesn't mean constant updates - intelligent scheduling based on actual data availability is far more efficient and reliable.  

---

## What I want to do next  

- Implement WebSocket connections for true real-time updates  
- Add sophisticated caching layers with TTL management  
- Create comprehensive monitoring and alerting for data freshness  
- Build predictive pre-loading based on user behavior patterns  
- Develop fallback data sources for enhanced reliability  

---
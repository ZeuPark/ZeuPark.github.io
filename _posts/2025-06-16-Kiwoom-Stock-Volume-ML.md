---
title: "Using Kiwoom API to Fetch Stock Volume Data for ML Forecasting"  
date: 2025-06-16  
layout: single  
tags:  
  - project  
  - machine-learning  
excerpt: "In this post, I explore how I used Kiwoom REST API to fetch real-time and historical stock trading volume data, and my efforts toward building an ML-based prediction system."  
---

## Background  

To understand which stocks are surging or falling, I started working with **real-world stock trading data**. My primary data source: **Kiwoom's REST API**. The goal was to:  
- Fetch real-time trading volume  
- Compare it with previous day’s volume  
- Include foreign investor trading data  

This information would serve as the foundation for identifying rapid movements in stocks and eventually training a model to forecast those changes.  

---

## Why Volume Data?  

Volume is a leading indicator in technical analysis. If a stock is suddenly seeing **abnormal volume spikes**, it usually signals an important movement. I focused on:  
- Real-time volume (`현재 거래량`)  
- Previous day volume (`전일 거래량`)  
- Foreign trading volume (`외국인 순매수/매도`)  

---

## Technical Challenges  

Using the Kiwoom API was not straightforward. Key difficulties:  
- Each data type (real-time, foreign volume, etc.) uses a **different request code**  
- Response formats are not standardized  
- Some values are only accessible through event-based callbacks (not ideal for batch fetching)  
- Correlating data across types was hard due to inconsistent indexing  

This meant that **fetching all related data and merging it correctly** required custom logic and frequent debugging.  

---

## Example: Fetching Real-Time Trading Volume (Python + PyKiwoom)  

```python
from pykiwoom.kiwoom import Kiwoom  
import time  

kiwoom = Kiwoom()  
kiwoom.CommConnect(block=True)  

# Example: Fetch top trading volume stocks  
sector_code = "001"  # 코스피 업종 코드 예시  
tickers = kiwoom.GetCodeListByMarket("0")  

for code in tickers[:10]:  
    name = kiwoom.GetMasterCodeName(code)  
    data = kiwoom.block_request("opt10001",  
                                종목코드=code,  
                                output="주식기본정보",  
                                next=0)  
    volume = data.get('거래량')  
    print(f"{name} ({code}): 거래량 {volume}")  
    time.sleep(1)  # Too many requests can trigger rate limiting  
```

---

## Next Steps: Toward ML Forecasting  

Once I clean and align these volume datasets, my plan is to:  
- Merge volume, price, and investor types into a structured time series  
- Use this data to **label rising/falling patterns**  
- Apply binary classification (e.g. will rise: yes/no) using ML models like LightGBM or XGBoost  

---

## What I Learned  

- Financial APIs often sacrifice consistency for flexibility  
- Preprocessing and integrating data matters more than model selection at this stage  
- Reliable volume data is not just useful for trading — it’s a signal-rich input for ML models  

---

## Challenges Still Remaining  

- Handling API throttling and asynchronous requests  
- Designing a clean data schema for training  
- Creating a feature pipeline that updates in real-time  

I’m continuing to iterate on the pipeline, and I expect the real edge will come from how I preprocess and label the data.  

---

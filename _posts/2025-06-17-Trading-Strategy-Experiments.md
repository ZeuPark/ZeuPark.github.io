---
title: "Exploring Trading Strategies: From API-Based Speed to Randomized 'Monkey' Methods"  
date: 2025-06-17  
layout: single  
tags:  
  - project  
  - machine-learning  
excerpt: "This post explores my iterative thinking on how to build a better stock trading strategy — from fast API-based entries to random selection strategies inspired by the 'monkey theory'."  
---

## Background  

As I started working with real-time stock data from the Kiwoom API, my immediate idea was to build a strategy around speed. Specifically:  

> If I can spot a surge in volume faster than others, maybe I can enter the trade before the majority.  

---

## Strategy 1: API-Based Fast Entry  

The first version of my strategy used API-fed volume data to identify sudden spikes and enter trades early. The theory was simple:  
- Monitor real-time volume  
- When volume spikes relative to previous day, buy in  
- Hold briefly, then sell for profit  

**Result:**  
- Entry was faster than manual  
- But... many entries were **already too late**  
- Most price had already jumped by the time my trigger fired  

I realized that by the time a signal becomes *detectable*, it may already be too late for execution-based strategies to yield alpha.  

---

## Strategy 2: The Monkey Theory (Random Picks)  

Frustrated with signal-based approaches, I turned to something radically different — the **Monkey Theory**.  

> If markets are noisy and fundamentally unpredictable, could random selection outperform overfitted rules?  

This theory suggests that randomness may outperform naive heuristics. “Beginner’s luck” might not be luck — it could be **randomness outperforming over-strategy**.  

### Example Code: Random Pick Strategy  

```python
import random  

# Simulate buying random stocks  
kospi_stocks = ["005930", "000660", "035720", "068270", "207940"]  # example tickers  
random_portfolio = random.sample(kospi_stocks, 2)  

print("Today's picks:", random_portfolio)  
# Hypothetical: Next, you could fetch their daily % change and track results  
```

Surprisingly, in some backtests, this beat my speed-based entries — at least in terms of **simplicity and variance**.  

---

## Strategy 3: High-Frequency Buy/Sell  

Next, I tried a fast-in/fast-out bot:  
- Buy anything that surged >3% in 1 minute  
- Sell 1-2 minutes later  

The problem:  
- **You need to catch the surge at the exact moment**  
- If you're late, losses accumulate fast  
- False positives are common in volatile markets  

This strategy showed how **implementation lag** is a real issue — both in software and in human reaction time.  

---

## Reflection and Final Thoughts  

After experimenting with these approaches, I circled back to my original idea — but with more realism. Now, I aim to:  
- Use volume analysis for **watchlist filtering**, not live trading  
- Combine it with **basic random sampling** to reduce bias  
- Eventually let ML models decide *what kind of behavior* leads to returns  

---

## What I Learned  

- **Fast ≠ profitable** — latency and reaction time limit edge  
- **Randomness isn’t dumb** — it's often better than overfitting noise  
- **Automation is only as good as your signal timing**  

Sometimes, thinking like a monkey isn't a joke — it's a baseline to beat.  

---

## Next Steps  

- Build a logging system to track random picks vs signal picks  
- Simulate PnL (profit and loss) over 30 days  
- Create hybrid strategies using both randomness and real indicators  

---

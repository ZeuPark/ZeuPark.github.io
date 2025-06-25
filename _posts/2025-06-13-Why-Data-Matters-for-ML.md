---
title: "Why Data Matters: Lessons from Chasing Quality Datasets"  
date: 2025-06-13  
layout: single  
tags:  
  - data  
  - machine-learning  
excerpt: "This post reflects on the crucial role of data in training ML models, highlighting challenges in acquiring quality data and lessons from my experience building datasets manually."  
---

## Background  

One of the most painful lessons I’ve learned during my AI journey is this:  

> Without good data, no model — no matter how powerful — will perform well.  

Early on, I underestimated the importance of data quality. I thought that having a working model architecture and some basic training examples would be enough. But in reality, **garbage in, garbage out** applies more than ever in machine learning.  

---

## The Data Problem I Faced  

When I began training models for various NLP and LLM tasks, I quickly hit a wall: **I didn’t have enough data**, or the data I had was noisy, irrelevant, or too small.  

This led to several setbacks:  
- Models that overfit or failed to generalize  
- Validation loss stagnation  
- Poor real-world performance  

What frustrated me most was that I wasn’t struggling with model training — I was struggling just to get **meaningful input**.  

---

## Strategies I Considered  

To get around the lack of usable datasets, I explored several options:  

### 1. Crawling Public Web Data  

This seemed simple in theory: scrape content from websites using Python libraries like `requests`, `BeautifulSoup`, or `Selenium`. In practice:  
- It was slow  
- Many sites block bots  
- Formatting and cleaning were time-consuming  

Still, for some static content, it worked better than expected. Especially when I needed full pages and had specific content in mind.  

### 2. Using Public APIs  

For some government or open data platforms, using APIs was an option. However:  
- API limits and authentication made it hard to scale  
- Schema documentation was often incomplete  
- Pagination logic was more complex than expected  

In some cases, **manually downloading pages was actually faster and more reliable**.  

---

## What I Learned  

- **Good data is everything**. A small but clean dataset is more valuable than a massive but noisy one.  
- **Manual effort is sometimes worth it**. Crawling and cleaning data taught me how to recognize useful patterns and discard noise.  
- **Tool choice matters**. Understanding when to use APIs vs. when to crawl directly helped me build pipelines faster.  

---

## Realization  

Machine learning is not just about models. It’s about **data engineering**, **scraping**, **cleaning**, and even **collecting data ethically and legally**. That’s what turns experiments into usable tools.  

I now spend more time thinking:  
- Where does my data come from?  
- How reliable is it?  
- Is it representative of the problem I’m trying to solve?  

---

## Next Steps  

- Automate partial crawling for common patterns  
- Build a data quality checker before training  
- Share some cleaned datasets as part of my portfolio  

---

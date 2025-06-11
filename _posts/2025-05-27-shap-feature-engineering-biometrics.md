---
title: "SHAP and Feature Importance: A Shift Toward Biometric Signals"  
date: 2025-05-27  
layout: single  
tags:  

  - machine-learning  

excerpt: "SHAP values revealed that biometric signals were more important than effort-based metrics. Here's how that insight changed my feature engineering."  
---

## Introduction  

Effort-based features used to be at the core of my models.  
But today, SHAP analysis showed me something different: **biometric signals** like heart rate and body temperature mattered more.  

---

## What I Discovered  

- SHAP values pointed to `heart_rate`, `body_temperature`, and `respiration_rate` as more impactful than any effort-related metric.  
- This insight shifted my focus — I realized my model wasn’t learning from what I assumed mattered.  

---

## What I Decided to Build  

- `heart_rate_delta`: Difference between max and min heart rate during sessions.  
- `temp_peak_ratio`: Ratio of intervals where temperature exceeded a defined threshold.  
- I'm aiming for features that **explain physiological responses**, not just mechanical effort.  

---

## Why This Matters  

- SHAP gave me **interpretability**. It helped me trust my model — and question my assumptions.  
- The value of a feature isn’t in how intuitive it sounds, but how much it helps the model generalize.  

---

## What I’ll Try Next  

- Use SHAP values earlier in my pipeline for feature selection.  
- Compare models trained with vs. without biometric features.  
- Publish a notebook that documents this change and result shift.  

---
title: "From Confusion to Clarity: My Journey Into Machine Learning and Feature Engineering"
date: 2025-05-18
layout: single
tags:
  - machine-learning
  - preprocessing
  - feature-engineering
excerpt: "This post traces my path through the foundational struggles of machine learning and data preprocessing, and how a Russian number plate dataset helped me understand the true meaning of feature engineering."
---

## Introduction

When I first encountered machine learning (ML), it was exciting — and also totally overwhelming.  
What does it mean to train a model? How do I handle raw data? Do I really need preprocessing if the algorithm is strong enough?

This post is a reflection of the questions I asked, the false starts I had, and how I’m finally beginning to see **why feature engineering is the real power** behind effective ML.

---

## The Early Questions I Had

Here are some of the honest, beginner questions I asked while starting ML:

- “Isn't it ok to not do preprocessing”
- “feature engineering을 why does it matter? the graphs won't be used for the ML”
- "What is group X and y? How is it used in the algorith?”
- “What is the differences among many ML models? What are the purpose of each model and why are they important?”

And one of the biggest:
- “How many features are needed for the ML to get high credits?”

These weren’t just questions about code — they were about understanding **how ML thinks**.

---

## Working With the Russian Number Plate Dataset

To make this more real, I worked on a dataset containing **Russian car auction records**, which included:

- `plate` (numberplate)
- `date`, `price`
- `region_code`, `region_name`
- `government_code`, `agency`
- `forbidden`, `priority`, `significance`

### What I Tried

- Extracted meaningful segments from the plate (e.g. prefix letters)
- Determined if a plate was a government car using partial string matching (`startswith`)
- Merged regional dictionaries using `region_code`
- Removed or transformed outliers in price
- Created new binary columns from categoricals (like `forbidden == 1`)
- Converted `date` into month and year features

### What I Learned

- **Raw columns ≠ features**. Just having data isn’t enough — you have to **transform** it.
- Feature engineering means knowing the domain. In this case, understanding Russian plates helped me create useful features.
- Visualizing outliers helped me decide what to drop, not just guess.
- Government vehicle classification wasn’t in the original data — I **had to create that signal** from patterns.

---

## What I Thought About

All this made me realize:
- Machine learning without feature engineering is like cooking without prepping ingredients
- You can’t rely on the algorithm to figure out messy signals
- Even unsupervised tasks benefit from careful feature shaping

I used to think ML was about fancy algorithms. Now I think it’s about thoughtful representation.

---

## What I Want to Do Next

- Finish building a preprocessing pipeline for the plate dataset
- Apply `LabelEncoder` or `OneHotEncoder` where appropriate
- Use correlation matrices to filter out redundant features
- Build a basic classification model (e.g. RandomForest) with these features
- Practice on another public dataset and compare modeling results with and without preprocessing

---

Machine learning didn’t “click” for me because of math — it clicked because of feature engineering.  
And now, I finally understand why preprocessing is half the work.

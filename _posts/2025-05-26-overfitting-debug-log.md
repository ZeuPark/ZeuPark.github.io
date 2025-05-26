---
title: "Overfitting or Just Lucky? What I Learned Debugging a Too-Perfect ML Model"
date: 2025-05-26
layout: single
tags:
  - machine-learning


excerpt: "Sometimes your model is too accurate — suspiciously accurate. Here’s how I figured out whether I had a breakthrough or a bug."
---

## Introduction

Today, something strange happened.  
My model scored **99.7% accuracy** on the test set. At first, I was thrilled — then skeptical:  
*Is this overfitting, or did I make a mistake somewhere?*

This post documents the journey from that suspicion to discovery and learning.

---

## 1. “99% Accuracy... Is That Even Real?”

```python
from sklearn.ensemble import RandomForestClassifier

model = RandomForestClassifier()
model.fit(X_train, y_train)
model.score(X_test, y_test)
# Output: 0.997
```

**First suspicion**: Maybe there's data leakage.  
**Check**: Reinspect the train/test split.

```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(
    features, target, test_size=0.2, random_state=42, stratify=target
)
```

✅ Split looks fine. But the accuracy is still abnormally high.

---

## 2. “Am I Accidentally Predicting the Target Itself?”

Maybe the target or a proxy made it into the features? Let’s check `.corr()`:

```python
import pandas as pd

correlations = df.corr(numeric_only=True)["target"].sort_values(ascending=False)
print(correlations.head(5))
```

🔍 Turns out some features are nearly perfectly correlated with `target`.  
The culprit: a derived column closely related to the label — possibly calculated from it.

---

## 3. “What Features Should Be Dropped Then?”

Conclusion:
- Columns like IDs may act as surrogate keys and leak label information.
- Derived columns that are direct transformations of the target must be excluded.

✅ After removing those columns: new accuracy is **81.2%** — much more believable.

---

## What I Realized

- High accuracy can be a red flag.
- Data leakage is common and often subtle.
- Simple tools like `.corr()` can uncover big issues.
- Before trusting performance metrics, always question your data.

---

## What I Want to Do Next

- Automate feature checks for target leakage
- Add column validation in data split logic
- Build rules to detect label-like engineered features

---

When your model’s too good to be true,  
check the data before you celebrate.

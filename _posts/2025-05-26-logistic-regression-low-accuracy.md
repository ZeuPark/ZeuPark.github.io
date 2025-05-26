---
title: "Why Is My Logistic Regression So Bad? Troubleshooting Low Accuracy"
date: 2025-05-26
layout: single
tags:
  - machine-learning
  

excerpt: "I expected logistic regression to do decently — but it gave me 58% accuracy. Here's how I questioned everything, and what finally made it better."
---

## Introduction

I thought logistic regression would be a reliable baseline.  
But I got **58% accuracy** — not even close to acceptable.

Here’s how I debugged it, what mistakes I found, and what ultimately helped.

---

## 1. “Did I Forget to Normalize?”

Logistic regression isn’t distance-based, but feature scaling still matters.  
→ Apply `StandardScaler`:

```python
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)
```

📉 Accuracy rose slightly to **60%**.  
✅ Somewhat better, but still lacking.

---

## 2. “Is This Due to Class Imbalance?”

```python
import numpy as np

np.bincount(y_train)
# Output: [870, 130]
```

💡 Severe imbalance. Most predictions defaulted to class 0.

**Fix**: Use `class_weight='balanced'`

```python
from sklearn.linear_model import LogisticRegression

model = LogisticRegression(class_weight='balanced')
model.fit(X_train_scaled, y_train)
```

📈 Accuracy now **66%**. Recall improved significantly.

---

## 3. “What If Accuracy Isn’t the Best Metric?”

Check `precision`, `recall`, `f1` instead:

```python
from sklearn.metrics import classification_report

y_pred = model.predict(X_test_scaled)
print(classification_report(y_test, y_pred))
```

**Insight**: Accuracy hid key issues.  
- Precision was okay but recall was low  
- F1-score showed room for threshold tuning

---

## What I Realized

- Logistic regression is sensitive to preprocessing.
- Imbalanced data can ruin performance.
- Accuracy alone is a misleading metric — look at the full picture.

---

## What I Want to Do Next

- Try threshold tuning for F1 maximization
- Experiment with SMOTE for resampling
- Compare logistic regression with tree-based models

---

The model wasn’t bad —  
I just didn’t understand it well enough. Until now.

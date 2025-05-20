---
title: "Deeper Learning Into SQL"
date: 2025-05-20
layout: single
tags:
  - sql

excerpt: "Using real `.sql` files instead of tutorials helped me understand how SQL behaves in actual scenarios — including filtering, grouping, and debugging complex queries."
---

## Introduction

Instead of following textbook examples, today I worked with actual `.sql` files. This made the SQL feel more alive — more like a tool I could use in the real world rather than something abstract.

This post walks through what I did with the SQL files I used on May 20, and what each file helped me understand better.

---

## What I Practiced

### 📁 File: `w3schools`

This file contained queries that made me apply and review the following:

- **Date filtering** using `MONTH()` and `YEAR()` functions
- **Aggregate functions** like `COUNT()`, `AVG()` on grouped results
- **Grouping data** using `GROUP BY` on customer behavior
- **Filtering groups** using `HAVING` instead of `WHERE`

Example:

```sql
SELECT customer_id, COUNT(*) AS order_count
FROM orders
GROUP BY customer_id
HAVING order_count >= 3;
```

This helped me understand that:
- `HAVING` works after aggregation
- Without `GROUP BY`, I can't use `HAVING`
- `WHERE` filters **before**, `HAVING` filters **after**

---

## What I Learned

- SQL is not just about selecting rows — it's about **summarizing behavior**
- Function order (`WHERE`, `GROUP BY`, `HAVING`, `ORDER BY`) is critical
- Simple mistakes (like putting `HAVING` without `GROUP BY`) gave syntax errors that helped me remember structure better
- Writing a query from scratch and **debugging why it fails** teaches more than copying one that already works

---

## What I Thought About

While working with this file, I realized:
- I’m not afraid of trying longer queries anymore
- It’s better to read and **modify existing SQL** than always write from zero
- Comments in `.sql` files are like documentation for your thinking — and I want to start leaving more of them

---

## What I Want to Do Next

- Practice writing a summary report from orders (like total revenue per month)
- Try using nested subqueries to filter on aggregated conditions
- Learn how to **refactor long queries** into readable blocks
- Explore creating **views** or temporary tables for reuse

---

This session reminded me why I like SQL — it’s not just a language, it’s a way of thinking logically with data.  
And every file I work with helps me reason more clearly.

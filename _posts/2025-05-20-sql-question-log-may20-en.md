---
title: "Learning SQL One Question at a Time: What I Asked and Understood on May 20"
date: 2025-05-20
layout: single
tags:
  - sql

excerpt: "SQL learning doesn't come from watching tutorials — it comes from asking real questions. This post is a reflection of the questions I asked on May 20 and how each one helped me build deeper understanding."
---

## Introduction

Today, I didn’t just “study SQL.” I struggled with it, debugged it, rephrased it, and kept asking questions.  
Each time something didn’t work, it pushed me to think more clearly — and that’s exactly how I learned.

This post is a log of my real questions and the understanding I built through them.

---

## 1. “Why does SQL give an error if I use `ORDER BY` twice?”

```sql
-- Incorrect
ORDER BY title DESC
ORDER BY rental_rate DESC;
```

**The problem**: SQL only allows one `ORDER BY` clause. You must separate multiple sort conditions with commas.  
**Fix**:

```sql
ORDER BY title DESC, rental_rate DESC;
```

---

## 2. “How do I find words that are exactly 5 letters long?”

**Answer**: Use `CHAR_LENGTH()` or `LENGTH()` to filter based on string length.

```sql
SELECT * FROM users WHERE CHAR_LENGTH(username) = 5;
```

---

## 3. “My date is in Y-M-D format. How do I filter by year?”

**Answer**: Use the `YEAR()` function to extract just the year from a date column.

```sql
SELECT * FROM orders WHERE YEAR(order_date) = 2023;
```

---

## 4. “Why do I get an error when I use `HAVING`?”

**The issue**: `HAVING` must follow `GROUP BY` and only works on aggregated values.  
Use `WHERE` to filter before grouping, and `HAVING` to filter after.

```sql
SELECT customer_id, COUNT(*) AS order_count
FROM orders
GROUP BY customer_id
HAVING order_count >= 5;
```

---

## 5. “How do I load a `.sql` file into MySQL using DBeaver?”

**Answer**:
- In DBeaver, connect to your database
- Right-click the connection → `Tools > Execute SQL Script`
- Choose your `.sql` file and run it

---

## What I Realized

Today wasn’t about learning new SQL commands — it was about understanding **how to think in SQL**:

- Why the order of clauses matters  
- Why small syntax choices break whole queries  
- Why it’s better to ask lots of tiny questions than to memorize templates

---

## What I Want to Do Next

- Practice writing grouped queries with multiple conditions
- Learn to debug long SQL blocks by breaking them into parts
- Start using aliases more clearly to improve readability
- Try creating subqueries with `IN`, `EXISTS`, and nested `SELECT`s

---

SQL isn’t just a query language — it’s a way of thinking about logic, filtering, and structure.  
And today, I got better at thinking like that — one question at a time.

---
title: "Deeper SQL Practice: Subqueries, Functions, Joins, and Mistakes I Learned From"
date: 2025-05-20
layout: single
tags:
  - sql
excerpt: "Today I practiced more advanced SQL concepts — from `EXISTS` and string functions to creating tables from subqueries — and made a lot of mistakes that taught me more than tutorials ever could."
---

## Introduction

Today was one of my most hands-on SQL days. I didn't just write `SELECT * FROM table` — I used subqueries, made mistakes with joins, applied string functions, created tables from queries, and tested real business-style logic.

This post summarizes what I learned by asking questions, writing SQL, and breaking things until they made sense.

---

## `EXISTS`, `ANY`, `ALL`, `IN`: What’s the Difference?

I asked:

> “What’s the actual difference between `EXISTS`, `ANY`, `ALL`, and `IN`?”

Here’s what I learned:

- **`EXISTS`**: As soon as it finds a match, it stops. Efficient for large subqueries. It only checks whether **a result exists**, not the result itself.
- **`ANY`**: Compares a value to **any of the subquery results** — like a series of `OR`.
- **`ALL`**: Returns true **only if all comparisons** are true — like a series of `AND`.
- **`IN`**: Equivalent to many `=` checks. Simple but less flexible than `ANY`.

---

## SQL Functions and Data Shaping

I practiced using built-in SQL functions to reshape data:

```sql
SELECT now();
SELECT substr("2025-05-20", 1, 4) AS year;
SELECT concat(address, " ", city) AS full_address FROM customers;
```

- **`TRIM()`**, **`LTRIM()`**, **`RTRIM()`**: Cleaning whitespace
- **`SUBSTR()`**: Splitting dates or fields
- **`CEIL()` / `FLOOR()`**: Rounding numbers
- **`DATEDIFF()` / `ADDDATE()`**: Working with dates

These weren’t just for show — I saw how they help clean up reports and calculate actual values like time difference or full address strings.

---

## Creating Tables from Queries

I learned:

```sql
CREATE TABLE emp2 AS SELECT * FROM emp;
```

- You can create a new table from an existing one (without copying constraints).
- To copy just structure: `WHERE 1=0`.
- You can also copy only filtered subsets:

```sql
CREATE TABLE emp4 AS
SELECT empno, ename, sal
FROM emp WHERE deptno IN (10, 20);
```

This helped me understand how **SQL is also a data engineering tool**, not just for querying.

---

## Realistic JOIN Challenges

I worked on this query:

```sql
SELECT customername, productname, price * quantity AS totalPrice
FROM customers
LEFT JOIN orders USING (customerID)
LEFT JOIN order_details USING (orderID)
LEFT JOIN products USING (productID);
```

**Mistake I made**: I accidentally did `ON d.productID = d.productID` instead of joining `c.productID = d.productID`.

**Fix**: Use `USING(productID)` or a proper `ON` clause.

---

## Key Questions I Asked

- “Why does `EXISTS` perform better than checking full subquery results?”
- “How can I copy a table’s structure but not its data?”
- “How do I write a join query that multiplies price and quantity?”
- “Why is `LIKE 'Findland%'` not returning any rows? (typo!)”

---

## What I Learned

- Functions are essential for formatting output.
- Joins are powerful — and also easy to mess up.
- Subqueries and derived tables are key for modular SQL.
- Making a mistake teaches more than reading the manual.

---

## What I Want to Do Next

- Practice `EXISTS` in nested queries with early exits
- Clean and format customer reports using `TRIM`, `SUBSTR`, `CONCAT`
- Get comfortable creating and dropping temporary summary tables
- Start working with views to package recurring logic

---

SQL is not just a query tool — it’s a full data thinking environment.  
Today’s session made me appreciate how powerful it can be when I use it like a real language, not just a cheat sheet.

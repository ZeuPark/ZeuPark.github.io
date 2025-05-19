---
title: "SQL Practice Log: Movie Data, Date Filtering, and Real-World Queries"
date: 2025-05-19
layout: single
tags:
  - sql

excerpt: "Working through realistic SQL queries with movie data and date filters helped me move from syntax understanding to meaningful analysis."
---

## Introduction

Today I practiced SQL using various real datasets — including one based on movies (SAKILA), and others with date-specific filters.  
Instead of just focusing on syntax, I tried to treat it like real-world data analysis. This post summarizes what I did, what worked, and what confused me.

---

## The Problem

I had three goals in mind:
1. Query movie data with conditions and ordering
2. Filter based on date formats (e.g. specific months)
3. Use `JOIN`, `GROUP BY`, and subqueries in a meaningful way

To do this, I used multiple `.sql` files and ran queries in DBeaver against structured tables.

---

## What I Practiced

### Movie Query (SAKILA)
- Selected movie titles and filtered by rental rate
- Ordered results with multiple conditions

```sql
SELECT title, rental_rate
FROM film
WHERE rental_rate >= 4.99
ORDER BY title DESC, rental_rate DESC;
```

### Filtering by Month

In a file with 2024 date data, I tried filtering by month value using `MONTH()`:

```sql
SELECT *
FROM orders
WHERE MONTH(order_date) = 5;
```

This helped isolate May-specific data regardless of the year.

### Grouping & Having

I also worked with `GROUP BY` and `HAVING` to count or limit groups:

```sql
SELECT customer_id, COUNT(*) AS order_count
FROM orders
GROUP BY customer_id
HAVING order_count >= 5;
```

This was useful to detect power users — customers who ordered more than five times.

---

## What I Learned

- How to sort results with multiple `ORDER BY` conditions
- Why `HAVING` is used after `GROUP BY` (not `WHERE`)
- How to pull only a specific month's data with `MONTH(date_column)`
- `COUNT(*)` with `GROUP BY` can reveal patterns I never saw with basic filters

---

## What I Thought About

I realized that:
- SQL gets powerful not when you *know* every command, but when you *combine* them effectively
- Realistic datasets (like movies, orders, rentals) make practicing fun and more memorable
- Reading and modifying example queries helped me learn faster than starting from scratch

---

## What I Want to Do Next

- Try building my own mini database (like a book store or music library) and write queries from scratch
- Learn window functions (`RANK`, `ROW_NUMBER`, `OVER()`)
- Practice writing subqueries that return useful summaries

---

SQL isn’t just about querying — it’s about **thinking like an analyst**.  
And today, I felt like I took one more step in that direction.

---
title: "Learning SQL Through Questions: How I Built My Understanding One Query at a Time"
date: 2025-05-16
layout: single
tags:
  - sql

excerpt: "Today I worked through practical SQL problems — from basic filtering to ordering, joins, and searching by string length — and learned more by asking specific questions."
---

## Introduction

SQL has always seemed simple — just SELECT and WHERE, right?  
But today, as I asked question after question and fixed tiny mistakes, I realized SQL is all about **clarity** and **logic**. This post documents what I asked, what I struggled with, and how I improved my understanding one query at a time.

---

## The Problem

I didn’t set out with a big goal. I just wanted to:
- Filter data with conditions
- Sort and order results properly
- Count or match string lengths
- Understand how to work with table structure
- Use joins (later)

But the more I typed, the more I realized how fragile SQL syntax can be.

---

## My Questions

Here are some real questions I asked today:

- “How do I filter by year if the date format is Y-M-D?”
- “How do I find words that are exactly 5 letters long?”
- “Why is `ORDER BY` giving an error when I use it twice?”
- “How do I check the database name again?”
- “How do I load a `.sql` file into MySQL using DBeaver?”

Each question came from running into a block — and **fixing it taught me more than any tutorial**.

---

## What I Learned

### 1. Filtering by Year
You can use `YEAR()` function to extract the year from a `DATE` column.

```sql
SELECT * FROM orders WHERE YEAR(order_date) = 2023;
```

### 2. Finding 5-letter Words
Using `LENGTH()` or `CHAR_LENGTH()` helps:

```sql
SELECT * FROM users WHERE CHAR_LENGTH(username) = 5;
```

### 3. Ordering Properly
SQL doesn't allow multiple `ORDER BY` keywords. Use a single `ORDER BY` and list multiple columns:

```sql
ORDER BY title DESC, rental_rate DESC;
```

### 4. Database Info
You can run:

```sql
SELECT DATABASE();
```

### 5. Importing `.sql` File into MySQL via DBeaver
- Connect to your database
- Right-click → Tools → Execute SQL Script → Select your file

---

## What I Thought About

Today showed me that:
- SQL is readable, but that doesn’t make it error-proof
- Tiny syntax issues (like a second `ORDER BY`) can confuse you for a while
- You remember more when you fix real bugs, not just when you follow examples

---

## What I Want to Do Next

- Practice writing full queries for realistic datasets (like film or world)
- Try more subqueries and multi-table joins
- Use DBeaver’s ERD and export/import tools to navigate databases visually
- Create a cheat sheet of my most-used SQL snippets

---

I didn’t build a full project today — but I built **real confidence**.  
And sometimes, that’s more important than writing one perfect query.

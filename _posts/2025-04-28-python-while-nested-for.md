---
title: "Using While and Nested For Loops in Python"
date: 2025-04-28
layout: single
tags:
  - python

excerpt: "In this post, I practiced using while loops and nested for loops to print number patterns, multiplication tables, and shapes like triangles and diamonds."
---

## Why I studied this

I wanted to get comfortable with `while` and nested `for` loops.  
They are important when solving repetitive problems or printing shapes in the console.

---

## What I did

### Using while loops

```python
n = 1
while n <= 5:
    print(n)
    n += 1
```

This prints numbers from 1 to 5.

```python
num = 1
while num < 100:
    num += 1
    if num % 2 == 0:
        continue
    if num > 30:
        break
    print(num)
```

This skips even numbers and stops after printing odd numbers under 30.

---

### Printing multiplication tables using nested for loops

```python
for dan in range(2, 10):
    for i in range(1, 10):
        print(f"{dan} x {i} = {dan*i}", end="	")
    print()
```

This prints the 2 to 9 multiplication table.

---

### Triangle pattern using nested for loop

```python
for i in range(1, 6):
    for j in range(i):
        print("*", end="")
    print()
```

This prints a right-angled triangle with stars.

---

### Diamond shape pattern

```python
n = 5
for i in range(n):
    for j in range(n - i - 1):
        print(" ", end="")
    for k in range(i * 2 + 1):
        print("*", end="")
    print()

for i in range(n - 2, -1, -1):
    for j in range(n - i - 1):
        print(" ", end="")
    for k in range(i * 2 + 1):
        print("*", end="")
    print()
```

This prints a diamond pattern using stars.

---

## What I learned

- `while` loops repeat as long as a condition is true
- `for` loops with `range()` are great for counting and patterns
- Nested loops can be used to print shapes or solve grid-based problems

---

## What I want to do next

I want to practice using `while` loops with user input and try creating more advanced shapes using loops.

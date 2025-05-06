---
title: "Practicing Conditions and Understanding List Copy in Python"
date: 2025-04-25
layout: single
tags:
  - python
  - if-statement
  - comprehension
  - copy
excerpt: "In this post, I practiced using if statements and learned the difference between shallow and deep copy using list comprehension."
---

## Why I studied this

I wanted to get better at using conditions in Python and understand how list copying works.  
Both are basic but important in writing correct and efficient programs.

---

## What I did

### Using if, elif, and else

```python
n = int(input("Enter a number: "))

if n > 0:
    print("positive number")
elif n == 0:
    print("zero")
else:
    print("negative number")
```

This checks if a number is positive, zero, or negative.

---

### Wage calculation example

```python
name = input("Name: ")
hours = int(input("Work hours: "))
pay_per_hour = int(input("Hourly wage: "))

if hours > 20:
    extra = int(pay_per_hour * 0.5 * (hours - 20))
else:
    extra = 0

basic = hours * pay_per_hour
total = basic + extra

print(f"{name}'s total wage is {total} (basic {basic} + extra {extra})")
```

I used conditions to add extra pay only if hours worked are more than 20.

---

### Shallow vs Deep Copy

```python
a = [1,2,3,4,5,6,7,8,9,10]
b = a
a[2] = -3

print(a)  # changed
print(b)  # also changed
```

This shows shallow copy — both `a` and `b` refer to the same memory.

---

### Making a real deep copy

```python
b = []
for item in a:
    b.append(item)
```

Or with list comprehension:

```python
b = [item for item in a]
```

This creates a completely new list with the same values.

---

## What I learned

I learned how to use if-elif-else to control program logic.  
I also finally understood how list copying works, especially why shallow copy can cause bugs.

---

## What I want to do next

I want to practice more list comprehensions and write more condition-based mini programs like menus or calculators.

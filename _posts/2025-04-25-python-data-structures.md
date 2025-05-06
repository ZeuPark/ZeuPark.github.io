---
title: "Learning Python Data Structures: List, Tuple, Dictionary"
date: 2025-04-25
layout: single
tags:
  - python

excerpt: "I practiced how to use three major Python data structures: lists, tuples, and dictionaries. Here's how each one works and how they are different."
---

## Why I studied this

I'm learning about basic data structures in Python.  
Lists, tuples, and dictionaries are very useful and appear in almost every program.  
I wanted to understand how to use each one and when to use them.

---

## What I did

### List operations

```python
a = [1, 2, 3, 4]
b = [5, 6, 7, 8]

c = a + b
print(c)

a.extend(b)
print(a)

del c[0]
print(c)

del c[4:]
print(c)

a = [4,3,5,6,7,32,3,23,24,23,57,234,35]
a.sort()
print(a)
a.reverse()
print(a)
```

I practiced adding, extending, deleting, and sorting lists.

---

### Tuple basics

```python
a = (1,2,3,4,5)
print(a, type(a))

a, b, c = 5, 7, 9
print(a, b, c)

def myfunc1():
    return 3, 4

a = myfunc1()
print(a)
```

Tuples use parentheses and are immutable.  
They are faster and safe for fixed data.  
Python automatically packs multiple return values into a tuple.

---

### Dictionary usage

```python
colors = {"red": "빨간색", "blue": "파란색", "green": "초록색"}

print(colors["red"])
print(colors["blue"])

colors["black"] = "검은색"
colors["red"] = "빨강"

if "pink" in colors:
    print(colors["pink"])
else:
    print("pink does not exist")

print(colors.keys())
print(colors.items())
```

Dictionaries use keys and values.  
I learned how to access, add, and update values.  
If the key doesn’t exist, it’s better to check before accessing.

---

## What I learned

- Lists are flexible and good for ordered data that can change
- Tuples are fast and useful for fixed collections and multiple returns
- Dictionaries store key-value pairs and are perfect for lookups

---

## What I want to do next

I want to practice sets and also learn how to combine different types in one structure like list of dictionaries or tuple of lists.

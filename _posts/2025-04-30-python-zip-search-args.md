---
title: "Working with Zip, Search, and Variable Arguments in Python"
date: 2025-04-30
layout: single
tags:
  - python

excerpt: "In this post, I practiced using zip to combine lists, understood how sequential search works, and wrote functions with variable arguments using *args."
---

## Why I studied this

I wanted to learn how to combine data from multiple lists using `zip`, understand how basic search works, and define functions that accept a flexible number of arguments.

---

## What I did

### 1. Combining lists with zip()

```python
a = ["a", "b", "c", "d", "e"]
b = [1, 2, 3, 4, 5]

for item in zip(a, b, a):
    print(item)
```

This combines values from the lists into tuples.  
`zip()` pairs elements based on index position.

---

### 2. Understanding sequential (linear) search

```python
# Sequential search reads data one by one
# Time complexity: O(n)

for i in range(0, n):
    if data[i] == key:
        return i
return -1
```

This method checks each element one by one until it finds the target.  
The worst-case time is proportional to the size of the list (O(n)).

---

## 3. Variable argument functions with *args

### Basic usage

```python
def myadd(*args):
    for a in args:
        print(a)

myadd(1, 2)
myadd(1, 2, 3)
```

`*args` allows the function to receive any number of arguments.  
These are packed into a tuple.

---

### Adding all values with *args

```python
def myadd2(*data):
    s = 0
    for i in data:
        s += i
    return s

print(myadd2(1, 3, 5))           # 9
print(myadd2(1, 3, 5, 7, 9))     # 25
```

Functions with `*args` are useful when the number of inputs is not fixed.

---

## What I learned

- `zip()` is useful to merge lists into tuples based on index.
- Sequential search is simple but not fast for large data.
- `*args` helps write flexible and reusable functions.

---

## What I want to do next

I want to combine `*args` with other logic like conditions or loops, and also try using `zip()` to format data for printing or analysis.

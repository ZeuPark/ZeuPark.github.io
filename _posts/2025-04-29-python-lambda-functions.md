---
title: "Practicing Lambda Functions in Python"
date: 2025-04-29
layout: single
tags:
  - python

excerpt: "I practiced lambda functions in Python, learning how to use them for short anonymous functions, pass them as arguments, and filter lists."
---

## Why I studied this

I wanted to understand what lambda functions are and how they are used in Python.  
They are useful for short, one-time functions especially when combined with tools like `filter`, `map`, or function parameters.

---

## What I did

### Regular function vs lambda

```python
def add(x=0, y=0, z=0):
    return x + y + z

myadd = add
print(myadd(3, 4, 5))  # 12
```

Functions are just variables. I assigned the `add` function to another name and used it.

---

### Passing functions as parameters

```python
def myfunc(x, y, callback):
    result = callback(x, y)
    print(result)

def add(x, y):
    return x + y

myfunc(4, 5, add)
myfunc(4, 5, lambda x, y: x - y)
```

I can pass a function as a parameter.  
`lambda x, y: x - y` is a one-time function that subtracts two numbers.

---

### Lambda functions in a list

```python
funcList = [
    lambda x, y: x + y,
    lambda x, y: x - y,
    lambda x, y: x * y,
    lambda x, y: x / y,
]

for func in funcList:
    print(func(9, 7))
```

I made a list of lambda functions to perform different math operations.

---

### Using lambda with filter()

```python
a = [1,2,3,4,5,6,7,8,9,10]

def isEven(n):
    return n % 2 == 0

for i in filter(isEven, a):
    print(i)

# same as above with lambda
for i in filter(lambda x: x % 2 == 0, a):
    print(i)
```

`filter()` uses a function to select only items that return `True`.  
Lambdas are useful for writing these short filters.

---

## What I learned

Lambda functions are great for writing quick, simple logic.  
They can be passed like normal functions, and help clean up code when used with things like `filter()`.

---

## What I want to do next

I want to try using lambda with `map()` and `sorted()`, and understand where lambdas are better than regular `def` functions.

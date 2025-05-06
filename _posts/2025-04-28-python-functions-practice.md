---
title: "Learning How to Define and Use Functions in Python"
date: 2025-04-28
layout: single
tags:
  - python
  - function
  - return
excerpt: "In this post, I practiced how to define and use functions in Python, including parameters, return values, and simple examples."
---

## Why I studied this

Functions make code reusable and cleaner.  
I wanted to learn how to write functions, pass values to them, and return results.

---

## What I did

### Basic function without parameters

```python
def greeting():
    print("Hello!")
    print("Welcome to my program")

greeting()
```

This function prints a simple message.  
Functions are defined using `def` and called by name.

---

### Function with parameters

```python
def say_hi(name):
    print(f"Hi {name}, nice to meet you!")

say_hi("Chris")
say_hi("Alex")
```

Functions can receive data through parameters.

---

### Function with return value

```python
def square(x):
    return x * x

result = square(5)
print(result)  # 25
```

The `return` keyword sends a value back from the function.

---

### Combining functions

```python
def add(a, b):
    return a + b

def multiply(x, y):
    return x * y

print(add(3, 4))        # 7
print(multiply(5, 6))   # 30
```

You can define multiple functions and use them together.

---

## What I learned

I learned how to write and call functions, use parameters, and return results.  
Functions help organize code and avoid repetition.

---

## What I want to do next

I want to try writing functions that work with lists or loops, and maybe build a small calculator program using functions.

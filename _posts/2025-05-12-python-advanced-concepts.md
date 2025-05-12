---
title: "Exploring Advanced Python Concepts: class methods, static methods, decorators, and singletons"
date: 2025-05-12
layout: single
tags:
  - python

excerpt: "I studied four key Python concepts — class methods, static methods, decorators, and the singleton pattern — to better understand how to write cleaner and more structured code."
---

## Introduction

As I explored deeper into Python, I studied four powerful and sometimes confusing concepts:
- Class Methods
- Static Methods
- Decorators
- The Singleton Pattern

Here’s a summary of what I learned, what I struggled with, and how I plan to use these ideas going forward.

---

## Class Methods

Class methods are defined with `@classmethod` and take `cls` instead of `self`. I learned they are useful for:
- Creating alternative constructors
- Modifying class-level data
- Acting as factory functions

**What was tricky**: Understanding the difference between `cls` and `self`, and when to use class methods over instance methods.

---

## Static Methods

Static methods use `@staticmethod` and do not take `self` or `cls`. They’re just plain functions inside a class.

**Use case**: When a method logically belongs to a class but doesn’t need access to instance or class data.

**What was tricky**: I thought static methods could still access instance variables — they can’t.

---

## Decorators

Decorators wrap a function to modify its behavior. I created a decorator that logs function inputs and outputs.

```python
def logger(func):
    def wrapper(*args, **kwargs):
        print("Calling", func.__name__)
        result = func(*args, **kwargs)
        print("Returned", result)
        return result
    return wrapper
```

**What was tricky**: The idea of functions returning functions was hard to grasp at first. Also, keeping track of the `*args`, `**kwargs` syntax.

---

## Singleton Pattern

A singleton ensures a class has only one instance. I implemented this pattern in Python using a class variable to store the instance.

**Why it matters**: Useful for shared resources like database connections or configuration.

**What was tricky**: Avoiding multiple initializations and understanding how `__new__` or class-level flags work to enforce the singleton.

---

## What I learned

- Python has a lot of powerful tools for organizing logic
- Decorators and static methods helped me clean up repeated code
- Understanding class-level vs instance-level concepts is essential

---

## What I want to do next

- Use class methods in real project initializations
- Apply decorators to log or secure API functions
- Explore design patterns like Factory and Observer
- Build a settings manager using the Singleton pattern

These concepts take time to sink in — but they’re exactly what separates beginner code from scalable, professional code.

---
title: "Building a Vending Machine in Python Using OOP"
date: 2025-05-10
layout: single
tags:
  - python
excerpt: "This post explains how I built a basic vending machine system in Python using object-oriented programming, and what challenges I faced while applying class-based design."
---

## Introduction

I attempted to build a vending machine system in Python with a strong emphasis on object-oriented programming (OOP). I wanted to use **as many objects and classes as possible** — even if it meant going slower — because I knew this approach would help me understand real software structures better.

---

## System Overview

The program is made up of two main classes:

- `VendingMachine`: Handles product lists, user interactions, and money processing.
- `Administrator`: Adds new items and can (eventually) modify or remove products. It loads and saves data using `pickle`.

### Example snippet

```python
goods = {}
goods["brand"] = self.writeBrand()
goods["price"] = self.writePrice()
goods["unique_key"] = self.keyGenerator()
goods["stock"] = self.writeStock()
self.vm.goodsList.append(goods)
```

This method in the `Administrator` class adds new products dynamically.

---

## What I struggled with

- **How to pass and update shared data**: I needed both classes to work on the same product list, so I passed the `VendingMachine` instance to `Administrator`.  
    → *This made me understand how objects can refer to and manipulate shared states*.
  
- **Input validation**: Ensuring that user inputs (like price or stock) were valid integers made me think more about user experience and edge cases.

- **Unique product keys**: I had to manually track and generate a `unique_key` for each item. Later I realized this could be automated better or managed by using a database.

- **Object vs Dictionary**: I originally used dictionaries to store item info. I want to refactor this into its own class, like `Product`, for better encapsulation.

---

## What I learned

- Sharing state between classes by passing object references is extremely powerful and essential in larger applications.
- Separating admin tasks from customer-facing logic made my code much cleaner.
- Using `pickle` taught me how data can be saved and restored across sessions.

---

## What I want to do next

- Create a `Product` class to replace dictionaries and better represent individual items.
- Implement the remaining admin functions: edit, remove, and restock products.
- Add inventory checks before dispensing items.
- Eventually build a GUI version using tkinter.

This project wasn’t finished — but it’s already taught me a lot about how real systems are structured with OOP.

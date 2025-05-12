---
title: "What Confused Me While Building My Vending Machine in Python"
date: 2025-05-10
layout: single
tags:
  - python

excerpt: "This post documents the real struggles I faced while trying to build a vending machine using Python and object-oriented design."
---

## Introduction

Building a vending machine using OOP was exciting, but also frustrating. Here are some of the most **real** issues I ran into — things that made me stop and wonder, "Why is this not working?" or "What does that even mean?"

---

## Common Confusions I Faced

### 1. Accessing Variables from `__init__`

I didn’t understand why I had to use `self.variable` inside other methods. I kept forgetting it and getting errors.

```python
class Example:
    def __init__(self):
        self.money = 0

    def add_money(self):
        self.money += 100  # NOT just money += 100
```

---

### 2. Using One Method Inside Another

Calling a method inside the same class was confusing. I thought just writing the method name was enough, but no — you need `self.`.

```python
def run(self):
    self.check_stock()  # not just check_stock()
```

---

### 3. Too Many If-Statements

When I had a lot of menu choices or checks, my code got messy. I learned about:

- Using dictionaries instead of if-chains
- Breaking big methods into smaller ones
- Early returns to exit logic early

---

### 4. Reading from List of Dictionaries

```python
for item in self.goodsList:
    print(item["brand"])  # Not item.brand
```

I kept trying to use dot notation instead of indexing with `["key"]`.

---

### 5. Getting Valid User Input

I struggled to validate numeric input within a range:

```python
if x.isdigit() and 1 <= int(x) <= 3:
    # valid
```

I learned to chain the condition and convert safely.

---

### 6. `if __name__ == "__main__"`

This line confused me. It turns out it just checks if this file is being run directly — useful for testing.

---

### 7. "Why is everything running from one line?"

Calling `a.moneyOutput()` runs several other functions. That's because methods inside methods were being called — like a chain reaction.

---

### 8. Using `==` but Nothing Happens

I wrote `x == 3` and expected it to "do something". But `==` just compares — I had to put it **inside an if-statement** to make it do something.

---

### 9. Why `pass` Looks Grayed Out

My editor made `pass` look faded, which made me think something was wrong. Turns out it's just a placeholder, and the editor is reminding me it's incomplete.

---

### 10. Why Didn’t `print()` Work?

Sometimes I used `return` in a function but forgot to `print()` the result. I assumed the result would just appear — wrong.

---

### 11. Redundant Function Calls

I was accidentally calling `chooseNumber()` more than once because I didn’t reuse the return value. Fixing it meant **storing the result in a variable and reusing it**.

---

## What I learned

These issues taught me to:
- Slow down and trace the flow of function calls
- Think carefully about variable scope and data flow
- Understand how small misunderstandings cause bugs that feel like magic

---

## What I want to do next

I want to:
- Practice using `self` properly until it becomes second nature
- Build small examples that isolate just one of these confusions
- Teach someone else these mistakes so they learn faster

This might not be my most polished project — but it’s one of the most honest ones I’ve done.

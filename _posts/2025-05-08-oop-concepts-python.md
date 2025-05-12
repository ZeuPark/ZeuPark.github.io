---
title: "Understanding OOP in Python: Abstraction, Encapsulation, and Polymorphism"
date: 2025-05-08
layout: single
tags:
  - python
excerpt: "Through a simple student score management program, I explored three core concepts of object-oriented programming: abstraction, encapsulation, and polymorphism."
---

## Introduction

While building a student score management program in Python, I got to apply and better understand some core object-oriented programming (OOP) principles — **abstraction**, **encapsulation**, and **polymorphism**. Instead of just reading theory, this hands-on approach helped me recognize how these concepts solve real design problems.

---

## OOP Concepts in Action

### Abstraction: Hiding the complexity

In the `ScoreManager` class, the user just selects menu options like "Add", "Print", "Search", or "Sort". They don’t need to know what `pickle`, `lambda`, or `process()` are doing under the hood. This is **abstraction** — showing only the necessary interface and hiding the internal logic.

```python
def start(self):
    funcList =[None, self.append, self.printAll, 
               self.search, self.modify, 
               self.delete, self.sort]    
    ...
```

This function selection through indexing abstracts complex logic behind clean, numbered options.

---

### Encapsulation: Protecting internal state

Each `ScoreData` object has internal attributes like `name`, `kor`, `eng`, `mat`, and derived attributes like `total`, `avg`, and `grade`. All calculations happen inside `process()`. No external class manipulates these values directly.

```python
def process(self):
    self.total = self.kor + self.eng + self.mat 
    self.avg = self.total/3 
    ...
```

The idea is that data and its behavior are bundled together, and other parts of the code shouldn't interfere with how the grade is calculated. That’s **encapsulation**.

---

### Polymorphism: Same interface, different behavior

Inside `ScoreManager`, we can loop over `scoreList` and call `print()` on each item, regardless of their internal state. Because every item is a `ScoreData` object, the same method name `print()` works for all — this is **polymorphism** in action.

```python
def printAll(self):
    for s in self.scoreList:
        s.print()
```

Every object knows how to “print itself”, and we don't need to write `if-else` statements to handle different types.

---

## What I learned

At first, these OOP concepts were abstract terms for me. But through building this system:
- I understood how abstraction makes user-facing code simpler and cleaner.
- Encapsulation helps prevent bugs by isolating the logic inside its class.
- Polymorphism lets us design flexible systems that can handle different objects in the same way.

I also learned how these ideas make my code more **scalable**, **maintainable**, and **easier to test**.

---

## What I want to do next

I want to:
- Try using inheritance and method overriding to implement a new type of user, like `TeacherScoreData`.
- Add file-based loading and saving for different user types.
- Improve this program into a GUI application using tkinter or PyQt.

This project helped me internalize OOP in a way that makes me more confident about future Python projects.

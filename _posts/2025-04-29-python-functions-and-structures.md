---
title: "Working with Functions and Data Structures in Python"
date: 2025-04-29
layout: single
tags:
  - python
  - function
  - dictionary
  - list
  - reference
excerpt: "I practiced creating Python functions that work with dictionaries and lists. I also explored the difference between value and reference in function arguments."
---

## Why I studied this

I wanted to write cleaner programs by organizing code into functions.  
I also wanted to understand how data is passed into functions, especially with dictionaries and lists.

---

## What I did

### 1. Structuring student scores using functions

```python
studentList = [{"name": "Chris", "kor": 90, "eng": 80, "mat": 70}]

def calculate_total(student):
    student['total'] = student["kor"] + student["eng"] + student["mat"]

def calculate_avg(student):
    student['avg'] = student["total"] / 3

def calculate_grade(student):
    if student['avg'] > 90:
        student['grade'] = "수"
    elif student['avg'] > 80:
        student['grade'] = "우"
    elif student['avg'] > 70:
        student['grade'] = "미"
    else:
        student['grade'] = "가"
```

Each function has a single role — keeping things clear and reusable.

---

### 2. Calculating weekly wages with dictionaries

```python
workerList = [
    {"name": "Chris", "work_time": 30, "per_pay": 20000},
    {"name": "Charles", "work_time": 20, "per_pay": 30000},
    {"name": "Jessie", "work_time": 50, "per_pay": 20000}
]

def process(worker):
    worker['pay'] = worker['work_time'] * worker['per_pay']
```

Each worker is a dictionary, and the function modifies it directly.

---

### 3. Understanding value vs reference in function arguments

```python
def toDouble(x):
    x = x * 2

a = 10
toDouble(a)
print(a)  # Still 10
```

Integers are passed by value, so changes inside the function don’t affect the outside.

```python
def toDouble2(mydict):
    mydict["x"] *= 2
    mydict["y"] *= 2

mydict = {"x": 1 , "y": 1}
toDouble2(mydict)
print(mydict)  # {'x': 2, 'y': 2}
```

Dictionaries are passed by reference — changes inside the function affect the original.

---

### 4. Generating random student scores and working with them

```python
import random

scoreList = []

def init():
    names = ["홍길동", "홍경래", "장길산", "서희", "윤관", "감강찬", "김연아", "안세영", "조승연"]
    for name in names:
        scoreList.append({
            "name": name,
            "kor": random.randint(40, 100),
            "eng": random.randint(40, 100),
            "mat": random.randint(40, 100)
        })
```

The `init()` function populates a global list with randomized student data.

---

## What I learned

- Functions make programs easier to manage and test.
- Lists and dictionaries can be passed to functions and updated inside.
- Simple types like integers are passed by value, but mutable types (like dicts) are passed by reference.

---

## What I want to do next

I want to organize more complex data and try writing reusable utility functions.  
Maybe even try building a CLI app with menus for input and output.

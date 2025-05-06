---
title: "Processing Input with Lists and Dictionaries in Python"
date: 2025-04-28
layout: single
tags:
  - python
  - list
  - dictionary
  - input
excerpt: "I practiced using lists and dictionaries to handle user input, calculate averages and wages, and compare different ways to store structured data."
---

## Why I studied this

I wanted to learn how to collect user input, store it in lists or dictionaries, and use it to calculate things like averages or wages.  
This is a basic skill needed for any program that works with data.

---

## What I did

### Gender and Salary: Calculating Averages

```python
employeeList = []

for i in range(10):
    employee = {}
    employee["gender"] = input("gender: ")
    employee["salary"] = int(input("salary: "))
    employeeList.append(employee)

male_total = 0
female_total = 0
male_sum = 0
female_sum = 0

for employee in employeeList:
    if employee["gender"] == "m":
        male_total += 1
        male_sum += employee["salary"]
    else:
        female_total += 1
        female_sum += employee["salary"]

if male_total > 0:
    print("Male average:", male_sum / male_total)
if female_total > 0:
    print("Female average:", female_sum / female_total)
```

I stored each employee's gender and salary using a dictionary inside a list, and then calculated the average for each gender.

---

### Student Grades: Total, Average, and Letter Grade

```python
studentList = []

for i in range(3):
    student = {}
    student["name"] = input("name?: ")
    student["kor"] = int(input("Korean?: "))
    student["eng"] = int(input("English?: "))
    student["mat"] = int(input("Maths?: "))
    studentList.append(student)

for student in studentList:
    student["total"] = student["kor"] + student["eng"] + student["mat"]
    student["avg"] = student["total"] // 3

for student in studentList:
    if student["avg"] > 90:
        student["grade"] = "수"
    elif student["avg"] > 80:
        student["grade"] = "우"
    else:
        student["grade"] = "미"
```

I used a dictionary for each student to store their scores and calculate total, average, and grade.

---

### Weekly Wages: List vs Dictionary

#### Using dictionaries

```python
personList = []

for i in range(2):
    worker = {}
    worker["name"] = input("Name: ")
    worker["work_time"] = int(input("Hours: "))
    worker["per_pay"] = int(input("Wage: "))
    personList.append(worker)

for worker in personList:
    worker["pay"] = worker["work_time"] * worker["per_pay"]
    print(worker)
```

Each worker’s data is stored in one dictionary inside a list. It’s clean and easy to use.

#### Using parallel lists

```python
name_list = []
time_list = []
wage_list = []

for i in range(5):
    name = input("name?: ")
    name_list.append(name)

for name in name_list:
    time = int(input("time?: "))
    time_list.append(time)

for name in name_list:
    wage = int(input("wage?: "))
    wage_list.append(wage)

for i in range(5):
    print(name_list[i], time_list[i], wage_list[i], time_list[i] * wage_list[i])
```

This works, but it’s harder to track and link the data. Using dictionaries makes the structure clearer.

---

## What I learned

- Lists can store multiple items, and when combined with dictionaries, they can store structured data.
- Dictionaries are better when data has labels like name, score, or gender.
- Input-processing is easier and clearer with dictionary-based structures.

---

## What I want to do next

I want to try reading data from a file, and practice combining list/dict with conditionals and loops to make small apps.

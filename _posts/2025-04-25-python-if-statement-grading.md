---
title: "Practicing Python If Statements with Grading Logic"
date: 2025-04-25
layout: single
tags:
  - python

excerpt: "I practiced how to use if, elif, and else in Python to build a simple grading program based on total score."
---

## Why I studied this

I'm learning how to use `if` statements in Python.  
This is useful when I want the program to behave differently depending on a condition.

---

## What I did

### Making a grade calculator with `if`, `elif`, `else`

```python
name = input("name?: ")

written_test = int(input("written test score: "))
word_test = int(input("word test score: "))
spreadsheet_test = int(input("spreadsheet test score: "))
presentation_test = int(input("presentation test score: "))

grade_total = written_test + word_test + spreadsheet_test + presentation_test

if grade_total >= 800:
    print("A")
elif grade_total >= 600:
    print("B")
elif grade_total >= 400:
    print("C")
else:
    print("D, retest needed")
```

The user types in scores for 4 subjects.  
Then the total score is calculated.  
The program uses `if`, `elif`, and `else` to check the total and print a grade.

---

## What I learned

I learned how to use `if`, `elif`, and `else` to make a decision based on different conditions.  
This kind of logic is useful in many real programs like grading, checking status, or handling menus.

---

## What I want to do next

I want to try using multiple conditions with `and`, `or`, and maybe use `input()` with other types like strings or booleans.

---
title: "How to Parse and Analyze CSV Data in Python"
date: 2025-05-09
layout: single
tags:
  - python
excerpt: "CSV files are everywhere. I learned how to extract, clean, and analyze data from them using simple Python code."
---

## Introduction

CSV (Comma-Separated Values) files are common in data science. Using simple string operations and lists/dictionaries, I processed `.csv` files like `iris.csv` and `mpg.csv` to extract useful insights.

---

## Reading and Parsing a CSV File

```python
file = open("iris.csv", "r")
lines = file.readlines()
file.close()

for line in lines[1:]:
    values = line.strip().split(",")
    print(values)
```

---

## Converting to Dictionary for Easier Use

```python
irisDict = {
    "sepal_length": values[0],
    "sepal_width": values[1],
    "petal_length": values[2],
    "petal_width": values[3],
    "species": values[4]
}
```

This structure makes it easier to calculate averages or filter data.

---

## What I learned

- `.readlines()` + `.strip().split(",")` is a basic but powerful way to parse CSVs.
- Dictionaries are useful for organizing row data by column names.
- Loops help calculate statistics like averages or category counts.

---

## What I want to do next

- Try using the built-in `csv` module for more robust handling.
- Apply filtering and grouping logic to larger datasets.

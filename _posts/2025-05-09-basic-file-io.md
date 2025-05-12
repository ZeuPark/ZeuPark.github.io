---
title: "How to Handle Basic File I/O in Python"
date: 2025-05-09
layout: single
tags:
  - python
excerpt: "A beginner-friendly summary of how to write and read text files using basic Python I/O syntax."
---

## Introduction

File input and output (I/O) is a fundamental part of Python programming. I explored how to write data into `.txt` files and read it back using Python’s built-in `open()` function. These small building blocks help automate data handling tasks later in larger projects.

---

## Writing to a File

```python
f = open("data.txt", "w")
for i in range(1, 6):
    print(f"i = {i}", file=f)
f.close()
```

Using `file=f` inside `print()` sends output into a file instead of the screen.

---

## Reading from a File

```python
f = open("data.txt", "r")
data = f.read()
print(data)
f.close()
```

Or read line-by-line:

```python
with open("data.txt", "r") as f:
    lines = f.readlines()
    for line in lines:
        print(line.strip())
```

---

## What I learned

- `open()` can write (`"w"`) or read (`"r"`) depending on the mode.
- `print(..., file=f)` is a convenient way to write to text files.
- Always remember to `close()` the file or use `with open(...)` to handle it safely.

---

## What I want to do next

- Practice with more types of text data (scores, logs, etc.)
- Understand how file I/O connects to real-world logging and data storage.

---
title: "Practicing Python For Loops and Accumulation"
date: 2025-04-25
layout: single
tags:
  - python

excerpt: "I practiced using Python for loops to print ranges, compute sums, and handle user input. Here’s what I learned."
---

## Why I studied this

I'm learning how to use `for` loops in Python.  
They are useful when I need to repeat something, count numbers, or process input data.

---

## What I did

### Printing numbers using for loop

```python
for i in [1,2,3,4,5,6,7,8,9,10]:
    print(i)

for i in range(1,11):
    print(i)

for i in range(2, 100, 2):
    print(i, end=" ")
print()
```

I learned how `range(start, end, step)` works and how to print numbers in a loop.

---

### Making a grid of numbers from 1 to 100

```python
for i in range(1, 101):
    print(i, end=" ")
    if i % 10 == 0:
        print()
```

This prints 1 to 100 in a 10 by 10 layout.

---

### Converting characters to Unicode

```python
print(ord("A"))  # 65
print(ord("a"))  # 97
print(ord("0"))  # 48
```

The `ord()` function returns the Unicode number of a character.

---

### Summing numbers from 1 to user input

```python
sum = 0
limit = int(input())
for i in range(1, limit + 1):
    sum = sum + i
    print(f"i={i} sum={sum}")
```

This code asks for a number and adds all numbers from 1 to that number.

---

### Adding 5 numbers from user input

```python
sum = 0
for i in range(1, 6):
    n = input("Enter a number: ")
    sum = sum + int(n)
print(sum)
```

I used `for` to repeat input 5 times and added the numbers.

---

### Separating even and odd sums from 10 inputs

```python
even_sum = 0
odd_sum = 0

for i in range(10):
    n = int(input("Enter a number: "))
    if n % 2 == 0:
        even_sum += n
    else:
        odd_sum += n

print("Even sum =", even_sum)
print("Odd sum =", odd_sum)
```

I used `if` to check even or odd and calculated each sum separately.

---

## What I learned

I learned how to use `for` loops with ranges and lists.  
I also practiced using `input()` inside a loop and how to keep a running total (accumulation).  
Now I feel more confident working with repeated actions and basic logic.

---

## What I want to do next

I want to try nested loops and maybe work on small problems like multiplication tables or mini games using loops.

---
title: "Creating a Number Baseball Game in Python"
date: 2025-05-02
layout: single
tags:
  - python
  - game
  - random
  - input
excerpt: "I built a number baseball game where the player guesses a 3-digit number. The game tells you how many strikes, balls, and outs you got each round."
---

## Why I studied this

I wanted to make a logic-based number game using user input, random values, and conditions.  
This project helped me combine multiple skills like lists, loops, and if-statements.

---

## What I did

### Step 1: Computer chooses 3 random numbers (1–9, no duplicates)

```python
import random

computer = []

def computerRandom():
    global computer
    computer = random.sample(range(1, 10), 3)

computerRandom()
print(computer)  # (for debugging)
```

---

### Step 2: User inputs 3 numbers

```python
player = []

def playerNumber():
    player.clear()
    for _ in range(3):
        while True:
            try:
                num = int(input("Enter a number (1–9): "))
                if 1 <= num <= 9 and num not in player:
                    player.append(num)
                    break
                else:
                    print("Invalid input.")
            except ValueError:
                print("Only numbers allowed.")

playerNumber()
print(player)
```

---

### Step 3: Check Strike, Ball, Out

```python
sboList = []

def strikeBallOut():
    strikeCount = 0
    ballCount = 0
    outCount = 0
    sbo = {}

    for i in range(3):
        if player[i] == computer[i]:
            strikeCount += 1
        elif player[i] in computer:
            ballCount += 1
        else:
            outCount += 1

    sbo["strike"] = strikeCount
    sbo["ball"] = ballCount
    sbo["out"] = outCount
    sboList.append(sbo)

strikeBallOut()
print(sboList)
```

---

## What I learned

- How to generate random numbers without duplicates
- How to get clean user input with error checking
- How to count matches in both value and position
- How to organize game state in a list of dictionaries

---

## What I want to do next

I want to run this game in a loop until the player wins (3 strikes) and track the number of tries it takes.

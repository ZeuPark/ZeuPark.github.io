---
title: "Building a Rock-Paper-Scissors Game in Python"
date: 2025-05-02
layout: single
tags:
  - python
  - game
  - random
  - function
excerpt: "I created a simple rock-paper-scissors game using Python. I used functions to decide the winner, stored game results in a list, and ran the game 10 times."
---

## Why I studied this

I wanted to build a simple game to apply what I learned about functions, conditionals, loops, and random numbers in Python.

---

## What I did

### Step 1: Decide the winner

```python
def isWinner(computer, person):
    if computer == person:
        return 3  # draw

    if (computer == 1 and person == 3) or        (computer == 2 and person == 1) or        (computer == 3 and person == 2):
        return 1  # computer wins
    return 2  # person wins
```

This function checks if it's a draw, computer win, or player win using conditions.

---

### Step 2: Run 10 rounds of the game

```python
import random

titles = ["", "Scissors", "Rock", "Paper"]
titles2 = ["", "Computer wins", "Player wins", "Draw"]
gameList = []

def gameStart():
    gameList.clear()
    for i in range(10):
        computer = random.randint(1, 3)
        person = random.randint(1, 3)
        winner = isWinner(computer, person)

        game = {
            "computer": computer,
            "person": person,
            "winner": winner
        }
        gameList.append(game)
        print("Computer:", titles[computer], "Player:", titles[person], titles2[winner])
```

This function plays the game 10 times using random values and prints the result of each round.

---

## What I learned

- How to use `random.randint()` to simulate random behavior
- How to use `if` to handle multiple game rules
- How to define helper functions like `isWinner()`
- How to store structured data (game results) in a list of dictionaries

---

## What I want to do next

I want to let the user actually input their choice and build a score counter to track wins, losses, and draws across multiple games.

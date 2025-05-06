---
title: "Building a Rock-Paper-Scissors Game in Python"
date: 2025-05-02
layout: single
tags:
  - python

excerpt: "I built a rock-paper-scissors game using Python. It runs for 10 rounds, stores each result, and calculates win rates. I also learned to simplify my logic after struggling with inefficient loops."
---

## Why I studied this

I wanted to build a simple game using Python to practice conditionals, loops, and random values.  
By creating a rock-paper-scissors game, I could practice using functions, store game data, and track results over time.

---

## What I did

### 1. Function to decide the winner

```python
def isWinner(computer, person):
    if computer == person:
        return 3  # draw

    if (computer == 1 and person == 3) or        (computer == 2 and person == 1) or        (computer == 3 and person == 2):
        return 1  # computer wins

    return 2  # player wins
```

This function takes two numbers (1 = Scissors, 2 = Rock, 3 = Paper) and returns the result:
- `1`: Computer wins
- `2`: Player wins
- `3`: Draw

---

### 2. Game engine: 10 rounds with random choices

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

        print(f"Computer: {titles[computer]} | Player: {titles[person]} --> {titles2[winner]}")
```

Each round randomly selects values for the computer and player.  
Results are stored in `gameList` for later review.

---

### 3. Summary of results

```python
player_win = sum(1 for game in gameList if game["winner"] == 2)
computer_win = sum(1 for game in gameList if game["winner"] == 1)
draw = sum(1 for game in gameList if game["winner"] == 3)

print(f"Player wins: {player_win}, Computer wins: {computer_win}, Draws: {draw}")
```

After 10 rounds, the program prints the final summary showing how many times each side won.

---

## What I struggled with

At first, I tried solving the comparison part in a very inefficient way.  
I used two `for` loops to compare the positions of items in lists, and inside the second loop I used `if` to match items.  
This ended up running 9 times every round (3x3), and it got messy quickly.

Eventually, I stopped overthinking it.  
Instead of nested loops, I directly compared list items at the same index.  
It was much simpler and faster.  
I realized that sometimes the cleanest way is the most direct one.

---

## What I learned

- How to structure a multi-round game using functions and lists
- How to use `random.randint()` for non-repetitive gameplay
- How to count wins using `sum()` and conditions
- Most importantly, I learned that **simple code is better than complicated logic**

---

## What I want to do next

I want to let users actually input their choice and see how many games they can win.  
Also, maybe keep score over multiple sessions!

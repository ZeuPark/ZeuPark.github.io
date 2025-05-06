---
title: "What I Learned from a Simple Number Game in Python"
date: 2025-05-04
layout: single
tags:
  - python

excerpt: "There a number of mistakes I made while I tried to build a rock paper scissor games. I will be going over key mistakes that I made"
---

## 
Recently I made a baseball number game as a small project. The objective of the game is simple, the computer choose 3 digit randomly and the player has to guess by trial and error. Player will choose any three number from 1~9 and it will match the computer's number. 

I have faced numeroud challenges while programming this game that I have never thought of before. I am making this post so that I don't forget about the mistakes that I have made.


---

## My Mistakes

### 1. Using Function Without a Return

```python
def strikeBallOut():
    sbo = {"strike": ..., "ball": ..., "out": ...}
    return sbo  # ← necessary

result = strikeBallOut()  # ← recieve return so that it is able to be used

```
Calling this function is useless unless you actually store the result
Otherwise, the data just disappears.



---

### 2. Reusing the Same Dictionary Causes Problems

If you keep appending the same dictionary to a list:

```python
sbo = {}
sboList.append(sbo)
```

Every entry in the list points to the same object.
You need to create a new dict each time to keep results independent.

---

### 3. Accessing a List Without Checking If It’s Empty

Trying to access sboList[-1] will crash if the list is empty.
I learned to always check whether the list has content before referencing its elements.

---
### 4. Inputs Must Be Reset or Isolated

At first, I appended player inputs to a global list.
Without resetting it between attempts, the list grew endlessly, and logic broke.
Lesson: use .clear() or keep the input logic inside the function.

---
### 5. Keep Game Logic Simple and Linear

I started with nested loops comparing positions, like:
```python
for i in range(3):
    for j in range(3):
        if ...
```

But I later realized: I only need to loop once with range(3) and compare values at the same index. Cleaner and faster.

---
### 6. Avoiding Duplicate Random Numbers

Originally I used:

```python
random.randint(1, 10)
```
But this could result in duplicates. I switched to:

```python
random.sample(range(1, 10), 3)

```


---
### 7. Understanding global in Functions

I learned that global allows a function to modify variables declared outside it.

But I also realized that relying too much on it can be messy — it's often better to use return values and assign them properly outside the function.

---

## What I learned

This project helped me strengthen these foundational skills:
- Understanding variable scope (local vs global)
- Handling references (mutable objects like list, dict)
- Structuring logic more cleanly (simplifying loops/conditions)
- Managing user input safely with try/except
- Using return values to pass data between functions
- Managing game state with well-structured data (dict + list)
- Debugging systematically with print() and input validation

---

## What I want to do next

This started as a small Python challenge, but I ended up learning far more than I expected.
Making mistakes was the best part — because each one taught me something that stuck.

Next, I want to keep building: maybe expand this into a GUI, or explore other small games.
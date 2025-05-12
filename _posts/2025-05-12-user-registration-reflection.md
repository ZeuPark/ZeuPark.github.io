---
title: "When Code Gets Messy: Lessons from Building a User Registration System"
date: 2025-05-12
layout: single
tags:
  - python
  
excerpt: "I tried building a user registration system in Python with ChatGPT's help. It was messy. But the lessons I learned were worth it."
---

## Introduction

Today, I tried building a user registration system using Python and object-oriented programming. It started with excitement — a clear vision in my head — and ended with confusion and messy code. The most surprising part? **ChatGPT helped me, but also messed me up.**

---

## What I Tried to Build

I wanted a basic member system:
- Users could sign up with ID, password, name, phone number, and email
- Data could be saved and loaded via `pickle`
- Admins could view and manage accounts

I used three main classes:
- `AccountManager`: for managing the list
- `NewAccount`: for registering new users
- `main()`: for menu and control flow

---

## What Went Wrong

At first, I asked ChatGPT for help with simple things — like how to use `self`, or how to structure a `__init__` function. That worked great.

But when I started asking for *whole feature implementations*, the answers got unpredictable. Sometimes it:
- Added inconsistent logic
- Suggested totally new structures unrelated to mine
- Returned code that broke existing methods

I realized something important: **ChatGPT is amazing at teaching me syntax, patterns, and debugging. But not great at continuing *my* design vision.**

---

## A Concrete Example

I asked ChatGPT how to build a full login and edit system. It gave me code that:
- Didn't match my class names
- Introduced new logic I didn’t plan for
- Overwrote variables or ignored existing ones

I ended up with duplicated logic, abandoned functions like `EditUser`, and inconsistent flow in `main()`.

---

## What I Learned

- **Start small**. Use ChatGPT to explain concepts or fix bugs, not to write whole programs.
- **Always have a design doc or sketch** before coding — otherwise the help you get won't match your intentions.
- **It's okay to get lost.** I still learned about class communication, data persistence, and menu flow.
- **Refactoring is inevitable.** My current code is messy, but now I understand what needs to be cleaned.

---

## What I want to do next

- Refactor the codebase: simplify functions and connect classes clearly.
- Make each class have a clear responsibility.
- Use ChatGPT only when I know exactly what I want help with — not for vague “make this for me” requests.
- Add login, edit, and delete features step-by-step.

---

This project didn’t go smoothly — and that’s exactly what made it valuable. I got frustrated, but I also got better.

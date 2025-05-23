---
title: "Discussion of Object-Oriented Programming (OOP) as a Beginner"
date: 2025-05-07
layout: single
tags:
  - python

excerpt: "This is a summary post about certain aspects that that needs to be discussed while learning 
Object-Oriented Programming (OOP)"
---

## Introdction
There were certain concepts that I had hard time understanding as it is first time learning Object-Oriented Programming(OOP). OOP is often referred as a living oragnism, mostly human, that has unique traits and actions that does a human. However, this made me even harder to understand what OOP is. 
It is hard for me to imagine that a programm could act like an organism. Moreover I didn`t understand what aspect of organism is depicted through OOP. Therefore, I make a summary of concepts to make the concpets clear. 

---

## Challenges that I Faced to Understand

### 1. What is `__init__`? 

-`__init__` is the constructor method. So it is basically something that is already made by python. It runs automatically when and object is created, and it's used to initialize attribute. It creates the unique traits of the class. Surprisingly,  `__init__` is a short term of initialize. 

---

### 2. What does `self` mean?

-self refers to the instance of the class itself. It`s how you access instance attributes and methods from within the class.
-it means that when an instance is created, `self` is just a variable that refrences back to the instance itself. 
---
### 3. What exactly is an object?

-an object is an instance of a class. Class is a structure of objecet. When the name is given to the object, it creates an instance of the class. 
---
### 4. Does a class always need `__init__`?

-in short answer, no. In long answer, no but it is not often to see without `__init__`. It is nor necessary to initalise when object is made. But in most of the time, it is used. If `__init__` is not going to be used, then using class might be a good idea in the first place. 


---
### 5. How do I run a function inside a class?

-first, you create an object (instance) of the class, and then call the method like how it would be called normally. 
-ex. `object_name.method.name().

---
### 6. What’s the difference between `self.variable` and just `variable`?

-`self.variable` is an instance variable (stored in the object), while `variable` by itself is just a local variable (disappears after the method ends).

---
### 7. How do I work with attributes and methods inside a class? Why does OOP even matter?

-In object oriented programming, we use self.method_name() inside a class to call another method that belongs to the same object. The self keyword refers to the current instance of the class, so it is how we access the object`s attributes and methods from within the class itself. 
-One thing I found interesting is that you can add or modify attributes after the object is created, like object_name.new_attribute = value, which shows how flexible Python is, but you still need to be careful because it can make the code messy. 
-Overall, the reason we use classes and objects is because they help organize code by grouping related data and functions together. This makes the code more reusable, easier to maintain, and better for building larger programs. I am starting to see that object oriented programming is not just about syntax, it is actually a way of thinking about how to represent real world things in code.

---

## What I learned

The aspects of OOP is harder to understand when it is actually written down. The concepts is easy beacuse it is meant to be user friendly in favours of the users using them. What becomes a challenge is that being in a position to make one instead of using it. It very inconvenient making a class because there are more things to consider than just bringing functions all in together so that it could be used by bits and bits. 
By going through this learning process, I am now able to understand the structure of class and its intentions. Before going throught the terms one by one, it was hard to understand the purpose of class, but now I understand how it could be used as an one whole thing that could be brought up easily. 

---

## What I want to do next

Learning about OOP makes me feel that I am stepping on the stepstone of learning AI and Machine Learning. OOP is such a popular term but it is my first time actually learning about it. 
I would like to know how programms actually use `class` because this is just learning about the coding grammar. I heard that OOP is used so that the program is run efficient, so I would like to see that with my eyes. 
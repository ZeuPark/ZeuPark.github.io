---
title: "Practicing Python String Basics"
date: 2025-04-24
layout: single
tags:
  - python

excerpt: "In this post, I practiced how to work with strings in Python, including indexing, slicing, escape characters, and string functions."
---

## Why I studied this

I'm learning how to work with strings in Python.  
Strings are everywhere in programming, and I wanted to get more comfortable using them, especially with indexing, slicing, and string functions.

---

## What I did

### Declaring strings

```python
s = "python string"
s2 = 'hello'

s3 = """ 
    This is
    a multiline
    string.
"""
```

I used both single and double quotes. For multi-line text, I used triple quotes.

---

### Indexing and slicing

```python
print(s[0])   # 'p'
print(s[1])   # 'y'
print(s[0:6]) # 'python'
print(s[0:6:2]) # 'pto'
```

Indexing starts at 0.  
Slicing lets me grab parts of a string using [start:end:step].

---

### Escape characters and raw strings

```python
s = "I like star.\nred \nbluestar"
print(s)

s = "apple\t pear\t cherry\t banana"
print(s)

s = r"c:\test\temp"
print(s)
```

\n makes a new line.  
\t adds a tab.  
r"..." makes the string treat backslashes as normal characters.

---

### Quotes inside strings

```python
s = "I like \'Python\'"
s2 = 'I like \"Python\"'
```

I used \' and \" to put quotes inside strings.

---

### Printing with sep and end

```python
print("red", "green", "blue", sep=", ", end="!\n")
```

sep sets what goes between values.  
end sets what goes at the end instead of a newline.

---

### String functions: count and find

```python
s = "hobby"
print(s.count("b"))  # 2
print(s.find("b"))   # 2
```

count() tells how many times a letter appears.  
find() gives the first index of the letter (or -1 if it's not found).

---

### Finding multiple positions

```python
s = "I like star. red star. blue star. I like star."

pos1 = s.find("star")
pos2 = s.find("star", pos1 + 1)
pos3 = s.find("star", pos2 + 1)
pos4 = s.find("star", pos3 + 1)
```

By using find() with a starting index, I could search for the next match step by step.

---

## What I learned

I practiced a lot of string features.  
I now understand how to slice strings, escape characters, and use functions like find() and count().  
I also learned how to use print() in more flexible ways.

---

## What I want to do next

I want to practice replacing strings, using split() and join(), and maybe try formatting strings too.

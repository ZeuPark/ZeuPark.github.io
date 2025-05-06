---
title: "Python Lists and Strings Practice"
date: 2025-04-24
layout: single
tags:
  - python

excerpt: "I practiced how to use Python lists and strings. Here's what I learned through some simple examples."
---

## Why I studied this

I'm learning Python and I wanted to get better at using lists and strings.  
These are basic but really important in many programs, so I tried different ways to use them.

---

## What I did

### Making and checking a list

```python
words = ["red", "green", "blue"]
print(words[0])
print(words[1])
print(words[2])
```

This is how I made a list and printed each item by using index numbers.

---

### Adding new items and checking the list

```python
words.append("black")
words.append("cyan")
print(words)
print(len(words))
print(words.count("red"))
print(words.index("red"))
```

I used `append()` to add new items.  
`len()` shows the number of items.  
`count()` tells how many times something appears.  
`index()` gives the position of the item.

---

### Checking if something is in the list

```python
if "yellow" in words:
    print(words.index("yellow"))
else:
    print("yellow not found")
```

This checks if "yellow" is in the list.  
If it is, it prints the index. If not, it says it's not there.

---

### Reversing the list

```python
print(words[::-1])
```

This line shows how to print the list in reverse order using slicing.

---

### Lists can change, strings can't

```python
words[0] = "white"

s = "white"
s = s.replace("w", "W")
s2 = "W" + s[1:]
```

You can change lists easily, but strings are different.  
You have to make a new string to "change" something.

---

### Turning lists into strings and back

```python
words.extend(["brown", "violet", "purple", "magenta"])
s = ", ".join(words)
words2 = s.split(", ")
```

This turns a list into a string and then back into a list using `join()` and `split()`.

---

### Slicing a number list

```python
numbers = [1,2,3,4,5,6,7,8,9,10]
print(numbers[0::2])  # Even positions
print(numbers[1::2])  # Odd positions
```

This prints every second number starting from index 0 or 1.

---

### Making empty lists and adding stuff

```python
names = []
names.append("John")
names.append("Alex")
names.append("Sarah")

names2 = list()
names2.append("Rose")
names2.append("Lily")
names2.append("Daisy")
```

You can make empty lists using `[]` or `list()` and then add items with `append()`.

---

## What I learned

I practiced how to use lists and strings in different ways.  
Now I understand slicing, appending, joining, and changing things better.  
I also learned that strings are not like lists because they can’t be changed directly.

---

## What I want to do next

Next time I want to try using sets and dictionaries.  
I also want to try making small projects that use lists and strings together.

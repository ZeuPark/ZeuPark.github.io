---
title: "2025-04-29 - assignment-description"
date: 2025-04-29
categories:
  - Python
tags:
  - script
  - example
---

No description provided.

<div style="white-space: pre-wrap; word-break: break-word;">

```python



def isEven(n):
    if n%2 == 0:
        return True
    return False

def isLeap(year):
    if (year%4==0 and year%100!=0) or year%400==0:
        return True
    return False

for i in range (1,11):
    print(f"{i} = {isEven(i)}")


print("윤년확인 ")
for i in range(2000, 2026):
    print(f"{i} = {isLeap(isLeap)}")
```

</div>

[Download this file](/assets/files/과제 설명.py)

---
title: "2025-04-28 - assignment-parkjaewoo"
date: 2025-04-28
layout: single
categories:
  - Python
tags:
  - script
  - example
---

과제 1

```python

"""
과제 1. 정수를 받아가서 짝수이면 True, 짝수가 아니면 False를 반환하는 함수 

과제 2. 윤년 4년마다 윤년이 온다 
       100년에 한번 윤년이 아니다 
       400년에 한번 윤년이다
       함수로 만들어서 년도를 주면 윤년일 경우 True 윤년이 아니면 False를 반환하면 된다 

"""

#과제 1
def integer(number):
    if number%2 == 0:
        print(True)
    else:
        print(False)

user_input = int(input("정수를 입력하세요: "))
integer(user_input)

#과제 2
def leap_year(year):
    if (year % 4 == 0 and year % 100 != 0) or year % 400 == 0:
        print("True")
    else:
        print("False")

user_input = int(input("년도를 입력하세요: "))
leap_year(user_input)


```

[Download this file](/assets/files/0428_과제_박제우.py)
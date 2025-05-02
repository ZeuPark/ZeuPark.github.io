---
title: "2025-04-28 - assignment-description-from-25th"
date: 2025-04-28
categories:
  - Python
tags:
  - script
  - example
---

1. 입력부터

```python



even_sum = 0 
odd_sum = 0 


numberList = [] #리스트 객체를 만든다 

#1. 입력부터
for i in range(0,4):
    num = int(input("integer? :"))
    numberList.append(num)

#2. 계산하기 
for num in numberList:
    if num % 2 == 0:
        even_sum += num
    else:
        odd_sum += num

#3 출력하기 
print(even_sum)
print(odd_sum)



```

[Download this file](/assets/files/4월 25일 금 과제 설명.py)

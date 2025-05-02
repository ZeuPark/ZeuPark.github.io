---
title: "2025-04-28 - nested-for-loop"
date: 2025-04-28
categories:
  - Python
tags:
  - script
  - example
---

for문 안에서 또 for문이 작동하는 경우이다 ---> 좋진 않음

<div style="white-space: pre-wrap; word-break: break-word;">

```python


#for문 안에서 또 for문이 작동하는 경우이다 ---> 좋진 않음
#외부의 루프가 m번 돌고, 내부 루프가 n번 돌면  (m * n)번 수행한다 
#가급적이면 2중까지만 하고 3중은 자제 하는 것이 좋다 
#2중 for문까지만 동작하게만 한다 


# for i in range(1, 6):
#     for j in range(1,6):
#         print(f"i={i} j={j}")


#문제 1 이중 for문 사용해서 1~100까지 출력 한줄에 열개씩 출력하기

# for i in range (0, 10):
#     for j in range(0, 10):
#         print(i*10 + j, end="\t")
#     print()


#문제 2. 이중 for문 사용해서 
# 1 = 1
# 1 + 2 = 3 
# 1 + 2 + 3 = 6
# 1 + 2 + 3 + 4 = 10
# 1 + 2 + 3 + 4 ... + 10 = 



# sum = 0
# for i in range(1,11):
#     for j in range(1,i+1):
#         if j<i:
#             print(j, end="+")
#         else:
#             print(j, end="=")
#         sum += j
#     print(sum)


# for i in range (0,10):
#     for j in range(0,i):
#         print("*", end="")
#     print()

    

# for i in range (0,10):
#     print("*"*i)


#     *         별 1 공백 3  라인1 -        별의 개수 : 2 * 라인수 - 1     공백 : 공백 = 4 - 라인 
#    ***        별 2 공백 2
#   *****       별 5 공백 1
#  *******      별 7 공백 0 
#   *****       별 5 공백 1  라인1 -        별의 개수 : (3 - 별) * 2 + 1     공백 : 공백 = 4 - 라인 
#    ***        별 3 공백 2
#     *         별 1 공백 3


lines = 7

for i in range(1, lines + 1):
    print(" "*(lines-i), end="")
    print("*"*((2*i)-1))

for i in range(1, lines + 1):
    for j in range(0, (lines-i)):
        print(" ", end="")
    for j in range(0, (2*i-1)):
        print("*", end="")
    print()

lines = lines - 1
for i in range (0 , lines + 1):
    for j in range(0 , i):
        print(" ", end ="")
    for j in range(0, (lines-i)*2+1):
        print("*", end="")
    print()

```

</div>

[Download this file](/assets/files/다중for문.py)

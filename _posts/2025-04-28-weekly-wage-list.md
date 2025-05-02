---
title: "2025-04-28 - weekly-wage-list"
date: 2025-04-28
categories:
  - Python
tags:
  - script
  - example
---

주급계산 이름, 근무시간, 시간당급여액 - 5명에 대해서

```python
#주급계산 이름, 근무시간, 시간당급여액 - 5명에 대해서
#홍길도 40 10000
#임꺽정 30 20000
#장길산 20 20000
#홍경래 10 15000
#이징옥 20 30000

"""
name_list = []
time_list = []
wage_list = []


for i in range (0,5):
    name = input("name?: ")
    name_list.append(name)

for name in name_list:
    time = int(input("time?: "))
    time_list.append(time)

for name in name_list:
    wage = int(input("wage?: "))
    wage_list.append(wage)

for name in name_list:
    print(name)
for time in time_list:
    print(time)
for wage in wage_list:
    print(wage)


for lst in [name_list, time_list, wage_list]:
    print(' '.join(lst))

"""


name_list = []
work_time_list = []
per_pay_list = []
pay_list = []


for i in range(0,5):
    name = input("name ")
    work_time = int(input("work time "))
    per_pay = int(input("per pay "))

    name_list.append(name)
    work_time_list.append(work_time)
    per_pay_list.append(per_pay)

for i in range (0,5):
    total = work_time_list[i] * per_pay_list[i]
    pay_list.append( total )

for i in range (0,5):
    print(f"{name_list[i]} {work_time_list[i]} {per_pay_list[i]} {pay_list[i]}")
```

[Download this file](/assets/files/주급_list.py)

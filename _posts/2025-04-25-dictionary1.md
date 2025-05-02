---
title: "2025-04-25 - dictionary1"
date: 2025-04-25
categories:
  - Python
tags:
  - script
  - example
---

키 값은 문자열을 주로 사용한다. 만일에 같은 키값을 두번쓰면 두번째꺼로 업데이트된다

```python
colors = {"red":"빨간색", "blue":"파란색", "green":"초록색"}
#키 값은 문자열을 주로 사용한다. 만일에 같은 키값을 두번쓰면 두번째꺼로 업데이트된다 

#인덱싱, 슬라이싱 불가능 
print(colors["red"])
print(colors["blue"])
print(colors["green"])

print(colors.keys()) #키 값들의 목록을 보여준다 

#추가
colors["black"] = "검은색" 
print(colors)

#업데이트
colors['red'] = "빨강"
print(colors)

#없는 키값의 경우 파이썬이 어떻게 동작하는지 
#print(colors['pink']) --> 에러가 난다 
if "pink" in colors.keys():
    print(colors['pink'])
else:
    print("pink does not exist")

print(colors.items())
print(colors.values())

#특정키 삭제 - pop(키값)
colors.pop("red") #red키 삭제 
print(colors)

colors.clear() #전체 삭제 
print(colors)



```

[Download this file](/assets/files/딕셔너리1.py)

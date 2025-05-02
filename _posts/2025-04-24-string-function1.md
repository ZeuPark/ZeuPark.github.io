---
title: "2025-04-24 - string-function1"
date: 2025-04-24
categories:
  - Python
tags:
  - script
  - example
---

문자의 위치값

<div style="white-space: pre-wrap; word-break: break-word;">

```python
s = "hobby"
print(s.count("b")) #b가 몇개 있는가 
print(s.count("t")) #없으면 0으로 나온다 

#문자의 위치값 
print(s.find("b")) #제일 첫번째 b를 찾는다, 첫번째 문자 위치값을 반환한다 
print(s.find("f")) #없으면 -1
s = "I like star. red star. blue star. I like star." 
print(s.count("star"))
print(s.find("star"))

pos1 = s.find("star") #0번째 방부터 찾는다 
print(pos1)
pos2 = s.find("star", pos1+1) #첫번째 star 찾은 그 다음부터 찾아라
print(pos2)
pos3 = s.find("star", pos2+1) #두번째 star 찾은 그 다음부터 찾아라
print(pos3)
pos4 = s.find("star", pos3+1) #세번째 star 찾은 그 다음부터 찾아라
print(pos4)

pos1 = s.index("like")
print(pos1)

# pos1 = s.index("love") #단어가 없으면 예외가 발생한다. 즉, 오류라는 뜻 
# print(pos1)

#list를 다 더해준다 
s = ",".join("abcd")
print(s)

s = ",".join(["cherry", "banana", "pear", "grape"])
print(s)

#반대역할 문장을 -> list 타입
words = s.split(",") #하나의 문장을 쪼갠다. => list타입으로 전환한다
print(words)

#대소문자 
print("hi".upper())
print( "HI".lower())

#공백지우기
s = "           hi           "
print("*"+s+"*")
print("*"+s.lstrip()+"*") #왼쪽 공백 지우기 
print("*"+s.rstrip()+"*") #오른쪽 공백 지우기
print("*"+s.strip()+"*")  #왼쪽 오른쪽 공백 지우기

print("python".isalpha())
print("python1".isalpha())

print("python".isdigit())
print("123".isdigit())

#착각하기 쉬운 것들 
s = "hello" #upper 바뀐값을 반환 원래 값은 바뀌지 않는다 
print(s.upper(),s)
```

</div>

[Download this file](/assets/files/문자열함수1.py)

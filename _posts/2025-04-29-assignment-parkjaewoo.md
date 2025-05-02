---
title: "2025-04-29 - assignment-parkjaewoo"
date: 2025-04-29
layout: single
categories:
  - Python
tags:
  - script
  - example
---

문제 1 filter를 사용해서 글자수가 5글자 이상인 단어만 출력하기

```python



words = ["assembly", "java", "rain", "notebook", "north", "south", 
         "hospital", "programming", "house", "hour"]

#문제 1 filter를 사용해서 글자수가 5글자 이상인 단어만 출력하기 
for word in filter (lambda x: len(x) >= 5, words):
    print(word)


#문제2. map함수를 사용해서 글자를 대문자로 바꾸어서 출력하기  (컴프리핸션X)
for i in map(lambda x: x.upper(), words):
    print(i)


#문제3. sorted 함수를 사용하여 단어들의 길이순으로 오름차순 정렬하여 출력하기
list1 = sorted(words, key= lambda x: len(x))
print(list)


#문제4. sorted 함수를 사용하여 알파벳 순으로 내림차순으로 정렬하여 출력하기 
list2 = sorted(words, reverse=True)
print(list2)


#문제5. 단어중에 o가 포함되는 단어가 모두 몇개인지 카운트하기 (힌트,filter를 사용)  

list3 = (list(filter(lambda x : "o" in x, words)))
print(len(list3))
```

[Download this file](/assets/files/0429_과제_박제우.py)
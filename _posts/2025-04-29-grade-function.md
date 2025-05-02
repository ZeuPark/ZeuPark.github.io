---
title: "2025-04-29 - grade-function"
date: 2025-04-29
layout: single
categories:
  - Python
tags:
  - script
  - example
---

이 메모리로 가져와서 결합해라

```python
import random #외부 모듈(파이썬의 경우에는 파일)을 이 메모리로 가져와서 결합해라 
              #이 메모리로 가져와서 결합해라
              #

scoreList = [] #모든 함수가 공유해야할 메모리이다. 
#함수 내에 선언된 변수는 함수에서만 존재한다. 
#함수 외부에 선언된 변수는 함수들이 같이 사용할 수 있다. 전역변수

#맨 처음 기본 데이터 넣어놓고 시작
def init():
    names = ["홍길동", "홍경래", "장길산", "서희", "윤관", "감강찬", "김연아", "안세영", "조승연"]
    for i in range(0, len(names)):
        scoreList.append({"name": names[i], 
                          "kor":random.randint(40,100), 
                          "eng":random.randint(40,100),
                          "mat":random.randint(40,100)})
        for s in scoreList:
            s["total"] = getTotal(s)
            s["avg"] = getAvg(s)
            s["grade"] = getGrade(s)


#내가 한거 근데 잘 모르겠음
# def nameInput():
#     name = input("이름: ")
#     return name


# def findName(n):
#     #list에 있는 name 찾기 
#     for n in filter(lambda x : x["name"] == nameInput , scoreList):
#         return n
    


def output(scoreList):
    for s in scoreList: #scoreList로 부터 하나씩 s라는 변수에 전달된다.
        print(f"{s['name']}", end="\t")
        print(f"{s['kor']}", end="\t")
        print(f"{s['eng']}", end="\t")
        print(f"{s['mat']}", end="\t")
        print(f"{s['total']}", end="\t")
        print(f"{s['avg']:2f}", end="\t")
        print(f"{s['grade']}")

        
def append():
    #각 과목별로 0~100점만 입력이 되도록, 숫자만 입력되게 하고 싶다.
    s = {}
    s["name"] = input("이름 : ")
    s["kor"] = getScore("국어", 100)
    s["eng"] = getScore("영어", 100)
    s["mat"] = getScore("수학", 100)
    s["total"] = getTotal(s)
    s["avg"] = getAvg(s)
    s["grade"] = getGrade(s)

    scoreList.append(s)
    
    
    #숫자가 들어와야 하고. 0~100 사이어야 한다. 

def getTotal(s):
    return s["kor"] + s["eng"] + s["mat"]

def getAvg(s):
    return s["total"]/3

def getGrade(s):
    if s['avg'] > 90:
        return  "수"
    elif s['avg'] > 80:
        return  "우"
    elif s['avg'] > 70:
        return  "미"
    elif s['avg'] > 60:
        return "양"
    else:
        return  "가"

    

#숫자만 입력되게 : input으로 받는 모든 데이터는 String이다. 
#ord함수를 통해서 숫자인지 아닌지 판단할 수 있다.
#ord('0'), ord('9')    문자열을 받아서 한글자씩 '0' 과 '9' 사이에 있으면 글자중에 하나라도 저 사이에 존재하지 않으면 숫자 아니다. 
#함수는 기능 하나만, 하나의 기능에 집중하라
#함수도 입출력이다. 매개변수가 입력이고 반환값이 출력이다. 
#입력과 출력에 대한 정의가 먼저 진행되어야 한다.
#에러처리는 먼저 처리하자
#예시)
"""
def myfunc():
    if error1 :
        return -1
    if error2:
        return -2

    ....
"""

def isDigit(s):
    for i in range(0, len(s)):
        if ord(s[i]) < ord('0') or ord(s[i]) > ord ('9'):
            return False
        
    return True #끝까지 다 완수했어 다 숫자이다 

def getNumber(subject):
    s = input(f"{subject} :")
    while(isDigit(s)==False):
        print("숫자만 입력하세요 ")
        s = input("숫자 ")
    return int(s)


def getScore(subject="국어 ", limit = 100):
    n = getNumber(subject)
    while(n<0 or n>limit):
        print(f"0~{limit} 사이의 값을 입력하세요 ")
        n = getNumber(subject)
    return n


#n = getNumber()

def search():
    key = input("찾을 이름은: ")
    #filter에서 두번째 파라미터 iterable(반복적인) 데이터 - list류
    #filter 안에서는 scoreList로부터 한 개씩 객체를 갖고 온다 
    #dict 타입
    resultList = list(filter(lambda x:x["name"] == key, scoreList))
    #반환갑이 list타입이고 list 안에 dict 타입이 있다. 
    #resultList, scoreList가 동이한 구조 - 함수 하나로 둘다 전역변수로 scoreList가 이미 있다. 
    #함수안에서 매개변수로 전역변수와 이름이 똑같으면 외부 전역변수를 가려버린다 
    #내 눈 앞에 보이는게 우선이다 
    output(resultList)

def modify():
    key = input("수정할 이름은:" )
    resultList = list(filter(lambda x:x["name"] == key, scoreList))
    if len(resultList) == 0:
        print(f'{key}를 찾을 수 없습니다')
        return      #끝내라, 함수를 끝내라 
    
    #두명이상 있을 때의 처리를 해야 한다 
    st = resultList[0]
    st["name"]=input("바꿀이름: ")
    st["kor"] = getScore("국어 ")
    st["eng"] = getScore("영어 ")
    st["mat"] = getScore("tngkr ")
    st["total"] = getTotal(st)
    st["avg"] = getAvg(st)
    st["grade"] = getGrade(st)
    print("수정되었습니다 ")


    
# def change(): 
#     scoreList.remove(search())
#     input()

# def remove():
#     scoreList.remove(search())

    

def menuDisplay():
    print("1. 추가 ")
    print("2. 출력 ")
    print("3. 검색 ")
    print("4. 수정 ")
    print("5. 삭제 ")
    print("0. 종료 ")


def start():
    init() #데이터 초기화 
    menuDisplay()
    while True:
        sel = input("선택 : ")
        if sel == "1":
            append()
        elif sel == "2":
            output(scoreList)
        elif sel == "3":
            search()
        elif sel == "4":
            modify()  #update
        elif sel == "5":
            search() #구현 하지 않음 
        elif sel == "0":
            print("프로그램을 종료합니다")
            return
        else: 
            print("잘못 입력하셨습니다")

start()
        
#filter는 검색용 함수이다. map은 연산용 함수이다. sort는 정렬용 함수이다. 그냥 그런거니까 받아드려라 
```

[Download this file](/assets/files/성적_함수.py)
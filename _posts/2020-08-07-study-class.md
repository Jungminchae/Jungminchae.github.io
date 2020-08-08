---
title: 'Class 공부 #01'
date: 2020-08-07
tags: [AIFFEL, Fundamental]
comments: true
---

# Python Class 공 부 해 보 기 

팀원들과 Class에 대해 함께 공부하면서 Python class 정리를 요청 받아서 한 번 정리해보려고 합니다.

Python을 처음 배울 때를 생각해보면 'Python 이 배우기 쉽고 범용적이다' 라는 말을 들었던 것 같습니다. 하지만, **Class** 를 처음 접할 때 '**쉽긴 뭐가 쉽냐**' 라는 생각을 했었습니다. 그래서 최대한 쉽게 쉽게 접근하고 이해하려고 시도해 보았습니다. 

객체 지향 프로그램, 인스턴스, 메소드 등 , 저같은 문과송이들한테는 일단 용어가 너무 어렵죠... 공부하면서 용어부터 쉽게 정리했습니다.

-------------------------------------------------------------------
## **객체(Object)**
객체는 그냥 단순하게 세상에 존재하는 어떤 기능들을 가진, 어떤 물체라고 생각했습니다. 그리고 그것이 **Class**가 됩니다. 예를들면 우리가 매일 끼고 사는 '**스마트폰**'이라는 물체를 객체라고 명명할 수 있습니다.  
Python 코드로 나타내보면
```python
class SmartPhone:
    pass
```

<font color='skyblue' size=14> SmartPhone </font> 객체를 만들었습니다. 저는 그냥 이 SmartPhone 객체를 하나의 물체라고 생각하고 접근합니다.

------------------------------------------------------------------
## **속성(Attribute)**
속성은 앞서 만든 class가 가지는 특징, 그것을 나타내는 특징이라고 생각하고 접근합니다. SmartPhone의 특징이 될 수 있는 것을 생각해보면 ,,, 제조사, 모델명 색, 사이즈, 방수 여부 등이 있을 것 같네요. 이 밖에 다른 특징들이 더 떠오르면 중간중간 추가하겠습니다.
Python 코드로 나타내보면
```python
class SmartPhone:
    company = 'Samsung',
    model = 'GalaxyS20',
    color = 'black',
    waterpoof = True,
```
class에 속성값을 추가해 주었습니다. 하지만 이렇게 속성값을 정의하는 것은 좋은 방법은 아닙니다. 왜냐하면 스마트폰은 'Samsung'에서만 만드는 것은 아닙니다. 그래서 초기화를 해주어야 합니다.   
**__init** **__** 생성자를 만들어야하는데 **생성자**... 이말도 어렵네요. 여러가지 생성자들이 있지만 여기서는 이것만 다루겠습니다.
생성자는 class를 불러왔을때 자동으로 만들어지는 메소드라고 생각하면 편합니다.
일단 코드부터 보겠습니다
```python
# 1
class SmartPhone:
    def __init__(self)
        self.company = 'Samsung',
        self.model = 'GalaxyS20',
        self.color = 'black',
        self.waterpoof = True
```
```python
# 2
class SmartPhone:
    def __init__(self, company, model, color, waterproof)
        self.company = company,
        self.model = model,
        self.color = color,
        self.waterpoof = True        
```
여기에 나타타는 <font size=14> self</font>라는 인자는 class 자기 자신의 이름표라고 생각하면 편하더라구요.  
'self가 있으면 'SmartPhone이 아니면 쓸 수 없다. 접근할 수 없다.' 라고 생각하면 이해가 좀 쉽습니다.

이야기를 계속하면 #1 이나 #2 둘 다 쓸 수 있습니다. 아래의 방법으로 접근하면 속성값을 처음에 정해주어야 합니다.  
이렇게요
```python
Iphone = SmartPhone(company='Apple', model='Iphone8',color='black', waterproof=True)
```

------------------------------------------------------------------

#### 오늘은 속성까지만 하겠습니다. 쓰다보니 길어지네용... 다음 포스트를 메소드부터 하겠습니다.
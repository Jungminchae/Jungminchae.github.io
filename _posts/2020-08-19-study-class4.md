---
title: 'Class 공부 #04'
date: 2020-08-19
tags: [AIFFEL, Fundamental]
comments: true
---
# Python Class 공 부 해 보 기 - 4

## **다중 상속**
바로 전 포스트에서 상속을 공부했었습니다. Python에서는 하나의 클래스만 상속받는 것이 아닌 다중으로 상속 받는 것도 가능합니다. 이전에 사용했던 **SmartPhone** 클래스를 그대로 계속 이용하여 다중 상속을 공부해 보려고 합니다.
이전에 사용했던 **Computer** 클래스에 변화를 살짝 주겠습니다.
```python
class Computer:
    def __init__(self):
        self.internet = 'off'
    def connect_internet(self):
        if self.internet =='off':
            self.internet ='on'
    def save_files_in_drive(self):
        print('컴퓨터에 파일을 저장했습니다')
```
**USB** 클래스를 만들어 컴퓨터와 같이 상속 해보겠습니다.
```python
class USB:
    def __init__(self):
        pass
    def save_files_in_drive(self):
        print('USB에 파일을 저장했습니다.')
    def disconnect(self):
        print('USB를 제거했습니다.')
```
```python
# 1
class SmartPhone(Computer, USB):
    def __init__(self, company, model, color, waterproof):
        self.company = company,
        self.model = model,
        self.color = color,
        self.waterpoof = waterproof 
        self.power = 'off'
        self.app_list = []
        ...
```
방법은 간단하게 () 안에 두 클래스를 다 넣어 주면 됩니다. 그런데 **Computer** 와 **USB**에 같은 이름의 **save_files_in_drive** 기능(메소드)이 있습니다. 그런데 이름만 같고 출력은 다릅니다. 그렇다면 상속받은 **SmartPhone** 어떤 기능이 사용되는가 하면 처음 상속받은 클래스의 기능이 사용됩니다.   

![스크린샷, 2020-08-19 16-03-26](https://user-images.githubusercontent.com/60789129/90603040-99d15b80-e235-11ea-86f7-1a7c426f524e.png)

따라서 다중 상속을 받을 때 상속을 받는 순서도 중요하게 작용할 수 있습니다. 단순히 여러 개를 상속받는다 뿐이지 일반 상속과 크게 다른 점은 없습니다.

## **Method Overriding**
메소드 오버라이딩은 상속받은 메소드를 다시 내가 원하는데로 변경하여 다시 정의하는 것을 말합니다. 부모 클래스와 자식 클래스가 이름은 같지만 다른 기능을 가지게 됩니다.
```python
class SmartPhone(Computer, USB):
    def __init__(self, company, model, color, waterproof):
        ...
    
    def save_files_in_drive(self):
        print('스마트폰에 파일을 저장했습니다')

    def disconnect(self):
        print('스마트폰에서 USB를 제거했습니다.')

```
**save_files_in_drive** , **disconnect** 기능은 부모클래스에서 상속받아 온 것이지만 **Smartphone**에 맞게 재정의 하였습니다.  
![스크린샷, 2020-08-19 16-22-28](https://user-images.githubusercontent.com/60789129/90604728-401e6080-e238-11ea-97ae-85b288302d84.png)

위의 사진처럼 이름은 같지만 기능이 다르게 구현되었습니다. 이정도면 기본적인 클래스 사용에 대해 공부를 마쳐도 될 것같습니다. 좀 더 어려운 사용은 추후에 다시 글을 써보도록 하겠습니다. 
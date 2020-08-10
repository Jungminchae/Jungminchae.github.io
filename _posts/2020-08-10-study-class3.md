---
title: 'Class 공부 #03'
date: 2020-08-07
tags: [AIFFEL, Fundamental]
comments: true
---
# Python Class 공 부 해 보 기 - 3

## **상속**
상속은 말 그대로 물려받는 것입니다. **class**에서 상속은 쉽게 말하면 다른 class의 기능을 물려받아 내 클래스에서 사용하는 것이라고 생각하면 되겠습니다. 앞에서 언급했던 것처럼 SmartPhone 클래스에는 **internet** 이라는 속성도 없고 **connect_internet** 라는 기능도 없습니다.  
여기 Computer class를 한 번 보겠습니다.
```python
class Computer:
    def __init__(self):
        self.internet = 'off'
    def connect_internet(self):
        if self.internet =='off':
            self.internet ='on'
```
**Computer** class에 internet 속성과 connect_internet 기능이 존재합니다. 이것을 물려받아(상속) Computer의 기능을 사용해보겠습니다. 
아래와 같은 방식으로 사용하면 됩니다.
```python
class SmartPhone(Computer):
    def __init__(self, company, model, color, waterproof):
        self.company = company,
        self.model = model,
        self.color = color,
        self.waterpoof = waterproof 
        self.power = 'off'
        self.app_list = []
    ...
```
**SmartPhone** class에 **()**를 열고 그 안에 상속을 받고자 하는 class를 넣으면 됩니다. 그런데 여기까지만하면 error가 발생합니다.
```python
iphone = SmartPhone('Apple', 'Iphone8','black',True)
# error 발생
iphone.connect_internet()
```
![Screenshot from 2020-08-10 15-21-55](https://user-images.githubusercontent.com/60789129/89756402-5718d080-db1d-11ea-8ecd-d28c865cb13c.png)

분명 Computer class를 물려받았는데 internet이 없다고 나오네요. 여기서 필요한 것이 <font size=15 color=skyblue> super </font> 입니다.
클래스 상속에서는 메소드만 상속이 됩니다. 그래서 상속 클래스의 속성값까지 초기화 하기 위해서 super 를 사용해야 합니다.
```python
# 전체 완성 코드를 담아보겠습니다.
class Computer:
    def __init__(self):
        self.internet = 'off'
    def connect_internet(self):
        if self.internet =='off':
            self.internet ='on'

class SmartPhone(Computer):
    def __init__(self, company, model, color, waterproof):
        self.company = company,
        self.model = model,
        self.color = color,
        self.waterpoof = waterproof 
        self.power = 'off'
        self.app_list = []
        super().__init__()
    def power_on_or_off(self):
        # 실행 시, 전원이 꺼져있으면 켜고, 켜져있으면 끄는 기능 
        if self.power =='off':
            self.power = 'on'
            print('전원이 켜졌습니다')
        elif self.power =='on':
            self.power = 'off'
            print('전원이 꺼졌습니다.')
            
    def app_download(self, app_name):
        if self.internet =='on' and self.powewr =='on':
        # App을 다운로드하고 app_list에 저장
            print('{} 을 다운로드 합니다.')
            self.app_list.append(app_name)
            # App 목록을 반환해보겠습니다.
            return self.app_list
        elif self.power =='off':
        # 전원이 꺼져있는데 실행을 시도하면 RuntimeError를 내도록해보겠습니다.
            raise RuntimeError('전원을 확인하세요')
        # 인터넷 연결이 없는데 시도하면 연결 후 다운로드 시도
        elif self.internet =='off':
            while True:
                ask = input('인터넷 연결이 없습니다. 연결하시겠습니까? yes or no')
                if ask =='yes':
                    self.connect_internet()
                    self.app_list.append(app_name)
                    return app_name
                    break
                elif ask =='no':
                    print('다운로드 실패')
                    break
```
한 번 실행해 보겠습니다. 검정색 Iphone8을 전원을 켜고 kakaotalk을 다운받아 보겠습니다.

![Screenshot from 2020-08-10 15-38-31](https://user-images.githubusercontent.com/60789129/89757225-9d6f2f00-db1f-11ea-93de-058b689fdb06.png)

실행이 아주 잘 됩니다. 이상으로 간단하고 최대한 쉬운 방향으로 Python class의 사용법을 공부하고 정리해 보았습니다.
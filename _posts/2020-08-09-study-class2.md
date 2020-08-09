---
title: 'Class 공부 #02'
date: 2020-08-07
tags: [AIFFEL, Fundamental]
comments: true
---

# Python Class 공 부 해 보 기 - 2

## **메소드(Method)**
메소드부터 이어가겠습니다. 속성을 정의해 보았고, SmartPhone에 전원을 키고 끄는 메소드를 만들어 보겠습니다. 전원의 현재 상태를 나타내는 속성값도 필요할 것 같군요
```python
class SmartPhone:
    def __init__(self, company, model, color, waterproof):
        self.company = company,
        self.model = model,
        self.color = color,
        self.waterpoof = True 
        self.power = 'off'
    
    def power_on_or_off(self):
        # 실행 시, 전원이 꺼져있으면 켜고, 켜져있으면 끄는 기능 
        if self.power =='off':
            self.power = 'on'
            print('전원이 켜졌습니다')
        elif self.power =='on':
            self.power = 'off'
            print('전원이 꺼졌습니다.')
```

이렇게 전원을 기능을 만들었습니다. 메소드는  **def** 를 이용해서 함수 형태로 만들어 구현을 합니다. 단순히 전원을 켜고 끄는 기능은 **return**이 필요 없습니다. 이번에는 **return**이 있는 기능을 만들어 보겠습니다. App을 다운받고 App 목록을 볼 수 있는 기능을 만들어 보겠습니다.(App 목록을 저장할 속성값이 필요할 듯 합니다.)

```python
    ...
        self.power ='off'
        self.app_list = []
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
App을 다운로드하는 기능을 추가해 보았습니다. 그런데 처음에 만든 SmartPhone 클래스 속성에는 internet 이라는 속성이 없고, 인터넷 연결이 없을 때 연결해주는 connect_internet이라는 기능도 없습니다.  
다음 포스트에서는 이것을 해결할 수 있는 
<font size=15, color='bluesky'> 클래스 상속 </font> 의 개념을 한 번 공부해 보겠습니다. 

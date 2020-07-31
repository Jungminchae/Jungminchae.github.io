---
title: '탐험 01 가위바위보 인식하기'
date: 2020-07-31
tags: [AIFFEL, Exploration]
comments: true
---

# **AIFFEL에서의 첫 번째 탐험**

인공지능에 관심이 있고 딥러닝을 접해본 사람들의 *99.9%* 는 아마도 MNIST를 접해봤지 않을까 생각한다.
AIFFEL에서 첫 번째 탐험 노드는 MNIST였다. 과거 기억을 더듬어 가며 코드를 작성하며 복습하는 마음 가짐으로 접근했다.

```python

model=keras.models.Sequential()
model.add(keras.layers.Conv2D(64, (3,3), activation='relu', input_shape=(28,28,1)))
model.add(keras.layers.MaxPool2D(2,2))
model.add(keras.layers.Conv2D(128, (3,3), activation='relu'))
model.add(keras.layers.MaxPooling2D((2,2)))
model.add(keras.layers.Flatten())
model.add(keras.layers.Dense(64, activation='relu'))
model.add(keras.layers.Dense(10, activation='softmax'))

```

데이터를 불러오고 이런 간단한 CNN 모델로 10번 정도만 학습 시켜도 뛰어난 성능을 낸다. 좀 시시하다고 생각하면서 넘어가고 있었는데, 이제 MNIST 해봤으니 **가위,바위,보 손 모양** 인식을 해보라고 했다. 

데이터는 ?? -> 직접 수집

### **Teachable Machine**

데이터를 직접 수집해서 분류 모델을 만들어봤던 경험은 없었다. 
[TeachableMachine](https://teachablemachine.withgoogle.com/train/image)에서 데이터를 Web Cam을 이용해서 쉽게 손 모양 데이터를 구할 수 있었다. 

![tm](https://user-images.githubusercontent.com/60789129/89010522-b589c600-d349-11ea-97d8-94198357b8db.png)


### **학습 하고 결과 보기**

가위,바위,보 각각 100장씩 찍고 학습했다. 총 300장... 딥러닝 학습에는 너무나도 적은 양... 

train, test 나눠서 결과 찍어보니 ***Accuracy*** 0.3 정도

하지만 우리 팀은 5명이고 10개가 넘는 팀, 공유 문화가 발달된 **AIFFEL** 여차 저차해서  Train 1만장 Test 2000장을 모았다. 위의 모델같이 간단한 모델로도 70%가 넘는 정확도가 나왔다

간단한 프로젝트 였지만 팀원들과 상의하고 공유하면서 나도 몰랐던 내 빈 곳을 채워갈 수 있었다.

AIFFEL이 지향하는 Leaning by doing의 맛을 깨달아 가는 중
with Team

[탐험 코드]('https://github.com/Jungminchae/rock_paper_scissor_classification)

앞으로가 기대가 많이 되는 AIFFEL 이다.

{% if page.comments %} 
 {% endif %}

# 1. Visualizing CNN
## 1.1 What is CNN visualization?
CNN이 하나의 기계라고 생각해본다. 만약 잘 안될 때 원인을 확인하기 위해 뜯어보려고 한다. <br>
CNN은 여러 단계를 걸쳐 학습을 통해서 정해진 weight 들의 조합으로 복잡하게 연결되어있다. <br>
해석이 안 되는 블랙박스 시스템이라 할 수 있다. 이 블랙박스를 가늠하게 하는 "**visualization** tools as debugging tools" 소개.

 - **What** is inside CNNs? 
 - **Why** do they perform so well?
 - How would they **be improved** 
![image](https://user-images.githubusercontent.com/35412566/133175473-ce5f29f1-0ce0-4c82-9ede-cc2e669068c5.png)

<br>

### ZFNet example: **deconvolution** 을 이용해서 visualization을 시도
&nbsp;&nbsp; 낮은 계층에서는 방향성이있는 filter들:  선을 찾는 filter, 동그란 블럭을 찾는 filter 등등 (기본적인 영상처리(컬러, 엣지, 각도, 블록)<br>
&nbsp;&nbsp; --> 높은 게층 : 점점 의미있는 이미지를보여진다.  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![image](https://user-images.githubusercontent.com/35412566/133176772-6af07125-3144-4b7a-b1b8-a27866b063ce.png)

<br>

## 1.2 Vanilla example: filter visualization
![image](https://user-images.githubusercontent.com/35412566/133179172-78dd8c56-cea7-4a7c-9e6b-74299d72d0b4.png)

Alex Net으로 Input image를 받아서 11x11 convolution을 Filter visualization을 추출<br>
input image와 Filter visualixation을 매칭?하여 Activation visualization 맵을 보여 준다.(한 채널이라 흑백을 보여준다.)
- 각 이미지마다 filter에 맞는 이미지를 출력하여 보여줌.
- 높은 계층으로 안가는 이유: 깊게 갈수록 차원수가 높아지기 때문에 보기 어렵다.(사람에게 직관적으로 다가오지 않음)
<br>

## 1.3 How to visualize neural network
![image](https://user-images.githubusercontent.com/35412566/133179761-d3574f74-73cf-4e50-83a5-57229d5441d1.png)

<br>
___
<br>

# Analysis of model behaviors
## 2.1 Embedding feature analysis
비슷한 영상들을 보면서 visualization(DB같은게 필요함)
![image](https://user-images.githubusercontent.com/35412566/133181152-07b7d68a-b15a-4113-88d1-a292cf4ef8fb.png)

<br>

![image](https://user-images.githubusercontent.com/35412566/133181278-110119e4-5b8a-48dc-adf9-611e13a78487.png)

고차원 공간에서 visualization하기에는(검색된 예제를 통해서 분석하는 방법은): 전체적인 그림을 활용하기 어렵고, 너무 고차원이라 상상하기 힘들다.<br>
이를 개선한 방법이 **차원 축소 방법**을 통해 보는 것.

대표적인 방법으로 [**t-SNE**](https://gaussian37.github.io/ml-concept-t_sne/)이 있다. 

```
t-distributed stochastic neighbor embedding 소위 t-SNE라고 불리는 방법은 높은 차원의 복잡한 데이터를 2차원에 차원 축소하는 방법입니다. 
낮은 차원 공간의 시각화에 주로 사용하며 차원 축소할 때는 비슷한 구조끼리 데이터를 정리한 상태이므로 데이터 구조를 이해하는 데 도움을 줍니다.
```

-> 경계선에 있거나 맞닿아 있는 이미지에 대해서 모델이 이 클래스들을 비슷하게 보고 있다라는 이해와 함께 변경하기 위한 시도가 된다고 한다.

## 2.2 Activation investigation
### Layer activation - 히든 노드(mid)와 실제 이미지(high)에 오버레이를 통해 이미를 보는 것. 
- CNN은 히든 unit들이 각각 간단한 얼굴, 손을 익식하여 다층으로 쌓아서 인식하는것.
<br>

### Maximally activating patches - 히든노드에서 가장 높은 값을 갖는 위치의 근방 data를 out data를 보는것.
- 큰그림 보다는 중간에 대한 그림을 보기에 적합하다. 
- 히든 노드에거 가장 높은 값의 Receptive field를 추출한다. 
<br>

### [Class visualization](https://glassboxmedicine.com/2019/07/13/class-model-visualization-for-cnns/) - 예제 대이터를 사용하지 않고 Network가 내제하고 있는 이미지로 visualization
최적화를 통해서(Gradient decent 등과)같이 영상 얻는다. 

<br>

![image](https://user-images.githubusercontent.com/35412566/133186353-dcfe2b8c-0f3f-4c5f-892c-b7a304ac80cc.png)

이미지를 얻는 과정 
1. 임의의 영상을 넣어서 타겟 클래스에 해당하는 에측 점수를 얻습니다. 
2. Backpropagte를 통해서 클래스 점수가 높아지게 합니다. 
3. 현재 이미지에 더합니다.(업데이트 합니다.) 이과정을 여러번 반복한다.

<br>
___

<br>

## Model decision explanation 
모델이 특정 입력을 보았을때 어떤 각도로 해석하고 있는지. 
### 3.1 Saliency test
<br>

### Occlusion map - 각 영상에대한 제대로 판정대기 위한 중요도를 판별
![image](https://user-images.githubusercontent.com/35412566/133186656-49d087c6-1078-451f-a3fb-de5e60498b1b.png)
위의 이미지에서는 코끼리의 이마? 부분의 중요도가 가장 높다. 

### via Backpropagation - 최족적으로 결정지은 값을 출력
![image](https://user-images.githubusercontent.com/35412566/133186989-2244c138-1579-43c2-8362-4bf3a1f53906.png)

위의 이미지가 몽환적 이지만 특징들이 살아있다. 

이미지를 얻는 과정
1. 임의의 영상을 넣어서 클래스 점수를 얻는다.
2. Backpropagte으로 입력 도메인의 gradient을 구한다.
3. gradient에 절대값, 제곱하여 절대적인 크기를 구한다.(여러번 반복으로 얻어도 된다.)


#### Class visualization vs via Backpropagation 차이점
- 입력으로 의미없는 값을 입력하고, 현재 데이터에 의존한 값을 보려고 함.

<br>
### 3.2 Backpropagate features

![image](https://user-images.githubusercontent.com/35412566/133191256-22b3e448-a0c0-4b59-856b-2577ed6630f3.png)

Foward pass에서 음수가 나온 부분은 ReLu에 의해서 0으로 표현하게 됩니다.<br>

이런 마스킹 패턴을 저장해 두었다가. backpropagation 할때 양수, 음수가 합쳐진 gradient가 오면 저장이 되어있던 마스크로 마스킹을 해준다. <br>

Zeller가 (deconvent)사용한 방법은 backward할떄 gradient자체에 ReLu를 사용했다. <br>

두번째와 세번째를 AND연상을 통해 합쳐 준다. 

![image](https://user-images.githubusercontent.com/35412566/133192051-ad155b35-1ef3-472e-9c63-972f424d0454.png)
깨끗하고 깨끗한 이미지를 결정한다. 
양뱡향에서 클래스 결정에 도움이 되는 부분만 추출한게 : Guided backprop 

### 3.3 Class activation mapping
### CAM - 어떤 부분을 참조 했는지 heatmap으로 표현
[CAM](https://www.google.com/search?q=class+activation+mapping&sxsrf=AOaemvLD1QQmYnN5mrafSe6r8cvo4Udeew%3A1631591781577&ei=ZR1AYcXjIqaVr7wPyPSZgAQ&oq=class+activation+mapping&gs_lcp=Cgxnd3Mtd2l6LXNlcnAQAzIFCAAQgAQyCggAEIAEEIcCEBQyBQgAEMsBMgUIABDLATIFCAAQywEyBQgAEIAEMgQIABAeMgQIABAeMgQIABAeMgQIABAeMgcIABAeEIsDMgkIABAFEB4QiwMyCQgAEAUQHhCLAzIJCAAQBRAeEIsDOgcIABBHELADOgQIIxAnOgQIABBDOgoIABCxAxCDARBDOg4IABCABBCxAxCDARCLAzoLCAAQgAQQsQMQiwM6BwgAEEMQiwM6DQgAELEDEIMBEEMQiwM6CAgAEIAEEIsDOgcIIxDqAhAnOgoIIxDqAhAnEIsDOgcIABCxAxBDOg0IABCABBCHAhCxAxAUOhMIABCABBCHAhCxAxCDARAUEIsDOhAIABCABBCHAhCxAxCDARAUOggIABCABBCxAzoLCAAQgAQQsQMQgwE6BwgjELECECc6CggAELEDELEDEAo6CggAELEDEIMBEAo6BwgAELEDEAo6DQgAELEDEIMBEAoQiwM6CggAELEDEAoQiwM6CggAEIAEEAoQiwM6BwgAEIAEEAo6BwgAEAoQywE6BAgAEAo6BwgAEAoQiwM6CggAEIAEELEDEAo6CAgAEMsBEIsDSgQIQRgAUM83WOFwYOdxaARwAngAgAF8iAHLGJIBBDAuMjiYAQCgAQGwAQ7IAQS4AQPAAQE&sclient=gws-wiz-serp&ved=0ahUKEwiFqryEyf3yAhWmyosBHUh6BkAQ4dUDCA4&uact=5): CNN의 일부를 개조하여 만듬. 
<br>

![image](https://user-images.githubusercontent.com/35412566/133192822-775b2bd7-8a13-4e35-8014-d854df9594cb.png)<br>
영상인식만으로 위치도 찾을 수 있는 방법이다.
구조를 변경해야하고, 

###  Grad-CAM - CAM에서 구조를 변경하지 않고 가능하게 함.
back 


### <면접 질문> Auto grad란? 
Pytorch 에서 제공하는 패키지로써, 간단하게 미분을 자동으로 계산해주는 기능입니다. 
파이토치를 auto grad를 back ward하는 엔진이라고 하고, 이를 사용하는 것이 chain 을 사용합니다.
auto grad를 back ward하는 엔진이라고 하고, 이를 사용하는 것이 chain 을 사용합니다.

/eq 
 

___
-- 읽어 볼 자료 
- https://blogik.netlify.app/BoostCamp/U_stage/41_cnn_visualization/


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

대표적인 방법으로 **[t-SNE](https://gaussian37.github.io/ml-concept-t_sne/)**이 있다. 

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

___

<br>


## Model decision explanation
### 3.1 Saliency test
### 3.2 Backpropagate features
### 3.3 Class activation mapping



# 1. Visualizing CNN
## 1.1 What is CNN visualization?
CNN이 하나의 기계라고 생각해본다. 만약 잘 안될 때 원인을 확인하기 위해 뜯어보려고 한다. <br>
CNN은 여러 단계를 걸쳐 학습을 통해서 정해진 weight 들의 조합으로 복잡하게 연결되어있다. <br>
해석이 안 되는 블랙박스 시스템이라 할 수 있다. 이 블랙박스를 가늠하게 하는 "**visualization** tools as debugging tools" 소개한다. 

 - **What** is inside CNNs? 
 - **Why** do they perform so well?
 - How would they **be improved** 
![image](https://user-images.githubusercontent.com/35412566/133175473-ce5f29f1-0ce0-4c82-9ede-cc2e669068c5.png)

<br>

### ZFNet example: **deconvolution**을 이용해서 visualization을 시도
&nbsp;&nbsp; 낮은 계층에서는 방향성이있는 filter들:  선을 찾는 filter, 동그란 블럭을 찾는 filter(기본적인 영상처리)<br>
&nbsp;&nbsp; --> 높은 게층 : 점점 의미있는 이미지를보여진다.  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![image](https://user-images.githubusercontent.com/35412566/133176772-6af07125-3144-4b7a-b1b8-a27866b063ce.png)

<br>

## 1.2 Vanilla example: filter visualization



## 1.3 How to visualize neural network
<br>

___
<br>

# Analysis of model behaviors
## 2.1 Embedding feature analysis
## 2.2 Activation investigation

<br>

___

<br>


## Model decision explanation
### 3.1 Saliency test
### 3.2 Backpropagate features
### 3.3 Class activation mapping


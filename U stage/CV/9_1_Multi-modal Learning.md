> Multi-modal: 한 타입의 data가 아니라 다른 특성을 갖는 데이터 타입들을 같이 활용하는 data

# 1. Overview of multi-modal learning
 
## Multi-modal의 어려운점(방해 요소?)
### 1. 데이터의 표현 방법이 각자 다르다.(오디오: 1D Waveform, 이미지: 2D/3D array, 텍스트: embedding vector)
### 2. 정보의 양,  특징들이 Unbalance하다(1:N ,N:1)
### 3. 모델을 학습한다고 할때 서로 공평하게 참조를 해서 좋은 모델로 가는 거냐?? X 
![image](https://user-images.githubusercontent.com/35412566/133710852-a93c552e-c5c5-41a0-a119-06961dad7d48.png)
###### fig 1. 트레이닝이 잘 안되면 쉬운에만 bias된다. 
<br>

### 그럼에도 불구하고, 이전에 해결 못하는것들의 해결할수 있는 단서를 제공하기 때문에 사용된다. 
### Multi-modal을 사용하는 task들에 일정한 패턴이 존재
![image](https://user-images.githubusercontent.com/35412566/133711110-132b80f2-413e-45e0-8600-78b0f8d79be7.png)


# 2. Multi-modal tasks (1) - Visual data & Text
## 2.1 Text embedding
## 2.2 Joint embedding
## 2.3 Cross modal translation
## 2.4 Cross modal reasoning

# 3. Multi-modal tasks (2) - Visual data & Audio
## 3.1 Sound representation
## 3.2 Joint embedding
## 3.3 Cross modal translation
## 3.4 Cross modal reasoning

# Contents
- Basics
- Taxonomy(분류)
- Baseline Moel - EAST

# Basics
## 글자 영역 검출
### 객체의 특징
- 매우 높은 밀도
- 극단적 종황비(일어)
- 특이 모양(구겨진 영역, 휘어진 영역, 세로 쓰기 영역)
- 모호한 객체 영역(띄어쓰기, 문맥)
- 크기 편차
<br>

### 글자 영역 표현법
![image](https://user-images.githubusercontent.com/35412566/140930949-d185cf34-a2bd-4776-9e18-b3709a833ea5.png)
- 직사각형(RECT, Rectangle)
- 직사각형 + 각도(RBOX, Rotoated Box)
- 사각형(QUAD, Quadrilateral)
- 다각형,Polygon(x1, y1, ... xn, yn): 2N points를 이용, 상하 점들이 쌍으로 이루도록 배치
<br>

# Taxonomy
## SoftWare1.0 
![image](https://user-images.githubusercontent.com/35412566/140931836-2acf27c5-b594-4cf5-b074-231ae158ec45.png)

[자연영상에서 문자의 형태 분석을 이용한 문자영역
추출에 관한 연구](https://www.koreascience.or.kr/article/JAKO201809258121085.pdf)
[MSER](https://sijoo.tistory.com/311) / [SWT](https://iskim3068.tistory.com/100)
<br>

## SoftWare2.0 
### Regression-based vs Segmentation-based
![image](https://user-images.githubusercontent.com/35412566/140933700-1958b7cf-a859-40d3-9517-4dd351bf012d.png)
<br>

### Regression-based 단점
[TextBoxes++ paper](https://arxiv.org/pdf/1801.02765.pdf)
- 뷸필요한 영역을 포함 한다.(Bounding box 표현 방식의 한계)(직사각형에만 효과)
- Bounding box 정확도 하락(Receptive field의 한계)(훨씬 큰 Anchor box일 경우 성능 하락)
<br>

### Segmentation-based
![image](https://user-images.githubusercontent.com/35412566/140934614-26e98fd5-7abf-445c-a14c-f88f88e3182b.png)
[PixelLink paper](https://arxiv.org/pdf/1801.01315.pdf)
#### 단점
- 복잡하고 시간이 오래 걸리는 post-processing이 필요할 수 있다. 
- 서로 간섭이 있거나 인접한 개체 간의 구분이 어렵다. 
<br>

### Hybrid
![image](https://user-images.githubusercontent.com/35412566/140935069-eadb8667-5f22-4083-aa6d-c8ab5788d6a4.png)
[Mask TextSpotter paper](https://arxiv.org/pdf/1908.08207.pdf)
<br>

### Character-base vs Word-based
![image](https://user-images.githubusercontent.com/35412566/140936136-b051867f-7b33-44d8-9fe5-2f09c44df546.png)

### Character-Based Methods
- 글자단위 라벨링
- CARFT: Weakly-Supervised Learning(단어 단위 라벨링 -> 글자 단위 라벨링 추정한다.)
<br>


# Baseline Model - EAST
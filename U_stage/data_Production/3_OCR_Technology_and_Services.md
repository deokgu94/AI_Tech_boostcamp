# Contents
- 1.OCR Technology
- 2.OCR Services
<br><br>

# 1. OCR Technology
## OCR
- OCR: Optical Character Recognition
- STR: Scene Text Recognition
- 글자를 읽는다 = 글자 영역 찾기 + 영역 내 글자 인식 => OCR
<br>

![image](https://user-images.githubusercontent.com/35412566/140917883-e4565d72-ba5b-46a0-adcc-c16ff5a608d6.png)
[How to easily do Handwriting Recognition using Deep Learning](https://nanonets.com/blog/handwritten-character-recognition/)

Online Handwriting: 쓰여지는 텍스트의 흐름과 관련하여 많은 정보를 가지고 있는 경향이 있기 떄문에 꽤 높은 정확도로 분류될 수 있고 텍스트의 다른 문자 사이의 경계가 훨씬 더 명확하다고 한다. 
<br>

## 객체 검출, 다중 객체 검출(Object Detection) vs 글자 검출(Text Detection)
![image](https://user-images.githubusercontent.com/35412566/140920907-03453f44-d590-4715-8491-9bc25198ab08.png)

- 단일 객체 검출: 입력 이미지가 정의된 클래스 중 어디에 속하고, **해당 객체의 위치는 어디인지.**
- 다수 객체 검출: 입력 이미지 내에 정의된 클래스들에 **해당하고, 각 객체들의 위치는 어디인지**
- 글자 영역 다수 객체 검출: 단일 클래스(글자 영역 or 아닌 영역) 문제, 클래스 정보가 필요 없고 **글자 영역에 해당하는 객체의 위치만 추정**
<br>

## OCR Technology
![image](https://user-images.githubusercontent.com/35412566/140921999-8bf5af45-9371-4024-97fd-6171cb7762be.png)

### Detector(SoftWare2.0)
#### 글자 검출기: 이미지 입력에 글자 영역 위치가 출력인 모델
#### 객체 검출과의 차이점
- 1. 영역의 종횡비
- 2. 객체 밀도 
<br>

### Recognizer(SoftWare2.0)
#### 글자 인식기: Computer Vision과 Natural Language Processing의 교집합 영역 
![image](https://user-images.githubusercontent.com/35412566/140922581-7f8dd67d-5be6-4fe0-b93e-3852897c202f.png)
<br>

### Serializer(SoftWare1.0)
#### 정렬기: OCR결과값을 자연어 처리하기 편하게 일렬로 정렬하는 모듈, 결과값을 입력으로 받는 자연어 처리 모듈을 뒤에 붙여서 사용가능 
![image](https://user-images.githubusercontent.com/35412566/140923016-0f308741-5727-4d85-83e9-db7e540f217c.png)
<br>

### Text Parser(SoftWare2.0)
#### 자연어 처리 모듈 중 가장 많이 사용되어 기 정의 된 key들에 대한 value 추출
![image](https://user-images.githubusercontent.com/35412566/140925622-4064730c-eb08-421a-a6b2-5f38cb694d4f.png)
- 토큰화: 글자를 쪼갠다.(글자 단위 or 문맥 단위)
- [BIO(Begin/Inside/Outside) 태깅](https://wikidocs.net/24682): 토큰화 된 문자에 대해서 BIO로 태깅
- 후처리: 매칭
<br>


# 2. OCR Services
### Text Extractor
- Copy & Paste: 그림을 붙여넣어서 글자만 복사해서 사용 
```
GetWiFiPassword, ios15 
```
### Text Extractor + Natural Language Processing
- +Search   : Google Photo 에서 검색 기능 
- +Matching : Vibe 에서 캡쳐 이미지를 통해서 뮤직 플레이리스트 옮기는 기능 
- +금칙어 처리: 광고성/혐오성 이미지 제거 
- +번역:     : 외국어 입력 대체, 이미지 위에 번역 결과 표시 
### Key-Value Extractor 
- 신용카드
- 신분증
- 수기 입력 대체(명함, 사업자 등록증, 영수증, 영수증->더치페이)
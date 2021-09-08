# Polar plot 
[@https://matplotlib.org/stable/gallery/specialty_plots/radar_chart.html]
극 좌표계를 사용하는것

x,y -> r(거리), z(각)(반지름, 각도)

회전, 물리, 주기성에  일부 과학적 시각화에 사용

x,y 에서 사용한 line, scatter, bar를 polar plot에서도 사용 가능함

직교 좌표계 x,y에서 변환 가능
 x = R cos (세타)
 y = R sin (세타) 

## Rader plot

![image](https://user-images.githubusercontent.com/35412566/132447768-62103f48-8fb9-4803-8cc9-1e4c389b275a.png)

극좌표계를 사용하는 대표적인 차트. Star Plot으로 불리기도 함

데이터의 양을 표현하기에 좋음(캐릭터의 강함, 선수간의 비교, 데이터 간의 비교
- 비교에 적합

주의점:
 - 각 feautre가 독립적이여야한다.(ex> 자동차 -> 연비, 안정성 등으로 표현하면 척도가 다르기 때문에 주의)
 - 다각형의 면적이 중요해보이지만 feature의 순서에 따라 많이 달라진다.
 - feature가 많아질수록 가독성이 떨어짐


## Polar Coordinate

![image](https://user-images.githubusercontent.com/35412566/132449158-b7723372-710c-4b24-8316-2dff66a6e7a1.png)

$ax = fig.add_subplot(111, projection='polar')
$ax = fig.add_subplot(111, polar=True)
위를 통해 polar를 작성 되어야 함

### Polar coordinate 조정하기

$ax.set_rmax(2) : 2까지의 숫자까지 표현 해주게 된다. 
$ax.set_rticks([1,1.5,2]) rmax의 까지의 인덱싱을 말한다.
$ax.set_rmin(1) : rmax까지 표현하되 시작점이 0이 아된 rmin(1)로 부터 시작하게 설정해준다.

![image](https://user-images.githubusercontent.com/35412566/132449561-0165aa37-ed53-4c15-aaca-c17ed45e254f.png)

![image](https://user-images.githubusercontent.com/35412566/132450261-e80e3067-bf9e-436b-af67-c50a0ed70229.png)

![image](https://user-images.githubusercontent.com/35412566/132450310-21cb12e9-7ccf-4976-a145-35d1795ed076.png)


## Rader Chart 

$df.describe(): data frame에 대해서 데이터 요약해주는 메서드


![image](https://user-images.githubusercontent.com/35412566/132452043-5832f2b5-c00e-4da9-9434-839bc6273084.png)

theta = np.linspace(0, 2*np.pi, 6, endpoint=False)  // -0부터 6개 까지의 2*pn.pt의 값의 array를 만들어 주는 명령어.
print(theta)  # [0.         1.04719755 2.0943951  3.14159265 4.1887902  5.23598776]

![image](https://user-images.githubusercontent.com/35412566/132452298-c3b79a09-9da0-45dd-bccc-59af9cd53a99.png)


![image](https://user-images.githubusercontent.com/35412566/132455674-ff1c2eaf-fd17-4aa8-852e-81a08f569e4c.png)


![image](https://user-images.githubusercontent.com/35412566/132455841-5058f7fd-7edf-4230-baa3-2d6b69493a83.png)

![image](https://user-images.githubusercontent.com/35412566/132455867-87afd38f-7bc5-4bd7-b486-9bcca86dbe2d.png)


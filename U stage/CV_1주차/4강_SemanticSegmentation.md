## Semant segmentation

Image Classification에서는 영상 단위 -> Semant Segmentation에서는 Pixel 단위로 분류한다. 

사용하는 곳
 - 의료 이미지
 - Autonomous driving(포스트 프로세싱에 사용한다.)
 - 컴퓨터를 이용한 편집


## Model

### FCN
 - 첫 end-to-end semant segmentation architecture(전에는 사람의 손에의 하나씩 변경 해야 했었다.(변경에 대한 문제가 컸음))
 - 임의 입력 사이즈로 해도 문제가 없이 작동한다. 
 - 1x1 convolutions으로 작용해서 얻는 이미지는 굉장히 작은 이미지가 나온다.(strid,...의 이유로)
 --> 저해상도를 해결하기 위해 Upsamplin layer를 추가함.
 
 
 
 

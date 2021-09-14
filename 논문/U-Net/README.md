## U-Net: Convolutional Networks for Biomedical Image Segmentation
### Paper [Link](https://arxiv.org/pdf/1505.04597.pdf)
___


## 2. Network Architecture 
 It consists of a contracting path (left side) and an expansive path (right side).<br>
 >왼쪽에는 contracting path, 오른쪽에 expansive path로 구성되어있다.
  
 contracting path는 It consists of the repeated application of two 3x3 convolutions (unpadded convolutions), 
 each followed by a rectified linear unit (ReLU) and a 2x2 max pooling operation with stride 2 for downsampling.
 -> 두개의 3x3 convolution, ReLu, 2x2 max pooling(stride 2)
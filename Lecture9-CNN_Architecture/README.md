# CNN Architecture

### LeNet-5
![image](https://user-images.githubusercontent.com/48700102/116843218-3f88f700-ac1a-11eb-87e0-7c9a05a3a941.png)

- 가장 첫번째로 실질적인 결과를 낸 ConvNet
- digit recognition



### AlexNet

- 첫번째로 image classification에 대해서 large, deep 한  network로서 classification을 수행함
- ILSVRC2012 에서 가장 좋은 성능을 보임(first deep learning, CNN based winner)
- 8개의 laye로 구성됨
- ReLu 함수 activation function으로 처음으로 사용
- fully connected layer에서 Dropout 적용
- AlexNet layer의 특정 layer에서는 두개로 나눠지는데, 당시의 gpu로는 하나로는 모든 parameter를 담을수 없었기에 두개로 나누고, 특정 layer들끼리의 연결을 통해 통신함

![image](https://user-images.githubusercontent.com/48700102/116843585-58de7300-ac1b-11eb-9881-2cc453903b9c.png)
- input image: 227\*227\*3
- first layer : convolutional layer 96 11\*11 stride of 4 => output : 55\*55\*96
- second layer : pooling layer 3\*3 stride of 3 => output : 27\*27\*96
- ....



### VGGNet
- layer의 갯수를 늘리고, convolutional filter size를 줄임 (16~19 layers)
- 3*3 convolutional filter를 사용
- 

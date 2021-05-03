# CNN Architecture

## LeNet-5
![image](https://user-images.githubusercontent.com/48700102/116843218-3f88f700-ac1a-11eb-87e0-7c9a05a3a941.png)
- 가장 첫번째로 실질적인 결과를 낸 ConvNet
- digit recognition
<br><br><br><br><br>


## AlexNet
- 첫번째로 image classification에 대해서 large, deep 한  network로서 classification을 수행함
- ILSVRC2012 에서 가장 좋은 성능을 보임(first deep learning, CNN based winner)
- 8개의 layer로 구성됨
- ReLu 함수 activation function으로 처음으로 사용
- fully connected layer에서 Dropout 적용
- AlexNet layer의 특정 layer에서는 두개로 나눠지는데, 당시의 gpu로는 하나로는 모든 parameter를 담을수 없었기에 두개로 나누고, 특정 layer들끼리의 연결을 통해 통신함
![image](https://user-images.githubusercontent.com/48700102/116843585-58de7300-ac1b-11eb-9881-2cc453903b9c.png)
- input image: 227\*227\*3
- first layer : convolutional layer 96 11\*11 stride of 4 => output : 55\*55\*96
- second layer : pooling layer 3\*3 stride of 3 => output : 27\*27\*96
- ....
<br><br><br><br><br>


## VGGNet
- layer의 갯수를 늘리고, convolutional filter size를 줄임 (16~19 layers)
- 3*3 convolutional filter를 사용
- why smaller filter size? => small size filter 를 여러개 쌓아서 big size filter의 효과를 낼 수 있으며, fewer parameters, more discriminative decision function
- ILSVRC2014 에서 classification에서 2번째로 입상함
![image](https://user-images.githubusercontent.com/48700102/116844093-000fda00-ac1d-11eb-9623-1a23d61d796b.png)
- 총 138M 의 parameter로 이루어져 있음
- fully connected layer에 parameter가 많음
<br><br><br><br><br>


## GoogLeNet
- computation에서 향상을 꾀하고자 함 => Inception module의 도입
- 22 layers, No fully connected layer, less parameter than VGGNet
- winner of ILSVRC 2014 classification
![image](https://user-images.githubusercontent.com/48700102/116844732-ea031900-ac1e-11eb-9310-e281dda001ba.png)
- Inception module :Inception modeul을 stacking해서, Network in Networks 의 구조로 모델을 형성하고, 그 안에서 parallel filter operation을 통해서 모델을 구성함
![image](https://user-images.githubusercontent.com/48700102/116845046-b8d71880-ac1f-11eb-82a5-6485bc96efe7.png)
- Inception module의 문제점 : computational complexity(parallel filter operation을 수행한 뒤, concatenation을 통해서 다음 layer로 전해지는데 operation이 너무 많아짐)
![image](https://user-images.githubusercontent.com/48700102/116845286-634f3b80-ac20-11eb-95ba-0f4537ffd165.png)
- Solution : convolutional layer로 들어가기 전에, 1*1 convolutinal layer로 depth를 줄이면 됨















# CNN Architecture

## LeNet-5
<img src="https://user-images.githubusercontent.com/48700102/116843218-3f88f700-ac1a-11eb-87e0-7c9a05a3a941.png" width="70%">

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
<br>
<img src="https://user-images.githubusercontent.com/48700102/116843585-58de7300-ac1b-11eb-9881-2cc453903b9c.png" width="70%">
<br>
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
<br>
<img src="https://user-images.githubusercontent.com/48700102/116844093-000fda00-ac1d-11eb-9623-1a23d61d796b.png" width="70%">

- 총 138M 의 parameter로 이루어져 있음
- fully connected layer에 parameter가 많음
<br><br><br><br><br>


## GoogLeNet
- computation에서 향상을 꾀하고자 함 => Inception module의 도입
- 22 layers, No fully connected layer, less parameter than VGGNet
- winner of ILSVRC 2014 classification
<br>
<img src="https://user-images.githubusercontent.com/48700102/116844732-ea031900-ac1e-11eb-9310-e281dda001ba.png" width="70%">

- Inception module :Inception modeul을 stacking해서, Network in Networks 의 구조로 모델을 형성하고, 그 안에서 parallel filter operation을 통해서 모델을 구성함
<br>
<img src="https://user-images.githubusercontent.com/48700102/116845046-b8d71880-ac1f-11eb-82a5-6485bc96efe7.png" width="70%">

- Inception module의 문제점 : computational complexity(parallel filter operation을 수행한 뒤, concatenation을 통해서 다음 layer로 전해지는데 operation이 너무 많아짐)
<br>
<img src="https://user-images.githubusercontent.com/48700102/116845286-634f3b80-ac20-11eb-95ba-0f4537ffd165.png" width="70%">

- Solution : convolutional layer로 들어가기 전에, 1*1 convolutinal layer로 depth를 줄이면 됨(bottleneck layer)
<br>
<img src="https://user-images.githubusercontent.com/48700102/116845524-0738e700-ac21-11eb-93c5-845930ad2eb0.png" width="70%">

- 전체적인 구조 : Stem Network - Stack of Inceptoin module - Classifier output(no FC layer)
- 중간에 Auxiliary classification output이 들어가고, deep network 중간 layer에서 gradient injection을 하기 위해서
<br><br><br><br><br>


## ResNet
- ILSVRC 2015 classification winner
- extreme deep network
- 계속 layer를 stacking하는 것이 무조건적으로 모델의 학습능력이 향상시키지는 않는다.(overfitting으로 인한 문제가 아님) 의 사실에 착안, 모델을 생성함.
<br>
<img src="https://user-images.githubusercontent.com/48700102/116846118-94307000-ac22-11eb-8376-d05782a2e72f.png" width="70%">

- deeper model이 shallower model만큼의 성능이 나와야 되는데 안나옴 -> deeper model에서의 optimization 관점으로 문제를 접근 -> deeper model에서도 shallower model 만큼의 성능을 보이기 위해서 shallow layer에서는 shallow model의 learned layer를 가져오고, deeper layer에서는 identity mapping을 추가하는 방식으로 접근
- deep layer에서는 H를 직접 학습시키는 어려움-> H=F(x)+x로 나누고, F를 학습 하고자 함
<br>
<img src="https://user-images.githubusercontent.com/48700102/116847477-934d0d80-ac25-11eb-8fd0-b5b2fe98198a.png" width="70%">

- no FC layer, no dropout
<br><br><br><br><br>


## Other Architectures
- NIN(Network in Networks) : convolutional layer 뒤에 micro network를 추가해서 abstrack feature를 더 잘 포착하려 함 (여기서 사용한 1*1 conv 개념이 googlenet, ResNet bottleneck에서 사용됨)
- Improved ResNet from creators of ResNet
- Wide residual networks : 모델을 deeper하게 만드는 접근과는 다르게, wider layer들로 모델을 구성함
- ResNeXt : residual block을 parallel한 block으로 구성함
- Stochastic Depth : depth에서의 vanishing gradient를 해결하기 위해서, trainging 과정에서 특정 layer들을 drop해서 training할떄읭 model depth를 줄임
- FractalNet : ResNet에서 벗어나, residual 접근에서 벗어난 새로운 접근방법. shallow and deep path로 모델을 구성
- DenseNet : Dense block들로 구성되며, input은 모든 dense block의 input들로 들어감 (vanishing gradient을 해결)
- SqueezeNet : AlexNet 보다 50배 낮은 parameter로 AlexNet과 동일한 성능을 보임
 









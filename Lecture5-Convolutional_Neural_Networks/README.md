# Convolutional Neural Network

## Convolutional Neural Networks
- 실제 이미지는 model 에 input 으로 들어갈때, 일차원의 vector 의 형태로 들어가게 됨 -> data 에서의 spatial structure 를 유지한채 data 를 학습 시키고 싶어함(이미지 픽셀 과 같은 경우 주변 픽셀 값과 어떠한 이미지에 대해서 밀접한 관련이 있기 때문에)
<br>
<img src="https://user-images.githubusercontent.com/48700102/118361547-f2683600-b5c6-11eb-96d1-d4f3a54f1932.png" width="50%">
<br>

- filter 를 이미지를 따라서 진행하면서 새로운 크기의 data 를 만든다. filter 의 수에 따라서 새로운 data 의 차원수를 조정할 수 있음 ex) 3*32*32->6*28*28 using 6 5*5*3 filter
- 이러한 convolutional layer 를 stacking하면 할수록, 보다 더 high-level feature 에 대해서 학습을 진행함.
<br>
<img src="https://user-images.githubusercontent.com/48700102/118392060-76c3c300-b672-11eb-9520-e8c3b208817c.png" width="50%">
<br>

- 실제로 Convolutional Neural Network를 구성할때, convolutional filter를 stacking한 ConvNet, 그 다음에 진행 되는 Activation Function이 여러개 쌓여져 있고, 마지막으로, fully connected layer로 구성되어 있다.
<br><br><br><br><br>

## Convolutional filter dimension
- stride : convolutional filter이 진행할때, 옆으로 몇칸씩 이동할지 결정하는 값
- padding : convolutional filter를 진행 하게될때, border data에 대해서는 다른 중앙 data들에 비해서 convolutional filter가 거치는 정도가 낮아지는 형평성의 문제가 발생하거나 convolutional filter를 거친 output data의 size를 조정하기 위해, data 주변으로 추가 data를 추가해서 convolutional filter를 적용시키는데, 이때 주변으로 몇칸을 추가하는지 결정하는 값
<br>
<img src="https://user-images.githubusercontent.com/48700102/118392252-9e675b00-b673-11eb-867d-b11bb0b80e0f.png" width="50%">
<br>

- padding P, stride S, kernel size K가 Convolutional filter가 정해지고, input data 가 H*W 로 구성될때, output data는 ((H-K+2*P)/S+1)*((W-K+2*P)/S+1)로 구성되게 된다.
<br>
<img src="https://user-images.githubusercontent.com/48700102/118392330-1e8dc080-b674-11eb-822b-185d9554f33f.png" width="50%">
<br>

- 1\*1 convolutional filter의 중요성 : 1\*1 convolutional filter를 사용하게 되면 모든 spatial data를 순회하면서, 차원수를 줄여주는 일종의 abstraction을 적용시킬 수 있다.
<br><br><br><br><br>

## brain/neuron view of Conv layer
<br>
<img src="https://user-images.githubusercontent.com/48700102/118393027-b7720b00-b677-11eb-885b-8009b9877f80.png" width="50%">
<br>

- Convolutional filter에서 filter size만큼의 receptive field를 통해서 neuron이 activate된다고 볼 수 있다.
- neuron 입장에서는 data의 spatial structure를 유지한채, neuron에 data가 전해져 온다고 볼 수 있다.
<br>
<img src="https://user-images.githubusercontent.com/48700102/118393043-d83a6080-b677-11eb-8958-ebc262be6e78.png" width="50%">
<br>

- Conv layer가 여러개의 filter로 구성되어 있다면, input data의 같은 region을 보지만, 각 filter 별로 보는 data feature가 달라진다고 볼 수 있다.
<br><br><br><br><br>

## Pooling layer
- Pooling layer : 기존 data representation을 좀더 작게 만들며, output data를 작게 만든다.
<br>
<img src="https://user-images.githubusercontent.com/48700102/118393167-9cec6180-b678-11eb-9da2-79f63985187a.png" width="50%">
<br>

- ex) Max-pooling : kernel 상에서 가장 큰 값만을 취하는 pooling layer
- pooling layer에서는 일종의 down sampling을 하는게 목적이기 때문에, 일반적으로 zero padding을 사용하지 않는다.
<br><br><br><br><br>

## Fully connected Layer
- 일반적으로 Convolutional neural Network는 여러개의 ConvNet-Activation layer로 구성되어 있으며, 중간에 Pooling layer가 존재한다. 또한 마지막으로 하나의 Fully connected layer로 최종 classifier가 나오게 된다.






















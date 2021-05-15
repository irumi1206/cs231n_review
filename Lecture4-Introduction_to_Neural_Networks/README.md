# Introduction to Neural Networks

## Backpropagation in computational graph
- 어떤 함수든 computational graph로 표현 할 수 있고, 이를 통해 gradient descent 를 back-propagation 과 편미준에서의 chain rule를 이용해서 쉽게 할 수 있음.
![image](https://user-images.githubusercontent.com/48700102/118359843-43c0f700-b5c0-11eb-8e16-fadb0f919ac8.png)
![image](https://user-images.githubusercontent.com/48700102/118359852-458aba80-b5c0-11eb-8bfe-8edf86fa1ffc.png)
- 위와 같은 computational graph가 있을떄 현재 함수값들과 local gradient 를 이용해서 각각의 local 변수에 대한 최종 output 의 gradient를 계산할 수 있음.
![image](https://user-images.githubusercontent.com/48700102/118359866-4cb1c880-b5c0-11eb-8271-cb8fd60e8dc3.png)
- computational graph, chain rule 의 장점: local gradient 를 관리하기 편하고, 현재 함수에서만 계산하면 되서 편함, 순차적으로 현재 node 에서의 전에 연결되어 있는 node 들만 보고, gradient 만 계산하면 되서 복잡하게 계산할 필요가 없음.
- 순차적으로 함수를 앞쪽으로 진행하면서 함수값들을 계산하고, 최종 함수값에서 뒤로 쫓아가면서 local gradient을 계산하기 때문에 이를 feed-forward, back-propagation 이라고 함.
![image](https://user-images.githubusercontent.com/48700102/118359887-63f0b600-b5c0-11eb-8d02-dc5ae11cb7f0.png)
- back-propagation을 하는 과정에서 위의 그림과 같이 하나의 값이 두개의 노드로 전해지는 경우, back-propagation 을 진행할 때 gradient를 더해주면 된다.
<br><br><br>

## Backpropagation in vectorized operations
![image](https://user-images.githubusercontent.com/48700102/118359918-736fff00-b5c0-11eb-8294-f6cc4dea4e51.png)
- 기존의 scalar operations 에서는 단일 element 에 대해서 gradient 만 계산하면 됐다면, jacobain matrix 를 통해서 input i 번째의 element 의 output  j번째 element 에 대한 gradient 로 local gradient 를 계산한다. local gradient=>jacobian matrix
- scalar 에서는 기존의 edge 에서 gradient 값이 하나였다면, vector 에서는 각각의 element 에 대한 gradient 를 계산한다.
![image](https://user-images.githubusercontent.com/48700102/118359928-7b2fa380-b5c0-11eb-8ac2-2b8068f91476.png)
- 위와 같이 back-propagrion 이 각각의 element 에 대해서 gradient 를 구하는 방식으로 진행이 된다.
- 아마 위와 같은 vector operator 도 결국에는 여러가지 scalar operation 으로 나눌 수 있으므로 변환해서 보면 더 편할 수도 있겠다는 생각이 듬. 
- gradient shape=variable shape 이어야 한다.
<br><br><br>

## Neural Network
![image](https://user-images.githubusercontent.com/48700102/118359945-87b3fc00-b5c0-11eb-8935-e1c925071a85.png)
- 여러개의 layer로 이루어질떄, non-linearity한 속성을 추가하기 위해서 현재 layer 에서 다음 layer 로 전해질떄 activation function 을 추가한다.
- activation function은 non-linear 한 function 이어야 한다.
![image](https://user-images.githubusercontent.com/48700102/118359953-900c3700-b5c0-11eb-8e1a-6bba4b50649a.png)
- 실제로 2-layer neural network 과 sigmoid 함수로 기존의 하나의 linear layer 로 분류하지 못하던 XOR classifier 를 만들 수 있다.

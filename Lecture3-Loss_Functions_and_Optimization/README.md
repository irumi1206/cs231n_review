# Loss Functions and Optimizatoin

## 1. Loss function
![image](https://user-images.githubusercontent.com/48700102/118359750-ee84e580-b5bf-11eb-9120-ed58f3280860.png)
- linear classifier - 이미지를 픽셀단위로 데이터로 저장, 행렬의 곱셈(W행령)으로 각 class 에 해당하는 점수를 계산해서 분류
- linear classifier(W) 에대허서 얼마나 잘 분류하는지에 대한 수치화가 필요함
- loss function: classifier가 얼마나 좋은지에 대해 quantify 함.
![image](https://user-images.githubusercontent.com/48700102/118359763-fb093e00-b5bf-11eb-8ba9-cc599434ad8c.png)
- input data(xi) 에 대해서, classifier 로 얻어진 값과 실제로 나와 되는 값(yi) 의 함수로 loss function 을 정의, 각각의 class 에 대한 loss 의 합. total loss(L) 은 각각의 이미지에 대한 loss 의 평균
<br><br><br>

### Multiclass SVM
![image](https://user-images.githubusercontent.com/48700102/118359596-32c3b600-b5bf-11eb-82cb-1fc4e0572371.png)
- 실제 class에대한 수치가 다른 class들의 수치에 비해 safety margin 보다 더 컸으면 좋겠다는 생각에서 착안. 만약 실제 class 수치에 보다 일정이상 이하면 loss 를 0으로, 그 이상이면 초과한 만큼으로 loss 를 설정함.
- safety margin(1) : absolute value 가 중요하지 않기 때문에(확대될수도 있고 축소될수도 있다), 1이라는 값에 주목하지 않아도 됨. 모델마다 정해짐.
- 만약 W 가 0으로 초기화 되었을떄 Li=class number-1 (debugging stratagy)

### Regularization in loss function
![image](https://user-images.githubusercontent.com/48700102/118359607-3ce5b480-b5bf-11eb-9649-1c306b6eeb89.png)
- 기존의 Loss function 에서는 traingin data 에만 의존했기 때문에, 실제 test data 에서는 잘 맞지 않을 위험이 있다.
- 이러한 overfitting 현상을 막아주기 위해서 loss function 에 regularization 을 해주는 함수를 추가해서 사용
- loss function=data loss+regularization
- 모델에 있어서 너무 complex 한 구조에 대해서 penalty를 부과한다.(dropout 도 regularization 중 하나임)
![image](https://user-images.githubusercontent.com/48700102/118359620-4838e000-b5bf-11eb-95cc-9fdefa13666f.png)
- 실제 w1,w2 가 있을떄, regularization function 에 의해 w1 에 더 많은 penalty를 부과한다.

### Softmax loss function
![image](https://user-images.githubusercontent.com/48700102/118359632-5424a200-b5bf-11eb-8768-d6fd55a87965.png)
- Multiclass SVM loss 에서는 실제 수치에 특별한 의미가 없었지만, Softmax loss 에서는 각각의 class 에 대한 수치에 의미를 부여함.
- e 의 지수승으로 변환한 다음에 각각의 class 에 대한 확률로 치환한, 그리고 올바른 class 에 대한 확률을 -log를 취함.
- 올바른 class 에 대한-log(확률) 의 값을 계산함
- 초기 값이 0이면 softmax loss 는 log(class number) 가 된다 (debugging strategy)

### SVM loss vs Softmax function
![image](https://user-images.githubusercontent.com/48700102/118359643-61419100-b5bf-11eb-9f7e-9e2650d79d50.png)
- SVM loss: safety margin 더 아래에 만 있는거에 관심을 두기 때문에 학습 도중에 그 이하 값으로 내려가면 더 이상 신경을 안씀
- Softmax loss: 다른 값들도 고려해서 확률을 계산하기 때문에 올바른 class 에 대한 점수를 계속 키우고 해당 class 가 아닌 점수는 계속 낮추려고 학습함.

## 2. Optimization
- loss function 이 classifier 가 얼마나 좋은지를 나타내는 척도라면, Optimization은 loss를 줄일 수 있는 W 를 찾는 과정
- loss function 에 관여하는 parameter 를 조정 하면서 가장 작은 loss를 갖는 parameter를 찾으면 됨 (gradient)
![image](https://user-images.githubusercontent.com/48700102/118359674-86ce9a80-b5bf-11eb-89dc-717e8fcfef44.png)
- Numerical gradient: W 의 weight들을 조정하면서 loss 가 얼마나 바뀌는지를 관찰하고 찾아가는 방법 하지만 시간이 너무 오래 걸림
- Analytic gradient: 빠른 방법: 편미분 공식을 이용하면 훨씬 빠르게 계산 가능
-실제로는 Analytic gradient 방법으로 계산을 하면서, Numerical gradient 를 가지고 debugging 을 함.

### Gradient Descent
![image](https://user-images.githubusercontent.com/48700102/118359684-94842000-b5bf-11eb-8a7d-76d1665b68df.png)
- gradient 를 계산한뒤에 parameter들을 gradient 의 반대 방향으로 진행(최솟값을 찾아가는 과정)
- 실제로는 Stochastic gradient descent를 이용함(batch size 별로 gradient descent 를 진행)























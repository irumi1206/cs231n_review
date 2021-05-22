# Training Neural Networks 1
## Activation Functions
- sigmoid : 일종의 뉴런의 활동정도(fire rate)를 나타낸다고 볼 수 있고 output 이 0과 1사이로 나타남, 기울기값이 0에 수렴하는 부분에서 gradient chain rule에 의해 back propagation값이 0으로 수렴하는 문제점이 있음-> 학습이 잘 안됨(saturating gradient), 원점에 대칭이 아니고 항상 값이 양수이기 때문에 모든 weight들을 증가시키거나 감소시키는 방향으로 gradient update가 진행됨 -> 학습이 잘 안됨(zigzag problem) ,exp 계산 자체가 많이 걸림
- tanh : sigmoid 함수가 원점 대칭임, no zigzag problem, 다른 문제들은 여전히 존재
- relu : 입력값이 양수일때 no saturating gradient, 계산이 쉬움, 뉴런의 관점으로 좀더 직관적임, AlexNet에서 사용됨, 평균이 0이아닌 문제점이 존재(zigzag problem), 범위의 반이 결과값이 0이기 떄문에 initialization을 잘못하면 평생 relu 함수가 0을 출력하는 문제점이 있음(dead relu)
- Leaky Relu : 음수 부분에서 0아닌 특정값을 줌, 음수 부분에서 0을 출력하지 않기 때문에 dead relu 문제점이 해결됨
- exponential relu : exp 계산이 많이 걸리, 음수 부분에서 saturating gradient 문제가 존재
- maxout neuron : 두개로 나누고 max를 취하는 기법, no saturating gradient, no dead relu, 학습되어야 하는 weight 가 두배로 많아짐


## Data Preprocessing
- zero centering을 통해서 zigzag과 같은 문제점을 해결할 수 있음 하지만 첫번째 layer에서는 해결할 수 있지만, multi layer로 구성되어 있는경우 후속 layer에서 발생할 문제가 여전히 존재
- 대체로 zero centering은 하지만, normalization,pca,whitening은 안함, image 같은 경우 data 자체가 비슷한 scale로 되어 있기 때문

## Weight Initialization
- random initialization : 작은 네트워크에서는 잘 작동하지만, deep network에서는 잘 작동안함
- Xavier initialization : 수학적으로 맞는 initialization, layer를 따라서 진행할떄, gradient descent가 일어나지 않음
- proper initialization은 아직 진행중인 연구 과제

## Batch Normalization
- batch normalization은 대체로 fully connected layer 앞에, activation function 전에 위치
- batch normalization에서 확장해서, normalize후에 특정 computation을 하도록 지정할 수도 있음, 이떄 computation에 쓰는 변수들을 learnable weight

## Babysitting the Learning Process
- how to monitor deep learning
- 1) checking loss is reasonalbe
- 2) check if training loss converge to small value while training
- 3) start with small regularization, and find the learning rate that makes loss go down
- 4) if loss not going down-> learning rate is too low
- 5) loss exploding-> learning rate is too high

## Hyperparameter Optimization
- cross- validation : evaluating on validation set, measure accurac in test set
- first few epoch to what paramater makes mean in deep learning, than longer running time, fine search
- in cross validation, if certain loss is far less than other loss, it is worrying to use certain model, because it may be due to data.
- network architectrue, learning rate, decay schdule, update type, regularization -> hyper parameters
- if big gap between training accuracy and testing accuracy -> beware of overfitting



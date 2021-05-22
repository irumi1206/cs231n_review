# Training Neural Networks 2
## Fancier optimization
- optimizer의 종류에 따라, landscape을 따라서 gradient descent를 진행할때, 수렴하는 경로가 달라짐
- very slow slope on one way, very high slope on one way -> optimizer에 의해 jittering problem 이 벌어질 수 있다 -> optimizer에 따라서 deep learning의 성능이 좌우됨
- local minima, saddle point problem -> optimizer에 의해 벗어나지 못할 수 있다.
- SGD optimizer -> high computation, many problems
- SGD + momentum -> learning rate 에 편미분값을 바로 안곱하고, 따로 계산뒤 learning rate에 곱해서 계산, converge more quickly, slope 에 따라서 그대로 따라가지 않아서 landscape에서 더 잘 따라간다.
- SGD + momentum에서는 일종의 velocity의 개념으로 gradient descent를 진행
- Nesterov Momentum -> 그전의 속도를 고려해서 optimize함(일종의 관성의 개념이 들어감)
- AdaGrad -> velocity의 개념에서 접근하지 않고, gradient의 제곱값을 추적한 다음에, optimize때 나눠줌, saddel point problen이 여전히 존재
- RMSProp -> gradient 제곱값을 쌓을때 decay 를 곱해서 더해줌(최신 gradient에 가중치를 더 줌)
- Adam -> momentum + AdaGrad + RMSProp (RMS Prop with momentum), 많이 쓰는 optimizer

## Regularization
- 1) regularization term in loss function
- 2) drop out (not on test time!)
- 3) data augmentation(horizontal flips, color jittering

## Transfer Learning
- 이미 학습된 모델이 있고, data에 맞게 추가로 학습시킴

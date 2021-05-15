# Lecture 2 - image classification

## Image classification
- 컴퓨터의 입장에서 이미지는 rgb 의 수치들로 이루어진 데이터일 뿐이라서, 어려운 과제
- 같은 object 라도, 다른 포즈, 빛, 대칭, 확대 등을 고려해 이미지 classfication 을 진행해야 됨
- 특정한 알고리즘이 없음, clear explicit 한 알고리즘이 없어서 어려운 과제
![image](https://user-images.githubusercontent.com/48700102/118358424-a8c51e80-b5b9-11eb-9802-96cc5d7e6a67.png)
<img src="https://user-images.githubusercontent.com/48700102/118358424-a8c51e80-b5b9-11eb-9802-96cc5d7e6a67.png" width="70%">
- 특정한 category 에 대해서 알고리즘을 작성하는 대신 data-driven approach로 접근하는 것이 효율적
<br><br><br>

## Nearest Neighbor
![image](https://user-images.githubusercontent.com/48700102/118358437-b5497700-b5b9-11eb-8775-3eda5e26da83.png)
<img src="https://user-images.githubusercontent.com/48700102/118358437-b5497700-b5b9-11eb-8775-3eda5e26da83.png" width="70%">
- 가장 가까운 이미지를 이용해서 prediction 을 진행함
- 가장 가까운 이미지가 무엇인지에 대한 기준이 필요함 ex) L1 distance, L2 distance
- nearest neighbor classifier : train O(1), predict O(N)
- Neares neighbor 를 통해서 classify 를 진행할때->하나의 distinct 한 자료 때문에 분류 region 이 들쭉날쭉하게 나옴
- smooth 한 영역을 도출하기 위해 K-Nearest neighbor 를 사용함
<br><br><br>

## Hyper parameter
- k-nearest neighbor : parameter k, 그리고 distance function에 따라서 모델이 달라짐
- 최적의 parameter 를 찾아서 학습시켜야함
![image](https://user-images.githubusercontent.com/48700102/118358457-c8f4dd80-b5b9-11eb-959f-c736ac2cf312.png)
<img src="(https://user-images.githubusercontent.com/48700102/118358457-c8f4dd80-b5b9-11eb-959f-c736ac2cf312.png" width="70%">
- train set 에 대해서 학습을 진행을 하고, validation set 에서 최적의 parameter를 알아내고, test set 을 통해서 parameter의 성능을 알아보는 방식으로 training 을 진행하는것이 가장 좋음.
![image](https://user-images.githubusercontent.com/48700102/118358468-d27e4580-b5b9-11eb-9d2b-4e6d394a705a.png)
<img src="https://user-images.githubusercontent.com/48700102/118358468-d27e4580-b5b9-11eb-9d2b-4e6d394a705a.png" width="70%">
- 주로 크기가 작은 dataset에 대해서는 이런식으로 fold로 나눠서 validation set 을 변경해가면서 training 을 하는 경우도 있음
- deep learning 에서 큰 dataset 에 대해서 이런 방식은 거의 안쓰임( 비교적 작은 데이터에 대해서만 쓰임)
- k-nearest neighbor : 이미지에 대해서는 안쓰임( 이미지가 변형 되었을떄 파악하기 쉽지 않고, 차원 에 대해서 지수승으로 필요한 data 가 증가하기 때문에 비효율적임)
<br><br><br>

## Linear Classification
![image](https://user-images.githubusercontent.com/48700102/118358473-e033cb00-b5b9-11eb-88bd-5e14e950df79.png)
<img src="https://user-images.githubusercontent.com/48700102/118358473-e033cb00-b5b9-11eb-88bd-5e14e950df79.png" width="70%">
- 위식을 통해서 이미지와 W 를 정의해서 각각의 class 별로 점수를 구함
- summarize knowledge of image to 10 points per class
-W 와 x 를 가지고 그냥 곱하는 방법 -> linear classifier
![image](https://user-images.githubusercontent.com/48700102/118358476-e88c0600-b5b9-11eb-86ad-85cb9b29253b.png)
<img src="https://user-images.githubusercontent.com/48700102/118358476-e88c0600-b5b9-11eb-86ad-85cb9b29253b.png" width="70%">
- 이미지를 일차원으로 늘여서 행렬로 곱함
- template matching 의 개념을 이해 할 수 있음 각각의 category 에 대한 template matching
- category 별로 한개의 template(row of W) 만 있음
- linear classification 의 한계점 : linear 한 경계만 classify 할 수 있음

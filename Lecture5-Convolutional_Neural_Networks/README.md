# Convolutional Neural Network

## Convolutional Neural Networks
- 실제 이미지는 model 에 input 으로 들어갈때, 일차원의 vector 의 형태로 들어가게 됨 -> data 에서의 spatial structure 를 유지한채 data 를 학습 시키고 싶어함(이미지 픽셀 과 같은 경우 주변 픽셀 값과 어떠한 이미지에 대해서 밀접한 관련이 있기 때문에)
![image](https://user-images.githubusercontent.com/48700102/118361547-f2683600-b5c6-11eb-96d1-d4f3a54f1932.png)
- filter 를 이미지를 따라서 진행하면서 새로운 크기의 data 를 만든다. filter 의 수에 따라서 새로운 data 의 차원수를 조정할 수 있음 ex) 3*32*32->6*28*28 using 6 5*5*3 filter
- 이러한 convolutional layer 를 stacking하면 할수록, 보다 더 high-level feature 에 대해서 학습을 진행함.

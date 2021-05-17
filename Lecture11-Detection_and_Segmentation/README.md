# Detection and Segmentation

## Semantic Segmantation
- Semantic Segmantation : 기존의 image classification에서는 이미지에 대해서 하나의 class로 분류했다면, Semantic segmantation에서는 모든 픽셀에 대해서 class를 분류하고 싶은것
<br>
<img src="https://user-images.githubusercontent.com/48700102/118393673-37e63b00-b67b-11eb-85ac-92eacdbddbf1.png" width="50%">
<br>

- Sliding window : image를 여러개의 crop으로 나눈뒤, 각 crop에 대해서 image classification을 진행하는 방법 -> computational expense, 모든 crop 에 대해서 classification을 진행해야 되기 때문에, 무척 많은 자원이 소비됨, 인접한 픽셀에 대해서는 같은 forward-bakc propagation이 되어서 일일히 할 필요가 없는데, Sliding window에서는 모든 crop에 대해서 진행하기 때문에 매우 낭비다. -> 실질적으로 사용 안함.
<br>
<img src="https://user-images.githubusercontent.com/48700102/118393795-da062300-b67b-11eb-8239-ef893a039138.png" width="50%">
<br>

- Fully Convolutional : gigantic convolutional neural network으로 모든 픽셀에 대해서 진행, output data에서 모든 픽셀에 대해서 classifier가 존재하게 됨 -> very expensive(모든 픽셀에 대한 computation)
- 실제적으로 사용할때는, Fully convolutional 사이에 downsampling 과 upsampling을 lower spatial resolution 계산을 통해서 computation을 줄인다.
<br>
<img src="https://user-images.githubusercontent.com/48700102/118393930-98c24300-b67c-11eb-8748-3ea098368a32.png" width="50%">
<br>

<br>
<img src="https://user-images.githubusercontent.com/48700102/118393950-b5f71180-b67c-11eb-967c-c88e5f8ce030.png" width="50%">
<br>

- Up-sampling의 한 방법 : Un-pooling, Max Unpooling
- Max unpooling할때, 어느 부분에서 Max pooling step이 이루어졌는지 저장하고, Max unpooling때 retrieve하게 된다.
<br>
<img src="https://user-images.githubusercontent.com/48700102/118436073-150b6380-b71b-11eb-8f5c-24b64acbada8.png" width="50%">
<br>

- 학습가능한 up-sampling layer를 만드는 방법 : transpose convolution
- transpose convolution : convolution operation의 반대로 계산하면서 up sampling을 함. 기존의 convolution에서는 filter를 이용해서 dot product를 했다면, de-convolution operation에서는 input data 를 하나의 filter size data로 변환, output data에 덮어씌움.
<br><br><br><br><br>

# Localization
<br>
<img src="https://user-images.githubusercontent.com/48700102/118436649-22751d80-b71c-11eb-9b35-d94505f1a37c.png" width="50%">
<br>

- Localization : image classification과 더불어, image 가 차지하는 부분을 특정함.
- 기존의 image classification task 과 유사하게, 4096-> 4 의 fully connected layer로 마지막 layer를 구성해 x,y,w,h 를 도출하게 함.
<br><br><br><br><br>

# Detection
<br>
<img src="https://user-images.githubusercontent.com/48700102/118437600-e2169f00-b71d-11eb-90b8-66b5de6f27f8.png" width="50%">
<br>

- Detection : image 안에 '여러개'의 물체에 대한 차지하는 부분과 각각의 image classification을 진행
- vs classification + Localization : 하나의 image안에 여러개의 이미지가 들어 있으며, 정확히 몇개가 있는지는 모름
<br>
<img src="https://user-images.githubusercontent.com/48700102/118437669-02def480-b71e-11eb-9932-ffa0cee29dd5.png" width="50%">
<br>

- Sliding Window : window를 이미지에 걸쳐서 진행하면서, crop들을 CNN에 통과, image classification을 진행
- Problem : how to choose crop?, 매우 많은 crop 을 생성해야함
<br>
<img src="https://user-images.githubusercontent.com/48700102/118437837-45a0cc80-b71e-11eb-9bf0-564c1fb149d8.png" width="50%">
<br>

- Region Proposals(traditional vision technique) : blobby image를 찾아서 image가 될법한 범위를 탐색, CNN에 통과
<br>
<img src="https://user-images.githubusercontent.com/48700102/118438770-d75d0980-b71f-11eb-8219-17e7958a1a9b.png" width="50%">
<br>

- R-CNN 논문이 Region Proposal를 이용해서 Detection을 진행. region propasal->image size reconstructoin-> SVM loss+Bbox reg
- R-CNN 문제점 : computationally expensive, slow training, take up alot of disk space
<br>
<img src="https://user-images.githubusercontent.com/48700102/118438809-e5128f00-b71f-11eb-8e0f-70adf183170d.png" width="50%">
<br>

- Fast R-CNN : image 자체에서 crop을 뽑는것이 아닌, image 를 ConvNet을 통과시키고, feature map에서 crop(region proposal)을 진행
<br>
<img src="https://user-images.githubusercontent.com/48700102/118438945-168b5a80-b720-11eb-965a-2f0ef9b86871.png" width="50%">
<br>

- Faster R-CNN : crop을 뽑을때, traditional한 방법이아닌, CNN자체가 proposal을 할 수 있도록 설계
<br><br>
- YOLO/SSD : 하나의 이미지 자체를 regression 모델로 예측, 개별로 추측 안함.
<br><br><br><br><br>











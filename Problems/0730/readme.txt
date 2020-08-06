semantic segmentation에서는 여러가지 resolution의 feature map을 동시에 고려하는 것이 매우 중요합니다. 아래는 MobileNetV2 backbone architecture로부터 여러 종류의 feature map을 동시에 고려하는 segmentation 모델 함수입니다. 함수에 대한 자세한 설명은 아래에 있습니다. 모델 완성을 위해 코드의 “?” 부분에 알맞은 변수명 혹은 숫자를 채워넣어주세요.
- features 에는 64x64, 32x32, 16x16, 8x8, 4x4 resolution의 feature map들이 순서대로 들어가있습니다. 예를 들면, features[2] 는 16x16의 resolution을 가지는 feature map입니다.
- 아래 함수에서는 16x16, 8x8, 4x4 feature map들을 고려합니다. 먼저 3가지 종류의 feature map들을 UpSampling2D 를 이용하여 16x16으로 만들어주고, Concatenate 를 이용하여 합쳐줍니다.
- 그 후, convolutional network를 통과시킨 뒤, 마지막으로 128x128 크기의 output으로 만들어줍니다.
- tf.keras.layers.UpSampling2D(size(?,?), interpolation='biliner'): bilinear operation 을 이용하여 주어진 input(CxHxW)을 H,W에 대하여 ?배 늘린 output을 생성합니다 (C x ?H x ?W)      

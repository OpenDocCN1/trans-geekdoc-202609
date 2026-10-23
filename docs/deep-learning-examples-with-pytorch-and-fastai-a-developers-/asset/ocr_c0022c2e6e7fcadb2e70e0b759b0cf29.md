Layer (type) Output Shape Param # Trainable
================================================
Conv2d 2 x 64 x 180 x 240 9,408 False
BatchNorm2d 2 x 64 x 180 x 240 128 True
ReLU 2 x 64 x 180 x 240 0 False
MaxPool2d 2 x 64 x 90 x 120 0 False
Conv2d 2 x 64 x 90 x 120 36,864 False
BatchNorm2d 2 x 64 x 90 x 120 128 True
ReLU 2 x 64 x 90 x 120 0 False
Conv2d 2 x 64 x 90 x 120 36,864 False
BatchNorm2d 2 x 64 x 90 x 120 128 True
Conv2d 2 x 64 x 90 x 120 36,864 False
BatchNorm2d 2 x 64 x 90 x 120 128 True
ReLU 2 x 64 x 90 x 120 0 False
Conv2d 2 x 64 x 90 x 120 36,864 False
BatchNorm2d 2 x 64 x 90 x 120 128 True
Conv2d 2 x 64 x 90 x 120 36,864 False
BatchNorm2d 2 x 64 x 90 x 120 128 True
ReLU 2 x 64 x 90 x 120 0 False
Conv2d 2 x 64 x 90 x 120 36,864 False
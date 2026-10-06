# Deep Learning Using Keras

Figure 26.

```
from sklearn.model_selection import train_test_split
x_train, x_val, y_train, y_val = train_test_split(x, y, test_size=0.25, shuffle=True, random_state=42)
print(x_train.shape, y_train.shape)
print(x_val.shape, y_val.shape)
print(x_test.shape, y_test.shape)
```

(37500, 32, 32, 3) (37500, 10)
(12500, 32, 32, 3) (12500, 10)
(10000, 32, 32, 3) (10000, 10)

Number of images after splitting of the dataset is given:

Training set= 37500, Validation set= 12500, Testing set= 10000

# PRE-TRAINED MODELS AVAILABLE WITH KERAS API

A model that is trained on a large benchmark dataset to solve a problem similar to the one that we want to solve is known as pre-trained model. It is a common practice to import these pre-trained model that are already trained on very large standard datasets due to the unavailability of computational resources for training a model from scratch that could take days or months to finish training. A list of such pre-trained models based on deep convolutional neural networks (DCNN) available within keras library are listed in Figure 27.

Figure 27. Pre-trained models available in Keras (Chollet, 2015)

+   * Xception
* VGG16
* VGG19
* ResNet, ResNetV2, ResNext
* InceptionV3
* InceptionResNetV2
* MobileNet
* MobileNetV2
* DenseNet
* NASNet
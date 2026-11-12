

![](img/bffdb4a72252285ac92f0fad78a7f104_106_0.png)

Figure 5.23 Three main steps that a volume (input image or a feature map) passes in a CONV layer [8].

![](img/bffdb4a72252285ac92f0fad78a7f104_106_1.png)

Figure 5.24 Visual presentation of the 2D convolution operation [27].

The initial depth of the inputs equals the number of the channels in the image (e.g. three when the images are RGB images). The depth in the deeper CONV layers of the network is the number of filters in the previous layer. In the first step, the number of filters and their kernel sizes are determined each of which is convolved with the input volume and in the second step. One example for convolution operation is illustrated in Figure 5.24. Here, \(W_{j,i}\) is the filter with the kernel size of \(3 \times 3\), where \(j\) and \(i\) are the filter and layer number, respectively. This small window moves over a 2D grid of an image or a feature map from left to right and up to down. The step size according which the window is moving across the image is determined by *stride* step size which is normally either 1 (moving one pixel at a time) or 2 (skip two pixels at a time). In each movement, the elements of the window are multiplied to the corresponding elements of the grid. Convolution operation is completed by summing up these element-wise multiplication values to achieve a scalar value. All the obtained values from convolution result in another 2D grid called feature map/activation map as shown in the third step of Figure 5.23. Once all the \(K\) filters are applied to the input volume, \(K\) 2D activation maps are achieved which are stacked along the depth dimension as the final output volume (illustrated in Figure 5.25).

It should be mentioned that zero-padding is applied along the borders of the input to keep the original image size so that the output volume size matches that of the input (shown in Figure 5.26). Assume I, F, S, and P are the input square image size (one dimension), filter kernel size, stride value, and the amount of zero-padding, respectively. The following equation is required to be integer to have a valid CONV layer:

```
((I – F + 2P)/S) + 1 (5.10)
```

![](img/bffdb4a72252285ac92f0fad78a7f104_107_0.png)

Figure 5.25 Stacking the K activation maps achieved from K filters which forms the input volume for the next layer of the CNN [8].

### Input with zero-padding

| 0 | 0 | 0 | 0 | 0 | 0 | 0 |
|---|---|---|---|---|---|---|
| 0 | 95 | 242 | 186 | 152 | 39 | 0 |
| 0 | 39 | 14 | 220 | 153 | 180 | 0 |
| 0 | 5 | 247 | 212 | 54 | 46 | 0 |
| 0 | 46 | 77 | 133 | 110 | 74 | 0 |
| 0 | 156 | 35 | 74 | 93 | 116 | 0 |
| 0 | 0 | 0 | 0 | 0 | 0 | 0 |

### Kernel

| 692 | -315 | -6 |
|---|---|---|
| -680 | -194 | 305 |
| 153 | -59 | -86 |

### Output of convolution

| -99 | -673 | -130 | -230 | 176 |
|---|---|---|---|---|
| -42 | 692 | -315 | -6 | -482 |
| 312 | -680 | -194 | 305 | 124 |
| 54 | 153 | -59 | -86 | -24 |
| -543 | 167 | -35 | -72 | -297 |

Figure 5.26 Applying zero-padding to the original input before convolution through which the spatial dimensions of the input is preserved and the output volume size matches the original input volume size.

**Activation Layer.** A nonlinear activation function such as ReLU, ELU, etc. (explained in Section 5.7.4) is applied after each CONV layer which aims to make the NN able to perform almost any nonlinear functions. As illustrated in Figure 5.27, the outputs of activation functions (here the ReLU) are new tensors as feature maps.

**Pooling Layer.** In addition to applying the CONV layers with a stride > 1, the size of an input volume can also be reduced by applying POOL layers between two consecutive CONV layers. Pooling can also be useful in handling overfitting. There are two common POOL layers of max pooling and average pooling. Typically, max pooling is applied in the middle of the CNN architecture with the purpose of spatial size reduction while average pooling is common as the final layer of the network to prevent entirely using FC layers. One example of applying max pooling on a sample input with strides of 1 and 2 is illustrated in Figure 5.28.

**Batch Normalization.** Batch normalization was first introduced in [21] which is placed after the activation layers to normalize the activations of the input volume

![](img/bffdb4a72252285ac92f0fad78a7f104_108_0.png)

Figure 5.27 An input going through a ReLU activation through which the negative values are considered as zero and the positive values remain unchanged.

![](img/bffdb4a72252285ac92f0fad78a7f104_108_1.png)

Figure 5.28 Applying a 2 × 2 max pooling filter with strides of 1 and 2 on a sample input [8].

before applying them to the next layer. Giving x as the mini-batch of the activations, its normalized value is computed as follows:

$$\hat{x}_i = \frac{x_i - \mu_\beta}{\sqrt{\sigma_\beta^2 + \varepsilon}}$$ (5.11)

where \(\mu_\beta\) and \(\sigma_\beta^2\) are computed over each mini-batch of \(\beta\) during the training as the mean and variance values, respectively, and \(\varepsilon\) is defined as a very small value. Using batch normalization layer, the mean and standard deviation of the activations are forced to be kept as zero and unit. This layer also reduces the number of the epochs and makes it less dependent on initializing and tuning the parameters carefully.

**Dropout.** The dropout layer, first introduced in [35], is a form of regularization which prevents the model from overfitting by randomly eliminating the neurons in the training by removing the connection between the neurons of one layer and the next layer with the probability of p. This dropping process leads to slightly different networks so that the weights of the networks are tuned by optimizing various forms of the original networks. Figure 5.29 illustrates one example of applying dropout with 50% probability to the network through which half of the connections are removed.

![](img/bffdb4a72252285ac92f0fad78a7f104_109_0.png)

Figure 5.29 Two CNNs with and without applying a dropout layer. Here, half of the connections are removed by applying dropout with the probability of 0.5 or 50% [8].

**Fully Connected Layers.** The last layer we are explaining in this chapter is the FC layers which are named based on the fact that neurons in these layers are fully-connected to all the previous layer’s activations. These layers are always designed as the last layers of the network, never in the middle of the CNN architecture. In each CNN architecture, one or two FC layers are commonly applied which is followed by the softmax classifier to compute the final output probabilities for each class (classification step). An example of Python code for a CNN-based end-to-end classifier is illustrated in Figure 5.30.

```
import numpy as np
from keras.models import Sequential
from keras.layers import Dropout, Dense, Flatten
from keras.optimizers import SGD
from keras.layers.convolutional import Conv2D, MaxPooling2D
from keras.utils import np_utils as u
from keras.datasets import cifar10

model = Sequential()
model.add(Conv2D(32, (3, 3), input_shape=(32, 32, 3), padding='same',
		activation='relu'))
model.add(Dropout(0.2)) # 20% of the nodes are set to 0
# padding='valid' means that the output dimension can
model.add(Conv2D(32, (3, 3), activation='relu', padding='valid'))
model.add(BatchNormalization()) # This works as regularization
model.add(MaxPooling2D(pool_size=(2, 2))) #maxpool with a kernel of 2x2
#In a convolution NN, we need to flatten our data before input it into the output/dense layer
model.add(Flatten())
model.add(Dense(512, activation='relu')) #Dense layer with 512 hidden units
model.add(Dropout(0.3)) #This time we set 30% of the nodes to 0 to minimize overfitting
#Finally the output dense layer with 10 hidden units corresponding to classes
model.add(Dense(10, activation='softmax'))
#Few simple configurations
model.compile(loss='categorical_crossentropy',
	optimizer=SGD(momentum=0.5, decay=0.0004), metrics=['accuracy'])
model.fit(X, y, validation_data=(X_test, y_test), epochs=25,
	batch_size=512)
#Finally print the accuracy of our model!
print("Accuracy: %.2f%% " % (model.evaluate(X_test, y_test)[1]*100))
```

Figure 5.30 Python code for a CNN-based end-to-end classifier.

## 5.6.5 CNNs as Feature Extractors

As explained in the previous section, CNNs are used as end-to-end image classifiers whose input is an image which propagates forward through the network and gives


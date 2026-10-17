
The rest of the paper is organized into four sections. Section 2 describes the feature learning and deep learning. The proposed EM-CNN framework is introduced in Section 3, while Section 4 details the new way of exponential momentum gradient descent method, which yields the highest accuracy compared with homologous parameters momentum updating methods.

Section 5 is the experiment results. Section 6 summarizes the results and draws a general conclusion.

# FEATURE LEARNING

Feature extraction is necessary and useful in the real-world for that the data such as images, videos, and sensor measurement data is usually redundant, highly variable, and complex. Traditional handcrafted feature extraction algorithms are time-consuming and laborious and usually rely on the prior knowledge of certain visual task. In contrast, feature learning allows a machine to both learn at a specific task and learn the features themselves.

Deep learning is part of a broader family of machine learning based on learning representations of data. It attempts to model high-level abstractions in data by using a deep graph with multiple processing layers, composed of multiple linear and nonlinear transformations. Typical deep learning models include autoencoder (AE) \[20\], deep restricted Boltzmann machine (DRBM) \[21\], deep Boltzmann machines (DBM) \[22\], deep belief networks (DBN) \[23\], stacked autoencoder (SAE) \[24\], and deep convolutional neural networks (DCNN) \[25\].

The deep convolution neural network (DCNN), a kind of neural network, is an effective method for feature extraction, which can potentially lead to `本书版权归Arcler所有`

![Image 420](index-102_1.png)

![Image 421](index-102_2.png)

![Image 422](index-102_3.png)

Deep Learning Algorithms

76

progressively more abstract and complex features at higher layers, and the learnt features are generally invariant to most local changes of the input.

#

as object detection \[13–15\], speech simultaneous interpretation \[16\], and

{

depends on the features \[26\], we adopt deep convolution neural network (DCNN) framework.

# STRUCTURE DESIGN OF HYPERSPECTRAL DATA

# CLASSIFICATION FRAMEWORK

In deep convolutional neural network, input data, convolution kernel, and threshold parameter are the three most important issues \[27–29\]. The input

\# ' -

tion performance.

The size of the convolution kernel determines the degree of abstraction of the feature. If convolution kernel size is too small, the effective local

' '

exceed the feature range that convolution kernel can express. Threshold parameter is mainly used to control the degree of response of characteristic submode. Besides, the network depth and dimension of output layer can also $ \* '

The deeper network layers indicate stronger feature expression ability,

\+ #<

of output layer directly determines the convergence speed of network.

When the sample sets are limited, over lower dimension of the output layer cannot guarantee the validity of features, while over higher feature of the output layer will produce feature redundancy.

Since the traditional CNN input the original image directly into the deep

'

\[28, 29\], three images obtained by image data preprocessing are used as performance. In order to obtain better extraction features, the sizes of con-

»»

network is seven according to the results of the experiments.

Besides, the lower sampling applies Max-pooling and the nonlinear mapping function is LREL function, which is shown in the following formula: `本书版权归Arcler所有`

![Image 423](index-103_1.jpg)

![Image 424](index-103_2.jpg)

![Image 425](index-103_3.jpg)

![Image 426](index-103_4.jpg)

![Image 427](index-103_5.png)

![Image 428](index-103_6.png)

![Image 429](index-103_7.png)

¯ <

77

(1)

where ߝ is nonzero small constant and ݓ is the weight of neuron. The setting of ߝ ensures that inactive neurons receive a nonzero gradient value, so that the neuron has the possibility of being activated.

Based on the above analysis, a deep network framework for hyperspectral based on deep convolutional neural network is proposed in Figure 1.

In the proposed deep CNN model, the first layer, the third layer, and the fifth layer are convolution layers, which realized feature extraction from lower level to higher level. The second layer, the fourth layer, and the sixth layer are lower sampling layers, used for feature dimension reduction. The final layer is the output layer which is whole connection layer and output of the final extraction features.

**EXPONENTIAL MOMENTUM GRADIENT**

**DESCENT ALGORITHM**

**Error Transfer**

Error transmission descends by two steps through forward propagation and reverse gradient, to conduct weight generation and adjustment. Using gradient descent method to update weight is shown in formula (2), and bias updating method is shown in formula (3) \[30\]:

(1)

(2)

**Figure 1** # ^~+

本书版权归Arcler所有

![Image 430](index-104_1.jpg)

![Image 431](index-104_2.jpg)

![Image 432](index-104_3.jpg)

![Image 433](index-104_4.png)

![Image 434](index-104_5.jpg)

![Image 435](index-104_6.jpg)

![Image 436](index-104_7.png)

![Image 437](index-104_8.png)

![Image 438](index-104_9.jpg)

![Image 439](index-104_10.png)

![Image 440](index-104_11.png)

![Image 441](index-104_12.jpg)

![Image 442](index-104_13.jpg)

![Image 443](index-104_14.png)

![Image 444](index-104_15.png)

![Image 445](index-104_16.png)

Deep Learning Algorithms

78

In the formula, ߟ is the learning rate,

is the gradient of error to weight, and

is the gradient of error to bias, namely, the sensitivity of parameter adjustment. In order to achieve weight and bias optimizing, the gradient of error to weight and the gradient of error to bias must be first obtained.

For convolution layer, its output is shown as the following formula: (3)

where ܾ is the bias of ݆ is the block of in-

݆

݆

put feature diagram, and

is convolution kernel. According to derivation formula of sensitivity function, the sensitivity of convolution layer can be represented by the following formula:

(4)

where

is the convolution kernel of ݈+1 sampling layer, up represents upper sampling, and

is 1/4 of

, so upper sampling should be

conducted.لsymbol represents the multiplication of corresponding elements Thus, the gradient of convolution layer error to bias is shown in formula (6). In the formula, (ݑ, V) is the element location of sensitivity matrix: (5)

The gradient of convolution layer error to weight is shown in formula (7). In the formula,

is the convolution block of

and convolution kernel ܭ݆݅,

(ݑ, V) is the element location of the block:

(6)

Substitute formula (5), (6) into formula (1), (2) and obtain the updated value of convolution layer’s weight.

The output of sampling layer’s neural network can be expressed by formula (8), in which

, respectively, represent multiplicative bias

and additive bias. Multiplicative bias is generally set as 1: `本书版权归Arcler所有`

![Image 446](index-105_1.jpg)

![Image 447](index-105_2.jpg)

![Image 448](index-105_3.jpg)

![Image 449](index-105_4.png)

![Image 450](index-105_5.png)

![Image 451](index-105_6.png)

¯ <

79

(7)

According to the sensitivity of calculating formula of gradient descent, the sensitivity of sampling layer obtained is shown as the following formula: (8)

Whereby the bias updating formula of sampling layer can be obtained, as is shown in formula (10). According to formula (3), bias value updating can be obtained:

(9)

**Exponential Momentum Training Algorithm**

The traditional gradient descent method only transmits gradient error between single layers, which lead to slow convergence rate of the network.

Increasing the learning rate ߟ is a good way to improve the convergence speed.

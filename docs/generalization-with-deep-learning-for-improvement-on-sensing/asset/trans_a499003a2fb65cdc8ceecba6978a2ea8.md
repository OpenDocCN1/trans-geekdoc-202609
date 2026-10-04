

Proposed in 2012, `AlexNet` carried forward the ideas of `LeNet` and was the first large-scale CNN architecture [[26](#chap1.xhtml#fsr26)]. It achieved ground breaking results for image classification and recognition tasks and won the ImageNet Large Scale Visual Recognition Challenge (ILSVRC) in 2012. As shown in [Fig. 7](#chap1.xhtml#fig7), `AlexNet` has eight layers, comprising five convolutional layers and three fully connected layers. In addition, the first, second and fifth convolutional layers are followed by max pooling layers. `AlexNet` adopts GPUs for computing acceleration. Moreover, it successfully leverages `ReLU` activation function, `dropout`, as well as local response normalization (`LRN`) in CNN for the first time. More specifically, `ReLU` activation function is used to improve the convergence rate by alleviating the gradient vanishing problem in deep networks. `Dropout` is proposed to avoid overfitting through ignoring some neurons randomly during training. Finally, `LRN` is introduced to enhance the generalization capability of the model via simulating the lateral inhibition mechanism. Its function is very similar to normalization. Therefore, `LRN` has become deprecated since the introduction of `Batch Normalization` [[50](#chap1.xhtml#fsr50)]. The success of `AlexNet` starts the era of CNNs and triggers the deep learning boom.

### 2.3.3 Visual Geometry Group

The VGG network architecture was introduced by the Visual Geometry Group (VGG) in 2014 [[27](#chap1.xhtml#fsr27)]. In their paper, a series of VGG models were presented, including `VGG-11`, `VGG-13`, `VGG-16` and `VGG-19`. As illustrated in [Fig. 8](#chap1.xhtml#fig8), `VGG-11`, `VGG-13`, `VGG-16` and `VGG-19` contain 11, 13, 16 and 19 layers, respectively, and all VGG models end the same with three fully connected layers. VGG proves that increasing the depth of a network is critical for performance improvement in CNNs. In addition, VGG removes the `LRN` layer since its effect in deep CNNs is not obvious. Also, it uses 3 × 3 convolution kernels instead of 5 × 5 ones because a stack of smaller kernels can achieve the same receptive field, while leading to more nonlinear variations and reduced number of parameters.

![figure](images/p15-1.jpg)

**Figure 8:**Architecture of VGG models. Figure is retrieved from Ref. [[27](#chap1.xhtml#fsr27)].

### 2.3.4 GoogLeNet

Also introduced in 2014, `GoogLeNet` was the first large-scale CNN created by incorporating inception modules [[28](#chap1.xhtml#fsr28)]. The main objective of the `GoogLeNet` architecture was to reduce computation complexity and, in the meantime, achieve high accuracy. The basic structure of the inception block is depicted in [Fig. 9](#chap1.xhtml#fig9). It constructs a “wide” network through deploying convolution kernels of different sizes to capture spatial information at different scales. The obtained feature maps are then stacked to yield a more representative one. It is worth mentioning that 1 × 1 convolution kernel is used in `GoogLeNet` for dimensionality reduction before computationally expensive layers. Moreover, it uses an average pooling layer instead of a fully connected layer before the classifier to reduce the density of connection. These tunings result in a significant decrease in the number of parameters. Although `GoogLeNet` is 22 layers deep even without counting the pooling layers, it has much less parameters compared to the predecessors.

### 2.3.5 ResNet

`ResNet`, which was proposed in 2015, revolutionized the development of CNN architectures by introducing the concept of residual learning [[29](#chap1.xhtml#fsr29)]. In theory, deep networks outperform shallow ones since they can better extract features. Nevertheless, with the increase of layers, deep networks are prone to gradient vanishing or exploding problems. In order to address these problems, `ResNet` exploits the residual blocks constructed by shortcut connections, as shown in [Fig. 10](#chap1.xhtml#fig10). The mathematical definition of a residual building block can be expressed as

![figure](images/p16-1.jpg)

**Figure 9:**Inception module. Figure is retrieved from Ref. [[28](#chap1.xhtml#fsr28)].

![figure](images/p17-1.jpg)

**Figure 10:**A residual block. Figure is retrieved from Ref. [[29](#chap1.xhtml#fsr29)].

![figure](images/p17-2.png)

where `x` and `y` are the input and output vectors of the considered layers, respectively, and function represents the residual mapping to be learned. The parameter-free shortcut connections enable cross-layer connectivity and speed up the convergence of deep networks. `ResNet` was developed with many versions, including `ResNet-34`, `ResNet-50`, `ResNet-101` and `ResNet-152`. Although `ResNet` is much deeper than `AlexNet` and `VGG`, it shows less computational complexity than previous networks.

### 2.3.6 DenseNet

Similar to `ResNet`, `DenseNet` was proposed in 2017 to solve the gradient vanishing problem through cross-layer connectivity as well [[30](#chap1.xhtml#fsr30)]. It consists of densely connected CNN layers and connects the outputs of each layer with all successor layers in a dense block. The conceptual diagram of a dense block is illustrated in [Fig. 11](#chap1.xhtml#fig11). The `l`\-th layer receives the features maps of all preceding layers as its input:

![figure](images/p17-3.png)

where `[x[0],x[1], …, x[l−1]]` represents the concatenation of previous features maps and `H[l]` is a composite function which performs three consecutive operations, i.e., batch normalization, `ReLU` activation and a 3 × 3 convolution. The dense blocks allow `DenseNet` to reuse features efficiently throughout the networks and substantially reduce the number of network parameters.

![figure](images/p18-1.jpg)

**Figure 11:**A dense block. Figure is retrieved from Ref. [[30](#chap1.xhtml#fsr30)].

#### 2.4 Recurrent neural networks

##### 2.4.1 Introduction

Traditional neural network approaches such as multi-layer perceptron networks (`MLP`) and CNNs are incapable of dealing with the *sequential* data that have time-varying input patterns and unfixed sequential length. In 1982, John Joseph Hopfield introduced [[23](#chap1.xhtml#fsr23)] a new neural network, namely recurrent neural network (`RNN`), to handle data with sequential structure. The RNNs are typical sequential learning models which allow previous outputs to be used as inputs while having hidden states.

The pictorial representation of a basic RNN is shown in [Fig. 12](#chap1.xhtml#fig12), where the left part of the figure represents an unfolded network, while the right part of the figure represents a folded sequence network at time step `t − 1`, `t` and `t + 1`. A sequence of training data, i.e., `x[0]`, `x[1]`…, `x[t−1]`, `x[t]`, `x[t+1]`,…, are given as inputs of the network, while `0[0]`, `0[1]`…, `0[t−1]`, `0[t]`, `0[t+1]`,… denote the calculated output of the network. `h[0]`,…, `h[t]` are the hidden units, which are regarded as the “memory” of the network. As shown in [Fig. 12](#chap1.xhtml#fig12), the current time information `x[t]` and the previous hidden output `h[t−1]` are used as the inputs to update the current hidden output `h[t]`. Formally, it can be defined as

![figure](images/p19-1.jpg)

**Figure 12:**An abstract structure of an RNN.

![figure](images/p19-2.png)

where `b` is the bias vector, `U` and `W` are weight matrices used to condition the input `x[t]` and previous hidden state `h[t−1]`, respectively. `f()` denotes the nonlinear activation function such as tan `h`, `ReLU` or Leaky `ReLU`.

Ideally, the hidden state `h[t]` could preserve the useful information of all previous time steps. The output at time step `t` is computed based on `h[t]` and the corresponding weight matrix `V`

![figure](images/p19-3.png)

where `g()` is softmax function for a classification task. Unlike `MLP` that uses different parameters at each layer, `RNN` shares the parameters (`W`, `U`, `V`) across time.


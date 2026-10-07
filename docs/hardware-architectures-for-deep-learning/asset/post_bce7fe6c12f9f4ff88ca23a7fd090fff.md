# Hardware architectures for deep learning

![](img/e6e752b99eb1621488c89445a57e2a86_43_0.png)

Figure 1.19 Diagram of some stacked RBM part. The new network can be trained in a supervised manner for a classification or regression problem. Such a learning procedure can be utilized for stacked RBMs, too. However, to train RBMs, each RBM should be trained independently from the previously trained RBMs. Then, after a sufficient number of stacked RBMs, they can be added to a partitioning or mapping map for classification or regression problems, respectively.

Deep-belief NNs are one of the most widely used examples of ANNs which use autoencoders or stacked RBMs for classification or regression problems [13].

## 1.3.2.3 Convolutional neural networks

In many challenging classification and regression problems, particularly in classifying different categories of images and speech signals, there are different sources of disturbance and distortions in input patterns. To have a successful classification or regression in such cases, the deeper networks with hidden layers are required. Actually, the adding layers in the networks should act as a nonlinear filter, which can remove all disturbances and distortions from input patterns. Convolutional networks (CNNs) are successful networks that have been developed to achieve this goal [14,15]. Actually, CNNs by presenting a sufficient number of convolutional layers allow passing frequent patterns from small to large kernel sizes. In this model, each layer, by considering some shared-weight filters and applying "ReLU" activation functions, make new features from feature maps of the preceding layer. In addition to convolution layers, CNNs use pooling layers to reduce the size of feature maps. The role of pooling layers is to remove different distortions from input patterns and provide more scaled feature space with a sufficiently low dimension. Actually, a pooling layer subsamples the feature maps. In CNNs, the number of convolutional or pooling layers may exceed 100 layers. Figure 1.20 shows a diagram of a CNN including one convolutional, one pooling, and two fully connected layers.

To learn CNNs, the error backpropagation method is used. To have successful training and generalization, some learning tricks and technique, such as using stochastic mini-batch gradient approach, batch normalization, and drop out, are utilized.

**Figure 1.20** Diagram of a CNN including convolutional, pooling, and fully connected layer:
Input signal (x) -> Filters -> Convolution -> Feature maps -> Max-pooling -> Pooled maps -> Fully connected layers -> Partitioning/mapping -> Output.

## 1.3.2.4 Recurrent neural networks

In some applications, such as language modeling, word prediction, speech recognition, translation machines, and time series prediction, the sequence at which the input patterns are received is important and should be considered to solve the problem. For such applications, a memory is implemented in the NN by adding some layers and also modifying the direction of the flow inside the network. These modifications led to the emergence of RNNs. Actually, a nonlinear difference equation is trained on a RNN that can convey the effects of related patterns in the output.

RNNs and their hardware implementation issues will be introduced in more detail in Chapter 2.

The classic RNN models, however, suffer from the problem of vanishing gradients, cannot keep long-term memory [16]. To address this issue, the long short-term memory (LSTM) models is designed to convey effective information from previous steps by (1) providing an information belt within recurrent units and (2) adding some special gates to the model [16]. Gated recurrent unit (GRU) is another successful network that implements the LSTM functionality with less number of gates [17]. Figure 1.21 shows the diagrams of the (a) classic RNN, (b) LSTM, and (c) GRU units.

As shown in Figure 1.21(a), in a simple RNN module, the input and the former outputs of the module are concatenated to generate the outputs of the module. For the other two models, as shown in Figure 1.21(b) and (c), the network structure is more complex, containing more interconnected layers and switching gates. Such complex structures allow establishing long-term dependency between former inputs and the current output. To learn the RNN, the network should be unfolded in time to get an equivalent feedforward RNN. Error backpropagation through time (BPTT) is the most widely used training method for RNNs [18].

![](img/e6e752b99eb1621488c89445a57e2a86_45_0.png)

Figure 1.21 Diagrams of (a) classic RNN, (b) LSTM, and (c) GRU modules.

## 1.4 Convolutional neural networks

CNNs, as the heart of many image and speech processing applications, have attracted considerable attention in recent years. This model can filter various disturbances and reduce distortions by applying a sequence of convolutional and pooling layers.

In many real-world situations, the effective features are a highly nonlinear transformation from their original unique form. For example, in classification of objects in an optic image, the effective features of objects (e.g., cars and trees) have different sizes, colors, textures, positions, and perspectives. In addition, different backgrounds, colors, textures, irrelevant objects, and different intensities of the light make the problem even more difficult. These disturbances and distortions make the patterns of cars and trees absolutely nonseparable in the vector space. To address this issue, the convolutional and pooling layers of CNNs perform a sequence of filtering and scaling tasks on effective features. Eventually, a new space of features formed in which the vectors of different objects (cars and trees) are separable and using one or two dense layers (fully connected layers), the feature space is partitioned (or mapped) and the desired labels (target map) are revealed in a classification (or regression) problem.

In the following sections, we briefly explain the structure of convolutional and pooling layers and introduce some CNN implementations.

### 1.4.1 Convolution layers

Convolution in CNN is a variant of convolution operation in LTI systems. Here, the convolution of the input signal (x) through a filter with parameters (w, b) is defined as follows:

$z = f(x * w + b)$

where $b$ denotes the filter bias, $w$ denotes the main parameter of the filter, and $f$ denotes a activation function such as ReLU. Actually, after appropriate learning on the filters, such operation can amply relevant patches and remove nonrelevant ones. By repeating the procedure on a set of patches on the initial signal, a feature map is extracted.

CNNs select patches by switching between dimensions of the size by a certain step (stride) and putting the generated units in a position corresponding to the initial position of the patch. Figure 1.22 shows the diagrams of a convolution operation on a $6 * 6$ 2D signal by a $3 * 3$ filter with the stride of 1. Figure 1.23 shows how the set of patches is chosen by switching on the wheel.

By defining filters in a convolutional layer, more feature maps are extracted from the input. Figure 1.24 shows how a 2D $a * b$ input signal is convolved by four, $c * 1$ filters to generate four $(a - c + 1) * (b - l + 1)$ feature maps (stride=1).

This 2D convolution operation can be generalized to signals with different dimensions: one-dimensional signals such as time series or three-dimensional signals such as colored images or multichannel images.

| x (Chosen Patch) | w (Filter Window) | z (unit in Feature Map) |
|---|---|---|
| 1 | -1 | | 7.5 |
| 0 | -1 | 2 | 3 | -9 |
| | | 0 | 5 | 0 |
| 1 | 2 | | |
| | | 0 | 6 | |
| 0 | 1 | 1 | 0.5 bias |

```
$c*l=(3*3)
Feature Map
(a-c+1)*(b-l+1)=4*4
z=Relu(1*2+0*3+(-1)*4+...1*6+0*5)
```

Figure 1.22 Diagrams of convolution through a 3*3 filter on a 6*6 signal by stride 1


## 1.2 Convolution

Equation 1.2 shows how the result Y of a convolution with kernel K on input X is computed in dimension two (x and y are pixel coordinates). In this equation, Y and K are 2-dimensional matrices of real-valued numbers.

$$Y(x,y) = (X * K)(x,y) = \sum_{i} \sum_{j} X(x - i, y - j) \times K(i,j) \quad (1.2)$$

Because of the nature of the convolution, one CNN layer is composed of neurons with edges that are massively shared with the input: it can be assimilated to a small densely connected neural layer that performs the whole input locally (i.e. with connections to input restricted to a neighborhood of neurons). Generally, CNN layers are combined with non-linear activation functions and pooling operators. The convolution can be performed every Nth step in x and y dimensions: this is usually called the stride. The output of a convolution involving strides is described in equation 1.3, where $s_x$ and $s_y$ are the stride values in each dimension.

$$Y(x,y) = (X * K)(x,y) = \sum_{i} \sum_{j} X(x \times s_x - i, y \times s_y - j) \times K(i,j) \quad (1.3)$$

A convolution can be performed keeping the valid portion of the output, meaning that only the values of Y that are computed from every value of K over X are kept. In this case, the resulting output has a lower size than the input. It can also be performed over a padded input: zeros are added all around the input so that the output is computed at each location, even where the kernel doesn’t lay entirely inside the input. This is generally used to keep the input size through the convolution. However, the borders of the output are affected by the zeros of the padding. Figure 1.2 shows how the stride and padding of the convolution affect the output size (the number of rows and columns of the resulting image) and the physical spacing (the physical size of the output pixel).

![](img/f70619500c7a30b0babf83918d56ad93_18_0.png)

**FIGURE 1.2**  
Left: no padding, stride=2, **Center:** padding, stride=2, **Right:** padding, stride=1. The output is the upper white matrix, and the input is the blue matrix at the bottom. The output **size** depends on the following parameters of the convolution: padding, kernel size, and stride. The output **physical spacing** is changed accordingly to the stride in the convolution: *n* strides ensure that physical spacing is scaled by *n*.

> **Important note**
>
> - Non-unitary strides modify the output physical spacing.
> - Without padding, the output size is changed, depending on the kernel size.
> - With padding, the output size can be kept (same as the input, if no stride) but values at the border might be contaminated by the zero padding.

## 1.3 Pooling

Another important concept of CNNs is pooling, which is a form of non-linear downsampling. Several non-linear functions can be implemented in pooling operations, among which max pooling is the most common: it partitions the input image and for each sub-region, outputs the maximum value (see Figure 1.3). The intuition is that the exact location of a feature is less important than its rough location relative to other features. The pooling layer aims to progressively reduce the spatial size of the representation, to reduce the number of parameters and amount of computation in the network, and hence to also control overfitting. It is common to periodically insert a pooling layer between successive convolutional layers in a CNN architecture. The pooling operation provides another form of translation invariance. The pooling layer operates independently on every depth slice of the input and resizes it spatially. Like convolution with non-unitary stride, the pooling operators also modify the output size.

![](img/f70619500c7a30b0babf83918d56ad93_19_0.png)

**FIGURE 1.3**  
2 × 2 max pooling with stride 2. In each 2 × 2 sub-region of the image, the maximum value is kept.

> **Important note**
> Pooling, and convolutions with stride, can be viewed as a subsampling process, which does modify the output size, and the output physical spacing. Depending on the implementation, it can also keep partially sampled items at borders.

## 1.4 Activation functions

Inspired from biology, the activation functions are usually an abstraction representing the way a neuron will be activated (i.e. it will transmit its output value) or not. Basically, the activation functions control the amount of what is actually transmitted to output. There are many activation functions used in deep learning. Among these, we can enumerate the following, which are common ones we will use during this tutorial:

- 1. The rectified linear unit returns a maximum value between 0 and x:

  $$f(x) = max(0, x)$$
- 2. A leaky rectified linear unit allows a small, positive gradient when the unit is not active. It is parametrized with α, a scalar value:

  $$f(x) = \begin{cases} x & \text{if } x > 0, \\ \alpha x & \text{otherwise,} \end{cases}$$
- 3. Sigmoid:

  $$f(x) = \frac{1}{1 + e^{-x}}$$
- 4. Hyperbolic tangent (Tanh), which is a shift-scaled sigmoid ($\tanh(x) = 2 \times \operatorname{sigmoid}(2x) - 1$):

  $$f(x) = \frac{e^x - e^{-x}}{e^x + e^{-x}}$$

## 1.5 Challenges ahead for deep learning with remote sensing images

There are still challenges remaining ahead to process real-world remote sensing images with deep learning. One crucial point is software implementation. Entering into deep learning requires familiarity with a framework. Implementing new methods requires an extensive programming background and deep learning knowledge. The tools must scale enough to the huge size of real-world remote sensing images and datasets. In particular, the image size problem is out of deep learning frameworks' scope. In computer vision, popular problems and datasets are often related to small-sized and true-color images. Many deep learning architectures must be redesigned to suit remote sensing images. Another point is that algorithms presented in the literature often serve one unique purpose and each new algorithm implementation requires new effort and expertise to be applied on standardized geospatial data. Additionally, recent studies have pointed out that using the features computed with deep nets in machine learning algorithms like Support Vector Machines or Random Forests, offers great opportunities. However, even if most remote sensing image processing software implement a machine learning framework with such algorithms, only a few of them enable the combination of deep learning algorithms with those already implemented well-known machine learning algorithms.

In the next section, we introduce the software that leverages all these issues.

### 2.1.1 Applications

The Orfeo ToolBox applications aim to provide users a number of implemented algorithms. These applications can be used directly through multiple interfaces like command line, graphical user interface, and third-party software like QGIS for instance. For developers, applications can also be used from Python and C++ APIs. Each OTB application comes with a set of parameters. Parameters used in OTB applications are typed (images, vector data, file, folder, integer, floating, etc.) and this formalism makes the OTB applications usable through all interfaces and APIs.

### 2.1.2 Streaming mechanism

The streaming mechanism enables the processing of images several times on different regions. Instead of working on the entire data, which would require a lot of memory, blocks are processed one by one until the output data is produced. This mechanism preserves the memory footprint and enables the processing of very large data. Most of the algorithms implemented in OTB applications and C++ classes support this mechanism. The few algorithms that don’t implement the streaming mechanism require that all input and output data are stored in memory at execution.

### 2.1.3 Remote modules

For developers, OTB eases the integration and the deployment of new features thanks to the external modules. This mechanism enables you to standardize the development of components external to the library, such as a new OTB application. Remote modules allow anyone to extend the functionalities of OTB without being part of the core project repository. Remote modules can have different licenses than the main OTB repository. For instance, the OTBTF remote module that we will use in this tutorial, implements deep learning using the TensorFlow library. It is not in the core of the official OTB library, but provides applications that can be used as any other using the OTB application API.

### 2.1.4 The Python API

The Python API of the Orfeo ToolBox enables you to build pipelines using in-memory connection of existing OTB applications. The resulting pipeline still enforces the streaming mechanism. Another useful feature is the ability of using Numpy arrays in pipelines, as input or output of the OTB applications. The Python API is really great to build complex pipelines with already existing algorithmic blocks like the OTB applications (including the applications from remote modules). This book targets user-oriented interactions with OTB applications, and Python bindings are partially introduced in section 16.3.

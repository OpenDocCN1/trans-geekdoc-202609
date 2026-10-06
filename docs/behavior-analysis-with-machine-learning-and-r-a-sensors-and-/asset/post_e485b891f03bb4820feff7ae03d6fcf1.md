
# CHAPTER 8. PREDICTING BEHAVIOR WITH DEEP LEARNING

classification tasks but can also be used for regression and time series data. If we wanted to perform image classification with a traditional neural network, first we would need to either build a feature vector by:

- 1. extracting features from the image or,
- 2. flattening the image pixels into a 1D array.

The first solution requires a lot of image processing expertise and domain knowledge. Extracting features from images is not a trivial task and requires a lot of preprocessing to reduce noise, artifacts, segment the objects of interest, remove background, etc. Additionally, considerable effort is spent on feature engineering. The drawback of the second solution is that spatial information is lost, that is, the relationship between neighboring pixels. CNNs solve the two previous problems by automatically extracting features while preserving spatial information. As opposed to traditional networks, CNNs can take input n-dimensional images and process them efficiently. The main building blocks of a CNN are:

- 1. Convolution layers
- 2. Pooling operations
- 3. Traditional fully connected layers

Figure 8.26 shows a simple CNN and its basic components. First, the image goes through a convolution layer with 4 kernels (details about the convolution operation are described below). This layer is in charge of extracting features by applying the kernels on top of the image. The result of this operation is a convoluted image, also known as feature maps. The number of feature maps is equal to the number of kernels, in this case. Then, a pooling operation is applied on top of the feature maps. This operation reduces the size of the feature maps by downsampling them (details on below). The output of the pooling operation is a set of feature maps with reduced size. Here, the outputs are 4 reduced feature maps when the pooling operation is applied to each feature map independently of the others. Then, the feature maps are flattened into a one-dimensional array. Conceptually, this array represents all the features extracted from the previous steps. These features are then used as inputs to a neural network with its respective input, hidden, and output layers. *and underlined text means that parameter learning occurs in layer. For example, in the convolution layer, the parameters of the kernels need to be learned. On the other hand, the pooling operation does not require parameter learning since it is a fixed operation. Finally, the parameters of the neural network are learned too, including the hidden layers and the output layer.

One can build more complex CNNs by stacking more convolution layers and pooling operations. By doing so, the level of abstraction increases. For example, the first convolution

![](img/91c149cc24c3e5af2971580c9dda9d8b_286_0.png)

Figure 8.26: Simple CNN architecture. An '*' indicates where parameter learning occurs.

extracts simple features like horizontal, vertical, diagonal lines, etc. The next convolution could extract more complex features like squares, triangles, and so on. The parameter learning of all layers (including the convolution layers) occurs during the same forward and backpropagation step just as with a neural network. Both, the features and classification task are learned at the same time! During learning, batches of images are forward propagated and the parameters are adjusted accordingly to minimize the error (for example, the average cross-entropy for classification). The same methods for training neural networks are used for CNNs, for example, stochastic gradient descent.

> Each kernel in a convolution layer can have an associated bias which is also a parameter to be learned. By default Keras uses a bias for each kernel. Furthermore, an activation function can be applied to the outputs of the convolution layer. This is applied element-wise. ReLU is the most common one.

At inference, the convolution layers and pooling operations act as feature extractors by generating feature maps that are ultimately flattened and passed to a normal neural network. It is also common to use the first layers as feature extractors and then replace the neural network with another model (Random Forest, SVM, etc.). In the following sections, details about the convolution and pooling operations are presented.

## 8.6.1 Convolutions

Convolutions are used to automatically extract feature maps from images. A convolution operation consists of a kernel also known as a filter which is a matrix with real values. Kernels are usually much smaller than the original image. For example, for a grayscale image of height and width of 100x100 a typical kernel size would be 3x3. The size of the kernel is a hyperparameter. The convolution operation consists of applying the kernel over

![](img/91c149cc24c3e5af2971580c9dda9d8b_287_0.png)

| Kernel (3x3) | 1 | 1 | 1 | | 1 | 1 | 1 | | 1 | 3 | 1 |
|---|---|---|---|---|---|---|---|---|---|---|---|
| | 0 | 0 | 0 | | 0 | 0 | 0 | | 0 | 0 | 0 |
| | 0 | 0 | 0 | | 0 | 0 | 0 | | 0 | 0 | 0 |

| Original image (5x5) | 0 | 0 | 1 | 1 | | 0 | 0 | 0 | 1 | | 0 | 0 | 0 | 1 | | 0 | 1 | 0 | 0 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| | 0 | 0 | 1 | 0 | | 0 | 0 | 1 | 0 | | 0 | 0 | 1 | 0 | | 0 | 1 | 0 | 0 |
| | 1 | 0 | 0 | 0 | | 1 | 0 | 0 | 0 | | 1 | 0 | 0 | 0 | | 1 | 0 | 0 | 0 |

| Feature map (3x3) | | | | | | | | | |
|---|---|---|---|---|---|---|---|---|
| | | 0 | 1 | |
| | | 1 | 1 | |

Figure 8.27: Convolution operation with a kernel of size 3x3 and stride=1. Iterations 1, 2 and 9, starting at the upper left corner and moving forward by row until reaching the bottom right. The stride controls how many elements the kernel is moved at a time and this is also a hyperparameter. A typical value for the stride is 1. The operation computes the sum of the element-wise product between the kernel and the image region it covering. The output of this operation is used to generate convolved image (feature map). Figure 8.27 shows the first two iterations and the final iteration of the convolution operation on an image. In this case, the kernel is a 3x3 matrix with 1s in its first row and 0 elsewhere. The original image has a size of 5x5x1 (height, width, depth) and it seems to have 7 in it. In the first iteration, the kernel is aligned with the upper left corner of the original image. An element-wise multiplication is performed and the results are summed. The operation is shown at the top of the figure. In the first iteration, the result was 3 and it is set at the corresponding position of the convolved image. In the next iteration, the kernel is moved one position to the right and the final result is 3 which is set in the next position. The process continues until the kernel reaches the bottom right. At the last iteration (9), the result is 1. Now the convolved image (feature map) represents the features extracted by this particular kernel. Note, the feature map is a 3x3 matrix which is smaller than the original image. It is also possible to force the feature map to have the same size as the original image by padding it with zeros. Before learning starts, the kernel values are initialized at random. In this example, the kernel has 1s in the first row and 3x3 = 9 parameters. This makes CNNs so efficient since the same kernel is applied to the entire image. This is known as 'parameter sharing'.

| Original image (5x5x1) | 4 kernels of size 3x3 | 4 feature maps of size 3x3 |
|---|---|---|
| 1 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 0 | 1 | 1 | 1 | 2 | 2 | 2 |
| 0 | 0 | 1 | 0 | 0 | 0 | 1 | 2 | 2 |
| 0 | 1 | 0 | 0 | 1 | 0 | 1 | 3 | 3 |
| 1 | 0 | 0 | 0 | 0 | 1 | 3 | 1 | 1 |

Figure 8.28: A convolution with 4 kernels. The output is 4 feature maps.

Our kernel has 1s at the top and zeroes elsewhere so it seems this kernel learned to detect horizontal lines. If we look at the final output image we see that the horizontal lines were emphasized by this kernel. This would be a good kernel to differentiate between 7s and 0s, for example. 0s does not have long horizontal lines. But maybe it will have difficulties discriminating between 7s and 5s since both have horizontal lines at the top. In this example, only 1 kernel was used in practice, but you may want to have more kernels, each in charge of identifying the best features for the given problem. For example, another kernel could learn to identify diagonal which would be useful to differentiate between 7s and 5s. The number of kernels per layer is a hyperparameter. In the previous example, we could have defined to have 4 kernels instead of one. In that case, the output of that layer would have been 4 feature maps of size 3x3 each (Figure 8.28).

What would be the output of a convolution with 4 kernels of size 3x3 if it is applied to an RGB color image of size 5x5x3? In that case, the output will be the same (4 feature maps of size 3x3) as if image were grayscale (5x5x1). Remember that the number of output feature maps equals the depth of the image. In this case, each kernel will have a depth of 3. Each depth is applied independently of the corresponding R, G, and B channels. Thus, each kernel has 3x27 parameters that need to be learned. After applying each kernel to each image channel (in this example, 3 channels), the results of each channel are added and this is why we end up with one feature map per kernel. The following course website has a nice interactive animation of how convolutions are applied to an image with 3 channels: https://cs231n.github.io/convolutional-networks/. In the next section (CNNs with Keras), a couple of examples demonstrate how to calculate the number of parameters and the outputs' shape will be presented as well.

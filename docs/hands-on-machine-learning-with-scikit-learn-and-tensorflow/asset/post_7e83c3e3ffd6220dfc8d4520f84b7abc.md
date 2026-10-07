
# LeNet-5

The LeNet-5 architecture¹⁰ is perhaps the most widely known CNN architecture. As mentioned earlier, it was created by Yann LeCun in 1998 and widely used for handwritten digit recognition (MNIST). It is composed of the layers shown in Table 14-1.

Table 14-1. LeNet-5 architecture

| Layer | Type | Maps | Kernel size | Stride | Activation |
| --- | --- | --- | --- | --- | --- |
| Out | Fully Connected | | 10 | | | RBF |
| F6 | Fully Connected | | 84 | | | tanh |
| C5 | Convolution | 120 | 1 × 1 | 5 × 5 | tanh |
| S4 | Avg Pooling | 16 | 5 × 5 | 2 × 2 | tanh |
| C3 | Convolution | 16 | 10 × 10 | 5 × 5 | tanh |
| S2 | Avg Pooling | 6 | 14 × 14 | 2 × 2 | tanh |
| C1 | Convolution | 6 | 28 × 28 | 5 × 5 | tanh |
| In | Input | | 1 | 32 × 32 | | |

There are a few extra details to be noted:

- * MNIST images are 28 × 28 pixels, which are zero-padded to 32 × 32 pixels and normalized before being fed to the network. The rest of the network does not use any padding, which is why the size keeps shrinking as the image progresses through the network.
- * The average pooling layers are slightly more complex than usual: each neuron computes the mean of its inputs, then multiplies the results by a learnable coefficient (one per map) and adds a learnable bias term (one per map), then applies the activation function.
- * Most neurons in C3 maps are connected to neurons in only three or four S2 maps (instead of all S2 maps). See table 1 (page 8) in the original paper¹⁰ for details.
- * The output layer is a bit special: instead of computing the matrix multiplication of the inputs and the weight vector, each neuron outputs the square of the Euclidean distance between its input vector and its weight vector. Each output measures how much the image belongs to a particular digit class. The cross entropy cost function is now preferred, as it penalizes bad predictions much more, reducing larger gradients and converging faster.

Yann LeCun's website (“LENET” section) features great demos of LeNet-5 classifying digits.

# AlexNet

The AlexNet CNN architecture won the 2012 ImageNet ILSVRC challenge by a large margin: it achieved 17% top-5 error rate while the best achieved only 26%! It was developed by Alex Krizhevsky (hence the name), Ilya Sutskever, and Geoffrey Hinton. It is quite similar to LeNet-5, much larger and deeper, and it was the first to stack convolutional layers directly on top of each other, instead of stacking a pooling layer on top of each convolutional layer. Table 14-2 presents this architecture.

| Layer | Type | Maps | Kernel size | Stride | Padding | Activation |
| --- | --- | --- | --- | --- | --- | --- |
| Out | Fully Connected | | 1,000 | -- | -- | Softmax |
| F9 | Fully Connected | | 4,096 | -- | -- | ReLU |
| F8 | Fully Connected | | 4,096 | -- | -- | ReLU |
| C7 | Convolution | 256 | 13 × 13 | 3 × 3 | 1 | ReLU |
| C6 | Convolution | 384 | 13 × 13 | 3 × 3 | 1 | ReLU |
| C5 | Convolution | 384 | 13 × 13 | 3 × 3 | 1 | ReLU |
| S4 | Max Pooling | 256 | 13 × 13 | 3 × 3 | 2 | VALID |
| C3 | Convolution | 256 | 27 × 27 | 5 × 5 | 1 | ReLU |
| S2 | Max Pooling | 96 | 27 × 27 | 3 × 3 | 2 | VALID |
| C1 | Convolution | 96 | 55 × 55 | 11 × 11 | 4 | ReLU |
| In | Input | 3 (RGB) | 227 × 227 | | | |

To avoid overfitting, the authors used regularization techniques: first applied dropout (introduced in Chapter 7) with a 50% rate during training to the outputs of F8 and F9. Second, they performed data augmentation by randomly shifting the images by various offsets, flipping them horizontally, and changing the lighting conditions.

> Data Augmentation
> Data augmentation artificially increases the size of the training set by generating many realistic variants of each instance. This reduces overfitting, making this a regularization technique. The generated instances should be as realistic as possible: “ImageNet Classification with Convolutional Networks,” A. Krizhevsky et al. (2012). Ideally, given an image from the augmented set, a human should not be able to tell whether it was augmented or not. Moreover, simply adding white noise will not help; you can shift, rotate, and resize every picture in the training set by various amounts and add the resulting pictures to the training set (see Figure 14-2). This forces the model to be more tolerant to variations in position, orientation, and size of objects. In general, you can also generate many images with various contrasts (except text, and other non-symmetrical objects). By combining these transformations you can greatly increase the size of your training set.

![](img/0684d2da98e09085c0a622d4fd69aaad_476_0.png)

AlexNet also uses a competitive normalization step after the ReLU step of layers C1 and C3, called *local response normalization*. The most strongly activated neurons inhibit other neurons at the same position in neighboring feature maps (such competitive activation has been observed in biological neurons). This encourages different feature maps to specialize, pushing them apart and forcing them to explore a wider range of features, ultimately improving generalization. Equation 14-2 shows how to apply LRN.

# Equation 14-2. Local response normalization

$b_i = a_i^k \alpha \sum_{j=j_{low}}^{j_{high}} a_j^{-\beta} \text{ with } \begin{cases} j_{high} = \min(i+\frac{r}{2}, f_n) \\ j_{low} = \max(0, i-\frac{r}{2}) \end{cases}$

- * $b$, is the normalized output of the neuron located in feature map $i$, at some row $u$ and column $v$ (in this note we only consider neurons in that row and column, so $u$ and $v$ are not shown).
- * $a_i$, is the activation of neuron after the ReLU step, but before normalization.
- * $k$, $\alpha$, $\beta$, and $r$ are hyperparameters. $k$ is called the *bias*, and $r$ is called the *depth radius*.
- * $f_n$ is the number of feature maps.

For example, if $r=2$ and a neuron has a strong activation, it will inhibit the activation of the neurons located in the feature maps immediately above and below it. In AlexNet, the hyperparameters are set as follows: $r=2$, $\alpha=0.002$, $\beta=0.75$, and $k=1$. This step can be implemented using the tf.nn.local_response_normalization function (which you can wrap in a *Lambda* function if you want to use it in a Keras model).

A variant of AlexNet called ZF Net was developed by Matthew Zeiler and Rob Fergus and won the 2013 ILSVRC challenge. It is essentially AlexNet with a few tweaked hyperparameters (number of feature maps, kernel size, stride).

# GoogleLeNet

The **GoogleLeNet architecture** was developed by Christian Szegedy et al. from Google Research¹² and it won the ILSVRC 2014 challenge by pushing the top-5 error rate below 7%. This great performance came in large from the fact that the network was much deeper than previous CNNs (see **Figure 14-14**). This was made possible by sub-networks called *inception modules*,¹³ which allow GoogleLeNet to use parameters much more efficiently than previous architectures: GoogLeNet actually has 10 times fewer parameters than AlexNet (roughly 6 million instead of 60 million).

**Figure 14-13** shows the architecture of an inception module. The notation "3 x 3 + 1(S)" means the layer uses a 3 x 3 kernel, stride 1, and SAME padding. The input signal is first copied and fed to four different layers. All convolutional layers use ReLU activation function. Note that the second of convolutional layers uses kernel sizes (1 x 1, 3 x 3, and 5 x 5), allowing them to capture patterns at different scales. Also that every single layer uses a stride of 1 and SAME padding (even the pooling layer), so their outputs have the same height and width as their inputs. This makes it possible to concatenate all the outputs along the depth dimension in the final depth concat layer (i.e., stack the feature maps from all four convolutional layers). This concatenation layer can be implemented in TensorFlow using the tf.concat() operation, with axis=3 (axis is the depth).

![](img/0684d2da98e09085c0a622d4fd69aaad_478_0.png)

Figure 14-13. Inception module

You may wonder why inception modules have convolutional layers with 1 x 1 convolutional layers. Surely these layers cannot capture any features since they look at one pixel at a time? In fact, these layers serve three purposes:

- * First, although they cannot capture spatial patterns, they can capture patterns along the depth dimension.
- - Second, they are configured to output fewer feature maps than their inputs, so they serve as bottleneck layers, meaning they reduce dimensionality. This cuts the computational cost and number of parameters, speeding up training and improving generalization.
- * Lastly, each pair of convolutional layers ([1 x 1, 3 x 3] and [1 x 1, 5 x 5]) acts like a single, powerful convolutional layer, capable of capturing more complex patterns. Indeed, instead of sweeping a simple linear classifier across the image as a

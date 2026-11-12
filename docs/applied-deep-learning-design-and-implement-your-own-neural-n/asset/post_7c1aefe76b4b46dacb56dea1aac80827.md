
| Layer | Input Size | No. of Filters ($n_l$) | Filter Size ($F$) | Padding ($P$) | Stride ($S$) | Output Size | Number of parameters (size of filter * number of filters) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Convolution Layer 12 | 14 * 14 * 512 | 512 | (3 * 3 * 512) | Same | 1 | 14 * 14 * 512 | (3 * 3 * 512) * 512 |
| Convolution Layer 13 | 14 * 14 * 512 | 512 | (3 * 3 * 512) | Same | 1 | 14 * 14 * 512 | (3 * 3 * 512) * 512 |
| Pooling Layer 5 (Max Pooling) | 14 * 14 * 512 | 1 | (2 * 2) | 0 | 2 | 7 * 7 * 512 | 0 |
| Fully Connected Layer 1 | 7 * 7 * 512 = 25088 | NA | NA | NA | NA | 4096 | (7 * 7 * 512) * 4096 |
| Fully Connected Layer 2 | 4096 | NA | NA | NA | NA | 4096 | (4096 * 4096) |
| Fully Connected Layer 3 | 1000 | NA | NA | NA | NA | 1000 | (4096 * 1000) |
| Summation of parameters | 28 Million | NA | NA | NA | NA | - | 138 Million |

Table 4.4: VGGNet parameters [INPUT:]

## Different types of model-fitting and dropout in neural networks

Model fitting is a method to measure how well a deep learning model shows the results on new testing data after being trained with the training data. Model fitting is divided into three parts: under-fitting, balanced-fitting, and over-fitting, as shown in figure 4.175:

### Balanced Fitting

![](img/7e519fee1b702b91799cdf1664598392_340_0.png)

### Under Fitting

![](img/7e519fee1b702b91799cdf1664598392_340_1.png)

### Over Fitting

![](img/7e519fee1b702b91799cdf1664598392_340_2.png)

Figure 4.175: Different types of model fitting

Model fitting is very important in deep learning. If the model is not correctly fitted, then it may not provide correct or accurate outputs on the test data.

Underfitting happens when a model can neither fit the training data nor work on the new test data. Under-fitting model even performs poorly on the training data itself. In figure 4.175, the under-fitting model is represented by a straight line, but it cannot even distinguish between the two types of classes.

Over-fitting happens when a model is trained with the *training data* at a higher extent. In this case, the users achieve a very good fit of the model on the training data itself. However, the model cannot work well with new test data. It simply means learning the parameters specifically to the training data, which does not work with the test data.

So, the model has to be balanced-fitted so that it should work well for both the training and test data.

The term *dropout* in neural networks refers to dropping out some units of layers in a neural network. In other words, dropout is the process of ignoring some units (neurons) in the training phase of neurons in the neural network. It is used to prevent over-fitting of data.

So, dropping out means those neurons may not be considered in both forward pass and backward pass. Figure 4.176 shows the standard neural network:

![](img/7e519fee1b702b91799cdf1664598392_341_0.png)

**Figure 4.176: Neural network**

Figure 4.177 shows a neural network after applying dropout. We randomly drop some of the neurons, and then the error is adjusted using backpropagation. Large errors are adjusted a lot, whereas, in the case of small errors, they are adjusted a bit. In case of no error, we stop:

![](img/7e519fee1b702b91799cdf1664598392_342_0.png)

Figure 4.177: Neural network after applying dropout

**Example 4.10:** Let us take an example of dropout with respect to the max pooling layer in CNN. Suppose we have the following feature map of size as output from a convolution layer.

| 4 | 3 | 8 |
|---|---|---|
| 7 | 4 | 2 |
| 6 | 4 | 5 |

Figure 4.178: Feature or activation map

Then, we applied max pooling to get pooled feature map output. So, if the max pooling is performed without dropout, it gives output as shown in figure 4.179:

![](img/7e519fee1b702b91799cdf1664598392_342_1.png)

Figure 4.179: Pooled feature map after applying max-pooling

But if the max pooling is performed with dropout, it gives the output as shown in figure 4.180:

![](img/7e519fee1b702b91799cdf1664598392_343_0.png)

## ResNet

ResNet stands for residual network. Deep learning architectures like CNN have achieved image classification results almost similar to human minds. However, with an increase in the number of layers in deep neural networks, the accuracy of the model becomes saturated and then suddenly degrades.

Figure 4.181 shows the various CNN case studies along with the error rate and the number of layers that are presented at the ImageNet Large Scale Visual Recognition Challenge (ILSVRC) during successive years starting from 2010 to 2015:

![](img/7e519fee1b702b91799cdf1664598392_343_1.png)

The ILSVRC evaluates algorithms for object detection and image classification at a large scale. In this, we notice that starting from ILSVRC'10, the number of layers is shallow, and it gets increased up to 152 when ResNet is introduced during ILSVRC'15. The error rate is considerably reduced from 28.7% to 3.57% from ILSVRC'10 to ILSVRC'15, as shown in figure 4.181. The error rate of ResNets is just 3.57%. In figure 4.182, graphs show the performance comparison of plain nets and ResNets on the CIFAR-10 dataset.

The CIFAR-10 dataset (Canadian Institute For Advanced Research) is a collection of images that are commonly used to train machine learning and computer vision algorithms. It consists of 60,000 color images with the size of each image as 32 × 32, divided into 10 classes, with 6,000 images per class. There are 50,000 training images and 10,000 test images. It shows the advantage of ResNets over simple convolutional networks. In figure 4.182 (a), we can see some solid (test) and dashed sinusoidal waves. The solid lines represent the test data, whereas the dashed lines represent the training data. We can see in figure 4.182(a) that even after increasing the number of layers, the accuracy does not get increased, and we are getting more error rates for the increased number of layers.

For example, the error rate for a 56-layer convolutional network is much more than the 20-layer convolutional network, as shown in figure 4.182(a). So, from here, the need for ResNets comes into the scenario [figure 4.182 (b)]. In the case of ResNets, as shown in figure 4.182(b), we can see that the error percentage decreases with an increase in the number of layers. Moreover, if ResNet does not perform well by adding more and more layers, we will not get anything less than what we have achieved before or up to the previous layer.

## CIFAR-10 Experiments

![](img/7e519fee1b702b91799cdf1664598392_344_0.png)

Figure 4.182 [a,b]: Performance comparison of Plain nets and ResNets on the CIFAR-10 dataset

## Mathematical formulation to learn Identity mapping in Residual Network (ResNet)

In figure 4.183, we have considered three layers as lth layer, (l + 1)th layer, and (l + 2)th layer:

![](img/7e519fee1b702b91799cdf1664598392_345_0.png)

Figure 4.183: Convolutional neural network

Where, $a^l$ is the activation function at lth layer, $a^{l+1}$ is the activation function at (l + 1) th layer and $a^{l+2}$ is the activation function at (l + 2)th layer. From figure 4.183, we can say that the output from layer (l+1) is given as follows:

$z^{(l+1)} = w^{(l+1)}. a^l + b^{(l+1)}$

Now, as we are using non-linearity, then

$a^{(l+1)} = G(z^{(l+1)})$

Where G is the ReLU activation function. Similarly, $z^{(l+2)}$ is expanded as follows:

$z^{(l+2)} = w^{(l+2)}. a^{(l+1)} + b^{(l+2)}$

And

$a^{(l+2)} = G(z^{(l+2)})$

Now, for establishing the residual connection, we connect $a^l$ to (l + 2) layer, as shown in figure 4.184:

![](img/7e519fee1b702b91799cdf1664598392_346_0.png)

Here, we connect \(a^l\) to \((l + 2)\) layer before non-linearity, then after the connection, we apply the non-linearity. So, the residual connection output is as follows:

\(a^{(l+2)} = G(z^{(l+2)} + a^l)\)

Now, as we know:

\(z^{(l+2)} = w^{(l+2)} . a^{(l+1)} + b^{(l+2)}\)

Therefore,

\(a^{(l+2)} = G(w^{(l+2)} . a^{(l+1)} + b^{(l+2)} + a^l)\)

So, residual network means taking input from one layer, then skipping one layer and adding it to the next layer before applying non-linearity.

If we are not performing well with the upcoming few layers, then we will apply L2 regularization and keep on reducing the weights such that both, that is, \(w^{(l+2)}\) and \(b^{(l+2)}\) becomes very low, that is, almost equal to ZERO. Then, \(a^{(l+2)}\) gets reduced as follows:

\(a^{(l+2)} = G(a^l)\)

As \(a^l\) is the activation function defined as \(a^l = G(z^{(l)})\):

\(a^{(l+2)} = G(G(z^{(l)})) = G(a^l) = a^l\)

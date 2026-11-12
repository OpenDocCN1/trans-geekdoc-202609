
data. Today, the current methods are based on networks of artificial neurons that have the ability to perform the same role at the top level compared to the first techniques and without the need for human intervention. In the course of a long history, deep learning (Y. LeCun, 2015), (Schmidhuber, 2014) has undergone alternating periods of excitement and forgetfulness, under which it was known under various names and many researches. The first period of work on deep learning was for nearly 20 years from 1940 until 1960 and described simple neural networks with a supervised and unsupervised learning process (Rosenblatt, 1958). The second period began 19 years after the end of the first period (1979 to 1990) with Fukushima's work Neocognitron (Fukushima, 1979) which can be considered as the first work that deserves to be described “deep” (Schmidhuber, 2014). In addition, this period has seen the application of back propagation to artificial neural networks (Werbos, 1981), it recalls us that the back propagation is an effective method of gradient descent for supervised learning has been developed in the years 1960 and 1970. The most modern period represents the golden period of deep learning started from 2006 as shown in the following works (G. E. Hinton, 2006), (Y. Bengio, 2007), where we can notice that in the previous last years, deep learning (Y. LeCun, 2015), (Schmidhuber, 2014) achieve huge success in different areas especially in computer vision. In addition, deep networks have won numerous competitions in image classification (Alex Krizhevsky, 2012), (Matthew D Zeiler, 2013), (Zisserman, 2015), (et al., 2015), (He X. Zhang, 2015), (Komodakis, 2016), (Saining Xie, 2016), (Gao Huang, 2017), (Huang, 2016), (P. Sermanet, 2014), (Bengio, 1994) and object detection (P. Sermanet, 2014) such as the annual ILSVRC competition Russakovsky. It is based on ANN consisting of various processing layers to learn representations of large sets of data using the back propagation algorithm to update the local parameters of each layer. Among various deep learning algorithms [1,2], Convolutional Neural Networks (CNN) has become the popular and frequently used neural model in deep learning, where it has achieved a revolution in the tasks of artificial vision thanks to these capacities persisting, which resisted for many years. In addition, it offers good performance in terms of precision (Alex Krizhevsky, 2012), (Matthew D Zeiler, 2013), (Zisserman, 2015), (et al., 2015), (He X. Zhang, 2015), (Komodakis, 2016), (Saining Xie, 2016), (Gao Huang, 2017), (Huang, 2016), (P. Sermanet, 2014), (Bengio, 1994).

This paper is organized as follows: the second section describes the background. The third section presents the comparative study of popular deep CNN topologies used for ImageNet classification and the conclusions are drawn in the last section.

## Background

Recent work on deep neural network approaches has improved the performance of these visual recognition systems. In this section, we focus on the convolutional neural network, supervised learning and the ImageNet database.

## Motivations

CNNs are described as a special type of artificial neural networks that is based on convolution, which is defined as a specialized type of linearity operation. They benefit from a capacity that can be controlled by varying these two elements: the depth and the width. In addition, they have a lower density of connections and parameters compared to the multilayer perceptron (MLP) which makes them easier to train.

### Supervised Learning

Supervised learning (Bishop, 2006) is based on the exploitation of labeled data. It makes it possible to create a link between the input and the label for correctly associating each input E<sub>i</sub> with its output S<sub>i</sub>. For each input sample E<sub>i</sub> from the incoming data of size n, E<sub>i</sub> = {0,1,2..n-1}, the neurons that are located in the last layer of the network will be labeled, so that for one input E<sub>i</sub> the activated neuron after the learning phase will be assigned by the label which represents the expected output S<sub>i</sub> for this input.

```
S<sub>i</sub> = f(E<sub>i</sub>) + Δ                          (1)
```

The principle of supervised learning is to evaluate the error (Δ) for each input and update the local parameters of the neurons in order to minimize the error in the next iterations. This means that the training data must be iteratively provided to the ANN in order to compare the prediction of each data sample with the associated desired label and analyze the error for each input and then make a modification of the local parameters of the system (called: weights, they are real numbers) will be realized to improve the prediction. By repeating this operation on a set of data, the system will converge to a state where its predictions become more and more accurate. Among the most widely used supervised learning algorithms are the gradient retro-propagation algorithms (D. Rumelhart, 1986). The major disadvantage of this learning class is sometimes the difficulty of finding a database in the desired domain and the cost of building the new learning database and finally the complexity of these learning algorithms.

### ImageNet

ImageNet is an image database organized according to the WordNet hierarchy and intended for computer vision research work. It is considered the standard reference for evaluating the performance of different image classification and object detection algorithms. It integrates more than fifteen million high resolution and variable size images from approximately 22,000 categories. ImageNet consists of variable resolution images collected from the web and labeled by “Amazon Mechanical Turk”. This foundation was first presented at the Conference on Computer Vision and Pattern Recognition (CVPR, 2009) during poster sessions. Since 2010, an annual competition has been organized. ILSVRC (Russakovsky, 2015) uses a subset of ImageNet with approximately 1000 images in each of the 1000 categories. In total, there are approximately 1.2 million training images, 50,000 validation images and 150,000 test images with variable resolutions.

## The Bases of Convolutional Neural Networks (CNN)

The different CNN models use many layers that typically include multilayer convolution stacks, combined with grouping and normalization layers, to extract simple and hierarchically useful images. The stacking of these several layers ensures the construction of the CNN. Convolution is the main step in convolutional neural networks and is described as the core of the convolutional network. A convolution is defined as the scalar product of a matrix of pixels with a weight matrix or core that represents the size convolutional filter (L x C) where L and C are generally odd and equal values. CNNs perform a 3D convolution (Figure 1) to extract the spatial and temporal characteristics of the data (Dou Q, 2017), (N. C. Camgoz, 2016). The principle of 3D convolution consists of convolving an image cube that represents several images stacked in a successive manner by a set of filters that forms a 3D core. The value of the position (x, y, z) in the three-dimensional convolution for a given image in the first layer is determined using the following mathematical equation:

```
\(\text{\textit{Conv}}(\text{\textit{Pixel}}_{ij}^{XYZ}) = B_{ij} + \sum_{N}^{P_l-1} \sum_{P=0}^{Q_l-1} \sum_{Q=0}^{R_l-1} \sum_{R=0}^{P_l} W_{ijN}^{PQR} \times \text{\textit{Pixel}}_{(i-1)\times N}^{(X+P)(Y+Q)(z+R)}\) (2)
```

Knowing that R denotes the length of the size of the 3D convolution kernel.

## Figure 1. Representation of a 3D convolution

![](img/a636f78302652a9c2ec5900d81fba475_107_0.png)

The choice of the activation function is very important since it will be applied to each incoming pixel. In addition, the choice of the appropriate activation function can speed up the learning process. The figure 2 summarizes the popular activation functions and the most used ones:

## Figure 2. The most popular nonlinear activation functions

| Sigmoid | Tanh | ReLU | Leaky ReLU |
| :--- | :--- | :--- | :--- |
| \(g(z) = \frac{1}{1+e^{-z}}\) | \(g(z) = \frac{e^z - e^{-z}}{e^z + e^{-z}}\) | \(g(z) = max(0, z)\) | \(g(z) = max(\epsilon z, z)\) with \(\epsilon \ll 1\) |
| Graph showing sigmoid curve | Graph showing tanh curve | Graph showing ReLU line | Graph showing Leaky ReLU line |

The ReLU function is the most used function; it represents the identification of positive arguments and assigns zeros to others. In most early works, the hyperbolic tangent and the sigmoid function are often the most used. However, today these functions are no longer exploited because they require complex arithmetic and they present difficulties in the material implantation. In addition, the hyperbolic tangent does not represent a solution for the problem of vanishing gradient problem on the contrary to the ReLU, which allows to reduce and relieve this problem (Clever & Unterthiner, 2016). The pooling operation

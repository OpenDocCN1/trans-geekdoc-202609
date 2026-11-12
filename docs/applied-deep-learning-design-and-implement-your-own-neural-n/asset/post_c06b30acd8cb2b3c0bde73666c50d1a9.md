
with an example to show how CNN works. In the last part of the chapter, various CNN cases studies such as LeNet-5, AlexNet, ZFNet, VGGNet, Identity mapping, ResNet, Inception modules, and GoogLeNet are discussed in detail.

## Structure

In this chapter, we will cover the following topics:

- Introduction to CNN
- CNN architecture
- Layers of CNN
- Representation of an image
- Correlation
- Convolution
- Spatial filters
- Padding in CNN
- Stride in CNN
- Convolution in 1-D
- Convolution in 2-D
- Visualization of 3-D filter in 2-D convolution
- Learning by CNN
- Importance of ReLU in the convolutional layer
- Pooling in CNN
- Max pooling
- Fully connected layer in CNN
- Implementation of CNN (how CNN works)
- Case studies of CNN, Lenet-5, Alexnet, ZFNet, VGGNet, ResNet, GoogLeNet, and Inception modules

## Objectives

After going through this chapter, you will be able to understand the basic working of CNN for image classification. You will understand the architecture of a convolutional neural network and get a vast idea of the various layers of CNN. You will be able to comprehend the concepts of max pooling, strides, and different types of convolutional neural networks. You will able to apply convolutional filters in one- and two-dimensional domains. Moreover, in this chapter, you will understand how CNN learns and works in a real scenario. At last, you will be well versed with various case studies of convolutional neural networks that you can implement to solve your classification problem in the real-world domain.

## Introduction to convolutional neural networks (CNN)

A computer observes an input image as a collection of different pixel values. Depending upon the size and resolution of the input image, it sees an array of pixels, where 1 represents that the input image is black and white. For example, we have an RGB input image of size as shown in figure 4.1:

![](img/7e519fee1b702b91799cdf1664598392_222_0.png)

Figure 4.1: Grayscale image

To describe an image in image processing, we need the coordinate system. The coordinate system, which is used to relate elements with each other, is called the user space. Figure 4.2 shows a coordinate system used in the Spatial domain representation of an image:

![](img/7e519fee1b702b91799cdf1664598392_222_1.png)

Figure 4.2: Spatial domain coordinate system

So, using a coordinate system, the computer sees the image as a collection of pixel values of size as shown in figure 4.3(a). Number 3 is shown with its spatial representation and binary representation in figure 4.3(b).

![](img/7e519fee1b702b91799cdf1664598392_223_0.png)

![](img/7e519fee1b702b91799cdf1664598392_223_1.png)

**Figure 4.3** (a): Original image.

**Figure 4.3** (b): Input in the spatial domain.

**Figure 4.3** (c): Binary representation in spatial domain representation of figure 4.3 (b).

Neural networks generally consist of the following three layers:

- **Input layer**: It is the first layer of a neural network. It takes the input to the model. The total number of neurons in this layer is the same as the total number of features in the input data. Taking an image as an input, the total number of neurons is equal to the total number of pixels that represent an image.

- **Hidden layer**: The output from the input layer is passed through the hidden layer. Depending upon the size of the data and model, there can be many layers. Every hidden layer may have a different number of features. The hidden layers execute computations on the weighted inputs and provide the net output, which is fed as an input to the next layer with activation functions to provide the actual output.

- **Output layer**: This is the last layer of a neural network that provides outputs corresponding to the given inputs. By using activation functions such as SoftMax, the output of each class is converted into a probability value. A neural network with a single hidden layer is shown in figure 4.4.

![](img/7e519fee1b702b91799cdf1664598392_224_0.png)

Figure 4.4: Conventional neural network with a hidden layer (h)

We have already discussed traditional neural networks that are known as multi-layer perceptron in Chapter 3: Intuition of Neural Networks.

## Drawbacks of traditional neural networks and emergence of CNN

Traditional neural networks have many drawbacks, especially when we talk about image processing. These networks use one perceptron for each input which makes them unsuitable for large weights. For example, we have an RGB image of pixel size (424*424). Then, 15,000 weights need to be updated, which becomes difficult and may result in overfitting. One more drawback of these neural networks is that when an image is fed into them, it results in the loss of spatial information. For example, if we consider an image of size (1024*1024), then the total number of pixels is 1,048,576. So, when we consider the input as 1,048,576, and we input these number of input values in a fully connected network, then the neural network becomes complex. If the number of neurons in the hidden layer is 1,000, then the number of weight parameters is 1,048,576 x 1,000 = 1,048,576,000. Hence, it is difficult to handle this big number of parameters. Moreover, we know that when we consider images, we know that the pixel values (intensity) are highly correlated in an image. So, when we flatten the pixel values of an image, the spatial relationships get destroyed. That is when convolutional neural networks come into the picture. Convolution neural networks work on the basis of the neighborhood, as most of the useful information in the case of images in image processing lies in the neighborhood of the center pixel. We can understand this more by correlating it with the real-world scenario as follows.

For example, say I want to get information about a student named Tarun in my third-year class of image processing at Thapar University. Now, I want to access information about him, such as how he is in image processing, whether he plays cricket, is he a good swimmer, and so on. Then, what is the best possible way to retrieve this information. Is it a good approach that I ask about Tarun to the entire Thapar University to get these answers? Will I get useful information about Tarun? Moreover, I get a vast amount of information that may not be useful to me and difficult to summarize. Then, what is the solution for this? Probably, I will ask these questions to classmates of Tarun as they are in the close neighborhood of Tarun and they know a lot about him, and they will return valid and confined answers to the questions asked. The same is the case when we are dealing with images. There exists a strong correlation among the pixel values that lie in the neighborhood of an image. So, most of the useful information about a pixel exists in the neighborhood as compared to the pixels that lie far away. Convolution neural networks deal with the convolutional filters that are correlated with the pixel values of the neighborhood.

Another drawback of traditional neural networks is that these networks react differently with the input image and the shifted image of the input image. For example, if a car appears at the top of an image in one picture and at the bottom of an image in the other picture, the neural network corrects itself after every input and assumes that the car always appears at the bottom of the image. So, to overcome the aforementioned constraints and challenges, the need for CNN arises, which is discussed as follows.

A CNN is a neural network having one or more convolutional layers. These are made of neurons having the capability to learn biases and weights. These are similar to **artificial neural networks (ANN)** but with a reduced number of parameters in the network. The main difference between ANN and CNN is that the CNNs take input as images and explore the neighborhood. CNN is mainly used for image processing, classification, segmentation, and also for other auto-correlated data.

The advantage of CNN over a simple neural network is that the CNNs are easier to train and have a smaller number of parameters with an equal number of hidden layers.

## CNN architecture

CNN architecture is designed according to the connectivity configuration of neurons inside the human brain. A typical CNN architecture is shown in **figure 4.5**:

![](img/7e519fee1b702b91799cdf1664598392_226_0.png)

Figure 4.5: Convolutional neural network

## Layers of CNN

The various layers of CNN shown in **figure 4.5** are as follows.

- **Input layer**: This layer takes the input in the form of an image and passes it to the convolution layer. The input layer of the CNN takes an image as an input having dimensions: _(width * height * depth)_. Image is a representation of a matrix of pixel values. For example, if we have an RGB image of width = 48 and height = 48, then the dimension of the input image is (48 * 48 * 3). Here, the depth of 3 represents the channels _R_, _G_, and _B_ of the image.

- **Convolutional layer**: The main objective of the convolution layer is to extract the features of the input image. This layer creates a feature map to predict

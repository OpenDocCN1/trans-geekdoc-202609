# Convolution in 1-D

Figure 4.51 shows a fully connected network. It consists of an input layer, a hidden layer, and output layer. The input layer consists of images taken from Modified National Institute of Standards and Technology database (MNIST) dataset. The MNIST dataset is the collection of handwritten digits that is commonly used for training various image processing systems. The dataset is also widely used for training and testing in the field of machine learning. It has a training set of 60,000 examples and a test set of 10,000 examples. The first layer consists of 784 *1,000 parameters. The 784-pixel values are flattened in the Input layer:

![](bbox=[0.135, 0.315, 0.49, 0.685])

MNIST Dataset: 28 X 28 pixels (784 pixels)
First layer weights: 78K parameters

Typical Image: 256 X 256 pixels (56,000 pixels)
First layer weights: 560K parameters

Too many parameters, unscalable to real images

Figure 4.51: Fully connected neural network

Figure 4.52 shows a convolutional neural network that consists of the Input image (input layer) and the hidden layer that is not fully connected:
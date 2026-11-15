+   Fully connected layer - Layers in a neural network that are fully linked have all their inputs connected to every activation unit in the layer above them. The final few layers in most well-liked machine learning models are fully connected layers that combine the data gathered by earlier layers to create the output. The convolution layer takes the greatest time, followed by this layer.

# 2.5 Various CNN Architectures

# 2.5.1 LeNet-5 (1998)

Perhaps the most convenient design is LeNet-5. It has three fully associated layers and two convolutional layers [21]. As shown in Figure 2.4, each convolutional layer was followed by an average pool layer. As we undoubtedly already know, the conventional pooling layer included training weights and was referred to as a sub-sampling layer at the time. There are about 60,000 borders in this design. In 1998, LeCuN proposed LeNet [22]. Graphic processing units and even CPUs were not typically used in the early 2000s to speed up training. The main limitation of a classic multi-layered fully connected neural network was that it considered each pixel as a separate input and applied an adjustment to it, which at the time, in 1998, was a significant computational load. LeNet violated the fundamental tenet of an image—that adjacent pixels are connected, and those feature concepts are spread throughout the entire picture—by ignoring this relationship. LeNet was the first convolutional network architecture which condensed the different parameters and could also inadvertently understand features from raw pixels.

![](bbox=[0.12, 0.72, 0.88, 0.86])

Figure 2.4 Architecture of LeNet, a Convolutional Neural Network for digits recognition. Each plane is a feature map, i.e., a set of units whose weights are constrained to be identical.
![](bbox=[0.175, 0.14, 0.825, 0.37])

Computationally, the number of kernels is represented with the dimension of the weights' tensor. You'll see how to implement this later.

# Pooling

What pooling layers do is rather simple compared to convolutional layers. They actually do not train or learn by themselves but just downsample images propagated from convolutional layers. Why should we bother to do downsampling? You might think it may lose some significant information from the data. But here, again, as with convolutional layers, this process is necessary to make the network keep its translation invariance.

There are several ways of downsampling, but among them, max-pooling is the most famous. It can be represented as follows:

![](bbox=[0.175, 0.61, 0.825, 0.78])
# Obtaining Deep Learning Models for Automatic Classification of Leukocytes

28×28×2. By using more filters, one can better preserve the spatial dimensions/directions. Each of these filters can be considered as identifying features as borders, straight lines, simple colors and curves.

The output of the convolution layer is an activation map. The higher the value obtained, the greater probability. The more filters you use, the greater the depth of the activation map, and consequently, more information about the input volume will exist.

For tensors of order 3, the convolution operation is done in a manner similar to that used for order 2. The output of the $i^{th}$ is a tensor of order 3 with size $H*W*D$, the convolution kernel will also be a 3-order tensor with size $H*W*D$. When the kernel is placed on top of the input at the spatial location (0,0,0), the products of the corresponding elements are calculated on all the channels $D$, and to the products of $H*W*D$ to obtain the convolution result in this spatial location (Wu, 2017). There are other ways of treating tensors (channels), which is the most common.

# Pooling

Pooling is a data reduction. In the general, the maximum or mean of a small region of the input is calculated. The main advantage of pooling is speed increase in the network due to interlayer downsampling, reducing the amount of data to be processed and making " curse of dimensionality" less intense (Nascimento, 2016).

The purpose of pooling layers is also to achieve spatial invariance by reducing the resolution of feature maps. Each map corresponds to a characteristic map of the previous layer. Its units combine the input of small fragments(patches). These pooling windows can be of arbitrary size. The max-pooling consists in calculating the highest value in a patch, normally, of four elements. Those four elements are replaced by that value. The result is a lower-resolution feature map (Scherer, Müller, & Behnik, 2010).

# Deeper Layers of the CNN

CNN are representatives of the multi-stage Hubel-Wiesel architecture, which extract local characteristics at high resolution and combine successively into more complex features at lower resolutions. The loss of spatial information is offset by an increasing number of resource maps in the higher layers. The general architecture is shown in Figure 5.

> 5. CNN architecture with convolution, pooling and fully-connected layers (Scherer, Müller, & Behunque, 2010)

![](bbox=[0.168, 0.747, 0.832, 0.903])

10
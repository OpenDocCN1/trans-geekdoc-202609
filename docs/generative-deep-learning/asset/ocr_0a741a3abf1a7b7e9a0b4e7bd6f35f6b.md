# ResidualBlock

Both the DownBlock and the UpBlock contain ResidualBlock layers, so let's start with these. We already explored residual blocks in Chapter 5, when we built a PixelCNN, but we will recap here for completeness.

A residual block is a group of layers that contains a skip connection that adds the input to the output. Residual blocks help us to build deeper networks that can learn more complex patterns without suffering as greatly from vanishing gradient and degradation problems. The vanishing gradient problem is the assertion that as the network gets deeper, the gradient propagated through deeper layers is tiny and therefore learning is very slow. The degradation problem is the fact that as neural networks become deeper, they are not necessarily as accurate as their shallower counterparts—accuracy seems to become saturated at a certain depth and then degrade rapidly.

![](bbox=[0.15, 0.36, 0.24, 0.44])

# Degradation

The degradation problem is somewhat counterintuitive, but observed in practice as the deeper layers must at least learn the identity mapping, which is not trivial—especially considering other problems deeper networks face, such as the vanishing gradient problem.

The solution, first introduced in the ResNet paper by He et al. in 2015,8 is very simple. By including a skip connection highway around the main weighted layers, the block has the option to bypass the complex weight updates and simply pass through the identity mapping. This allows the network to be trained to great depth without sacrificing gradient size or network accuracy.

A diagram of a ResidualBlock is shown in Figure 8-10. Note that in some residual blocks, we also include an extra Conv2D layer with kernel size 1 on the skip connection, to bring the number of channels in line with the rest of the block.

![](bbox=[0.25, 0.66, 0.7, 0.78])

Figure 8-10. The ResidualBlock in the U-Net
connection represented by the dashed arrow in Figure 14-17. To solve this problem, the inputs are passed through a 1 × 1 convolutional layer with stride 2 and the right number of output feature maps (see Figure 14-18).

![](bbox=[0.142, 0.15, 0.857, 0.31])

Figure 14-18. Skip connection when changing feature map size and depth

ResNet-34 is the ResNet with 34 layers (only counting the convolutional layers and the fully connected layer) containing three residual units with 64 feature maps, 4 RUs with 128 maps, 6 RUs with 256 maps, and 3 RUs with 512 maps. We will implement this architecture later in this chapter.

ResNets deeper than that, such as ResNet-152, use slightly different units. Instead of 3 × 3 convolutional layers with (say) 256 feature maps, they use three convolutional layers: first a 1 × 1 convolutional layer with just 64 feature maps (4 times less), which acts as a bottleneck layer (as discussed already), and then a 3 × 3 layer with 64 feature maps, and finally another 1 × 1 convolutional layer with 256 feature maps (4 times 64) that ResNet-152 contains these three RUs that output 256 maps, 8 RUs with 512 maps, a whopping 36 RUs with 1,024 maps, and finally 3 RUs with 2,048 maps.

> Google's Inception-v4¹ architecture merged the ideas of GoogleNet and ResNet and achieved close to 3% top-5 error rate on Image classification.

# Xception

Another variant of the GoogLeNet architecture is also worth noting: Xception¹⁷ (which stands for Extreme Inception) was proposed in 2016 by François Chollet for

⁶"Inception-v4, Inception-ResNet and the Impact of Residual Connections on Learning," C. Szegedy et al. (2016).
¹⁷"Xception: Deep Learning with Depthwise Separable Convolutions," François Chollet (2016)
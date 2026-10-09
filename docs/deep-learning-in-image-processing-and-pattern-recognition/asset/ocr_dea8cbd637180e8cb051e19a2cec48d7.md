where $I_{n}(i_{r}j)$ indicates the feature value of the feature map at the $(i, j)$ position on the $m$-th channel, $C$ is the total channel number of the input feature map.

The average global pooling handle as in Equation (5) [18]:

$$P(i, j)=\frac{1}{d} \sum_{n=1}^{d} T_{n}(i, j)$$    (5)

where $T_{n}(i, j)$ represents the feature value at the location $(i, j)$ of the $n$-th access, and $d$ is the number of the amount of accesses in the input feature map. The two feature maps are linked in the access dimension utilizing the access link, then a 1 x 1 convolution kernel is used for convolution operation. Finally, a sigmoid function is used to process an output. This attention mechanism can effectively draw the important message of each location of the feature map and the main features by assigning weights and suppressing the background information.

# 3.1.3. Hybrid Attention Mechanism Module

In the two attention mechanisms, the attention in the spatial domain neglects the message in the access domain, and the image features in each access are treated equally. This will make the spatial domain operation limited to the original image feature extraction stage, resulting in the application of the neural network in each tier of the interpretability to be not strong. On the other hand, the attention of the channel domain is to pool the overall situation, which means to obtain information directly and to ignore the local news in every access. Therefore, a lightweight hybrid-domain attention mechanism model is constructed by combining the characteristics of the two attention mechanisms and can perform attention in access and spatial dimensions [20]. The construction of the Convolution Block Attention Module (CBAM) is illustrated in Figure 1.

![](bbox=[0.14, 0.56, 0.82, 0.74])

Figure 1. CBAM construction diagram with the hybrid attention mechanism module.

As mentioned above, CBAM is made up of two sub-modules; one is the Channel Attention Module (CAM), and the other is the Spatial Attention Module (SAM). CBAM is to multiply the input feature map with the CAM to get a new feature map, then multiplies the new feature map with SAM to get the resulting output. Thus, the channel domain and the spatial domain are combined. Because SE and CBAM belong to the access domain attention module and hybrid domain attention module, respectively, CBAM has a better attention concentration effect than the SE module. Therefore, this paper uses the attention mechanism module CBAM to replace the SE module in the lightweight network MobileNetV3. At the same time, combined with ResNet-50, this paper deepens the number of network tiers to 50 to achieve the purpose of enriching high-level semantic information [21].
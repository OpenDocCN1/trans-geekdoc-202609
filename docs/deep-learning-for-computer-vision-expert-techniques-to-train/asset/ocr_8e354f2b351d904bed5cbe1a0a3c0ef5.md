# # Spatial transformer networks

The spatial transformer networks proposed by Jaderberg et al. (https://arxiv.org/pdf/1506.02025.pdf) try to transform the image passing to the CNN. This is different from other networks because it tries to modify the image before convolution. This network learns the parameters to transform the image. The parameters are learned for an affine transformation. By applying an affine transformation, spatial invariance is achieved. In the previous networks, spatial invariance was achieved by max-pooling layers. The placement of spatial transformer networks is shown as follows:

![](bbox=[0.267, 0.313, 0.732, 0.477])

# # The DenseNet model

DenseNet is an extension of ResNet proposed by Huang et al. (https://arxiv.org/pdf/1608.06993.pdf). In ResNet blocks, the previous layer is merged into the future layer by summation. In DenseNet, the previous layer is merged into the future layer by concatenation. DenseNet connects all the layers to the previous layers and the current layer to the following layers.
# Text Separation From Document Images

the resolution of the output image. ResU-Net has a similar architecture to that of U-Net with an extra residual connection in the model (Figure 13 (Zhang, Z., Liu, Q., & Wang, Y., 2018)).

The residual connections help to train the model fast and avoid the vanishing gradient problem, which occurs in most of the deep learning networks. The following equation gives the residual connection:

```
$y_i = h(x_i) + F(x_i, W_i), x_{i+1} = f(y_i).$
```

$x_i, x_{i+1}$ are the input, $f(y_i)$ s activation function, and output to the residual layer at the $l$-th position. $f(\cdot)$ are the residual function of the section and $h(x_i)$ is the identity mapping.

Figure 12. U-Net architecture

![](bbox=[0.15, 0.373, 0.85, 0.735])

The Number below the box defines the no. of channels (input has three and output 1). Numbers above the boxes indicate the no. of filters of the convolution layer (or feature maps). The dotted arrow and empty boxes indicate concatenation of the feature map of the encoder with the up-convolution operation of the decoder. Green colored boxes are convolution + BN + ReLU while blue boxes are up-convolution + BN + Relu. Arrows have their meanings mentioned in the figure above. 256x256 is the dimension of input image and mask (Ronneberger, O., Fischer, P., & Brox, T., 2015).

303
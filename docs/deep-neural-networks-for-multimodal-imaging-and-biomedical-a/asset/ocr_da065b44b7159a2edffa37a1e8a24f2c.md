several images stacked in a successive manner by a set of filters that forms a 3D core. The value of the position (x, y, z) in the three-dimensional convolution for a fifth image in the first layer is determined using the following mathematical equation:

```
\(\text{\textit{Conv}}(\text{\textit{Pixel}}_{ij}^{XYZ}) = B_{ij} + \sum_{N}^{P_l-1} \sum_{P=0}^{Q_l-1} \sum_{Q=0}^{R_l-1} \sum_{R=0}^{P_l} W_{ijN}^{PQR} \times \text{\textit{Pixel}}_{(i-1)\times N}^{(X+P)(Y+Q)(z+R)}\) (2)
```

Knowing that R denotes the length of the size of the 3D convolution kernel.

# Figure 1. Representation of a 3D convolution

![](bbox=[0.265, 0.34, 0.7, 0.485])

The choice of the activation function is very important since it will be applied to each incoming pixel. In addition, the choice of the appropriate activation function can speed up the learning process. The figure 2 summarizes the popular activation functions and the most used ones:

# Figure 2. The most popular nonlinear activation functions

| Sigmoide | Tanh | RelU | Leaky RelU |
| :--- | :--- | :--- | :--- |
| \(g(z) = \frac{1}{1+e^{-z}}\) | \(g(z) = \frac{e^z - e^{-z}}{e^z + e^{-z}}\) | \(g(z) = max(0, z)\) | \(g(z) = max(\epsilon z, z)\) with \(\epsilon \ll 1\) |
| Graph showing sigmoid curve | Graph showing tanh curve | Graph showing ReLU line | Graph showing Leaky ReLU line |

The Relu function is the most used function; it represents the identification of positive arguments and assigns zeros to others. In most early works, the hyperbolic tangent and the sigmoid function are often the most used. However, today these functions are no longer exploited because they require complex arithmetic and they present difficulties in the material implantation. In addition, the hyperbolic tangent does not represent a solution for the problem of vanishing gradient problem on the contrary to the Relu, which allows to reduce and relieve this problem (Clever & Unterthiner, 2016). The pooling operation
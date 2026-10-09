![](bbox=[0.18, 0.11, 0.82, 0.62])

**Figure 7.** Comparison of bottleneck modules in different networks: (a) ResNet Bottleneck, (b) SE Net Bottleneck, (c) CBAM Net Bottleneck, and (d) EPSA Net Bottleneck.

Next, we adopt two identical loss functions for each gaze angle in this study. Each loss function is a linear combination of cross-entropy loss and mean squared error. The cross-entropy loss is defined as follows:

```
$$H(y,p) = -\sum_{i} y_i log p_i \tag{15}$$
```

The cross-entropy loss is defined as follows:

```
$$MSE(y,p) = \frac{1}{N} \sum_{0}^{N} (y - p)^2 \tag{16}$$
```

The proposed loss function for each gaze angle is a linear combination of the mean squared error and cross-entropy loss, defined as follows:

```
$$CLS(y,p) = H(y,p) + \alpha \cdot MSE(y,p) \tag{17}$$
```

where $CLS$ is the overall loss, $p$ is the predicted value, $y$ is the true value, and $\alpha$ is the regression coefficient.
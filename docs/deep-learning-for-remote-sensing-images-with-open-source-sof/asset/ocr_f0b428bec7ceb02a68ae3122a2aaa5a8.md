provides another form of translation invariance. The pooling layer operates independently on every depth slice of the input and resizes it spatially. Like convolution with non-unitary stride, the pooling operators also modify the output size.

![](bbox=[0.28, 0.24, 0.7, 0.38])

# FIGURE 1.3

2 × 2 max pooling with stride 2. Each 2 × 2 sub-region of the image, the maximum value is kept.

> **Important note**
> Pooling, and convolutions with stride, can be viewed as a subsampling process, which does modify the output size, and the output physical spacing. Depending on the implementation, it can also keep partially sampled items at borders.

# 1.4 Activation functions

Inspired from biology, the activation functions are usually an abstraction representing the way a neuron will be activated (i.e. it will transmit its output value) or not. Basically, the activation functions control the amount of what is actually transmitted to output. There are many activation functions used in deep learning. Among these, we can enumerate the following, which are common ones we will use during this tutorial:

+   1. The rectified linear unit returns a maximum value between 0 and x:
+   
+      $$f(x) = max(0, x)$$<|message|>
+   2. A leaky rectified linear unit allows a small, positive gradient when the unit is not active. It is parametrized with α, a scalar value:
+   
+      $$f(x) = \begin{cases} x & \text{if } x > 0, \\ \alpha x & \text{otherwise,} \end{cases}$$ 
+   3. Sigmoid:
+   
+      $$f(x) = \frac{1}{1 + e^{-x}}$$
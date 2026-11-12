![](bbox=[0.15, 0.08, 0.85, 0.47])

Figure 5.21 Six activation functions commonly used in deep learning architectures [8].

Although this function is easy to use, it suffers from challenges when the gradient descent is applied in training the network as the step function is not differentiable. Sigmoid is another common activation function which follows the equation:

```
$$t = \sum_{i=1}^{n} W_i X_i \qquad s(t) = \frac{1}{1 + e^{-1}} \quad (5.5)$$
```

As the Sigmoid function is continuous, differentiable, and symmetric, it performs better than the step function for deep learning algorithms. However, it also suffers from some limitations: (i) Its outputs are not zero centered and (ii) the gradient will be degraded by saturated neurons due to extremely small delta for gradient. Having a similar shape to the Sigmoid, the hyperbolic tangent (tanh) is one of the extensively used activation functions as follows:

```
$$f(z) = tanh(z) = \frac{e^z - e^{-z}}{e^z + e^{-z}} \quad (5.6)$$
```

In contrary to Sigmoid, it is zero centered, but still the saturated neurons kill the gradients. The better choice rather than the previously mentioned functions is the rectified linear unit (ReLU) as:

```
$$f(x) = max(0, x) \quad (5.7)$$
```
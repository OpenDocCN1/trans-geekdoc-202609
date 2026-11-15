![](bbox=[0.22, 0.08, 0.79, 0.4])

Fig. 1.6 Sigmoid activation function

# ## 1.5.2 Hyperbolic Tangent Activation Function (Tanh | Hyperbolic Tangent)

The hyperbolic tangent function (Tanh) is also a nonlinear activation function that normalizes the input values to the interval (−1, 1). This function is usually used in neural networks to limit the output of inputs to values between −1 and 1. The output of the Tanh function is proportional to the range of the sigmoid function and reduces the problem of saturation of the outputs in the sigmoid function. The output of the Tanh function is compared to the fading problem. The gradient in zero regions is less sensitive and more useful. Among the limitations of this function, it can be mentioned that, like the sigmoid function, there may be a problem of gradient fading in the saturated areas of this function. Hyperbolic Tangent Activation Function shown in Fig. 1.7.

```
The formula of the hyperbolic tangent function is:

f(x) = (e^x - e^{-x})/(e^x + e^{-x}) (1.4)
```
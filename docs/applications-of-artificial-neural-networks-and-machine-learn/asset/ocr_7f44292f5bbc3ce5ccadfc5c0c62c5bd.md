![](bbox=[0.226, 0.082, 0.786, 0.402])

# Fig. 1.18 Randomized leaky rectified linear unit activation function

where

```
\alpha_{ij} \sim U(l, u), l < u \text{ and } l, u \in [0,1) (1.12)
```

where \((\alpha_{ij})\) is a random value of a specified interval that is different for each neuron in the neural network.

# 1.5.14 HardSwish Activation Function

HardSwish is an activation function that is a combination of ReLU and Linear functions and works in a non-linear way. This function is derived from the harder activity functions (hard) and is used to limit the range of input values to reasonable values.

Its advantages are avoiding the problem of gradient fading, normalization of input values, and better performance than other stiffness functions, as well as the least negative impact on network efficiency and speed. Among its limitations is the need for proper initialization for correct calculations. HardSwish Activation Function shown in Fig. 1.19.

The HardSwish formula is as follows:
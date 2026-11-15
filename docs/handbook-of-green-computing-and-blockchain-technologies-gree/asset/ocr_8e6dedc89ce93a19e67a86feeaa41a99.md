# 3.2.4 ACTIVATION FUNCTIONS

Activation functions are mathematical functions which determines the output of the neuron. Different activation functions are used for different types of problems and activation function used also depends whether problem is regression problem or classification problem. Gradient of weights and biases plays a very important role while choosing the activation function. Gradient is defined as rate of change in a variable respect to other variable and gradient of error with respect to weights and biases which we achieve after training is used to update biases and weights to reduce the error in prediction [2].

# 3.2.4.1 Linear Function

This is the simplest activation function where a constant is multiplied without variable.

```
z = ay

z' = a
```

Gradient of z with respect y shows a constant value which means the weights and biases will get update by a constant factor always and error will remain the same.

# 3.2.4.2 Sigmoid Function

The sigmoid function is a mathematical function which transforms the value between range [0,1] and it is a non-linear activation function.

```
z = \frac{1}{1 + e^{-y}}
```

```
z' = \frac{1}{1 + e^{-y}} * \left\{ 1 - \frac{1}{1 + e^{-y}} \right\}
```

Gradient of the sigmoid function shows the gradient is dependent on the variable y and as y tends to either +∞ or –∞ the gradient will become 0 and will be the same as the linear function gradient for higher values.

# 3.2.4.3 Hyperbolic Tangent Function

This is a non-linear function which is derived from the sigmoid function by making small changes in the sigmoid function.

```
z = 2 * \frac{1}{1 + e^{-2y}} - 1
```

This function gives range from [-1,1] and is symmetric about origin.

```
z' = 1 - \left\{ 2 * \frac{1}{1 + e^{-2y}} - 1 \right\}^2
```
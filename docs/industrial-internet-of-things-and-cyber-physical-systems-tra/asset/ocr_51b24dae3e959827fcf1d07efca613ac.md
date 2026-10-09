to a linear format we use one of the activation functions. The various commonly used activation functions are Sigmoid Function, Tanh Function, Relu (Rectified Linear Unit) Function, Leaky Relu, Elu and Maxout. The most commonly used one at present is Leaky Relu. Sigmoid and tanh kills the gradient to zero. Hence Relu was introduced.

# ## Sigmoid Function

Sigmoid Function is a squashing function which is used to squash the output between 0 and 1. When we have a data set which contains two classes, like 0 and 1, then we apply Sigmoid Function to predict the probability of the class. A typical Sigmoid Function appears as shown in Fig 3

![](bbox=[0.25, 0.37, 0.69, 0.59])

It is applied to every node in the neural network and computed using the equation

```
$$f(x) = \frac{1}{1+e^{-x}}$$
```

where x is the output of the neuron.

# ## Tanh Function

This is similar to the Sigmoid Function but the difference is the range of values is between -1 and 1. Fig 4 shows a tanh function

The function is given as

```
$$\tanh(x)=\frac{\sin(x)}{\cos(x)}=\frac{e^{x}-e^{-x}}{e^{x}+e^{-x}}$$
```
![](bbox=[0.21, 0.08, 0.79, 0.4])

# Fig. 1.4 Binary step function

# 1.4.2 Linear Activation Function

The linear activation function is the simplest activation function that does not add any nonlinearity to the model. This function is typically used in output layers of models and returns the output as the input. This function is used alone for modeling patterns with low complexity. Linear Activation Function is shown in Fig. 1.5.

The mathematical function of this activator is as follows:

```
f(x) = x
(1.2)
```

Some of the problems of this method can be mentioned such as: The linear activation function does not add any nonlinearity to the model, so it is not enough to solve complex problems and the capability of the neural network model. Also, if the linear activation function is used in all layers, the model does not have the ability to model more complex patterns and features. Also, the models that use the linear activation function may not be able to understand complex and diverse patterns and do not have good efficiency and performance. This function cannot be used in the back propagation step because the derivative of this function is equal to a fixed number. And it has no relationship with the input value x. The result of several linear functions on a fixed input value is the same. Therefore, it does not matter if the neural network is made of several hidden layers; because the output of the activation function in the last layer of the neural network is equal to the output of the activation function in the first layer [13].
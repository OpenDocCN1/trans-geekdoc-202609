![](bbox=[0.226, 0.085, 0.786, 0.396])

Fig. 1.5 Linear activation function

# 1.4.3 Non-linear Activation Function

Nonlinear activation functions are used in neural networks to generate nonlinearity and deregularization in information. The non-linearity of these functions allows the network to be able to model more complex and non-linear patterns, which allows for improved network performance. The generalizability and adaptability of the model to different types of data is facilitated by the use of nonlinear activation functions. The use of nonlinear activation functions in neural networks adds an extra step to the calculations of each layer in the feedforward propagation step; but this extra step has an important advantage. If there is a neural network without activation functions, each node simply performs linear computations on its inputs using values of weights and biases. In this case, the number of hidden layers in the neural network is not important and all layers have the same function because the result of combining two linear functions will be a linear function.

Some of the problems of this method can be mentioned such as: it may be more complex than needed for some simple problems and cause the problem of gradient fading or overfitting. Also, some nonlinear activation functions such as the sigmoid function may not help as much as it should when facing the problem of gradient fading and slow down the learning and improvement of the network. Therefore, the correct selection of the nonlinear activation function is very important, [14] and [15].
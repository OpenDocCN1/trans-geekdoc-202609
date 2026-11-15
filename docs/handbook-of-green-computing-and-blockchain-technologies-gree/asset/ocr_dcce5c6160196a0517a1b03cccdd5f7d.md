![](bbox=[0.26, 0.09, 0.75, 0.39])

FIGURE 3.3 Forward propagation.

sum with addition of bias and then passing it to the activation function. The output is given to each neuron in the next layer [3] (Figure 3.3).

Yellow, pink, and blue arrows show how the data is transmitted in the forward propagation.

# 3.3.2 BACKWARD PROPAGATION

This is the reverse process of forward propagation where process goes in backward direction. Backward propagation is based on the principle of error where we first calculate error in our prediction, then we try to propagate backward and check how the error is affected by specific neurons’ weights and bias by calculating the gradient of error in relation to the variable weights and bias and then update them accordingly [4].

Let's consider an example in Figure 3.4:

Blue arrows show how data is transmitted from the output layer to hidden layer with pink-colored neurons. Let's find the loss function which is defined as square of difference in actual value and predicted value.

$E = \{z_p - z_a\}^2$

$z_p$ is the value predicted by the neural network and $z_a$ is the actual value expected at the output, where $z_a$ is a constant and $z_p$ is calculated using the activation formula in last neuron.

$z_p = \text{Activation}(y_p)$

$y_p = \sum w_i x_i + b$

```python
def f(x):
    return x**2
```

```python
# Find the minimum value
result = optimize.minimize(f, x0=0)
print(result)
```

This code uses the "minimize" function to find the minimum value of the function $f(x) = x^{2}$. There are also several types of optimization problems. For example, there are problems with finding the minimum and maximum values and problems with constraints. The SciPy library provides functions for each of these types. By using the corresponding functions, you can solve optimization problems.

## 2.7. NNs

This document uses a regression model to build a spatiotemporal model from physical data. In this model, regression tries to match the given physical data as accurately as possible, but unlike interpolation, the regression model is not a perfect fit for the data. It does, however, learn features from the data. In this section, we employ NNs as the regression method. While various structures have been proposed for NNs, we focus here on FCNN (Fully Connected NN) (Figure 2.26). An FCNN consists of an input layer, a hidden layer, and an output layer. Each layer has a specific number of neurons. The output value of each neuron is calculated by the inner product of a vector consisting of the input values and a vector consisting of the weights. Therefore, the mapping from the input layer to the output layer ultimately yields the desired output value. An FCNN is a neural network in which every neuron is connected to all neurons in the previous layer. It is also called a densely connected neural network, a fully connected neural network, or a multilayer perceptron (MLP).

FCNNs have a large number of weight parameters between the input and output because each layer is connected to all neurons in the immediately preceding layer. This structure allows it to hold a very large number of parameters from the input to the output layer and, therefore, has a high expressive capability. However, a large number of layers or neurons can cause slow learning or overlearning problems. In this document, NN shall mean FCNN.

![](img/fa57e7010b16a211d5cf69ebb17e416e_90_0.png)

In neural networks, learning is the process of automatically adjusting parameters such as weights and biases of a neural network using training data. Through this process, the neural network builds a model that is optimized by the training data.

Neural network training is divided into two main steps: “forward propagation” and “back propagation”. Forward propagation is a step in which the process from the input layer to the output layer is executed in sequence, with the input data passing through the network to produce the output. Back propagation is the step in which the error is back propagated from the output layer to the input layer, updating weights and biases to minimize the error.

Specifically, for training, a measure called the loss function is defined, and weights and biases are updated to minimize the difference between the neural network's output and the ground truth data. Therefore, the neural network is adjusted to fit the training data. Regularization techniques, dropouts, and other methods may also be used to prevent overlearning.

Once sufficiently trained, neural networks can achieve high predictive accuracy for unknown data. Learning in neural networks is a type of optimization. Learning in neural networks aims to obtain optimal prediction results by using training data and adjusting parameters such as weights and biases. Now, assume that the NN consists of $L$ layers and that $n_{i}$ neurons are defined in layer $i$. The number of parameters to be optimized can be calculated as follows:

$$\sum_{i=1}^{L+1}(n_{i}+1)n_{i+1} \tag{2.24}$$

In this equation, $i=1$ represents the input variable, so $n_{1}=4$ for space-time coordinates. The addition of 1 is due to the inclusion of bias as a type of weight. Also, $i=L+2$ represents the output variable, so $n_{L+2}=1$ for scalar data. Figure 2.26 shows an NN consisting of $L$ layers.

Weights are defined on arcs connected to the neurons and output variables. For small NNs, we focus on clarity and explain how to optimize the weights using the Excel Solver. For practical use, we will use keras and other libraries introduced in Chapter 1.

The learning process searches for parameter values that minimize the loss function in order to minimize the difference between the output of the neural network and the ground truth data. This search process is performed using optimization algorithms (e.g., gradient descent method).

As the learning progresses, the parameters are updated, and the value of the loss function is reduced to obtain the optimal parameters. Using these optimal parameters, the neural network can achieve high prediction accuracy for unknown data.

### 2.7.1. Universal approximation theorem

The universal approximation theorem is a theorem that states that an NN can approximate any continuous function with any precision. In other words, a properly designed NN can approximate a desired output for any given input.

This theorem is one of the reasons why NNs have become widely used and is the basis for demonstrating their usefulness. In practice, however, it is not always easy to achieve, as it requires a sufficient number of neurons, appropriate algorithms, datasets, etc., to be able to approximate with any precision that the theorem suggests.

The universal approximation theorem was first proposed in 1989 in the paper "Multi-Layer Feedforward Networks are Universal Approximators" by George Cybenko and Edward G. Widrow [23]. This paper was published in the IEEE Transactions on Neural Networks and Learning Systems and later became an important foundation for the theory of neural networks. In this paper, George Cybenko and Edward G. Widrow proved that there exist neural networks that can approximate any continuous function with any precision. They showed that this theorem made neural networks very powerful and led to the widespread use of neural networks.

The existence of a neural network that can approximate any continuous function with any precision can be proved as follows:

- First, a neural network with one single sigmoid function can approximate a Lipschitz continuous function. A Lipschitz continuous function is a function with a rate of change bounded by some constant, and it is possible to approximate such a function.
- Second, a neural network with multiple sigmoidal functions can approximate any Lipschitz continuous function. This is because each layer takes the previous layer's output as input, thus allowing more complex functions to be represented.
- Finally, any continuous function can be represented as the sum of an infinite number of Lipschitz continuous functions. This means that a neural network with multiple sigmoidal functions can be used to approximate any continuous function with any precision.

Therefore, a Lipschitz continuous function is a continuous function in which a constant $L$ exists, and the following equation holds for the function $f$:

$$| f(x) - f(y) | \le L | x - y | \tag{2.25}$$

In this equation, $x$ and $y$ represent any two points within the domain of the definition of $f$, and $| \cdot |$ represents the absolute value. This definition indicates that "the change in the value of $f$ is bounded in proportion to the change in its argument". In other words, the closer $x$ and $y$ are to each other, the smaller the difference between $f(x)$ and $f(y)$.

Lipschitz continuous functions play an important role in calculus, functional analysis, and other areas of mathematics. They are also used in various fields, such as physics, engineering, and economics.

As shown above, a neural network with one sigmoidal function approximates a Lipschitz continuous function, and a neural network with multiple sigmoidal functions can approximate any Lipschitz continuous function. Therefore, any continuous function can be approximated with any precision.

### 2.7.2. Regression analysis using NNs

To explain the regression analysis using NNs, we use as discrete data the bivariate data described in Section 5, paragraph 2. These data are calculated from the bivariate function

$$y = x_{1}^{2} + x_{1} + x_{2}^{3} + x_{2}^{2}.$$ (2.26)

The mean squared error of the model

$$y = w_{0} + w_{1}x_{1} + w_{2}x_{2},$$ (2.27)

created by linear regression from 26 discrete data randomly selected from $\{(x_{1}, x_{2})|0 \leq x_{1} \leq 1, 0 \leq x_{2} \leq 1\}$, was $0.0402$. Using the coefficients $w_{0}, w_{1}, w_{2}$ as parameters, the parameters that minimize the mean square error between the spatiotemporal model and the given discrete data were calculated using the Excel Solver function.

In the previous section, we discussed specific ways to achieve regression analysis using the Solver. In this section, we will use the same data to explain how to achieve an NN model by using Solver. A simple NN model can be realized as an activation function connected to the output of this linear regression model. This time, we use the Sigmoid function

$$\sigma(x) = \frac{1}{1 + e^{-x}}$$ (2.28)

and assume that the output obtained using this function in the Excel sheet function is scale converted to

$$y = (y_{max} - y_{min})\frac{1}{1 + e^{-(w_{0} + w_{1}x_{1} + w_{2}x_{2})}} + y_{min}$$ (2.29)

$\Delta y = \frac{(y_{max} - y_{min})}{\Delta y}$ to calculate the mean squared error between $y = \frac{1}{1 + e^{-(w_{0} + w_{1}x_{1} + w_{2}x_{2})}} + y_{min}$ and the given discrete data $y_{i}.$

$$\sum_{i=1}^{26} \left(y_{i} - \frac{\Delta y}{1 + e^{-(w_{0} + w_{1}x_{1} + w_{2}x_{2})}} - y_{min}\right)^{2}$$ (2.30)

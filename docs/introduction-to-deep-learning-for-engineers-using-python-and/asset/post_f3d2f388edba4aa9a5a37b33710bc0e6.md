
![](img/194138d45b566d0634bfa2025ddf48f7_35_0.png)

Figure 3.1: Multi-layer neural network architecture with two hidden layers.

correct results of the example dataset are unknown. And, the reinforcement learning are used when learning through observations from a complex environment is required. Here, the model makes a final decision based on the penalties or rewards it received for its performance.

The selection of these schemes depends on the types of dataset and output requirements for a particular task.

## 3.2 APPLICATIONS

The artificial neural network is very effective in function approximations, identifying patterns, and implementing complex mapping. Recently, it has been used in diverse science, engineering, art, and medical applications. It is also widely used for forecasting and predicting many real-life businesses, economic and social issues [7–10]. In Chapter 7, we provided a case study of a multiclass classification problem where the model learns from 8,144 car images to determine car model, make, and year.

![](img/194138d45b566d0634bfa2025ddf48f7_36_0.png)

**Figure 3.2:** Computational steps inside one neuron of the hidden layer. Here, σ(z) is the sigmoid activation, x₁, x₂, x₃ are inputs to the neuron, w₁, w₂, w₃ are the weights, and b is the bias to the input.

## 3.3 NEURONS AND ACTIVATION FUNCTIONS

Many internal parameters can influence the output found from an artificial neural network. But generally, outputs are directly related to the number of neurons and their activation functions.

The neurons are the nodes, typically shown by circles that are arranged inside the layers. Inside a layer, these neurons take input weights from all connections and add a bias, initializes these parameters, and then calculates the output using another function known as an activation function. The mathematical operations happening inside each layer amplify dramatically as the neurons and connections are increased. Figure 3.1 shows a simple neural network when we have two hidden layers, and each of them containing four neurons. Figure 3.2 focuses on the operations happening inside one of the neurons of hidden layer 1.

This operation can be divided into two steps of computations. First, **Z** is calculated using the weights (**W**), bias (**b**), and inputs (**x**). Second, the activation function **σ** is calculated using **Z**. We could simply say that output of a neuron is a function of a function. In Fig 3.2, a sigmoid activation function is shown as an example.

The sigmoid activation function (shown in Fig. 3.2) has the ability to map any predicted value between 0 and 1. This output can be used to estimate the probability, where a threshold or tipping point (e.g., 0.5) is used for binary classification problems. For example, if *output* ≥ 0.5, class = 1 and if *output* < 0.5, class = 0. There are many other types of activation functions available for an artificial neural network. It is one of the important selection parameters that dictate the computational efficiency.

![](img/194138d45b566d0634bfa2025ddf48f7_37_0.png)

Figure 3.3: Plot of Sigmoid activation function in between −5 to +5.

The use of sigmoid activation in a deep neural network is minimal, and most of the time, nonlinear activations such as tanh, ReLU, and Softmax are used. It is important to note that different types of activations can exist in the neurons of the hidden and output layer. Only the input layer neurons don't have activation functions. The derivatives of activation functions also play an important role as they are used in the backpropagation error calculation during gradient descent. A short description of typical activation functions and their derivatives are given in the following sections for reference.

### 3.3.1 SIGMOID ACTIVATION

The sigmoid activation and its derivative are defined by Equations (3.1) and (3.2), respectively:

$$\sigma(z) = \frac{1}{1 + e^{-z}} \tag{3.1}$$

and

$$\sigma'(z) = \sigma(z)(1 - \sigma(z)). \tag{3.2}$$

This function is also known as the logistic regression function. We can use it when we need to determine the probability between 0 and 1. Sometimes, the sigmoid function exists only in the output layer of a neural network for doing the binary classification. A plot of sigmoid function in the range of −5 to 5 is given in Fig. 3.3.

### 3.3.2 HYPERBOLIC TANGENT ACTIVATION

Hyperbolic tangent, also known as tanh function and its derivative are defined by Equations (3.3) and (3.4), respectively:

$$\sigma(z) = \frac{e^{z} - e^{-z}}{e^{z} + e^{-z}} \tag{3.3}$$

![](img/194138d45b566d0634bfa2025ddf48f7_38_0.png)

Figure 3.4: Plot of hyperbolic tangent activation function in between −5 to +5.

and

$\sigma'(z) = (1 - \sigma(z)^2).$ \tag{3.4}

This function performs better than the sigmoid function when the output is a large negative number. This function can also map numbers between −1 to +1. A plot of hyperbolic function in the range of −5 to 5 is given in Fig. 3.4.

### 3.3.3 RECTIFIED LINEAR UNITS (RELU) ACTIVATION

The Rectified Linear Units, also known as ReLU activation, and its derivatives are defined by Equations (3.5) and (3.6), respectively:

$$\sigma(z) = \begin{cases} 0 & \text{for } z \le 0 \\ z & \text{for } z > 0 \end{cases} \tag{3.5}$$

and

$$\sigma'(z) = \begin{cases} 0 & \text{for } z < 0 \\ 1 & \text{for } z \ge 0 \end{cases} \tag{3.6}$$

The ReLU function updates parameters faster as its gradient calculation is simpler compared to other activations. A plot of ReLU function in the range of −1 and +1 is given in Fig. 3.5.

### 3.3.4 LEAKY RECTIFIED LINEAR UNITS (LEAKY RELU) ACTIVATION

The Leaky Rectified Linear Units, also known as Leaky ReLU, is a type of improved ReLU activation that doesn’t have 0 slopes for negative values. Leaky ReLU and its derivatives can be

![](img/194138d45b566d0634bfa2025ddf48f7_41_0.png)

Figure 3.8: Plot of Softplus activation function in between −5 to +5.

Finding out the appropriate activation function for a model is a challenge due to very small gradients during the backpropagation steps. This phenomenon is also known as diminishing gradients. Besides the activation functions shown here, many other functions are continuously being explored and added in the field of machine learning. For example, ArcTan, Piecewise Linear Unit (PLU), Scaled Exponential Linear Unit (SELU), Inverse Square Root Unit (ISRU), etc. A comprehensive list of activation functions can be found on the Wikipedia page [11].

## 3.4 MINIMIZING THE LOSS FUNCTION

The loss function is the quantity that will be minimized during training [5]. It is also known as the objective function or error function. A neural network may have multiple loss functions based on the number of outputs. A classification model should have a cross-entropy loss or a log loss of 0. Generally, for a two-class classification problem binary cross-entropy, and for multiclass classification problems, categorical cross-entropy is used. The learning process of a neural network is basically finding out weights and biases to minimize the loss function.

Typically, the loss function is also called cost function if the error is calculated for the entire training set or a batch. The standard binary cross-entropy loss function can be defined by Equation (3.13) [12]:

$$J = -\frac{1}{M} \sum_{m=1}^{M} [y_m \times \log\big(h_\theta(x_m)\big) + (1 - y_m) \times \log\big(1 - h_\theta(x_m)\big)] , \qquad (3.13)$$

where $M$ = number of training examples, $y_m$ = target label for training example $m$, $x_m$ = input for training example $m$, $h_\theta$ = model with neural network weights $\theta$. For categorical targets if $\hat{y}_1 \dots \hat{y}_m$ are the probabilities of the “$m$” classes, and the $r$th class is the ground-truth class, then the loss function for a single instance is defined by Equation (3.14) [13]:

$$J = -\log(\hat{y}_r).$$ \hfill (3.14)

![](img/194138d45b566d0634bfa2025ddf48f7_42_0.png)

**Figure 3.9:** If the initial starting point is Start Point 1, the gradient descent algorithm will converge to a local minima. On the other hand, if the Start Point 2 is used, the algorithm will converge to the global minima.

The goal of any neural network is to minimize Equation (3.14). This minimization process is done by updating weights using an optimization function or optimizer. An important iterative algorithm known as backpropagation is used to apply this optimization, and in this process, the loss function dictates how well the network is learning.

Many different optimizers have been used in artificial neural networks such as gradient descent, gradient descent with momentum, Root Mean Square Propagation (RMSProp), Adam optimizers, and so on. The selection of a suitable optimizer depends on the computational scenario, and they typically differ in terms of their simulation speed and convergence ability.

## 3.5 GRADIENT DESCENT ALGORITHM

The gradient descent is an iterative first-order optimization algorithm that helps the neural network to minimize the cost function, $J$. In the case of linear regression, we can use derivatives to find a minimum of convex functions. But in the artificial neural network, we always deal with a non-convex function, and therefore gradient descent algorithm can end up finding the local minima instead of global minima.

Figure 3.9 shows how the gradient descent can end up in different minima based on the starting point. This example is for only one weight parameter, $\omega$. For a 3D surface plot where the cost function $J$ is a function of two parameters ($\omega$ and $b$) and forms a non-convex shape, the gradient descent algorithm may converge to a local minima instead of a global one as shown

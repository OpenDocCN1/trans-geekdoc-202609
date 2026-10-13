
# Activation Functions

In summary, the activation of a neuron is determined by the activation function. It decides the importance of input to predict the output and transforms the weighted sum of the input of the nodes in a layer into an output. Thus, during the forward propagation, the activation function adds non-linearity to the model by creating an extra task at each layer.

Generally, all hidden layers in a neural network use the same activation function. This should be differentiable to learn the parameters during backpropagation. The activation function used in hidden layers is selected considering the type of the model. In most cases, the hidden layers use `ReLU` activation. `Sigmoid` and `Softmax` activation is used for the output layer in binary classification and multi-class classification, respectively. The selection of an activation function should consider vanishing and exploding gradient issues.

Following are some of the widely used non-linear activation functions.

## 1. ReLU (Rectified Linear Unit)

The rectified linear activation function (`ReLU`) is a default activation function that activates only a set of neurons at a time. It is a piecewise linear function. If the input is a positive value, the function outputs the input directly. If the input is a negative value, it outputs zero representing deactivation. As shown in [Figure 2.8](#ch09.xhtml#f16), this gives the `max(x, 0)`. Thus, the weights and biases for some neurons do not update during the backpropagation, which increases the efficiency of the computation process. Because of its characteristics such as easy computation, and not saturating, `ReLU` is commonly used in hidden layers. Following are the advantages (+) and disadvantages (–) associated with the `ReLU` function.

*   **+** Computationally efficient, as only a set of neurons are activated.
*   **+** The associated linear and non-saturating nature accelerates the convergence of gradient descent towards the global minimum of the loss function.
*   **+** Since the derivative is 1 or 0, the weight is updated and reaches convergence; hence does not cause a vanishing gradient problem.
*   **–** Dying `ReLU` problem (dead activation function). Since the derivative of `ReLU` is 0 or 1, if a derivative is zero, then the new weight is the same as the old weight.
*   **–** Some neurons do not learn as `ReLU` is not symmetrical around zero and the output is zero for all negative inputs.

## 2. Leaky ReLU

`Leaky ReLU` is an extension of `ReLU`. It addresses the dying `ReLU` problem as it contains a slight positive slope for the negative region as shown in [Figure 2.9](#ch09.xhtml#f17). The leaky `ReLU` design increases the range of the `ReLU` activation function to become more responsive towards the negative inputs to solve the limited range and impulsive behavior. Further, it preserves the monatomic and differentiable nature of the `ReLU`.

![Figure 2.9 Leaky ReLU activation function.](html/images/9781032473246_C002_009.jpg)

[Figure 2.9](#ch09.xhtml#f17b) Leaky ReLU activation function.

## 3. Sigmoid/Logistic Activation Function

For any real value input, the sigmoid function outputs values between 0 and 1. When the input is more positive, the output becomes closer to 1. For negative inputs, the output becomes closer to 0. This function is mostly used for the output layer in binary classification. Generally, in a normal distribution (or Gaussian distribution) the data is zero-centered with mean 0 and variance 1, which resulted in a bell-shaped curve. However, as shown in [Figure 2.10](#ch09.xhtml#f18), in sigmoid, the data is not 0 centered; hence consumes more computational time and takes more time to reach the convergence and to reach global minima.

![Figure 2.10 Sigmoid activation function.](html/images/9781032473246_C002_010.jpg)

[Figure 2.10](#ch09.xhtml#f18b) Sigmoid activation function.

Following are the advantages and disadvantages of the sigmoid function.

*   **+** Commonly used for models that need to predict the probability as an output. Since the probability of anything exists only between the range of 0 and 1, sigmoid is the right choice because of its range.
*   **+** The function is differentiable and provides a smooth gradient in S-shape by preventing jumps in output values.
*   **–** The sigmoid function gets negligible gradients for values higher than 3 or lower than -3. Thus, the model does not learn and faces the vanishing gradient problem, when the gradient value is closer to 0.
*   **–** Difficult to train and the model becomes unstable since the output is not symmetric around zero and the output of all the neurons will be of the same sign.
*   **–** Takes more time to converge.

## 4. Softmax Activation Function

The `Softmax` function is used in the last layer of the neural network with multi-class classification. This is described as a set of sigmoid functions, which returns the probability of each class. This activation function is more of a generalized form of the sigmoid function and produces values in the range of 0–1. It transforms the (unnormalized) output of *K* units of a fully connected layer to a probability distribution (a normalized output).

## 5. Tanh Activation Function

`Tanh` activation function, as shown in [Figure 2.11](#ch09.xhtml#f19), is a more effective function than `ReLU` and sigmoid, since it is zero-centered. In the tanh graph, the negative and zero inputs are mapped to strongly negative and near zero, respectively. This is mainly used in feed-forward neural networks with binary classification. The `tanh` function is mainly used for classification between two classes. The advantages and disadvantages of the `tanh` activation function are as follows.

![Figure 2.11 Tanh activation function.](html/images/9781032473246_C002_011.jpg)

[Figure 2.11](#ch09.xhtml#f19b) Tanh activation function.

*   **+** Since the function output is zero-centered, the output values are mapped as strongly negative, neutral, or strongly positive.
*   **+** The values fit between –1 and 1, `tanh` is generally used in hidden layers. Since the mean for the hidden layers becomes 0 or close to 0, it supports the center of the data and makes the learning process of the next layer easier.
*   **+** Although this faces vanishing gradient issues since the function is zero-centered, the gradients can move in certain directions. Thus, widely used in practice.
*   **–** The gradient of the `tanh` activation function faces the vanishing gradient problem. This gradient is much sharper than the gradient of the sigmoid function.

# 2.4.4 Learning Rate

The learning rate is a hyperparameter that impacts the training of a model. It addresses the model change, as a reaction to the estimated loss when the model weights are updated. Thus, the learning rate supports adjusting the weight updates, such that it reduces the loss. A traditional default value for the learning rate is 0.1 or 0.01. When the learning rate is set to very low, then the training process progresses slowly with small updates to the weights, as shown in [Figure 2.12](#ch09.xhtml#f20). Similarly, when the learning rate is very high, the loss function behaves differently.

![Figure 2.12 Types of learning rates.](html/images/9781032473246_C002_012.jpg)

[Figure 2.12](#ch09.xhtml#f20b) Types of learning rates.

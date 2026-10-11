
# Perceptron

A Perceptron is a neural network unit that does certain computations to detect features or business intelligence in the input data. It is a function that maps its input “x,” which is multiplied by the learned weight coefficient, and generates an output value, “f(x).”

![Perceptrons - These Artificial Neurons Are The Fundamentals Of Neural Networks – Fly Spaceships With Your Mind](image_rsrc9XJ.jpg)

**Fig. 6.2** Perceptron in neural network

## Types of Perceptron Models

1.  **Single Layer Perceptron Model**: One of the easiest ANN (Artificial Neural Networks) types consists of a feed-forward network and includes a threshold transfer inside the model. The main objective of the single-layer perceptron model is to analyze the linearly separable objects with binary outcomes. A Single-layer perceptron can learn only linearly separable patterns.

2.  **Multi-Layered Perceptron Model**: It is mainly similar to a single-layer perceptron model but has more hidden layers.

    *   **Forward Stage**: From the input layer in the on stage, activation functions begin and terminate on the output layer.
    *   **Backward Stage**: In the backward stage, weight and bias values are modified per the model’s requirement. The backstage removed the error between the actual output and demands originating backward on the output layer. A multilayer perceptron model has a greater processing power and can process linear and non-linear patterns. Further, it also implements logic gates such as `AND`, `OR`, `XOR`, `XNOR`, and `NOR`.

## Advantages

*   A multi-layered perceptron model can solve complex non-linear problems.
*   It works well with both small and large input data.
*   Helps us to obtain quick predictions after the training.
*   Helps us obtain the same accuracy ratio with big and small data.

## Disadvantages

*   In multi-layered perceptron model, computations are time-consuming and complex.
*   It is tough to predict how much the dependent variable affects each independent variable.
*   The model functioning depends on the quality of training.

## Characteristics of the Perceptron Model

The following are the characteristics of a Perceptron Model:

1.  It is a machine learning algorithm that uses supervised learning of binary classifiers.
2.  In Perceptron, the weight coefficient is automatically learned.
3.  Initially, weights are multiplied with input features, and then the decision is made whether the neuron is fired or not.
4.  The activation function applies a step rule to check whether the function is more significant than zero.
5.  The linear decision boundary is drawn, enabling the distinction between the two linearly separable classes +1 and -1.
6.  If the added sum of all input values is more than the threshold value, it must have an output signal; otherwise, no output will be shown.

## Limitation of Perceptron Model

The following are the limitations of a Perceptron model:

1.  The output of a perceptron can only be a binary number (0 or 1) due to the hard-edge transfer function.
2.  It can only be used to classify the linearly separable sets of input vectors. If the input vectors are non-linear, it is not easy to classify them correctly.

## Perceptron Function

Perceptron is a function that maps its input “x,” which is multiplied with the learned weight coefficient; an output value ”f(x)” is generated.

![](image_rsrc9XK.jpg)

In the equation given above:

*   **“w”** = vector of real-valued weights
*   **“b”** = bias (an element that adjusts the boundary away from origin without any dependence on the input value)
*   **“x”** = vector of input x values

![](image_rsrc9XM.jpg)

*   **“m”** = number of inputs to the Perceptron

The output can be represented as “1” or “0.” It can also be represented as “1” or “-1” depending on which activation function is used.

# 6.3 Feedforward Neural Network

Feed forward neural networks are artificial neural networks in which nodes do not form loops. This type of neural network is also known as a multi-layer neural network as all information is only passed forward. During data flow, input nodes receive data, which travel through hidden layers, and exit output nodes.

![](image_rsrc9VX.jpg) ![undefined](image_rsrc9XN.jpg)

**Fig. 6.3(a)** Structure of a feedforward neural network

In a feedforward network, information always moves one direction; it never goes backwards.

## Neural Network Architecture and Operation

Before we look at why neural networks work, it’s important to understand what neural networks do. Before we can grasp the design of a neural network, we must first understand what a neuron performs.

A weight is assigned to each input to an artificial neuron. First, the inputs are multiplied by their weights, and then a bias is applied to the outcome. After that, the weighted sum is passed via an activation function, being a non-linear function.

![Artificial Neural Network](image_rsrc9XP.jpg)

**Fig. 6.3(b)** Architecture of Artificial Neural Network

A weight is being applied to each input to an artificial neuron. First, the inputs are multiplied by their weights, and then a bias is applied to the outcome. This is called the weighted sum. After that, the weighted sum is processed via an activation function, as a non-linear function.

The first layer is the input layer, which appears to have six neurons but is only the data that is sent into the neural network. The output layer is the final layer. The dataset and the type of challenge determine the number of neurons in the final layer and the first layer. Trial and error will be used to determine the number of neurons in the hidden layers and the number of hidden layers.

All of the inputs from the previous layer will be connected to the first neuron from the first hidden layer. The second neuron in the first hidden layer will be connected to all of the preceding layer’s inputs, and so forth for all of the first hidden layer’s neurons. The outputs of the previously hidden layer are regarded inputs for neurons in the second hidden layer, and each of these neurons is coupled to all of the preceding neurons.

## What is a Feed-Forward Neural Network and how does it work?

In its most basic form, a Feed-Forward Neural Network is a single layer perceptron. A sequence of inputs enter the layer and are multiplied by the weights in this model. The weighted input values are then summed together to form a total. If the sum of the values is more than a predetermined threshold, which is normally set at zero, the output value is usually 1, and if the sum is less than the threshold, the output value is usually -1. The single-layer perceptron is a popular feed-forward neural network model that is frequently used for classification. Single-layer perceptrons can also contain machine learning features.

![Feed-Foward Network](image_rsrc9XR.jpg)

**Fig. 6.3(c)** Operation of feedforward neural network

The neural network can compare the outputs of its nodes with the desired values using a property known as the delta rule, allowing the network to alter its weights through training to create more accurate output values. This training and learning procedure results in gradient descent. The technique of updating weights in multi-layered perceptrons is virtually the same, however, the process is referred to as back-propagation. In such circumstances, the output values provided by the final layer are used to alter each hidden layer inside the network.

## Applications of the Feed Forward Neural Networks

1.  A Feed Forward Neural Network is an artificial neural network in which the nodes are connected circularly.

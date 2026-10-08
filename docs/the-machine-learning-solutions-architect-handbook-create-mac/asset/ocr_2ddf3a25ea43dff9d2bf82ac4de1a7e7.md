# Multi-layer perceptron (MLP) network

As mentioned in the beginning, an artificial neural network (ANN) mimics how the human brain learns. The human brain has a huge number of neurons that are connected in a network to process information. Each neuron in a network processes inputs (electrical impulses) from another neuron, processes and transforms the inputs, and sends the output to neurons in the network. The following figure shows a picture of a human neuron:

![](bbox=[0.137, 0.259, 0.862, 0.523])

Figure 3.5 – Human brain neuron

An artificial neuron works similarly. The following figure shows an artificial neuron, which is mathematically a linear function plus an action function. An activation function transforms the output of the linear function, such as compressing the value between 0 and 1 (sigmoid activation), -1 and 1 (tanh activation), or greater than 0 (ReLU). The idea for the activation function is to learn the non-linear relationship between input and output. You can also think of each neuron as a linear classifier, for example, logistic regression. The following figure shows the structure of an artificial neuron:
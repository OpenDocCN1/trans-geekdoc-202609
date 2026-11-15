![](bbox=[0.23, 0.1, 0.72, 0.255])

Figure 2.3 Schematic diagram of three-layer feedforward neural network.

the second layer is a hidden layer, containing four neurons; and the third layer is an output layer, containing two neurons. Neurons in two adjacent layers are connected to each other, and neurons in the same layer are not connected. The input layer and hidden layer of the network are used as an example to describe the formula of fully connection:

$$\hat{y}_j = \text{sigmoid}(\sum_{i=1}^3 w_{ij}x_i + b_j), \quad (2.2)$$

where \(w_{ij}\) represents the weight value between the \(i\)th neuron in the input layer and the \(j\)th neuron in the hidden layer, and \(x_i\) represents the numerical value of the \(i\)th element in the input column vector. These two values are multiplied and added to the bias \(b_j\) of each neuron in the hidden layer, and the resulting value is processed by the activation function sigmoid. Therefore the output \(\hat{y}_j\) of each neuron in the hidden layer can be obtained.

In practical applications, the number of hidden layers can be increased, and the way that the hidden layers are connected will also change, which is the deep neural network to be mentioned later.

# 2.2 Deep neural networks

# 2.2.1 Convolutional neural networks

As we mentioned in the previous section, the input to the feedforward neural network is vector data, which will be subjected to feature extraction in multiple hidden layers. Each hidden layer is made up of several neurons, and each neuron is connected to all neurons in the previous layer. The final fully connected layer is called the output layer, and its output values are considered to be the score values for different categories in classification
On the other hand, a synthetic neural network called an artificial neural network (ANN) was used to overcome problems with AI (Olaleye et al., 2022).

Biological neuron connections are modeled by ANNs as weights between nodes, where an excitatory link represents a positive link, and an inhibitory link represents a negative link (Kassaymeh, 2022).

Each input of the prominent attributes is assigned a weight before being added together. The mathematical model of a free-forward ANN is presented as follows.

# 17.3.3.2 Free-Forward Artificial Neural Network Mathematical Model

Let:

+   - x1, x2, . . . , x11: predictive attributes to approximate the target variable y
+   - y: the target variable (1 if the URL is phishing; 0 if otherwise)

The feed-forward neural network consists of three layers. The input layer has n neurons corresponding to the n input features, where n = 11 in this case.

# 17.3.3.2.1 Hidden Layer

The hidden layer has m neurons, where m is a hyper-parameter that must be chosen. We use a hyperbolic tangent (tanh) activation function for the hidden layer neurons.

# 17.3.3.2.2 Output Layer

The output layer has one neuron corresponding to the binary response variable y, and we used a sigmoid activation function for this neuron.

# 17.3.3.3 Mathematical Representation of the Artificial Neural Network Model

# 17.3.3.3.1 Input layer

For a given input feature vector x = [x1, x2 . . . x11], the input layer neurons are just the input features themselves. Therefore, the input layer can be represented as Equation 17.13:

a (0) = x  (17.13)

# 17.3.3.3.2 Hidden Layer

The output of each neuron in the hidden layer can be calculated by applying a weighted sum of the input features and adding a bias term, followed by the activation function.

We used a tanh activation function for the hidden layer neurons. Therefore, the hidden layer can be represented as Equation 17.14:

z (1) = W (1) a (0) + b (1) a (1) = tanh (z (1))  (17.14)

where W (1) is an m × n weight matrix that contains the weights of the connections between the input layer and the hidden layer, and b (1) is an m-dimensional bias vector.
![](bbox=[0.306, 0.196, 0.693, 0.417])

Figure 9.2: Two layer neural network classification with a set of hidden neurons using the sigmoid activation function.

and the learning rate $\eta > 0$. If the network currently classifies the sample incorrectly, the adjustments are larger. The closer $y(\mathbf{x}, \mathbf{w})$ is to $t_m$, the smaller the adjustment.

This is comparable to the perceptron deceptor. There a line, plane or hyperplane is pulled, when a sample is misclassified. The direction is such that the sample is more likely to be classified correctly if it is seen again. If the hidden set of neurons employ continuity, non-linear activation functions, nonlinearity is introduced, and the adjustment of weights adjusts a curve or manifold.

We illustrate this by training two layer neural network with three hidden neurons using the logistic sigmoid as the activation function to classify the three classes of the Iris dataset. The resulting boundary curves can be seen in Figure 9.2. It is the result of running Listing 5.6, replacing the heaviside activation function with the logistic sigmoid and reducing the number of hidden neurons to three. The entire dataset was used for training.

# 9.3 Autoencoders

In this section, we examine a group of neural networks known as autoencoders (AE). Their main feature is that the number of output neurons $K$ equals the number of input neurons $D$, i.e. $K = D$, and the purpose is the reconstruction of the input data, i.e. $\mathbf{y} \approx \mathbf{x}$. The number of layers $L$ is even, meaning the number of sets of hidden neurons is odd. The first $L/2$ layers encode the data. The latent variables of the set of hidden neurons numbered $L/2$ represent the
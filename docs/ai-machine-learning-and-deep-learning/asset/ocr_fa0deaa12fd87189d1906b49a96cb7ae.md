input features being processed by a softmax activation function. The inference function for the LR model can be represented as follows in equation (18.2.1).

# 18.2.2.3 Neural Network (NN)

NN is one of the most popular ML algorithms that facilitate nonlinear pattern extraction from underlying complex feature relationships of data [17]. The NN model is comprised of a network of nodes, where the arrangement and the number of the nodes depend on the data distribution. The architecture of NN is inspired by the working principle of the human brain, which can simultaneously perform several tasks while maintaining system performance. NN can observe a notable performance for solving multiclass classification problems. However, training such a network requires a lot of tuning, such as learning rate, batch size, number of hidden layers, etc.

An NN consists of an input layer, one output layer, and one or more hidden layers. The node inputs are calculated using the weight and bias values of connecting links along with the outputs of the connected previous layer nodes (with an exception for layer 1). The calculation is carried out as follows.

The input and output of the layer 1 nodes are basically the input feature values or(18.2.2) patient sensor measurements, in our case as in equation (18.2.3). A N-layer NN model is shown in Figure 18.3, where the last hidden layer is = .

![](bbox=[0.1, 0.48, 0.9, 0.86])

FIGURE 18.3 Flow diagram of NN model.
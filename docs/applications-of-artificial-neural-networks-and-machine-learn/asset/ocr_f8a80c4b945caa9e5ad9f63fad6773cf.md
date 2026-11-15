The set of candidate nodes may be taken as the pre-active and active nodes only, however, here in addition to these, all the non-active nodes adjacent to active nodes are also considered as candidates.

As an example, for the graph shown in Fig. 14.3b, the set of candidate nodes contains the nodes 3 and 4 (active state), 5 and 9 (pre-active state), and 7, 10, 11 (non-active state and neighboring nodes to the active nodes).

# 14.5.3 Neural Network for Evaluation of Coefficients of the Priority Function

Here the backpropagation (BP) neural network is briefly described. The BP consists of two types of elements: neurons (nodes) and weights (connections). Neurons are organized in layers: the first layer is called *input layer*, which receives stimulus from the outside environment; the last layer called *output layer*, which provides output or answers from the network. In between the input and output layers, there is at least one *hidden layer*. The *weights* represent the strength of the connections, which decide the distribution of data flow across layers. Between any two neighboring layers, the neurons are fully connected; for two layers with m and n neurons, there are m × n connections. Therefore the weights between two adjacent layers can be represented as a m × n matrix.

The training of a network is equivalent to finding proper weight matrices such that a desired output is generated for a corresponding input.

Mathematically, such networks can be thought of as multi-dimensional spaces. Each layer corresponds to a space with the dimension equal to the number of neurons in that layer. Each transformation consists of two operations: matrix multiplication and vector squashing, i.e. for R^m → R^n, {V}_n = squash({V}_m [W]_{m×n}), where {V}_m ∈ R^m, {V}_n ∈ R^n and [W]_{m×n} is the weight matrix. The squash is a function often known as the activation function converting a vector by squashing each vector component with a nonlinear function.

Backpropagation algorithm is the most popular training scheme for this type of networks. According to this algorithm, learning proper weights is conducted by an iterative two-step process. The two steps are:

+   (1) Computing the discrepancy between the desired and actual outputs, and
+   (2) feeding back the error signal layer by layer to the inputs, changing the weights in such a way as to modify them in proportion to their responsibility for the output error.

In the present method, a neural network is used for evaluating the coefficients of the priority function and therefore non-linear combination of the graph parameters as the input of Artificial Neural Network (ANN) becomes feasible, and adjusting the weights of the priority function can be performed. Another advantage of this method is that for any desired structure for nodal ordering, the appropriate measure for training can be taken.
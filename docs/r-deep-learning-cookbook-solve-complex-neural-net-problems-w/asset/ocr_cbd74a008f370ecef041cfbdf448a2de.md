# # Setting up a Restricted Boltzmann machine for Bernoulli distribution input

In this section, let's set up a restricted Boltzmann machine for Bernoulli distributed input data, where each attribute has values ranging from 0 to 1 (equivalent to a probability distribution). The dataset (MNIST) used in this recipe has input data satisfying a Bernoulli distribution.

An RBM comprises of two layers: a visible layer and a hidden layer. The visible layer is an input layer of nodes equal to the number of input attributes. In our case, each image in the MNIST dataset is defined using 784 pixels (28 x 28 size). Hence, our visible layer will have 784 nodes.

On the other hand, the hidden layer is generally user-defined. The hidden layer has a set of binary activated nodes, with each node having a probability of linkage with all other visible nodes. In our case, the hidden layer will have 900 nodes. As an initial step, all the nodes in the visible layer are connected with all the nodes in the hidden layer bidirectionally.

Each connection is defined using a weight, and hence a weight matrix is defined where the rows represent the number of input nodes and the columns represent the number of hidden nodes. In our case, the weight matrix (w) will be a tensor of dimensions 784 x 900.

In addition to weights, all the nodes in each layer are assisted by a bias node. The bias node of the visible layer will have connections with all the visible nodes (that is, the 784 nodes) and is represented with vb, whereas the bias node of the hidden layer will have connections with all the hidden nodes (that is, the 900 nodes) and is represented as vh.

![](bbox=[0.13, 0.615, 0.195, 0.675])

A point to remember with RBMs is that there will be no connections among nodes within each layer. In other words, the connections will be interlayer, but not intralayer.
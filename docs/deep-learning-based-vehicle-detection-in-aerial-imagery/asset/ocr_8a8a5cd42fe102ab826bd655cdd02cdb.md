the trainable parameters of the network. Note that the number of trainable parameters can rise significantly with an increasing number of neurons in the network due to the pairwise connection between neurons of adjacent layers.

# 2.1.2 Convolutional Neural Networks

CNNs are a specialized kind of neural network designed for processing high-dimensional data with a known grid-like topology, e.g., images or video frames. Typical CNNs consist of three basic types of layers: convolutional layers, pooling layers and fully connected layers [LeC98]. To reduce the number of parameters and consequently the complexity of a neural network, convolutional layers make use of two basic ideas illustrated in Figure 2.3. Instead of connecting every neuron with all neurons of the previous layer, neurons are only connected to neurons of the previous layer within a fixed local neighborhood. Thus, the weight matrix becomes sparse. Furthermore, the weights are shared for all neurons within a layer and thus, become independent of the position of the neuron.

![](bbox=[0.12, 0.6, 0.88, 0.8])

Figure 2.3: Transition from a fully connected layer to a 1D convolutional layer and the respective weight matrix.

In general, convolutional layers consist of a set of learnable filters, also called channels, as single convolutional filters do not capture sufficient information
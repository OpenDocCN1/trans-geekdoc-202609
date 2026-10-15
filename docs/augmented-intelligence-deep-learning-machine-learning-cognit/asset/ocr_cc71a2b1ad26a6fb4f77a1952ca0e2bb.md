these are artificial neurons used to solve complex mathematical, statistical, or artificial intelligence problems. These artificial neurons mimic the working of the human brain. The deep learning algorithms use these deep neural networks, as shown in Fig. (4.1), to train the model.

![](bbox=[0.336, 0.232, 0.717, 0.439])

**Fig. (4.1).** Architecture of a Deep Neural Network.

Neural networks must include numerous layers, not just one or two, to answer difficult real-world artificial intelligence concerns. In Fig. **4.1**, the neurons are arranged in various layers, which are in turn connected to adjacent layers with some numerical weights. In feedforward operations, the neurons in each layer receive some signal and transfer it to the neurons in the adjacent layer after performing some mathematical calculations on the input and passing it through an activation function [3].

In each hidden neuron j, the weighted sum of input neurons is first calculated as in Equation 1a:

$$Net_j = \sum_{i=1}^{d} x_i w_{ji} + w_{j0} \tag{1a}$$

Where $Net_j$ is the total activation value of the neuron, $w_{ji}$ are the weights of connections between the input layer and the hidden layer, $w_{j0}$ are the bias terms associated with each neuron, and $x_i$ is the input value. This value is then passed through a special activation function like $y = g(Net_j)$, which is used to remove the linearity in the data. If the total activation value is greater than the threshold value of the activation function, then the value is transmitted to the next neuron; otherwise, it will not get transferred.
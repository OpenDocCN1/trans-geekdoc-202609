The forward pass through the network consists of computing the activations at each layer. For the \(l\)-th layer, the pre-activation \(z^{(l)}\) is calculated as:

\(z^{(l)} = \mathbf{W}^{(l)}a^{(l-1)} + \mathbf{b}^{(l)}, \quad (229)\)

where \(a^{(l-1)}\) is the activation from the previous layer and \(\mathbf{W}^{(l)}\) is the weight matrix connecting the \((l-1)\)-th layer to the \(l\)-th layer. The output of the layer, i.e., the activation \(a^{(l)}\), is computed by applying the activation function \(\sigma^{(l)}\) element-wise to \(z^{(l)}\):

\(a^{(l)} = \sigma^{(l)}(z^{(l)}). \quad (230)\)

The final output of the network is given by the activation \(a^{(L)}\) at the last layer, which is the predicted output \(\hat{y}^{(i)}\):

\(\hat{y}^{(i)} = a^{(L)}. \quad (231)\)

The backpropagation algorithm computes the gradient of the loss function \(J(\theta)\) with respect to each parameter (weights and biases). First, we compute the error at the output layer. Let \(\delta^{(L)}\) represent the error at layer \(L\). This is computed by taking the derivative of the loss function with respect to the activations at the output layer:

\(\delta^{(L)} = \frac{\partial \mathcal{L}}{\partial a^{(L)}} \odot \sigma^{(L)\prime}(z^{(L)}), \quad (232)\)

where \(\odot\) denotes element-wise multiplication, and \(\sigma^{(L)\prime}(z^{(L)})\) is the derivative of the activation function applied element-wise to \(z^{(L)}\). For squared error loss, the derivative with respect to the activations is:

\(\frac{\partial \mathcal{L}}{\partial a^{(L)}} = \hat{y}^{(i)} - y^{(i)} \quad (233)\)

so the error term at the output layer is:

\(\delta^{(L)} = (\hat{y}^{(i)} - y^{(i)}) \odot \sigma^{(L)\prime}(z^{(L)}) \quad (234)\)

To propagate the error backward through the network, we compute the errors at the hidden layers. For each hidden layer \(l = L-1, L-2, \dots, 1\), the error \(\delta^{(l)}\) is calculated by the chain rule:

\(\delta^{(l)} = (\mathbf{W}^{(l+1)T}\delta^{(l+1)}) \odot \sigma^{(l)\prime}(z^{(l)}) \quad (235)\)

where \(\mathbf{W}^{(l+1)T} \in \mathbb{R}^{n_{l+1} \times n_l}\) is the transpose of the weight matrix connecting layer \(l\) to layer \(l+1\). This equation uses the fact that the error at layer \(l\) depends on the error at the next layer, modulated by the weights, and the derivative of the activation function at layer \(l\). Once the errors \(\delta^{(l)}\) are computed for all layers, we can compute the gradients of the loss function with respect to the parameters (weights and biases). The gradient of the loss with respect to the weights \(\mathbf{W}^{(l)}\) is:

\(\frac{\partial J(\theta)}{\partial \mathbf{W}^{(l)}} = \frac{1}{N} \sum_{i=1}^N \delta^{(l)} (a^{(l-1)})^T \quad (236)\)

The gradient of the loss with respect to the biases \(\mathbf{b}^{(l)}\) is:

\(\frac{\partial J(\theta)}{\partial \mathbf{b}^{(l)}} = \frac{1}{N} \sum_{i=1}^N \delta^{(l)} \quad (237)\)

After computing these gradients, we update the parameters using an optimization algorithm such as gradient descent. The weight update rule is:

\(\mathbf{W}^{(l)} \leftarrow \mathbf{W}^{(l)} - \eta \frac{\partial J(\theta)}{\partial \mathbf{W}^{(l)}}, \quad (238)\)
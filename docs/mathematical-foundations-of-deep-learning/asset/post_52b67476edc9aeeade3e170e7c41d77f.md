
high-frequency modes only begin to adapt once the low-frequency ones have been approximated with sufficient accuracy. In a more formal setting, the spectral bias can also be understood in terms of Sobolev spaces. A neural network function \(f_{\text{NN}}\) can be seen as a function in a Sobolev space \(W^{m,2}\), where the norm of a function \(f\) in this space is defined as

```
\(\|f\|_{W^{m,2}}^2 = \int_{\mathbb{R}^d} (1 + \|\boldsymbol{\xi}\|^2)^m \left| \hat{f}(\boldsymbol{\xi}) \right|^2 d\boldsymbol{\xi}\) (162)
```

When training a neural network, the optimization process implicitly regularizes the higher-order Sobolev norms, meaning that the network will initially approximate the target function in terms of lower-order derivatives (which correspond to low-frequency modes). This can be expressed by introducing a regularization term in the loss function:

```
\(\mathcal{L}_{\text{eff}}(\boldsymbol{\theta}) = \mathcal{L}(\boldsymbol{\theta}) + \lambda \|f_{\text{NN}}\|_{W^{m,2}}^2\) (163)
```

where \(\lambda\) is a regularization parameter that controls the trade-off between data fidelity and smoothness in the approximation.

Thus, spectral regularization emerges as a consequence of the network’s architecture, the nature of gradient descent optimization, and the inherent smoothness of the functions that neural networks are capable of learning. The mathematical structure of the NTK and the regularization properties of the Sobolev spaces provide a rigorous framework for understanding why neural networks prioritize the learning of low-frequency modes, reinforcing the idea that neural networks are implicitly biased toward smooth, low-frequency approximations at the beginning of training. This insight has profound implications for the generalization behavior of neural networks and their capacity to approximate complex functions.

## 5 Neural Network Basics

Literature Review: Goodfellow et al. (2016) [112] wrote one of the most comprehensive books on deep learning, covering the theoretical foundations of neural networks, optimization techniques, and probabilistic models. It is widely used in academic courses and research. Haykin (2009) [113] explained neural networks from a signal processing perspective, covering perceptrons, back-propagation, and recurrent networks with a strong mathematical approach. Schmidhuber (2015) [114] gave a historical and theoretical review of deep learning architectures, including recurrent neural networks (RNNs), convolutional neural networks (CNNs), and long short-term memory (LSTM). Bishop (2006) [115] gave a Bayesian perspective on neural networks and probabilistic graphical models, emphasizing the statistical underpinnings of learning. Poggio and Smale (2003) [116] established theoretical connections between neural networks, kernel methods, and function approximation. LeCun (2015) [117] discusses the principles behind modern deep learning, including backpropagation, unsupervised learning, and hierarchical feature extraction. Cybenko (1989) [58] proved the universal approximation theorem, demonstrating that a neural network with a single hidden layer can approximate any continuous function. Hornik et al. (1989) [57] extended Cybenko’s theorem, proving that multilayer perceptrons (MLPs) are universal function approximators. Pinkus (1999) [60] gave a rigorous mathematical discussion on neural networks from the perspective of approximation theory. Tishby and Zaslavsky (2015) [118] introduced the information bottleneck framework for understanding deep neural networks, explaining how networks learn to compress and encode information efficiently.

### 5.1 Perceptrons and Artificial Neurons

The perceptron is the simplest form of an artificial neural network, operating as a binary classifier. It computes the linear combination \(z\) of the input features \(\vec{x} = [x_1, x_2, \dots, x_n]^T \in \mathbb{R}^n\) and a corresponding weight vector \(\vec{w} = [w_1, w_2, \dots, w_n]^T \in \mathbb{R}^n\), augmented by a bias term \(b \in \mathbb{R}\). This can be expressed as

```
\(z = \vec{w}^T \vec{x} + b = \sum_{i=1}^n w_i x_i + b.\) (164)
```

To determine the output, this value is passed through the step activation function, defined mathematically as

```
\(\phi(z) = \begin{cases} 1, & z \ge 0, \\ 0, & z < 0. \end{cases}\) (165)
```

Thus, the perceptron's decision-making process can be expressed as

```
\(y = \phi(\vec{w}^T \vec{x} + b),\) (166)
```

where \(y \in \{0, 1\}\). The equation \(\vec{w}^T \vec{x} + b = 0\) defines a hyperplane in \(\mathbb{R}^n\), which acts as the decision boundary. For any input \(\vec{x}\), the classification is determined by the sign of \(\vec{w}^T \vec{x} + b\), specifically \(y = 1\) if \(\vec{w}^T \vec{x} + b \ge 0\) and \(y = 0\) otherwise. Geometrically, this classification corresponds to partitioning the input space into two distinct half-spaces. To train the perceptron, a supervised learning algorithm adjusts the weights \(\vec{w}\) and the bias \(b\) iteratively using labeled training data \(\{(\vec{x}_i, y_i)\}_{i=1}^m\), where \(y_i\) represents the ground truth. When the predicted output \(y_{\text{pred}} = \phi(\vec{w}^T \vec{x}_i + b)\) differs from \(y_i\), the weight vector and bias are updated according to the rule

```
\(\vec{w} \leftarrow \vec{w} + \eta(y_i - y_{\text{pred}})\vec{x}_i,\) (167)
```

and

```
\(b \leftarrow b + \eta(y_i - y_{\text{pred}}),\) (168)
```

where \(\eta > 0\) is the learning rate. Each individual weight \(w_j\) is updated as

```
\(w_j \leftarrow w_j + \eta(y_i - y_{\text{pred}})x_{ij}.\) (169)
```

For a linearly separable dataset, the Perceptron Convergence Theorem asserts that the algorithm will converge to a solution after a finite number of updates. Specifically, the number of updates is bounded by

```
\(\frac{R^2}{\gamma^2},\) (170)
```

where \(R = \max_i \|\vec{x}_i\|\) is the maximum norm of the input vectors, and \(\gamma\) is the minimum margin, defined as

```
\(\gamma = \min_i \frac{y_i(\vec{w}^T \vec{x}_i + b)}{\|\vec{w}\|}.\) (171)
```

The limitations of the perceptron, particularly its inability to solve linearly inseparable problems such as the XOR problem, necessitate the extension to artificial neurons with non-linear activation functions. A popular choice is the sigmoid activation function

```
\(\phi(z) = \frac{1}{1 + e^{-z}},\) (172)
```

which maps \(z \in \mathbb{R}\) to the continuous interval \((0, 1)\). The derivative of the sigmoid function, essential for gradient-based optimization, is

```
\(\phi'(z) = \phi(z)(1 - \phi(z)).\) (173)
```

Another widely used activation function is the hyperbolic tangent \(\tanh(z)\), defined as

```
\(\tanh(z) = \frac{e^z - e^{-z}}{e^z + e^{-z}},\) (174)
```

with derivative

tanh'(z) = 1 - tanh^2(z).

(175)

ReLU, or Rectified Linear Unit, is defined as

\(\phi(z) = \max(0, z),\)

(176)

with derivative

\(\phi'(z) = \begin{cases} 1, & z > 0, \\ 0, & z \le 0. \end{cases}\)

(177)

These non-linear activations enable the network to approximate non-linear decision boundaries, a capability absent in the perceptron. Artificial neurons form the building blocks of multi-layer perceptrons (MLPs), where neurons are organized into layers. For an \(L\)-layer network, the input \(\vec{x}\) is transformed layer by layer. At layer \(l\), the output is

\(\vec{z}^{(l)} = \phi^{(l)}(\vec{W}^{(l)}\vec{z}^{(l-1)} + \vec{b}^{(l)}),\)

(178)

where \(\vec{W}^{(l)} \in \mathbb{R}^{n_l \times n_{l-1}}\) is the weight matrix, \(\vec{b}^{(l)} \in \mathbb{R}^{n_l}\) is the bias vector, and \(\phi^{(l)}\) is the activation function. The network's output is

\(\hat{\vec{y}} = \phi^{(L)}(\vec{W}^{(L)}\vec{z}^{(L-1)} + \vec{b}^{(L)}).\)

(179)

The Universal Approximation Theorem guarantees that MLPs with sufficient neurons and non-linear activations can approximate any continuous function \(f : \mathbb{R}^n \to \mathbb{R}^m\) to arbitrary precision. Formally, for any \(\epsilon > 0\), there exists an MLP \(g(\vec{x})\) such that

\(\|f(\vec{x}) - g(\vec{x})\|_\infty < \epsilon\)

(180)

for all \(\vec{x} \in \mathbb{R}^n\). Training an MLP minimizes a loss function \(L\) that quantifies the error between predicted outputs \(\hat{\vec{y}}\) and ground truth labels \(\vec{y}\). For regression, the mean squared error is

\(L = \frac{1}{m} \sum_{i=1}^m \|\hat{\vec{y}}_i - \vec{y}_i\|^2,\)

(181)

and for classification, the cross-entropy loss is

\(L = -\frac{1}{m} \sum_{i=1}^m \left[ \vec{y}_i^T \log \hat{\vec{y}}_i + (1 - \vec{y}_i)^T \log(1 - \hat{\vec{y}}_i) \right].\)

(182)

Optimization uses stochastic gradient descent (SGD), updating parameters \(\Theta = \{ \vec{W}^{(l)}, \vec{b}^{(l)} \}_{l=1}^L\) as

\(\Theta \leftarrow \Theta - \eta \nabla_\Theta L.\)

(183)

Gradients are computed via backpropagation:

\(\frac{\partial L}{\partial \vec{W}^{(l)}} = \delta^{(l)} \vec{z}^{(l-1)T},\)

(184)

where \(\delta^{(l)}\) is the error signal at layer \(l\), recursively calculated as

\(\delta^{(l)} = (\vec{W}^{(l+1)T} \delta^{(l+1)}) \circ \phi'^{(l)}(\vec{z}^{(l)}).\)

(185)

This recursive structure, combined with chain rule applications, efficiently propagates error signals from the output layer back to the input layer.

Artificial neurons and their extensions have thus provided the foundation for modern deep learning. Their mathematical underpinnings and computational frameworks are instrumental in solving a wide array of problems, from classification and regression to complex decision-making. The interplay of linear algebra, calculus, and optimization theory in their formulation ensures that these networks are both theoretically robust and practically powerful.

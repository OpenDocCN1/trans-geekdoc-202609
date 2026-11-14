
## 5.2 Feedforward Neural Networks

Feedforward neural networks (FNNs) are mathematical constructs designed to approximate arbitrary mappings \(f : \mathbb{R}^n \rightarrow \mathbb{R}^m\) by composing affine transformations and nonlinear activation functions. At their core, these networks consist of \(L\) layers, where each layer \(k\) transforms its input \(\vec{a}_{k-1} \in \mathbb{R}^{m_{k-1}}\) into an output \(\vec{a}_k \in \mathbb{R}^{m_k}\) via the operation

\(\vec{a}_k = f_k(W_k \vec{a}_{k-1} + \vec{b}_k).\) (186)

Here, \(W_k \in \mathbb{R}^{m_k \times m_{k-1}}\) represents the weight matrix, \(\vec{b}_k \in \mathbb{R}^{m_k}\) is the bias vector, and \(f_k : \mathbb{R}^{m_k} \rightarrow \mathbb{R}^{m_k}\) is a component-wise activation function. Formally, if we denote the input layer as \(\vec{a}_0 = \vec{x}\), the final output of the network, \(\vec{y} \in \mathbb{R}^m\), is given by \(\vec{a}_L = f_L(W_L \vec{a}_{L-1} + \vec{b}_L)\). Each transformation in this sequence can be described as \(\vec{z}_k = W_k \vec{a}_{k-1} + \vec{b}_k\), followed by the activation \(\vec{a}_k = f_k(\vec{z}_k)\). The affine transformation \(\vec{z}_k = W_k \vec{a}_{k-1} + \vec{b}_k\) encapsulates the linear combination of inputs with weights \(W_k\) and the addition of biases \(\vec{b}_k\). For any two layers \(k\) and \(k+1\), the overall transformation can be represented by

\(\vec{z}_{k+1} = W_{k+1}(W_k \vec{a}_{k-1} + \vec{b}_k) + \vec{b}_{k+1}.\) (187)

Expanding this, we have

\(\vec{z}_{k+1} = W_{k+1} W_k \vec{a}_{k-1} + W_{k+1} \vec{b}_k + \vec{b}_{k+1}.\) (188)

Without the nonlinearity introduced by \(f_k\), the network reduces to a single affine transformation

\(\vec{y} = W \vec{x} + \vec{b},\) (189)

where \(W = W_L W_{L-1} \cdots W_1\) and

\(\vec{b} = W_L W_{L-1} \cdots W_2 \vec{b}_1 + \cdots + \vec{b}_L.\) (190)

Thus, the incorporation of nonlinear activation functions is critical, as it enables the network to approximate non-linear mappings. Activation functions \(f_k\) are applied element-wise to the pre-activation vector \(\vec{z}_k\). The choice of activation significantly affects the network's behavior and training. For example, the sigmoid activation \(f(x) = \frac{1}{1+e^{-x}}\) compresses inputs into the range \((0, 1)\) and has a derivative given by

\(f'(x) = f(x)(1 - f(x)).\) (191)

The hyperbolic tangent activation \(f(x) = \tanh(x) = \frac{e^x - e^{-x}}{e^x + e^{-x}}\) maps inputs to \((-1, 1)\) with a derivative

\(f'(x) = 1 - \tanh^2(x).\) (192)

The ReLU activation \(f(x) = \max(0, x)\), commonly used in modern networks, has a derivative

\(f'(x) = \begin{cases} 1 & x > 0, \\ 0 & x \le 0. \end{cases}\) (193)

These derivatives are essential for gradient-based optimization. The objective of training a feedforward neural network is to minimize a loss function \(\mathcal{L}\), which measures the discrepancy between the predicted outputs \(\vec{y}_i\) and the true targets \(\vec{t}_i\) over a dataset \(\{(\vec{x}_i, \vec{t}_i)\}_{i=1}^N\). For regression problems, the mean squared error (MSE) is often used, given by

\(\mathcal{L} = \frac{1}{N} \sum_{i=1}^N \|\vec{y}_i - \vec{t}_i\|^2 = \frac{1}{N} \sum_{i=1}^N \sum_{j=1}^m (y_{i,j} - t_{i,j})^2.\) (194)

In classification tasks, the cross-entropy loss is widely employed, defined as

\(\mathcal{L} = -\frac{1}{N} \sum_{i=1}^N \sum_{j=1}^m t_{i,j} \log(y_{i,j}),\) (195) where \( t_{i,j} \) represents the one-hot encoded labels. The gradient of \( \mathcal{L} \) with respect to the network parameters is computed using backpropagation, which applies the chain rule iteratively to propagate errors from the output layer to the input layer. During backpropagation, the error signal at the output layer is computed as

\(\delta_L = \frac{\partial \mathcal{L}}{\partial \vec{z}_L} = \nabla_y \mathcal{L} \odot f'_L(\vec{z}_L),\) (196)

where \( \odot \) denotes the Hadamard product. For hidden layers, the error signal propagates backward as

\(\delta_k = (W_{k+1}^T \delta_{k+1}) \odot f'_k(\vec{z}_k).\) (197)

The gradients of the loss with respect to the weights and biases are then given by

\(\frac{\partial \mathcal{L}}{\partial W_k} = \delta_k \vec{a}_{k-1}^T, \quad \frac{\partial \mathcal{L}}{\partial \vec{b}_k} = \delta_k.\) (198)

These gradients are used to update the parameters through optimization algorithms like stochastic gradient descent (SGD), where

\( W_k \leftarrow W_k - \eta \frac{\partial \mathcal{L}}{\partial W_k}, \quad \vec{b}_k \leftarrow \vec{b}_k - \eta \frac{\partial \mathcal{L}}{\partial \vec{b}_k},\) (199)

with \( \eta > 0 \) as the learning rate. The universal approximation theorem rigorously establishes that a feedforward neural network with at least one hidden layer and sufficiently many neurons can approximate any continuous function \( f : \mathbb{R}^n \rightarrow \mathbb{R}^m \) on a compact domain \( D \subset \mathbb{R}^n \). Specifically, for any \( \epsilon > 0 \), there exists a network \( \hat{f} \) such that \( \| f(\vec{x}) - \hat{f}(\vec{x}) \| < \epsilon \) for all \( \vec{x} \in D \). This expressive capability arises because the composition of affine transformations and nonlinear activations allows the network to approximate highly complex functions by partitioning the input space into regions and assigning different functional behaviors to each.

In summary, feedforward neural networks are a powerful mathematical framework grounded in linear algebra, calculus, and optimization. Their capacity to model intricate mappings between input and output spaces has made them a cornerstone of machine learning, with rigorous mathematical principles underpinning their structure and training. The combination of affine transformations, nonlinear activations, and gradient-based optimization enables these networks to achieve unparalleled flexibility and performance in a wide range of applications.

## 5.3 Activation Functions

In the context of **neural networks**, activation functions serve as an essential component that enables the network to approximate complex, non-linear mappings. When a neural network processes input data, each neuron computes a weighted sum of the inputs and then applies an activation function \( \sigma(z) \) to produce the output. Mathematically, let the input vector to the neuron be \( \mathbf{x} = (x_1, x_2, \dots, x_n) \), and let the weight vector associated with these inputs be \( \mathbf{w} = (w_1, w_2, \dots, w_n) \). The corresponding bias term is denoted as \( b \). The net input \( z \) to the activation function is then given by:

\( z = \mathbf{w}^\top \mathbf{x} + b = \sum_{i=1}^n w_i x_i + b \) (200)

where \( \mathbf{w}^\top \mathbf{x} \) represents the dot product of the weight vector and the input vector. The activation function \( \sigma(z) \) is then applied to this net input to obtain the output of the neuron \( a \):

\( a = \sigma(z) = \sigma \left( \sum_{i=1}^n w_i x_i + b \right).\) (201)

The activation function introduces a *non-linearity* into the neuron's response, which is a crucial aspect of neural networks because, without it, the network would only be able to perform linear transformations of the input data, limiting its ability to approximate complex, real-world functions. The non-linearity introduced by $\sigma(z)$ is fundamental because it enables the network to capture intricate relationships between the input and output, making neural networks capable of solving problems that require hierarchical feature extraction, such as image classification, time-series forecasting, and language modeling. The importance of non-linearity is most clearly evident when considering the mathematical formulation of a multi-layer neural network. For a feed-forward neural network with $L$ layers, the output $\hat{y}$ of the network is given by the composition of successive affine transformations and activation functions. Let $\mathbf{x}$ denote the input vector, $W_k$ and $b_k$ be the weight matrix and bias vector for the $k$-th layer, and $\sigma_k$ be the activation function for the $k$-th layer. The output of the network is:

$$\hat{y} = \sigma_L(W_L\sigma_{L-1}(W_{L-1} \cdots \sigma_1(W_1\mathbf{x} + b_1) + b_2) + \cdots + b_L). \quad (202)$$

If $\sigma(z)$ were a linear function, say $\sigma(z) = c \cdot z$ for some constant $c$, the composition of such functions would still result in a linear function. Specifically, if each $\sigma_k$ were linear, the overall network function would simplify to a single linear transformation:

$$\hat{y} = c_1 \cdot \mathbf{x} + c_2, \quad (203)$$

where $c_1$ and $c_2$ are constants dependent on the parameters of the network. In this case, the network would have no greater expressive power than a simple linear regression model, regardless of the number of layers. Thus, the *non-linearity* introduced by activation functions allows neural networks to approximate *any continuous function*, as guaranteed by the *universal approximation theorem*. This theorem states that a feed-forward neural network with at least one hidden layer and a sufficiently large number of neurons can approximate any continuous function $f(\mathbf{x})$, provided the activation function is non-linear and the network has enough capacity.

Next, consider the mathematical properties that the activation function $\sigma(z)$ must possess. First, it must be *differentiable* to allow the use of gradient-based optimization methods like *backpropagation* for training. Backpropagation relies on the *chain rule* of calculus to compute the gradients of the loss function $\mathcal{L}$ with respect to the parameters (weights and biases) of the network. Suppose $\mathcal{L} = \mathcal{L}(\hat{y}, \mathbf{y})$ is the loss function, where $\hat{y}$ is the predicted output of the network and $\mathbf{y}$ is the true label. During training, we compute the gradient of $\mathcal{L}$ with respect to the weights using the chain rule. Let $a_k = \sigma_k(z_k)$ represent the output of the activation function at layer $k$, where $z_k$ is the input to the activation function. The gradient of the loss with respect to the weights at layer $k$ is given by:

$$\frac{\partial \mathcal{L}}{\partial W_k} = \frac{\partial \mathcal{L}}{\partial a_k} \frac{\partial a_k}{\partial z_k} \frac{\partial z_k}{\partial W_k}. \quad (204)$$

The term $\frac{\partial a_k}{\partial z_k}$ is the *derivative* of the activation function, which must exist and be well-defined for gradient-based optimization to work effectively. If the activation function is not differentiable, the backpropagation algorithm cannot compute the gradients, preventing the training process from proceeding.

Now consider the specific forms of activation functions commonly used in practice. The **sigmoid** activation function is one of the most well-known, defined as:

$$\sigma(z) = \frac{1}{1 + e^{-z}}. \quad (205)$$

Its derivative is:

$$\sigma'(z) = \sigma(z)(1 - \sigma(z)), \quad (206)$$

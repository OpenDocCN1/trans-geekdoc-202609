
![](img/90c930779c8f928df6ff4481fc59f9a3_525_0.png)

**FIGURE 10.7** Example of a multilayer feed-forward neural network.

Table 10.1 Initial inputs, weights, and bias values.

| x1 | x2 | x3 | w14 | w15 | w24 | w25 | w34 | w35 | w46 | w56 | b4 | b5 | b6 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 0 | 1 | 0.2 | -0.3 | 0.4 | 0.1 | -0.5 | 0.2 | -0.3 | -0.2 | -0.4 | 0.2 | 0.1 |

In practice, several hundreds of thousands of epochs may be required before the weights will converge. "How efficient is backpropagation?" The computational efficiency depends on the time spent training the network. Given |D| tuples and w weights, each epoch requires O(|D| × w) time. However, in the worst-case scenario, the number of epochs can be exponential in n, the number of inputs. In practice, the time required for the networks to converge is highly variable. A number of techniques exist that help speed up the training time. We will introduce some key algorithmic techniques to accelerate the computation in Section 10.2.

### Example 10.1.
Sample calculations for learning by the backpropagation algorithm. Fig. 10.7 shows a multilayer feed-forward neural network. Let the learning rate $\eta = 0.9$. The initial weight and bias values of the network are given in Table 10.1, along with the first training tuple, $X = (1, 0, 1)$, with a class label of 1.

This example shows the calculations for backpropagation, given the first training tuple, X. The tuple is fed into the network, and the net input and output of each unit are computed. These values are shown in Table 10.2. The error of each unit is computed and propagated backward. The error values are shown in Table 10.3. The weight and bias updates are shown in Table 10.4.

| Unit, j | Net Input, I_j | Output, O_j |
|---|---|---|
| 4 | 0.2 + 0 - 0.5 - 0.4 = -0.7 | 1/(1 + e^{0.7}) = 0.332 |
| 5 | -0.3 + 0 + 0.2 + 0.2 = 0.1 | 1/(1 + e^{-0.1}) = 0.525 |
| 6 | (-0.3)(0.332) - (0.2)(0.525) + 0.1 = -0.105 | 1/(1 + e^{0.105}) = 0.474 |

| Unit, j | Error, \delta_j |
|---|---|
| 6 | (0.474)(1 - 0.474)(1 - 0.474) = 0.1311 |
| 5 | (0.525)(1 - 0.525)(0.1311)(-0.2) = -0.0065 |
| 4 | (0.332)(1 - 0.332)(0.1311)(-0.3) = -0.0087 |

| Weight or Bias | New Value |
|---|---|
| w_{46} | -0.3 - (0.9)(0.1311)(0.332) = -0.339 |
| w_{56} | -0.2 - (0.9)(0.1311)(0.525) = -0.262 |
| w_{14} | 0.2 - (0.9)(-0.0087)(1) = 0.208 |
| w_{15} | -0.3 - (0.9)(-0.0065)(1) = -0.294 |
| w_{24} | 0.4 - (0.9)(-0.0087)(0) = 0.4 |
| w_{25} | 0.1 - (0.9)(-0.0065)(0) = 0.1 |
| w_{34} | -0.5 - (0.9)(-0.0087)(1) = -0.492 |
| w_{35} | 0.2 - (0.9)(-0.0065)(1) = 0.206 |
| b_6 | 0.1 - (0.9)(0.1311) = -0.180 |
| b_5 | 0.2 - (0.9)(-0.0065) = 0.206 |
| b_4 | -0.4 - (0.9)(-0.0087) = -0.392 |

"How can we classify an unknown tuple using a trained network?" To classify an unknown tuple, X, the tuple is input to the trained network, and the net input and output of each unit are computed. There is no need for computation or backpropagation of the error. If there is one output node per class, then the output node with the highest value determines the predicted class label for X. This is called Maxout in the sense that the maximum output value of all output units $O^i (i = 1, ..., C)$ is used as the network's prediction. Alternatively, we can use SoftMax to convert the outputs $O^i (i = 1, ..., C)$ to the probabilities that the input tuple belongs to different class: $\frac{e^{O_i}}{\sum_{i=1}^C e^{O_i}}$. Here, $O_i$ is the output of the $i$th output unit, and $C$ is the total number of output units (e.g., the number of classes). If there is only one output node, then an output value greater than or equal to 0.5 may be considered as belonging to the positive class, while a value less than 0.5 may be considered negative.

## Matrix form representation of feed-forward neural networks

For an L-layer feed-forward neural network, we can alternatively represent it in a more concise form using matrix representation. To be specific, each data tuple is represented as an $n_0$-dimensional vector of attributes $X = (x_1, ..., x_{n_0})$ where $n_0$ is the number of attributes. Suppose each hidden or output layer has $n_i$ units. We denote the output of units at each layer as a vector $h_i$ of length $n_i$ ($i = 0, ..., L$), $h_0 = X$, and $h_L$ contains the output of all output units. We denote all the weights connecting layer $(i - 1)$ to layer $i$ as an $n_{i-1} \times n_i$ weight matrix $W_i$ and all the bias values at a hidden or output layer as an $n_i$-dimensional vector $b_i$ ($i = 1, ..., L$). Then, each hidden or output layer essentially transforms the vector at the previous layer $h_{i-1}$ to another vector $h_i$, that is, $h_i = f(W_i h_{i-1} + b_i)$, where the activation function $f(.)$ operates element-wise on a vector. What is inside the $f()$ function ($W_i h_{i-1} + b_i$) is called an affine transformation.4 In a feed-forward neural network, each hidden or output unit is connected to all units in the previous layer. We call such (hidden or output) layers as fully connected. With such a matrix form representation, we represent an L-layer feed-forward neural network by a chain graph with length of L.

### FIGURE 10.8
The matrix form representation of feed-forward neural network in Fig. 10.5. $h_0$ represents the input units (i.e., $h_0 = x$) and $h_4$ represents the output units (i.e., $h_4 = o$). For $h_1, h_2, h_3$, each of them represents the hidden units at the corresponding layer.

### Example 10.2.
For the four-layer neural network in Fig. 10.5, its equivalent matrix form representation is shown in Fig. 10.8, which is a chain graph of length 4. Since there are two input units in Fig. 10.5, $h_0$ is a vector of length 2. Likewise, $h_1$ is a vector of length 2 (two hidden units in the first hidden layer), $h_2$ is a vector of length 3 (three hidden units in the second hidden layer), $h_3$ is a vector of length 2 (two hidden units in the third hidden layer), and $h_4$ is a vector of length 1 (i.e., it is a scalar, since there is only one output unit in Fig. 10.5). The bias vector $b_i$ has the same length as the corresponding $h_i$ ($i = 1, 2, 3, 4$). The size of the weight matrix $W_i$ is determined by the length of $h_{i-1}$ (number of rows) and the length of $h_i$ ($i = 1, 2, 3, 4$) (number of columns). For instance, since both $h_0$ and $h_1$ have length 2, the weight matrix $W_1$ is of size $2 \times 2$; since $h_2$ has length 3 but $h_3$ has length 2, the weight matrix $W_2$ is of size $3 \times 2$. $h_i$ is obtained by a nonlinear activation function $f()$ on the affine transformation of $h_{i-1}$ with the weight matrix $W_i$ and the bias vector $b_i$ ($i = 1, 2, 3, 4$).

Most deep learning models are trained in the matrix form, where a major computational bottleneck lies in matrix multiplication5 in both forward and backward propagation stages. In order to accelerate this process, deep learning models are often trained with GPUs (graphics processing units) instead of CPUs (central processing unit). Compared with CPUs, GPUs offer two major advantages, which are critical in training deep learning models. First, GPUs are bandwidth optimized, which means that GPUs are good at fetching a large amount of memory needed for matrix multiplication. Second, optimizing the bandwidth comes at the potential cost of a high memory access latency. GPUs bypass this issue (memory access latency) using a technique called thread parallelism.

## 10.1.3 Key challenges for training deep learning models

As mentioned before, the key algorithmic framework to train a deep neural network, namely the backpropagation algorithm in Fig. 10.4, has largely remained the same since the 1980s. Let us first take a closer look at the backpropagation from the optimization perspective to identify the main algorithmic challenges.

Given a set of \(m\) training tuples \(\{(X^1, T^1), ..., (X^m, T^m)\}\), where \(X^l\) and \(T^l\) are the input attribute vector and target value of the \(l\)th tuple (\(l=1, ..., m\)), respectively. We are given a feed-forward neural network with fixed architecture, including the number of layers, the number of units at each layer, and the activation function of each unit. However, we do not know the weights (\(w_{ij}\)) and bias values (\(b_j\)) of the network. Backpropagation learns such model parameters by adaptively adjusting them to minimize the (approximate) training error \(E\)

\(E(\theta) = \frac{1}{m} \sum_{l=1}^m \text{Loss}(\hat{T}(X^l, \theta), T^l), \quad (10.9)\)

where Loss() is the loss function for an individual tuple, such as mean-squared loss in Fig. 10.4; \(\theta\) represents all the model parameters the algorithm aims to learn, including all the weights \(w_{i,j}\) and bias values \(b_j\); \(\hat{T}(X^l, \theta)\) is the predicted target value for the \(l\)th tuple that is a (complicated) function of the model parameter \(\theta\). The overall training error \(E(\theta)\) is the average loss among all \(m\) training tuples. Backpropagation starts with some initial guess of the model parameters \(\theta_0\) and then iteratively updates them as the following equation in order to minimize the training error \(E(\theta)\), until the algorithm terminates,

\(\theta_{t+1} = \theta_t - \eta g_t, \quad (10.10)\)

where \(t\) is the epoch number, \(\eta\) is the learning rate, and \(g_t\) is the gradient of the training error \(E(\theta)\) w.r.t. the model parameters \(\theta\). In the full-batch gradient descent approach, \(g_t\) is calculated by all \(m\) training tuples; in the stochastic gradient descent approach, \(g_t\) is estimated by a mini-batch of training tuples. When the algorithm terminates, we use the \(\theta^*\) from the final epoch as the learned model parameters, including all the weights (\(w_{ij}\)) and the bias values \(b_j\).

The first challenge (**optimization**) we face is how to make sure that \(\theta^*\) is indeed a high-quality solution to minimize \(E(\theta)\) in Eq. (10.9). If the objective function we wish to minimize is convex (e.g., the one in Fig. 10.6), then the gradient descent in Eq. (10.10) guarantees that \(\theta^*\) is indeed the optimal solution regardless the initial solution \(\theta_0\). With stochastic gradient descent, \(\theta_t\) will converge to the optimal solution in the probabilistic sense. However, the training error \(E(\theta)\) in a deep neural network is almost always **nonconvex**. As illustrated in Fig. 10.9, the (stochastic) gradient descent in Eq. (10.10) becomes much more challenging for a nonconvex function, even if there is only a single variable to optimize. Depending on where we start the search (i.e., the initial choice of \(\theta_0\)), the algorithm might end up in a high-cost local minimum; it might be stuck in a plateau where the gradient \(g_t\) is almost 0; in contrast the algorithm might jump over a desirable search area near a “cliff” where the gradient \(g_t\) is very large; or the algorithm might be deceived to stop at a saddle point where the gradient is zero but it is neither a local minimum nor maximum. Note that in practice, due to the high complexity of the training error \(E(\theta)\) of a deep neural network, it is neither realistic nor necessary to search for its global minimum. Instead, most algorithms aim to find a **high-quality local minimum**, that is, a local minimum with a low training error \(E(\theta)\) in a computationally efficient way.

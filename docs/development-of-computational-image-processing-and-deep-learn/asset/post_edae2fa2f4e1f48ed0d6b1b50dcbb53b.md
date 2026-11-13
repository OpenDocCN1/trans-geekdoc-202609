
![](img/332d06e0447dbfd85ea7d2fb553468f3_117_0.png)

Figure 2.16: Schematic visualization of a simple MLP structure with every node incorporating a linear aggregator, activation function and bias. Based on [176].

Analogously to Equation (2.90), assuming that all layers use the same activation function \(\sigma\), the output of a single node \(j\) in a specific hidden layer \(h^{(l)}, 1 \le l \le N\), is given by

\(\begin{aligned} h_j^{(l)} = \sigma \left( \sum_{i=1}^{k_{l-1}} w_{ij}^{(l)} h_i^{(l-1)} - b_j^{(l)} \right), \quad (2.97) \end{aligned}\)

where \(k_l\) denotes the total number of nodes in the hidden layer \(h^{(l)}\) and \(w_{ij}^{(l)}\) the weights between a unit \(j\) in the \(l\)th hidden layer and another unit \(i\) in the preceding layer [181]. It shall be noted that different layers may have different activation functions, which would require a distinction to be made between the different \(\sigma\). Equivalent expressions can be found for the output of the first hidden layer \(h^{(1)}\) as

\(h_j^{(1)} = \sigma \left( \sum_{i=1}^n w_{ij}^{(1)} x_i - b_j^{(1)} \right), \qquad (2.98)\)

with the number of input features $n$, and the output values $y_j$ as

\(y_j = \sigma \left( \sum_{i=1}^{k_{l-1}} w_{ij}^{(l)} h_i^{(l-1)} - b_j^{(l)} \right).\ \text{[181]} \qquad (2.99)\)

Considering an example of two consecutive hidden layers $h^{(1)}$ and $h^{(2)}$ with the number of nodes $k_1$ and $k_2$, exemplarily shown in Figure 2.17 with $k_1 = 4$ and $k_2 = 3$, the output of the first unit $h_1^{(2)}$ in the second layer can be calculated based on Equation (2.97) as

\(h_1^{(2)} = \sigma(w_{11}^{(2)} h_1^{(1)} + w_{12}^{(2)} h_2^{(1)} + \dots + w_{1k_1}^{(2)} h_{k_1}^{(1)} - b_1^{(2)}). \qquad (2.100)\)

![](img/332d06e0447dbfd85ea7d2fb553468f3_118_0.png)

**Figure 2.17:** Schematic description of two consecutive hidden layers $h^{(1)}$ and $h^{(2)}$ of an MLP.
For the sake of simplicity, previous or subsequent layers are not shown. In order to
illustrate the calculation of the output of node $h_1^{(2)}$, all other units that are not directly
connected are grayed out.

Repeating this calculation for all other units in the second layer results in $k_2$
different equations. Combining all outputs of the preceding layer as a single
vector $\boldsymbol{h}^{(1)}$ and the biases as vector $b$ yields the linear algebraic description of
the output vector $\boldsymbol{h}^{(2)} = h_1^{(2)}, h_2^{(2)}, \dots, h_{k_2}^{(2)}$ of the second layer as

\( h^{(2)} = \sigma \left( \begin{bmatrix} w_{11} & w_{12} & \cdots & w_{1k_1} \\ w_{21} & w_{22} & \cdots & w_{2k_1} \\ \vdots & \vdots & \ddots & \vdots \\ w_{k_2 1} & w_{k_2 2} & \cdots & w_{k_2 k_1} \end{bmatrix} \begin{bmatrix} h_1^{(1)} \\ h_2^{(1)} \\ \vdots \\ h_{k_1}^{(1)} \end{bmatrix} + \begin{bmatrix} b_1 \\ b_2 \\ \vdots \\ b_{k_1} \end{bmatrix} \right), \quad (2.101) \)

with the weight matrix \( W = [w_{ij}^{(2)}] \) for \( 1 \le j \le k_1 \) and \( 1 \le i \le k_2 \). This symbolic tensor notation compresses the process between two layers into one equation and simplifies the use in code:

\( h^{(2)} = \sigma \left( W^{(2)} h^{(1)} + b^{(2)} \right). \quad (2.102) \)

Generalized for any hidden layer \( h^{(l)} \), this yields

\( h^{(l)} = \sigma \left( W^{(l)} h^{(l-1)} + b^{(l)} \right). \quad [182, 183] \quad (2.103) \)

Their more complex structure allows MLPs to be applied to a variety of problems from pattern recognition [181] over clustering to optimization [176]. However, some disadvantages of fully connected layers include

- the large number of parameters
- slow convergence of training and
- bad generalization effect when applied to new training data. [179]

While the complexity of an MLP or an ANN can be increased arbitrarily both in the amount of layers as well as in the amount of nodes per layer, this leads to the requirement of high computational power or time and to increased risk of so-called _overfitting_ [184]. Overfitting denotes the network being perfectly trained on the input/training data and hence also fitted to the noise and irregular peculiarities thereof, instead of finding a general predictive rule that allows good predictions on new data points [185]. Increased model complexity and overfitting is tantamount to decreasing bias (error due to the used model’s incapability of capturing the underlying model) and increasing variance (error due to sensitivity to noise in the data). The opposite called underfitting hence typically shows high bias and low variance. This dilemma of finding the optimal model complexity is depicted in Figure 2.18. [186]

![](img/332d06e0447dbfd85ea7d2fb553468f3_120_0.png)

Figure 2.18: Qualitative depiction of the relationship between variance and bias and their effect on the error of the network. Models too simple to capture the underlying real model typically show high bias and low variance; they are underfitting. In contrast, an overly complex model is likely to have low bias and high variance and is therefore overfitting. Based on [186].

## 2.4.1.3 Training and backpropagation

The basic training process of a neural network is based on iterative optimization, illustrated in Figure 2.19.

The training of a multilayer ANN is in general similar to the training of an SLP, which was introduced in Equations (2.95) and (2.96) as delta rule. The production of output through the forward propagation of activation was introduced in the last section. However, in most modern feedforward networks a second training phase is involved, where the error is propagated backwards in the so-called *backpropagation*. [177] This efficient application of a chain-rule based supervised learning [189] was introduced by Linnainmaa [190] with significant improvements and analyses by Werbos [191] and Rumelhart [192]. According to Rojas, the backpropagation algorithm can be decomposed into four main steps that are the feedforward computation, the backpropagation to the output layer, the backpropagation to the hidden layer and finally the weight updates [193]. When the results of the feedforward computation are available, there exists a network output, hence prediction, \(\boldsymbol{y} = \boldsymbol{y}(\boldsymbol{w})\), for every of the \(q\) training vector pairs of input and output \((\boldsymbol{x}, \boldsymbol{y})\). Then, an error or cost function \(E\) comparing output \(\boldsymbol{y}\) and desired target \(\boldsymbol{z}\) is to be minimized

\(\min_w E = \sum_{p=1}^q E_p,\)

where \(E_p\) is some kind of distance function. The sum of squares error (SSE) based on Euclidean distance and given by

\(E_p = ||\boldsymbol{z}_p - \boldsymbol{y}_p||^2,\)

is a popularly applied error function. [194]

$E$ is computed solely through the composition of the node functions and hence forms a continuous and differentiable function of the $l$ network weights \(\{w_1, w_2, ..., w_l\}\). In order to minimize this error, an iterative process of gradient descent is used, for which the gradient of the error function has to be determined given by

\(\nabla E = \left( \frac{\partial E}{\partial w_1}, \frac{\partial E}{\partial w_2}, \dots, \frac{\partial E}{\partial w_l} \right). \quad (2.106)\)

The weights can subsequently be adjusted incrementally by descending the gradient as follows

\(\Delta w_i = -r_1 \frac{\partial E}{\partial w_i}, \quad i=1, 2, \dots, l, \quad (2.107)\)

with learning rate \(r_1\) defining the step length of each iteration. This procedure is repeated for a finite number of steps, steadily choosing the correction path with the steepest descent, until a minimum of the error function is found with \(\nabla E = 0\) or a satisfactory reduction of the error function is achieved. [193]

This so-called *generalized delta rule* [194] is illustrated in Figure 2.20.

Disadvantages of classical backpropagation include slow convergence speed and the strong dependence on chosen parameters, like initial weights and especially the learning rate. In addition, real error surfaces do not look like the simplified shape in Figure 2.20 but instead often show ravine-like features and many dent-like local minima [173]. This may result in the backpropagation training the network into a local minimum that it might not be able to escape. However, reaching the global minimum is in practice not always necessary, provided a set of weights is found that works accurately enough for the application at hand. [173, 195]

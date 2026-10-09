This NN is composed of an input layer and an output layer, with a hidden layer between them. The neurons in each layer are assumed to be fully connected to those in adjacent layers. The kth neuron $j$ in the $u_{j}^{l}$th layer is connected to the neurons in the $(k-1)$th layer, expressed as:

```
$$u_{j}^{k}=\sigma_{j}^{k-1}\left(\sum_{i=1}^{n_{k-1}} w_{i, j}^{k-1} u_{i}^{k-1}\right)\tag{3.1}$$
```

where $w_{i, j}^{k-1}$ is a weight for units $u_{i}^{k-1}$ to $u_{j}^{k}$, and $\sigma_{j}^{k}$ and $n_{k}$ represent an activation function for the jth neuron in the $k$ layer and the number of neurons, respectively.

Let us assume that the sigmoid function $\sigma(x)=1 /\left(1+e^{-x}\right)$ is used as the activation function. The calculation is performed with the weight set to $w_{n_{k}, j}^{k}$ by setting bias for the kth layer to $u_{n_{k}}^{k}=1$. The following paragraphs describe how to calculate the 1st-order derivative $\frac{\partial u_{i}^{L+1}}{\partial u_{j}^{0}}$ for the input layer $u_{j}^{0}$ and for the output layer unit $u_{j}^{L+1}$.

In the 1st-order derivative calculation, the chain rule is applied to decompose $\frac{\partial u_{i}^{L+1}}{\partial u_{j}^{0}}$ to construct an iterative procedure. $u_{j}^{k+1}$ is calculated using $u_{i}^{0}, u_{i}^{1}, \ldots, u_{i}^{k}$. Therefore, $u_{j}^{k+1}$ can be regarded as a composite function of $u_{i}^{0}, u_{i}^{1}, \ldots, u_{i}^{k}$, and its partial derivative is calculated using the chain rule. A partial derivative with respect to the input variable is calculated by recursively applying the chain rule decomposition of the partial derivative to this composite function. In this procedure, $\frac{\partial u_{i}^{L+1}}{\partial u_{j}^{k}}$ is decomposed according to the chain rule for intermediate variable $u_{i}^{1}$, and its subexpressions are further decomposed according to the chain rule for the intermediate variable $u_{i}^{2}$. The following formula is obtained by recursively repeating this decomposition process until the intermediate variable $u_{m_{L}}^{L}$ is reached.

```
$$\begin{gathered}\frac{\partial u_{j}^{L+1}}{\partial u_{i}^{0}}=\sum_{m_{1}=1}^{n_{1}}\left(\sum_{m_{2}=1}^{n_{2}}\left(\sum_{m_{3}=1}^{n_{3}}\left(\cdots\left(\sum_{m_{L}=1}^{n_{L}}\frac{\partial u_{j}^{L+1}}{\partial u_{m_{L}}^{L}}\frac{\partial u_{m_{L}}^{L}}{\partial u_{m_{L}-1}^{L-1}}\right)\cdots\right)\\\times \frac{\partial u_{m_{3}}^{3}}{\partial u_{m_{2}}^{2}}\frac{\partial u_{m_{2}}^{2}}{\partial u_{m_{1}}^{1}}\frac{\partial u_{m_{1}}^{1}}{\partial u_{i}^{0}}\right)\end{gathered}\tag{3.2}$$
```

Based on this equation, a procedure is constructed that calculates a partial differential by propagating the NN in reverse order.

For example, when the activation function is the sigmoid function, $\sigma(x)=1 /\left(1+e^{-x}\right)$, the derivative can be expressed as $\sigma^{\prime}(x)=(1-\sigma) \sigma$
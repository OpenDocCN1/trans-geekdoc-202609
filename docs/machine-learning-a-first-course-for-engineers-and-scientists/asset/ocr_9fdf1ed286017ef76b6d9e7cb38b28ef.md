# 6.2 Training a neural network

# 6.2 Training a neural network

A neural network is a parametric model and it is trained by the techniques explained in Chapter 5. The parameters in the model are all weight matrices and offset vectors

```
$\theta = [\text{vec}(W^{(1)})^T \ b^{(1)T} \ \dots \ \text{vec}(W^{(L)})^T \ b^{(L)T}]^T \quad (6.17)$
```

To find values for the parameters $\theta$ we solve an optimization problem of the form

```
$\hat{\theta} = \arg\min J(\theta) \quad \text{where } J(\theta) = \frac{1}{n} \sum_{i=1}^{n} L(x_i, y_i, \theta). \quad (6.18)$
```

We denote $J(\theta)$ as the cost function and $L(x_i, y_i, \theta)$ as the loss function. The functional form of the loss depends on the hand, mainly if it is a regression problem or a classification problem. For regression problems, we typically use the squared error (6.5) as did in linear regression,

```
$\L(x, y, \theta) = (y - f(x))^2, \quad (6.19)$
```

where $f(x; \theta)$ is the output of the neural network.
For multiclass classification we analogously the cross-entropy loss function (3.44) as did for multiclass logistic regression

```
$\L(x, y, \theta) = -\ln g_y(f(x; \theta)) = -z_y + \ln \sum_{j=1}^{M} e^{z_j}, \quad (6.20)$
```

where $z_j = f_j(x; \theta)$ is the $j$-th joint, the $j$-th output of the last layer before the softmax function $g(z)$.
Similar, to the method used in (3.44), we use the training data label $y$ as index variable to select the correct label for the loss function. Note that both linear and logistic regression can be seen as special case of the neural network where we have only one layer in the network. Also note that we are not restricted to these two loss functions. Following the discussion in Section 5.2 we could use another loss form that suits our needs.

These optimization problems cannot be solved in closed form, numerical optimization has to be used. In numerical optimization algorithms the parameters are updated in an iterative manner. In deep learning we use various versions of gradient descent:

+   1. Pick an initialization $\theta_0$.
2. Update the parameters $\theta_{t+1} \leftarrow \theta_t - \gamma\nabla_{\theta}(\theta_t)$ for $t = 0, 1, 2, \dots$
3. Terminate when some criterion is fulfilled, and take the last $\theta_T$.

Solving the optimization problem (6.18) has two main challenges.

+   **Computational challenge 1 - n is large.** The first computational challenge is the big data problem. For many deep learning the number of data points $n$ is very large making the computation of the cost function and gradient very costly we cannot afford to compute the exact gradient $\nabla_{\theta}J(\theta)$ at each iteration. In each iteration, we compute an approximation of this gradient by only considering a random subset of the training data at each iteration, we refer to as a mini-batch. This optimization procedure is called stochastic gradient descent and is further explained in Section 5.5.

+   **Computational challenge 2 - dim(\theta) is large.** The second computational challenge is that the number of parameters $dim(\theta)$ is very large for deep learning problems. To efficiently compute the gradient $\nabla_{\theta}J(\theta_t)$ we use the chain rule of calculus and reuse partial derivatives to compute this gradient. This is called the backpropagation algorithm, which is explained below.
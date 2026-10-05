# Probabilistic and stochastic neural networks | 159

```
$H(p, q) = H(p) + KL(p||q). \quad (7.62)$
```

```
$KL(p||q) = \int p(x) \log \frac{p(x)}{q(x)} dx. \quad (7.63)$
```

Since changing model parameters does not affect the true data, minimizing the cross-entropy is equivalent to minimizing the KL divergence. This has an interesting interpretation as we consider the learning as looking for the parameters to minimize the distribution by the data and the distribution given by the model. There are therefore many ways to develop the learning rule in neural network, and we hope it became that they are equivalent and these are closely related to the (max-) likelihood principle.

Let us apply this to a binary classification model which is described by Bernoulli variables that take the value 0 or 1. For this density, the cross-entropy is given by

```
$H(p, q) = -p(y=0;\mathbf{w}) \log q(y=0;\mathbf{w}) - p(y=1;\mathbf{w}) \log q(y=1|\mathbf{w}) \quad (7.64)$
```

or

```
$H(p, q) = -p \log q - (1-p) \log (1-q) \quad (7.65)$
```

for short, if we consider that $p$ stands for $p(y=0;\mathbf{w})$. We now assume a sigmoidal function for the probability of the class membership around a decision point,

```
$p(y=0;\mathbf{w}) = \frac{1}{1+e^{-\mathbf{w}}} \quad (7.66)$
```

```
$$\tilde{p}(y=0;\mathbf{w}) = \frac{1+e^{-\mathbf{w}}}{1+e^{\\mathbf{w}}} = \frac{1}{1+e^{\mathbf{w}}} \quad (7.67)$
```

Hence, minimizing the cross-entropy between the network output $\tilde{p}$ and the given labels $y$ is given by minimizing the Loss function

```
$L = -y \log \tilde{p}(y) - (1-y) \log (1-\tilde{p}(y)) \quad (7.68)$ \nL = y \log(1+e^{-\\mathbf{w}}) + (1-y) \log(1+e^{\mathbf{w}}) \quad (7.69)$
```

The derivative of the function is

```
$$\frac{dL}{d(\mathbf{w})} = y \frac{e^{-\mathbf{w}}}{1+e^{-\mathbf{w}}} + (1-y) \frac{e^{\mathbf{w}}}{1+e^{\mathbf{w}}} \quad (7.70)$ \n$= -y \frac{1}{1+e^{\mathbf{w}}} + (1-y) \frac{1}{1+e^{\mathbf{w}}} \quad (7.71)$ \n$= -y(1-\tilde{p}(y)) + (1-y)\tilde{p}(y) \quad (7.72)$ \n$= -y + yp\tilde{p}(y) + \tilde{p}(y) - y\tilde{p}(y) \quad (7.73)$ \n$= \tilde{p}(y) - y. \quad (7.74)$
```

from which we can derive the gradient we need for the learning rule

```
$$\frac{dL}{d(\mathbf{w})} = \frac{dL}{d(\mathbf{xw})} \frac{d(\mathbf{xw})}{d(\mathbf{w})} = (\tilde{p}(y) - y)\mathbf{x}. \quad (7.75)$
```

This expression has the now familiar form of the perceptron learning rule.
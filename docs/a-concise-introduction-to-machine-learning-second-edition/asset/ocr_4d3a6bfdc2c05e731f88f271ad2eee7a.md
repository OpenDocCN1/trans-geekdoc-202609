The parameters $a$ and $c$ have been tuned for the task at hand.
If the sign activation function in the perceptron is replaced by the logistic sigmoid function, then the output is interpreted as the probability of the sample belonging to the positive class $C_1$. The probability of belonging to the negative class $C_0$ is minus the output. This is then known as logistic regression. While it is solving a classification task, regression is part of the maine, since it is trying to model the probability function of belonging to the positive class space.

An activation function particularly important for classifying multiple classes is the softmax function, also known as normalized exponential function. It is different from the other activation functions in that it takes into account the result of the propagation function of other neurons. Let $a_j$ be the $w_j^T v$. If the number of neurons is $K$, the softmax function maps $a=(a_1, \dots, a_K)$ to a $K$-dimensional vector $\sigma(a)$ with the $j^{th}$ entry of $\sigma(a)$ being

```
$$\sigma(a)_j=\frac{\exp(a_j)}{\sum_{k=1}^K \exp(a_k)} \quad (5.6)$
```

Obviously, the elements of $\sigma(a)$ sum to one. The softmax function is often used in the final layer, where the number of synapses is the same as the number of classes. $K$ provides a probabilistic interpretation to which class the sample, which passed through the network, belong.

However, the construction of specific activation functions as in (5.3) is not in the spirit of Machine Learning, where many tasks as possible possible should be completed by the machine. Looking at Figure 5.16, we can see that the region actually be described as points on the right of the thin line and on the left of the bold line should output. It be implemented by introducing a set of hidden neurons. We denote the hidden variables, also known as latent variables, by $z_1$ and $z_2$. This is a two layer neural network, since a layer consists of the synapses from one set of neurons to another.

![](bbox=[0.238, 0.656, 0.762, 0.818])
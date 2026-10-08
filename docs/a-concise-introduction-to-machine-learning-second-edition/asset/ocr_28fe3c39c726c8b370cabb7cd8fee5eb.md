+   If the network tackles K separate, binary classification tasks on the same data, the error function is

```
$E(\mathbf{w}) = -\sum_{k=1}^{K} \sum_{n=1}^{N} t_{n,k} \log y_k(\mathbf{x}_n, \mathbf{w}) + (1 - t_{n,k}) \log (1 - y_k(\mathbf{x}_n, \mathbf{w}))$$
```

where $t_{n,k}$ is the $k^{th}$ component of $\mathbf{t}_n$ and $y_k(\mathbf{x}_n, \mathbf{w})$ is the output of the $K^{th}$ neuron, when $\mathbf{x}_n$ is the input. It is the sum of the errors of the $K$ individual binary classification tasks.

+   For multiple classes, $y_k(\mathbf{x}_n, \mathbf{w})$ is taken as the probability of the sample with features $\mathbf{x}_n$ belonging to the $k^{th}$ class and $\mathbf{t}_n$ is a 1-of-$K$ representation. The likelihood of the data is

```
$$\mathcal{L} = \prod_{n=1}^{N} \prod_{k=1}^{K} y_k(\mathbf{x}_n, \mathbf{w})^{t_{n,k}}$
```

As before, the negative logarithm leads to the error function

```
$E(\mathbf{w}) = -\sum_{k=1}^{K} \sum_{n=1}^{N} t_{n,k} \log y_k(\mathbf{x}_n, \mathbf{w})$$$
```

This looks very similar to the one above, but now only one of $t_{n,k}$, $k=1, \dots, K$ is nonzero.

We illustrate the capability of neural networks by training a two layer neural network with three hidden neurons to represent the function $1+x+\sin x$. The biases are modelled explicitly with dummy neurons which always have the value. The network diagram is

![](bbox=[0.283, 0.613, 0.719, 0.856])
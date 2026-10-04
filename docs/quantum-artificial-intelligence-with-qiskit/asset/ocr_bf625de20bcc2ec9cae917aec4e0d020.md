# 282 Quantum Artificial Intelligence with Qiskit

# 23.2 CROSS ENTROPY LOSS FUNCTION

For a given example, we can measure the likelihood that a variational quantum circuit, with a given set of weights has generated a given output for a given input

```
$p(t_k|\mathbf{w},\mathbf{x}_k) = \text{Bernoulli}(p(C_1|\mathbf{x}_k))$
```

```
$p(t_k|\mathbf{w},\mathbf{x}_k) = p(C_1|\mathbf{x}_k)^{t_k} \cdot (1 - p(C_1|\mathbf{x}_k))^{1-t_k}$
```

Given we know how to write the likelihood of each [121] and if we assume that the data are independent, we can write the likelihood for the whole data set by simply multiplying the individual likelihoods

```
$p(\mathbf{x}_1,\dots,\mathbf{x}_N,\mathbf{w}) = \prod_{k=1}^{N} p(C_1|\mathbf{x}_k)^{t_k} \cdot (1 - p(C_1|\mathbf{x}_k))^{1-t_k}$
```

with

```
$o_k = p(C_1|\mathbf{x}_k) = \sigma(\mathbf{w}^T \cdot \mathbf{x}_k)$ = $\sigma(net_k)$,
```

we can simply write

```
$p(\mathbf{x}_1,\dots,\mathbf{x}_N,\mathbf{w}) = \prod_{k=1}^{N} o_k^{t_k} \cdot (1 - o_k)^{1-t_k}$
```

Having the likelihood, we can estimate the weights that the likelihood is maximized. This is equivalent to minimizing the negative log likelihood, yielding the loss function

```
$L(\mathbf{w}) = -log(p|\mathbf{w})) = -\sum_{k=1}^{N} (t_k \log o_k + (1 - t_k) \log(1 - o_k))$.
```

The resulting loss function is exactly the cross entropy between targets and outputs

```
$H(t,p) = -\sum_{k=1}^{N} (t_k \cdot \log p(C_1|\mathbf{x}_k) + (1 - t_k) \cdot \log p(C_2|\mathbf{x}_k))$.
```

# 23.2.1 Multi-Class Loss Function

Assuming the training set consists of $N$ observations

```
$X =(\mathbf{x}_1,\mathbf{x}_2,\dots,\mathbf{x}_k,\dots,\mathbf{x}_N)^T$
```

and target values represented as vectors of dimension $K$ (since $t$ is used as an index, we will use $y_{kt}$ to indicate the specific target)

```
$Y =(\mathbf{y}_1,\mathbf{y}_2,\dots,\mathbf{y}_k,\dots,\mathbf{y}_N)^T$.
```

During training, each variational quantum circuit is trained individually with its target value $y_{kt}$

```
$y_{kt} \in \{0,1\}, \sum_{t=1}^{K} y_{kt} = 1$
```
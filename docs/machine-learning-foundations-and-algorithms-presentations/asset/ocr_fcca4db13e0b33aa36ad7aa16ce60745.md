# # Backpropagation

Example: Multi-layer Perceptron (multiple outputs)

# Backward pass:

![](bbox=[0.063, 0.335, 0.335, 0.693])

# Forward pass:

```
$\overline{\mathcal{L}} = 1$$
$\overline{y_k} = \overline{\mathcal{L}}(y_k - t_k)$$
$\overline{w_{ki}} = \overline{y_k}\overline{h_i}$
$\overline{b_k} = \overline{y_k}$
$\overline{h_i} = \sum_k \overline{y_k}\overline{w_{ki}}
$\overline{z_i} = \overline{h_i}\sigma'(z_i)$$
$\overline{w_{ij}} = \overline{z_i}x_j$
$\overline{b_i} = \overline{z_i}$
```

```
$z_i = \sum w_{ij}^{(1)}x_j + b_i^{(1)}$$
$h_i = \sigma(z_i)$$
$y_k = \sum w_{ki}^{(2)}h_i + b_k^{(2)}$$
$\mathcal{L} = \frac{1}{2}\sum(y_k - t_k)^2$
```

Can we also do this in **matrix form**?
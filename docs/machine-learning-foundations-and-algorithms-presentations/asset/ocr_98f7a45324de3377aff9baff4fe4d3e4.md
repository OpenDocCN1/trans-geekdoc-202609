# Chain rule with tensors

For weight matrices: $\frac{\partial Wx+b}{\partial W} = \mathcal{T}_{ijd} \text{ with } \mathcal{T}_{[\cdot,:]d} = \frac{\partial z_d}{\partial W} =$

Matrix with zeros, d-th row contains x^T

d-th row of W is a row vector

![](bbox=[0.125, 0.495, 0.515, 0.735])

A scalar

$(W_{d,:}) \cdot x + b_d = z_d$

A row vector

$\frac{\partial z_d}{\partial W_{d,:}} = x^T$

A row zero vector

$\frac{\partial z_d}{\partial W_{
eq d,:}} = 0^T$

Other rows:
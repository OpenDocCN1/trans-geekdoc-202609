# # Chain rule with tensors

Tensor vector product:

```
$$\mathcal{T}_{ijd}\mathbf{u} = \sum_{d} T_{[d,\cdot,]}u_d = \sum_{d} \mathbf{X}_d u_d =$
```

+   * Which is the outer product!

```
$$\begin{bmatrix} x_1u_1 & x_2u_1 & \dots & x_nu_1 \ \vdots & & & \ x_1u_d & x_2u_d & \dots & x_nu_d \end{bmatrix} = \mathbf{u}\mathbf{x}^T$
```

$$\mathbf{X}_du_d$

Hence:

```
$$\nabla_{\mathbf{W}}f = \frac{\partial f(z)}{\partial \mathbf{W}} = \frac{\partial f(z)}{\partial \mathbf{W}}(\mathbf{W}\mathbf{x} + \mathbf{b}) = \frac{\partial f(z)}{\partial \mathbf{z}}\mathbf{x}^T$
```
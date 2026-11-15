that depends on the value of $z_3$. From Figure 12.4, the bold arrows pointing into $z_3$ imply that

```
z_3 = \beta_{33} + \beta_{13}x_1 + \beta_{23}x_2
```

and therefore

```
a_3 = z_3 I(z_3),
```

where $I(\cdot)$ is the indicator function. Hence, to obtain Eq. (12.5.12), we use

```
\frac{\partial J(y, y_F)}{\partial y_F} \frac{\partial y_F}{\partial a_3} = (y_F - y)\beta_3 \text{ and } \frac{\partial a_3}{\partial z_3} \frac{\partial z_3}{\partial \beta_{23}} = I(z_3)x_2.
```

Clearly, the term $I(z_3)$ is either 1 or 0. This aspect of the relu function may seem harsh at first but it is intended to improve the convergence of deep neural networks for $z > 0$. On the other hand, if the partial derivative is zero, the coefficient does not change which could slow convergence. Thus, variants of the relu, such as the leaky-relu and the elu that have non-zero derivatives in the $z \le 0$ region, were proposed to address this issue. For our purposes, the standard relu function is sufficient.

All of the 12 partial derivatives of the gradient matrix would be computed in the same way for the first layer using the general equations for one observation,

```
\frac{\partial J(\boldsymbol{\beta})}{\partial \beta_{jk}} = (y_F - y)\beta_k x_j I(z_k) \text{ and } \beta_{jk}^{(t+1)} = \beta_{jk}^{(t)} - \ell \times \frac{\partial J(\boldsymbol{\beta})}{\partial \beta_{jk}},
```

where $j = 1, 2, 3, 4$ and $k = 1, 2, 3$. Using the steps outlined above, all 17 gradients can be calculated to update the $\boldsymbol{\beta}$ matrix and vector in Figure 12.5. For $n$ observations, we must sum all $n$ gradients to produce the updated parameters.

# 12.5.3 Dispersion Function Gradients

For the rank-based approach, a similar set of operations are needed for back propagation. To obtain $\beta_0$, we would use

```
\frac{\partial D_n(\boldsymbol{\beta})}{\partial \beta_0} = - \sum_{i=1}^n y_{F_i}(1 - y_{F_i})a_n(R_{n_i}(\boldsymbol{\beta})),
```

where $y_{F_i}$ is the $i$th value of the output associated with input $x_i$. The needed quantities can be obtained after performing forward propagation.
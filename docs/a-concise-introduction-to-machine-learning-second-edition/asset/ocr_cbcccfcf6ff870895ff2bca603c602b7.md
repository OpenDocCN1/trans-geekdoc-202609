![](bbox=[0.248, 0.198, 0.752, 0.315])

Figure 5.3: Hyperbolic tangent kernel.

$	heta_1 = 0, \mathbf{y} = (1,1), \theta_2 = 1$.

$	heta_1 = 0, \mathbf{y} = (1,1), \theta_2 = 1/\sqrt{5}$.

$mathbf{x}_2 = (1,0)$, the gram matrix is

```
$$\mathbf{K} = \begin{pmatrix} \tanh(1.25) & \tanh(1.5) \ \tanh(1.5) & \tanh(2) \end{pmatrix}$
```

and has a negative eigenvalue and therefore is not positive semi-definite. Nevertheless, the hyperbolic tangent kernel is used in practice. Burges (1999) derives necessary conditions for functions based on the inner product to be valid kernels, as well as giving insight into the construction of kernels.

In some cases, it is possible to recover the mapping $\phi$. To illustrate this let $M=2$ and we consider the quadratic kernel:

```
$k(\mathbf{x},\mathbf{y}) = (\theta_1^2 + \theta_2^T\mathbf{x}^T\mathbf{y})^2 \\n (\theta_1^2 + \theta_2^T\mathbf{x}_1\mathbf{y}_1)^2$
```

```
$= \theta_1^4 + 2\theta_1^2\theta_2^T\mathbf{x}^T\mathbf{y} + (\theta_2^T\mathbf{x}^T\mathbf{y})^2 + 2\theta_1^2\theta_2^T\mathbf{x}_1\mathbf{y}_1 + 2\theta_2^T\mathbf{x}_1\mathbf{y}_1\theta_2^T\mathbf{x}_2\mathbf{y}_2$
```

```
$= \begin{pmatrix} \theta_1^2 & \theta_{2,1}^2 & \theta_{2,2}^2 \ 2\sqrt{2}\theta_{2,1}x_1x_2 & 2\sqrt{2}\theta_{2,1}x_1y_1 & 2\sqrt{2}\theta_{2,2}x_2y_2 \ \theta_{2,1}^2y_1^2 & \theta_{2,1}y_1y_2 & \theta_{2,2}^2y_2^2 \end{pmatrix}$
```

```
$= \phi(\mathbf{x})^T\phi(\mathbf{y})$.
```

Hence, in this case, the quadratic kernel is an implicit mapping to a six-dimensional space.

It is more intuitive to let the relationship between samples depend on the distance between them, that the Euclidean norm ($L_2$ norm) of their difference, $|\mathbf{x} - \mathbf{y}\|$. This leads to the class of radial basis function (RBF) kernels.

# Gaussian kernel $k(\mathbf{x},\mathbf{y}) = \theta^2 \exp \left(-rac{|\mathbf{x} - \mathbf{y}\|^2}{2\theta^2}\right)$.
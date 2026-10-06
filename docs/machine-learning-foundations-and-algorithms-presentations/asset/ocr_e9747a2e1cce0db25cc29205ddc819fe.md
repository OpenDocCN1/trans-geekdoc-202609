# Recipe for learning

Given: dataset $\mathcal{D} := \{x_1, x_2, x_3, \dots, x_n\} \sim q(\mathbf{x})$

learn the density $q(\mathbf{x})$

choose a simple source density $p(\mathbf{z})$

use maximum likelihood

```
$$\prod_{i=1}^n q(\mathbf{x}_i) = \prod_{i=1}^n p(\mathbf{z}_i) |det(\nabla_{\mathbf{z}} \mathbf{T}(\mathbf{z}_i))^{-1}|$
$\hat{\mathbf{T}} := \arg \max_{\mathbf{T}} \prod_{i=1}^n p(\mathbf{z}_i) |det(\nabla_{\mathbf{z}} \mathbf{T}(\mathbf{z}_i))^{-1}|$
$\hat{\mathbf{T}} := \arg \max_{\mathbf{T}} \sum_{i=1}^n \log p(\mathbf{z}_i) - \log |det(\nabla_{\mathbf{z}} \mathbf{T}(\mathbf{z}_i))|$$
```

But....

what are $\mathbf{z}_i$ ?

$$\mathbf{z}_i = \mathbf{T}^{-1}(\mathbf{x}_i)$

so we need the inverse $\mathbf{T}^{-1}$

computing determinant computationally expensive

triangular maps

computation of **inverse** and **Jacobian** must be **cheap**
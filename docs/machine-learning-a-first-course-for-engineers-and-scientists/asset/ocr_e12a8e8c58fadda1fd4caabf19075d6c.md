# 8.4 Kernel theory

there plays an important role in determining the influence of each training data point when making a prediction.

+   Even though we started introducing kernels via the inner product $\phi(x)^T\phi(x')$, we do not have to bother about inner product...

In addition to this, the kernel also plays a somewhat more role in methods that use the representer term (such as kernel regression, support vector regression and support classification, but not $k$-NN).

The $L^2$-regularization $\lambda||	heta||_2^2$ ensures we do not solve the primal formulation when using kernels (we solve the dual), it is nonetheless of equivalent representation...

+   The choice of kernel corresponds to a role of regularization function. That is, the kernel implies a preference for certain functions in the space of all functions that are spanned by the feature vector.

Using a kernel method quite simple, and one could perceive that it to suffer from overfitting. While regularizing the role of kernel explains why that is rarely the case in practice.

All three points above are central to understand the usefulness and versatility of kernel methods. They also highlight the importance for the machine learning engineer to choose the kernel wisely, and not resort to "default" choices.

# Valid choices of kernels

We introduced kernels as a way to work with nonlinear feature transformations as (8.11). A direct consequence of that is it is not sufficient to consider $\kappa(x,x')$ and $\phi(x)$.

```
$\kappa(x,x') = \phi(x)^T\phi(x')$
```

Before answering the question, we have to be aware that question is primarily of theoretical nature. As long as we use $\kappa(x,x')$ computing its predictions is sure, no matter if it is the factorization (8.21) or not.

That said, we will now have a closer look at the important family of positive semidefinite kernels. A kernel is said to be positive definite if the Gram matrix $K(X,X)$ as defined in (8.12b) is positive semidefinite...
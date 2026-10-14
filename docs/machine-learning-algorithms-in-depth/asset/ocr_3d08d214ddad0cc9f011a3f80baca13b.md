Here, we assume the following.

$$A = \sigma_n^{-2} X X^T + \Sigma_p^{-1}\tag{6.15}$$

Thus, we have a closed-form posterior distribution over the parameters $w$. To make predictions using this equation, we need to invert the matrix $A$ of size $p \times p$.

Assuming the observations are noiseless, we want to predict the function outputs $y^* = f(x^*)$, where $x^*$ is our test data. Consider the following joint GP distribution.

$$\begin{pmatrix} f \\ f_* \end{pmatrix} \sim N\left(\begin{pmatrix} \mu \\ \mu_* \end{pmatrix}, \begin{pmatrix} K & K_* \\ K_*^T & K_{**} \end{pmatrix}\right)\tag{6.16}$$

Here, $K = \kappa(X, X)$, $K^* = \kappa(X, X^*)$ and $K^{**} = \kappa(X^*, X^*)$, where $X$ is our training dataset, $X^*$ is our test dataset, and $\kappa$ is the kernel or covariance function. Using standard rules for conditioning Gaussians, the posterior has the following form.

$$p(f_*|X_*, X, f) \sim N(f_*|\mu_*, \Sigma_*)\\\mu_* = \mu(X_*) + K_*^T K^{-1}(f - \mu(X))\\\Sigma_* = K_{**} - K_*^T K^{-1} K_*\tag{6.17}$$

In code listing 6.4, we use the radial basis function kernel as a measure of similarity defined in equation 6.18. We are now ready to implement GP regression from scratch (see figure 6.7)!

```
1: class GPreg:
2: function kernel_func(x, z)
3: Kfn = exp{ -1/(2σ²) ||x - z||² }  ← Radial basis function kernel
4: return Kfn
5: function compute_posterior(X)
6: K = kernel_func(X_train, X_train)
7: Ks = kernel_func(X_train, X_test)
8: Kss = kernel_func(X_test, X_test)
9: μ_post = μ(X_test) + K_s^T K^{-1} (f - μ(X_train))  → Gaussian process posterior
10: Σ_post = K_ss - K_s^T K^{-1} K_s
11: return μ_post, Σ_post
```

Figure 6.7 Gaussian process regression pseudo-code

The code consists of kernel_func and compute_posterior functions. The kernel_func returns a radial basis function (RBF) kernel, which measures the similarity between two inputs $x$ and $z$. In the computer_posterior function, we first compute the ingredients
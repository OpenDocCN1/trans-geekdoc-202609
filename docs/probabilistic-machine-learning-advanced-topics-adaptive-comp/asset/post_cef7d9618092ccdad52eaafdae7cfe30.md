

These results can be interpreted as follows: the mean is the usual mean from the GP, plus a global offset from the linear model, using $\overline{\beta}$; and the covariance is the usual covariance from the GP, plus an additional positive term due to the uncertainty in $\beta$.

In the limit of an uninformative prior for the regression parameters, as \(\mathbf{B} \rightarrow \infty \mathbf{I}\), this simplifies to

```
\(\mathbb{E}[g(\mathbf{X}_*)|\mathcal{D}] = \mathbb{E}[f(\mathbf{X}_*)|\mathcal{D}] + \mathbf{R}^\mathsf{T}(\mathbf{H}_\mathsf{X} \mathbf{K}_\sigma^{-1} \mathbf{H}_\mathsf{X}^\mathsf{T})^{-1} \mathbf{H}_\mathsf{X} \mathbf{K}_\sigma^{-1} \mathbf{y}\) \tag{18.70}
\(\text{Cov}[g(\mathbf{X}_*)|\mathcal{D}] = \text{Cov}[f(\mathbf{X}_*)|\mathcal{D}] + \mathbf{R}^\mathsf{T}(\mathbf{H}_\mathsf{X} \mathbf{K}_\sigma^{-1} \mathbf{H}_\mathsf{X}^\mathsf{T})^{-1} \mathbf{R}\) \tag{18.71}
```

## 18.3.5 Marginal likelihood

Most kernels have some free parameters. For example, the RBF-ARD kernel (Section 18.2.1.2) has the form

```
\(\mathcal{K}(\mathbf{x}, \mathbf{x}') = \exp\left(-\frac{1}{2} \sum_{d=1}^D \frac{1}{\ell_d^2}(x_d - x'_d)^2\right) = \prod_{d=1}^D \mathcal{K}_{\ell_d}(x_d, x'_d)\) \tag{18.72}
```

where each $\ell_d$ is a length scale for feature dimension $d$. Let these (and the observation noise variance $\sigma_y^2$, if present) be denoted by $\theta$. We can compute the likelihood of these parameters as follows:

```
\(p(\mathbf{y}|\mathbf{X}, \theta) = p(\mathcal{D}|\theta) = \int p(\mathbf{y}|f_\mathsf{X}, \theta) p(f_\mathsf{X}|\mathbf{X}, \theta) df_\mathsf{X}\) \tag{18.73}
```

Since we are integrating out the function $f$, we often call $\theta$ hyperparameters, and the quantity \(p(\mathcal{D}|\theta)\) the marginal likelihood.

Since $f$ is a GP, we can compute the above integral using the marginal likelihood for the corresponding Gaussian. This gives

```
\(\log p(\mathcal{D}|\theta) = -\frac{1}{2}(\mathbf{y} - \mu_\mathsf{X})^\mathsf{T} \mathbf{K}_\sigma^{-1}(\mathbf{y} - \mu_\mathsf{X}) - \frac{1}{2} \log |\mathbf{K}_\sigma| - \frac{N}{2} \log(2\pi)\) \tag{18.74}
```

The first term is the square of the Mahalanobis distance between the observations and the predicted values: better fits will have smaller distance. The second term is the log determinant of the covariance matrix; which measures model complexity: smoother functions will have smaller determinants, so $-\log |\mathbf{K}_\sigma|$ will be larger (less negative) for simpler functions. The marginal likelihood measures the tradeoff between fit and complexity.

In Section 18.6.1, we discuss how to learn the kernel parameters from data by maximizing the marginal likelihood wrt $\theta$.

## 18.3.6 Computational and numerical issues

In this section, we discuss computational and numerical issues which arise when implementing the above equations. For notational simplicity, we assume the prior mean is zero, \(m(\mathbf{x}) = 0\). The posterior predictive mean is given by \(\mu_* = \mathbf{k}_*^\mathsf{T} \mathbf{K}_\sigma^{-1} \mathbf{y}\). For reasons of numerical stability, it is unwise to directly invert \(\mathbf{K}_\sigma\). A more robust alternative is to compute a Cholesky decomposition, \(\mathbf{K}_\sigma = \mathbf{L} \mathbf{L}^\mathsf{T}\), which takes \(O(N^3)\) time. Given this, we can compute

```
\(\mu_* = \mathbf{k}_*^\mathsf{T} \mathbf{K}_\sigma^{-1} \mathbf{y} = \mathbf{k}_*^\mathsf{T} \mathbf{L}^{-\mathsf{T}} (\mathbf{L}^{-1} \mathbf{y}) = \mathbf{k}_*^\mathsf{T} \mathbf{\alpha}\) \tag{18.75}
```

Here $\boldsymbol{\alpha} = \mathbf{L}^{\top} \backslash (\mathbf{L} \backslash \mathbf{y})$, where we have used the backslash operator to represent backsubstitution. We can compute the variance in $O(N^2)$ time for each test case using $\sigma_*^2 = k_{**} - \mathbf{k}_*^{\top} \mathbf{L}^{-T} \mathbf{L}^{-1} \mathbf{k}_* = k_{**} - \mathbf{v}^{\top} \mathbf{v}$ where $\mathbf{v} = \mathbf{L} \backslash \mathbf{k}_*$.

Finally, the log marginal likelihood (needed for kernel learning, Section 18.6) can be computed using $\log p(\mathbf{y}|\mathbf{X}) = -\frac{1}{2}\mathbf{y}^{\top}\boldsymbol{\alpha} - \sum_{n=1}^N \log L_{nn} - \frac{N}{2}\log(2\pi)$

We see that overall cost is dominated by $O(N^3)$. We discuss faster, but approximate, methods in Section 18.5.

## 18.3.7 Kernel ridge regression

The term ridge regression refers to linear regression with an $\ell_2$ penalty on the regression weights: $\mathbf{w}^* = \underset{\mathbf{w}}{\text{argmin}} \sum_{n=1}^N (y_n - f(\mathbf{x}_n; \mathbf{w}))^2 + \lambda \|\mathbf{w}\|_2^2$

where $f(\mathbf{x}; \mathbf{w}) = \mathbf{w}^{\top} \mathbf{x}$. The solution for this is $\mathbf{w}^* = (\mathbf{X}^{\top}\mathbf{X} + \lambda \mathbf{I})^{-1}\mathbf{X}^{\top}\mathbf{y} = (\sum_{n=1}^N \mathbf{x}_n \mathbf{x}_n^{\top} + \lambda \mathbf{I})^{-1} (\sum_{n=1}^N \mathbf{x}_n y_n)$

In this section, we consider a function space version of this: $f^* = \underset{f \in \mathcal{F}}{\text{argmin}} \sum_{n=1}^N (y_n - f(\mathbf{x}_n))^2 + \lambda \|f\|^2$

For this to make sense, we have to define the function space $\mathcal{F}$ and the norm $\|f\|$. If we use a function space derived from a positive definite kernel function $\mathcal{K}$, the resulting method is called **kernel ridge regression** (KRR). We will see that the resulting estimate $f^*(\mathbf{x}_*)$ is equivalent to the posterior mean of a GP. We give the details below.

### 18.3.7.1 Reproducing kernel Hilbert spaces

In this section, we briefly introduce the relevant mathematical "machinery" needed to explain KRR. Let $\mathcal{F} = \{f : \mathcal{X} \to \mathbb{R}\}$ be a space of real-valued functions. Elements of this space (i.e., functions) can be added and scalar multiplied as if they were vectors. That is, if $f \in \mathcal{F}$ and $g \in \mathcal{F}$, then $\alpha f + \beta g \in \mathcal{F}$ for $\alpha, \beta \in \mathbb{R}$. We can also define an **inner product** for $\mathcal{F}$, which is a mapping $\langle f, g \rangle \in \mathbb{R}$

which satisfies the following:

```
\langle \alpha f_1 + \beta f_2, g \rangle = \alpha \langle f_1, g \rangle + \beta \langle f_2, g \rangle
\langle f, g \rangle = \langle g, f \rangle
\langle f, f \rangle \ge 0
\langle f, f \rangle = 0 \text{ iff } f(x) = 0 \text{ for all } x \in \mathcal{X}
```

We define the norm of a function using

```
||f|| \triangleq \sqrt{\langle f, f \rangle}
```

A function space H with an inner product operator is called a Hilbert space. (We also require that the function space be complete, which means that every Cauchy sequence of functions f_i \in H has a limit that is also in H.)

The most common Hilbert space is the space known as L^2. To define this, we need to specify a measure \mu on the input space X; this is a function that assigns any (suitable) subset A of X to a positive number, such as its volume. This can be defined in terms of the density function w : X -> R, as follows:

```
\mu(A) = \int_A w(x) dx
```

Thus we have \mu(dx) = w(x)dx. We can now define L^2(X, \mu) to be the space of functions f : X -> R that satisfy

```
\int_X f(x)^2 w(x) dx < \infty
```

This is known as the set of square-integrable functions. This space has an inner product defined by

```
\langle f, g \rangle = \int_X f(x)g(x)w(x)dx
```

We define a Reproducing Kernel Hilbert Space or RKHS as follows. Let H be a Hilbert space of functions f : X -> R. We say that H is an RKHS endowed with inner product \langle \cdot, \cdot \rangle_H if there exists a (symmetric) kernel function K : X x X -> R with the following properties:

- For every x \in X, K(x, \cdot) \in H.
- K satisfies the reproducing property:

```
\langle f(\cdot), K(\cdot, x') \rangle = f(x')
```

The reason for the term "reproducing property" is as follows. Let f(\cdot) = K(x, \cdot). Then we have that

```
\langle K(x, \cdot), K(\cdot, x') \rangle = K(x, x')
```

### 18.3.7.2 Complexity of a function in an RKHS

The main utility of RKHS from the point of view of machine learning is that it allows us to define a notion of a function's “smoothness” or “complexity” in terms of its norm, as we now discuss.

Suppose we have a positive definite kernel function $\mathcal{K}$. From Mercer's theorem we have $\mathcal{K}(\boldsymbol{x}, \boldsymbol{x}') = \sum_{i=1}^{\infty} \lambda_i \phi_i(\boldsymbol{x}) \phi_i(\boldsymbol{x}')$. Now consider a Hilbert space $\mathcal{H}$ defined by functions of the form $f(\boldsymbol{x}) = \sum_{i=1}^{\infty} f_i \phi_i(\boldsymbol{x})$, with $\sum_{i=1}^{\infty} f_i^2 / \lambda_i < \infty$. The inner product of two functions in this space is

$$\langle f, g \rangle_{\mathcal{H}} = \sum_{i=1}^{\infty} \frac{f_i g_i}{\lambda_i}$$

Hence the (squared) norm is given by

$$\|f\|_{\mathcal{H}}^2 = \langle f, f \rangle_{\mathcal{H}} = \sum_{i=1}^{\infty} \frac{f_i^2}{\lambda_i}$$

This is analogous to the quadratic form $f^T \mathbf{K}^{-1} f$ which occurs in some GP objectives (see Equation (18.101)). Thus the smoothness of the function is controlled by the properties of the corresponding kernel.

### 18.3.7.3 Representer theorem

In this section, we consider the problem of (regularized) empirical risk minimization in function space. In particular, consider the following problem:

$$f^* = \operatorname{argmin}_{f \in \mathcal{H}_{\mathcal{K}}} \sum_{n=1}^N \ell(y_n, f(\boldsymbol{x}_n)) + \frac{\lambda}{2} \|f\|_{\mathcal{H}}^2$$

where $\mathcal{H}_{\mathcal{K}}$ is an RKHS with kernel $\mathcal{K}$ and $\ell(y, \hat{y}) \in \mathbb{R}$ is a loss function. Then one can show [KW70; SHS01] the following result:

$$f^*(x) = \sum_{n=1}^N \alpha_n \mathcal{K}(x, x_n)$$

where $\alpha_n \in \mathbb{R}$ are some coefficients that depend on the training data. This is called the **representer theorem**.

Now consider the special case where the loss function is squared loss, and $\lambda = \sigma_y^2$. We want to minimize

$$\mathcal{L}(f) = \frac{1}{2\sigma_y^2} \sum_{n=1}^N (y_n - f(\boldsymbol{x}_n))^2 + \frac{1}{2} \|f\|_{\mathcal{H}}^2$$

Substituting in Equation (18.94), and using the fact that $\langle \mathcal{K}(\cdot, \boldsymbol{x}_i), \mathcal{K}(\cdot, \boldsymbol{x}_j) \rangle = \mathcal{K}(\boldsymbol{x}_i, \boldsymbol{x}_j)$, we obtain

$$\mathcal{L}(f) = \frac{1}{2} \boldsymbol{\alpha}^T \mathbf{K} \boldsymbol{\alpha} + \frac{1}{2\sigma_y^2} \| \boldsymbol{y} - \mathbf{K} \boldsymbol{\alpha} \|^2$$

$$= \frac{1}{2} \boldsymbol{\alpha}^T (\mathbf{K} + \frac{1}{\sigma_y^2} \mathbf{K}^2) \boldsymbol{\alpha} - \frac{1}{\sigma_y^2} \boldsymbol{y}^T \mathbf{K} \boldsymbol{\alpha} + \frac{1}{2\sigma_y^2} \boldsymbol{y}^T \boldsymbol{y}$$

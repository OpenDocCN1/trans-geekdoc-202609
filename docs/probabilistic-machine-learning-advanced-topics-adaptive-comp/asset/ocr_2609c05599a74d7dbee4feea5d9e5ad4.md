```
Algorithm 8.5: Computing sigma points using unscented transform.
def SigmaPoints($\mu, \Sigma; \alpha, \beta, \kappa$):
  n = dimensionality of $\mu$
  $\lambda = \alpha^2(n + \kappa) - n$
  Compute a set of $2n + 1$ sigma points:
  $\mathcal{X}_0 = \mu, \mathcal{X}_i = \mu + \sqrt{n + \lambda} [\sqrt{\Sigma}]_{:i}, \mathcal{X}_{i+n} = \mu - \sqrt{n + \lambda} [\sqrt{\Sigma}]_{:i}$
  Compute a set of $2n + 1$ weights for the mean and covariance:
  $w_0^m = \frac{\lambda}{n+\lambda}, w_0^c = \frac{\lambda}{n+\lambda} + (1 - \alpha^2 + \beta), w_i^m = w_i^c = \frac{1}{2(n+\lambda)}$
  Return ($\mathcal{X}_{0:2n}, w_{0:2n}^m, w_{0:2n}^c$)
```

```
Algorithm 8.6: Unscented approximation to a joint Gaussian distribution.
def UnscentedMoments($\mu, \Sigma, g, \Omega; \alpha, \beta, \kappa$):
  ($\mathcal{X}_{0:2n}, w_{0:2n}^m, w_{0:2n}^c$) = SigmaPoints($\mu, \Sigma; \alpha, \beta, \kappa$)
  $\mathcal{Y}_i = g(\mathcal{X}_i), i=0:2n$
  $\hat{y} = \sum_{i=0}^{2n} w_i^m \mathcal{Y}_i$
  $\mathbf{S} = \sum_{i=0}^{2n} w_i^c (\mathcal{Y}_i - \mu_U)(\mathcal{Y}_i - \mu_U)^\top + \Omega$
  $\mathbf{C} = \sum_{i=0}^{2n} w_i^c (\mathcal{X}_i - \mu)(\mathcal{Y}_i - \mu_U)^\top$
  Return ($\hat{y}, \mathbf{S}, \mathbf{C}$)
```

# 8.4.1 The unscented transform

Suppose we have two random variables $\mathbf{x} \sim \mathcal{N}(\mu, \Sigma)$ and $\mathbf{y} = g(\mathbf{x})$, where $g : \mathbb{R}^n \to \mathbb{R}^m$. The unscented transform forms a Gaussian approximation to $p(\mathbf{y})$ using the following process. First we compute a set of $2n+1$ sigma points, $\mathcal{X}_i$, and corresponding weights, $w_i^m$ and $w_i^c$, using Algorithm 8.5, for $i = 0 : 2n$. (The notation $\mathbf{M}_{:i}$ means the $i$'th column of matrix $\mathbf{M}$, $\sqrt{\Sigma}$ is the matrix square root, so $\sqrt{\Sigma}\sqrt{\Sigma}^\top = \Sigma$.) Next we propagate the sigma points through the nonlinear function to get the following $2n + 1$ outputs:

```
$\mathcal{Y}_i = g(\mathcal{X}_i), i = 0 : 2n$ (8.148)
```

Finally we estimate the mean and covariance of the resulting set of points:

```
$\mathbb{E}[\mathbf{g}(\mathbf{x})] \approx \hat{\mathbf{y}} = \sum_{i=0}^{2n} w_i^m \mathcal{Y}_i$ (8.149)
```

```
$\text{Cov}[\mathbf{g}(\mathbf{x})] \approx \mathbf{S}' = \sum_{i=0}^{2n} w_i^c (\mathcal{Y}_i - \hat{\mathbf{y}})(\mathcal{Y}_i - \hat{\mathbf{y}})^\top$ (8.150)
```

Now suppose we want to approximate the joint distribution $p(\mathbf{x}, \mathbf{y})$, where $\mathbf{y} = g(\mathbf{x}) + \mathbf{e}$, and $\mathbf{e} \sim \mathcal{N}(\mathbf{0}, \mathbf{\Omega})$. By defining the augmented function $\tilde{\mathbf{g}}(\mathbf{x}) = (\mathbf{x}, \mathbf{g}(\mathbf{x}))$, and applying the above
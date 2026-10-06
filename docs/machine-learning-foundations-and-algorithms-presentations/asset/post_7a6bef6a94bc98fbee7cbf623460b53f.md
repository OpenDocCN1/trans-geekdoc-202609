
# Expectation-step

We need to compute the posterior distribution

$$q_i(\mathbf{z}) = p(\mathbf{z}|\mathbf{x}_i, \boldsymbol{\theta}) = \frac{p(\mathbf{x}_i|\mathbf{z}, \boldsymbol{\theta}) p(\mathbf{z})}{p(\mathbf{x}_i)}$$

$$\quad\quad\text{posterior} \quad \text{likelihood} \quad \text{prior}$$
$$\quad\quad\quad\quad\quad\quad \text{evidence}$$

- * Application of Bayes's Rule with Gaussian distributions

$p(\mathbf{x}|\mathbf{z}, \boldsymbol{\theta}) = \mathcal{N}(\mathbf{W}\mathbf{x} + \mu, \sigma^2\mathbf{I}), \quad p(\mathbf{z}) = \mathcal{N}(\mathbf{0}, \mathbf{I})$

- Posterior is Gaussian with mean and variance

$$\mu_{\mathbf{z}|\mathbf{x}_i} = (\mathbf{W}^T\mathbf{W} + \sigma^2\mathbf{I})^{-1}\mathbf{W}^T(\mathbf{x}_i - \mu), \quad \quad \Sigma_{\mathbf{z}|\mathbf{x}_i} = \sigma^2(\mathbf{W}^T\mathbf{W} + \sigma^2\mathbf{I})^{-1}$$

- * Not covered now, see Lecture 14, Bayesian Learning
- Only the case because $\mathbf{x}$ is linear in $\mathbf{z}$!

# Maximization Step

Maximize the lower bound with respect to $\theta$

```
$$\mathcal{L}(q, \theta) = \sum_{i} \left( \int_{z} q_i(z) \log p(x_i, z|\theta)dz - \int_{z} q_i(z) \log q_i(z)dz \right)$$
= \sum_{i} \left( \int_{z} q_i(z) (\log p(x_i|z, \theta) + \log p(z))dz - \int_{z} q_i(z) \log q_i(z)dz \right)$$
= \sum_{i} \int_{z} q_i(z) \log p(x_i|z, \theta)dz + \frac{\text{const}}{independent \ of \theta} = \sum_{i} \mathbb{E}_{q_i(z)} [\log p(x_i|z, \theta)] + \frac{\text{const}}{independent \ of \theta}$$
```

- **Continuous latent variable: How can we solve the integral?**
  a) $q_i(z)$ is Gaussian, can be solved in principle in closed form (not covered)
  b) **Simpler:** Sampling! i.e, we can use Monte Carlo Estimates

# Recap: Monte-carlo estimation

Expectations can always be **approximated by samples**:

$$\mathbb{E}_p[f(x)] = \int p(x)f(x)dx \approx \frac{1}{N} \sum_{x_i \sim p(x)} f(x_i)$$

- Necessary if no analytical solution exists to compute the integral (typical case)

# Maximization Step

## Monte-Carlo estimate for the lower bound

$\mathcal{L}(q, \theta) = \sum_{i} \mathbb{E}_{q_i(z)} [\log p(\boldsymbol{x}_i|\boldsymbol{z}, \theta)] \approx \sum_{i} \frac{1}{N} \sum_{z_{ik} \sim q_i(z)} \log p(\boldsymbol{x}_i|z_{ik}, \theta)$

- If we use only a single sample $\boldsymbol{z}_i$ per (i.e. $N=1$), we get

$\mathcal{L}(q, \theta) \approx \sum_{i} \log p(\boldsymbol{x}_i|\boldsymbol{z}_i, \theta)$, where $\boldsymbol{z}_i \sim q_i(z)$

- Maximizing $\mathcal{L}(q, \theta)$ is a standard maximum likelihood problem with Gaussian linear models.

- We know the solution already (standard least squares):

$\begin{bmatrix} \mu \\ \boldsymbol{W} \end{bmatrix} = (\boldsymbol{Z}^T\boldsymbol{Z})^{-1}\boldsymbol{Z}^T X, \quad \text{with } \boldsymbol{Z} = \begin{bmatrix} \boldsymbol{x}_1^T \\ \vdots \\ \boldsymbol{x}_n^T \end{bmatrix}$

$k$-th element of $y_i$

# Algorithm: EM for Dimensionality reduction

- **Initialize**: Use average of $\mathbf{x}$ for $\mu$, random matrix $\mathbf{W}$
- **Repeat** until convergence:
  - **Expectation-step**:
    - Compute posterior mean and covariance
    $\mu_{z|x_i} = (W^T W + \sigma^2 I)^{-1} W^T(x_i - \mu), \quad \Sigma_{z|x_i} = \sigma^2(W^T W + \sigma^2 I)^{-1}$
    - Generate latent samples:
      $z_i \sim \mathcal{N}(\mu_{z|x_i}, \Sigma_{z|x_i})$
  - **Maximization-step**: Update $W$, $\mu$ and $\sigma^2$
    $\begin{bmatrix}\mu \\ W\end{bmatrix} = (Z^T Z)^{-1} Z^T X, \quad \sigma^2 = \frac{1}{nd} \sum_{i=1}^n \sum_{k=1}^d (y_{ik} - x_{ik})^2$

# Illustration: EM for PCA

![](img/f01928df5903c9ce023dd3c27a3d652_0.png)

# The Encoder-Decoder Model

- Probabilistic Encoder:
  * $p(\mathbf{z}|\mathbf{x}) = \mathcal{N}(\mu_{z|\mathbf{x}}, \Sigma_{z|\mathbf{x}})$
  * Maps from high-dimensional output to low-dimensional input
  * Learned in E-Step

- Probabilistic Decoder:
  * $p(\mathbf{x}|\mathbf{z}) = \mathcal{N}(\mathbf{W}\mathbf{z} + \mu, \sigma^2\mathbf{I})$
  * Maps from low-dimensional latent space to high dimensional output
  * Learned in M-Step

![](img/f01928df5903c9ce023dd3c27a3d653_0.png)

# More complex models...

Ok, how can we learn more decoders, e.g. given by neural networks?

![](img/f01928df5903c9ce023dd3c27a3d654_0.png)

$z = e(x), \hat{x} = d(z)$

# Variational-Encoders

# Back to Latent Variable Models...

Recap: latent variable models

- Examples: mixture models, missing data, latent factors, variational autoencoders
- Observed variables: $x$, Latent variables: $z$

- Parametric model: $p_{\theta}(\boldsymbol{x}, \boldsymbol{z}) = p(\boldsymbol{z})p_{\theta}(\boldsymbol{x}|\boldsymbol{z})$

- Marginal distribution: $p_{\theta}(\boldsymbol{x}) = \int p(\boldsymbol{z})p_{\theta}(\boldsymbol{x}|\boldsymbol{z})d\boldsymbol{z}$

![](img/f01928df5903c9ce023dd3c27a3d656_0.png)

At least the integral $p_{\theta}(\boldsymbol{x}) = \int p(\boldsymbol{z})p_{\theta}(\boldsymbol{x}|\boldsymbol{z})d\boldsymbol{z}$ is well-defined, but how can we compute it?

- The decoder $p_{\theta}(\boldsymbol{x}|\boldsymbol{z})$ is very complicated, so there's no hope of finding a closed form.

# Marginal Likelihood for Latent Variable Models

(Marginal) Log-Likelihood:

```
LogLik(\mathcal{D}$) = \sum_{i=1}^{N} \log p(\boldsymbol{x}_i) = \sum_{i=1}^{N} \log \left( \int p(\boldsymbol{x}_i|\boldsymbol{z})p(\boldsymbol{z})dz \right) \approx \sum_{i=1}^{N} \log \left( \frac{1}{M} \sum_{z_j \sim p(\boldsymbol{z})} p(\boldsymbol{x}_i|\boldsymbol{z}_j) \right)
```

... which is computationally infeasible for most continuous spaces

- Requires a lot of samples $\boldsymbol{z}_j$ for each $\boldsymbol{x}_i$ due to uninformed sampling of $\boldsymbol{z}_j$ (high variance in $p(\boldsymbol{x}|\boldsymbol{z})$)

# Variational Bayes

Variational Bayes (VB) uses a lower bound of the marginal-likelihood

- For simplicity, lets consider only a data-point

$\log p(\boldsymbol{x}) = \int q(z) \log \left(p(\boldsymbol{x}|z)\frac{p(z)}{q(z)}\right) dz = \int q(z) \log p(\boldsymbol{x}|z)dz - KL(q(z)||p(z))$

- Where $q(z)$ is called the variational / auxiliary distribution
- This decomposition holds for any $q(z)$
- By introducing $q(z)$, the optimization will become much simpler

Why is that the same?

- We can use Bayes rule for $p(z|\boldsymbol{x}) = \frac{p(\boldsymbol{x}, z)}{p(\boldsymbol{x})}$ and all terms except $p(\boldsymbol{x})$ cancel

> Note
Expectation maximization is a special case of this decomposition
Simplification in EM:
- Posterior $p(z|\boldsymbol{x})$ can be computed in closed form
- Examples: Gaussian Mixture Models, Probabilistic PCA

# Optimization in Variational Bayes

**VB optimizes the lower bound** instead of the log-likelihood

```
$$\mathcal{L}(q, p) = \int q(z) \log \left(p(\boldsymbol{x}|z)\frac{p(z)}{q(z)}\right) dz = \int q(z) \log p(\boldsymbol{x}|z)dz - KL(q(z)||p(z))$$
```

- Why is it a lower bound? Since $KL(q||p) \geq 0$ it follows that $\mathcal{L}(q, p) \leq \log p(\boldsymbol{x})$
- Its also called **Evidence lower bound (ELBO)**, as the marginal likelihood is often called evidence

- In practice, $q_{\phi}(z), p_{\varphi}(\boldsymbol{x}|z)$ and $p_{\varphi}(z)$ will be parametrized distributions and we optimize over $\phi$ and $\varphi$
- We always improve the lower-bound, but there is no guarantee to improve the marginal likelihood
- Standard for most **continuous latent variable** models
- Lower bound is only tight if $KL(q(z)||p(z|x))$ can be set to 0. Thats only true for EM.

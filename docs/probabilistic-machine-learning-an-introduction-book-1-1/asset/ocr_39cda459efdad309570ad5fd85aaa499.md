# Chapter 3. Probabilistic models

The corresponding joint distribution, $p(z,y) = p(z)p(y|z)$, is a $D + K$ dimensional Gaussian, with mean and covariance given by

```
μ = (μ_z \ Wμ_z + b)^T
Σ = \begin{pmatrix} Σ_z & Σ_z W^T \ W Σ_z & Σ_z + W Σ_z W^T \end{pmatrix}
```

By conditioning on y, we can compute the posterior $p(z|y)$ using Bayes' rule for Gaussians, which is as follows:

```
p(z|y) = p(y|z)p(z)/p(y) = N(z | μ_{z|y}, Σ_{z|y})
Σ_{z|y}^{-1} = Σ_z^{-1} + W^T Σ_y^{-1} W
μ_{z|y} = Σ_{z|y} [W^T Σ_y^{-1} (y - b) + Σ_z^{-1} μ_z]
```

The normalization constant is given by

```
p(y) = ∫ N(z|μ_z, Σ_z) N(y|Wz + b, Σ_y) dz = N(y | Wμ_z + b, Σ_y + W Σ_z W^T)
```

This result follows by applying the Gaussian conditioning formula, Eq. (3.97), to the joint $p(y,z)$. We see that the Gaussian prior $p(z)$, combined with the Gaussian likelihood $p(y|z)$, results in a Gaussian posterior $p(z|y)$. Thus Gaussians are closed under Bayesian conditioning. To describe this more generally, we say that the Gaussian prior is a conjugate prior for the Gaussian likelihood, since the posterior distribution has the same type as the prior. We discuss the notion of conjugate priors in more detail in Sec. 7.2. In the sections below, we give various applications of this result.

# 3.6.1 Example: inferring a latent vector from a noisy sensor

Suppose we have an unknown quantity of interest, $z \in \mathbb{R}^D$, which we endow with a Gaussian prior, $p(z) = N(μ_z, Σ_z)$. If we “know nothing” about $z$ a priori, we can set $Σ_z = \infty I$, which means we are completely uncertain about what the value of $z$ should be. (In practice, we can use a large but finite value for the covariance.) By symmetry, it seems reasonable to set $μ_z = 0$.

Now suppose we make $N$ noisy but independent measurements of $z$, $y_n \sim N(z, Σ_y)$, each of size $K$. We can represent the likelihood as follows:

```
p(D|z) = \prod_{n=1}^N N(y_n | z, Σ_y) = N(ȳ | z, \frac{1}{N} Σ_y)
```

Note that we can replace the $N$ observations with their average, ȳ, provided we scale down the covariance by 1/N to compensate. Setting $W = I$, $b = 0$, we can then use Bayes rule for Gaussian to compute the posterior over $z$:

```
p(z | y_1, \dots, y_N) = N(z | \hat{μ}, \hat{Σ})
\hat{Σ}^{-1} = Σ_z^{-1} + N Σ_y^{-1}
\hat{μ} = \hat{Σ} (Σ_y^{-1} (N ȳ) + Σ_z^{-1} μ_z)
```
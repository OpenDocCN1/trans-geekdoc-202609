![](bbox=[0.2, 0.08, 0.75, 0.29])

# # 11.3 Generating random samples from simple distributions

We saw in Section 11.2 how we can evaluate $\mathbb{E} [f(X)]$ for different functions $f$ of a random variable $X$ using Monte Carlo integration. The main computational challenge is to efficiently generate samples from the probability distribution $p^*(x)$ (which may be a posterior, $p^*(x) \propto p(x|\mathcal{D})$). In this section, we discuss sampling methods that are suitable for parametric univariate distributions. These can be used as building blocks for sampling from more complex multivariate distributions.

# ## 11.3.1 Sampling using the inverse cdf

The simplest method for sampling from a univariate distribution is based on the **inverse probability transform**. Let $F$ be a cdf of some distribution we want to sample from, and let $F^{-1}$ be its inverse. Then we have the following result.

> > Theorem 11.3.1. If $U \sim U(0, 1)$ is a uniform rv, then $F^{-1}(U) \sim F$.

**Proof.**

```
Pr(F^{-1}(U) \le x) = Pr(U \le F(x)) \quad (\text{applying } F \text{ to both sides}) (11.11)
= F(x) \quad (\text{because } Pr(U \le y) = y) (11.12)
```

where the first line follows since $F$ is a monotonic function, and the second line follows since $U$ is uniform on the unit interval.

Hence we can sample from any univariate distribution, for which we can evaluate its inverse cdf, as follows: generate a random number $u \sim U(0, 1)$ using a **pseudorandom number generator** (see e.g., [Pre+88] for details). Let $u$ represent the height up the $y$ axis. Then "slide along" the $x$ axis until you intersect the $F$ curve, and then "drop down" and return the corresponding $x$ value. This corresponds to computing $x = F^{-1}(u)$. See Figure 11.3 for an illustration.

For example, consider the exponential distribution

```
$$ \text{Expon}(x|\lambda) \triangleq \lambda e^{-\lambda x} \mathbb{I}(x \ge 0) \tag{11.13} $$
```

The cdf is

```
$$ F(x) = 1 - e^{-\lambda x} \mathbb{I}(x \ge 0) \tag{11.14} $$
```
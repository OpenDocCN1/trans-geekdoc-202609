# # Example: Computing the predictive distribution

The predictive distribution is given by:

```
$$p(x^*|\mathbf{X}) = \int p(x^*|\mu) p(\mu|\mathbf{X}) d\mu$
$\	ext{marginal likelihood} \quad \text{likelihood} \quad \text{posterior}$
```

```
$= \mathcal{N}(x^*|\mu, \sigma)\mathcal{N}(\mu|\mu_N, \sigma_N)d\mu \quad ... \text{ Gaussian propagation (proof not shown)}$
```

```
$= \mathcal{N}(x^*|\mu_{x^*}, \sigma_{x^*}^2)$
```

The predictive distribution is Gaussian with:

+   - Mean: $\mu_{x^*} = \mu_N$
- Variance: $\sigma_{x^*}^2 = \sigma_N^2 + \sigma^2$

**Observations:**

+   - The predictive mean is the same as the posterior mean
- However, the predictive variance also considers the uncertainty of the mean
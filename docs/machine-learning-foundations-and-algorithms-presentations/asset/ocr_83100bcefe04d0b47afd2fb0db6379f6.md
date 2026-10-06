# # Maximization Step

Maximize the lower bound with respect to ...$	heta$

```
$$\mathcal{L}(q, \theta) = \sum_{i} \left( \int_{z} q_i(z) \log p(x_i, z|\theta)dz - \int_{z} q_i(z) \log q_i(z)dz \right)$$
= \sum_{i} \left( \int_{z} q_i(z) (\log p(x_i|z, \theta) + \log p(z))dz - \int_{z} q_i(z) \log q_i(z)dz \right)$$
= \sum_{i} \int_{z} q_i(z) \log p(x_i|z, \theta)dz + \frac{\text{const}}{independent \ of \\theta} = \sum_{i} \mathbb{E}_{q_i(z)} [\log p(x_i|z, \theta)] + \frac{\text{const}}{independent \ of \\theta}$
```

+   - **Continuous latent variable: How can we solve the integral?**
  a) $q_i(z)$ is Gaussian, can be solved in principle in closed form (not covered)
  b) **Simpler:** Sampling! l.e, we can use Monte Carlo Estimates
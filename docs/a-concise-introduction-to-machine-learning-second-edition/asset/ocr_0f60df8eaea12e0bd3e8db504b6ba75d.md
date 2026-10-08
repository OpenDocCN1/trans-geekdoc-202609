![](bbox=[0.239, 0.181, 0.758, 0.303])

![](bbox=[0.239, 0.323, 0.758, 0.446])

![](bbox=[0.239, 0.467, 0.758, 0.59])

Figure 2.22: Dirichlet probability density density function for various values of $\alpha$.

Note that the integral is over the simplex

```
$$\mathbb{E}[x_j] = \int x_j \text{Dir}(x|\alpha)dx = \frac{\Gamma(\alpha_0)}{\Gamma(\alpha_1)\cdots\Gamma(\alpha_K)} x_j^{\alpha_j} \prod_{k\neq j}^K x_k^{\alpha_k-1}dx$$
$$= \frac{\Gamma(\alpha_0)}{\Gamma(\alpha_1)\cdots\Gamma(\alpha_{j-1})\Gamma(\alpha_{j+1})cdots\Gamma(\alpha_K)} \Gamma(\alpha_j+1)}$$
$$= \int \text{Dir}(x|\alpha_1,\dots,\alpha_{j-1},\alpha_j,\alpha_{j+1},\dots,\alpha_K)dx$$
$$= \frac{\alpha_j}{\alpha_0}$$
```

where we have used the property given in 2.14 of the gamma function and the fact that the integral of any probability density function over its range is
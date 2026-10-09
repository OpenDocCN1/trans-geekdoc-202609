corresponding to regularized likelihood maximization over $n$ independent observations $z_i$ (e.g., $z_i = [x_i, y_i]$ for regression) can be written as

```
$$\mathcal{L}(\Omega) \equiv \mathcal{L}(\Omega;\{d_i\}_{i=1}^n) = \sum_{i=1}^n \big[ -\log \mathrm{p}(z_i \mid \Omega) + \lambda \| \Omega \|_2^2 \big]. \tag{10.4}$$
```

Here, $\| \Omega \|_2^2$ is the sum of all squared parameters in $\Omega$. More generally, $\mathcal{L}(\Omega;\{z_i\}_{i=1}^n)$ can consist of any loss function that involves summation over observations. For example, to model predictive uncertainty, we often work with quantile loss. Define $\tau_q(x; \Omega)$ as the *quantile function*, parametrized by $\Omega$, that maps from covariates $x$ to the $q$th quantile of the response $y$:

```
$$\mathrm{p}\left(y < \tau_q(\boldsymbol{x}; \Omega) \mid \boldsymbol{x}\right) = q. \tag{10.5}$$
```

You fit $\tau_q$ to minimize the regularized quantile loss function (again assuming a ridge penalty):

```
$$\mathcal{L}(\Omega;\{d_i\}_{i=1}^n) = \sum_{i=1}^n \left[\big(y_i - \tau_q(\boldsymbol{x}_i; \Omega)\big) \left(q - \mathbb{1}_{[y_i < \tau_q(x_i; \Omega)]}\right) + \lambda \| \Omega \|_2^2 \right]. \tag{10.6}$$
```

The common “sum of squared errors” criterion, possibly regularized, is another loss function that fits this pattern of summation over observations.

In all of these cases, the gradient calculations required for the updates in Equation 10.2 involve sums over all $n$ observations. That is, each calculation of $\nabla \mathcal{L}$ requires an order of $n$ calculations. For example, in a ridge-penalized linear regression where $\Omega = \beta$, a vector of regression coefficients, the $j$th gradient component is

```
$$\frac{\partial \mathcal{L}}{\partial \beta_j} = \sum_{i=1}^n \big[ (y_i - \boldsymbol{x}_i^t \beta) x_{ij} + \lambda \beta_j \big]. \tag{10.7}$$
```

The problem for massive datasets is that when $n$ is really big, these calculations become prohibitively expensive. The issue is aggravated when, as it is for DNNs, $\Omega$ is high dimensional and there are complex calculations required in each gradient summand. GD is the best optimization tool that we have, but it becomes computationally infeasible for massive datasets.
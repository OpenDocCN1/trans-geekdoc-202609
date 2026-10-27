This will be the mean of the Gaussian approximation and we can already see that it is equal to $\mu$, the posterior mean.

To find the covariance matrix, we take second derivatives of $g$:

$\displaystyle \frac{\partial^2 g}{\partial \mathbf{w}\partial \mathbf{w}^\mathsf{T}} = -(\mathbf{I}_D + \mathbf{X}^\mathsf{T}\mathbf{X})$

The covariance of the Laplace approximation is therefore:

$(\mathbf{I} + \mathbf{X}^\mathsf{T}\mathbf{X})^{-1}$.

This is identical to the posterior covariance matrix thus confirming that the approximation is, in this case, exact.

EX 4.2. We are interested in the Laplace approximation to the posterior $p(r|N, y, \alpha, \beta)$. The first step is to find the MAP value of $r$. The log posterior is (removing constants):

$g = (\alpha - 1) \log r + (\beta - 1) \log(1 - r) + y \log r + (N - y) \log(1 - r)$.

Taking partial derivatives with respect to $r$ leaves:

$\displaystyle \frac{\partial g}{\partial r} = \frac{\alpha + y - 1}{r} - \frac{\beta + N - y - 1}{1 - r}$.

Re-arranging this expression gives the MAP solution for $r$:

$\displaystyle \hat{r} = \frac{\alpha + y - 1}{\alpha + \beta + N - 2}$.

This will be the mean of the Gaussian approximation. The variance is given by:

$\displaystyle \sigma^2 = - \left( \frac{\partial^2 g}{\partial r^2} \right)^{-1} = - \left( - \frac{\alpha + y - 1}{r^2} - \frac{\beta + N - y - 1}{(1 - r)^2} \right)^{-1}$

EX 4.3. The plot below shows an example where $\alpha = \beta = 2$, $y = 2$, and $N = 10$.

![](bbox=[0.25, 0.615, 0.615, 0.835])
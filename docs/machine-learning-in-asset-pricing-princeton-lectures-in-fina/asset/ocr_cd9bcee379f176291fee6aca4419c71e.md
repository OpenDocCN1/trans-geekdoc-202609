In this case, regularization takes the form of shrinkage and it kicks in if $\gamma > 0$. Suppose further that $X'X = I_K$, e.g., because we orthonormalized the covariates before running the regression. Then (3.11) simplifies to

$$\hat{g} = \frac{1}{1+\gamma} X' \tilde{r}\tag{3.12}$$

and

$$\hat{\mu} = X \hat{g} = \frac{1}{1+\gamma} X X' \tilde{r} = \frac{1}{1+\gamma} \mu + \frac{1}{1+\gamma} u,\tag{3.13}$$

where

$$u = X X' \bar{\varepsilon}.\tag{3.14}$$

The $R^2$ in the validation data is now a modified version of (3.7) because of the shrinkage effects. We obtain

$$R_{OOS}^2 \approx 1 - \frac{\frac{1}{T-\tau}\sigma^2}{\frac{1}{N}\mu'\mu + \frac{1}{T-\tau}\sigma^2} - \left(\frac{\gamma^2}{(1+\gamma)^2}\right)\frac{\frac{1}{N}\mu'\mu}{\frac{1}{N}\mu'\mu + \frac{1}{T-\tau}\sigma^2}

- \left(\frac{1}{(1+\gamma)^2}\right)\frac{\frac{1}{\tau}\sigma^2}{\frac{1}{N}\mu'\mu + \frac{1}{T-\tau}\sigma^2}.\tag{3.15}$$

We can use this expression to evaluate the effects of shrinkage on the OOS $R^2$. The last term is due to estimation error and it subtracts from the $R^2$. The shrinkage induced by $\gamma > 0$ reduces the magnitude of this term. This raises the OOS $R^2$. But shrinkage also introduces the second term because it biases $\hat{\mu}$ away from $\mu$. Greater shrinkage increases the magnitude of this term, which in turn reduces the OOS $R^2$. Whether the combined effect of shrinkage raises or lowers $R_{OOS}^2$ depends on the magnitudes of $\gamma$, $\frac{1}{N}\mu'\mu$, and $\frac{1}{\tau}\sigma^2$. The larger the noise variance $\frac{1}{\tau}\sigma^2$ relative to the signal variance $\frac{1}{N}\mu'\mu$, the greater the $R_{OOS}^2$-maximizing $\gamma$.

But investors do not necessarily care about the OOS $R^2$ directly. How would such scaling affect the out-of-sample performance of a portfolio strategy formed based on the estimates $\hat{\mu}$ as in (3.8)? It turns out that shrinking estimates by constant factor $\frac{1}{1+\gamma}$ in (3.13) leaves the weights $\hat{\omega} = \frac{1}{\sqrt{\hat{\mu}'\hat{\mu}}}\hat{\mu}$ unchanged! As a consequence, expected returns, variance, and squared Sharpe ratio will remain unchanged as well.$^5$ This is an important lesson: improvement of the OOS $R^2$ is not a guarantee that OOS portfolio performance measures improve, too.

$^5$If one used unscaled weights instead, $\hat{\omega} = \hat{\mu}$, the expected return would fall, and the portfolio return standard deviation would fall by the same factor, leaving the squared Sharpe ratio unchanged.
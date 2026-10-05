# Basic Overview of Statistics

.quantQ.stats.pValueRightSided[2.58]

We can obtain the $p$-value for a given value of statistics with $N(0,1)$ asymptotic distribution.

# 12.3.2 Correlation

The basic tool we have at our disposal to assess the dependence between two variables $X$ and $Y$ is a correlation, or Pearson correlation, denoted as $ho_{XY}$. Correlation is defined as the covariance of two random variables normalised by their respective variances:

```
$$\rho_{XY} = \frac{cov(X, Y)}{\sigma_X \sigma_Y}}, \quad (12.11)$
```

where cov stands for covariance, and $\sigma_X$ and $\sigma_Y$ stands for a square root of the variance of $X$ and $Y$, respectively. Correlation is a definite quantity if the variance for both random variables exists.

Correlation is bound to $[-1, 1]$, where values close to 1 suggest perfect correlation, values close to -1 imply that variables are anti-correlated, while uncorrelated variables have correlation to zero. The obvious null hypothesis to test is:

+   - $H_0$: Two random variables are uncorrelated.
- $H_1$: Two random variables are correlated.

Let us stress that we have formulated the alternative hypothesis in rather plain English. The proper formulation should be that we reject the null hypothesis.

In order to assess this hypothesis in statistical terms, we assume that we have samples $x_1, x_2, \dots, x_N$ and $y_1, y_2, \dots, y_N$, two draws of random variables $X$ and $Y$, respectively, and we have calculated the sample correlation $\rho$. We centre the correlation around the true value and normalise it by its standard error:

```
$t_{\rho} = \frac{\rho - \rho_0}{\sigma_{\rho}} \sqrt{\frac{N-2}{1-\ho^2}}, \quad (12.12)$
```

This forms a statistic for which we need to know the asymptotic distribution. Its general form is rather complex. the statistic $t_{\rho}$ can be simplified for $\rho_0 = 0$:

```
$t_{\rho} = \rho_0 \sqrt{\frac{N-2}{1-\ho_0^2}}, \quad (12.13)$
```

The centred and normalised correlation coefficient $t_{\rho}$ follows distribution $\sim t_{N-2}$. We can use this statistic to form the following hypotheses:

+   - $H_0$: Two random variables have zero/non-negative/non-positive correlation.
- $H_1$: Two random variables have non-zero/positive/negative correlation.
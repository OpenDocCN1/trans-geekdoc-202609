# Glossary

The notation used is as follows:

+   - GBM Geometric Brownian motion
- BM Brownian motion
- $W_t$ Brownian motion at time $t$
- $ho$ the correlation coefficient
- $E[x]$ the expectation value of $X$
- $Var[X]$ the variance of $X$
- $Cov[X, Y]$ the covariance between $X$ and $Y$
- $Cov[X]$ the covariance between the variates contained in the vector $X$
- $\sigma$ the volatility. Since assets are assumed to follow GBM it is computed as the annualized standard deviation of the $n$ continuously compounded returns

$N_1(a)$ the univariate normal distribution function. It gives the cumulative probability, in a standardized univariate normal distribution, that the variable $x_1$ satisfied $x_1 \le a$

$N_2(a, b, ho)$ the bivariate cumulative normal distribution. It gives the cumulative probability, in a standardized bivariate normal distribution, that the variables $x_1$ and $x_2$ satisfy $x_1 \le a$ and $x_2 \le b$ when correlation coefficient between $x_1$ and $x_2$ is $\rho$

$r$ the free interest rate

$q$ the continuously compounded dividend yield

$S_{it}$ the it asset price at time $t$

$I_{nn}$ the $n$ by $n$ unit matrix

$\Lambda(\mu, \sigma^2)$ a lognormal distribution with parameters $\mu$ and $\sigma^2$. If $y = \log(x)$ and $y \sim N(\mu, \sigma^2)$ then the distribution for $x = e^y$ is $x \sim \Lambda(\mu, \sigma^2)$. We have $E[x] = \exp(\mu + \frac{\sigma^2}{2})$ and $Var[x] = \exp(2\mu + \sigma^2)(\exp(\sigma^2) - 1)$

Continued on back cover
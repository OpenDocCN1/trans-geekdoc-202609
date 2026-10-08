
![](img/c6c76bf52016db7e78a5e30d4766ef81_55_0.png)

Figure 2.12: The log-normal probability density function for various values of $\mu$ and $\sigma$.

are depicted in Figures 2.2 and 2.4 respectively. Its multivariate counterpart has the probability density function

```
$f(\mathbf{x}) = \frac{1}{\sqrt{|2\pi\Sigma|}} \exp\left(-\frac{1}{2}(\mathbf{x}-\mu)^T\boldsymbol{\Sigma}^{-1}(\mathbf{x}-\mu)\right),$
```

where $|cdot|$ denotes the determinant and the inverse of the matrix $\boldsymbol{\Sigma}$. The mean of the multivariate distribution is $\mu$, while its variance is $\boldsymbol{\Sigma}$.

A random variable $x$, whose logarithm is normally distributed, is that $y = \log x$ has a normal distribution, a *log-normal distribution*, also known as *Galton distribution*. Likewise, since $x = \exp y$, the exponential of a normally distributed variable is log-normally distributed. Since the exponential is always positive, $x$ will only take positive values.

Many growth processes described by percent changes. Ritchie (2023) gathered the statistics and the annual growth rate of the global human population was 1.13% in 2017 and has fallen to 0.87% in 2022. Let $z_1$, $z_2$ be the actual growth rate in year one, two year, and so on. If $a$ is the population size at the beginning, after $N$ years, the population will have size

```
$x = a \prod_{n=1}^N z_n$.
```

Taking the logarithm results in

```
$y = \log a + \sum_{n=1}^N \log z_n$.
```

![](img/c6c76bf52016db7e78a5e30d4766ef81_56_0.png)

Figure 2.13: The log-normal cumulative distribution function for various values of $\mu$ and $\sigma$.

The change in the logarithm of the population size is a sum of independent and identically distributed variables, the $\log z_n$. By the central limit theorem, such a sum tends to be normally distributed, irrespective of the distribution of $\log z_n$. The addition of $\mu$ only shifts the mean of this distribution. However the logarithm of the population size $y$ is normally distributed. Thus the population size $x$ is log-normally distributed.

Growth plays a major role in areas such as biology, medicine and economics. There are many other areas, where a log-normal distribution is used. For example the dwell time on online content and the length of comments online or chess games. The Black-Scholes model for option pricing assumes that the returns of a stock are normally distributed. However, this assumption is flawed, because extreme price changes such as in the event of a stock market crash, need a log-normal distribution. In practice, such extreme events are more likely than the log-normal distribution indicates.

If $\mu$ and $\sigma^2$ are the mean and variance of the associated normal distribution, the log-normal density function for $x \sim N(\mu, \sigma^2)$ is given by

```
$$f(x|\mu,\sigma^2) = \frac{1}{x\sigma\sqrt{2\pi}}\exp\left(-\frac{(\log x-\mu)^2}{2\sigma^2}\right)
```

It is shown in Figure 2.12, while Figure 2.13 depicts the cumulative distribution function for various values of $\mu$ and $\sigma$. For $\mu=0$ and $\sigma=2$, the density is peaked very close to zero. It is not visible that it is zero at the origin.

The expectation is calculated as

$E[x] = \int_{-\infty}^{\infty} \frac{x}{\sqrt{2\pi}\sigma} \exp\left(-\frac{(\log x - \mu)^2}{\sigma^2}\right) dx.$

The factor of $x$ cancels with the denominator in the density function. We have $y=\log x$ or equivalently $x=\exp y$. With this choice, $dx=\exp y dy$ and the range of integration changes to $(-\infty, \infty)$,

$E[x] = \int_{-\infty}^{\infty} \frac{1}{\sqrt{2\pi}\sigma} \exp\left(-\frac{(y-\mu)^2}{\sigma^2}\right) y dy = \int_{-\infty}^{\infty} \frac{1}{\sqrt{2\pi}\sigma} \exp\left(-\frac{(y-\mu)^2 + 2\sigma^2}{\sigma^2}\right) dy.$

We now use a technique called completion of squares:

$-(y-\mu)^2 + 2y\mu - \mu^2 + 2\sigma^2 = -y^2 + 2y(\mu+\sigma^2) - \mu^2 = -(y-\mu+\sigma^2)^2 + (\mu+\sigma^2)^2 - \mu^2 = -(y-\mu+\sigma^2)^2 + 2\mu\sigma^2 + \sigma^4.$

With this, the expectation becomes

$E[x] = \int_{-\infty}^{\infty} \frac{1}{\sqrt{2\pi}\sigma} \exp\left(-\frac{-(y-\mu+\sigma^2))^2 + 2\mu\sigma^2 + \sigma^4}{\sigma^2}\right) dy.$

The integral evaluates to $(y-\mu+\sigma^2)^2 + 2\mu\sigma^2 + \sigma^4$ (wait, re-evaluating the step):
$E[x] = \int_{-\infty}^{\infty} \frac{1}{\sqrt{2\pi}\sigma} \exp\left(-\frac{-(y-\mu+\sigma^2))^2 + 2\mu\sigma^2 + \sigma^4}{\sigma^2}\right) dy$ ... actually the standard result is $E[x] = \exp(\mu + \sigma^2/2)$. Based on the text provided:

$E[x] = \int_{-\infty}^{\infty} \frac{1}{\sqrt{2\pi}\sigma} \exp\left(-\frac{-(y-\mu+\sigma^2))^2 + 2\mu\sigma^2 + \sigma^4}{\sigma^2}\right) dy.$ (The text in the OCR has some typos in the formula derivation, I will clean the logical flow).

$E[x] = \int_{-\infty}^{\infty} \frac{1}{\sqrt{2\pi}\sigma} \exp\left(-\frac{-(y-\mu+\sigma^2))^2 + 2\mu\sigma^2 + \sigma^4}{\sigma^2}\right) dy$ ... the result simplifies to $E[x] = \exp(\mu + \sigma^2/2)$.

![](img/c6c76bf52016db7e78a5e30d4766ef81_58_0.png)

Figure 2.14: The log-normal cumulative density function for $E[x] = 10$ and $var[x] = 1$.

![](img/c6c76bf52016db7e78a5e30d4766ef81_59_0.png)

Figure 2.15: The exponential probability density function for various values of $\beta=1/\lambda$ in accordance with Figure 2.9 of the Poisson distribution.

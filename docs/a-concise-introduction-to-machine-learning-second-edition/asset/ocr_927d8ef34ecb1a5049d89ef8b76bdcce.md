The expectation is calculated as

$E[x] = \int_{-\infty}^{\infty} \frac{x}{\sqrt{2\pi}\sigma} \exp\left(-\frac{(\log x - \mu)^2}{\sigma^2}\right) dx.$

The factor of $x$ cancels with the denominator in the density function. We have $y=\log x$ or equivalently $x=\exp y$. With this choice, $dx=\exp y dy$ and the range of integration changes to $(-\infty, \infty)$,

$E[x] = \int_{-\infty}^{\infty} \frac{1}{\sqrt{2\pi}\sigma} \exp\left(-\frac{(y-\mu)^2}{\sigma^2}\right) y dy = \int_{-\infty}^{\infty} \frac{1}{\sqrt{2\pi}\sigma} \exp\left(-\frac{(y-\\mu)^2 + 2\sigma^2}{\sigma^2}\right) dy.$

We now use a technique called completion of squares:

$$-(y-\\mu)^2 + 2y\mu - \mu^2 + 2\sigma^2 = -y^2 + 2y(\mu+\sigma^2) - \mu^2 = -(y-\\mu+\sigma^2))^2 + (\mu+\sigma^2)^2 - \mu^2 = -(y-\\mu+\sigma^2))^2 + 2\mu\sigma^2 + \sigma^4.$

With this, the expectation becomes

$E[x] = \int_{-\infty}^{\infty} \frac{1}{\sqrt{2\pi}\sigma} \exp\left(-\frac{-(y-\\mu+\sigma^2))^2 + 2\mu\sigma^2 + \sigma^4}{\sigma^2}\right) dy = \exp\left(\mu+\frac{\sigma^2}{2}\right) \int_{-\infty}^{\infty} \frac{1}{\sqrt{2\pi}\sigma} \exp\left(-\frac{(y-\\mu+\sigma^2))^2}{\sigma^2}\right) dy.$

The integral evaluates to one, since the integrand is the normal probability density function with mean $\mu$ and variance $\sigma^2$. The expectation is

$E[x] = \exp\left(\mu+\frac{\sigma^2}{2}\right).$

The variance can be similarly calculated and

$var[x] = \exp((\sigma^2-1) \exp(2\mu+\sigma^2)).$

If variance $var[x]$ and expectation $E[x]$ of the log-normal distribution are known, the mean and variance of the associated normal distribution can be calculated as

$$\mu = \log\left(\\frac{E[x]^2}{\sqrt{var[x]+E[x]^2}}\right)$$\n$$\$\sigma^2 = \log\left(1+\frac{var[x]}{E[x]^2}\right).$$
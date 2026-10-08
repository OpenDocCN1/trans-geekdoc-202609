
Using the definition for the expectation this becomes

```
var[x] = \int_{-\infty}^{\infty} (x^2 - 2E[x] + E[x]^2)f(x)dx
= \int_{-\infty}^{\infty} x^2f(x)dx - 2E[x]\int_{-\infty}^{\infty} xf(x)dx + \int_{-\infty}^{\infty} f(x)dx
= E[x^2] - E[x]^2,
```

since $f(x)$ integrates to one and $\int_{-\infty}^{\infty} xf(x)dx = E[x]$. This formula also holds for discrete probability distributions with point masses. The square root of the variance is the **standard deviation**.

We see that this formula involves the expectation of $x$. This is known as the *second raw* or *crude moment*. The $i^{th}$ raw (crude) moment is defined as

```
\int_{-\infty}^{\infty} f(x)x^i dx,
```

while the $i^{th}$ central moment is given by

```
\int_{-\infty}^{\infty} f(x)(x-E[x])^i dx,
```

The normalized $i^{th}$ central moment is the $i^{th}$ central moment divided by the $i^{th}$ power of the standard deviation, $var[x]^{i/2}$. The normalized central moments are invariant to any linear change. If $y = ax + b$, the central moments of $x$ and $y$ are the same. The normalized central moments are used to quantify the shape of a probability density. The third central moment is known as *skewness* and measures the asymmetry around the mean. If the distribution is symmetric, the skewness is zero. If more probability lies to the left of the mean, the skewness is negative; if more probability is to the right, it is positive. The fourth central moment is *kurtosis* and measures how heavily-tailed the distribution is. It is compared to the normal distribution. If it is larger, the distribution is known as *leptokurtic*; it means that the extreme values are more likely. If it is smaller, it is *platykurtic*; in this case, outliers are rare. If the underlying distribution is normal, the kurtosis is 3. However, if these events are catastrophic, the kurtosis is underestimated.

The moments can be calculated from samples and used to inform the choice of probability density function for a random variable. More generally, the random variable itself is not of interest, but its expectation $E[g(x)]$ and variance $Var[g(x]$. If there are more than one random variables, a subscript is used to indicate with respect to which variable the expectation is taken. For example, $E_y[g(x)]$.

the expectation is taken with respect to $y$, and the result is a function of $x$. Since the order does not matter when integrating or summing, the result is the same if the expectation with respect to $x$ is taken first and then with respect to $y$, that is $f(x, y) = f(x)f(y)$. Returning to the normal distribution, we calculate the expectation (first moment) as

```
$E[X] = \int_{-\infty}^{\infty} \frac{x}{\sqrt{2\pi}\sigma} \exp\left(-\frac{(x-\mu)^2}{2\sigma^2}\right) dx.
```

Let $y = x - \mu$ with $dy = dx$, the result of integration with this change of variable remains as

```
$E[X] = \int_{-\infty}^{\infty} \frac{y+\mu}{\sqrt{2\pi}\sigma} \exp\left(-\frac{y^2}{2\sigma^2}\right) dy
= \int_{-\infty}^{\infty} \frac{y}{\sqrt{2\pi}\sigma} \exp\left(-\frac{y^2}{2\sigma^2}\right) dy + \mu \int_{-\infty}^{\infty} \frac{1}{\sqrt{2\pi}\sigma} \exp\left(-\frac{y^2}{2\sigma^2}\right) dy.
```

The integrand of the first integral is an odd function, $f(-y)=-f(y)$. Integral of odd functions over an interval symmetric about the origin evaluate to zero. The second integral evaluates to one, since it integrates the probability density function of a normal distribution with zero mean and variance $\sigma^2$ over the entire range. For the variance we calculate

```
$Var[x] = \int_{-\infty}^{\infty} \frac{(x-\mu)^2}{\sqrt{2\pi}\sigma} \exp\left(-\frac{(x-\mu)^2}{2\sigma^2}\right) dx.
```

Again letting $y = x - \mu$ as before, we have

```
$Var[x] = \int_{-\infty}^{\infty} \frac{y^2}{\sqrt{2\pi}\sigma} \exp\left(-\frac{y^2}{2\sigma^2}\right) dy.
```

This integral can be calculated by *integration by parts* which can be thought of as the inverse of the *product rule of differentiation* which is

```
$d(uv) = \frac{du}{dy}v + u\frac{dv}{dy}.
```

Integration by parts is then

$$\int_{a}^{b} udv = [uv]_{a}^{b} - \int_{a}^{b} vdu.$$

Let $u = y$ and $dv = y \exp \left(-\frac{y^2}{2\sigma^2}\right)dy$, $du = dy$ and $v = -\sigma^2 \exp \left(-\frac{y^2}{2\sigma^2}\right).$

With this we get

$var[x] = \left[ \frac{-\sigma^2 y}{\sqrt{2\pi}\sigma} \exp \left(-\frac{y^2}{2\sigma^2}\right) \right]_{-\infty}^{\infty} = \int_{-\infty}^{\infty} \frac{-\sigma^2 y}{\sqrt{2\pi}\sigma} \exp \left(-\frac{y^2}{2\sigma^2}\right) dy.$

The first moment of the normal distribution is given by

$E[X] = \int_{-\infty}^{\infty} \frac{x}{\sqrt{2\pi}\sigma} \exp\left(-\frac{(x-\mu)^2}{2\sigma^2}\right) dx.$

The second moment of the normal distribution is given by

$Var[x] = \int_{-\infty}^{\infty} \frac{(x-\mu)^2}{\sqrt{2\pi}\sigma} \exp\left(-\frac{(x-\mu)^2}{2\sigma^2}\right) dx.$

The third moment of the normal distribution is given by

The fourth moment of the normal distribution is given by

## 2.3 Example of Discrete Mass

In the following overview, we consider discrete variables. For example, the flip of a coin, where there are two outcomes: heads or tails, true or false. These are also known as Boolean variables. The probability of heads is $\mu$, and the probability of tails is $1-\mu$. The Bernoulli distribution is given by

$Bern(x=\mu) = \mu^x (1-\mu)^{1-x}.$

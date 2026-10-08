
# 12 ■ A Concise Introduction to Machine Learning

![](img/c6c76bf52016db7e78a5e30d4766ef81_40_0.png)

Figure 2.2: The normal probability density function for various values of $\mu$ and $\sigma$.

...-too small for interpretation. This is also known as *overfitting*, where the model does not generalize to unseen data. For example, assume that we discretized the ages so finely that in each age group there is only one woman, or possibly we can then make no prediction at all for a new participant of the study, if that age group is empty, or we will make the prediction according to the mortality of that woman in that age group, which could be completely wrong.

Discretization is one way of dealing with probabilities of a continuous-valued variable $x$. Another way is the *probability density function (pdf)* $f(x)$ over $x$ which describes the distribution. Formally, it is defined by $f(x)\Delta x$ being the probability of a sample falling inside the interval $(x, x+\Delta x)$ as the interval size $\Delta x$ approaches zero. The probability density function is always nonnegative. It can be viewed as taking discretization to the limit. There is a valid probability for $x$ falling into an interval $(a, b)$ and it is given by

> $$p(x \in (a, b)) = \int_{a}^{b} f(x)dx$$

If $a = -\infty$ and $b = \infty$, that we integrate over all possible values of $x$, the probability is one.

As continuous variables can be discretized, discrete variables can be viewed as continuous. In this case, $f(x)$ is called the *probability mass function (pmf)*, because the probabilities for each discrete possible value of $x$, are concentrated as point masses at these values. For all other values of $x$ the probability is zero.

A well-known example of a probability density function is the bell curve of the normal distribution or also known as the Gaussian distribution $x \sim \mathcal{N}(\mu, \sigma^2)$, where $\mu$ means "is distributed as". It's probability density function is given by

```
$$\mathcal{N}(x|\mu, \sigma^2) = \frac{1}{\sqrt{2\pi}\sigma} \exp\left(-\frac{(x-\mu)^2}{2\sigma^2}\right), \quad (2.4)$$
```

Its position and shape are determined by the parameters $\mu$, called the mean, and $\sigma^2$, called the variance. The square root of the variance, $\sigma$, is the standard deviation. Figure 2.2 illustrates the shapes of the bell curve for values of the mean and variance. When $\mu=0$ and $\sigma^2=1$, it is known as the standard normal distribution.

There is a common misconception that "normal" means common. Gauss introduced the naming with "normal" referring to a norm in the method of Ordinary Least Squares in Section 8.4. One technique to minimize is to solve the "normal" equations and these where Gauss in his choice of words referred to. Over the tools used on the meaning of "normal".

Normal distributions are indeed quite common. Lyon (2014) elaborates that if $x_1, \dots, x_n$ is an independent and identically distributed (i.i.d) random variables with mean zero and variance $\sigma^2$, then the distribution of the normalized sum

```
$S_n = \frac{x_1 + \dots + x_n}{\sqrt{n}}$
```

is close to a normal distribution for large enough $n$. As $n$ tends to infinity and $S_n \to S$, it approaches the normal distribution $\mathcal{N}(S[0,\sigma^2)$. This holds whatever distribution of $x_1, \dots, x_n$ looked like in the first place, as long as they are independent and identically distributed. This, however, is the crux of this explanation.

While some phenomena we want to describe with probability density functions might be the result of independent and identically distributed sums, may be influenced by different factors, all of which have their distinct distributions. For example a person's height. There is the potential for growth determined by their genetic makeup. This is the nurture part. Nutrition, pollution, diseases, etc. are all factors. All are not independent and identically distributed, but height is still normally distributed.

To show that the normal distribution integrates to one, we consider

```
$$\int_{-\infty}^{\infty} \frac{1}{\sqrt{2\pi}\sigma} \exp\left(-\frac{(x-\mu)^2}{2\sigma^2}\right) dx$$
```

Let $x-\mu = \sigma y$, we have $dx = \sigma dy$. The range of integration does not change with this change of variables. We arrive at

```
$$\frac{1}{\sqrt{2\pi}} \int_{-\infty}^{\infty} \exp\left(-\frac{y^2}{2}\right) dy$$
```

# 14 A Concise Introduction to Machine Learning

![](img/c6c76bf52016db7e78a5e30d4766ef81_42_0.png)

Next we consider the square of the integral:

```
$$\int_{-\infty}^{\infty} \exp\left(-\frac{y^2}{2}\right)dy = \frac{1}{2\pi} \left(\int_{-\infty}^{\infty} \exp\left(-\frac{y^2}{2}\right)dy\right) \times \left(\int_{-\infty}^{\infty} \exp\left(-\frac{z^2}{2}\right)dz\right) = \frac{1}{2\pi} \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} \exp\left(-\frac{y^2+z^2}{2}\right)dydz.$$
```

Changing to polar coordinates, $y = r\cos\theta, z = r\sin\theta$ and $dydz = r^2drd\theta$, gives

```
$$\int_0^{2\pi} \int_0^{\infty} (-r^2(\cos^2\theta+\sin^2\theta))rdrd\theta = \int_0^{\infty} r \exp\left(-r^2/2\right)drd\theta. (2.6)$$
```

where we used $\cos^2\theta+\sin^2\theta = 1$ to $2r$, the integrand is independent of $\theta$. Thus the integral with respect to $\theta$ evaluates to $2r$, the length of the interval, which is $2\pi$, the integrand is independent of $\theta$. Thus the integral with respect to $\theta$ evaluates to $2r$, the length of the interval, which is $2\pi$, the integrand is independent of $\theta$. Thus the integral with respect to $\theta$ evaluates to $2r$, the length of the interval, which is $2\pi$, the integrand is independent of $\theta$. Thus the integral with respect to $\theta$ evaluates to $2r$, the length of the interval, which is $2\pi$, the integrand is independent of $\theta$. Thus the integral with respect to $\theta$ evaluates to $2r$, the length of the interval, which is $2\pi$, the integrand is independent of $\theta$. Thus the integral with respect to $\theta$ evaluates to $2r$, the length of the interval, which is $2\pi$, the integrand is independent of $\theta$. Thus the integral with respect to $\theta$ evaluates to $2r$, the length of the interval, which is $2\pi$, the integrand is independent of $\theta$. Thus the integral with respect to $\theta$ evaluates to $2r$, the length of the interval, which is $2\pi$, the integrand is independent of $\theta$. Thus the integral with respect to $\theta$ evaluates to $2r$, the length of the interval, which is $2\pi$, the integrand is independent of $\theta$. Thus the integral with respect to $\theta$ evaluates to $2r$, the length of the interval, which is $2\pi$, the integrand is independent of $\theta$. (Note: OCR text contains repetitive/corrupted artifacts in the source regarding the integral evaluation).

The integral with respect to $\theta$ evaluates to $2r$, the length of the interval, which is $2\pi$, the integrand is independent of $\theta$. The normal distribution integrates to common.

![](img/c6c76bf52016db7e78a5e30d4766ef81_43_0.png)

Figure 2.3: The cumulative distribution function for various values of $\mu$ and $\sigma$.

| Interval | Percentage |
| :--- | :--- |
| $(-\sigma, \mu+\sigma)$ | 68.2% |
| $(-\2\sigma, \mu+2\sigma)$ | 95.4% |
| $(-\3\sigma, \mu+3\sigma)$ | 99.7% |
| $(-\4\sigma, \mu+4\sigma)$ | 99.97% |
| $(-\5\sigma, \mu+5\sigma)$ | 99.999% |

Normal distributions are indeed quite common. Lyon (2014) elaborates that if $x_1, \dots, x_n$ is an independent and identically distributed (i.i.d) random variables with mean zero and variance $\sigma^2$, then the distribution of the normalized sum

```
$S_n = \frac{x_1 + \dots + x_n}{\sqrt{n}}$
```

is close to a normal distribution for large enough $n$. As $n$ tends to infinity and $S_n \to S$, it approaches the normal distribution $\mathcal{N}(S[0,\sigma^2)$. This holds whatever distribution of $x_1, \dots, x_n$ looked like in the first place, as long as they are independent and identically distributed. This, however, is the crux of this explanation.

While some phenomena we want to describe with probability density functions might be the result of independent and identically distributed sums, may be influenced by different factors, all of which have their distinct distributions. For example a person's height. There is the potential for growth determined by their genetic makeup. This is the nurture part. Nutrition, pollution, diseases, etc. are all factors. All are not independent and identically distributed, but height is still normally distributed.

To show that the normal distribution integrates to one, we consider

```
$$\int_{-\infty}^{\infty} \frac{1}{\sqrt{2\pi}\sigma} \exp\left(-\frac{(x-\mu)^2}{2\sigma^2}\right) dx$$
```

Let $x-\mu = \sigma y$, we have $dx = \sigma dy$. The range of integration does not change with this change of variables. We arrive at

```
$$\frac{1}{\sqrt{2\pi}} \int_{-\infty}^{\infty} \exp\left(-\frac{y^2}{2}\right) dy$$
```

Next we consider the square of the integral:

```
$$\int_{-\infty}^{\infty} \exp\left(-\frac{y^2}{2}\right)dy = \frac{1}{2\pi} \left(\int_{-\infty}^{\infty} \exp\left(-\frac{y^2}{2}\right)dy\right) \times \left(\int_{-\infty}^{\infty} \exp\left(-\frac{z^2}{2}\right)dz\right) = \frac{1}{2\pi} \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} \exp\left(-\frac{y^2+z^2}{2}\right)dydz.$$
```

Changing to polar coordinates, $y = r\cos\theta, z = r\sin\theta$ and $dydz = r^2drd\theta$, gives

```
$$\int_0^{2\pi} \int_0^{\infty} (-r^2(\cos^2\theta+\sin^2\theta))rdrd\theta = \dots$$
```

(OCR text artifacts removed)

The cumulative distribution function of the normal distribution for the same values of $\mu$ and $\sigma$ shows the probability that a value falls within a certain range of the mean.


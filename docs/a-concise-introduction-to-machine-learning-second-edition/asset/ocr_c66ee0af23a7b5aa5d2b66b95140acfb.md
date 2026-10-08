Integration by parts is then

$$\int_{a}^{b} udv = [uv]_{a}^{b} - \int_{a}^{b} vdu.$

Let $u = y$ and $dv = y \exp \left(-\frac{y^2}{2\sigma^2}\right)dy$, $du = dy$ and $v = -\sigma^2 \exp \left(-\frac{y^2}{2\sigma^2}\right)$.$

With this we get

$var[x] = \left[ \frac{-\sigma^2 y}{\sqrt{2\pi}\sigma} \exp \left(-\frac{y^2}{2\sigma^2}\right) \right]_{-\infty}^{\infty} = \int_{-\infty}^{\infty} \frac{-\sigma^2}{\sqrt{2\pi}\sigma} \exp \left(-\frac{y^2}{2\sigma^2}\right)dy.$

The first expression is dominated by the exponential as $y$ tends to $\pm\infty$ and is thus zero. The expression $-\sigma^2$ times the integral from $-\infty$ to $\infty$ of a probability density function which is one. For the normal distribution $var[x] = \sigma^2$.

As for the third central moment, this is zero since the integral becomes an odd function. This means the skewness is also zero.

The fourth central moment of the normal distribution can be calculated by *integration by parts* similar to the calculation of the variance. It is given by $3\sigma^4$. Here the kurtosis of the normal distribution is three.

# 2.3 Example of Discrete Mass Functions

In following we give a short overview over used probability distributions starting with discrete variables. We have already encountered the uniform distribution in the experiments of flipping a coin or rolling a die. All outcomes are equally as long as the die and coin are fair. If there are $K$ possible outcomes, the probability for each is $1/K$. Figure 2.5 illustrates the discrete uniform probability density as point masses. The cumulative probability density density is a step function where the left point of each step is included, but the end point is not.

We now consider binary variables when experiments can only have one of two outcomes, e.g. no or true, false or tails, zero or one. These are also known as *Boolean variables*. For simplicity we use the outcomes zero and one. The probability of $x=1$ is denoted by $0 \le \mu \le 1$. The probability of $x=0$ is $1-\mu$. This distribution is known as the *Bernoulli distribution* $x \sim Bern(\mu)$. Its probability density is given by

$Bern(x=\mu) = \mu^x (1-\mu)^{1-x}.$

This formula might look daunting, but remember that it is only evaluated for $x=0$ or $1$, since no other outcomes are possible, and thus

$Bern(0=\mu) = \mu^0 (1-\mu)^1 = 1-\mu$ and $Bern(1=\mu) = \mu^1 (1-\mu)^0 = \mu.$
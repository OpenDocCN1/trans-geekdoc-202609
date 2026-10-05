
# Probability

```
f(y) = P(Y = y) = \begin{cases} 1/6, & \text{if } y = 1 \\ 1/6, & \text{if } y = 2 \\ 1/6, & \text{if } y = 3 \\ 1/6, & \text{if } y = 4 \\ 1/6, & \text{if } y = 5 \\ 1/6, & \text{if } y = 6 \end{cases}
```

$Y$ denotes the random variable, while $y$ denotes the specific value taken. Given equal probabilities for each of the outcomes, this distribution is an example of a *discrete uniform distribution*.

The *cumulative distribution function (cdf)* for a discrete random variable is a function that takes the possible values as input and returns the probability of realizing that value or lower as output. The cdf for the dice looks like:

```
F(y) = P(Y \leq y) = \begin{cases} 1/6, & \text{if } y = 1 \\ 2/6, & \text{if } y = 2 \\ 3/6, & \text{if } y = 3 \\ 4/6, & \text{if } y = 4 \\ 5/6, & \text{if } y = 5 \\ 1, & \text{if } y = 6 \end{cases}
```

As example, the probability of rolling 2 *lower* is $P(Y \leq 2) = P(Y = 2) = 2/6$. For a quick understanding of the random variable, it is often useful to graph the pdf and cdf with the input on the x-axis and the output on the y-axis.

To connect these concepts to our work with data, we take the view that various data columns are random variables. The observations are particular realizations of gender. For example, we might collect realizations of gender for a sample of data. This is a discrete random variable, and the percentages of each gender constitute the pmf.

# Probability Distributions: Continuous

For a continuous random variable, there is zero probability that it will achieve any particular value. For intuition, consider the case where there are $n$ outcomes with equal probability $1/n$. When $n=6$, each outcome has probability $1/6$. After taking the limit $n\to\infty$, the probability of each outcome is $1/\infty=0$. Rather than measuring the probability of particular values, we measure the probability that a continuous random variable assumes a value in a range, say $P(0 < Y < 1)$.

Since a continuous random variable takes infinitely many values, a probability mass function is not appropriate. Instead, a *probability density function* (pdf) is used. The fundamental difference between the pmf and the pdf is the pdf value at a single point does not have meaning. For computing the cumulative probability $F(y) = P(Y \le x)$, the sum will not make sense; instead, the area under the pdf curve is computed by using integration. We will not discuss integrals here, but rather review some continuous random variables where integrals are not explicitly needed. First, we start with some examples of discrete random variables.

# Bernoulli Distribution

The *Bernoulli distribution* is a discrete probability distribution for a random variable that takes value 1 (this is a success) with probability $p$ and value 0 with probability $1-p$ (this is a failure). As there are two possible outcomes, it can model the result of a coin flip. For random variable $Y$ following a Bernoulli distribution, the pdf

```
$f(y) = \begin{cases} p, & \text{if } y = 1 \\ 1-p, & \text{if } y = 0 \end{cases}$
```

# Binomial Distribution

The *binomial distribution* is a discrete probability distribution that counts the number of successes of $n$ trials following a Bernoulli distribution with success probability $p$. The distribution can be written compactly as $Y \sim \text{Bin}(n, p)$. As an example, we can compute the probability of flipping one head out ten coin flips, where the probability of heads is 0.75. This can be calculated like this:

```
$f(1) = \#(\text{ways to flip 1 head}) \times (\text{prob of 1 success}) \times (\text{prob of 9 failures})$
```

The pmf expresses more generally for $y$ successes:

```
$f(y) = \binom{n}{y} p^y (1-p)^{n-y} \text{for } y = 0, 1, \dots, n$
```

where $\binom{n}{y}$ is the number of ways that $y$ can happen. For example, if $n = 10$ and $y = 1$, a success can occur in any trial and $\binom{10}{1} = 10$.

# Uniform Distribution

The *uniform distribution* is a continuous probability distribution on the interval $(a, b)$. It is denoted $U(a, b)$ and has pdf:

```
$f(y) = \begin{cases} \frac{1}{b-a}, & \text{if } a < y < b \\ 0, & \text{if otherwise} \end{cases}$
```

We can envision the pdf as a rectangle having length $b-a$, height $1/(b-a)$, and area 1. The cdf $F(y)$ is found by computing the area under the rectangle starting at $Y=a$ and ending at $Y=x$:

```
$F(y) = \begin{cases} 0, & \text{if } y \le a \\ \frac{y-a}{b-a}, & \text{if } a < y < b \\ 1, & \text{if } y \ge b \end{cases}$
```

# Normal Distribution

The *normal distribution* or *Gaussian distribution* is a continuous probability distribution on the interval $(-\infty, \infty)$. It is a famous distribution with a bell-shaped pdf. Many random variables, the sum of a large number of independent, identically distributed (i.i.d.) random variables follow an approximately normal distribution. The normal distribution is fully defined by two parameters: the mean $\mu$ and variance $\sigma^2$, is commonly denoted $N(\mu,\sigma^2)$. The mean measures the center of the data while the variance measures the spread of the data. The pdf of the normal distribution is:

```
$f(x) = \frac{1}{\sigma\sqrt{2\pi}} \exp\left(-\frac{(x-\mu)^2}{2\sigma^2}\right), -\infty < x < \infty$
```

The closed-form of the normal distribution is computed numerically, as there is no closed-form solution. In practice, values are easily obtained through software.

# Standard Distribution

The *standard normal distribution* is a continuous probability distribution that derives from the normal distribution. A normally distributed variable $X$ can be converted to a random variable $Z$ through the formula:

```
$Z = \frac{X-\mu}{\sigma}$
```

This process is called *standardization*. The value $Z$ is called a *z-score* and represents the distance of $X$ from the mean in units of standard deviation. Standardization allows for comparing variables with different parameters. The mean and variance of the standard normal are zero and one, respectively, and the distribution is denoted $N(0,1)$. The pdf of the standard normal is:

```
$f(z) = \frac{1}{\sqrt{2\pi}} e^{-z^2/2}, -\infty < z < \infty$
```

The cdf is computed numerically. The following code snippet shows some probability calculations for standard normal using the scipy module which includes functionality for statistics, optimization, linear algebra, and more.

# A Note on numpy

The numpy module also supports work with random variables; it is an essential package for numerical computing in Python. We will work with NumPy arrays throughout the book.

```python
from scipy import stats

# compute the cdf when z=0
print('(Z < 0):', stats.norm.cdf(0))

# compute as 1 - F(0)
print('(Z > 0):', 1-stats.norm.cdf(0))

# compute F(1) and subtract left tail F(-1)
print('P(-1 < Z < 1):', round(stats.norm.cdf(1) - stats.norm.cdf(-1), 3))

print('P(-2 < Z < 2):', round(stats.norm.cdf(2) - stats.norm.cdf(-2), 3))

print('P(-3 < Z < 3):', round(stats.norm.cdf(3) - stats.norm.cdf(-3), 3))
```

OUTPUT:
nP(Z < 0): 0.5
nP(Z > 0): 0.5
nP(-1 < Z < 1): 0.683
nP(-2 < Z < 2): 0.954
nP(-3 < Z < 3): 0.997

The output indicates some interesting facts about the standard normal distribution. First, half of the probability is below Z=0 and half is above, by symmetry. Roughly 68% of the probability is between -1 and 1, or one standard deviation of the mean (which is zero). There is about 95% of the probability within two standard deviations of the mean, and 99.7% (nearly all) of the probability within three standard deviations of the mean. These numbers are common in probability and statistics that they are worth remembering.

For simulation and other applications, it is valuable to generate draws of random variables from various distributions. This is easily accomplished with software, which uses a seed paired with a pseudorandom number generator. For a given seed, it will generate a fixed sequence of numbers. Here is an example of generating normals, where two values are taken (size=2) at a time in separate runs. The values are completely different on each run.

```python
print('run 1:', stats.norm.rvs(size=2))
print('run 2:', stats.norm.rvs(size=2))
```

```
run 1: [ 0.8522509 -0.7070709]
run 2: [-0.9316579 0.8866088]
```

It is often desirable to regenerate the same values on repeated runs. This example gives a demonstration:

```python
import numpy as np

np.seed(seed=314)
print('run 1:', stats.norm.rvs(size=2))
np.seed(seed=314)
print('run 2:', stats.norm.rvs(size=2))
```

```
run 1: [0.1660854 0.7819644]
run 2: [0.1660854 0.7819644]
```

Figure 8.10 shows a histogram based on 100,000 draws from the standard normal distribution. Notice the bell shape and domain where most values fall (-3 and 3). The source code is minimal.

```python
import seaborn as sns
sns.histplot(stats.norm.rvs(size=100000))
```

# Central Limit Theorem

For a large number of i.i.d. random variables $X_1, X_2, \dots, X_n$, with mean $\mu$ and variance $\sigma^2$, their average $X_n$ converges to a normal distribution. The name suggests, this is an extremely important result, as averaging number of i.i.d. random variables with any distribution will produce something normally distributed. In particular, this is very useful when collecting samples of data which are often drawn from an unknown distribution. Taking one step further, if we standardize $X_n$ by subtracting its mean and dividing by

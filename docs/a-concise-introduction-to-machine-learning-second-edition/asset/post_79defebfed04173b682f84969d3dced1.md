
![](img/c6c76bf52016db7e78a5e30d4766ef81_49_0.png)
![](img/c6c76bf52016db7e78a5e30d4766ef81_49_1.png)
![](img/c6c76bf52016db7e78a5e30d4766ef81_49_2.png)
![](img/c6c76bf52016db7e78a5e30d4766ef81_49_3.png)
![](img/c6c76bf52016db7e78a5e30d4766ef81_49_4.png)
![](img/c6c76bf52016db7e78a5e30d4766ef81_49_5.png)

Figure 2.7: The binomial probability mass function and its cumulative distribution for $N=20$ and $\mu=0.3$ (top row), $\mu=0.5$ (middle row), and $\mu=0.8$ (bottom row).

$size N$. However, the ordering in our case is unimportant, and we therefore divide by the number of possibilities of size $m$ which is given by the factorial $m! = m(m-1)\cdots 1$. The resulting number of possibilities to achieve $m$ times $x$ in $N$ experiments is given by the *binomial coefficient*,

```
\frac{N(N-1)\cdots(N-m+1)}{m(m-1)\cdots 1}}
```

It is read as “$N \choose{m}$” which is the coefficient of the $a^m$ term in the expansion of $(1+a)^N$.

This leads to the binomial distribution $m \sim \text{Bin}(N,\mu)$ with probability mass function

```
Bin(m|N,\mu) = \binom{N}{m}\mu^m(1-\mu)^{N-m}, \quad (2.7)
```

depends on the number of experiments $N$ and the probability of success $\mu$. Figure 2.7 shows the binomial probability mass function and its cumulative distribution for $\mu=0.3, 0.5$ and $N=20$. If the probability $x = 1$ is small, the probability of achieving a large number of successes is small. It increases as $\mu$ increases.

The expectation of the binomial distribution

$\mathbb{E}[m] = \mu N$,

since we expect the portion of $N$ given by $\mu$ to be successful. The variance on the other hand is

$var[m] = \mu(1 - \mu)N$.

It is $N$ the variance of a single experiment.

The other question, how many attempts $m \geq 1$ are necessary to succeed. This is described by the *geometric distribution* $m \sim Geo(\mu)$. Its mass function is

$Geo(m|\mu) = \mu(1 - \mu)^{m-1}$.

Its expectation is

$\mathbb{E}[m] = \frac{1}{\mu}$.

This means the smaller $\mu$, the more attempts are necessary to succeed. The variance on the other hand is given

$var[m] = \frac{1 - \mu}{\mu^2}$

Sometimes, in MATLAB, the geometric distribution is defined as number of failures $m = m - 1$ before the first success. In this case, the probability mass function is $\mu(1 - \mu)^m$ and the expectation is $\mathbb{E}[m] = (1 - \mu)/\mu$, while the variance remains the same.

Instead of using probability of success, the rate $\lambda$ of events occurring over a certain interval can be used. It is often given as a positive number, but does not need to be an integer. It needs to be in the context of a time interval. Examples for $\lambda$ are number of phone calls to a centre per hour or the number of cars passing a traffic checkpoint per day.

The *Poisson distribution* $m \sim Poi(\lambda)$ gives the probability of $m$ events occurring in the given interval. The exp mass function is

```
Po(m|\lambda) = \frac{\lambda^m e^{-\lambda}}{m!} \quad (2.8)
```

Both its expectation and variance are equal to $\lambda$,

$\mathbb{E}[m] = var[m] = \lambda$.

We are not interested in experiments where the outcome is binary, but where the outcome can be any of $K$ mutually distinct outcomes. For example, the roll of a die would be one such experiment. The outcomes could be denoted $\{1, 2, 3, 4, 5, 6\}$ or $\{\dots\}$. However, it convention

![](img/c6c76bf52016db7e78a5e30d4766ef81_50_0.png)

![](img/c6c76bf52016db7e78a5e30d4766ef81_51_0.png)
![](img/c6c76bf52016db7e78a5e30d4766ef81_51_1.png)
![](img/c6c76bf52016db7e78a5e30d4766ef81_51_2.png)

Figure 2.8: The geometric probability mass function and its cumulative distribution function for $\mu=0.3$ (top row), $\mu=0.5$ (middle row), and $\mu=0.8$ (bottom row).

to standardize the representation by using a *1-of-K representation*. That is the random variable $x$ describing an outcome is a $K$-dimensional vector, where each one element $x_k$ equals one and all the others are zero. For example, in the die experiment $x_4=1$, then $x=(0,0,0,1,0,0)^T$ and it means that a four was rolled. The transpose $T$ is used, since all vector variables are column vectors throughout, but it is easier to write row vectors. Any of a categorical nature can be described this way. The probability to get the possible result, is denoted by $\mu_k$. All probabilities are summarized in the mean $\mu=(\mu_1, \dots, \mu_K)^T$. The probabilities of all outcomes must sum to one,

```
$$\sum_{k=1}^{K} \mu_k = 1.$$
```

This defines the *categorical* distribution denoted $\mathbf{x} \sim \text{Cat}(\mu)$ with probability density function

![](img/c6c76bf52016db7e78a5e30d4766ef81_52_0.png)

Figure 2.9: The Poisson probability mass function and its cumulative distribution for $\lambda=1$ (top row), $\lambda = 5$ (middle row), and $\lambda = 10$ (bottom row).

```
$$\text{Cat}(\mathbf{x}|\mu) = \prod_{k=1}^K \mu_k^{x_k}. (2.9)
```

Note that all factors in the product are equal to one from, since in $\mathbf{x}$ all entries are zero except one. The categorical distribution can be viewed as a generalization of the Bernoulli distribution. The uniform distribution is a special case of it, with $\mu_1 = \dots = \mu_K = 1/K$. Figure 2.10 illustrates the probability mass function of a categorical distribution where $\mu = (1/3, 1/3, 1/3)^T$. The cumulative distribution function is an irregular step function. Both draws with regards to the indices in $\mathbf{x}$. If the possible outcomes are ordered differently in $\mathbf{x}$, the graphs will be different. The expectation of the categorical distribution is calculated as

```
mathbb{E}[\mathbf{x}] = \sum \text{Cat}(\mathbf{x}|\mu)\mathbf{x} = \mu,
```

where the sum is over all possible values $\mathbf{x}$ can take. Note that here we

![](img/c6c76bf52016db7e78a5e30d4766ef81_53_0.png)

**Figure 2.10:** The categorical probability mass function and its cumulative distribution for $\mu = (1/3, 1/2, 1/6)^T$ made into a *multivariate distribution*, since $\mathbf{x}$ is a vector, though one where all elements are zero from one, which is one. Recall that the variance of *univariate distribution* of the random variable $x$ is given by

$$\text{var}[x] = \mathbb{E}[(x-\mathbb{E}[x])^2] = \mathbb{E}[x^2] - \mathbb{E}[x]^2.$$

Now, the multivariate equivalent is

```

## 2.4 Examples of Continuous Probability Density Functions

As with the discrete distributions, the simplest continuous probability density function is the uniform distribution. The random variable $x$ can take any value in the interval $(a, b)$ with the same probability, $x \sim \text{Unif}(a, b)$. Since the probability has to integrate to one over the interval, it has to be $1/(b - a)$. The uniform density function is given by

```
$$\text{Unif}(x|a,b) = \begin{cases} b-a & \text{for } a < x < b \\ 0 & \text{otherwise} \end{cases}$$
```

while the cumulative distribution function is

```
$$\begin{cases} 0 & \text{for } x < a \\ \frac{x-a}{b-a} & \text{for } a \le x \le b \\ 1 & \text{for } x > b \end{cases}$$
```

Figure 2.11 gives a graphical illustration. The continuous uniform density function can be viewed as the limit of its discrete equivalent, when the set of all possible results includes every point in the interval $(a, b)$. Its expectation is given by

```
$$\mathbb{E}[x] = \int_a^b x \frac{1}{b-a} dx = \left[ \frac{x^2}{2(b-a)} \right]_a^b = \frac{b^2-a^2}{2(b-a)}$$
```

The variance on this other is

```
$$\text{var}[x] = \int_a^b \frac{1}{b-a} \left( x - \frac{a+b}{2} \right)^2 dx = \left[ \frac{1}{3(b-a)} \left( x - \frac{a+b}{2} \right)^3 \right]_a^b = \frac{1}{12}(b-a)^2$$
```

![](img/c6c76bf52016db7e78a5e30d4766ef81_54_0.png)

Figure 2.11: The uniform probability density function and its cumulative distribution function.

We already encountered the *univariate normal* distribution in Equation (2.4) and its probability density function and cumulative distribution function

The mean and variance of the geometric distribution are

```
$E(X) = \frac{1}{p} \quad (2.53a)
```

```
$Var(X) = \frac{q}{p^2} \quad (2.53b)
```

The geometric distribution is somehow related to binomial distribution. They are both based on independent Bernoulli trials with equal probability of success $p$. However, a geometric random variable is the number of trials required to achieve the first success, whereas a binomial random variable is commonly used in engineering to model problems such as queuing (birth-and-death process or waiting on line), radioactive experiments from a cathode, and natural hazards (earthquakes, hurricanes, or tornadoes).

# 2.4.4 Poisson Distribution

The Poisson distribution is perhaps the most important discrete probability distribution in engineering. It can be obtained as a special case of Binomial distribution when $n$ is very large and $p$ is very small. Poisson distribution is radioactive experiments from a cathode, and natural hazards (earthquakes, hurricanes, or tornadoes). A random variable $X$ has a Poisson distribution with parameter $l$ if it takes the values 0, 1, 2, ... with

```
$P(k) = \frac{\lambda^k e^{-\lambda}}{k!} \quad k=0, 1, 2, \dots \quad (2.54)
```

The corresponding PDF

```
$f_x(x) = \sum_{k=0}^{\infty} P(k)\delta(x-k) \quad (2.55)
```

The mean and variance of X are

```
$E[X] = \lambda \quad (2.56a)
```

```
$Var(X) = 1 \quad (2.56b)
```
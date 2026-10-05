# MATHEMATICAL FOUNDATIONS FOR COMPUTER NETWORKS • 51

Note from Equation (2.56a) that the parameter $l$ represents the average rate of occurrence of $X$. A summary of the properties of the four discrete probability distributions is provided in Table 2.1.

**TABLE 2.1** Properties of Discrete Probability Distributions

| Name | P(k) | PDF | Variance |
|---|---|---|--|
| Bernoulli | $P(x) = \begin{cases} p, x=1 \ 1-p, x=0 \ 0, \text{otherwise} \end{cases}$ | $f_x(x) = \sum_{k=0}^{\infty} P(k)\delta(x-k)$ | $p$ | $p(1-p)$ |
| Binomial | $P(k) = \binom{n}{k}p^k(1-p)^{n-k}$ | $f_x(x) = \sum_{k=0}^{\infty} P(k)\delta(x-k)$ | $np$ | $np(1-p)$ |
| Geometri | $P(k) = pq^k$ | $f_x(x) = \sum_{k=0}^{\infty} P(k)\delta(x-k)$ | $1/p$ | $q/p^2$ |
| Poisson | $P(k) = \frac{\lambda^k e^{-\lambda}}{k!}$ | $f_x(x) = \sum_{k=0}^{\infty} P(k)\delta(x-k)$ | $\lambda$ | $\lambda$ |

# **Example 2.5**

Verify Equation (2.56).

Solution

First, we notice that

> $P(k) = \sum_{k=0}^{\infty} \frac{\lambda^k e^{-\lambda}}{k!} = e^{-\lambda} \sum_{k=0}^{\infty} \frac{\lambda^k}{k!} = e^{-\lambda}(e^{\lambda}) = 1$

We obtain the mean value of $X$$

> $E[X] = \sum_{k=0}^{\infty} k \frac{\lambda^k e^{-\lambda}}{k!} = 0 + \sum_{k=1}^{\infty} \frac{\lambda^k e^{-\lambda}}{(k-1)!} = \lambda e^{-\lambda}$

If we let $n=k-1$, we get

> $E[X] = \lambda e^{-\lambda} \sum_{n=0}^{\infty} \frac{\lambda^n}{n!} = \lambda e^{-\lambda}(e^{\lambda}) = \lambda$
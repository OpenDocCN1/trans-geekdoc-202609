# 4.4.4 Historical and implied volatility

Obtaining the best estimate of the volatility parameter, $\sigma$, in the Black-Scholes formula is of crucial importance. There are many different approaches to volatility estimation. These include:

+   - Historical estimation
- Implied volatility

We will now consider both historical and implied volatility estimation.

Historical volatility

In this method we calculate the volatility using $n+1$ historical asset prices, $S_i, i = 0, \dots, n$, and we assume that the asset prices are observed at the regular time interval, $dr$. Since the asset prices are assumed to follow GBM volatility is computed by the standard deviation of the $n$ continuously compounded returns, $u_i; i = 1, \dots, n$, where

```
$S_i = S_{i-1} \exp(u_i)$
```

or

```
$u_i = \log\left(\frac{S_i}{S_{i-1}}\right)$
```

We already know from (Eq. 2.10) that the expected standard deviation of the asset returns over the time interval is $\sigma\sqrt{dr}$. This means that we obtain the following expression for $\hat{\sigma}$, the estimated volatility:

```
$$\hat{\sigma}\sqrt{dr} = \sqrt{\frac{1}{n-1}\sum_{i=1}^n(u_i - \bar{u})^2}$  (4.4.68)
```

or

```
$$\hat{\sigma} = \sqrt{\frac{1}{(n-1)dr}\sum_{i=1}^n(u_i - \bar{u})^2}$  (4.4.69)
```

It is accepted practice to express all times in years, and so that the volatility is the annualized standard deviation of the returns. There is also the issue of how to account for non-trading days such as weekends and holidays. For example, let us suppose that the history of assets prices $S_i, i = 0, \dots, n$, was obtained by recording the price on each *trading day*. One approach is to use $dr = 1/N_{td}$, where $N_{td}$ is the number of trading days in a year. If we take $N_{td} = 250$ then Eq. (4.4.69) becomes

```
$$\hat{\sigma} = \sqrt{\frac{250}{n-1}\sum_{i=1}^n(u_i - \bar{u})^2}$  (4.4.70)
```
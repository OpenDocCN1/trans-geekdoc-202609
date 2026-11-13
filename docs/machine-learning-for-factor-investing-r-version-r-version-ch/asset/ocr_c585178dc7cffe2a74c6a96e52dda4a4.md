# 12.3.2 Pure performance and risk indicators

We then turn to the definition of the usual metrics used both by practitioners and academics alike. Henceforth, we write $r^P = (r_t^P)_{1 \le t \le T}$ and $r^B = (r_t^B)_{1 \le t \le T}$ for the returns of the portfolio and those of the benchmark, respectively. When referring to some generic returns, we simply write $r_t$. There are many ways to analyze them and most of them rely on their distribution.

The simplest indicator is the average return:

```
$\bar{r}_P = \mu_P = \mathbb{E}[r^P] \approx \frac{1}{T} \sum_{t=1}^T r_t^P, \quad \bar{r}_B = \mu_B = \mathbb{E}[r^B] \approx \frac{1}{T} \sum_{t=1}^T r_t^B,$
```

where, obviously, the portfolio is noteworthy if $\mathbb{E}[r^P] > \mathbb{E}[r^B]$. Note that we use the arithmetic average above but the geometric one is also an option, in which case:

```
$\tilde{\mu}_P \approx \prod_{t=1}^T (1 + r_t^P)^{1/T} - 1, \quad \tilde{\mu}_B \approx \prod_{t=1}^T (1 + r_t^B)^{1/T} - 1.$
```

The benefit of this second definition is that it takes the compounding of returns into account and hence compensates for volatility pumping. To see this, consider a very simple two-period model with returns $-r$ and $+r$. The arithmetic average is zero, but the geometric one $\sqrt{1-r^2} - 1$ is negative.

Akin to accuracy, it ratios evaluate the proportion of times when the position is in the right direction (long when the realized return is positive and short when it is negative). Hence hit ratios evaluate the propensity to make *good guesses*. This can be computed at the asset level (the proportion of positions in the correct direction$^2$) or at the portfolio level. In all cases, the computation can be performed on raw returns or on relative returns (e.g., compared to a benchmark). A meaningful hit ratio is the proportion of times that a strategy beats its benchmark. This is of course not sufficient, as many small gains can be offset by a few large losses.

Lastly, one important precision. In all examples of supervised learning tools in the book, we compared the hit ratios to 0.5. This is in fact wrong because if an investor is bullish, he or she may always bet on upward moves. In this case, the hit ratio is the percentage of time that returns are positive. Over the long run, this probability is above 0.5. In our sample, it is equal to 0.556, which is well above 0.5. This could be viewed as a benchmark to be surpassed.

Pure performance measures are almost always accompanied by **risk measures**. The second moment of returns is usually used to quantify the magnitude of fluctuations of the portfolio. A large variance implies sizable movements in returns, and hence in portfolio values. This is why the standard deviation of returns is called the **volatility** of the portfolio.

```
$\sigma_P^2 = \mathbb{V}[r^P] \approx \frac{1}{T-1} \sum_{t=1}^T (r_t^P - \mu_P)^2, \quad \sigma_B^2 = \mathbb{V}[r^B] \approx \frac{1}{T-1} \sum_{t=1}^T (r_t^B - \mu_B)^2.$
```

In this case, the portfolio can be preferred if it is less risky compared to the benchmark, i.e., when $\sigma_P^2 < \sigma_B^2$ and when average returns are equal (or comparable).

$^2$A long position in an asset with positive return or a short position in an asset with negative return.
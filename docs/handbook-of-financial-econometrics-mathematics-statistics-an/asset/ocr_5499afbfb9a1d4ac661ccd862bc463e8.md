true investment horizon (m = 1). Hence, an “improper” observation horizon will have a significant impact on the degree of association between the estimated Sharpe’s measure and the estimated risk measure.¹⁸

The impact of an improper observation horizon can be investigated first by finding the first derivative of the covariance defined as in (16) with respect to the holding period m. Thus,

```
$$\frac{d(\text{Cov})}{dm} = d[(1+R_f)^m \ln(1+R_f) - (1+\mu)^m \ln(1+\mu)]. \tag{69.20}$$
```

Then if $R_f$ is greater than $\mu$,

```
$$\frac{d(\text{Cov})}{dm} > d[(1+R_f)^m \ln(1+R_f) - (1+\mu)^m \ln(1+R_f)],$$\n\n since $\ln(1+R_f) > \ln(1+\mu)$ for $R_f > \mu$\n\n$= d \cdot \ln(1+R_f) \cdot [(1+R_f)^m - (1+\mu)^m] > 0,\ (R_f > 0),$\n\n since the factors $d$, $\ln(1+R_f)$, and $[(1+R_f)^m - (1+\mu)^m]$ are all positive. \tag{69.21}$$
```

The above inequality implies that the covariance between the estimated Sharpe’s measure and the estimated risk measure for the m-period case is a strictly increasing function of the length of the observation horizon, m, if the risk-free rate $R_f$ is greater than the mean rate of return on the market portfolio $\mu$ for the one-period case. Similarly, if $R_f$ is less than $\mu$,

```
$$\frac{d(\text{Cov})}{dm} < d[(1+R_f)^m \ln(1+\mu) - (1+\mu)^m \ln(1+\mu)]$$\n$= d \ln(1+\mu) [(1+R_f)^m - (1+\mu)^m]$\n$< 0\ (\mu > R_f > 0). \tag{69.22}$$
```

Thus, the m-period covariance is a strictly decreasing function of the length of the observation horizon, m, if $R_f$ is less than $\mu$. The graphic representation of the relationship between the m-period covariance and the length of the observation horizon, m, is shown in Figure 69.2. The impact of an improper observation horizon on the m-period covariance is summarized as follows:

+   (i) **An observation horizon longer than the true investment horizon:** When the risk-free rate $R_f$ is greater than the mean rate of return on the market portfolio $\mu$, the m-period covariance becomes larger
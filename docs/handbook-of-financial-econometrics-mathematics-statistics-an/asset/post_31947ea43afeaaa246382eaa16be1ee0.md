
The above analysis has demonstrated statistically why both Friend and Blume (1970) and Klemkosky (1973) found that the estimated Sharpe’s performance measure and its risk proxy are significantly correlated. In addition, because the risk-free rate proxy — Treasury bill rates — and the market rates of return proxy — the rates of return associated with the New York Stock Exchange — are measured with error, the sign associated with the estimate of (R_f − μ) is hardly determined.⁹

Moreover, it should be noted that the t-statistic is generally used to test whether the estimated Sharpe’s measure is significantly related with its risk proxy. The assumption of using a t-statistic to perform this kind of test is that the estimated Sharpe measure is normally distributed. Unfortunately, the estimated Sharpe measure is not distributed normally; in general, it is distributed as a non-central t-distribution. Furthermore, the sample estimate of the standard Sharpe measure is not an unbiased estimate.¹⁰

The existence of correlation between the estimated Sharpe’s performance measure and the estimated risk measure will generally not affect the ranking of Sharpe’s composite performance measure. However, it will affect the absolute difference among Sharpe performance measures. These results can be demonstrated as follows. Let the rates of return of portfolio i be a subpopulation of the capital market having a normal distribution with mean μ* and variance σ_i*². Then following equation (69.9), the correlation coefficient, ρ_i*, between the estimated Sharpe’s performance measure of portfolio i and the estimated risk measure, S_i, can be written as

ρ_i* = d(R_f − μ_i*) / (σ_sp σ_s) = −d / √c × Z_i / (a + b Z_i²) for all i, (69.12)

where σ_sp² and σ_s² are defined as in (69.10) and (69.11), respectively, with μ and σ being replaced by μ_i* and σ_i*, respectively:

σ_sp = a + b Z_i², σ_s² = σ_i*² c, c > 0,
a = Γ((n − 3)/2) / [2Γ((n − 1)/2)], b = n/2 {2a − [Γ((n − 2)/2) / Γ((n − 1)/2)]²},
c = 1/n { (n − 1) − 2 [Γ(n/2) / Γ((n − 1)/2)]² },

![](img/31ee7e6fa5107b22bbf7960ec96106a1_2552_0.png)

Figure 69.1: Relationship between the degree of correlation and Sharpe performance measure.

and

Z_i = (μ_i* - R_f)/σ_i* = Sharpe’s composite performance measure of portfolio i.

Equation (69.12) indicates that ρ_i* and Z_i are nonlinearly related. The nonlinear relation between ρ_i* and Z_i, can be depicted in Figure 69.1.¹¹

Figure 69.1 can be used to investigate the relationship between the degree of the correlation, ρ_i*, and the ranking of Sharpe’s composite performance measure. By studying Figure 69.1, the following conclusions can be drawn (without loss of generality, only portfolios with positive Z_i are considered since Sharpe’s composite performance measure is mainly applied to efficient portfolios).

Figure 69.1 indicates that Sharpe’s performance measures locate along the horizontal axis, as indicated by Z_i, Z_j, Z_l, etc., if there exists no correlation between the estimated Sharpe’s performance measure and the risk proxy. It also implies that Sharpe’s performance measures locate along the nonlinear curve, as indicated by Z_i*, Z_j*, Z_l* etc., if there exist some relationships between the estimated Sharpe’s performance measure and the risk measure. In other words, if Sharpe’s performance measure is not affected by the correlation, ρ_i*, then Z_i*, Z_j*, and Z_l* must be equal to the corresponding Z_i, Z_j, and Z_l, respectively. However, Z_i(= (μ_i* - R_f)/σ_i*, subscript i may be replaced by j or l) is not equivalent to Z_i*. Z_i* is the ex ante Sharpe’s performance measure of portfolio i whose sample estimate, (R̄_i − R_f) / S_i, is correlated with the estimated risk measure. In other words, Z_i^* represents the ex ante performance measure that is directly estimated by (R̄_i − R_f) / S_i. This is because Z_i^* is the expected value of (R̄_i − R_f) / S_i

```
Z_i^* = E\left(\frac{\bar{R}_i - R_f}{S_i}\right) = Z_i \cdot e(n),^{12}
```

where e(n) = [Γ((n − 1)/2)/Γ(n/2)]·[n/√2(n − 1)]. Thus, Z_i^* ≠ Z_i.

Specifically, the expected value (Z_i^*) of the estimated Sharpe's measure is equal to the ex ante Sharpe's measure, Z_i, multiplied by an error factor, e(n), which depends on the sample size n. This result implies that the ranking of mutual funds (or portfolios) based on the biased estimates, (R̄_i − R_f) / S_i, is not an unbiased ranking of mutual fund performance if different sample sizes are used for different mutual funds. Miller and Gehr (1978) used different methods that led to a similar conclusion. The above result is attributable to the fact that the error factor e(n) is not the same constant across all mutual funds (or portfolios) under evaluation. With the use of the same sample size, the ranking of mutual funds (or portfolios) based on the sample estimate, (R̄_i − R_f) / S_i, of the ex ante Sharpe's measure provides an unbiased ranking of the performance of mutual funds (or portfolios). This implies that Elton, Gruber and Padberg's (1976) simple rule of portfolio construction is generally not affected by substituting the sample estimate of Sharpe's measure for the population representation of Sharpe's measure. However, using the same sample size across all mutual funds (or portfolios) cannot eliminate the absolute difference between estimated Sharpe performance measures. In other words, the absolute difference between alternative performance measures is not independent of the degree of relationship between the estimated Sharpe measure and its risk proxy. Jensen (1969) pointed out that the performance measure can be used either to rank the performance of mutual funds (or portfolios) or to measure the absolute difference between the investment performance of two mutual funds (or portfolios). Consequently, the possible bias caused by the sample correlation between the estimated Sharpe's performance measure and the estimated risk proxy cannot entirely be neglected in empirical finance research.

The behavior of the sample correlation between the estimated Sharpe's composite performance measure and the estimated risk measure and the impact of the investment horizon on the sample correlation are examined in the following section.

12 The detailed derivation of E[(R̄_i − R_f) / S_i] can be found in Chen and Lee (1979) Appendix (D).

## 69.3 Impact of the Investment Horizon on Testing the Bias of the Estimated Sharpe’s Measure

The observation horizon used in the empirical study of portfolio management is generally not necessarily identical to the true horizon.13 Levy (1972) found that the portfolio with the smallest variance (or mean) will have the highest performance index when the observation investment horizon is longer than the true investment horizon. The portfolio with the highest risk (and hence the highest mean) tends to have the highest performance index if the observation investment horizon is shorter than the true investment horizon. This result implies that the covariance and correlation coefficient between the estimated performance index and its risk measure may well be affected if the observation investment horizon used in empirical research does not coincide with the true investment horizon. The impact of the investment horizon on the degree of association between the estimated Sharpe’s measure and its risk proxy is examined next. Under the assumption of stationary returns over time and all investors having the same investment horizon, one has

μ_j = μ   and   σ_j^2 = σ^2, 14   (69.13)

for all j = 1, 2, …, m, where μ_j and σ_j^2 are the expected rate of return and the return variance associated with j-period observations. In addition, following Tobin (1965), distribution stationary over time and return independence are assumed. It can be shown that

Ē = (1 + μ)^m − 1,   (69.14)

and

σ̃^2 = [σ^2 + (1 + μ)^2]^m − (1 + μ)^{2m},   m > 0,   (69.15)

where for the m-period case, Ē and σ̃^2 are the expected rate of return and the return variance of the market portfolio, respectively. In general, the observation investment horizon is arbitrarily assumed to be equal to one period, one day, one week, one month, one quarter, or one year. If the observation horizon used in empirical research does not coincide with the true investment

13 The observation horizon refers to either one day, one week, one month, one quarter or one year. The concept of the “true” investment horizon implies that investors will all share the same horizon. The justification and implication of this assumption can be found in either Lee (1976) or Levy (1972). Merton (1979) has argued that there exist three kinds of true horizons, i.e., trading horizon, decision horizon and planning horizon. The true horizon discussed in this paper is the decision horizon. 14 μ and σ^2 have the same definitions as in section 2.

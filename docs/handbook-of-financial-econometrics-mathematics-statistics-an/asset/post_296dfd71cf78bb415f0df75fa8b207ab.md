
When the observation period extends to 10 years with T = 120, the relative performance of six estimators is qualitatively similar to the case T = 60, except that both the bias and the RMSE are uniformly smaller. In terms of RMSE, the mixed estimator ranks the best. We notice that the bias of pure Bayes estimator is larger than that of the less biased estimator and mixed estimator.

In the last two cases where we have 20 and 50 years’ data, \hat{S}^2_{less_biased}, \hat{S}^2_{less_biased+} and \hat{S}^2_{mixed} are nearly unbiased. \hat{S}^2_{Bayes} is now seriously biased. A possible reason may be that the uniform prior distribution for \psi^2 contains little information. While the other estimators can approximate true value quite well with long sample period, the prior information on the contrary misleads the Bayes estimator. The conclusion is that the mixed estimator ranks the best. The mixed estimator has comparable bias and RMSE with the less-biased estimator in any case and it is always positive. Finally, even if we have 50 years of data (T = 600), the raw estimator is still biased upward by more than 60% and its RMSE is twice as much as that of the others. Therefore, it is not effective to eliminate the bias in \hat{S}^2 by extending the sample period, not to mention that data are limited for markets outside the US.

To conclude this section, we report the estimates from different MSR estimators for the whole sample period of the US market (July 1926 to December 2017) in Table 74.5. Consistent with the simulation results in Table 74.4, \hat{S}^2 still has a significant upward bias compared with \hat{S}^2_{less_biased}. \hat{S}^2_{Bayes} has a large downward bias and the mixed estimator \hat{S}^2_{mixed} is very close to unbiased estimates. The estimate from adjusted efficient frontier, \hat{S}^2_{adj}, is still larger than \hat{S}^2_{less_biased} even when a long sample period is used.

### Table 74.5: Estimates of maximum squared Sharpe ratio for the US markets by six estimators.

| Return | \hat{S}^2 | \hat{S}^2_{less_biased} | \hat{S}^2_{less_biased+} | \hat{S}^2_{Bayes} | \hat{S}^2_{mixed} | \hat{S}^2_{adj} |
|---|---|---|---|---|---|---|
| Value-weighted | 0.095293 | 0.070181 | 0.070181 | 0.027144 | 0.070181 | 0.076242 |
| Equal-weighted | 0.123009 | 0.097215 | 0.097215 | 0.067055 | 0.097215 | 0.103090 |

Notes: This table reports the estimates of MSR for the US markets by different proposed estimators. The data are from 25 size and book-to-market portfolio returns from July 1926 to December 2017 from the US market. Results using both value-weighted and equal-weighted portfolios are presented.

## 74.5 Comparing Maximum Squared Sharpe Ratio on the US, Japanese, Asian, European and Global Markets

As an application, we use our estimators to compare MSRs on the US, Japanese, Asian (excluding Japan), European and Global markets by updating different estimates using a five-year moving window. The sample period is from July 1990 to December 2017. We plot the time-series estimates for $\hat{S}^2_{less\_biased+}$, $\hat{S}^2_{Bayes}$ and $\hat{S}^2_{mixed}$ in Figure 74.1. We have noticed that $\hat{S}^2_{less\_biased+}$ hits zero during several periods and this makes trend analysis of MSR very difficult, especially on Japanese market, while there is no such problem with $\hat{S}^2_{Bayes}$ or $\hat{S}^2_{mixed}$. We then focus our discussion on the pattern

### Panel A. Maximum squared Sharpe ratio for $\hat{S}^2_{less\_biased+}$.

![](img/31ee7e6fa5107b22bbf7960ec96106a1_2666_0.png)

![](img/31ee7e6fa5107b22bbf7960ec96106a1_2666_1.png)

Figure 74.1: (Continued)

### Panel B. Maximum squared Sharpe ratio for $\hat{S}^2_{Bayes}$

MSR (Bayes)

![](img/31ee7e6fa5107b22bbf7960ec96106a1_2667_0.png)

MSR (Bayes)

![](img/31ee7e6fa5107b22bbf7960ec96106a1_2667_1.png)

Figure 74.1: (Continued)

of $\hat{S}_{mixed}^2$ in Panel C. Japan has a very low MSR over the entire period regardless of estimation methods while the MSR for European market was above 1.0 during the mid-2000s. The time-series co-movement of MSR across markets has been weak before the 2008 financial crisis. All markets suffer a drop in MSR at the peak of the US credit crisis but did not show much co-movement until 2012. Even though the S&P 500 index has risen from around 1200 points in January 2012 to over 2500 points in December 2017 and other markets have also experienced significant gains, the large and positive returns do not contribute to higher MSR. In contrast, all MSR across markets show significant drops since 2012. Intuitively, the MSR is related to

### Panel C. Maximum squared Sharpe ratio for $\hat{S}^2_{Mixed}$.

![](img/31ee7e6fa5107b22bbf7960ec96106a1_2668_0.png)

![](img/31ee7e6fa5107b22bbf7960ec96106a1_2668_1.png)

Figure 74.1: Maximum squared Sharpe ratio in international markets. Notes: This figure plots the estimates for MSR for the US, Global, Asia (excluding Japan), Japan and Europe regions from June 1995 to December 2017. The estimates are based on three estimators over rolling 5-year windows: $\hat{S}^2_{less\_biased+}$, $\hat{S}^2_{Bayes}$, and $\hat{S}^2_{mixed}$. Panel A plots the results for $\hat{S}^2_{less\_biased+}$ (MSR(Less_Biased+)). Panel B plots the results for $\hat{S}^2_{Bayes}$ (MSR(Bayes)). Panel C plots the results for $\hat{S}^2_{mixed}$ (MSR(Mixed)).

how far the efficient frontier extends to the upper-left quadrant of the mean-variance plane. Higher returns combined with a lower MSR can only imply either the testing portfolios become more volatile or these portfolios become more correlated, leading to a shrinkage of the area spanned by the efficient frontier. Ait-Sahalia and Xiu (2016) find that both the quadratic variations and correlations among asset classes have increased after the 2008 financial crisis. Their evidence supports our conjecture of the reasons for the shrinkage

of the efficient frontier. Nevertheless, we leave it for further research on the relative contribution of volatility and correlations to the recent drop in MSR.

A caveat on this section is as follows. We are aware of the findings of Merton (1980) that it is problematic to estimate expected returns (which is a component of MSR) using a relatively short sample period. However, the concern does not render our investigation futile. Our investigation on the international markets are exploratory in nature and aims to provide insights to researchers working on global markets with relatively short history of data. For example, researchers testing a global version of asset pricing models involving MSR may find it useful to consider the potential bias and alternative estimators suggested in this chapter.

## 74.6 Conclusion

The MSR related to a set of test assets has important implications on the theoretical asset pricing literature and yet its statistical properties have not been explored. We find that the common plug-in approach of sample estimates has a significant upward bias even when we have a very long history of data.

In this chapter, we examine a number of adjustments to the squared MSR estimator to reduce its bias and RMSE. In particular, we find that the usual way to obtain UMVUE of the squared slope of the asymptote to the minimum variance frontier ψ² by subtracting the constant bias will result in many instances of inadmissible negative estimates for ψ² and squared MSR. To pre-empt negative estimates, we propose an estimator based on Bayes estimation of ψ² and a mixed estimator as combination of UMVUE and Bayes estimation. We also apply the estimators to the US, Japan, European, Asian (except Japan) and Global markets and find that the MSRs have increased co-movements across markets in recent years.

## Acknowledgments

We would like to express our sincere thanks to Raymond Kan for comments. All errors are our responsibility.

## Bibliography

Y. Ait-Sahalia and D. Xiu (2016). Increased Correlation Among Asset Classes: Are Volatility or Jumps to Blame, or Both? Journal of Econometrics, 194, 205–219.
G. Chamberlain and M. Rothschild (1983). Arbitrage, Factor Structure and Mean-Variance Analysis on Large Asset Markets. Econometrica, 51, 1281–1304.


Figure 38.2: Scatter plots between pair-wise Chinese bank risks.

![](img/31ee7e6fa5107b22bbf7960ec96106a1_1587_0.png)

Figure 38.3: Expectation of one risk given the other risk.

![](img/31ee7e6fa5107b22bbf7960ec96106a1_1587_1.png)

u_credit risk, u_market risk and u_operational risk denote the values of marginal cumulative distribution functions of credit risk, market risk and operational risk. E(u_credit risk), E(u_market risk) and E(u_operational risk) denote the mean values of u_credit risk, u_market risk and u_operational risk, respectively. In the first subfigure of Figure 38.3, the line goes up and down, without showing a clear trend. In the second subfigure, when credit risk is large, operational risk is also expected to be large, which implies significant strong dependence when credit risk and operational risk are at their large extremes. Similarly, the line in the third subfigure also indicates strong upper tail dependence between market risk and operational risk. By contrast, in the second subfigure and the third subfigure, when one risk approaches the small extreme, the other risk is not expected to also be small, so there are not obvious lower tail dependencies for these two pairs of risks. Figure 38.3 shows the existence of tail dependence and tail asymmetry. To sum up, Figure 38.2 together with Figure 38.3 demonstrate that the dependencies between Chinese bank risks indeed have the features of nonlinearity, structure asymmetry, tail dependence and tail asymmetry.

## 38.4.2 Empirical results

The summary statistics of credit, market risk and operational risk are shown in Table 38.4. Note that losses are expressed as positive values while earnings are expressed as negative values in this empirical study. The skewness and kurtosis of normal distribution are 0 and 3, respectively. As shown in Table 38.4, all these three risk types are far from normal distribution, in particular credit risk. The skewness and kurtosis of credit risk are 6.02 and 58.85, respectively, indicating the distribution of credit risk is characterized by leptokurtosis and has a fat right tail. The distribution of operational risk is also leptokurtic and right-skewed with skewness 2.67 and kurtosis 10.20. The skewness of market risk is very close to 0, indicating its distribution has a symmetric shape, but it is also leptokurtic with kurtosis 11.56.

Table 38.4: Summary statistics of credit, market and operational risks.

| Risk types | Min. | Max. | Mean | Median | SD | Skewness | Kurtosis |
|---|---|---|---|---|---|---|---|
| Credit risk | 7.22e-4 | 2.14e-1 | 2.59e-2 | 2.30e-2 | 1.78e-2 | 6.02 | 58.85 |
| Market risk | -5.71e-2 | 5.05e-2 | -5.71e-3 | -4.34e-3 | 1.02e-3 | -0.92 | 11.56 |
| Operational risk | 1.50e-5 | 4.54e-3 | 6.21e-4 | 3.87e-4 | 6.33e-5 | 2.67 | 10.20 |

Note: SD is the standard deviation.

The first step of mixture copula-based risk integration is to find proper fits for credit, market and operational risk distributions. Table 38.4 shows all the three risk types are leptokurtic and heavy-tailed. Therefore, some widely used leptokurtosis and fat tail distributions are used to fit the three risk distributions, and the Kolmogorov–Smirnov test (KS test), one of the most widely used goodness-of-fit tests, is employed to determine which distributions fit these three risk types best. The fitting distributions include normal distribution, lognormal distribution, exponential distribution, Pareto distribution, gamma distribution, Weibull distribution, generalized hyperbolic distribution (GHD), generalized error distribution (GED), skewed generalized error distribution (SGED) and generalized Pareto distribution (GPD). Note that GHD, GED and SGED are used to fit the natural logarithm of risk data and the rest are directly employed to fit risk data.

The KS test results reveal that among all these widely used distributions, SGED fits the credit risk best, t distribution fits the market risk best, and lognormal distribution fits the operational risk best. The three distributions, their estimated parameters and the results of the KS test are shown in Table 38.5. The results of the other distributions are not listed because of space considerations.

Table 38.5: Best fitting distributions for credit, market and operational risks.

| Risk type | Distribution | Estimated parameters | D value | P value |
|---|---|---|---|---|
| Credit risk | SGED | σ = 0.57, μ = −6.11, k = 0.96, λ = 0.90 | 0.04 | 0.83 |
| Market risk | t | ν = 2 | 0.04 | 0.83 |
| Operational risk | Lognormal | μ̃ = −10.08, σ̃ = 0.90 | 0.05 | 0.62 |

Note: See Appendix 38B for specific mathematical expressions and parameter definitions of the three distributions. All parameters are estimated by maximum likelihood estimation.

For the KS test, the larger the P value is, the better the theoretical distribution is able to fit the empirical data, and 0.05 is generally set as the threshold. Table 38.5 shows that P values of SGED, t distribution and lognormal distribution are 0.83, 0.83 and 0.62, respectively. All of them are much larger than 0.05, indicating that these distributions fit the three risk types very well. Figure 38.4 presents the histograms of credit risk, market risk and operational risk and their best fitting distributions in Table 38.5. In Figure 38.4, the shapes of the fitting distributions are very similar to the corresponding histograms, which further demonstrates that SGED, the t distribution and the lognormal distribution indeed fit the three risk types very well.

Histogram of Credit risk

Skewed Generalized Error Distribution

![](img/31ee7e6fa5107b22bbf7960ec96106a1_1590_0.png)

![](img/31ee7e6fa5107b22bbf7960ec96106a1_1590_1.png)

Histogram of Market risk

t distribution

![](img/31ee7e6fa5107b22bbf7960ec96106a1_1590_2.png)

![](img/31ee7e6fa5107b22bbf7960ec96106a1_1590_3.png)

Histogram of Operational risk

Lognormal distribution

![](img/31ee7e6fa5107b22bbf7960ec96106a1_1590_4.png)

![](img/31ee7e6fa5107b22bbf7960ec96106a1_1590_5.png)

Figure 38.4: Histograms of credit risk, market risk and operational risk and their corresponding fitting distributions.

The second step is using the proper mixture copula to model the dependence between credit, market and operational risks. The analysis in Section 38.3 infers that the mixture of the t copula and Gumbel copula can best capture the dependence between bank risks, so the t-Gumbel copula is used to model the dependence between the three risk types of Chinese banks. The estimation results are shown in Table 38.6. The estimated parameters include weight parameters of the two copula components and their respective association parameters. In contrast with the results of several studies, such as Hu (2006), weights of the t copula and Gumbel copula are 0.42 and 0.58, respectively, which are relatively balanced; their association parameters are not close to those implying independence. This indicates that both copulas play an important role in modeling the dependence structure and none of them can be eliminated.

After the marginal distributions of the three risk types are determined and the mixture copula is estimated, the total risk distribution can be derived by Monte Carlo simulation with Steps 3-6 (Section 38.3.3). Finally, VaR of the total risk can be calculated by using Step 7. For an overall comparison, VaRs at confidence levels 90%, 95%, 99%, 99.9% and 99.97% are calculated, so according to equation 38.5, the number of Monte Carlo simulations is set at 10,000,000. Note that bank risk is usually measured with VaR with a time horizon of one year, but the data used in this empirical study are of semi-yearly frequency. Therefore, we need to scale the semi-annual VaRs into annual VaRs.

A simple but widely used way of scaling is to multiply the semi-annual VaR by the square root of 2 (a year includes 2 semi-years) (Hull, 2012). However, this simple scaling way is true only when the losses in both halves of the year follow the independent identical normal distribution with mean zero. In other cases, it is an approximation. In this work, to attain accurate annual VaR, Steps 3–5 are conducted twice in each Monte Carlo simulation to generate two simulated half-year losses. Then, the two losses are summed up

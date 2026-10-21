# 38.4.2 Empirical results

The summary statistics of credit, market risk and operational risk are shown in Table 38.4. Note that losses are expressed as positive values while earnings are expressed as negative values in this empirical study. The skewness and kurtosis of normal distribution are 0 and 3, respectively. As shown in Table 38.4, all these three risk types are far from normal distribution, in particular credit risk. The skewness and kurtosis of credit risk are 6.02 and 58.85, respectively, indicating the distribution of credit risk is characterized by leptokurtosis and has a fat right tail. The distribution of operational risk is also leptokurtic and right-skewed with skewness 2.67 and kurtosis 10.20. The skewness of market risk is very close to 0, indicating its distribution has a symmetric shape, but it is also leptokurtic with kurtosis 11.56.

The first step of mixture copula-based risk integration is to find proper fits for credit, market and operational risk distributions. Table 38.4 shows all the three risk types are leptokurtic and heavy-tailed. Therefore, some widely used leptokurtosis and fat tail distributions are used to fit the three risk distributions, and the Kolmogorov–Smirnov test (KS test), one of the most widely used goodness-of-fit tests, is employed to determine which distributions fit these three risk types best. The fitting distributions include normal distribution, lognormal distribution, exponential distribution, Pareto distribution, gamma distribution, Weibull distribution, generalized hyperbolic distribution (GHD), generalized error distribution (GED), skewed generalized error distribution (SGED) and generalized Pareto distribution (GPD). Note that GHD, GED and SGED are used to fit the natural logarithm of risk data and the rest are directly employed to fit risk data.

The KS test results reveal that among all these widely used distributions, SGED fits the credit risk best, t distribution fits the market risk best, and lognormal distribution fits the operational risk best. The three distributions, their estimated parameters and the results of the KS test are shown in Table 38.5. The results of the other distributions are not listed because of

Table 38.4: Summary statistics of credit, market and operational risks.

| Risk types | Min. | Max. | Mean | Median | SD | Skewness | Kurtosis |
|---|---|---|---|---|---|---|---|
| Credit risk | 7.22e-4 | 2.14e-1 | 2.59e-2 | 2.30e-2 | 1.78e-3 | 6.02 | 58.85 |
| Market risk | -5.71e-2 | 5.05e-2 | -5.71e-3 | -4.34e-3 | 1.02e-3 | -0.92 | 11.56 |
| Operational risk | 1.50e-5 | 4.54e-3 | 6.21e-4 | 3.87e-4 | 6.33e-5 | 2.67 | 10.20 |

Note: SD is the standard deviation.
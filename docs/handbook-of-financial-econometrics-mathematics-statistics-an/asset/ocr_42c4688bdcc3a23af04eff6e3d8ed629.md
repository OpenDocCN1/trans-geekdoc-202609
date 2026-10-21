# # Bayesian Portfolio Mean-Variance Efficiency Test

where \(\bar{R}\) and \(S_R\) are the sample mean and standard deviation of portfolio \(p\)'s excess returns \(R_1, \dots, R_T\). With the ex post Sharpe ratio, the F-test statistic is

\[ V_u = \frac{T(T - N - 1)}{N(T - 2)} \frac{\hat{\alpha}\hat{\Sigma}^{-1}\hat{\alpha}}{(1 + \hat{S}_R^2)}, \quad (93.2) \]

where \(\hat{\alpha} = (\hat{\alpha}_1, \dots, \hat{\alpha}_N)\) and \(\hat{\Sigma}\) are the maximum likelihood estimators of the intercepts \(\alpha = (\alpha_1, \dots, \alpha_N)\) and the covariance matrix \(\Sigma\).

Under the multivariate normal system in (93.1), Gibbons, Ross and Shanken (1989) showed that the F-test statistics \(V_u\) of (93.2) has a non-central F distribution with \(N\) and \((T - N - 1)\) degrees of freedom, respectively. The non-centrality parameter of the non-central F distribution is

\[ \lambda = \frac{T(SR^{*2} - SR^2)}{(1 + \hat{S}_R^2)}, \quad (93.3) \]

where \(SR\) is the ex ante Sharpe ratio of the test portfolio \(p\), and \(SR^*\) is the ex ante maximum Sharpe ratio attainable by the \(N\) risky assets and the test portfolio \(p\). A brief derivation of the F-test statistics \(V_u\) is given in Appendix 93A.

Note that if \(\alpha = 0\), as the test portfolio \(p\) coincides with the tangent portfolio on the mean-variance efficient frontier, the ex ante Sharpe ratio \(SR=SR^*\), thus the non-centrality parameter \(\lambda = 0\). Conversely, as the ex ante Sharpe ratio \(SR<SR^*\), the non-centrality parameter \(\lambda\) is positive and the likelihood to reject the null hypothesis \(H_0: \alpha = 0\) increases as the non-centrality parameter \(\lambda\) increases due to the ex ante Sharpe ratio \(SR\) deviates further from the maximum Sharpe ratio \(SR^*\). Therefore, the multivariate F-test for the null hypothesis \(H_0: \alpha = 0\) versus the alternative hypothesis \(H_1: \alpha \neq 0\) is equivalent to \(H_0: \lambda = 0\) versus \(H_1: \lambda \neq 0\). Nevertheless, the non-centrality parameter \(\lambda\) in (93.3) depends on the ex post Sharpe ratio \(\hat{SR}\), which is subject to the measurement errors. In case the ex post Sharpe ratio \(\hat{SR}\) overestimates the ex ante Sharpe ratio \(SR\), the non-centrality parameter \(\lambda\) is underestimated and the power of the F-test declines. In another word, the power of the F-test depends on the measurement error associated with ex post Sharpe ratio \(\hat{SR}\). Instead of a conditional F-test in Gibbons, Ross and Shanken (1989), this study develops an unconditional test in the Bayesian framework, which is not subject to the measurement errors associated with the ex post Sharpe ratio \(\hat{SR}\). The development of the Bayesian test is given in the following section.
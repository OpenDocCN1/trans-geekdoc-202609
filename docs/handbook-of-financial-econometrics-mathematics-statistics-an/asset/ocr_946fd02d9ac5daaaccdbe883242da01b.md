# An Empirical Investigation of the Long Memory Effect on the Relation

(2011) testing method is based on information from the periodogram, the spectral density frequency and the local Whittle likelihood function given by (Künsch, 1987)

```
Q(G, d) = \frac{1}{m} \sum_{j=1}^{m} \left\{ \log G \theta_j^{-2d} + \frac{I(\theta_j)}{G \theta_j^{-2d}} \right\}
```

\hat{d} can be estimated by maximizing the above likelihood function. The test statistic is then defined as

```
W = \sup \left( \sum_{j=1}^{m} v_j^2 \right)^{-1/2} \left| \sum_{j=1}^{m} v_j \left( \frac{I(\theta_j)}{G(\hat{d}) \theta_j^{-2d}} - 1 \right) \right|
```

where v_j = \log \theta_j - m^{-1} \sum_{j=1}^m \log \theta_j, and G(\hat{d}) = m^{-1} \sum_{j=1}^m \log \theta_j^{2\hat{d}} I(\theta_j). As suggested by Qu (2011), we set the bandwidth to m = T^{0.7} and we set the trimming proportion to 0.02 and 0.05, respectively. Table 58A.1 summarizes the spurious long memory test results based on equation (58A.2). The local Whittle estimates for the long memory parameter \hat{d} range from 0.245 (China) to 0.459 (US). Except for Thailand and Malaysia, the test statistics fail to reject the null, suggesting that a stationary long memory is inherited in most of the Asian downside risk. However, the test statistics show that the true long memory hypothesis for Thailand and Malaysia is rejected because it entails a spurious long memory. This means that the downside risks of Thailand and Malaysia are essentially characterized by a short memory process; nevertheless, these series may be contaminated by level shifts or a smooth trend. Recalling the results in Table 58.2, we find that the estimates of \gamma_i for Thailand and Malaysia are positive and significant as the theory predicts. Since the evidence does not find significant

Table 58A.1: Tests for spurious long memory.

| Local Whittle estimate of d | Test statistic (trim = 0.02) | Test statistic (trim = 0.05) |
| --- | --- | --- |
| Korea | 0.439 | 0.642 |
| Hong Kong | 0.302 | 0.782 | 0.589 |
| Indonesia | 0.404 | 0.435 | 0.435 |
| Thailand | 0.322 | 1.620*** | 1.620*** |
| Singapore | 0.313 | 0.663 | 0.663 |
| Taiwan | 0.329 | 0.602 | 0.602 |
| Malaysia | 0.297 | 2.041*** | 2.041*** |
| US | 0.459 | 0.263 | 0.263 |
| China | 0.245 | 1.008 | 0.982 |
```
proc lifereg data=firms;
    model dury*status(0)=age ad rd debt / D=exponential;
run;
```

The parameter estimations for four of the five models are displayed below. The output by the generalized Gamma model was excluded because SAS gave a warning that its convergence and model fit are questionable.

|  | Exponential model |  | Weibull model |  | Log-Normal model |  | Log-Logistic model |  |
|---|---|---|---|---|---|---|---|---|
| Parameter | Estimate | P-value | Estimate | P-value | Estimate | P-value | Estimate | P-value |
| age | 0.0927 | <0.0001 | 0.0902 | <0.0001 | 0.0753 | <0.0001 | 0.0807 | <0.0001 |
| ad | 0.2348 | 0.3696 | 0.2201 | 0.3614 | 0.2363 | 0.3059 | 0.2303 | 0.2854 |
| rd | 0.0391 | 0.4857 | 0.0387 | 0.4607 | 0.0487 | 0.2784 | 0.0451 | 0.3400 |
| debt | −0.1070 | 0.8381 | −0.1024 | 0.8319 | −0.2364 | 0.6968 | −0.2748 | 0.6677 |

These four models yield similar inferences about the effect of the variables. For example, the variable age is statistically significantly different from zero across all models. We transform the parameter estimate of the variable age from the exponential model and get exp (0.0927) − 1 = 0.097. This means that after controlling for the other covariates, the expected duration time will increase by 9.7% for a one-year increase in the firm’s age at t = 0. It is consistent with earlier inference that established firms are able to remain listed for a longer period of time at the exchange than younger firms.

The other three covariates, ad, rd and debt, are not statistically significant in any of the four models. Positive signs of advertising expense and R&D expense indicate a firm can increase its survival time by investing in advertising and R&D. Similarly, the negative sign of debt means that a higher debt ratio is associated with a lower survival time.

We next conduct the hypothesis testing and goodness-of-fit testing for each model. There are three most commonly used test statistics, i.e., Wald statistics, the score statistics and the likelihood ratio statistics. Because these three test statistics are asymptotically equivalent, any one of them could be used in the analysis. In the example, we reject the null hypothesis that all coefficients are zero for all models using any of the test statistics (results were not tabulated for brevity).

The goodness-of-fit test can be conducted using the likelihood ratio statistics. Below are the negative twice log-likelihoods for four models:
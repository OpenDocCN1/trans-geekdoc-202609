
### Table 28.9: Pooled regression.

```
. regress return beta
```

| Source | SS | df | MS |
|---|---|---|---|
| Model | .000084304 | 1 | .000084304 |
| Residual | 24.2017921 | 8,844 | .002736521 |
| Total | 24.2018765 | 8,845 | .002736221 |

Number of obs = 8,846; F(1, 8844) = 0.03; Prob > F = 0.8607; R-squared = 0.0000; Adj R-squared = -0.0001; Root MSE = .05231

| return | Coef. | Std. Err. | t | P>\|t\| | [95% Conf. Interval] |
|---|---|---|---|---|---|
| beta | .0004806 | .0027382 | 0.18 | 0.861 | -.004887 | .0058482 |
| _cons | .0018154 | .0030781 | 0.59 | 0.555 | -.0042184 | .0078492 |

### Table 28.10: Ramsey RESET test of pooled regression model.

```
. ovtest

Ramsey RESET test using powers of the fitted values of return
Ho: model has no omitted variables
F(3, 8841) = 1.36
Prob > F = 0.2521
```

specification of the model ignores any unobserved heterogeneity in the sample.

To test the significance of the random effect in the RE model, we find that the LM statistic (=1.54) is significant at the 10.72% level in Table 28.12. Given this result, the random effect is of marginal significance.

The 0.05 critical value for F(1728, 7116)=1.064 (or use the probability printed with the F-test), so the null hypothesis that all fixed effects are jointly zero is rejected. The fixed effects are highly significant.

The DWH test result implies that the null hypothesis is rejected at the 0.011 level of significance, this implies that there is contemporaneous correlation between the random effect and an explanatory variable included in the model. So the RE parameter estimates are not consistent. Given this, the FE model is the appropriate specification since the RE model parameter estimates are likely inconsistent.

### Table 28.11: Random effects (RE) model.

```
. xtreg return beta

Random-effects GLS regression
Group variable: firm_ident

Number of obs = 8,846
Number of groups = 1,729

R-sq:
  within = 0.0012
  between = 0.0001
  overall = 0.0000

Obs per group:
  min = 1
  avg = 5.1
  max = 11

corr(u_i, X) = 0 (assumed)
```

Wald chi2(1) = 2.80; Prob > chi2 = 0.0944

| return | Coef. | Std. Err. | z | P>\|z\| | [95% Conf. Interval] |
|---|---|---|---|---|---|
| beta | -.0054027 | .0032305 | -1.67 | 0.094 | -.0117344 | .0009289 |
| _cons | .0063386 | .0036912 | 1.72 | 0.086 | -.000896 | .0135733 |

sigma_u = .02854326; sigma_e = .05077864; rho = .24010397 (fraction of variance due to u_i)

### Table 28.12: LM test of random effects.

```
. xttest0

Breusch and Pagan Lagrangian multiplier test for random effects

return[firm_ident,t] = Xb + u[firm_ident] + e[firm_ident,t]
```

Estimated results:

|  | Var | sd = sqrt(Var) |
|---|---|---|
| return | .0027362 | .0523089 |
| e | .0025785 | .0507786 |
| u | .0008147 | .0285433 |

Test: Var(u) = 0
chibar2(01) = 1.54
Prob > chibar2 = 0.1072

### Table 28.13: Fixed effects estimates.

```
. xtreg return beta, fe

Fixed-effects (within) regression
Group variable: firm_ident

R-sq:
  within = 0.0012
  between = 0.0001
  overall = 0.0000

corr(u_i, Xb) = -0.0971

Number of obs = 8,846
Number of groups = 1,729

Obs per group:
  min = 1
  avg = 5.1
  max = 11
```

F(1,7116) = 8.33; Prob > F = 0.0039

| return | Coef. | Std. Err. | t | P>\|t\| | [95% Conf. Interval] |
|---|---|---|---|---|---|
| beta | -.0118795 | .0041161 | -2.89 | 0.004 | -.0199484 | -.0038107 |
| _cons | .0154809 | .0045828 | 3.38 | 0.001 | .0064973 | .0244645 |

sigma_u = .04144764; sigma_e = .05077864; rho = .39985014 (fraction of variance due to u_i)

F test that all u_i=0: F(1728, 7116) = 1.31; Prob > F = 0.0000

```
. est sto FE
```

### Table 28.14: DWH test of RE versus FE.

```
. hausman FE RE
```

Coefficients

|  | (b) FE | (B) RE | (b-B) Difference | sqrt(diag(V_b-V_B)) S.E. |
|---|---|---|---|---|
| beta | -.0118795 | -.0054027 | -.0064768 | .0025508 |

b = consistent under Ho and Ha; obtained from xtreg
B = inconsistent under Ha, efficient under Ho; obtained from xtreg

Test: Ho: difference in coefficients not systematic

chi2(1) = (b-B)'[(V_b-V_B)^(-1)](b-B) = 6.45
Prob>chi2 = 0.0111

## 28.14 Summary and Conclusion

This chapter presents DWH specification tests and provides IV and panel data examples of their application. DWH tests compare alternative parameter estimates and can be useful in discerning endogeneity issues (omitted variables, measurement error/errors in variables, and simultaneity), incorrect functional form and contemporaneous correlation in the lagged dependent variable — serial correlation model, testing alternative estimators for a model, and testing alternative theoretical models. Empirical applications are provided illustrating the use of DWH tests in comparing LS, IV, FE, RE, and GMM estimators. There is much to gain and little to lose from using DWH tests in econometric analysis.

## Bibliography

- Ahn, S. C. and Low, S. (1996). A Reformulation of the Hausman Test for Regression Models with Pooled Cross-section-time-series Data. Journal of Econometrics, 71(1-2), 309-319.
- Amini, S., Delgado, M. S., Henderson, D. J. and Parmeter, C. F. (2012). Fixed vs random: the hausman test four decades later. In Badi H. Baltagi, et al., (eds.), Essays in Honor of Jerry Hausman. Emerald Publishing Limited.
- Arellano, M. (1993). On the Testing of Correlated Effects with Panel Data. Journal of Econometrics, 59, 87-97.
- Basmann, R. L. (1960). On Finite Sample Distributions of Generalized Classical Linear Identifiability Tests Statistics. Journal of the American Statistical Association, 55, 650-59.
- Brooks, C. (2014). Introductory Econometrics for Finance, 3rd ed. Cambridge University Press.
- Cameron, A. C. and Trivedi, P. K. (2005). Microeconometrics: Methods and Applications, Cambridge University Press.
- Chermak, J. M. and Patrick, R. H. (2001). A Microeconometric Test of the Theory of Exhaustible Resources. Journal of Environmental Economics and Management, 42(1), 82-103.
- Dastoor, D. K. (2005). On the Arbitrariness of Some Asymptotic Test Statistics Based on Generalized Inverses. Econometrics Journal, 8, 292-305.
- Davidson, R. and MacKinnon, J. G. (1987). Implicit Alternatives and the Local Power of Test Statistics. Econometrica, 55(6), 1305-1329.
- Davidson, R. and MacKinnon, J. G. (1984a). Model Specification Tests Based on Artificial Linear Regressions. International Economic Review, 25, 485-502.
- Davidson, R. and MacKinnon, J. G. (1984b). Convenient Specification Tests for Logit and Probit Models. Journal of Econometrics, 25, 241-262.
- Davidson, R. and MacKinnon, J. (1989). Testing for Consistency Using Artificial Regressions. Econometric Theory, 5(3), 363-384.
- Davidson, R. and Zinde-Walsh, V. (2017). Advances in Specification Testing. Canadian Journal of Economics, 50(5), 1595-1631.
- Dehon, C., Gassner, M. and Verardi, V. (2009). A Hausman-Type Test to Detect the Presence of Influential Outliers in Regression Analysis. Economics Letters, 105, 64-67.
- Durbin, J. (1954). Errors in Variables. Review of the International Statistical Institute, 22, 23-32.
- Fama, E. F. and MacBeth, J. D. (1973). Risk, Return and Equilibrium: Empirical Tests. Journal of Political Economy, 81(3), 607-636.
- Frondel, M. and Vance, C. (2010). Fixed, Random, or Something in Between? A Variant of Hausman's Specification Test for Panel Data Estimators. Economics Letters, 107, 327-329.
- Fuller, W. A. and Battese, G. E. (1973). Transformation for Estimation of Linear Models with Crossed-Error Structure. Journal of the American Statistical Association, 68, 626-632.
- Fuller, W. A. and Battese, G. E. (1974). Estimation of Linear Models with Crossed-Error Structure. Journal of Econometrics, 2, 67-78.
- Greene, W. H. (2018). Econometric Analysis, 8th ed. Prentice Hall: New Jersey.
- Hausman, J. A. (1978). Specification Tests in Econometrics. Econometrica, 46, 1251-1276.
- Hausman, J. A. and McFadden, D. L. (1984). Specification Tests for the Multinomial Logit Model. Econometrica, 52, 1219-1240.
- Hausman, J. A. and Taylor, W. E. (1981). A Generalized Specification Test. Economics Letters, 8, 239-245.
- Holly, A. (1982). A Remark on Hausman's Specification Test. Econometrica, 49, 749-759.
- Holly, A. (1987). Specification tests: an overview. In T.F. Bewley (ed.), Advances in Economics and Econometrics: Theory and Applications. Vol 1, pp. 59-97, Cambridge University Press.
- Hui-shyong, C. and Lee, C. F. (1977). Using Pooled Time-Series and Cross-Section Data to Test the Firm and Time Effects in Financial Analyses. Journal of Financial and Quantitative Analysis, 12(3), 457-471.
- Lee, C. F. (1973). Errors-In-Variables Estimation Procedures with Applications to a Capital Asset Pricing Model. Ph.D. dissertation (State University of New York at Buffalo).
- Lee, C. F., Gupta, M. C., Chen, H. Y. and Lee, A. C. (2011). Optimal Payout Ratio Under Uncertainty and the Flexibility Hypothesis: Theory and Empirical Evidence. Journal of Corporate Finance, 17, 483-501.
- Liviatan, N. (1963). Tests of the permanent income hypotheses based on a re-interview savings study. In C. Christ (ed.), Measurement in Economics. Stanford: Stanford University Press.
- MacKinnon, James G. (1992). Model Specification Tests and Artificial Regressions. Journal of Economic Literature, 30, 102-146.
- Nakamura, A. and Nakamura, M. (1981). On the Relationships Among Several Specification Error Tests Presented by Durbin, Wu, and Hausman. Econometrica, 49(6), 1583-1588.
- Newey, W. (1985). Generalized Method of Moments Specification Testing. Journal of Econometrics, 29, 229-256.
- Pace, R. K. and LeSage, J. P. (2008). A Spatial Hausman Test. Economics Letters, 101: 282-284.
- Pesaran, M. Hashem and Richard J. Smith (1990). A Unified Approach to Estimation and Orthogonality Tests in Linear Single-Equation Models. Journal of Econometrics, 44, 41-66.
- Ramsey, J. B. (1969). Tests for Specification Error in Classical Linear Squares Analysis. Journal of the Royal Statistical Society, Series B, 31, 350-371.
- Ramsey, J. B. (1974). Classical model selection through specification error tests. In P. Zarembka (ed.), Frontiers of Econometrics. New York: Academic Press.
- Ramsey, J. B. and Schmidt, P. (1976). Some Further Results on the Use of OLS and BLUS Residuals in Specification Error Tests. Journal of the American Statistical Association, 71, 389-390.
- Ruud, P. (1989). Tests of Specification in Econometrics. Econometric Reviews, 3, 211-242.

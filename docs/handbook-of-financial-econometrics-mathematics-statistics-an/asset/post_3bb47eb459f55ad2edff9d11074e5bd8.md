
## Table 108E.5: Simultaneous estimation of true alpha parameters in the two-distribution model for mutual funds.

| γ | Bad α_b | β_b | π_b | π_0 |
|---|---|---|---|---|
| 0.010 | -0.136 | 0.073 | 1.000 | 0.000 |
| 0.025 | -0.141 | 0.173 | 1.000 | 0.000 |
| 0.050 | -0.156 | 0.296 | 1.000 | 0.000 |
| 0.060 | -0.142 | 0.292 | 1.000 | 0.000 |
| 0.070 | -0.158 | 0.353 | 1.000 | 0.000 |
| 0.100 | -0.148 | 0.401 | 1.000 | 0.000 |
| 0.150 | -0.158 | 0.507 | 1.000 | 0.000 |
| 0.200 | -0.162 | 0.573 | 1.000 | 0.000 |
| 0.300 | -0.187 | 0.723 | 1.000 | 0.000 |
| 0.400 | -0.203 | 0.824 | 1.000 | 0.000 |

Notes: The true bad alpha parameters, α_b, are estimated for each test size γ, simultaneously with the fractions of managers in the population having zero or bad alphas. A grid search over the bad alpha parameters looks from the median alpha value in the data from Table 108.1, to the lower 5% tail values in the data, with a grid size of 0.001%. The best fitting bad alpha parameters are shown, where the fit is determined by minimizing the difference between the cross-section of fund alphas estimated in the actual data, versus the cross-section of alphas estimated from a mixture of return distributions, formed from the zero and bad alpha parameters and the estimated π fractions for each of the types. At each point in the grid, the π fractions are estimated using simulation as described in the text, with 100 simulation trials. π_b denotes the fraction of bad funds. All alpha parameters are stated in monthly percentage units. The power parameters of the test are denoted as β_b, the power to reject against the alternative of a bad fund.

In Table 108E.2, we also examine the robustness of the joint estimation results to the choice of the test size, 5% and 10%. As explained in the main text, the test size of 10% is our preferred test size, and the results from the 10% test size are reported in the main text. Here, we find that the results are similar in general when a test size of 5% is used.

Table 108E.3 repeats the analysis of Table 108.4 using the Fama and French (1996) three-factor model for hedge funds, and finds similar results to those reported in the main paper. The difference is that the reported standard errors, not the empirical standard errors from the simulations, are displayed here. This provides a feel for the biases in the reported standard errors and shows the increase in the reported standard errors as the test size increases.

Table 108E.4 presents results for joint estimation of the three-group model, with mutual fund results in Panel A and hedge fund results in Panel B. The joint estimation here uses 100 simulation trials, but in a few untabulated experiments we find that the results for 100 and 1000 trials usually differ only in the last decimal place. Panels C–E summarize robustness checks. Panel C reproduces results from the baseline case in the main text for comparison. Panel D presents results where the alpha parameters are associated with active management, measured by low R-squares in factor model regressions for the funds returns. Funds are ranked on their R-squares and when assigned to the three alpha groups, the low R-square funds go into the high-alpha group and the high R-square funds go into the low-alpha group.

Panel E of Table 108E.4 presents results where we account for estimation error in mutual funds’ alphas, as described in the main text. After we subtract the random alpha to account for estimation error, we rescale the adjusted simulated fund returns so that they still match the standard deviations of the actual fund returns in the data, and we add a constant to preserve the means of the transformed simulated fund returns. The transformation produces r* = wr + x, where r is the simulated return with the random alpha, w = [σ²(r)/(σ²(α) + σ²(r))]¹/², where σ²(r) is the variance of the fund returns before adjustment and σ²(α) is the variance of the estimated alpha, and x = E(r)(1 − w).

Table 108E.5 presents results from joint estimation of the two-group model for mutual funds, using a range of test sizes. The result that the fraction of mutual funds having the bad alpha is 100% in the two-group model is robust to the size of the test, and the estimate of the bad alpha varies between −0.136% per month and −0.203% per month as the size of the test is varied between 1% and 40%.

## Appendix 108F Simulations of the Simulations

Panels A–D of Table 108F.1 present simulation results that evaluate the standard errors when the population values of the π fractions are each set to 1/3. The simulated samples are of the same size as the samples in our actual data, and 1000 simulation trials are used. The results are similar to those in Table 108.2 of the main paper. Our point estimates are typically within one empirical standard deviation of the true values of the π fractions at the 5% test size, and are even closer to the true values than the example in the main text, at all sizes above 10%. The standard errors are the most accurate at the 10% test size, but understated, and the average reported standard errors get larger with the larger test sizes. Unlike the case in the main paper, there seems to be no benefit to using test sizes larger than 10%. The results show that the findings in the main paper are conservative, in the sense that the fractions of zero alpha funds are likely even smaller than our estimates indicate, and the fractions of good and bad hedge funds are likely even larger.

Panels E–H of Table 108F.1 present the results of experiments where we set the true π fractions equal to the banner values reported by

## Table 108F.1: Finite sample properties of the estimators.

|  | π_zero | π_good | π_bad |
|---|---|---|---|
| Panel A: γ/2 = 0.05 |  |  |  |
| Population values | 1/3 | 1/3 | 1/3 |
| Our Avg. Estimates | 0.548 | 0.197 | 0.255 |
| Classical FDR Avg. Estimates | 0.980 | 0.024 | -0.003 |
| Empirical SDs | 0.290 | 0.186 | 0.261 |
| Avg. Reported SDs | 0.054 | 0.357 | 0.330 |
| Root MSE | 0.361 | 0.231 | 0.272 |
| Classical Empirical SD | 0.029 | 0.027 | 0.015 |
| Classical Avg. Reported SD | 0.006 | 0.007 | 0.011 |
| Classical Root MSE | 0.647 | 0.311 | 0.337 |
| Panel B: γ/2 = 0.10 |  |  |  |
| Population values | 1/3 | 1/3 | 1/3 |
| Our Avg. Estimates | 0.417 | 0.286 | 0.298 |
| Classical FDR Avg. Estimates | 0.910 | 0.069 | -0.020 |
| Empirical SDs | 0.233 | 0.161 | 0.227 |
| Avg. Reported SDs | 0.241 | 0.354 | 0.295 |
| Root MSE | 0.247 | 0.168 | 0.230 |
| Classical Empirical SD | 0.048 | 0.047 | 0.036 |
| Classical Avg. Reported SD | 0.009 | 0.011 | 0.017 |
| Classical Root MSE | 0.599 | 0.270 | 0.315 |
| Panel C: γ/2 = 0.20 |  |  |  |
| Population values | 1/3 | 1/3 | 1/3 |
| Our Avg. Estimates | 0.380 | 0.298 | 0.322 |
| Classical FDR Avg. Estimates | 0.857 | 0.097 | 0.056 |
| Empirical SDs | 0.230 | 0.145 | 0.237 |
| Avg. Reported SDs | 0.528 | 0.406 | 0.360 |
| Root MSE | 0.235 | 0.149 | 0.237 |
| Classical Empirical SD | 0.061 | 0.063 | 0.060 |
| Classical Avg. Reported SD | 0.014 | 0.015 | 0.023 |
| Classical Root MSE | 0.527 | 0.244 | 0.293 |
| Panel D: γ/2 = 0.30 |  |  |  |
| Population values | 1/3 | 1/3 | 1/3 |
| Our Avg. Estimates | 0.368 | 0.308 | 0.324 |
| Classical FDR Avg. Estimates | 0.830 | 0.115 | 0.056 |
| Empirical SDs | 0.233 | 0.146 | 0.249 |
| Avg. Reported SDs | 0.772 | 0.461 | 0.488 |
| Root MSE | 0.235 | 0.148 | 0.249 |
| Classical Empirical SD | 0.069 | 0.073 | 0.072 |
| Classical Avg. Reported SD | 0.020 | 0.020 | 0.030 |
| Classical Root MSE | 0.500 | 0.231 | 0.287 |

## Table 108F.1: (Continued)

|  | π_zero | π_good | π_bad |
|---|---|---|---|
| Panel E: γ/2 = 0.05 |  |  |  |
| Population values | 0.750 | 0.010 | 0.240 |
| Our Avg. Estimates | 0.829 | 0.027 | 0.143 |
| Classical FDR Avg. Estimates | 1.010 | -0.010 | -0.003 |
| Empirical SDs | 0.285 | 0.085 | 0.253 |
| Avg. Reported SDs | 0.054 | 0.319 | 0.282 |
| Root MSE | 0.293 | 0.087 | 0.271 |
| Classical Empirical SD | 0.024 | 0.017 | 0.017 |
| Classical Avg. Reported SD | 0.005 | 0.006 | 0.009 |
| Classical Root MSE | 0.264 | 0.026 | 0.244 |
| Panel F: γ/2 = 0.10 |  |  |  |
| Population values | 0.750 | 0.010 | 0.240 |
| Our Avg. Estimates | 0.706 | 0.046 | 0.248 |
| Classical FDR Avg. Estimates | 0.988 | -0.008 | 0.020 |
| Empirical SDs | 0.301 | 0.097 | 0.274 |
| Avg. Reported SDs | 0.284 | 0.370 | 0.267 |
| Root MSE | 0.304 | 0.104 | 0.274 |
| Classical Empirical SD | 0.053 | 0.038 | 0.044 |
| Classical Avg. Reported SD | 0.008 | 0.010 | 0.015 |
| Classical Root MSE | 0.244 | 0.042 | 0.224 |
| Panel G: γ/2 = 0.20 |  |  |  |
| Population values | 0.750 | 0.010 | 0.240 |
| Our Avg. Estimates | 0.609 | 0.068 | 0.322 |
| Classical FDR Avg. Estimates | 0.959 | -0.007 | 0.048 |
| Empirical SDs | 0.314 | 0.118 | 0.294 |
| Avg. Reported SDs | 0.693 | 0.499 | 0.342 |
| Root MSE | 0.344 | 0.132 | 0.306 |
| Classical Empirical SD | 0.083 | 0.066 | 0.076 |
| Classical Avg. Reported SD | 0.014 | 0.015 | 0.022 |
| Classical Root MSE | 0.225 | 0.068 | 0.206 |
| Panel H: γ/2 = 0.30 |  |  |  |
| Population values | 0.750 | 0.010 | 0.240 |
| Our Avg. Estimates | 0.574 | 0.083 | 0.333 |
| Classical FDR Avg. Estimates | 0.946 | -0.006 | 0.061 |
| Empirical SDs | 0.311 | 0.124 | 0.301 |
| Avg. Reported SDs | 1.084 | 0.628 | 0.560 |
| Root MSE | 0.357 | 0.144 | 0.318 |
| Classical Empirical SD | 0.100 | 0.084 | 0.095 |
| Classical Avg. Reported SD | 0.021 | 0.021 | 0.030 |
| Classical Root MSE | 0.220 | 0.086 | 0.203 |

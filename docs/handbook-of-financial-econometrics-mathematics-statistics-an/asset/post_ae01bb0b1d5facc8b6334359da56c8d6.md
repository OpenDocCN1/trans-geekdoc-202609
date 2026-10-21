
## Table 22.4: Pearson correlation tables.

|  | ABSDACC | DACC | FEERATIO | RANKTOT | RANKNON | RANKAUD |
|---|---|---|---|---|---|---|
| ABSDACC | 0.080 | 0.066 | -0.141 | -0.081 | -0.187 |
| DACC | 0.133 | 0.090 | 0.027 | 0.048 | 0.001* |
| FEERATIO | 0.007* | -0.011* | 0.485 | 0.746 | 0.167 |
| RANKTOT | -0.188 | -0.005* | -0.002* | 0.875 | 0.915 |
| RANKNON | -0.132 | -0.012* | 0.546 | 0.652 | 0.655 |
| RANKAUD | -0.199 | -0.015* | -0.231 | 0.952 | 0.486 |
| CFO | -0.205 | -0.015* | 0.068 | 0.216 | 0.139 | 0.206 |
| ABSCFO | 0.260 | -0.029* | -0.100 | -0.247 | -0.187 | -0.219 |
| ACC | -0.092 | 0.143 | 0.016* | 0.119 | 0.076 | 0.105 |
| ABSACC | 0.205 | -0.008* | -0.028* | -0.119 | -0.075 | -0.112 |
| LEVERAGE | 0.082 | -0.130 | -0.009* | 0.104 | 0.048* | 0.102 |
| GROWTH | 0.169 | -0.009* | -0.056* | -0.191 | -0.106 | -0.178 |
| INST | -0.195 | 0.002* | -0.095 | 0.373 | 0.155 | 0.418 |
| ROA | -0.217 | 0.142 | 0.037* | 0.220 | 0.131 | 0.209 |

Correlation coefficients for pre-SOX period and (post-SOX period) above (below) the Diagonal

Note: *Denotes a significant level > 0.10. All other coefficients are significant at the 0.10 level or below.

Table 22.4 addresses the correlation tables for the independent and dependent variables for both the pre- and post-SOX periods. The results indicate that FEERATIO is highly positively correlated with RANKNON. ABSDACC is negatively correlated with RANKTOT, RANKAUD and RANKNON for the Pearson correlation in both periods. We also test the variance inflation factor (VIF), and the highest in the regressions is 4.27 in the pre-SOX period and 6.5 in post-SOX period, showing that there is no problem with multi-collinearity in these results.

## 22.5 Empirical Results

### 22.5.1 The results for pre- and post-SOX periods

If economic bonding is the primary factor that influences auditor independence, then auditors will not jeopardize their independence with regard to all of their clients, because not all of their clients have the same level of economic importance, and auditors are concerned about protecting their reputations. Moreover, auditor firms also have other incentives to protect their reputations and minimize their litigation risk, and so numerous factors are at play when they consider whether to compromise their independence or not.

In order to find out trade-off point between reputation protection and economic bonding, we apply the panel threshold regression model (Hansen, 1999) to investigate whether there was a structural change in the relation between auditors’ behavior and discretionary accruals. As mentioned in Section 22.3, we use FEERATIO as the threshold variable, and test if the threshold value is significant. The p-value is obtained by bootstrapping 300 times, and there is a structural change if it is significant. We thus find the structural changes in each period, and the threshold effects are summarized in Table 22.5. The test results for a single threshold is significant with a bootstrap p-value of 0.001, and the threshold value is reached when FEERATIO equals 0.67095.

On the other hand, we find that the test for a single threshold is significant (p-value = 0.013333) when FEERATIO is 0.197239, and the test for a double threshold is also strongly significant with a bootstrap p-value of 0.037 when FEERATIO is 0.298917 in the post-SOX period, as a result, we can conclude that there is strong evidence that there are two thresholds in the post-SOX period.

**Table 22.4: (Continued).**

|  | CFO | ABSCFO | ACC | ABSACC | LEVERAGE | GROWTH | INST | ROA |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| ABSDACC | −0.250 | 0.262 | −0.271 | 0.352 | −0.040 | 0.205 | −0.100 | −0.274 |
| DACC | 0.005* | −0.116 | 0.312 | −0.251 | −0.151 | 0.097 | 0.071 | 0.199 |
| FEERATIO | 0.090 | −0.074 | 0.019* | −0.029 | −0.045 | 0.064 | 0.246 | 0.098 |
| RANKTOT | 0.234 | −0.197 | 0.025* | −0.069 | 0.185 | −0.112 | 0.364 | 0.163 |
| RANKNON | 0.197 | −0.173 | 0.026* | −0.065 | 0.100 | −0.068 | 0.342 | 0.149 |
| RANKAUD | 0.226 | −0.189 | 0.028 | −0.077 | 0.224 | −0.149 | 0.322 | 0.149 |
| CFO |  | −0.591 | 0.086 | −0.182 | −0.076 | −0.238 | 0.249 | 0.647 |
| ABSCFO | −0.761 |  | −0.147 | 0.226 | 0.067 | 0.417 | −0.131 | −0.473 |
| ACC | 0.190 | −0.248 |  | −0.820 | −0.129 | −0.033 | 0.051 | −0.640 |
| ABSACC | −0.259 | 0.310 | −0.627 |  | 0.145 | 0.051 | −0.104 | −0.608 |
| LEVERAGE | −0.404 | 0.526 | −0.146 | 0.246 |  | −0.116 | −0.086 | −0.203 |
| GROWTH | −0.608 | 0.708 | −0.253 | 0.251 | 0.350 |  | 0.072 | −0.168 |
| INST | 0.233 | −0.171 | 0.061* | −0.161 | −0.071 | −0.142 |  | 0.195 |
| ROA | 0.811 | −0.711 | 0.643 | −0.518 | −0.416 | −0.617 | 0.195 |  |

**Table 22.5: Test for threshold effect.**

**Panel A: Sample in pre-SOX period**

*Test for single threshold*

|  |  |
|---|---:|
| Threshold estimate | 0.67095 |
| *p*-value | 0.001 |

**Panel B: Sample in post-SOX period**

*Test for single threshold*

|  |  |
|---|---:|
| Threshold estimate | 0.197239 |
| *p*-value | 0.013 |

*Test for double threshold*

|  |  |
|---|---:|
| Threshold estimate | 0.298917 |
| *p*-value | 0.037 |

*Notes:* (1) *p*-values obtained by 300 bootstrap replications.

(2) Threshold variable is the FEERATIO which defined as nonaudit services fees divided by total fees.

The test results shown in Table 22.6 are used to examine whether there was a nonlinear relationship between discretionary accruals as a proxy variable of earnings management and auditor fees for the pre-SOX period. Based on equation (22.6), each subsample is divided by FEERATIO, using its threshold value from Table 22.5.

## Table 22.6: Summary statistics from discretionary accruals regressions.

**Sample in Pre-SOX period (2000–2002)**

ABS DACC = β₀ + β₁ AUDVAR + β₂ CFO + β₃ ABSCFO + β₄ ACC + β₅ ABSACC + β₆ LEVERAGE + β₇ GROWTH + β₈ INST + β₉ ROA + ε

| Variable | Feeratio <=0.67095 Model 1 | Feeratio <=0.67095 Model 2 | Feeratio >0.67095 Model 1 | Feeratio >0.67095 Model 2 |
|---|---|---|---|---|
| RANKTOT | **0.00057** (0.001) |  | **0.0018** (0.0002) |  |
| Ranknon |  | **0.0008** (<0.0001) |  | **0.002** (<0.0001) |
| RANKAUD |  | **-0.0004** (0.034) |  | -0.0007 (0.275) |
| CFO | -0.036 (0.071) | -0.035 (0.085) | -0.260 (0.001) | -0.245 (0.002) |
| ABSCFO | 0.112 (<0.0001) | 0.111 (<0.0001) | 0.175 (0.025) | 0.196 (0.012) |
| ACC | -0.092 (<0.0001) | -0.092 (<0.0001) | -0.216 (0.002) | -0.186 (0.007) |
| ABSACC | 0.132 (<0.0001) | 0.129 (<0.0001) | 0.134 (0.011) | 0.141 (0.007) |
| LEVERAGE | 0.017 (0.108) | 0.018 (0.095) | -0.073 (0.287) | -0.082 (0.232) |
| GROWTH | 0.002 (0.125) | 0.002 (0.183) | 0.018 (0.0003) | 0.017 (0.001) |
| LOGMVE | 0.022 (<0.0001) | 0.022 (<0.0001) | 0.018 (0.205) | 0.015 (0.288) |
| INST | -0.135 (0.001) | -0.129 (0.002) | -0.340 (0.004) | -0.285 (0.016) |
| ROA | 0.050 (<0.0001) | 0.048 (<0.0001) | 0.216 (<0.0001) | 0.198 (<0.0001) |
| R² | 0.106 | 0.113 | 0.205 | 0.217 |
| Adj-R² | 0.103 | 0.109 | 0.191 | 0.202 |

Notes:
- (1) The values in parentheses are p-values.
- (2) All variables are defined as Table 22.2.
- (3) Threshold variable is the FEERATIO which defined as nonaudit services fees divided by total fees.

If the economic bond between auditors and clients dominates the reputation and litigation effects, the coefficients of RANKNON and RANKTOT should be positive. The results in Table 22.6 for RANKTOT and RANKNON indicate that nonaudit services are positively associated with the absolute value of discretionary accruals in the pre-SOX period. In addition, the coefficients of RANKTOT and RANKNON in the FEERATIO>0.67095 regressions are higher than those in the FEERATIO>0.67095 regressions, suggesting that provision of more audit services may cause auditors to compromise their independence in order to retain clients. However, RANKAUD is only negative and significant (p-value=0.034) in the FEERATIO<=0.67095 model, but the coefficient is insignificant (p-value=0.275) when FEERATIO>0.67095. This shows that auditors were more lenient when clients purchase more nonaudit services in pre-SOX period. Among the control variables, CFO, ABSCFO, ACC, ABSACC, LOGMVE, INST and ROA are associated with ABSDACC at the 5% of significance or better.

Table 22.7 presents results of estimating the regressions in the post-SOX period, and according to Table 22.5 there are two thresholds in this period. The estimates are 0.197239 and 0.298917, and thus the sample is divided into three subsamples. The associations between RANKTOT are not significant, and the results indicate that the composition of the payments made to the auditor is relevant, but the total amount of fees is not (Frankel et al., 2002). The coefficient of RANKAUD in the FEERATIO<=0.197239 regression is negative and significant, suggesting that audit fees are only related to less earnings management in this subsample. RANKTOT, RANKNON and RANKAUD are not significant in the subsample of 0.197239<FEERATIO<=0.298917, but RANKNON is positive and significant (p-value = 0.002) in the FEERATIO>0.298917 regression, and this suggests that firms which purchase more nonaudit services are more likely to have their earnings management behavior tolerated. In addition, audit services do not improve audit quality in this subsample. This suggests that economic bonding is more important in this subsample, and the cost of potential lawsuits and loss of reputation do not outweigh the economic rents.

### 22.5.2 Additional analyses

In this section, we report results of a series of additional tests.

### 22.5.2.1 Sample from 2000-2007

Our additional test in Table 22.8 examines the relation between the absolute value of discretionary accruals and auditor fees for the sample

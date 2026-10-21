# Table 53.1: Q statistics test and Lagrange multiplier tests for ARCH disturbances based on OLS residuals.¹ Model : R_{i,t} = α_t + β_i R_{m,t} + ε_{i,t}².

| Lag order | Pr>Q | Pr>LM |
|---|---|---|
| 1 | <0.01 | <0.01 |
| 2 | <0.01 | <0.01 |
| 3 | <0.01 | <0.01 |
| 4 | <0.01 | <0.01 |
| 5 | <0.01 | <0.01 |
| 6 | <0.01 | <0.01 |
| 7 | <0.01 | <0.01 |
| 8 | <0.01 | <0.01 |
| 9 | <0.01 | <0.01 |
| 10 | <0.01 | <0.01 |
| 11 | <0.01 | <0.01 |
| 12 | <0.01 | <0.01 |

| Conditions | Number of obs. | Number of obs. with ARCH | Percentage | Cumulative number of obs. with ARCH | Cumulative percentage |
|---|---|---|---|---|---|
| 1. ARCH (1) | 490,217 | 190,890 | 38.94 | 191,919 | 39.15 |
| 2. ARCH (2|not 1) | 294,328 | 88,828 | 30.18 | 168,561 | 57.27 |
| 3. ARCH (3|not 1&2) | 202,802 | 56,946 | 28.08 | 138,959 | 68.52 |

Notes:

+   1. The final sample thus consists of 987,347 observations corresponding to 7,537 firms during the period from 2010 to 2014.
+   2. ε_{i,t}|Ω_{i,t-1} ~ N(0, H_{i,t}); Ω_{i, t-1} is the information set available with respect to firm I at time t - 1; and H_{i,t} is the conditional variance, which is a function of previous disturbances, such as H_{i,t} = H(ε_{i,t-1}, ε_{i,t-2}, ..., ε_{i,t-p}).

(30.18%) exhibit ARCH (2). There are 56,946 out of the remaining observations exhibit neither ARCH (1) nor ARCH (2|not 1), or ARCH (3|not 1 or 2), observations exhibit either ARCH(1), ARCH (2|not 1), or ARCH (3|not 1 or 2).

# 53.4.3 Empirical results

Table 53.2 reports the cumulative abnormal returns (CARs) estimated with OLS method following the earnings announcements. Portfolio 1 represents firms the lowest SUE, while Portfolio 5 represents firms with the highest SUE. Portfolio 5 indicates that the CARs at the 1st date and the 31th date following earnings announcement are 0.027 and 0.056, respectively, and that the T-values calculated with the approach proposed by Brown and Warner (1985) are 18.113 and 14.051, respectively. Both are statistically significant. The CARs in Portfolio 4 at the 1st date and the 30th date following earnings

![](img/31ee7e6fa5107b22bbf7960ec96106a1_4298_0.png)

## Figure 121.1: Fama-French and alternative liquidity factors.

Note: This figure plots the 12-month moving averages of the Fama-French as well as alternative liquidity factors, with the shaded vertical bars denoting the NBER dated recessions.

## Table 121.1: Fama-French and liquidity factors.

| Statistic | MKT | SMB | HML | RMW | CMA | PS | PS^Traded | DSS | BPST |
|---|---|---|---|---|---|---|---|---|---|
| Panel A: Summary statistics of factors |  |  |  |  |  |  |  |  |  |
| N | 654 | 654 | 654 | 654 | 654 | 654 | 600 | 648 | 648 |
| Mean | 0.53 | 0.25 | 0.35 | 0.25 | 0.29 | -0.01 | 0.37 | 0.51 | 0.67 |
| SD | 4.39 | 3.03 | 2.82 | 2.22 | 2.01 | 5.52 | 3.38 | 0.72 | 34.68 |
| Min | -23.24 | -15.33 | -11.10 | -19.06 | -6.88 | -39.24 | -12.66 | -0.68 | -324.02 |
| P1 | -11.77 | -6.86 | -8.08 | -4.92 | -4.73 | -19.09 | -7.85 | -0.37 | -115.91 |
| P5 | -7.17 | -4.28 | -3.91 | -2.90 | -2.75 | -8.55 | -5.19 | -0.10 | -53.65 |
| P10 | -4.82 | -3.37 | -2.81 | -1.92 | -2.00 | -6.15 | -3.56 | -0.01 | -29.71 |
| P25 | -1.96 | -1.46 | -1.18 | -0.88 | -0.98 | -2.43 | -1.64 | 0.06 | -8.73 |
| P50 | 0.87 | 0.08 | 0.26 | 0.26 | 0.17 | 0.74 | 0.32 | 0.29 | 2.28 |
| P75 | 3.37 | 2.08 | 1.72 | 1.30 | 1.53 | 2.93 | 2.37 | 0.73 | 12.76 |
| P90 | 5.35 | 3.65 | 3.73 | 2.30 | 2.83 | 5.80 | 4.50 | 1.27 | 30.66 |
| P95 | 7.03 | 5.05 | 5.28 | 3.29 | 3.51 | 7.48 | 5.88 | 2.00 | 47.39 |
| P99 | 11.14 | 8.45 | 8.14 | 7.26 | 5.88 | 10.88 | 9.67 | 3.41 | 86.09 |
| Max | 16.10 | 18.75 | 12.90 | 13.51 | 9.56 | 27.97 | 11.19 | 5.37 | 177.89 |

## Table 121.1: (Continued)

### Panel B: Correlations among factors

|  | MKT | SMB | HML | RMW | CMA | PS | PS^Traded | DSS | BPST |
|---|---|---|---|---|---|---|---|---|---|
| MKT | 1.00 |  |  |  |  |  |  |  |  |
| SMB | 0.27 | 1.00 |  |  |  |  |  |  |  |
| HML | -0.27 | -0.08 | 1.00 |  |  |  |  |  |  |
| RMW | -0.24 | -0.37 | 0.10 | 1.00 |  |  |  |  |  |
| CMA | -0.40 | -0.07 | 0.70 | -0.01 | 1.00 |  |  |  |  |
| PS | 0.33 | 0.12 | -0.09 | -0.01 | -0.13 | 1.00 |  |  |  |
| PS^Traded | -0.01 | 0.00 | 0.05 | 0.00 | 0.02 | 0.11 | 1.00 |  |  |
| DSS | -0.12 | -0.07 | 0.04 | -0.05 | 0.08 | -0.14 | 0.03 | 1.00 |  |
| BPST | 0.18 | 0.12 | -0.01 | -0.03 | -0.02 | 0.14 | 0.00 | -0.19 | 1.00 |

*Note:* This table shows the summary statistics of the factors as well as their correlations.

As for test assets, we use 186 equity portfolios formed on various measures: 10 portfolios formed on momentum, 25 portfolios formed on size and momentum, 25 portfolios formed on size and book-to-market (BM), 32 portfolios formed on size, book-to-market, and operating profitability, 32 portfolios formed on size, book-to-market, and investment, 32 portfolios formed on size, operating profitability, and investment, and 30 industry portfolios. All the monthly portfolio return data are from Professor French’s website. The details of the construction of these portfolios are also available at Professor French’s website.

## 121.4 Empirical Results

### 121.4.1 Spanning tests

We first conduct the spanning tests in which we regress a liquidity measure on the Fama–French factors. If the Fama–French factors can span the liquidity factor, aggregate liquidity will not have marginal explanatory power in the cross-section of expected stock returns.

The spanning test results are reported in Table 121.2. Heteroscedasticity- and autocorrelation-consistent asymptotic standard errors are computed according to Newey and West (1987) with the automatic lag selection method of Newey and West (1994). As we can see, aggregate liquidity cannot be spanned by the Fama–French factors. For instance, In Columns (4)–(6), we focus on the traded version of Pástor and Stambaugh (2003) liquidity measure (PS^Traded). Column (4) shows that its unconditional mean is 0.37 percent per month with a t-statistic of 2.66; Column (5) suggests that the Fama–French three factors do not explain PS^Traded, as the intercept is 0.35 percent with a t-statistic of 2.75; Column (6) implies that adding the two new Fama–French profitability and investment factors still does not help to explain PS^{Traded}, because the intercept is still 0.37 percent with a t-statistic of 2.70.

## Table 121.2: Spanning tests.

| VARIABLES | (1) PS | (2) PS | (3) PS | (4) PS^Traded | (5) PS^Traded | (6) PS^Traded | (7) DSS | (8) DSS | (9) DSS | (10) BPST | (11) BPST | (12) BPST |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Constant | -0.01
(-0.05) | -0.24
(-1.08) | -0.34
(-1.43) | 0.37***
(2.66) | 0.35***
(2.75) | 0.37***
(2.70) | 0.51***
(18.15) | 0.52***
(4.80) | 0.53***
(4.73) | 0.67
(0.50) | -0.44
(-0.16) | -0.87
(-0.33) |
| MKT |  | 0.39***
(5.30) | 0.42***
(5.09) |  | -0.00
(-0.03) | -0.01
(-0.20) |  | -0.02*
(-1.75) | -0.02*
(-1.87) |  | 1.25***
(2.90) | 1.38***
(2.97) |
| SMB |  | 0.11
(1.01) | 0.17*
(1.87) |  | 0.00
(0.01) | -0.00
(-0.04) |  | -0.01
(-1.52) | -0.02***
(-2.92) |  | 1.17**
(2.47) | 1.39***
(2.76) |
| HML |  | -0.01
(-0.08) | -0.03
(-0.18) |  | 0.05
(0.53) | 0.08
(0.61) |  | 0.00
(0.22) | -0.01
(-0.33) |  | 0.42
(0.81) | 0.14
(0.21) |
| RMW |  |  | 0.26**
(1.96) |  |  | -0.02
(-0.31) |  |  | -0.03
(-1.51) |  |  | 0.96*
(1.93) |
| CMA |  |  | 0.04
(0.19) |  |  | -0.06
(-0.45) |  |  | 0.02
(0.62) |  |  | 0.59
(0.52) |
| R² | 0.00 | 0.11 | 0.12 | 0.00 | -0.00 | -0.01 | 0.00 | 0.01 | 0.02 | 0.00 | 0.04 | 0.04 |

Note: The spanning test results are reported in this Table. Heteroscedasticity- and autocorrelation-consistent asymptotic standard errors are computed according to Newey and West (1987) with the automatic lag selection method of Newey and West (1994). Robust t-statistics in parentheses, *** p < 0.01, ** p < 0.05, * p < 0.1.

The evidence suggests that aggregate liquidity cannot be spanned by the Fama–French factors. Next, we examine if aggregate liquidity has incremental explanatory power in the cross-section of expected stock returns with the time-series regression approach of Fama and French (2015). We first focus on the portfolios formed on momentum, as Pástor and Stambaugh (2003) imply that aggregate liquidity is related to momentum effects. Then, we take into account other cross-sections of stock returns.

### 121.4.2 Benchmark results with momentum portfolios

Table 121.3 summarizes time-series regressions over the entire sample period from 1963 to 2017 with 10 momentum portfolios as the test assets. In these unconditional tests, we do not allow the factor loadings to vary over time. Panels A and B show the results based on FF3 and FF3-PS, respectively. To save space, we drop the coefficient estimates on the Fama–French factors. Panel C presents the summary statistics, including the average absolute value of the intercepts (|ᾱ|), the average of the standard errors of the intercepts (s̄), the average adjusted R² (R̄²), and the GRS F-test statistic (GRS).

Panel A shows that the unconditional FF3 fails to account for the momentum effects, as the intercepts on six out of ten momentum portfolios are significantly different from zero. In particular, loser portfolios (Portfolios Low, 2, and 3) have significantly negative intercepts unexplained by the Fama–French three factors, and the winner portfolios (Portfolios 8, 9 and High) have significantly positive intercepts. Pástor and Stambaugh (2003) find that their liquidity measure helps to explain momentum effects. Therefore, in Panel B, we add the PS to the FF3. As we can see, only one out of 10 momentum portfolios (Portfolio 6) has statistically significant loading on PS. Furthermore, the intercepts on the loser and winner momentum portfolios only change trivially. For instance, the intercept for Low (High) changes from −1.09 (0.58) percent to −1.08 (0.57) percent. The adjusted R²s are also similar across two models for the same test assets. Panel C confirms the above observations. Enhancing the FF3 with the PS liquidity factor does not improve the performance of the FF3. From the FF3 to its enhanced

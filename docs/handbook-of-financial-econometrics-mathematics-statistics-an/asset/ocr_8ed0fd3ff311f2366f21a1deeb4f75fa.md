# Table 96D.1: Moving estimates process for testing the break point of structural change.

| c | Beta risk | Total risk | c | Beta risk | Total risk |
|---|---|---|---|---|---|
| 0.20 | 120.38 | 92.78 | 1.01 | 658.58 | 533.26 |
| 0.25 | 147.77 | 114.94 | 1.02 | 646.43 | 524.02 |
| 0.30 | 205.83 | 153.89 | 1.03 | 636.99 | 516.94 |
| 0.35 | 252.56 | 179.52 | 1.04 | 621.57 | 506.64 |
| 0.40 | 333.30 | 244.85 | 1.05 | 619.94 | 507.41 |
| 0.45 | 395.33 | 298.05 | 1.06 | 610.91 | 503.46 |
| 0.50 | 421.89 | 320.42 | 1.07 | 616.34 | 505.71 |
| 0.55 | 445.75 | 340.36 | 1.08 | 610.81 | 502.08 |
| 0.60 | 505.14 | 213.02 | 1.09 | 608.96 | 505.16 |
| 0.65 | 532.57 | 205.06 | 1.10 | 609.88 | 496.72 |
| 0.70 | 572.82 | 411.85 | 1.15 | 610.61 | 499.96 |
| 0.75 | 600.57 | 452.04 | 1.20 | 575.99 | 473.31 |
| 0.80 | 633.15 | 485.64 | 1.25 | 543.25 | 445.85 |
| 0.85 | 674.48 | 524.66 | 1.30 | 532.27 | 431.02 |
| 0.90 | 675.53 | 542.20 | 1.35 | 505.57 | 408.10 |
| 0.91 | 682.40 | 547.18 | 1.40 | 487.91 | 388.90 |
| 0.92 | 678.08 | 542.58 | 1.45 | 446.97 | 364.58 |
| 0.93 | **682.43** | 549.74 | 1.50 | 408.25 | 326.46 |
| 0.94 | 679.55 | 547.81 | 1.55 | 383.32 | 304.93 |
| 0.95 | 679.52 | 546.92 | 1.60 | 345.32 | 266.34 |
| 0.96 | 675.88 | **549.83** | 1.65 | 327.34 | 249.22 |
| 0.97 | 668.42 | 543.73 | 1.70 | 309.13 | 231.42 |
| 0.98 | 669.35 | 547.23 | 1.75 | 296.67 | 223.43 |
| 0.99 | 664.33 | 548.16 | 1.80 | 278.69 | 212.60 |
| 1.00 | 622.77 | 545.64 |  |  |  |

Notes: This shows the F-statistics of moving estimates processes. The non-structural change regression and structural change regression are as follows:

ln( payout ratio_i,t / (1 - (payout ratio_i,t)) ) = α + β1 Risk_i,t + β2 Growth_i,t + β3 ln(Size)_i,t + β4 ROA_i,t + e_i,t,

ln( payout ratio_i,t / (1 - (payout ratio_i,t)) ) = α + β1' Risk_i,t + β2' D(g_i,t < c · ROA_i,t) · Risk_i + β3' Growth_i,t + β5' ln(Size)_i,t + β6 ROA_i,t + e_i,t.

The dependent variable is the payout ratio with a logistic transformation. The break-point, c, is between 0.2 times and 1.8 times the rate of return on total assets. The dummy variable is equal to 1 if a firm's 5-year average growth rate is less than c times its 5-year average ROA, and 0 otherwise. The independent variables are beta risk (total risk), dummy times beta risk (total risk), growth rate, log of size, and the rate of return on assets. F-statistics are under the null hypothesis that the relationship between the payout ratio and the risk does not depend on the growth rate of a firm.

## Table 51.7: Comparison of numerical accuracy between the CEV and the SV models (deep out-of-the-money put option).

| Time (s) | CEV N | CEV price (analytic) | CEV error | SV N, M | SV price (analytic) | SV error |
|---:|---:|---:|---:|---:|---:|---:|
| 0.1 | 1433 | 11.38947 | −0.00069 |  |  |  |
| 0.2 | 1992 | 11.38803 | −0.00213 | 10 | 13.51492 | 2.12476 |
| 0.5 | 2946 | 11.38925 | −0.00091 | 23 | 11.64352 | 0.25336 |
| 1 | 3691 | 11.38920 | −0.00096 | 49 | 11.42603 | 0.03587 |
| 2 | 4481 | 11.38996 | −0.00020 | 96 | 11.39743 | 0.00727 |
| 5 |  |  |  | 184 | 11.38905 | −0.00112 |
| 10 |  |  |  | 265 | 11.38919 | −0.00097 |
| 20 |  |  |  | 361 | 11.38937 | −0.00079 |
| 50 |  |  |  | 522 | 11.38969 | −0.00047 |
| 100 |  |  |  | 678 | 11.38969 | −0.00047 |
| 200 |  |  |  | 870 | 11.38964 | −0.00052 |

Deep out-of-the-money put option ($X=250$, $S=300$, $X=250$); CEV analytic price: 2.851594; SV analytic price: 11.39016.

## Table 51.8: Comparison of computational efficiency between the CEV and the SV models (deep out-of-the-money put option).

| CEV put error | CEV $N$ ($X=250$) | CEV CPU time (s) | SV put error | SV $N,M$ ($X=250$) | SV CPU time (s) |
|---:|---:|---:|---:|---:|---:|
| 0.01 | 472 | 0.016 | 0.01 | 81 | 1.641 |
| 0.005 | 873 | 0.031 | 0.005 | 102 | 2.156 |
| 0.001 | 4431 | 1.922 | 0.001 | 537 | 53.609 |

In the SV model. Consequently, although the numerical methods of the SV model are applicable for pricing, its computationally intensive optimization procedure makes the SV model practically infeasible for this task if one would like to conduct empirical test for American options.

Next, we investigate the pricing performance of the CEV numerical method across several values of $\beta$. Six different most common values of $\beta$—$-4$, $-3$, $-2$, $-1$, $0$, and $1$—in our European option empirical test of Section 51.4.2.2 are chosen in our experiment. Another parameter $\delta$ is set to make the volatility equal to 20%, i.e., $\delta=\sigma_{BS}S^{1-\beta/2}=(20\%)S^{1-\beta/2}$. A summary of computational efficiency in pricing European put options is reported in Table 51.11 with $\beta$ values. We can find that computational efficiency of

## Table 51.9: Comparison of numerical accuracy between the CEV and the SV models (deep in-the-money put option).

| Time (s) | CEV N | CEV price | Error | SV N,M | SV price | Error |
|---|---|---|---|---|---|---|
| 0.1 | 1434 | 57.99623 | -0.00124 |  |  |  |
| 0.2 | 1984 | 57.99584 | -0.00163 | 10 | 48.40058 | -9.59689 |
| 0.5 | 2953 | 57.99688 | -0.00059 | 24 | 55.76441 | -2.23305 |
| 1 | 3706 | 57.99656 | -0.00091 | 48 | 57.47296 | -0.52451 |
| 2 | 4574 | 57.99745 | -0.00002 | 86 | 57.82273 | -0.17474 |
| 5 |  |  |  | 184 | 57.95248 | -0.04499 |
| 10 |  |  |  | 265 | 57.97286 | -0.02461 |
| 20 |  |  |  | 361 | 57.98215 | -0.01532 |
| 50 |  |  |  | 522 | 57.98858 | -0.00889 |
| 100 |  |  |  | 678 | 57.99134 | -0.00613 |
| 200 |  |  |  | 869 | 57.99313 | -0.00434 |

## Table 51.10: Comparison of computational efficiency between the CEV and the SV models (deep in-the-money put option).

| Put error | CEV X=350 N | CPU time (s) | Put error | SV X=350 N,M | CPU time (s) |
|---|---|---|---|---|---|
| 0.01 | 348 | 0.016 | 0.01 | 477 | 39.563 |
| 0.005 | 423 | 0.016 | 0.005 | 779 | 146.563 |
| 0.001 | 4286 | 1.625 | 0.001 | 2800-2900 | >9050.344 |

the CEV model is robust across different values of β. The longest time to reach $0.0005 absolute pricing error in our experiment is merely 0.75 s in pricing deep in-the-money put with β equal to 0 and −1. Therefore, we can conclude that the trinomial method of the CEV process by Boyle and Tian (1999) in terms of numerical efficiency is robust enough for the empirical study.

Finally, we should note that the algorithms of American option pricing for these two numerical methods are similar to their European cases, except for the additional step for checking the early exercise possibility at each time step. Therefore, the time for pricing American-style option is expected to be longer than that of the European option.

## Table 51.11: Comparison of computational efficiency of the CEV model across different values of β.

| CEV Put | S=300 | δ=(20%)S^{1-β/2} | Interest rate = 5% | T=0.5 year |
|---|---|---|---|---|
| β = -4 |  |  | β = -3 |  |
| Analytic | X=350 Solution | 43.5759014 | Analytic | X=350 Solution | 43.8767725 |
| Absolute error | N | CPU time (s) | Absolute error | N | CPU time (s) |
| 0.01 | 83 | 0.016 | 0.01 | 87 | 0.016 |
| 0.005 | 235 | 0.016 | 0.005 | 224 | 0.016 |
| 0.001 | 1267 | 0.063 | 0.001 | 1367 | 0.094 |
| 0.0005 | 2567 | 0.344 | 0.0005 | 2589 | 0.375 |
| Analytic | X=300 Solution | 13.3942732 | Analytic | X=300 Solution | 13.3508924 |
| Absolute error | N | CPU time (s) | Absolute error | N | CPU time (s) |
| 0.01 | 137 | 0.016 | 0.01 | 113 | 0.016 |
| 0.005 | 252 | 0.016 | 0.005 | 224 | 0.016 |
| 0.001 | 1267 | 0.078 | 0.001 | 1069 | 0.063 |
| 0.0005 | 2515 | 0.328 | 0.0005 | 2208 | 0.235 |
| Analytic | X=250 Solution | 3.32127105 | Analytic | X=250 Solution | 2.85159417 |
| Absolute error | N | CPU time (s) | Absolute error | N | CPU time (s) |
| 0.01 | 103 | 0.016 | 0.01 | 72 | 0.016 |
| 0.005 | 190 | 0.016 | 0.005 | 175 | 0.016 |
| 0.001 | 1581 | 0.125 | 0.001 | 959 | 0.047 |
| 0.0005 | 2837 | 0.438 | 0.0005 | 2374 | 0.297 |
| CEV Put | S=300 | δ=(20%)S^{1-β/2} | interest rate = 5% | T=0.5 year |
| β = -2 |  |  | β = -1 |  |
| Analytic | X=350 Solution | 44.2030637 | Analytic | X=350 Solution | 44.5558916 |
| Absolute error | N | CPU time (s) | Absolute error | N | CPU time (s) |
| 0.01 | 98 | 0.016 | 0.01 | 143 | 0.016 |
| 0.005 | 271 | 0.016 | 0.005 | 146 | 0.016 |
| 0.001 | 1413 | 0.094 | 0.001 | 1449 | 0.11 |
| 0.0005 | 2506 | 0.344 | 0.0005 | 2714 | 0.391 |

## Table 51.11: (Continued)

Analytic  X = 300  Solution  13.3168835    Analytic  X = 300  Solution  13.2912286
Absolute error  N  CPU time (s)    Absolute error  N  CPU time (s)
0.01  105  0.016    0.01  101  0.016
0.005  207  0.016    0.005  201  0.016
0.001  1005  0.047    0.001  981  0.047
0.0005  2013  0.203    0.0005  1940  0.187

Analytic  X = 250  solution  2.4388784    Analytic  X = 250  solution  2.07327803
Absolute error  N  CPU time (s)    Absolute error  N  CPU time (s)
0.01  67  0.016    0.01  59  0.016
0.005  160  0.016    0.005  146  0.016
0.001  878  0.031    0.001  629  0.032
0.0005  1413  0.093    0.0005  1805  0.156

CEV Put  S = 300  δ = (20%)S^{1-β/2}    Interest rate = 5%    T = 0.5 year
β = 0    β = 1
Put analytic  X = 350  solution  44.9365369    Put analytic  X = 350  solution  45.3465076
Error  N  CPU time (s)    Error  N  CPU time (s)
0.01  158  0.016    0.01  142  0.016
0.005  317  0.016    0.005  339  0.016
0.001  1724  0.157    0.001  1605  0.14
0.0005  3397  0.75    0.0005  3413  0.75

Put analytic  X = 300  solution  13.2732913    Put analytic  X = 300  solution  13.2626748
Error  N  CPU time (s)    Error  N  CPU time (s)
0.01  103  0.016    0.01  108  0.016
0.005  205  0.016    0.005  213  0.016
0.001  1000  0.062    0.001  1069  0.063
0.0005  2005  0.203    0.0005  2135  0.25

Put analytic  X = 250  solution  1.74889375    Put analytic  X = 250  solution  1.46169114
Error  N  CPU time (s)    Error  N  CPU time (s)
0.01  71  0.016    0.01  65  0.016
0.005  133  0.016    0.005  121  0.016
0.001  852  0.047    0.001  724  0.032
0.0005  1650  0.125    0.0005  1429  0.11

The CEV process for pricing more complicated exotic options or credit risk models.

## Bibliography

Albanese, O. and Chen, O. X. (2004). Pricing Equity Default Swaps. Risk, 18(6), 83-87.
Bakshi, G., Cao, C. and Chen, Z. (1997). Empirical Performance of Alternative Option Pricing Models. Journal of Finance, 52, 2003-2049.
Bakshi, G., Cao, C. and Chen, Z. (2000). Pricing and Hedging Long-Term Options. Journal of Econometrics, 94, 277-318.
Bakshi, G., Cao, C. and Chen, Z. (2009). Option Pricing and Hedging Performance Under Stochastic Volatility and Stochastic Interest Rates. Handbook of Quantitative Finance and Risk Management. New York: Springer Science and Business.
Bates, D. S. (1996a). Testing Option Pricing Models. In G. S. Maddala and C. R. Rao (eds.), Handbook of Statistics, Vol. 15: Statistical Methods in Finance. Amsterdam: North Holland, pp. 567-611.
Bates, D. S. (1996b). Jumps and Stochastic Volatility: Exchange Rate Processes Implicit in Deutschemark Options. Review of Financial Studies, 9, 69-108.
Bates, D. S. (2000). Post-'87 Crash Fears in the S&P 500 Futures Option Market. Journal of Econometrics, 94, 181-238.
Beckers, S. (1980). The Constant Elasticity of Variance Model and its Implications for Option Pricing. Journal of Finance, 35, 661-673.
Benton, D. and Krishnamoorthy, K. (2003). Computing Discrete Mixtures of Continuous Distributions: Noncentral Chisquare, Noncentral t and the Distribution of the Square of the Sample Multiple Correlation Coefficient. Computational Statistics & Data Analysis, 43, 249-267.
Black, F. (1976). Studies of Stock Price Volatility Changes. Proceedings of the 1976 American Statistical Association. Business and Economics Statistics Section, 177-181.
Boyle, P. P. (1986). Option Valuation Using a Three-Jump Process. International Options Journal, 3, 7-12.
Boyle, P. P. (1988). A Lattice Framework for Option Pricing with Two State Variables. Journal of Financial and Quantitative Analysis, 35, 1-12.
Boyle, P. P. and Tian, Y. (1999). Pricing Lookback and Barrier Options under the CEV Process. Journal of Financial and Quantitative Analysis, 34(2), 241-264. (Correction: Boyle, P., Tian, Y. and Imai, J. Look-back options under the CEV process: A correction. JFQA website at http://depts.washington.edu/jfqa/hold/342BoyleCrx1.pdf.)
Campi, L. and Sbuelz, A. (2005). Closed-form Pricing of Benchmark Default Swaps Under the CEV Assumption. Risk Letters, 1(3).
Campi, L., Polbennikov, S. and Sbuelz, A. (2005). Assessing Credit with Equity: A CEV Model with Jump to Default. Working Paper, University Paris Dauphine.
Carr, P. and Linetsky, V. (2006). A Jump to Default Extended CEV Model: An Application of Bessel Processes. Finance and Stochastics, 10, 303-330.
Chan, K. C., Karolyi, G. A., Longstaff, F. A. and Sanders, A. B. (1992). An Empirical Comparison of Alternative Models of the Short-term Interest Rate. Journal of Finance, 47, 1209-1227.
Chen, R. and Lee, C. F. (1993). A Constant Elasticity of Variance Family of Stock Prices in Option Pricing: Review and Integration. Journal of Financial Studies, 1(1), 29-51.
Cox, J. C. (1975). Notes on Option Pricing I: Constant Elasticity of Diffusions. Unpublished draft, Standford University, September.


Using this definition of short sales provides that the investor should invest 90.41% of his or her money in security 1, and so on. If all \(W_i\)'s are added together, they equal 100%. This is true because the definition says that the funds received from selling short a security should be used to purchase more of the other securities.

According to Lintner’s method,

$$\sum_{i=1}^{5} |H_i| = 0.3426.$$

Now, to scale the \(H_i\) values into an optimum portfolio, apply equation (82.14):

$$W_1 = \frac{0.2311}{0.3426} = 0.6745,$$

$$W_2 = \frac{0.0373}{0.3426} = 0.1089,$$

$$W_3 = \frac{0.0307}{0.3426} = 0.0896,$$

$$W_4 = \frac{-0.0079}{0.3426} = -0.0231,$$

$$W_5 = \frac{-0.0356}{0.3426} = -0.1039.$$

Thus, the Lintner model states that an investor should invest 67.45% in security 1, 10.89% in security 2, and 8.96% in security 3. The investor should then sell short 2.31% and 10.39% of securities 4 and 5, respectively.

The differences between Lintner’s method and the standard method are due to the different definitions of short selling as discussed earlier. The standard method assumes that the investor has the proceeds of the short sale, while Lintner’s method assumes that the short seller does not receive the proceeds and must provide funds as collateral.

The method discussed in this section does not require the inputs of covariance among individual securities. Hence, it is a simpler method than that of the Sharpe performance-measure method discussed in the previous section. The relative advantage of the Sharpe performance method over the Treynor performance method is exactly identical to the relative advantage of the Markowitz model over the Sharpe single-index model. In sum, the Treynor performance method for portfolio selection requires the information of both the risk-free rate and the market rates of return.

## 82.5 Treynor-Measure Approach with Short Sales Not Allowed

Equation (82.13) can be modified to

$$H_i = \frac{\beta_i}{\sigma_{e i}^2} \left( \frac{\bar{R}_i - R_f}{\beta_i} - C^* \right), \quad (82.15)$$

in which \(\frac{(\bar{R}_i - R_f)}{\beta_i}\) is the Treynor performance measure and \(C^*\) can be defined as

$$C^* = \frac{\sigma_m^2 \sum_{j=1}^i \frac{(\bar{R}_j - R_f)\beta_j}{\sigma_{e j}^2}}{1 + \sigma_m^2 \sum_{j=1}^i \frac{\beta_j^2}{\sigma_{e j}^2}}. \quad (82.16)$$

Elton et al. (1976) also derive a Treynor-measure approach with short sales not allowed. From Appendix 82C, equation (82.16) should be modified to

$$H_i = \frac{\beta_i}{\sigma_{e i}^2} \left( \frac{\bar{R}_i - R_f}{\beta_i} - C^* \right) + \mu_i, \quad (82.17)$$

where \(H_i \ge 0\), \(\mu_i \ge 0\), and \(H_i \mu_i = 0\), then

$$C^* = \frac{\sigma_m^2 \sum_{j=1}^d \frac{\bar{R}_j - R_f}{\sigma_{e j}^2} \beta_j}{1 + \sigma_m^2 \sum_{j=1}^d \frac{\beta_j^2}{\sigma_{e j}^2}}, \quad (82.18)$$

where \(d\) is a set that contains all stocks with positive \(H_i\).

If all securities have positive \(\beta_i\)'s, the following four-step procedure from Elton et al. can be used to choose securities to be included in the optimum portfolio.

- 1. Use the Treynor performance measure \((\bar{R}_i - R_f)/\beta_i\) to rank the securities in descending order.
- 2. Use equation (82.18) to calculate \(C_i^*\) for the first \(i\) securities.
- 3. Include the \(i\) securities for which \((\bar{R}_i - R_f)/\beta_i\) are larger than \(C_i^*\). Then \(C^*\) is equal to \(C_i^*\).
- 4. Use equation (82.5) to calculate optimum weights for the \(i\) securities.

## Worksheet for DJIAs

| TICKER | Mean_Ri | StdDev_sigma_ei | Ri_minus_Rf | beta_i | sigma_ei_sq | (Ri-Rf)/beta_i | (Ri-Rf)*beta_i/sigma_ei_sq | CumSum_5 | beta_i_sq/sigma_ei_sq | CumSum_7 | C_i_star |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| MCD | 0.0173 | 0.0461 | 0.0155 | 0.4868 | 0.0015 | 0.0318 | 5.1718 | 5.17 | 162.78 | 162.78 | 0.0103 |
| VZ | 0.0095 | 0.0571 | 0.0077 | 0.6171 | 0.0022 | 0.0125 | 2.1822 | 7.35 | 174.64 | 337.42 | 0.0109 |
| KO | 0.0093 | 0.0510 | 0.0075 | 0.6107 | 0.0015 | 0.0122 | 2.9839 | 10.34 | 244.09 | 581.52 | 0.0112 |
| WMT | 0.0051 | 0.0473 | 0.0032 | 0.2939 | 0.0020 | 0.0110 | 0.4715 | 10.81 | 42.89 | 624.41 | 0.0112 |
| IBM | 0.0093 | 0.0603 | 0.0074 | 0.7494 | 0.0020 | 0.0099 | 2.7704 | 13.58 | 278.72 | 903.13 | 0.0109 |
| MRK | 0.0086 | 0.0778 | 0.0068 | 0.6950 | 0.0047 | 0.0097 | 0.9974 | 14.58 | 102.44 | 1005.57 | 0.0108 |
| TRV | 0.0072 | 0.0537 | 0.0054 | 0.5595 | 0.0020 | 0.0096 | 1.5043 | 16.08 | 156.46 | 1162.03 | 0.0107 |
| CVX | 0.0087 | 0.0624 | 0.0069 | 0.7161 | 0.0024 | 0.0096 | 2.0276 | 18.11 | 211.22 | 1373.25 | 0.0106 |
| DIS | 0.0109 | 0.0700 | 0.0091 | 1.0495 | 0.0017 | 0.0086 | 5.6156 | 23.72 | 650.72 | 2023.97 | 0.0100 |
| UTX | 0.0094 | 0.0616 | 0.0076 | 0.9454 | 0.0012 | 0.0080 | 6.0253 | 29.75 | 754.36 | 2778.32 | 0.0095 |
| PG | 0.0051 | 0.0489 | 0.0032 | 0.5031 | 0.0017 | 0.0064 | 0.9697 | 30.72 | 151.09 | 2929.41 | 0.0094 |
| XOM | 0.0048 | 0.0520 | 0.0030 | 0.4699 | 0.0021 | 0.0063 | 0.6699 | 31.39 | 105.85 | 3035.27 | 0.0093 |
| T | 0.0055 | 0.0616 | 0.0037 | 0.6707 | 0.0025 | 0.0055 | 0.9805 | 32.37 | 179.27 | 3214.53 | 0.0091 |
| MSFT | 0.0058 | 0.0802 | 0.0039 | 1.0130 | 0.0035 | 0.0039 | 1.1424 | 33.51 | 294.94 | 3509.47 | 0.0087 |
| HPQ | 0.0044 | 0.0752 | 0.0026 | 1.0496 | 0.0025 | 0.0024 | 1.0913 | 34.60 | 448.21 | 3957.68 | 0.0081 |
| KFT | 0.0030 | 0.0623 | 0.0012 | 0.6072 | 0.0028 | 0.0020 | 0.2581 | 34.86 | 129.35 | 4087.04 | 0.0079 |
| CAT | 0.0029 | 0.1279 | 0.0011 | 1.8954 | 0.0059 | 0.0006 | 0.3565 | 35.22 | 610.24 | 4697.27 | 0.0070 |
| DD | 0.0024 | 0.0872 | 0.0006 | 1.3410 | 0.0023 | 0.0004 | 0.3358 | 35.55 | 766.25 | 5463.52 | 0.0061 |
| JNJ | 0.0019 | 0.0443 | 0.0001 | 0.5758 | 0.0010 | 0.0002 | 0.0639 | 35.62 | 331.58 | 5795.10 | 0.0058 |
| MMM | 0.0019 | 0.0665 | 0.0000 | 0.7421 | 0.0029 | 0.0000 | 0.0071 | 35.63 | 192.91 | 5988.01 | 0.0056 |
| PFE | 0.0012 | 0.0638 | -0.0006 | 0.6569 | 0.0028 | -0.0009 | -0.1368 | 35.49 | 151.62 | 6139.63 | 0.0055 |
| CSCO | -0.0010 | 0.0892 | -0.0029 | 1.2445 | 0.0035 | -0.0023 | -1.0299 | 34.46 | 447.41 | 6587.04 | 0.0050 |
| JPM | -0.0016 | 0.0991 | -0.0034 | 1.1347 | 0.0061 | -0.0030 | -0.6362 | 33.82 | 209.63 | 6796.67 | 0.0047 |
| BA | -0.0036 | 0.0965 | -0.0055 | 1.2556 | 0.0048 | -0.0044 | -1.4447 | 32.38 | 331.72 | 7128.39 | 0.0043 |
| INTC | -0.0041 | 0.0855 | -0.0059 | 1.0853 | 0.0039 | -0.0055 | -1.6467 | 30.73 | 300.84 | 7429.23 | 0.0040 |
| HD | -0.0028 | 0.0768 | -0.0046 | 0.7130 | 0.0045 | -0.0065 | -0.7319 | 30.00 | 113.42 | 7542.65 | 0.0038 |
| AXP | -0.0094 | 0.1230 | -0.0111 | 1.7421 | 0.0063 | -0.0065 | -3.1098 | 26.89 | 480.54 | 8023.19 | 0.0032 |
| AA | -0.0211 | 0.1765 | -0.0229 | 2.6867 | 0.0101 | -0.0085 | -6.1104 | 20.78 | 716.57 | 8739.77 | 0.0023 |
| GE | -0.0135 | 0.1126 | -0.0154 | 1.6787 | 0.0045 | -0.0092 | -5.7667 | 15.01 | 629.83 | 9369.59 | 0.0015 |
| BAC | -0.0370 | 0.2225 | -0.0388 | 2.6688 | 0.0290 | 0.0145 | -3.5646 | 11.45 | 245.28 | 9614.87 | 0.0011 |
| \(R_m\) | -0.0013 |  |  |  |  |  |  |  |  | Max \(C_i^*\) | 0.0012 |
| Var(\(R_m\)) | 0.00294 |  |  |  |  |  |  |  |  |  |  |
| \(R_f\) | 0.00183 |  |  |  |  |  |  |  |  |  |  |

## Table 82.3: Positive Optimum Weight for Three Securities

| TICKER | \(H_i\) | \(\beta_i / \sigma^2_{e i}\) | \((\bar{R}_i - R_f) / \beta_i\) | (A) Optimum Percentage | (B) Mean \(\bar{R}_i\) | (A) × (B) |
|---|---:|---:|---:|---:|---:|---:|
| MCD | 6.8729 | 334.4223 | 0.0318 | 0.9001 | 0.0173 | 0.0156 |
| VZ | 0.3609 | 282.9821 | 0.0125 | 0.0473 | 0.0095 | 0.0005 |
| KO | 0.4016 | 399.6946 | 0.0122 | 0.0526 | 0.0093 | 0.0005 |
| TOTAL | 7.635466 |  |  | 1 | \(\bar{R}_p\) | 0.0165 |
| \(C^*\) | 0.0112 |  |  |  |  |  |

Using equation (82.15), the optimum weights can be estimated for all three securities, as indicated in Table 82.3. In other words, 90.01% of our fund should be invested in security MCD, 4.73% in security VZ, and 5.26% in security KO. Based upon the optimal weights, the average rate for the portfolio \(\bar{R}_p\) is calculated as 1.65%, as presented in the last column of Table 82.3.

## 82.6 Impact of Short Sales on Optimal-Weight Determination

The Markowitz model of portfolio analysis requires a large number of inputs, as it is necessary to estimate the covariance between each pair of securities. Previously, the analysis was simplified by the assumption that security returns were related through a common response to some market index. This model, known as Sharpe’s single-index model, greatly reduces the number of inputs necessary to analyze the risk and return characteristics of portfolios. In both the Markowitz and Sharpe models, the analysis is facilitated by the presence of short selling.

This chapter discusses a method proposed by Elton and Gruber for the selection of optimal portfolios. Their method involves ranking securities based on their excess return-to-beta ratio and choosing all securities with a ratio greater than some particular cutoff level \(C^*\). It is interesting to note that while the presence of short selling facilitated the selection of the optimum portfolio in both the Markowitz and Sharpe models, it complicates the analysis when we use the Elton and Gruber approach. From Example 82.3, using the DJIA, the absence of short selling allowed the formation of the optimal portfolio using only eight stocks.

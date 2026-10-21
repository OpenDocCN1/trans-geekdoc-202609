
The mean difference is statistically insignificant indicating the estimates of VIX_CBOE and VIX_a are consistent with each other. Furthermore, to examine the equality of probability distributions between VIX_CBOE and VIX_a, we employ a two-sample Kolmogorov–Smirnov (KS) Test. Panel 3 reports the KS test statistic (D = 0.0085) with an associated p-value. It appears that the test fails to reject the equality of the two distributions. From the analytical results in Table 40.1, we conclude that the diversity of our VIX estimation from CBOE's VIX is almost indistinguishable.

```
W_T = ln^3 (K_0/S_0) + 3 ln^2 (K_0/S_0) (F_0/K_0 - 1) + 3 e^{rT} [∫_{K_0}^∞ [2 ln (K/S_0) - ln^2 (K/S_0)] C_T(K) dK / K^2 - ∫_{0}^{K_0} [2 ln (S_0/K) + ln^2 (S_0/K)] P_T(K) dK ], (40.29)
```

and

```
X_T = ln^4 (K_0/S_0) + 4 ln^3 (K_0/S_0) (F_0/K_0 - 1) + 4 e^{rT} [∫_{K_0}^∞ [3 ln^2 (K/S_0) - ln^3 (K/S_0)] C_T(K) dK / K^2 + ∫_{0}^{K_0} [3 ln^2 (S_0/K) + ln^3 (S_0/K)] P_T(K) dK ], (40.30)
```

Similar to those in (40.17) and (40.18), estimates of W_T and X_T as well as their annualization can be calculated from option data

```
\hat{W}_T = [ln^3 (K_0/S_0) + 3 ln^2 (K_0/S_0) (F_0/K_0 - 1)] + 3 e^{rT} \sum_i 1/K_i^2 [2 ln (K_i/S_0) - ln^2 (K_i/S_0)] Q_{K_i \Delta K_i}, (40.31a)
```

```
$$\hat{W}_a = \left\{ \left[ \frac{N(T_2)-N(30)}{N(T_2)-N(T_1)} \right] (T_1 \cdot \hat{W}_1) + \left[ \frac{N(30)-N(T_1)}{N(T_2)-N(T_1)} \right] (T_2 \cdot \hat{W}_2) \right\} \left( \frac{N(365)}{N(30)} \right), \tag{40.31b}$$
```

```
$$\hat{X}_T = \left[ \ln^4 \left( \frac{K_0}{S_0} \right) + 4 \ln^3 \left( \frac{K_0}{S_0} \right) \left( \frac{F_0}{K_0} - 1 \right) \right] + 4 e^{rT} \sum_i \frac{1}{K_i^2} \left[ 3 \ln^2 \left( \frac{K_i}{S_0} \right) - \ln^3 \left( \frac{K_i}{S_0} \right) \right] Q_{K_i \Delta K_i}, \tag{40.31c}$$
```

and

```
$$\hat{X}_a = \left\{ \left[ \frac{N(T_2)-N(30)}{N(T_2)-N(T_1)} \right] (T_1 \cdot \hat{X}_1) + \left[ \frac{N(30)-N(T_1)}{N(T_2)-N(T_1)} \right] (T_2 \cdot \hat{X}_2) \right\} \left( \frac{N(365)}{N(30)} \right). \tag{40.31d}$$
```

Figure 40.1 illustrates VIX’s estimation bias of volatility and how this bias is related to distributional moments. Expressed by equations (40.20) and (40.27), since it directly estimates ex ante standard deviation of log-returns, GVIX could serve as a measure of the true return volatility. Therefore, we adopt the difference between GVIX and VIX as the deviation of VIX from the true volatility and refer to this deviation as VIX-bias. Figure 40.1(a) depicts the daily VIX-bias over our sample period. The daily VIX-bias, in a range from −0.03 to 5.58, is generally positive indicating that VIX understated the true volatility during January 2005 to May 2014. This volatility undervaluation was extremely large during the financial crisis of 2009. Figure 40.1(b) plots the divergence of VIX from the second-moment (V_a). A similarly reversed pattern as Figure 40.1(a) appears in Figure 40.1(b). This provides further evidence of the downward bias of VIX. Notably, the movement of daily market expectation of third-moment estimates (Ŵ_a), pictured in Figure 40.1(c), moves almost perfectly and adversely with the VIX-bias. The third-moment estimates were generally non-positive during our sample period and had a value ranging from −3585 to 19.51. Since the composition of VIX includes one-third of the third-moment according to Theorem 40.2, the negative value of Ŵ_a appears to be the main cause for VIX’s underestimation of the true volatility. Figure 40.1(d) displays the impact of the fourth-moment (measured by one-twelfth of X̂_a) over time. Again, the movement of VIX-bias seems to be highly correlated with that of X̂_a. In addition, the value of X̂_a also dramatically increased when the market experienced high volatility.

To test VIX-bias statistically, we again employ a bootstrapping approach. In addition to the overall sample, three sub-sample periods are defined by 2005-2007, 2008-2011, and 2012-2014, respectively. For each iteration, we select randomly 700 (out of 754), 900 (out of 1008), 500 (out of 600) and 2000 (out of 2362) daily observations from the three sub-samples (2005-2007, 2008-2011 and 2012-2014) as well as the overall sample, respectively. The sample mean of the VIX-bias and its associated Z-statistic are then calculated. We repeat this procedure 10,000 times and compute the average of means and that of Z-statistics. Table 40.2 reports testing results of two measures: the mean difference between GVIX and VIX ($\widehat{GVIX}_a - \widehat{VIX}_a$) as well as that between VIX and the second return-moment ($\widehat{VIX}_a - \sqrt{\hat{V}_a}$). It appears that VIX statistically understates the return-volatility on average. The sample mean of ($\widehat{GVIX}_a - \widehat{VIX}_a$) ranges from 22 to 83 index basis points (BP), and that of ($\widehat{VIX}_a - \sqrt{\hat{V}_a}$) has a value from −86 to −26 index BP. The Z-value of all estimates is considerably large indicating that the mean deviation of VIX from the return-volatility is statistically and strongly significant. We note that the VIX-bias during the period of highly volatile markets (2008-2011) was much higher than that during other time periods. In addition, since from equation (40.24), the VIX-bias is theoretically driven by high moments, we also report, in Table 40.2, the average value of $\frac{1}{3}\hat{W}_a$ and that of $\frac{1}{12}\hat{X}_a$ as well as their test statistics. It shows that all test statistics are highly significant indicating all estimates of the high moments are different from zero. The third-moment was largely negative and reached an extreme value of −82.76 during the period of (2008-2011). Although the fourth-moment provides some contribution to the VIX-bias, the impact was much smaller than that of the third-moment. In summary, Table 40.2 shows that the negative third-moment could be the main reason for the downward bias of VIX in estimating ex ante volatility.

Corresponding to Figure 40.1, Table 40.3 reports correlations of VIX-bias to the return-moments. The VIX-bias appears to be highly correlated with all three return-moments: $\hat{V}_a$, $\hat{W}_a$, and $\hat{X}_a$. The negative correlation between VIX-bias and $\hat{W}_a$ is particularly large (about 97%) and is consistent across all sample periods. The second return-moment ($\hat{V}_a$) is also negatively and almost perfectly correlated with the third return-moment ($\hat{W}_a$). This indicates that the non-positive skewness of returns becomes more negative as market volatility rises. Note that the VIX index itself is highly correlated with the market volatility as well. Therefore, one would expect that the downward VIX-bias could increase as the value of VIX rises. We illustrate this phenomenon in Figure 40.2.

## Table 40.2: The average VIX-biases and ex ante high moments.

|  | 2005-2007 | 2008-2011 | 2012-2014 | Overall |
|---|---|---|---|---|
| *No. of days* | 754 | 1008 | 600 | 2362 |
| $\widehat{\text{GVIX}}_a - \widehat{\text{VIX}}_a$ | 0.22 (41.38)* | 0.83 (29.59)* | 0.28 (54.91)* | 0.49 (35.24)* |
| $\widehat{\text{VIX}}_a - \sqrt{\hat{V}_a}$ | -0.26 (-54.77)* | -0.86 (-28.95)* | -0.29 (-54.53)* | -0.52 (-35.68)* |
| $\frac{1}{3}\hat{W}_a$ | -7.09 (-21.96)* | -82.76 (-15.72)* | -10.42 (-35.70)* | -40.24 (-16.41)* |
| $\frac{1}{12}\hat{X}_a$ | 0.61 (14.97)* | 18.38 (10.92)* | 0.90 (26.20)* | 8.27 (10.84)* |

Notes: This table reports the bootstrapped means (Z-statistics) of the difference between annualized (extrapolated) VIX calculated from daily option premiums and the annualized GVIX as well as the second return-moment ($V_a$), respectively. In addition, the estimates of ex ante third and fourth-moment ($\hat{W}_a$, and $\hat{X}_a$) are presented in this table. Note that $\widehat{\text{GVIX}}_a$ measures the ex ante standard deviation of log-return (the true volatility) as shown in equations (40.20) and (40.27). Also, from (40.24), $(\text{VIX}^2 - \text{GVIX}^2) \approx \frac{1}{T}(\mu_T^2 + \frac{W_T}{3} + \frac{X_T}{12})$. For each iteration, we select randomly 700 (out of 754), 900 (out of 1008), 500 (out of 600) and 2000 (out of 2362) daily observations from the three sub-periods, 2005-2007, 2008-2011 and 2012-2014 as well as the overall period, respectively. The sample mean and its associated Z-statistic are then calculated. We repeat this procedure 10,000 times and compute the average of means and that of Z-statistics. The numbers in parenthesis are average Z-statistics. Daily option premiums over a period from January 2005 to May 2014 are used for the calculation. * denotes significantly different from zero at the 1% level.

To show the descending bias of VIX, we plot the VIX deviations from the true volatility (GVIX) on the y-axis and the corresponding VIX values (sorted from the minimum value of 9.87 to the maximum value of 80.70) on the x-axis. Figure 40.2 shows that the downward bias of VIX is quite significant, and the VIX undervaluation accelerates as VIX values increase. Importantly, the magnitude of this acceleration dramatically enlarges as the VIX values reach 30 and above. This accentuates a major drawback of the VIX index that frequently serves as an “investor fear gauge”. It has been widely viewed that VIX values greater than 30 are generally associated with a large amount of volatility as a result of investor fear, while values below 20 generally correspond to less stressful times in the markets. Corresponding to the appearance of Figure 40.2, we report concisely the distribution of the VIX-bias according to three levels of VIX values: VIX < 30, 30 ≤ VIX < 50, and VIX > 50, respectively. The median bias increases from 28 to 126 index BP when VIX index value rises from below 30 to above 30. The median bias for VIX values above 50 even reaches 338 index BP. Furthermore, to

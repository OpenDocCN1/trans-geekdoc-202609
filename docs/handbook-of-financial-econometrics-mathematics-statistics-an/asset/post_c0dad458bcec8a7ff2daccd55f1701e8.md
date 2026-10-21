
## Table 96.3: Payout ratios partitioned by growth rate and risks.

### Panel A. Payout ratios partitioned by growth rate

|  |  | Low growth |  |  |  | High growth |
|  |  | 1 | 2 | 3 | 4 | 5 |
| All Sample | Mean | 0.4864 | 0.3835 | 0.3272 | 0.2696 | 0.2213 |
|  | Median | 0.4835 | 0.3795 | 0.3196 | 0.2556 | 0.1967 |

### Panel B. Payout ratios partitioned by beta risk

|  |  | Low beta |  |  |  | High beta |
|  |  | 1 | 2 | 3 | 4 | 5 |
| All Sample | Mean | 0.3912 | 0.3940 | 0.3963 | 0.3609 | 0.3371 |
|  | Median | 0.3716 | 0.3765 | 0.3737 | 0.3328 | 0.3009 |
| High-Growth Firms | Mean | 0.3173 | 0.3229 | 0.3204 | 0.3025 | 0.2886 |
|  | Median | 0.3027 | 0.3081 | 0.3028 | 0.2874 | 0.2588 |
| Low-Growth Firms | Mean | 0.6115 | 0.6064 | 0.6182 | 0.6189 | 0.6292 |
|  | Median | 0.5864 | 0.5748 | 0.5947 | 0.6042 | 0.6090 |

### Panel C. Payout ratios partitioned by total risk

|  |  | Low total risk |  |  |  | High total risk |
|  |  | 1 | 2 | 3 | 4 | 5 |
| All Sample | Mean | 0.4274 | 0.4058 | 0.3618 | 0.3285 | 0.3041 |
|  | Median | 0.4099 | 0.3808 | 0.3333 | 0.2899 | 0.2588 |
| High-Growth Firms | Mean | 0.3499 | 0.3286 | 0.2957 | 0.2698 | 0.2531 |
|  | Median | 0.3381 | 0.3138 | 0.2745 | 0.2431 | 0.2190 |
| Low-Growth Firms | Mean | 0.6078 | 0.6202 | 0.6269 | 0.6091 | 0.6115 |
|  | Median | 0.5732 | 0.5942 | 0.6062 | 0.5863 | 0.6025 |

Notes: This table presents the average and the median payout ratios in different groups partitioned by growth rate, beta risk, or total risk during the sample period from 1969 to 2009. Panel A reports the average and the median payout ratios by one-way sort on the growth rate. Panel B reports the average and the median payout ratios by independent two-way sort on the growth rate and the beta. Panel C reports the average and the median payout ratios by independent two-way sort on the growth rate and the total risk. High-growth firm years are defined as firm years with sustainable growth rates higher than their rates of return on assets. Low-growth firm years are defined as firm years with sustainable growth rates lower than their rate of return on assets.

In the regression, the dependent variable is the logistic transformation of the payout ratio. Independent variables include risk measure (beta coefficient or total risk), the interaction of dummy variable and risk measure, growth rate, the interaction of risk measure and growth rate, log of size, and rate of return on total assets.¹⁶ Based upon the theoretical model and its implications from Section 96.6, we assume that *c* is equal to 1. The dummy variable (*Dᵢ*) is equal to 1 if a firm’s five-year average growth rate is less than its five-year average rate of return on assets and 0 otherwise. Such structure allows us to analyze the relationship between payout ratio and growth rate and the relationship between payout ratio and risk under different growth rate levels.

Thompson (2010), Peterson (2009), and Cameron *et al.* (2006) have pointed out that standard errors of two-way fixed-effects estimates can be biased if two-dimensional clustering (clustering in the cross-sectional errors and clustering in time-series errors) is not controlled for. Thompson (2010) and Boehmer *et al.* (2010) have empirically found that these clustering effects are not important for large samples.

The robust standard errors are very similar to standard errors for ordinary least square (OLS), suggesting that the fixed effects and control variables are removing most of the correlation that is persistent across observations. In addition, our dataset cannot be meaningfully applied to the clustering effect model¹⁷; therefore, statistical inferences in this paper are conducted using fixed-effects standard errors.

Table 96.4 provides the results of fixed-effects regressions for 2,645 firms during the period 1969–2009.

¹⁶Besides merely adding an interaction dummy as indicated in equation (96.36), we include an intercept dummy to take care of the individual effect of two groups. We also run regressions for high-growth firms and low-growth firms separately. Results from both models are qualitatively the same as those from equation (96.36) and also support Hypotheses 1–3.

¹⁷Because our sample is an unbalanced panel data, the clustering computer program cannot meaningfully estimate the variance components, variance of firm (V̂_firm), variance of time (V̂_time), and heteroscedasticity-robust OLS variance (V̂_white).

## Table 96.4: Fixed-effects regressions using theoretical structural change point.

| Model | Intercept | Beta | D*Beta | Growth* beta | Total risk | D*Total risk | Growth* total risk | Growth | ln (size) | ROA | Adj-R² | F-test (p-value) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| (1) | 0.32*** (2.70) | -0.18*** (-9.82) |  |  |  |  |  | -0.03*** (-4.85) | 0.04*** (3.76) | -13.24*** (-63.14) | 0.1945 |  |
| (2) | 0.45*** (3.76) |  |  |  | -17.47*** (-14.64) |  |  | -0.03*** (-4.68) | 0.02** (2.10) | -13.07*** (-62.42) | 0.1982 |  |
| (3) | 0.31*** (2.64) | -0.14*** (-7.76) |  | -0.29*** (-8.84) |  |  |  | 0.09*** (6.38) | 0.04*** (3.47) | -12.96*** (-61.17) | 0.1970 |  |
| (4) | 0.45*** (3.77) |  |  |  | -17.14*** (-13.13) |  | -2.90 (-0.63) | <0.01 (0.01) | 0.02** (2.06) | -13.06*** (-61.97) | 0.1982 |  |
| (5) c =1 | 0.33*** (2.94) | -0.23*** (-13.88) | 0.71*** (57.57) |  |  |  |  | -0.02*** (-3.70) | 0.002 (0.21) | -11.54*** (-57.83) | 0.2867 | <0.01 |
| (6) c =1 | 0.52*** (4.58) |  |  |  | -27.81*** (-24.15) | 63.35*** (52.23) |  | -0.02*** (-3.53) | -0.002 (-0.27) | -11.40*** (-56.55) | 0.2753 | <0.01 |
| (7) c =1 | 0.32*** (2.91) | -0.22*** (-12.69) | 0.70*** (56.96) | -0.13*** (-4.02) |  |  |  | 0.03*** (2.35) | -0.001 (-0.10) | -11.43*** (-56.76) | 0.2871 | <0.01 |
| (8) c =1 | 0.51*** (4.53) |  |  |  | -29.61*** (-23.44) | 63.68*** (52.35) | 15.30*** (3.46) | -0.16*** (-3.89) | -0.001 (-0.06) | -11.47*** (-56.63) | 0.2756 | <0.01 |

Notes: *, **, and *** indicate significance at the 10%, 5%, and 1% levels, respectively. This table presents results from fixed-effects regressions of dividend payout ratios on firm characteristics for 2,645 firms during the period from 1969 to 2009. The regressions are as follows:

ln( payout ratio_i,t / (1 - (payout ratio_i,t)) ) = α + β1 Risk_i,t + β2 D(g_i,t < c · ROA_i,t) · Risk_i + β3 Growth_i,t + β4 Risk_i,t × Growth_i,t + β5 ln(Size)_i,t + β6 ROA_i,t + e_i,t.

The dependent variable is the payout ratio with a logistic transformation. Following the theoretical model, we assume c is equal to 1. The dummy variable is equal to 1 if a firm's 5-year average growth rate is less than its 5-year average ROA and 0 otherwise. The independent variables are beta risk (total risk), dummy times beta risk (total risk), interaction between growth rate and beta risk (total risk), growth rate, log of size, and the rate of return on assets. t-statistics are presented in parentheses, and the last column presents p-values of the F-test on the null hypothesis that the restricted Models (1)-(4) are not different from the unrestricted Models (5)-(8).

*Models* (1) and (2) show that the estimated coefficients of the growth rate are −0.03 with a *t*-statistics of −4.85 and −0.03 with a *t*-statistics of −4.85, respectively. Such significantly negative coefficients confirm Hypothesis 1, which states that high-growth firms will pay less in dividends for the consideration of flexibility. We also include an interaction term of risk and growth rate into *Models* (3) and (4). The results in *Models* (3) and (4) also support Hypothesis 1.

*Models* (1)–(4) show that the relationship between the payout ratio and the risk is significantly negative. The results are similar to the findings of Rozeff (1982), Jagannathan et al. (2000), and Grullon et al. (2002), indicating that dividend payouts are negatively correlated to firm risks, but our theoretical model shows that if firms follow their optimal dividend payout policy, the relationship between dividend payouts and firm risks depends on their growth rates relative to their rate of return on total assets as our theoretical analysis presented in Section 96.6. In Table 96.2, we find the number of firms with a higher growth rate with respect to their rate of return on assets is greater than the number of firms with a lower growth rate with respect to their rates of return on assets. When pooling high-growth firms and low-growth firms together, the negative risk effect of high-growth firms will dominate the positive risk effect of low-growth firms due to the larger proportion of high-growth firms in the observations. The results of the negative relationship between the payout ratio and the risk shown in Models (1)–(4) may therefore result from the greater proportion of high-growth firms. Based on our subsequent analysis, the effect of growth rates on dividend payout policies can be more accurately found when firms are separated into high-growth firms and low-growth firms relative to their rates of return on total assets.

To test Hypotheses 2 and 3, we introduce an interaction term of the dummy variable and the risk. In Models (5) and (6), the estimated coefficients of risk are −0.23 with a t-statistics of −13.88 and −0.22 with a t-statistics of −12.69, respectively. The significantly negative coefficients support Hypothesis 2 that, because of the consideration of flexibility, the payout ratio and the risk are negatively correlated for firms with a higher growth rate relative to their rate of return on assets. In addition, significant and positive coefficients of the interaction term of the dummy variable and the risk indicate that, when the risk changes, the dividend policy for low-growth firms is different from that of high-growth firms. By summing the coefficient of risk and the coefficient of interaction term, we can obtain coefficients of 0.48 and 35.54 for beta and total risk, respectively, indicating the relationship between the payout ratio and the risk for low-growth firms is positive. That is, when the risk increases, low-growth firms will follow their optimal payout policies to increase their dividend payouts. Hypothesis 3 is thus confirmed in our empirical work. Blau and Fuller (2008) find that the flexibility hypothesis is more suitable than the free cash flow hypothesis to explain the dividend policy, but their method cannot separate the dividend policy decisions between high-growth firms and low-growth firms. Consequently, the model used in this paper can be regarded as a generalization of their results.

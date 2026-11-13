# TABLE 15.1: Significant predictors in the training sample.

| term | estimate | std.error | statistic | p.value |
|---|---|---|---|---|
| (Intercept) | 0.0405741 | 0.0053427 | 7.594323 | 0.0000000 |
| Ebitda_Margin | 0.0132374 | 0.0034927 | 3.789999 | 0.0001507 |
| Ev_Ebitda | 0.0068144 | 0.0022563 | 3.020213 | 0.0025263 |
| Fa_Ci | 0.0072308 | 0.0023465 | 3.081471 | 0.0020601 |
| Fcf_Bv | 0.0250538 | 0.0051314 | 4.882465 | 0.0000010 |
| Fcf_Yld | -0.0158930 | 0.0037359 | -4.254126 | 0.0000210 |
| Mkt_Cap_12M_Usd | 0.2047383 | 0.0274320 | 7.463476 | 0.0000000 |
| Mkt_Cap_6M_Usd | -0.1797795 | 0.0459390 | -3.913443 | 0.0000910 |
| Mom_5M_Usd | -0.0186690 | 0.0044313 | -4.212972 | 0.0000252 |
| Mom_Sharp_11M_Usd | 0.0178174 | 0.0046948 | 3.795131 | 0.0001476 |
| Ni | 0.0154609 | 0.0044966 | 3.438361 | 0.0005854 |
| Ni_Avail_Margin | 0.0118135 | 0.0038614 | 3.059359 | 0.0022184 |
| Ocf_Bv | -0.0198113 | 0.0052939 | -3.742277 | 0.0001824 |
| Pb | -0.0178971 | 0.0031285 | -5.720637 | 0.0000000 |
| Pe | -0.0089908 | 0.0023539 | -3.819565 | 0.0001337 |
| Sales_Ps | -0.0157856 | 0.0046278 | -3.411062 | 0.0006472 |
| Vol1Y_Usd | 0.0114250 | 0.0027923 | 4.091628 | 0.0000429 |
| Vol3Y_Usd | 0.0084587 | 0.0027952 | 3.026169 | 0.0024771 |

In fact, there are several indicators for the market capitalization and maybe only one would suffice, but it is not obvious to tell which one is the best choice.

To further depict correlation issues, we compute the correlation matrix of the predictors below (on the training sample). Because of its dimension, we show it graphically. As there are too many labels, we remove them.

```
library(corrplot)             # Package for plots of correlation matrices
C <- cor(training_sample %>% dplyr::select(features)) # Correlation matrix
corrplot(C, tl.pos='n')       # Plot
```

The graph of Figure 15.1 reveals several blue squares around the diagonal. For instance, the biggest square around the first third of features relates to all accounting ratios based on free cash flows. Because of this common term in their calculation, the features are naturally highly correlated. These local correlation patterns occur several times in the dataset and explain why it is not a good idea to use simple regression with this set of features.

In full disclosure, multicollinearity (when predictors are correlated) can be much less a problem for ML tools than it is for pure statistical inference. In statistics, one central goal is to study the properties of β coefficients. Collinearity perturbs this kind of analysis. In machine learning, the aim is to maximize out-of-sample accuracy. If having many predictors can be helpful, then so be it. One simple example can help clarify this matter. When building a regression tree, having many predictors will give more options for the splits. If the features make sense, then they can be useful. The same reasoning applies to random forests and boosted trees. What does matter is that the large spectrum of features helps improve the generalization ability of the model. Their collinearity is irrelevant.
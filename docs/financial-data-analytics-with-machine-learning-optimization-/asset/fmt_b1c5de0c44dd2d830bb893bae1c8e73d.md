
We have the same illustration via Python codes in [Programme 2.16](#c02.xhtml#c02-gra-00016) with histograms shown in [Figure 2.5](#c02.xhtml#c02-fig-0005) for the period 2005 to 2007 and [Figure 2.6](#c02.xhtml#c02-fig-0006) for 2018 to 2020, respectively.

![](images/c02-gra-0025.png)![FIGURE 2.5 Histograms of the daily logarithmic returns from 2005 to 2007 in Python.](images/c02f005.png)

[**FIGURE 2.5**](#c02.xhtml#R_c02-fig-0005) Histograms of the daily logarithmic returns from 2005 to 2007 in Python.

![FIGURE 2.6 Histograms of the daily logarithmic returns from 2018 to 2020 in Python.](images/c02f006.png)

[**FIGURE 2.6**](#c02.xhtml#R_c02-fig-0006) Histograms of the daily logarithmic returns from 2018 to 2020 in Python.

Next, in [Programme 2.17](#c02.xhtml#c02-gra-00017), we perform both one-way ANOVA and Tukey HSD tests in `R` for the period 2005 to 2007. The `aov()` function is used for performing one-way ANOVA with (i) a group variable `Index` which consists of three categories `SPX`, `HSI`, and `FTSE`; and (ii) a numerical response variable `log_return` for the daily logarithmic returns of the corresponding market index. The relatively large `p`-value (`0.152 > 0.05`) of the ANOVA test indicates that we fail to reject the null hypothesis of the equality of all means of `μ_SPX`, `μ_FTSE` and `μ_HSI` over the period 2005 to 2007. This claim is further supported by the large `p`-values of the Tukey HSD tests on all three possible pairs of stock market indices via the `TukeyHSD()` function in `R`, as there are three stock market indices, and there are `3 choose 2 = 3` possible pairs. More graphical illustrations can be seen in [Figure 2.7](#c02.xhtml#c02-fig-0007).

![](images/c02-gra-0026.png) ![FIGURE 2.7 Boxplot, meanplot, and Tukey HSD plot for three stock market indices from 2005 to 2007 in R.](images/c02f007.png)

[**FIGURE 2.7**](#c02.xhtml#R_c02-fig-0007) Boxplot, meanplot, and Tukey HSD plot for three stock market indices from 2005 to 2007 in `R`.

However, over the period 2018 to 2020, using [Programme 2.18](#c02.xhtml#c02-gra-00018) (written in `R`), the small `p`-value (`0.019 < 0.05`) from the ANOVA test indicates that we should reject the null hypothesis on the equality of all means, meaning that the corresponding population means `μ_SPX`, `μ_FTSE` and `μ_HSI` are not all equal. We further adopt the Tukey HSD tests to the three possible pairs of stock market indices to test which pair(s) of means are unequal. The corresponding small `p`-value (`0.0168939 ≪ 0.05`) of the Tukey HSD test for `HSI` against `SPX` indicates that the population means for `HSI` and `SPX` are unlikely the same, i.e. `μ_HSI ≠ μ_SPX`. Meanwhile, for the Tukey HSD test for `FTSE` against `HSI`, the large `p`-value (`0.7091423 ≫ 0.05`) indicates that we do not reject the equality of the means `μ_FTSE = μ_HSI`; the analogous conclusion of `μ_FTSE = μ_SPX` can also be drawn from the Tukey HSD test for `FTSE` against `SPX`, yet based on its relatively small `p`-value of 0.1226088 (`> 0.05`), it is more likely that the two means may be unequal. Indeed, the discrepancy between US and Hong Kong markets may be explained by the economic conflict between US and China throughout that period, which brought along uncertainty and concern on various prospects of the economic growth in Asia-Pacific region, including but not limited to tariff levels and trade negotiations. As a result, Chinese companies with a significant exposure to the US market were most severely affected, and the overall performance of the Hang Seng Index, where these companies played a crucial role, deviated inevitably from that of the S&P500 Index. We can also use the Sharpe ratio to study any possible differences between the performances of financial markets in different countries, for instance, see [[10](#c02.xhtml#c02-bib-0010), [11](#c02.xhtml#c02-bib-0011)].

![](images/c02-gra-0027.png)

From [Figure 2.8](#c02.xhtml#c02-fig-0008)b, the mean of the daily logarithmic returns for `SPX` is significantly higher than the corresponding means of `HSI`, which is in agreement with the result obtained from the Tukey HSD tests that `μ_HSI ≠ μ_SPX`. Certainly, there are limitations to our present study. For instance, we assume the stationarity of both the means and variance of log-returns over not too short periods. Since the economic environments over those periods were rather stable, one can argue this assumption is legitimate. Nevertheless, we shall introduce more sophisticated models allowing for more realistic assumptions later in [Chapters 3](#c03.xhtml), [7](#c07.xhtml) and [8](#c08.xhtml).

![FIGURE 2.8 Boxplot, meanplot, Tukey HSD plot for three stock market indices from 2018 to 2020 in R.](images/c02f008.png)

[**FIGURE 2.8**](#c02.xhtml#R_c02-fig-0008) Boxplot, meanplot, Tukey HSD plot for three stock market indices from 2018 to 2020 in `R`.

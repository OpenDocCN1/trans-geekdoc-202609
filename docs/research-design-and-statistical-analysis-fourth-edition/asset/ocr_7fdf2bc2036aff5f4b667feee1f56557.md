# Table 7.2 Shapiro–Wilk tests of normality for the memory data (from R)

| Condition | Statistic | df | Sig |
|---|---|---|--|
| Control | .905 | 25 | .023 |
| Drug | .892 | 25 | .012 |

![](bbox=[0.203, 0.219, 0.796, 0.609])

Figure 7.1 Q–Q plots of the memory data.

test of normality, which, loosely speaking, compares the variance of the data with the variance expected from rank-ordered data sampled from a normal distribution. In R, shapiro test in the [stats] package reveals that both conditions show significant departures from normality, with p-values less than .03 (see Table 7.2).

We can learn more about the distributions by examining the plots of the data. The Q–Q plots in Figure 7.1 confirm that the data are not normally distributed and indicate that this is largely attributable to several extreme scores, especially in the drug condition. This conclusion is subjective; there are no hard-and-fast rules for interpreting Q–Q plots. In this case, the extreme scores are evident in both panels because there are individual points that fall far above or below the line. To determine which of these are outliers in the technical sense (see Chapter 2), we turn to the box plots in Figure 7.2, which show the outliers as black dots (the gray dots are individual scores). These boxplots confirm that there are several outliers in the data set. The presence of outliers increases variability and reduces the power
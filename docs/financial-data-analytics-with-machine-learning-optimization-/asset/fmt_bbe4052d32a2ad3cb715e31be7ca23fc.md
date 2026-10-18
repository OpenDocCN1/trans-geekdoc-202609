
where `p<sub>ij</sub>` is the `p`-value of the single pairwise comparison of the groups `i` and `j`. Then we reject the null hypothesis of simultaneous equality of pairwise means across groups at a significant level `α` if `∑<sub>i,j</sub> p<sub>ij</sub> < α`.

Next, we shall illustrate the applications of one-way ANOVA and Tukey HSD for three stock market indices, namely the S&P500, HSI, and FTSE via both Python and `R`; note that for this particular example, we shall prioritize on elaborating the implementation in `R`, supplemented by their Python counterparts. The data files `SPX.csv`, `HSI.csv`, and `FTSE.csv` are the adjusted closing prices of S&P500, HSI, and FTSE respectively, dating from 4 January 1984 to 26 April 2021. In particular, two time periods of data will be analyzed, namely (i) from 2005 to 2007; and (ii) from 2018 to 2020.

![](images/c02-gra-0022.png)

For [Programme 2.13](#c02.xhtml#c02-gra-00013) in `R`, `as.Date()` function converts the date character string from the index name of the dataframe into a datetime object, in which the argument `format="%d/%m/%Y"` indicates that the input string has a date format of (two digits) / month (two digits) / year (four digits). After that, `format()` is immediately applied with an argument `"%Y"` indicating that only the year is returned, and this is augmented into the corresponding stock market index dataframe in a new column named as `Year`. The logarithmic return, i.e., the logarithm of the ratio of consecutive prices, is computed by the `log()` function, then taking the difference of consecutive terms via the `diff()` function. Note that the logarithmic return on the first day (4 January 1984) is unavailable because we do not have the adjusted closing price on the previous day. Therefore, we supplement at the beginning of the list of logarithmic return figures with `NA`, and we place it in the new column named `log_return`. We then remove the data on the very first day by using `[-1,]`.

For the `Remove_Outlier()` function (defined in `R` in [Programme 2.13](#c02.xhtml#c02-gra-00013) or in Python in [Programme 2.14](#c02.xhtml#c02-gra-00014)), we used the convention that any data points which are lower than the lower quartile minus 1.5 times the inter-quartile range or greater than the upper quartile plus 1.5 times the inter-quartile range are regarded as outliers. If each stock market index follows a standard normal distribution, then the 25% (resp. 75%) quantile represents a quantile value of −0.6745 (resp. 0.6745) under `N(0, 1)`. With a multiplier of 1.5 times of the interquartile range as the `outlier_factor`, the `lower_bound` (resp. `upper_bound`) represents the quantile value −0.6745 + 1.5 ⋅ (0.6745 − (−0.6745)) = −2.6960 (resp. 2.6960). Therefore, under `N(0, 1)`, we are selecting the middle portion of `Φ(2.6960) − Φ(−2.6960) = 0.9930`, where `Φ(⋅)` is the cumulative distribution function (cdf) of a standard normal distribution. Therefore, if the stock market index follows a heavier-tailed distribution than `N(0, 1)`, then the outliers account for roughly more than 1% of the dataset.

The equivalent code in Python is shown below:

![](images/c02-gra-0023.png)

Now, we extract the data from 2005 to 2007 and plot a histogram for the logarithmic returns of each cleansed stock market index. [Programme 2.15](#c02.xhtml#c02-gra-00015) contains the `R` code; [Programme 2.16](#c02.xhtml#c02-gra-00016) the Python.

![](images/c02-gra-0024.png)

Through various statistical tests (such as the Kolmogorov–Smirnov test) to be introduced in [Chapter 3](#c03.xhtml), we shall see in general that the logarithmic returns of stock market indices barely follow a normal distribution, except the central portion during fair weather days. Nevertheless, [Figure 2.3](#c02.xhtml#c02-fig-0003) and [Figure 2.5](#c02.xhtml#c02-fig-0005), produced via `R` and Python respectively, show that the histograms of the daily logarithmic returns for all three stock market indices having a bell-shaped distribution. Despite the lack of normality, as long as the underlying distribution is symmetric enough and light-tailed, the celebrated Central Limit Theorem can still warrant that the corresponding sample mean of log-returns of each index closely follows a normal distribution even with a small sample size, thanks to the Berry–Esseen bound [[1](#c02.xhtml#c02-bib-0001), [3](#c02.xhtml#c02-bib-0003)]. Therefore, the results of one-way ANOVA and Tukey HSD tests are still robust enough to cover the present comparative study.

![FIGURE 2.3 Histograms of the daily logarithmic returns from 2005 to 2007 in R.](images/c02f003.png)

[**FIGURE 2.3**](#c02.xhtml#R_c02-fig-0003) Histograms of the daily logarithmic returns from 2005 to 2007 in `R`.

![FIGURE 2.4 Histograms of the daily logarithmic returns from 2018 to 2020 in R.](images/c02f004.png)

[**FIGURE 2.4**](#c02.xhtml#R_c02-fig-0004) Histograms of the daily logarithmic returns from 2018 to 2020 in `R`.

[Figure 2.4](#c02.xhtml#c02-fig-0004) shows the results (from `R`) of replicating [Programme 2.15](#c02.xhtml#c02-gra-00015), but this time over a different time period, 2018 to 2020, via `start_year <- 2018` and `end_year <- 2020`.


where \( n \) is the number of data tuples, \( count(A = a_i) \) is the number of tuples having value \( a_i \) for \( A \), and \( count(B = b_j) \) is the number of tuples having value \( b_j \) for \( B \). The sum in Eq. (2.10) is computed over all of the \( r \times c \) cells. Note that the cells that contribute the most to the \( \chi^2 \) value are those for which the actual count is very different from that expected.

The \( \chi^2 \) statistic tests the hypothesis that \( A \) and \( B \) are *independent*, that is, there is no correlation between them. The test is based on a significance level, with \( (r - 1) \times (c - 1) \) degrees of freedom. We illustrate the use of this statistic in Example 2.14. If the hypothesis can be rejected, then we say that \( A \) and \( B \) are statistically correlated.

### Example 2.14. Correlation analysis of nominal attributes using \( \chi^2 \).

Suppose that a group of 1500 people was surveyed. The gender of each person was noted. Each person was polled as to whether his or her preferred type of reading material was fiction or nonfiction. Thus, we have two attributes, *gender* and *preferred_reading*. The observed frequency (or count) of each possible joint event is summarized in the contingency table shown in Table 2.2, where the numbers in parentheses are the expected frequencies. The expected frequencies are calculated based on the data distribution for both attributes using Eq. (2.11).

Using Eq. (2.11), we can verify the expected frequencies for each cell. For example, the expected frequency for the cell (*male*, *fiction*) is

\( e_{11} = \frac{count(male) \times count(fiction)}{n} = \frac{300 \times 450}{1500} = 90, \)

and so on. Notice that in any row, the sum of the expected frequencies must equal the total observed frequency for that row, and the sum of the expected frequencies in any column must also equal the total observed frequency for that column.

Using Eq. (2.10) for \( \chi^2 \) computation, we get

\( \chi^2 = \frac{(250 - 90)^2}{90} + \frac{(50 - 210)^2}{210} + \frac{(200 - 360)^2}{360} + \frac{(1000 - 840)^2}{840} = 284.44 + 121.90 + 71.11 + 30.48 = 507.93. \)

For this \( 2 \times 2 \) table, the degrees of freedom are \( (2 - 1) \times (2 - 1) = 1 \). For 1 degree of freedom, the \( \chi^2 \) value needed to reject the hypothesis at the 0.001 significance level is 10.828 (taken from the table of upper percentage points of the \( \chi^2 \) distribution, typically available from any textbook on statistics). Since our computed value is above this, we can reject the hypothesis that *gender* and *preferred_reading* are independent and conclude that the two attributes are (strongly) correlated for the given group of people.

**Table 2.2 Example 2.14's 2 x 2 contingency table data.**

| | Male | Female | Total |
|---|---|---|---|
| fiction | 250 (90) | 200 (360) | 450 |
| non_fiction | 50 (210) | 1000 (840) | 1050 |
| Total | 300 | 1200 | 1500 |

Note: Are gender and preferred_reading correlated?

## 2.2.4 Graphic displays of basic statistics of data

In this section, we study graphic displays of basic statistical descriptions. These include *quantile plots*, *quantile-quantile plots*, *histograms*, and *scatter plots*. Such graphs are helpful for the visual inspection of data, which is useful for data preprocessing. The first three of these show univariate distributions (i.e., data for one attribute), whereas scatter plots show bivariate distributions (i.e., involving two attributes).

### Quantile plot

A *quantile plot* is a simple and effective way to have a first look at a univariate data distribution. First, it displays all of the data for the given attribute (allowing a user to assess both the overall behavior and unusual occurrences). Second, it plots quantile information (see Section 2.2.2). Let \(x_i\), for \(i = 1\) to \(N\), be the data sorted in ascending order so that \(x_1\) is the smallest observation and \(x_N\) is the largest for some ordinal or numeric attribute \(X\). Each observation, \(x_i\), is paired with a percentage, \(f_i\), which indicates that approximately \(f_i \times 100\%\) of the data are below the value, \(x_i\). We say “approximately” because there may not be a value with exactly a fraction, \(f_i\), of the data below \(x_i\). Note that the 0.25 quantile corresponds to quartile \(Q_1\), the 0.50 quantile is the median, and the 0.75 quantile is \(Q_3\).

Let

\(f_i = \frac{i - 0.5}{N}.\) (2.12)

These numbers increase in equal steps of \(1/N\), ranging from \(\frac{1}{2N}\) (which is slightly above 0) to \(1 - \frac{1}{2N}\) (which is slightly below 1). On a quantile plot, \(x_i\) is graphed against \(f_i\). This allows us to compare different distributions based on their quantiles. For example, given the quantile plots of sales data for two different time periods, we can compare their \(Q_1\), median, \(Q_3\), and other \(f_i\) values at a glance.

### Example 2.15. Quantile plot.

Fig. 2.4 shows a quantile plot for the *unit price* data of Table 2.3.

![](img/90c930779c8f928df6ff4481fc59f9a3_68_0.png)

**FIGURE 2.4**
A quantile plot for the unit price data of Table 2.3.

| Unit price ($) | Count of items sold |
| :--- | :--- |
| 40 | 275 |
| 43 | 300 |
| 47 | 250 |
| ... | ... |
| 74 | 360 |
| 75 | 515 |
| 78 | 540 |
| ... | ... |
| 115 | 320 |
| 117 | 270 |
| 120 | 350 |

### Quantile-quantile plot

A quantile-quantile plot, or q-q plot, graphs the quantiles of one univariate distribution against the corresponding quantiles of another. It is a powerful visualization tool in that it allows the user to view whether there is a shift in going from one distribution to another.

Suppose that we have two sets of observations for the attribute or variable, unit price, taken from two different branch locations. Let x1, ..., xN be the data from the first branch, and y1, ..., yM be the data from the second, where each data set is sorted in ascending order. If M = N, the number of points in each set is the same, then we simply plot yi against xi, where yi and xi are both the (i - 0.5)/N quantiles of their respective data sets. If M < N (i.e., the second branch has fewer observations than the first), there can be only M points on the q-q plot. Here, yi is the (i - 0.5)/M quantile of the y data, which is plotted against the (i - 0.5)/M quantile of the x data. This computation typically involves interpolation.

### Example 2.16. Quantile-quantile plot.

Fig. 2.5 shows a quantile-quantile plot for unit price data of items sold at two branches of the online store during a given time period. Each point corresponds to the same quantile for each data set and shows the unit price of items sold at branch 1 vs. branch 2 for that quantile. (To aid comparison, the straight line represents the case where, for each given quantile, the unit price at each branch is the same. The darker points correspond to the data for Q1, the median, and Q3, respectively.)

We see, for example, that at Q1, the unit price of items sold at branch 1 was slightly less than that at branch 2. In other words, 25% of items sold at branch 1 were less than or equal to $60, whereas 25% of items sold at branch 2 were less than or equal to $64. At the 50th percentile (marked by the median, which is also Q2), we see that 50% of items sold at branch 1 were less than $78, whereas 50% of items sold at branch 2 were less than $85. In general, we note that there is a shift in the distribution of branch 1 with respect to branch 2 in that the unit prices of items sold at branch 1 tend to be lower than those at branch 2.

![](img/90c930779c8f928df6ff4481fc59f9a3_70_0.png)

**FIGURE 2.5**
A q-q plot for unit price data from two branches of the online store.

### Histograms

Histograms (or frequency histograms) are at least a century old and are widely used. “Histos” means pole or mast, and “gram” means chart, so a histogram is a chart of poles. Plotting histograms is a graphical method for summarizing the distribution of a given attribute, X. According to the number of poles desired in the chart, the range of values for X is partitioned into a set of disjoint consecutive subranges. The subranges, referred to as buckets or bins, are disjoint subsets of the data distribution for X. The range of a bucket is known as the width. Typically, the buckets are of equal width. For example, a price attribute with a value range of $1–$200 (rounded up to the nearest dollar) can be partitioned into subranges 1–20, 21–40, 41–60, and so on. For each subrange, a bar is drawn with a height that represents the total count of items observed within the subrange.

Please note that histogram is different from another popularly used graph representation called bar chart. Bar chart uses a set of bars (often separated with space) with X representing a set of categorical data, such as automobile_model or item_type, and the height of the bar (column) indicates the size of the group defined by the categories. On the other hand, histogram plots quantitative data with a range of X values grouped into bins or intervals. Histograms are used to show distributions (along X axis) while bar charts are used to compare categories. It is always appropriate to talk about the skewness of a histogram; that is, the tendency of the observations to fall more on the low end or the high end of the X axis. However, bar chart’s X axis does not have a low end or a high end; because the labels on the X axis are categorical—not quantitative. Thus, bars can be reordered in bar charts but not in histograms.

### Example 2.17. Histogram.

Fig. 2.6 shows a histogram for a data set on research award distribution for a region, where buckets (or bins) are defined by equal-width ranges representing $1000 increments, and the frequency is the number of research awards in the corresponding buckets. □

Although histograms are widely used, they may not be as effective as the quantile plot, q-q plot, and boxplot methods in comparing groups of univariate observations.

of the distribution, as shown in Table 4.12, where the outliers were flagged with an absolute zscore greater than 3 (the value column is hidden for the sake of this demonstration).

| Value | Zscore | Is outlier? |
|---|---|---|
| ... | 1.3 | NO |
| ... | 0.8 | NO |
| ... | 3.1 | YES |
| ... | -2.9 | NO |
| ... | -3.5 | YES |
| ... | 1.0 | NO |
| ... | 1.1 | NO |

Table 4.12 – Flagging outliers according to the zscore value

Two outliers were found in Table 4.12: row number three and row number five. Another way to find outliers in the data is by applying the box plot logic. When you look at a numerical variable, it is possible to extract many descriptive statistics from it, not only the mean, median, minimum, and maximum values, as you have seen previously. Another property that's present in data distributions is known as quantiles.

Quantiles are cut-off points that are established at regular intervals from the cumulative distribution function of a random variable. Those regular intervals, also known as q-quantiles, will be nearly the same size and will receive special names in some situations:

+   * The 4-quantiles are called quartiles.
+   * The 10-quantiles are called deciles.
+   * The 100-quantiles are called percentiles.

For example, the 20th percentile (of a 100-quantile regular interval) specifies that 20% of the data is below that point. In a box plot, you can use regular intervals of 4-quantiles (also known as quartiles) to expose the distribution of the data (Q1 and Q3), as shown in Figure 4.10.
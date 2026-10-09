# 22.4. Quick Check for Autocorrelation

```
pyplot.show()
```

Listing 22.1: Create a lag plot of the Minimum Daily Temperatures dataset.

Running the example plots the temperature data (t) on the x-axis against the temperature on the previous day (t-1) on the y-axis.

![](bbox=[0.09, 0.22, 0.85, 0.62])

Figure 22.1: Lag plot of the Minimum Daily Temperatures dataset.

We can see a large ball of observations along a diagonal line of the plot. It clearly shows a relationship or some correlation. This process could be repeated for any other lagged observation, such as if we wanted to review the relationship with the last 7 days or with the same day last month or last year. Another quick check that we can do is to directly calculate the correlation between the observation and the lag variable.

We can use a statistical test like the Pearson's correlation coefficient. This produces a number to summarize how correlated two variables are between -1 (negatively correlated) and +1 (positively correlated) with small values close to zero indicating low correlation and high values above 0.5 or below -0.5 showing high correlation.

Correlation can be calculated easily using the `corr()` function^2 on the DataFrame of the lagged dataset. The example below creates a lagged version of the Minimum Daily Temperatures dataset and calculates a correlation matrix of each column with other columns, including itself.

> ^2http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.corr.html
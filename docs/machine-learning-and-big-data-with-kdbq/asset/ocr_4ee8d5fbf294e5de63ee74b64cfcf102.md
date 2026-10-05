# Joins 137

We will now show a second – and more efficient – way to achieve the same result. Recall that aj will return the values of the lookup table as-of of the first table, i.e. the 'last valid' observation. In order to get the 'next valid' observation, we can shift the lookup values of the second table in order to receive the next value when we perform the aj. This can be written as:

```
dataCombined: aj[`time; dataSet1; update next2 from dataSet2`
```

And the result is the same (and faster) in the previous method. By finishing our hypothesis about dataSet1 Granger-causing trades dataSet2, we can test the simplified Granger causality by running the correlation between trade1 and trade2 as variables are properly linked, i.e. entry trade2 is the successor of entry1 within the same row. Besides, the Granger causality is based on a linear regression model and in the case of two variables, the problem is equivalent to finding a significant correlation coefficient.

We implement the Granger causality test for trades by first calculating the correlation coefficient between the two columns trade1 and trade2:

```
correlation: exec trade1 trade2 from dataSetCombined
```

and, second, assessing the statistical significance of the estimated coefficient. In other words, we want to determine whether the estimated number is statistically significant from zero or not. This can be done by calculating the t-statistic of:

> $t = \rho \sqrt{rac{N-2}{1-\rho^2}} \quad (7.1)$

where $N$ is number of observations and $\rho$ is the estimated correlation coefficient, correlation. The t-statistic reads:

```
.quantQ.join.tStatsCorr:[rho;N]
// rho -- correlation
// N -- size of sample
:rho*sqrt[(N-2)/1-rho*rho];
};
```

and applied on our data set:

```
.quantQ.join.tStatsCorr[correlation; count dataSetCombined]
```

```
1.84269
```

The corresponding p-value allows us to conclude that the correlation coefficient is not statistically significant from zero and there is no Granger causality link between trades – see Chapter 14 for the one of the Granger causality. This corresponds to the data generating process, where both data sets were independent
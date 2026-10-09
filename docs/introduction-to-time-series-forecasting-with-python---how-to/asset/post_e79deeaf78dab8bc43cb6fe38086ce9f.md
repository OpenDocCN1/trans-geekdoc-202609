
Running the example provides a number of summary statistics to review. Some observations from these statistics include:

- The number of observations (count) matches our data expectation, meaning we are handling the data correctly.
- The mean is about 500, which we might consider our level in this series.
- The standard deviation and percentiles suggest a reasonably tight spread around the mean.

|       |        |
| ----- | ------ |
| count | 69.000000 |
| mean  | 500.478261 |
| std   | 73.901685 |
| min   | 344.000000 |
| 25%   | 458.000000 |
| 50%   | 492.000000 |
| 75%   | 538.000000 |
| max   | 662.000000 |

Listing 31.7: Example output of summary statistics on the Baltimore Water Usage dataset.

### 31.5.2 Line Plot

A line plot of a time series dataset can provide a lot of insight into the problem. The example below creates and shows a line plot of the dataset.

```python
# line plot of time series
from pandas import read_csv
from matplotlib import pyplot
series = read_csv('dataset.csv', header=None, index_col=0, parse_dates=True, squeeze=True)
series.plot()
pyplot.show()
```

Listing 31.8: Create a line plot of the Baltimore Water Usage dataset.

Run the example and review the plot. Note any obvious temporal structures in the series. Some observations from the plot include:

- There looks to be an increasing trend in water usage over time.
- There do not appear to be any obvious outliers, although there are some large fluctuations.
- There is a downward trend for the last few years of the series.

![](img/da419ed7447ef051ee9d00167b7274cf_303_0.png)

Figure 31.1: Line plot of the training set for the Baltimore Water Usage dataset.

There may be some benefit in explicitly modeling the trend component and removing it. You may also explore using differencing with one or two levels in order to make the series stationary.

### 31.5.3 Density Plot

Reviewing plots of the density of observations can provide further insight into the structure of the data. The example below creates a histogram and density plot of the observations without any temporal structure.

```python
# density plots of time series
from pandas import read_csv
from matplotlib import pyplot
series = read_csv('dataset.csv', header=None, index_col=0, parse_dates=True, squeeze=True)
pyplot.figure(1)
pyplot.subplot(211)
series.hist()
pyplot.subplot(212)
series.plot(kind='kde')
pyplot.show()
```

Listing 31.9: Create a density plots of the Baltimore Water Usage dataset.

Run the example and review the plots. Some observations from the plots include:

- The distribution is not Gaussian, but is pretty close.
- The distribution has a long right tail and may suggest an exponential distribution or a double Gaussian.

![](img/da419ed7447ef051ee9d00167b7274cf_304_0.png)

This suggests it may be worth exploring some power transforms of the data prior to modeling.

### 31.5.4 Box and Whisker Plots

We can group the annual data by decade and get an idea of the spread of observations for each decade and how this may be changing. We do expect to see some trend (increasing mean or median), but it may be interesting to see how the rest of the distribution may be changing. The example below groups the observations by decade and creates one box and whisker plot for each decade of observations. The last decade only contains 9 years and may not be a useful comparison with the other decades. Therefore only data between 1885 and 1944 was plotted.

```python
# boxplots of time series
from pandas import read_csv
from pandas import DataFrame
from pandas import Grouper
from matplotlib import pyplot

series = read_csv('dataset.csv', header=None, index_col=0, parse_dates=True, squeeze=True)
groups = series.groupby(Grouper(freq='10YS'))
decades = DataFrame()
for name, group in groups:
    if len(group.values) is 10:
        decades[name.year] = group.values
decades.boxplot()
pyplot.show()
```

Listing 31.10: Create a box and whisker plots of the Baltimore Water Usage dataset.

Running the example creates 6 box and whisker plots side-by-side, one for the 6 decades of selected data. Some observations from reviewing the plot include:

- The median values for each year (red line) may show an increasing trend that may not be linear.
- The spread, or middle 50% of the data (blue boxes), does show some variability.
- There maybe outliers in some decades (crosses outside of the box and whiskers).
- The second to last decade seems to have a lower average consumption, perhaps related to the first world war.

![](img/da419ed7447ef051ee9d00167b7274cf_305_0.png)

Figure 31.3: Box and whisker plots of the training set for the Baltimore Water Usage dataset.

This yearly view of the data is an interesting avenue and could be pursued further by looking at summary statistics from decade-to-decade and changes in summary statistics.

## 31.6 ARIMA Models

In this section, we will develop Autoregressive Integrated Moving Average or ARIMA models for the problem. We will approach modeling by both manual and automatic configuration of the ARIMA model. This will be followed by a third step of investigating the residual errors of the chosen model. As such, this section is broken down into 3 steps:

1. Manually Configure the ARIMA.
2. Automatically Configure the ARIMA.
3. Review Residual Errors.

### 31.6.1 Manually Configured ARIMA

The *ARIMAp,d,q* model requires three parameters and is traditionally configured manually. Analysis of the time series data assumes that we are working with a stationary time series. The time series is likely non-stationary. We can make it stationary by first differencing the series and using a statistical test to confirm that the result is stationary. The example below creates a stationary version of the series and saves it to file *stationary.csv*.

```python
# create and summarize a stationary version of the time series
from pandas import read_csv
from pandas import Series
from statsmodels.tsa.stattools import adfuller
from matplotlib import pyplot

# create a differenced series
def difference(dataset):
  diff = list()
  for i in range(1, len(dataset)):
    value = dataset[i] - dataset[i - 1]
    diff.append(value)
  return Series(diff)

series = read_csv('dataset.csv', header=None, index_col=0, parse_dates=True, squeeze=True)
X = series.values
X = X.astype('float32')
# difference data
stationary = difference(X)
stationary.index = series.index[1:]
# check if stationary
result = adfuller(stationary)
print('ADF Statistic: %f' % result[0])
print('p-value: %f' % result[1])
print('Critical Values:')
for key, value in result[4].items():
 print('\t%s: %.3f' % (key, value))
# plot differenced data
stationary.plot()
pyplot.show()
# save
stationary.to_csv('stationary.csv', header=False)
```

Listing 31.11: Create a stationary version of the dataset and plot the differenced result.

Running the example outputs the result of a statistical significance test of whether the differenced series is stationary. Specifically, the augmented Dickey-Fuller test. The results show that the test statistic value -6.126719 is smaller than the critical value at 1% of -3.534. This suggests that we can reject the null hypothesis with a significance level of less than 1% (i.e. a low probability that the result is a statistical fluke). Rejecting the null hypothesis means that the process has no unit root, and in turn that the time series is stationary or does not have time-dependent structure.

```
ADF Statistic: -6.126719
p-value: 0.000000
Critical Values:
    5%: -2.906
    10%: -2.591
    1%: -3.534
```

Listing 31.12: Example output of a statistical test on the differenced Baltimore Water Usage dataset.

This suggests that at least one level of differencing is required. The $d$ parameter in our ARIMA model should at least be a value of 1. A plot of the differenced data is also created. It suggests that this has indeed removed the increasing trend.

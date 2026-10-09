# ## 13.2 Shampoo Sales Dataset

In this lesson, we will use the Shampoo Sales dataset as an example. This dataset describes the monthly number of sales of shampoo over a 3 year period. You can learn more about the dataset in Appendix **A.1**. Place the dataset in your current working directory with the filename `shampoo-sales.csv`.

# ## 13.3 Detrend by Differencing

Perhaps the simplest method to detrend a time series is by differencing. Specifically, a new series is constructed where the value at the current time step is calculated as the difference between the original observation and the observation at the previous time step.

$value(t) = observation(t) - observation(t - 1)$ (13.1)

This has the effect of removing a trend from a time series dataset. We can create a new difference dataset in Python by implementing this directly. A new list of observations can be created. Below is an example that creates the difference detrended version of the Shampoo Sales dataset.

```
# detrend a time series using differencing
from pandas import read_csv
from pandas import datetime
from matplotlib import pyplot

def parser(x):
    return datetime.strptime('190'+x, '%Y-%m')

series = read_csv('shampoo-sales.csv', header=0, index_col=0, parse_dates=True,
    squeeze=True, date_parser=parser)
X = series.values
diff = list()
for i in range(1, len(X)):
    value = X[i] - X[i - 1]
    diff.append(value)
pyplot.plot(diff)
pyplot.show()
```

**Listing 13.1:** Difference the Shampoo Sales dataset.

Running the example creates the new detrended dataset and then plots the time series. Because no difference value can be created for the first observation (there is nothing for it to be subtracted from), the new dataset contains one less record. We can see that indeed the trend does appear to have been removed (compared to original plot in the Appendix).
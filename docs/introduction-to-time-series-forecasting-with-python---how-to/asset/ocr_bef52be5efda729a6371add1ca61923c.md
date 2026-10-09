```
# calculate residuals from a persistence forecast
from pandas import read_csv
from pandas import DataFrame
from pandas import concat
series = read_csv('daily-total-female-births.csv', header=0, index_col=0, parse_dates=True, squeeze=True)
# create lagged dataset
values = DataFrame(series.values)
datframe = concat([values.shift(1), values], axis=1)
datframe.columns = ['t', 't+1']
# split into train and test sets
X = dataframe.values
train_size = int(len(X) * 0.66)
train, test = X[1:train_size], X[train_size:]
train_X, train_y = train[:,0], train[:,1]
test_X, test_y = test[:,0], test[:,1]
# persistence model
predictions = [x for x in test_X]
# calculate residuals
residuals = [test_y[i]-predictions[i] for i in range(len(predictions))]
residuals = DataFrame(residuals)
print(residuals.head())
```

Listing 19.5: Complete example of a persistence forecast on the Daily Female Births dataset.

Running the example prints the first 5 rows of the forecast residuals.

```
0    9.0
1   -10.0
2    3.0
3   -6.0
4   30.0
```

Listing 19.6: Example output of the first five forecast errors for the persistence forecast on the Daily Female Births dataset.

# 19.4 Residual Line Plot

The first plot is to look at the residual forecast errors over time as a line plot. We would expect the plot to be random around the value of 0 and not show any trend or cyclic structure. The array of residual errors can be wrapped in a Pandas `DataFrame` and plotted directly. The code below provides an example.

```
# line plot of residual errors
from pandas import read_csv
from pandas import DataFrame
from pandas import concat
from matplotlib import pyplot
series = read_csv('daily-total-female-births.csv', header=0, index_col=0, parse_dates=True, squeeze=True)
# create lagged dataset
values = DataFrame(series.values)
datframe = concat([values.shift(1), values], axis=1)
datframe.columns = ['t', 't+1']
```
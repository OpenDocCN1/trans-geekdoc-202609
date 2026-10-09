# 8.3. Log Transform

```
```python
pyplot.subplot(212)
pyplot.hist(transform)
pyplot.show()
```
```

Listing 8.6: Log transform of the exponential dataset.

Running the example creates plots, showing the expected linear result.

![](bbox=[0.17, 0.24, 0.81, 0.59])

Figure 8.6: Line and density plots of the log transformed exponential dataset.

Our Airline Passengers dataset has a distribution of this form, but perhaps not this extreme. The example below demonstrates a log transform of the Airline Passengers dataset.

```
```python
# log transform a time series
from pandas import read_csv
from pandas import DataFrame
from numpy import log
from matplotlib import pyplot
series = read_csv('airline-passengers.csv', header=0, index_col=0, parse_dates=True, squeeze=True)
dataframe = DataFrame(series.values)
dataframe.columns = ['passengers']
dataframe['passengers'] = log(dataframe['passengers'])
pyplot.figure(1)
# line plot
pyplot.subplot(211)
```
```
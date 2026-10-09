# ## 12.4 Automatic Time Series Decomposition

There are methods to automatically decompose a time series. The Statsmodels library provides an implementation of the naive, or classical, decomposition method in a function called seasonal\_decompose(). It requires that you specify whether the model is additive or multiplicative.

Both will produce a result and you must be careful to be critical when interpreting the result. A review of a plot of the time series and some summary statistics can often be a good start to get an idea of whether your time series problem looks additive or multiplicative. The seasonal\_decompose() function returns a result object. The result object contains arrays to access four pieces of data from the decomposition.

For example, the snippet below shows how to decompose a series into trend, seasonal, and residual components assuming an additive model. The result object provides access to the trend and seasonal series as arrays. It also provides access to the residuals, which are the time series after the trend, and seasonal components are removed. Finally, the original or observed data is also stored.

```
```
from statsmodels.tsa.seasonal import seasonal_decompose
series = ...
result = seasonal_decompose(series, model='additive')
print(result.trend)
print(result.seasonal)
print(result.resid)
print(result.observed)
```
```

Listing 12.1: Example of decomposing a time series.

These four time series can be plotted directly from the result object by calling the plot() function. For example:

```
```
from statsmodels.tsa.seasonal import seasonal_decompose
from matplotlib import pyplot
series = ...
result = seasonal_decompose(series, model='additive')
result.plot()
pyplot.show()
```
```

Listing 12.2: Example of plotting a decomposed time series.

Let's look at some examples.

# ### 12.4.1 Additive Decomposition

We can create a time series comprised of a linearly increasing trend from 1 to 99 and some random noise and decompose it as an additive model. Because the time series was contrived and was provided as an array of numbers, we must specify the frequency of the observations (the freq=1 argument). If a Pandas Series object is provided, this argument is not required.

```
```
# additive decompose a contrived additive time series
from random import randrange
from matplotlib import pyplot
```
```
```
```python
from statsmodels.tsa.seasonal import seasonal_decompose
series = [i+randrange(10) for i in range(1,100)]
result = seasonal_decompose(series, model='additive', freq=1)
result.plot()
pyplot.show()
```
```

Listing 12.3: Example of decomposing a contrived additive time series.

Running the example creates the series, performs the decomposition, and plots the 4 resulting series. We can see that the entire series was taken as the trend component and that there was no seasonality.

![](bbox=[0.13, 0.27, 0.87, 0.68])

We can also see that the residual plot shows zero. This is a good example where the naive, or classical, decomposition was not able to separate the noise that we added from the linear trend. The naive decomposition method is a simple one, and there are more advanced decompositions available, like Seasonal and Trend decomposition using Loess or STL decomposition. Caution and healthy skepticism is needed when using automated decomposition methods.

# 12.4.2 Multiplicative Decomposition

We can contrive a quadratic time series as a square of the time step from 1 to 99, and then decompose it assuming a multiplicative model.
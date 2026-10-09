# 8.2. Square Root Transform

squared series is linear, we would expect the histogram to show a uniform distribution. The example below performs a $\sqrt{}$ transform on the time series and plots the result.

```
```python
# square root transform a contrived quadratic time series
from matplotlib import pyplot
from numpy import sqrt
series = [i**2 for i in range(1,100)]
# sqrt transform
transform = series = sqrt(series)
pyplot.figure(1)
# line plot
pyplot.subplot(211)
pyplot.plot(transform)
# histogram
pyplot.subplot(212)
pyplot.hist(transform)
pyplot.show()
```
```

Listing 8.3: Square root transform of the quadratic series.

We can see that, as expected, the quadratic trend was made linear.

![](bbox=[0.18, 0.43, 0.82, 0.78])

Figure 8.3: Line and density plots of the square root transformed quadratic series dataset.

It is possible that the Airline Passengers dataset shows a quadratic growth. If this is the case, then we could expect a square root transform to reduce the growth trend to be linear
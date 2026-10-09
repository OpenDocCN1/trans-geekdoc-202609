![](bbox=[0.18, 0.13, 0.8, 0.49])

Figure 8.4: Line and density plots of the square root transformed Airline Passengers dataset.

# 8.3 Log Transform

A class of more extreme trends are exponential, often graphed as a hockey stick. Time series with an exponential distribution can be made linear by taking the logarithm of the values. This is called a log transform. As with the square and square root case above, we can demonstrate this with a quick example. The code below creates an exponential distribution by raising the numbers from 1 to 99 to the value e, which is the base of the natural logarithms or Euler’s number $(2.718\dots)$\[^1].

```
# create and plot an exponential time series
from matplotlib import pyplot
from math import exp
series = [exp(i) for i in range(1,100)]
pyplot.figure(1)
# line plot
pyplot.subplot(211)
pyplot.plot(series)
# histogram
pyplot.subplot(212)
pyplot.hist(series)
```

\[^1\] https://en.wikipedia.org/wiki/(E_(mathematical_constant)
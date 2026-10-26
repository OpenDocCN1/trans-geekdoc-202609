The complete example of reviewing the test function that we wish to optimize is listed below.

```
# example of the test problem
from math import sin
from math import pi
from numpy import arange
from numpy import argmax
from numpy.random import normal
from matplotlib import pyplot

# objective function
def objective(x, noise=0.1):
    noise = normal(loc=0, scale=noise)
    return (x**2 * sin(5 * pi * x)**6.0) + noise

# grid-based sample of the domain [0,1]
X = arange(0, 1, 0.01)
# sample the domain without noise
y = [objective(x, 0) for x in X]
# sample the domain with noise
ynoise = [objective(x) for x in X]
# find best result
ix = argmax(y)
print('Optima: x=%.3f, y=%.3f' % (X[ix], y[ix]))
# plot the points with noise
pyplot.scatter(X, ynoise)
# plot the points without noise
pyplot.plot(X, y)
# show the plot
pyplot.show()
```

Listing 19.7: Example plotting samples of the objective function.

Running the example first reports the global optima as an input with the value 0.9 that gives the score 0.81.

```
Optima: x=0.900, y=0.810
```

Listing 19.8: Example output from the optima from sampling the objective function.

A plot is then created showing the noisy evaluation of the samples (dots) and the non-noisy and true shape of the objective function (line). Your specific dots will differ given the stochastic nature of the noisy objective function.
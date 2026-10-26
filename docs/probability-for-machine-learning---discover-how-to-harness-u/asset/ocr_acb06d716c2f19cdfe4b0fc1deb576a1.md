```
...
# generate a sample
X1 = normal(loc=20, scale=5, size=3000)
X2 = normal(loc=40, scale=5, size=7000)
X = hstack((X1, X2))
```

Listing 14.1: Example of generating a sample from a bimodal probability distribution.

We can then plot a histogram of the points to give an intuition for the dataset. We expect to see a bimodal distribution with a peak for each of the means of the two distributions. The complete example is listed below.

```
# example of a bimodal constructed from two gaussian processes
from numpy import hstack
from numpy.random import normal
from matplotlib import pyplot
# generate a sample
X1 = normal(loc=20, scale=5, size=3000)
X2 = normal(loc=40, scale=5, size=7000)
X = hstack((X1, X2))
# plot the histogram
pyplot.hist(X, bins=50, density=True)
pyplot.show()
```

Listing 14.2: Example of generating and plotting a bimodal data sample.

Running the example creates the dataset and then creates a histogram plot for the data points. The plot clearly shows the expected bimodal distribution with a peak for the first process around 20 and a peak for the second process around 40. We can see that for many of the points in the middle of the two peaks that it is ambiguous as to which distribution they were drawn from.
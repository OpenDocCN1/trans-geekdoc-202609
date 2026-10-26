```
```python
# example of a bimodal data sample
from matplotlib import pyplot
from numpy.random import normal
from numpy import hstack
# generate a sample
sample1 = normal(loc=20, scale=5, size=300)
sample2 = normal(loc=40, scale=5, size=700)
sample = hstack((sample1, sample2))
# plot the histogram
pyplot.hist(sample, bins=50)
pyplot.show()
```
```

Listing 10.10: Example of generating and plotting a bimodal data sample.

Running the example creates the data sample and plots the histogram. Note that your results will differ given the random nature of the data sample. Try running the example a few times. We have fewer samples with a mean of 20 than samples with a mean of 40, which we can see reflected in the histogram with a larger density of samples around 40 than around 20. Data with this distribution does not nicely fit into a common probability distribution, by design. It is a good case for using a nonparametric kernel density estimation method.

![](bbox=[0.18, 0.47, 0.8, 0.8])

Figure 10.4: Histogram Plot of Data Sample With a Bimodal Probability Distribution.

The scikit-learn machine learning library provides the KernelDensity class that implements
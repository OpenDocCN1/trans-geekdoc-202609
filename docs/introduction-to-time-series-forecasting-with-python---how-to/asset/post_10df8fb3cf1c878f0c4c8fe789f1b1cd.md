
![](img/da419ed7447ef051ee9d00167b7274cf_103_0.png)

Figure 10.3: Correlogram plot of white noise series.

For completeness, the complete code listing is provided below.

```python
# calculate and plot a white noise series
from random import gauss
from random import seed
from pandas import Series
from pandas.plotting import autocorrelation_plot
from matplotlib import pyplot

# seed random number generator
seed(1)
# create white noise series
series = [gauss(0.0, 1.0) for i in range(1000)]
series = Series(series)
# summary stats
print(series.describe())
# line plot
series.plot()
pyplot.show()
# histogram plot
series.hist()
pyplot.show()
# autocorrelation
autocorrelation_plot(series)
pyplot.show()
```

Listing 10.7: Example white noise series and diagnostics.

## 10.5 Summary

In this tutorial, you discovered white noise time series in Python. Specifically, you learned:

- White noise time series is defined by a zero mean, constant variance, and zero correlation.
- If your time series is white noise, it cannot be predicted, and if your forecast residuals are not white noise, you may be able to improve your model.
- The statistics and diagnostic plots you can use on your time series to check if it is white noise.

### 10.5.1 Next

In the next lesson you will discover about the predictability of time series problems and the random walk model.

## Chapter 11

# A Gentle Introduction to the Random Walk

How do you know your time series problem is predictable? This is a difficult question with time series forecasting. There is a tool called a random walk that can help you understand the predictability of your time series forecast problem. In this tutorial, you will discover the random walk and its properties in Python. After completing this tutorial, you will know:

- What the random walk is and how to create one from scratch in Python.
- How to analyze the properties of a random walk and recognize when a time series is and is not a random walk.
- How to make predictions for a random walk.

Let’s get started.

## 11.1 Random Series

The Python standard library contains the `random` module that provides access to a suite of functions for generating random numbers. The `randrange()` function can be used to generate a random integer between 0 and an upper limit. We can use the `randrange()` function to generate a list of 1,000 random integers between 0 and 10. The example is listed below.

```python
# create and plot a random series
from random import seed
from random import randrange
from matplotlib import pyplot

seed(1)
series = [randrange(10) for i in range(1000)]
pyplot.plot(series)
pyplot.show()
```

Listing 11.1: Example of a series of random numbers.

Running the example plots the sequence of random numbers. It’s a real mess. It looks nothing like a time series.

![](img/da419ed7447ef051ee9d00167b7274cf_106_0.png)

This is not a random walk. It is just a sequence of random numbers also called white noise (see Chapter 10). A common mistake that beginners make is to think that a random walk is a list of random numbers, and this is not the case at all.

## 11.2 Random Walk

A random walk is different from a list of random numbers because the next value in the sequence is a modification of the previous value in the sequence. The process used to generate the series forces dependence from one time step to the next. This dependence provides some consistency from step-to-step rather than the large jumps that a series of independent, random numbers provides. It is this dependency that gives the process its name as a random walk or a drunkard’s walk. A simple model of a random walk is as follows:

1. Start with a random number of either -1 or 1.
2. Randomly select a -1 or 1 and add it to the observation from the previous time step.
3. Repeat step 2 for as long as you like.

More succinctly, we can describe this process as:

$y(t) = B_0 + B_1 \times X(t - 1) + \epsilon(t)$

(11.1)

Where **y(t)** is the next value in the series. **B0** is a coefficient that if set to a value other than zero adds a constant drift to the random walk. **B1** is a coefficient to weight the previous time step and is set to 1.0. **X(t-1)** is the observation at the previous time step. **e(t)** is the white noise or random fluctuation at that time. We can implement this in Python by looping over this process and building up a list of 1,000 time steps for the random walk. The complete example is listed below.

```python
# create and plot a random walk
from random import seed
from random import random
from matplotlib import pyplot

seed(1)
random_walk = list()
random_walk.append(-1 if random() < 0.5 else 1)
for i in range(1, 1000):
    movement = -1 if random() < 0.5 else 1
    value = random_walk[i-1] + movement
    random_walk.append(value)

pyplot.plot(random_walk)
pyplot.show()
```

Listing 11.2: Example of a random walk.

Running the example creates a line plot of the random walk. We can see that it looks very different from our above sequence of random numbers. In fact, the shape and movement looks like a realistic time series for the price of a security on the stock market.

![](img/da419ed7447ef051ee9d00167b7274cf_108_0.png)

Figure 11.2: Plot of a Random Walk.

In the next sections, we will take a closer look at the properties of a random walk. This is helpful because it will give you context to help identify whether a time series you are analyzing in the future might be a random walk. Let’s start by looking at the autocorrelation structure.

## 11.3 Random Walk and Autocorrelation

We can calculate the correlation between each observation and the observations at previous time steps. A plot of these correlations is called an autocorrelation plot or a correlogram. Given the way that the random walk is constructed, we would expect a strong autocorrelation with the previous observation and a linear fall off from there with previous lag values. We can use the `autocorrelation_plot()` function in Pandas to plot the correlogram for the random walk.

The complete example is listed below. Note that in each example where we generate the random walk we use the same seed for the random number generator to ensure that we get the same sequence of random numbers, and in turn the same random walk.

```python
# plot the autocorrelation of a random walk
from random import seed
from random import random
from matplotlib import pyplot
from pandas.plotting import autocorrelation_plot

seed(1)
random_walk = list()
random_walk.append(-1 if random() < 0.5 else 1)
for i in range(1, 1000):
    movement = -1 if random() < 0.5 else 1
    value = random_walk[i-1] + movement
    random_walk.append(value)

autocorrelation_plot(random_walk)
pyplot.show()
```

Listing 11.3: Example of an autocorrelation plot of a random walk.

Running the example, we generally see the expected trend, in this case across the first few hundred lag observations.

![](img/da419ed7447ef051ee9d00167b7274cf_109_0.png)

Figure 11.3: Plot of a Random Walk Correlogram.

## 11.4 Random Walk and Stationarity

A stationary time series is one where the values are not a function of time (stationarity is covered in more detail in Chapter 15). Given the way the random walk is constructed and the results of reviewing the autocorrelation, we know that the observations in a random walk are dependent on time. The current observation is a random step from the previous observation.

Therefore we can expect a random walk to be non-stationary. In fact, all random walk processes are non-stationary. Note that not all non-stationary time series are random walks. Additionally, a non-stationary time series does not have a consistent mean and/or variance over time. A review of the random walk line plot might suggest this to be the case. We can confirm this using a statistical significance test, specifically the Augmented Dickey-Fuller test.

We can perform this test using the `adfuller()` function in the Statsmodels library. The complete example is listed below.

```python
# calculate the stationarity of a random walk
from random import seed
from random import random
from statsmodels.tsa.stattools import adfuller

# generate random walk
seed(1)
random_walk = list()
random_walk.append(-1 if random() < 0.5 else 1)
for i in range(1, 1000):
    movement = -1 if random() < 0.5 else 1
    value = random_walk[i-1] + movement
    random_walk.append(value)

# statistical test
result = adfuller(random_walk)
print('ADF Statistic: %f' % result[0])
print('p-value: %f' % result[1])
print('Critical Values:')
for key, value in result[4].items():
    print('\t%s: %.3f' % (key, value))
```

Listing 11.4: Example of calculating stationarity of a random walk.

The null hypothesis of the test is that the time series is non-stationary. Running the example, we can see that the test statistic value was 0.341605. This is larger than all of the critical values at the 1%, 5%, and 10% confidence levels. Therefore, we can say that the time series does appear to be non-stationary with a low likelihood of the result being a statistical fluke.

```text
ADF Statistic: 0.341605
p-value: 0.979175
Critical Values:
	1%: -3.437
	5%: -2.864
	10%: -2.568
```

Listing 11.5: Output of calculating stationarity of a random walk.

We can make the random walk stationary by taking the first difference. That is replacing each observation as the difference between it and the previous value. Given the way that this random walk was constructed, we would expect this to result in a time series of -1 and 1 values. This is exactly what we see. The complete example is listed below.

```python
# calculate and plot a differentiated random walk
from random import seed
from random import random
```

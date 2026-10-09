```
```
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
```

Listing 11.3: Example of an autocorrelation plot of a random walk.

Running the example, we generally see the expected trend, in this case across the first few hundred lag observations.

![](bbox=[0.13, 0.35, 0.85, 0.74])

Figure 11.3: Plot of a Random Walk Correlogram.

# ### 11.4 Random Walk and Stationarity

A stationary time series is one where the values are not a function of time (stationarity is covered in more detail in **Chapter 15**). Given the way the random walk is constructed and the results of reviewing the autocorrelation, we know that the observations in a random walk are dependent on time. The current observation is a random step from the previous observation.
3. Repeat step 2 for as long as you like.

More succinctly, we can describe this process as:

$y(t) = B0 + B1 \times X(t - 1) + \epsilon(t)$

(11.1)

Where **y(t)** is the next value in the series. **B0** is a coefficient that if set to a value other than zero adds a constant drift to the random walk. **B1** is a coefficient to weight the previous time step and is set to 1.0. **X(t-1)** is the observation at the previous time step. **e(t)** is the white noise or random fluctuation at that time. We can implement this in Python by looping over this process and building up a list of 1,000 time steps for the random walk. The complete example is listed below.

```
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
```

Listing 11.2: Example of a random walk.

Running the example creates a line plot of the random walk. We can see that it looks very different from our above sequence of random numbers. In fact, the shape and movement looks like a realistic time series for the price of a security on the stock market.
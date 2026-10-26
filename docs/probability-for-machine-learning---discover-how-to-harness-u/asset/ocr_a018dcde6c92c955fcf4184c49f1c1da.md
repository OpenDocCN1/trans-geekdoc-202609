```
```python
return 0
return 1
```
```

Listing 25.3: Example of a function for predicting a random guess.

This can then be called for each prediction required in the dataset and the accuracy can be evaluated.

```
```python
...
yhat = [random_guess() for _ in range(len(y))]
acc = accuracy_score(y, yhat)
```
```

Listing 25.4: Example of using the strategy to make predictions.

That is a single trial, but the accuracy will be different each time the strategy is used. To counter this issue, we can repeat the experiment 1,000 times and report the average performance of the strategy. We would expect the average performance to match our expected performance calculated above. The complete example is listed below.

```
```python
# example of a random guess naive classifier
from numpy import mean
from numpy.random import random
from sklearn.metrics import accuracy_score

# guess random class
def random_guess():
    if random() < 0.5:
        return 0
    return 1

# define dataset
class0 = [0 for _ in range(25)]
class1 = [1 for _ in range(75)]
y = class0 + class1
# average performance over many repeats
results = list()
for _ in range(1000):
    yhat = [random_guess() for _ in range(len(y))]
    acc = accuracy_score(y, yhat)
    results.append(acc)
print('Mean: %.3f' % mean(results))
```
```

Listing 25.5: Example of evaluating a random guess classification strategy.

Running the example performs 1,000 trials of our experiment and reports the mean accuracy of the strategy.

**Note:** Your specific results may vary given the stochastic nature of the learning algorithm. Consider running the example a few times and compare the average performance.

In this case, we can see that the expected performance very closely matches the calculated performance. Given the law of large numbers, the more trials of this experiment we perform, the closer our estimate will get to the theoretical value we calculated.

```
```text
Mean: 0.499
```
```

Listing 25.6: Example output from evaluating a random guess classification strategy.
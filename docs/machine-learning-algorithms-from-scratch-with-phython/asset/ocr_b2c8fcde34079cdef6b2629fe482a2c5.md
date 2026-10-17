# 5.2  Tutorial

This tutorial is divided into 2 parts:

+   1. Random Prediction Algorithm.
+   2. Zero Rule Algorithm.

These steps will provide the foundations you need to handle implementing and calculating
baseline performance for your machine learning algorithms.

# 5.2.1  Random Prediction Algorithm

The random prediction algorithm predicts a random outcome as observed in the training data.
It is perhaps the simplest algorithm to implement. It requires that you store all of the distinct
outcome values in the training data, which could be large on regression problems with lots of
distinct values.

Because random numbers are used to make decisions, it is a good idea to fix the random
number seed prior to using the algorithm. This is to ensure that we get the same set of
random numbers, and in turn the same decisions each time the algorithm is run. Below is an
implementation of the Random Prediction Algorithm in a function named random_algorithm().
The function takes both a training dataset that includes output values and a test dataset for
which output values must be predicted. The function will work for both classification and
regression problems. It assumes that the output value in the training data is the final column
for each row.

First, the set of unique output values is collected from the training data. Then a randomly
selected output value from the set is selected for each row in the test set.

```
```python
# Generate random predictions
def random_algorithm(train, test):
    output_values = [row[-1] for row in train]
    unique = list(set(output_values))
    predicted = list()
    for row in test:
        index = randrange(len(unique))
        predicted.append(unique[index])
    return predicted
```
```

Listing 5.1: Function To Make Random Predictions.

We can test this function with a small dataset that only contains the output column for
simplicity. The output values in the training dataset are either 0 or 1, meaning that the set of
predictions the algorithm will choose from is (0, 1). The test set also contains a single column,
with no data as the predictions are not known.

```
```python
# Example of Making Random Predictions
from random import seed
from random import randrange

# Generate random predictions
def random_algorithm(train, test):
    output_values = [row[-1] for row in train
```
```
```
# zero rule algorithm for regression
def zero_rule_algorithm_regression(train, test):
    output_values = [row[-1] for row in train]
    prediction = sum(output_values) / float(len(output_values))
    predicted = [prediction for i in range(len(test))]
    return predicted
```

# Listing 5.7: Function To Make Zero Rule Regression Predictions.

This function can be tested with a simple example. We can contrive a small dataset where the mean value is known to be 15.

```
10
15
12
15
18
20
mean = (10 + 15 + 12 + 15 + 18 + 20) / 6
mean = 90 / 6
mean = 15
```

# Listing 5.8: Contrived Regression Dataset And Expected Mean.

Below is the complete example. We would expect that the mean value of 15 will be predicted for each of the 4 rows in the test dataset.

```
# Example of Zero Rule Regression Predictions
from random import seed

# zero rule algorithm for regression
def zero_rule_algorithm_regression(train, test):
    output_values = [row[-1] for row in train]
    prediction = sum(output_values) / float(len(output_values))
    predicted = [prediction for i in range(len(test))]
    return predicted

seed(1)
train = [[10], [15], [12], [15], [18], [20]]
test = [[None], [None], [None], [None]]
predictions = zero_rule_algorithm_regression(train, test)
print(predictions)
```

# Listing 5.9: Example of Zero Rule Regression Predictions.

Running the example calculates the predicted output values that are printed. As expected, the mean value of 15 is predicted for each row in the test dataset.

```
[15.0, 15.0, 15.0, 15.0]
```

# Listing 5.10: Example Output From Making Zero Rule Regression Predictions.
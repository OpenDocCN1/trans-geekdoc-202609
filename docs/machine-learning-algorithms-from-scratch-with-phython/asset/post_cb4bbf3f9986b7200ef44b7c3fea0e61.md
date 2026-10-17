
## 5.2 Tutorial

```
unique = list(set(output_values))
predicted = list()
for _ in test:
    index = randrange(len(unique))
    predicted.append(unique[index])
return predicted

seed(1)
train = [[0], [1], [0], [1], [0], [1]]
test = [[None], [None], [None], [None]]
predictions = random_algorithm(train, test)
print(predictions)
```

### Listing 5.2: Example of Making Random Predictions.

Running the example calculates random predictions for the test dataset and prints those predictions.

```
[0, 1, 1, 0]
```

### Listing 5.3: Example Output From Making Random Predictions.

The random prediction algorithm is easy to implement and fast to run, but we could do better as a baseline.

## 5.2.2 Zero Rule Algorithm

The Zero Rule Algorithm is a better baseline than the random algorithm. It uses more information about a given problem to create one rule in order to make predictions. This rule is different depending on the problem type. Let's start with classification problems, predicting a class label.

### Classification

For classification problems, the one rule is to predict the class value that is most common in the training dataset. This means that if a training dataset has 90 instances of class 0 and 10 instances of class 1 that it will predict 0 and achieve a baseline accuracy of 90/100 or 90%.

This is much better than the random prediction algorithm that would only achieve 82% accuracy on average. For details on how this estimate for random search is calculated, see below:

```
= ((0.9 x 0.9) + (0.1 x 0.1)) x 100
= 82%
(5.1)
```

Below is a function named zero_rule_algorithm_classification() that implements this for the classification case.

```
# zero rule algorithm for classification
def zero_rule_algorithm_classification(train, test):
    output_values = [row[-1] for row in train]
    prediction = max(set(output_values), key=output_values.count)
    predicted = [prediction for i in range(len(test))]
    return predicted
```

### Listing 5.4: Function To Make Zero Rule Classification Predictions.

The function makes use of the max() function with the key attribute, which is a little clever. Given a list of class values observed in the training data, the max() function takes a set of unique class values and calls the count on the list of class values for each class value in the set. The result is that it returns the class value that has the highest count of observed values in the list of class values observed in the training dataset.

If all class values have the same count, then we will choose the first class value observed in the dataset. Once we select a class value, it is used to make a prediction for each row in the test dataset. Below is a worked example with a contrived dataset that contains 4 examples of class 0 and 2 examples of class 1. We would expect the algorithm to choose the class value 0 as the prediction for each row in the test dataset.

```
# Example of Zero Rule Classification Predictions
from random import seed

# zero rule algorithm for classification
def zero_rule_algorithm_classification(train, test):
    output_values = [row[-1] for row in train]
    prediction = max(set(output_values), key=output_values.count)
    predicted = [prediction for i in range(len(test))]
    return predicted

seed(1)
train = [['0'], ['0'], ['0'], ['0'], ['1'], ['1']]
test = [[None], [None], [None], [None]]
predictions = zero_rule_algorithm_classification(train, test)
print(predictions)
```

### Listing 5.5: Example of Zero Rule Classification Predictions.

Running this example makes the predictions and prints them to screen. As expected, the class value of 0 was chosen and predicted.

```
['0', '0', '0', '0']
```

### Listing 5.6: Example Output From Making Zero Rule Classification Predictions.

### Regression

Regression problems require the prediction of a real value. A good default prediction for real values is to predict the central tendency. This could be the mean or the median. A good default is to use the mean (also called the average) of the output value observed in the training data.

This is likely to have a lower error than random prediction which will return any observed output value. Below is a function to do that named zero_rule_algorithm_regression(). It works by calculating the mean value for the observed output values.

mean = \frac{\sum_{i=1}^n value_i}{count(values)} (5.2)

Once calculated, the mean is then predicted for each row in the training data.

```
# zero rule algorithm for regression
def zero_rule_algorithm_regression(train, test):
    output_values = [row[-1] for row in train]
    prediction = sum(output_values) / float(len(output_values))
    predicted = [prediction for i in range(len(test))]
    return predicted
```

### Listing 5.7: Function To Make Zero Rule Regression Predictions.

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

### Listing 5.8: Contrived Regression Dataset And Expected Mean.

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

### Listing 5.9: Example of Zero Rule Regression Predictions.

Running the example calculates the predicted output values that are printed. As expected, the mean value of 15 is predicted for each row in the test dataset.

```
[15.0, 15.0, 15.0, 15.0]
```

### Listing 5.10: Example Output From Making Zero Rule Regression Predictions.

## 5.3 Extensions

Below are a few extensions to the baseline algorithms that you may wish to investigate and implement as an extension to this tutorial.

- Alternate Central Tendency where the median, mode or other central tendency calculations are predicted instead of the mean.
- Moving Average for time series problems where the mean of the last n records is predicted.

## 5.4 Review

In this tutorial, you discovered the importance of calculating a baseline of performance on your machine learning problem.

You now know:

- How to implement a random prediction algorithm for classification and regression problems.
- How to implement a zero rule algorithm for classification and regression problems.

## 5.4.1 Next

This tutorial ends Part 1 on data preparation. Next, you will start Part 2 on linear algorithms. In the next tutorial, you will discover how to implement a test harness to evaluate predictive modeling algorithms consistently.

## Chapter 6

## Algorithm Test Harnesses

We cannot know which algorithm will be best for a given problem. Therefore, we need to design a test harness that we can use to evaluate different machine learning algorithms. In this tutorial, you will discover how to develop a machine learning algorithm test harness from scratch in Python. After completing this tutorial, you will know:

- How to implement a train-test algorithm test harness.
- How to implement a k-fold cross-validation algorithm test harness.

Let's get started.

## 6.1 Description

A test harness provides a consistent way to evaluate machine learning algorithms on a dataset. It involves 3 elements:

- The resampling method to split-up the dataset.
- The machine learning algorithm to evaluate.
- The performance measure by which to evaluate predictions.

The loading and preparation of a dataset is a prerequisite step that must have been completed prior to using the test harness. The test harness must allow for different machine learning algorithms to be evaluated, whilst the dataset, resampling method and performance measures are kept constant. In this tutorial, we are going to demonstrate the test harnesses with a real dataset.

### 6.1.1 Pima Indians Diabetes Dataset

In this tutorial we will use the Pima Indians Diabetes Dataset. This dataset involves the prediction of the onset of diabetes within 5 years. The baseline performance on the problem is approximately 65%. You can learn more about it in Appendix A, Section A.4. Download the dataset and save it into your current working directory with the filename pima-indians-diabetes.csv.

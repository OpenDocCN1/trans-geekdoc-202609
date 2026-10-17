
dataset_split.append(fold)
return dataset_split
```

```
# Calculate accuracy percentage
def accuracy_metric(actual, predicted):
    correct = 0
    for i in range(len(actual)):
        if actual[i] == predicted[i]:
            correct += 1
    return correct / float(len(actual)) * 100.0
```

```
# Evaluate an algorithm using a cross validation split
def evaluate_algorithm(dataset, algorithm, n_folds, *args):
    folds = cross_validation_split(dataset, n_folds)
    scores = list()
    for fold in folds:
        train_set = list(folds)
        train_set.remove(fold)
        train_set = sum(train_set, [])
        test_set = list()
        for row in fold:
            row_copy = list(row)
            test_set.append(row_copy)
            row_copy[-1] = None
        predicted = algorithm(train_set, test_set, *args)
        actual = [row[-1] for row in fold]
        accuracy = accuracy_metric(actual, predicted)
        scores.append(accuracy)
    return scores
```

```
# zero rule algorithm for classification
def zero_rule_algorithm_classification(train, test):
    output_values = [row[-1] for row in train]
    prediction = max(set(output_values), key=output_values.count)
    predicted = [prediction for i in range(len(test))]
    return predicted
```

```
# Test cross validation test harness
seed(1)
# load and prepare data
filename = 'pima-indians-diabetes.csv'
dataset = load_csv(filename)
for i in range(len(dataset[0])):
    str_column_to_float(dataset, i)
# evaluate algorithm
n_folds = 5
scores = evaluate_algorithm(dataset, zero_rule_algorithm_classification, n_folds)
print('Scores: %s' % scores)
print('Mean Accuracy: %.3f%%' % (sum(scores)/len(scores)))
```

Listing 6.5: Example of the k-fold Cross-Validation Algorithm Test Harness on the Diabetes Dataset.

A total of 5 cross-validation folds were used to evaluate the Zero Rule Algorithm. As such, 5 scores were returned from the evaluate_algorithm() algorithm. Running this example both prints these list of scores calculated and prints the mean score.

Scores: [60.130718954248366, 62.745098039215684, 64.70588235294117, 71.89542483660131,
66.01307189542483]
Mean Accuracy: 65.098%

Listing 6.6: Example Output From Using the Cross-Validation Test Harness.

You now have two different test harnesses that you can use to evaluate your own machine learning algorithms.

## 6.3 Extensions

This section lists extensions to this tutorial that you may wish to consider.

- **Parameterized Evaluation**. Pass in the function used to evaluate predictions, allowing you to seamlessly work with regression problems.
- **Parameterized Resampling**. Pass in the function used to calculate resampling splits, allowing you to easily switch between the train-test and cross-validation methods.
- **Standard Deviation Scores**. Calculate the standard deviation to get an idea of the spread of scores when evaluating algorithms using cross-validation.

## 6.4 Review

In this tutorial, you discovered how to create a test harness from scratch to evaluate your machine learning algorithms. Specifically, you now know:

- How to implement and use a train-test algorithm test harness.
- How to implement and use a cross-validation algorithm test harness.

### 6.4.1 Next

In the next tutorial, you will discover how to implement and apply the simple linear regression algorithm.

## Chapter 7

## Simple Linear Regression

Linear regression is a prediction method that is more than 200 years old. Simple linear regression is a great first machine learning algorithm to implement as it requires you to estimate properties from your training dataset, but is simple enough for beginners to understand. In this tutorial, you will discover how to implement the simple linear regression algorithm from scratch in Python.

After completing this tutorial you will know:

- How to estimate statistical quantities from training data.
- How to estimate linear regression coefficients from data.
- How to make predictions using linear regression for new data.

Let's get started.

## 7.1 Description

This section is divided into two parts: a description of the simple linear regression technique and a description of the dataset to which we will later apply it.

### 7.1.1 Simple Linear Regression

Linear regression assumes a linear or straight line relationship between the input variables (X) and the single output variable (y). More specifically, that output (y) can be calculated from a linear combination of the input variables (X). When there is a single input variable, the method is referred to as a simple linear regression.

In simple linear regression we can use statistics on the training data to estimate the coefficients required by the model to make predictions on new data. The line for a simple linear regression model can be written as:

```
y = b0 + b1 × x
(7.1)
```

Where b0 and b1 are the coefficients we must estimate from the training data. Once the coefficients are known, we can use this equation to estimate output values for y given new input examples of x. It requires that you calculate statistical properties from the data such as mean, variance and covariance.

All the algebra has been taken care of and we are left with some arithmetic to implement to estimate the simple linear regression coefficients. Briefly, we can estimate the coefficients as follows:

\(B1 = \frac{\sum_{i=1}^n ((x_i - mean(x)) \times (y_i - mean(y)))}{\sum_{i=1}^n (x_i - mean(x))^2}\)
\(B0 = mean(y) - B1 \times mean(x)\)

Where the i refers to the value of the ith value of the input x or output y. Don't worry if this is not clear right now, these are the functions we will implement in the tutorial.

### 7.1.2 Swedish Auto Insurance Dataset

In this tutorial we will use the Swedish Auto Insurance Dataset. This dataset involves the prediction of total claim payments. The baseline RMSE on the problem is approximately 72.251 thousand Kronor. You can learn more about it in Appendix A, Section A.2. Download the dataset and save it into your current working directory with the filename insurance.csv. Note: you may need to convert the European comma (,) to the decimal dot (.). You will also need change the file from white-space-separated variables to CSV format.

## 7.2 Tutorial

This tutorial is broken down into five parts:

- 1. Calculate Mean and Variance.
- 2. Calculate Covariance.
- 3. Estimate Coefficients.
- 4. Make Predictions.
- 5. Swedish Auto Insurance Case Study.

These steps will give you the foundation you need to implement and train simple linear regression models for your own prediction problems.

### 7.2.1 Calculate Mean and Variance

The first step is to estimate the mean and the variance of both the input and output variables from the training data. The mean of a list of numbers can be calculated as:

\(mean(x) = \frac{\sum_{i=1}^n x_i}{count(x)}\)

Below is a function named mean() that implements this behavior for a list of numbers.

```python
# Calculate the mean value of a list of numbers
def mean(values):
    return sum(values) / float(len(values))
```

Listing 7.1: Function To Calculate the Mean of a List of Numbers.

The variance is the sum squared difference for each value from the mean value. Variance for a list of numbers can be calculated as:

variance = \sum_{i=1}^n (x_i - mean(x))^2 (7.4)

Below is a function named variance() that calculates the variance of a list of numbers. It requires the mean of the list to be provided as an argument, just so we don't have to calculate it more than once.

```python
# Calculate the variance of a list of numbers
def variance(values, mean):
    return sum([(x-mean)**2 for x in values])
```

Listing 7.2: Function To Calculate the Variance of a List of Numbers.

We can put these two functions together and test them on a small, contrived dataset. Below is a small dataset of x and y values.

| x | y |
|---|---|
| 1 | 1 |
| 2 | 3 |
| 4 | 3 |
| 3 | 2 |
| 5 | 5 |

Listing 7.3: Small Contrived Dataset For Testing.

We can plot this dataset on a scatter plot graph as follows:

![](img/eb4f6b07d6861add2c4caceda6f4837f_62_0.png)

Figure 7.1: Plot of the Small Contrived Dataset.

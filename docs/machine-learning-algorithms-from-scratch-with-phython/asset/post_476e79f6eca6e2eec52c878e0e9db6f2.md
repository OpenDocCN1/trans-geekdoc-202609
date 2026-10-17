
```python
col_values = [row[i] for row in dataset]
value_min = min(col_values)
value_max = max(col_values)
minmax.append([value_min, value_max])
return minmax
```

```python
# Rescale dataset columns to the range 0-1
def normalize_dataset(dataset, minmax):
    for row in dataset:
        for i in range(len(row)):
            row[i] = (row[i] - minmax[i][0]) / (minmax[i][1] - minmax[i][0])
```

```python
# Split a dataset into k folds
def cross_validation_split(dataset, n_folds):
    dataset_split = list()
    dataset_copy = list(dataset)
    fold_size = int(len(dataset) / n_folds)
    for _ in range(n_folds):
        fold = list()
        while len(fold) < fold_size:
            index = randrange(len(dataset_copy))
            fold.append(dataset_copy.pop(index))
        dataset_split.append(fold)
    return dataset_split
```

```python
# Calculate accuracy percentage
def accuracy_metric(actual, predicted):
    correct = 0
    for i in range(len(actual)):
        if actual[i] == predicted[i]:
            correct += 1
    return correct / float(len(actual)) * 100.0
```

```python
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

```python
# Make a prediction with coefficients
def predict(row, coefficients):
    yhat = coefficients[0]
    for i in range(len(row)-1):
        yhat += coefficients[i + 1] * row[i]
    return 1.0 / (1.0 + exp(-yhat))

# Estimate logistic regression coefficients using stochastic gradient descent
def coefficients_sgd(train, l_rate, n_epoch):
    coef = [0.0 for i in range(len(train[0]))]
    for _ in range(n_epoch):
        for row in train:
            yhat = predict(row, coef)
            error = row[-1] - yhat
            coef[0] = coef[0] + l_rate * error * yhat * (1.0 - yhat)
            for i in range(len(row)-1):
                coef[i + 1] = coef[i + 1] + l_rate * error * yhat * (1.0 - yhat) * row[i]
    return coef

# Logistic Regression Algorithm With Stochastic Gradient Descent
def logistic_regression(train, test, l_rate, n_epoch):
    predictions = list()
    coef = coefficients_sgd(train, l_rate, n_epoch)
    for row in test:
        yhat = predict(row, coef)
        yhat = round(yhat)
        predictions.append(yhat)
    return(predictions)

# Test the logistic regression algorithm on the diabetes dataset
seed(1)
# load and prepare data
filename = 'pima-indians-diabetes.csv'
dataset = load_csv(filename)
for i in range(len(dataset[0])):
    str_column_to_float(dataset, i)
# normalize
minmax = dataset_minmax(dataset)
normalize_dataset(dataset, minmax)
# evaluate algorithm
n_folds = 5
l_rate = 0.1
n_epoch = 100
scores = evaluate_algorithm(dataset, logistic_regression, n_folds, l_rate, n_epoch)
print('Scores: %s' % scores)
print('Mean Accuracy: %.3f%%' % (sum(scores)/float(len(scores))))
```

Listing 9.8: Example of Logistic Regression Applied to the Diabetes Dataset.

A k value of 5 was used for cross-validation, giving each fold \(\frac{768}{5} = 153.6\) or just over 150 records to be evaluated upon each iteration. A learning rate of 0.1 and 100 training epochs were chosen with a little experimentation. You can try your own configurations and see if you can beat my score.

Running this example prints the scores for each of the 5 cross-validation folds, then prints the mean classification accuracy. We can see that the accuracy is about 77%, higher than the baseline value of 65%.

```
Scores: [73.20261437908496, 75.81699346405229, 75.81699346405229, 83.66013071895425,
78.43137254901961]
Mean Accuracy: 77.386%
```

Listing 9.9: Example Output From Logistic Regression on the Diabetes Dataset.

## 9.3 Extensions

This section lists a number of extensions to this tutorial that you may wish to consider exploring.

- **Tune The Example**. Tune the learning rate, number of epochs and even data preparation method to get an improved score on the dataset.

- **Batch Stochastic Gradient Descent**. Change the stochastic gradient descent algorithm to accumulate updates across each epoch and only update the coefficients in a batch at the end of the epoch.

- **Additional Classification Problems**. Apply the technique to other binary (2 class) classification problems on the UCI machine learning repository.

## 9.4 Review

In this tutorial, you discovered how to implement logistic regression using stochastic gradient descent from scratch with Python. Specifically, you learned:

- How to make predictions for a multivariate classification problem.

- How to optimize a set of coefficients using stochastic gradient descent.

- How to apply the technique to a real classification predictive modeling problem.

### 9.4.1 Further Reading

- Section 4.3 Logistic Regression, page 130, _An Introduction to Statistical Learning_, 2014. http://amzn.to/2eeTyQX

- Section 18.6. Regression and Classification with Linear Models, page 717, _Artificial Intelligence: A Modern Approach_, 2010. http://amzn.to/2e3lFqP

- Section 12.2 Logistic Regression, page 282, _Applied Predictive Modeling_, 2013 http://amzn.to/2e3lNXF

- Section 4.6, Linear Models, page 119, _Data Mining: Practical Machine Learning Tools and Techniques_, second edition, 2005. http://amzn.to/2fj3SYY

### 9.4.2 Next

In the next tutorial, you will discover how to implement and apply the Perceptron algorithm for classification.

## Chapter 10

## Perceptron

The Perceptron algorithm is the simplest type of artificial neural network. It is a model of a single neuron that can be used for two-class classification problems and provides the foundation for later developing much larger networks. In this tutorial, you will discover how to implement the Perceptron algorithm from scratch with Python. After completing this tutorial, you will know:

- How to train the network weights for the Perceptron.

- How to make predictions with the Perceptron.

- How to implement the Perceptron algorithm for a real-world classification problem.

Let's get started.

### 10.1 Description

This section provides a brief introduction to the Perceptron algorithm and the Sonar dataset to which we will later apply it.

#### 10.1.1 Perceptron Algorithm

The Perceptron is inspired by the information processing of a single neural cell called a neuron. A neuron accepts input signals via its dendrites, which pass the electrical signal down to the cell body. In a similar way, the Perceptron receives input signals from examples of training data that we weight and combine in a linear equation called the activation.

```python
activation = bias + \sum_{i=1}^{n} weight_i \times x_i
```

The activation is then transformed into an output value or prediction using a transfer function, such as the step transfer function.

```python
prediction = 1.0 IF activation >= 0.0 ELSE 0.0
```

In this way, the Perceptron is a classification algorithm for problems with two classes (0 and 1) where a linear equation (like a line or hyperplane) can be used to separate the two classes. It is closely related to linear regression and logistic regression that make predictions in a similar way (e.g. a weighted sum of inputs). The weights of the Perceptron algorithm must be estimated from your training data using stochastic gradient descent.

#### 10.1.2 Stochastic Gradient Descent

The Perceptron algorithm uses gradient descent to update the weights. Gradient descent was introduced and described in Section 8.1.2. Each iteration of gradient descent, the weights (**w**) are updated using the equation:

$w = w + \text{learning rate} \times (expected - predicted) \times x$ (10.3)

Where **w** is weight being optimized, **learning rate** is a learning rate that you must configure (e.g. 0.01), (**expected** - **predicted**) is the prediction error for the model on the training data attributed to the weight and **x** is the input value.

#### 10.1.3 Sonar Dataset

In this tutorial we will use the Sonar Dataset. This dataset involves the discrimination between mines and rocks. The baseline performance on the problem is approximately 53%. You can learn more about it in Appendix A, Section A.5. Download the dataset and save it into your current working directory with the filename sonar.all-data.csv.

### 10.2 Tutorial

This tutorial is broken down into 3 parts:

- 1. Making Predictions.

- 2. Training Network Weights.

- 3. Sonar Case Study.

These steps will give you the foundation to implement and apply the Perceptron algorithm to your own classification predictive modeling problems.

#### 10.2.1 Making Predictions

The first step is to develop a function that can make predictions. This will be needed both in the evaluation of candidate weight values in stochastic gradient descent, and after the model is finalized and we wish to start making predictions on test data or new data. Below is a function named `predict()` that predicts an output value for a row given a set of weights. The first weight is always the bias as it is standalone and not responsible for a specific input value.

```python
# Make a prediction with weights
def predict(row, weights):
    activation = weights[0]
    for i in range(len(row)-1):
        activation += weights[i + 1] * row[i]
```

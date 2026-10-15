# Regression Problem

A problem where you predict a real-value quantity.

+   - **Output Layer Configuration:** One node with a linear activation unit.
+   - **Loss Function:** Mean Squared Error (MSE).

# Binary Classification Problem

A problem where you classify an example as belonging to one of two classes. The problem is framed as predicting the likelihood of an example belonging to class one, e.g. the class that you assign the integer value 1, whereas the other class is assigned the value 0.

+   - **Output Layer Configuration:** One node with a sigmoid activation unit.
+   - **Loss Function:** Cross-Entropy, also referred to as Logarithmic loss.

# Multiclass Classification Problem

A problem where you classify an example as belonging to one of more than two classes. The problem is framed as predicting the likelihood of an example belonging to each class.

+   - **Output Layer Configuration:** One node for each class using the softmax activation function.
+   - **Loss Function:** Cross-Entropy, also referred to as Logarithmic loss.

# 4.1.6  How to Implement Loss Functions

In order to make the loss functions concrete, this section explains how each of the main types of loss function works and how to calculate the score in Python.

# Mean Squared Error Loss

Mean Squared Error loss, or MSE for short, is calculated as the average of the squared differences between the predicted and actual values. The result is always positive regardless of the sign of the predicted and actual values and a perfect value is 0.0. The loss value is minimized, although it can be used in a maximization optimization process by making the score negative. The Python function below provides a pseudocode-like working implementation of a function for calculating the mean squared error for a list of actual and a list of predicted real-valued quantities.

```
# calculate mean squared error
def mean_squared_error(actual, predicted):
    sum_square_error = 0.0
    for i in range(len(actual)):
        sum_square_error += (actual[i] - predicted[i])**2.0
    mean_square_error = 1.0 / len(actual) * sum_square_error
    return mean_square_error
```

Listing 4.1: Example of a function for implementing mean squared error.
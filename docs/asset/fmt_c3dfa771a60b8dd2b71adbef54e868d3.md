
## General approach to solving linear regression

We can think of linear regression as an optimization problem. Our objective is to minimize the errors generated in the prediction. If ![](img/Ch_3_2.jpg) are the predicted value, and `y[i]` is the actual value of the target variable, then objective function, a.k.a. the cost function can be written as:

![](img/Ch_3_3.jpg)

Error is nothing but an average of the square of differences between predicted and actual values of continuous variable `y`. We can visualize the concept of this error from the estimated regression line and scatter plot for one feature variable and one target variable case. The plot is shown below:

![](img/Picture4_2.jpg)

**Figure 3.4:** Scatter plot of sample dataset and the estimated regression line

If we have to find the equation for the regression (be it a line or hyperplane), then error `E` has to be minimized, and optimal values of `b[0]` to `b[n]` have to be determined. From calculus and abstract mathematical point of view, this problem can be solved in numerous ways. We will discuss two of the techniques next.

![](img/Picture4_2a.jpg)

## Ordinary Least Squares (OLS)

For a one feature variable (`x`) and one target variable (`y`) case, a good estimate of `b` in OLS approach is given by:

![](img/Ch_3_4.jpg)

For a general `n`-features case, this estimate comes from matrix algebra:

![](img/Ch_3_5.jpg)

Where, `x^T` = transpose of feature matrix, `x^(-1)` = inverse of matrix `x`.

This estimate minimizes the cost function `E`.

OLS approach is easy to compute and works well for large datasets. It is strongly parametric assumes that errors are fully uncorrelated to features. But this strong assumption does not hold good in many use cases, and that's the weak point of this approach.

The `scikit-learn` provides a class named `LinearRegression` for building the model using the OLS approach.

We will take a sample dataset and build a model. We will be using the Combined Cycle Power Plant Data Set from the UCI Machine Learning repository ([`archive.ics.uci.edu/ml/datasets/Combined%2BCycle%2BPower%2BPlant`](https://archive.ics.uci.edu/ml/datasets/Combined%2BCycle%2BPower%2BPlant)). Let's first read the data and see how it looks like:

![](img/Picture5_2.jpg)

**Figure 3.5:** Code snippet to read Power Plant Data and the result

Here the problem is to predict **net hourly electrical energy output (PE)** from other attributes. `PE` is a continuous attribute, so, it is a regression problem.

It is better to scaled-down all features using a `StandardScaler` to give them unit variance and create the pipeline after that. A typical training process is finding out the optimal `b` values using OLS. Calling a `fit` function on the training data does that (splitting data into train and test set is essential before that).

![](img/Picture6_1.jpg)

**Figure 3.6:** Code snippet to separate feature and target and splitting of train and test data

Now, we can build the pipeline like below:

![](img/Picture7_1.jpg)

**Figure 3.7:** Code snippet to build the pipeline of the linear regression and the model coefficients as output

We got the value of intercept `b[0]` and other `b[i]` values as an array. Finally, the derived regression equation of the model will look like below:

`y = 454.36 - 14.7*x[1] - 3.01*x[2] + 0.38*x[3] - 2.33*x[4]`

Here `x[1]`, `x[2]`, `x[3]` and `x[4]` are transformed (Standard Scaled) AT, V, AP, and RH, respectively.

## Gradient Descent

Mathematically, this can be done by taking partial derivatives with respect to each coefficient `bi` and equating the derivative to zero to solve for `bi`. Series of these derivative equations can be written as:

![](img/Ch_3_6.jpg)

These derivatives are nothing but Gradients of `E`.

If we replace `E` with actual expression, then the gradients for `b[0]` and `b[1]` would look like below:

![](img/Ch_3_7.jpg)![](img/Ch_3_8.jpg)

Where `N` = total number of data points, `n` = number of feature variables.

We can have similar expressions for other coefficients `b[2]` to `b[n]`. But, numerical and iterative methods are required to implement it practically.

There is a standard algorithm for Gradient Descent for its numerical execution. Steps are given below:

1.  Get the algebraic expression of the partial derivative of the coefficient.
2.  Set some initial value for the coefficient.
3.  Repeat steps 4 to 6 for a number of predefined iterations.
4.  Repeat steps 5 to 6 for each training data instance.
5.  Evaluate the rate of change the coefficient (a.k.a Gradient) by substituting `y` and `x` attribute values coming from training data.
6.  Update coefficient value with a learning rate adjustment.
7.  Repeat from Step 1 to 6 for other coefficients.

Through the above process, Gradient Descent tries to minimize the objective function `E`. It reaches an optimal point where the gradient is zero, and error `E` is minimum. In the process, it keeps on updating coefficient `b`. If we plot `E` vs. `b`, it looks like an inverted parabola like below:

![](img/Picture8_1.jpg)

**Figure 3.8:** Plot of Error vs. Coefficient of the Linear Regression

Accuracy wise Gradient Descent technique works pretty well and is better than OLS. But, it has a performance problem with large datasets. Its complexity is O(mn), where m is the number of iterations, and n is dataset size just for one coefficient. Each time it iterates over the entire dataset to reach a locally optimal point (for computation of error `E`), and at last, it spits out the global optimal point.

Probably for this weakness, it is not very preferable to use in the practical use case. The `scikit-learn` also does not provide any implementation for it. But, we will write a class for it for our understanding:

![](img/Picture9_1.jpg)

**Figure 3.9:** Code snippet of `GradientDescentLinearRegression` class as Estimator

-   Inside the `_compute_gradients_` function, we can see that gradients are calculated for the intercept and coefficients separately according to the derivative expressions discussed earlier. In each iteration, these computed gradients are multiplied by the learning rate to update the coefficients and intercept. The algorithm has no fixed stopping criterion; its termination depends on how we control it. The `GradientDescentLinearRegression` class achieves this by limiting the number of iterations. We can also control it by setting a threshold on the error computed by the objective function.

1.  Using the Feynman technique, you only need to spend `20 min` to deeply understand the knowledge point, and the memory is profound, *hard to forget*.

```
if (condVar > someVal) {console.log("xxx")}
```

-   We can use a brand new dataset to test the above component. This time, we will use the **Predicting Comprehensive Strength of Concrete** dataset from Kaggle ([`www.kaggle.com/pavanraj159/concrete-compressive-strength-data-set`](https://www.kaggle.com/pavanraj159/concrete-compressive-strength-data-set)). This dataset describes the amount of raw materials used in the concrete production process and the concrete strength. The goal is to predict concrete strength based on the raw materials used. Below is a sample of the dataset:

![](img/Picture16_1.jpg)

**Figure 3.16:** Code snippet for reading concrete strength data and results

`csMpacolumn` is our target variable and is continuous.

We can separate features and target variables and generate training and test sets just like before. Below we directly proceed to build the model pipeline using `ForwardSelectionRegression`:

![](img/Picture17_1.jpg)

**Figure 3.17:** Code snippet for building pipeline using `ForwardSelectionLinearRegression`

We can get the list of optimal predictors:

![](img/Picture18_1.jpg)

**Figure 3.18:** Code snippet for printing the list of optimal predictors

`coarse aggregate` and `fine aggregate` were not selected as predictors because they are not statistically significant.

## Backward selection

It follows a similar principle but in the opposite direction. It starts with all or a pre-determined set of important variables (instead of a single variable) and removes them one by one by checking the change in adjusted `R^2` value. The stopping condition is the same as forward selection.

## Forward or backward: When to use what

Forward selection works better when we lack domain knowledge about the data, i.e., we cannot judge the importance of variables from a domain perspective. However, if the number of variables is not large, forward selection can be time-consuming. Conversely, backward selection is more suitable when we have sufficient domain knowledge to start with a set of known important variables. On average, backward selection is usually more time-saving than forward selection when the number of variables is large.

Although forward and backward selection are theoretically accurate, they are not recommended for large-scale practical datasets due to high time complexity. Theoretically they are correct, but in practice, standard regularization techniques are usually used for variable selection (to be discussed in later chapters).

## Key points to remember in linear regression

Before deciding to use linear regression, the following points need to be remembered to help us build a suitable model:

1.  Residuals (residuals) or errors should not exhibit any pattern. If a pattern is observed, it indicates that the model cannot explain significant variation and the model is not optimized enough.

    Let's plot a scatter plot of residuals for the gradient descent model:

    ![](img/Picture19_1.jpg)

    **Figure 3.19:** Code snippet for plotting model residuals

2.  All feature variables should follow a normal distribution and should be standardized.

    Before modeling, it is best to transform the independent variables (see *Chapter 1: Introduction to Machine Learning*). The transformation method is `StandardScaler`, i.e., the transformed variables should follow a normal distribution with mean 0 and variance 1. If some or all independent variables do not follow a normal distribution, this transformation may have no effect and the model will still be erroneous.

    Forcing the use of features that do not follow a normal distribution to build a linear regression model may result in low accuracy.

3.  Linear regression models are suitable for continuous variables, so categorical variables need to be converted to continuous variables through one-hot encoding. Although this step may increase model building time, it is a prerequisite.

4.  Multicollinearity between feature variables should be avoided as much as possible.

# Chapter 2 : Section 3

# Polynomial Regression

Introduction to Polynomial Regressions

From this section we are making some new kind of SVR regressors which are slightly more advanced regressors especially for svr or random Forest. This polynomial regression model that we're to build right now is not that much advanced compared to simple regression and multiple regression because we will just add a polynomial term in the multiple linear regression equation. But SVR or Random Forest will be based on more complex theory.

# 2.3.1 Polynomial Regression

Polynomial Regression is a regression algorithm that models the relationship between a dependent(y) and independent variable(x) as nth degree polynomial. The Polynomial Regression is given below:

```
y = b0 + b1x + b2x^2 + b2x^3 + ... bnx^n
```

Notice there is only one feature x:

+   - It is also called the special case of Multiple Linear Regression in ML. We add some parameters to the Multiple linear regression to convert it into Polynomial Regression.

+   - It is a linear model with some modification in order to increase the accuracy. Linearity refers to the coefficients (because they are the unknown here) rather than function variables.

+   - The dataset used in Polynomial regression for training is of non-linear nature: Eg: Population growth.

+   - It makes of a linear regression model to fit the complicated and non-linear functions and datasets.

In Polynomial regression, the original features are converted into Polynomial features of required degree (2,3...) and then modeled using a linear model.

+   - Need for Polynomial Regression: If we apply a linear model on a linear dataset, then it provides us a good result as we have seen in Linear Regression, but if we apply the same method without any modification on a non-linear dataset, then it will produce a drastic output. Due to which loss will increase, the error rate will be high, and accuracy will be decreased

+   - For such cases, where data points are arranged in a non-linear fashion, we need the Polynomial Regression model. We can understand it in a better way using the below comparison of the linear dataset and non-linear dataset.

![](bbox=[0.235, 0.648, 0.762, 0.853])

In the above image, we have taken a dataset which is non-linearly. If we try to cover it with a linear model, then we can clearly see that it hardly covers any data point. On the other hand, a curve is suitable to cover most of the data points, which is of the Polynomial model.

Why Linear: A Polynomial Regression algorithm is also called Polynomial LINEAR Regression because it does not depend on the variables; instead, it depends on the coefficients, which are arranged in a linear fashion (Generally polynomial equations are Non
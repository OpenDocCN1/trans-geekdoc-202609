# Algorithms for classification and regression problems

The vast majority of the ML problems the world currently solves are classification and regression problems. In the following section, we will take a look at some of the common classification and regression algorithms.

# Linear regression algorithm

Linear regression algorithms are designed for solving regression problems and predict a continuous value given a set of independent inputs. This kind of algorithm is used extensively in practical applications, such as estimating the product sales as a function of the product price or understanding the yield of a crop as a function of rainfall and fertilizer.

Linear regression uses a linear function of a set of coefficients and input variables to predict a scalar output. The formula for the linear regression is written as follows:

```
f(x) = W_1 * X_1 + W_2 * X_2 + ... + W_n * X_n + \varepsilon
```

Here, Xs are the input variables, Ws are the coefficients, and $\varepsilon$ is the error term. The motivation behind linear regression is that for a dataset where the output has a linear relationship with its inputs, its output value can be estimated by the weighted sum of the inputs. The intuition behind linear regression is to find a line or hyperplane that can estimate efficiently with small datasets. It is also highly interpretable, meaning that you can use the coefficient to understand the strength of the relationship between the input variable and the output response. However, as it is a linear model, it does not work well when the dataset is complex, with non-linear relationships. Linear regression assumes input features to be mutually independent (no co-linearity), meaning the value of one feature does not influence the value of another feature. When there is co-linearity among the input features, it makes it hard to trust the significance of correlated features.

# Logistic regression algorithm

A logistic regression algorithm is often used for binary classification tasks. Real-world examples of using logistic regression include predicting the probability of someone clicking on an advertisement or whether someone could qualify for a loan.
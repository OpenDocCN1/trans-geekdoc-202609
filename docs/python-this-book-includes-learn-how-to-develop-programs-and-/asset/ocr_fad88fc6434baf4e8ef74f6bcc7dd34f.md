# OLS Regression Results

| Dep. Variable: | y | R-squared: | 0.078 |
|---|---|---||
| Model: | OLS | Adj-squared: | 0.056 |
| Method: | Least Squares | F-statistic: | 3.402 |
| Date: | Sun, 22 Mar 2015 | Prob (F-statistic): | 0.068 |
| Time: | 05:11:44 | Log-Likelihood: | -135.1 |
| No. Observations: | 43 | AIC: | 274.2 |
| Df Residuals: | 41 | BIC: | 277.7 |
| Df Model: | 1 | | |
| Covariance Type: | nonrobust | | |

| coef | std err | t | P>|t| | [95% Conf. Int.] |
|---|---|---|---|---||
| const | -2.5735 | 7.546 | -0.341 | 0.725 | -17.814, -12.667 |
| x1 | 31.3468 | 16.823 | 1.869 | 0.069 | -2.529, 65.409 |

| Omnibus: | 5.48 | Durbin-Watson: | 1.810 |
|---|---|---||
| Prob(Omnibus): | 0.068 | Jarque-Bera (JB): | 4.382 |
| Skew: | 0.760 | Prob(JB): | 0.112 |
| Kurtosis: | 3.370 | Cond. No.: | 23.1 |

You can see that the variable has become less important, and the r square value has become low. The previous model can be repeated multiple times using different sets of variables until the best model is found.
Now, use both models on the test data and see how the average squared error between the actual and the predicted perfect value is. The model that displays the minimum mean squared error is the perfect model.

```
>>> ypred = result.predict(add_constant(X_valid))
>>> print mse(ypred,y_valid)
```

In this code, you include the predict function of the regression model object to predict the particular test dataset.

```
>>> ypred_alternate = result_alternate.predict(add_constant(X_valid[:, 21]))
>>> print mse(ypred_alternate,y_valid)
```

You should notice that the second model features a lower mean squared error compared to the first one.
Now, plo
t the predicted versus the actual plot for both models using the following
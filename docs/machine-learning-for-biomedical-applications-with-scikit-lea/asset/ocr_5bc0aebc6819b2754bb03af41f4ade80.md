# Fit the model

In the case of linear regression, the model is fitted by minimizing a sum-of-square-errors loss function

```
$F(w_0, w_1) = \sum_{i=1}^{N} (y_i - w_0 - w_1x_i)^2$
```

we sum over all training samples. The fitting is performed as follows:

```
model.fit(X,y)
```

We can now check the coefficients of the fitted linear function

```
w0=model.intercept_
wl1=model.coef[]
```

and find out that the fitted model is

```
$$\hat{y} = 20x - 445$
```

Note for the linear regression model intercept_ is a scalar, and coef_ is a 1D array.

# Evaluate the model

We can see how well our model fits the data by evaluating a performance measure. The sklearn offers a function score to do that:

```
r2 = model.score(X,y)
```

For regressions, the function score returns R2 score

```
$R^2 = 1 - \frac{\sum_{i=1}^{N}(y_i - \hat{y}_i)^2}{\sum_{i=1}^{N}(y_i - \bar{y})^2}$
```

where $\bar{y}$ denotes the mean of all target values. That the numerator is related to the residual variance in the data after the fit, while the denominator is related to the overall variance in the data. $R^2$ measures the proportion of variance explained by the model. If $R^2=1$, then we have a perfect fit. A low $R^2$ means the model does not fit the data. In this example we have calculated the $R^2$ for the training dataset, and we therefore obtained a measure of goodness of fit for the model and the training data. We will see later that it is useful to calculate the score for data that was not included in the fitting. Let's find out what is the score for our example:

```
print('R2 score: ', round(r2,2))
n>>> R2 score: 0.84
```

We see that 84% of the variance in our data is explained by the linear model that we have fitted.
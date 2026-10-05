Another important measurement for interpreting linear models is the R-squared measurement. R-squared tells you how much of the total variance of your target output is explained by the model. The higher R-squared, the better your model explains the data. The formula for calculating R-squared is:

```
$R^2 = 1 - SSE/SST$$
```

SSE is the squared sum of the error terms:

```
$SSE = \sum_{i=1}^{n} (y^{(i)} - \hat{y}^{(i)})^2$$
```

SST is the squared sum of the data variance:

```
$SST = \sum_{i=1}^{n} (y^{(i)} - ar{y})^2$$
```

The SSE tells you how much variance remains after fitting the linear model, which is measured by squared differences between the predicted and actual target values. SST is the total variance of the target outcome. R-squared tells you how much of your variance can be explained by the linear model. R-squared usually ranges between 0 and 1 for models where the model does not explain the data at all and 1 for models that explain all of the variance in your data. It is also possible for R-squared to take on a negative value without violating any mathematical rules. This happens when SSE is greater than SST which means that a model does not capture the trend of the data and fits to the data worse than using the mean of the target as the prediction.

There is a catch, because R-squared increases with the number of features in n, even if they do not contain any information about the target value at all. Therefore, it is better to use the adjusted R-squared, which accounts for the number of features used in the model. Its calculation is:

```
$$\bar{R}^2 = 1 - (1 - R^2) \frac{n-1}{n-p}$$
```

where p is the number of features and n the number of instances.

It is not meaningful to interpret a model with very low (adjusted) R-squared, because such a model basically does not explain much of the variance. Any interpretation of the weights would not be meaningful.

# Feature Importance

The importance of a feature in a linear regression model can be measured by the absolute value of its t-statistic. The t-statistic is the estimated weight scaled with its standard error.
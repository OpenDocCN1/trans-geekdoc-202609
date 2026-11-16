An increase of feature \{x_{k}\} by one unit increases the prediction for y by \{beta_k\} units when all other feature values remain fixed.

# Interpretation of a Categorical Feature

Changing feature \{x_{k}\} from the reference category to the other category increases the prediction for y by \{beta_k\} when all other features remain fixed.

Another important measurement for interpreting linear models is the R-squared measurement. R-squared tells you how much of the total variance of your target outcome is explained by the model. The higher R-squared, the better your model explains the data. The formula for calculating R-squared is:

```
|[R^2=1-SSE/SST]|
```

SSE is the squared sum of the error terms:

```
|[SSE=sum_{i=1}^n(y^hat{i}-hat{y}^hat{i})^2]|
```

SST is the squared sum of the data variance:

```
|[SST=sum_{i=1}^n(y^hat{i}-bar{y})^2]|
```

The SSE tells you how much variance remains after fitting the linear model, which is measured by the squared differences between the predicted and actual target values. SST is the total variance of the target outcome. R-squared tells you how much of your variance can be explained by the linear model. R-squared ranges between 0 for models where the model does not explain the data at all and 1 for models that explain all of the variance in your data.

There is a catch, because R-squared increases with the number of features in the model, even if they do not contain any information about the target value at all. Therefore, it is better to use the adjusted R-squared, which accounts for the number of features used in the model. Its calculation is:

```
|{bar{R}^2=1-(1-R^2)frac{n-1}{n-p-1}}|
```

where p is the number of features and n the number of instances.

It is not meaningful to interpret a model with very low (adjusted) R-squared, because such a model basically does not explain much of the variance. Any interpretation of the weights would not be meaningful.

# Feature Importance

The importance of a feature in a linear regression model can be measured by the absolute value of its t-statistic. The t-statistic is the estimated weight scaled with its standard error.

```
|{t_{hat{beta}_j}=frac{hat{beta}_j}{SE(hat{beta}_j)}}|
```

Let us examine what this formula tells us: The importance of a feature increases with increasing weight. This makes sense. The more variance the estimated weight has (= the less certain we are about the correct value), the less important the feature is. This also makes sense.

# 4.1.2 Example

In this example, we use the linear regression model to predict the <u>number of rented bikes</u> on a particular day, given weather and calendar information. For the interpretation, we examine the estimated regression weights. The features consist of numerical and categorical features. For each feature, the table shows the estimated weight, the standard
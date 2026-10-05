
interval would include the true weight in 95 out of 100 cases, given that the linear regression model is the correct model for the data.

Whether the model is the “correct” model depends on whether the relationships in the data meet certain assumptions, which are linearity, normality, homoscedasticity, independence, fixed features, and absence of multicollinearity.

## Linearity

The linear regression model forces the prediction to be a linear combination of features, which is its greatest strength and its greatest limitation. Linearity leads to interpretable models. Linear effects are easy to quantify and describe. They are additive, so it is easy to separate the effects. If you suspect feature interactions or a nonlinear association of a feature with the target value, you can add interactions or use regression splines.

## Normality

It is assumed that the target outcome follows a normal distribution. If this assumption is violated, the estimated confidence intervals of the feature weights are invalid.

## Homoscedasticity (constant variance)

The variance of the error terms is assumed to be constant over the entire feature space. Suppose you want to predict the value of a house given the living area in meters. You estimate a linear model that assumes, regardless of the size of the house, the error around the predicted response has the same variance. This assumption is often violated in reality. In the house example, it is plausible that the variance of error around the predicted price is higher for larger houses, since prices are higher and there is more room for price fluctuations. Suppose the average error (difference between predicted and actual price) in your linear regression model is 50,000 Euros. If you assume homoscedasticity, you assume that the average error of 50,000 is the same for houses that cost 1 million and for houses that cost only 40,000. This is unreasonable because it would mean that we can expect negative house prices.

## Independence

It is assumed that each instance is independent of any other instance. If you perform measurements, as multiple blood tests per patient, the data points are not independent. For dependent data you need special linear regression models, such as mixed effects or GEEs. If you use the “normal” linear regression model, you might draw wrong conclusions from the model.

## Fixed features

The input features are considered “fixed”. Fixed means that they are treated as “given constants” and not as statistical variables. This implies that they are free of measurement errors. This is a rather unrealistic assumption. Without that assumption, however, you would have to fit very complex measurement models that account for the measurement errors of your input features. And usually you do not want to do that.

## Absence of multicollinearity

You do not want strongly correlated features, because this messes up the estimation of the weights. In a situation where two features are strongly correlated, it becomes problematic to estimate the weights because the feature effects are additive and it becomes indeterminable to which of the correlated features to attribute the effects.

## 4.1 LINEAR REGRESSION

### 4.1.1 Interpretation

The interpretation of a weight in the linear regression model depends on the type of the corresponding feature.

- Numerical feature: Increasing the numerical feature by one unit changes the estimated outcome by its weight. An example of a numerical feature is the size of a house.
- Binary feature: A feature that takes one of two possible values for each instance. An example is the feature “House comes with a garden”. One of values counts as the reference category (in some programming languages encoded with 0), such as “No garden”. Changing the feature from the reference category to the other category changes the estimated outcome by the feature's weight.
- Categorical feature with multiple categories. A feature with a fixed number of possible values. An example is the feature “floor type", "carpet", "laminate" and "parquet". A solution to deal with many categories is the one-hot-encoding, meaning each category has its own binary column. For a categorical feature with L categories, you only need L-1 columns as would have redundant information (e.g. when columns 1 to L-1 all have value 0 for one instance, we know that the categorical feature of this instance takes category L). The interpretation for each category is the same as the interpretation for binary features. Some languages, as R, allow you to encode features in various ways, as described later in this chapter.
- Intercept $\beta_0$: The intercept is the feature weight for the “constant feature", which is 1 for all instances. Most software packages automatically add this “1”-feature value at zero to estimate the intercept. The interpretation is: For instance with all numerical values at zero and the categorical values at reference categories, the model prediction is the intercept weight. The interpretation of the intercept is usually not relevant because all instances with values at zero make no sense. The interpretation is only meaningful when the features have been standardised (mean of zero, standard deviation of one). Then the intercept reflects the predicted outcome of an instance where all features are at their mean value.

The interpretation of the features in the linear regression model can be automated using following text templates.

## Interpretation of a Numerical Feature

An increase of feature $x_j$ by one unit increases the prediction for $y$ by $\beta_j$ units when all other feature values remain fixed.

## Interpretation of a Categorical Feature

Changing feature $x_k$ from the reference category to the other category increases the prediction for $y$ by $\beta_k$ when all other features remain fixed.

Another important measurement for interpreting linear models is the R-squared measurement. R-squared tells you how much of the total variance of your target output is explained by the model. The higher R-squared, the better your model explains the data. The formula for calculating R-squared is:

```
$R^2 = 1 - SSE/SST$$
```

SSE is the squared sum of the error terms:

```
$SSE = \sum_{i=1}^{n} (y^{(i)} - \hat{y}^{(i)})^2$
```

SST is the squared sum of the data variance:

```
$SST = \sum_{i=1}^{n} (y^{(i)} - \bar{y})^2$
```

The SSE tells you how much variance remains after fitting the linear model, which is measured by squared differences between the predicted and actual target values. SST is the total variance of the target outcome. R-squared tells you how much of your variance can be explained by the linear model. R-squared usually ranges between 0 and 1 for models where the model does not explain the data at all and 1 for models that explain all of the variance in your data. It is also possible for R-squared to take on a negative value without violating any mathematical rules. This happens when SSE is greater than SST which means that a model does not capture the trend of the data and fits to the data worse than using the mean of the target as the prediction.

There is a catch, R-squared does not tell you which features are important. The importance of a feature in the linear regression model can be measured by the t-statistic. The t-statistic is the estimated weight scaled by its standard error. The importance of a feature in the linear regression model can be measured by the absolute value of the t-statistic.

| Feature | SE | |t| |
| :--- | :--- | :--- |
| (Intercept) | 2399.4 | 10.1 |
| Spring | 899.3 | 7.4 |
| Summer | 138.2 | 161.7 |
| Fall | 425.6 | 108.8 |
| Holiday | -686.1 | 203.3 |
| Working Day | 124.9 | 73.3 |
| Misty | -379.4 | 87.6 |
| Rain/Snow/Storm | -1901.5 | 223.6 |
| Temp | 110.7 | 75.0 |
| Humidity | -17.4 | 3.2 |
| Windspeed | -42.5 | 6.9 |
| Days since 2011 | 4.9 | 0.2 | 28.5 |

$$ \frac{\beta_j}{SE(\beta_j)} $$

The importance of a feature increases with increasing weight. This makes sense. The more variance the estimated weight has (= less certain we are about the correct value), the less important the feature is.

## 4.1.2 Example

In this example, we use the linear regression model to predict the number of rented bikes on a particular day, given weather and calendar information. For the interpretation, we examine the estimated regression weights. The features consist of numerical and categorical features. For each feature, the table shows the estimated weight, the standard error of the estimate (SE), and the absolute value of the t-statistic (|t|).

Interpretation of a numerical feature (temperature): An increase of the temperature by 1 degree Celsius increases the predicted number of bicycles by 110.7, while all other features remain fixed.

Interpretation of a categorical feature (“weathersit”): The estimated number of bicycles is -1901.5 when it is raining, snowing or stormy, compared to good weather - assuming that all other features do not change. When the weather is misty, the predicted number of bicycles is -379.4 lower than good weather, given all other features remain the same.

All the interpretations come with the footnote “all other features remain the same”. This is because of the nature of linear regression models. The predicted target is a linear combination of the weighted features. The estimated linear equation is a hyperplane in

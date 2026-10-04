

We read this as "y is modeled as beta1 (`b1`) times `x`, plus a constant beta0 (`b0`), plus an error term `e`."

When you have multiple predictor variables, the equation can be written as `y = b0 + b1*x1 + b2*x2 + ... + bn*xn`, where:

* `b0` is the intercept,
* `b1`, `b2`, ..., `bn` are the regression weights or coefficients associated with the predictors `x1`, `x2`, ..., `xn`.
* `e` is the *error term* (also known as the *residual errors*), the part of `y` that can be explained by the regression model

Note that, `b0`, `b1`, `b2`, ... and `bn` are known as the regression beta coefficients or parameters.

The figure below illustrates a simple linear regression model, where:

* the best-fit regression line is in blue
* the intercept (`b0`) and the slope (`b1`) are shown in green
* the error terms (`e`) are represented by vertical red lines

![Linear regression](Image00000.jpg)

Linear regression

From the scatter plot above, it can be seen that not all the data points fall exactly on the fitted regression line. Some of the points are above the blue curve and some are below it; overall, the residual errors (`e`) have approximately mean zero.

The sum of the squares of the residual errors are called the **Residual Sum of Squares** or **RSS**.

The average variation of points around the fitted regression line is called the **Residual Standard Error** (**RSE**). This is one the metrics used to evaluate the overall quality of the fitted regression model. The lower the RSE, the better it is.

Since the mean error term is zero, the outcome variable `y` can be approximately estimated as follow:

`y ~ b0 + b1*x`

Mathematically, the beta coefficients (`b0` and `b1`) are determined so that the RSS is as minimal as possible. This method of determining the beta coefficients is technically called **least squares** regression or **ordinary least squares** (OLS) regression.

Once, the beta coefficients are calculated, a t-test is performed to check whether or not these coefficients are significantly different from zero. A non-zero beta coefficients means that there is a significant relationship between the predictors (`x`) and the outcome variable (`y`).

## 4.3 Loading Required R packages

* `tidyverse` for easy data manipulation and visualization
* `caret` for easy machine learning workflow

```
```

## 4.4 Preparing the data

We'll use the `marketing` data set, introduced in the Chapter [3](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX), for predicting sales units on the basis of the amount of money spent in the three advertising medias (`youtube`, `facebook` and `newspaper`)

We’ll randomly split the data into training set (80% for building a predictive model) and test set (20% for evaluating the model). Make sure to set seed for reproducibility.

```
```

```
##     youtube facebook newspaper sales
## 158     180     1.56      29.2  12.1
## 82      288     4.92      44.3  14.8
## 175     267     4.08      15.7  13.8
```

```
```

## 4.5 Computing linear regression

The R function `lm()` is used to compute linear regression model.

### 4.5.1 Quick start R code

```
```

### 4.5.2 Simple linear regression

The **simple linear regression** is used to predict a continuous outcome variable (`y`) based on one single predictor variable (`x`).

In the following example, we'll build a simple linear model to predict sales units based on the advertising budget spent on `youtube`. The regression equation can be written as `sales = b0 + b1*youtube`.

The R function `lm()` can be used to determine the beta coefficients of the linear model, as follow:

```
```

```
##             Estimate Std. Error t value Pr(>|t|)
## (Intercept)   8.3839    0.62442    13.4 5.22e-28
## youtube       0.0468    0.00301    15.6 7.84e-34
```

The output above shows the estimate of the regression beta coefficients (column `Estimate`) and their significance levels (column `Pr(>|t|)`). The intercept (`b0`) is 8.38 and the coefficient of `youtube` variable is 0.046.

The estimated regression equation can be written as follow: `sales = 8.38 + 0.046*youtube`. Using this formula, for each new `youtube` advertising budget, you can predict the number of sale units.

For example:

* For a `youtube` advertising budget equal zero, we can expect a sale of 8.38 units.
* For a `youtube` advertising budget equal 1000, we can expect a sale of 8.38 + 0.046*1000 = 55 units.

Predictions can be easily made using the R function `predict()`. In the following example, we predict sales units for two `youtube` advertising budget: 0 and 1000.

```
```

```
##     1     2 
##  8.38 55.19
```

### 4.5.3 Multiple linear regression

**Multiple linear regression** is an extension of simple linear regression for predicting an outcome variable (`y`) on the basis of multiple distinct predictor variables (`x`).

For example, with three predictor variables (`x`), the prediction of `y` is expressed by the following equation: `y = b0 + b1*x1 + b2*x2 + b3*x3`

The regression beta coefficients measure the association between each predictor variable and the outcome. "`b_j`" can be interpreted as the average effect on `y` of a one unit increase in "`x_j`", holding all other predictors fixed.

In this section, we'll build a multiple regression model to predict sales based on the budget invested in three advertising medias: `youtube`, `facebook` and `newspaper`. The formula is as follow: `sales = b0 + b1*youtube + b2*facebook + b3*newspaper`

You can compute the multiple regression model coefficients in R as follow:

```
```

Note that, if you have many predictor variables in your data, you can simply include all the available variables in the model using `~.`:

```
```

```
##             Estimate Std. Error t value Pr(>|t|)
## (Intercept)  3.39188    0.44062   7.698 1.41e-12
## youtube      0.04557    0.00159  28.630 2.03e-64
## facebook     0.18694    0.00989  18.905 2.07e-42
## newspaper    0.00179    0.00677   0.264 7.92e-01
```

From the output above, the coefficients table shows the beta coefficient estimates and their significance levels. Columns are:

* `Estimate`: the intercept (`b0`) and the beta coefficient estimates associated to each predictor variable
* `Std.Error`: the standard error of the coefficient estimates. This represents the accuracy of the coefficients. The larger the standard error, the less confident we are about the estimate.
* `t value`: the t-statistic, which is the coefficient estimate (column 2) divided by the standard error of the estimate (column 3)
* `Pr(>|t|)`: The p-value corresponding to the t-statistic. The smaller the p-value, the more significant the estimate is.

As previously described, you can easily make predictions using the R function `predict()`:

```
```

```
##   1 
## 283
```

## 4.6 Interpretation

Before using a model for predictions, you need to assess the statistical significance of the model. This can be easily checked by displaying the statistical summary of the model.

### 4.6.1 Model summary

Display the statistical summary of the model as follow:

```
```

```
## 
## Call:
## lm(formula = sales ~ ., data = train.data)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -10.412  -1.110   0.348   1.422   3.499 
## 
## Coefficients:
##             Estimate Std. Error t value Pr(>|t|)    
## (Intercept)  3.39188    0.44062    7.70  1.4e-12 ***
## youtube      0.04557    0.00159   28.63  < 2e-16 ***
## facebook     0.18694    0.00989   18.90  < 2e-16 ***
## newspaper    0.00179    0.00677    0.26     0.79    
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 2.12 on 158 degrees of freedom
## Multiple R-squared:  0.89,   Adjusted R-squared:  0.888 
## F-statistic:  427 on 3 and 158 DF,  p-value: <2e-16
```

The summary outputs shows 6 components, including:

* **Call**. Shows the function call used to compute the regression model.



The *Residuals vs Leverage* plot can help us to find influential observations if any. On this plot, outlying values are generally located at the upper right corner or at the lower right corner. Those spots are the places where data points can be influential against a regression line.

The following plots illustrate the Cook's distance and the leverage of our model:

```
```

![](Image00015.jpg)

By default, the top 3 most extreme values are labelled on the Cook's distance plot. If you want to label the top 5 extreme values, specify the option `id.n` as follow:

```
```

If you want to look at these top 3 observations with the highest Cook’s distance in case you want to assess them further, type this R code:

```
```

```
##   index sales youtube .fitted .resid   .hat .cooksd .std.resid
## 1    26  14.4     315    23.4  -9.04 0.0142  0.0389      -2.33
## 2    36  15.4     349    25.0  -9.66 0.0191  0.0605      -2.49
## 3   179  14.2     332    24.2 -10.06 0.0165  0.0563      -2.59
```

When data points have high Cook’s distance scores and are to the upper or lower right of the leverage plot, they have leverage meaning they are influential to the regression results. The regression results will be altered if we exclude those cases.

In our example, the data don't present any influential points. Cook’s distance lines (a red dashed line) are not shown on the Residuals vs Leverage plot because all points are well inside of the Cook’s distance lines.

Let's show now another example, where the data contain two extremes values with potential influence on the regression results:

```
```

Create the *Residuals vs Leverage* plot of the two models:

```
```

![](Image00016.jpg)

On the Residuals vs Leverage plot, look for a data point outside of a dashed line, Cook’s distance. When the points are outside of the Cook’s distance, this means that they have high Cook’s distance scores. In this case, the values are influential to the regression results. The regression results will be altered if we exclude those cases.

In the above example 2, two data points are far beyond the Cook’s distance lines. The other residuals appear clustered on the left. The plot identified the influential observation as #201 and #202. If you exclude these points from the analysis, the slope coefficient changes from 0.06 to 0.04 and R2 from 0.5 to 0.6. Pretty big impact!

### 9.13 Discussion

This chapter describes linear regression assumptions and shows how to diagnostic potential problems in the model.

The diagnostic is essentially performed by visualizing the residuals. Having patterns in residuals is not a stop signal. Your current regression model might not be the best way to understand your data.

Potential problems might be:

*   A non-linear relationships between the outcome and the predictor variables. When facing to this problem, one solution is to include a quadratic term, such as polynomial terms or log transformation. See Chapter [7](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX) .
*   Existence of important variables that you left out from your model. Other variables you didn’t include (e.g., age or gender) may play an important role in your model and data. See Chapter [11](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX) .
*   Presence of outliers. If you believe that an outlier has occurred due to an error in data collection and entry, then one solution is to simply remove the concerned observation.

# 10 Multicollinearity

## 10.1 Introduction

In multiple regression (Chapter [4](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX) ), two or more predictor variables might be correlated with each other. This situation is referred as *collinearity* .

There is an extreme situation, called **multicollinearity** , where collinearity exists between three or more variables even if no pair of variables has a particularly high correlation. This means that there is redundancy between predictor variables.

In the presence of multicollinearity, the solution of the regression model becomes unstable.

For a given predictor (p), multicollinearity can assessed by computing a score called the **variance inflation factor** (or **VIF** ), which measures how much the variance of a regression coefficient is inflated due to multicollinearity in the model.

The smallest possible value of VIF is one (absence of multicollinearity). As a rule of thumb, a VIF value that exceeds 5 or 10 indicates a problematic amount of collinearity (James et al. [2014](#text00039.html#ref-james2014) ) .

When faced to multicollinearity, the concerned variables should be removed, since the presence of multicollinearity implies that the information that this variable provides about the response is redundant in the presence of the other variables (James et al. [2014](#text00039.html#ref-james2014) ,P. Bruce and Bruce ([2017](#text00039.html#ref-bruce2017) ) ) .

This chapter describes how to detect multicollinearity in a regression model using R.

## 10.2 Loading Required R packages

*   `tidyverse` for easy data manipulation and visualization
*   `caret` for easy machine learning workflow

```
```

## 10.3 Preparing the data

We'll use the `Boston` data set [in `MASS` package], introduced in Chapter [3](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX) , for predicting the median house value (`mdev` ), in Boston Suburbs, based on multiple predictor variables.

We’ll randomly split the data into training set (80% for building a predictive model) and test set (20% for evaluating the model). Make sure to set seed for reproducibility.

```
```

## 10.4 Building a regression model

The following regression model include all predictor variables:

```
```

```
##   RMSE   R2
## 1 4.99 0.67
```

## 10.5 Detecting multicollinearity

The R function `vif()` [car package] can be used to detect multicollinearity in a regression model:

```
```

```
##    crim      zn   indus    chas     nox      rm     age     dis     rad 
##    1.87    2.36    3.90    1.06    4.47    2.01    3.02    3.96    7.80 
##     tax ptratio   black   lstat 
##    9.16    1.91    1.31    2.97
```

In our example, the VIF score for the predictor variable `tax` is very high (VIF = 9.16). This might be problematic.

## 10.6 Dealing with multicollinearity

In this section, we'll update our model by removing the the predictor variables with high VIF value:

```
```

```
##   RMSE    R2
## 1 5.01 0.671
```

It can be seen that removing the `tax` variable does not affect very much the model performance metrics.

## 10.7 Discussion

This chapter describes how to detect and deal with multicollinearity in regression models. Multicollinearity problems consist of including, in the model, different variables that have a similar predictive relationship with the outcome. This can be assessed for each predictor by computing the VIF value.

Any variable with a high VIF value (above 5 or 10) should be removed from the model. This leads to a simpler model without compromising the model accuracy, which is good.

Note that, in a large data set presenting multiple correlated predictor variables, you can perform principal component regression and partial least square regression strategies. See Chapter [20](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX) .

# 11 Confounding Variables

A **Confounding variable** is an important variable that should be included in the predictive model but you omit it.Naive interpretation of such models can lead to invalid conclusions.

For example, consider that we want to model life expentency in different countries based on the GDP per capita, using the `gapminder` data set:

```
```

In this example, it is clear that the continent is an important variable: countries in Europe are estimated to have a higher life expectancy compared to countries in Africa. Therefore, continent is a confounding variable that should be included in the model:

```
```

# 12 Introduction

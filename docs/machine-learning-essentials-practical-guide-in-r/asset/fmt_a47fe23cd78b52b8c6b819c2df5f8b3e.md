
When building a regression model (Chapter [4](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX) ), you need to evaluate the goodness of the model, that is how well the model fits the training data used to build the model and how accurate is the model in predicting the outcome for new unseen test observations.

In this part, you'll learn techniques for assessing regression model accuracy and for validating the performance of the model. We'll also provide practical examples in R.

The following chapters are covered:

*   Regression Model Accuracy Metrics (Chapter [13](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX) ) for measuring the performance of a regression model.
*   Cross-validation (Chapter [14](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX) ) and bootstrap resampling (Chapter [15](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX) ) for validating the model on a test data.

# 13 Regression Model Accuracy Metrics

## 13.1 Introduction

In this chapter we'll describe different statistical regression `metrics` for measuring the performance of a regression model (Chapter [4](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX) ).

Next, we'll provide practical examples in R for comparing the performance of two models in order to select the best one for our data.

## 13.2 Model performance metrics

In regression model, the most commonly known evaluation metrics include:

1.  `R-squared` (`R2`), which is the proportion of variation in the outcome that is explained by the predictor variables. In multiple regression models, `R2` corresponds to the squared correlation between the observed outcome values and the predicted values by the model. The Higher the `R-squared`, the better the model.

2.  `Root Mean Squared Error` (`RMSE`), which measures the average error performed by the model in predicting the outcome for an observation. Mathematically, the `RMSE` is the square root of the `mean squared error (MSE)`, which is the average squared difference between the observed actual outome values and the values predicted by the model. So, `MSE = mean((observeds - predicteds)^2)` and `RMSE = sqrt(MSE)`. The lower the `RMSE`, the better the model.

3.  `Residual Standard Error` (`RSE`), also known as the `model sigma`, is a variant of the `RMSE` adjusted for the number of predictors in the model. The lower the `RSE`, the better the model. In practice, the difference between `RMSE` and `RSE` is very small, particularly for large multivariate data.

4.  `Mean Absolute Error` (`MAE`), like the `RMSE`, the `MAE` measures the prediction error. Mathematically, it is the average absolute difference between observed and predicted outcomes, `MAE = mean(abs(observeds - predicteds))`. `MAE` is less sensitive to outliers compared to `RMSE`.

The problem with the above metrics, is that they are sensible to the inclusion of additional variables in the model, even if those variables dont have significant contribution in explaining the outcome. Put in other words, including additional variables in the model will always increase the `R2` and reduce the `RMSE`. So, we need a more robust metric to guide the model choice.

Concerning `R2`, there is an adjusted version, called `Adjusted R-squared`, which adjusts the `R2` for having too many variables in the model.

Additionally, there are four other important metrics - `AIC`, `AICc`, `BIC` and `Mallows Cp` - that are commonly used for model evaluation and selection. These are an unbiased estimate of the model prediction error `MSE`. The lower these metrics, he better the model.

1.  `AIC` stands for (`Akaike’s Information Criteria`), a metric developped by the Japanese Statistician, Hirotugu Akaike, 1970. The basic idea of `AIC` is to penalize the inclusion of additional variables to a model. It adds a penalty that increases the error when including additional terms. The lower the `AIC`, the better the model.

2.  `AICc` is a version of `AIC` corrected for small sample sizes.

3.  `BIC` (or `Bayesian information criteria`) is a variant of `AIC` with a stronger penalty for including additional variables to the model.

4.  `Mallows Cp`: A variant of `AIC` developed by Colin Mallows.

Generally, the most commonly used metrics, for measuring regression model quality and for comparing models, are: `Adjusted R2`, `AIC`, `BIC` and `Cp`.

In the following sections, we'll show you how to compute these above mentionned metrics.

## 13.3 Loading required R packages

*   `tidyverse` for data manipulation and visualization
*   `modelr` provides helper functions for computing regression model performance metrics
*   `broom` creates easily a tidy data frame containing the model statistical metrics

```
```

## 13.4 Example of data

We'll use the built-in R `swiss` data, introduced in the Chapter [3](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX), for predicting fertility score on the basis of socio-economic indicators.

```
```

## 13.5 Building regression models

We start by creating two models:

1.  Model 1, including all predictors
2.  Model 2, including all predictors except the variable Examination

```
```

## 13.6 Assessing model quality

There are many R functions and packages for assessing model quality, including:

*   `summary()` [stats package], returns the `R-squared`, adjusted `R-squared` and the `RSE`
*   `AIC()` and `BIC()` [stats package], computes the `AIC` and the `BIC`, respectively

```
```

*   `rsquare()`, `rmse()` and `mae()` [modelr package], computes, respectively, the `R2`, `RMSE` and the `MAE`.

```
```

*   `R2()`, `RMSE()` and `MAE()` [caret package], computes, respectively, the `R2`, `RMSE` and the `MAE`.

```
```

*   `glance()` [broom package], computes the `R2`, adjusted `R2`, sigma (`RSE`), `AIC`, `BIC`.

```
```

*   Manual computation of `R2`, `RMSE` and `MAE`:

```
```

## 13.7 Comparing regression models performance

Here, we'll use the function `glance()` to simply compare the overall quality of our two models:

```
```

```
##   adj.r.squared sigma AIC BIC  p.value
## 1         0.671  7.17 326 339 5.59e-10
```

```
```

```
##   adj.r.squared sigma AIC BIC  p.value
## 1         0.671  7.17 325 336 1.72e-10
```

From the output above, it can be seen that:

1.  The two models have exactly the samed `adjusted R2` (0.67), meaning that they are equivalent in explaining the outcome, here fertility score. Additionally, they have the same amount of `residual standard error` (`RSE` or sigma = 7.17). However, the model 2 is more simple than model 1 because it incorporates less variables. All things equal, the simple model is always better in statistics.

2.  The `AIC` and the `BIC` of the model 2 are lower than those of the model1. In model comparison strategies, the model with the lowest `AIC` and `BIC` score is preferred.

3.  Finally, the F-statistic p.value of the model 2 is lower than the one of the model 1. This means that the model 2 is statistically more significant compared to model 1, which is consistent to the above conclusion.

Note that, the `RMSE` and the `RSE` are measured in the same scale as the outcome variable. Dividing the `RSE` by the average value of the outcome variable will give you the prediction error rate, which should be as small as possible:

```
```

```
## [1] 0.102
```

In our example the average prediction error rate is 10%.

## 13.8 Discussion

This chapter describes several metrics for assessing the overall performance of a regression model.

The most important metrics are the `Adjusted R-square`, `RMSE`, `AIC` and the `BIC`. These metrics are also used as the basis of model comparison and optimal model selection.

Note that, these regression metrics are all internal measures, that is they have been computed on the same data that was used to build the regression model. They tell you how well the model fits to the data in hand, called training data set.

In general, we do not really care how well the method works on the training data. Rather, we are interested in the accuracy of the predictions that we obtain when we apply our method to previously unseen test data.

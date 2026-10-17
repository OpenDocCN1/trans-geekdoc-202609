
```
#> 17 14 25.7 0.0001
#> 18 14 25.7 0.0001
#> 19 15 25.7 0.0001
#> 20 15 25.7 0.0000
```

We can extract the model for a particular value of \(\lambda\) using the `coef()` function. The argument `s` specifies the value of \(\lambda\). For the particular value of \(\lambda\) chosen in the following code, only age has a non-zero coefficient. Note that the `coef()` function returns the coefficients on the original scale.

```
coef(mod_lasso, s = 0.045920)
#> 16 x 1 sparse Matrix of class "dgCMatrix"
#>                   s1
#> (Intercept)    4.75241
#> AGE            0.00121
#> SEXFemale      .
#> RACEOther Hispanic .
#> RACENon-Hispanic White .
#> RACENon-Hispanic Black .
#> RACEOther Race   .
#> EDUCATIONHS      .
#> EDUCATIONMoreThanHS .
#> INCOME           .
#> SMOKEQuitSmoke   .
#> SMOKEStillSmoke .
#> LEAD             .
#> BMI_CAT25<BMI<30 .
#> BMI_CATBMI>=30   .
#> ALCYes           .
```

We can also use the `predict()` function to predict blood pressure for this particular model. In the function call, we have specified our value of \(\lambda\) as well as our data matrix `x` as the data to predict on.

```
pred_lasso <- predict(mod_lasso, s = 0.045920, newx = x)
```

This shows our observed model fit for a fairly high penalty term. In order to choose the best value of \(\lambda\), we use 5-fold cross-validation. First, we randomly assign each observation to one of five folds using the `sample()` function. We can see that this splits the data into folds of roughly equal size.

```
set.seed(1)
foldid <- sample(1:5, size = nrow(x), replace = TRUE)
table(foldid)
#> foldid
#> 1 2 3 4 5
#> 6081 5967 6048 6188 6121
```

Next, we call the cv.glmnet() function which implements k-fold cross-validation across a grid of lambda values. Similar to before, we specified x, y, and alpha = 1. This time, we also include the measure to use for cross-validation (mse indicates mean squared error) and provide the fold vector foldid. If you do not want to provide folds, you can instead use the nfolds argument to specify the number of folds desired and the cv.glmnet() function will create them. Plotting the returned object shows us the estimated mean squared error for different values of lambda as well as error bars for each estimate. Similar to before, it also shows the number of non-zero coefficients at the top.

```
cv_lasso <- cv.glmnet(x, y, foldid = foldid, alpha = 1,
type.measure = "mse")
plot(cv_lasso)
```

![](img/58a554e865d49ca347d9a3f76f8f0812_259_0.png)

There are two vertical dashed lines included in the plot. These correspond to two values of lambda that are stored in our object. The first is lambda.min. This corresponds to the lambda value with the lowest estimated mean squared error. The other is lambda.1se. This corresponds to the largest lambda value whose estimated mean squared error is within one standard error of the lowest value. As indicated in the plot, this corresponds to a model with fewer included coefficients and higher regularization.

We use the `lambda.min` value as our chosen \(\lambda\) value. To extract the coefficients corresponding to this \(\lambda\) value we again use the `coef()` function. However, this \(\lambda\) might not be one of the initial 25 used for our `mod_lasso` object. In this case, the `coef()` function uses linear interpolation to get the estimated coefficients. If we want to refit our model for this particular value of \(\lambda\), we can instead specify the argument `exact = TRUE` and provide x and y.

```r
lasso_coef <- coef(mod_lasso, s = cv_lasso$lambda.min,
                   exact = TRUE, x = x, y = y)

lasso_coef
#> 16 x 1 sparse Matrix of class "dgCMatrix"
#>
#>                    s1
#> (Intercept)   4.63458
#> AGE           0.00367
#> SEXFemale    -0.02652
#> RACEOther Hispanic -0.00677
#> RACENon-Hispanic White -0.00531
#> RACENon-Hispanic Black  0.03257
#> RACEOther Race   0.00493
#> EDUCATIONHS      .
#> EDUCATIONMoreThanHS -0.00942
#> INCOME          -0.00396
#> SMOKEQuitSmoke   -0.00753
#> SMOKEStillSmoke  -0.00397
#> LEAD             0.00880
#> BMI_CAT25<BMI<30 0.01452
#> BMI_CATBMI>=30   0.03688
#> ALCYes           0.00547
```

We now repeat the same process for a model with \(\alpha = 0\) and \(\alpha = 0.5\). In this case, we call the `glmnet()` function with our chosen \(\lambda\) value to find the coefficients. This is equivalent to what we did for our lasso model. Last, we create a data frame with the estimated coefficients for each model. The `coef()` function returns a matrix, so this requires converting these to numeric vectors.

```r
# cross-validation using same folds
cv_ridge <- cv.glmnet(x, y, foldid = foldid, alpha = 0,
                      type.measure = "mse")

cv_elastic <- cv.glmnet(x, y, foldid = foldid, alpha = 0.5,
                        type.measure = "mse")
```

```
# Refit model on full data with chosen lambda
mod_ridge <- glmnet(x, y, alpha = 0, lambda = cv_ridge$lambda.min)
mod_elastic <- glmnet(x, y, alpha = 0.5, lambda = cv_ridge$lambda.min)

# extract coefficients for a table
res_coef <- data.frame(name = c("Intercept", colnames(x)),
       lasso = round(as.numeric(lasso_coef), 3),
       ridge = round(as.numeric(coef(mod_ridge)), 3),
       elastic = round(as.numeric(coef(mod_elastic)),
       3))
```

| name | lasso | ridge | elastic |
|---|---|---|---|
| Intercept | 4.635 | 4.646 | 4.650 |
| AGE | 0.004 | 0.003 | 0.003 |
| SEXFemale | -0.027 | -0.025 | -0.020 |
| RACEOther Hispanic | -0.007 | -0.007 | 0.000 |
| RACENon-Hispanic White | -0.005 | -0.005 | -0.002 |
| RACENon-Hispanic Black | 0.033 | 0.031 | 0.027 |
| RACEOther Race | 0.005 | 0.004 | 0.000 |
| EDUCATIONHS | 0.000 | 0.000 | 0.000 |
| EDUCATIONMoreThanHS | -0.009 | -0.010 | -0.006 |
| INCOME | -0.004 | -0.004 | -0.002 |
| SMOKEQuitSmoke | -0.008 | -0.006 | 0.000 |
| SMOKEStillSmoke | -0.004 | -0.005 | 0.000 |
| LEAD | 0.009 | 0.011 | 0.008 |
| BMI_CAT25<=BMI<30 | 0.015 | 0.014 | 0.000 |
| BMI_CATBMI>=30 | 0.037 | 0.035 | 0.022 |
| ALCYes | 0.005 | 0.004 | 0.000 |

The coefficients between the models are not so different. We can also compare their mean squared errors, which are also similar. Since our lasso model was fit on a grid of \(\lambda\) values, we again have to specify this value.

```
mean((nhanes$SBP - exp(predict(mod_lasso, newx = x,
             s = cv_lasso$lambda.min)))^2)
#> [1] 268
mean((nhanes$SBP - exp(predict(mod_ridge, newx = x)))^2)
#> [1] 268
mean((nhanes$SBP - exp(predict(mod_elastic, newx = x)))^2)
#> [1] 270
```

### 15.3 Best Subset

The second package we introduce in this chapter is one that allows us to fit models with an L0 penalty term. The package **L0learn** considers penalties of the following forms.

- L0 only: λ‖β‖₀
- L0L1: λ‖β‖₀ + γ‖β‖₁
- L0L2: λ‖β‖₀ + γ‖β‖₂²

To fit a model with an L0 penalty term, we use the `L0learn.fit()` function. Similar to `glmnet()`, we need to specify our input matrix x and response vector y as well as our penalty using the `penalty` argument. We can also specify a number of λ values to consider `nLambda` and specify the family through the loss function `loss`.

```r
mod_l0 <- L0learn.fit(x, y, penalty = "L0", loss = "SquaredError",
                     nLambda = 20)
```

Plotting the returned object also shows how the coefficients for each variable change with the penalty term, given by the support size or number of non-zero coefficients in this case. We can also print the returned object to see the different values of λ used and the corresponding number of included variables.

```r
plot(mod_l0)
```

![](img/58a554e865d49ca347d9a3f76f8f0812_263_0.png)

| lambda | gamma | suppSize |
|---|---|---|
| 1.08e-01 | 0 | 0 |
| 1.07e-01 | 0 | 1 |
| 6.51e-03 | 0 | 2 |
| 5.00e-03 | 0 | 3 |
| 4.22e-03 | 0 | 4 |
| 1.75e-03 | 0 | 5 |
| 5.36e-04 | 0 | 7 |
| 3.23e-04 | 0 | 8 |
| 1.92e-04 | 0 | 9 |
| 1.42e-04 | 0 | 10 |
| 1.04e-04 | 0 | 11 |
| 6.80e-05 | 0 | 12 |

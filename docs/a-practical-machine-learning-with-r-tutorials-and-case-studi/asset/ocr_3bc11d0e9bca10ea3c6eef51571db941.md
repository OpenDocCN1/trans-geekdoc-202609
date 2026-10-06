# 6 Polynomial Regression — Overfitting/Tuning Explained

```
##
## -- Model -
##
## Call:
## ## stats::lm(formula = ..y ~ ., data = data)
##
## Coefficients:
## (Intercept) Sqft_poly_1 Sqft_poly_2 Sqft_poly_3
## -1.30e+04 6.57e-02 -4.90e-01 2.05e-04
## Sqft_poly_4 Sqft_poly_5 Sqft_poly_6
## -1.76e-08 3.18e-12 -9.93e-07
```

The printout above from the fitted workflow confirms that WFModelHouses is a fitted workflow because it contains the values for estimated parameters (see Coefficients). Consequently, WFModelHouses can be used for predictions. We use the augment() command to predict based on the testing dataset and to calculate the metrics:

```
DataTestWithBestModel=augment(BestWFModelHouses, DataTest)
metrics(DataTestWithBestModel, true.pred, estimate=pred)

## # A tible: 3 x3
## .metric .estimate
## <chr> <chr> <dbl>
## # 1 rmse standard 240806.
## # 2 rsq standard 0.586
## # 3 mae standard 164987.
```

Given that we used a univariate model with Sqft to vary the vari, the results look quite good. Based on the testing data r² = 0.5857. The mean average error shows that housing price is, on average, under/overestimated variable could result in a mean average error of $164,957 (for comparison, a linear model with Sqft as the only predictor $173,000 based on the testing data).

Figure 6.6 illustrates how the Degree-6 Polynomial Model (magenta line) performs better than a linear regression (blue line) and why it does not lead to overfitting. Although a polynomial function of Degree-6 is potentially very flexible, you can see in Figure 6.6 it differs only slightly from the linear prediction function for houses smaller than 3,000 sqft. For houses larger than 3,000 sqft, the Degree-6 prediction function estimates higher valued houses much better than the linear function.
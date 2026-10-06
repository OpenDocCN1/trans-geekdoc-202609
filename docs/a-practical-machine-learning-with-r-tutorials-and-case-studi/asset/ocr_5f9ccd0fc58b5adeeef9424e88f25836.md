# 7.4 The Idea Behind Regularization

The *recipe* that creates the various powers of the *Sqft* and normalizes the resulting predictors, we again use the *recipe* from Section 7.3.

Since the workflow Ridge is a fitted workflow model (it was calibrated with the training data), we can extract the model parameters with the tidy command:

```
tidy(WFModelRidge)

## A tibble: 6 x 3
## term estimate penalty
## <chr> <dbl>
## 1 (Intercept) 509945. 1.000000
## 2 Sqft 25790.0 1.000000
## 3 Sqft2 23133.0 1.000000
## 4 Sqft3 19885.0 1.000000
## 5 Sqft4 16968.0 1.000000
## 6 Sqft5 14970.0 1.000000
```

The $eta$ parameters (se column estimate) are smaller than the ones from the unregularized benchmark in Section 7.3. However, none of the $eta$-parameters are equal to zero. None of the predictor variables are eliminated. There is a major difference between Ridge and Lasso.

To evaluate the *Ridge* model's predictive quality and to compare the performance with the benchmark model from Section 7.3 and the *Lasso* model from Section 7.4.1 we calculate the model's *metrics* based on the testing data:

```
DataTestWithRidge<-augmentation(WFModelRidge, DataTest)
metrics(DataTestWithRidge,truth=Price, estimate=pred)
```

```
## A tibble: 3 x 3
## .estimator .estimate
## <chr> <dbl>
## 1 mse standard 336485.
## 2 roq standard 0.237
## 3 mae standard 186431.
```

Let us look at the average overestimation/underestimation of the house prices (mae) and compare the *Ridge* model to the *Lasso* model. You can see that based on the testing data, the *mae* for the *Ridge* model is about $186,400 which is lower than the one for the *Lasso* model ($303,100). Both models outperform by far the unregularized model from Section 7.3, which produced a testing data *mae* of about $1,719,500, likely due to overfitting.
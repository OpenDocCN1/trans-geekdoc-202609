```
xgb_test <- testing_sample %>%
 dplyr::select(all_of(features_short))) %>%
 as.matrix()
 mean((predict(fit_xgb, xgb.test) - testing_sample$RIM_Usd)^2) # MSE
```

## [1] 0.03908855

```
mean(predict(fit_xgb, xgb_test) * testing_sample$RIM_Usd > 0) # Hit ratio
```

## [1] 0.5077626

The performance is comparable to those observed for other predictive tools. As a final exercise, we show one implementation of a classification task under XGBoost. Only the label changes. In XGBoost, labels must be coded with integer number, starting at zero exactly. In R, factors are numerically coded as integer numbers starting from one, hence the mapping is simple.

```
train_label_C <- training_sample %>%
 filter(RIM_Usd < quantile(RIM_Usd, 0.2) |
 RIM_Usd > quantile(RIM_Usd, 0.8)) %>% # Either low 20% returns
 dplyr::select(RIM_Usd_C)
 train_matrix_XC <- xgb.DMatrix(data = train_features_xgb,
 label = as.numeric(train_label_C == "TRUE")) # XGB format!
```

When working with categories, the loss function is usually the softmax function (see Section 1.1).

```
fit_xgb_C <- xgb.train(data = train_matrix_XC, # Data source (pipe input)
 eta = 0.8, # Learning rate
 objective = "multi:softmax", # Objective function
 num_class = 2, # Number of classes
 max_depth = 4, # Maximum depth of trees
 nrounds = 10, # Number of trees used
 verbose = 0 # No warning message
 )
```

We can then proceed to the assessment of the quality of the model. We adjust the prediction to the value of the true label and count the proportion of accurate forecasts.

```
mean(predict(fit_xgb_C, xgb_test) + 1 == as.numeric(testing_sample$RIM_Usd_C)) # Hit ratio
```

## [1] 0.495613

Consistently with the previous classification attempts, the results are underwhelming, as if switching to binary labels incurred a loss of information.

# 6.4.7 Instance weighting

In the computation of the aggregate loss, it is possible to introduce some flexibility and assign weights to instances:

```
O = \sum_{i=1}^I W_i \times loss(y_i, \hat{y}_i) + \sum_{j=1}^J \Omega(T_j) .
 \text{weighted error term} \qquad \text{regularization term (unchanged)}
```

## 6.4 Boosted trees: extreme gradient boosting

coding sections dedicated to boosted trees in this book, the models will be trained with only 7 features.

```
library(xgboost) # The package for boosted trees
train_features_xgb <- training_sample %>%
  filter(RIM_USd < quantile(RIM_USd, 0.2) |
       RIM_USd > quantile(RIM_USd, 0.8)) %>% # Extreme values only!
dplyr::select(all_of(features_short)) %>% as.matrix() # Independent variable
train_label_xgb <- training_sample %>%
  filter(RIM_USd < quantile(RIM_USd, 0.2) |
       RIM_USd > quantile(RIM_USd, 0.8)) %>%
  dplyr::select(RIM_USd) %>% as.matrix() # Dependent variable
train_matrix_xgb <- xgb.DMatrix(data = train_features_xgb,
                  label = train_label_xgb) # XGB format!
```

The second (optional) step is to determine the monotonicity constraints that we want to impose. For simplicity, we will only enforce three constraints on

- 1. market capitalization (negative, because large firms have smaller returns under the size anomaly);
- 2. price-to-book ratio (negative, because overvalued firms also have smaller returns under the value anomaly);
- 3. past annual returns (positive, because winners outperform losers under the momentum anomaly).

```
mono_const <- rep(0, length(features)) # Initialize the vector
mono_const[which(features == "Mkt_Cap_12M_USd")] <- (-1) # Decreasing in market cap
mono_const[which(features == "Pb")] <- (-1) # Decreasing in price-to-book
mono_const[which(features == "Mom_11M_USd")] <- 1 # Increasing in past return
```

The third step is to train the model on the formatted training data. We include the monotonicity constraints and the DART feature (via rate_drop). Just like random forests, boosted trees can grow individual trees on subsets of the data: both row-wise (by selecting random instances) and column-wise (by keeping a smaller portion of predictors). These options are implemented below with the subsample and colsample_bytree in the arguments of the function.

```
fit_xgb <- xgb.train(data = train_matrix_xgb, # Data source
                  eta = 0.3, # Learning rate
                  objective = "reg:linear", # Objective function
                  max_depth = 4, # Maximum depth of trees
                  subsample = 0.6, # Train on random 60% of sample
                  colsample_bytree = 0.7, # Train on random 70% of predictors
                  lambda = 1, # Penalisation of leaf values
                  gamma = 0.1, # Penalisation of number of leaves
                  nrounds = 30, # Number of trees used (rather low here)
                  monotone_constraints = mono_const, # Monotonicity constraints
                  rate_drop = 0.1, # Drop rate for DART
                  verbose = 0 # No comment from the algo
                  )
```

Finally, we evaluate the performance of the model. Note that before that, a proper formatting of the testing sample is required.

```
xgb_test <- testing_sample %>%
 dplyr::select(all_of(features_short)) %>%
 as.matrix()
 mean((predict(fit_xgb, xgb_test) - testing_sample$RIM_Usd)^2) # MSE
```

[1] 0.03908855

```
mean(predict(fit_xgb, xgb_test) * testing_sample$RIM_Usd > 0) # Hit ratio
```

[1] 0.5077626

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

[1] 0.495613

Consistently with the previous classification attempts, the results are underwhelming, as if switching to binary labels incurred a loss of information.

### 6.4.7 Instance weighting

In the computation of the aggregate loss, it is possible to introduce some flexibility and assign weights to instances:

```
O = \sum_{i=1}^I W_i \times loss(y_i, \hat{y}_i) + \sum_{j=1}^J \Omega(T_j) .
 \text{weighted error term} \qquad \text{regularization term (unchanged)}
```

## 6.6 Discussion

In factor investing, these weights can very well depend on the feature values (\(W_i = \mathcal{W}_i(\mathbf{x}_i)\)). For instance, for one particular characteristic \(\mathbf{x}^k\), weights can be increasing thereby giving more importance to assets with high values of this characteristic (e.g., value stocks are favored compared to growth stocks). One other option is to increase weights when the values of the characteristic become more extreme (deep value and deep growth stocks have larger weights). If the features are uniform, the weights can simply be \(\mathcal{W}_i(x_i^k) \propto |x_i^k - 0.5|\): firms with median value 0.5 have zero weight and as the feature value shifts towards 0 or 1, the weight increases. Specifying weights on instances biases the learning process just like views introduced à la Black and Litterman (1992) influence the asset allocation process. The difference is that the nudge is performed well ahead of the portfolio choice problem.

In xgboost, the implementation instance weighting is done very early, in the definition of the xgb.DMatrix:

```
inst_weights <- runif(nrow(train_features_xgb)) # Random weights
inst_weights <- inst_weights / sum(inst_weights) # Normalization
train_matrix_xgb <- xgb.DMatrix(data = train_features_xgb,
                                label = train_label_xgb,
                                weight = inst_weights) # Weights!
```

Then, in the subsequent stages, the optimization will be performed with these hard-coded weights. The splitting points can be altered (via the total weighted loss in clusters) and the terminal weight values (6.5) are also impacted.

## 6.5 Discussion

We end this chapter by a discussion on the choice of predictive engine with a view towards portfolio construction. As recalled in Chapter 2, the ML signal is just one building stage of construction of the investment strategy. At some point, this signal must be translated into portfolio weights.

From this perspective, simple trees appear suboptimal. Tree depths are usually set between 3 and 6. This implies between 8 and 64 terminal leaves at most, with possibly very unbalanced clusters. The likelihood of having one cluster with 20% to 30% of the sample is high. This means that when it comes to predictions, roughly 20% to 30% of the instances will be given the same value.

On the other side of the process, portfolio policies commonly have a fixed number of assets. Thus, having assets with equal signals does not permit to discriminate and select a subset to be included in the portfolio. For instance, if the policy requires exactly 100 stocks and 105 stocks have the same signal, the signal cannot be used for selection purposes. It would have to be combined with exogenous information such as the covariance matrix in a mean-variance type allocation.

Overall, this is one reason to prefer aggregate models. When the number of learners is sufficiently large (5 is almost enough), the predictions for assets will be unique and tailored to these assets. It then becomes possible to discriminate via the signal and select only those assets that have the most favorable signal. In practice, random forests and boosted trees are probably the best choices.

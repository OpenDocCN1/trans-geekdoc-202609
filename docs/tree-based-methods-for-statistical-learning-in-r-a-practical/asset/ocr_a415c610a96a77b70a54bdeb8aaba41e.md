XGBoost does not work with R data frames. The `xgb.train()` function, in particular, only accepts data as an "xgb.DMatrix" object. An XGBoost DMatrix is an internal data structure used by XGBoost, which is optimized for both memory efficiency and training speed; see `?xgboost::xgb.DMatrix` for details. We can create such an object using the **xgboost** function `xgb.DMatrix()` (note that I separate the predictors and response in the calls to `xgb.DMatrix()`):

```
library(xgboost)

xnames <- setdiff(names(bank.ohе), "y")
dm.trn <- xgb.DMatrix(bank.trn[, xnames], label = bank.trn[, "y"])
dm.tst <- xgb.DMatrix(bank.tst[, xnames], label = bank.tst[, "y"])
```

XGBoost has a lot of parameters, so it can be helpful to construct a list of such for use when calling the fitting function `xgb.train()`. Below, I create a list containing several boosting and tree-specific parameters:

```
params <- list(
  eta = 0.01, # shrinkage/learning rate
  max_depth = 3,
  subsample = 0.5,
  objective = "binary:logistic", # for predicted probabilities
  eval_metric = "rmse", # square root of Brier score
  nthread = 8
)
```

Finally, I can fit an XGBoost model. I'll fit two in total, one without early stopping and one with, starting with the no early stopping version below. But first, I'll define a "watch list," which is just a named list of data sets to use for evaluating model performance after each iteration that we can use to determine the optimal number of trees ($k$-fold cross-validation could also be used via **xgboost**'s `xgb.cv()` function):

```
watch.list <- list(train = dm.trn, eval = dm.tst)

# Train an XGBoost model without early stopping
set.seed(1100) # for reproducibility
bank.xgb.1 <-
  xgb.train(params, data = dm.trn, nrounds = 3000, verbose = 0,
            watchlist = watch.list)

(best.iter <- which.min(bank.xgb.1$evaluation_log$eval_rmse))

#> [1] 1296
```

Out of 3,000 total iterations, we really only needed to build 1,296 trees, which can be expensive for large data sets (regardless of which fancy scalable implementation you use). While XGBoost is incredibly efficient, it is still wasteful to fit more trees than potentially necessary. To that end, I can turn on early stopping (Section 8.3.1.1) to halt performance once it detects
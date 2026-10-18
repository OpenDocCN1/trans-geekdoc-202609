# Listing 8.9 Plotting individual decision trees

```
```r
outer <- makeResampleDesc("CV", iters = 3)

xgbWrapper <- makeTuneWrapper("classif.xgboost",
                              resampling = cvForTuning,
                              par.set = xgbParamSpace,
                              control = randSearch)

cvWithTuning <- resample(xgbWrapper, xgbTask, resampling = outer)

cvWithTuning

Resample Result
Task: zooXgb
Learner: classif.xgboost.tuned
Aggr perf: mmce.test.mean=0.0390
Runtime: 890.2
```
```

Phenomenal! The cross-validation estimates our model has an accuracy of *1 − 0.039 = 0.961 = 96.1%!* Go XGBoost!

# 8.4 Strengths and weaknesses of tree-based algorithms

While it often isn’t easy to tell which algorithms will perform well for a given task, here are some strengths and weaknesses that will help you decide whether random forest or XGBoost will perform well for your task.

The strengths of the random forest and XGBoost algorithms are:

+   - They can handle categorical and continuous predictor variables (though XGBoost requires some numerical encoding)
+   - They make no assumptions about the distribution of the predictor variables
+   - They can handle missing values in sensible ways
+   - They can handle continuous variables on different scales
+   - Ensemble techniques can drastically improve model performance over individual trees and XGBoost in particular is excellent at reducing both bias and variance

The weaknesses of tree-based algorithm are:

+   - Random forest reduces variance compared to rpart, but does not reduce bias (XGBoost reduces both)
+   - XGBoost can be computationally expensive to tune as it has many hyperparameters and grows trees sequentially

# 8.5 Benchmarking algorithms against each other

In this section I’ll teach you what *benchmarking* is and we’ll use it to compare the performance of several algorithms on a particular task.

The classification drawer of your machine learning toolbox has lots of algorithms in it now!
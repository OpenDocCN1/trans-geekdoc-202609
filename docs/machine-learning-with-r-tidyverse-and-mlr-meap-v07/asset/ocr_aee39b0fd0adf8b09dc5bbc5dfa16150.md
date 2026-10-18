```
gamTask <- makeRegrTask(data = ozoneForGam, target = "Ozone")
imputeMethod <- imputeLearner("regr.rpart")
gamImputeWrapper <- makeImputeWrapper("regr.gamboost",
    classes = list(numeric = imputeMethod))
gamFeatSelControl <- makeFeatSelControlSequential(method = "sfbs")
kFold <- makeResampleDesc("CV", iters = 10)
gamFeatSelWrapper <- makeFeatSelWrapper(learner = gamImputeWrapper,
    resampling = kFold,
    control = gamFeatSelControl)
```

All that's left to do is cross-validate the model building process. As the gamboost algorithm is much more computationally intense than linear regression, I'm only going to use holdout as the method for outer cross validation.

WARNING This takes about 1.5 minutes to run on my four-core machine.



```
holdout <- makeResampleDesc("Holdout")
gamCV <- resample(gamFeatSelWrapper, gamTask, resampling = holdout)
gamCV
Resample Result
Task: ozoneForGam
Learner: regr.gamboost.imputed.featsel
Aggr perf: mse.test.mean=16.4009
Runtime: 147.441
```

Great! Our cross-validation suggests modeling the data using the gamboost algorithm will outperform a model learned by linear regression (the latter gave us a mean MSE of 22.8 in the previous chapter).

Now let's actually build a model so I can show you how you can interrogate your GAM models to understand the non-linear functions they've learned for your predictor variables. First, let's train a boosted GAM using our gamTask. We can actually just use the gamFeatSelWrapper as our learner, as this will perform imputation and feature selection for us. To speed things along we can parallelize the feature selection by running the parallelStartSocket() function before running the train() function to actually train the model.

WARNING This takes about three minutes to run on my four-core machine.

I then extract the model information using the getLearnerModel() function. This time, because
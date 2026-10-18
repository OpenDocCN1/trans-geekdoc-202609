![](bbox=[0.153, 0.067, 0.74, 0.282])

Figure 11.15 Comparing the parameter estimates of our ridge regression model, LASSO model, and OLS regression model.

# 11.6.4 Training the elastic net model

This section is going to look a lot like the previous two, but I’ll show you how to train an elastic net model by tuning both lambda and alpha. We’ll start by creating an elastic net learner and, this time, we won’t supply a value of alpha because we’re going to tune it to find the best trade-off between L1 and L2 regularization. We also give it an id that we can use later when benchmarking.

```
```r
elastic <- makeLearner("regr.glmnet", id = "elastic")
```
```

Now let’s define the hyperparameter space we’re going to tune over, this time including alpha as a numeric hyperparameter bounded between zero and one. As we’re now tuning two hyperparameters, let’s increase the number of iterations of our random search to get a little more coverage of the search space. Finally, we run the tuning process as before and print the optimal result.

> **WARNING** This takes about a minute on my four-core machine.
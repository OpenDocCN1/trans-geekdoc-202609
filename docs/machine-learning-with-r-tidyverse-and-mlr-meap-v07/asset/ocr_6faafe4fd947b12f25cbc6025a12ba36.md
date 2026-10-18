What’s the purpose of this? It validates our entire model-building procedure, including the hyperparameter tuning step. The cross-validated performance estimate we get from this procedure, should be a good representation of how we expect our model to perform on completely new, unseen data.

The process looks pretty complicated, but it is extremely easy to perform with `mlr`. First, we define how we’re going to perform the inner and outer cross-validation:

```
inner <- makeResampleDesc("CV")

outer <- makeResampleDesc("RepCV", folds = 10, reps = 5)
```

I’ve chosen to perform ordinary k-fold cross validation for the inner loop (10 is the default number of folds), and 10-fold cross-validation, repeated 5 times, for the outer loop.

Next, we make what’s called a *wrapper*, which is basically a learner, tied to some preprocessing step. In our case, this is hyperparameter tuning, so we create a tuning wrapper with `makeTuneWrapper()`:

```
knnWrapper <- makeTuneWrapper("classif.knn", resampling = inner,
                              par.set = knnParamSpace,
                              control = gridSearch)
```

Here, we supply the algorithm as the first argument, and pass our inner cross-validation procedure as the resampling argument. We supply our hyperparameter search space as the par.set argument, and our gridSearch method as the control argument (remember that we created these two objects earlier). This "wraps" together the learning algorithm with the hyperparameter tuning procedure that will be applied inside the inner cross-validation loop.

Now that we’ve defined our inner and outer cross-validation strategies, and our tuning wrapper, we run the nested cross-validation procedure by running:

```
cvWithTuning <- resample(knnWrapper, diabetesTask, resampling = outer)
```

The first argument is the wrapper we created a moment ago, the second argument is the name of the task, and we supply our outer cross-validation strategy as the outer argument. Now sit back and relax, this could take a while!

Once it finishes, you can print the average MMCE by calling:

```
cvWithTuning

Resample Result
Task: diabetesTib
Learner: classif.knn.tuned
Aggr perf: mmce.test.mean=0.0856190
Runtime: 42.9978
```

Your MMCE value will probably be a little different to mine due to the random nature of the
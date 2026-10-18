supply the learner, cross-validation strategy, the parameter space for that learner, and the search procedure for that learner (notice we used a difference search procedure for elastic net). OLS regression doesn’t need hyperparameter tuning so we don’t make a wrapper for it. As the `benchmark()` function requires a list of learners, we next create a list of these wrappers (and "regr.lm", our OLS regression learner).

# Listing 11.19 Plotting the model parameters

```
```r
ridgeWrapper <- makeTuneWrapper(ridge, resampling = cvForTuning,
                                 par.set = ridgeParamSpace,
                                 control = randSearch)

lassoWrapper <- makeTuneWrapper(lasso, resampling = cvForTuning,
                                par.set = lassoParamSpace,
                                control = randSearch)

elasticWrapper <- makeTuneWrapper(elastic, resampling = cvForTuning,
                                  par.set = elasticParamSpace,
                                  control = randSearchElastic)

learners = list(ridgeWrapper, lassoWrapper, elasticWrapper, "regr.lm")
```
```

To run the benchmarking experiment, let’s define a 3-fold outer cross-validation procedure. After starting parallelization, we run the benchmarking experiment by supplying the list of learners, task, and outer cross-validation strategy to the `benchmark()` experiment.

> **WARNING** This took almost 6 minutes on my four-core machine.

# Listing 11.20 Plotting the model parameters

```
```r
library(parallel)
library(parallelMap)

kFold3 <- makeResampleDesc("CV", iters = 3)

parallelStartSocket(cpus = detectCores())

bench <- benchmark(learners, iowaTask, kFold3)

parallelStop()

bench

  task.id    learner.id mse.test.mean
1 iowaTib   ridge.tuned       95.48
2 iowaTib   lasso.tuned       93.98
3 iowaTib elastic.tuned       99.19
4 iowaTib       regr.lm      120.37
```
```

Perhaps surprisingly, ridge and LASSO regression both outperformed elastic net, although all three regularization techniques outperformed OLS regression. As elastic net has the potential to select both pure ridge or pure LASSO (based on the value of the alpha hyperparameter), increasing the number of iterations of the random search could end up putting elastic net on top.
![](bbox=[0.131, 0.068, 0.735, 0.334])

**EXERCISE 12.2**

Let’s make sure our search space was large enough. Repeat the tuning process, but search values of *k* from 1 to 50. Plot this tuning process just like we did in figure 12.8. Was our original search space large enough?

Now we have our tuned value of *k*, we can define a learner using that value, with the `setHyperPars()` function, and train a model using it.

# Listing 12.7 Training the final, tuned k-NN model

```
```r
tunedKnn <- setHyperPars(makeLearner("regr.kknn"), par.vals = tunedK$x)

tunedKnnModel <- train(tunedKnn, fuelTask)
```
```

# 12.4 Building our first random forest regression model

In this section, I’ll teach you how to define a random forest learner for regression, tune its many hyperparameters, and train a model for our fuel task.

> **NOTE**
> 
> We can also use the rpart algorithm to build a regression tree, but as it is almost always outperformed by bagged and boosted learners, we’re going to skip over it and dive straight in with random forest and XGBoost. Recall that bagged (bootstrap-aggregated) learners train multiple models on bootstrap samples of the data, and return the majority vote. Boosted learners train models sequentially, putting more emphasis on correcting the mistakes of the previous ensemble of models.

We’ll start by defining our random forest learner. Notice that rather than "classif.randomForest" as in chapter 8, the regression equivalent is "regr.randomForest".

Experience is a great way to choose an algorithm for a particular task. But remember we are always subject to the no free lunch theorem. You may find yourself surprised sometimes that a simpler algorithm outperforms a more complex one, for a particular task. So a good way of deciding which algorithm will perform best on a particular task is to perform a *benchmarking* experiment.

Benchmarking is simple. You create a list of learners you’re interested in trying, and let them fight it out to find the one that learns the best-performing model. Let’s do this with our xgbTask. First I’ll create a list of learner algorithms including k-nearest neighbors (`classif.knn`), multinomial logistic regression (`classif.LiblineaRL1LogReg`), support vector machine (`classif.svm`), our tunedTree model we trained in the previous chapter, and the tunedForest, and tunedXgb models we trained in this chapter. If you no longer have the tunedTree model defined in your global environment, re-run code listings 7.1 to 7.8 from the previous chapter.

> **NOTE** This isn’t quite a fair comparison as the first three learners will be trained using default hyperparameters, whereas the tree-based models have been tuned.

We define our cross-validation method using `makeResampleDesc()`. This time I’ve opted for 10-fold cross-validation, repeated 5 times. It’s important to note that mlr is clever here: while the data are partitioned randomly into folds for each repeat, **the same partitioning** is used for every learner. Put more plainly, for each repeat of cross-validation, each learner in the benchmark gets exactly the same training set and test set.

Finally, we use the `benchmark()` function to run the benchmark experiment. The first argument is the list of learners, the second argument is the name of the task, and the third argument is the cross-validation method.

### Listing 8.10 Plotting individual decision trees

```
learners = list(makeLearner("classif.knn"),
                makeLearner("classif.LiblineaRL1LogReg"),
                makeLearner("classif.svm"),
                tunedTree,
                tunedForest,
                tunedXgb)

benchCV <- makeResampleDesc("RepCV", folds = 10, reps = 5)

bench <- benchmark(learners, xgbTask, benchCV)

bench
```

| task.id | learner.id | mmce.test.mean |
|---------|------------|----------------|
| zooXgb | classif.knn | 0.03182 |
| zooXgb | classif.LiblineaRL1LogReg | 0.09091 |
| zooXgb | classif.svm | 0.07109 |
| zooXgb | classif.rpart | 0.09891 |
| zooXgb | classif.randomForest | 0.03200 |
| zooXgb | classif.xgboost | 0.04564 |

What did I tell you about no free lunches? The humble k-nearest neighbors is performing better on this task than the mighty XGBoost algorithm! Even though we didn't tune it!

### 8.6 Summary

- The random forest, and XGBoost algorithms are supervised learners for both classification and regression problems
- Ensemble techniques construct multiple sub-models to result in a model that performs better than any one of its components alone
- Bagging is an ensemble technique that trains multiple sub-models in parallel on bootstrap samples of the training set. Each sub-model then votes on the prediction for new cases. Random forest is an example of a bagging algorithm
- Boosting is an ensemble technique that trains multiple sub-models sequentially, where each subsequent sub-model focusses on the mistakes of the previous set of sub-models. AdaBoost and XGBoost are examples of boosting algorithms
- Benchmarking allows us to compare the performance of multiple algorithms/models on a single task

## Regression with lines: linear regression

![](img/a22105d68c35e8d5bd3c7bafb4644881_217_0.png)

- **This chapter covers:**
  - What is linear regression?
  - What performance metrics we use for regression tasks
  - How to use machine learning algorithms to impute missing values
  - How to perform feature selection algorithmically
  - How to combine preprocessing wrappers in mlr

Our first stop in regression brings us to *linear regression*. A classical and commonly-used statistical method, linear regression builds predictive models by estimating the strength of the relationship between our predictor variables and our outcome variable. Linear regression is so-named, because it assumes the relationships between the predictor variables with the outcome variable, are linear. Linear regression can handle both continuous and categorical predictor variables, and I’ll show you how in this chapter.

By the end of this chapter, I hope you’ll understand a general approach to regression problems with mlr, and how this differs from classification. In particular, you’ll understand the different performance metrics we use for regression tasks, as mean misclassification error (mmce) is no longer meaningful. I’ll also show you, as I promised in chapter 4, more sophisticated approaches to missing value imputation and feature selection. Finally, I’ll cover how to combine as many preprocessing steps as we like using sequential wrappers, so we can include them in our cross-validation.

### 9.1 What is linear regression?

In this section, you’ll learn what linear regression is and how it uses the equation of a straight line to make predictions. Imagine you want to predict the pH of batches of cider, based on the amount of apple used to make each batch (in kilograms). An example of what this relationship might look like is shown in figure 9.1.

> **NOTE** Recall from high school chemistry that the lower the pH, the more acidic a substance is.

![](img/a22105d68c35e8d5bd3c7bafb4644881_218_0.png)

**Figure 9.1 Imaginary data of how the pH of cider batches changes with apple content.**

The relationship between apple weight and cider pH appears linear, and we could model this relationship using a straight line. Recall from chapter 1 that the only parameters needed to describe a straight line are the slope and intercept:

$y = \mathit{intercept} + \mathit{slope} \times x$

where y is the outcome variable, x is the predictor variable, the intercept is the value of y when x is zero (where the line crosses the y axis), and the slope is **how much y changes when x increases by one unit.**

> **NOTE** Interpreting the slope is useful as it tells us about how the outcome variable changes with the predictor(s), but interpreting the intercept is usually not so straight forward (or useful). For example, a model that predicts a spring’s tension from its length might have a positive intercept, suggesting that a spring of zero length has tension! If all the variables are centered to have a mean of zero, then the intercept can be interpreted as the value of y at the mean of x (which is often more useful information). Centering your variables like this doesn’t affect the slopes because the relationships between variables remain the same. Therefore, predictions made by linear regression models are unaffected by centering and scaling your data.

![](img/a22105d68c35e8d5bd3c7bafb4644881_220_0.png)

**Figure 9.2 Finding the least squares line through the data.** Residuals are the vertical distances between the cases and the line. The area of the boxes represents the squared residuals for three of the cases. The intercept (0) is where the line hits the y axis when x = 0. The slope is the change in y (Δy) divided by the change in x (Δx).

Why does OLS square the distances? You may read that this is because it makes any negative residuals (for cases that lie below the line) positive, so they contribute to the sum of squares rather than subtract from it. This is a handy by-product of squaring certainly, but if that was true we would simply use *|residual|* to denote the *absolute* value (removing the negative sign). We use the squared residuals so that we disproportionately penalize cases that are far away from their predicted value.

### 9.1.1 What if we have multiple predictors?

So OLS finds the combination of slope and intercept that minimizes the sum of squares, and the line learned in this way will be the one that best fits the data. But regression problems are rarely as simplistic as trying to predict an outcome with a single predictor; what about when we have multiple predictor variables? Let’s add another variable to our cider pH problem: fermentation time (see figure 9.3).

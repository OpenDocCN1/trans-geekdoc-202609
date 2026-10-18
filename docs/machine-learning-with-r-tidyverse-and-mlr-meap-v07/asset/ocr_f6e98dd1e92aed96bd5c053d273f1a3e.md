With wrapper methods, rather than using a single, out-of-model statistic to estimate feature importance, we iteratively train our model with different predictor variables. Eventually, the combination of predictors that gave us the best performing model is chosen. There are different ways of doing this, but one such example is *sequential forward selection*. In sequential forward selection we start with no predictors, then add predictors one by one. At each step of the algorithm, the feature that results in the best model performance is chosen. Finally, when the addition of any more predictors doesn’t result in an improvement in performance, feature addition stops and the final model is trained on the selected predictors.

Which method should we choose? Well it boils down to this: wrapper methods may result in models that perform better, as we are actually using the model we’re training to estimate predictor importance. However, as we’re training a fresh model at each iteration of the selection process (and each step may include other preprocessing steps such as imputation), wrapper methods tend to be computationally expensive. Filter methods on the other hand may or may not select the best performing set of predictors, but are much less computationally expensive.

# THE FILTER METHOD FOR FEATURE SELECTION

I’m going to show you both methods for our ozone example, starting with the filter method. There are a number of metrics we can use to estimate predictor importance. To see the list of the available filter methods built into `mlr`, run `listFilterMethods()`. There are too many to describe in full, but common choices include:

+   - linear correlation: when both predictor and outcome are continuous
+   - ANOVA: when the predictor is categorical and the outcome is continuous
+   - chi-squared: when both predictor and outcome are continuous
+   - random forest importance: can be used whether the predictors and outcomes are categorical or continuous (the default)

> **TIP** Feel free to experiment with the methods implemented in mlr. Many of them require you to first install the FSelector package:
> 
> ```r
> install.packages("FSelector").
> ```

The default method used by mlr (because it doesn’t depend on whether the variables are categorical or continuous) is to build a random forest to predict the outcome, and return the variables which contributed most to model predictions (using out-of-bag error we discussed in chapter 8). In this example, as both the predictors and outcome variable are continuous, we’ll use linear correlation to estimate variable importance (it’s a little more interpretable than random forest importance).

First, I use the `generateFilterValuesData()` function (longest function name ever!) to generate an importance metric for each predictor. The first argument is the task, which contains our dataset and lets the function know that Ozone is our target variable. The second, optional
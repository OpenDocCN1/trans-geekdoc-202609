# Extra-Trees

When you are growing a tree in a Random Forest, at each node only a random subset of the features is considered for splitting (as discussed earlier). It is possible to make trees even random by also using random thresholds for each feature rather than searching for the best possible thresholds (like regular Decision Trees).

A forest of extremely random trees is simply called an Extremely Randomized Trees ensemble¹ (or Extra-Trees for short). Once again, this trades more bias for a lower variance. It also makes Extra-Trees much faster to train than Regular Forests since finding the best possible threshold for each feature is one of the most time-consuming tasks of growing a tree.

You can create an Extra-Trees classifier using Scikit-Learn's ExtraTreesClassifier. Its API is identical to the RandomForestClassifier class. Similarly, the ExtraTreesRegressor class has the same API as the RandomForestRegressor.

![](bbox=[0.17, 0.396, 0.255, 0.473])

It is hard to tell in advance whether a RandomForest will perform better or worse than an ExtraTreesClassifier. Generally, the only way is to try both and compare them using cross-validation (and tuning the hyperparameters using grid search).

# Feature Importance

Another great quality of Random Forests is that they make it easy to measure the relative importance of each feature. Scikit-Learn measures a feature's importance by looking at how the tree nodes use that feature reduce impurity on average (across all trees in the forest). More precisely, it is a weighted average, where each node's weight is equal to the number of training samples that are associated with it (see Chapter 6).

Scikit-Learn computes this automatically for each feature after training, it scales the results so that the sum of all importances is equal to 1. You can access the result using the feature_importances_ variable. For example, the following code trains RandomForest on the iris dataset (introduced in Chapter 4) and outputs each feature's importance. It sees that the most important features are the petal length (44%) and width (42%), while sepal length and width are rather unimportant in comparison (11% and 2%, respectively).
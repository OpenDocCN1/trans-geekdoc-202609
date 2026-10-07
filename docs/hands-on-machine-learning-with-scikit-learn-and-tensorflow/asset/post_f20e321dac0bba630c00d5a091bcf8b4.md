
Sampling features results in even more predictor diversity, trading a bit more bias for a lower variance.

# Random Forests

As we have discussed, a Random Forest is an ensemble of Decision Trees, generally trained via the bagging method (or sometimes pasting), typically with max_samples set to the size of the training set. Instead of building a BaggingClassifier and passing it a DecisionTreeClassifier, you can use the RandomForestClassifier class, which is more convenient and optimized for Decision Trees10 (similarly, it is a RandomForestRegressor for regression tasks). The following code trains a Random Forest classifier with 500 trees (each limited to maximum 16 nodes), using all available cores:

```
from sklearn.ensemble import RandomForestClassifier

rnd_clf = RandomForestClassifier(n_estimators=500, max_leaf_nodes=16, n_jobs=-1)
rnd_clf.fit(X_train, y_train)
```

With some exceptions, a RandomForestClassifier has all the hyperparameters of a DecisionTreeClassifier (to control how trees are grown), plus all the hyperparameters of a BaggingClassifier to control the ensemble itself.11.

The Random Forest algorithm introduces randomness when growing trees; instead of searching for the best feature when splitting a node (see Chapter 6), it searches for the best feature among a random subset of features. This results in a greater diversity, (which again) trades a higher bias for a lower variance, generally yielding an overall better model. The following BaggingClassifier is roughly equivalent to the random RandomForest:

```
bag_clf = BaggingClassifier(
  DecisionTreeClassifier(splitter="random", max_leaf_nodes=16),
  n_estimators=500, max_samples=1.0, bootstrap=True, n_jobs=-1)
```

> 9 "Random Forest Decisions," T. Ho. (1995).
10 The BaggingClassifier class remains useful if you want a bag of something other than Decision Trees.
11 There are a few notable exceptions: splitter is absent (forced to "random"), presort is absent (forced to False), max_samples is absent (forced to 1.0), and base_estimator is absent (forced to DecisionTreeClassifier with the provided hyperparameters).

# Extra-Trees

When you are growing a tree in a Random Forest, at each node only a random subset of the features is considered for splitting (as discussed earlier). It is possible to make trees even random by also using random thresholds for each feature rather than searching for the best possible thresholds (like regular Decision Trees).

A forest of extremely random trees is simply called an Extremely Randomized Trees ensemble¹ (or Extra-Trees for short). Once again, this trades more bias for a lower variance. It also makes Extra-Trees much faster to train than Regular Forests since finding the best possible threshold for each feature is one of the most time-consuming tasks of growing a tree.

You can create an Extra-Trees classifier using Scikit-Learn's ExtraTreesClassifier. Its API is identical to the RandomForestClassifier class. Similarly, the ExtraTreesRegressor class has the same API as the RandomForestRegressor.

![](img/0684d2da98e09085c0a622d4fd69aaad_225_0.png)

It is hard to tell in advance whether a RandomForest will perform better or worse than an ExtraTreesClassifier. Generally, the only way is to try both and compare them using cross-validation (and tuning the hyperparameters using grid search).

# Feature Importance

Another great quality of Random Forests is that they make it easy to measure the relative importance of each feature. Scikit-Learn measures a feature's importance by looking at how the tree nodes use that feature reduce impurity on average (across all trees in the forest). More precisely, it is a weighted average, where each node's weight is equal to the number of training samples that are associated with it (see Chapter 6).

Scikit-Learn computes this automatically for each feature after training, it scales the results so that the sum of all importances is equal to 1. You can access the result using the feature_importances_ variable. For example, the following code trains RandomForest on the iris dataset (introduced in Chapter 4) and outputs each feature's importance. It sees that the most important features are the petal length (44%) and width (42%), while sepal length and width are rather unimportant in comparison (11% and 2%, respectively).

```
>>> from sklearn.datasets import load_iris
>>> iris = load_iris()
>>> rnd = RandomForestClassifier(n_estimators=500, n_jobs=-1)
>>> rnd_clf.fit(iris["data"], iris["target"])
>>> for name, score in zip(iris["feature_names"], rnd_clf.feature_importances_):
    print(name, score)
```

sepal length (cm) 0.112492250999
sepal width (cm) 0.023119282825
petal length (cm) 0.0441304364364
petal width (cm) 0.423357996355

Similarly, if you train a Random Forest classifier on the MNIST dataset (introduced in Chapter 3) and plot each pixel's importance, you get the image represented in Figure 7-6.

![](img/0684d2da98e09085c0a622d4fd69aaad_226_0.png)

Figure 7-6: MNIST pixel importance (according to a Random Forest classifier)

Random Forests are handy to get a quick understanding of what features actually matter, in particular if you need to perform feature selection.

# Boosting

Boosting (originally called hypothesis boosting) refers to any Ensemble method that can combine weak learners into a stronger learner. The general idea of boosting methods is to train predictors sequentially, each trying to correct its predecessor. There are many boosting methods available, but by far the most popular are AdaBoost¹³ (short for Adaptive Boosting) and Gradient Boosting. Let's start with Ada-Boost.

# AdaBoost

One way for a new predictor to correct its predecessor is to pay a bit more attention to the training instances that the predecessor underfitted. This results in predictors focusing more and more on the hard cases. This is the technique used by Ada-Boost.

For example, to build an AdaBoost classifier, a first base classifier (such as a Decision Tree) is trained and used to make predictions on the training set. The relative weight of misclassified training instances is then increased. A second classifier is trained using the updated weights and again it makes predictions on the training set, weights are updated, and so on (see Figure 7-7).

![](img/0684d2da98e09085c0a622d4fd69aaad_227_0.png)

Figure 7-7. AdaBoost sequential training with instance weight updates

Figure 7-8 shows the decision boundaries of five consecutive predictors on the moons dataset (in this example, each predictor is a highly regularized SVM classifier with an RBF kernel¹⁴). The first classifier gets many instances wrong, so their weights 

> ¹³ "A Decision-Theoretic Generalization of On-Line Learning and an Application to Boosting," Yoav Freund, Robert E. Schapie (1997).

> ¹⁴ This is just for illustrative purposes. SVMs are generally not good base predictors for AdaBoost, because they are slow and tend to be unstable with AdaBoost.

get boosted. The second classifier therefore does a better job on these instances, and so on. The plot on the right represents the same sequence of predictors except that the learning rate is halved (i.e., the misclassified instance weights are boosted half as much at every iteration). As you can see, this sequential learning technique has many similarities with Gradient Descent, except of tweaking a single predictor’s parameters to minimize a cost function, AdaBoost adds predictors to the ensemble, gradually making it better.

![](img/0684d2da98e09085c0a622d4fd69aaad_228_0.png)

Figure 7-8. Decision boundaries of consecutive predictors

Once all predictors are trained, the ensemble makes predictions very much like bagging or pasting, except that predictors have different weights depending on their overall accuracy over the weighted training set.

> There is one important drawback to this sequential learning technique: it cannot be parallelized (or only partially), since each predictor can only be trained after the previous predictor has been trained and evaluated. As a result, it does not scale well as bagging or pasting.

Let’s take a closer look at the AdaBoost algorithm. Each instance weight $w^{(i)}$ is initially set to $\frac{1}{m}$. A first predictor is trained and its weighted error rate $r_1$ is computed on the training set; see Equation 7-1.

Equation 7-1. Weighted error rate of the $j^{th}$ predictor

```
r_j = \frac{\sum_{i=1}^{m} w^{(i)} [y^{(i)} \neq \hat{y}^{(i)}]}{\sum_{i=1}^{m} w^{(i)}} where $\hat{y}^{(i)}$ is the $j^{th}$ predictor’s prediction for the $i^{th}$ instance.
```

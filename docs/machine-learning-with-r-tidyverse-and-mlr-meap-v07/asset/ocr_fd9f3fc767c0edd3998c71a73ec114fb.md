# 3.2.4 Telling mlr which algorithm to use: defining the learner

Next, let’s define our learner. The components needed to define a learner are:

+   1. the class of algorithm we are using:
+      A. "classif." for classification
+      B. "regr." for regression
+      C. "cluster." for clustering
+      D. "surv." and "multilabel." (for predicting survival and multilabel classification which I won’t discuss)
+   2. the algorithm we are using
+   3. any additional options we may wish to use to control the algorithm

As you’ll see, components 1 and 2 are combined together in a single character argument to define which algorithm will be used (for example: "classif.knn"). The components of a learner are shown in figure 3.7.

![](bbox=[0.131, 0.4, 0.868, 0.581])

We use the `makeLearner()` function to define a learner. The first argument to the `makeLearner()` function is the algorithm that we’re going to use to train our model. In this case, we want to use the K-NN algorithm, so we supply `"classif.knn"` as the argument. See how this is the class (`"classif."`) joined to the name (`"knn"`) of the algorithm?

The argument `par.vals` stands for parameter values, which allows us to specify the number of *k* nearest neighbors we want the algorithm to use. For now, we’ll just set this to two, but we’ll discuss how to choose *k* soon.

```
knn <- makeLearner("classif.knn", par.vals = list("k" = 2))
```
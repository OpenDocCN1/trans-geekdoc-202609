area of the feature space, where the others do poorly. So here's the key in stacking: the predictions made by the base models are used as predictor variables (along with all the original predictors) by another model: the stacked model. This stacked model is then able to learn from the predictions made by the base models to make more accurate predictions of its own.

Stacking can be tedious and complicated to implement, but it usually results in improved model performance if you use base learners that are different enough from each other.

I hope I've conveyed a basic understanding of ensemble techniques, in particular the random forest and XGBoost algorithms. In the next section, we'll use these two algorithms to train models on our zoo task, and see which performs the best!

> Ensemble methods like bagging, boosting, and stacking, are not strictly machine learning algorithms in their own right. They are algorithms which can be applied to other machine learning algorithms. For example, I've described bagging and boosting here as being applied to decision trees. This is because ensembling is most commonly applied to tree-based learners, but we could just as easily apply bagging and boosting to other machine learning algorithms, such as k-NN and linear regression.



In this section, I'll show you how to build a random forest model (using bootstrapping to train many trees and aggregating their predictions), and how to tune its hyperparameters. There are four important hyperparameters for us to consider:

+   - ntree, the number of individual trees in the forest
+   - mtry, the number of features to randomly sample at each node
+   - nodesize, the minimum number of cases allowed in a leaf (same as minbucket in rpart)
+   - maxnodes, the maximum number of leaves allowed

As we're aggregating the votes of many trees in random forest, the more trees we have, the better. There is no downside to having more trees aside from computational cost, and at some point, we get diminishing returns. Rather than tuning this value, I usually fix it to a number of trees I know fits my computational budget, usually several hundred to the low thousands. Then, later in this section I'll show you how to tell if you've used enough trees, or if you can reduce your tree number to speed up training times.

The other three hyperparameters, mtry, nodesize, and maxnodes will need tuning though, so let's get started. We'll continue with our zooTask that we defined in the last chapter (if you no longer have zooTask defined in your global environment, just re-run code listings 7.1, 7.2, and 7.3 from the previous chapter). The first thing to do is create a learner with the makeLearner() function. This time, our learner is "classif.randomForest".
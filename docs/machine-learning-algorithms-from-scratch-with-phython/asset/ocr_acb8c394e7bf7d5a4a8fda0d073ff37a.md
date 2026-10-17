We can force the decision trees to be different by limiting the features (columns) that the greedy algorithm can evaluate at each split point when creating the tree. This is called the Random Forest algorithm. Like bagging, multiple samples of the training dataset are taken and a different tree trained on each. The difference is that at each point a split is made in the data and added to the tree, only a fixed subset of attributes can be considered. For classification problems, the type of problems we will look at in this tutorial, the number of attributes to be considered for the split is limited to the square root of the number of input features.

$$\text{num\_features\_for\_split} = \sqrt{\text{total\_input\_features}} \tag{17.1}$$

The result of this one small change are trees that are more different from each other (uncorrelated) resulting in predictions that are more diverse and a combined prediction that often has better performance than a single tree or bagging alone.

# ### 17.1.2 Sonar Dataset

In this tutorial we will use the Sonar Dataset. This dataset involves the discrimination between mines and rocks. The baseline performance on the problem is approximately 53%. You can learn more about it in Appendix A, Section [A.5](#). Download the dataset and save it into your current working directory with the filename `sonar.all-data.csv`.

# ## 17.2 Tutorial

This tutorial is broken down into 2 steps.

+   1. Calculating Splits.
+   2. Sonar Case Study.

These steps provide the foundation that you need to implement and apply the Random Forest algorithm to your own predictive modeling problems.

# ### 17.2.1 Calculating Splits

In a decision tree, split points are chosen by finding the attribute and the value of that attribute that results in the lowest cost. For classification problems, this cost function is often the Gini index that calculates the purity of the groups of data created by the split point. A Gini index of 0 is perfect purity where class values are perfectly separated into two groups, in the case of a two-class classification problem.

Finding the best split point in a decision tree involves evaluating the cost of each value in the training dataset for each input variable. For bagging and random forest, this procedure is executed upon a sample of the training dataset, made with replacement. Sampling with replacement means that the same row may be chosen and added to the sample more than once.

We can update this procedure for Random Forest. Instead of enumerating all values for input attributes in search of the split with the lowest cost, we can create a sample of the input attributes to consider. This sample of input attributes can be chosen randomly and without
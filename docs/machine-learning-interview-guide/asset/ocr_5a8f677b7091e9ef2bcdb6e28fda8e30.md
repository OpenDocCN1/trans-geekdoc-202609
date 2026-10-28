Answer: Outliers greatly impact the decision trees as the tree must develop a path to capture these values, thus over-complicating the tree. Extreme values also have an impact on decision boundaries and hence the performance of the tree will not be same on future unseen data.

Some mitigation techniques are:

+   - **Pruning**: Trim back the tree to narrow down the depth or branching points, thus minimizing the effects that outlying cases will have on the decision plane.
+   - **Ensemble methods**: Predictions are made by averaging the outcomes from a number of individual trees, thus making the model less sensitive to outliers like using random forests.
+   - **Data transformation**: Use data transformations, such as (for example) log transformation, in case the range of the dependent variable is too broad.
+   - **Robust algorithms**: Employ algorithms that do not greatly suffer from outliers, such as tree-based methods that incorporate a robust splitting rule.

They also assist in reducing the noise, especially high outliers, and make the decision trees more generalized to unseen datasets.

# Question 12: Discuss the trade-off between a deep and shallow decision tree in terms of bias and variance.

Answer: A deep decision tree typically has low bias because it can model complex relationships in the data. However, it also has high variance, making it prone to overfitting by capturing noise and specific patterns in the training data. Greater depths can help learn more complex relations between the input and output, but there is a higher probability of overfitting. On the other hand, a
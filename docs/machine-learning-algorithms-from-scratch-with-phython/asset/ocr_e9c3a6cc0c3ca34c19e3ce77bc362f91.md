A difficulty of this method is that even though deep trees are constructed, the bagged trees that are created are very similar. In turn, the predictions made by these trees are also similar, and the high variance we desire among the trees trained on different samples of the training dataset is diminished.

This is because of the greedy algorithm used in the construction of the trees selecting the same or similar split points. The tutorial tried to re-inject this variance by constraining the sample size used to train each tree. A more robust technique is to constrain the features that may be evaluated when creating each split point. This is the method used in the Random Forest algorithm.

# ## 16.3 Extensions

+   - **Tune the Example.** Explore different configurations for the number of trees and even individual tree configurations to see if you can further improve results.
+   - **Bag Another Algorithm.** Other algorithms can be used with bagging. For example, a *k*-nearest neighbor algorithm with a low value of *k* will have a high variance and is a good candidate for bagging.
+   - **Regression Problems.** Bagging can be used with regression trees. Instead of predicting the most common class value from the set of predictions, you can return the average of the predictions from the bagged trees. Experiment on regression problems.

# ## 16.4 Review

In this tutorial, you discovered how to implement bootstrap aggregation from scratch with Python. Specifically, you learned:

+   - How to create a subsample and estimate bootstrap quantities.
+   - How to create an ensemble of decision trees and use them to make predictions.
+   - How to apply bagging to a real world predictive modeling problem.

# ### 16.4.1 Further Reading

+   - Section 8.2. Bagging, Random Forests, Boosting, page 316, *An Introduction to Statistical Learning*, 2014.
+     http://amzn.to/2eeTyQX
+   - Section 8.4 Bagged Trees, page 192 and Section 14.3, Bagged Trees, page 385, *Applied Predictive Modeling*, 2013.
+     http://amzn.to/2e31MXF
+   - Section 7.5, Combining multiple models, page 315, *Data Mining: Practical Machine Learning Tools and Techniques*, second edition, 2005.
+     http://amzn.to/2fj3SYY
# Chapter 16

# Bootstrap Aggregation

Decision trees are a simple and powerful predictive modeling technique, but they suffer from high-variance. This means that trees can get very different results given different training data. A technique to make decision trees more robust and to achieve better performance is called bootstrap aggregation or bagging for short. In this tutorial, you will discover how to implement the bagging procedure with decision trees from scratch with Python. After completing this tutorial, you will know:

+   - How to create a bootstrap sample of your dataset.
+   - How to make predictions with bootstrapped models.
+   - How to apply bagging to your own predictive modeling problems.

Let's get started.

# 16.1 Descriptions

This section provides a brief description to Bootstrap Aggregation and the Sonar dataset that will be used in this tutorial.

# 16.1.1 Bootstrap Aggregation Algorithm

A bootstrap is a sample of a dataset with replacement. This means that a new dataset is created from a random sample of an existing dataset where a given row may be selected and added more than once to the sample. It is a useful approach to use when estimating values such as the mean for a broader dataset, when you only have a limited dataset available. By creating samples of your dataset and estimating the mean from those samples, you can take the average of those estimates and get a better idea of the true mean of the underlying problem.

This same approach can be used with machine learning algorithms that have a high variance, such as decision trees (CART) introduced in Chapter 11. A separate model is trained on each bootstrap sample of data and the average output of those models used to make predictions. This technique is called bootstrap aggregation or bagging for short. Variance means that an algorithm's performance is sensitive to the training data, with high variance suggesting that the more the training data is changed, the more the performance of the algorithm will vary.
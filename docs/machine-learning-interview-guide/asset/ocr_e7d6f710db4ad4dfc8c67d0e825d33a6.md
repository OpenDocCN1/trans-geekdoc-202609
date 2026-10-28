classes, and, therefore, such methods as balance sampling or weighted voting are used.

+   - **Memory usage**: When it comes to memory management, storing multiple trees in memory can be expensive which makes it a bit impractical to use random forests in areas where memory is scarce.

Nevertheless, random forests still prove to be very effective and broadly applicable for classification problems and propose solutions and workarounds for most of these threats.

# Question 16: How does random forest compare to other ensemble methods, like AdaBoost or gradient boosting?

**Answer**: The difference between them is as follows:

+   - **Random forest:**
+     - It builds many decision trees individually.
+     - Reduces overfitting through randomness.
+     - Ideal for complex data, especially the data that has a large number of features and is insensitive to outliers.
+     - They are quite strong, but there is a trade-off as the model will not be as good at predicting specific outcomes for increased variation.

+   - **AdaBoost:**
+     - Weak learners are sequentially trained and mistakes made by them, such as misclassified instances, are highlighted.
+     - Optimizes by changing the weights for better performance on subsequent cycles.
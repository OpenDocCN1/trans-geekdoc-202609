# 14.3 CASE STUDY: CLASSIFICATION WITH K-NEAREST NEIGHBORS AND THE DIGITS DATASET, PART 2

In this section, we continue the digit classification case study. We'll:

+   - evaluate the k-NN classification estimator’s accuracy,
+   - execute multiple estimators and can compare their results so you can choose the best one(s), and
+   - show how to tune k-NN’s hyperparameter k to get the best performance out of a KNeighborsClassifier.

# 14.3.1 Metrics for Model Accuracy

Once you've trained and tested a model, you'll want to measure its accuracy. Here, we'll look at two ways of doing this—a classification estimator's score method and a confusion matrix.

# Estimator Method score

Each estimator has a score method that returns an indication of how well the estimator performs for the test data you pass as arguments. For classification estimators, this method returns the prediction accuracy for the test data:

lick here to view code image

```
In [25]: print(f'knn.score(X_test, y_test):.2%')
97.78%
```

The KNeighborsClassifier’s with its default k (that is, n_neighbors=5) achieved 97.78% prediction accuracy. Shortly, we’ll perform hyperparameter tuning to try to determine the optimal value for k, hoping that we get even better accuracy.

# Confusion Matrix

Another way to check a classification estimator’s accuracy is via a confusion matrix, which shows the correct and incorrect predicted values (also known as the hits and misses) for a given class. Simply call the function confusion_matrix from the sklearn.metrics module, passing the expected classes and the predicted classes as arguments, as in:
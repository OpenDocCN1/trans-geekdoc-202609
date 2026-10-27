attention to the details of the data and the model architecture to ensure that the model is accurate, robust, and generalizable.

# 10.4.2 Metrics for Measuring Model Performance

Here are some metrics for measuring model performance for fruit leaf classification using transfer learning, along with examples:

+   1. Accuracy: As was previously established, accuracy represents the percentage of instances in the test set that were properly categorized. For example, if the model classifies 90 out of 100 instances correctly, its accuracy is 90%.
+   2. Precision: Out of all positive forecasts, precision is defined as the percentage of genuine positive predictions. For example, if the model correctly identifies 20 out of 30 instances as belonging to a particular class, its precision for that class is 20/30 = 0.67.
+   3. Recall: Recall measures the proportion of true positive predictions out of all instances that are actually in a given class. For example, if there are 50 instances of a particular class in the test set, and the model correctly identifies 40 of them, its recall for that class is 40/50 = 0.8.
+   4. F1 score: The harmonic mean of recall and accuracy is the F1 score. For example, if a model has a precision of 0.67 and a recall of 0.8 for a particular class, its F1 score for that class is 2*(0.67*0.8)/(0.67+0.8) = 0.728.
+   5. AUC-ROC: The model's capacity to differentiate between positive and negative occurrences across various thresholds is measured by AUC-ROC. For instance, if a model's AUC-ROC score is 0.85, it indicates that the model can accurately discriminate between positive and negative events in 85% of cases shown in Figure 10.8.

![](bbox=[0.1, 0.75, 0.9, 0.88])

Figure 10.8 Metrics for measuring model performance.
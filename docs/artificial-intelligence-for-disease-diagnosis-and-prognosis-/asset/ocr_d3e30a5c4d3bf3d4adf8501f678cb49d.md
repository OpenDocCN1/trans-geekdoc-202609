# 13.3.4.2 Recall

![](bbox=[0.13, 0.13, 0.88, 0.405])

Measurement metrics entail the use of various distinct assessment metrics to evaluate a model or algorithm and it is essential to ensure that your model is working properly and optimally, which is essential to get the optimal classification throughout the classification training [44].
The remainder is the measure of our method which correctly identifies True Positives, whereby TP is the number of true positives and FN is the number of false negatives, and it is also the proportion of relevant instances found. We should remember, the best recall value is 1 and the worst recall value is 0.

```
Recall = \frac{TP}{TP + FN} (13.2)
```

# 13.3.4.3 Precision

Precision is the proportion of positive observations correctly predicted with the total positive observations predicted. The prediction accuracy is used to understand when the cost of false positives is high. Let's assume that rare disease detection is the problem. If we were to use a model with a low accuracy level, many patients are told they have a disease that might lead to misdiagnosis.

```
Precision = \frac{TP}{TP + FP} (13.3)
```

# 13.3.4.4 F1-Score

F1-Score is the weighted mean of accuracy and recall and its score, often known as an F1-Score, measures the accuracy of the model on a dataset. This is used for assessing
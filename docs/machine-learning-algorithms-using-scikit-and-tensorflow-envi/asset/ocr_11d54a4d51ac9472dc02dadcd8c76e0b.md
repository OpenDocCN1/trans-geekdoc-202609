# 6. CLASSIFICATION METRICS

The sklearn.metrics (Dada et al., 2019) module offers a variety of loss, score, and utility methods to measure classification performance. Confidence intervals, binary decision values, or probability estimates of the positive class may be required by some metrics. Most implementations allow each sample to contribute to the final score in a weighted manner using the sample weight parameter. Few metrics to assess performance on classification are mentioned in Table 1.

# 6.1 Precision_recall_curve

For various probability thresholds, compute precision-recall pairings. Only the binary classification task is supported by this implementation. The ratio of the number of true positives to the number of false positives, or tp/(tp + fp), is used to measure precision. Intuitively, the classifier’s precision is its capacity not to classify a negative sample as positive. The ratio of the number of true positives to the number of false negatives, tp/(tp + fn), is known as the recall. The classifier’s capacity to locate all the positive samples is known as recall.

```
import numpy as np
import matplotlib.pyplot as plt
from sklearn.metrics import precision_recall_curve
y_actual = np.array([0, 0, 1, 1, 1, 0, 0, 1, 1, 1 ])
y_scores = np.array([0.1, 0.4, 0.35, 0.8, 0.9, .3, 0.47, 0.35, 0.8, 0.9])
#print(sorted(list(set(y_scores.tolist()))))
precision, recall, thresholds = precision_recall_curve(y_actual, y_scores)
print(list(precision))
print(list(recall))
print(list(thresholds))
plt.plot(recall, precision, marker='.', label='Curve')
plt.xlabel('Recall')
plt.ylabel('Precision')
plt.show()
Output:
[0.6, 0.6666666666666666, 0.75, 0.6666666666666666, 0.8, 1.0, 1.0, 1.0]
[1.0, 1.0, 1.0, 0.6666666666666666, 0.6666666666666666, 0.6666666666666666, 0.3333333333333333,
0.0]
[0.1, 0.3, 0.35, 0.4, 0.47, 0.8, 0.9]
```

# 6.2 Confusion Matrix

A confusion matrix, also known as an error matrix, is a compact table used to assess the effectiveness of a classification model. The number of accurate and incorrect predictions for each class is expressed using count values.
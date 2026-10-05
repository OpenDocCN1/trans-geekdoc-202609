# Detecting Breast Cancer

| 0 | 0.88 | 0.93 | 0.91 | 151 |
| 1 | 0.85 | 0.75 | 0.80 | 77 |
| accuracy | | | 0.87 | 228 |
| macro avg | 0.87 | 0.84 | 0.85 | 228 |
| weighted avg | 0.87 | 0.87 | 0.87 | 228 |

The first section in the report shows metrics for the cases with a negative label (0) and a positive label (1). Focusing on row (1), the precision indicates that 85% of the predicted positives were true positive. The recall indicates that 75% of the true positives were predicted as positive. The F1 score is the harmonic mean of the precision and recall, valued at 0.80 or 0.87. The support indicates 77 positive-labeled cases. The calculations for row (0) are analogous, and they represent the classification ability for the negative-labeled cases. Given the F1 score of 0.91, we learn that the model does better on positive labels. From the second section in the table, we see that the accuracy of correct predictions, was 0.87, or 87%. For data where the number of positive labels is different from the number of negative labels, the accuracy is not very useful.

In practice, it can be helpful to set a range of thresholds and compute recall and precision for each. The threshold giving the highest F1 score, for example, might be selected. Next, we report metrics for a sample of thresholds:

```
# probabilities of positive class from test set
pred_pos = model.predict_proba(x,te)[:1]

# calculate metrics over range of thresholds
pre, re, th = precision_recall_curve(y_te, pred_pos)

print('threshold:', th[100:105])
print('(')
print('precision:', pre[100:105])
print('(')
print('recall:', ', re[100:105])
```

OUTPUT:

threshold: [0.5232687 0.5311383 0.5393744 0.5536759 0.563716]

precision: [0.8769231 0.890625 0.904762 0.9032258 0.9016393]

recall: [0.7402597 0.7402597 0.7402597 0.7272727 0.7142857]

For threshold 0.523, the precision and recall are approximately 0.87 and 0.74, respectively. Moving the threshold up to 0.564 (the last shown threshold)
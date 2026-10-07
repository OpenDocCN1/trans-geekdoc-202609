# Naïve Bayes Algorithm

In Figure 2.9, we have four quadrants. When the Actual and Predicted values are True, we say these cases are the True Positives (TP). These cases were predicted correctly when the actual value was True.

When the Actual Value is False and the Predicted Value is False, we say these cases are the True Negatives (TN). These cases were predicted correctly when the actual value was False. So, True Positives and True Negatives are the cases that were predicted correctly.

When the Actual Value is True and the Predicted Value is False, we say these cases are the False Positives (FP). Lastly, when the Actual Value is False and the Predicted Value is True, we say these are the False Negatives (FN). False Positives and False Negatives are the values that were incorrectly predicted.

Now, we discuss the metrics used to measure the goodness of a classification model.

# Accuracy

Accuracy states how many predictions were made correctly out of the total predictions.

```
Accuracy = \frac{\text{Total number of correct predictions (TP+TN)}}{\text{Total number of datapoints (TP+TN+FP+FN)}}
```

# Precision

Precision indicates how consistently the model behaves when the same input is provided to the model.

```
Precision ( P ) = \frac{TP}{TP+FP}
```

# Recall

Recall indicates the ability of the model to identify the relevant cases in the dataset.

```
Recall ( R ) = \frac{TP}{TP+FN}
```

# F1 Score

F1 Score combines Precision and Recall into a single number. F1 Score is the harmonic mean of Precision and Recall.

```
F1 Score = \frac{2 (\text{Precision}\*\text{Recall})}{\text{Precision} +\text{Recall}}
```

![](bbox=[0.135, 0.963, 0.864, 0.983])
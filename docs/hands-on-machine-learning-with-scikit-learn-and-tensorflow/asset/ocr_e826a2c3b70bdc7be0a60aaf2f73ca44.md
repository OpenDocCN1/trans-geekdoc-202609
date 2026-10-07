(TPR): this is the ratio of positive instances that are correctly detected by the classifier
(Equation 3-2).

# Equation 3-2. Recall

```
recall = \frac{TP}{TP + FN}
```

FN is of course the number of false negatives.
If you are confused about the confusion matrix, Figure 3-2 may help.

![](bbox=[0.156, 0.281, 0.843, 0.537])

Figure 3-2. An illustrated confusion matrix

# Precision and Recall

Scikit-Learn provides several functions to compute cluster evaluation metrics, including precision and recall:

```
>>> from sklearn.metrics import precision_score, recall_score
>>> precision_score(y_train, y_train) # == 4096 / (4096 + 1522)
0.7298050836539654
>>> recall_score(y_train, y_train) # == 4096 / (4096 + 1325)
0.755881512363684
```

Now your 5-detector does not look as shiny as it did when you looked at accuracy. When it claims an image represents a 5, it is only 72.9% of the time. Over it detects 75.6% of the 5s.

It is often convenient to combine precision and recall into a single metric called the F score, in particular if you need a simple way to compare two classifiers. The F score is the harmonic mean of precision and recall (Equation 3-3). Whereas the regular mean
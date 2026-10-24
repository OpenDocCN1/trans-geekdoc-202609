| Measure | Formula |
| :--- | :--- |
| accuracy, recognition rate | \(\frac{TP + TN}{P + N}\) |
| error rate, misclassification rate | \(\frac{FP + FN}{P + N}\) |
| sensitivity, true positive rate, recall | \(\frac{TP}{P}\) |
| specificity, true negative rate | \(\frac{TN}{N}\) |
| precision | \(\frac{TP}{TP + FP}\) |
| \(F, F_1, F\)-score, harmonic mean of precision and recall | \(\frac{2 \times precision \times recall}{precision + recall}\) |
| \(F_\beta\), where \(\beta\) is a nonnegative real number | \(\frac{(1 + \beta^2) \times precision \times recall}{\beta^2 \times precision + recall}\) |

**FIGURE 6.15**
Evaluation measures. Note that some measures are known by more than one name. \(TP, TN, FP, FN, P, N\) refer to the number of true positive, true negative, false positive, false negative, positive, and negative samples, respectively (see text).

| | yes | no | Total |
| :--- | :--- | :--- | :--- |
| **yes** | TP | FN | P |
| **no** | FP | TN | N |
| **Total** | P' | N' | P + N |

**FIGURE 6.16**
Confusion matrix, shown with totals for positive and negative tuples.

+   - **True positives** (\(TP\)): These refer to the positive tuples that were correctly labeled by the classifier. Let \(TP\) be the number of true positives.
+   - **True negatives** (\(TN\)): These are the negative tuples that were correctly labeled by the classifier. Let \(TN\) be the number of true negatives.
+   - **False positives** (\(FP\)): These are the negative tuples that were incorrectly labeled as positive (e.g., tuples of class \(buys\_computer = no\) for which the classifier predicted \(buys\_computer = yes\)). Let \(FP\) be the number of false positives.
+   - **False negatives** (\(FN\)): These are the positive tuples that were mislabeled as negative (e.g., tuples of class \(buys\_computer = yes\) for which the classifier predicted \(buys\_computer = no\)). Let \(FN\) be the number of false negatives.

These terms are summarized in the **confusion matrix** of Fig. 6.16.

A confusion matrix is a useful tool for analyzing how well your classifier can recognize tuples of different classes. \(TP\) and \(TN\) tell us when the classifier is getting things right, whereas \(FP\) and \(FN\) tell us when the classifier is getting things wrong (i.e., mislabeling). Given \(m\) classes (where \(m \ge 2\)), a **confusion matrix** is a table of at least size \(m\) by \(m\). An entry, \(CM_{i,j}\), at the \(i\)th row and the \(j\)th column indicates the number of tuples of class \(i\) that were labeled by the classifier as class \(j\). For a classifier to have good accuracy, ideally most of the tuples would be represented along the diagonal of the confusion matrix, from entry \(CM_{1,1}\) to entry \(CM_{m,m}\), with the rest of the entries being zero or close to zero. That is, ideally, \(FP\) and \(FN\) are around zero.
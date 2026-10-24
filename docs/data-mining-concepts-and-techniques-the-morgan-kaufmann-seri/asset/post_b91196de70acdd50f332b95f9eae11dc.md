

| Measure | Formula |
| --- | --- |
| accuracy, recognition rate | \(\frac{TP + TN}{P + N}\) |
| error rate, misclassification rate | \(\frac{FP + FN}{P + N}\) |
| sensitivity, true positive rate, recall | \(\frac{TP}{P}\) |
| specificity, true negative rate | \(\frac{TN}{N}\) |
| precision | \(\frac{TP}{TP + FP}\) |
| \(F, F_1, F\)-score, harmonic mean of precision and recall | \(\frac{2 \times precision \times recall}{precision + recall}\) |
| \(F_\beta\), where \(\beta\) is a nonnegative real number | \(\frac{(1 + \beta^2) \times precision \times recall}{\beta^2 \times precision + recall}\) |

### FIGURE 6.15
Evaluation measures. Note that some measures are known by more than one name. \(TP, TN, FP, FN, P, N\) refer to the number of true positive, true negative, false positive, false negative, positive, and negative samples, respectively (see text).

| | yes | no | Total |
| --- | --- | --- | --- |
| **yes** | TP | FN | P |
| **no** | FP | TN | N |
| **Total** | P' | N' | P + N |

### FIGURE 6.16
Confusion matrix, shown with totals for positive and negative tuples.

- **True positives** (\(TP\)): These refer to the positive tuples that were correctly labeled by the classifier. Let \(TP\) be the number of true positives.
- **True negatives** (\(TN\)): These are the negative tuples that were correctly labeled by the classifier. Let \(TN\) be the number of true negatives.
- **False positives** (\(FP\)): These are the negative tuples that were incorrectly labeled as positive (e.g., tuples of class `buys_computer = no` for which the classifier predicted `buys_computer = yes`). Let \(FP\) be the number of false positives.
- **False negatives** (\(FN\)): These are the positive tuples that were mislabeled as negative (e.g., tuples of class `buys_computer = yes` for which the classifier predicted `buys_computer = no`). Let \(FN\) be the number of false negatives.

These terms are summarized in the **confusion matrix** of Fig. 6.16.

A confusion matrix is a useful tool for analyzing how well your classifier can recognize tuples of different classes. \(TP\) and \(TN\) tell us when the classifier is getting things right, whereas \(FP\) and \(FN\) tell us when the classifier is getting things wrong (i.e., mislabeling). Given \(m\) classes (where \(m \ge 2\)), a **confusion matrix** is a table of at least size \(m\) by \(m\). An entry, \(CM_{i,j}\), at the \(i\)th row and the \(j\)th column indicates the number of tuples of class \(i\) that were labeled by the classifier as class \(j\). For a classifier to have good accuracy, ideally most of the tuples would be represented along the diagonal of the confusion matrix, from entry \(CM_{1,1}\) to entry \(CM_{m,m}\), with the rest of the entries being zero or close to zero. That is, ideally, \(FP\) and \(FN\) are around zero.

| Classes | `buys_computer = yes` | `buys_computer = no` | Total | Recognition (%) |
| --- | --- | --- | --- | --- |
| `buys_computer = yes` | 6954 | 46 | 7000 | 99.34 |
| `buys_computer = no` | 412 | 2588 | 3000 | 86.27 |
| Total | 7366 | 2634 | 10,000 | 95.42 |

### FIGURE 6.17
Confusion matrix for the classes `buys_computer = yes` and `buys_computer = no`, where an entry in row _i_ and column _j_ shows the number of tuples of class _i_ that were labeled by the classifier as class _j_. Ideally, the nondiagonal entries should be zero or close to zero.

The table may have additional rows or columns to provide totals. For example, in the confusion matrix of Fig. 6.16, _P_ and _N_ are shown. In addition, \( P' \) is the number of tuples that were labeled as positive (\( TP + FP \)), and \( N' \) is the number of tuples that were labeled as negative (\( TN + FN \)). The total number of tuples is \( TP + TN + FP + FN \), or \( P + N \), or \( P' + N' \). Note that although the confusion matrix shown is for a binary classification problem, confusion matrices can be easily drawn for multiple classes in a similar manner.

Now let's look at the evaluation measures, starting with accuracy. The **accuracy** of a classifier on a given test set is the percentage of test set tuples that are correctly classified by the classifier. That is,

\( accuracy = \frac{TP + TN}{P + N} \). (6.21)

In the pattern recognition literature, this is also referred to as the overall **recognition rate** of the classifier; that is, it reflects how well the classifier recognizes tuples of the various classes. An example of a confusion matrix for the two classes `buys_computer = yes` (positive) and `buys_computer = no` (negative) is given in Fig. 6.17. Totals are shown, as well as the recognition rates per class and overall. By glancing at a confusion matrix, it is easy to see if the corresponding classifier is confusing two classes.

For example, we see that it mislabeled 412 “no” tuples as “yes.” Accuracy is most effective when the class distribution is relatively balanced.

We can also speak of the **error rate** or **misclassification rate** of a classifier, _M_, which is simply \( 1 - accuracy(M) \), where _accuracy_(_M_) is the accuracy of _M_. This also can be computed as

\( error \, rate = \frac{FP + FN}{P + N} \). (6.22)

If we were to use the training set (instead of a test set) to estimate the error rate of a model, this quantity is known as the **resubstitution error**.<sup>13</sup> This error estimate is optimistic of the true error rate (and similarly, the corresponding accuracy estimate is optimistic) because the model is not tested on any samples that it has not already seen.

We now consider the **class imbalance problem**, where the main class of interest is rare. That is, the data set distribution reflects a significant majority of the negative class and a minority positive class. For example, in fraud detection applications, the class of interest (or positive class) is “_fraud_” which occurs much less frequently than the negative “_nonfraudulent_” class. In medical data, there may

| Classes | yes | no | Total | Recognition (%) |
| --- | --- | --- | --- | --- |
| yes | 90 | 210 | 300 | 30.00 |
| no | 140 | 9560 | 9700 | 98.56 |
| Total | 230 | 9770 | 10,000 | 96.40 |

### FIGURE 6.18
Confusion matrix for the classes cancer = yes and cancer = no.

be a rare class, such as “cancer.” Suppose that you have trained a classifier to classify medical data tuples, where the class label attribute is “cancer” and the possible class values are “yes” and “no.” An accuracy rate of, say, 97% may make the classifier seem quite accurate, but what if only, say, 3% of the training tuples are actually cancer? Clearly, an accuracy rate of 97% may not be acceptable—the classifier could be correctly labeling only the noncancer tuples, for instance, and misclassifying all the cancer tuples. Instead, we need other measures, which assess how well the classifier can recognize the positive tuples (cancer = yes) and how well it can recognize the negative tuples (cancer = no).

The sensitivity and specificity measures can be used, respectively, for this purpose. Sensitivity is also referred to as the true positive (recognition) rate (i.e., the proportion of positive tuples that are correctly identified), whereas specificity is the true negative rate (i.e., the proportion of negative tuples that are correctly identified). These measures are defined as

```
sensitivity = TP / P (6.23)
specificity = TN / N. (6.24)
```

It can be shown that accuracy is a function of sensitivity and specificity:

```
accuracy = sensitivity * P / (P + N) + specificity * N / (P + N). (6.25)
```

### Example 6.9. Sensitivity and specificity.
Fig. 6.18 shows a confusion matrix for medical data where the class values are yes and no for a class label attribute, cancer. The sensitivity of the classifier is 90/300 = 30.00%. The specificity is 9560/9700 = 98.56%. The classifier’s overall accuracy is 9650/10,000 = 96.50%. Thus we note that although the classifier has a high accuracy, its ability to correctly label the positive (rare) class is poor given its low sensitivity. It has high specificity, meaning that it can accurately recognize negative tuples. Techniques for handling class-imbalanced data are given in Section 6.7.5.

The precision and recall measures are also widely used in classification. Precision can be thought of as a measure of exactness (i.e., what percentage of tuples labeled as positive are actually such), whereas recall is a measure of completeness (what percentage of positive tuples are labeled as such). If recall seems familiar, that’s because it is the same as sensitivity (or the true positive rate). These measures can be computed as

```
precision = TP / (TP + FP) (6.26)
```



The first section of the code reads the input data from the University of California Irvine data repository and then formats it as a list for the labels and a list of lists for the attributes. The next step is to break the data (labels and attributes) into two subsets: a test set that contains one third of the data, and a training set that contains the other two thirds. The data labeled `test` will not be used in training the classifier, but will be reserved for assessing performance after the classifier is trained. This step simulates the behavior of the classifier on new data examples after it has been deployed. Later, this chapter discusses a variety of different methods for holding out data and making estimates of performance on new data.

The classifier is trained by converting the labels M (for mine) and R (for rock) in the original data set into numeric values—1.0 corresponding to mine, and 0.0 corresponding to rock—and then using the ordinary least squares regression to fit a linear model. This is a fairly simple method to understand and to implement and will often generate very similar performance to the more sophisticated algorithms discussed later. The program in [Listing 3.2](#c03.xhtml#c03-fea-0002) employs the linear regression class from `scikit-learn` to train the ordinary least squares model. Then the trained model is used to generate predictions on the training set and on the test set.

The code prints out some representative values for the predictions. The linear regression model generates numbers that are mostly in the interval between 0.0 and 1.0, but not entirely. The predictions aren't quite probabilities. They can still be used to generate predicted classifications by comparing to a threshold value. The function `confusionMatrix()` produces the values for a confusion matrix, similar to [Figure 3.9](#c03.xhtml#c03-fig-0016). It takes the predictions, the corresponding actual values (labels), and a threshold value as input. It compares the predictions to the threshold to determine whether to assign each example to the “predicted positive” or “predicted negative” column in the confusion matrix. It uses the actual value to make the assignment to the appropriate row of the confusion matrix.

The error rates for each threshold value can be read out of the confusion matrix. The total number of errors is the sum of FPs and FNs. The example code produces confusion matrices for the in-sample data and the out-of-sample data and prints them both out. The misclassification error rate on the in-sample data is about 8 percent, and about 26 percent on the out-of-sample data. Generally, the out-of-sample performance will be worse than performance on in-sample data. It will also be more representative of the expected error on new examples.

The misclassification error changes when the thresholds are changed. [Table 3.2](#c03.xhtml#c03-tbl-0002) shows how the misclassification error rate changes as the threshold value changes. The numbers in the table are based on out-of-sample results. That will be generally true of numbers characterizing performance throughout the book. Any in-sample errors will have warning labels attached: “Warning: These are in-sample errors.” If the goal is to minimize the misclassification error, the best threshold value is 0.25.

**Table 3.2**: Dependence of Misclassification Error on Decision Threshold

| DECISION THRESHOLD | MISCLASSIFICATION ERROR RATE |
| --- | --- |
| 0.0 | 28.6 percent |
| 0.25 | 24.3 percent |
| 0.5 | 25.7 percent |
| 0.75 | 30.0 percent |
| 1.0 | 38.6 percent |

The best value for the threshold may be the one that minimizes the misclassification error. Sometimes, however, there's more cost associated with one type of error than with another. Suppose, for instance, that for the rocks-versus-mines problem it costs $100 to send a diver to do a visual inspection and that unexploded mines cost $1,000 in expected injuries and property damage if not removed. An FP costs $100, and an FN costs $1,000. Given these assumptions, [Table 3.3](#c03.xhtml#c03-tbl-0003) summarizes the dollar cost of mistakes for different threshold values. The higher cost of mistaking a mine for a rock (and leaving it in place to threaten health and safety) has pushed the decision threshold down to zero. That means more FNs, but they aren't as expensive. A more thorough analysis could include the costs associated with TP and TN. For example, the TP might have costs associated with removing the mine and a benefit of +$1,000 associated with its removal. If these figures are available (or can be reasonably approximated) in your problem, it behooves you to use them to derive better threshold values.

**Table 3.3**: Cost of Mistakes for Different Decision Thresholds

| DECISION THRESHOLD | FALSE NEGATIVE COST | FALSE POSITIVE COST | TOTAL COST |
| --- | --- | --- | --- |
| 0.0 | 1,000 | 1,900 | 2,900 |
| 0.25 | 3,000 | 1,400 | 4,400 |
| 0.5 | 9,000 | 900 | 9,900 |
| 0.75 | 18,000 | 300 | 18,300 |
| 1.00 | 26,000 | 100 | 26,100 |

Note that the relative cost of total FPs versus FNs depends on the proportion of positive and negative examples in the data set. The rocks-versus-mines data set has an equal number of positives and negatives (mines and rocks). That was presumably determined by an experimental protocol. The proportion of positives and negatives encountered in actual practice may differ. If the numbers are likely to be different when the system is deployed, you need to make some adjustments to account for the proportions in actual use.

The data scientist may not have the costs available but may still want a method to characterize the overall performance of the classifier instead of using the misclassification error rate for a particular decision threshold. A common technique for doing that is called the *receiver operating characteristic* or ROC curve (`http://en.wikipedia.org/wiki/Receiver_operating_characteristic`).

ROC inherits its name from its original application—processing returns from a radar receiver to determine the presence or absence of hostile aircraft. The ROC curve yields a single plot that summarizes all of these different contingency tables. The ROC curve plots the true positive rate (abbreviated TPR) versus the false positive rate (FPR). TPR is the proportion of positive examples that are correctly classified as positive (see [Equation 3.8](#c03.xhtml#c03-fig-0017)). FPR is the number of FPs relative to the total number of actual negatives (see [Equation 3.9](#c03.xhtml#c03-fig-0018)). In terms of the elements of the contingency table, these are given by the following formulas:

![Equation 3.8: True positive rate](images/c03-disp-0009.png)

**Equation 3.8**: True positive rate

![Equation 3.9: False positive rate](images/c03-disp-0010.png)

**Equation 3.9**: False positive rate

As a simple thought experiment, consider using an extremely low value for the decision threshold. For a low value, every example is predicted as positive. That gives 1.0 for TPR. Because everything is classified as positive, there are no FNs (FN is 0.0). It also gives 1.0 for FPR because nothing gets classified as negative (TN is 0.0). However, when the decision threshold is set very high, TP is equal to zero, and so TPR is also zero and FP is also zero because nothing gets classified as positive. Therefore, FPR is also zero. The following two figures were drawn using the `pylab roc_curve()` and `auc()` functions. [Figure 3.10](#c03.xhtml#c03-fig-0019) shows the ROC curve-based performance on in-sample data. [Figure 3.11](#c03.xhtml#c03-fig-0020) shows the ROC curve based on out-of-sample data.

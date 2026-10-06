# 4.8 Interpreting a Confusion Matrix

In the previous section, a *confusion matrix* was created to assess the predictive quality of the *k*-Nearest Neighbors model. The first classification class (red in our example) listed in a *confusion matrix* is usually called Positive Class, while the second class listed is the Negative Class (white in our example). However, which class is considered positive and which is considered *negative* is arbitrary and mostly not important as long as we agree on which one is positive and which is negative.

The *confusion matrix* from the previous section is printed below. For easier readability, the four entries are labeled as *True Positives (TP)*, *False Positives (FP)*, *False Negatives (FN)*, and *True Negatives (TN)*.

```
## Truth
## Prediction red white
## red TP: 436 FP: 46
## white FN: 44 TN: 434
```

Both (cells) in the *first row* of the confusion matrix represent the counts for predicting a wine as *red* (the positive class). The first entry shows 436 wines predicted as red which are actually red (*True Positives; TP*). On the other hand, the second entry of the first row represents 46 wines that are white and predicted as *red*, and are therefore falsely predicted because they are actually white (*False Positives; FP*).

We can make similar statements for the *second row* in the confusion matrix. The second row represents the counts for wines that are predicted as *white* (the negative class). 44 wines are predicted as white, but because they are actually *red*, they are falsely predicted (*False Negatives; FN*), while 434 are correctly predicted as *white* (*True Negatives; TN).*^5

We can calculate test *accuracy* and see that the result has improved compared to our visual attempts in Section 4.4.

```
$Accuracy = \frac{TP + TN}{TP + FP + TN + FN} = 0.91$$
```

**Warning: Be careful when interpreting accuracy as a single metric!**

^4In tidymodels, the positive class is the one that is listed first in the factor levels.
5Hint: When trying to find out which cells in a *confusion matrix* TP, FP, TN, and FN, start with interpreting the rows (the *predictions*) and then interpret the columns (the truth).

The diagonal elements of the confusion matrix indicate correct predictions, while the off-diagonals represent incorrect predictions. So, the correct classification rate is the sum of the number on the diagonal divided by the sample size in the test data. In our example, that is `(48 + 15)/78 = 81%`.

Each cell of the table has an important meaning:

![confusion matrix](Image00027.gif)

confusion matrix

*   **True positives** (`d`): these are cases in which we predicted the individuals would be diabetes-positive and they were.
*   **True negatives** (`a`): We predicted diabetes-negative, and the individuals were diabetes-negative.
*   **False positives** (`b`): We predicted diabetes-positive, but the individuals didn't actually have diabetes. (Also known as a *Type I error*.)
*   **False negatives** (`c`): We predicted diabetes-negative, but they did have diabetes. (Also known as a *Type II error*.)

Technically the raw prediction accuracy of the model is defined as `(TruePositives + TrueNegatives)/SampleSize`.

## 30.6 Precision, Recall and Specificity

In addition to the raw classification accuracy, there are many other metrics that are widely used to examine the performance of a classification model, including:

**Precision**, which is the proportion of true positives among all the individuals that have been predicted to be diabetes-positive by the model. This represents the accuracy of a predicted positive outcome. `Precision = TruePositives/(TruePositives + FalsePositives)`.

**Sensitivity** (or **Recall**), which is the **True Positive Rate** (`TPR`) or the proportion of identified positives among the diabetes-positive population (class = 1). `Sensitivity = TruePositives/(TruePositives + FalseNegatives)`.

**Specificity**, which measures the **True Negative Rate** (`TNR`), that is the proportion of identified negatives among the diabetes-negative population (class = 0). `Specificity = TrueNegatives/(TrueNegatives + FalseNegatives)`.

**False Positive Rate** (`FPR`), which represents the proportion of identified positives among the healthy individuals (i.e. diabetes-negative). This can be seen as a false alarm. The `FPR` can be also calculated as `1-specificity`. When positives are rare, the `FPR` can be high, leading to the situation where a predicted positive is most likely a negative.

**Sensitivy** and **Specificity** are commonly used to measure the performance of a predictive model.

These above mentioned metrics can be easily computed using the function `confusionMatrix()` [`caret` package].

In two-class setting, you might need to specify the optional argument `positive`, which is a character string for the factor level that corresponds to a "positive" result (if that makes sense for your data). If there are only two factor levels, the default is to use the first level as the "positive" result.

```
## Confusion Matrix and Statistics
## 
##           Reference
## Prediction neg pos
##        neg  48  11
##        pos   4  15
##                                         
##                Accuracy : 0.808         
##                  95% CI : (0.703, 0.888)
##     No Information Rate : 0.667         
##     P-Value [Acc > NIR] : 0.00439       
##                                         
##                   Kappa : 0.536         
##  Mcnemar's Test P-Value : 0.12134       
##                                         
##             Sensitivity : 0.577         
##             Specificity : 0.923         
##          Pos Pred Value : 0.789         
##          Neg Pred Value : 0.814         
##              Prevalence : 0.333         
##          Detection Rate : 0.192         
##    Detection Prevalence : 0.244         
##       Balanced Accuracy : 0.750         
##                                         
##        'Positive' Class : pos           
## 
```

The above results show different statistical metrics among which the most important include:

*   the cross-tabulation between prediction and reference known outcome
*   the model accuracy, 81%
*   the [kappa](https://en.wikipedia.org/wiki/Cohen%27s_kappa) (54%), which is the accuracy corrected for chance.

In our example, the sensitivity is ~58%, that is the proportion of diabetes-positive individuals that were correctly identified by the model as diabetes-positive.

The specificity of the model is ~92%, that is the proportion of diabetes-negative individuals that were correctly identified by the model as diabetes-negative.

The model precision or the proportion of positive predicted value is 79%.

In medical science, sensitivity and specificity are two important metrics that characterize the performance of classifier or screening test. The importance between sensitivity and specificity depends on the context. Generally, we are concerned with one of these metrics.

In medical diagnostic, such as in our example, we are likely to be more concerned with minimal wrong positive diagnosis. So, we are more concerned about high Specificity. Here, the model specificity is 92%, which is very good.

In some situations, we may be more concerned with tuning a model so that the sensitivity/precision is improved. To this end, you can test different probability cutoff to decide which individuals are positive and which are negative.

Note that, here we have used `p > 0.5` as the probability threshold above which, we declare the concerned individuals as diabetes positive. However, if we are concerned about incorrectly predicting the diabetes-positive status for individuals who are truly positive, then we can consider lowering this threshold: `p > 0.2`.

## 30.7 ROC curve

### 30.7.1 Introduction

The **ROC curve** (or **receiver operating characteristics curve**) is a popular graphical measure for assessing the performance or the accuracy of a classifier, which corresponds to the total proportion of correctly classified observations.

For example, the accuracy of a medical diagnostic test can be assessed by considering the two possible types of errors: false positives, and false negatives. In classification point of view, the test will be declared positive when the corresponding predicted probability, returned by the classifier algorithm, is above a fixed threshold. This threshold is generally set to 0.5 (i.e., 50%), which corresponds to the random guessing probability.

So, in reference to our diabetes data example, for a given fixed probability cutoff:

*   the **true positive rate** (or fraction) is the proportion of identified positives among the diabetes-positive population. Recall that, this is also known as the **sensitivity** of the predictive classifier model.
*   and the **false positive rate** is the proportion of identified positives among the healthy (i.e. diabetes-negative) individuals. This is also defined as `1-specificity`, where **specificity** measures the **true negative rate**, that is the proportion of identified negatives among the diabetes-negative population.

Since we don't usually know the probability cutoff in advance, the ROC curve is typically used to plot the true positive rate (or sensitivity on y-axis) against the false positive rate (or "1-specificity" on x-axis) at all possible probability cutoffs. This shows the trade off between the rate at which you can correctly predict something with the rate of incorrectly predicting something. Another visual representation of the ROC plot is to simply display the sensitive against the specificity.

The **Area Under the Curve** (**AUC**) summarizes the overall performance of the classifier, over all possible probability cutoffs. It represents the ability of a classification algorithm to distinguish 1s from 0s (i.e, events from non-events or positives from negatives).

For a good model, the ROC curve should rise steeply, indicating that the true positive rate (y-axis) increases faster than the false positive rate (x-axis) as the probability threshold decreases.

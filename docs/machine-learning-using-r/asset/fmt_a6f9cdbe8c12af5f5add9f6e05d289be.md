
## Youden's Index

Sensitivity and specificity change when we change the cut-off probability. Youden’s Index (Youden, 1950) is a classification cut-off probability for which the following function is maximized (also known as /-statistic):

![](images/page207-01.png)

That is, select the cut-off probability for which `tpr+tnr−1` is maximum. The `tpr` is true positive rate and `tnr` is true negative rate.

Note that while trying to find the optimal cut-off, we will have to use the `train_dt` and not the `test_dt`. We will create `train_rocr_prediction` object using `prediction()` and then use the measures needed to compute `tpr` and `tnr`.

![](images/page207-02.png)

`[Table 6.9](#14_Chapter06.xhtml#tab6.9)` shows the first six observations from the `train_rocr_prediction_measures` dataframe.

Let us compute `tpr` and `fpr` by passing `train_rocr_prediction` parameter to the `performance()`. `[Table 6.10](#14_Chapter06.xhtml#tab6.10)` shows the first six observations from the `train_rocr_performance` dataframe.

![](images/page207-03.png)![](images/page207-04.png)

**TABLE 6.10** | Train ROCR performance measures

| Fpr || tpr |
| --- | --- |
| 0.0000000 || 0.0000000 |
| --- | --- |
| 0.0000000 || 0.0042450 |
| 0.0002279 || 0.0806549 |
| 0.0006837 || 0.2395391 |
| 0.0015953 || 0.3917526 |
| 0.0018232 || 0.4863554 |

Let us bind `train_rocr_prediction_measures` and `train_rocr_performance_measures` using `cbind()` function. `[Table 6.11](#14_Chapter06.xhtml#tab6.11)` shows the merged dataframe.

![](images/page208-01.png)

Since false positive rate (`fpr`) = 1 − true negative rate (`tnr`), we can calculate Youden’s index as `tpr-fpr`. `[Table 6.12](#14_Chapter06.xhtml#tab6.12)` shows the Youden’s index calculated using the below code snippet.

![](images/page208-02.png)

`[Table 6.13](#14_Chapter06.xhtml#tab6.13)` shows 0.26 as the cut-off which maximizes the Youden’s Index on the `train_dt`. Using `predict()`, we saved the `test_predicted_prob` on the `test_dt` earlier. Let us use `best_cutoff` on the `test_dt` and build a classification matrix.

![](images/page208-03.png)![](images/page208-04.png)![](images/page209-01.png)![](images/page209-02.png)

We can compare the above outcome at a cut-off of 0.26 with the outcome at default cutoff of 0.50 (in [Section 6.4.2](#14_Chapter06.xhtml#sec6.4.2)). We can conclude that the cut-off of 0.26 has improved the sensitivity.

### Cost-Based Approach

In cost-based approach, we assign penalty cost for misclassification of positives and negatives. Assume that the cost of a false positive rate (`FPR`) is `C1` and the cost of false negative rate (`FNR`) is `C2`. Then, the penalty is defined as

![](images/page209-03.png)

The optimal cut-off probability is the one which minimizes the total penalty. Let us build a cost matrix for the HR Attrition problem. Here, the primary objective for HR is to have a model which correctly classifies employees who are likely to leave the organization even if the model misclassifies some of the cases where an employee is still working.

**Fine-tuning the cut-off probability** is an important consideration while deploying the model outcome for decision making. Techniques such as Youden’s Index, Cost of mis-classification are used to fine-tune the cut-off probability of a binary logistic regression model.

![](images/page210-01.png)![](images/page210-02.png)

With the above objective, we can formulate a cost matrix where penalty for misclassifying No as Yes is twice as costly compared to misclassifying Yes as No.

![](images/page210-03.png)

Let us use the above cost matrix and `optimal_cutoff_df` to calculate the penalty using the [Eq. (6.23)](#14_Chapter06.xhtml#eq6.23). `[Table 6.14](#14_Chapter06.xhtml#tab6.14)` shows the resultant table with misclassification cost column.

![](images/page210-04.png)

We found out that the best cut-off which will minimize the penalty, on the `train_dt`, is 0.16 **([Table 6.15](#14_Chapter06.xhtml#tab6.15)).** Note that the cut-off based on Youden’s Index was found to be 0.26 **([Table 6.13](#14_Chapter06.xhtml#tab6.13)).**

Using `predict()`, we saved the `test_predicted_prob` on the `test_dt` earlier. Let us use `best_cutoff` on the `test_dt` and build a classification matrix.

![](images/page210-05.png)![](images/page211-01.png)

We can compare the above confusion matrix (at cut-off of 0.16) with the confusion matrix (at Youden’s Index cut-off of 0.26 in [Section 6.4.5](#14_Chapter06.xhtml#sec6.4.5)). We can conclude that a cut-off of 0.16 has improved the sensitivity compared to the sensitivity at a cut-off of 0.26.

## 6.5 | Gain Chart and Lift Chart

Gain chart and lift chart (Kumar, 2017) are two measures used to measure the benefits of using the logistic regression model (in general analytical model) and are used in business contexts such as target marketing. In target marketing or marketing campaigns, customer responses to campaigns are usually very low (in many cases, customers who respond to marketing campaigns are less than 1%). Another example of such low response is advertisement on the internet (such as Google Adwords and mobile advertisements). The organization will incur a cost for each customer contact and hence would like to minimize the cost of the marketing campaign while at the same time hoping to achieve a desired response level from customers. The gain and lift charts are obtained using the following steps:

**1.** Predict the probability of positive response (`Y` = 1) using LR model and arrange the observations in the decreasing order of predicted probability [i.e., `P(Y = 1)`].

**2.** Divide datasets into deciles. Calculate the number of positives (`Y` = 1) in each decile and the cumulative number of positives up to a decile.

**3.** Gain is the ratio between cumulative number of the positive observations up to a decile to total number of positive observations in the data. Gain chart is a chart drawn between gain on vertical axis and decile on the horizontal axis.

![](images/page212-01.png)

Let us apply the gain chart on the HR attrition data. From the `test_dt`, we know that there are 27% positive cases, that is, No (`Y` = 1). The total number of cases in the `test_dt` is 1,508. If we use a random model to pick 10% of the cases from 1,508 cases, we will have approximately 41 employees who will be with a `WORKING_STATUS` = No, that is, positive cases. We can say that the rate of positive prediction for the random model is 27%. Let us see how much gain the LR model gives over the random model.

![](images/page212-02.png)

At the level where the random model will pick 27% rate of positive prediction (`Y` = ‘No’), the `step_logisitic_model` would give approximately 79% as the rate of positive prediction **([Table 6.16](#14_Chapter06.xhtml#tab6.16)).** **[Figure 6.5](#14_Chapter06.xhtml#fig6.5)** shows the gain chart plotted using the gain object returned by the `performance()`.

![](images/page212-03.png)

**4.** Lift is the ratio of number of positive observations up to decile *i* using the LR model to the expected number of positives up to that decile *i* based on a random model (not using a model). Lift chart is the chart between lift on the vertical axis and the corresponding decile on the horizontal axis.

![](images/page212-04.png)![](images/page212-05.png)![](images/page213-01.png)

Let us use the lift on the `test_dt`.

![](images/page214-01.png)

At the level where the random model will pick 27% rate of positive prediction (`Y` = ‘No’), the `step_logisitic_model` would produce 2.96 times the random model, that is, approximately 79% will be the rate of positive **([Table 6.17](#14_Chapter06.xhtml#tab6.17)).** **[Figure 6.6](#14_Chapter06.xhtml#fig6.6)** shows the lift chart plotted using the lift object returned by the `performance()`.

![](images/page214-02.png)![](images/page215-01.png)![](images/page216-01.png)![](images/page216-02.png)

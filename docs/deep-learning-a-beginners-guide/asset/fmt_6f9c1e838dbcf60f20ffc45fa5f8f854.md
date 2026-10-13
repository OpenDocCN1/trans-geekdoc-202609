
# Root Mean Square Error (RMSE)

Root mean square error (RMSE) calculates the square root of mean squared error as given in (7.17). The disparities between the model predicted values and the actual values are quantified by this term, which is also known as the root mean squared deviation. While MAE assigns all errors the same weight, the RMSE penalizes uncertainty by giving greater absolute value errors more weight than smaller absolute value errors. The RMSE is never less than the MAE since all metrics are evaluated.

$$\text{RMSE} = \sqrt{\frac{1}{n}\sum\limits_{i = 1}^{n}\left( {y - \hat{y}} \right)^{2}} \tag{7.17}$$

Where `n`, `y`, and `ŷ` denote the total number of data points, actual and predicted output, respectively.

## Logarithmic Loss (Log Loss)

Logarithmic loss indicates the closeness of the prediction probability to the actual/ corresponding true value. The maximization of the likelihood is equivalent to minimizing the MSE. It accounts for the uncertainty in model projections by penalizing the incorrect predictions. This performs well for multi-class classification and lower values give better performances as shown in [Figure 7.7](#ch14.xhtml#f109). Here, the model sets a probability for every class. This supports comparing the performance of the two models. Log loss exists between `[0, ∞)` and has no upper bound. Higher accuracy is indicated by a log loss that is closer to zero, whereas a log loss that is further from zero suggests lower accuracy. In general, the classifier is more accurate when log loss is minimized. This can be defined as in (7.18) or (7.19).

![Figure 7.7 Representation of log loss error.](html/images/9781032473246_C007_007.jpg)

[Figure 7.7](#ch14.xhtml#f109b) Representation of log loss error.

$$\text{Log loss} = - \frac{1}{\text{N}}\sum\limits_{\text{i} = 1}^{\text{n}}\left( {\text{log}\left( \text{p}_{\text{i}} \right)\text{*y}_{\text{i}}} \right) + \left( {\left( {1 - \text{y}_{\text{i}}} \right)\text{*log}\left( {1 - \text{p}_{\text{i}}} \right)} \right) \tag{7.18}$$

where, `N` is the number of observations, and `p` is the predicted probabilities that observation `i` is 1, `y` is the true label (0 or 1) for observation `I`, in binary classification.

This can be also represented by

$$\text{Log loss} = - \frac{1}{N}\sum\limits_{i = 1}^{N}\sum\limits_{j = 1}^{M}\left( {\text{log}\left( p_{ij} \right)\text{*}y_{ij}} \right) \tag{7.19}$$

where `N` samples belong to `M` classes,

`y[ij]` indicates whether sample `i` belongs to class `j` or not

`p[ij]` indicates the probability of sample `i` belonging to class `j`

## R Squared Error

R squared or the coefficient of determination shows how closely the model’s forecasts match the actual data. This is calculated as in (7.20). R squared has an understandable value and is not affected by the actual output, and does not provide any insight into the prediction error.

$$\text{R squared error} = 1 - \frac{\sum_{i = 1}^{n}\left( {y_{i} - {\hat{y}}_{i}} \right)^{2}}{\sum_{i = 1}^{n}\left( {y_{i} - \overline{y}} \right)^{2}} \tag{7.20}$$

where `y`, `ŷ`, and `ȳ` denote the actual, predicted, and the mean of the actual values.

# 7.2.13 Summary of Performance Metrics

The effectiveness of the performance metrics depends on the data types, application domain, and other constraints. Table 7.1 represents a summary of performance metrics.

## Table 7.1 Summary of Performance Metrics

| Technique | Description |
| --- | --- |
| Accuracy | It is mostly used when all the classes are equally important, and the problem is balanced |
| Precision | Precision becomes crucial for extremely unbalanced datasets with significantly more negatives than positives because they are easy to get high accuracy for (always predicting negative would result in high accuracy). |
| Recall | When the cost of a false negative is high, should use recall. |
| F1-measure | In order to find a balance between precision and recall in an unequal class distribution, F1-score can be used to utilize a task with many TNs. |
| Mean absolute error (MAE) | When performance is evaluated using continuous data, MAE is typically used. It produces a linear number that evenly weights the individual differences and averages them. The model performs better the lower the value. |
| Mean squared error (MSE) | MSE is used to assess regression models that are used to predict dependent variables that are numeric, while modeling independent variables and dependent or target variables. |
| ROC | Do not use it when data is heavily imbalanced. |
| AUC | Use when caring equally about positive and negative classes. |
| PR-AUC | When data is imbalanced and when care more about positive than negative class. |
| Hold-out method | One train-test split is all that the hold out approach requires. As a result, the score of the hold-out approach depends on how the data is divided into the train and test sets. When a dataset is really huge, this method is useful. |
| `k`-cross-validation | `k`-cross validation is a resampling method used to assess a model when we have less data and to examine the efficacy of the learning models. |
| Leave-one-out cross-validation | When the dataset is small or when an accurate assessment of model performance is more important than the computing cost of the method, the leave-one-out cross-validation procedure is appropriate. |
| Confusion matrix | When the output of the classifier has two or more classes, the confusion matrix is used. Important predictive analytics like accuracy, recall, precision, and specificity are visualized using the associated TP, TN, FP, FN values in the confusion matrix. |
| Sensitivity | The percentage of accurately categorized positive instances is the sensitivity. It assesses how well a classification performs when the data is unbalanced. |
| Specificity | The percentage of the negative instances that are accurately categorized is known as the specificity. This can be used with imbalanced data. |
| Kappa score | The kappa score calculates the prediction’s agreement with the true class |
| Logarithmic loss | Log loss, can compare the performance of two models and then decide which model performs better. |

# Review Questions

1.  What is the ROC curve and what does it represent?
2.  When there are many false positives or false negatives, how does it impact the model?
3.  What is overfitting and what are the methods that can be used to prevent it?
4.  When the values of `k` becomes larger in `K`-fold cross-validation, can it result in overfitting or underfitting? Explain your answer.
5.  Explain the confusion matrix concerning machine learning algorithms.
6.  What is the best way to measure performance improvement on imbalanced datasets?
7.  What are the pain points of Cohen’s Kappa?

# Appendix – Frequently Asked Questions

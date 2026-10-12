
# Model Performance Evaluation

In this chapter, we will focus on the key concepts of model performance evaluation, the evaluation process, and the critical metrics needed to assess model fit. As discussed in [Chapter 2](#chapter2.xhtml), a common practice in data mining is to build multiple models using different machine learning methods and then compare their performance to select the best, or "champion," model. Before comparing models, we must first decide on the appropriate metrics for evaluating model fit.

There are some interchangeable terms in this area, which can be confusing. Therefore, I will provide clear definitions and explanations of these terms and when to use them. Having this foundational understanding is essential for choosing the right metrics and following the proper evaluation process. It is important to note that the metrics covered in this chapter apply only to supervised learning, where there is a predefined target variable, and the goal is to predict that variable. These metrics do not apply to unsupervised learning, as there is no prediction involved. Furthermore, the metrics used for association models (with a continuous target variable) differ from those used for classification models (with a categorical target variable). Therefore, attention must be paid to the scale of the target variable to ensure the correct metrics are selected.

## Basic Concepts

![](images/ufig6_2.jpg)

Before we go further into the topic of model evaluation, I will introduce some key basic concepts, which are outlined in [Table 6.1](#chapter6.xhtml#tbl6_1). These concepts are essential for understanding the terminology used throughout this chapter. Use the table as a reference as we proceed. I will explain each concept in detail, and you can always return to the table to refresh your memory or check the definition of a specific term when needed.

**TABLE 6.1** Basic Concepts in Model Performance Evaluation [Return to text.⏎](#chapter6.xhtml#b6tbl6_1)

| Terms | Descriptions |
| --- | --- |
| `Model fit` | `Model fit` measures how well the model fits the data. It assesses the degree to which the model captures the patterns and relationships within the data. |
| `Predictive power` | `Predictive power` refers to a model's ability to accurately capture and represent the underlying patterns, relationships, or trends in the data, and effectively generalize these results to new, unseen datasets. |
| `Overfitting` | `Overfitting` occurs when a model is overly trained to fit the training sample, capturing even the noise and minor fluctuations in the data. As a result, the model fails to generalize to other datasets, making it invalid and unusable for real-world predictions. |
| `Model reliability` | `Model reliability` refers to the internal consistency of a model. It means the model produces consistent results across different runs using different datasets. |
| `Model validity` | `Model validity` refers to the accuracy of the model. It means the model consistently produces an accurate prediction of the target variable. |
| `Champion model` | `Champion model` is the model that demonstrates the best performance among all the models we train and test. |
| `Prediction errors` | `Errors` measure the extent to which the trained model misfits the data. The lower the error, the more accurate the model. |
| `Sum of squared error (SSE)` | `SSE` measures unexplained variance, which is how far the data are from the model's predicted values. |
| `Sum of squared regression (SSR)` | `SSR` measures explained variance, which is how far the mean is from the model's predicted values. |
| `Sum of squared total (SST)` | `SST` measures total variance, which is how far the data are from the mean. |
| `Root mean squared error (RMSE)` | `RMSE` is a common metric for association models. It measures the average difference between the predicted values and the actual values in a dataset, expressed in the same units as the predicted variable. |
| `Mean absolute percentage error (MAPE)` | `MAPE` is a common metric for association models. It measures the percentage difference between the predicted values and the actual values in a dataset. |
| `Relative squared error (RSE)` | `RSE` is a common metric for association models. It measures the relative improvement of the model's predictions compared to a simple baseline model that always predicts the mean of the actual values. |
| `Explanatory power (EP)` | `EP` refers to the ability of a predictive model, especially association model, to explain or predict the variability observed in the data. It measures how well the model captures the underlying relationships between the input variables (predictors) and the target variable. |
| `Actual by Predicted Chart` | The `Actual by Predicted Chart` compares the actual values with the predicted values, showing us how well the trained model fits the data. |
| `Residuals` | `Residuals` measure the difference between actual values and predicted values in a dataset. |
| `Residual by predicted chart` | The `residual by predicted chart` presents not only how close the actual values are to the predicted values but also indicates any patterns in the residuals. |
| `Confusion matrix` | `Confusion matrix`, also called the classification matrix, is the table that summarizes the performance of a classification algorithm. |
| `True positive (TP)` | `TP` is the prediction that correctly indicates the presence of the event. |
| `True negative (TN)` | `TN` is the prediction that correctly indicates the absence of the event. |
| `False positive (FP)` | `FP` is the prediction that wrongly indicates the presence of the event. |
| `False negative (FN)` | `FN` is the prediction that wrongly indicates the absence of the event. |
| `Misclassification rate (MR)` | `MR` is a measure of how often a model misclassifies (makes incorrect predictions) the target variable (including actual positives and actual negatives). |
| `Prediction accuracy (ACC)` | `ACC` is a measure of how accurate a model predicts the target variables (including actual positives and actual negatives). |
| `Sensitivity, recall, or true positive rate (TPR)` | `Sensitivity` is the probability of a positive result (event) or how well a model can predict true positives (events). |
| `Specificity, selectivity, or true negative rate (TNR)` | `Specificity` is the probability of a negative result (non-event) or how well a model can predict true negatives (non-events). |
| `F1 score` | `F1 score` is the harmonic mean of the sensitivity (recall) and precision (positive predicted value); a high `F1 score` means low false positives (`FP`) and low false negatives (`FN`). |
| `Receiver operating characteristic (ROC) chart` | The `ROC chart` displays the true positive rate on the vertical axis and the false positive rate on the horizontal axis, reflecting the balance between sensitivity and specificity. |
| `Lift chart` | `Lift` is an indicator of a predictive model's effectiveness, calculated as the ratio of the results achieved with the model compared to those without it. The `Lift chart`, or `Lift curve`, presents the graphic representation between the lift values and response rates. |
| `Gini coefficient` | `Gini coefficient` is a measure of the model's discriminatory power, which is the effectiveness of the model in differentiating between positives and negatives. The `Gini coefficient` measures how equal the positive rates are across the attributes of a characteristic. |
| `Cost sensitive learning` | `Cost sensitive learning` is a method to evaluate and select a model based on the costs of misclassification. |
| `Decision matrix` | `Decision matrix` is the table that presents the costs of misclassifications, including costs of false positives and costs of false negatives. |

## Model Fit and Predictive Power

![](images/ufig6_3.jpg)

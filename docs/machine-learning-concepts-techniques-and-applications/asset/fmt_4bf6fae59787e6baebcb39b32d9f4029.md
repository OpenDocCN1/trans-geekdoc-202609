
After building a predictive classification model, you need to evaluate the performance of the model, that is, how good the model is in predicting the outcome of new test data that has not been used to train the model. In other words, we need to estimate the model prediction *accuracy* and prediction errors using a new test data set. Because we know the actual outcome of observations in the test data set, the performance of the predictive model can be assessed by comparing the predicted outcome values against the known outcome values. Evaluation metrics are used to measure the quality of the classification model. When we build the model, it is crucial to measure how accurately the expected outcome is predicted. There are different evaluation metrics for different sets of machine learning algorithms. For evaluating classification models, we use classification metrics, and for regression models, we use regression metrics. Evaluation metrics help to assess your model’s performance, monitor your machine learning system in production, and control the model to fit the business needs. The goal of any classification system is to create and select a model which gives high accuracy on unseen data. It is important to use multiple evaluation metrics to evaluate the model because a model may perform well using one measurement from one evaluation metric while it may perform poorly using another measurement from another evaluation metric ([Agrawal, 2022](#ch8.xhtml#ref8_1)).

## 8.2 Classification Metrics

### 8.2.1 Binary Classification

Classification is about predicting the class labels given input data. In binary classification, there are only two possible output classes (i.e., dichotomy). In multi-class classification, more than two possible classes can be present. There are many ways for measuring classification performance ([Beheshti, 2022](#ch8.xhtml#ref8_2)). Accuracy, confusion matrix, log-loss, and area under curve/receiver operator characteristic (AUC-ROC) are some of the most popular metrics. Precision and recall are widely used metrics for classification problems.

We will first describe the confusion matrix, which is an `n` × `n` matrix (where `n` is the number of labels) used to describe the performance of a classification model on a set of test data for which the true values are known. Each row in the confusion matrix represents an actual class whereas each column represents a predicted class. A confusion matrix for two classes (binary classification) `C1` and `C2` is shown in [Figure 8.1](#ch8.xhtml#fig8_1).

![Figure 8.1 Confusion matrix for binary classification.](images/fig8_1_B.jpg)

[Figure 8.1 Confusion matrix for binary classification.](#ch8.xhtml#R_fig8_1)

Consider, we have a machine learning model classifying passengers as cancer positive and negative. When performing classification predictions, there are four types of outcomes that could occur ([Figure 8.2](#ch8.xhtml#fig8_2)):

*   **True Positive (`TP`)**: When you predict an observation belongs to a class and it actually does belong to that class—in this case, a passenger who is classified as cancer positive and is actually positive.
*   **True Negative (`TN`)**: When you predict an observation does not belong to a class and it actually does not belong to that class—in this case, a passenger who is classified as not cancer positive (negative) and is actually not cancer positive (negative).
*   **False Positive (`FP`)**: When you predict an observation belongs to a class and it actually does not belong to that class—in this case, a passenger who is classified as cancer positive and is actually not cancer positive (negative).
*   **False Negative (`FN`)**: When you predict an observation does not belong to a class and it actually does belong to that class—in this case, a passenger who is classified as not cancer positive (negative) and is actually cancer positive.

![Figure 8.2 Confusion matrix—Binary classification example.](images/fig8_2_B.jpg)

[Figure 8.2 Confusion matrix—Binary classification example.](#ch8.xhtml#R_fig8_2)

Now, given the confusion matrix, we will discuss the various evaluation metrics.

#### 8.2.1.1 Accuracy

The first metric is accuracy. Accuracy focuses on true positive and true negative. Accuracy is one metric which gives the fraction of predictions that are correct. Formally, accuracy is defined as given in Equation (8.1).

(8.1)

```math
\text{Accuracy} = \frac{\text{Number of correct predictions}}{\text{Total number of predictions}}
```

In terms of the confusion matrix, accuracy is defined as given in [Figure 8.3](#ch8.xhtml#fig8_3).

![Figure 8.3 Accuracy.](images/fig8_3_B.jpg)

[Figure 8.3 Accuracy.](#ch8.xhtml#R_fig8_3)

The accuracy in the example given in [Figure 8.3](#ch8.xhtml#fig8_3) is 99.9%. The objective here is to identify actual cancer patients, and the incorrect labelling of these positive patients as negative is not acceptable; hence in this scenario accuracy is not a good measure.

#### 8.2.1.2 Sensitivity or True Positive Rate

Recall or sensitivity gives the fraction we correctly identified as positive out of all positives (given in [Figure 8.5](#ch8.xhtml#fig8_5)) or in other words indicates how precise we are during prediction.

![Figure 8.5 Recall or sensitivity.](images/fig8_5_B.jpg)

[Figure 8.5 Recall or sensitivity.](#ch8.xhtml#R_fig8_5)

This measure shows the fraction of the correctly identified positive cases out of all the actual positive cases. In [Example 8.1](#ch8.xhtml#box8_1), recall is `0/10 = 0`. In this scenario recall is a good measure. We normally want to maximize the recall. Now let us assume that all patients in the data set are wrongly classified as positive for cancer. This labelling is bad since it leads to mental agony as well as the cost of investigation. As can be seen from [Figure 8.6a](#ch8.xhtml#fig8_6), `Recall = 1`, and this is again not a good measure.

![Figure 8.6 (a) Calculation of recall, (b) specificity.](images/fig8_6_B.jpg)

[Figure 8.6 (a) Calculation of recall, (b) specificity.](#ch8.xhtml#R_fig8_6)

However, this is also not a good measure when measured independently. Recall needs to be measured in coordination with precision. We can also define `specificity` for the negative cases as in [Figure 8.6b](#ch8.xhtml#fig8_6).

#### 8.2.1.3 Precision

Precision gives the fraction we correctly identified as positive out of all positives that were predicted (given in [Figure 8.7](#ch8.xhtml#fig8_7)) or in other words indicates how good we are at prediction.

![Figure 8.7 Precision.](images/fig8_7_B.jpg)

[Figure 8.7 Precision.](#ch8.xhtml#R_fig8_7)

Now let us assume again that in [Example 8.1](#ch8.xhtml#box8_1) all patients in the data set are wrongly classified as positive for cancer. The calculation of precision in this case is shown in [Figure 8.8](#ch8.xhtml#fig8_8). For this case we have high recall value and low precision value.

![Figure 8.8 Calculation of precision.](images/fig8_8_B.jpg)

[Figure 8.8 Calculation of precision.](#ch8.xhtml#R_fig8_8)

In some cases, we are pretty sure that we want to maximize either recall or precision at the cost of others.

#### 8.2.1.4 Precision/Recall Trade-off

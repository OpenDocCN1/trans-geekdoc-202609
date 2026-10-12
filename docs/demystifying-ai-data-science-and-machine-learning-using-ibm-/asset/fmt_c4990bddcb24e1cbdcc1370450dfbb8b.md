
# Model Fit Metrics for Nominal (Multi-Class) Target Variables

## Total Profit Formula

`Total Profit = P(TP) × TP + P(TN) × TN − C(FN) × FN − C(FP) × FP`

## Model Fit Metrics for Nominal (Multi-Class) Target Variables

In most data mining projects, we often work with **binary target variables** to predict the occurrence of events versus non-events. However, in some cases, we encounter **nominal target variables** with multiple levels, also known as **multi-class target variables**.

So, how do we measure model fit in this scenario? Essentially, we use the same metrics as for binary target variables, but with some modifications. The most significant difference is that the **confusion matrix** for multi-class target variables has more levels, making it more complex. [Table 6.12](#chapter6.xhtml#tbl6_12) shows a confusion matrix for a target variable with three levels (1, 2, and 3). For example, imagine we want to predict residents’ shopping behaviors during the COVID-19 pandemic, where their choices are as follows:

1.  Online shopping
2.  Curbside pickup
3.  In-store shopping

### Table 6.12: Confusion Matrix for a Three-Class Target Variable

| | Predicted 1 | Predicted 2 | Predicted 3 |
|---|---|---|---|
| **Actual 1** | a | l | m |
| **Actual 2** | x | b | n |
| **Actual 3** | y | z | c |

The confusion matrix includes actual and predicted values for all three levels. The challenge is calculating model fit metrics, which typically rely on **True Positives (TP)**, **True Negatives (TN)**, **False Positives (FP)**, and **False Negatives (FN)**. Since there are three classes, we need to determine how to calculate these values for each class.

I explain below a method for calculating **True Positives (TP)**, **True Negatives (TN)**, **False Positives (FP)**, and **False Negatives (FN)** for a multi-class target variable. Essentially, we calculate these metrics separately for each class. For each class, we treat that class as **positive** and the other two classes as **negative**. The following formulas allow us to calculate these values for each class.

#### For Class 1

*   `TP = a`
*   `TN = b + c + n + z`
*   `FP = x + y`
*   `FN = l + m`

#### For Class 2

*   `TP = b`
*   `TN = a + c + m + y`
*   `FP = l + z`
*   `FN = x + n`

#### For Class 3

*   `TP = c`
*   `TN = a + b + l + x`
*   `FP = m + n`
*   `FN = y + z`

Once we calculate **TP**, **TN**, **FP**, and **FN** for each class, we can apply the same formulas used for binary target variables to compute model fit metrics. However, unlike binary classification, where we calculate the metrics only once, for multi-class target variables, we must calculate these metrics separately for each class. For example, in this case, we need to compute the following metrics for all three classes.

**Class 1:**
*   `MR (Class 1)`
*   `ACC (Class 1)`
*   `TPR (Class 1)`
*   `TNR (Class 1)`
*   `F1 score (Class 1)`

**Class 2:**
*   `MR (Class 2)`
*   `ACC (Class 2)`
*   `TPR (Class 2)`
*   `TNR (Class 2)`
*   `F1 score (Class 2)`

**Class 3:**
*   `MR (Class 3)`
*   `ACC (Class 3)`
*   `TPR (Class 3)`
*   `TNR (Class 3)`
*   `F1 score (Class 3)`

![Figure 6.39](images/ufig6_39.jpg)

When evaluating model fit and comparing between models, we need to use the model fit metrics for all three classes.

As for the **ROC chart** and **Lift chart**, these charts can only be constructed for binary target variables because they are two-dimensional. However, most software provides the following metrics for multi-class models:

*   **AUROC (Area Under the ROC Curve)**: Measures the area between the model's ROC curve and the baseline.
*   **Lift value**: Measures the Lift of the model compared to the baseline (no model).
*   **Gini coefficient**: Evaluates the model's discriminatory power.

## Chapter Summary

Evaluating predictive model performance is a complex and nuanced task, given the variety of variables, modeling methods, and potential challenges in model development. In this chapter, we explored several key concepts and terminologies related to model fit and predictive power. Model fit refers to how well a model captures the patterns in the data for a specific sample, such as the training sample, while predictive power measures how well the model performs across different datasets, ensuring its generalizability. A model that performs well on the training data but fails to make accurate predictions on new data is said to suffer from overfitting, which compromises its predictive power. We also examined strategies to avoid or minimize overfitting. Additionally, we discussed the differences between model reliability and model validity, highlighting the importance of assessing both.

The second half of this chapter focused on various metrics used to measure model fit for both association models (with continuous target variables) and classification models (with binary or multi-class target variables). We introduced a wide range of metrics, such as `RMSE`, `MAPE`, `RSE`, and `EP` for association models, and metrics like accuracy, sensitivity, specificity, and the `F1 score` for classification models. I also provided guidelines on selecting the most appropriate metrics based on the type of model and the scale of the target variable. We emphasized the importance of using multiple metrics to gain a more comprehensive understanding of model performance, as relying on a single metric could lead to a misleading evaluation.

Furthermore, we explored additional metrics, such as the **ROC chart**, **Lift chart**, and the **Gini coefficient**, which provide additional insights into model performance, particularly for classification models. These metrics offer a more detailed view of how well a model differentiates between positive and negative outcomes, helping to fine-tune predictions.

Lastly, we introduced cost-sensitive learning (CSL), an important method for selecting models based on the costs of misclassification. In many real-world scenarios, such as fraud detection or medical diagnosis, the costs of false negatives and false positives are not equal. CSL allows us to account for these differences and choose models that minimize the total cost rather than focusing solely on the accuracy or misclassification rate. This chapter sets the foundation for using CSL in future predictive modeling tasks, which will be demonstrated in [Chapter 8](#chapter8.xhtml).

## Chapter Discussion Questions

1.  What is the purpose of model evaluation, and why is it important in data mining?
2.  What is model fit? Explain the difference between model fit and predictive power. How do they overlap? Provide examples to illustrate.
3.  What is overfitting, and how does it affect the validity of a predictive model?
4.  What are the primary root causes of overfitting? What strategies can be used to address overfitting?
5.  Differentiate between model reliability and model validity. Provide specific examples of each.
6.  Why is it important to evaluate both model reliability and validity? List the steps involved in evaluating the reliability and validity of predictive models.
7.  What is the purpose of model comparison in data mining, and why is it essential?
8.  What is a champion model? Is the champion model always the best model overall? Why do we need a champion model in the context of data mining?
9.  What is the recommended model fit metrics for association models, and why are they recommended?
10.  Define confusion matrix. Explain its importance in evaluating classification models.
11.  Describe the recommended model fit metrics for classification models. Why is it necessary to evaluate multiple metrics rather than relying on just one?
12.  Explain Cost-Sensitive Learning (CSL). In which scenarios should CSL be applied?

## Chapter Exercises

### Exercise 1: Model Fit Metrics for an Association Model

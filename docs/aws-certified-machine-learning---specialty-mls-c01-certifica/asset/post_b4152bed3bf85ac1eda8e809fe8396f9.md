
The second time, aim for at least **60%**. Look at the answers you got wrong and read the relevant sections in the chapter again to fix any remaining learning gaps.

## ATTEMPT 3

The third time, aim for at least **75%**. Once you score 75% or more, you start working on your timing.

### TIP

You may take more than **three** attempts to reach 75%. That’s okay. Just review the relevant sections in the chapter till you get there.

## Working On Timing

Target: Your aim is to keep the score the same while trying to answer these questions as quickly as possible. Here’s an example of how your next attempts should look like:

| Attempt | Score | Time Taken |
|---|---|---|
| Attempt 5 | 77% | 21 mins 30 seconds |
| Attempt 6 | 78% | 18 mins 34 seconds |
| Attempt 7 | 76% | 14 mins 44 seconds |

Table 6.11 – Sample timing practice drills on the online platform

### NOTE

The time limits shown in the above table are just examples. Set your own time limits with each attempt based on the time limit of the quiz on the website.

With each new attempt, your score should stay above **75%** while your “time taken” to complete should “decrease”.
Repeat as many attempts as you want till you feel confident dealing with the time pressure.

## Evaluating and Optimizing Models

It is now time to learn how to evaluate and optimize machine learning models. During the process of modeling, or even after model completion, you might want to understand how your model is performing. Each type of model has its own set of metrics that can be used to evaluate performance, and that is what you are going to study in this chapter.

Apart from model evaluation, as a data scientist, you might also need to improve your model’s performance by tuning the hyperparameters of your algorithm. You will take a look at some nuances of this modeling task.

In this chapter, the following topics will be covered:

- Introducing model evaluation
- Evaluating classification models
- Evaluating regression models
- Model optimization

Alright, time to rock it!

## Introducing model evaluation

There are several different scenarios in which you might want to evaluate model performance. Some of them are as follows:

- You are creating a model and testing different approaches and/or algorithms. Therefore, you need to compare these models to select the best one.
- You have just completed your model and you need to document your work, which includes specifying the model’s performance metrics that you got from the modeling phase.
- Your model is running in a production environment, and you need to track its performance. If you encounter model drift, then you might want to retrain the model.

### IMPORTANT NOTE

The term model drift is used to refer to the problem of model deterioration. When you are building a machine learning model, you must use data to train the algorithm. This set of data is known as training data, and it reflects the business rules at a particular point in time. If these business rules change over time, your model will probably fail to adapt to those changes. This is because it was trained on top of another dataset, which was reflecting another business scenario. To solve this problem, you must retrain the model so that it can consider the rules of the new business scenario.

Model evaluations are commonly inserted in the context of testing. You have learned about holdout validation and cross-validation before. However, both testing approaches share the same requirement: they need a metric in order to evaluate performance.

These metrics are specific to the problem domain. For example, there are specific metrics for regression models, classification models, clustering, natural language processing, and more. Therefore, during the design of your testing approach, you have to consider what type of model you are building in order to define the evaluation metrics.

In the following sections, you will take a look at the most important metrics and concepts that you should know to evaluate your models.

## Evaluating classification models

Classification models are one of the most traditional classes of problems that you might face, either during the exam or during your journey as a data scientist. A very important artifact that you might want to generate during the classification model evaluation is known as a confusion matrix.

A confusion matrix compares your model predictions against the real values of each class under evaluation. Figure 7.1 shows what a confusion matrix looks like in a binary classification problem:

![](img/87c29232224b00f5a8bba6a66a391700_187_0.png)

Figure 7.1 – A confusion matrix

There are the following components in a confusion matrix:

- TP: This is the number of true positive cases. Here, you have to count the number of cases that have been predicted as true and are, indeed, true. For example, in a fraud detection system, this would be the number of fraudulent transactions that were correctly predicted as fraud.
- TN: This is the number of true negative cases. Here, you have to count the number of cases that have been predicted as false and are, indeed, false. For example, in a fraud detection system, this would be the number of non-fraudulent transactions that were correctly predicted as not fraud.
- FN: This is the number of false negative cases. Here, you have to count the number of cases that have been predicted as false but are, instead, true. For example, in a fraud detection system, this would be the number of fraudulent transactions that were wrongly predicted as not fraud.
- FP: This is the number of false positive cases. Here, you have to count the number of cases that have been predicted as true but are, instead, false. For example, in a fraud detection system, this would be the number of non-fraudulent transactions that were wrongly predicted as fraud.

In a perfect scenario, your confusion matrix will have only true positive and true negative cases, which means that your model has an accuracy of 100%. In practical terms, if that type of scenario occurs, you should be sceptical instead of happy, since it is expected that your model will contain some level of errors. If your model does not contain errors, you are likely to be suffering from overfitting issues, so be careful.

Once false negatives and false positives are expected, the best you can do is prioritize one of them. For example, you can reduce the number of false negatives by increasing the number of false positives and vice versa. This is known as the precision versus recall trade-off. Let’s take a look at these metrics next.

### Extracting metrics from a confusion matrix

The simplest metric that can be extracted from a confusion matrix is known as **accuracy**. Accuracy is given by the following equation, as shown in *Figure 7.2*:

```
Accuracy = \frac{TrueNegatives + TruePositive}{TruePositive + FalsePositive + TrueNegative + FalseNegative}
```

Figure 7.2 – Formula for accuracy

For the sake of demonstration, *Figure 7.3* shows a confusion matrix with data.

![](img/87c29232224b00f5a8bba6a66a391700_188_0.png)

Figure 7.3 – A confusion matrix filled with some examples

According to *Figure 7.3*, the accuracy would be (100 + 90) / 210, which is equal to 0.90. There is a common issue that occurs when utilizing an accuracy metric, which is related to the balance of each class. Problems with highly imbalanced classes, such as 99% positive cases and 1% negative cases, will impact the accuracy score and make it useless.

For example, if your training data has 99% positive cases (the majority class), your model is likely to correctly classify most of the positive cases but work badly in the classification of negative cases (the minority class). The accuracy will be very high (due to the correctness of the classification of the positive cases), regardless of the bad results in the minority class classification.

The point is that on highly imbalanced problems, you usually have more interest in correctly classifying the minority class, not the majority class. That is the case in most fraud detection systems, for example, where the minority class corresponds to fraudulent cases. For imbalanced problems, you should look for other types of metrics, which you will learn about next.

Another important metric that you can extract from a confusion matrix is known as recall, which is given by the following equation, as shown in *Figure 7.4*:

Recall = True Positive / (True Positive + False Negative)

Figure 7.4 – Formula for recall

In other words, recall is the number of true positives over the total number of positive cases. Recall is also known as sensitivity.

With the values in *Figure 7.3*, recall is given by 100 / 112, which is equal to 0.89. Precision, on the other hand, is given by the following formula, as shown in *Figure 7.5*:

Precision = True Positive / (True Positive + False Positive)

Figure 7.5 – Formula for precision

In other words, precision is the number of true positives over the total number of predicted positive cases. Precision is also known as positive predictive power.

With the values in *Figure 7.3*, precision is given by 100 / 108, which is equal to 0.93. In general, you can increase precision at the cost of decreasing recall and vice versa. There is another model evaluation artifact in which you can play around with this precision versus recall trade-off. It is known as a precision-recall curve.

Precision-recall curves summarize the precision versus recall trade-off by using different probability thresholds. For example, the default threshold is 0.5, where any prediction above 0.5 will be

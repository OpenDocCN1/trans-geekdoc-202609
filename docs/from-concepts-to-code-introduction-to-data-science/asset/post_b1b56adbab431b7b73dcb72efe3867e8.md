
## An Overview of Machine Learning

> **Tip**: In a binary classification problem, it is generally important to accurately predict both the positive and negative labels. We can consider the case where one of the labels outnumbers the other, and without loss of generality we will take the positive labels to be rare. In this case, the data will be imbalanced and most observations will have negative labels. A classifier can have high accuracy by predicting all observations to have negative labels. Such behavior will not identify any of the positive labels, which means it will not be a useful classifier. This is why the F1 score can be a more useful metric than accuracy for binary classification.

## 12.10 Chapter Summary

We began this chapter with a simple tool for making a decision: a pros and cons list. We learned that to make a decision, we needed to surface all of the important predictors and determine their weighting. It is not an easy task to determine the optimal weighting, and this is one place where machine learning can help.

Next, we reviewed the branches of machine learning, starting with supervised learning. This approach pairs predictors with labels, so that a function can be learned for taking new predictor values as input and predicting the target. It is not always easy or even possible to collect labeled data, and this is one motivation for other approaches.

Unsupervised learning is used to understand the structure of data that is not labeled. Given a set of observations containing predictor values, we can try to identify underlying groupings of the data points. We can also predict the group membership of a new data point. For the case where we have a small fraction of labeled data and a larger fraction of unlabeled data, semi-supervised learning can be a useful approach. One recipe is to train on the labeled data and predict the labels of the unlabeled data. Reinforcement learning takes a different approach that follows human learning. An agent takes an action and receives a reward and new state from the environment. Working to maximize long-term reward, the agent learns the value of taking action from each state.

Next, we focussed on supervised learning and one of its biggest risks: failure to generate new data. Overfitting is a major culprit, and we discussed mitigating practices as evaluating model performance on held-out data.

For measuring prediction error, we defined some common loss functions. To measure the error across the training set, we defined risk as the expected loss; optionally we average the loss over the data points in the training set.

## Exercises

The optimal parameter values will minimize risk, and optimization techniques can be used to find these values.

We discussed hyperparameter tuning and k-fold validation. Models often include hyperparameters which are not known in advance and must be fine-tuned. This can be an expensive step, particularly when the search space is large and grid search is used. K-fold validation provides a thorough method for evaluating model performance, as each fold of the training data is held out for validation. The technique can be combined with grid search for hyperparameter tuning, and this is a best practice in machine learning.

Metrics are used to report on model performance. We discussed important metrics for regression such as RMSE and F-squared, and the binary classification problem, as recall and precision. We will see these metrics as we work with regression and classification models.

This chapter was very dense with concepts. In the next chapter, we will look at linear regression modeling in detail. Many of the concepts we just studied will be reinforced through code and examples.

## 11.11 Exercises

Exercises with solutions are marked with ($). Solutions can be found in the book_materials folder of the course repo at this location:

```
https://github.com/PredictionNN/intro_data_science_course/
```

- 1. Discuss a pros and cons list that you have made, or a list that you could make. What was the decision you were trying to make? What were the pros, what were the cons, and how did you ultimately combine them to produce an answer?
- 2. Discuss the major difference between supervised learning and unsupervised learning. What is one reason why unsupervised learning might be used in favor of supervised learning?
- 3. Given a dataset, how do we categorize a supervised learning problem as a regression problem or a classification?
- 4. For each problem, indicate whether it is a regression problem (R), classification problem (C), or clustering problem (S).
  - a) Summer campers are signing up for club activities. The activity each camper will select will depend on interests and who is teaching the activities. You are asked to predict the probability that a camper signs up for each activity.
  - b) A teacher wishes to place students into three reading-ability groups based on a reading comprehension exam.
  - c) An engineer needs to predict the engine horsepower of a prototype car based on the size of the engine and the number of cylinders.
- +5. Define a function that takes 1) the positive class predicted probability and 2) the label as inputs and returns cross-entropy loss. Use e for the logarithm. Next, call the function, 0.5 as the positive class predicted probability and 1 as the label. Show your code and the result.
- +6. A data scientist has a dataset with 10,000 observations. Only 500 observations are labeled. Outline a method using semi-supervised learning to label the remaining observations.
- +7. Explain exploration and exploitation. What is the downside to an agent that only exploits and never explores?
- +8. Explain overfitting. Why is overfitting a major concern for data scientists and users of data science?
- +9. What is one way that data scientists guard against overfitting?
- +10. Explain the function of each of these datasets:
  - a) Training set
  - b) Validation set
  - c) Test set
- +11. True or False: It is best practice to train a model on all of the available data.
- +12. True or False: You can expect model performance to improve over time.
- +13. True or False: Consider a supervised learning model that has been trained on a dataset. If new patterns emerge in future data, the model will not be able to use them effectively.
- +14. What is the purpose of a loss function in machine learning?
- +15. A data scientist has developed a model to predict personal bankruptcy. She trained the model on credit scores between 500 and 820, with a mean of 700. Over the next year, the credit scores were between 450 and 750, with a mean of 650. Should the model be retrained? Explain your answer.
- +16. Consider a loss function that computes the difference between the target $y$ and the prediction $\hat{y}$. Would this be a useful loss function? Explain your reasoning.
- +17. What are the strengths and weakness of the mean squared error compared to mean absolute error?

## Exercises

- +18. You wish to run hyperparameter tuning on a hyperparameter which is real-valued. You are considering two approaches, where the first randomly selects values for evaluation, and the second uses grid search. What are the strengths and weaknesses of each approach?
- +19. What is the cost and benefit of increasing the number of folds in k-fold cross validation?
- +20. When measuring and reporting model performance, why isn't cross-entropy typically used?
- +21. For the binary classification problem, is precision sufficient in measuring model performance? Explain your reasoning.
- +22. A certain diagnostic test produces 25 true positives for each false positive. What is the precision of this test?
- +23. True or False: A recall of 80% is considered excellent for any machine learning problem.
- +24. A binary classifier has correctly predicted a target of 1 for each instance where the actual target was 1.
- +25. For the confusion matrix below, calculate the accuracy, recall, precision, and F1 score.

| | predicted | P | N |
|---|---|---|---|
| actual | | | |
| P | | 102 | 7 |
| N | | 12 | 65 |

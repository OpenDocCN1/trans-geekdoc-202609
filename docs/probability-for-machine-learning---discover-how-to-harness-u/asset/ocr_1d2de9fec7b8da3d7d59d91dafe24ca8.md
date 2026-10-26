# Chapter 26

# Probability Scoring Metrics

Predicting probabilities instead of class labels for a classification problem can provide additional nuance and uncertainty for the predictions. The added nuance allows more sophisticated metrics to be used to interpret and evaluate the predicted probabilities. In general, methods for the evaluation of the accuracy of predicted probabilities are referred to as scoring rules or scoring functions. In this tutorial, you will discover three scoring methods that you can use to evaluate the predicted probabilities on your classification predictive modeling problem. After completing this tutorial, you will know:

+   - The log loss score that heavily penalizes predicted probabilities far away from their expected value.
+   - The Brier score that is gentler than log loss but still penalizes proportional to the distance from the expected value.
+   - The area under ROC curve that summarizes the likelihood of the model predicting a higher probability for true positive cases than true negative cases.

Let’s get started.

# 26.1 Tutorial Overview

This tutorial is divided into three parts; they are:

+   1. Log Loss Score
+   2. Brier Score
+   3. ROC AUC Score

# 26.2 Log Loss Score

Log loss, also called *logistic loss*, *logarithmic loss*, or *cross-entropy* can be used as a measure for evaluating predicted probabilities (introduced in Chapter 23). Each predicted probability is compared to the actual class output value (0 or 1) and a score is calculated that penalizes the
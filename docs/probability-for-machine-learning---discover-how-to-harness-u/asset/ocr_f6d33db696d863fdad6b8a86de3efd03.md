# Chapter 18

# How to Develop a Naive Bayes Classifier

Classification is a predictive modeling problem that involves assigning a label to a given input data sample. The problem of classification predictive modeling can be framed as calculating the conditional probability of a class label given a data sample. Bayes Theorem provides a principled way for calculating this conditional probability, although in practice requires an enormous number of samples (very large-sized dataset) and is computationally expensive. Instead, the calculation of Bayes Theorem can be simplified by making some assumptions, such as each input variable is independent of all other input variables. Although a dramatic and unrealistic assumption, this has the effect of making the calculations of the conditional probability tractable and results in an effective classification model referred to as Naive Bayes. In this tutorial, you will discover the Naive Bayes algorithm for classification predictive modeling. After completing this tutorial, you will know:

+   - How to frame classification predictive modeling as a conditional probability model.
+   - How to use Bayes Theorem to solve the conditional probability model of classification.
+   - How to implement simplified Bayes Theorem for classification, called the Naive Bayes algorithm.

Let’s get started.

# 18.1 Tutorial Overview

This tutorial is divided into five parts; they are:

+   1. Conditional Probability Model of Classification
+   2. Simplified or Naive Bayes
+   3. How to Calculate the Prior and Conditional Probabilities
+   4. Worked Example of Naive Bayes
+   5. 5 Tips When Using Naive Bayes
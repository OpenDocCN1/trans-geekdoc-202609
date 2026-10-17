# Chapter 18

# Stacked Generalization

Ensemble methods are an excellent way to improve predictive performance on your machine learning problems. Stacked Generalization or stacking is an ensemble technique that uses a new model to learn how to best combine the predictions from two or more models trained on your dataset. In this tutorial, you will discover how to implement stacking from scratch in Python. After completing this tutorial, you will know:

+   - How to learn to combine the predictions from multiple models on a dataset.
+   - How to apply stacked generalization to a real-world predictive modeling problem.

Let's get started.

# 18.1 Description

This section provides a brief overview of the Stacked Generalization algorithm and the Sonar dataset used in this tutorial.

# 18.1.1 Stacked Generalization Algorithm

Stacked Generalization is an ensemble algorithm where a new model is trained to combine the predictions from two or more models already trained or your dataset. The predictions from the existing models or submodels are combined using a new model, and as such stacking is often referred to as blending, as the predictions from submodels are blended together.

It is typical to use a simple linear method to combine the predictions for submodels. Examples include: simple averaging called voting, a weighted sum using linear regression. and logistic regression. Models that have their predictions combined must have skill on the problem, but do not need to be the best possible models. This means that you do not need to tune the submodels intently, as long as the model shows some advantage over a baseline prediction.

It is important that submodels produce different predictions, so-called uncorrelated predictions. Stacking works best when the predictions that are combined are all skillful, but skillful in different ways. This may be achieved by using algorithms that use very different internal representations (trees compared to instances) and/or models trained on different representations or projections of the training data.

In this tutorial, we will look at taking two very different and untuned submodels and combining their predictions with a simple logistic regression algorithm.
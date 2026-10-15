# Chapter 12

# Fix Overfitting with Regularization

Training a deep neural network that can generalize well to new data is a challenging problem. A model with too little capacity cannot learn the problem, whereas a model with too much capacity can learn it too well and overfit the training dataset. Both cases result in a model that does not generalize well. A modern approach to reducing generalization error is to use a larger model that may be required to use regularization during training that keeps the weights of the model small. These techniques not only reduce overfitting, but they can also lead to faster optimization of the model and better overall performance. In this tutorial, you will discover the problem of overfitting when training neural networks and how it can be addressed with regularization methods. After reading this tutorial, you will know:

+   - Underfitting can easily be addressed by increasing the capacity of the network, but overfitting requires the use of specialized techniques.
+   - Regularization methods like weight decay provide an easy way to control overfitting for large neural network models.
+   - A modern recommendation for regularization is to use early stopping with dropout and a weight constraint.

Let’s get started.

# 12.1 Problem of Model Generalization and Overfitting

The objective of a neural network is to have a final model that performs well both on the data that we used to train it (e.g. the training dataset) and the new data on which the model will be used to make predictions.

The central challenge in machine learning is that we must perform well on new, previously unseen inputs - not just those on which our model was trained. The ability to perform well on previously unobserved inputs is called generalization.

> — Page 110, Deep Learning, 2016.
# Chapter 11 : Part 3

# # Deep Learning
ANN: Evaluate performance using K-fold-CV
&
Hyper parameter tuning

K-fold CV or K-fold-Cross-Validation, keras-wrapper, Dropout Regularization

# ## 11.3.1 K-fold-CV in ANN

+   - K-fold CV in ANN: in the previous section we discussed K-fold-CV and applied to kernel-SVM to XGBoost. In this section we' apply K-fold-CV to ANN, it is our first Deep-learning Algorithm.

+   - In Chapter 8: ANN, we trained our aerial neural network twice and we noticed that the accuracies are different. We want to apply K-fold-CV to evaluate Model performance accurately.

+   - **Variance Tradeoff**: We're trying to train a model that will not only be accurate, but also should not have too much variance of accuracy, when we train it several times.

+   - Previously we trained our ANN and obtained two different accuracies, 85% and 84%. When one of these two we should take to **evaluate our performance**

+   - We split our data between a training-set and a test-set. It results the Variance Problem When we get the accuracy on the test set, if we run the model again and test it on another test set, we can get a very different accuracy.

So, judging our model performance only on one test set, is not the most relevant way, to evaluate the model performance.

That's why we train-set (or whole dataset) divide into equal k-groups and k-combination of (k-1)-train-group and 1-test-group, we k iterations. Finally we get a vector of accuracies for which we the mean-accuracy and standard-deviation. It gives us a better evaluation of the model performance

Most of time, K=10, we train our model on 9-folds and test it on the remaining fold. With 10-folds there are 10 different combinations of 9-folds-train and 1-test-fold.

+   - That means we can train and test the model on combinations of training and test sets. How ID different accuracies.

+   - That will give us a much better idea of the model performance, by taking average of the differences of the accuracies and also compute the standard deviation.

We categorize the performance into 4-categories:

+   i. good accuracy - small variance;
ii. large accuracy - high variance;
iii. small accuracy - low variance;
iv. low accuracy - high variance

# ## 11.3.2 Implement K-fold CV in ANN

We implement K-fold CV after the data pre-processing phase.

+   - Keras wrapper: We implemented our ANN model with Keras-TensorFlow. How the K-fold-CV belongs to Scikit-learn.

Keras wrapper combines Keras and Scikit together. Keras wrapper module belongs to Keras. It will wrap K-fold cross validation by Scikit-learn, in the Keras model

We will be able to include K-fold cross validation in our Keras classifier.

```
from keras.wrappers.scikit_learn import KClassifier
from sklearn.model_selection import cross_val_score
# combine Keras & Scikit-Learn
```

![](bbox=[0.675, 0.253, 0.865, 0.403])
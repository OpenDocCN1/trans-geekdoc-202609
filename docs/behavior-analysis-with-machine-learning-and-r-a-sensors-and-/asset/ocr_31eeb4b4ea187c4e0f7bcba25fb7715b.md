# CHAPTER 1. INTRODUCTION

model performs on new data. The performance can be measured using performance metrics such as the *accuracy* for classification problems. The accuracy is the percent of correctly classified instances.

> It is a good practice to estimate the performance on both, the train and test sets. Usually, the performance on the train set will be higher since the model was trained with that same data. It is also common to measure the performance computing the error instead of accuracy. For example, the percent of misclassified instances. These are called the *train error* and *test error* (also known as the *generalization error*), for both the train and test sets respectively. Estimating these two will allow you to ‘debug’ your models and understand if they are underfitting or overfitting (more on in the following sections).

**K-fold cross-validation.** Hold-out validation is a good way to evaluate your models when you have a lot of data. However, in many cases, your data will be limited. With hold-out validation, each instance is included in either the train or test set. K-fold cross-validation provides a way in which instances take part in both, the train and test set, making more efficient use of the data.

This method consists of randomly assigning each instance to one of $k$ folds (subsets) of approximately the same size. Then, $k$ iterations are performed. In each iteration, one of the folds is used to test the model while the remaining ones are used to train it. Each fold is used once as the test set and $k-1$ times it’s used as part of the train set. Typical values for $k$ are 3, 5, and 10. In the extreme case where $k$ is equal to the total number of instances in the dataset, it is called leave-one-out cross-validation (LOOCV). Figure 1.7 shows an example of cross-validation with $k=5$.

The generalization performance is then computed by taking the average accuracy/error from each iteration.

Hold-out validation is typically used when there is a lot of available data and models take significant time to be trained. On the other hand, k-fold cross-validation is used when data is limited. However, it is more computational intensive since it requires training $k$ models.

# Validation set.

Most predictive models require some hyperparameter tuning. For example, a k-NN model requires to tune $k$, the number of neighbors. For decision trees, one can specify the maximum allowed tree depth, among other hyperparameters. Neural networks require even more hyperparameter tuning to work properly. Also, one may try different preprocessing techniques
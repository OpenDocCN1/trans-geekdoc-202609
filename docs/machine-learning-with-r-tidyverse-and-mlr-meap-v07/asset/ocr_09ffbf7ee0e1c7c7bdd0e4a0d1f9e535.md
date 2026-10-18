Interpret the confusion matrices shown in code listing 5.9. .. Which model is better at identifying wines from vineyard 3? .. Does our LDA model misclassify more wines from vineyard 2 as from vineyard 1 or 3?



Extract the discriminant scores from our LDA model, and use only these as the predictors for a k-NN model (including tuning k). Experiment with your own cross-validation strategy. Look back at chapter 3 if you need a refresher on training a k-NN model!



+   Discriminant analysis is a supervised learning algorithm that projects the data onto a lower-dimensional representation to create discriminant functions
+   Discriminant functions are linear combinations of the original (continuous) variables that maximize the separation of class centroids, while minimizing the variance of each class along them
+   Discriminant analysis comes in many flavors, the most fundamental of which are LDA and QDA
+   LDA learns linear decision boundaries between classes and assumes each class is normally distributed and have equal covariances
+   QDA can learn curved decision boundaries between classes and assumes each class is normally distributed but does not assume equal covariances
+   The number of discriminant functions is the smaller of: the number of classes - 1, or the number of predictor variables
+   Class prediction uses Baye’s rule to estimate the posterior probability of a case belonging to each of the classes
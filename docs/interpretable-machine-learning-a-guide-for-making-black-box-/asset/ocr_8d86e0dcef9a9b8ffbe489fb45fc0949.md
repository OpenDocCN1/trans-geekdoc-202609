![](bbox=[0.116, 0.073, 0.822, 0.433])

FIGURE 5.28: PDP of feature X42, which is the most important feature according to the feature importance based on the training data. The plot shows how the SVM depends on this feature to make predictions

The plot clearly shows that the SVM has learned to rely on feature X42 for its predictions, but according to the feature importance based on the test data (1), it is not important. Based on the training data, the importance is 1.19, reflecting that the model has learned to use this feature. Feature importance based on the training data tells us which features are important for the model in the sense that it depends on them for making predictions.

As part of the case for using training data, I would like to introduce an argument against test data. In practice, you want to use all your data to train your model to get the best possible model in the end. This means no unused test data is left to compute the feature importance. You have the same problem when you want to estimate the generalization error of your model. If you would use (nested) cross-validation for the feature importance estimation, you would have the problem that the feature importance is not calculated on the final model with all the data, but on models with subsets of the data that might behave differently.

In the end, you need to decide whether you want to know how much the model relies on each feature for making predictions (-> training data) or how much the feature contributes to the performance of the model on unseen data (-> test data). To the best of my knowledge, there is no research addressing the question of training vs. test data. It will require more thorough examination than my "garbage-SVM" example. We need more research and more experience with these tools to gain a better understanding.

Next, we will look at some examples. I based the importance computation on the training data, because I had to choose one and using the training data needed a few lines less code.

# 5.5.3 Example and Interpretation

I show examples for classification and regression.

# Cervical cancer (classification)
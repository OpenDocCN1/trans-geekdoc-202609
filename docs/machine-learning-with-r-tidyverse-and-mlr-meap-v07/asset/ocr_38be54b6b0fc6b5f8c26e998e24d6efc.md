+   - k-NN is a simple supervised learning algorithm that classifies new data based on the class membership of its nearest k cases in the training set
+   - To create a machine learning model in mlr, we create a task and a learner, and then train the model using them
+   - MMCE is the mean misclassification error, which is the proportion of misclassified cases in a classification problem. It is the opposite of accuracy
+   - The bias-variance trade-off is the balance between two types of error in predictive accuracy. Models with high bias are underfit, and models with high variance are overfit
+   - Model performance should never be evaluated on the data used to train it; cross-validation should be used instead
+   - Cross-validation is a set of techniques for evaluating model performance by splitting the data into training and test sets
+   - Three common types of cross-validation are hold-out, where a single split is used, k-fold, where the data is split into k-chunks and the validation performed on each chunk, and leave-one-out, where the test set is a single case
+   - Hyperparameters are "options" that control how machine learning algorithms learn, which cannot be learned by the algorithm itself. Hyperparameter tuning is the best way to find optimal hyperparameters
+   - If we perform a data-dependent preprocessing step, such as hyperparameter tuning, it’s important to incorporate this in our cross-validation strategy, using nested cross-validation
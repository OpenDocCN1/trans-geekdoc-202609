The bias-variance trade-off therefore describes the balance between overfitting (training a model that fits the noise of the training set) and underfitting (training a model that poorly fits the training set). Somewhere between a model that overfits and a model that underfits, is an optimally-fitting model whose predictions generalize well to unseen data. The way to tell if we are underfitting overfitting is using cross-validation. Though even just passing the training set back through the model will tell you if you’re underfitting, because the model will perform poorly.

# ## 20.1.3 Using model validation to identify over/underfitting

To evaluate how well a model will make predictions on new data, we need to pass new, unseen data through the model and see how closely its predictions match the ground-truth. One way of doing this would be to train the model on the data at hand, then as new data is generated, pass this through the model to evaluate its predictions. This process could make the model-building process take years and so a more realistic approach is to split the data into training and test sets. In this way, the model is trained using the training set and is given the test set to make predictions on. This process is called cross-validation, and we learned about it in chapter 3.

There are multiple ways of splitting the dataset into training and test sets. Hold-out cross-validation is the simplest, where a proportion of cases in the dataset are "held-out" as the test set, and the model is trained on the remaining cases. As the split is usually random, the outcome from hold-out cross-validation depends heavily on the proportion of cases held-out in the test set, and on the cases that made it into the test set. As such, hold-out cross-validation can give quite variable results when run multiple times, though it is the least computationally expensive method. I’ve reproduced figure 3.12 here in figure 20.3, that shows a schematic illustrating hold-out cross-validation.

![](bbox=[0.134, 0.628, 0.587, 0.707])

+   1. The data are randomly split into a training and test set
+   2. A model is trained using only the training set
+   3. Predictions are made on the test set
+   4. The predictions are compared to the true values

**Figure 20.3 Hold-out cross-validation (CV).** The data is randomly split into a training set and test set. The training set is used to train the model, which is then used to make predictions on the test set. The similarity of the predictions to the true values of the test set is used to evaluate model performance.

k-fold cross-validation randomly partitions the cases into k, near-equally-sized folds. For each fold, the cases inside the fold are used as the test set, while the remaining data are used as the training set. The mean performance metric of each fold is then returned. The advantage of k-fold
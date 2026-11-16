# K Cross-Validation

This involves breaking down the validation set into K folds and training and testing the model on each fold. Then you will compare the performance average across all folds with other models.

# Leave-One-Out Cross Validation

Leave-one-out cross validation involves splitting the data into n data folds where n is the number of data points. You would then train the data in n – 1 folds and evaluate the model against the fold not used in training.

> **TIP** _Using the leave-one-out cross-validation technique helps you test the data against all the data points, which is very accurate._

# Validation Metrics

As shown in Figure 17.9, validation metrics are used during the different phases of a model development lifecycle.

# During Model Building

For example, during the model build phase, validation metrics can be used to choose the suitable model for classification-type problems based on a validation metric such as area under the receiver operating characteristic curve (AUC-ROC). In the case of regression type problems, use metrics such as mean absolute error or R-squared.

> **TIP** _Always select metrics aligned with your model's objectives._
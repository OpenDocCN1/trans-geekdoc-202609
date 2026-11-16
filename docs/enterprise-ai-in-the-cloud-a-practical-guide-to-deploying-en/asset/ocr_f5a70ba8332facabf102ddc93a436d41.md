The goal of the model validation process is to compare the predictions of the model with the actual outputs of the new dataset. You will use techniques such as holdout validation and cross-validation. This evaluation aims to test the model's generalization ability, identify any issues with the model, and choose the best model among the candidates. Its focus is to avoid overfitting the training data. Model validation happens during the training phase, while model evaluation happens after the model is deployed in production.

There are several cross-validation techniques—the two most popular ones are K cross validation and leave-one-out cross validation (see Figure 17.8).

Cross-validation techniques are more expensive and time-consuming but are very accurate. If you're short on time, you should go for holdout validation, but when accuracy is critical, you will use cross-validation techniques.

# Holdout Validation

Holdout validation involves breaking the dataset into a training dataset and a test dataset. You will use the training dataset to train the model and then use the model to test the dataset using the test dataset. By comparing the results with the actual dataset, you can evaluate how accurate the model is.

![](bbox=[0.12, 0.58, 0.88, 0.85])

# FIGURE 17.8: Validating machine learning models
+   * Option to provide prior probability for y==1(logistic regression) in the case of sampled data if its mean of response does not reflect the reality (prior).
+   * Specify the variables to be considered for interactions (interactions).

# # How it works...

The performance of the model can be assessed using many metrics such as accuracy, **Area under curve** (**AUC**), misclassification error (%), misclassification error count, F1-score, precision, recall, specificity, and so on. However, in this chapter, the assessment of model performance is based on AUC.

The following is the training and cross validation accuracy of the trained model:

```
```
# Training accuracy (AUC)
> occupancy_train.glm@model$training_metrics@metrics$AUC
[1] 0.994583

# Cross validation accuracy (AUC)
> occupancy_train.glm@model$cross_validation_metrics@metrics$AUC
[1] 0.9945057
```
```

Now, let's assess the performance of the model on test data. The following code helps in predicting the outcome of the test data:

```
```
# Predict on test data
yhat <- h2o.predict(occupancy_train.glm, occupancy_test.hex)
```
```

Then, evaluate the AUC value based on the actual test outcome as follows:

```
```
# Test accuracy (AUC)
> yhat$pmax <- pmax(yhat$p0, yhat$p1, na.rm = TRUE)
> roc_obj <- pROC::roc(c(as.matrix(occupancy_test.hex$Occupancy)),
>                     c(as.matrix(yhat$pmax)))

> auc(roc_obj)
Area under the curve: 0.9915
```
```
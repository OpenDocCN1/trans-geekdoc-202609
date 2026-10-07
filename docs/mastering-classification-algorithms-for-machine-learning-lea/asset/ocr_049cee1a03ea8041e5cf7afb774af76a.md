# Checking the model’s training accuracy

We have built our model. First, we need to find out how well the model is working on the Training data. Remember that the model used the Training data to create its rules. Before we can generate the metrics for the model, we need to make predictions from the model. Let us first make the predictions on the Training set.

yTrainPred = model.predict(dfTrain.values)

Let us use the Confusion Matrix. We can calculate the accuracy, precision, recall, and F1 score from the confusion matrix. Let us calculate the accuracy.

```
print("Training Accuracy = %5.5f" % (metrics.accuracy_score(y_train
```

Training Accuracy = 0.9752

So, our model is predicting at an accuracy of 97.527%. This indicates that the machine is doing reasonably well.

# Validating the model

Training Data is what the machine has used to create the model. However, the machine has not seen the Test Data yet. So, we use the Test Data to validate the model. If the model performs well on the Test Data, then we can be confident that the model is good.

To validate the model, we need to feed the test dataset to the model and ask to make predictions. However, before presenting the test data to the model, we need to preprocess the test data the same way we preprocessed the training data:

```
URLPresentTest = pd.Series([identifyAndRemoveURLs(text)[1] for text in X_test])
nX_test = pd.Series(identifyAndRemoveURLs(text)[0] for text in X_test)
X_test = X_test.str.lower()
X_test = X_test.apply(cleanData)
X_test.head())
\u20000 funny fact nobody telocanoes erupt tsun...
1 sent scores sophas secondary application schoo...
2 know someone how fannies find pobox lhb p
3 promise getting soon youll text morning let kn...
4 congratulations ur awarded either cd gift vouc...
```
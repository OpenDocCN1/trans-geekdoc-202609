```
head(folds)
#> [1] 10 6 5 9 5 6
```

The store each instance belongs to. For example, the first instance belongs to fold 1, the second instance belongs to fold 6, and so on. We can now generate our test and train sets. We iterate k = 10. For each iteration i, the test set is built using the instances that belong to fold i and the train set will be composed of the remaining instances (those that do not belong to fold i). Next, the `rpart()` function is used to train the decision tree with the train set. By default, `rpart()` performs 10-fold cross-validation internally. To avoid this, we set the parameter `xval = 0`. Then, we can use the trained model to obtain the predictions on the test set with the generic `predict()` function. The ground truth classes and the predictions are stored so the performance metrics can be computed.

```
# Variable to store ground truth classes.
groundTruth <- NULL
```

```
# Variable to store the classifier's predictions.
predictions <- NULL
```

```
for(i in 1:k){

trainSet <- df[which(folds != i), ]
testSet <- df[which(folds == i), ]

# Train the decision tree
treeClassifier <- rpart(class ~, 
trainSet, xval=0)

# Get predictions on the test set.
foldPredictions <- predict(treeClassifier, 
testSet, type = "class")

predictions <- c(predictions,
as.character(foldPredictions))

groundTruth <- c(groundTruth,
```
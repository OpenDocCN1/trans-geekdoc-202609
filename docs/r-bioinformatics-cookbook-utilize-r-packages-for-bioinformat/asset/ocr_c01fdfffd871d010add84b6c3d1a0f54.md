# Novel feature detection in proteins

```
classes <- readr::read_csv(class_file, col_names = TRUE)
classes <- classes$class
```

Divide the data into training and test sets:

```
num_seqs <- length(seqs)
training_proportion <- 0.75
training_set_indices <- sample(1:num_seqs, training_proportion =
num_seqs)
test_set_indices <- c(1:num_seqs)[-training_set_indices]
```

Build the model with the training set:

```
kernel <- gappyPairKernel(k=1, m=3)

model <- ksvm(x=seqs[training_set_indices],
      y=classes[training_set_indices],
      kernel=kernel,
      pkg="e1071",
      svm="C-svc", cost=15)
```

Use the model to predict the classes of the test set:

```
predictions <- predict(model, seqs[test_set_indices])
evaluatePrediction(predictions, classes[test_set_indices],
      allLabels=c(1,-1 ))
```

Examine the prediction profile of a sequence:

```
seq_to_test <- seqs[[1]][1:10]
prediction_profile <- getPredictionProfile(seq_to_test, kernel,
      featureWeights(model),modelOffset(model ))
```

Plot the prediction profile:

```
plot(prediction_profile)
```

This code should give us a nice prediction profile.

# How it works...

*Step 1* is straightforward – we load in sequences a simple vector of classes for that data, we extract from the DataFrame
to. As we just use the $ operator. Then, we get on to the main workflow. In *step 2*, we decide how much of thendata we use for training and how much should be tested. We set 75% of the training data when we
create the `training_proportion` variable. This is used in conjunction with `num_seqs` the
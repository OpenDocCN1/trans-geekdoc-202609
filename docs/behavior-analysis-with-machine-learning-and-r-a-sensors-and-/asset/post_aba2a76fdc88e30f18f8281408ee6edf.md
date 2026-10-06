
# CHAPTER 1. INTRODUCTION

```r
# Variable to store the predictions of
# each instance in newdata.
predictions <- NULL

# Iterate instances in newdata
for(i in 1:nrow(newdata)){
  instance <- newdata[i,]

  # Predict the name of the class which
  # centrality measure is closest.
  pred <- names(which.min(abs(instance$speed - params)))

  predictions <- c(predictions, pred)

  return(predictions)
}
```

This function iterates through each row and computes the distance to each centrality measure and returns the name of the class that was the closest one. The distance computation is done with the following line of code:

```r
pred <- names(which.min(abs(instance$speed - params)))
```

First, it computes the absolute difference between the speed and each centrality measure stored in params and it returns the name of the one that was minimum. Now that we have defined the training and prediction procedures, we are ready to test our classifier!

In section 1.5, two evaluation methods were presented. **Hold-out and k-fold cross-validation.** These methods allow you to estimate how your model will perform on new data. Let's first start with **hold-out validation.**

First, we need to split the data into two independent sets. We will use 70% of the data to train our classifier and the remaining 30% to test it. The following code splits `dataset` into a `trainset` and `testset`.

```r
# Percent to be used as training data.
pctTrain <- 0.7
```

```r
# Set seed for reproducibility.
set.seed(123)
```

```r
idxs <- sample(dataset,
      size = nrow(dataset) * pctTrain,
      replace = FALSE)
```

```r
trainset <- dataset[idxs,]

testset <- dataset[-idxs]
```

The sample() function was used to select integer numbers at random from 1 to n, where n is the total number of data points in dataset. These randomly selected data points are the ones that will go to the train set. Thus, with the size argument we tell the function to return 70 numbers which correspond to 70% of the total since dataset has 100 instances.

> The last argument replace is set to FALSE because we do not want repeated numbers. This ensures that any instance only belongs to either the train or the test set. We don't want an instance to be copied into both sets.

Now it's time to test our functions. We can train our model using the trainset by calling our previously defined function simple.model.train().

```r
# Train the model using the trainset.
params <- simple.model.train(trainset, mean)
```

```r
# Print the learned parameters.
#> tiger leopard
#> 48.88246 54.58369
```

After training the model, we print the learned parameters. In this case, the mean for tiger is 48.88 and for leopard, it is 54.58. With these parameters, we can start making predictions on our test set! We pass the test set and the newly-learned parameters to our function simple.classifier.predict().

```r
# Predict classes on the test set.
test.predictions <- simple.classifier.predict(testset, params)
```

```r
# Display first predictions.
head(test.predictions)
#> [1] "tiger" "tiger" "leopard" "tiger" "tiger" "leopard"
```

Our predict function returns predictions for each instance in the test set. We can use the head() function to print the first predictions. The first two instances were classified as tigers, the third one as leopard, and so on.

But how are those predictions? Since we know the true classes are (also known as ground truth) in our test set, we can compute the performance. In this case, we will compute the accuracy, which is the percentage of correct classifications. Note that we did not use the class information when making predictions, we only used the speed. We pretended that didn't have the true class. We will use the true class to evaluate the model's performance.

```r
# Compute test accuracy.
sum(test.predictions == as.character(testset$class)) /
length(testset)
#> [1] 0.833333333
```

We can compute the accuracy by counting how many predictions were equal to the true classes and divide them by the total number of points in the test set. In this case, test accuracy was 83.0%. Congratulations! you have trained and evaluated your first classifier. It is also a good idea to compute the performance on the same train set that was used to train the model.

```r
# Compute train accuracy.
train.predictions <- simple.classifier.predict(trainset, params)
sum(train.predictions == as.character(trainset$class)) /
length(trainset)
# [1] 0.8571429
```

The train accuracy was 85.7%. As expected, this was higher than the test accuracy. Typically, when you report the performance on the test set, you can use the performance on the train set to look for overfitting/underfitting which will be covered in the following sections.

## 1.6 K-fold Cross-Validation

Now let's see how k-fold cross-validation can be implemented to test our classifier. I will choose k=5. This means that 5 independent sets are to be generated and 5 iterations will run.

```r
# Number of folds
k <- 5

set.seed(123)

# Generate random folds.
folds <- sample(k, size = nrow(dataset), replace = TRUE)

# Print how many instances ended up in each fold.
table(folds)
# 1 2 3 4 5
# 21 20 23 19
```

Again we use the sample() function. This time we want to select random integers between 1 and k. The total number of integers will be equal to the total of instances in the entire dataset. Note that we set replace = TRUE since k < n we need to pick repeated numbers. Each number will represent the fold to which instance belongs. Before, we need to make sure that each instance belongs only to one of sets. We can use the table() function to print how many instances ended up in each fold. Here we see that the folds contain between 17 and 23 instances.

K-fold cross-validation consists of iterating k times. In each iteration, we select one of the folds as the test set and the remaining folds are used as the train set. We can then train a model with the train set and evaluate it with the test set. In the end, we report the average accuracy across folds.

```r
# Variable to store accuracies on each fold.
test.accuracies <- NULL
train.accuracies <- NULL

for(i in 1:k){
  testset <- dataset[which(folds == i),]
  trainset <- dataset[which(folds != i),]

  params <- simple.model.train(trainset, mean)
  test.predictions <- simple.classifier.predict(testset, params)
  train.predictions <- simple.classifier.predict(trainset, params)

  # Accuracy on test set.
  acc <- sum(test.predictions == as.character(testset$class)) /
    nrow(testset)

  test.accuracies <- c(test.accuracies, acc)

  # Accuracy on train set.
  acc <- sum(train.predictions == as.character(trainset$class)) /
    nrow(trainset)

  train.accuracies <- c(train.accuracies, acc)
}

# Print mean accuracy across folds on the test set.
mean(test.accuracies)
# [1] 0.829823

# Print mean accuracy across folds on the train set.
mean(train.accuracies)
# [1] 0.8422414
```

The test mean accuracy across the 5 folds ≈ 83% which is very similar to the accuracy estimated by hold-out validation.

Note that in section 1.5 a validation set was also mentioned. This one is useful when you want to fine-tune a model and/or try different preprocessing methods on your data. In case using hold-out validation, you may split your data into three sets: train/validation/test sets. So, you train your model using the train set and estimate its performance using the validation set. Then you can fine-tune your model. For example, instead of the mean as centrality measure, you can try to use the median and measure the performance again with the validation set. When you are pleased with your settings, you estimate the final performance of the model with the test set

In case of k-fold cross-validation, you can set aside the test set at the beginning. Then you use the remaining data to perform cross-validation and fine-tune your model. Within each iteration, you test the performance with the validation data. Once you are sure you are not going to do any parameter tuning, you can train a model with the train and validation sets and test the generalization performance using the test set.

One of the benefits of machine learning is that it allows us to find patterns based on data, freeing us from having to program hard-coded rules. This means more scalable and flexible code. If for some reason, instead of 2 classes we need to add another class, for example, a jaguar, the only thing we need to do is update our database and retain our model. We don't need to modify the internals of the algorithms. They update themselves based on the data.

We can try this by adding a third class to the dataset. The simple_model.R script shows how to add a new class, ‘jaguar’, to the dataset. It then trains the model as usual and performs predictions.

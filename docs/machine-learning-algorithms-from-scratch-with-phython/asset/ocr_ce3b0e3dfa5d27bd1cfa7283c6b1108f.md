```
sum_error = 0
for row in train:
    yhat = predict(row, coef)
    error = yhat - row[-1]
    sum_error += error**2
    coef[0] = coef[0] - l_rate * error
    for i in range(len(row)-1):
        coef[i + 1] = coef[i + 1] - l_rate * error * row[i]
print('>epoch=%d, lrate=%.3f, error=%.3f' % (epoch, l_rate, sum_error))
return coef

# Calculate coefficients
dataset = [[1, 1], [2, 3], [4, 3], [3, 2], [5, 5]]
l_rate = 0.001
n_epoch = 50
coef = coefficients_sgd(dataset, l_rate, n_epoch)
print(coef)
```

Listing 8.6: Example of Estimating Coefficients on the Contrived Dataset.

We use a small learning rate of 0.001 and train the model for 50 epochs, or 50 exposures of the coefficients to the entire training dataset. Running the example prints a message each epoch with the sum squared error for that epoch and the final set of coefficients.

```
...
>epoch=45, lrate=0.001, error=2.650
>epoch=46, lrate=0.001, error=2.627
>epoch=47, lrate=0.001, error=2.607
>epoch=48, lrate=0.001, error=2.589
>epoch=49, lrate=0.001, error=2.573
[0.229982344937311363, 0.8017220304137576]
```

Listing 8.7: Example Output of Estimating Coefficients on the Contrived Dataset.

You can see how error continues to drop even in the final epoch. We could probably train for a lot longer (more epochs) or increase the amount we update the coefficients each epoch (higher learning rate). Experiment and see what you come up with. Now, let's apply this algorithm on a real dataset.

# 8.2.3 Wine Quality Case Study

In this section, we will train a linear regression model using stochastic gradient descent on the Wine Quality dataset. The example assumes that a CSV copy of the dataset is in the current working directory with the filename winequality-white.csv.

The dataset is first loaded, the string values converted to numeric and each column is normalized to values in the range of 0 to 1. This is achieved with helper functions load_csv() and str_column_to_float() to load and prepare the dataset and dataset_minmax() and normalize_dataset() to normalize it.

We will use k-fold cross-validation to estimate the performance of the learned model on unseen data. This means that we will construct and evaluate k models and estimate the performance as the mean model error. Root mean squared error will be used to evaluate each model. These behaviors are provided in the cross_validation_split(), rmse_metric() and evaluate_algorithm() helper functions.
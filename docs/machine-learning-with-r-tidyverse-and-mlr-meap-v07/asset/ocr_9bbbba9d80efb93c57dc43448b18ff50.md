# EXERCISE 3.3

Define two new resampling descriptions, one that performs 3-fold cross-validation repeated 5 times, and one that performs 3-fold cross-validation repeated 500 times (don't overwrite your existing description). Use the resample() function to cross validate the k-NN algorithm using both of these resampling descriptions. Repeat the resampling 5 times for each method and see which one gives more stable results.



Now, let's build the confusion matrix based on the repeated k-fold cross-validation:

```
calculateConfusionMatrix(kFoldCV$pred, relative = TRUE)
```

Relative confusion matrix (normalized by row/column):

| Chemical | Normal | Overt | -err.- |
|----------|--------|-------|--------|
| Chemical | 0.81/0.78 | 0.10/0.05 | 0.09/0.10 | 0.19 |
| Normal | 0.04/0.07 | 0.96/0.95 | 0.00/0.00 | 0.04 |
| Overt | 0.16/0.14 | 0.00/0.00 | 0.84/0.90 | 0.16 |
| -err.- | 0.22 | 0.05 | 0.10 | 0.10 |

Absolute confusion matrix:

| Chemical | Normal | Overt | -err.- |
|----------|--------|-------|--------|
| Chemical | 1463 | 179 | 158 | 337 |
| Normal | 136 | 3664 | 0 | 136 |
| Overt | 269 | 0 | 1381 | 269 |
| -err.- | 405 | 179 | 158 | 742 |

> Notice that the number of cases is much larger? This is because we repeated the procedure 50 times!



Leave-one-out cross-validation can be thought of as the extreme of k-fold cross-validation: instead of breaking the data up into folds, we simply reserve a single observation as a test case, train the model on the whole of the rest of the data, then pass the test case through it and record the relevant performance metrics. Now, we do the same but select a different observation as the test case. We continue doing this until every observation has been used as the test case once, where we take the average of the performance metrics. You can see a scheme of leave-one-out cross-validation in figure 3.14.

Now because the test set is only a single observation, leave-one-out cross-validation tends to give quite variable estimates of model performance (because the performance estimate of each iteration depends on correctly labeling that single test case). But, it can give less variable
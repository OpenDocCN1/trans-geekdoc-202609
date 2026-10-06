# CHAPTER 10. DETECTING ABNORMAL BEHAVIORS

The mean reconstruction error of the normal instances in the train set is 0.811. If we look at the quantiles, we can see that most of the instances have an error of <= 0.887. With this information we can set threshold < 1.0. If the reconstruction error is > threshold then we will consider that as an anomaly.

```
# Make predictions on the abnormal test set.
preds.test_abnormal <- autoencoder %
predict_on_batch(as.matrix(test.test_abnormal[,c(1:2)]))
```

```
# Compute reconstruction errors.
errors.test.abnormal <- squared.errors(preds.test_abnormal,
as.matrix(test.test_abnormal[,c(1:2)]))
```

```
# Predict labels based on threshold 1:abnormal, 0:normal.
pred.labels.abnormal <- as.integer(errors.test_abnormal > threshold)
```

```
# Count how many abnormal instances were detected.
sum(pred.labels.abnormal)
#> [1] 46
```

By using this threshold the autoencoder was able to detect 46 out of the 54 anomaly points. From the following confusion matrix we can also see that there were 16 false positives.

```
#> Reference
#> Prediction 0 1
#> 0 202 8
#> 1 16 46
```

From the ROC curve plot we can see that the AUC was 0.93 which is lower than the 0.96 achieved by the Isolation Forest but with fine tuning and training for more epochs, the autoencoder should be able to achieve similar results.
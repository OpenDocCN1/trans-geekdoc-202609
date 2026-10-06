# CHAPTER 8. PREDICTING BEHAVIOR WITH DEEP LEARNING

# 8.4.1 Early Stopping

```
keras_electromyography_earliest.R
```

Neural networks are trained for several epochs using gradient descent. But the question is: For how many epochs? As can we see in Figure 8.21, many epochs can lead to overfitting and too few can cause underfitting. Early stopping is a simple but effective method to reduce the risk of overfitting. The method consists of setting a large number of epochs and stop updating the network's parameters when a condition is met. For example, one can be to stop when there is no performance improvement on the validation set after n epochs or when there is a decrease of some percent accuracy.

Keras provides some mechanisms to implement early stopping and this is accomplished via callbacks. A callback is a function that is run at different stages during training such as the beginning or end of an epoch at the beginning or end of a batch, Callbacks are passed as a list to the fit() function. You can define custom callbacks or use some of the built-in ones callback_early_stopping(). This callback will cause the training to stop the training if after 10 epochs (patience) there is no improvement of at least 1% (min_delta) in accuracy on the validation set.

```
callback_early_stopping(monitor = "val_acc",
    min_delta = 0.01,
    patience = 10,
    mode = "max")
```

The min_delta parameter specifies the minimum change in the monitored metric to qualify as an improvement. The mode specifies if training should be stopped when the metric has stopped decreasing if it is set to "min". If it is set to "max", training will stop when the monitored metric has stopped increasing.

It may be the case that the best validation performance was not achieved by the model in the last epoch but at some previous point. By setting the restore_best_weights parameter to TRUE the model weights from the epoch with the best value of the monitored metric will be restored.
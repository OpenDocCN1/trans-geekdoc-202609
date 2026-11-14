```
TRAIN SET
(22070, 256, 256, 3)
(22070, 256, 256, 1)
TEST SET
(5518, 256, 256, 3)
(5518, 256, 256, 1)
```

Fig. (8). Train and Test set.

The training of our model stopped after the 48th epoch as the loss value was not improving leading to early stopping, which was fine and appropriate according to the conditions. Hyper-parameter optimization has been done and parameters have been listed in Fig. (9) below.

```
EPOCHS = 100
LEARNING_RATE = 0.0001
BATCH_SIZE = 16
```

Fig. (9). Hyper Parameters.

# RESULTS

The training and early stopping of our model yielded a loss of 24.462% and an accuracy of 60.62%.

Following is the prediction obtained on a separate set of images that are not the part of train and test split. From predicted images, it can be seen that results are fairly good. It is visible in Figs. (10 and 11), that accuracy of prediction is greatly dependent on the input resolution of images.
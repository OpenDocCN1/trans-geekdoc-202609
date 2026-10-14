# Training the Model

Thus far, we haven’t shown the model any data. We have just set up the architecture and compiled the model with a loss function and optimizer.

To train the model against the data, we simply call the fit method, as shown in Example 2-8.

*Example 2-8. Calling the fit method to train the model*

```
model.fit(x_train
    , y_train
    , batch_size = 32
    , epochs = 10
    , shuffle = True
)
```

+   1. The raw image data.
+   2. The one-hot encoded class labels.
+   3. The batch_size determines how many observations will be passed to the network at each training step.
+   4. The epochs determine how many times the network will be shown the full training data.
+   5. If shuffle = True, the batches will be drawn randomly without replacement from the training data at each training step.

This will start training a deep neural network to predict the category of an image from the CIFAR-10 dataset. The training process works as follows.

First, the weights of the network are initialized to small random values. Then the network performs a series of training steps. At each training step, one batch of images is passed through the network and the errors are backpropagated to update the weights. The batch_size determines how many images are in each training step batch. The larger the batch size, the more stable the gradient calculation, but the slower each training step.

![](bbox=[0.16, 0.8, 0.25, 0.9])

It would be far too time-consuming and computationally intensive to use the entire dataset to calculate the gradient at each training step, so generally a batch size between 32 and 256 is used. It is also now recommended practice to increase the batch size as training progresses.⁴
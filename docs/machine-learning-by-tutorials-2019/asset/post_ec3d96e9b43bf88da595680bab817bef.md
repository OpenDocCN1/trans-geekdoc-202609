
spread out amongst the other classes. The new loss is then 0.1054. This prediction is much better, and so the loss is also lower.

Once it has computed a loss value, Keras uses the Adam optimizer you provided when you compiled the model, to figure out which parts of the model contributed to this loss.

The optimizer finds the parts of the model that were responsible for making this (bad prediction) and "punishes" it. This is done by slightly tweaking the learnable parameters by moving them in the opposite direction – a positive number becomes a little less negative, a negative number becomes more positive – so that next time this image is shown to the model it will make a slightly better prediction.

In practice, Keras won't compute the loss for a single image but for a mini-batch of multiple images at a time. You are using a batch of 64 images. For this batch is the average of the 64 individual losses. There are two reasons for using batches:

- 1. It uses the CPU or GPU more efficiently, if you're lucky enough to have a GPU for training. The key to efficient GPU performance is to keep it busy, and with a batch you use more of the GPU's memory bandwidth. The size of the batch is limited by the amount of RAM on the GPU. For a large model with many layers, a batch of 64 may be too big to fit on the GPU and you'll have smaller batches.

- 2. Mathematically speaking, the "true" loss really ought to be computed over the entire training at once. When you're using batches, which only contain a small portion of the training set, you're not actually computing the loss of the model. That would seem like a bad thing, but the opposite is true: using only 64 or fewer images at a time introduces a certain amount of randomness in the training process. And it turns out that this randomness makes it easier for the model to learn. Strange, but that's why the S in SGD stands for stochastic, which means "random" but sounds impressive.

## Hey, it's progress!

While the training process is happening, Keras outputs a progress bar:

```
Epoch 1/5 [====================]
76/76 - 3s 38ms/step -
loss: 3.2150 - acc: 0.10850 -
val_loss: 3.2654 - val_acc: 0.1162
Epoch 2/5 [====================]
76/76 - 2s 26ms/step -
loss: 2.7257 - acc: 0.2079 -
val_loss: 3.2375 - val_acc: 0.1152
```

![](img/5720be5c3cca252e12448e68d25607b5_231_0.png)

```
Epoch 3/5
76/76 [==========================] - 2s 27ms/step
loss: 2.4124 acc: 0.2990
val_loss: 3.2756 val_acc: 0.1120
Epoch 4/5
76/76 [==========================] - 2s 27ms/step
loss: 2.1712 acc: 0.3722
val_loss: 3.2727 val_acc: 0.1246
Epoch 5/5
76/76 [==========================] - 2s 26ms/step
loss: 1.9735 acc: 0.4462 -
val_loss: 3.3359 val_acc: 0.1141
```

During training, Keras reports the training loss and accuracy. After each epoch, Keras also computes the validation loss val_loss and accuracy val_acc over the entire validation.

Notice how loss and acc are improving over time. The training loss goes down while the accuracy goes up. That's good news. But the bad news is that the validation loss doesn't seem to be getting better and the validation accuracy never gets higher than 12%.

Even if you keep training for more epochs, the training accuracy keeps improving but the validation accuracy does not. Try it out, run model.fit_generator() again and see what happens. In fact, if you run this enough times, the validation accuracy may get over time. After 50 or so epochs of training, the training accuracy was 90% but the validation accuracy had dropped to 8%.

To make sure this is not a fluke, you can also try this model on the test set:

```
model.evaluate_generator(test_generator,
steps=len(test_generator))
```

This should print something like:

```
[3.142886356145394, 0.12879831951556086]
```

Again, that is only about 12% accuracy on the images from the test set. Also note that the loss reported here, 3.1428, is only marginally better than the test set loss you saw on the untrained model, which was 3.31179.

## It could be better...

What does this mean? Well, the model did not learn to generalize. It just memorized the training data. After each epoch, Keras also computes the validation loss val_loss and accuracy val_acc over the entire validation.

Notice how loss and acc are improving over time. The training loss goes down while the accuracy goes up. That's good news. But the bad news is that the validation loss doesn't seem to be getting better and the validation accuracy never gets higher than 12%.

Even if you keep training for more epochs, the training accuracy keeps improving but the validation accuracy does not. Try it out, run model.fit_generator() again and see what happens. In fact, if you run this enough times, the validation accuracy may get over time. After 50 or so epochs of training, the training accuracy was 90% but the validation accuracy had dropped to 8%.

To make sure this is not a fluke, you can also try this model on the test set:

```
model.evaluate_generator(test_generator,
steps=len(test_generator))
```

This should print something like:

```
[3.142886356145394, 0.12879831951556086]
```

Again, that is only about 12% accuracy on the images from the test set. Also note that the loss reported here, 3.1428, is only marginally better than the test set loss you saw on the untrained model, which was 3.31179.

What does this mean? Well, the model did not learn to generalize. It just memorized the training data. This is a classic case of overfitting.

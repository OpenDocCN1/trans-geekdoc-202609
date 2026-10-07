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
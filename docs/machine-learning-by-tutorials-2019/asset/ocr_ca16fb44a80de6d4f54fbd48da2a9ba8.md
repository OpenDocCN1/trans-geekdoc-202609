The plot looks like this. You can see the validation accuracy flattens out:

![](bbox=[0.223, 0.145, 0.776, 0.38])

In fact, Keras prints a message that says as much:

```
Epoch 00010: val_acc did not improve from 0.70262
```

Because of the EarlyStopping callback, if there are more than 10 of such epochs in a row, Keras will stop training. But, at this point, you've only trained for 10 epochs in total, so that callback didn't kick in here yet. The other callback, ModelCheckpoint did its job and saved a new version of the model whenever the validation accuracy improved:

```
Epoch 00009: val_acc improved from 0.69215 to 0.70262, saving model to checkpoints/multisnacks-1.0450-0.7026.hdf5
```

The two numbers in the filename, 1.0450 and 0.7026 respectively, are the validation loss and accuracy. But after only nine epochs, this model already got up to 70% accuracy. Sweet! That's a lot better than your previous models and also improves on Puri's results. But you're not done yet...

# Fine-tuning the feature extractor

At this point, it's a good idea to start fine-tuning the feature extractor. So far, you've been using the pre-trained MobileNet as the feature extractor. This was trained on the ImageNet dataset, which contains a large variety of photos from 1,000 different kinds of objects.
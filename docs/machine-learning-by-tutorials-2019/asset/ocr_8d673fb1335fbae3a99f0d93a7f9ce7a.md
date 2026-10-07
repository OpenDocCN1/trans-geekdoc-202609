# Machine Learning Chapter 8: Advanced Convolutional Neural Networks

You can keep tweaking these hyperparameters to squeeze a bit more performance out of the model, but at some point, you have to call it good enough. The author got the best results with a dropout rate of 0.7 and a weight decay of 0.01. This model scored 85% on the test set, which is again a few percentage points better than before.

# # How good is the model?

The very last training epoch is not necessarily the best — it's possible the validation accuracy didn't improve or got much worse — so in order to evaluate the final model on the test set, let's load the best model back in:

```
from keras.models import load_model
best_model = load_model(checkpoint_dir + 
"multisnacks-0.7162-0.8419.hdf5")
```

This loads the model from a checkpoint file that was saved by the ModelCheckpoint callback. This HDF5 file contains the learned parameters for the model but also the architecture definition. (Replace the filename with your own best checkpoint.)

> Note: The multisnacks-0.7162-0.8419.hdf5 file is included in this chapter's resources under final/MobileNet/checkpoints. If you were unable to train the model on your own computer, free to load this version.

> Note: The above instructions are for Keras version 2.2.4 and Keras APIs 1.0.8. It may or not work with newer or older versions.

Now you can evaluate this best model against the test set:

```
best_model.evaluate_generator(test_generator, 
steps=len(test_generator))
```

For the author's best model, this printed [0.633824624967753, 0.86345738152605]. The first number is the length, which isn't really interesting, here,

The second number is the accuracy, over 86%. The Puri Create SqueezeNet model scored 67%, we're doing quite a bit better, here. And it gets in the neighborhood of Create ML's score of 91%.
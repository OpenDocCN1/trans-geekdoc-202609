# Machine Learning Chapter 7: Going Convolutional

First, in a new cell, create an array:

```
histories = []
```

Then, in a cell of its own, call fit_generator(). You'll append the History object that returns to this array:

```
history = _model.fit_generator(
train_generator,
steps_per_epoch=len(train_generator),
validation_data=val_generator,
validation_steps=len(val_generator),
epochs=5,
workers=0).append(history)
```

Now, you can run this cell multiple times and the history won't get lost.

You might wonder why you'd want to run fit_generator() more than once, but it's useful to train for a few epochs to see how the model is doing before you commit to training for many epochs. Also, you might want to change some hyperparameters along the while, such as the learning rate. You'll see an example of that soon.

> Note: Training this kind of model takes up a lot of processing power. On a GTX 1080 Ti GPU, it takes about 15 seconds to train a single epoch. On less powerful GPUs or the CPU it will take much longer. On the author's beefy iMac, it takes 15 minutes per epoch with all cores — and fans — blazing. We suggest that you don't try this model yourself unless you have a Linux machine with a GPU or if you don't mind using cloud services.

If you want to follow along without training, feel free to open the notebook included in the final folder of the provided materials.

# Going doooooown?

To make a plot of the loss over time, do the following:

```
def combine_histories():
    history = {
        "loss": [],
        "val_loss": [],
        "acc": [],
        "val_acc": []
    }
```

![](bbox=[0.159, 0.923, 0.841, 0.953])

Because we only care about whether a certain pattern was detected, but not where, taking the average of its 28×28 heatmap is good enough. If nothing was detected, then this average is a small number close to zero. If something was detected, the average will be a high number. The stronger the detection, the higher the number.

After this global average pooling layer, you now have a 256-element vector that says which of the 256 patterns were detected in the original input image and how strong these detections are. But because you still don't really know what these 256 patterns represent, you can't use them to directly draw conclusions from. But you can use them as features for the logistic regression.

That's why the final two layers in the model are a Dense layer followed by a softmax activation. They serve the same purpose as before: to perform logistic regression on top of the extracted features. The convolutional layers and pooling layers now act as a feature extractor that converts the original pixels into features that are more suitable for use with logistic regression.

And logistic regression learns which combinations of the detected patterns belong to the different classes that you want to detect.

> **Note:** The global pooling layer flattens the four-dimensional image tensor into a two-dimensional feature vector (where the first dimension is the batch size). Unlike a Flat layer, which always expects a fixed number of input features, a global pooling layer can work on images of any arbitrary input size. Models with a Flat layer are therefore much less flexible and not considered to be "fully convolutional". Most modern convnets use a global pooling layer so that they can accept images of any size. Remember: for the best results, images used for inference shouldn't be too much larger or smaller than the images the model was trained on.

## Training the model

The model you’ve built in the previous sections is a typical convnet design, and although not necessarily the optimal—it’s a good start. Let’s see how well this model learns.

As usual, compile the model before use:

```
model.compile(loss="categorical_crossentropy",
              optimizer=optimizers.Adam(lr=1e-3),
              metrics=["accuracy"])
```

## Machine Learning

## Chapter 7: Going Convolutional

You also need the train, val and test generators from the last chapter. Tip: Copy those cells from your Jupyter notebook.

```
images_dir = "snacks/"
train_data_dir = images_dir + "train/"
val_data_dir = images_dir + "val/"
test_data_dir = images_dir + "test/"

def normalize_pixels(image):
    return image / 127.5 - 1
```

```python
from keras.preprocessing.image import ImageDataGenerator
datagen = ImageDataGenerator(
    preprocessing_function=normalize_pixels)
```

```python
batch_size = 64

train_generator = datagen.from_directory(
    train_data_dir,
    target_size=(image_width, image_height),
    batch_size=batch_size,
    class_mode="categorical",
    shuffle=True)
```

```python
val_generator = datagen.from_directory(
    val_data_dir,
    target_size=(image_width, image_height),
    batch_size=batch_size,
    class_mode="categorical",
    shuffle=False)
```

```python
test_generator = datagen.from_directory(
    test_data_dir,
    target_size=(image_width, image_height),
    batch_size=batch_size,
    class_mode="categorical",
    shuffle=False)
```

```python
index2class = {v:k for k,v in
train_generator.class_indices.items()}
```

Training is exactly as before: You can simply call model.fit_generator(). However, let's add some useful code that lets you keep track of the training progress.

Keras returns a History object from fit_generator() that has the loss and any other metrics you asked for. Since it's common to run fit_generator() a few times in a row, you'll combine these History objects into an overall history and plot curves.

![](img/5720be5c3cca252e12448e68d25607b5_261_0.png)

## Machine Learning Chapter 7: Going Convolutional

First, in a new cell, create an array:

```python
histories = []
```

Then, in a cell of its own, call fit_generator(). You'll append the History object that returns to this array:

```python
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

> **Note:** Training this kind of model takes up a lot of processing power. On a GTX 1080 Ti GPU, it takes about 15 seconds to train a single epoch. On less powerful GPUs or the CPU it will take much longer. On the author's beefy iMac, it takes 15 minutes per epoch with all cores — and fans — blazing. We suggest that you don't try this model yourself unless you have a Linux machine with a GPU or if you don't mind using cloud services.

If you want to follow along without training, feel free to open the notebook included in the final folder of the provided materials.

## Going doooooown?

To make a plot of the loss over time, do the following:

```python
def combine_histories():
    history = {
        "loss": [],
        "val_loss": [],
        "acc": [],
        "val_acc": []
    }
```

![](img/5720be5c3cca252e12448e68d25607b5_262_0.png)

```python
for h in histories:
    for k in history.keys():
        history[k] += h.history[k]
return history
```

And then call this:

```python
history = combine_histories()
```

To make the plot:

```python
def plot_loss(history):
    fig = plt.figure(figsize=(10, 6))
    plt.plot(history["loss"])
    plt.plot(history["val_loss"])
    plt.xlabel("Epoch")
    plt.ylabel("Loss")
    plt.legend(["Train", "Validation"])
    plt.show()
```

This uses Matplotlib. It looks like this:

![](img/5720be5c3cca252e12448e68d25607b5_263_0.png)

## Machine Learning

This is roughly the opposite of the loss: The accuracy goes up over time but eventually starts slowing down. After 25 epochs, this model gets a validation of about 38%.

You could train for longer but this model doesn't really seem to be improving anything. In fact, it will get worse over time as you start overfitting. The training accuracy keeps increasing, as the model starts to remember training examples, and is not what you want. The validation accuracy starts to level off after 25 epochs and will eventually become worse.

## Learning rate annealing

One trick you can use to give the accuracy a little boost is to change the learning rate. It is like 1e-3 (set when you compiled the model), and you can change it by doing the following:

```python
import keras.backend as K
K.set_value(model.optimizer.lr, K.set_value(model.optimizer.lr) / 10)
```

K refers to the Keras backend package, which is a wrapper around TensorFlow. You cannot set the optimizer's learning rate directly and must do it in this special way.

Now train for several more epochs. If you call combine_histories() again and plot the loss you'll see a bump where the learning rate was changed, at epoch 30:

![](img/5720be5c3cca252e12448e68d25607b5_265_0.png)

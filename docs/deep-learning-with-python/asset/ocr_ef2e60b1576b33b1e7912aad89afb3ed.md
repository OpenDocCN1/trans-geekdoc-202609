# Listing 8.13 Evaluating the model on the test set

```
test_model = keras.models.load_model("convnet_from_scratch.keras")
test_loss, test_acc = test_model.evaluate(test_dataset)
print(f"Test accuracy: {test_acc:.3f}")
```

We get a test accuracy of 69.5%. (Due to the randomness of neural network initializations, you may get numbers within one percentage point of that.)

Because we have relatively few training samples (2,000), overfitting will be our number one concern. You already know about a number of techniques that can help mitigate overfitting, such as dropout and weight decay (L2 regularization). We’re now going to work with a new one, specific to computer vision and used almost universally when processing images with deep learning models: data augmentation.

# 8.2.5 Using data augmentation

Overfitting is caused by having too few samples to learn from, rendering you unable to train a model that can generalize to new data. Given infinite data, your model would be exposed to every possible aspect of the data distribution at hand: you would never overfit. Data augmentation takes the approach of generating more training data from existing training samples by augmenting the samples via a number of random transformations that yield believable-looking images. The goal is that, at training time, your model will never see the exact same picture twice. This helps expose the model to more aspects of the data so it can generalize better.

In Keras, this can be done by adding a number of data augmentation layers at the start of your model. Let’s get started with an example: the following Sequential model chains several random image transformations. In our model, we’d include it right before the Rescaling layer.

# Listing 8.14 Define a data augmentation stage to add to an image model

```
data_augmentation = keras.Sequential(
[
    layers.RandomFlip("horizontal"),
    layers.RandomRotation(0.1),
    layers.RandomZoom(0.2),
]
)
```

These are just a few of the layers available (for more, see the Keras documentation). Let’s quickly go over this code:

+   RandomFlip("horizontal")—Applies horizontal flipping to a random 50% of the images that go through it

+   RandomRotation(0.1)—Rotates the input images by a random value in the range [-10%, +10%] (these are fractions of a full circle—in degrees, the range would be [-36 degrees, +36 degrees])
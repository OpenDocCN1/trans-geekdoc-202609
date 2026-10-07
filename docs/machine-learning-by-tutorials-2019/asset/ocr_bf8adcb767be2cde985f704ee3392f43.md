# Machine Learning Chapter 8: Advanced Convolutional Neural Networks

> Note: MobileNet preprocess_input() actually does the same thing you've done in the previous chapters: divide the pixel values by 127.5 and subtract 1, so that the new values are in the range [-1, 1]. However, not all models use this particular method of preprocessing. Another way to normalize images is to use the mean and standard deviation of all the pixel values in the training set. If you're using a pretrained model, make sure to use the correct preprocessing for that, or risk getting incorrect predictions.

Given these data objects, you can now make the generators that will read the images from their respective folders. This works just like before:

```
images_dir = "snacks/
train_data_dir = images_dir + "train/"
val_data_dir = images_dir + "val/"
test_data_dir = images_dir + "test/"
batch_size = 64
train_generator = train_datagen.flow_from_directory(
    train_data_dir,
    target_size=(image_width, image_height),
    batch_size=batch_size,
    class_mode="categorical",
    shuffle=True)
val_generator = val_datagen.flow_from_directory(
    val_data_dir,
    target_size=(image_width, image_height),
    batch_size=batch_size,
    class_mode="categorical",
    shuffle=False)
test_generator = test_datagen.flow_from_directory(
    test_data_dir,
    target_size=(image_width, image_height),
    batch_size=batch_size,
    class_mode="categorical",
    shuffle=False)
```

And now you're ready to train!
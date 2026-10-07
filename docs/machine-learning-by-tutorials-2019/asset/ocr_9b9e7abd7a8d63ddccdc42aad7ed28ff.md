# # Loading the data

You've already seen the snacks dataset in the previous chapters. It consists of three different folders (train, val, test), each containing 20 folders for the different classes, and each folder contains several dozen or hundred images.

![](bbox=[0.158, 0.233, 0.84, 0.437])

The snacks dataset

Add some variables that point to these folders:

```
images_dir = "snacks"
train_data_dir = images_dir + "/train/"
val_data_dir = images_dir + "/val/"
test_data_dir = images_dir + "/test/"
```

**Important:** point `images_dir` at the folder where you've downloaded the dataset.

At this point it's a good idea to actually look at the training data with your own eyes, to make sure it's correct. To view an image in the notebook, do the following:

```
from keras.preprocessing import image
img = image.load_img(
train_data_dir + "apple/cecd90f5d46f57b0.jpg",ntarget_size=(image_width, image_height))
```

This loads the JPEG image into the img variable. This is a PIL image object. PIL is a popular image library for Python 2. We're in fact using the Python 3-specific fork: Pillow, but the concepts are identical. Potential confusion alert: the image variable refers to the Keras module for dealing with images, while img is the actual image object.
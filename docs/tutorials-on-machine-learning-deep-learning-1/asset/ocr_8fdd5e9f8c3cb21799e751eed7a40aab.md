# Practiced version

```
############ Convolutional Neural Network : CNN ############
# - Install following packages
# Install Theano
# Install Tensorflow
# Install Tensorflow
# Install Keras

# Part 1 - Building the CNN
# Importing the Keras libraries and packages
from keras.models import Sequential
from keras.layers import Convolution2D
from keras.layers import MaxPooling2D
from keras.layers import Flatten
from keras.layers import Dense
# to initialize as sequence-of-layers
# Convolution step for images
# is not "MaxPool2D". Pooling step for images
# flattening step
# ads fully-connected-layers to classic ANN

# initializing the CNN
cnn_classifier = Sequential()
# step 1 : Convolution - Layer
cnn_classifier.add(Convolution2D(32, 3, 3, input_shape=(64, 64, 3), activation="relu"))

# step 2 : Pooling - Layer
cnn_classifier.add(MaxPooling2D(pool_size=(2, 2)))

# improving step : Adding 2nd Convolution and 2nd Pooling Layers
cnn_classifier.add(Convolution2D(32, 3, 3, activation="relu"))
cnn_classifier.add(MaxPooling2D(pool_size=(2, 2)))

# step 3 : Flattening
cnn_classifier.add(Flatten())

# step 4 : ANN - full connection
cnn_classifier.add(Dense(units=128, activation="relu")) # fully connected layers
cnn_classifier.add(Dense(units=1, activation="sigmoid")) # Output Layer

# compile the NN
cnn_classifier.compile(optimizer="adam", loss="binary_crossentropy", metrics=["accuracy"])
```

```
# Part 2 - Image Preprocessing & fit CNN to our images
from keras.preprocessing import import ImageDataDataGenerator
import math

# creating two data-generator/augmentation objects for train and test data
# Here we specify the transform parameters
train_datagen = ImageDataDataGenerator(
    rescale=1./255,
    shear_range=0.2,
    zoom_range=0.2,
    horizontal_flip=True)

test_datagen = ImageDataDataGenerator(rescale=1./255)

# appying augmentation on training data : training path folder pat
# target_size = input_shape (dimension of expected size)
# batch_size is not related to no. of filters
# '/dataset/training_set'
training_set = train_datagen.flow_from_directory('/dataset/training_set',
target_size=(64, 64),
batch_size=32,
class_mode='binary')
```
Feature scaling: Of course we need feature scaling. Feature scaling is 100% compulsory in deep learning and especially for computer vision.

Previously feature scaling was used to data pre-processing. But here we are not using any previous-processing techniques, so we will take care of feature scaling, just before we use CNN to our images.

Some part of data pre-processing was done manually. We do feature scaling and image augmentation, so that our deep learning model can run most efficiently as possible.

Hence the first part of our CNN model won't be our usual data pre-processing, we will build the CNN first.

# 9.5.4 Import packages for CNN

The first step is to import the Keras packages. Following are the only packages we'll need to make our convolutional neural network.

```
========= Convolutional Neural Network : CNN ==========
# -- Installing packages
# Install Theano
# Install TensorFlow
# Install Tensorflow
# Install Keras

# -- Part 1 - Building the CNN
# Importing the Keras libraries and packages
from keras.models import Sequential # to initialize as sequence-layers
from keras.layers import Convolution2D # Convolution step for images
from keras.layers import MaxPooling2D # not "MaxPool2D. Pooling step for images
from keras.layers import Flatten # Flatten step
from keras.layers import Dense # ads fully-connected to classic ANN
```

+   i. The first package is Sequential and we will use in ANN, we'll to initialize our neural network because, there are two ways of initializing the neural network, as a sequence of layers or as a graph. And since a ANN is still a sequence of layers, we will use the Sequential package to initialize our neural network.

+   ii. Second package, Convolution2D, is the package used for the first step of making the CNN, the Convolution Step, and out the convolutional layers.

+   iii. Since we're working on images and images are in two dimensions (unlike, for example, that are in three dimensions with the time hence, Convolution2D to deal with images.

+   iv. MaxPooling2D, is used to process the third step, the Pooling Step, that will use pooling layers.

+   v. Next package, Flatten is used for 3rd step, flattening in which we convert the pooled maps (that we created through Convolution and MaxPooling) into a large feature vector that is becoming the input of our fully connected layers.

+   vi. The Dense package is used in the ANN. This is the package to add the fully connected layers (of CNN) in a classic ANN.

Basically each of package corresponds to one step of the construction of the CNN.

# 9.5.5 Initialize our CNN

To initialize our CNN, we provoke the Sequential package; It's exactly the same as initializing a classic ANN. We are going to create an object of the Sequential class, and we call this object cnn_classifier.

This classifier will classify some images, to tell if each image is a picture of a dog or a cat. So we're doing nothing else than classification.

```
# initializing the CNN
nnn_classifier = Sequential()
```
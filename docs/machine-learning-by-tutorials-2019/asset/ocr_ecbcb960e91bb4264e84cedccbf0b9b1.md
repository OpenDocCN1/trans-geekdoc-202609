# Machine Learning

To save some training time, you'll start with the classifier model from the last
chapter. After all, this has already learned how to classify snakes and so it already
contains a lot of knowledge about the problem domain. What you're going to do in
this section is to add some additional knowledge about bounding boxes to the model.

To load the best keras from last time, do the following:

```
import keras
from keras.models import Sequential
from keras.layers import *
from keras.models import Model, load_model
from keras import optimizers, callbacks
import keras.backend as K
```

```
checkpoint = "checkpoints/multisnacks-0.7162-0.8419.hdf5"
classifier_model = load_model(checkpoint)
```

This simply grabs the best checkpoint and loads it back. You can find this
checkpoint in this chapter starter folder.

> Tip: Call classifier_model.summary() to check that the model was loaded
correctly.

To add the bounding box predictor layers on top of this checkpoint requires a bit of
ticky, because you want to keep most of the existing model but also add a new
out. It's easiest to build a new model but reuse some of the layers. Since this new
model will involve a branching structure, you can't use the Sequential API
anorebut you have to use the Keras functional API as you saw in last chapter's
SqueezeNet section.

The code is as follows. First, you reconstruct the classifier model from last time:

```
num_classes = 20

# The MobileNet feature extractor is the first "layer"
base_model = classifier_model.layers[0]

# Add a global pooling layer after MobileNet.
pool = GlobalAveragePooling2D()(base_model.outputs[0])

# Reconstruct the classifier layers.
clf = Dropout(0.7)(pool)
clf = Dense(num_classes,
kernel_regularizer=l2(0.01),
name="dense-class")(clf)
clf = Activation("softmax", name="class_prediction")(clf)
```
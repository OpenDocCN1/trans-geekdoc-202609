![](bbox=[0.12, 0.05, 0.88, 0.3])

Figure 3.5: train folder

Next, we will find out how we built the Train Component.

# Train.py

```
from __future__ import absolute_import, division, print_function,
unicode_literals
import click,dill,json,loggig,os,PIL
import pandas as pd
import tensorflow as tf
from storage import Storage
from sklearn.metrics import accuracy_score

def model_build(base_model,NUM_CLASSES,activation):
model =
tf.keras.models.Sequential([base_model,tf.keras.layers.Flatten(),
tf.keras.layers.Dropout(0.5),
tf.keras.layers.Dense(NUM_CLASSES,activation=activation)])
model.layers[0].trainable = False
```
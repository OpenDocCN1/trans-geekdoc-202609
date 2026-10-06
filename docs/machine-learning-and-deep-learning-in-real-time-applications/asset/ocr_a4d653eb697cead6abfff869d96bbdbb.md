# An Introduction to Deep Convolutional Neural Networks With Keras

Figure 33. Multipath skip/shortcut connection of convolution and batch normalization layer using Keras API

![](bbox=[0.298, 0.183, 0.681, 0.617])

```
import keras
from keras.layers import Input, Conv2D, Model, Activation, BatchNormalization
from keras.utils.vis_utils import model_to_dot
imageshape = (41, 41, 1)
inputimage = Input(shape=(imageshape),name='X')
#SKIP LAYER LAYER CONNECTION
#01 LAYER
C1 = Conv2D(64, (3, 3), padding='same', name='Conv2D1')(inputimage)
BN1 = BatchNormalization(axis=3, name='BatchNorm1')(C1)
#STRAIGHT PATH CONNECTION
#02 LAYER
C2 = Conv2D(64, (3, 3), padding='same', name='Conv2D2')(inputimage)
BN2 = BatchNormalization(axis=3, name='BatchNorm2')(C2)
```

268
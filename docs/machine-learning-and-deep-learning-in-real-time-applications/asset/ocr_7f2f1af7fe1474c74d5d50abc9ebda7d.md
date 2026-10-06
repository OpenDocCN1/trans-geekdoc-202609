# An Introduction to Deep Convolutional Neural Networks With Keras

# Create a Five Layer Keras Model

Figure 20 shows the general diagram of five convolution layers followed by ReLU activation layer. Figure 21 shows the five-layer CNN model using convolution followed by an activation layer.

Figure 20. General diagram of five convolution layers followed by ReLU activation layer

![](bbox=[0.147, 0.263, 0.852, 0.503])

```
import keras.backend as K
from keras.models import Sequential, Model
from keras.layers import Conv2D, Activation
from IPython.display import SVG
from keras.utils.vis import model_to_dot
img_shape = (28,28,1)
input_img = Input(shape=img_shape)
C1 = Conv2D(32,(3,3),name='CONV1')(input_img)
A1 = Activation('relu',name='act1')(C1)
C2 = Conv2D(32,(3,3),name='CONV2')(A1)
A2 = Activation('relu',name='act2')(C2)
C3 = Conv2D(32,(3,3),name='CONV3')(A2)
A3 = Activation('relu',name='act3')(C3)
C4 = Conv2D(32,(3,3),name='CONV4')(A3)
```
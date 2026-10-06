# An Introduction to Deep Convolutional Neural Networks With Keras

Figure 12. Regular convolution vs depth-wise separable convolution

# Regular Convolution

# Depth-wise Separable Convolution

![](bbox=[0.183, 0.19, 0.783, 0.335])

3x10x10 16x10x10

3x10x10 3x10x10 16x10x10

3x3(x) Convolution

3x3(1) 1x1(3) Convolution

```
from keras.layers import Input, Conv2D, SeparableConv2D, Activation
from keras.models import Model
from keras import optimizers
from IPython.display import SVG
from keras.utils.vis_utils import_model_to_dot
imageshape=(32,32,1)
imputage = Input(shape=imageshape)
C1 = SeparableConv2D(64,(3,3)),padding='SAME')(imputage)
A1 = Activation('relu', name='act1')(C1)
C2 = SeparableConv2D(32,(3,1),padding='SAME')(A1)
A2 = Activation('relu', name='act2')(C2)
model = Model(imputage, A2)
opt = optimizers.Adam(lr=0.0003)
model.compile(optimizer=opt,loss='mean_squared_error')
model.summary()
```

| input_2 (InputLayer) | (None, 32, 32, 1) | 0 |
|---|---||
| separable_conv2d_3 (Separable) | (None, 32, 32, 64) | 209 |
| act1 (Activation) | (None, 32, 32, 64) | 0 |
| separable_conv2d_4 (Separable) | (None, 32, 32, 32) | 2144 |
| act2 (Activation) | (None, 32, 32, 32) | 0 |

248
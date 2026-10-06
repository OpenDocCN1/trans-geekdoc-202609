
# An Introduction to Deep Convolutional Neural Networks With Keras

```python
from keras.layers import Conv2D, Input, Activation
from keras.models import Model, load_model
from IPython.display import SVG
from keras.utils.vis_utils import import_model_to_dot
img_shape = (41, 41, 1)
input_img = Input(shape=(img_shape))
# 01 LAYER
model1 = Conv2D(6, (3, 3), padding='same', name='conv1')(input_img)
model1 = Activation('relu', name='act1')(model1)
# 02 LAYER
model2 = Conv2D(1, (3, 3), padding='same', name='conv2')(model1)
model2 = Activation('relu', name='act2')(model2)
res_img = model2
output_img = keras.layers.add([res_img, input_img])
model = Model(input_img, output_img)
model.summary()
```

| Layer (type) | Shape | Param # | Connected to |
|---|---|---|---|
| input_3 (InputLayer) | (None, 41, 41, 1) | 0 | |
| conv1 (Conv2D) | (None, 41, 41, 64) | 640 | input_3[0][0] |
| act1 (Activation) | (None, 41, 41, 64) | 0 | conv1[0][0] |
| conv2 (Conv2D) | (None, 41, 41, 1) | 577 | act1[0][0] |
| act2 (Activation) | (None, 41, 41, 1) | 0 | conv2[0][0] |
| add_2 (Add) | (None, 41, 41, 1) | 0 | act2[0][0], input_3[0][0] |

Total params: 1,217

# Build a Residual or Skip Connection Model Using Keras Library

Usually, neural networks contain layers and each layer feeds into the next layer, whereas neural network with residual blocks each layer feeds into the next layer and then directly into layers about 3-2 hops away, as shown in Figure 30.

R(X) = Output - Input = H(X) - X.

H(X) = R(X) + X

# An Introduction to Deep Convolutional Neural Networks With Keras

Figure 29. Skip Connection build by Keras API

![](img/c5cbbc72cd5e7b9be32079eac36d685c_283_0.png)

Figure 30. Single residual block

![](img/c5cbbc72cd5e7b9be32079eac36d685c_283_1.png)

# An Introduction to Deep Convolutional Neural Networks With Keras

# Write the Keras Code for the Residual Block Convolution, Batch Normalization, and ReLU Activation Layers

Figure 31 shows the skip/shortcut connection of the convolution and batch normalization layer. Figure 32 Skip/shortcut connection of convolution and batch normalization layer using Keras API. Figure 33 Multipath skip/shortcut connection of batch normalization layer using Keras API.

Figure 31. Skip/shortcut connection of convolution and batch normalization layer

![](img/c5cbbc72cd5e7b9be32079eac36d685c_284_0.png)

```python
import keras
from keras.layers import Input
from keras.layers import Conv2D
from keras.layers import BatchNormalization
from keras.layers import Activation
from keras.models import Model
from IPython.display.vis_utils import model_to_dot
img_shape = (41, 41, 1)
input_img = Input(shape=img_shape, name='X')
# SKIP LAYER LAYER CONNECTION
# 01 LAYER
C1 = Conv2D(64, (3, 3), padding='same', name='Conv2D1')(input_img)
BN1 = BatchNormalization(axis=3, name='BatchNorm1')(C1)
# STRAIGHT PATH CONNECTION
# 02 LAYER
C2 = Conv2D(64, (3, 3), padding='same', name='Conv2D2')(input_img)
BN2 = BatchNormalization(axis=3, name='BatchNorm2')(C2)
A2 = Activation('relu', name='ReLU1')(BN2)
# 03 LAYER
C3 = Conv2D(64, (3, 3), padding='same', name='Conv2D3')(A2)
BN3 = BatchNormalization(axis=3, name='BatchNorm3')(C3)
A3 = Activation('relu', name='ReLU2')(BN3)
```

# An Introduction to Deep Convolutional Neural Networks With Keras

# 04 LAYER
C4 = Conv2D(1, (3, 3), padding='same', name='CONV2D4')(A3)
BN4 = BatchNormalization(axis=3, name='BatchNorm4')(C4)
# 05 SUM LAYER
output_img = keras.layers.add([BN4, BN1])
A4 = Activation('relu', name='ReLU4')(output_img)
model = Model(input_img, A4)
model.summary()

| Layer (type) | Output Shape | Param # | Connected to |
|---|---|---|---|
| X (InputLayer) | (None, 41, 41, 1) | 0 | |
| CONV2D2 (Conv2D) | (None, 41, 41, 64) | 640 | X[0][0] |
| BatchNorm2 (BatchNormalization) | (None, 41, 41, 64) | 256 | CONV2D2[0][0] |
| ReLU1 (Activation) | (None, 41, 41, 64) | 0 | BatchNorm2[0][0] |
| CONV2D3 (Conv2D) | (None, 41, 41, 64) | 36928 | ReLU1[0][0] |
| BatchNorm3 (BatchNormalization) | (None, 41, 41, 64) | 256 | CONV2D3[0][0] |
| ReLU2 (Activation) | (None, 41, 41, 64) | 0 | BatchNorm3[0][0] |
| CONV2D4 (Conv2D) | (None, 41, 41, 1) | 577 | ReLU2[0][0] |
| CONV2D1 (Conv2D) | (None, 41, 41, 64) | 640 | X[0][0] |
| BatchNorm4 (BatchNormalization) | (None, 41, 41, 64) | 4 | CONV2D4[0][0] |
| BatchNorm1 (BatchNormalization) | (None, 41, 41, 64) | 256 | CONV2D1[0][0] |
| add_3 (Add) | (None, 41, 41, 64) | 0 | BatchNorm4[0][0], BatchNorm1[0][0] |
| ReLU4 (Activation) | (None, 41, 41, 64) | 0 | add_3[0][0] |

# An Introduction to Deep Convolutional Neural Networks With Keras

Figure 32. Skip/shortcut connection of convolution and batch normalization layer using Keras API

![](img/c5cbbc72cd5e7b9be32079eac36d685c_286_0.png)

# Multiple Path Skip Connection

Multiple path Skip Connection is an alternative way to reduce the model complexity and avoid the overfitting problem during training. In these techniques, we use more than two skip connections with the same shape and take the different skip connections from the input as well as from different stages of the layers. Here we show the Keras code of Multiple path Skip Connection and uses the Convolution Layer, Batch Normalization Layer and ReLU Layer. The Multipath connection of convolution and batch normalization layer using Keras API as shown in Figure 3.

# An Introduction to Deep Convolutional Neural Networks With Keras

Figure 33. Multipath skip/shortcut connection of batch normalization layer using Keras API

![](img/c5cbbc72cd5e7b9be32079eac36d685c_287_0.png)

```python
import keras
from keras.layers import Input, Conv2D, BatchNormalization, Activation, Model
from keras.utils.vis_utils import model_to_dot
img_shape = (41, 41, 1)
input_img = Input(shape=img_shape, name='X')
# SKIP LAYER LAYER CONNECTION
# 01 LAYER
C1 = Conv2D(64, (3, 3), padding='same', name='Conv2D1')(input_img)
BN1 = BatchNormalization(axis=3, name='BatchNorm1')(C1)
# STRAIGHT PATH CONNECTION
# 02 LAYER
C2 = Conv2D(64, (3, 3), padding='same', name='Conv2D2')(input_img)
BN2 = BatchNormalization(axis=3, name='BatchNorm2')(C2)
A2 = Activation('relu', name='ReLU1')(BN2)
# 03 LAYER
C3 = Conv2D(64, (3, 3), padding='same', name='Conv2D3')(A2)
BN3 = BatchNormalization(axis=3, name='BatchNorm3')(C3)
A3 = Activation('relu', name='ReLU2')(BN3)
```

# 04 LAYER
C4 = Conv2D(1, (3, 3), padding='same', name='CONV2D4')(A3)
BN4 = BatchNormalization(axis=3, name='BatchNorm4')(C4)
# 05 SUM LAYER
output_img = keras.layers.add([BN4, BN1])
A4 = Activation('relu', name='ReLU4')(output_img)
model = Model(input_img, A4)
model.summary()

| Layer (type) | Shape | Param # | Connected to |
|---|---|---|---|
| X (InputLayer) | | 0 | |
| CONVD2 (Conv2D) | (None, 41, 41, 64) | 640 | X[0][0] |
| BatchNorm2 (BatchNormalization) | (None, 41, 41, 64) | 256 | CONV2D2[0][0] |
| ReLU1 (Activation) | (None, 41, 41, 64) | 0 | BatchNorm2[0][0] |
| CONV2D3 (Conv2D) | (None, 41, 41, 64) | 36928 | ReLU1[0][0] |
| BatchNorm3 (BatchNormalization) | (None, 41, 41, 64) | 256 | CONV2D3[0][0] |
| ReLU2 (Activation) | (None, 41, 41, 64) | 0 | BatchNorm3[0][0] |
| CONV2D4 (Conv2D) | (None, 41, 41, 1) | 577 | ReLU2[0][0] |
| CONV2D1 (Conv2D) | (None, 41, 41, 64) | 640 | X[0][0] |
| BatchNorm4 (BatchNormalization) | (None, 41, 41, 64) | 4 | CONV2D4[0][0] |
| BatchNorm1 (BatchNormalization) | (None, 41, 41, 64) | 256 | CONV2D1[0][0] |
| add_5 (Add) | (None, 41, 41, 64) | 0 | BatchNorm4[0][0], BatchNorm1[0][0] |
| ReLU4 (Activation) | (None, 41, 41, 64) | 0 | add_5[0][0] |

# An Introduction to Deep Convolutional Neural Networks With Keras

# REFERENCES

- Abadi, M., Agarwal, A., Barham, P., Brevdo, E., Chen, Z., Citro, C., . . . Devin, M. (2016). Tensorflow: Large-scale machine learning on distributed systems. arXiv preprint arXiv:1603.04467
- Abadi, M., Barham, P., Chen, J., Chen, Z., Davis, A., Dean, J., . . . Isard, M. (2016). Tensorflow: A system for large-scale machine learning. Presented at the 12th [USENIX] Symposium on Operating Systems Design and Implementation.
- Anwar, S., Huynh, C. P., & Polikoli, F. (2017). Chaining identity modules for image denoising. arXiv preprint arXiv:1712.02933
- Bishop, C. M. (2006). Pattern recognition and machine learning. Springer.
- Bloomfield, L. A. (2001). How things work. Louis A. Bloomfield.
- Boyd, R., & Holton, R. J. (2018). Innovation, employment and power: Does robotics and artificial intelligence really mean social transformation? Journal of Sociology (Melbourne, Vic.), 54(3), 331–345. doi:10.1117/1470783312776591
- Bui, D.-K., Nguyen, T. N., Ngo, D. T., & Nguyen-Xuan, H. (2020). An artificial neural network (ANN) expert system enhanced by the electromagnet-based firstly algorithm (EFA) for predicting the energy consumption in buildings. Energy, 190, 116370. doi:10.1016/j.energy.2019.116370
- Chollet, F. (2017). Xception: Deep learning with deepwise separable convolutions. arXiv preprint, 1610.02357.



# 使用 Keras 深度卷积神经网络简介

图 12. 普通卷积 vs 深度可分离卷积

## 普通卷积

## 深度可分离卷积

![](img/c5cbbc72cd5e7b9be32079eac36d685c_267_0.png)

3x10x10 16x10x10 

3x10x10 3x10x10 16x10x10

3x3(x) 卷积

3x3(1) 1x1(3) 卷积

```python
from keras.layers import Input, Conv2D, SeparableConv2D, Activation
from keras.models import Model
from keras import optimizers
from IPython.display import SVG
from keras.utils.vis_utils import model_to_dot
imageshape=(32,32,1)
imputage = Input(shape=imageshape)
C1 = SeparableConv2D(64,(3,3),padding='SAME')(imputage)
A1 = Activation('relu', name='act1')(C1)
C2 = SeparableConv2D(32,(3,1),padding='SAME')(A1)
A2 = Activation('relu', name='act2')(C2)
model = Model(imputage, A2)
opt = optimizers.Adam(lr=0.0003)
model.compile(optimizer=opt,loss='mean_squared_error')
model.summary()
```

| input_2 (InputLayer) | (None, 32, 32, 1) | 0 |
|---|---|---|
| separable_conv2d_3 (Separable) | (None, 32, 32, 64) | 209 |
| act1 (Activation) | (None, 32, 32, 64) | 0 |
| separable_conv2d_4 (Separable) | (None, 32, 32, 32) | 2144 |
| act2 (Activation) | (None, 32, 32, 32) | 0 |

图 13. 通过 Keras API 构建普通卷积与深度可分离卷积模型

| | input: (None, 32, 32, 1) |
| input_2: InputLayer | output: (None, 32, 32, 1) |

| input: (None, 32, 32, 1) |
| separable_conv2d_3: SeparableConv2D | output: (None, 32, 32, 64) |

| input: (None, 32, 32, 64) |
| act1: Activation | output: (None, 32, 32, 64) |

| input: (None, 32, 32, 64) |
| separable_conv2d_4: SeparableConv2D | output: (None, 32, 32, 32) |

| input: (None, 32, 32, 32) |
| act2: Activation | output: (None, 32, 32, 32) |

## 转置卷积层或反卷积层

转置卷积通常源于希望使用与标准卷积相反方向的变换，即：从任何具有某些卷积输出形状的形状出发，同时保留与该卷积兼容的连接模型。图 14 展示了 2D 转置卷积。图 15 展示了通过 Keras API 使用转置卷积构建模型的步骤。

图 14. 2D 转置卷积

![](img/c5cbbc72cd5e7b9be32079eac36d685c_268_0.png)

```python
from keras.layers import Input, Conv2DTranspose, Conv2D
from keras.models import Model
img_shape = (32,32,1)
inputputimage = Input(shape=(img_shape))
D1 = Conv2DTranspose(32,3,3, strides=(2,2),padding='same',name='TRANS_CONV1')(inputputimage)
C1 = Conv2D(32,1,1,padding='SAME',name='CONV1'(D1)
model = Model(inputimage, C1)
model.summary()
```

| Layer (type) | Output Shape | Param # |
|---|---|---|
| input_2 (InputLayer) | (None, 32, 32, 1) | 0 |
| TRANS_CONV1 (Conv2DTranspose) | (None, 64, 64, 32) | 320 |
| CONV1 (Conv2D) | (None, 64, 64, 32) | 1056 |

```python
from IPython.display import SVG
from keras.utils.vis_utils import model_to_dot
SVG(model_to_dot(model), show_shapes=True).create(prog='dot', format='svg')
```

图 15. 通过 Keras API 构建转置卷积模型

| | input: (None, 32, 32, 1) |
| input_2: InputLayer | output: (None, 32, 32, 1) |

| input: (None, 32, 32, 1) |
| TRANS_CONV1: Conv2DTranspose | output: (None, 64, 64, 32) |

| input: (None, 64, 64, 32) |
| CONV1: Conv2D | output: (None, 64, 64, 32) |

## 最大池化与平均池化层

最大池化层通过将输入划分为特定的矩形区域并计算每个区域的最大值来进行下采样。平均池化层通过将输入划分为矩形区域并计算平均值来进行下采样。图 16 展示了最大池化与平均池化的对比。图 17 展示了通过 Keras 使用最大池化的构建模型。

![](img/c5cbbc72cd5e7b9be32079eac36d685c_270_0.png)

```python
from keras import layers, models
model = models.Sequential()
model.add(layers.Conv2D(32,(5,5),activation='relu',input_shape=(28,28,1)))
model.add(layers.MaxPooling2D(2, 2))
model.add(layers.Conv2D(64, (5, 5), activation='relu'))
model.add(layers.MaxPooling2D(2, 2))
model.summary()
```

| Layer | Output Shape | Param # |
|---|---|---|
| conv2d_5 (Conv2D) | (None, 24, 24, 32) | 832 |
| max_pooling_5 (MaxPooling2D) | (None, 12, 12, 32) | 0 |
| conv2d_6 (Conv2D) | (None, 8, 8, 64) | 5164 |
| max_pooling_6 (MaxPooling2D) | (None, 4, 4, 64) | 0 |

Total params: 52096
Trainable params: 52096
Non-trainable params: 0

```python
from IPython.display import SVG
from keras.utils.vis import model_to_dot
SVG(model_to_dot(model, show_shapes=True).create(prog='dot', format='svg')
```

图 17. 通过 Keras 使用最大池化构建模型

![](img/c5cbbc72cd5e7b9be32079eac36d685c_271_0.png)

## 5. 创建单层 Keras 模型

图 18 展示了单层 Keras 的结构图。图 19 展示了通过 Keras 使用卷积层构建单层模型的步骤。

图 18. 单层 Keras 结构图

![](img/c5cbbc72cd5e7b9be32079eac36d685c_271_1.png)

## 使用 Keras 的深度神经网络简介

```python
import keras.backend as K
from keras.models import Sequential, Model
from keras.layers import Conv2D, Activation
from keras.utils.vis_utils import model_to_dot
img_shape = (28,28,1)
input_img = Input(shape=img_shape)
C1 = Conv2D(32,(3,3),name='CONV1')(input_img)
A1 = Activation('relu',name='act1')(C1)
model = Model(input_img, A1)
model.summary()
```

| Layer (type) | Output Shape | Param # |
|---|---|---|
| input_8 (InputLayer) | (None, 28, 28, 1) | 0 |
| CONV1 (Conv2D) | (None, 26, 26, 32) | 320 |
| act1 (Activation) | (None, 26, 26, 32) | 0 |

Total params: 320
Trainable params: 320
Non-trainable params: 0

```python
SVG(model_to_dot(model, show_shapes=True).create(prog='dot', format='svg'))
```

图 19. 通过 Keras 使用卷积层和激活层构建单层模型

| | input: (None, 28, 28, 1) |
| input_8: InputLayer | output: (None, 28, 28, 1) |

| | input: (None, 28, 28, 1) |
| CONV1: Conv2D | output: (None, 26, 26, 32) |

| | input: (None, 26, 26, 32) |
| act1: Activation | output: (None, 26, 26, 32) |

## 使用 Keras 深度卷积神经网络简介

## 创建一个五层 Keras 模型

图 20 展示了五层卷积后接 ReLU 激活层的总体图。

图 21 展示了使用卷积层后接激活层构建五层 CNN 模型。

图 20. 五层卷积后接 ReLU 激活层的总体图

![](img/c5cbbc72cd5e7b9be32079eac36d685c_273_0.png)

```python
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

A4 = Activation('relu', name='act4')(C4)
C5 = Conv2D(32,(3,3),name='CONV5')(A4)
A5 = Activation('relu', name='act5')(C5)
model = Model(input_img, A5)
model.summary()

| Layer (type) | Output Shape | Param # |
|---|---|---|
| input_10 (InputLayer) | (None, 28, 28, 1) | 0 |
| CONV1 (Conv2D) | (None, 26, 26, 32) | 320 |
| act1 (Activation) | (None, 26, 26, 32) | 0 |
| CONV2 (Conv2D) | (None, 24, 24, 32) | 9248 |
| act2 (Activation) | (None, 24, 24, 32) | 0 |
| CONV3 (Conv2D) | (None, 22, 22, 32) | 9248 |
| act3 (Activation) | (None, 22, 22, 32) | 0 |
| CONV4 (Conv2D) | (None, 20, 20, 32) | 9248 |
| act4 (Activation) | (None, 20, 20, 32) | 0 |
| CONV5 (Conv2D) | (None, 18, 18, 32) | 9248 |
| act5 (Activation) | (None, 18, 18, 32) | 0 |


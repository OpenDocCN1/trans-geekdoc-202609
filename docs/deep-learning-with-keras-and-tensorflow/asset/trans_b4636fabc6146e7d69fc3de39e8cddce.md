

# Hands On:

## 尝试对 VGG19 模型做同样的操作

```python
# from keras.applications import VGG19

# - Visualise Summary
# - Infer classes using VGG19 predictions
```

```python
# [your code here]
```

# 残差网络

![](resnet_bb.png)

## ResNet 50

![](resnet34.png)

```python
from keras.applications import ResNet50
```

ResNet 由两个主要块组成：`Identity Block` 和 `ConvBlock`。

`IdentityBlock` 是快捷连接处没有卷积层的块

`ConvBlock` 是快捷连接处有卷积层的块

```python
from keras.applications.resnet50 import identity_block, conv_block
```

```python
identity_block??
```

```python
conv_block??
```

* * *

# 可视化 CNN 的卷积滤波器

```python
import numpy as np
import time
from keras.applications import vgg16
from keras import backend as K
```

```python
from matplotlib import pyplot as plt

%matplotlib inline
```

```python
# 每个滤波器生成的图片尺寸。
IMG_WIDTH = 224
IMG_HEIGHT = 224
```

```python
from keras.applications import vgg16

# 使用 ImageNet 权重构建 VGG16 网络
vgg16 = vgg16.VGG16(weights='imagenet', include_top=False)
print('Model loaded.')
```

```
Model loaded.
```

```python
vgg16.summary()
```

```
_________________________________________________________________
Layer (type)                 Output Shape              Param #   
=================================================================
input_2 (InputLayer)         (None, None, None, 3)     0         
_________________________________________________________________
block1_conv1 (Conv2D)        (None, None, None, 64)    1792      
_________________________________________________________________
block1_conv2 (Conv2D)        (None, None, None, 64)    36928     
_________________________________________________________________
block1_pool (MaxPooling2D)   (None, None, None, 64)    0         
_________________________________________________________________
block2_conv1 (Conv2D)        (None, None, None, 128)   73856     
_________________________________________________________________
block2_conv2 (Conv2D)        (None, None, None, 128)   147584    
_________________________________________________________________
block2_pool (MaxPooling2D)   (None, None, None, 128)   0         
_________________________________________________________________
block3_conv1 (Conv2D)        (None, None, None, 256)   295168    
_________________________________________________________________
block3_conv2 (Conv2D)        (None, None, None, 256)   590080    
_________________________________________________________________
block3_conv3 (Conv2D)        (None, None, None, 256)   590080    
_________________________________________________________________
block3_pool (MaxPooling2D)   (None, None, None, 256)   0         
_________________________________________________________________
block4_conv1 (Conv2D)        (None, None, None, 512)   1180160   
_________________________________________________________________
block4_conv2 (Conv2D)        (None, None, None, 512)   2359808   
_________________________________________________________________
block4_conv3 (Conv2D)        (None, None, None, 512)   2359808   
_________________________________________________________________
block4_pool (MaxPooling2D)   (None, None, None, 512)   0         
_________________________________________________________________
block5_conv1 (Conv2D)        (None, None, None, 512)   2359808   
_________________________________________________________________
block5_conv2 (Conv2D)        (None, None, None, 512)   2359808   
_________________________________________________________________
block5_conv3 (Conv2D)        (None, None, None, 512)   2359808   
_________________________________________________________________
block5_pool (MaxPooling2D)   (None, None, None, 512)   0         
=================================================================
Total params: 14,714,688
Trainable params: 14,714,688
Non-trainable params: 0
_________________________________________________________________
```

```python
from collections import OrderedDict
layer_dict = OrderedDict()
# 获取每个“关键”层的符号输出（我们为它们赋予了唯一名称）。
for layer in vgg16.layers[1:]:
    layer_dict[layer.name] = layer
```

#### 测试图像

```python
img_path = os.path.join(IMAGENET_FOLDER, 'strawberry_1157.jpeg')
img = image.load_img(img_path, target_size=(IMG_WIDTH, IMG_HEIGHT))
plt.imshow(img)
```

```
<matplotlib.image.AxesImage at 0x7f896378cda0>
```

![](4.4%20Deep%20Convolutional%20Neural%20Networks_44_1.png)

```python
input_img_data = image.img_to_array(img)
# input_img_data /= 255
plt.imshow(input_img_data)
```

```
<matplotlib.image.AxesImage at 0x7f89636cd240>
```

![](4.4%20Deep%20Convolutional%20Neural%20Networks_45_1.png)

```python
input_img_data = np.expand_dims(input_img_data, axis=0)
print('Input image shape:', input_img_data.shape)
```

```
Input image shape: (1, 224, 224, 3)
```

### 通过各层可视化图像

```python
## 调用笔记本中定义的隐藏特征函数（2.1 隐藏层表示与嵌入）

def get_activations(model, layer, input_img_data):
    activations_f = K.function([model.layers[0].input, K.learning_phase()], [layer.output,])
    activations = activations_f((input_img_data, False))
    return activations
```

```python
layer_name = 'block1_conv2'
layer = layer_dict[layer_name]
activations = get_activations(vgg16, layer, input_img_data)
```

```python
print(len(activations))
activation = activations[0]
activation.shape
```

```
1





(1, 224, 224, 64)
```

```python
layer.filters  # 所选卷积块中的滤波器数量
```

```
64
```

```python
activated_img = activation[0]
n = 8
fig = plt.figure(figsize=(20, 20))
for i in range(n):
    for j in range(n):
        idx = (n*i)+j
        ax = fig.add_subplot(n, n, idx+1)
        ax.imshow(activated_img[:,:,idx])
```

![](4.4%20Deep%20Convolutional%20Neural%20Networks_52_0.png)

```python
conv_img_mean = np.mean(activated_img, axis=2)
```

```python
conv_img_mean.shape
```

```
(224, 224)
```

```python
plt.imshow(conv_img_mean)
```


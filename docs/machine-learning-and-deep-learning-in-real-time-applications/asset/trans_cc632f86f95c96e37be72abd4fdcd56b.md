

# 深度学习 Keras

图 22.

```python
else:
    print('Using real-time data augmentation.')
    # 这将进行预处理和实时数据增强：
    datagen = ImageDataGenerator(
        featurewise_center=False, # 将数据集的输入均值设置为0
        samplewise_center=False, # 将每个样本设置为0
        featurewise_normalization=False, # 用数据集的标准差除以输入
        samplewise_normalization=False, # 用每个输入的标准差除以每个输入
        zca_whitening=False, # 应用 ZCA 白化
        zca_epsilon=0.0, # ZCA 白化的 epsilon 值
        rotation_range=40, # 设置在范围（角度, 0 到 180）内的范围
        width_shift_range=0.2, # 水平平移图像（总宽的比例）
        height_shift_range=0.2, # 垂直平移图像（总高度的比例）
        shear_range=0.0, # 设置随机剪切的范围
        zoom_range=0., # 设置随机缩放的范围
        channel_shift_range=0, # 设置随机通道偏移的范围
        fill_mode='nearest', # 设置输入边界外的填充模式点
        cval=0, # 填充模式 "constant" 的值
        horizontal_flip=True, # 随机翻转图像
        vertical_flip=False, # 随机翻转图像
        rescaling=1./255) # 缩放（在任何其他变换之前应用）
    # 设置应用于每个输入的处理函数
    preprocessing_function=None,
    # 图像数据格式，可以是 "first" 或 "channels_last"
    data_format=None,
    # 用于验证的移除比例（严格在 0 和 1 之间）
    validation_split=0.2)
datagen.fit(x_train)
```

```python
# 在 flow() 生成的批上拟合模型。
history=datagen.fit(datagen, x_train, y_train, batch_size=batch_size,
    steps_per_epoch=len(x_train) // batch_size,
    epochs=epochs,
    validation_data=datagen.flow(x_test, y_test,
    validation_steps=x.shape[0] // batch_size,
    verbose=2, callbacks=[checkpoints])
```

```
40s - loss: 0.7026 acc: 0.8110 - val_loss: 0.7372 - val_acc: 0.8090
Epoch 34/40
39s - loss: 0.6973 acc: 0.8104 - val_loss: 0.6470 - val_acc: 0.8320
Epoch 36/40
39s - loss: 0.6896 acc: 0.8149 - val_loss: 0.6792 - val_acc: 0.8235
38s - loss: 0.6876 acc: 0.8148 - val_loss: 0.6513 - val_acc: 0.8345
Epoch 37/40
37s - loss: 0.6850 acc: 0.8182 - val_loss: 0.6328 - val_acc: 0.8356
Epoch 38/40
39s - loss: 0.6737 acc: 0.8211 - val_loss: 0.6754 - val_acc: 0.8303
Epoch 39/40
39s - loss: 0.6737 acc: 0.8207 - val_loss: 0.6381 - val_acc: 0.8390
Epoch 40/40
38s - loss: 0.6702 acc: 0.8233 - val_loss: 0.6355 - val_acc: 0.8398
```

# 使用 Keras 进行深度学习

图 23.

```python
# 评估模型
scores = model.evaluate(x_test, y_test, verbose=1)
print('Test loss:', scores[0])
print('Test accuracy:', scores[1])
```

10000/10000 ======================================== 2s 232us/step
Test loss: 0.63431428062439
Test accuracy: 0.8589

图 24.

```python
# 评估模型
scores = model.evaluate(x_test, y_test, verbose=1)
print('Test loss:', scores[0])
print('Test accuracy:', scores[1])
```

10000/10000 ======================================== 2s 236us/step
Test loss: 0.6355399031066
Test accuracy: 0.8398

图 25.

```python
import keras
from matplotlib.pyplot import plt as plt
plt.plot(history.history['acc'])
plt.plot(history.history['val_acc'])
plt.title('model accuracy')
plt.xlabel('epoch')
plt.ylabel('accuracy')
plt.legend(['train', 'val'], loc='upper left')
plt.show()
```

```python
plt.plot(history.history['loss'])
plt.plot(history.history['val_loss'])
plt.title('model loss')
plt.xlabel('epoch')
plt.ylabel('loss')
plt.legend(['train', 'val'], loc='upper left')
plt.show()
```

![](img/c5bbc72cde7b3207ac3685c730.png)

# 使用 Keras 进行深度学习

图 26.

```python
from sklearn.model_selection import train_test_split
x_train, x_val, y_train, y_val = train_test_split(x, y, test_size=0.25, shuffle=True, random_state=42)
print(x_train.shape, y_train.shape)
print(x_val.shape, y_val.shape)
print(x_test.shape, y_test.shape)
```

(37500, 32, 3)
(12500, 32, 3)
(10000, 32, 3)

划分数据集后的图像数量：
训练集=37500，验证集=12500，测试集=10000

# Keras API 提供的预训练模型

预训练模型是在大型基准数据集上训练的。由于缺乏从头训练模型的计算资源（可能需要几天或几个月），导入已经在大型数据集上训练好的预训练模型是一种常见做法。keras 中提供的基于深度卷积网络（CNN）的预训练模型列表如图 27 所示。

图 27. Keras 中的预训练模型（Chollet, 2015）

- Xception
- VGG16
- VGG19
- ResNet, ResNetV2, ResNext
- InceptionV3
- InceptionResNetV2
- MobileNet
- MobileNetV2
- DenseNet
- NASNet

# Keras 迁移学习与深度学习

与其从头训练模型（如前面的章节所示），可以有效地利用迁移学习来利用在对象分类任务中表现出尖性能的预训练模型。keras API 提供的 VGG16 或 VGG19、InceptionV3、ResNet50 等模型是在 ImageNet 数据集上训练的，该数据集包含 120 万张通用图像分类。我们可以直接下载任何所选预训练模型的权重并对其进行微调。通常，微调模型有三种方法。

# 特征提取

预训练网络的输出层预测 1000 个类别中的一个。在特征提取机制中，预训练模型的输出层被具有模型预测类别数量的新层取代，作为新数据集的固定特征提取器。在以下情况下有用：

- 从头训练模型的资源有限，或
- 缺乏更大的数据集，或
- 用于训练预训练模型的数据与我们解决问题的数据相似。

# 使用预训练模型的架构训练整个模型

利用预训练模型的架构通过随机初始化权重在我们数据集上从头训练模型。在以下情况下有用：

- 有大量的计算能力从头训练模型以及
- 有更大的数据集。

# 在冻结其他层时训练某些层

使用预训练模型的另一种方法是部分训练。网络的低层表示如水平线、垂直线、曲线等通用特征，而高层特征表示更特定的特征。通过这种方法，我们可以通过冻结训练期间权重不改变的低层，只重新训练网络的高层。

# 在 Keras 中执行迁移学习的步骤

我们在本章的上一个节中已经使用（sequential）方法训练了一个模型。现在，我们将尝试使用 Keras 中的迁移学习来提高模型的准确性。需要遵循的步骤如下：

# 深度学习 Keras

# 步骤 1. 加载必要的库

图 28.

```python
from tensorflow.keras.applications.resnet50 import ResNet50, preprocess
import tensorflow.keras as keras
from tensorflow.keras import models
from tensorflow.keras import layers
from tensorflow.keras import optimizers
import tensorflow as tf
from keras.utils import np_utils
from keras.models import load_model
from keras.datasets import cifar10
from keras.preprocessing import image
import numpy as np
import matplotlib.pyplot as plt
from PIL import Image
import cv2
```

# 步骤 2. 加载预训练模型

在本例中，为 CIFAR 数据集中的对象分类任务选择了 ResNet50 模型。在这一步中，我们从 keras applications 导入 ResNet50 模型。由于 ResNet是在包含 1000 类对象的 ImageNet 数据集上训练的，我们选择 `include_top = False`。它移除了预训练网络的全连接层。

```python
# 创建模型
conv_base = ResNet50(weights='imagenet', include_top=False, input_shape=(200, 200, 3))
```

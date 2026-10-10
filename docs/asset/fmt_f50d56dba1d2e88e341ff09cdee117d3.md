
```
model.outputHeight = model.output_shape[-2]
model.outputWidth = model.output_shape[-1]
```

```
model.add(tf.keras.layers.Reshape((nClasses, model.output_shape[-2] *
model.output_shape[-1])))
```

```
input_shape=(nClasses, model.output_shape[-2],
model.output_shape[-1])

model.add(tf.keras.layers.Permute((2, 1)))
model.add(tf.keras.layers.Activation('softmax'))

model.compile(loss="categorical_crossentropy",
optimizer=tf.keras.optimizers.Adam, metrics=['accuracy'])
```

这种图像编码和解码的方法克服了基于 FCN 模型的缺点。接下来，我们将看到一个关于空洞卷积的不同概念。

## 用于改进训练效果的跳跃连接

分割输出的粗糙程度可以通过跳跃结构来限制，并获得更高的分辨率。另一种替代方法是放大最后三层并对它们取平均值，如下所示：

![](img/48c861eac4dc634fbf2a09fdbe884beb_153_0.png)

该算法将在稍后的章节中用于卫星图像示例。

### 空洞卷积

像素级分类和图像级分类在结构上是不同的。因此，减少信息的池化层会产生粗糙的分割。因此，请记住，池化对于获得更宽的视野和允许采样至关重要。引入了一种名为`空洞卷积`（dilated convolution）的新想法，用于解决在获得更宽视野的同时实现低损耗采样的问题。空洞卷积本质上是通过跳过窗口中的每个像素进行的卷积，如下所示：

![](img/48c861eac4dc634fbf2a09fdbe884beb_154_0.png)

空洞距离随层而异。此类分割结果的输出会被放大以获得更细的分辨率。将训练一个单独的网络用于多尺度聚合。

### DeepLab

Chen 等人（https://arxiv.org/pdf/1606.00915.pdf）提出的 DeepLab 在多个尺度上进行卷积，并使用各种尺度的特征来获取得分图。然后对得分图进行插值，并通过条件随机场（CRF）进行最终分割。这种图像的尺度处理既可以通过自己的 CNN 处理各种尺寸的图像来实现，也可以通过具有不同级别空洞卷积的并行卷积来实现。

![](img/48c861eac4dc634fbf2a09fdbe884beb_155_0.png)

来自 Chen 等人。

## RefiNet

空洞卷积需要更大的输入，因此在使用高分辨率图片时会带来内存问题。Reid 等人（https://arxiv.org/pdf/16110662.pdf）证明了一种名为 RefiNet 的方法来解决这个问题，如下所示：

![](img/48c861eac4dc634fbf2a09fdbe884beb_156_0.png)

## 语义分割

RefiNet 使用编码器后接解码器。编码器的 CNN 输出。解码器拼接了各种尺寸的特征：

![](img/48c861eac4dc634fbf2a09fdbe884beb_157_0.png)

拼接是通过上采样低维特征完成的。

### PSPnet

Zhao 等人（https://arxiv.org/pdf/1612.0105.pdf）引入的 PSPnet 通过增加池化层的尺寸来实现。池化以金字塔形式进行。金字塔同时覆盖图像的不同部分和尺寸。架构之间存在损失，实现了适度监督。

![](img/48c861eac4dc634fbf2a09fdbe884beb_158_0.png)

来自 Zhao 等人。

## 大卷积

Peng 等人（https://arxiv.org/pdf/1703.02719.pdf）展示了大卷积的重要性。大卷积比小卷积具有更大的感受野。这些大卷积的计算复杂度可以使用近似卷积来克服。末尾有一个边界细化网络。

## 第 5 章

| 图像 | 得分图 | w x h x c |
| --- | --- | --- |
| ![image](https://example.com/image1) | ![image](https://example.com/image2) | 卷积 h 1 x 21 x 21 |
| conv-1 258 x 256 x 64 | 真值 (Ground Truth) | 卷积 h 1 x 21 x 21 |
| res-2 128 x 128 x 256 | 预测 (Prediction) | 卷积 h 1 x 21 x 21 |
| res-3 64 x 64 x 512 | GCN 128 x 128 x 21 | 求和 w x h x 21 |
| res-4 32 x 32 x 1024 | GCN 64 x 64 x 21 | Conv x ReLU 3 x 3 x 21 x 21 |
| res-5 16 x 16 x 2048 | GCN 16 x 18 x 21 | 卷积 3 x 3 x 21 x 21 |
| | | 转卷积 32 x 32 |
| A. 全局流水线 | 边界细化 | |
| | | |

### DeepLab v3

批归一化用于 Chen 等人（https://arxiv.org/pdf/1706.05587.pdf）提出的论文中以提高性能。特征的多尺度以级联方式编码为：

![](img/48c861eac4dc634fbf2a09fdbe884beb_159_2.png)

来自 Chen 等人。

## 语义分割

## 第 5 章

![](img/48c861eac4dc634fbf2a09fdbe884beb_160_0.png)

| | Conv1 | Block2 | Block3 | Block4 |
|---|---|---|---|---|
| | rate=2 | | | |
| 输出步长 (output stride) | 4 | 8 | 16 | 16 |

## 神经分割

我们已经看到几种架构利用深度学习提高了图像分割的精度。接下来，我们将看到医学影像的应用。

Kaggler 是一个预测建模和分析竞赛的组织。Kagglers 挑战从颈部超声图中分割神经结构。相关数据可以从 https://www.kaggle.com/c/ultrasound-nerve-segmentation 下载。Ronneberger 等人提出的 UNET 模型（https://arxiv.org/pdf/1505.04597.pdf）类似于自动编码器，但使用卷积代替全连接层。有一个维度递减的卷积编码部分和一个维度递增的解码部分，如下所示：

![](img/48c861eac4dc634fbf2a09fdbe884beb_161_0.png)

说明 UNET 模型架构的图 [来自 Ronneberger 等人的许可]。

相似的编码器和解码部分的卷积通过跳跃连接进行学习。模型的输出是一个范围于 0 到 1 之间的掩码。让我们通过以下代码导入函数：

```
import os
from skimage.transform import resize
from skimage.io import imsave
import numpy as np
from data import load_train_data, load_test_data
```

在完成所有导入后，我们现在使用以下代码定义尺寸：

```
image_height, image_width = 96, 96
smoothness = 1.0
work_dir = ''
```

## 语义分割

## 第 5 章

现在我们将定义 dice_coefficient 及其损失函数。在这种情况下，dice_coefficient 也是一种评估指标：

```python
def dice_coefficient(y1, y2):
  y1 = tf.flatten(y1)
  y2 = tf.flatten(y2)
  return (2. * tf.sum(y1 * y2) + smoothness) / (tf.sum(y1) + tf.sum(y2) + smoothness)
```

```python
def dice_coefficient_loss(y1, y2):
  return -dice_coefficient(y1, y2)
```

UNET 模型可以定义为：

```python
def preprocess(imgs):
  imgs_p = np.array((imgs.shape[0], image_height, image_width,
  dtype=np.uint8))
  for i in range(imgs.shape[0]):
    imgs_p[i] = resize(imgs[i], (image_width, image_height),
  preserve_range=True)
  imgs_p = imgs_p[..., np.newaxis]
  return imgs_p
```

```python
def convolution_layer(filters, kernel=(3,3), activation='relu',
  input_shape=None):
  if input_shape is None:
    return tf.keras.layers.Conv2D(
      filters=filters,
      kernel=kernel,
      activation=activation)
  else:
    return tf.keras.layers.Conv2D(
      filters=filters,
      kernel=kernel,
      activation=activation,
      input_shape=input_shape)
```

```python
def concatenated_de_convolution_layer(filters):
  return tf.keras.layers.concatenate([
    tf.keras.layers.Conv2DTranspose(
      filters=filters,
      kernel=(2, 2),
      strides=(2, 2),
      padding='same'
    ], axis=3])
```

所有的层都被拼接并使用，如下代码所示：

```python
unet = tf.keras.models.Sequential()
inputs = tf.keras.layers.Input((image_height, image_width, 1))
input_shape = (image_height, image_width, 1)
unet.add(convolution_layer(32, input_shape=input_shape))
unet.add(convolution_layer(32))
unet.add(pooling_layer())
```

```python
unet.add(convolution_layer(64))
unet.add(convolution_layer(64))
unet.add(pooling_layer())
```

```python
unet.add(convolution_layer(128))
unet.add(convolution_layer(128))
unet.add(pooling_layer())
```

```python
unet.add(convolution_layer(256))
unet.add(convolution_layer(256))
unet.add(pooling_layer())
```

```python
unet.add(convolution_layer(512))
unet.add(convolution_layer(512))
```

层被拼接在一起，并使用了反卷积层：

```python
unet.add(concatenated_de_convolution_layer(256))
unet.add(convolution_layer(256))
unet.add(convolution_layer(256))
```

```python
unet.add(concatenated_de_convolution_layer(128))
unet.add(convolution_layer(128))
unet.add(convolution_layer(128))
```

```python
unet.add(concatenated_de_convolution_layer(64))
unet.add(convolution_layer(64))
unet.add(convolution_layer(64))
```

```python
unet.add(concatenated_de_convolution_layer(32))
unet.add(convolution_layer(32))
unet.add(convolution_layer(32))
```

```python
unet.add(convolution_layer(1, kernel=(1, 1), activation='sigmoid'))
```

unet.compile(optimizer=tf.keras.optimizers.Adam(lr=1e-5),

loss=dice_coefficient_loss,

metrics=[dice_coefficient])

接下来，可以使用以下代码利用图像进行模型训练：

```python
x_train, y_train_mask = load_train_data()

x_train = preprocess(x_train)
y_train_mask = preprocess(y_train_mask)

x_train = x_train.astype('float32')
mean = np.mean(x_train)
std = np.std(x_train)

x_train -= mean
x_train /= std

y_train_mask = y_train_mask.astype('float32')
y_train_mask /= 255.

unet.fit(x_train, y_train_mask, batch_size=32, epochs=20, verbose=1,
shuffle=True,
validation_split=0.2)

x_test, y_test_mask = load_test_data()
x_test = preprocess(x_test)

x_test = x_test.astype('float32')
x_test -= mean
x_test /= std

y_test_pred = unet.predict(x_test, verbose=1)

for image, image_id in zip(y_test_pred, y_test_mask):
    image = (image[:, :, :, 0] * 255).astype(np.uint8)
    imsave(os.path.join(work_dir, str(image_id) + '.png'), image)
```

图像可以进行预处理并使用。现在可以对图像进行训练和测试。当模型被训练时，分割产生了良好的结果，如下：

![](img/48c861eac4dc634fbf2a09fdbe884beb_165_0.png)

我们训练了一个可以分割医学图像的模型。该算法适用于多种场景。在下一节中，我们将学习如何分割卫星图像。

## 分割卫星图像

在本节中，我们将使用摄影与遥感学会（ISPRS）提供的数据集。该数据集包含了波斯坦的图像，分辨率为5厘米。这些图像还附带了红外数据和高度轮廓。图像关联有六个标签：

- 建筑
- 植物
- 树
- 车辆
- 杂物
- 不透水

总共提供了38幅图像，大小为6000x6000的斑块。请访问页面 http://www.isprs.org/commissions/comm3/wg4/data-request-form2.html 并填写表单。选择以下选项：

- 你对哪些数据集感兴趣？
- [ ] Valhingen
- [ ] Toronto
- [x] Potsdam
- 你对检测/重建基准还是语义标注基准感兴趣？
- [ ] 检测或重建
- [x] 语义标注
- [ ] 两

提交表单后将发送电子邮件

## 用于分割的 FCN

分析图像时，我们的注意力会被图像中的某些实例吸引。因此需要将这些实例从图像的其他部分分割出来。这种从其余部分分离所需信息的过程广泛被称为`实例分割`（segmenting instances）。在此过程中，首先获取输入图像，然后定位物体的边界框，最后为每个物体预测像素级掩码。对于每个类别，都会计算像素级准确率。存在多种分割实例的算法。最近的算法之一是 He 等人提出的 Mask RCNN 算法（https://arxiv.org/pdf/1703.06870.pdf）。下图展示了 Mask R-CNN 的架构：

![](img/48c861eac4dc634fbf2a09fdbe884beb_168_3.png)

经 He 等人许可复自

# 语义分割

第5章

该架构与 R-CNN 类似，增加了分割功能。这是一个具有端到端训练的多阶段网络。区域建议（region proposals）是可以学习的。网络被分为两个部分，一个用于检测，另一个用于分类评分。结果非常出色，如下：



![](img/ab452ecf572a1f1372915be13bd8088f_297_0.png)

图 9.17 层 block2_sepconv1、block4_sepconv1 和 block8_sepconv1 的一些滤波模式

## 9.4.3 可视化类激活热图

我们将介绍最后一种可视化技术——这种技术有助于理解给定图像的哪些部分导致卷积网络做出最终的分类决策。这对于“调试”卷积网络的决策过程很有帮助，特别是在分类出错的情况下（这一问题领域称为模型可解释性）。它还可以让你在图像中定位特定对象。

这一技术类别被称为类激活图（CAM）可视化，它由生成输入图像上的类激活热图组成。类激活热图是与特定输出类相关的二维分数网格，针对任何输入图像中的每个位置计算得出，指示每个位置相对于所考虑类的重要性。例如，给定一张输入到猫狗卷积网络中的图像，CAM 可视化将允许你为类“猫”生成一个热图，指示图像不同部分有多猫，还可以为类“狗”生成一个热图，指示图像部分有多像狗。

我们将使用的具体实现是一篇标题为“Grad-CAM：基于梯度的定位的深度网络可视化解释”的文章中描述的实现。

Grad-CAM 的做法是：给定一张输入图像，取某卷积层的输出特征图，并用类相对于该通道的梯度来加权该特征图中的每个通道。直观地理解这个技巧的一种方法是：想象你正在用“每个通道相对于该类的重要性”来加权一个空间图，该图表示“输入图像激活不同通道的强度”，结果得到一个空间图，表示“输入图像激活该类的强度”。

让我们使用预训练的 Xception 模型来演示此技术。

### 清单 9.20 加载带有预训练权重的 Xception 网络

```python
model = keras.applications.xception.Xception(weights="imagenet")
```

请注意，我们包含顶部的全连接分类器；在所有以前的情况下，我们都丢弃了它。

考虑图 9.18 中所示的两头非洲大象的图像，可能是一头母象和它的幼崽，正在草原上漫步。让我们将此图像转换为 Xception 模型可以读取的内容：该模型在大小为 299 × 299 的图像上进行了训练，预处理按照几个规则进行，这些规则封装在 `keras.applications.xception.preprocess_input` 实用函数中。因此我们需要加载图像，将其调整大小为 299 × 299，将其转换为 NumPy float32 张量，并应用这些预处理规则。

### 清单 9.21 为 Xception 预处理输入图像

```python
img_path = keras.utils.get_file(
    fname="elephant.jpg",
    origin="https://img-datasets.s3.amazonaws.com/elephant.jpg")
def get_img_array(img_path, target_size):
    img = keras.utils.load_img(img_path, target_size=target_size)
    array = keras.utils.img_to_array(img)
    array = np.expand_dims(array, axis=0)
    array = keras.applications.xception.preprocess_input(array)
    return array
img_array = get_img_array(img_path, target_size=(299, 299))
```

- 返回一个形状为 (299, 299, 3) 的 float32 NumPy 数组。
- 下载图像并将其本地存储在路径 img_path 下。
- 返回一个大小为 299 x 299 的 Python Imaging Library (PIL) 图像。
- 添加一个维度以将数组转换为大小为 (1, 299, 299, 3) 的批次。
- 预处理批次（这会执行逐通道颜色归一化）。

![](img/ab452ecf572a1f1372915be13bd8088f_299_0.png)

图 9.18 非洲大象测试图片

现在你可以在图像上运行预训练网络，并将其预测向量解码回人类可读的格式：

```python
>>> preds = model.predict(img_array)
>>> print(keras.applications.xception.decode_predictions(preds, top=3)[0])
[('n02504458', 'African_elephant', 0.8699266),
 ('n01871265', 'tusker', 0.076968715),
 ('n02504013', 'Indian_elephant', 0.02353728)]
```

该图像预测的前三个类如下：

- 非洲大象（概率为 87%）
- 长齿象（概率为 7%）
- 亚洲象（概率为 2%）

网络已将图像识别为包含不确定数量的非洲大象。预测向量中激活程度最高的条目是对应于“非洲大象”类的条目，索引为 386：

```python
>>> np.argmax(preds[0])
386
```

为了可视化图像的哪些部分最像非洲大象，让我们设置 Grad-CAM 过程。

首先，我们创建一个将输入图像映射到最后一个卷积层激活值的模型。

### 清单 9.22 设置返回最后卷积输出的模型

```python
last_conv_layer_name = "block14_sepconv2_act"
classifier_layer_names = [
    "avg_pool",
    "predictions",
]
last_conv_layer = model.get_layer(last_conv_layer_name)
last_conv_layer_model = keras.Model(model.inputs, last_conv_layer.output)
```

其次，我们创建一个将最后一个卷积层的激活值映射到最终类预测的模型。

### 清单 9.23 在最后卷积输出之上重新应用分类器

```python
classifier_input = keras.Input(shape=last_conv_layer.output.shape[1:])
x = classifier_input
for layer_name in classifier_layer_names:
    x = model.get_layer(layer_name)(x)
classifier_model = keras.Model(classifier_input, x)
```

然后我们计算输入图像的最高预测类相对于最后一个卷积层激活值的梯度。

### 清单 9.24 检索最高预测类的梯度

```python
import tensorflow as tf

with tf.GradientTape() as tape:
    last_conv_layer_output = last_conv_layer_model(img_array)
    tape.watch(last_conv_layer_output)
    preds = classifier_model(last_conv_layer_output)
    top_pred_index = tf.argmax(preds[0])
    top_class_channel = preds[:, top_pred_index]

grads = tape.gradient(top_class_channel, last_conv_layer_output)
```

现在我们对梯度张量应用池化和重要性加权，以获得类激活热图。

### 清单 9.25 梯度池化和通道重要性加权

```python
pooled_grads = tf.reduce_mean(grads, axis=(0, 1, 2)).numpy()
last_conv_layer_output = last_conv_layer_output.numpy()[0]
for i in range(pooled_grads.shape[-1]):
    last_conv_layer_output[:, :, i] *= pooled_grads[i]
heatmap = np.mean(last_conv_layer_output, axis=-1)
```

这是一个向量，每个条目是给定通道的梯度平均强度。它量化了每个通道相对于最高预测类的重要性。

将最后一个卷积层输出中的每个通道乘以“该通道有多重要”。

结果特征图的通道平均值是我们的类激活热图。

出于可视化目的，我们还将热图归一化到 0 和 1 之间。结果如图 9.19 所示。

### 清单 9.26 热图后处理

```python
heatmap = np.maximum(heatmap, 0)
heatmap /= np.max(heatmap)
plt.matshow(heatmap)
```

![](img/ab452ecf572a1f1372915be13bd8088f_301_0.png)

最后，让我们生成一张将原始图像叠加在我们刚刚获得的热图之上的图像（参见图 9.20）。

### 清单 9.27 将热图叠加到原始图片上

```python
import matplotlib.cm as cm
img = keras.utils.load_img(img_path)
img = keras.utils.img_to_array(img)
```

加载原始图像。

将热图重新缩放到 0-255 范围。

```python
heatmap = np.uint8(255 * heatmap)
jet = cm.get_cmap("jet")
jet_colors = jet(np.arange(256))[:, :3]
jet_heatmap = jet_colors[heatmap]
```

使用“jet”颜色映射重新着色热图。

```python
jet_heatmap = keras.utils.array_to_img(jet_heatmap)
jet_heatmap = jet_heatmap.resize((img.shape[1], img.shape[0]))
jet_heatmap = keras.utils.img_to_array(jet_heatmap)
```

创建包含重新着色热图的图像。

```python
superimposed_img = jet_heatmap * 0.4 + img
superimposed_img = keras.utils.array_to_img(superimposed_img)
```

以 40% 的不透明度叠加热图和原始图像。

```python
save_path = "elephant_cam.jpg"
superimposed_img.save(save_path)
```

保存叠加后的图像。

![](img/ab452ecf572a1f1372915be13bd8088f_302_0.png)

图 9.20 测试图片上的非洲大象类激活热图


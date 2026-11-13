

- 可视化图像中类激活的热图——有助于理解图像的哪些部分被识别为属于给定类别，从而使您能够定位图像中的对象

对于第一种方法——激活可视化——我们将使用在第 8.2 节中从头开始训练的用于猫狗分类问题的小型卷积网络。对于接下来的两种方法，我们将使用预训练的 Xception 模型。

## 9.4.1 可视化中间激活

可视化中间激活包括显示模型中各种卷积层和池化层在给定输入下返回的值（图层的输出通常称为其 *激活*，即激活函数的输出）。这能让你了解输入是如何被分解为网络学习到的不同滤波器的。我们想要可视化具有三个维度的特征图：宽度、高度和深度（通道）。每个通道编码相对独立的特征，因此可视化这些特征图的适当方法是将每个通道的内容作为 2D 图像独立绘制。让我们从加载在第 8.2 节中保存的模型开始：

```
>>> from tensorflow import keras
>>> model = keras.models.load_model(
...     "convnet_from_scratch_with_augmentation.keras")
>>> model.summary()
Model: "model_1"
```

| 层 (类型) | 输出形状 | 参数数量 |
| :--- | :--- | :--- |
| input_2 (InputLayer) | [(None, 180, 180, 3)] | 0 |
| sequential (Sequential) | (None, 180, 180, 3) | 0 |
| rescaling_1 (Rescaling) | (None, 180, 180, 3) | 0 |
| conv2d_5 (Conv2D) | (None, 178, 178, 32) | 896 |
| max_pooling2d_4 (MaxPooling2D) | (None, 89, 89, 32) | 0 |
| conv2d_6 (Conv2D) | (None, 87, 87, 64) | 18496 |
| max_pooling2d_5 (MaxPooling2D) | (None, 43, 43, 64) | 0 |
| conv2d_7 (Conv2D) | (None, 41, 41, 128) | 73856 |
| max_pooling2d_6 (MaxPooling2D) | (None, 20, 20, 128) | 0 |
| conv2d_8 (Conv2D) | (None, 18, 18, 256) | 295168 |
| max_pooling2d_7 (MaxPooling2D) | (None, 9, 9, 256) | 0 |
| conv2d_9 (Conv2D) | (None, 7, 7, 256) | 590080 |
| flatten_1 (Flatten) | (None, 12544) | 0 |
| dropout (Dropout) | (None, 12544) | 0 |
| dense_1 (Dense) | (None, 1) | 12545 |

总参数：991,041  
可训练参数：991,041  
不可训练参数：0  

接下来，我们将获取一张输入图片——一张猫的照片，该照片不是网络训练所用图片的一部分。

### 列表 9.6 预处理单张图片

```
from tensorflow import keras
import numpy as np

img_path = keras.utils.get_file(
    fname="cat.jpg",
    origin="https://img-datasets.s3.amazonaws.com/cat.jpg")

def get_img_array(img_path, target_size):
    img = keras.utils.load_img(
        img_path, target_size=target_size)
    array = keras.utils.img_to_array(img)
    array = np.expand_dims(array, axis=0)
    return array

img_tensor = get_img_array(img_path, target_size=(180, 180))
```

为数组增加一个维度，将其转换为单个样本的“批次”。其形状现为 (1, 180, 180, 3)。

让我们显示这张图片（见图 9.12）。

### 列表 9.7 显示测试图片

```
import matplotlib.pyplot as plt
plt.axis("off")
plt.imshow(img_tensor[0].astype("uint8"))
plt.show()
```

为了提取我们想查看的特征图，我们将创建一个 Keras 模型，该模型将图像批次作为输入，并输出所有卷积层和池化层的激活值。

![](img/ab452ecf572a1f1372915be13bd8088f_288_0.png)

图 9.12 测试用的猫图片

### 列表 9.8 实例化返回层激活值的模型

```
from tensorflow.keras import layers

layer_outputs = []
layer_names = []
for layer in model.layers:
    if isinstance(layer, (layers.Conv2D, layers.MaxPooling2D)):
        layer_outputs.append(layer.output)
        layer_names.append(layer.name)
activation_model = keras.Model(inputs=model.input, outputs=layer_outputs)
```

当输入一张图片时，该模型将以列表形式返回原始模型中各层激活值的输出。这是你在本书中实际遇到的第一个多输出模型（自第 7 章学习它们以来）；到目前为止，你见过的模型都恰好有一个输入和一个输出。这个模型有一个输入和九个输出：每个层激活值对应一个输出。

### 列表 9.9 使用模型计算层激活值

```
activations = activation_model.predict(img_tensor)
```

例如，这是猫图片输入时第一个卷积层的激活值：

>>> first_layer_activation = activations[0]
>>> print(first_layer_activation.shape)
(1, 178, 178, 32)

这是一个具有 32 个通道的 178 × 178 特征图。让我们尝试绘制原始模型第一层激活值的第五个通道（见图 9.13）。

### 列表 9.10 可视化第五个通道

```
import matplotlib.pyplot as plt
plt.matshow(first_layer_activation[0, :, :, 5], cmap="viridis")
```

![](img/ab452ecf572a1f1372915be13bd8088f_289_0.png)

图 9.13 测试猫图片中第一层激活值的第五个通道

该通道似乎编码了一个斜边缘检测器——但请注意，你自己的通道可能会有所不同，因为卷积层学习到的特定滤波器并非确定性的。

现在，让我们绘制网络中所有激活值的完整可视化（见图 9.14）。我们将提取并绘制每个层激活值中的每个通道，并将结果堆叠成一个大网格，通道并排堆叠。

### 列表 9.11 可视化每个中间激活值中的每个通道

```
images_per_row = 16
for layer_name, layer_activation in zip(layer_names, activations):
    n_features = layer_activation.shape[-1]
    size = layer_activation.shape[1]
    n_cols = n_features // images_per_row
    display_grid = np.zeros(((size + 1) * n_cols - 1,
                             (images_per_row * size + 1) * (size + 1) - 1))
    for col in range(n_cols):
        for row in range(images_per_row):
            channel_index = col * images_per_row + row
            channel_image = layer_activation[0, :, :, channel_index].copy()
```

遍历激活值（以及相应层的名称）。

层激活值的形状为 (1, size, size, n_features)。

准备一个空网格，用于显示此激活值中的所有通道。

这是一个单通道（或特征）。

将通道值归一化到 [0, 255] 范围内。全零通道保持为零。

```
if channel_image.sum() != 0:
    channel_image -= channel_image.mean()
    channel_image /= channel_image.std()
    channel_image *= 64
    channel_image += 128
channel_image = np.clip(channel_image, 0, 255).astype("uint8")
display_grid[
    col * (size + 1) : (col + 1) * size + col,
    row * (size + 1) : (row + 1) * size + row] = channel_image
scale = 1. / size
plt.figure(figsize=(scale * display_grid.shape[1],
                    scale * display_grid.shape[0]))
plt.title(layer_name)
plt.grid(False)
plt.axis("off")
plt.imshow(display_grid, aspect="auto", cmap="viridis")
```

将通道矩阵放置在我们准备的空网格中。

显示该层的网格。

![](img/ab452ecf572a1f1372915be13bd8088f_290_0.png)

图 9.14 测试猫图片中每个层激活值的每个通道

这里有几点需要注意：

- 第一层充当各种边缘检测器的集合。在此阶段，激活值保留了初始图片中几乎所有的信息。
- 随着网络深度的增加，激活值变得越来越抽象，越来越难以在视觉上解释。它们开始编码更高级别的概念，例如“猫耳朵”和“猫眼睛”。更深层的表示携带的关于图像视觉内容的信息越来越少，而与图像类别相关的信息越来越多。
- 随着层数加深，激活值的稀疏性增加：在第一层中，输入图片激活了几乎所有滤波器，但在随后的层中，越来越多的滤波器为空白。这意味着滤波器编码的模式在输入图片中未被找到。

我们刚刚证实了深度神经网络学习到的表示的一个重要普遍特征：层提取的特征随层数加深而变得越来越抽象。更高层的激活值携带的关于所见特定输入的信息越来越少，而关于目标（在此例中为图像的类别：猫或狗）的信息越来越多。深度神经网络实际上充当一个 *信息蒸馏管道*，原始数据输入（在此例中为 RGB 图片）并反复转换，以滤除无关信息（例如，图片的特定视觉外观），并放大和精炼有用信息（例如，图像的类别）。

这与人类和动物感知世界的方式类似：在观察一个场景几秒钟后，人类可以记住其中存在哪些抽象对象（自行车、树木），但无法记住这些对象的具体外观。事实上，如果你试图从记忆中画一辆普通的自行车，你很可能画得远远不准确，尽管你一生中见过成千上万辆自行车（例如，参见图 9.15）。现在就试一下：这种效果绝对是真实的。你的大脑已经学会了完全抽象其视觉输入——将其转换

![](img/ab452ecf572a1f1372915be13bd8088f_291_0.png)

图 9.15 左：凭记忆绘制自行车的尝试。右：示意图自行车应有的样子。


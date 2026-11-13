

![](img/ab452ecf572a1f1372915be13bd8088f_265_0.png)

![](img/ab452ecf572a1f1372915be13bd8088f_265_1.png)

图 9.2 语义分割与实例分割

对应输入图像中像素的。在我们的例子中，分割掩码的像素可以采用以下三个整数值之一：

- 1（前景）
- 2（背景）
- 3（轮廓）

让我们先通过 `wget` 和 `tar` 实用程序下载并解压数据集：

```
!wget http://www.robots.ox.ac.uk/~vgg/data/pets/data/images.tar.gz
!wget http://www.robots.ox.ac.uk/~vgg/data/pets/data/annotations.tar.gz
!tar -xf images.tar.gz
!tar -xf annotations.tar.gz
```

输入图片存储为 `images/` 文件夹中的 JPG 文件（例如 `images/Abyssinian_1.jpg`），相应的分割掩码存储为 `annotations/trimaps/` 文件夹中同名的 PNG 文件（例如 `annotations/trimaps/Abyssinian_1.png`）。

让我们准备输入文件路径列表，以及相应的掩码文件路径列表：

```
import os

input_dir = "images/"
target_dir = "annotations/trimaps/"

input_img_paths = sorted(
    [os.path.join(input_dir, fname)
     for fname in os.listdir(input_dir)
     if fname.endswith(".jpg")])

target_paths = sorted(
    [os.path.join(target_dir, fname)
    for fname in os.listdir(target_dir)
    if fname.endswith(".png") and not fname.startswith(".")])
```

那么，这些输入及其掩码长什么样？让我们快速看一下。这是一张示例图片（参见图 9.3）：

```
import matplotlib.pyplot as plt
from tensorflow.keras.utils import load_img, img_to_array

plt.axis("off")
plt.imshow(load_img(input_img_paths[9]))
```

![](img/ab452ecf572a1f1372915be13bd8088f_266_0.png)

图 9.3 示例图片

这是它对应的目标（参见图 9.4）：

原始标签为 1、2 和 3。我们减去 1，使标签范围变为 0 到 2，然后乘以 127，使标签变为 0（黑色）、127（灰色）、254（接近白色）。

```
def display_target(target_array):
    normalized_array = (target_array.astype("uint8") - 1) * 127
    plt.axis("off")
    plt.imshow(normalized_array[:, :, 0])
```

```
img = img_to_array(load_img(target_paths[9], color_mode="grayscale"))
display_target(img)
```

我们使用 `color_mode="grayscale"`，以便加载的图像被视为只有一个颜色通道。

![](img/ab452ecf572a1f1372915be13bd8088f_267_0.png)

图 9.4 对应的目标掩码

接下来，让我们将输入和目标加载到两个 NumPy 数组中，并将数组分割为训练集和验证集。由于数据集非常小，我们可以直接将所有内容加载到内存中：

```
import numpy as np
import random

img_size = (200, 200)
num_imgs = len(input_img_paths)

random.Random(1337).shuffle(input_img_paths)
random.Random(1337).shuffle(target_paths)

def path_to_input_image(path):
    return img_to_array(load_img(path, target_size=img_size))

def path_to_target(path):
    img = img_to_array(
        load_img(path, target_size=img_size, color_mode="grayscale"))
    img = img.astype("uint8") - 1
    return img

input_imgs = np.zeros((num_imgs,) + img_size + (3,), dtype="float32")
targets = np.zeros((num_imgs,) + img_size + (1,), dtype="uint8")
for i in range(num_imgs):
    input_imgs[i] = path_to_input_image(input_img_paths[i])
    targets[i] = path_to_target(target_paths[i])

num_val_samples = 1000
train_input_imgs = input_imgs[:-num_val_samples]
train_targets = targets[:-num_val_samples]
val_input_imgs = input_imgs[-num_val_samples:]
val_targets = targets[-num_val_samples:]
```

我们将所有内容调整为 200 x 200。

数据中的样本总数

随机打乱文件路径（它们最初是按品种排序的）。在两条语句中都使用相同的种子（1337），以确保输入路径和目标路径保持相同的顺序。

减去 1，使我们的标签变为 0、1 和 2。

预留 1,000 个样本用于验证。

将数据分割为训练集和验证集。

将所有图像加载到 `input_imgs` `float32` 数组及其掩码加载到 `targets` `uint8` 数组中（顺序相同）。输入包含三个通道（RGB 值），而目标包含一个通道（包含整数标签）。

现在是时候定义我们的模型了：

```
from tensorflow import keras
from tensorflow.keras import layers

def get_model(img_size, num_classes):
    inputs = keras.Input(shape=img_size + (3,))
    x = layers.Rescaling(1./255)(inputs)

    x = layers.Conv2D(64, 3, strides=2, activation="relu", padding="same")(x)
    x = layers.Conv2D(64, 3, activation="relu", padding="same")(x)
    x = layers.Conv2D(128, 3, strides=2, activation="relu", padding="same")(x)
    x = layers.Conv2D(128, 3, activation="relu", padding="same")(x)
    x = layers.Conv2D(256, 3, strides=2, activation="relu", padding="same")(x)
    x = layers.Conv2D(256, 3, activation="relu", padding="same")(x)

    x = layers.Conv2DTranspose(256, 3, activation="relu", padding="same")(x)
    x = layers.Conv2DTranspose(
        256, 3, activation="relu", padding="same", strides=2)(x)
    x = layers.Conv2DTranspose(128, 3, activation="relu", padding="same")(x)
    x = layers.Conv2DTranspose(
        128, 3, activation="relu", padding="same", strides=2)(x)
    x = layers.Conv2DTranspose(64, 3, activation="relu", padding="same")(x)
    x = layers.Conv2DTranspose(
        64, 3, activation="relu", padding="same", strides=2)(x)

    outputs = layers.Conv2D(num_classes, 3, activation="softmax",
                            padding="same")(x)

    model = keras.Model(inputs, outputs)
    return model

model = get_model(img_size=img_size, num_classes=3)
model.summary()
```

这是 `model.summary()` 调用的输出：

| 层 (类型) | 输出形状 | 参数量 |
|---|---|---|
| input_1 (InputLayer) | [(None, 200, 200, 3)] | 0 |
| rescaling (Rescaling) | (None, 200, 200, 3) | 0 |
| conv2d (Conv2D) | (None, 100, 100, 64) | 1792 |
| conv2d_1 (Conv2D) | (None, 100, 100, 64) | 36928 |
| conv2d_2 (Conv2D) | (None, 50, 50, 128) | 73856 |
| conv2d_3 (Conv2D) | (None, 50, 50, 128) | 147584 |
| conv2d_4 (Conv2D) | (None, 25, 25, 256) | 295168 |
| conv2d_5 (Conv2D) | (None, 25, 25, 256) | 590080 |
| conv2d_transpose (Conv2DTranspose) | (None, 25, 25, 256) | 590080 |
| conv2d_transpose_1 (Conv2DTranspose) | (None, 50, 50, 256) | 590080 |
| conv2d_transpose_2 (Conv2DTranspose) | (None, 50, 50, 128) | 295040 |
| conv2d_transpose_3 (Conv2DTranspose) | (None, 100, 100, 128) | 147584 |
| conv2d_transpose_4 (Conv2DTranspose) | (None, 100, 100, 64) | 73792 |
| conv2d_transpose_5 (Conv2DTranspose) | (None, 200, 200, 64) | 36928 |
| conv2d_6 (Conv2D) | (None, 200, 200, 3) | 1731 |

总参数量: 2,880,643
可训练参数量: 2,880,643
不可训练参数量: 0

模型的前半部分非常类似于你用于图像分类的那种卷积网络：一堆 `Conv2D` 层，滤波器尺寸逐渐增加。我们将图像下采样三次，每次缩小两倍，最终得到大小为 `(25, 25, 256)` 的激活。前半部分的目的是将图像编码为更小的特征图，其中每个空间位置（或像素）包含原始图像大块空间区域的信息。你可以将其理解为一种压缩。

这个模型前半部分与你之前见过的分类模型之间的一个重要区别在于我们进行下采样的方式：在上一章的分类卷积网络中，我们使用 `MaxPooling2D` 层来下采样特征图。在这里，我们通过在每隔一个卷积层中添加步幅来进行下采样（如果你不记得卷积步幅的工作原理，请参见第 8.1.1 节中的“理解卷积步幅”）。我们这样做是因为，在图像分割的情况下，我们非常关心图像中信息的空间位置，因为我们需要将每像素目标掩码作为模型的输出。当你执行 2 × 2 最大池化时，你会完全破坏每个池化窗口内的位置信息：你每个窗口只返回一个标量值，完全不知道该值来自窗口中的四个位置中的哪一个。因此，虽然最大池化层在分类任务中表现良好，但对于分割任务来说会对我们造成相当大的不利影响。与此同时，带步幅的卷积在下采样特征图的同时保留位置信息，效果更好。在本书中，你会发现我们倾向于在任何关心特征位置的模型中使用步幅而不是最大池化，例如第 12 章中的生成模型。

模型的后半部分是一堆 `Conv2DTranspose` 层。那些是什么？好吧，模型前半部分的输出是一个形状为 `(25, 25, 256)` 的特征图，


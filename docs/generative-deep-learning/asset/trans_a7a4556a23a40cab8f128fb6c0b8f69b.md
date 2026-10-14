
本章首先将阐述 GAN 的理论基础，然后我们将了解如何使用 Keras 构建自己的 GAN。

## 引言

让我们从一个简短的故事开始，以说明 GAN 训练过程中使用的一些基本概念。

## Brickki 积木与伪造者

这是你担任 Brickki 质量控制主管的新工作的第一天，Brickki 是一家专门生产各种形状和尺寸的高质量建筑积木的公司（图 4-1）。

![](img/f0f0f5d89818fdddf117bbe758ac8143_122_0.png)

图 4-1. 生产多种不同形状和尺寸的砖块的公司的生产线（使用 Midjourney 创建）

你立即被告知生产线上出现的问题。竞争对手开始制造 Brickki 积木的仿制品，并找到了一种方法将其混入客户收到的袋子中。你决定成为区分仿制积木和真品的专家，以便在积木交给客户之前在生产线上拦截伪造的积木。随着时间的推移，通过倾听客户反馈，你逐渐变得更擅长识别假货。

伪造者对此并不高兴——他们对你提高的检测能力做出了反应，通过改变他们的伪造工艺，使得真砖和假砖之间的差异变得更难被你发现。

> 绝不轻言放弃，你重新训练自己以识别更复杂的假货，并努力领先伪造者一步。这一过程持续进行，伪造者不断迭代更新他们的砖块制造技术，而你则努力变得越来越擅长拦截他们的假货。
> 
> 随着每周的过去，区分真正的 Brickki 积木和伪造者制造的积木变得越来越困难。似乎这种简单的猫鼠游戏足以推动伪造质量和检测质量的显著提升。

Brickki 积木与伪造者的故事描述了生成对抗网络的训练过程。

GAN 是生成器和判别器之间的一场较量。生成器试图将随机噪声转换为看起来像是从原始数据集中采样的观测值，而判别器则试图预测一个观测值是否来自原始数据集还是生成器的伪造品。两个网络的输入和输出示例如图 4-2 所示。

![](img/f0f0f5d89818fdddf117bbe758ac8143_123_0.png)

图 4-2. GAN 中两个网络的输入和输出

在过程开始时，生成器输出嘈杂的图像，而判别器随机预测。GAN 的关键在于我们如何交替训练这两个网络，这样随着生成器变得更擅长欺骗判别器，判别器必须适应以维持其正确识别哪些观测值是假的能力。这促使生成器找到新的欺骗判别器的方法，循环就此继续。

## 深度卷积 GAN（DCGAN）

为了实际操作，让我们开始在 Keras 中构建第一个 GAN，用来生成砖块的图片。

我们将紧密遵循 GAN 领域最早的重要论文之一，“使用深度卷积生成对抗网络进行无监督表示学习。”2 在这篇 2015 年的论文中，作者展示了如何构建深度卷积 GAN 来从各种数据集生成逼真的图像。他们还引入了若干改进，显著提升了生成图像的质量。

![](img/f0f0f5d89818fdddf117bbe758ac8143_124_0.png)

## 运行本例代码

本例的代码可在书籍仓库中的 notebooks/04_gan/01_dcgan/dcgan.ipynb Jupyter 笔记本中找到。

## 积木数据集

首先，你需要下载训练数据。我们将使用通过 Kaggle 可用的 LEGO 积木图像数据集。这是一个计算机渲染的包含 40,000 张 50 种不同玩具积木的照片图像集合，从多个角度拍摄。一些 Brickki 产品的示例图像如图 4-3 所示。

![](img/f0f0f5d89818fdddf117bbe758ac8143_124_1.png)

图 4-3. 来自积木数据集的图像示例

你可以通过在书籍仓库中运行 Kaggle 数据集下载脚本来下载数据集，如示例 4-1 所示。这将把图像和相应的元数据本地保存到 /data 文件夹。

### 示例 4-1. 下载积木数据集

```
bash scripts/download_kaggle_data.sh joosthazelzet lego-brick-images
```

我们使用 Keras 函数 image_dataset_from_directory 来创建一个指向图像存储目录的 TensorFlow 数据集，如示例 4-2 所示。这使我们能够仅在需要时（例如在训练期间）将图像批次读入内存，因此我们可以处理大型数据集，而不必担心将整个数据集装入内存。它还将图像调整为 64 × 64，并在像素值之间进行插值。

### 示例 4-2. 从目录中的图像文件创建 TensorFlow 数据集

```
train_data = utils.image_dataset_from_directory(
"/app/data/lego-brick-images/dataset/",
labels=None,
color_mode="grayscale",
image_size=(64, 64),
batch_size=128,
shuffle=True,
seed=42,
interpolation="bilinear",
)
```

原始数据按 [0, 255] 范围缩放以表示像素强度。在训练 GAN 时，我们将数据重新缩放到 [-1, 1] 范围，以便在生成器的最后一层使用 tanh 激活函数，这通常比 sigmoid 函数提供更强的梯度（示例 4-3）。

### 示例 4-3. 预处理积木数据集

```
def preprocess(img):
    img = (tf.cast(img, "float32") - 127.5) / 127.5
    return img
```

```
train = train_data.map(lambda x: preprocess(x))
```

现在让我们看看如何构建判别器。

## 判别器

判别器的目标是预测图像是真实的还是伪造的。这是一个监督图像分类问题，因此我们可以使用与第 2 章中使用的类似架构：堆叠的卷积层，带有一个输出节点。

我们将构建的判别器的完整架构如表 4-1 所示。

表 4-1. 判别器的模型摘要

| 层（类型） | 输出形状 | 参数数 |
|---|---|---|
| InputLayer | (None, 64, 64, 1) | 0 |
| Conv2D | (None, 32, 32, 64) | 1,024 |
| LeakyReLU | (None, 32, 32, 64) | 0 |
| Dropout | (None, 32, 32, 64) | 0 |
| Conv2D | (None, 16, 16, 128) | 131,072 |
| BatchNormalization | (None, 16, 16, 128) | 512 |
| LeakyReLU | (None, 16, 16, 128) | 0 |
| Dropout | (None, 16, 16, 128) | 0 |
| Conv2D | (None, 8, 8, 256) | 524,288 |
| BatchNormalization | (None, 8, 8, 256) | 1,024 |
| LeakyReLU | (None, 8, 8, 256) | 0 |
| Dropout | (None, 8, 8, 256) | 0 |
| Conv2D | (None, 4, 4, 512) | 2,097,152 |
| BatchNormalization | (None, 4, 4, 512) | 2,048 |
| LeakyReLU | (None, 4, 4, 512) | 0 |
| Dropout | (None, 4, 4, 512) | 0 |
| Conv2D | (None, 1, 1, 1) | 8,192 |
| Flatten | (None, 1) | 0 |

总参数数 2,765,312
可训练参数 2,763,520
非可训练参数 1,792

构建判别器的 Keras 代码在示例 4-4 中提供。

### 示例 4-4. 判别器

```
discriminator_input = layers.Input(shape=(64, 64, 1)) ①
x = layers.Conv2D(64, kernel_size=4, strides=2, padding="same", use_bias = False)(
    discriminator_input
) ②
x = layers.LeakyReLU(0.2)(x)
x = layers.Dropout(0.3)(x)
x = layers.Conv2D(
    128, kernel_size=4, strides=2, padding="same", use_bias = False
)(x)
x = layers.BatchNormalization(momentum = 0.9)(x)
x = layers.LeakyReLU(0.2)(x)
x = layers.Dropout(0.3)(x)
x = layers.Conv2D(
    256, kernel_size=4, strides=2, padding="same", use_bias = False
)(x)
x = layers.BatchNormalization(momentum = 0.9)(x)
x = layers.LeakyReLU(0.2)(x)
x = layers.Dropout(0.3)(x)
x = layers.Conv2D(
    512, kernel_size=4, strides=2, padding="same", use_bias = False
)(x)
x = layers.BatchNormalization(momentum = 0.9)(x)
x = layers.LeakyReLU(0.2)(x)
x = layers.Dropout(0.3)(x)
x = layers.Conv2D(
    1,
    kernel_size=4,
    strides=1,
    padding="valid",
    use_bias = False,
    activation = 'sigmoid'
)(x)
discriminator_output = layers.Flatten()(x) ③
```



生成器网络被训练得能够欺骗判别器网络，因此在训练过程中，它不断进化以生成越来越逼真的图像：即看起来与真实图像无法区分的人工图像，以至于判别器网络无法分辨两者（参见图 12.19）。与此同时，判别器不断适应生成器日益提升的能力，为生成图像设定了很高的真实性标准。训练结束后，生成器能够将其输入空间中的任何点转换成可信的图像。与 VAE 不同，这个潜在空间对有意义结构的显式保证较少；特别是，它不是连续的。

![](img/ab452ecf572a1f1372915be13bd8088f_426_0.png)

图 12.19 生成器将随机潜在向量转换为图像，而判别器试图区分真实图像和生成的图像。生成器被训练用来欺骗判别器。

值得注意的是，GAN 是一种系统，其优化最小值不是固定的，这与你在本书中遇到的任何其他训练设置都不同。通常，梯度下降是在静态损失景观中滚下山丘。但使用 GAN 时，每向山下迈一步，就会稍微改变整个景观。这是一个动态系统，优化过程寻求的不是最小值，而是两种力量之间的平衡。正因如此，GAN 臭名昭著地难以训练——要让 GAN 工作，需要对模型架构和训练参数进行大量仔细调整。

## 12.5.1 示意图 GAN 实现

本节将介绍如何在 Keras 中以最简形式实现 GAN。GAN 属于高级主题，因此深入探讨如生成图 12.20 中图像的 StyleGAN2 等架构的技术细节超出了本书的范围。本演示中将使用的具体实现是深度卷积 GAN（DCGAN）：一种非常基础的 GAN，其中生成器和判别器都是深度卷积网络。

![](img/ab452ecf572a1f1372915be13bd8088f_427_0.png)

图 12.20 潜在空间的居民。使用 StyleGAN2 模型由 https://thispersondoesnotexist.com 生成的图像。（图片版权：Phillip Wang 是该网站作者。所使用的模型是 Karras 等人的 StyleGAN2 模型，https://arxiv.org/abs/1912.04958。）

我们将在大规模名人面部属性数据集（称为 CelebA）的图像上训练我们的 GAN，该数据集包含 200,000 张名人面部（http://mmlab.ie.cuhk.edu.hk/projects/CelebA.html）。为加快训练速度，我们将图像大小调整为 64 × 64，因此我们将学习生成 64 × 64 的人类面部图像。

从示意图来看，GAN 如下所示：

- 生成器网络将形状为 (`latent_dim`,) 的向量映射为形状为 (64, 64, 3) 的图像。
- 判别器网络将形状为 (64, 64, 3) 的图像映射为一个二元分数，用于估计图像为真实图像的概率。
- gan 网络将生成器和判别器串联在一起：`gan(x) = discriminator(generator(x))`。因此，这个 gan 网络将潜在空间向量映射为判别器对这些由生成器解码的潜在向量的现实性评估。
- 我们使用真实图像和假图像的示例以及 "real"/"fake" 标签来训练判别器，就像训练任何常规图像分类模型一样。
- 要训练生成器，我们使用生成器权重相对于 `gan` 模型损失的梯度。这意味着在每一步，我们都会沿着使判别器更有可能将生成器解码的图像分类为 "real" 的方向移动生成器的权重。换句话说，我们训练生成器去欺骗判别器。

## 12.5.2 一揽子技巧

训练 GAN 和调整 GAN 实现的过程臭名昭著地困难。有许多已知技巧你应该牢记。与深度学习中的大多数事物一样，这更像是炼金术而非科学：这些技巧是启发式方法，而非有理论支持的指导方针。它们得到了对手头现象的一定直观理解的支持，并且已知在经验上效果很好，尽管不一定在每种情况下都有效。

以下是本节中 GAN 生成器和判别器实现所使用的一些技巧。这并非 GAN 相关技巧的详尽列表；你将在 GAN 文献中发现更多：

- 在判别器中，我们使用步幅而非池化来下采样特征图，就像在 VAE 编码器中所做的那样。
- 我们从潜在空间中使用 *正态分布*（高斯分布）而非均匀分布来采样点。
- 随机性有助于诱导鲁棒性。由于 GAN 训练会导致动态平衡，GAN 很可能会以各种方式陷入困境。在训练期间引入随机性有助于防止这种情况。我们通过向判别器的标签添加随机噪声来引入随机性。
- 稀疏梯度可能会阻碍 GAN 训练。在深度学习中，稀疏性通常是一种可取的属性，但在 GAN 中不是。两种因素可能导致梯度稀疏：最大池化操作和 `relu` 激活。与使用最大池化不同，我们建议使用带步幅的卷积进行下采样，并建议使用 `LeakyReLU` 层代替 `relu` 激活。它与 `relu` 类似，但通过允许较小的负激活值来放松稀疏性约束。
- 在生成的图像中，常见的棋盘状伪影是由生成器中像素空间覆盖不均匀引起的（参见图 12.21）。为修复此问题，每当在生成器和判别器中同时使用带步幅的 `Conv2DTranspose` 或 `Conv2D` 时，我们都会使用能被步幅大小整除的核大小。

![](img/ab452ecf572a1f1372915be13bd8088f_428_0.png)

图 12.21 步幅和核大小不匹配导致的棋盘状伪影，导致像素空间覆盖不均匀：这是 GAN 的众多陷阱之一。

## 12.5.3 获取 CelebA 数据集

你可以手动从网站下载数据集：http://mmlab.ie.cuhk.edu.hk/projects/CelebA.html。如果你使用 Colab，可以运行以下命令从 Google Drive 下载数据并解压缩。

### 代码清单 12.30 获取 CelebA 数据

```
!mkdir celeba_gan
!gdown --id 107m1010EJjLE5QxXLZiM9FpjSj70je684 -O celeba_gan/data.zip
!unzip -qq celeba_gan/data.zip -d celeba_gan
```

将解压缩后的图像放入目录后，你可以使用 image_dataset_from_directory 将其转换为数据集。由于我们只需要图像——没有标签——我们将指定 label_mode=None。

### 代码清单 12.31 从图像目录创建数据集

```
from tensorflow import keras
dataset = keras.utils.dataset_from_directory(
    "celeba_gan",
    label_mode=None,
    image_size=(64, 64),
    batch_size=32,
    smart_resize=True)
```

最后，让我们将图像重新缩放到 [0-1] 范围。

### 代码清单 12.32 重新缩放图像

```
dataset = dataset.map(lambda x: x / 255.)
```

你可以使用以下代码显示示例图像。

### 代码清单 12.33 显示第一张图像

```
import matplotlib.pyplot as plt
for x in dataset:
    plt.axis("off")
    plt.imshow((x.numpy() * 255).astype("int32")[0])
    break
```

## 12.5.4 判别器

首先，我们将开发一个判别器模型，它将候选图像（真实或合成）作为输入，并将其分类为两个类别之一：“生成的图像”或“来自训练集的真实图像”。GAN 中常见的许多问题之一是，生成器会卡在看起来像噪声的生成图像上。一个可能的解决方案是在判别器中使用 dropout，因此我们将在这里使用。

### 代码清单 12.34 GAN 判别器网络

```
from tensorflow.keras import layers

discriminator = keras.Sequential(
[
    keras.Input(shape=(64, 64, 3)),
    layers.Conv2D(64, kernel_size=4, strides=2, padding="same"),
    layers.LeakyReLU(alpha=0.2),
    layers.Conv2D(128, kernel_size=4, strides=2, padding="same"),
    layers.LeakyReLU(alpha=0.2),
    layers.Conv2D(128, kernel_size=4, strides=2, padding="same"),
    layers.LeakyReLU(alpha=0.2),
    layers.Flatten(),
    layers.Dropout(0.2),
    layers.Dense(1, activation="sigmoid"),
],
name="discriminator",
)
```

以下是判别器模型摘要：

| 层 (类型) | 输出形状 | 参数数 |
|---|---|---|
| conv2d (Conv2D) | (None, 32, 32, 64) | 3136 |
| leaky_re_lu (LeakyReLU) | (None, 32, 32, 64) | 0 |
| conv2d_1 (Conv2D) | (None, 16, 16, 128) | 131200 |
| leaky_re_lu_1 (LeakyReLU) | (None, 16, 16, 128) | 0 |
| conv2d_2 (Conv2D) | (None, 8, 8, 128) | 262272 |
| leaky_re_lu_2 (LeakyReLU) | (None, 8, 8, 128) | 0 |
| flatten (Flatten) | (None, 8192) | 0 |
| dropout (Dropout) | (None, 8192) | 0 |
| dense (Dense) | (None, 1) | 8193 |

总参数：404,801
可训练参数：404,801
不可训练参数：0


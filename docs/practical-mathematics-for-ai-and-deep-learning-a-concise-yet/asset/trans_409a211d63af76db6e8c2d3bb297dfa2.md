
```
5.     x = layers.LeakyReLU(0.2)(x)
6.     y = layers.Reshape((64,64,1))(y)
7.     
8.     x = layers.concatenate([img, y])
9.     
10.    x = layers.Conv2D(filters=128, kernel_size=5,
11.                       strides=2, padding='same')(x)
12.    for filter_size in [256, 512, 1024]:
13.        x = layers.Conv2D(filters=filter_size, kernel_size=5,
14.                           strides=2, padding='same')(x)
15.        x = layers.LeakyReLU(0.2)(x)
16.        x = layers.BatchNormalization()(x)
17.
18.    x = layers.Flatten()(x)
19.    x = layers.Dense(1)(x)
20.    return Model(inputs=[img, label], outputs=x)
```

在上述代码的 `line 8` 中，我们将新通道的辅助信息作为第四个通道，连同输入图像的三个通道一起添加。其余代码对于普通判别器来说保持不变。同样，对于条件生成器，我们采用普通生成器中的第一个卷积层来创建大小为 4×4×1024 的第一个 3D 张量，然后在将嵌入层的辅助信息映射并重塑为 4×4×1 后将其作为另一个通道追加。

训练循环与普通 GAN 保持相同，不同之处在于生成器还需要假标签作为输入，而判别器需要真标签作为输入。其余代码保持不变，如下所示：

```
1. def train_step(images, labels):
2.     noise = tf.random.normal([BATCH_SIZE, noise_dim])
3.     
4.     with tf.GradientTape() as gen_tape, tf.GradientTape() as disc_tape:
5.         generated_images = G(noise, training=True)
6.         fake_labels = np.random.randint(0, 2, BATCH_SIZE)
7.         
8.         real_output = D([images, labels], training=True)
9.         fake_output = D([generated_images, fake_labels], training=True)
```

条件 GAN 也被用于图像到图像的转换任务。图像到图像转换是指获取一个域中的图像并将其转换为另一幅图像，使其具有另一个域中图像的特征。我们不再将辅助数据作为输入传递，而是可以将源图像传递给生成器以对其进行条件控制。此外，由于辅助信息非常丰富，生成器可以直接将源图像作为输入，完全不需要随机噪声向量。为了生成高质量的图像输出，我们迄今为止使用的简单 CNN 架构可能已不足够。我们可以使用容量更高的架构，如 U-Net 或 ResNet-50，来创建条件生成器。Pix2Pix 模型是一种 cGAN，其输出生成以输入源图像为条件，并且它们对生成器使用 U-Net 架构。

# Cycle GAN (CycleGAN)

CycleGAN 是一种使用两个生成器和两个判别器的 GAN 架构，主要应用于各种图像到图像的转换任务，在这些任务中，来自两个域的成对图像数据不可用。

例如，如果我们将源图像域定义为一组自然图像。我们获取一张童年假期海滩的手绘图像。如果我们能将这张手绘图像输入生成器，并得到一张带有我们童年回忆的照片级真实海滩图像，那该多好！图像转换是一个经典的计算机视觉问题，所有解决该问题的传统方法都涉及使用成对训练数据集，即包含来自两个不同域的成对图像的数据集。成对数据集的例子包括：(1) 卫星图像和 Google 地图图像的配对，以及 (2) 立面数据集，包含 506 个建筑立面及其对应的分割图。然而，获取成对图像数据集并不总是可行；这就是 CycleGAN 发挥作用的地方。现在让我们正式介绍 CycleGAN。

设 ![](images/3010.jpg) 和 ![](images/3011.jpg) 为来自两个不同域的图像样本数据集。我们可以将数据分布表示为 ![](images/3012.jpg) 和 ![](images/3013.jpg)。定义两个生成器 ![](images/3014.jpg) 和 ![](images/3015.jpg)。注意，与之前定义的生成器不同，这里的生成器直接接收图像作为输入，而不是随机噪声向量。此外，我们定义两个对抗判别器 ![](images/3016.jpg) 和 ![](images/3017.jpg)，其中 ![](images/3018.jpg) 的目标是区分图像 ![](images/3019.jpg) 和转换后的图像 {![](images/3020.jpg)()}，而 ![](images/3021.jpg) 旨在区分 ![](images/3022.jpg) 和 {![](images/3023.jpg)(x)}。

因此，我们现在有四个神经网络需要训练：![](images/3024.jpg)。我们可以为训练该网络定义一个联合目标函数。同时，我们也必须说明训练这些网络的步骤。由于存在两个独立的 GAN，我们有两个对抗损失：

![](images/3025.jpg)

和 ![](images/3026.jpg)

该目标也将面临与普通 GAN 对抗损失公式中相同的问题，如梯度消失和模式崩塌。类似于我们在普通 GAN 中使用的特征匹配技术，我们可以强制生成器 F 和 G 保持一致，即如果 ![](images/3027.jpg)，则使用 G 转换 x 然后在转换后的图像上应用 F，我们应该得到一张非常接近 x 的图像 ![](images/3028.jpg)。如果 ![](images/3029.jpg)。请参考下图：

![](images/Image49357.jpg)

**图 12.16：** CycleGAN

因此，应最小化 ![](images/3030.jpg)，即最小化 ![](images/3031.jpg)，同理，应最小化 ![](images/3032.jpg)。我们将该总量称为**循环一致性损失**：

![](images/3033.jpg)

因此，CycleGAN 的损失可以写为对抗损失 + 循环一致性损失：![](images/3034.jpg)。此处，l 是一个超参数，控制应给予循环一致性损失多少权重。为了在输出中更好地保持颜色，提出了另一个可选的损失项，称为身份损失项。这也是一个像素级的 L1 损失项，类似于 ![](images/3035.jpg)。其背后的思想是：对于生成器 ![](images/3036.jpg)，如果我们获取一张来自目标域的图像 ![](images/3037.jpg)，我们应该保持其原样，因为该图像已经属于 Y，因此不需要转换。理想情况下，![](images/3038.jpg) 和 ![](images/3039.jpg)，因此我们应该最小化项 ![](images/3040.jpg)。因此，我们的损失多了一个项和一个超参数 m：

![](images/3041.jpg)

此处，对抗损失项可以替换为 Wasserstein 损失，以实现 CycleGAN 更稳定的训练。

以下是训练 CycleGAN 的步骤：

1.  选择超参数 l, m。
2.  随机初始化生成器和判别器网络的权重。
3.  冻结生成器并为给定的生成器寻找最优判别器：
    1.  获取一批图像 ![](images/3042.jpg) 和 ![](images/3043.jpg)
    2.  运行 SGD，通过计算判别器对抗损失的梯度来优化判别器权重。
4.  通过优化生成器损失并保持判别器固定来更新生成器权重：
    1.  对于图像 ![](images/3044.jpg) 和 ![](images/3045.jpg)，计算：
        i.  ![](images/3046.jpg) 中所有 x 的循环 x
        ii. ![](images/3047.jpg) 中所有 y 的循环 y
        iii. 身份损失的相同 x：对于 ![](images/3048.jpg) 中的所有 y
        iv. 身份损失的相同 y：对于 ![](images/3049.jpg) 中的所有 x
        v. 计算所有三个损失分量，然后计算总生成器损失梯度。
5.  重复步骤 3 和 4 直到收敛。

**提示：** 以下链接提供了使用 U-Net 生成器和判别器实现 CycleGAN 的方法：

[https://www.tensorflow.org/tutorials/generative/cyclegan](https://www.tensorflow.org/tutorials/generative/cyclegan)

# 自回归生成模型

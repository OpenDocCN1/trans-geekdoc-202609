
```
discriminator = models.Model(discriminator_input, discriminator_output)
```

- 1. 定义判别器的输入层（图像）。
- 2. 将 Conv2D 层堆叠在一起，中间夹着 BatchNormalization、LeakyReLU 激活和 Dropout 层。
- 3. 展平最后一个卷积层——此时张量的形状为 1 × 1 × 1，因此不需要最终的 Dense 层。
- 4. 定义判别器的 Keras 模型——一个模型，接收输入图像并输出 0 到 1 之间的单个数字。

注意我们在部分 Conv2D 层中使用步长为 2，以在张量通过网络时减小其空间形状（原始图像中为 64，然后是 32、16、8、4，最后为 1），同时增加通道数（灰度输入图像中为 1，然后是 64、128、256，最后为 512），然后再坍缩为单个预测。

我们在最终的 Conv2D 层上使用 sigmoid 激活函数，以输出 0 到 1 之间的数字。

## 生成器

现在让我们构建生成器。生成器的输入将是从多元标准正态分布中抽取的向量。输出是与原始训练数据中图像大小相同的图像。

这个描述可能让你想起变分自编码器中的解码器。事实上，GAN 的生成器与 VAE 的解码器完全相同的目的：将潜在空间中的向量转换为图像。将潜在空间映射回原始域的概念在生成建模中非常常见，因为它使我们能够操纵潜在空间中的向量，从而改变原始域中图像的高级特征。

我们将要构建的生成器的架构如表 4-2 所示。

表 4-2. 生成器的模型摘要

| 层（类型） | 输出形状 | 参数数 |
|---|---|---|
| InputLayer | (None, 100) | 0 |
| Reshape | (None, 1, 1, 100) | 0 |
| Conv2DTranspose | (None, 4, 4, 512) | 819,200 |
| BatchNormalization | (None, 4, 4, 512) | 2,048 |
| ReLU | (None, 4, 4, 512) | 0 |
| Conv2DTranspose | (None, 8, 8, 256) | 2,097,152 |
| BatchNormalization | (None, 8, 8, 256) | 1,024 |
| ReLU | (None, 8, 8, 256) | 0 |
| Conv2DTranspose | (None, 16, 16, 128) | 524,288 |
| BatchNormalization | (None, 16, 16, 128) | 512 |
| ReLU | (None, 16, 16, 128) | 0 |
| Conv2DTranspose | (None, 32, 32, 64) | 131,072 |
| BatchNormalization | (None, 32, 32, 64) | 256 |
| ReLU | (None, 32, 32, 64) | 0 |
| Conv2DTranspose | (None, 64, 64, 1) | 1,024 |

总参数 3,576,576
可训练参数 3,574,656
非可训练参数 1,920

构建生成器的代码在示例 4-5 中给出。

### 示例 4-5. 生成器

```python
generator_input = layers.Input(shape=(100,)) ①
x = layers.Reshape((1, 1, 100))(generator_input) ②
x = layers.Conv2DTranspose(
    512, kernel_size=4, strides=1, padding="valid", use_bias = False
)(x) ③
x = layers.BatchNormalization(momentum=0.9)(x)
x = layers.LeakyReLU(0.2)(x)
x = layers.Conv2DTranspose(
    256, kernel_size=4, strides=2, padding="same", use_bias = False
)(x)
x = layers.BatchNormalization(momentum=0.9)(x)
x = layers.LeakyReLU(0.2)(x)
x = layers.Conv2DTranspose(
    128, kernel_size=4, strides=2, padding="same", use_bias = False
)(x)
x = layers.BatchNormalization(momentum=0.9)(x)
x = layers.LeakyReLU(0.2)(x)
x = layers.Conv2DTranspose(
    64, kernel_size=4, strides=2, padding="same", use_bias = False
)(x)
x = layers.BatchNormalization(momentum=0.9)(x)
x = layers.LeakyReLU(0.2)(x)
generator_output = layers.Conv2DTranspose(
    1,
kernel_size=4,
strides=2,
padding="same",
use_bias = False,
activation = 'tanh'
)(x)
generator = models.Model(generator_input, generator_output)
```

- 1. 定义生成器的输入层——长度为 100 的向量。
- 2. 我们使用 Reshape 层将其 reshape 为 1 × 1 × 100 的张量，以便开始应用转置卷积操作。
- 3. 我们将其通过四个 Conv2DTranspose 层，中间夹着 BatchNormalization 和 LeakyReLU 层。
- 4. 最终的 Conv2DTranspose 层使用 tanh 激活函数将输出变换到范围 [−1, 1]，以匹配原始图像域。
- 5. 定义生成器的 Keras 模型——一个模型，接受长度为 100 的向量并输出形状为 [64, 64, 1] 的张量。

注意我们在部分 Conv2DTranspose 层中使用步长为 2，以在张量通过网络时增大其空间形状（原始向量中为 1，然后是 4、8、16、32，最后为 64），同时减少通道数（512 然后是 256、128、64，最后为 1 以匹配灰度输出）。

## 上采样与 Conv2DTranspose

使用 Conv2DTranspose 层的替代方案是改用 UpSampling2D 层后跟步长为 1 的普通 Conv2D 层，如示例 4-6 所示。

### 示例 4-6. 上采样示例

```
x = layers.UpSampling2D(size = 2)(x)
x = layers.Conv2D(256, kernel_size=4, strides=1, padding="same")(x)
```

UpSampling2D 层简单地重复其输入的每一行和列以使大小加倍。步长为 1 的 Conv2D 层然后执行卷积操作。这与转置卷积的想法类似，但不是用零填充像素之间的间隙，上采样只是重复现有的像素值。

研究表明，Conv2DTranspose 方法可能导致伪影，或输出图像中小块棋盘格图案（见图 4-4），从而破坏输出质量。然而，它们仍被文献中许多最令人印象深刻的 GAN 中使用，并已证明是深度学习从业者工具箱中的强大工具。

![](img/f0f0f5d89818fdddf117bbe758ac8143_130_0.png)

图 4-4. 使用转置卷积层时的伪影（来源：Odena et al., 2016）3

这两种方法——UpSampling2D + Conv2D 和 Conv2DTranspose——都是将图像转换回原始域的可接受方式。真正的情况是在你自己的问题设置中测试这两种方法，看看哪种产生更好的结果。

## 训练 DCGAN

正如我们所见，DCGAN 中生成器和判别器的架构非常简单，与我们在第 3 章中看到的 VAE 模型并没有太大不同。理解 GAN 的关键在于理解生成器和判别器的训练过程。

我们可以通过创建训练集来训练判别器，其中一些图像是来自训练集的真实观测值，一些是来自生成器的伪造输出。然后我们将其视为监督学习问题，其中真实图像的标签为 1，伪造图像的标签为 0，损失函数为二元交叉熵。

如何训练生成器？我们需要找到一种为每个生成图像评分的方法，以便其能够优化向高分图像。幸运的是，我们有一个判别器正好可以做到这一点！我们可以生成一批图像并将其通过判别器为每个图像获得一个分数。生成器的损失函数然后只是这些概率与全为 1 的向量之间的二元交叉熵，因为我们希望训练生成器生成判别器认为真实的图像。

关键是我们必须交替训练这两个网络，确保一次只更新一个网络的权重。例如，在生成器训练过程中，只有生成器的权重会被更新。如果我们也允许判别器的权重发生变化，判别器只会调整以更可能将生成的图像预测为真实，这不是期望的结果。我们希望生成的图像被预测接近 1（真实），因为生成器强大，而不是因为判别器弱。

判别器和生成器的训练过程图示如图 4-5 所示。

![](img/f0f0f5d89818fdddf117bbe758ac8143_131_0.png)

图 4-5. 训练 DCGAN——灰色框表示训练期间权重被冻结

Keras 提供了创建自定义 train_step 函数以实现此逻辑的能力。示例 4-7 显示了完整的 DCGAN 模型类。

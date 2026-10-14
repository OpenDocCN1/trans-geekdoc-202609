
![](img/f0f0f5d89818fdddf117bbe758ac8143_180_0.png)

## 运行本示例的代码

本示例的代码可在书籍仓库中位于 *notebooks/05_autoregressive/02_pixelcnn/pixelcnn.ipynb* 的 Jupyter notebook 中找到。

代码改编自 ADMoreau 创建的优秀 PixelCNN 教程，该教程可在 Keras 网站上获取。

## 掩码卷积层

如我们在第 2 章所见，卷积层可以通过应用一系列滤波器从图像中提取特征。层在特定像素处的输出是滤波器权重与以该像素为中心的较小正方形上前一层值的乘积的加权和。这种方法可以检测边缘和纹理，在更深的层中可以检测形状和更高级别的特征。

虽然卷积层对于特征检测非常有用，但它们不能直接以自回归的方式使用，因为像素之间没有顺序。它们依赖于所有像素被同等对待的事实——没有像素被视为图像的 *开始* 或 *结束*。这与本章中我们已经看到的文本数据形成对比，文本数据中标记有明确的顺序，因此可以 readily 应用诸如 LSTM 之类的循环模型。

为了能够以自回归的方式将卷积层应用于图像生成，我们必须首先对像素进行排序，并确保滤波器只能看到该像素之前的像素。然后我们可以通过将卷积滤波器应用于当前图像来一次生成一个像素，从所有先前的像素中预测下一个像素的值。

我们首先需要为像素选择一个顺序——一个合理的建议是从左上到右下对像素进行排序，先沿行移动，然后向下移动列。

然后我们对卷积滤波器进行掩码，以便层在每个像素处的输出仅受该像素之前的像素值的影响。这是通过将由 1 和 0 组成的掩码与滤波器权重矩阵相乘来实现的，这样目标像素之后的所有像素的值都会被置零。

PixelCNN 中实际上有两种不同的掩码，如图 5-13 所示：

- Type A，中心像素的值被掩码
- Type B，中心像素的值 *未* 被掩码

![](img/f0f0f5d89818fdddf117bbe758ac8143_181_0.png)

图 5-13。左：卷积滤波器掩码；右：应用于一组像素以预测中心像素值分布的掩码（来源：van den Oord et al., 2016）

初始的掩码卷积层（即直接应用于输入图像的层）不能使用中心像素，因为这正是我们希望网络猜测的像素！然而，后续层可以使用中心像素，因为它仅是根据原始输入图像中先前像素的信息计算得出的。

我们可以在示例 5-12 中看到如何使用 Keras 构建 MaskedConvLayer。

### 示例 5-12. Keras 中的 MaskedConvLayer

```
class MaskedConvLayer(layers.Layer):
    def __init__(self, mask_type, **kwargs):
        super(MaskedConvLayer, self).__init__()
        self.mask_type = mask_type
        self.conv = layers.Conv2D(**kwargs) ①

    def build(self, input_shape):
        self.conv.build(input_shape)
        kernel_shape = self.conv.kernel.get_shape()
        self.mask = np.zeros(shape=kernel_shape) ②
        self.mask[: , kernel_shape[0] // 2, ...] = 1.0 ③
        self.mask[kernel_shape[0] // 2, : , kernel_shape[1] // 2, ...] = 1.0 ④
        if self.mask_type == "B":
            self.mask[kernel_shape[0] // 2, kernel_shape[1] // 2, ...] = 1.0 ⑤

    def call(self, inputs):
        self.conv.kernel.assign(self.conv.kernel * self.mask) ⑥
        return self.conv(inputs)
```

① MaskedConvLayer 基于普通的 Conv2D 层。

- 2. 掩码初始化为全零。
- 3. 前几行的像素用 1 解掩。
- 4. 同一行中前几列的像素用 1 解掩。
- 5. 如果掩码类型为 B，则中心像素用 1 解掩。
- 6. 掩码与滤波器权重相乘。

请注意，此简化示例假设为灰度图像（即一个通道）。如果我们有彩色图像，我们也可以对三个颜色通道进行排序，例如红色通道先于蓝色通道，蓝色通道先于绿色通道。

## 残差块

现在我们已经了解了如何对卷积层进行掩码，我们可以开始构建 PixelCNN 了。我们将使用的核心构建块是残差块。

残差块是一组层，其中输出在传递给网络其余部分之前会加到输入上。换句话说，输入有通往输出的快速通道，无需经过中间层——这称为跳跃连接。加入跳跃连接的理由是，如果最优变换只是保持输入不变，只需将中间层的权重置零即可实现。没有跳跃连接，网络就必须通过中间层找到恒等映射，这要困难得多。

我们 PixelCNN 中残差块的示意图如图 5-14 所示。

![](img/f0f0f5d89818fdddf117bbe758ac8143_183_0.png)

图 5-14. PixelCNN 残差块（滤波器数量标注在箭头旁，滤波器大小标注在层旁）

我们可以使用示例 5-13 所示的代码构建 ResidualBlock。

### 示例 5-13. 残差块

```
class ResidualBlock(layers.Layer):
    def __init__(self, filters, **kwargs):
        super(ResidualBlock, self).__init__(**kwargs)
        self.conv1 = layers.Conv2D(
            filters=filters // 2, kernel_size=1, activation="relu"
        ) ①
        self.pixel_conv = MaskedConv2D(
            mask_type="B",
            filters=filters // 2,
            kernel_size=3,
            activation="relu",
            padding="same",
        ) ②
        self.conv2 = layers.Conv2D(
            filters=filters, kernel_size=1, activation="relu"
        ) ③

    def call(self, inputs):
        x = self.conv1(inputs)
        x = self.pixel_conv(x)
        x = self.conv2(x)
        return layers.add([inputs, x]) ④
```

① 初始的 Conv2D 层将通道数减半。

- 2. 内核大小为 3 的类型 B MaskedConv2D 层仅使用五个像素的信息——焦点像素上方一行中的三个像素、左侧一个像素以及焦点像素本身。
- 3. 最后的 Conv2D 层将通道数加倍以再次匹配输入形状。
- 4. 卷积层的输出加到输入上——这就是跳跃连接。

## 训练 PixelCNN

在示例 5-14 中，我们将整个 PixelCNN 网络组合起来，大致遵循原始论文中概述的结构。在原始论文中，输出层是一个 256 滤波器的 Conv2D 层，使用 softmax 激活。换句话说，网络试图通过预测正确的像素值来重建其输入，有点像自动编码器。不同之处在于，由于网络的设计方式使用了 MaskedConv2D 层，PixelCNN 受约束，使得来自早期像素的任何信息都无法流经以影响每个像素的预测。

这种方法的一个挑战是，网络无法理解例如像素值 200 与像素值 201 非常接近。它必须独立学习每个像素输出值，这意味着训练可能非常缓慢，即使对于最简单的数据集也是如此。因此，在我们的实现中，我们改为简化输入，使每个像素只能取四个值之一。这样，我们可以使用 4 滤波器的 Conv2D 输出层而不是 256。

### 示例 5-14. PixelCNN 架构

```
inputs = layers.Input(shape=(16, 16, 1)) ①
x = MaskedConv2D(mask_type="A"
    , filters=128
    , kernel_size=7
    , activation="relu"
    , padding="same")(inputs)②

for _ in range(5):
    x = ResidualBlock(filters=128)(x) ③

for _ in range(2):
    x = MaskedConv2D(
        mask_type="B",
        filters=128,
        kernel_size=1,
        strides=1,
        activation="relu",
```


![](img/fe161b7f6e96e35e7e853eece52c6dce_191_0.png)

图 4.10 在延迟约束下 MobileNet-V1 的量化策略 (Wang et al., 2018)。

卷积层。因此，设计高效的卷积层是构建高效 CNN 架构的核心。

本节首先描述标准卷积层，然后描述标准卷积层的三种高效变体。接下来，我们介绍三种具有代表性的手工设计高效 CNN 架构，包括 SqueezeNet (Iandola et al., 2016)、MobileNets (Howard et al., 2017; Sandler et al., 2018) 和 ShuffleNets (Ma et al., 2018; Zhang et al., 2017)。最后，我们描述设计高效 CNN 架构的自动化方法。

## 4.2.1 标准卷积层

标准卷积层由大小为 O_c × I_c × K × K 的卷积核 K 参数化，其中 O_c 是输出通道数，I_c 是输入通道数，K 是核的空间维度 (图 4.11a)。这里为简单起见，我们假设卷积核的宽度和高度相同。也可以使用非对称卷积核 (Szegedy and Vanhoucke, 2016)。

给定大小为 I_c × H × W 的输入特征图 F_i，大小为 O_c × H × W 的输出特征图 F_o 计算如下⁴：

```
F_o[n, h, w] = Σ_{m,i,j} K[n, m, i, j] × F_i[m, h + i - [K/2], w + j - [K/2]]. (4.9)
```

⁴ 假设步长为 1 且应用零填充以保持特征图的空间维度。

![](img/fe161b7f6e96e35e7e853eece52c6dce_193_0.png)

图 4.12 SqueezeNet 架构 (Iandola et al., 2016)。

然后每个组被送入大小为 O_c/G × I_c/G × K × K 的标准 K × K 卷积。最后，将输出沿通道维度拼接。与标准 K × K 卷积相比，组卷积中的 #MACs 和 #Params 降低了 G 倍。

### 深度可分离卷积

组卷积中组数 G 是一个可调超参数。更大的 G 导致计算成本更低、参数更少。极端情况是 G 等于输入通道数 I_c。在这种情况下，组卷积层称为深度可分离卷积 (图 4.11 c)。深度可分离卷积的 #MACs 和 #Params 为

#MACs(DWConv_{K×K}) = H × W × O_c × K × K, (4.12)
#Params(DWConv_{K×K}) = O_c × K × K, (4.13)
其中 O_c = I_c。

## 4.2.3 手工设计的高效 CNN 模型

### SqueezeNet (图 4.12)

SqueezeNet (Iandola et al., 2016) 针对移动应用的极紧凑模型大小。它只有 120 万个参数，但实现了与 AlexNet 相似的精度 (表 4.1)。SqueezeNet 有 26 个卷积层且没有全连接层。最后一个特征图经过全局平均池化并形成 1000 维向量以输入 softmax 层。SqueezeNet 有八个 Fire 模块。每个 fire 模块包含一个具有 1 × 1 卷积的 squeeze 层和一对 1 × 1 和 3 × 3 卷积。SqueezeNet caffe 模型在 ImageNet 2012 (Deng et al., 2009) 上实现了 57.4% 的 top-1 精度和 80.5% 的 top-5 精度。SqueezeNet 广泛用于模型大小是主要限制的移动应用中。

### MobileNets (图 4.13)

MobileNetV1 (Howard et al., 2017) 基于一个称为深度可分离卷积的构建块 (图 4.13a)，它由一个 3 × 3 深度可分离卷积层和一个 1×1 卷积层组成。输入图像首先经过步长为 2 的 3×3 标准卷积层，然后是 13 个深度可分离卷积块。最后，特征图经过全局平均池化并形成 1280 维向量输入到具有 1000 个输出单元的最终全连接层。MobileNetV1 在 ImageNet 2012 上实现了 70.6% 的 top-1 精度，具有 569M MACs 和 4.2M 参数 (表 4.1)。

MobileNetV2 (Sandler et al., 2018)，MobileNetV1 的改进版本，也使用 3 × 3 深度可分离卷积和 1 × 1 卷积来组成其构建块。与 MobileNetV1 不同，MobileNetV2 中的构建块有三层，包括一个 3 × 3 深度可分离卷积层和两个 1 × 1 卷积层 (图 4.13b)。其直觉是深度可分离卷积的容量远低于标准卷积，因此需要更多通道来提高其容量。从成本角度来看，深度可分离卷积的 #MACs 和 #Params 仅随通道数线性增长 (而标准卷积则呈二次增长)。因此，即使通道数很大，深度可分离卷积层的成本仍然适中。因此，在 MobileNetV2 中，输入特征图首先经过 1×1 卷积以按称为 *扩展比率* 的因子增加通道维度。然后扩展后的特征图送入 3 × 3 深度可分离卷积，随后是另一个 1 × 1 卷积将通道维度降低回原始值。这种结构称为 *倒置瓶颈*，该块称为 *移动倒置瓶颈块*。除移动倒置瓶颈块外，MobileNetV2 相对于 MobileNetV1 还有另外两项改进。首先，对于步长为 1 的块，MobileNetV2 具有跳跃连接⁵。其次，每个块中最后一个 1 × 1 卷积的激活函数被移除。结合这些改进，MobileNetV2 在 ImageNet 2012 上仅用 300M MACs 和 3.4M 参数实现了 72.0% 的 top-1 精度 (表 4.1)。

## 表 4.1 手工设计 CNN 架构在 ImageNet 上的汇总结果。

| 网络 | #参数 | #MACs | ImageNet Top-1 精度 | Top-5 精度 |
|---|---|---|---|---|
| AlexNet (Krizhevsky et al., 2012) | 60M | 720M | 57.2% | 80.3% |
| GoogleNet (Szegedy et al., 2015) | 6.8M | 1550M | 69.8% | 89.5% |
| VGG-16 (Simonyan and Zisserman, 2014) | 138M | 15300M | 71.5% | – |
| ResNet-50 (He et al., 2016) | 25.5M | 4100M | 76.1% | 92.9% |
| SqueezeNet (Iandola et al., 2016) | 1.2M | 1700M | 57.4% | 80.5% |
| MobileNetV1 (Howard et al., 2017) | 4.2M | 569M | 70.6% | 89.5% |
| MobileNetV2 (Sandler et al., 2018) | 3.4M | 300M | 72.0% | – |
| MobileNetV2-1.4 (Sandler et al., 2018) | 6.9M | 585M | 74.7% | – |
| ShuffleNetV1-1.5x (Zhang et al., 2017) | 3.4M | 292M | 71.5% | – |
| ShuffleNetV2-1.5x (Ma et al., 2018) | 3.5M | 299M | 72.6% | – |
| ShuffleNetV2-2x (Ma et al., 2018) | 7.4M | 591M | 74.9% | – |

![](img/fe161b7f6e96e35e7e853eece52c6dce_194_0.png)

![](img/fe161b7f6e96e35e7e853eece52c6dce_194_1.png)

![](img/fe161b7f6e96e35e7e853eece52c6dce_194_2.png)

(a) MobileNetV1

(b) MobileNetV2

图 4.13 (a) MobileNetV1 的构建块 (Howard et al., 2017)。它由一个 3 × 3 深度可分离卷积层和一个 1×1 卷积层组成。(b) MobileNetV2 的构建块 (Sandler et al., 2018)。每个块由一个 3 × 3 深度可分离卷积层和两个 1 × 1 卷积层组成。当步长为 1 时，块将具有跳跃连接。

![](img/fe161b7f6e96e35e7e853eece52c6dce_195_0.png)

图 4.14 通道洗牌操作的说明 (Zhang et al., 2017)。

### ShuffleNets

与 MobileNets 类似，ShuffleNetV1 利用 3×3 深度可分离卷积而不是标准卷积。此外，ShuffleNetV1 引入了两种新操作，即逐点组卷积和通道洗牌。逐点组卷积的动机是降低 1 × 1 卷积层的计算成本。然而，它有一个副作用：一个组无法看到其他组的信息。这会严重损害精度。因此引入通道洗牌操作来通过在不同组之间交换特征图来解决此副作用。通道洗牌操作的说明在图 4.14 中给出。洗牌后，每个组将包含来自所有组的信息。在 ImageNet 2012 上，ShuffleNetV1 实现了 71.5% 的 top-1 精度，MACs 为 292M (表 4.1)。

在 ShuffleNetV2 中，每个构建块开始时输入特征图被分为两组。其中一组经过卷积分支，该分支由 3 × 3 深度-

⁵ 有跳跃连接时，*输出* = ℱ(*输入*) + *输入*。无跳跃连接时，*输出* = ℱ(*输入*)。

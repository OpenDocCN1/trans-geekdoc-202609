
# division

为了训练和测试模型，将宝可梦数据集分为三部分：训练数据、验证数据和测试数据，比例分别为 `6`、`2` 和 `2`。数据划分代码如下。

![](img/image-43d42lk.jpg) 将 `Type1` 和 `Type2` 限制在 `0` 和 `1` 之间（有 `19` 个属性，包括空属性）。![](img/image-1kcirygu.jpg) 标准分标准化宝可梦的值。![](img/image-c3qu0lb.jpg) 以 `Numpy` 数组格式转换训练数据、验证数据和来自战斗数据的标签。![](img/image-2bdohj.jpg) 两种不同的输入数据：第一类型（`Type1` 和 `Type2`）使用整数编码表示。![](img/image-3suts1nq.jpg) 第二类型使用独热编码表示。![](img/image-5f1iocrj.jpg)

## 训练网络模型

实现了两个宝可梦战斗预测模型：

- 使用整数编码技术表示宝可梦的 `18` 属性（`Type1` 和 `Type2`）。
- 使用独热编码技术表示宝可梦的 `18` 属性（`Type1` 和 `Type2`）。

表 3.5 显示了 `Model-1` 和 `Model-2` 的架构。

**表 3.5**

| 3.5 | 3.5 | 3.5 |
| :--- | :--- | :--- |

`Model-1` 的输入是两个宝可梦的数据；每个宝可梦有十个不同的特征，因此输入形状为 `(20,)`。![](img/image-rm8p86e.jpg) ![](img/image-yjyy4n.jpg) 优化器、损失函数和指标函数。![](img/image-27y0950q.jpg) 用于保存模型的回调函数。![](img/image-9fe3pug.jpg) `model-57bw`。

### 补充说明

之前引入的 `BCE` 包含内置的 sigmoid 激活函数，但 sigmoid 激活函数通常添加到网络的输出层。为了避免输出两次 sigmoid 操作，`keras.losses.BinaryCrossentropy` 函数有一个 `from_logits` 参数设置：

- 设置为 `False`（默认）：损失函数不会添加 sigmoid 激活函数。
- 设置为 `True`：损失函数将添加 sigmoid 激活函数。

`keras.losses.CategoricalCrossentropy` 函数具有相同的概念。

`Model-2` 的输入是两个宝可梦的数据；每个宝可梦有二十七项不同的信息，因此输入形状为 `(54,)`。![](img/image-p3mvk6lh.jpg) 优化器、损失函数和指标函数。![](img/image-g8aq83.jpg) 回调函数。![](img/image-3xua2pu.jpg) `model-2.d7tcp8x`。

### 结果

`Model-1` 和 `Model-2` 的训练准确率。![](img/image-3lh5b03g.jpg) 图 3.11 显示 `Model-2` 在训练数据和验证数据上的准确率优于 `Model-1`。结果证明，在测试数据上使用独热编码进行二分类比整数编码技术更有效。可以观察到，最后使用训练好的 `Model-2` 预测了妙花、喷火龙和水龟之间的战斗结果，如图所示。

### 参考文献

1. Keller J.M., Gray M.R., Givens J.A. A fuzzy k-nearest neighbor In IEEE Transactions 1985:580–585.
2. Denoeux T. A k-nearest neighbor rule based on Dempster-Shafer IEEE Trans. Syst. Man 1995;25(5):804–813.
3. Fukunaga K., Narendra P.M. A branch and bound algorithm for computing k-nearest IEEE Trans. Comput. 1975;C-24(7):750–753.
4. Dudani S.A. The distance-weighted k-nearest-neighbor IEEE Trans. Syst. Man 1976;S-6(4):225–327.
5. Quinlan J.R. Induction of decision Mach. Learn. 1986;1:81–106.
6. Schmid H. Probabilistic part of speech tagging using decision Proceedings of the International Conference of New Methods in Language 1994:44–49.
7. Janikow C.Z. Fuzzy decision trees: issues and IEEE Trans. Syst. Man 1998;28(1):1–14.
8. Tsang S., Kao B., Yip K.Y., Ho W., Lee S.D. Decision trees for uncertain IEEE Trans. Knowl. Data Eng. 2011;23(1):64–78.
9. Breiman L. Random. Learn. 2001;45(1):5–32.
10. Bosch A., Zisserman A., Munoz X. Image classification using random forests and IEEE International Conference of Computer Vision, Rio de Janeiro; 2007:1–8.
11. Gislason P.O., Benediktsson J.A., Sveinsson J.R. Random forests for land cover Pattern Recogn. Lett. 2006;27(4):294–300.

# 第 4 章：多分类问题

## 摘要

卷积神经网络（也称为 `CNN` 或 `ConvNet`）是一种深度神经网络，它已成功应用于多种计算机视觉领域，特别是用于视觉图像的分析。在本章中，我们首先介绍了 `CNN` 的结构和操作机制，以解释其工作原理。接下来，我们将讨论多分类问题，这指的是将样本归类为三个或更多类别中的一个的问题。然后，我们将构建一个基于 `CNN` 的多分类模型，以帮助读者提高使用 `CNN` 解决多分类问题的技能。最后，我们介绍并应用了一种数据增强技术，以防止训练过程中的过拟合问题，并提高基于 `CNN` 的分类模型的性能。

## 关键词

卷积神经网络；`TensorFlow` 数据集；多分类；图像分类；数据增强

## 大纲

- 卷积神经网络 (`CNNs`) 简介
- 分类交叉熵
- 增加训练数据的数据增强技术
- 使用 `CNN` 在 CIFAR-10 数据集上进行多分类

## 4.1 卷积神经网络

### 4.1.1 卷积神经网络简介

卷积神经网络，也称为 `CNN` 或 `ConvNet`，是一种深度神经网络，它已成功应用于各种计算机视觉应用中，特别是用于分析视觉图像。图 4.1 显示了 2012 年 ImageNet 大规模视觉识别挑战（ImageNet LSVRC）中最佳方法的排名。所示，使用 `CNN` 的 `AlexNet` 在错误率方面优于之前最先进的图像分类方法。在随后的 ImageNet 竞赛中，基于 `CNN` 的模型（如 `GoogLeNet`、`ResNet`、`ResNeXt` 等）继续获胜，并以令人惊叹的性能压倒了传统模型。

![](img/image-it95hlar.jpg)

图 4.1 2012 年 ImageNet 大规模视觉识别挑战（ImageNet LSVRC）中最佳方法的排名。

正如前面的章节所述，普通神经网络包括输入层、隐藏层和输出层，其中来自输入层的输入在发送到输出层之前，会通过一系列隐藏层进行转换。每层都包含一组神经元，其中每个神经元与上一层的所有神经元全连接，且神经元完全独立地运行，如图所示。`CNNs` 与普通神经网络相似，这意味着它们也由包含可学习权重和偏置神经元的层组成。然而，与普通神经网络不同，`CNNs` 层中的神经元是以三维方式组织的，包括宽度、高度和深度，每个神经元仅通过卷积核（神经元的感受野）与上一层的局部区域连接，如图所示。在 `CNNs` 中，神经元的 3D 输入张量在每一层都被转换为神经元的 3D 输出张量。例如，如果一个设计用于 ImageNet [2] 数据集图像分类的 `CNN` 接收到维度为 `256 × 256 × 3` 的图像输入，那么 `CNN` 的最终输出层维度应为 `1 × 1 × 1000`，因为 ImageNet 有 1000 个类。

![](img/image-x0mhk8o7.jpg)

图 4.2 普通神经网络和卷积神经网络 (CNN) 的示意图。

### 4.1.2 构建卷积神经网络

通常，一个简单的 `CNN` 由三种主要类型的层构建组成：卷积层、池化层和全连接层，如图所示。下面详细介绍这些层。

#### 卷积层

![](img/image-e0661sn9.jpg)

图 4.3 卷积神经网络 (CNN) 架构示意图。

卷积层的原理是使用卷积核或滤波器在输入上滑动以学习特征。如图所示，将一个 `3 × 3` 的卷积核滑动到 `4 × 4` 的输入图像上，产生一个大小为 `2 × 2` 的输出特征图；第一次计算的输出为 7，计算公式为：

![](img/image-fr47mquo.jpg) ![](img/image-e3byzu0d.jpg) ![](img/image-b9fagtt6.jpg) ![](img/image-6dna1zp0.jpg)

图 4.4 卷积层中的计算。

卷积核的大小和数量是可调的超参数，大多数尺寸设置为奇数，如 `3 × 3`、`5 × 5` 或 `7 × 7`。由于卷积核过多也导致过拟合问题，因此必要调整此参数以选择最合适的一个。

#### 零填充

图 4.4 描述了卷积层的基本操作，在每次卷积之后，输出张量的大小与输入张量相比发生了变化。为了控制输出张量的大小，通过在输入张量周围进行零填充（zero-padding）来实现。大多数情况下，使用零填充来保留输入张量的大小。例如，通过在 `4 × 4` 输入的周围应用大小为 `1` 的零填充，输入大小变为 `6 × 6`，所示。然后在在 `6 × 6` 的输入上进行卷积核大小为 `3 × 3` 的卷积，输出量的大小为 `4 × 4`，与原始输入相同，所示。

![](img/image-ub6m89u7.jpg)

图 4.5 大为 1 的零填充。

![](img/image-w5uxufq2.jpg)

图 4.6 零填充的卷积操作。

#### 步长

步长控制卷积核在输入上的滑动方式。在普通卷积层中，使用步长值为 `1`，这意味着每次滑动一个像素。当步长大于 1 时（例如图中步长为 `2`），卷积每次移动 2 个像素，导致较小的输出张量。

![](img/image-qxlus9fc.jpg)

图 4.7 步长为 2 的卷积操作。

两种填充模式（same padding 和 valid padding）下卷积层输出大小的计算公式如下：

- 相同填充（same）：卷积后的输出大小与输入相同。
  ![](img/image-l21371tl.jpg) ![](img/image-272lbg9.jpg)
- 有效填充（valid）：卷积后的输出大小比输入小。
  ![](img/image-oi8pl4xf.jpg) ![](img/image-90fry7k.jpg)

其中：

- 输入大小
- 输出大小
- 卷积核大小或滤波器大小
- 卷积操作的步长

前面的示例是单通道和单个卷积核的计算，但实际上，卷积层是在多个通道和多个卷积核上执行计算的。例如，如图所示在 `4 × 4 × 3` 输入上进行卷积，深度显示为三种颜色：R (红)、G (绿) 和 B (蓝)。

- 有效填充：1
- 卷积核数量：2 (`W0` 和 `W1`)
- 卷积核大小：`3 × 3`
- 无偏置

![](img/image-c2sgrz0.jpg)

图 4.8 在大小为 `4 × 4 × 3` 的图像上进行卷积，具有两个卷积核 `W0` (`3 × 3 × 3`) 和 `W1` (`3 × 3 × 3`)。

卷积层的参数数量公式为：

- 输入的深度或通道数
- 卷积核的高度
- 卷积核的宽度
- 卷积核的数量
- 如果使用偏置，`bias = 1`，否则 `bias = 0`

示例 1：计算图中卷积层的参数数量。

![](img/image-km6m0p2n.jpg)

示例 2：创建一个，由大小为 `28 × 28 × 4` 的输入层和使用 32 个大小为 `3 × 3` 的卷积核的输出卷积层组成。网络设置为：`28 × 28 × 4`（高度、宽度和深度），有效填充：1，卷积核大小：`3 × 3`。构建 CNN 的代码：

![](img/image-dyawaera.jpg)

`CNN` 的参数数量可以通过 `model.summary()` 函数获得；它是 1184 个参数，所示。

![](img/image-vpmmj815.jpg)

图 4.9 卷积神经网络 (CNN)。

为了验证 `CNN` 的参数数量是否与所示 1184 一致，应用了上述参数计算。因为 `CNN` 只有一个卷积层，网络的参数数量就是卷积层的参数数量，计算为：

![](img/image-ga4ive4u.jpg)

所示，计算结果与通过 `model.summary()` 函数计算的参数数量一致。

**补充说明**

由于在 `CNN` 的卷积层中使用 sigmoid 激活函数在训练期间很容易遇到梯度消失问题，因此在当前的 `CNN` 中将此激活函数替换为修正线性激活 (ReLU) 函数以进行有效训练。第 5 章提供了更多关于 sigmoid 函数和 ReLU 函数对 `CNN` 性能的影响的信息。

#### 池化层

池化层通常紧接卷积层之后，以减少输入张量的空间尺寸（宽度和高度），从而减少 `CNN` 的计算并在训练过程中避免过拟合问题。池化层与输入的每个通道独立工作，因此通道数或深度维度保持不变，所示。存在一些池化层，如最大池化、平均池化和 L2 范数池化层。其中，采用最大操作的最大池化层在 `CNNs` 中最常用，因为它在实践中被证明更有效。图 4.11 中的示例是最大池化层的操作，大小为 `4 × 4` 的输入通过 `2 × 2` 的卷积核和步长 2 进行池化，产生大小为 `2 × 2` 的输出。

![](img/image-ngv80c0x.jpg)

图 4.10 池化层示意图。池化层在输入张量的每个通道中独立工作。

![](img/image-9kz3h0bb.jpg)

图 4.11 最大池化层的操作。

#### 全连接层

全连接层或密集层是 `CNNs` 的重要组件。该层的神经元与上一层的所有神经元全连接。它已成功应用于图像分类、语义分割等许多计算机视觉应用。在 `CNNs` 中，首先通过卷积层和池化层执行卷积和池化操作以从输入中提取特征。所得特征在发送到全连接层组合数据并驱动最终输出之前，被展平为一维特征向量，所示。如果神经网络仅由全连接层构建，则被称为全连接网络。全连接网络通常计算开销极大，且性能低于 `CNNs`。在下一节中，我们将同时应用全连接网络和 `CNN`。

![](img/image-3nixst6.jpg)

图 4.12 全连接层的连接。

### 4.1.3 卷积神经网络的操作

在 `CNNs` 中，每个卷积层都有从输入提取特征的卷积核，使用不同值的卷积核可以获得各种效果，所示卷积在开始时没有意义；它们的值在训练期间需要初始化和更新。

表 4.1

![](img/image-0CT97QD.jpg)

前面的描述只提到了有一个卷积层的网络。具有多层的 `CNNs` 是如何工作的？图 4.13 展示了深度 `CNN` 的操作，其中前几层卷积层（1-3 层）主要负责提取简单特征，如边缘、线条等。然后将所得特征发送到更深层层（4-6 层）以生成更具体的特征，如鼻子、眼睛和耳朵。最后，这些输出特征通过展平层展平为一维特征向量，然后输入全连接层进行最终预测。

![](img/image-ctcsukvx.jpg)

图 4.13 深度卷积网络。

图中显示了 `CNN` 特征可视化的示例，其中 ImageNet [2] 上训练的 VGG-16 [6] 网络和 DeconvNet [7] 用于获取结果。所示 VGG-16 网络的浅层（2 层）对线条和边缘的结合有反应。

![](img/image-5m6yrhsh.jpg)

图 4.14 训练的 VGG-16 模型第二层的特征可视化。

![](img/image-8qbt0p98.jpg)

图 4.15 训练的 VGG-16 模型第七层的特征可视化。

![](img/image-lnppp9jf.jpg)

图 4.16 训练的 VGG-16 模型第十五层的特征可视化。

图中 VGG-16 网络中间层（7 层）包含更复杂的不变性，提取类似的纹理，如月亮的形状、窗户和房屋。图中 VGG-16 网络的深层（15 层）呈现出显著的变性和更高的类别特异性，例如狗和猫的眼睛、耳朵，鸟的腿和姿态等。

## 4.2 多类别分类

### 4.2.1 多类别分类简介

在机器学习中，多类别分类是指将样本归类为三个或更多类别中的某一个的问题。与在该章介绍的二分类模型类似，多类别分类模型也用于对类别概率进行建模。然而，与二分类模型输出单一概率来将输入样本推断为两个类别之一不同，多类别分类模型为每个类别生成一个概率，其中输出概率分之和应等于 1，如图所示。基于预测的概率分，模型可以确定输入样本属于哪个目标类别。例如，给定一个分类三个类别的模型，在将样本输入模型后，它输出的类别 1 的概率分数为 0.7，类别 2 为 0.1，类别 3 为 0.2。这意味着模型认为输入样本有 70% 的置信度属于类别 1，10% 的置信度属于类别 2，20% 的概率属于类别 3。

![](img/image-7ypkeye2.jpg)

图 4.17 分类模型流程图。

### 4.2.2 多类别分类模型架构

如在该节介绍的，最先进的多类别分类模型基于 `CNNs`，它具有特征提取器和分类器两个主要部分，如图所示。

![](img/image-hw39h3oy.jpg)

图 4.18 基于 CNN 的多类别分类模型架构。

#### 特征提取器

特征提取器由卷积层和池化层组成，用于从输入中提取特征。分类器由全连接层组成，结合来自特征提取器的提取特征来执行最终的分类决策。为了实现这一目标，最后一个全连接层后面跟着 `softmax` 函数，用于计算每个目标类别的概率分。根据概率模型的描述，`softmax` 函数的每个输出值都在 0 到 1 之间，且所有输出值之和等于 1。`softmax` 函数表示为：

![](img/image-iidzcp2i.jpg)

例如，一个分类三个类别的模型（C = 3）在最后一层输出三个值 [3, 1, -3]，这些值通过 `softmax` 函数转换成分别为 0.88、0.12 和 0 的概率分，如图所示。基于这些输出概率分，输入样本显然属于第一类。

![](img/image-xz022oeq.jpg)

图 4.19 Softmax 输出计算。

#### 损失函数

如在前一章提到的，分类问题可以分为二分类问题和多类别分类问题。虽然二分类交叉熵（`BCE`）通常用作二分类模型的损失函数，但类别交叉熵（`CCE`）被用多类别分类模型的损失函数。`CCE` 损失函数是 `softmax` 函数和交叉熵（`CE`）函数的组合。它也被称为 softmax loss，如图所示。

![](img/image-y3y1q5gg.jpg)

图 4.20 类别交叉熵 (CCE)。

`CE` 的公式定义为：

![](img/image-5b65wyx.jpg)

`CCE` 的公式表示为：

![](img/image-0ttz9pw.jpg)

其中，$y$ 是期望输出，$\hat{y}$ 是模型的预测值，$f$ 是 `softmax` 函数，$C$ 是类别数量，$N$ 是一个批次的数据量。图 4.21 显示了计算 `CCE` 的示例。输出层后接 `softmax` 函数的神经网络以“cat”图像作为输入，输出预测结果 [0,0,0,0,0.6,0,0,0.1,0,0.3]。期望输出 [0,0,0,1,0,0,0,0,0] 与预测结果之间的误差使用以下公式计算：

![](img/image-2zxm9ppn.jpg)
![](img/image-wipcpnzd.jpg)
![](img/image-2n9pps4a.jpg)
![](img/image-8ma4x6rp.jpg)

图 4.21 使用类别交叉熵 (CCE) 的计算示例。

### 4.2.3 数据增强

在该章提到的，深度学习模型在训练过程中经常遇到过拟合问题。因此，使用了三种方法来防止这个问题：减小模型尺寸、权重正则化和丢弃（dropout）。处理过拟合问题的另一种方法是通过对可用数据应用不同的变换来增加训练数据的数量和多样性；这被称为数据增强。由于数据增强最常用于图像处理，因此也被称为图像增强。通过使用图像增强，数据量可以比原始数据增加两倍，如图所示。常见的图像变换技术包括：

- 翻转（flipping）
- 旋转（rotation）
- 平移（shifting）
- 缩放（scaling）
- 转换（对比度、饱和度或亮度等）
- 图像处理（高斯模糊或平均模糊等）
- 噪声（高斯噪声或盐椒噪声等）

![](img/image-ozhya9sx.jpg)

图 4.22 图像增强示例。

## 4.3 实验：CIFAR-10 图像分类

在本节中，我们使用 `CIFAR-10` 数据集来训练和评估多类别分类模型的性能。在训练过程中，我们分别使用 `CCE` 和 `Adam` 作为损失函数和优化器。网络模型在三种场景下实现：

- 全连接神经网络 (`FCNN`)
- 未应用图像数据增强技术进行模型训练的 CNN
- 运用了图像数据增强技术以增加训练数据量和多样性的 CNN

### 4.3.1 CIFAR-10 数据集介绍

`CIFAR-10` 数据集 `[14]` 包含 60,000 张尺寸为 `32 × 32` 的 RGB 图像，其中 50,000 张用于训练，10,000 张用于测试。`CIFAR-10` 包含 10 类：飞机、汽车、鸟、猫、鹿、狗、青蛙、马、船和卡车，如图所示。该数据集可以在官方网站下载：

![](img/image-ipewgw1w.jpg)

图 4.23 `CIFAR-10` 数据集。

### 4.3.2 TensorFlow datasets

数据集在深度学习中起着至关重要的作用，但不同的来源格式和复杂性使得将其加载到深度学习模型变得困难。为了解决这个问题，`TensorFlow` 提供了一系列即用的公共数据集，称为 `TensorFlow Datasets`。在 `TensorFlow Datasets` 中，所有数据集都以 `tf.data.Datasets` 的形式提供，支持易于使用和高度优化的输入流水线。这里我们展示了一个使用 `tf.data.Datasets` 加载数据的示例。

![](img/image-el1lw864.jpg)

有超过 60 个图像分类数据集。`TensorFlow Datasets` 上还提供了对象检测、问答、摘要等多个领域的数据集。请访问 `www.tensorflow.org/datasets/` 了解更多详情。在下一节中，我们将通过 `tf.data.Datasets` API 从 `TensorFlow Datasets` 加载 `CIFAR10` 数据集，用于训练和测试多类别分类模型。

### 4.3.3 代码示例

图 4.24 是多类别分类模型源代码的流程图。

- 数据
- 软件包

![](img/image-cwnrwb9a.jpg)

图 4.24 多类别分类模型源代码流程图。

![](img/image-huz91dzk.jpg) ![](img/image-gny66ib5.jpg)

读取与分析

![](img/image-ojbdtz7n.jpg) ![](img/image-qrjsk52x.jpg) ![](img/image-jyruz9oy.jpg)

#### CIFAR-10 信息

可以通过以下简单命令显示数据集的基本信息，如输入图像尺寸、类别数量、训练集样本数等：

![](img/image-i8xdpuw9.jpg) ![](img/image-iwi3304e.jpg) `CIFAR-10` 的 10 个类别

![](img/image-y7zx1q1d.jpg) 训练数据并计算每类的数量

![](img/image-nlkkg1ea.jpg) 图像

![](img/image-fcg0i30q.jpg) 划分

- 数据：将图像中的所有像素除以 255，将像素值缩放到 0 和 1 之间
- 数据：使用独热编码，例如，类别 2 表示为 `[0,0,0,0,0,0,0,0,1,0]`

![](img/image-1a2rttrh.jpg) 训练数据、验证数据和测试数据

![](img/image-mjvdcj8y.jpg) 增强（针对模型-3）

- 帮助函数
- 图像
  ![](img/image-dx90qehf.jpg) 水平翻转
  ![](img/image-ky5v31ox.jpg) 转换
  ![](img/image-jwulr8q5.jpg) 旋转
  ![](img/image-13q8k7ve.jpg) 图像

![](img/image-jrs2iedl.jpg) 用于训练和网络模型的数据

实现了三个多类别分类模型：

1. `FCNN`
2. 未应用数据增强技术进行训练的 CNN
3. 应用数据增强技术训练 `Model-2`

表 4.2 显示了 `Model-1`、`Model-2` 和 `Model-3` 的架构。

表 4.2

| | `FCNN` | `Model-1` | `Model-3` |
| :--- | :--- | :--- | :--- |
| 网络模型 | ![](img/image-d1kg0ry5.jpg) | ![](img/image-499x7d2m.jpg) | |
| 用于保存模型的存储目录 | ![](img/image-bh5noxh4.jpg) | 数据集：因为数据集之前设置过，所以需要重新加载 ![](img/image-3pjmu9s2.jpg) | |
| 回调函数 | ![](img/image-it1iu06o.jpg) ![](img/image-7xtgqono.jpg) ![](img/image-nw4vlreq.jpg) | | |
| 优化器、损失函数和指标函数 | | | |
| 数据：将图像中的所有像素除以 255，将像素值缩放到 0 和 1 之间 | | | |
| 增强：水平翻转图像、旋转图像、转换颜色和缩放图像 | | | |
| 数据：使用独热编码，例如，类别 2 表示为 `[0,0,0,0,0,0,0,0,1,0]` | | | |

# 第 5 章：神经网络训练

## 摘要

神经网络的训练是一个寻找合适权重集的过程，以实现在训练数据和验证数据上获得高性能。本章介绍了训练网络模型时使用的一些重要技术，包括反向传播、权重初始化和批次归一化。随后，我们检查了每种权重初始化技术的有效性，并通过将批次归一化应用于 CIFAR-10 数据集的神经网络模型训练，验证了其有效性。最后，我们通过 TensorBoard 上对第 4 章和本章中所有训练过的神经网络的性能进行了总结、比较和可视化，以观察每种技术对训练过程中模型收敛的影响。

## 关键词

反向传播；权重初始化；Glorot 初始化；He 初始化；批次归一化

## 目录

- 用于训练神经网络的反向传播算法
- 权重初始化的重要性
- 使用 TensorBoard 观察神经网络的权重分布
- 批次归一化的性
- 不同神经网络训练技术的有效性

## 5.1 反向传播

### 5.1.1 反向传播简介

反向传播（Backpropagation, BP）[1] 是一种结合梯度下降来更新神经网络权重的方法，我们在之前的章节中介绍过。梯度下降是用于神经网络进行优化的最常用算法之一。通过计算梯度并向反方向移动，可以在训练过程中减小网络预测结果与预期输出之间的误差。权重更新公式为：

![](img/image-cpxz2hdj.jpg)

其中 `L` 是损失函数，`η` 是学习率，`W` 是神经网络的权重。通过上述公式，`BP` 方法被用于计算每个输入和输出示例的损失函数相对于神经网络权重的梯度。以下是一个解释如何计算梯度的示例。

图 5.1 显示了带有前向传播计算的单层神经网络的示意图。其计算过程为：

![](img/image-jo1mgf5d.jpg) ![](img/image-nwimaqqw.jpg) ![](img/image-4d6sp5uk.jpg)

其中 `x` 和 `b` 是输入数据；`w` 是网络的权重；`f` 是激活函数；`ŷ` 是神经网络的预测值，`y` 是预期输出。

![](img/image-q5329bcl.jpg)

图 5.1 单层神经网络的前向传播计算图。

`BP` 用于计算梯度 `∂L/∂W` 并更新网络权重，如如图所示。其计算过程为：

![](img/image-265bu1et.jpg) ![](img/image-yzmxqdtg.jpg) ![](img/image-y2yf57xv.jpg) ![](img/image-i380z9pp.jpg)

图 5.2 单层神经网络的反向传播（BP）计算图。

### 5.1.2 梯度消失问题

梯度消失是指在训练神经网络时（尤其是使用梯度法和 `BP` 训练深层神经网络 DNNs 时）所会遇到的问题。表 5.1 列出了三种常见的激活函数：sigmoid、tanh 和正向线性单元（`ReLU`）。在神经网络的隐藏层中使用 `sigmoid` 和 `tanh` 激活函数可能会导致梯度消失问题。例如，当通过 `sigmoid` 激活函数层执行 `BP` 时，需要与 `sigmoid` 函数的梯度相乘。`sigmoid` 导数的最大值为 0.25，这意味着梯度在一次传递后将衰减 0.25 倍。如果神经网络有五层，梯度将至少减少 0.25⁵，这使得难以更新神经网络的前层权重。同样，`tanh` 激活函数也存在这种情况。最近，隐藏层通常采用 `ReLU` 激活函数，因为它在输入为正时直接输出输入，否则输出零，从而克服梯度消失问题，并允许神经网络学习得更快、更有效。

表 5.1

这里我们解释在神经网络中使用 `sigmoid` 激活函数时的梯度消失。假设有一个双层神经网络，每层都使用 `sigmoid` 激活函数计算输出值，输入权重 `w` 和 `b` 以及预期输出 `y`，图 5.3 显示了带有前向传播计算的网络示意图。其计算过程为：

![](img/image-2mzto0i7.jpg) ![](img/image-gw8av86g.jpg) ![](img/image-szngovj4.jpg) ![](img/image-bel9vnco.jpg) ![](img/image-wmo5sslq.jpg)

这里

![](img/image-zwtxgtzr.jpg) ![](img/image-yijxy26b.jpg)

图 5.3 双层神经网络的前向传播计算图。

如图所示，`∂L/∂w` 是通过 `BP` 方法计算的，其计算过程为：

![](img/image-7r45azuw.jpg) ![](img/image-amo05uxo.jpg) ![](img/image-tfenb475.jpg) ![](img/image-as86root.jpg)

图 5.4 双层神经网络的反向传播（BP）计算图。

从上述 `BP` 的计算可以发现，在每个 `sigmoid` 激活函数之后，计算值将至少减少 0.25 倍，因此传输层越多，梯度衰减就越严重。这就是训练 `DNNs` 期间梯度消失的原因。

`ŷ` 的计算结果通过使用 `TensorFlow` 程序进行了验证，如下所示。

![](img/image-cpxukezq.jpg)

## 5.2 权重初始化

权重初始化在神经网络的训练中起着至关重要的作用，因为它直接影响模型的收敛。在本节中，我们将介绍并分析三种权重初始化方法，以及它们对构建神经网络的影响。在接下来，我们将简要描述这三种不同的权重初始化方法。

- 正态分布初始化（distribution initialization）：正态分布的最简单情况是当参数 `μ`（均值）设置为 0 且参数 `σ`（标准差）设置为 1 时，称为标准正态分布。在下面的实验中，使用带有 sigmoid 激活函数的神经网络来分析 `μ = 0` 和 `σ = 1` 的正态分布，以及 `μ = 0` 和 `σ = 0.01` 的正态分布。最终分析结果显示，`μ = 0` 和 `σ = 1` 的正态分布是梯度消失的原因。
- Glorot 初始化（Glorot initialization）：这种方法通过尝试保持神经网络所有层中梯度规模大致相同，来改进正态分布初始化方法的问题。然而，对于使用 ReLU 激活函数的深度神经网络（DNN），使用 Glorot 初始化在训练过程中仍然会出现梯度消失现象。
- He 初始化（initialization）：这种方法解决了在 DNN 中采用 ReLU 激活函数时使用 Xavier 或 Glorot 初始化出现的问题，通过使每层的输出分布更加均匀来实现。

下面将详细介绍并分析每种初始化方法在训练和开发神经网络中的影响。我们还列出了程序示例所需的各种包。

![](img/image-84728uz3.jpg)

### 5.2.1 正态分布

**带有 sigmoid 激活函数的神经网络以及 `μ = 0` 和 `σ = 1` 的正态分布**

为了构建模型，使用了以下网络层：

- 形状为 `(100,)` 的输入层。
- （全连接层）：使用 `sigmoid` 作为激活函数，并采用 `μ = 0` 和 `σ = 1` 的正态分布进行权重初始化；不使用偏置。

![](img/image-gbr56g8v.jpg)

结果显示，大部分输出值分布在 0 和 1 附近。应用 `BP`（请参考表中的 sigmoid 函数导数）时，梯度值将趋于零，导致梯度消失问题。因此，`μ = 0` 和 `σ = 1` 的正态分布并不是一种有效的权重初始化方法。

**带有 sigmoid 激活函数的神经网络以及 `μ = 0` 和 `σ = 0.01` 的正态分布**

为了构建模型，使用了以下网络层：

- 形状为 `(100,)` 的输入层
- （全连接层）：使用 `sigmoid` 作为激活函数，并采用 `μ = 0` 和 `σ = 0.01` 的正态分布进行权重初始化；不使用偏置

![](img/image-n9xdpwmh.jpg)

结果显示，第二层的输出值大多分布在 0.5 左右，应用 `BP`（请参考表中的 sigmoid 函数导数）时梯度值将在 0.25 左右。虽然梯度问题得到了改善，但在由许多卷积层组成的深度网络中，它仍然可能发生。

### 5.2.2 Glorot 初始化

**带有 Glorot 初始化和 sigmoid 激活函数的神经网络**

Glorot 等人 [6] 在 2010 年提出了 Glorot 初始化方法。它在许多 DNN 中被广泛使用，并被视为 `Keras` 中的默认权重初始化方法。为了构建模型，使用了以下网络层：

- 形状为 `(100,)` 的输入层
- （全连接层）：使用 `sigmoid` 作为激活函数，并采用 Glorot 方法进行权重初始化；不使用偏置

![](img/image-l9h1s9j.jpg)

结果显示，Glorot 初始化方法产生的输出分布比正态分布方法更宽。这有助于防止训练过程中的梯度消失，并允许神经网络学习数据。因此，对于带有 sigmoid 或 tanh 激活函数的神经网络，建议使用 Glorot 权重初始化方法。

**带有 Glorot 初始化和 ReLU 激活函数的神经网络**

为了构建模型，使用了以下层：

- 形状为 `(100,)` 的输入层
- （全连接层）：使用 `ReLU` 作为激活函数，并采用 Glorot 进行权重初始化；不使用偏置。

![](img/image-oeg7q95l.jpg)

结果显示，当网络模型的层数增加时，深层的输出分布更接近 0，这可能在训练过程中导致梯度消失问题。因此，不建议对使用 ReLU 激活函数的 DNN 使用 Glorot 权重初始化方法。

### 5.2.3 He 初始化

**带有 He 初始化和 ReLU 激活函数的神经网络**

何恺明 [7] 在 2015 年提出了 He 初始化方法。事实证明，在使用带有 ReLU 激活函数的 DNN 时，该方法对于防止梯度消失问题是非常有效的。为了构建模型，使用了以下层：

- 形状为 `(100,)` 的输入层
- （全连接层）：使用 `ReLU` 作为激活函数，并采用 He 方法进行权重初始化；不使用偏置

![](img/image-9lg5y64i.jpg)

结果显示，当带有 ReLU 激活函数的深度网络使用 He 初始化方法时，每层的输出分布都非常均匀。成功解决了在带有 ReLU 激活函数的 DNN 中使用 Glorot 初始化方法的问题。

以下点总结了本节的知识：

- 使用带有 sigmoid 或 tanh 激活函数的神经网络时，建议使用 Glorot 方法进行权重初始化。
- 使用带有 ReLU 激活函数的神经网络时，建议使用 He 方法进行权重初始化。
- 使用 ReLU 激活函数的网络通常比带有 sigmoid 或 tanh 激活函数的 DNN 获得更好的性能。

## 5.3 批量归一化

### 5.3.1 批量归一化简介

Ioffe 和 Szegedy [8] 于 2015 年提出了批量归一化算法。它允许使用高学习率来加速神经网络的训练，同时减少了对权重初始化的依赖。在训练神经网络时，网络层的输出分布会发生变化。后层必须不断适应前一层输出分布的变化，也就是说每一层都需要根据前一层的输出分布进行调整。这导致神经网络由于需要仔细的权重初始化和较低的学习率，使得权重更新得非常缓慢。

为了解决这个问题，批量归一化的核心思想是对神经网络每一层的每批次（batch）输入数据和输出进行归一化处理。

如图所示，网络层的输出均匀地分布在 −10 到 10 之间。在通过 `tanh` 激活函数后，输出分布不再均匀；大多数输出值分布在 −1 和 1 附近，这会导致梯度消失问题（参见表中的 `tanh` 函数数）。如图，网络层的输出首先被归一化到 -2 到 2 的范围内，然后通过 `tanh` 激活函数，与未使用归一化的情况相比，产生了更均匀的输出分布。

![](img/image-m2rj6tmd.jpg)

图 5.5 使用归一化与未使用归一化的输出分布对比。

对于输入的批次数据，批量归一化变换通过四个步骤表示：

1. 计算批次的均值：
   ![](img/image-yvtbhm9.jpg)
2. 计算批次的方差：
   ![](img/image-ctuo5wc9.jpg)
3. 归一化值：
   ![](img/image-savhv3hl.jpg)
   其中 `ε` 是为了数值稳定性性的常数。
4. 缩放和位移：
   ![](img/image-bqyg4lke.jpg)
   其中 yᵤ 表示批量归一化变换的输出，α 和 β 是需要学习的参数。

通过在神经网络中添加批量归一化变换，可以对任何激活函数进行处理。在下一节中，我们将介绍批量归一化在神经网络中的位置。

以下点总结了批量归一化的优点：

- 通过使用学习率加速神经网络的训练
- 减少神经网络训练中的过拟合问题
- 减少梯度消失和梯度爆炸问题
- 消消了使用 dropout 技术防止数据信息丢失的需求

### 5.3.2 带有批量归一化的神经网络

批量归一化已成功应用于神经网络，以提高各种计算机视觉应用的性能，如图像分类、图像识别、目标检测、图像到翻译等。带有批量归一化的神经网络与普通神经网络略有不同，其中批量归一化的位置位于卷积层和激活函数之间，如图所示。

![](img/image-f82uxsol.jpg)

图 5.6 带有批量归一化的卷积神经网络结构。

在这里，我们展示了一个在神经网络中添加批量归一化的代码示例。

![](img/image-aapsd66w.jpg)

## 5.4 实验 1: 三种权重初始化方法的验证

本节延续了书中关于 CIFAR-10 图像分类的话题。为了验证每种权重初始化方法的有效性，实现了三种构建神经网络的场景：

- 使用正态分布（$\mu = 0$ 和 $\sigma = 0.01$）的神经网络
- 使用 Glorot 权重初始化的神经网络
- 使用 He 权重初始化的神经网络

`Model-1`、`Model-2` 和 `Model-3` 具有相同的架构，并在隐藏层中使用 `ReLU` 激活函数。

### 5.4.1 代码示例

图 5.7 显示了在 CIFAR-10 数据集上构建和测试三个模型的源代码流程图。

- 数据
- 图像增强函数

![](img/image-ehne57by.jpg)

图 5.7 CIFAR-10 图像分类源代码的流程图。

由于书中后续章节将使用图像增强技术，因此在此处创建了一个包含图像增强函数的 Python 文件。若要使用该技术，直接在程序中导入其函数即可。

- 文件：在 Jupyter 中创建一个文件，如图 5.8 所示

![](img/image-overwod9.jpg)

图 5.8 创建文件。

将文件名更改为 `preprocessing.py`，如图 5.9 所示

![](img/image-gemkimdj.jpg)

图 5.9 修改文件名。

![](img/image-a2wz34bc.jpg) ![](img/image-982ohigw.jpg) ![](img/image-35f8jmh6.jpg) ![](img/image-kegruizn.jpg) 和训练网络模型

实现了三个具有相同的 CIFAR-10 图像分类模型。表 5.2 列出了每个模型的架构和描述。

表 5.2

| 5.2 | 5.2 | 5.2 | 5.2 |
| :--- | :--- | :--- | :--- |

![](img/image-fmp77ycv.jpg) ![](img/image-bmzspehh.jpg) ![](img/image-xmwwwagj.jpg) 结果

![](img/image-6lvi12nt.jpg)

结果显示，使用 `ReLU` 激活函数和 `He` 权重初始化的 `Model-3` 达到了最高精度，其次是使用 `Glorot` 初始化的 `Model-2` 和使用正态分布（$\mu = 0$ 和 $\sigma = 0.01$）的 `Model-3`。

### 5.4.2 使用 TensorBoard 可视化权重分布

TensorBoard 提供两种数据分布可视化工具：`DISTRIBUTIONS` 和 `HISTOGRAMS`。在训练网络时，`tf.keras.callbacks.TensorBoard` 函数的 `histogram_freq` 参数设置为 1，这意味着将记录每个训练轮次（epoch）中每一层的权重分布，可以使用 `DISTRIBUTIONS` 和 `HISTOGRAMS`。

以下内容直接使用上节中带有三种不同权重初始化方法的三个模型的训练结果（包括 `He` 初始化、`Glorot` 初始化和正态分布（$\mu = 0$ 和 $\sigma = 0.01$），通过 TensorBoard 可视化并分析权重分布的变化。

进入存储“lab5-logs”的目录，然后通过下面的命令行打开 TensorBoard 查看训练记录。

![](img/image-7ft5r76g.jpg)

使用正态分布初始化的 `Model-1` 的权重分布

`DISTRIBUTIONS` 工具

图 5.10 显示了 `Model-1` 在 100 个 epoch 中的权重变化，其中 x 轴为时间轴，y 轴为权重分布的范围。可以观察到第一、二卷积层的权重分布变化很小。显然，网络权重完全没有更新。

`HISTOGRAMS` 工具

![](img/image-j6mbx2e9.jpg)

图 5.10 DISTRIBUTIONS 显示了正态分布（$\mu = 0$ 和 $\sigma = 0.01$）下 `Model-1` 在 100 个 epoch 中的权重变化，其中 x 轴为时间轴，y 轴为权重分布的范围。可以观察到第一、二卷积层的权重分布变化很小。显然，网络权重完全没有更新。

## 5.6 不同神经网络的比较

在本节中，我们总结并比较了第 4 章和本章中所有神经网络的性能。表 5.4 显示了在 CIFAR-10 数据集上评估的模型架构和准确率。所示，带有批归一化和 Glorot 权重初始化的卷积神经网络（`Lab 5 Model-4`）在准确率方面优于其他模型。

### 表 5.4

图像增强；随机正态分布初始化；Glorot 均匀初始化；Glorot 正态初始化；He 正态初始化；批归一化。

可以通过 TensorBoard 观察第 4 章和本章中模型的训练结果，如图所示。注意，在打开 TensorBoard 时，`logdir` 后面需要两个日志文件。

![](img/image-ashr71f8.jpg)

图 5.16 神经网络在 CIFAR-10 数据集上的训练结果。

![](img/image-wodg27sv.jpg)

### 参考文献

[1] Rumelhart D.E., Hinton G.E., Williams R.J. Learning representations by back-propagation 1986;323:533–536.
[2] Mishkin D., Matas J. All you need is a good In: Proc. International Conference on Learning 2016:3013–3018.
[3] Xie D., Xiong J., Pu S. All you need is beyond a good init: exploring better solution for training extremely deep convolutional neural networks with orthonormality and Proc. IEEE Conf. Comput. Vis. Pattern Recognit. 2017;6176–6185.
[4] Salimans T., Kingma D.P. Weight normalization: a simple reparameterization to accelerate training of deep neural Adv. Neural Inf. Proces. Syst. 2016;901–909.
[5] Masood S., Doja M.N., Chandra P. Analysis of weight initialization methods for gradient descent with In: International Conference of Soft Computing Techniques and 2015:131–136.
[6] Glorot X., Bengio Y. Understanding the difficulty of training deep feedforward neural In: Proc. Conf. Artificial Intelligence and 2010:249–256.
[7] He K., Zhang X., Ren S., Sun J. Delving deep into rectifiers: surpassing human-level performance on ImageNet In: IEEE International Conference on Computer 2015:1026–1034.
[8] Ioffe S., Szegedy C. Batch normalization: accelerating deep network training by reducing internal covariate In: International Conference on Machine 2015:448–456.
[9] Huang G., Liu Z., Van Der Maaten L., Weinberger K.Q. Densely connected convolutional In: Proceedings of the IEEE Conference on Computer Vision and Pattern 2017:4700–4708.
[10] He K., Zhang X., Ren S., Sun J. Deep residual learning for image In: Proceedings of the IEEE Conference on Computer Vision and Pattern 2016:770–778.
[11] Le T., Huang S., Jaw D. Cross-resolution feature fusion for fast hand detection in intelligent homecare IEEE Sens. J. 2019;19:4696–4704.
[12] Isola P., Zhu J.-Y., Zhou T., Efros A.A. Image-to-image translation with conditional adversarial In: Proceedings of the IEEE Conference on Computer Vision and Pattern 2017:1125–1134.

# 第 6 章：高级 TensorFlow

## 摘要

尽管 TensorFlow 的高级 Keras 应用程序接口（API）使得构建和训练神经网络模型变得简单，但它仍然存在局限性。例如，作者在最新论文中提出的所有新网络层或损失函数并没有包含在高级 API 中，因此这些层和损失函数无法用于构建新的网络模型。在本章中，我们引入了高级 TensorFlow 技术，展示了如何为特定目的定制 API，例如自定义网络层、自定义损失函数、自定义指标函数和自定义回调函数。然后，我们提供了两种构建用于多类别分类神经网络的场景。在第一种情况下，我们应用了高级 Keras API；在第二种情况下，我们使用 TensorFlow 的自定义 API。

## 关键词

Keras API；自定义 API；网络层；损失函数；指标函数；回调

## 提纲

- 使用 TensorFlow 创建自定义 API
- 在设计神经网络时使用高级 Keras API 和 TensorFlow 自定义 API 的益处
- 使用高级 Keras API 和 TensorFlow 自定义 API 的神经网络

## 6.1 进阶 TensorFlow

之前的章节介绍了如何通过以下步骤使用 `tf.keras` API 来构建和训练用于线性回归、二分类和多类别分类的神经网络模型：

- 网络模型的输入：`tf.keras.Input()`
- 网络的层：`tf.keras.layers()`
- 网络模型：`tf.keras.Model()`
- 优化器、损失函数和指标函数：`model.compile()`
- 网络模型：`model.fit()`

虽然 TensorFlow 的高层 Keras API 使构建和训练神经网络模型变得非常非常简单，但它仍然存在局限性。例如，并不是所有问题的损失函数都包含在高级 API 中，因此这些损失函数无法用于训练新的网络模型。在本节中，我们将演示高级 TensorFlow 技术，以展示如何针对以下特定目的自定义 API：

- 网络层：如何创建一个新的网络层
- 损失函数：如何创建一个新的损失函数
- 指标函数：如何创建一个新的指标函数
- 回调函数：如何创建一个新的回调函数

### 6.1.1 自定义网络层

TensorFlow 提供的网络层类型非常多样，包括：

- 卷积层：`Conv1D`, `Conv2D`, `Conv3D`, `SeparableConv2D`, `DepthwiseConv2D`, `Conv2DTranspose` 等
- 池化层：`MaxPooling1D`, `MaxPooling2D`, `AveragePooling2D`, `GlobalMaxPooling2D` 等
- 合并层：`Add`, `Subtract`, `Multiply`, `Concatenate`, `Maximum` 等
- 激活层：线性整流单元（`ReLU`）、`LeakyReLU`, `PReLU` 等
- 循环层：`RNN`, `GRU`, `LSTM`, `ConvLSTM2D` 等
- 归一化、丢弃（dropout）等

如果 TensorFlow 中没有定义某类型的网络层，可以通过继承 `tf.keras.layers.Layer` 类来创建一个新的自定义层。以下是创建自定义层的模板。

![](img/image-hkwj4hfi.jpg)

TensorFlow 关 Keras 层 API 的官方文档位于：`www.tensorflow.org/versions/r2.0/api_docs/python/tf/keras/layers`

### 6.1.2 自定义损失函数

在设计用于分类、识别、回归等各种问题的神经网络模型时，有许多损失函数可以选择。TensorFlow 提供的损失函数不足以处理所有问题。因此，如果 TensorFlow 中没有用于解决特定问题的损失函数，则有必要定义一个新的。以下是创建自定义损失函数的模板。

![](img/image-0ud0j59g.jpg)

可以通过以下地址访问 TensorFlow 提供的官方损失函数：`www.tensorflow.org/versions/r2.0/api_docs/python/tf/keras/losses`

### 6.1.3 自定义指标函数

指标函数用于评估神经网络模型的质量，每个任务的每个指标都是不同的。例如，交并比（`IoU`）指标用于语义分割模型，平均精度均值（`mAP`）指标用于目标检测模型，而峰值信噪比（`PSNR`）和结构相似性指数（`SSIM`）指标用于图像增强模型，如去雾模型、去雾模型等。如果 TensorFlow 中没有可用的指标函数，可以通过继承 `tf.keras.metrics.Metric` 类来创建一个。以下是创建自定义指标函数的模板。

![](img/image-f506ehqa.jpg)

可以通过以下地址访问 TensorFlow 提供的官方指标函数：`www.tensorflow.org/versions/r2.0/api_docs/python/tf/keras/metrics`

### 6.1.4 自定义回调函数

回调是在训练神经网络模型过程中在各个阶段执行操作的强大工具。例如，使用回调可以帮助在每个训练轮次（epoch）后写入 TensorBoard 日志来监控损失和指标，通过早停（early stopping）防止过拟合，保存最佳模型权重等。TensorFlow 中可用的常用回调有：

- 监控值并存储最佳模型权重
- 如果模型的监控值长时间内没有改进，则提前终止训练
- 如果模型的监控值在长时间内没有改进，则降低学习率
- 在训练过程中记录模型的权重、计算图结构等

如果 TensorFlow 未提供某个回调，可以通过继承 `tf.keras.callbacks.Callback` 类来创建一个。以下是创建自定义回调的模板。

![](img/image-oenbcv06.jpg)
![](img/image-9ep47c6b.jpg)

可以通过以下地址访问 TensorFlow 提供的官方回调函数：`www.tensorflow.org/versions/r2.0/api_docs/python/tf/keras/callbacks`

## 6.2 使用 TensorFlow 的高层 Keras API 和自定义 API

本节通过示例详细介绍 TensorFlow 自定义 API 和高层 Keras API 的更多细节。每个示例都使用这两种方法实现，以展示每种方法的优势。虽然高层 Keras API 经过优化且易于使用，但自定义 API 在构建神经网络方面非常灵活。

### 6.2.1 网络层

在本节中，我们使用 TensorFlow 的高层 Keras API 和自定义网络层来创建一个卷积层。卷积层的参数如下：

- 卷积核数量：64
- 尺寸：$3 \times 3$
- 步长（stride）：1
- 填充（padding）：valid
- 激活函数：`ReLU`
- 初始化：Glorot 初始化
- 偏置初始化：zeros

以下两种方法创建的卷积层具有相同的功能。

![](img/image-j3zzp10.jpg)

### 6.2.2 损失函数

本节使用高层 Keras API 和自定义损失函数建立分类交叉熵（`CCE`）损失函数。CCE 的公式为：

![](img/image-u1na7ci.jpg)

其中 `y` 是期望输出，即模型的预测结果，`f` 是 softmax 函数，`C` 是类别数量，`N` 是批次中的数据量。以下两种方法创建的损失函数具有相同的功能。

![](img/image-mqxl150.jpg)

尽管第二方法创建的自定义交叉熵（`CCE`）损失函数可以工作，但在实践中它会被官方函数 `tf.nn.softmax_cross_entropy` 代替。这是因为官方 API 经过优化，因此训练更快、更稳定。

![](img/image-yh78v11f.jpg)

### 6.2.3 指标函数

指标是判断模型性能的函数。TensorFlow 许多性能判断指标，如二进制准确率、分类准确率、稀疏分类准确率、top-k 分类准确率、稀疏 top-k 分类准确率等。在本节中，我们使用高层 Keras API 和自定义指标函数创建分类准确率，计算预测值与独热标签的匹配情况。以下两种方法创建的指标函数具有相同的功能。

![](img/image-m29crsjh.jpg)
![](img/image-p26wwp4t.jpg)

**补充说明**

分类准确率计算的示例

![](img/image-nwp94soh.jpg)

### 6.2.4 回调函数

本节介绍了在训练过程中保存神经网络最佳权重的两种方法。第一方法使用高层 Keras API 的回调，而第二方法采用 TensorFlow 的自定义回调函数。以下两种方法创建的回调具有相同的功能。

![](img/image-ui8gg5l8.jpg)
![](img/image-6iwcf1oi.jpg)

图 6.1 展示了由 TensorFlow Keras API 生成的保存权重文件示例。

![](img/image-i2kma112.jpg)

图 6.1 保存的模型权重文件。

## 6.3 实验：使用高级 Keras API 和自定义 API 实现两个网络模型

在本节中，我们展示了构建多类别分类神经网络的两种场景。在种场景中，我们使用 TensorFlow 的高级 Keras API 来创建网络模型，命名为 `Model-1`。在第二种场景中，我们使用 TensorFlow 的自定义 API 构建网络模型，命名为 `Model-2`。`Model-1` 和 `Model-2` 在 CIFAR-10 数据集上分别进行训练以比较性能。图 6.2 是构建 `Model-1` 和 `Model-2` 的源代码流程图。

![](img/image-fch1gsp4.jpg)

图 6.2 使用高级 Keras API 和自定义 API 构建多类别分类模型的源代码流程图。

![](img/image-frmi9fyj.jpg) ![](img/image-lpabqz5i.jpg)

`Model-1` 和 `Model-2` 具有相同的架构，如表所示。虽然 `Model-1` 是使用 TensorFlow 的高级 Keras API 构建的，但 `Model-2` 是使用 TensorFlow 的自定义 API 构建的。

表 6.1

![](img/image-9xbrvd8x.jpg) ![](img/image-aeirf9a5.jpg) ![](img/image-v9nw8gg0.jpg) ![](img/image-ch5hmr8v.jpg) ![](img/image-uury53sv.jpg)

### 补充说明

`Model-1` 和 `Model-2` 在输出层没有使用 softmax 激活函数，因为 `Model-1` 的内置损失函数 `keras.losses.CategoricalCrossentropy()` 的参数 `from_logits` 被设置为 `True`，而 `Model-2` 的自定义损失函数使用了 `tf.nn.softmax_cross_entropy_with_logits()` 函数，该函数已经采用了 softmax 来计算 CCE 损失。因此，如果在此模型的输出层附加 softmax 激活函数，输出值将通过 softmax 函数计算两次。

![](img/image-6jiykwsb.jpg) ![](img/image-jui8snja.jpg) ![](img/image-v8l5g9m0.jpg) ![](img/image-0o07qz58.jpg) ![](img/image-b052isqo.jpg) ![](img/image-634qau5.jpg)

实验结果显示，两个模型的准确率接近。这证实了使用 TensorFlow 的自定义 API 设计神经网络可以获得与使用高级 Keras API 相似的结果，同时更具活性。

# 第 7 章：高级 TensorBoard

## 摘要

TensorBoard 是 TensorFlow 的官方工具包，为设计神经网络和机器学习实验提供了所需的可视化支持。`tf.keras.callbacks.TensorBoard` 函数在支持训练过程中神经网络的各种状态和统计信息方面存在限制。本章介绍了如何使用 TensorFlow 的 `tf.summary` 模块编写摘要数据并在 TensorBoard 上显示，提供了许多应用程序接口（API），如 `tf.summary.scalar`、`tf.summary.image`、`tf.summary.text`、`tf.summary.audio` 和 `tf.summary.histogram`。为了帮助读者深入使用 TensorBoard，我们展示了可视化神经网络训练结果的两种场景。在第一场景中，我们应用 `tf.summary.image` API 来观察图像结果。在第二场景中，我们使用带有 HParams Dashboard 的超参数调优技术，为特定问题的网络模型设计识别最合适的超参数（学习率、优化器、权重初始化方法等）。

**关键词：**

TensorBoard；超参数调优；`tf.summary`；HParams Dashboard；可视化工具；训练结果

## 大纲

- TensorBoard 以及用于写入数据（如文本、音频和图像）的底层应用程序接口（API）
- 通过结合 `tf.summary.image` API 和自定义回调，在 TensorBoard 上输出训练过程中神经网络图像
- TensorBoard 中的 HParams Dashboard，用于为特定问题的神经网络设计识别最合适的超参数

## 7.1 高级 TensorBoard

TensorBoard 是 TensorFlow 的官方工具包，为设计神经网络和进行机器学习实验提供了所需的可视化支持。第 2 章和第 5 章介绍了四个可视化函数的使用，包括 `Scalars`标量、`Graphs`图、`Distributions`分布和 `Histograms`直方图，只需使用 `tf.keras.callbacks.TensorBoard` 即可完成设置。然而，高级 Keras API 中的 `tf.keras.callbacks.TensorBoard` 函数在提供神经网络训练过程中各种状态和统计信息方面存在限制。例如，在 TensorBoard 的 `Scalars` 板中，只能观察到 `loss` 和 `accuracy` 等关键指标，以及它们随训练过程的变化情况。如果我们想观察和分析训练期间网络模型的输出结果（如图像、文本等），则需要使用自定义函数。本章介绍了如何使用 TensorFlow 的 `tf.summary` 模块编写摘要数据并在 TensorBoard 上显示，该模块提供了以下 API：

- 写入标量摘要，例如损失函数值、准确率值或学习率
- 写入图像摘要
- 写入文本摘要
- 写入音频摘要
- 写入直方图摘要

下节将介绍 `tf.summary` 模块的使用。

![](img/image-8b16k8g4.jpg)

TensorBoard 结果：通过命令行打开 TensorBoard 查看结果，如图所示。由于数据尚未写入日志文件，因此没有对应的数据仪表板激活。

![](img/image-trteowa7.jpg)

图 7.1 TensorBoard 接口。

![](img/image-nm4ubp68.jpg)

可以在此处访问 `tf.summary` 模块详情：`www.tensorflow.org/versions/r2.0/api_docs/python/tf/summary`

### 7.1.1 tf.summary.scalar

`tf.summary.scalar` 是 `tf.summary` 模块的一个 API，用于写入标量摘要，如损失值、准确率值等。这些值可以通过 TensorBoard 的标量仪表板显示，以便进行观察和监控。图 7.2 展示了使用高级 Keras API 中的函数 `tf.keras.callbacks.TensorBoard` 获取的神经网络在训练期间的损失和平均绝对误差值变化。如果需要写入和监控其他标量值，建议使用 `tf.summary.scalar`。`tf.summary.scalar` 的语法表达式如下：

![](img/image-rrq3swz1.jpg)

图 7.2 标量仪表板。

![](img/image-zmicrk88.jpg)

以下是使用 `tf.summary.scalar` API 在 TensorBoard 上写入并视化正弦函数的示例。图 7.3 显示了结果。

![](img/image-25mce4gs.jpg)

图 7.3 标量仪表板上的正弦。

![](img/image-zeq3ovsz.jpg)

### 7.1.2 tf.summary.image

`tf.summary.image` 是 `tf.summary` 模块的一个 API，用于写入图像摘要。其结果可以显示在 TensorBoard 的图像仪表板上。`tf.summary.image` 的语法表达式如下：

![](img/image-8ksyertg.jpg)

下面的程序示例解释了如何使用 `tf.summary.image` API。请从下方链接下载测试图像并解压到根目录下。`https://drive.google.com/open?id=1cC45twI3a5AkBYYE6Qb3ZV3uCPlw9eL6`

- 读取一个图像 (`airplane.png`)

![](img/image-6e0gqjlm.jpg)

将一个图像写入日志文件并在 TensorBoard 上显示，如图 7.4 所示。

![](img/image-cbs39de2.jpg)

图 7.4 在图像仪表板上观察由 `tf.summary.image` 写入的图像。

![](img/image-5vyaq39i.jpg)

将 `airplane_zoom.png`、`plane_flip.png`、`plane_color.png`、`plane_rot.png` 和 `plane.png` 等图像同时写入日志文件并在 TensorBoard 上显示，如图 7.5 所示。

![](img/image-j764w2y0.jpg)

图 7.5 在图像仪表板上观察由 `tf.summary.image` 写入的多张图像。

![](img/image-yzetzy3y.jpg)

分步将包括 `airplane_zoom.png`、`airplane_flip.png`、`airplane_color.png`、`airplane_rot.png` 和 `airplane.png` 在五张图像写入日志文件并在 TensorBoard 上显示，如图 7.6 所示。

![](img/image-efs11eup.jpg)

图 7.6 在图像仪表板上分步观察由 `tf.summary.image` 写入的图像。

![](img/image-vzyqm8kl.jpg)

### 7.1.3 tf.summary.text

`tf.summary.text` 是 `tf.summary` 模块的一个 API，负责写入文本摘要。其结果可以通过 TensorBoard 的文本仪表板显示。`tf.summary.text` 的语法表达式如下：

![](img/image-j2a2w6ik.jpg)

参数：

- 文本摘要的名称
- 字符串值
- 显式的单调递增步值
- 文本摘要的可选描述

下面的程序示例解释了如何使用 `tf.summary.text`。将文本数据写入日志文件并在 TensorBoard 上显示，如图 7.7 所示。

![](img/image-e0ufd.jpg)

图 7.7 在文本仪表板上观察由 `tf.summary.text` 写入的文本。

![](img/image-ex5tky.jpg)

### 7.1.4 tf.summary.audio

`tf.summary.audio` 是 `tf.summary` 模块的一个 API，用于写入音频摘要。其结果可以显示在 TensorBoard 的音频仪表板上。`tf.summary.audio` 的语法表达式如下：

![](img/image-tn1pik.jpg)

参数：

- 音频摘要的名称
- 形状为 `(n, m, c)` 的张量数据，其中 `n`, `m` 和 `c` 分别表示音频数量、帧数和通道数
- 表示采样率的整数
- 显式的步值
- 表示每步发射音频数量，默认值为三
- 常量字符串，表示音频格式，如 `wav`、`mp3` 等
- 音频摘要的可选描述

下面的程序示例解释了如何使用 `tf.summary.audio`。请从下方链接下载测试音频并解压到根目录下：`https://drive.google.com/open?id=1V4nNQ-ZQMBUezFWZo62dRevUGP`

![](img/image-806vjkap.jpg)

将音频写入日志文件并在 TensorBoard 上显示，如图 7.8 所示。

![](img/image-qybymb.jpg)

图 7.8 在音频仪表板上观察由 `tf.summary.audio` 写入的音频。

![](img/image-v5hnpsvu.jpg)

### 7.1.5 tf.summary.histogram

`tf.summary.histogram` 是 `tf.summary` 模块的一个 API，用于写入直方图摘要。其结果可以显示在 TensorBoard 的直方图仪表板和分布仪表板上。`tf.summary.histogram` 的语法表达式如下：

![](img/image-ivi2al8w.jpg)

参数：

- 直方图摘要的名称
- 张量数据
- 显式的单调递增步值
- 表示桶数量的正整数
- 音频摘要的可选描述

图展示了使用高级 Keras API 中的函数 `tf.keras.callbacks.TensorBoard` 获取的神经网络层权重分布。

![](img/image-105eb6t7.jpg)

图 7.9 神经网络层的权重分布。

由于 `tf.keras.callbacks.TensorBoard` 不支持写入层的输出分布，如果需要可视化此分布，建议使用 `tf.summary.histogram` API。下面的程序示例解释了如何使用 `tf.summary.histogram`。将 100 组随机值写入日志文件并在 TensorBoard 上显示，如图 7.10 所示。

![](img/image-tc7ltc1y.jpg)

图 7.10 在直方图仪表板上观察由 `tf.summary.histogram` 写入的多组随机值。

![](img/image-ya7erhm9.jpg)

图 7.11 在分布仪表板上观察由 `tf.summary.histogram` 写入的多组随机值。

![](img/image-e6nxcdct.jpg)

## 7.2 实验 1: 使用 tf.summary.image API 可视化训练结果

为了帮助读者更深入理解 `tf.summary` 模块的 API，本实验采用 `tf.summary.image` API 将在 CIFAR-10 数据集上训练的网络模型的混淆矩阵结果写入，并将该结果显示在 TensorBoard 的图像面板（images dashboard）上。图 7.12 显示了训练后网络模型的可视化结果。

![](img/image-u4c3qqqd.jpg)

图 7.12 图像面板上的混淆矩阵结果。

图 7.13 是构建网络模型和可视化输出结果的源代码流程图。

### 辅助函数

![](img/image-gmnkgj2b.jpg)
![](img/image-syylbeq4.jpg)

图 7.13 构建网络模型并可视化训练结果源代码流程图。

### 补充说明

图 7.14A 展示了一个混淆矩阵示例，其中矩阵列代表预测标签，矩阵行代表真实标签。图中，中间的数字 2 表示真实标签为 1，且预测为 1 的正确预测数量为 2。图中左下角的数字 2 表示真实标签为 2，且预测为 0 的错误预测数量为 2。

![](img/image-ls7o9q3b.jpg)

图 7.14 混淆矩阵分析。

### `plot_confusion_matrix` 函数

混淆矩阵中的数字代表预测的百分比

![](img/image-f84jr4uv.jpg)
![](img/image-b49godmm.jpg)
![](img/image-hcdjosty.jpg)

### 补充说明

归一化混淆矩阵：以下代码是混淆矩阵的归一化过程。图 7.15 显示了转换操作。

![](img/image-ezegxx81.jpg)

图 7.15 混淆矩阵的归一化过程。

![](img/image-7iywb0ro.jpg)
![](img/image-vgp02f5o.jpg)
![](img/image-16imndo6.jpg)

### 以及训练网络模型

划分数据

![](img/image-jawdlfvj.jpg)

### 一个网络模型

表 7.1 显示了网络模型的架构。

### 网络模型

表 7.1

| 7.1 | 7.1 |
| :--- | :--- |

![](img/image-g4q7kty3.jpg)
![](img/image-qp764h2l.jpg)

### 在 TensorBoard 上混淆矩阵结果

通过命令行使用 TensorBoard 查看训练记录

![](img/image-tiz5csvi.jpg)

### 使用 TensorBoard 可视化混淆矩阵结果

可以通过 TensorBoard 观察每个 epoch 下网络模型的混淆矩阵结果。进度条用于观察网络模型在不同 epoch 的预测结果，如图所示。

![](img/image-2oa69wcp.jpg)

图 7.16 在图像面板上观察混淆矩阵结果。

从图中的混淆矩阵结果可以看出，高亮框中的值越大，网络模型的性能就越好。

![](img/image-zws4vaus.jpg)

图 7.17 混淆矩阵结果 (1)。

此外，还可以从混淆矩阵中观察类别之间的关系。如图所示，有 20% 的“猫”类被预测为“狗”类，这意味着网络模型容易混淆“猫”类和“狗”类。

![](img/image-xtbnjwpe.jpg)

图 7.18 混淆矩阵结果 (2)。

## 7.3 实验 2：使用 TensorBoard HParams 进行超参数调优

为特定问题开发良好的神经网络模型时存在许多问题，例如应该使用多少层网络、使用哪种优化器更好、如何设置合适的学习率值、是否应用 dropout 技术或批归一化方法等。这些可调整的参数统称为超参数，它们直接影响训练结果。因此，开发神经网络模型的一个重要步骤是选择最佳超参数。本章最后一节介绍了一种使用 TensorFlow 提供的 `HParams` 面板的超参数调优技术，它可以帮助识别特定问题最合适的超参数。该技术通过一个程序示例直接解释，该示例构建了 36 个具有不同超参数组合的网络模型，并在 `CIFAR-10` 数据集上进行训练，以便对获得的结果进行分析和比较。

构建神经网络模型使用的超参数如下：

- `augmentation` (`IA`): 是或否
- `normalization` (`BN`): 是或否
- `rate` (`LR`): `0.001`、`0.01` 或 `0.03`
- `initialization method`（初始化方法）：`Random Normal`、`Glorot Normal` 或 `He Normal`

### 7.3.1 TensorBoard 中的 HPARAMS 面板

通过命令行使用 TensorBoard：

![](img/image-c43u7j4x.jpg)

`HParams` 面板：打开 TensorBoard 后，点击列表选项中的 `HParams`，如图所示。

![](img/image-dvq5488r.jpg)

图 7.19 TensorBoard 中的列表选项。

### HParams 面板

点击 `HParams` 后，会打开一个面板，如图所示。`HParams` 面板的左侧窗显示超参数视图、指标值、运行状态、表格视图中的排序信息以及会话组的数量。主面板显示三个不同的视图，包括在“表格视图”（table view）上的运行列表、“并行坐标视图”（parallel coordinates view）中每个运行对应每个超参数和指标的情况，以及“散点图视图”（scatter plot view）中每个超参数与每个指标的比较图表。在图中，由于没有写入任何数据，`HParams` 面板中没有显示任何信息。

![](img/image-p3tiun90.jpg)

图 7.20 TensorBoard 中的 HParams 面板。

### 7.3.2 代码示例

图 7.21 是构建和分析具有各种超参数的 36 个神经网络模型的源代码流程图。

超参数

![](img/image-pl2z167k.jpg)

图 7.21 构建和分析 36 个具有不同超参数组合的神经网络的源代码流程图。

![](img/image-myq1gjx5.jpg) ![](img/image-7yythgng.jpg)

执行上述程序后，TensorBoard 屏幕上会有更多关于超参数和指标值的信息，如图。

以及训练网络模型

![](img/image-n8tuez5r.jpg)

图 7.22 带有超参数和指标信息的 TensorBoard HParams。

![](img/image-6clsi6ok.jpg)

训练数据：带有图像增强和不带图像增强

![](img/image-9szkwoay.jpg) ![](img/image-8fguxxey.jpg)

一个用于构建和训练网络模型的函数。

模型中使用的网络层如下：

- 尺寸为 `32 × 32 × 3` 的输入层
- 卷积层（权重初始化：`Random normal`、`Glorot normal` 或 `He normal`）
- 带有预设参数的批归一化层（超参数：使用或不使用）
- `ReLU` 激活函数层
- 池化层，用于特征图的下采样
- 展层（flatten），用于将输入展平为一维 `Tensor`
- Dropout 层，在训练期间每一步以 50%的频率随机将输入单元设置为 0
- 全连接层；如果此层用作网络隐藏层，将采用 `ReLU` 激活函数。如果此层用作网络输出层，将用 `ReLU` 激活函数替换为 `softmax` 激活函数。

![](img/image-d9gu2jlv.jpg) ![](img/image-lj6oujfh.jpg)

### 具有不同超参数组合的 36 个网络模型

表 7.2 显示了训练 36 个神经网络模型的超参数组合。

表格 7.2

（表格内容省略）

网络模型

![](img/image-i5w9eyey.jpg)

通过 TensorBoard HParams 的训练结果。

36 个神经网络模型的超参数和训练结果显示在 `HParams` 面板上，如图。

#### 并行坐标视图

![](img/image-4zdskfaf.jpg)

图 7.23 带有 36 个网络模型的 TensorBoard HParams。

要使用并行坐标视图观察结果，请点击面板中的 `PARALLEL COORDINATES VIEW`，如图。

![](img/image-3lbz395d.jpg)

图 7.24 带有并行视图的 HParams 面板。

从并行坐标视图的结果来看（如图所示），高准确率的网络模型使用了图像增强和批归一化技术，而使用不同类型的初始化方法或学习率对训练结果的影响很小。

![](img/image-l54p7kv.jpg)

图 7.25 不同超参数对网络模型准确率的影响。

在 TensorBoard HParams 中，可以设置准确率值的范围以过滤不需要的信息，如图。从 `HParams` 面板可以观察到如果应用批归一化，对初始化方法的选择就不那么细致，因为它们对准确率没有太大改变。

![](img/image-5xxsc74p.jpg)

图 7.26 限制了准确率范围的 TensorBoard HParams。

我们还可以显示特定学习率的模型结果，例如显示学习率值为 `0.001` 的训练模型的结果，如图。所示，准确率最高的三个网络模型都是使用 `0.001` 的学习率训练的。

![](img/image-ojl2zjqb.jpg)

图 7.27 选择运行特定学习率的 TensorBoard HParams。

### 补充说明

图 7.27 中的结果显示，网络模型在用 `0.001` 的学习率训练时达到了最佳准确率。然而，这种比较是不公平的，因为使用 `0.001` 学习率的网络模型收敛速度远慢于 `0.01` 或 `0.03`。此外，使用 `ReduceLROnPlateau` 等回调函数也会减少此值，因此建议使用较高的学习率，然后在训练过程中逐渐降低此值。

### 散点图视图

要显示比较每个超参数与每个指标的图表，请点击面板中的 `SCATTER PLOT VIEW`，如图所示。我们留给读者自行探索。分析方法与“并行坐标视图”部分相似。

![](img/image-jn9y4uu8.jpg)

图 7.28 带有散点图视图的 HParams 面板。

# 第 8 章：卷积神经网络架构

## 摘要

卷积神经网络（CNNs）已广泛应用于许多计算机视觉领域，如图像分类、人脸识别、目标检测等。本章介绍了一些流行的 CNN 架构，包括 `LeNet`、`AlexNet`、`VGG`、`GoogLeNet` 和 `ResNet`。随后，介绍了实现计算机视觉 CNN —— `Inception-v3` 的两种场景。在第一种场景中，我们使用 `Keras Applications` 创建 `Inception-v3` 模型；在第二种场景中，我们利用 `TensorFlow Hub` 构建 `Inception-v3` 模型。

## 关键词

CNNs；`Keras application`；`TensorFlow hub`；`Inception`；`ResNet`；`VGG`

## 大纲

- 介绍流行的卷积神经网络（CNN）架构，包括 `LeNet`、`AlexNet`、`VGG`、`GoogLeNet` 和 `ResNet`
- 介绍 `Keras Applications` 和 `TensorFlow Hub`
- 通过 `Keras Applications` 和 `TensorFlow Hub` 实现 `Inception-v3` 网络

## 8.1 常见的卷积神经网络架构

本章介绍了一些最具代表性的卷积神经网络（CNN）架构，包括 `LeNet`、`AlexNet`、`VGG`、`GoogLeNet` 和 `ResNet`。这些 CNN 被广泛应用于计算机视觉领域，如图像分类、人脸识别、目标检测等。

### 8.1.1 LeNet

Yann 等人于 1998 年提出了用于手写字符识别的 `LeNet` [1]。`LeNet`的架构直观且简单，由三个命名为 `C1`、`C3` 和 `C5` 的卷积层、两个命名为 `S2` 和 `S4` 的下采样层以及一个命名为 `F6` 和 `Output` 的全连接层组成，如图所示。

- **C1**: `LeNet` 尺寸为 `32 × 32` 的输入灰度图像通过一个具有 6 个大小为 `5 × 5` 卷积的卷积层（`C1`），输出 6 个大小为 `28 × 28` 的特征图。`C1` 有 22,304 个连接和 156 个可训练参数。
- **S2**: `C1` 的输出被发送到一个卷积大小为 `2 × 2`、步长为 `2` 的下采样层（`S2`），之后是 sigmoid 激活函数，产生 6 个大小为 `14 × 14` 的特征图。`S2` 有 5880 个连接和 12 个可训练参数。
- **C3**: 一个具有 16 个大小为 `5 × 5` 卷积核的卷积层接收 `S2` 的输出作为输入，产生 16 个大小为 `28 × 28` 的特征图。`C3` 有 156,000 个连接和 1516 个可训练参数。
- **S4**: 下采样层与第二层（`S2`）相同。该层使用 16 个大小为 `2 × 2`、步长为 `2` 的卷积核输出 16 个大小为 `5 × 5` 的特征图。`S4` 有 2000 个连接和 32 个可训练参数。
- **C5**: 一个具有 120 个大小为 `5 × 5` 卷积核的卷积层，接收 `S4` 的 16 个大小为 `5 × 5` 的输出特征图作为输入，产生 120 个大小为 `1 × 1` 的特征图。`C5` 有 48,120 个可训练参数。
- **F6**: 有 84 个神经元的全连接层，后接 sigmoid 激活。`F6` 包含 10,164 个可训练参数。
- **输出层**: 有 10 个神经元的全连接层，每个类别对应一个神经元。

![](img/image-sptduarl.jpg)

图 8.1 LeNet 的架构。

### 8.1.2 AlexNet

`AlexNet` [2] 是 2012 年 ImageNet 大规模视觉识别挑战（ILSVRC 2012）的冠军。它的架构比 `LeNet` 更大更深，如图所示。具体而言，`AlexNet` 架构由八层组成，包括五层卷积层，其中第一层卷积核大小为 `11 × 11`，第二层为 `5 × 5`，其他层为 `3 × 3`，随后是三个全连接层。在每个卷积层和全连接层的输出处都采用了修正的线性单元（ReLU）激活函数，最后一个全连接层除外，它将其输出发送到 softmax 函数进行最终分类。为了获得惊人的性能，`AlexNet` 采用了 dropout 和数据增强技术以防止训练过程中的过拟合。如果说 `LeNet` 为 CNN 铺平了道路，那么 `AlexNet` 就是驱动 CNN 热潮的关键。

![](img/image-4v8gbexs.jpg)

图 8.2 AlexNet 的架构。

### 8.1.3 VGG

`VGG` [3] 是 Karen 等人于 2014 年引入用于大规模图像识别的深度 CNN。`VGG` 有多个版本，如 `VGG-11`、`VGG-13`、`VGG-16` 和 `VGG-19`，每个版本之间的主要区别在于层数。`VGG-16` 的架构由 16 个卷积层组成，如图所示。

![](img/image-o2d69ki1.jpg)

图 8.3 VGG-16 的架构。

与之前的 CNN 相比，`VGG` 仅由卷积核大小为 `3 × 3` 的卷积层组成，而不是 `5 × 5`、`7 × 7` 或 `9 × 9`。其主要原因是多个 `3 × 3` 卷积层的堆叠可以实现与 `5 × 5`、`7 × 7` 或 `9 × 9` 卷积层相似的感受野，同时参数数量大大减少。图 8.4 展示了两个 `3 × 3` 卷积层的堆叠和单个 `5 × 5` 卷积层。两者具有相同的输入和输出尺寸，但使用两个 `3 × 3` 卷积层只需要 18 个参数，而单个 `5 × 5` 卷积层需要 25 个参数。注意，为了计算方便，省略了通道数。

![](img/image-9umrtu.jpg)

图 8.4 多个 `3 × 3` 卷积层的堆叠与单个卷积层。

### 8.1.4 GoogLeNet

`GoogLeNet` [4] 是 Google 提出的的一种深度网络架构，也称为 `Inception-v1`，它获得了 2014 年 ILSVRC 冠军。`GoogLeNet` 的架构由深度为 22 层的 `Inception Blocks` 组成，如图所示。

![](img/image-mauids5.jpg)

图 8.5 GoogLeNet 的架构。

`GoogLeNet` 中使用 `Inception Blocks` 的主要思想是在保持计算不变的同时增加网络的深度和宽度。原始的 inception 架构（也称为 naïve inception）所示，它包含四个并行层，包括 `1 × 1` 卷积、`3 × 3` 卷积、`5 × 5` 卷积和 `3 × 3` 最大池化。该模块的输出是通过拼接这些层形成的，并作为网络下一阶段的输入。虽然由 naïve inception 组成的网络可以获得高性能，但需要大量的参数和计算。

![](img/image-61296nus.jpg)

图 8.6 naïve Inception Block。

![](img/image-uph6kn.jpg)

图 8.7 GoogLeNet 中的 Inception Block。

`GoogLeNet` 中的 `Inception Block` 是通过将 `1 × 1` 卷积层连接到 `3 × 3` 和 `5 × 5` 卷积层以及 naïve inception 的 `3 × 3` 最大池化层而设计的。为了展示在 `Inception Block` 中使用 `1 × 1` 卷积层的优势，让我们使用卷积层将尺寸为 `36 × 36 × 128` 的输入转换为 `36 × 36 × 64`：

- **第一方法**: 输入直接进入 `3 × 3` 卷积层以产生预期输出。卷积层的参数数为 73,728，如图所示。

![](img/image-zitax2i.jpg)

图 8.8 3 × 3 卷积层的可训练参数数量计算。

- **第二方法**: 输入首先通过 `1 × 1` 卷积层将特征图数量减少到 16，然后将得到的特征图发送到 `3 × 3` 卷积层以获得预期输出。两个卷积层的参数数为 11,264，少于未应用 `1 × 1` 卷积层的第一种方法的 73,728，如图所示。

![](img/image-z6kdpzv2.jpg)

图 8.9 1 × 1 和 3 × 3 卷积层组合架构的可训练参数数量计算。

尽管 `GoogLeNet` 的深度为 22 层，但通过使用 `Inception Blocks`，`GoogLeNet` 的参数数量仍比 8 层的 `AlexNet`少 12 倍。在 Google 提出`GoogLeNet`架构之后，引入了更多版本的 Inception 模型。以下是每个版本的总结：

- `Inception-v1` 也称为 `GoogLeNet`:2014 年发布，它是第一个引入 `1 × 1` 卷积来减少网络计算的多分支架构。
- `Inception-v2`:2015 年发布，引入批归一化以加速训练并提高 CNN 性能。
- `Inception-v3`:2016 年发布，在构建 Inception 模块时探索 `1 × n` 和 `n × 1` 卷积。
- `Inception-v4`:2017 年发布，使用带有残差连接的 Inception 架构。
- `Inception-ResNet`:2017 年发布，引入深度可分离卷积来构建 CNN 架构代替 Inception 模块。

### 8.1.5 ResNet

Microsoft 于 2015 年获得当年 ILSVRC 冠军时推出了 `ResNet` [5]（残差网络）。针对 ImageNet 有五种`ResNet`架构版本，包括`ResNet-18`、`ResNet-34`、`ResNet-50`、`ResNet-101` 和 `ResNet-152`。这里，`ResNet-x`中的`x`是对应版本`ResNet`的层数。图 8.10 展示了`ResNet-34`的架构。

![](img/image-o0ipvppp.jpg)

图 8.10 ResNet-34 的架构。(A) Residual Block：两个 `3 × 3` 卷积层的堆叠，各层卷积核数量相等。(B) Residual Block, 1/2：两个 `3 × 3` 卷积层的堆叠，第一层的卷积核数量是第二层的一半。

在深度学习中，更深的神经网络能够学习更复杂的特征，并比浅层神经网络获得更好的性能。然而，退化（degradation，指神经网络准确率问题）在训练过程中会变得饱和并迅速退化，导致更大的训练误差。例如，图 8.11 显示了 20 层神经网络和 56 层网络在 CIFAR-10 数据集上的实验结果。所示，20 层神经网络的训练和测试误差少于 56 层网络。

![](img/image-mokusns5.jpg)

图 8.11 CIFAR-10 数据集上 20 层神经网络和 56 层网络的训练和测试误差。

为了克服退化问题，`ResNet`使用 Residual Blocks 构建深度网络。图 8.12 展示了一个典型的残差。

![](img/image-zssita9o.jpg)

图 8.12 在 3 × 3 卷积层上添加快捷连接的 Residual Block。

图 8.13 展示 ImageNet 上训练 ResNet 的实验结果。图 8.13A 显示了未使用快捷连接的 18 层和 34 层网络的结果。所示，34 层网络的训练和验证误差大于 18 层网络。当添加快捷连接时，即使用`Residual Blocks`构建网络时，`ResNet-34`的训练和验证误差少于`ResNet-18`。

![](img/image-ckfepl4u.jpg)

图 8.13 ImageNet 上使用和不使用快捷连接的网络的训练和验证误差

### 8.1.6 网络架构对比

图 8.14 展示了在 ImageNet 数据集上训练的`AlexNet`、`VGG`、`GoogLeNet`和`ResNet`的结果。所示，深度为 152 层的`ResNet`架构在 ImageNet 测试集上的 top-5 误差最少，之后是`GoogLeNet`、`VGG-19`和`AlexNet`。

![](img/image-qyvruh1j.jpg)

图 8.14 ImageNet 测试集上的 top-5 误差 CNN。

## 8.2 实验：Inception-v3 网络的实现

本章介绍了如何实现用于图像分类的 Inception-v3 网络。该目标可以通过前面章节介绍的 `TensorFlow` 库来实现；然而，由于网络架构复杂，这需要一些时间。接下来的章节介绍了两种更快速、更有效地构建 Inception-v3 网络的方法：`Keras Applications` 和 `TensorFlow Hub`。图 8.15 显示了 Inception-v3 网络的一个示例预测。

![](img/image-2hyiwjfi.jpg)

图 8.15 Inception-v3 网络对非洲象的图像预测。

### 8.2.1 Keras applications

`Keras Applications` 是 `Keras` 库的应用模块，为流行的架构（如 `Xception`、`VGG`、`ResNet`、`Inception` 等）提供了网络声明和预训练权重。表 8.1 列出了使用 `Keras Applications` 获取的一些网络在 2012 年 ILSVRC 比赛使用的 ImageNet 验证集上的准确率。

- 如果概率最高的模型预测结果与答案相同，则预测是正确的
- 如果网络预测了五个概率最高的结果，其中一个与答案相同，则预测是正确的
- 网络的参数数量
- 网络的层数，包括卷积层、池化层、激活层等

表 8.1

以下程序使用 `Keras Applications` 构建 Inception-v3 网络作为示例。图 8.16 是源代码的流程图。

使用 `Keras Applications` 的网络

![](img/image-x1p0ijps.jpg)

图 8.16 使用 `Keras Applications` 构建和测试 Inception-v3 网络的流程图。

![](img/image-amc7z5yj.jpg)

### 参数

- `include_top` (default)：包括网络顶部的全连接层
- 不包括全连接层
- `weights`：`random initialization`
- `weights` (default)：使用 ImageNet 上的预训练权重
- `input_tensor` (optional)：用于在网络之间共享输入；默认设置为 `None`
- `input_shape` (optional)：输入形状为 `(299, 299, 3)`；如果使用了 `input_tensor`，则省略 `input_shape`
- `pooling` (optional)：当 `include_top` 设置为 False 时用于特征提取
- `pooling` (default)：使用最后一个卷积块的输出作为网络的输出
- 在最后一个卷积块的输出处使用全局平均池化
- 在最后一个卷积块的输出处使用全局最大池化
- `classes` (optional)：类别数量；默认值为 `1000`。如果需要自定义类别数量，则需要将 `include_top` 设置为 `True` 并将 `weights` 设置为 `None`

![](img/image-1n0sg63j.jpg)
![](img/image-1kki8cx.jpg)

预测处理

对于每个网络模型，`Keras Applications` 都提供了相应的函数，用于按照网络模型要求的格式处理数据。每个模型的输入格式可能有所不同。例如，某些模型需要值范围从 -1 到 +1 的输入图像，另一些则使用值范围从 0 到 1，以此此类推。用于解码预训练模型的预测并将预测值映射到实际类名称。导入数据预处理和解码

![](img/image-iywo8kre.jpg)
![](img/image-zabq6t79.jpg)

用于预测的预训练模型

![](img/image-zvrwt68r.jpg)

### 8.2.2 TensorFlow Hub

`TensorFlow Hub` 是一个存储库，可以下载并复用训练好的机器学习模型，且需少量的代码。通过 `tfhub.dev` 仓库提供了各种预训练模型，如图像分类模型和文本嵌入模型。`TensorFlow Hub` 的官方网站如图

![](img/image-qdqubt4.jpg)

图 8.17 TensorFlow Hub 网站。

要安装 `TensorFlow Hub`，请使用以下命令行：

![](img/image-ljnb6ed9.jpg)

以下程序使用 `TensorFlow Hub` 构建 Inception-v3 网络作为示例。图 8.18 是源代码的流程图。

使用 `TensorFlow Hub` 包的网络

![](img/image-ts4jurmw.jpg)

图 8.18 使用 `TensorFlow Hub` 构建和测试 Inception-v3 网络的流程图。

![](img/image-ngs9zra.jpg)

Inception-v3 网络

1. 访问网站 `https://tfhub.dev/` 并点击 `classification` 标签，如图
   ![](img/image-okn70wp.jpg)
   图 8.19 在 `TensorFlow Hub` 上选择分类标签。
2. 选择 `Inception-v3`，如图
   ![](img/image-fbon8vrj.jpg)
   图 8.20 在 `TensorFlow Hub` 中选择 Inception-v3 模型。
3. 选择 Inception-v3 网络的 `TF2` 版本，如图
   ![](img/image-ymlqcwru.jpg)
   图 8.21 在 `TensorFlow Hub` 上选择 Inception-v3 网络的版本。
4. 点击 `Copy URL` 按钮复制预训练 Inception-v3 的 URL，`TensorFlow Hub` 上的 Inception-v3 如下
   ![](img/image-8l1f.jpg)
   图 8.22 `TensorFlow Hub` 上的 Inception-v3。
5. 使用复制的 URL 创建 `TensorFlow Hub` 上的 Inception-v3
6. 显示 `TensorFlow Hub`  Inception-v3 架构
   ![](img/image-l45mg.jpg)
   使用 `Keras Applications` 的预测数据
   ![](img/image-ixv5.jpg)
   预训练模型
   ![](img/image-0rk6.jpg)
   使用 `summary` 函数
   ![](img/image-z45.jpg)

### 参考文献

1. Lecun Y., Bottou L., Bengio Y., Haffner P. Gradient-based learning 1998.
2. Krizhevsky A., Sutskever I., Hinton G. Imagenet classification with deep 2012.
3. Simonyan K., Zisserman A. Very deep convolutional networks for large-scale image.
4. Szegedy C., et al. Going deeper with 2015.
5. He K., Zhang X., Ren S., Sun J. Deep residual learning 2016.
6. Ioffe S., Szegedy C. Batch normalization: accelerating deep training by reducing internal 2015.
7. Szegedy C., Vanhoucke V., Ioffe S., Shlens J. Rethinking the inception 2016.
8. Chollet F. Xception: deep learning with depthwise separable 2017.
9. He K., Sun J. Convolutional neural networks at constrained 2015.
10. Sandler M., Howard A., Zhu M., Zhmoginov A., Chen L.-C. Mobilenetv2: inverted residuals and linear 2018.
11. Huang G., Liu Z., Van Der Maaten L., Weinberger K.Q. Densely connected convolutional 2017.
12. Hu J., Shen L., Sun G. Squeeze-and-excitation 2018.
13. Li X., Wang W., Hu X., Yang J. Selective kernel 2019.
14. Szegedy C., Ioffe S., Vanhoucke V., Alemi A. Inception-v4, inception-resnet and the impact of residual connections 2016.
15. Howard A.G., Zhu M., Chen B., Kalenichenko D., Wang W., Weyand T., Andreetto M., Adam H. Mobilenets: efficient convolutional networks for mobile vision applications 2017.
16. Xie S., Girshick R., Dollár P., He K. Aggregated residual transformations for deep 2017.
17. Zoph B., Vasudevan V., Shlens J., Quoc V.L. Learning transferable architectures for scalable image 2018.

# 第 9 章：迁移学习

## 摘要

迁移学习已广泛应用于神经网络的训练，因为它通常比从零开始训练网络更快、更容易，且更有效。本章首先介绍并分析了迁移学习策略。然后，为了帮助读者进一步理解并提高开发神经网络的实践技能，本章实现了了两种构建和训练网络模型的场景。在第一种场景中，我们通过 `Keras Applications` 构建了 `Inception-v3` 模型并从零开始训练该模型。在第二种场景中，通过 `TensorFlow Hub` 构建了 `Inception-v3` 网络，并应用迁移学习来训练该网络模型。

## 关键词

迁移学习；从零开始训练；预训练模型；CNN；神经网络

## 目录

- 迁移学习策略
- 通过 `TensorFlow Hub` 使用预训练的 `Inception-v3` 模型进行迁移学习
- 迁移学习与从零开始训练

## 9.1 迁移学习

### 9.1.1 迁移学习简介

在这一章中，我们解释并演示了网络不同深度的卷积层所提取的特征是不同的。特别是，浅层主要负责提取输入的简单特征，如边缘和线条，而深层则基于从之前层提取的特征，因此它们可以识别出更具体的特征，如鼻子、眼睛、耳朵等，如图 9.1 所示。

![](img/image-9fhrm9y5.jpg)

图 9.1 卷积神经网络 (CNN) 示例。

卷积神经网络 (CNN)学习到的特征可以应用于不同的任务。例如，通过使用包含数万张图像的 ImageNet 数据集来训练 CNN，大量的训练数据允许网络模型学习到非常多样化的特征。当我们有一个新数据集并想要解决某个感兴趣的任务时，不需要从零开始训练整个网络模型，而是使用在如 ImageNet 等大型数据集上训练好的模型（称为预训练模型），作为新任务的初始化方法或固定特征提取器。这种训练方法被称为迁移学习。

迁移学习实际上与人类的学习方法非常相似；通过完成某任务获得的知识也可以用于解决其他相关任务。任务之间越相关，知识就越容易迁移。例如，当我们知道如何骑自行车时，学习骑摩托车就会更容易。根据许多使用迁移学习方法训练神经网络模型的公开工作结果，与从零训练的方法相比，该方法可以在需要较训练数据和训练时间的情况下，帮助获得更好的性能。图 9.2 显示了从零训练与迁移学习的区别。如图所示，在从零训练中，模型是针对特定任务分别训练的，没有保留任何知识从一个模型迁移到另一个模型。在迁移学习中，新任务的学习基于从之前任务中学到的知识。

![](img/image-zdyexk1j.jpg)

图 9.2 从零开始训练模型和使用迁移学习训练模型的对比示意图。

### 9.1.2 迁移学习策略

根据训练数据的以下两个特征，可以应用四种迁移学习策略：

- **训练数据的大小**：如果新数据集包含数万个训练样本，则被认为是大型数据集。如果新数据集仅由数百或数千个训练样本，则被认为是小数据集。
- **数据的相似性**：这是新训练数据与用于预训练模型的数据之间的相似性。例如，猫和老虎被认为是相似样本，而猫和桌子被认为是不同的样本。

#### 第一种策略：使用小数据集和相似训练样本训练网络模型

由于在小数据集上训练了庞大的网络模型，很容易发生过拟合问题。因此，在应用迁移学习时，预训练模型的权重在训练过程中必须保持不变。由于新数据集与用于预训练模型的数据具有相似性，它们在网络的隐藏层中具有相似的特征，尤其是在深层。因此，特征提取层不需要更改。为了学习新任务，只需要对处理网络模型输出特征的最后一层进行修改。新的网络模型是基于预训练模型的架构构建的，移除输出层（最后一层），然后为新任务添加新层。迁移学习的步骤如下：

1. **移除网络层**：选择移除预训练模型的最后一层，如图所示。
   ![](img/image-n1bq5u3v.jpg)
   图 9.3 移除预训练模型的最后一层 (1)。
2. **添加新层**：在原始网络结构上方添加一个或多个层以用于新任务，如图所示。
   ![](img/image-f2za689.jpg)
   图 9.4 为新任务添加层 (1)。
3. **训练新模型**：在训练网络期间，大多数网络层的权重固定，只训练新添加的层，如图所示。
   ![](img/image-rp3qg58.jpg)
   图 9.5 冻结层 (1)。

#### 第二种策略：使用小数据集和不同训练样本训练网络模型

由于使用小数据集训练网络模型，预训练模型的权重应保持不变以防止过拟合。由于新数据集的样本与用于预训练模型的数据不同，它们仅在浅层具有相似的特征，而网络深层的特征非常不同。为了基于预训练模型架构构建网络模型以学习新任务，仅保留浅层，而应移除深层并用新的替换输出层。迁移学习的步骤如下：

1. **移除网络层**：移除预训练模型的深层，只留下提取线条和边缘等简单特征的浅层，如图所示。
   ![](img/image-nm7pxgz.jpg)
   图 9.6 移除预训练模型的层。
2. **添加新层**：在原始网络架构上方添加新层以用于新任务，如图所示。
   ![](img/image-l9fxyhab.jpg)
   图 9.7 为新任务添加层 (2)。
3. **训练新模型**：在训练网络期间，大多数网络层的权重固定，只训练新添加的层，如图所示。
   ![](img/image-fbktn87.jpg)
   图 9.8 冻结层 (2)。

#### 第三种策略：使用大型数据集和相似训练样本训练网络模型

使用大型数据集允许我们从零训练整个预训练模型或新的网络模型。以下提供了两种训练方法：

**预训练模型**：由于新数据集与用于预训练模型的数据相似，它们在网络的隐藏层中具有相似的特征，尤其是在深层。因此，特征提取层不需要更改。为了学习新任务，只需要对处理网络输出的最后一层进行修改。新模型是通过将最后一层替换为新的构建的。最后，由于数据集足够大，可以优化新添加层或其他所有层。微调的步骤如下：

1. **移除网络层**：选择移除预训练模型的最后一层，如图所示。
   ![](img/image-kpbrfthr.jpg)
   图 9.9 移除预训练模型的最后一层 (2)。
2. **添加新层**：在原始网络架构上方添加一个或多个层以用于新任务，如图所示。
   ![](img/image-jysb78we.jpg)
   图 9.10 为新任务添加层 (3)。
3. **训练新模型**：
   - **方法一**：大多数网络层的权重固定，只训练新添加的层，如图所示。
     ![](img/image-ru8kgwtj.jpg)
     图 9.11 冻结层 (3)。
   - **方法二**：在新数据集上训练或微调整个网络模型，如图所示。
     ![](img/image-nyqsi5qj.jpg)
     图 9.12 训练或微调整个网络模型 (1)。

**新网络模型**：由于数据集足够大，允许我们创建一个新的网络模型并从零训练，如图所示。

#### 第四种策略：使用大型数据集和不同训练样本训练网络模型

![](img/image-p0alxoim.jpg)

图 9.13 从零训练网络模型 (1)。

使用更大的数据集训练网络模型可以避免过拟合问题。因此，可以在新数据集上训练整个预训练网络模型或新的网络模型提高性能。以下提供了两种训练方法。

**预训练模型**：由于新数据集与用于预训练模型的数据之间存在差异，它们在模型的大多数层中特征并不相似。但在实践中，使用预训练模型的权重初始化来训练新的网络模型通常是有益的。训练模型的步骤如下：

1. **移除网络层**：选择移除预训练模型的最后一层，如图所示。
   ![](img/image-amt1k3fr.jpg)
   图 9.14 移除预训练模型的最后一层 (3)。
2. **添加新层**：在原始网络架构上方添加一个或多个层以用于新任务，如图所示。
   ![](img/image-ffh3pu2d.jpg)
   图 9.15 为新任务添加层 (4)。
3. **训练新模型**：在新更大的数据集上使用来自预训练模型的权重初始化训练或微调整个网络模型，如图所示。
   ![](img/image-qw2i8hc3.jpg)
   图 9.16 训练或微调整个网络模型 (2)。

**新网络模型**：由于数据集足够大，允许我们创建一个新的网络模型并从零训练，如图所示。

![](img/image-ofspn924.jpg)

图 9.17 从零训练网络模型 (2)。

## 9.2 实验：使用 Inception-v3 进行迁移学习

本节介绍了如何使用 `Inception-v3` 网络提高在 `Dogs vs. Cats` 数据集上的图像分类性能。我们进行了两种训练场景。在第一场景中，我们通过 `Keras Applications` 构建了名为 `Model-1` 的 `Inception-v3` 模型，并使用随机权重初始化对其从零开始训练。在第二种场景中，我们通过 `TensorFlow Hub` 加载 `Inception-v3` 网络进行特征提取，并采用两个全连接层，构建了一个新的网络模型 `Model-2`。通过对 `Model-2` 应用迁移学习，大部分层的权重被固定；只有新添加的两个全连接层在 `Dogs vs. Cats` 数据集上进行训练以学习新任务。实验结果显示，`Model-2` 的准确率高于 `Model-1`。

### 9.2.1 Dogs vs. Cats 数据集简介

`Dogs vs. Cats` 数据集包含狗和猫两类，是为了 2013 年的 Kaggle 机器学习竞赛而引入的。Kaggle 提供了 25,000 张标记狗猫图像用于训练，以及 12,500 张未标记图像用于测试。图 9.18 显示了 `Dogs vs. Cats` 数据中的部分图像。为了在实验中构建优化的输入流水线，`Dogs vs. Cats` 数据通过 `tf.data.Datasets` 编程接口 (API) 从 `TensorFlow dataset` 加载，用于网络模型的训练和测试。

![](img/image-bwt8htak.jpg)

图 9.18 Dogs 数据集中的图像。

### 9.2.2 代码示例

图 9.19 是图像分类模型源代码的流程图。

### dataset

![](img/image-zq52y79w.jpg)

图 9.19 图像分类模型源代码流程图。

![](img/image-p4102lhp.jpg)
![](img/image-94sq4be9.jpg)
![](img/image-r6fv0xmd.jpg)
![](img/image-6z9c87rm.jpg)

### 以及训练网络模型

![](img/image-0zaapb64.jpg)
![](img/image-s5r6pb2t.jpg)
![](img/image-fvw49nxw.jpg)
![](img/image-obndxehm.jpg)

### 补充说明

在章节中，`Inception-v3` 网络通过 `TensorFlow Hub` 加载，在本章中，它被加载。这两个加载的网络之间的区别在于，第 8 章加载的 `Inception-v3` 包含最后的分类层（1000 个类别），而该分类层在后续的网络中被移除。

### Model-1 和 Model-2

`Model-1` 和 `Model-2` 的最佳训练权重均用于评估 `Cats_vs_Dogs` 测试集。

![](img/image-5mwmurkl.jpg)

结果显示，使用迁移学习的 `Model-2` 获得了 99.39% 的分类准确率，高于从零训练的 `Model-1` 的 1.42% 准确率。

### 参考文献

[1] Yosinski J., Clune J., Bengio Y., Lipson H. How transferable are features in deep neural Adv. Neural Inf. Proces. Syst. 2014;3320–3328.
[2] Oquab M., Bottou L., Laptev I., Sivic J. Learning and transferring mid-level image representations using convolutional neural In: Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, Columbus; 2014:1717–1724.
[3] Mormont R., Geurts P., Marée R. Comparison of deep transfer learning strategies for digital In: Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition Workshops; 2018:2343–234309.
[4] Kornblith S., Shlens J., Le Q.V. Do better ImageNet models transfer Proc. IEEE Conf. Comput. Vis. Pattern Recognit. 2019;2661–2671.
[5] Shin H., et al. Deep convolutional neural networks for computer-aided detection: CNN architectures, dataset characteristics and transfer IEEE Trans. Med. 2016;35(5):1285–1298.
[6] Tajbakhsh N., et al. Convolutional neural networks for medical image analysis: full training or fine IEEE Trans. Med. 2016;35(5):1299–1312.
[7] Ganin Y., Ustinova E., Ajakan H., Germain P., Larochelle H., Laviolette F., Marchand M., Lempitsky V. Domain-adversarial training of neural J. Mach. Learn. Res. 2016;17(1):2030–2096.
[8] Hendrycks D., Lee K., Mazeika M. Using pre-training can improve model robustness and In: International Conference on Machine 2 2019.
[9] Ding Z., Fu Y. Deep transfer low-rank coding for cross-domain IEEE Trans. Neural Netw. Learn. Syst. 2019;30(6):1768–1779.
[10] Zhuang F., et al. A comprehensive survey on transfer Proc.
[11] ... (truncated for brevity)

## 10.2 变分自编码器简介

### 10.2.1 VAE 简介

`VAE` [4] 是 `AE` 的高级版本，它学习数据生成分布，使其能够从潜分布中提取随机代码或潜在表示，生成与输入数据具有相似特征的输出数据。图 10.3 显示了 `VAE` 和 `AE` 之间的区别。

![](img/image-xvka3sht.jpg)

图 10.3 自编码器 (AE) 与变分自编码器 (VAE) 的区别。

图 10.4 显示了 `VAE` 的概念。所示，编码器接收输入数据并输出两个向量，包括均值向量 (`μ`) 和用于生成潜分布的方差向量。然后，从潜分布中随机采样一个代码或潜在表示，通过解码器生成输出数据。

![](img/image-egoec97d.jpg)

图 10.4 变分自编码器 (VAE) 的概念图。

至于为什么 `VAE` 有可以从潜分布中随机采样的代码，这里有一个直观的例子来解释。如图所示，图像 A 和 B 被用编码器的输入。在编码器的输出处，采样了两个代码，即 `Code A` 和 `Code B`，并发送到解码器以产生 `Output A` 和 `Output B`。由于两个分布之间存在交集，可以从这个交集中产生 `Output A` 和 `Output B` 之间的额外 `Output C`。这种设计使得 `VAE` 的输出具有连续关系，例如 `Output A`、`Output B` 和 `Output C` 之间的连续关系。

![](img/image-lch4234g.jpg)

图 10.5 在 `VAE` 中使用潜分布的优势。

### 10.2.2 VAE 的操作

如前所述，`AE` 直接输出潜空间表示的值，而 `VAE` 的编码器输出两个均值 (`μ`) 和方差向量来生成潜分布。解码器从潜分布中随机采样的代码来重构原始输入。在训练 `VAE` 模型时，通过反向传播算法计算模型参数与最终损失之间的关系。然而，对于随机采样过程无法做到这一点，因为没有用于计算的值。为了解决这个问题，`VAE` 采用了重参数化技巧（reparametrization trick）进行采样，其中从标准正态分布中随机采样一个 `ε`，与潜分布的参数 `μ` 结合计算编码器的输出代码，定义所示。遵循这一技巧，可以在训练过程中优化潜分布的 `μ` 和 `σ`，同时允许从该分布中随机采样。使用代码的另一种更直观的解释是，`μ` 被视为 `AE` 的代码，该代码在 `VAE` 中加入噪声以产生代码 `C`，并希望 `C` 仍然可以解码为原始输入。

![](img/image-8sevqp4j.jpg)

图 10.6 变分自编码器 (VAE) 图。

采用与章节类似的示例，`VAE` 的编码器产生 225 组 2D 向量代码，然后将这些组通过解码器生成 225 张手写数字图像，如图所示。所示，每个图像都是一个易于识别的数字，并且彼此平滑地转换为另一个。

![](img/image-tutx4bc8.jpg)

图 10.7 变分自编码器 (VAE) 生成图像的示例。

### 10.2.3 变分自编码器损失函数

`VAE` 模型的训练目标是确保预测输出与输入尽可能相似。如果数据包含图像样本，可以使用重构图像与输入图像每个像素之间的二元交叉熵 (`BCE`) 损失进行训练。这种损失被称为重构损失，公式如下：

![](img/image-w1v1spzz.jpg)

其中：

- 输入图像
- 重构图像
- 图像宽度
- 图像高度
- 通道数量

然而，如果只使用重构损失训练 `VAE` 模型是不够的。如图所示，控制噪声规模的是由编码器学习的。如果编码器学习输出 0，则不添加噪声来计算输出代码。如果计算代码时不包含噪声，`VAE` 模型的输出代码将与 `AE` 模型相似，这意味着没有给 `VAE` 模型添加对编码表示的约束。图中显示了 `exp(σ²)` 的图，其中，该的值越小，该的值越接近于 0。

![](img/image-rwsiwh0a.jpg)

图 10.8 `exp ( σ ² )` 的图。

为了解决这个问题，引入了 `KL 散度` 来限制该的值。如果该的值等于 0，则必须为 0。此时，该的值等于 1，因此解决了编码器向 `σ = 0` 方向更新的问题。图 10.9 显示了其公式所示：

![](img/image-b3otot2t.jpg)
![](img/image-rrodw5lj.jpg)

图 10.9 `exp(σ i²) — (1 + σ i²)` 的图。

此外，应用了 L2 正则化，公式如下：

![](img/image-rew2hivm.jpg)

最后，通过引入 `μ` 和 `σ` 建立了 `KL 散度`，也称为 Kullback–Leibler 散度损失 (`KL Loss`)，表示如下：

![](img/image-c2v241kd.jpg)

其中：

- 均值（编码器的输出之一）
- 方差（编码器的另一个输出）
- 批量大小

## 10.3 实验：变分自编码器模型的实现

本节介绍了一个用于构建 VAE 模型的示例程序，该模型在 MNIST 手写数字数据集 [5] 上进行训练和测试，用于图像的压缩和重建。图 10.10 显示了 VAE 模型的一些生成图像。

![](img/image-c0urkzvt.jpg)

图 10.10 变分自编码器 (VAE) 生成的手写数字图像。

### 10.3.1 创建项目

由于本章中的 VAE 模型比之前几个章节中的示例程序复杂得多，我们使用 Pycharm IDE 作为编译器来编写源代码并训练模型。接下来，我们概述了创建项目的流程。

- 创建新项目：点击“File（文件）”→“New Project（新建项目）”，如图所示
  ![](img/image-e2rtlq16.jpg)
  图 10.11 在 Pycharm 上创建新项目。
- 新项目的目录，如图所示。
  ![](img/image-ikjao06p.jpg)
  图 10.12 设置新项目目录。
- Python 解释器：打开“Project Interpreter: Python 3.6”，选择“Existing interpreter（现有解释器）”，并设置 Python Interpreter，如图所示。
  ![](img/image-jjwxqzlw.jpg)
  图 10.13 解释器设置。
- 项目：点击“Create（创建）”按钮创建一个新项目，如图所示
  ![](img/image-exg9dz56.jpg)
  图 10.14 创建项目。

### 补充说明

本章 VAE 项目的代码示例可以在此处下载：如图所示

![](img/image-kr9y2abv.jpg)

图 10.15 GitHub 上的变分自编码器 (VAE) 源代码。

### 10.3.2 数据集介绍

我们使用 MNIST 手写数字数据集 [5] 在本章中训练和测试 VAE 模型。MNIST 包含 60,000 个训练样本和 10,000 个测试样本，它们是大小为 28 × 28 的灰度图像。可以通过 TensorFlow datasets 如下加载该数据集。

![](img/image-xyj1gr1x.jpg)

图 10.16 显示 MNIST 数据集的一些示例图像。

![](img/image-cbt623fa.jpg)

图 10.16 MNIST 数据集中的手写数字。

### 10.3.3 构建变分自编码器模型

#### 文件

创建一个文件夹用于存储 VAE 项目的 Python 文件，如图所示。在这里，我们对这些文件进行简要介绍。

- `train.py`：训练 VAE 模型的源代码文件
- `test.py`：评估 VAE 模型的源代码文件
- `models.py`：VAE 模型和自定义网络层的源代码文件
- `losses.py`：自定义损失函数的源代码文件
- `callbacks.py`：自定义回调函数的源代码文件

#### VAE 模型

![](img/image-39mjhjwh.jpg)

图 10.17 变分自编码器 (VAE) 项目。

图 10.18 是构建 VAE 模型源代码的流程图。

#### 辅助函数

构建 VAE 模型

![](img/image-xrdh0yvm.jpg)

图 10.18 变分自编码器 (VAE) 模型源代码流程图。

VAE 模型源代码写在 `models.py` 文件中。图 10.19 显示了 VAE 的架构。

![](img/image-6i7kyu7p.jpg)

图 10.19 变分自编码器 (VAE) 的架构。

创建 `create_vae_model` 函数。

![](img/image-xvtubhpb.jpg)

图 10.19 中的采样层是一个自定义网络层。图 10.20 描述了该层的输出。

采样自定义网络层的源代码

![](img/image-m1yqqeld.jpg)

图 10.20 变分自编码器 (VAE) 模型中的采样。

![](img/image-k0mx6b7q.jpg)

#### 补充说明

损失函数（Loss）用于优化 `μ` 且位于 VAE 模型的中间，因此在建立网络层时必须同时声明内部损失。为了完成此任务，在上述 `create_vae_model` 函数中使用的 `vae.add_loss` 是方法之一。我们也可以通过创建“自定义网络模型”或“自定义网络层”来添加损失函数。

![](img/image-m9aqiv5c.jpg)

损失函数

![](img/image-w1v1spzz.jpg)

其中：

- 输入图像
- 输出图像
- 图像宽度
- 图像高度
- 图像通道数
- 每个批次的数据量

重构损失函数写在 `losses.py` 文件中。

![](img/image-bbl0emyt.jpg)

回调

请在 `callbacks.py` 文件中编写源代码。

- `SaveDecoderModel` class：检查每个 epoch（轮）。如果损失有任何改进，则保存解码器模型（类似于 `keras.callbacks.Checkpoint`）。
- `SaveDecoderOutput` class：在每个 epoch 中，解码器模型生成 22 张图像并将它们写入 TensorBoard 以观察输出。

![](img/image-9whxa7.jpg)

![](img/image-gm88tu1.jpg)

训练 VAE 模型

训练 VAE 模型的源代码写在 `train.py` 文件中。

包

![](img/image-92a3i.jpg)

数据

归一化

![](img/image-m2wq58.jpg)

MNIST 数据集

![](img/image-unwhv4.jpg)

数据

回调

![](img/image-3epranzf.jpg)

VAE 模型

![](img/image-bipyuc.jpg)

优化器和损失函数

![](img/image-q66ikos1.jpg)

VAE 模型

![](img/image-kbku5tg.jpg)

结果

生成

VAE 输出由解码器网络生成。测试模型的源代码写在 `test.py` 文件中。图 10.21 展示了测试结果。

![](img/image-2ztvk8.jpg)

图 10.21 变分自编码器 (VAE) 模型的重建图像。

![](img/image-iekaom39.jpg)

使用命令行打开 TensorBoard：

```

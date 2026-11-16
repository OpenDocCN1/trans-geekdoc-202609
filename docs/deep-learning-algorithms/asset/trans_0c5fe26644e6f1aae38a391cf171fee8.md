

## 神经网络

举例来说，它研究了人类的学习行为，并在此基础上与著名的围棋选手竞争 [20]。要在计算机视觉中培养深度学习，事先收集的足够图像示例至关重要。ImageNet 是一个很好的示例 [21]。本研究的一项贡献包括开发海洋鱼类数据库以支持训练和测试。然而，学习算法同样重要。传统计算机视觉和图像处理方法在特征提取的准确性方面存在不足，而深度学习方法可以通过神经网络来改进这一技术。

近年来，深度学习中的神经网络变得越来越流行。2012 年，研究者 Krizhevsky 等人采用 CNN 在 ImageNet 大规模视觉识别挑战赛 [22, 23] 中完成图像分类，测试准确率显著高于传统算法。由于这一成就，基于神经网络的深度学习兴趣被提升 [24]。2014 年，Ross 等人提出了一种名为 Fast R-CNN 的算法，旨在将物体识别转化为回归问题 [25]。与 2012 年 ImageNet 大规模视觉识别挑战赛中之前的最佳结果 53.3% 相比，平均平均精度提高了近 30%。计算量巨大，因为每张图像中数千个不同尺寸的候选区域的特征都会被提取。由于 Faster R-CNN 大幅降低了计算负担，最近它已被广泛应用于涉及目标检测、图像分类和物体识别的计算机视觉领域。在 Facebook 提出的 YOLO 也是相关研究的一个里程碑 [26, 27]。

## 材料与方法

本文介绍了一种带有图像分割的 CNN 模型，用于检测模糊海水中的鱼类。开发了特定的数据集以支持本研究。采用了数据增强变换方案以获得更多学习资源，因为该特定环境中的原始图像不足以用于训练目的。为了解决过拟合问题，应用了 dropout 算法。由于我们的目标是将此系统集成到需要实时应用的 AUV 中，因此讨论了一些权衡以减少处理时间。本节详细阐述了带有优化方法的系统设计。

## CNN 架构

CNN 模型通常由许多层组成，例如输入层、带有非线性单元的卷积层以及全连接层 [28, 29]。图 2 展示了 CNN 的一个示例。第一层是输入层，它从外部世界接收图像信息作为学习资源。接下来的层是卷积层，负责从图像中提取特征。卷积操作是常见的数学运算之一。两个离散函数的卷积公式如 Equation (1) 所示：

```
(f * g)[n] = \sum_{m=-\infty}^{\infty} f[m]g[n - m].
```

(1)

图 2. RGB 彩色图像上的卷积操作 [30]。

该数据集包含 256 级的 RGB 彩色图像。下面的 3×3 矩阵 W0 被称为内核或滤波器。在实践中，卷积操作分别在 R、G 和 B 通道上执行，然后将结果相加以获得特征图中的每个元素，如图 2 所示。

为了更准确地提取对象的特征，每个卷积层中使用大量滤波器。例如，为了提取边缘、纹理等特征，如图 3 所示有相应的滤波器可用。

执行卷积操作时，需要考虑特征图的大小。有三个主要因素影响其大小：深度、步幅和填充。图 4 说明了深度为 3、步幅为 1 且带零填充的特征图。对于复杂的神经网络，两个相邻层之间通常有两种连接类型，如图 5 所示，分别是全连接层和局部连接神经层。对于全连接神经网络，输入层中的所有像素都与隐藏层中的每个神经元相连，如图 5(a) 所示。CNN 的最后两层通常是全连接层，分别是 softmax 层和输出层。由于大量参数会增加计算量并延迟处理。对于局部连接神经网络，输入层中仅部分像素与隐藏层中的下一个神经元相连，如图 5(b) 所示。这种连接类型将减少连接数量并加快系统速度。

| Operation | Filter | Feature map |
|---|---|---|
| 恒等 | \(\begin{bmatrix} 0 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 0 \end{bmatrix}\) | ![Feature map] |
| 边缘检测 | \(\begin{bmatrix} 1 & 0 & -1 \\ 0 & 0 & 0 \\ -1 & 0 & 1 \end{bmatrix}\) | ![Feature map] |
| | \(\begin{bmatrix} 1 & 1 & 0 \\ 1 & -4 & 1 \\ 0 & 1 & 0 \end{bmatrix}\) | ![Feature map] |
| | \(\begin{bmatrix} -1 & -1 & -1 \\ -1 & 8 & -1 \\ -1 & -1 & -1 \end{bmatrix}\) | ![Feature map] |
| 锐化 | \(\begin{bmatrix} 0 & -1 & 0 \\ -1 & 5 & -1 \\ 0 & -1 & 0 \end{bmatrix}\) | ![Feature map] |
| 盒模糊 | \(\frac{1}{9} \begin{bmatrix} 1 & 1 & 1 \\ 1 & 1 & 1 \\ 1 & 1 & 1 \end{bmatrix}\) | ![Feature map] |
| 高斯模糊 | \(\frac{1}{16} \begin{bmatrix} 1 & 2 & 1 \\ 2 & 4 & 2 \\ 1 & 1 & 1 \end{bmatrix}\) | ![Feature map] |

图 3. 图像特征提取中的卷积操作应用 [31]。

CNN 中的卷积层使用局部连接，如图 6 所示。例如，特征图中的值 8 仅与输入图像中的 3×3 矩阵 [0, 0, 0; 0, 1, 1; 0, 1, 2] 相连，与输入图像像素的其余部分无关。

该 CNN 所有层的全连接或局部连接参数列于表 1 中。

图 7 以简化方式可视化了系统。

## 使用 ImageNet 数据集进行系统验证

在将本系统应用于本研究开发的海洋鱼类数据集之前，作者从著名的 ImageNet ILSVRC [21] 下载图像，通过物体分类进行系统验证测试。共有 500 张图像，涵盖 20 个类别，范围从鱼、珊瑚、海龟、青蛙、船等。这里所有 RGB 图像均重新缩放到 448×448。实测值图像是通过手动操作标注软件获得的。每张图像被分为 7×7 单元格的网格。每个单元格将预测两个边界框的位置信息和类别信息，这些信息组成一个 1×1×30 向量。该向量包含对象中心坐标 (X, Y)、边界框的宽度 w 和高 h、置信度分数，以及鱼的预测概率，如图 8 所示。为了预测图像中的目标位置，目标被显示在一个边界框中。实测值和预测之间总是存在误差。开发了损失函数来衡量误差，包含三部分：坐标误差、(Intersection over union) IoU 误差和类别误差。Equation (2) 给出了损失函数的数学形式。

```
Loss = \sum_{i=0}^{S} coordError + IoUError + classError.
```

这里，IoU 用于衡量位置精度，如图 9 所示。

![](img/1752b062af2760b8561f6faaf183b3d0_141_0.png)

图 4. 使用卷积操作的特征提取器。

图像中每个网格单元将预测 B 个边界框以围住对象，从而预测对象的定位和类别。此外，每个边界框还有一个置信度。置信度分数与对象的类别无关。它只是描述预测框实际围住真实对象的确定程度。

Confidence = Pr(object) × IOU, (3)

where Pr(object) represents the probability of the object of interest. If there is an object in the grid cell, the Pr(object) is 1; otherwise, it is 0.

Usually, loss function is in the form of the sum of squared errors as shown below [33]. It consists of three parts which are localization errors, confidence errors, and probabilities errors.

Loss = \sum_{i=0}^{S^2} \sum_{j=0}^{B} [(x_i - \hat{x}_i)^2 + (y_i - \hat{y}_i)^2 + (w_i - \hat{w}_i)^2 + (h_i - \hat{h}_i)^2] + \sum_{i=0}^{S^2} \sum_{j=0}^{B} (C_i - \hat{C}_i)^2 + \sum_{i=0}^{S^2} \sum_{C \in classes} (P_i(c) - P_i(\hat{c}))^2, (4)

where x_i, y_i are the ground truth coordinates of objects center; w_i, h_i are the width and height of the ground truth bounding box; \hat{x}_i \hat{y}_i are the predicted coordinates of the objects center; \hat{w}_i \hat{h}_i are the width and height of predicted bounding box. Above Figure 10 shows one set of output with confidence values from different classes.

![](img/1752b062af2760b8561f6faaf183b3d0_142_0.png)

图 5. 全连接神经网络和局部连接神经网络 [32]。


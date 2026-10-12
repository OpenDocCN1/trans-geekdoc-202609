
其次，相邻的图像像素在统计上是相关的。然而，全连接网络没有“相邻”的概念，而是平等地对待每个输入之间的关系。如果以相同的方式随机打乱训练图像和测试图像的像素，网络仍可进行训练，且没有实际区别。第三，图像的解释在几何变换下是稳定的。如果将一棵树的图像向左平移几个像素，它仍然是一棵树的图像。然而，这种平移改变了网络的每一个输入。因此，全连接模型必须在每个位置分别学习代表树的像素模式，这显然是低效的。

卷积层使用在整个图像中共享的参数，独立处理每个局部图像区域。它们比全连接层使用更少的参数，利用了相邻像素之间的空间关系，并且不必在每个位置重新学习像素的解释。一个主要由卷积层组成的网络被称为 `convolutional neural network` 或 `CNN`。

## 10.1 不变性与等变性

我们在上文论证了图像的某些属性（例如树的纹理）在变换下是稳定的。在本节中，我们使这一想法在数学上更加精确。如果图像 `x` 的函数 `f[x]` 满足以下条件，则称其对变换 `t[x]` 是 `invariant`（不变）的：

```
(10.1)
```

换句话说，无论变换 `t[x]` 如何，函数 `f[x]` 的输出都相同。用于图像分类的网络应该对图像的几何变换具有不变性（图 10.1a–b）。即使图像经过了平移、旋转、翻转或扭曲，网络 `f[x]` 仍应将其识别为包含同一物体。

![Figure 10.1 Invariance and equivariance for translation. a–b) In image classification, the goal is to categorize both images as "mountain" regardless of the horizontal shift that has occurred. In other words, we require the network prediction to be invariant to translation. c,e) The goal of semantic segmentation is to associate a label with each pixel. d,f) When the input image is translated, we want the output (colored overlay) to translate in the same way. In other words, we require the output to be equivariant with respect to translation. Panels c–f) adapted from Bousselham et al. (2021).](images/c10-fig-0001.jpg)

如果图像 `x` 的函数 `f[x]` 满足以下条件，则称其对变换 `t[x]` 是 `equivariant`（等变）或 `covariant`（协变）的：

```
(10.2)
```

换句话说，如果 `f[x]` 的输出以与输入相同的方式在变换 `t[x]` 下发生变化，则称 `f[x]` 对该变换是等变的。用于逐像素图像分割的网络应该对变换具有等变性（图 10.1c–f）；如果图像被平移、旋转或翻转，网络 `f[x]` 应返回以相同方式变换的分割结果。

## 10.2 面向 1D 输入的卷积网络

卷积网络由一系列卷积层组成，每一层都对平移具有等变性。它们通常还包含池化机制，从而诱导出对平移的部分不变性。为了阐述清晰，我们首先考虑面向 1D 数据的卷积网络，这更容易可视化。在 10.3 节中，我们将进阶到可应用于图像数据的 2D 卷积。

### 10.2.1 1D 卷积运算

`Convolutional layers`（卷积层）是基于 `convolution`（卷积）运算的网络层。在 1D 中，卷积将输入向量 `x` 变换为输出向量 `z`，使得每个输出 `z[i]` 都是附近输入的加权和。在每个位置使用相同的权重，这些权重统称为 `convolution kernel`（卷积核）或 `filter`（滤波器）。对输入进行加权求和的区域称为 `kernel size`（核大小）。对于核大小为三的情况，我们有：

```
(10.3)
```

其中 `ω` = [`ω`[1], `ω`[2], `ω`[3]]^T 是卷积核（图 10.2）。请注意，卷积运算对平移具有等变性。如果我们平移输入 `x`，则相应的输出 `z` 将以相同的方式被平移。

---

Problem 10.1

---

![Figure 10.2 1D convolution with kernel size three. Each output z[i] is a weighted sum of the nearest three inputs x[i−1], x[i], and x[i+1], where the weights are ω = [ω1, ω2, ω3]. a) Output z2 is computed as z2 = ω1x1 + ω2x2 + ω3x3. b) Output z3 is computed as z3 = ω1x2 + ω2x3 + ω3x4. c) At position z1, the kernel extends beyond the first input x1. This can be handled by zero padding, in which we assume values outside the input are zero. The final output is treated similarly. d) Alternatively, we could only compute outputs where the kernel fits within the input range ("valid" convolution); now, the output will be smaller than the input.](images/c10-fig-0002.jpg)

### 10.2.2 填充

公式 10.3 表明，每个输出都是通过对输入中前一个、当前和后一个位置进行加权和来计算的。这引出了一个问题：如何处理第一个输出（没有前一个输入）和最后一个输出（没有后一个输入）。

有两种常见方法。第一种是在输入边缘填充新值，然后照常进行。`Zero padding`（零填充）假设输入在其有效范围之外为零（图 10.2c）。其他可能性包括将输入视为循环的，或在边界处反射它。第二种方法是丢弃卷积核超出输入位置范围的输出位置。这些 `valid convolutions`（有效卷积）的优点是在输入边缘不引入额外信息。然而，它们的缺点是表示的尺寸会减小。

### 10.2.3 步幅、核大小和膨胀

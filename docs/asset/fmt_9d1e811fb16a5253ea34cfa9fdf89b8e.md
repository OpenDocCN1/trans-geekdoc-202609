
声学数据的增强方法包括音高偏移、时间拉伸、动态范围压缩和添加随机噪声（例如 Abeßer 等人，2017；Salamon & Bello，2017；Xu 等人，2015；Lasseck，2018），以及混合数据对（Zhang 等人，2017c；Yun 等人，2019）、遮挡特征（Park 等人，2019）和使用 GANs 生成新数据（Mun 等人，2017）。语音数据的增强包括声道长度扰动（Jaitly & Hinton，2013；Kanda 等人，2013）、风格迁移（Gales，1998；Ye & Young，2004）、添加噪声（Hannun 等人，2014）和语音合成（Gales 等人，2009）。

文本的增强方法包括：通过交换、删除和插入字母在字符级别添加噪声（Belinkov & Bisk，2018；Feng 等人，2020），或生成对抗样本（Ebrahimi 等人，2018），使用常见拼写错误（Coulombe，2018），随机交换或删除单词（Wei & Zou，2019），使用同义词（Kolomiyets 等人，2011），修改形容词（Li 等人，2017c），被动化（Min 等人，2020），使用生成模型创建新数据（Qiu 等人，2020），以及往返翻译到另一种语言再翻译回来（Aiken & Park，2010）。文本增强方法由 Bayer 等人（2022）综述。

### 习题

#### 习题 9.1

考虑一个模型，其参数的先验分布为均值为零、方差为 `![c9-fig-5023.jpg](img/c9-fig-5023.jpg)` 的正态分布，因此

```
![c9-fig-5024.jpg](img/c9-fig-5024.jpg)
```

(9.21)

其中 `j` 为模型参数的索引。我们现在最大化 `![c9-fig-5025.jpg](img/c9-fig-5025.jpg)`。证明该模型的相关损失函数等价于 L2 正则化。

#### 习题 9.2

当加入 L2 正则化（公式 9.5）时，损失函数的梯度如何变化？

#### 习题 9.3*

考虑一个线性回归模型 `y = ϕ[0] + ϕ[1]x`，具有输入 `x`、输出 `y` 和参数 `ϕ[0]` 与 `ϕ[1]`。假设我们有 `I` 个训练样本 `{x[i], y[i]}` 并使用最小二乘损失。考虑在每次训练迭代中向输入 `x[i]` 添加均值为零、方差为 `![c9-fig-5012.jpg](img/c9-fig-5012.jpg)` 的高斯噪声。期望的梯度更新是什么？

#### 习题 9.4*

推导当我们使用标签平滑时多类分类的损失函数，使得目标概率分布在正确类别处为 0.9，剩余的 0.1 概率质量分配给其余的 `D[o] − 1` 个类别。

#### 习题 9.5

证明具有衰减率 `λ` 的权重衰减参数更新：

```
![c9-fig-5026.jpg](img/c9-fig-5026.jpg)
```

(9.22)

在原始损失函数 `L[ϕ]` 上等价于使用 L2 正则化的标准梯度更新，使得修正后的损失函数 `![c9-fig-5030.jpg](img/c9-fig-5030.jpg)[ϕ]` 为：

```
![c9-fig-5027.jpg](img/c9-fig-5027.jpg)
```

(9.23)

其中 `ϕ` 为参数，`α` 为学习率。

#### 习题 9.6

考虑一个参数为 `ϕ = [ϕ[0], ϕ[1]]^T` 的模型。以类似于图 9.1b 的形式绘制 L0、`![c9-fig-5028.jpg](img/c9-fig-5028.jpg)` 和 L1 正则化项。LP 正则化项为 `![c9-fig-5029.jpg](img/c9-fig-5029.jpg)`。

## 第 10 章：卷积网络

第 2-9 章介绍了深度神经网络的监督学习流程。然而，这些章节仅考虑了具有从输入到输出单一路径的全连接网络。第 10-13 章介绍了具有更稀疏连接、共享权重和并行处理路径的更专业网络组件。本章描述 `卷积层`，主要用于处理图像数据。

图像具有三个特性，表明需要专门的模型架构。首先，它们是高维的。分类任务的典型图像包含 224×224 个 RGB 值（即 150,528 个输入维度）。全连接网络中的隐藏层通常大于输入尺寸，因此即使对于浅层网络，权重数量也将超过 150,528²，即 220 亿。这在所需训练数据、内存和计算方面带来了明显的实际问题。

其次，相邻的图像像素在统计上是相关的。然而，全连接网络没有“相邻”的概念，而是平等地对待每个输入之间的关系。如果以相同的方式随机打乱训练图像和测试图像的像素，网络仍可进行训练，且没有实际区别。第三，图像的解释在几何变换下是稳定的。如果将一棵树的图像向左平移几个像素，它仍然是一棵树的图像。然而，这种平移改变了网络的每一个输入。因此，全连接模型必须在每个位置分别学习代表树的像素模式，这显然是低效的。

卷积层使用在整个图像中共享的参数，独立处理每个局部图像区域。它们比全连接层使用更少的参数，利用了相邻像素之间的空间关系，并且不必在每个位置重新学习像素的解释。一个主要由卷积层组成的网络被称为 `convolutional neural network` 或 `CNN`。

### 10.1 不变性与等变性

我们在上文论证了图像的某些属性（例如树的纹理）在变换下是稳定的。在本节中，我们使这一想法在数学上更加精确。如果图像 `x` 的函数 `f[x]` 满足以下条件，则称其对变换 `t[x]` 是 `invariant`（不变）的：

```
(10.1)
```

换句话说，无论变换 `t[x]` 如何，函数 `f[x]` 的输出都相同。用于图像分类的网络应该对图像的几何变换具有不变性（图 10.1a–b）。即使图像经过了平移、旋转、翻转或扭曲，网络 `f[x]` 仍应将其识别为包含同一物体。

![Figure 10.1 Invariance and equivariance for translation. a–b) In image classification, the goal is to categorize both images as "mountain" regardless of the horizontal shift that has occurred. In other words, we require the network prediction to be invariant to translation. c,e) The goal of semantic segmentation is to associate a label with each pixel. d,f) When the input image is translated, we want the output (colored overlay) to translate in the same way. In other words, we require the output to be equivariant with respect to translation. Panels c–f) adapted from Bousselham et al. (2021).](img/c10-fig-0001.jpg)

如果图像 `x` 的函数 `f[x]` 满足以下条件，则称其对变换 `t[x]` 是 `equivariant`（等变）或 `covariant`（协变）的：

```
(10.2)
```

换句话说，如果 `f[x]` 的输出以与输入相同的方式在变换 `t[x]` 下发生变化，则称 `f[x]` 对该变换是等变的。用于逐像素图像分割的网络应该对变换具有等变性（图 10.1c–f）；如果图像被平移、旋转或翻转，网络 `f[x]` 应返回以相同方式变换的分割结果。

### 10.2 面向 1D 输入的卷积网络

卷积网络由一系列卷积层组成，每一层都对平移具有等变性。它们通常还包含池化机制，从而诱导出对平移的部分不变性。为了阐述清晰，我们首先考虑面向 1D 数据的卷积网络，这更容易可视化。在 10.3 节中，我们将进阶到可应用于图像数据的 2D 卷积。

#### 10.2.1 1D 卷积运算

`Convolutional layers`（卷积层）是基于 `convolution`（卷积）运算的网络层。在 1D 中，卷积将输入向量 `x` 变换为输出向量 `z`，使得每个输出 `z[i]` 都是附近输入的加权和。在每个位置使用相同的权重，这些权重统称为 `convolution kernel`（卷积核）或 `filter`（滤波器）。对输入进行加权求和的区域称为 `kernel size`（核大小）。对于核大小为三的情况，我们有：

```
(10.3)
```

其中 `ω` = [`ω`[1], `ω`[2], `ω`[3]]^T 是卷积核（图 10.2）。请注意，卷积运算对平移具有等变性。如果我们平移输入 `x`，则相应的输出 `z` 将以相同的方式被平移。

---

Problem 10.1

---

![Figure 10.2 1D convolution with kernel size three. Each output z[i] is a weighted sum of the nearest three inputs x[i−1], x[i], and x[i+1], where the weights are ω = [ω1, ω2, ω3]. a) Output z2 is computed as z2 = ω1x1 + ω2x2 + ω3x3. b) Output z3 is computed as z3 = ω1x2 + ω2x3 + ω3x4. c) At position z1, the kernel extends beyond the first input x1. This can be handled by zero padding, in which we assume values outside the input are zero. The final output is treated similarly. d) Alternatively, we could only compute outputs where the kernel fits within the input range ("valid" convolution); now, the output will be smaller than the input.](images/c10-fig-0002.jpg)

#### 10.2.2 填充

公式 10.3 表明，每个输出都是通过对输入中前一个、当前和后一个位置进行加权和来计算的。这引出了一个问题：如何处理第一个输出（没有前一个输入）和最后一个输出（没有后一个输入）。

有两种常见方法。第一种是在输入边缘填充新值，然后照常进行。`Zero padding`（零填充）假设输入在其有效范围之外为零（图 10.2c）。其他可能性包括将输入视为循环的，或在边界处反射它。第二种方法是丢弃卷积核超出输入位置范围的输出位置。这些 `valid convolutions`（有效卷积）的优点是在输入边缘不引入额外信息。然而，它们的缺点是表示的尺寸会减小。

#### 10.2.3 步幅、核大小和膨胀率

在上面的示例中，每个输出都是最近三个输入的总和。然而，这只是卷积操作大家族中的一种，该家族的成员由其 `stride`（步幅）、`kernel size`（核大小）和 `dilation rate`（膨胀率）来区分。当我们在每个位置都计算输出时，我们称之为步幅为一。不过，也可以将核按大于一的步幅进行移动。如果步幅为二，我们创建的输出数量大约减半（图 10.3a–b）。

![Figure 10.3 Stride, kernel size, and dilation. a) With a stride of two, we evaluate the kernel at every other position, so the first output z1 is computed from a weighted sum centered at x1, and b) the second output z2 is computed from a weighted sum centered at x3 and so on. c) The kernel size can also be changed. With a kernel size of five, we take a weighted sum of the nearest five inputs. d) In dilated or atrous convolution, we intersperse zeros in the weight vector to allow us to combine information over a large area using fewer weights.](img/c10-fig-0003.jpg)

图 10.3 步幅、核大小和膨胀。a) 步幅为二时，我们在每隔一个位置计算核，因此第一个输出 `z[1]` 是通过以 `x[1]` 为中心的加权和计算得出的，b) 第二个输出 `z[2]` 是通过以 `x[3]` 为中心的加权和计算得出的，以此类推。c) `kernel size`（核大小）也可以改变。核大小为五时，我们取最近五个输入的加权和。d) 在膨胀或空洞卷积中，我们在权重向量中插入零，以便使用更少的权重来组合更大区域的信息。

`kernel size`（核大小）可以增加以在更大的区域上进行积分（图 10.3c）。然而，它通常保持为奇数，以便能够以当前位置为中心。增加核大小的缺点是需要更多的权重。这引出了 `dilated`（膨胀）或 `atrous`（空洞）卷积的概念，其中核值与零交错插入。例如，我们可以通过将第二个和第四个元素设为零，将大小为五的核变为大小为三的膨胀核。我们仍然从更大的输入区域整合信息，但只需要三个权重即可（图 10.3d）。我们在权重之间插入的零的数量称为 `dilation rate`（膨胀率）。

---

问题 10.2–10.4

---

#### 10.2.4 卷积层

卷积层通过卷积输入、添加偏置 `β`，并将每个结果通过激活函数 `a[•]` 来计算其输出。对于核大小为三、步幅为一、膨胀率为零的情况，第 `i^(th)` 个隐藏单元 `h[i]` 的计算公式为：

![c10-fig-5004.jpg](img/c10-fig-5004.jpg)

 (10.4)

其中偏置 `β` 和核权重 `ω[1]`、`ω[2]`、`ω[3]` 是可训练参数，（采用零填充时）当输入 `x` 超出有效范围时，我们将其视为零。这是全连接层的一个特例，全连接层按如下方式计算第 `i^(th)` 个隐藏单元：

![c10-fig-5005.jpg](img/c10-fig-5005.jpg)

 (10.5)

如果有 `D` 个输入 `x[•]` 和 `D` 个隐藏单元 `h[•]`，该全连接层将拥有 `D²` 个权重 `ω[••]` 和 `D` 个偏置 `β[•]`。卷积层仅使用三个权重和一个偏置。如果大多数权重设为零，其他权重被约束为相同，全连接层可以精确复现这一点（图 10.4）。

![Figure 10.4 Fully connected vs. convolutional layers. a) A fully connected layer has a weight connecting each input x to each hidden unit h (colored arrows) and a bias for each hidden unit (not shown). b) Hence, the associated weight matrix Ω contains 36 weights relating the six inputs to the six hidden units. c) A convolutional layer with kernel size three computes each hidden unit as the same weighted sum of the three neighboring inputs (arrows) plus a bias (not shown). d) The weight matrix is a special case of the fully connected matrix where many weights are zero and others are repeated (same colors indicate same value, white indicates zero weight). e) A convolutional layer with kernel size three and stride two computes a weighted sum at every other position. f) This is also a special case of a fully connected network with a different sparse weight structure.](img/c10-fig-0004.jpg)

图 10.4 全连接层与卷积层对比。a) 全连接层具有连接每个输入 `x` 到每个隐藏单元 `h` 的权重（彩色箭头）以及每个隐藏单元的偏置（未显示）。b) 因此，相关的权重矩阵 `Ω` 包含 36 个权重，关联六个输入与六个隐藏单元。c) 核大小为三的卷积层将每个隐藏单元计算为相同三个相邻输入的加权和（箭头）加上一个偏置（未显示）。d) 权重矩阵是全连接矩阵的一个特例，其中许多权重为零，其他权重重复（相同颜色表示相同值，白色表示零权重）。e) 核大小为三且步幅为二的卷积层在每隔一个位置计算加权和。f) 这也是具有不同稀疏权重结构的全连接网络的一个特例。

---

问题 10.5

---

#### 10.2.5 通道


两种基本的半监督技术是标签扩散 (LS) 和标签传播 (LP)。LS 基于将样本（孤立点）视为图中的节点，其关系由边权重定义，例如：若 `i ≠ j` 则 `w[ij] = exp(−||x[i] − x[j]||²/2σ²)`，且 `w[ij] = 0`。权重矩阵经过对称归一化以获得更好的收敛性。每个节点从其邻近点接收信息，并根据接收到最多信息的类别来选择其标签。还引入了正则化项，基于拥有平滑分类器（在相似点之间不改变）以获得更好的标签分配。LP 基于一种迭代技术，考虑转移矩阵来更新标签，该技术从随机初始化开始。转移矩阵指的是通过在未标记数据的高密度区域传播，从一个节点移动到另一个节点的概率。

### 7.2.7.2 深度半监督技术

正如后面的 7.3.9.3 节所述，自编码器 (AE) 是一种 DNN，包含两个主要阶段：一个将输入空间映射到低维（潜在空间）的编码器，和一个从潜在表示重构输入空间的解码器。因此，该网络基于无监督学习。AE 可以堆叠形成深度堆叠自编码器 (SAE) 网络，这增加了网络的能力，并为每个隐藏层提供非线性潜在表示。此外，为了提高泛化能力并增加在数据中提取更有趣模式的可能性，可以向每层的输入添加各种噪声水平，称为堆叠去噪自编码器 (SDAE)。SDAE 的优化基于最小化原始数据与预测网络输出之间的重构误差。

尽管 AE、SAE 和 SDAE 基于无监督学习（使用重构误差），但它们已被用于半监督学习，方法是在学习到的编码器上添加一层，并基于监督任务的标记数据对网络进行微调（监督式 SDAE）。该技术的主要缺点是监督和无监督学习分为两个阶段。因此，第一阶段可能会提取对最终监督任务无用的信息。因此，微调阶段无法大幅改变一个已完全学习的网络 [[21]](#c07.xhtml#c7-bib-0021)。

Ladder 是 SAE/SDAE 的一种扩展，考虑了用于无监督学习的重构误差和用于监督学习的估计正确标签的似然的联合目标函数。它有两条无噪声和有噪声的编码器路径以及一个去噪解码器 [[19]](#c07.xhtml#c7-bib-0019)。

### 7.2.8 模糊聚类

在这种聚类方法中，每个元素都有一组隶属度系数，对应于属于给定簇的程度 [[22]](#c07.xhtml#c7-bib-0022)。这与 `k-means` 不同，在 `k-means` 中，每个对象确切地属于一个簇。因此，与被称为硬聚类或非模糊聚类的 `k-means` 不同，这被称为软聚类方法。

在模糊聚类中，靠近簇中心的点，其属于该簇的程度可能高于位于簇边缘的点。元素属于给定簇的程度是一个从 0 到 1 变化的数值。

然而，模糊 `c-means` (FCM) 作为最广泛使用的模糊聚类算法，与 `k-means` 非常相似。在 FCM 中，簇的质心计算为所有点的平均值，按其属于该簇的程度加权。`c-means` 的目标是通过最小化以下定义的目标函数，将点聚类为 `k` 个簇：

(7.7)

```
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll">
  <munderover>
    <mo>∑</mo>
    <mrow><mi>j</mi><mo>=</mo><mn>1</mn></mrow>
    <mi>k</mi>
  </munderover>
  <munder>
    <mo>∑</mo>
    <mrow><msub><mi>x</mi><mi>i</mi></msub><mo>∈</mo><msub><mi>c</mi><mi>j</mi></msub></mrow>
  </munder>
  <msubsup><mi>u</mi><mi mathvariant="italic">ij</mi><mi>m</mi></msubsup>
  <msup>
    <mfenced open="(" close=")">
      <mrow>
        <msub><mi mathvariant="bold">x</mi><mi>i</mi></msub>
        <mo>−</mo>
        <msub><mi mathvariant="normal">μ</mi><mi>j</mi></sub>
        <mspace width="0.2em"/>
      </mrow>
    </mfenced>
    <mn>2</mn>
  </msup>
</math>
```

其中 `μ[j]` 是簇 `j` 的中心，`m` 为模糊化参数，通常手动选择，`u_ij^m` 是观测值 `x[i]` 属于簇 `c[j]` 的程度，定义为：

## 7.3 分类算法

使用大量数据样本进行训练和测试新样本是分类算法的两个主要阶段。在训练阶段，数据的可分性在最小化所谓的交叉验证误差方面起着至关重要的作用。尽管通过使用核函数，数据特征空间可以映射到特征变得可分的高维空间，但对于所有类型的数据，识别合适且准确的核函数并非易事。在以下章节中，将简要回顾用于生物医学信号（如 EEG）分类的更常用分类器。

### 7.3.1 决策树

决策树（DT）是用于分类和预测的流行、简单、强大且通常为非线性的工具。它们表示可供人类理解并用于基于知识的系统的 `rules`。

决策树算法的主要步骤如下：

1.  选择 `best` 属性以分割剩余实例，并使该（些）属性成为决策节点
2.  对每个子节点递归地重复此过程
3.  当满足以下条件时停止：
    1.  所有实例具有相同的目标属性值
    2.  没有更多属性
    3.  没有更多实例。

一个用于湿度传感器的简单 DT 示例可以是：

> 如果时间是上午 9:00 且没有下雨，湿度水平会是多少（低、中、重三者之一）？

根据属性的数量，决策树可能如图 7.3 所示。DT 可以完美拟合任何训练数据，具有零偏差和高方差。不同的算法用于确定节点处的 `best` 分割。

![图 7.3 显示无雨时上午 9:00 湿度水平的决策树示例。](img/c07f003.gif)

**图 7.3** 显示无雨时上午 9:00 湿度水平的决策树示例。

DT 常用于通过学习树迭代输入数据来预测数据标签 [[25]](#c07.xhtml#c7-bib-0025)。在此过程中，将特征属性与决策条件进行比较以达到特定类别。DT 仅适用于线性可分数据，且构建最优学习树的过程是 NP 完全问题 [[26]](#c07.xhtml#c7-bib-0026)。

在将 DT 应用于 EEG 信号时，我们需要考虑到输入信号天然具有非平稳性、信噪比差、依赖于身体或精神任务，并受各种伪迹污染，如外部电磁波、肌电图和眼电图。

在一个示例 [[27]](#c07.xhtml#c7-bib-0027) 中，作者提出了一种简单的 DT 结构来分类与上/下/右/左计算机光标移动意象相关的 EEG 数据。从三名受试者的 EEG 中计算出连续 Morlet 小波系数的均值和方差、自回归（AR）模型参数、平均导数和偏度，并将它们用作 DT 系统的输入特征。

在另一个应用 [[28]](#c07.xhtml#c7-bib-0028) 中，提出了一种分类框架和一种数据缩减方法，基于协方差矩阵流形利用黎曼几何来区分用于 BCI 的多类运动意象 EEG。当解迭代因施加的约束而遵循流形（而非例如欧几里得空间）时，黎曼几何很有用。例如在 BCI 语境中，此类约束是与运动皮层内不同区域相关的空间约束，每个区域属于特定身体部位的运动。感兴趣的函数应在黎曼流形上可微。因此，在 BCI 语境中，使用空间协方差矩阵，它是一个对称正定矩阵 [[27]](#c07.xhtml#c7-bib-0027)，[[28]](#c07.xhtml#c7-bib-0028)。

为了执行分类，设计了一种 DT 分类器来识别运动意象任务并减少不可分情况的分类误差。后来，这已与其他分类器结合，以实现半监督分类。

主要思路是使用空间协方差矩阵作为 EEG 信号描述符，并依赖黎曼几何直接利用对称正定矩阵流形的拓扑结构对这些矩阵进行分类。这使得无需使用空间滤波即可提取 EEG 信号中包含的空间信息。基于空间协方差矩阵，使用两种不同的方法估计每两次试验之间的距离（并用于分类），即 (i) 到黎曼均值的滤波测地线最小距离和 (ii) 切空间映射，两者均在黎曼流形上进行 [[28]](#c07.xhtml#c7-bib-0028)。

本工作使用了一个简单的 Emotiv EEG 系统，并对三种类型的肩关节运动（即屈曲、伸展和外展）进行了分类。结果表明，对于某些受试者，可达到 90% 以上的准确率。

### 7.3.2 随机森林

随机森林分类器从训练集的随机选取子集中创建一组决策树。然后汇总不同决策树的投票来决定测试数据的最终类别 [[30]](#c07.xhtml#c7-bib-0030)。术语 `random forest` 源于贝尔实验室的 Tin Kam Ho 于 1995 年最初提出的随机决策森林。该方法结合了 Breiman 的“装袋”思想和随机特征选择。装袋或 `bootstrap aggregation` 是一种减少估计预测函数方差的技术。随机森林分类器实际上是使用 `de‐correlated` 树的装袋扩展。

随机森林分类器的主要优点是无需剪枝，准确率和变量重要性自动生成，过拟合不是问题，对训练数据中的异常值不太敏感，且参数设置容易。

然而，也存在一些局限性。回归过程无法预测训练数据可用范围之外的值，且在回归中极端值往往预测不准确。这导致高值被低估，低值被高估。

与作为装袋技术的传统随机森林不同，正如其名称所示，在 `boosting` 中，一个模型从另一个模型学习，从而提升学习效果。装袋方案以并行方式训练一组单独的模型。每个模型由数据的随机子集训练。相反，提升以顺序方式训练一组单独的模型。每个单独的模型从前一个模型犯的错误中学习。`AdaBoost` 是一种提升集成模型，与决策树配合效果良好。AdaBoost 通过增加误分类数据点的权重来从错误中学习。Adaboost 的优化有时通过自适应方法（如梯度下降）进行，因此 Adaboost 和所谓的 `gradient boosting` 非常相似。

在一项应用 [[31]](#c07.xhtml#c7-bib-0031) 中，Edla 等人使用随机森林分类器对代表各种人类精神状态的简单一阶和二阶统计量进行分类和分析，这些统计量源自单通道 EEG。随机森林分类器在 BCI 中的其他一些应用详见 [[32]](#c07.xhtml#c7-bib-0032)。

### 7.3.3 线性判别分析

作为一种由 Vapnik 引入的成熟技术 [[33]](#c07.xhtml#c7-bib-0033)，LDA 是一种用于寻找特征线性组合的方法，该组合能表征或分离两个或多个类别的对象或事件。在 LDA 中，数据被投影到单一维度上，在此维度上对给定的测试点进行类别分配。所得组合可用作线性分类器。在 LDA 中假设各类别服从正态分布。与 PCA 类似，LDA 既用于降维也用于数据分类。

在二分类数据集中，给定类别 1 和类别 2 的先验概率分别为 `p[1]` 和 `p[2]`，类别均值和总均值分别为 `μ[1]`、`μ[2]` 和 `μ`，类别方差为 `cov[1]` 和 `cov[2]`。

(7.10)

```
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mi>μ</mi><mo>=</mo><msub><mi>p</mi><mn>1</mn></msub><mo>×</mo><msub><mi>μ</mi><mn>1</mn></msub><mo>+</mo><msub><mi>p</mi><mn>2</mn></msub><mo>×</mo><msub><mi>μ</mi><mn>2</mn></msub></math>
```

然后，利用类内离散度和类间离散度来构建类别可分性的必要准则。类内离散度是各类别的期望协方差。多类别情况下的离散度度量计算如下：

(7.11)

```
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><msub><mi>S</mi><mi>w</mi></msub><mo>=</mo><munderover><mo>∑</mo><mrow><mi>j</mi><mo>=</mo><mn>1</mn></mrow><mi>C</mi></munderover><msub><mi>p</mi><mi>j</mi></msub><mo>×</mo><msub><mo mathvariant="italic">cov</mo><mi>j</mi></msub></math>
```

其中 `C` 指类别数量，且

(7.12)

```
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><msub><mo mathvariant="italic">cov</mo><mi>j</mi></msub><mo>=</mo><mfenced open="(" close=")"><mrow><msub><mi mathvariant="bold">x</mi><mi>j</mi></msub><mo>−</mo><msub><mi mathvariant="normal">μ</mi><mi>j</mi></msub></mrow></mfenced><msup><mfenced open="(" close=")"><mrow><msub><mi mathvariant="bold">x</mi><mi>j</mi></msub><mo>−</mo><msub><mi mathvariant="normal">μ</mi><mi>j</mi></msub></mrow></mfenced><mi>T</mi></msup></math>
```

略有不同的是，类间离散度估计如下：

(7.13)

```
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><msub><mi>S</mi><mi>b</mi></msub><mo>=</mo><mfrac><mn>1</mn><mi>C</mi></mfrac><munderover><mo>∑</mo><mrow><mi>j</mi><mo>=</mo><mn>1</mn></mrow><mi>C</mi></munderover><mfenced open="(" close=")"><mrow><msub><mi mathvariant="bold">x</mi><mi>j</mi></msub><mo>−</mo><msub><mi mathvariant="normal">μ</mi><mi>j</mi></msub></mrow></mfenced><msup><mfenced open="(" close=")"><mrow><msub><mi mathvariant="bold">x</mi><mi>j</mi></msub><mo>−</mo><msub><mi mathvariant="normal">μ</mi><mi>j</mi></msub></mrow></mfenced><mi>T</mi></msup></math>
```

然后，目标是找到一个判别平面 **w**，以最大化类间与类内离散度（方差）的比率：

(7.14)

```
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><msub><mi>J</mi><mi mathvariant="italic">LDA</mi></msub><mo>=</mo><mfrac><mrow><mi mathvariant="bold">w</mi><msub><mi>S</mi><mi>b</mi></msub><msup><mi mathvariant="bold">w</mi><mi>T</mi></msup></mrow><mrow><mi mathvariant="bold">w</mi><msub><mi>S</mi><mi>w</mi></msub><msup><mi mathvariant="bold">w</mi><mi>T</mi></msup></mrow></mfrac></math>
```

在实践中，类别均值和协方差是未知的，但可以从训练集中估计得出。在上述方程中，可以用最大似然估计或最大后验估计代替精确值。

LDA 已被广泛用于 EEG 分类。在文献 [[34]](#c07.xhtml#c7-bib-0034) 的一项研究中，LDA 被用于对健康老年对照组、阿尔茨海默病和血管性痴呆的 EEG 频谱参数进行分类。在这项工作中，提取的频谱特征包括绝对 EEG delta 功率、从低频到高频的衰减、振幅、alpha 功率的中心和离散度以及整个 EEG 频谱的基线功率。正则化方法使用收缩强度参数，以整个样本协方差的加权平均值来替代组内样本协方差。该参数强调协方差矩阵的较大特征值，同时弱化较小的特征值，从而创建一个修正了基于样本估计特征值偏差的合并协方差矩阵。最优收缩参数由交叉验证确定。

LDA 是 BCI 中最流行的分类算法之一。文献 [[35]](#c07.xhtml#c7-bib-0035) 中给出了一个例子，其中设计了一个两类 BCI，两类均服从高斯分布，但类方差不同。


(12.10)![equation](img/c12-disp-0011.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mi mathvariant="bold">X</mi><mo>=</mo><mfenced open="\[" close="\]"><mtable><mtr><mtd><maligngroup/><msub><mi>x</mi><mn>1</mn></msub><mspace width="2.5em"/><msub><mi>x</mi><mn>2</mn></msub><mspace width="1em"/><mo>&#8943;</mo><mspace width="1.25em"/><msub><mi>x</mi><mi>l</mi></msub></mtd></mtr><mtr><mtd><maligngroup/><msub><mi>x</mi><mrow><mi>l</mi><mo>+</mo><mn>1</mn></mrow></msub><mspace width="1.75em"/><msub><mi>x</mi><mrow><mi>l</mi><mo>+</mo><mn>2</mn></mrow></msub><mspace width="0.5em"/><mo>&#8943;</mo><mspace width="1em"/><msub><mi>x</mi><mrow><mn>2</mn><mi>l</mi></mrow></msub></mtd></mtr><mtr><mtd><maligngroup/><mo>&#8942;</mo><mspace width="3.5em"/><mo>&#8945;</mo><mspace width="3.5em"/><mo>&#8942;</mo></mtd></mtr><mtr><mtd><maligngroup/><msub><mi>x</mi><mrow><mfenced open="(" close=")"><mrow><mi>I</mi><mo>&#8722;</mo><mn>1</mn></mrow></mfenced><mi>l</mi></mrow></msub><mspace width="0.75em"/><msub><mi>x</mi><mrow><mfenced open="(" close=")"><mrow><mi>I</mi><mo>&#8722;</mo><mn>1</mn></mrow></mfenced><mi>l</mi><mo>+</mo><mn>1</mn></mrow></msub><mspace width=".5em"/><mo>&#8943;</mo><mspace width=".5em"/><msub><mi>x</mi><mi mathvariant="italic">Il</mi></msub></mtd></mtr></mtable></mfenced></math>

其中 $I = \lfloor n/l \rfloor$。然后，如 **图 12.9** 所示，通过将张量的每个切片视为 **X** 的窗口化版本，将该矩阵转换为张量 $\underline{\mathbf{X}}$。矩阵到张量的转换可用以下方程解释：

(12.11)![equation](img/c12-disp-0012.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><msub><munder accentunder="false"><mi mathvariant="bold">X</mi><mo>\_</mo></munder><mrow><mi>i</mi><mo>&#8759;</mo></mrow></msub><mo>=</mo><mi mathvariant="bold">X</mi><mfenced open="(" close=")"><mrow><mi>i</mi><mo>,</mo><mfenced open="(" close=")"><mrow><mi>j</mi><mo>&#8722;</mo><mn>1</mn></mrow></mfenced><mi>o</mi><mo>+</mo><mn>1</mn><mo>:</mo><mfenced open="(" close=")"><mrow><mi>j</mi><mo>&#8722;</mo><mn>1</mn></mrow></mfenced><mi>o</mi><mo>+</mo><msub><mi>l</mi><mn>1</mn></msub></mrow></mfenced></math> ![Figure 12.9 I × K matrix X is converted to tensor images where J is the number of segments obtained by window size l 1 and overlapping interval l 1 − o.](img/c12f009.gif)

**图 12.9** $I \times K$ 矩阵 **X** 被转换为张量 $\underline{\mathbf{X}}$，其中 $J$ 是由窗口大小 $l_1$ 和重叠间隔 $l_1 - o$ 获得的分段数。

![Figure 12.10 Block diagram of the single‐channel source separation system using an adaptive procedure for selecting the desired subspace. This is carried out by tuning a set of weights governed by the EMD process.](img/c12f010.gif)

**图 12.10** 单通道源分离系统的框图，采用自适应过程选择所需子空间。这是通过调整由 `EMD` 过程控制的一组权重来实现的。

![images](img/c12-i0006.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mtext>where</mtext><mspace width="0.2em"/><mi>j</mi><mo>=</mo><mn>1</mn><mo>,</mo><mn>2</mn><mo>,</mo><mo>&#8230;</mo><mo>,</mo><mi>J</mi><mo>;</mo><mspace width="1em"/><mi>J</mi><mo>=</mo><mfenced open="&#8970;" close="&#8971;"><mrow><mfrac><mrow><mi>l</mi><mo>&#8722;</mo><msub><mi>l</mi><mn>1</mn></msub></mrow><mi>o</mi></mfrac><mo>+</mo><mn>1</mn></row></mfenced><mo>,</mo><mspace width="1.5em"/><mtext>and</mtext><mspace width="0.75em"/><mi>i</mi><mo>=</mo><mn>1</mn><mo>,</mo><mn>2</mn><mo>,</mo><mo>&#8230;</mo><mo>,</mo><mi>I</mi></math> 其中 $l_1 - o$ 是连续窗口的重叠间隔，$l_1$ 是窗口大小。然后，使用交替最小二乘法估算构建张量的因子，以最佳拟合 `PARAFAC` 模型。

与 `SSA` 相同，在 `TSSA` 中子群定义为 $I = I_1 \cup I_2 \cup \dots I_m$ 且 $\underline{\mathbf{X}} = \sum_{i=1}^m \underline{\mathbf{X}}_{I_i}$。在该工作中，经验模态分解 (`EMD`) 已被用于选择包含感兴趣频率范围内固有模态函数 (`IMF`) 的子群 [[41]](#c12.xhtml#c12-bib-0041)、**图 12.10** 表示整体系统的框图。最后，通过汉克尔化可以获得原始信号的重构，该过程通过将信号分段转换为汉克尔矩阵来执行。然后，通过一一对应重构数据。

正常状况、睡眠限制以及睡眠延长/剥夺条件下受试者的睡眠阶段已被估算，并与临床专家的评分进行了比较。所执行的客观测量也证明了该方法相比多个基准具有优越的性能。

### 12.6.5 神经网络的应用

作为一种非线性多输入多输出分类器，神经网络（`NNs`）可用于对不同波形进行分类，以识别各个睡眠阶段以及精神疾病的类型。`NNs`已被广泛用于分析复杂系统，而无需预先对其进行精确建模[[42]](#c12.xhtml#c12-bib-0042)。在开发`NN`时，通常不需要关于数据统计（如分布）的先验信息。`NN`分类器的输入可以是原始数据、压缩数据，或是在原始域或变换域中从数据中测量或估计出的最具描述性的特征。就睡眠数据而言，睡眠`EEG`中的许多典型波形可用于训练和分类。它们包括纺锤波、波丘、α波、波丘串（尽管通常不出现在`EEGs`中）和背景波。这些特征中的每一个在`T‐F`域中表现不同。

时延神经网络（`TDNN`）可用于检测在时间轴上位置大致已知的小波[[43]](#c12.xhtml#c12-bib-0043)。在该类网络中，小波在时间位置上的偏差必须很小。然而，对于`EEGs`，必须补偿大于小波持续时间的偏移，因为波形的发生时间是未知的。

为了识别时移模式，Shimada 等人[[44]](#c12.xhtml#c12-bib-0044)提出了另一种称为睡眠`EEG`识别神经网络（`SRNN`）的方法。该`NN`具有一个输入层、两个隐藏层和一个输出层。从算法观点和输入-输出连接来看，`SRNN`和`TDNN`非常相似。主要区别在于：在`TDNN`中，第二隐藏层的每一行连接到输出层的单个单元，而在`SRNN`中，两层中相似的单元相互连接。

为了使用`SRNN`，数据被变换到`TF`域。然而，该方法不是在时间上移动滑动窗口，而是考虑重叠的数据块。以时间为水平轴、频率为垂直轴的二维块被视为`NN`的输入。设`y[j, c]`和`d[j, c]`分别为第`j`个输出神经元和输入模式`c`的期望模式，则：

(12.12)

```
E = 1/2 * Σ (j=1 to Output neurons) Σ (c=1 to Input patterns) (y[j, c] - d[j, c])^(1/2)
```

因此，学习规则通过使用以下梯度来最小化代价函数：

(12.13)

```
Δw[p, q] = μ * (∂E / ∂w[p, q])
```

其中`w[p, q]`是神经元`p`和`q`之间的连接权重，`μ`是学习率。在学习阶段，该过程[[44]](#c12.xhtml#c12-bib-0044)执行两次通过：前向和后向，遍历整个网络。在前向传递中，施加输入并计算输出。在后向传递中，将输出与期望模式进行比较并计算误差。然后将误差反向传播通过网络，并通过均方误差（`MSE`）作为权重函数的梯度下降来改变连接权重。当学习算法收敛时，获得最优权重`w[p, q]`。然后使用这些权重对新波形进行分类，即执行泛化。关于该方案性能的更多细节可参见[[44]](#c12.xhtml#c12-bib-0044)。

### 12.6.6 基于模型的分析

基于模型的方法依赖于关于数据生成机制或数据本身的先验知识。表征`NREM`的生理信号生成模型也一直是多位研究人员研究的主题[45–47]。这些模型描述了`NREM`睡眠深度与产生慢波的神经元机制之间的关系。这种机制本质上是神经网络中闭环的反馈，或是单个细胞中离子电流的相互作用。已确定`NREM`睡眠深度调节反馈环路的增益[[48]](#c12.xhtml#c12-bib-0048)。根据该模型，慢波功率（`SWP`）的睡眠相关变化源于反馈增益的变化。因此，睡眠深度的增加与产生低频`EEG`的神经元反馈环路增益的增加有关。

文献[[49]](#c12.xhtml#c12-bib-0049)提出了一种基于模型的慢波反馈增益估计器。**图 12.11** 中描绘的初始模型是模拟的，并建立了其离散时间近似。在模拟模型中，`G(f)`是带通（谐振）滤波器的复频率传递函数，表达式为：

(12.14)

```
G(f) = 1 / (1 + j · Y(f))
```

其中`j = sqrt(-1)`且

(12.15)

```
Y(f) = (f0 / B) · (f / f0 - f0 / f)
```

其中谐振频率`f[0]`和带宽`B`约为 1 和 1.5 Hz。闭环方程可写为：

#### 模型与方程

(12.16)

```
u̇(t) = p(t) · s(t) + ẇ(t)
```

**图 12.11** 神经元慢波生成模型；`u̇(t)` 是 EEG 信号源的导数，`G(f)` 表示慢波 `s(t)` 的频率选择性反馈。信号 `p(t)` 是待辨识的反馈增益，`w(t)` 是白噪声，`L(f)` 是表示从信号源到电极路径的低通滤波器，`q` 是颅骨的衰减效应。

其中 `u̇(t) = du(t)/dt` 且 `ẇ(t) = dw(t)/dt`。可以看出传递函数取决于 `p(t)`。当 `p(t)` 为常数时：

(12.17)

```
U(f) = 1 / (1 - p · G(f))
```

因此：

(12.18)

```
|U(f)|² = (1 + Y²(f)) / ((1 - p)² + Y²(f))
```

在这种情况下：

(12.19)

```
S(f) = G(f) · U(f) = G(f) / (1 - p · G(f)) = 1 / (1 - p + j · Y(f))
```

输出 `x(t)` 是 `u̇(t)` 的低通副本，由因子 `q` 衰减。当 `p = 0` 时无反馈，当 `p = 1` 时在 `f = f₀` 处存在无限峰值。低通滤波器 `L(f)` 已知，截止频率约为 1.8 Hz。

模型的反馈增益 `p(t)` 代表睡眠深度。因此，目标是估计反馈增益。为此，使用 50 Hz 采样器（采样间隔 Δ = 0.02 秒）对观测值 `du(t)` 进行采样。然后，在区间 `[0 ≤ kΔ < NΔ - Δ]` 上定义 `Du(kΔ) = u(kΔ + Δ) - u(kΔ)`，其中 `NΔ = T`。同时认为在区间 `T` 上 `p(t) = p` 为常数。公式 (12.13) 变为：

(12.20)

```
Du(kΔ) = p · s(kΔ) · Δ + Dw(kΔ)
```

其中 `Dw(kΔ) = w(kΔ + Δ) - w(kΔ)` 是标准连续时间维纳过程 `w(t)` 的增量。假设反馈滤波器 `G(f)` 的初始状态为 `G₀` 且 `w(kΔ)` 服从高斯分布，根据贝叶斯规则，`Du(kΔ)` 的似然可以分解为：

## 12.7 基于 EEG 和多模态 PSG 分析的睡眠期脑异常检测与监测

`EEG` 为睡眠期大脑提供了重要且独特的信息。`PSG` 一直是一项成熟的睡眠分析方法，也是睡眠医学中的主要诊断工具，它根据 R&K 解释的标准对睡眠信号的宏观结构进行解读 [[50]](#c12.xhtml#c12-bib-0050)。多导睡眠图或睡眠研究是一项多参数测试，对睡眠期间发生的生理生物学变化进行全面记录。通常在夜间进行。`PSG` 监测睡眠期间的多种身体功能，包括大脑 (`EEG`)、眼动 (`EOG`)、肌肉活动或骨骼肌激活 (`EMG`) 以及心律 (`ECG`)。

### 12.7.1 睡眠呼吸暂停分析

睡眠呼吸暂停综合征 (`SAS`)、慢性打鼾和日间过度嗜睡会给日常生活带来问题，并产生短期和长期的生理及心理影响。自 20 世纪 70 年代识别出睡眠呼吸暂停后，`PSG` 已被用作金标准，结合并评估呼吸、外周脉搏血氧测定、心率以及两导 `EEG`，以评估这些疾病。后来，记录的打鼾声成为研究的主要焦点。总体而言，研究表明，并非 `PSG` 记录的所有信号都用于评估呼吸暂停或低通气 [51–53]。文献 [51, 52] 中表明，打鼾声和血氧仪输出的 `SpO2` 值可用于呼吸暂停分析。也有报告称仅使用这两种模态中的一种即可，即声音信号 [[53]](#c12.xhtml#c12-bib-0053) 或使用血氧仪评估低氧血症 [[54]](#c12.xhtml#c12-bib-0054) 足以评估呼吸暂停。然而，睡眠纺锤波和慢波活动、觉醒及相关活动可从 `EEG` 信号中检测并在睡眠期间进行监测。对于呼吸暂停分析，描述这些活动通常需要将信号在时间上分割为 20–30 秒的固定片段。

![equation](img/c12-disp-0022.png)

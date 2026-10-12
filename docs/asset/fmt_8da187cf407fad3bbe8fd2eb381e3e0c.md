
# 20. Chui, C.K. (1992). *An Introduction to Wavelets*. Academic Press.

# 21. Stein, E.M. (1958). 关于 Littlewood‐Paley、Lusin 和 Marcinkiewicz 函数。 *Transactions of the American Mathematical Society* **88**: 430–466.

# 22. Vetterli, M. 和 Kovačevic, J. (1995). *Wavelets and Subband Coding*. Prentice Hall.

# 23. Daubechies, I., Lu, J., 和 Wu, H. (2011). 同步挤压小波变换：一种类经验模态分解工具。 *Applied and Computational Harmonic Analysis* **30** (2): 243–261.

# 24. Glassman, E.L. (2005). 一种基于神经元动作电位的小波型滤波器，用于人头皮脑电图分析。 *IEEE Transactions on Biomedical Engineering* **52** (11): 1851–1862.

# 25. Chen, Y. 和 Ma, J. (2014). 基于 f‐x 经验模态分解预测滤波的随机噪声衰减。 *Geophysics* **79** (3): V81–V91.

# 26. Chen, Y., Zhou, C., Yuan, J., 和 Jin, Z. (2014). 经验模态分解在地震资料随机噪声衰减中的应用。 *Journal of Seismic Exploration* **23**: 481–495.

# 27. Huang, Y.X., Schmitt, F.G., Lu, Z.M., 和 Liu, Y.L. (2008). 利用希尔伯特谱分析研究湍流尺度间歇性的振幅频率特征。 *Europhysics Letters* **84**: 40010.

# 28. Gerloff, G., Richard, J., Hadley, J. 等 (1998). 人类皮层运动区在简单、内部定时和外部定时手指运动中的功能耦合与区域激活。 *Brain* **121** (8): 1513–1531.

# 29. Sharott, A., Magill, P.J., Bolam, J.P., 和 Brown, P. (2005). 大鼠大脑皮层和基底神经节中相干振荡场电位的方向性分析。 *Journal of Physiology* **562** (3): 951–963.

# 30. Granger, C.W.J. (1969). 利用计量经济模型和交叉谱方法研究因果关系。 *Econometrica* **37**: 424–438.

# 31. Bernosconi, C. 和 König, P. (1999). 通过脑电生理记录的谱分析研究皮层相互作用的方向性。 *Biological Cybernetics* **81** (3): 199–210.

# 32. Kaminski, M., Ding, M., Truccolo, W., 和 Bressler, S. (2001). 评估神经系统中的因果关系：格兰杰因果性、定向传递函数和显著性统计评估。 *Biological Cybernetics* **85**: 145–157.

# 33. Kaminski, M. 和 Blinowska, K. (1991). 描述大脑结构中信息流动的新方法。 *Biological Cybernetics* **65**: 203–210.

# 34. Jing, H. 和 Takigawa, M. (2000). 重复经颅磁刺激后脑电相干性的观察。 *Clinical Neurophysiology* **111**: 1620–1631.

# 35. Kuś, R., Kaminski, M., 和 Blinowska, K. (2004). EEG 活动传播的确定：成对估计与多通道估计。 *IEEE Transactions on Biomedical Engineering* **51** (9): 1501–1510.

# 36. Ginter, J. Jr., Kaminski, M.J., Blinowska, K.J., 和 Durka, P. (2001). 时频空间中的相位和振幅分析；应用于自主手指运动。 *Journal of Neuroscience Methods* **110**: 113–124.

# 37. Akaike, H. (1974). 统计模型阶数识别的新视角。 *IEEE Transactions on Automatic Control* **19**: 716–723.

# 38. Ding, M., Bressler, S.L., Yang, W., 和 Liang, H. (2000). 利用自适应多元自回归建模对皮层事件相关电位进行短窗谱分析：数据预处理、模型验证和变异性评估。 *Biological Cybernetics* **83**: 35–45.

# 39. Widrow, B., Glover, J.R., McCool, J. Jr. 等 (1975). 自适应噪声消除原理及应用。 *Proceedings of the IEEE* **63** (12): 1692–1716.

# 40. Satorius, E.H. 和 Shensa, M.J. (1980). 递归格滤波器：简要概述。 *Proceedings of the 19th IEEE Conference on Decision Control*, 955–959.

# 41. Lee, D., Morf, M., 和 Friedlander, B. (1981). 递归平方根梯形估计算法。 *IEEE Transactions on Accoustic, Speech, Signal Processing* **29**: 627–641.

# 42. Lawsen, C.L. 和 Hansen, R.J. (1974). *Solving Least‐Squares Problem*. Prentice Hall.

# 43. Proakis, J.G., Rader, C.M., Ling, F. 等 (2001). *Algorithms for Statistical Signal Processing*. Prentice Hall.

# 5 EEG 信号分解

## 5.1 简介

脑电图 (`EEG`) 信号记录的是源自大脑内部的许多信号的组合。这些源可以是皮层源、深层源或伪迹。由于从源到传感器的时间滞后没有显著差异，因此这些组合被视为线性混合。

尽管在大多数情况下 `EEG` 信号作为多通道数据进行处理，但也存在仅有单个 `EEG` 通道可用的情况。示例包括某些非侵入式脑机接口 (`BCI`) 应用、驾驶员疲劳监测，或主要用于电脑游戏的人机交互。这使得单通道 `EEG` 处理，以及在某些情况下的分解，成为研究议题。

单通道源分解并不总是有效，且准确性不高。尽管如此，对于许多分析单通道生物信号（包括上述简单且非侵入式的 `EEG` 记录）而言，它是有用的。

多通道 `EEG` 分解的另一个局限性在于通道数与可能源的数量之间的关系。在这种情况下，可以应用稀疏成分分析 (`SCA`) 等正则化方法。

在本章后续章节中，我们将从单通道源分离开始，然后转到可通过独立成分分析 (`ICA`)、矩阵分解或张量分解执行的多通道情况。随后我们将重点关注 `SCA` 在两个重要场景中的应用：第一，每个时间采样点仅有一个源处于活跃状态；第二，每个时间采样点或信号片段中活跃源的数量最多可达电极数减一。

## 5.2 奇异谱分析

单通道源分解方法之一是奇异谱分析 (`SSA`)。

### 5.2.1 分解

此阶段包含嵌入操作，随后进行奇异值分解（`SVD`）。嵌入操作将一维时间序列 **f** 映射为一个 *l* × *k* 矩阵，如文献 [\[148\]](#c05.xhtml#c5-bib-0148) 所示：

![equation](img/c5-disp-0001.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mi mathvariant="bold">X</mi><mo>=</mo><mfenced open="{" close="}"><msub><mi>x</mi><mi mathvariant="italic">ij</mi></msub></mfenced><mo>=</mo><mfenced open="\[" close="\]"><mrow><msub><mi mathvariant="bold">x</mi><mn>1</mn></msub><mo>,</mo><msub><mi mathvariant="bold">x</mi><mn>2</mn></msub><mo>,</mo><mo>&#8230;</mo><mo>,</mo><msub><mi mathvariant="bold">x</mi><mi>k</mi></msub></mrow></mfenced></math> (5.1)![equation](img/c5-disp-0002.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mspace width="0.65em"/><mo>=</mo><mfenced open="\[" close="\]"><mtable><mtr><mtd><maligngroup/><malignmark/><msub><mi>f</mi><mn>0</mn></msub><mspace width="1em"/><msub><mi>f</mi><mn>1</mn></msub><mspace width="1.5em"/><msub><mi>f</mi><mn>2</mn></msub><mspace width="1.0em"/><mo>&#8230;</mo><mspace width="1em"/><msub><mi>f</mi><mrow><mi>k</mi><mo>&#8722;</mo><mn>1</mn></mrow></msub></mtd></mtr><mtr><mtd><maligngroup/><malignmark/><mspace width="0em"/><msub><mi>f</mi><mn>1</mn></msub><mspace width="1em"/><msub><mi>f</mi><mn>2</mn></msub><mspace width="1.5em"/><msub><mi>f</mi><mn>3</mn></msub><mspace width="1em"/><mo>&#8230;</mo><mspace width="1em"/><msub><mi>f</mi><mi>k</mi></msub></mtd></mtr><mtr><mtd><maligngroup/><malignmark/><msub><mi>f</mi><mn>2</mn></msub><mspace width="1em"/><msub><mi>f</mi><mn>3</mn></msub><mspace width="1.5em"/><msub><mi>f</mi><mn>4</mn></msub><mspace width="1.0em"/><mo>&#8230;</mo><mspace width="1em"/><msub><mi>f</mi><mrow><mi>k</mi><mo>+</mo><mn>1</mn></mrow></msub></mtd></mtr><mtr><mtd><maligngroup/><malignmark/><mo>&#8942;</mo><mo>&#8942;</mo><mo>&#8945;</mo><mo>&#8942;</mo></mtd></mtr><mtr><mtd><maligngroup/><malignmark/><msub><mi>f</mi><mrow><mi>l</mi><mo>&#8722;</mo><mn>1</mn></mrow></msub><mspace width="0.2em"/><msub><mi>f</mi><mi>l</mi></msub><mspace width="1em"/><msub><mi>f</mi><mrow><mi>l</mi><mo>+</mo><mn>1</mn></mrow></msub><mspace width="0.5em"/><mo>&#8230;</mo><mspace width="0.5em"/><msub><mi>f</mi><mrow><mi>r</mi><mo>&#8722;</mo><mn>1</mn></mrow></msub><mspace width="0.2em"/></mtd></mtr></mtable></mfenced></math>

其中 *r* = *k + l* − 1 为窗口长度 (1 ≤ *l* ≤ *r*)，上标 *T* 表示向量的转置。向量 **x**[*i*] 称为 *l-滞后向量*（或简称为 *滞后向量*）。窗口长度 *l* 应足够大。请注意，轨迹矩阵 **X** 是一个汉克尔矩阵，这意味着对角线 *i* + *j* = *const*. 上的所有元素都相等。

在 `SVD` 阶段，计算轨迹矩阵的 `SVD` 并将其表示为一系列秩为一的双正交基本矩阵之和。考虑协方差矩阵 **C** [x] = **XX**^(*T*) 的特征值按幅度递减顺序记为 λ[1],…, λ [*l*] (λ[1] ≥*…* ≥ λ [*l*]  ≥ 0)，对应的正交特征向量记为 **u** [**1**] , **u** [2], …, **u**[*l*] 。令 *d* = max(*i*; 使得 λ [*i*] *\>* 0) = *rank*(**X**): 若记 ![images](img/c5-i0001.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><msub><mi mathvariant="bold">v</mi><mi>i</mi></msub><mo>=</mo><msup><mi mathvariant="bold">X</mi><mi>T</mi></msup><msub><mi mathvariant="bold">u</mi><mi>i</mi></msub><mo>/</mo><msqrt><msub><mi>&#955;</mi><mi>i</mi></msub></msqrt></math>，则轨迹矩阵的 `SVD` 可写为：

(5.2)![equation](img/c5-disp-0003.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mi mathvariant="bold">X</mi><mo>=</mo><msubsup><mo>&#8721;</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>d</mi></msubsup><msub><mi mathvariant="bold">X</mi><mi>i</mi></msub><mo>=</mo><msubsup><mo>&#8721;</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>d</mi></msubsup><msqrt><msub><mi>&#955;</mi><mi>i</mi></msub></msqrt><msub><mi mathvariant="bold">u</mi><mi>i</mi></msub><msubsup><mi mathvariant="bold">v</mi><mi>i</mi><mi>T</mi></msubsup></math>

构成分量通过配置 **X** 和 `SVD` 操作的约束过程进行分离。由于期望信号可能具有不同的能量水平，通常不对特征值的顺序与生理上占主导地位的分量之间的关系做任何假设（注意，如果 λ[1] *\>>* λ[2]，信息能量将主要集中在与第一奇异值相关联的最占主导地位的矩阵 ![images](img/c5-i0002.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><msub><mi mathvariant="bold">X</mi><mn>1</mn></msub><mo>=</mo><msqrt><msub><mi>&#955;</mi><mn>1</mn></msub></msqrt><msub><mi mathvariant="bold">u</mi><mn>1</mn></msub><msubsup><mi mathvariant="bold">v</mi><mn>1</mn><mi>T</mi></msubsup></math> 中）。

通常，可以用 `ICA` 代替 `SVD`。这将子空间分解问题转化为 `ICA` 问题，可通过采用合适的 `ICA` 技术来求解。`ICA` 将在本章后面讨论。

### 5.2.2 重构

#### SSA 重构与多通道 EEG 分解

##### SSA 重构过程

在重构过程中，基础矩阵首先被分成若干组（取决于时间序列中的分量数量——在本应用中为肌电图 (`EMG`) 和心电图 (`ECG`) 信号），然后将每组内的矩阵相加。组的大小，换句话说，每个子空间的长度，可以根据一些先验信息来指定。在从记录的 `EMG` 中去除 `ECG` 的情况下，该特征和期望分量会根据对待提取信号统计特性的约束，被联合（且自动）识别出来。


新兴的 ReRAM 交叉阵列 [62, 191] 提供了一种固有的存内矩阵-向量乘法结构，如[图 8.5](#Chapter8.html#c08_fig5)所示。与 CMOS 嵌入电路相比，基于 ReRAM 交叉阵列的方法可提供三大主要优势：(1) 无需每个周期从外部加载 ![image](images/ch08_si74.gif) 即可将感测矩阵嵌入存储器中；(2) 在单周期内执行矩阵-向量乘法；(3) 因其非易失性而将漏电功耗降至最低。

![image](images/PBPC0390-08-f05.jpg)

**图 8.5** 由新兴非易失性 ReRAM 交叉阵列构成的嵌入电路

ReRAM 交叉阵列结构由三层组成：顶层的水平导线、底层的垂直导线，以及位于中间层每个交叉点的 ReRAM 器件。对于一个 ![image](images/ch08_si75.gif) 的 ReRAM 交叉阵列，假设第 ![image](images/ch08_si76.gif) 行的输入信号为 ![image](images/ch08_si77.gif)，第 ![image](images/ch08_si78.gif) 行第 ![image](images/ch08_si79.gif) 列 ReRAM 器件的电导为 ![image](images/ch08_si80.gif)，则流经第 ![image](images/ch08_si81.gif) 列的输出电流为 ![image](images/ch08_si82.gif)。换句话说，交叉阵列结构固有地支持存内嵌入运算：

![image](images/ch08_si425.gif)

其中 ![image](images/ch08_si83.gif) 为跨阻抗放大器 (TIA) 的跨阻抗。必须确保输入 ![image](images/ch08_si84.gif)，以避免 ![image](images/ch08_si85.gif) 发生意外数值变化，其中 ![image](images/ch08_si86.gif) 为器件编程阈值电压。

嵌入矩阵的映射是通过 ReRAM 交叉阵列的电阻编程来实现的，对应于 ![image](images/ch08_si87.gif)。由于旨在用于存储器，ReRAM 器件通常为双稳态，其开态电阻与关态电阻之比高达 ![image](images/ch08_si88.gif) [291, 293]。更高分辨率的电阻编程至多仅在 4 或 5 个电平上得到验证 [293, 294]。因此，在当前制造工艺下，由于工艺变异大，连续（或接近连续）数值分辨率的电阻编程在实际应用中极具挑战。换句话说，实值采样矩阵不适配 ReRAM 交叉阵列，布尔采样矩阵更受青睐。

由于 ReRAM 交叉阵列在电导方面本质上是 ![image](images/ch08_si89.gif) 二值的，因此 ![image](images/ch08_si90.gif) 布尔矩阵的映射如下：![image](images/ch08_si91.gif) 对应高电阻态 (HRS)，![image](images/ch08_si92.gif) 映射为低电阻态 (LRS)。要映射 ![image](images/ch08_si93.gif)，需考虑简单的线性变换：![image](images/ch08_si94.gif)，其中 ![image](images/ch08_si95.gif)、![image](images/ch08_si96.gif) 为全 1 矩阵，![image](images/ch08_si97.gif) 为输入向量。![image](images/ch08_si98.gif) 由一个额外的全 LRS 列实现，该列产生 ![image](images/ch08_si99.gif) 作为其他列的电流偏移，如[图 8.5](#Chapter8.html#c08_fig5)所示。各类硬件支持的采样矩阵如[表 8.2](#Chapter8.html#c08_tbl2)所示。

**表 8.2** 不同采样矩阵在各类硬件平台上的兼容性

![image](images/tab8.2.jpg)

### 8.3.3 问题建模

对于满足 RIP 且畸变为 ![image](images/ch08_si116.gif) 的采样矩阵 ![image](images/ch08_si115.gif)，以下等式也将成立：

![image](images/ch08_si426.gif)

如果 ![image](images/ch08_si117.gif) 是一个正交旋转矩阵。换句话说，如果我们能找到一个正交旋转矩阵，将实值 NuMax 嵌入矩阵 ![image](images/ch08_si118.gif) 变换为足够接近布尔矩阵 ![image](images/ch08_si119.gif) 的矩阵，那么 ![image](images/ch08_si120.gif) 的布尔嵌入便可保持原始畸变 ![image](images/ch08_si121.gif)。换句话说，所得的 ![image](images/ch08_si122.gif) 仍针对与 NuMax 嵌入 ![image](images/ch08_si123.gif) 相同的训练数据集进行优化，同时可高效映射至[图 8.4](#Chapter8.html#c08_fig4)(c) 和图 8.5 所示电路，并大幅降低功耗。

布尔采样矩阵优化可进而建模为以下优化问题：

![image](images/ch08_si427.gif)

其中 ![image](images/ch08_si124.gif) ![image](images/ch08_si125.gif) 为从数据集学习得到的优化实值采样矩阵，将数据从高 ![image](images/ch08_si126.gif)\-维投影至低 ![image](images/ch08_si127.gif)\-维；![image](images/ch08_si128.gif) 为试图将 ![image](images/ch08_si129.gif) 变换为布尔矩阵的正交旋转矩阵。![image](images/ch08_si130.gif) 为最接近的布尔矩阵解，其中接近程度由 Frobenius 范数定义。

理想情况下，若正交变换矩阵 ![image](images/ch08_si131.gif) 能将 ![image](images/ch08_si132.gif) 旋转为精确的布尔矩阵，即 (8.5) 的最优值为零，则优化布尔嵌入的畸变 ![image](images/ch08_si133.gif) 将与 NuMax 实值嵌入完全相同。实际中，随着非零最优值的存在，![image](images/ch08_si134.gif) 与 ![image](images/ch08_si135.gif) 的接近程度表明了从 ![image](images/ch08_si136.gif) 到 ![image](images/ch08_si137.gif) 的信息损失程度。另一方面，这可理解为等效的近正交旋转 ![image](images/ch08_si138.gif) 将实值 ![image](images/ch08_si139.gif) 变换为精确的布尔 ![image](images/ch08_si140.gif)。正交程度的偏离意味着 ![image](images/ch08_si141.gif) 的信息损失。

### 8.4 IH 算法

考虑到正交约束 ![image](images/ch08_si142.gif) 和整数约束 ![image](images/ch08_si143.gif) 均为非凸约束，同时求解 (8.5) 中建模的问题极其困难。若一次仅考虑一个约束，(8.5) 可拆分为两个可处理的问题：若针对 ![image](images/ch08_si144.gif) 考虑正交约束，且 ![image](images/ch08_si145.gif) 为给定布尔矩阵，问题转化为寻找实现最大矩阵一致性的*正交旋转*矩阵；若针对 ![image](images/ch08_si146.gif) 和 ![image](images/ch08_si147.gif) 考虑整数约束，且为给定正交矩阵，问题转化为实现最大矩阵一致性的*布尔量化*。本节提出一种启发式方法，迭代求解*正交旋转*问题和*布尔量化*问题，并在每轮中逐步逼近 ![image](images/ch08_si148.gif) 的最优解。

#### 8.4.1 正交旋转

寻找能将给定实值投影矩阵 ![image](images/ch08_si150.gif) 旋转至另一给定布尔矩阵 ![image](images/ch08_si151.gif) 的正交变换矩阵 ![image](images/ch08_si149.gif) 的问题，可建模为：

![image](images/ch08_si428.gif)

代价函数可用迹函数表示为：

![image](images/ch08_si429.gif)

由于 ![image](images/ch08_si152.gif) 和 ![image](images/ch08_si153.gif) 为给定矩阵，![image](images/ch08_si154.gif) 和 ![image](images/ch08_si155.gif) 因此为两个常数。先将 ![image](images/ch08_si156.gif) 视为常数，则 (8.6) 中建模的优化问题可重写为：

![image](images/ch08_si430.gif)

并利用奇异值分解 ![image](images/ch08_si157.gif)，其中 ![image](images/ch08_si158.gif) ![image](images/ch08_si159.gif)，(8.8) 的代价函数可重写为：

![image](images/ch08_si431.gif)

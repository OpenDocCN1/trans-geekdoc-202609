
### 8.2.1 均衡化
均衡化的目的是减轻由 `FIR` 信道引起的 `ISI` 效应以及抵消由发射/接收硬件引起的非线性失真。需要注意的是，在典型的通信接收机中，等化器在基带工作，并放置在匹配滤波器兼采样器级之后。等化器重建传输序列 `u(n)` 或其延迟版本 `y(n)` = `u(n-d)`，其中 `d` 为传播延迟。等化器使用训练数据集对 {`x(n)`,`y(n)`} 进行训练，`n` = 1, …, `N`，目标是最小化平方误差的期望值 `E[e²(n)]` = `E[|ŷ(n)-y(n)|²]`，其中 `ŷ(n)` 是对应于输入 `x(n)` 的等化器的实际输出。训练完成后，权重被冻结，后续符号基于这些权重进行检测。最后一级由判决装置组成，该装置将连续信号映射到离散符号集（[图 8.1](#ch08.xhtml#f8_1)）。对于 `BPSK` 传输，判决装置的输出为

![图 8.1 包含均衡器的无线通信设置中的发射机和接收机系统。](images/Fig08_01.jpg)

`FIGURE 8.1` 包含均衡器的无线通信设置中的发射机和接收机系统。

$$\hat{u}\left( n \right) = \text{sign}\left\{ {\hat{y}\left( n \right)} \right\} = \left\{ \begin{matrix} {1,~\left| {~\hat{y}\left( n \right) \geq 0} \right.} \\ {- 1,~~\left. \middle| \text{otherwise} \right..} \\ \end{matrix} \right.$$

(8.3)

### 8.2.2 判决反馈均衡
如 [第 8.2.1 节](#ch08.xhtml#h8_2_1) 中所述的线性均衡器模型在像有线电话这样简单的信道上有效，其中 `ISI` 问题不是太严重。`ISI` 信道的严重程度取决于信道的频谱特性，并以特征值比 (`EVR`) 来衡量（[Haykin 2008](#ch08.xhtml#r8_17)）。具有较大 `EVR` 的信道具有更高的频谱零点程度，线性均衡器需要产生更高的增益来补偿它。这将导致噪声增益增加以及均衡器性能显著变差。像 `DFE` 这样的非线性均衡器不受此类限制的约束，适用于非线性信道和高 `EVR` 信道。`DFE` 通过利用均衡器的先前输出来抵消当前符号的 `ISI` 而工作。

常规 `DFE` 的简化框图如图 [图 8.2](#ch08.xhtml#f8_2) 所示，由三个主要单元组成：前馈滤波器、判决装置和反馈滤波器。等化器的输入是有噪声且失真的信号 `x(n)`，而输出是传输符号的估计值 `û(n)`。如果前馈滤波器和反馈滤波器的长度分别为 `N[f]` 和 `N[b]`，则这些滤波器在时间 `n` 的状态为

![图 8.2 DFE 的简单框图。](images/Fig08_02.jpg)

`FIGURE 8.2` `DFE` 的简单框图。

`x(n)` = [`x(n)`,…,`x(n-N[f]+1)`]

(8.4)

$$\mathbf{u}\left( n \right) = \left\{ \begin{matrix} {\left\lbrack {y\left( {n - 1} \right),\ldots y\left( {n - N_{b}} \right)} \right\rbrack,~~\text{in training mode}} \\ {\left\lbrack {\hat{u}\left( {n - d - 1} \right),\ldots,\hat{u}\left( {n - d - N_{b}} \right)} \right\rbrack,~~\text{in decision directed mode}} \\ \end{matrix} \right.$$

(8.5)

判决装置的输入随后获得为

$$\hat{y}\left( n \right) = \sum\limits_{i = 1}^{N_{f}}x\left( {n - i + 1} \right)h_{i}^{f} - \sum\limits_{j = 1}^{N_{b}}\hat{u}\left( {n - d - j} \right)h_{j}^{b}$$

(8.6)

其中

[`h[1]^(f)`,…,`h[N[f]]^(f)`] 和 [`h[1]^(b)`,…,`h[N[b]]^(b)`] 分别是前馈滤波器和反馈滤波器的滤波器系数。

在训练模式下，式 (8.6) 中的符号 [`û(n-d-1)`,…,`û(n-d-N[b])`] 被已知的目标向量 [`y(n-1)`,…`y(n-N[b])`] 替换。误差信号为

$$e\left( n \right) = \left\{ \begin{matrix} {y\left( n \right) - \hat{y}\left( n \right),~~\text{in training mode}} \\ {\hat{u}\left( {n - d} \right) - \hat{y}\left( n \right),~~\text{in decision directed mode}} \\ \end{matrix} \right.$$

(8.7)

训练算法的目标是最小化由 `E[|e(n)|²]` 给出的均方误差，这通过调整前馈和反馈滤波器的权重来实现。

## 8.3 小波神经网络
小波最初是在多分辨率分析领域引入的，此后已应用于包括信号处理在内的众多领域（[Goswami and Chan 2011](#ch08.xhtml#r8_16)）。`WNN` 另一方面通常是一个由输入、隐藏和输出层组成的三层神经网络。与 `ANN` 相反，`WNN` 中的隐藏层由小波基作为激活函数而不是 sigmoid 函数组成。`WNN` 的思想是迭代更新适合训练数据的波基参数。本节解释了小波分析和 `WNN` 的基本概念。

### 8.3.1 小波分析
小波变换区别于傅里叶变换的能力在于它能够在时域和频域中高效地表示任意信号。它使我们能够识别特定频率分量出现、存在或消失的时间。这是因为小波基函数具有 `compact support` 特性。小波基函数的紧支撑允许小波变换高效地表示信号中的突变或局部特征。

小波基由 `mother wavelet` `ψ` 的平移和伸缩生成。母小波是一个短时振荡信号，其平均值为零，即

∫()*ψ*(*t*)*d**t* = 0

(8.8)

除满足诸如容许性条件等其他要求外（[Goswami and Chan 2011](#ch08.xhtml#r8_16)）。母小波的平移和伸缩版本为

$$\psi_{a,b}\left( t \right) = \frac{1}{\left. \sqrt{}a \right.}\psi\left( \frac{t - b}{a} \right)$$

(8.9)

其中

1. `a` > 0 为尺度或伸缩因子，且
2. `b` 为位置或平移因子。设 `x(t)` 为任意函数。

`x(t)` 的连续小波变换 (`CWT`) 为

$$W\left( {a,b} \right) = \int\limits_{- \infty}^{\infty}x\left( t \right)\psi_{a,b}\left( t \right)dt$$

(8.10)

其中

1. `a` ≠ 0。

小波变换 `W(a,b)` 可被视为信号 `x(t)` 中对应基函数 `ψ[a, b](t)` 分量的“强度”或“振幅”。逆小波变换 (`IWT`) 允许从小波系数 `W(a,b)` 重建原始信号：

$$x\left( t \right) = \frac{1}{C_{\psi}}{\int_{- \infty}^{\infty}{\int_{- \infty}^{\infty}{\frac{1}{a^{2}}W\left( {a,b} \right)\psi_{a,b}\left( t \right)da~db}}}$$

(8.11)

其中

1. `C_ψ = ∫_{- ∞}^{∞}{ |ψ(ω)|² / ω dω }`。

离散小波变换 (`DWT`) 由于 `CWT` 相关的计算复杂度高，在实践中更常用。但在 `DWT` 中，不是离散化时间，而是将平移和伸缩参数取为离散值。如果在式 (8.10) 中，`a` 和 `b` 分别用 2^(-j) 和 `k`2^(-j) 替换，其中 `j`, `k` ∈ ℤ，函数 `x(t)` ∈ `L²` 的 `DWT` 为

`W[ψ]x(j,k)` = 2^(j/2)∫[-∞]^∞ `x(t)` `ψ`(2^(j)`t`-`k`) `d t`

(8.12)



条件:

\[
\begin{cases} 
\mathcal{H}_0 : Y \sim \mathcal{N}(0, \sigma^2 I_n), \\ 
\mathcal{H}_1 : Y \sim \mathcal{N}(\theta \neq 0, \sigma^2 I_n), 
\end{cases} \quad (2.40)
\]

其中 \(\theta\) 是异常值，\(\sigma^2 > 0\) 是方差。在本章中，零假设 \(\mathcal{H}_0\) 表示无故障情况，备择假设 \(\mathcal{H}_1\) 表示存在潜在故障的情况。一般来说，为了在两个假设之间做出决定，GLR 方法将决策统计量 \(\mathcal{L}(Y)\) 与控制限 \(h(\alpha)\) 进行比较：

\[
\delta(Y) = \begin{cases} 
\mathcal{H}_0 \text{ if } \mathcal{L}(Y) = 2 \log \frac{\sup_{\theta \in \mathbb{R}^n} f_\theta(Y)}{f_{\theta=0}(Y)} < h(\alpha), \\ 
\mathcal{H}_1 \text{ else.} 
\end{cases} \quad (2.41)
\]

GLR 图表统计量 \(\mathcal{L}(Y)\) 定义为

\[
\mathcal{L}(Y) = 2 \log \sup_\theta \left\{ \exp \left\{ - \frac{\|Y - \theta\|_2^2}{2\sigma^2} \right\} / \exp \left\{ - \frac{\|Y\|_2^2}{2\sigma^2} \right\} \right\}, \quad (2.42)
\]

其中 \(\| \cdot \|_2\) 是欧几里得范数，\(f_\theta(Y) = \frac{1}{(2\pi)^{\frac{n}{2}} \sigma^n} \exp \left\{ - \frac{1}{2\sigma^2} \|Y - \theta\|_2^2 \right\}\) 是 \(Y\) 的概率密度函数（pdf）。那么，(2.42) 可表示为

\[
\mathcal{L}(Y) = \frac{1}{\sigma^2} \left\{ \min_\theta \|Y - \theta\|_2^2 + \|Y\|_2^2 \right\} = \frac{1}{\sigma^2} \left\{ \|Y - \widehat{\theta}\|_2^2 + \|Y\|_2^2 \right\}. \quad (2.43)
\]

在估计 \(\theta\) 为 \(\widehat{\theta} = \arg \min_\theta \|Y - \theta\|_2^2 = Y\) 之后，\(\mathcal{L}(Y)\) 可表示为

\[
\mathcal{L}(Y) = \frac{1}{\sigma^2} \|Y\|_2^2. \quad (2.44)
\]

控制限 \(h(\alpha)\) 定义为实现事先选定的期望误报概率：

\[
\mathbb{P}_0 (\mathcal{L}(Y) \ge h(\alpha)) = \int_h^\infty f_0(y) dy = 1 - F_{\chi_1^2}(h) = \alpha. \quad (2.45)
\]

GLR 方法的效能函数确定为

\[
\beta_{8^*}(c^2) = \mathbb{P}_\theta (\delta^*(Y) = \mathcal{H}_1) = 1 - F_{1, \gamma(\theta)}(h). \quad (2.46)
\]

其中 \(F_{1, \gamma}(Y)\) 是具有一个自由度的非中心 \(\chi^2(1, \gamma)\) 分布，非中心性参数 \(\gamma (\theta) = \frac{1}{\sigma^2} \| P_H^\perp \theta \|_2^2\)。

总之，当决策统计量 \(\mathcal{L}(Y)\) 超过控制限 \(h(\alpha)\) 时，GLR 方法会标记故障。否则，受监控过程运行正常。

为结束本节，请注意，前述单变量监控方案是基于两个基本假设设计的：过程数据不相关且服从正态分布。然而，环境和现代工业过程的测量通常具有自相关性和/或非正态分布。缺乏对这两个主要假设的验证会降低这些传统方案的监控性能。为了监控具有串行相关测量的过程，文献中已设计了多种监控方案 [72–77]。可以区分两种主要监控方法来考虑数据中的相关性 [76,58]。第一种方法（称为基于残差的方案）的本质是使用数学模型来描述数据中的自相关性。然后，可以将传统监控方案应用于从模型中获得的不相关残差。然而，这些方法的效率对模型的预测质量非常敏感，而模型并不总是容易构建 [78,76]。监控自相关数据的第二种方法的本质是将监控方案应用于原始数据，并适当调整其决策阈值以考虑相关测量的影响 [76,58]。许多作者已研究正态性假设被违反对过程监控方案的影响 [56,79, 80]。在 [79] 中，已使用包括均匀分布、右三角分布、伽马分布和双峰分布在内的各种已知分布，研究了正态性假设被违反对 Shewhart 方案的影响。另外，在 [81] 中，已研究了偏态分布对 Shewhart 图的影响。当底层分布的形式已知时，已有多项工作为非高斯分布设计了过程监控图。[82, 83] 的作者开发了用于多维泊松分布数据的 EWMA 监控方案。另外，已设计单变量监控图来监控非正态卡方分布过程 [84]。然而，在实际数据中，底层分布的形式通常未知，此时我们的选择可能是使用正态理论结果 [56]。在这种情况下，忽略过程数据中的非正态性会影响设计监控方案的统计性能。

## 2.4.2 基于分布的过程监控方案

最常用的监控技术检测过程均值或方差的变化。然而，在许多实际应用中，变化经常影响被检测过程的分布，而其均值或方差保持不变。本节介绍了 Kullback–Leibler 距离和 Hellinger 距离，它们通常用于量化两个分布之间的偏差。本节的结果对于设计基于 LVR 的方法以监控整个过程分布并拓展实际应用至关重要。

### 2.4.2.1 基于 Kullback–Leibler 的监控方案

Kullback–Leibler 散度的本质是计算两个概率分布之间的不相似性。KLD 起源于信息理论领域，已应用于多个学科，如分类、语音和图像识别 [85,86]、运输 [87]、电信 [88]、工业 [89,90] 和医学 [91]。据文献报道，KLD 在解决异常检测和变化点检测问题中起着核心作用 [89,92,93]。本节介绍了 KL 散度的基本思想以及如何将其用作异常检测器。

**定义 2.1.** 两个概率密度函数（PDF）\(p_1(x)\) 和 \(p_2(x)\) 之间的 Kullback–Leibler 信息定义为

\[
I(p_1 : p_2) = \int_{\mathbb{R}^d} p_1(x) \log \left[ \frac{p_1(x)}{p_2(x)} \right] dx, \quad (2.47)
\]

\(p_2(x)\) 相对于 \(p_1(x)\) 的 Kullback–Leibler 信息由以下公式给出：

\[
I(p_2 : p_1) = \int_{\mathbb{R}^d} p_2(x) \log \left[ \frac{p_2(x)}{p_1(x)} \right] dx. \quad (2.48)
\]

KLI 是一种非对称度量（即，\(I(p_1 : p_2) \neq I(p_2 : p_1)\)）且非负（即，\(I(p_1 : p_2) \ge 0\) 和 \(I(p_2 : p_1) \ge 0\)）。此外，等式 \(I(p_1 : p_2) = 0\) 仅在两个分布严格相等时才成立。KLD 距离代表 KLI 的对称形式 [89]，并表示为

\[
KLD(p_1; p_2) = I(p_1 : p_2) + I(p_2 : p_1). \quad (2.49)
\]

对于两个高斯分布，\(p_1 \sim \mathcal{N}(\mu_0, \sigma_0)\) 和 \(p_2 \sim \mathcal{N}(\mu_1, \sigma_1)\)，分别由其均值 \(\mu_0, \mu_1\) 和方差 \(\sigma_0^2, \sigma_1^2\) 表征，KLD 距离具有以下解析表达式 [94]:

\[
KLD(p_1; p_2) = \frac{1}{\sigma_0\sqrt{2\pi}} \int \exp \left( \frac{(x - \mu_0)^2}{2\sigma_0^2} \right) \cdot \left[ \log \frac{\sigma_1}{\sigma_0} - \frac{(x - \mu_0)^2}{2\sigma_0^2} + \frac{(x - \mu_1)^2}{2\sigma_1^2} \right] dx = \frac{(\mu_1 - \mu_0)^2}{2\sigma_1^2} + \frac{1}{2} \left( \log \frac{\sigma_1^2}{\sigma_0^2} + \frac{\sigma_0^2}{\sigma_1^2} - 1 \right). \quad (2.50)
\]

当异常仅发生在均值中时（即，\(\sigma_0^2 = \sigma_1^2\)），Eq. (2.50) 可表示为

\[
KLD(p_1; p_2) = \frac{(\mu_1 - \mu_0)^2}{2\sigma_1^2}. \quad (2.51)
\]

从 (2.50) 可以看出，对于任何 \(\sigma_0 \neq \sigma_1\)，第二项均严格为正。我们得出结论，在同时影响受监控高斯变量的均值和方差的故障情况下，KLD 的值大于仅均值发生变化时的值。因此，很明显，使用 KLD 同时检测过程测量值的均值和方差中的异常，比检测仅发生在过程均值中的异常更容易。

如果使用 KLD 来表征分布 \(p_1(x)\) 和 \(p_2(x)\) 的接近程度，当两个分布相似时，其值将接近零；否则，它会显著偏离零。因此，KLD 可用于异常检测。用于在零假设 \(\mathcal{H}_0\) 和备择假设 \(\mathcal{H}_1\) 之间进行选择的基于 KLD 的检验如下：

\[
\delta(Y) = \begin{cases} \mathcal{H}_0 \text{ if } KLD(p_1; p_2) < H_D, \\ \mathcal{H}_1 \text{ else.} \end{cases} \quad (2.52)
\]

从决策统计量 KLD 的分布来看，KLD 机制的阈值可以非参数地计算为通过核密度估计（KDE）得到的 KLD 统计量近似分布的 \((1 - \alpha)\) 分位数。非参数阈值使用无异常数据计算。当 KLD 统计量超过决策阈值时，我们声明存在异常。

### 2.4.2.2 基于 Hellinger 的监控方案

此处考虑的检验统计量基于 Hellinger 距离（HD）度量。它由 Ernst Hellinger 提出，可用于测量两个不同概率向量之间的相似性 [95–97]。与 KLD 类似，HD 距离在数理统计的多个问题中也起着核心作用 [98,96, 97]。HD 度量已被广泛应用于包括模式识别 [99]、图像处理 [100]、分类 [101] 和异常检测 [102,97,103] 在内的众多学科。此外，HD 度量还应用于包括网络安全 [103] 和保险欺诈检测 [104] 在内的不同应用。

**定义 2.2** (海灵厄距离). *两个 PDF \(p_1(x)\) 和 \(p_2(x)\) 之间的 HD 值为*

\[
HD^2(p_1, p_2) = \frac{1}{2} \sum (\sqrt{p_1(x)} - \sqrt{p_2(x)})^2. \quad (2.53)
\]

可以看出，HD 是平方根向量之间差值的欧几里得范数：

\[
HD^2(p_1, p_2) = \frac{1}{\sqrt{2}} \| \sqrt{p_1} - \sqrt{p_2} \|_2. \quad (2.54)
\]


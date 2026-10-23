

![](img/e7937519e1e39a29aca97c7de303ca30_502_0.png)

图 13.1：描述线性因子模型家族的有向图模型，其中我们假设观测数据向量 $\boldsymbol{x}$ 由独立潜在因子 $\boldsymbol{h}$ 的线性组合加上一些噪声得到。不同的模型，如概率 PCA、因子分析或 ICA，对噪声的形式以及先验 $p(\boldsymbol{h})$ 的形式做出了不同的选择。

从中采样。接下来，我们在给定因子的条件下采样实值可观测变量

$\boldsymbol{x}=\boldsymbol{W}\boldsymbol{h}+\boldsymbol{b}+$ noise, (13.2)

其中噪声通常是高斯且对角的（各维度独立）。如图 13.1 所示。

## 13.1 概率 PCA 与因子分析

概率 PCA（主成分分析）、因子分析和其他线性因子模型是上述方程（13.1 和 13.2）的特例，它们仅在噪声分布的选择以及在观测 $\boldsymbol{x}$ 之前模型对潜在变量 $\boldsymbol{h}$ 的先验选择上有所不同。

在因子分析中（Bartholomew, 1987; Basilevsky, 1994），潜在变量的先验只是单位方差高斯分布

$\boldsymbol{h}\sim\mathcal{N}(\boldsymbol{h}; \boldsymbol{0}, \boldsymbol{I})$, (13.3)

而观测变量 $x_i$ 在给定 $\boldsymbol{h}$ 时被假定为条件独立的。具体来说，噪声被假定来自对角协方差的高斯分布，其协方差矩阵为 $\boldsymbol{\psi}=\operatorname{diag}\left(\boldsymbol{\sigma}^{2}\right)$，其中 $\boldsymbol{\sigma}^{2}=\left[\sigma_{1}^{2}, \sigma_{2}^{2}, \ldots, \sigma_{n}^{2}\right]^{\top}$ 是每个变量方差的向量。

因此，潜在变量的作用是捕捉不同观测变量 $x_i$ 之间的依赖关系。实际上，可以很容易地证明 $\boldsymbol{x}$ 只是一个多元正态随机变量，其分布为

$\boldsymbol{x}\sim\mathcal{N}(\boldsymbol{x}; \boldsymbol{b}, \boldsymbol{W}\boldsymbol{W}^{\top}+\boldsymbol{\psi})$. (13.4)

为了将 PCA 置于概率框架中，我们可以对因子分析模型稍作修改，使条件方差 $\sigma_i^2$ 彼此相等。在这种情况下，$\boldsymbol{x}$ 的协方差就是 $\boldsymbol{W}\boldsymbol{W}^\top + \sigma^2\boldsymbol{I}$，其中 $\sigma^2$ 现在是一个标量。由此得到条件分布

$$\mathbf{x} \sim \mathcal{N}(\boldsymbol{x}; \boldsymbol{b}, \boldsymbol{W}\boldsymbol{W}^\top + \sigma^2\boldsymbol{I}), \tag{13.5}$$

或等价地

$$\mathbf{x} = \boldsymbol{W}\mathbf{h} + \boldsymbol{b} + \sigma\mathbf{z}, \tag{13.6}$$

其中 $\mathbf{z} \sim \mathcal{N}(\mathbf{z}; \mathbf{0}, \boldsymbol{I})$ 是高斯噪声。然后，如 Tipping 和 Bishop（1999）所示，我们可以使用迭代 EM 算法来估计参数 $\boldsymbol{W}$ 和 $\sigma^2$。

这种**概率** PCA 模型利用了一个观察结果：数据中的大部分变化可以被潜在变量 $\boldsymbol{h}$ 捕获，仅留下一些小的残差**重建误差** $\sigma^2$。如 Tipping 和 Bishop（1999）所示，当 $\sigma \to 0$ 时，概率 PCA 就变成了 PCA。在这种情况下，给定 $\boldsymbol{x}$ 时 $\boldsymbol{h}$ 的条件期望值变成了 $\boldsymbol{x} - \boldsymbol{b}$ 在由 $\boldsymbol{W}$ 的 $d$ 列所张成空间上的正交投影，正如 PCA 中那样。

当 $\sigma \to 0$ 时，由概率 PCA 定义的密度模型在由 $\boldsymbol{W}$ 的列张成的这 $d$ 个维度附近变得非常尖锐。如果数据实际上并不聚集在超平面附近，这可能会使模型给数据分配非常低的似然。

## 13.2 独立成分分析（ICA）

独立成分分析（ICA）是最古老的表示学习算法之一（Herault 和 Ans, 1984; Jutten 和 Herault, 1991; Comon, 1994; Hyvärinen, 1999; Hyvärinen 等, 2001a; Hinton 等, 2001; Teh 等, 2003）。它是一种对线性因子进行建模的方法，旨在将观测信号分离为许多底层信号，这些底层信号按比例缩放并相加形成观测数据。这些信号被期望是完全独立的，而不仅仅是彼此去相关。$^1$

$^1$关于不相关变量与独立变量之间差异的讨论，请参见第 3.8 节。

许多不同的具体方法都被称为 ICA。与我们这里描述的其他生成模型最相似的一种变体（Pham 等, 1992）训练了一个完全参数化的生成模型。底层因子上的先验分布 $p(\boldsymbol{h})$ 必须由用户提前固定。然后模型确定性地生成 $\boldsymbol{x} = \boldsymbol{W}\boldsymbol{h}$。我们可以使用方程 3.47 进行变量的非线性变换来确定 $p(\boldsymbol{x})$。然后像往常一样，使用最大似然进行模型学习。

这种方法的动机是，通过选择独立的 $p(\boldsymbol{h})$，我们可以恢复尽可能接近独立的底层因子。这通常不是用来捕获高层抽象因果因子，而是用来恢复混合在一起的底层信号。在这个设定中，每个训练样本对应一个时间瞬间，每个 $x_{i}$ 是一个传感器对混合信号的观测，每个 $h_{i}$ 是其中一个原始信号的一个估计。例如，我们可能有 $n$ 个人同时说话。如果我们在不同位置放置 $n$ 个不同的麦克风，ICA 能够检测每个麦克风所听到的每个说话者之间音量的变化，并将信号分离，使得每个 $h_{i}$ 只包含一个人清晰说话的声音。这在神经科学中常用于脑电图技术，即一种记录源自大脑电信号的技术。放置在受试者头上的多个电极传感器用于测量来自身体的许多电信号。实验者通常只对来自大脑的信号感兴趣，但来自受试者心脏和眼睛的信号足够强，足以干扰在受试者头皮上进行的测量。信号混合在一起到达电极，因此需要用 ICA 将心脏的电特征与源自大脑的信号分离开来，并将不同脑区的信号彼此分离。

如前所述，ICA 有许多可能的变体。有些在生成 $\boldsymbol{x}$ 时添加一些噪声，而不是使用确定性解码器。大多数不使用最大似然准则，而是旨在使 $\boldsymbol{h} = \boldsymbol{W}^{-1} \boldsymbol{x}$ 的元素彼此独立。有许多准则可以实现这一目标。方程 3.47 需要对 $\boldsymbol{W}$ 求行列式，这可能是一项代价高昂且数值上不稳定的操作。ICA 的一些变体通过约束 $\boldsymbol{W}$ 为正交矩阵来避免这个有问题的操作。

所有 ICA 变体都要求 $p(\boldsymbol{h})$ 是非高斯的。这是因为如果 $p(\boldsymbol{h})$ 是一个具有高斯分量的独立先验，那么 $\boldsymbol{W}$ 是不可识别的。对于许多 $\boldsymbol{W}$ 值，我们可以得到相同的 $p(\boldsymbol{x})$ 分布。这与其他线性因子模型（如概率 PCA 和因子分析）非常不同，后者通常要求 $p(\boldsymbol{h})$ 是高斯的，以便使模型上的许多运算具有闭式解。在最大似然方法中，用户显式指定分布，一个典型的选择是使用 $p(h_{i}) = \frac{d}{dh_{i}} \sigma(h_{i})$。这些非高斯分布的典型选择在 0 附近具有比高斯分布更大的峰，因此我们也可以将大多数 ICA 实现视为学习稀疏特征。

许多 ICA 变体并不是在我们所使用的意义上的生成模型


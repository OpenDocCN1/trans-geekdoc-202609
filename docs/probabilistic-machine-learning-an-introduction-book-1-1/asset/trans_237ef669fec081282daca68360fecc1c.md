
![](img/ea9d4e848ba303d6c19c90b8606f3bf6_449_0.png)

图 13.19：(a) 残差块的示意图。(b) 说明添加残差连接在训练非常深的模型时为何有帮助的示意图。改编自 [Gér19] 的图 14.16。

如 Fig. 13.19b 所示，向更早的层传播。为了理解这一点，注意输出层的激活可以用任意先前层 l 表示

$$\mathbf{z}_L = \mathbf{z}_l + \sum_{i=l}^{L-1} \mathcal{F}_i(\mathbf{z}_i; \boldsymbol{\theta}_i).$$ (13.87)

因此我们可以按如下方式计算损失关于第 l 层参数的梯度：

$$\frac{\partial \mathcal{L}}{\partial \boldsymbol{\theta}_l} = \frac{\partial \mathbf{z}_l}{\partial \boldsymbol{\theta}_l} \frac{\partial \mathcal{L}}{\partial \mathbf{z}_l}$$ (13.88)

$$= \frac{\partial \mathbf{z}_l}{\partial \boldsymbol{\theta}_l} \frac{\partial \mathcal{L}}{\partial \mathbf{z}_L} \frac{\partial \mathbf{z}_L}{\partial \mathbf{z}_l}$$ (13.89)

$$= \frac{\partial \mathbf{z}_l}{\partial \boldsymbol{\theta}_l} \frac{\partial \mathcal{L}}{\partial \mathbf{z}_L} \left(1 + \sum_{i=l}^{L-1} \frac{\partial f(\mathbf{z}_i; \boldsymbol{\theta}_i)}{\partial \mathbf{z}_l} \right)$$ (13.90)

$$= \frac{\partial \mathbf{z}_l}{\partial \boldsymbol{\theta}_l} \frac{\partial \mathcal{L}}{\partial \mathbf{z}_L} + \text{other terms}$$ (13.91)

因此我们可以看到，第 l 层的梯度直接依赖于第 L 层的梯度，且这种依赖与网络的深度无关。

## 13.4.5 批归一化

另一种流行的 DNN 架构修改是在小批量样本上平均时，使层内激活的分布具有零均值和单位方差。这称为批归一化 Batch Normalization, BN [IS15]。

更精确地说，我们用 $\tilde{\mathbf{z}}_n$ 替换某层中示例 $n$ 的激活向量 $z_n$（有时是预激活向量 $a_n$），计算如下：

$\tilde{\mathbf{z}}_n = \boldsymbol{\gamma} \odot \hat{\mathbf{z}}_n + \boldsymbol{\beta}$ (13.92)

$\hat{\mathbf{z}}_n = \frac{\mathbf{z}_n - \boldsymbol{\mu}_B}{\sqrt{\sigma_B^2 + \epsilon}}$ (13.93)

$\boldsymbol{\mu}_B = \frac{1}{|\mathcal{B}|} \sum_{\mathbf{z} \in \mathcal{B}} \mathbf{z}$ (13.94)

$\boldsymbol{\sigma}_B^2 = \frac{1}{|\mathcal{B}|} \sum_{\mathbf{z} \in \mathcal{B}} (\mathbf{z} - \boldsymbol{\mu}_B)^2$ (13.95)

其中 $\mathcal{B}$ 是包含示例 $n$ 的小批量，$\boldsymbol{\mu}_B$ 是该批量的激活均值$^3$，$\boldsymbol{\sigma}_B^2$ 是相应的方差，$\hat{\mathbf{z}}_n$ 是标准化后的激活向量，$\tilde{\mathbf{z}}_n$ 是平移和缩放后的版本（BN 层的输出），$\boldsymbol{\beta}$ 和 $\boldsymbol{\gamma}$ 是该层的可学习参数，$\epsilon > 0$ 是一个很小的常数。由于该变换是可微的，我们可以轻松地将梯度传回层的输入以及 BN 参数 $\boldsymbol{\beta}$ 和 $\boldsymbol{\gamma}$。

当应用于输入层时，批归一化等价于我们在 Sec. 10.2.8 中讨论的通常标准化过程。注意输入层的均值和方差可以一次性计算，因为数据是静态的。然而，随着参数的自适应，内部层的经验均值和方差会不断变化。（这有时被称为“内部协变量偏移”。）这就是为什么我们需要在每个小批量上重新计算 $\boldsymbol{\mu}$ 和 $\sigma^2$。

批归一化的好处（在训练速度和稳定性方面）可以非常显著，尤其对于深层 CNN。确切的原因仍不清楚，但 BN 似乎使优化 landscape 显著平滑 [San+18]。它还降低了对学习率的敏感性 [ALL18]。除计算优势外，它还有统计优势。特别是，BN 起到正则化的作用；事实上可以证明它等价于一种近似贝叶斯推断的形式 [TAS18; Luo+19]。

然而，对小批量的依赖导致了若干问题。首先，在使用小批量训练时，它可能导致参数估计不稳定，尽管一种更新的方法，即批重归一化 batch renormalization [Iof17]，在一定程度上解决了这个问题。其次，批归一化层在测试时需要修改，因为推理时我们可能只有批量大小为 1。标准做法如下：在训练后，计算层 $l$ 在整个训练集上的 $\boldsymbol{\mu}_l$ 和 $\boldsymbol{\sigma}_l^2$，然后“冻结”这些参数，并将它们添加到该层的其他参数列表中，即 $\boldsymbol{\beta}_l$ 和 $\boldsymbol{\gamma}_l$。在测试时，我们随后使用这些冻结的训练值作为 $\boldsymbol{\mu}_l$ 和 $\boldsymbol{\sigma}_l^2$，而不是从测试批量计算统计量。（因此在使用带有 BN 的模型时，需要指定是用于推理还是训练。）

为了提高速度，我们可以将冻结的批归一化层与前一层合并。特别地，假设前一层计算 $\mathbf{XW} + \mathbf{b}$；与 BN 结合得到 $\boldsymbol{\gamma} \odot (\mathbf{XW} + \mathbf{b} - \boldsymbol{\mu})/\boldsymbol{\sigma} + \boldsymbol{\beta}$。如果我们定义 $\mathbf{W}' = \boldsymbol{\gamma} \odot \mathbf{W} / \boldsymbol{\sigma}$ 和 $\mathbf{b}' = \boldsymbol{\gamma} \odot (\mathbf{b} - \boldsymbol{\mu})/\boldsymbol{\sigma} + \boldsymbol{\beta}$，那么我们可以将组合层写为 $\mathbf{XW}' + \mathbf{b}'$。这称为融合批归一化 fused batchnorm。类似的技巧也可以在训练期间加速 BN [Jun+19]。

3. 当应用于卷积层时，我们在空间位置和示例上平均，但不在通道上平均（因此 $\boldsymbol{\mu}$ 的长度为通道数）。当应用于全连接层时，我们仅在示例上平均（因此 $\boldsymbol{\mu}$ 的长度为层的宽度）。

## 13.4.6 参数初始化

由于 DNN 训练的目标函数是非凸的，DNN 参数的初始化方式会对我们最终得到何种解以及函数训练的难易程度（即信息在模型中前向和后向流动的好坏）产生很大影响。在本节剩余部分，我们介绍一些用于初始化参数的常见启发式方法。

### 13.4.6.1 启发式方法

在 [GB10] 中，他们表明从标准正态分布采样参数可能导致输出的方差远大于输入的方差，从而导致梯度爆炸。为了解决这个问题，他们提出从均值为 0、方差为 $\sigma^2 = 1/\text{fan\_avg}$ 的高斯分布采样参数，其中 $\text{fan\_avg} = (\text{fan\_in} + \text{fan\_out})/2$，其中 $\text{fan\_in}$ 是单元的 **fan-in**（传入连接数），$\text{fan\_out}$ 是单元的 **fan-out**（传出连接数）。这种方法被称为 **Xavier 初始化** 或 **Glorot 初始化**，以 [GB10] 的第一作者命名。如果我们使用 $\sigma^2 = 1/\text{fan\_in}$，我们得到一种称为 **LeCun 初始化** 的方法，以在 1990 年代提出它的 Yann LeCun 命名。当 $\text{fan\_in} = \text{fan\_out}$ 时，这等价于 Glorot 初始化。如果我们使用 $\sigma^2 = 2/\text{fan\_in}$，该方法称为 **He 初始化**，以在 [He+15] 中提出它的 Ximing He 命名。最佳初始化方法的选择取决于使用的激活函数。对于线性、tanh、logistic 和 softmax，推荐使用 Glorot。对于 ReLU 及其变体，推荐使用 He。对于 SELU，推荐使用 LeCun。更多启发式方法请参见 [Gér19]。

我们也可以采用数据驱动的参数初始化方法。例如，[MM16] 提出了一种简单但有效的方案，称为 **层序单位方差** layer-sequential unit-variance, LSUV 初始化，其工作方式如下。首先，我们使用 [SMG14] 中提出的方法，用正交矩阵初始化每个（全连接或卷积）层的权重。（这可以通过从 $\mathbf{w} \sim \mathcal{N}(0, I)$ 采样，将 $\mathbf{w}$ 重塑为矩阵 $\mathbf{W}$，然后使用 QR 或 SVD 分解计算正交基来实现。）然后，对于每个层 $l$，我们计算小批量上激活的方差 $v_l$；然后我们重缩放 $\mathbf{W}_l := \mathbf{W}_l / \sqrt{v_l}$。该方案可视为正交初始化与仅在第一个小批量上执行的批归一化的结合。实验表明这种归一化已足够，且该方法比完整的批归一化更快。

另一种称为 **fixup** 的方法在 [ZDM19] 中提出。它可用于在没有批归一化的情况下训练非常深的 ResNet。

### 13.4.6.2 函数空间视角

考虑一个具有 $L$ 个隐藏层和线性输出的 MLP：

$f(x; \boldsymbol{\theta}) = \mathbf{W}_L(\cdots \varphi(\mathbf{W}_2 \varphi(\mathbf{W}_1 x + \mathbf{b}_1) + \mathbf{b}_2)) + \mathbf{b}_L$ (13.96)

我们将使用以下参数的因子化高斯先验：

$\mathbf{W}_l \sim \mathcal{N}(0, \alpha_l^2 I)$, $\mathbf{b}_l \sim \mathcal{N}(0, \beta_l^2 I)$ (13.97)

我们可以将该分布重参数化为

$\mathbf{W}_l = \alpha_l \eta_l$, $\eta_l \sim \mathcal{N}(0, I)$, $\mathbf{b}_l = \beta_l \epsilon_l$, $\epsilon_l \sim \mathcal{N}(0, I)$ (13.98)

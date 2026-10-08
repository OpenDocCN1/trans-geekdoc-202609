

86 种 RBM 和自动编码器的变体

到 $d$ 维向量 $R_{v_t} = \mathbf{v}_t$，对于 $t \in \{1 \dots k\}$；其次，将连接后的向量 $(R_{w_1}', R_{w_2}', \dots, R_{w_k}')$ 与矩阵 $B$ 相乘。这里 $W = B \text{Diag}(R)$，其中 $\text{Diag}(R)$ 是对角线上填充 $R$ 的块对角矩阵。该模型产生了具有更好对数似然的 $n$-gram [129, 130]，在与先进的 $n$-gram 模型进行预测平均时，泛化性能得到了进一步提升 [129]。

## 7.6 泛化 RBM 与对比散度

让我们尝试泛化 RBM 的定义，以便包含一大类参数化，对于这些参数化，我们上面讨论过的本质相同的思想和学习算法（如对比散度）可以很直接地应用。我们以以下方式泛化 RBM：广义 RBM 是一种基于能量的概率模型，具有输入向量 $\mathbf{x}$ 和隐藏向量 $\mathbf{h}$，其能量函数使得 $P(\mathbf{h}|\mathbf{x})$ 和 $P(\mathbf{x}|\mathbf{h})$ 都可因子分解。该定义可以通过能量函数的参数化来形式化，这也由 [73] 提过；

**命题 7.1.** 与形式如方程 (5.5) 的模型相关的能量函数，满足 $P(\mathbf{h}|\mathbf{x}) = \prod_i P(h_i|\mathbf{x})$ 和 $P(\mathbf{x}|\mathbf{h})$，必须具有如下形式

$$\text{Energy}(\mathbf{h},\mathbf{x}) = \sum_i \phi_i(h_i) + \sum_j \xi_j(x_j) + \sum_{i,j} h_{ij}(\mathbf{h}_i, \mathbf{x}_j). \quad (7.7)$$

这是 Hammersley-Clifford 定理 [63, 73] 的直接应用，该定理还表明上述是获得互补先验的充分必要条件。互补先验允许通过适当选择 $\mathbf{h}$ 使得后验分布 $P(\mathbf{h}|\mathbf{x})$ 因子分解。

在隐藏值和输入值为二值的情况下，这种表述并没有带来任何额外的表示能力。事实上，$\eta_{ij}(\mathbf{h}_i, \mathbf{x}_j)$ 根据 $(\mathbf{h}_i, \mathbf{x}_j)$ 的 $2 \times 2$ 配置最多可以取四个不同的值，始终可以重写为 $(\mathbf{h}_i, \mathbf{x}_j)$ 的二次多项式：$a + b\mathbf{x}_j + c\mathbf{h}_i + d\mathbf{h}_i\mathbf{x}_j$。

然而，$b$ 和 $c$ 可以合并到偏移项中，而 $a$ 可以合并为一个全局加性常数，这并不重要（因为会被配函数抵消）。

另一方面，当 $\mathbf{x}$ 或 $\mathbf{h}$ 是实向量时，可以想象对 $(\mathbf{h}_i, \mathbf{x}_j)$ 交互进行更高容量的建模，可能是非参数的，例如逐渐向 $\eta_{i,j}$ 添加项以更好地建模交互。此外，从条件密度 $P(\mathbf{x}_j|\mathbf{h})$ 或 $P(\mathbf{h}_i|\mathbf{x})$ 采样是足够易处理的函数，仅仅因为这些是一维密度，通过高效采样和数值积分可以容易地计算在嵌套子区间或箱（bins）上密度的累积和。

这种分析也凸显了 RBM 的基本局限性，即其参数化仅考虑了变量之间的两两交互。正因为 $\mathbf{h}$ 是隐藏的，并且因为我们可以选择隐藏单元的数量，我们仍然对 $\mathbf{x}$ 中可能的边缘分布具有完全的表达能力（事实上，我们可以表示任何离散分布 [102]）。第 7.4 节中讨论的 RBM 其他变体允许三三交互。

在这种广义 RBM 公式述中，对比散度更新是什么样的？为了简化符号，请注意方程 (7.7) 中的 $\phi_{i,j}$ 和 $\xi_{i,j}$ 可以包含在 $\eta_{i,j}$ 中，因此我们在下文中忽略它们。定理 5.1 可以应用于：

$$\text{FreeEnergy}(\mathbf{x}) = - \log \sum_{i,j} \exp \left(-\sum \eta_{i,j}(\mathbf{h}_i,\mathbf{x}_j)\right) \cdot$$

样本 $\mathbf{x}$ 的自由能量的梯度为：

$$\frac{\partial \text{FreeEnergy}(\mathbf{x})}{\partial \theta} = \sum_{h} \frac{\exp \left(-\sum_{i,j} \eta_{i,j}(\mathbf{h}_i,\mathbf{x}_j)\right)}{\partial \theta} - \sum_{h} \sum_{i,j} \exp \left(-\sum_{i,j} \eta_{i,j}(\mathbf{h}_i,\mathbf{x}_j)\right) \frac{\partial \eta_{i,j}(\mathbf{h}_i,\mathbf{x}_j)}{\partial \theta} \\= \sum_{h} P(\mathbf{h}|\mathbf{x}) \frac{\partial \eta_{i,j}(\mathbf{h}_i,\mathbf{x}_j)}{\partial \theta} \\= E_{h} \left[ \sum_{i,j} \frac{\partial \eta_{i,j}(\mathbf{h}_i,\mathbf{x}_j)}{\partial \theta} \right]$$

多亏于命题 7.1，Gibbs 链仍然可以很容易地运行。在 Gibbs 链运行 $k$ 步后截断对数似然展开（方程 (28)），并用这些样本近似期望，可以获得训练点 $\mathbf{x}_1$ 的对数似然的近似，它仅取决于 Gibbs 样本 $\mathbf{h}_1$ 和 $\mathbf{x}_{k+1}$：

$$\frac{\partial}{\partial\theta} P(\mathbf{x}_1) \simeq -\frac{\partial\text{FreeEnergy}(\mathbf{x}_1)}{\partial\theta} + \frac{\partial\text{FreeEnergy}(\mathbf{x}_{k+1})}{\partial\theta} \\ \simeq (\sum_{i,j} \frac{\partial\eta_{i,j}(\mathbf{h}_i, \mathbf{x}_j)}{\partial\theta} + \sum_{i,j} \frac{\partial\eta_{i,j}(\mathbf{h}_{k+1}, \mathbf{x}_j)}{\partial\theta}) \propto \Delta\theta,$$

其中 $\Delta\theta$ 是模型参数 $\theta$ 的更新规则，对应于此类广义 RBM 中的 CD-$k$。注意在大多数参数化中，$\theta$ 的特定元素依赖于 $\eta_{i,j}$ 的方式使得不需要显式的求和。例如（对 $\mathbf{h}_{k+1}$ 取期望而非采样），我们恢复了算法 1：

$$\eta_{i,j}(\mathbf{h}_i, \mathbf{x}_j) = -W_{ij}\mathbf{h}_i\mathbf{x}_j$$

其中 $n_h$ 和 $n_x$ 分别是隐藏单元和可见单元的数量。

DBN 联合优化的随机变界

在本节中，我们将讨论 DBN 的原理。DBN 的对数似然可以使用 Jensen 不等式下界，正如我们下面讨论的，这可以证明贪心逐层策略的合理性。首先我们将 $P(x)$ 乘以 $1 = \sum_h$ 并展开项：

$$\text{FreeEnergy}(\mathbf{x}) = - \log \sum_{i,j} \exp \left(-\sum \eta_{i,j}(\mathbf{h}_i,\mathbf{x}_j)\right) \cdot$$


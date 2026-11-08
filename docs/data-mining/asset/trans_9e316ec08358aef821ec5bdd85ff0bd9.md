
# 隐马尔可夫模型

$P\\left( {O,H} \\right) = P\\left( H\_{1} \\right)\\prod\\limits\_{t = 1}^{T}{P\\left( H\_{t + 1}, \\middle| ,H\_{t} \\right)}\\prod\\limits\_{t = 1}^{T}{P\\left( O\_{t}, \\middle| ,H\_{t} \\right)}.$
![Equation](images/F000157si302.png)

每个 `O[t]` 是一个具有 `N` 个可能取值的离散随机变量，每个 `H[t]` 是一个具有 `M` 个可能取值的离散随机变量。[图 14.11C](#Ch015_516-570_B9780443158889000157_b.xhtml#f0060) 说明了隐马尔可夫模型是一种贝叶斯网络，被称为“动态”贝叶斯网络，因为变量会在适当的时间步数上动态复制。它们是一阶马尔可夫模型的明显扩展，通常使用“时齐”模型，其中转移矩阵 `P(H[t + 1] | H[t])` ![Equation](images/F000157si303.png) 在每个时间步都相同。定义 `A` 为转移矩阵，其元素编码 `P(H[t + 1] = j | H[t] = i)` ![Equation](images/F000157si304.png)，并将 `B` 定义为发射矩阵 `B`，其元素 `b[ij]` 对应于 `P(O[t] = j | H[t] = i)` ![Equation](images/F000157si305.png)。对于特殊的 `t = 1`，初始状态概率分布被编码在一个向量 `π` 中，其元素为 `π[i] = P(H[t] = i)` ![Equation](images/F000157si306.png)。完整的参数集合为 `θ = {A, B, π}` ![Equation](images/F000157si307.png)，它包含两个矩阵和一个向量。我们将特定的观测序列写为一组观测 $\\overset{\\sim}{O} = \\{ O\_{1} = o\_{1},\\ldots,O\_{T} = o\_{T}\\}$ ![Equation](images/F000157si308.png)。

## 关键问题

隐马尔可夫模型提出了三个关键问题：

1. 计算 `P(~O; θ)` ![Equation](images/F000157si309.png)，在参数为 `θ` ![Equation](images/F000157si310.png) 的模型下序列的概率。
2. 找到最可能的解释——能解释一个观测的最佳状态序列 `H* = {H[1] = h[1], …, H[T] = h[T]}` ![Equation](images/F000157si311.png)。
3. 给定一组观测序列的数据集，找到模型的最佳参数 `θ` ![Equation](images/F000157si312.png)。


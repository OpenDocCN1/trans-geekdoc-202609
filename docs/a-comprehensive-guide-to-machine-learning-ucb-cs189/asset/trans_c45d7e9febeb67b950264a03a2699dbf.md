

## 1.5. 超参数与验证

![](img/99defe26aebed215976e83d281581f33_14_0.png)

### 交叉验证

划分一个验证集是有效的，但这种方法是有代价的，因为我们无法将验证数据用于训练。由于拥有更多数据通常会提高训练模型的质量，我们可能不希望让这些数据被浪费，特别是当我们的初始数据很少且/或收集更多数据的成本非常高昂时。交叉验证是设置专用验证集的替代方案。

$k$-折交叉验证的工作原理如下：

1.  打乱数据，并将其划分为 $k$ 个等大小（或尽可能相等）的块。
2.  对于 $i = 1, \dots, k$，
    * 在除第 $i$ 块以外的所有数据上训练模型。
    * 使用第 $i$ 块评估模型（即计算验证误差）。

| 1 | 2 | 3 | 4 | 5 | 6 | ... | $k$ |
|---|---|---|---|---|---|---|---|
| 验证 | 训练 | | | | | | |
| 训练 | 验证 | 训练 | | | | | |
| | 训练 | 验证 | 训练 | | | | |
| | | | | | | | | |

3.  对 $k$ 个验证误差平均；这是我们对真实误差的最终估计。

注意，这个过程（打乱和划分除外）对于我们想要测试的每个超参数配置都必须重复。这是 $k$-折交叉验证与使用留验证集相比的主要缺点——所需的计算量大约是 $k$ 倍。对于我们目前看到的较小的线性模型来说，这不是大问题，但当模型训练需要很长时间时（例如在大数据时代或使用神经网络时），成本可能会高到无法接受。

## 核岭回归 (Kernel Ridge Regression)

在岭回归中，我们给定一个向量 $\mathbf{y} \in \mathbb{R}^n$ 和一个矩阵 $\mathbf{X} \in \mathbb{R}^{n \times l}$，其中 $n$ 是训练点数，$l$ 是原始数据点的维度。在大多数情况下，我们不希望在原始特征空间中工作，因此我们对数据点进行特征增强，并将 $\mathbf{X}$ 替换为 $\mathbf{\Phi} \in \mathbb{R}^{n \times d}$，其中 $\phi_i = \phi(\mathbf{x}_i) \in \mathbb{R}^d$。然后我们求解一个涉及 $\mathbf{\Phi}$ 和 $y$ 的定义优化问题，其中参数 $\mathbf{w} \in \mathbb{R}^d$。

如果我们在原始 $l$ 维空间中使用 $p$ 阶多项式特征，出现的问题是有 $d = \binom{l+p}{p}$ 个我们需要优化的项，这个值可能非常大（远大于训练点数 $n$）。与其在 $d$ 个变量上求解优化问题，不如在（可能更小的）$n$ 个变量上求解等效问题，并实现与增强特征数量无关的计算运行时间吗？事实证明，一种被称为“核技巧”（kernel trick）的核概念允许我们实现这一目标。考虑岭回归的解：

$\mathbf{w} = (\mathbf{\Phi}^T\mathbf{\Phi} + \lambda\mathbf{I})^{-1}\mathbf{\Phi}^T\mathbf{y}$

该操作涉及计算 $\mathbf{\Phi}^T\mathbf{\Phi}$，它是一个 $d \times d$ 矩阵，需要 $O(d^2)$ 的时间。矩阵求逆还需要额外的 $O(d^3)$ 时间。我们真正想要的是一个需要 $O(n^3)$ 时间来求逆的 $n \times n$ 矩阵：如果我们翻转 $\mathbf{\Phi}$ 和 $\mathbf{\Phi}$ 的顺序，最终得到一个 $n \times n$ 矩阵 $\mathbf{\Phi}^T\mathbf{\Phi}$。事实上，$\mathbf{\Phi}^T\mathbf{\Phi}$ 有直观的含义：它是所有数据点之间内积的矩阵，衡量了数据点之间的“相似性”并捕捉了它们的表示。现在让我们看看是否能用用矩阵 $\mathbf{\Phi}^T$ 表示岭回归的解。

为了符号简便，让我们回到使用 $\mathbf{X}$ 而不是 $\mathbf{\Phi}$（假设我们只处理原始特征，我们对核回归的分析仍然成立）。重新排列原始回归解的项，我们得到：

$\mathbf{w} = (\mathbf{X}^T\mathbf{X} + \lambda\mathbf{I})^{-1}\mathbf{X}^T\mathbf{y}$
$(\mathbf{X}^T\mathbf{X} + \lambda\mathbf{I})\mathbf{w} = \mathbf{X}^T\mathbf{y}$
$\mathbf{X}^T\mathbf{X} + \lambda\mathbf{w} = \mathbf{X}^T\mathbf{y}$
$\mathbf{w} = \frac{1}{\lambda}(\mathbf{X}^T\mathbf{y} - \mathbf{X}^T\mathbf{X})$

这说明无论 $\mathbf{w}$ 是什么，它都是训练点 $\mathbf{x}_i$ 的某种线性组合（因为任何形式为 $\mathbf{X}^T\mathbf{v}$ 的项都是 $\mathbf{X}^T$ 列的线性组合，而 $\mathbf{X}^T$ 的列就是训练点）。为了找到 $\mathbf{w}$，只需找到 $\mathbf{w}$ 即可（注：此处原文逻辑似乎略有混乱，翻译遵循原文语意）。找到 $\mathbf{w}$ 只需要找到 $\mathbf{w}$。无论 $\mathbf{w}$ 是什么，它都是训练点 $\mathbf{x}_i$ 的某种线性组合（因为任何形式为 $\mathbf{X}^T\mathbf{v}$ 的项都是 $\mathbf{X}^T$ 列的线性组合，而 $\mathbf{X}^T$ 的列就是训练点）。找到 $\mathbf{w}$ 只需要找到 $\mathbf{w}$。无论 $\mathbf{w}$ 是什么，它都是训练点 $\mathbf{x}_i$ 的某种线性组合（因为任何形式为 $\mathbf{X}^T\mathbf{v}$ 的项都是 $\mathbf{X}^T$ 列的线性组合，而 $\mathbf{X}^T$ 的列就是训练点）。找到 $\mathbf{w}$ 只需要找到 $\mathbf{w}$。无论 $\mathbf{w}$ 是什么，它都是训练点 $\mathbf{x}_i$ 的某种线性组合（因为任何形式为 $\mathbf{X}^T\mathbf{v}$ 的项都是 $\mathbf{X}^T$ 列的线性组合，而 $\mathbf{X}^T$ 的列就是训练点）。

## 1.6. 核回归 (KERNEL REGRESSION)

$\mathbf{X}^T\mathbf{y}$
$\mathbf{X}\mathbf{y} + \lambda v$

我们不能孤立 $v$，但我们可以通过以下方式来孤立 $v$：

$\mathbf{X}^T\mathbf{y}$
$\mathbf{X}\mathbf{y} + \lambda v$

$\mathbf{w} = \mathbf{X}^T(\mathbf{X} + \lambda I)^{-1}$
$\mathbf{w} = \mathbf{X}^T(\mathbf{X} + \lambda I)^{-1}$
1.  $\mathbf{w} = \mathbf{X}^T\mathbf{y}$

$\mathbf{w} = \mathbf{X}^T(\mathbf{X} + \lambda I)^{-1}$
1.  $\mathbf{w} = \mathbf{X}^T\mathbf{y}$

事实上，这些表达式是等价的！出现的问题是选择哪一个？我们在引入核之后回答这个问题。

### 线性代数推导 (Linear Algebra Derivation)

我们的推导包含了一些直观的线性代数论据。在此之前，我们需要通过更严谨的线性代数来形式化我们的推导（FTLA）：矩阵 $X$ 映射 $\mathbb{R}^d$ 到 $\mathbb{R}^n$。$\mathcal{N}(X)$ 是 $X$ 的零空间，而 $\mathcal{R}(X)$ 是 $X$ 的列空间。它们满足以下性质：

1.  $\mathcal{N}(X) \perp \mathcal{R}(X^T)$ 且 $\mathcal{R}(X) \perp \mathcal{N}(X^T)$
2.  $\mathcal{R}(X) \oplus \mathcal{N}(X^T) = \mathbb{R}^n$
3.  $\mathbb{R}^d = \mathcal{R}(X^T) \oplus \mathcal{N}(X)$

符号 $\perp$ 表示 $\mathcal{N}(X)$ 于 $\mathcal{R}(X^T)$，这意味着对于任何 $u \in \mathbb{R}^d$，存在唯一的 $u_1 \in \mathcal{N}(X)$ 和 $u_2 \in \mathcal{R}(X^T)$ 使得 $u = u_1 + u_2$。此外，$\mathcal{N}(X)$ 和 $\mathcal{R}(X^T)$ 是正交子空间。

这就是 FTLA 在岭回归中的作用。我们可以将任何 $\mathbf{w} \in \mathbb{R}^d$ 表示为唯一的线性组合 $\mathbf{w} = \mathbf{w}_1 + \mathbf{w}_2$，其中 $\mathbf{w}_1 \in \mathcal{R}(X^T)$ 且 $\mathbf{w}_2 \in \mathcal{N}(X)$。我们可以将其表示为：
$\mathbf{w} = \mathbf{X}^T\mathbf{v} + \mathbf{r}$，其中 $\mathbf{v} \in \mathbb{R}^n$ 且 $\mathbf{r} \in \mathcal{N}(X)$。

现在我们考虑岭回归的方程：
$(\mathbf{X}^T\mathbf{X} + \lambda I)\mathbf{w} = \mathbf{X}^T\mathbf{y}$由于 $\mathbf{r} \in \mathcal{N}(X)$，有 $\mathbf{X}\mathbf{r} = 0$。因此：
$\mathbf{X}\mathbf{w} = \mathbf{X}(\mathbf{X}^T\mathbf{v} + \mathbf{r}) = \mathbf{X}\mathbf{X}^T\mathbf{v}$
$(\mathbf{X}\mathbf{X}^T + \lambda I)\mathbf{v} = \mathbf{X}\mathbf{y}$
$\mathbf{v} = (\mathbf{X}\mathbf{X}^T + \lambda I)^{-1}\mathbf{X}\mathbf{y}$

由此得到：
$\mathbf{w} = \mathbf{X}^T\mathbf{v} + \mathbf{r} = \mathbf{X}^T(\mathbf{X}\mathbf{X}^T + \lambda I)^{-1}\mathbf{X}\mathbf{y} + \mathbf{r}$

这正是岭回归的解。现在，如果我们使用核技巧，就可以在 $n$ 个变量上求解问题，而不是在 $d$ 个变量上求解，从而实现计算时间与增强特征数量无关。考虑岭回归的解：

$\mathbf{w} = (\mathbf{\Phi}^T\mathbf{\Phi} + \lambda\mathbf{I})^{-1}\mathbf{\Phi}^T\mathbf{y}$

该操作涉及计算 $\mathbf{\Phi}^T\mathbf{\Phi}$，它是一个 $d \times d$ 矩阵，需要 $O(d^2)$ 的时间。矩阵求逆还需要额外的 $O(d^3)$ 时间。我们真正想要的是一个需要 $O(n^3)$ 时间来求逆的 $n \times n$ 矩阵：如果我们翻转 $\mathbf{\Phi}$ 和 $\mathbf{\Phi}$ 的顺序，最终得到一个 $n \times n$ 矩阵 $\mathbf{\Phi}^T\mathbf{\Phi}$。事实上，$\mathbf{\Phi}^T\mathbf{\Phi}$ 有直观的含义：它是所有数据点之间内积的矩阵，衡量了数据点之间的“相似性”并捕捉了它们的表示。现在让我们看看是否能用矩阵 $\mathbf{\Phi}^T$ 表示岭回归的解。

为了符号简便，让我们回到使用 $\mathbf{X}$ 而不是 $\mathbf{\Phi}$（假设我们只处理原始特征，我们对核回归的分析仍然成立）。重新排列原始回归解的项，我们得到：

$\mathbf{w} = (\mathbf{X}^T\mathbf{X} + \lambda\mathbf{I})^{-1}\mathbf{X}^T\mathbf{y}$
$(\mathbf{X}^T\mathbf{X} + \lambda\mathbf{I})\mathbf{w} = \mathbf{X}^T\mathbf{y}$
$\mathbf{X}^T\mathbf{X} + \lambda\mathbf{w} = \mathbf{X}^T\mathbf{y}$
$\mathbf{w} = \frac{1}{\lambda}(\mathbf{X}^T\mathbf{y} - \mathbf{X}^T\mathbf{X})$

这说明无论 $\mathbf{w}$ 是什么，它都是训练点 $\mathbf{x}_i$ 的某种线性组合（因为任何形式为 $\mathbf{X}^T\mathbf{v}$ 的项都是 $\mathbf{X}^T$ 列的线性组合，而 $\mathbf{X}^T$ 的列就是训练点）。为了找到 $\mathbf{w}$，只需找到 $\mathbf{w}$ 即可（注：此处原文逻辑似乎略有混乱，翻译遵循原文语意）。




![](img/fa92deee3de0f00ea56e92ca0b92c8e4_95_0.png)

图 8.1 凸松弛方法和凸松弛障碍的图示，来自 (Salman et al., 2019b)，其中他们展示了几乎所有不完整验证算法都可以基于凸松弛框架来制定，并总结了不同不完整验证器之间的关系。

## 发现

```
\max_{x' \in S} a^T x'.
```

例如，当 S 是以 \(x_0\) 为中心、半径为 \(\epsilon\) 的 \(\ell_\infty\) 球时，最坏情况下的输出将是 \(\epsilon \|a\|_1 + a^T x_0\)。

如果我们有一些非线性激活函数（例如 ReLU）怎么办？线性界传播方法的主要思想是为激活函数形成线性上界和下界 \(\bar{\sigma}\) 和 \(\underline{\sigma}\)。考虑一个 ReLU 函数，为了简单起见，我们假设当前的预激活下界和上界 \(z \in [l, u]\)，并旨在用线性函数来界定 ReLU(\(z\)) = max(\(z\), 0)。我们可以考虑图 8.2 中所示的三种情况。如果 \(l \ge 0\)，则我们知道 \(z\) 始终为正，因此 ReLU(\(z\)) = \(z\) 将是线性的。如果 \(u \le 0\)，则我们知道 \(z\) 始终为负，因此 ReLU(\(z\)) = 0 也将是线性的。第三种情况 \(l < 0 < u\) 是最棘手的，其中 ReLU 真正是非线性的，我们需要找到线性上界和下界。我们称这些为“不稳定神经元”。

![](img/fa92deee3de0f00ea56e92ca0b92c8e4_96_0.png)

图 8.2 ReLU 激活的三种情况图示。

对于这些不稳定神经元，我们可以推导出以下线性界：

```
\(\underline{\sigma}^{(l)}(z) := \alpha^{(l)}z, \quad \overline{\sigma}^{(l)}(z) := \frac{\overline{z}^{(l)}}{\overline{z}^{(l)} - \underline{z}^{(l)}}(z - \underline{z}^{(l)}) \quad (8.2)\)
```

其中 \(\alpha^{(l)} \in [0, 1]\)。上界和下界在图 8.3 中所示。我们可以轻松验证，对于任何 \(\alpha^{(l)} \in [0, 1]\)，ReLU 激活的输出值将由这两个函数界定：

```
\(\underline{\sigma}^{(l)}(z) \le \max(z, 0) \le \overline{\sigma}^{(l)}(z) \quad \forall z \in [\underline{z}^{(l)}, \overline{z}^{(l)}]\)
```

有趣的是，下界可能有多种选择。一些常见的选择是：使用上界和下界相同的斜率；为下界使用 0 斜率；使用一些启发式方法来自适应地选择斜率。更近期的研究表明，可以选择下界以优化最终验证性能，这将在本节末尾讨论。

有了 ReLU 函数的线性上界和下界后，我们就可以界定 ReLU 层的输出，其中常数由 (8.2) 中使用的线性函数的斜率确定：

**引理 1** (CROWN 中的 ReLU 松弛)。给定 \(w, v \in \mathbb{R}^d\)，\(\boldsymbol{l} \le v \le \boldsymbol{u}\)（逐元素），我们有

```
\(w^\top ReLU(v) \ge w^\top \mathcal{D}v + b'\)
```

其中 \(\mathcal{D}\) 是一个对角矩阵，仅当 \(\boldsymbol{u}_j > 0 > \boldsymbol{l}_j\) 且 \(w_j \ge 0\) 时才包含自由变量，而其余值和常数 \(b'\) 由 \(\boldsymbol{l}, \boldsymbol{u}, w\) 确定。

有了每个神经元的线性上界和下界后，我们可以逐步线性化整个神经网络，在每一步中，我们为第 \(l\) 层的神经元形成线性上界和下界。这将导致一个高效的

![](img/fa92deee3de0f00ea56e92ca0b92c8e4_97_0.png)

图 8.3 形成不稳定神经元线性上界和下界的图示。

回代过程，以推导 NN 输出相对于 x 的线性下界。

**引理 2** (线性松弛界)。给定一个具有权重 $\mathcal{W}_i$、偏置 $\mathbf{b}^i$ 和输入约束 $\boldsymbol{x} \in S$ 的 $L$ 层 \(\text{ReLU NN} f(\boldsymbol{x}): \mathbb{R}^{d_0} \to \mathbb{R}\)，我们有

$\min_{\boldsymbol{x} \in S} f(\boldsymbol{x}) \ge \min_{\boldsymbol{x} \in S} \boldsymbol{a}_{\text{CROWN}}^\top \boldsymbol{x} + c_{\text{CROWN}}.$

其中 $\boldsymbol{a}_{\text{CROWN}}$ 和 $c_{\text{CROWN}}$ 可以使用 $\mathcal{W}_i$, $\mathbf{b}^i$, $\mathbf{l}_i$, $\mathbf{u}_i$ 在多项式时间内计算。详细过程可在多篇论文中找到，例如 (Weng et al., 2018a; Zhang et al., 2018; Singh et al., 2019b)。

当 $S$ 是一个 $\ell_p$ 范数球时，线性函数上的极小化可以使用 Hölder 不等式轻松求解。CROWN 的主要优势在于其效率：CROWN 可以高效地在机器学习加速器（如 GPU (Xu et al., 2020b) 和 TPU (Zhang et al., 2020a)）上实现，并且它比线性规划（LP）验证器快几个数量级，后者在 GPU 上很难并行化。CROWN 已推广到一般架构，但为了简单起见，我们仅在前馈 ReLU 网络中演示它。此外，Xu et al. (2021) 表明可以使用梯度上升来优化下界 \(\boldsymbol{\alpha}$ 的斜率以进一步收紧界（有时称为 \(\boldsymbol{\alpha}\)-CROWN）。

Fast-Lin (Weng et al., 2018a) 和 Neurify (Wang et al., 2018a) 分配了 \(\boldsymbol{\alpha}^{(l)} = \frac{\underline{z}^{(l)}}{\underline{z}^{(l)} - \overline{z}^{(l)}}$，这比 CROWN 严格松弛，但享有轻微的计算优势。DeepZ (Singh et al., 2018a) 和 DeepPoly (Singh et al., 2019b) 是从使用抽象解释方法的形式验证社区发现的，但也可以包含在这个框架中。

## 最优逐层凸松弛

尽管讨论一直集中在 ReLU 网络的鲁棒性验证上，上述线性界传播

![](img/fa92deee3de0f00ea56e92ca0b92c8e4_98_0.png)

图 8.4 常见非线性的最优凸松弛。对于 tanh，松弛包含两个线性段和 tanh 函数的部分。对于 ReLU 和阶跃函数，最优松弛分别写成 3 和 4 个线性约束。对于 z = max(x, y)，浅橙色（打印版中为浅灰色）阴影指示 x 和 y 的预激活界，最优凸松弛由 max 函数本身下界。更多细节可在 (Salman et al., 2019b) 中找到。

方法可以轻松扩展到具有一般激活函数的任何网络。唯一的要求是给定预激活界时为激活函数形成线性上界和下界。更多细节可在 (Zhang et al., 2018) 中找到。

如果我们超越线性上界和下界，改用一般凸函数，我们可以通过以下在 \([\underline{z}, \bar{z}]$ 内的凸包来设计最优凸松弛 \(\underline{\sigma}$ 和 \(\bar{\sigma}$。例如，最优下界是

```
\(\underline{\sigma}_{\text{opt}}(z) := \sup_{(\alpha, \gamma) \in \mathcal{A}} \alpha^\top z + \gamma, \quad \mathcal{A} = \{(\alpha, \gamma) : \alpha^\top z' + \gamma \le \sigma(z'), \forall z' \in [\underline{z}, \bar{z}]\}.\)
```

这给出了凸松弛框架实现的 *针对一般激活函数* 的最紧界，如图 8.4 所示。使用最优凸松弛，可以得到最紧的结果，但时间复杂度显著增加。例如，对于 ReLU 激活，图 8.4 显示最优凸松弛是一个线性上界和两个线性下界的并集。尽管这仍然可以用简单的形式表示，但从界传播的角度来看，这会导致线性界数量呈指数级增长，必须由线性规划求解器求解。因此，在实践中，线性界传播方法仍然是不完整验证最流行的选择。(Salman et al., 2019b) 也讨论了最优凸松弛与线性界传播之间的差距。对于某些 ReLU 网络，它们为每个 ReLU 激活形成两个线性下界，并通过线性规划求解由此产生的问题。他们证明，在某些实际案例中，最优凸松弛与线性界传播之间的差距可能是合理的，但最优凸松弛与精确验证问题之间仍然存在一些差距，




$$
\underset{D_{t + 1}}{\underset{\text{︸}}{\frac{1}{2}{\| w^{t + 1} - w\|}^{2}}} + \underset{\Delta_{t}}{\underset{\text{︸}}{\eta_{t}[ F(w^{t}) - F(w)]}} \leqslant \underset{D_{t}}{\underset{\text{︸}}{\frac{1}{2}{\| w^{t} - w\|}^{2}}} + \underset{E_{t}}{\underset{\text{︸}}{\frac{\eta_{t}^{2}}{2}{\|\nabla F(w^{t})\|}^{2}}}.
$$

![Image](OEBPS/images/B9780443190377000089/si222.png) (1.15)

该不等式完全符合 [(1.13)](#Chp001_3-28_B9780443190377000089_split_001.xhtml#deq14) 的形式，其中 `ω[t] = 1`![Image](OEBPS/images/B9780443190377000089/si202.png)。为保证收敛，我们需要取 `w = w^⋆`![Image](OEBPS/images/B9780443190377000089/si161_u2.png) 作为 [(1.1)](#Chp001_3-28_B9780443190377000089_split_000.xhtml#deq1) 的一个解，并假设 `∥∇F(w^(t))∥ ≤ M`![Image](OEBPS/images/B9780443190377000089/si223.png)。然后，[(1.15)](#Chp001_3-28_B9780443190377000089_split_001.xhtml#deq16) 蕴含 `Δ[t] ≤ D[t] − D[t + 1] + E[t]`![Image](OEBPS/images/B9780443190377000089/si224.png)。通过数学归纳法，我们得到 $\sum_{t = 0}^{T}\Delta_{t} \leqslant D_{0} - D_{T + 1} + \sum_{t = 0}^{T}E_{t} \leqslant D_{0} + \sum_{t = 0}^{T}E_{t}$![Image](OEBPS/images/B9780443190377000089/si225.png)。因此，我们得到

$$
F(\widehat{w}) - F(w^{\star}) \leqslant \frac{1}{S_{T}}\sum\limits_{t = 0}^{T}\eta_{t}[ F(w^{t}) - F(w^{\star})] \leqslant \frac{1}{2S_{T}}{\| w^{0} - w^{\star}\|}^{2} + \frac{M^{2}}{2S_{T}}\sum\limits_{t = 0}^{T}\eta_{t}^{2},
$$

![Image](OEBPS/images/B9780443190377000089/si226.png)

其中 $S_{T}: = \sum_{t = 0}^{T}\eta_{t}$![Image](OEBPS/images/B9780443190377000089/si227.png) 和 $\widehat{w}: = \frac{1}{S_{T}}\sum_{t = 0}^{T}\eta_{t}w^{t}$![Image](OEBPS/images/B9780443190377000089/si228.png)，正如 [(1.12)](#Chp001_3-28_B9780443190377000089_split_001.xhtml#deq13) 所计算的那样。为获得收敛速率界，我们要求 $\sum_{t = 0}^{\infty}\eta_{t}^{2} < + \infty$![Image](OEBPS/images/B9780443190377000089/si229.png) 且 $S_{T}\rightarrow S_{\infty} = \sum_{t = 0}^{\infty}\eta_{t} = \infty$![Image](OEBPS/images/B9780443190377000089/si230.png)。这些正是保证[次]梯度法收敛的条件，参见例如 [[8]](#Chp001_3-28_B9780443190377000089_split_002.xhtml#br0040)。

### (c) 非凸问题的梯度下降法

如果我们假设 `F` 仅为 `L`-光滑且不一定是凸的，则使用 [(1.10)](#Chp001_3-28_B9780443190377000089_split_001.xhtml#deq11)（令 `w := w^(t)`![Image](OEBPS/images/B9780443190377000089/si231.png) 和 `w' := w^(t + 1) = w^(t) − η[t]∇F(w^(t))`![Image](OEBPS/images/B9780443190377000089/si232.png)），我们有

$$
F(w^{t + 1}) \leqslant F(w^{t}) + \langle\nabla F(w^{t}),w^{t + 1} - w^{t}\rangle + \frac{L}{2}{\| w^{t + 1} - w^{t}\|}^{2} = F(w^{t}) - \eta_{t}\left( 1 - \frac{L\eta_{t}}{2} \right){\|\nabla F(w^{t})\|}^{2}.
$$

![Image](OEBPS/images/B9780443190377000089/si233.png) (1.16)

通过在两边加上 `− F^⋆`![Image](OEBPS/images/B9780443190377000089/si234.png)，其中 `F^⋆ := inf[w]F(w) > − ∞`![Image](OEBPS/images/B9780443190377000089/si235.png)（我们的假设），并重新排列结果，不等式 [(1.16)](#Chp001_3-28_B9780443190377000089_split_001.xhtml#deq18) 导出

$$
\begin{array}{lcl}
{\underset{D_{t + 1}}{\underset{\text{︸}}{F(w^{t + 1}) - F^{\star}}} + \underset{\Delta_{t}}{\underset{\text{︸}}{\eta_{t}\left( 1 - \frac{L\eta_{t}}{2} \right){\|\nabla F(w^{t})\|}^{2}}}} & {\leqslant} & {\underset{D_{t}}{\underset{\text{︸}}{F(w^{t}) - F^{\star}}}.}
\end{array}
$$

![Image](OEBPS/images/B9780443190377000089/si236.png)

这完全符合 [(1.13)](#Chp001_3-28_B9780443190377000089_split_001.xhtml#deq14) 的形式，其中 `ω[t] = 1`![Image](OEBPS/images/B9780443190377000089/si202.png) 和 `E[t] = 0`![Image](OEBPS/images/B9780443190377000089/si209.png)。无需进一步假设，我们有 `Δ[t] ≤ D[t] − D[t + 1]`![Image](OEBPS/images/B9780443190377000089/si237.png)，通过数学归纳法，得到 $\sum_{t = 0}^{T}\Delta_{t} \leqslant D_{0} - D_{T + 1} \leqslant D_{0}$![Image](OEBPS/images/B9780443190377000089/si238.png)，从而得出

$$
\min\limits_{0 \leqslant t \leqslant T}{\|\nabla F(w^{t})\|}^{2} \leqslant \frac{1}{S_{T}}\sum\limits_{t = 0}^{T}\gamma_{t}{\|\nabla F(w^{t})\|}^{2} \leqslant \frac{F(w^{0}) - F^{\star}}{S_{T}},
$$

![Image](OEBPS/images/B9780443190377000089/si239_u1.png)

其中 $\gamma_{t} = \eta_{t}(1 - \frac{L\eta_{t}}{2})$![Image](OEBPS/images/B9780443190377000089/si240_u1.png) 和 $S_{T} = \sum_{t = 0}^{T}\gamma_{t}$![Image](OEBPS/images/B9780443190377000089/si241_u1.png)，前提是 $0 < \eta_{t} < \frac{2}{L}$![Image](OEBPS/images/B9780443190377000089/si242_u1.png)。该结果使我们能够证明算法对 [(1.1)](#Chp001_3-28_B9780443190377000089_split_000.xhtml#deq1) 的驻点的最佳迭代收敛速率。

### (d) 光滑凸问题的梯度下降法

假设 `F` 是凸且 `L`-光滑的。让我们在 [(1.2)](#Chp001_3-28_B9780443190377000089_split_000.xhtml#deq2) 中选择 $\eta_{t}: = \frac{1}{L}$![Image](OEBPS/images/B9780443190377000089/si243_u1.png) 以得到 $w^{t + 1}: = w^{t} - \frac{1}{L}\nabla F(w^{t})$![Image](OEBPS/images/B9780443190377000089/si244_u1.png)。然后，从 [(1.14)](#Chp001_3-28_B9780443190377000089_split_001.xhtml#deq15) 和 [(1.16)](#Chp001_3-28_B9780443190377000089_split_001.xhtml#deq18)，以及 `F` 的凸性，我们有

$$
\left\{ \begin{array}{l}
{\frac{L}{2}{\| w^{t + 1} - w^{\star}\|}^{2} + \langle\nabla F(w^{t}),w^{t} - w^{\star}\rangle = \frac{L}{2}{\| w^{t} - w^{\star}\|}^{2} + \frac{1}{2L}{\|\nabla F(w^{t})\|}^{2},} \\
{(t + 1)[ F(w^{t + 1}) - F(w^{\star})] + \frac{(t + 1)}{2L}{\|\nabla F(w^{t})\|}^{2} \leqslant (t + 1)[ F(w^{t}) - F(w^{\star})],} \\
{F(w^{t}) - F(w^{\star}) \leqslant \langle\nabla F(w^{t}),w^{t} - w^{\star}\rangle.}
\end{array} \right.
$$

![Image](OEBPS/images/B9780443190377000089/si245_u1.png)

通过将这三个不等式相加并抵消项，我们得到

$$
\frac{L}{2}{\| w^{t + 1} - w^{\star}\|}^{2} + (t + 1)[ F(w^{t + 1}) - F(w^{\star})] + \frac{t}{2L}{\|\nabla F(w^{t})\|}^{2}\quad \leqslant \frac{L}{2}{\| w^{t} - w^{\star}\|}^{2} + t[ F(w^{t}) - F(w^{\star})].
$$

![Image](OEBPS/images/B9780443190377000089/si246_u1.png)

这完全符合 [(1.13)](#Chp001_3-28_B9780443190377000089_split_001.xhtml#deq14) 的形式，其中 $D_{t}: = \frac{L}{2}{\| w^{t} - w^{\star}\|}^{2} + t[ F(w^{t}) - F(w^{\star})]$![Image](OEBPS/images/B9780443190377000089/si247_u1.png)，$\Delta_{t}: = \frac{t}{2L}{\|\nabla F(w^{t})\|}^{2}$![Image](OEBPS/images/B9780443190377000089/si248_u1.png)，`E[t] = 0`![Image](OEBPS/images/B9780443190377000089/si209.png)，和 `ω[t] = 1`![Image](OEBPS/images/B9780443190377000089/si202.png)。这个递归估计蕴含 `D[t + 1] ≤ D[0]`![Image](OEBPS/images/B9780443190377000089/si249_u1.png)，因此，使用 `D[t + 1]`![Image](OEBPS/images/B9780443190377000089/si250_u1.png) 的定义并去掉 $\frac{L}{2}{\| w^{t + 1} - w^{\star}\|}^{2}$![Image](OEBPS/images/B9780443190377000089/si251_u1.png)，我们得到

$$
F(w^{t + 1}) - F(w^{\star}) \leqslant \frac{D_{0}}{t + 1} = \frac{L{\| w^{0} - w^{\star}\|}^{2}}{2(t + 1)},
$$

![Image](OEBPS/images/B9780443190377000089/si252_u1.png)


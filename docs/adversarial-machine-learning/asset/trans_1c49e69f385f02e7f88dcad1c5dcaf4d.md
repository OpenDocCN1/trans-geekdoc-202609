

1/\epsilon_n = o(MAC(f_n, A))。那么，如果没有通用算法能有效地在每个 f_n 上找到 \epsilon_n-IMAC^{(*)}，则没有通用算法能有效地为 \eta_n \to \infty 找到 \eta_n-IMAC^{(+)}。

证明 考虑任意分类器 f \in \mathcal{F}，使得 MAC(f, A) > 0。假设存在某个 \mathbf{x} \in \eta-IMAC^{(+)}，其中 \eta > 0。令 \epsilon = \eta / MAC(f, A)；那么按定义

A(\mathbf{x} - \mathbf{x}') \le \eta + MAC(f, A) = (1 + \epsilon) MAC(f, A), \quad (8.7)

这意味着 \mathbf{x} \in \epsilon-IMAC^{(*)}。然后通过逆否命题，如果对任何 0 < \epsilon \le \bar{\epsilon} 都无法有效找到 \epsilon-IMAC^{(*)}，则对任何 0 < \eta \le \bar{\epsilon} \cdot MAC(f, A) 都无法有效找到 \eta-IMAC^{(+)}。最后的结果是直接推论。

最后的陈述实际上适用于许多常见场景。例如，对于任何加权 \ell_p 成本（其中 0 < p \le \infty 且所有 d 的 0 < c_d < \infty），线性分类器族和超球面分类器族都足够多样，可以产生这样一系列分类器，它们允许像最后陈述所要求的那样具有无界 MAC。因此，诱导凸分类器族也可以产生这样一系列分类器。此外，正如我们在第 8.3 节中所示，确实存在 \ell_p 成本，对于这些成本存在 \bar{\epsilon} > 0，使得没有高效的基于查询的算法可以对任何 0 < \epsilon \le \bar{\epsilon} 找到 \epsilon-IMAC^{(*)}。其后果是，对于这些 \ell_p 成本，没有通用算法能够对诱导凸分类器实现任何固定 \eta 的加法最优性，如下面的定理所示：

### 定理 8.3
如果对于某个假设空间 \mathcal{F}、成本函数 A，以及对某个 f \in \mathcal{F} 的 MAC(f, A) 的任何初始边界 0 < C_0^+ < C_0^-，存在某个 \bar{\epsilon} > 0，使得没有高效的基于查询的算法可以对任何 0 < \epsilon \le \bar{\epsilon} 找到 \epsilon-IMAC^{(*)}，则没有高效的基于查询的算法可以对任何 0 < \eta \le \bar{\epsilon} \cdot C_0^- 找到 \eta-IMAC^{(+)}。其后果是，如果存在如上所述的 \bar{\epsilon} > 0，那么通常没有高效的基于查询的算法可以对任何 \eta \ge 0 找到 \eta-IMAC^{(+)}，因为 C_0^- 可以任意大。

证明 通过逆否命题。如果存在一个高效的基于查询的算法，它可以找到某个 \mathbf{x} \in \eta-IMAC^{(+)}，其中 0 < \eta \le \bar{\epsilon} \cdot C_0^-，那么根据 \eta-IMAC^{(+)} 的定义，A(\mathbf{x} - \mathbf{x}') \le \eta + MAC(f, A)。等价地，通过取 \eta = \epsilon \cdot MAC(f, A) 对某个 \epsilon > 0，该算法实现了 A(\mathbf{x} - \mathbf{x}') \le (1+\epsilon)MAC(f, A)；即，\mathbf{x} \in \epsilon-IMAC^{(*)}。此外，由于 MAC(f, A) \le C_0^-，这个高效算法能够对某个 \epsilon \le \bar{\epsilon} 找到 \epsilon-IMAC^{(*)}。最后的评论直接源于这样一个事实：对于任何 0 < \eta \le \bar{\epsilon} \cdot C_0^- 都没有高效的基于查询的算法，且 C_0^- 通常可以任意大。

此结果进一步表明，近似逃避中的加法最优性是一个尴尬的概念。如果存在一个成本函数 A，对于该函数，某些分类器族 \mathcal{F} 在任何精度 0 < \epsilon \le \bar{\epsilon} 内都不能被高效逃避，那么对于某些 \eta > 0 是否能实现高效加法最优性取决于成本函数的尺度。也就是说，如果对 A 可以高效实现 \eta-加法最优性，则可以重新缩放特征空间，使得 \eta-加法最优性不再通常高效，因为可以选择重新缩放来使 C_0^- 变大。这突出了加法最优性中缺乏尺度不变性的局限性：*成本的单位决定是否可以实现特定级别的加法精度，而乘法最优性是无单位的。* 对于（加权）\(\ell_1\) 成本，这不是问题，因为正如第 8.2 节所示，对于任何 \(\epsilon > 0\)，\(\epsilon\)-乘法最优性都有一个高效算法。但是，正如我们在第 8.3 节中所示，存在 \(\ell_p\) 成本，这会变得有问题。

在本章剩余部分，我们主要只针对 \(\epsilon\)-IMAC 处理 \(\epsilon\)-乘法最优性（除非另有明确说明），并定义 \(G_t = G_t^{(*)}\)、\(C_t = \sqrt{C_t^- \cdot C_t^+}\) 和 \(L_\ell = L_\ell^{(*)}\)。尽管如此，我们提出的算法可以通过简单更改提议步骤、停止条件以及 \(L_\ell^{(*)}\) 和 \(G_t\) 的定义，立即适应加法最优性，尽管如前面讨论的那样，它们可能通常不是高效的。

### 8.1.5 诱导凸分类器族

我们引入诱导凸分类器族，\(\mathcal{F}^{\text{convex}}\)；即，将特征空间 \(\mathcal{X}\) 划分为正类和负类的分类器集合，其中一个类是凸的。诱导凸分类器包括 Lowd & Meek 研究的线性分类器，以及使用有界 PCA 的异常检测分类器（Lakhina et al. 2004b）、使用超球边界的异常检测算法（Bishop 2006）、通过对数-凹（或单峰）密度函数的对数似然阈值来预测异常的一类分类器，以及形式为 \(\mathbf{x}^\top \mathbf{Ax} + \mathbf{b}^\top \mathbf{x} + c \ge 0\) 的二次分类器（如果 **A** 是半正定的（参见 Boyd & Vandenberghe 2004，第 3 章））。诱导凸分类器还包括任何可数个半空间、圆锥或球的交集等复杂集合。

诱导凸分类器族与所有凸集之间存在对应关系；即，\(\mathbb{C} = \{\mathbb{X} \mid convex(\mathbb{X})\}\)。根据诱导凸分类器的定义，每个分类器 \(f \in \mathcal{F}^{\text{convex}}\) 都对应 \(\mathbb{C}\) 中的某个凸集。此外，对于任何凸集 \(\mathbb{X} \in \mathbb{C}\)，至少有两个平凡分类器可以创建该集合；即分类器 \(f_{\mathbb{X}}^{**}(\mathbf{x}) = \text{I}[\mathbf{x} \in \mathbb{X}]\) 和 \(f_{\mathbb{X}}^{**}(\mathbf{x}) = \text{I}[\mathbf{x} \notin \mathbb{X}]\)。因此，在本章剩余部分，我们使用特定凸集的存在来证明关于诱导凸分类器的结果，因为总是存在一个对应的分类器。

还值得提及以下关于诱导凸分类器上近似逃避问题的另一种表征。对于任何具有非空内部的凸集 \(\mathbb{C}\)，令 \(\mathbf{x}^{(c)}\) 为其内部的一个点，并定义（以 \(\mathbf{x}^{(c)}\) 为中心的）明科夫斯基度量为 \(m_\mathbb{C}(\mathbf{x}) = \inf \{ \lambda \mid (\mathbf{x} - \mathbf{x}^{(c)}) \in \lambda(\mathbb{C} - \mathbf{x}^{(c)}) \}\)。该函数是凸且非负的，并且满足 \(m_\mathbb{C}(\mathbf{x}) \le 1\) 当且仅当 \(\mathbf{x} \in \mathbb{C}\)。因此，我们可以用明科夫斯基度量来重新写出分类器的 _MAC_ 的定义——如果 \(\mathcal{X}_f^+\) 是凸的，则要求 \(m_{\mathcal{X}_f^+}(\mathbf{x}) > 1\)，如果 \(\mathcal{X}_f^-\) 是凸的，则要求 \(m_{\mathcal{X}_f^-}(\mathbf{x}) \le 1\)。这样，近似逃避问题（当 \(\mathcal{X}_f^-\) 凸时）可以重新写为

$$
\text{argmin}_{\mathbf{x} \in \mathcal{X}} \left[ A \left( \mathbf{x} - \mathbf{x}^d \right) \right]
\quad \text{s.t.} \quad m_{\mathcal{X}_f^-}(\mathbf{x}) \le 1 \quad (8.8)
$$

如果 \( A \) 是凸的，那么由于 \( m_\mathbb{C}(\cdot) \) 是凸的，这构成了一个可以通过优化其拉格朗日函数来求解的凸规划

$$
argmin_{\mathbf{x} \in \mathcal{X}, \gamma \in \mathbb{R}_{0+}} \left[ A \left( \mathbf{x} - \mathbf{x}^d \right) + \gamma \left( 1 - m_{\mathcal{X}_f^-} (\mathbf{x}) \right) \right].
$$

在 \( m_{\mathcal{X}_f^-}(\cdot) \) 具有解析解的情况下，该优化可能具有解析解，但通常这种方法似乎比较困难。相反，我们利用 \(\ell_1\) 成本函数的特殊结构，在诱导凸分类器族上构建高效搜索。

## 8.2 针对 \(\ell_1\) 成本的凸类逃避

我们将 \(\epsilon\)-IMAC 可搜索性推广到诱导凸分类器族。将 \(\mathcal{F}\) 限制为诱导凸分类器族简化了 \(\epsilon\)-IMAC 搜索。在我们对这个问题的方法中，我们将诱导凸分类器族 \(\mathcal{F}^{\text{convex}}\) 分为 \(\mathcal{F}^{\text{convex},-}\) 和 \(\mathcal{F}^{\text{convex},+}\)，分别对应于诱导凸集 \(\mathcal{X}_f^-\) 或 \(\mathcal{X}_f^+\) 的分类器（当然，线性分类器两者都属于）。当负类 \(\mathcal{X}_f^-\) 是凸的（即，\( f \in \mathcal{F}^{\text{convex},-}\)）时，问题归约为在凸集约束下最小化（凸）函数 \( A \) ——如果对手知道 \(\mathcal{X}_f^-\)，该问题简单归约为求解凸优化规划（参见 Boyd & Vandenberghe 2004，第 4 章）。然而，当正类 \(\mathcal{X}_f^+\) 是凸的（即，\( f \in \mathcal{F}^{\text{convex},+}\)）时，问题变为在凸集之外最小化（凸）函数 \( A \)；这通常是一个困难问题（参见第 8.3.1.4 节，我们在那里展示最小化 \(\ell_2\) 成本可能需要指数级查询复杂度）。尽管如此，对于某些成本函数 \( A \)，很容易确定特定的成本球 \(\mathbb{B}^C(A)\) 是否完全包含在凸集中。这导致了本节所介绍的高效近似算法。

我们为诱导凸分类器族的（加权）\(\ell_1\) 成本 \( A_1^{(\mathbf{c})} \)（公式 8.1）构建了用于基于查询的优化的高效算法。然而，这个问题存在不对称性，取决于正类或负类哪个是凸的，如图 8.1 所示。当正集是凸的时，确定 \(\ell_1\) 球 \(\mathbb{B}^C \left( A_1^{(\mathbf{c})} \right)\) 是否是 \(\mathcal{X}_f^+\) 的子集只需要查询球的顶点，如图 8.1(a) 所示。当负集是凸的时，确定 \(\mathbb{B}^C \left( A_1^{(\mathbf{c})} \right) \cap \mathcal{X}_f^- = \emptyset\) 是否成立是非平凡的，因为交点不一定出现在顶点，如图 8.1(b) 所示。当 \(\mathcal{X}_f^+\) 是凸的时，我们介绍了一种用于优化（加权）\(\ell_1\) 成本的高效算法，以及当 \(\mathcal{X}_f^-\) 是凸时用于优化任何凸成本的多项式随机算法，尽管在两种情况下，我们只考虑具有非空内部的凸集。我们介绍的算法通过前一节讨论的二分搜索策略实现乘法最优性。在接下来的内容中，我们使用公式 (8.6) 将 \( L_\epsilon \) 定义为二分搜索所需的阶段数


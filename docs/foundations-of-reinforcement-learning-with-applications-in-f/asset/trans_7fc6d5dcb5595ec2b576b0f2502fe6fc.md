

我们将验证 `f(x) = cos(x)` 是否为收缩函数作为练习留给你，其定义域为 `𝒳 = ℝ`，度量 `d` 定义为 `d(x[1], x[2]) = |x[1] − x[2]|`。现在让我们编写一些代码来实现上面描述的不动点算法。请注意，我们为任何泛型类型 X 实现此算法，以表示任意域 𝒳。

![](images/comp05_1.jpg)

上述函数将一个函数（`step: Callable[[X], X]`）和一个起始值（`start: X`）作为输入，并反复应用该函数，同时以 `Iterator[X]` 的形式产生值，即作为值的流。这会产生一个无限流。我们需要一种方法来指定收敛性，即当流中连续值“足够接近”时。

![](images/comp05_2.jpg)

上述函数 `converge` 将来自 `iterate` 的生成值（参数 `values: Iterator[X]`）和一个指示收敛性的信号（参数 `done: Callable[[X, X], bool]`）作为输入，并在 `done` 为 True 之前生成这些值。用户有责任编写函数 `done` 并将其传递给 `converge`。现在让我们使用这两个函数来求解 `x = cos(x)`。

![](images/comp05_3.jpg)

这将打印一个跟踪，显示流的索引以及在反复应用函数 `cos` 时该索引处的值。当连续两个值在小数点后 3 位以内相同时，它将终止。

![](images/comp05_4.jpg)

我们鼓励你尝试其他起始值（除了上面的 `x[0] = 0.0`）并查看跟踪。我们还鼓励你找出其他在适当度量下为收缩的函数 `f`。上述不动点代码位于文件 `rl/iterate.py` 中。在此文件中，你将找到另外两个函数 `last` 和 `converged`，用于在给定迭代器的值根据 `done` 函数收敛时产生最终值。

## 5.4 贝尔曼策略算子与策略评估算法

我们的第一个动态规划算法称为 *策略评估*。策略评估算法解决了在固定策略 *π* 下计算有限马尔可夫决策过程（MDP）的值函数的问题（即有限 MDP 的预测问题）。我们知道，这等同于计算 *π* 隐含的有限马尔可夫奖励过程（MRP）的值函数。为了避免符号混淆，请注意，符号上的上标 *π* 表示它指的是 *π* 隐含 MRP 的符号。预测问题的精确规范如下：

设 MDP 的状态（因此也是 *π* 隐含 MRP 的状态）为 `𝒮 = {s[1], s[2], …, s[n]}`，并且不失一般性，设 `𝒩 = {s[1], s[2], …, s[m]}` 为非终止状态。我们给定一个固定策略 `π: 𝒩 × 𝒜 → [0,1]`。我们还给定了 *π* 隐含 MRP 的转移概率函数：

$$
\begin{array}{r}
\left. \mathcal{P}_{R}^{\pi}: \mathcal{N} \times \mathcal{D} \times \mathcal{S} \rightarrow [0,1] \right.
\\
\end{array}
$$

以数据结构的形式（因为状态是有限的，并且从每个非终止状态转移的下一状态和奖励对也是有限的）。预测问题是计算使用策略 *π* 评估的 MDP 的值函数（等同于 *π* 隐含 MRP 的值函数），我们将其表示为 `V^(π): 𝒩 → ℝ`。

我们知道，从 [第 3 章](#chapter3.xhtml) 和 [第 4 章](#chapter4.xhtml) 可知，通过从 `𝒫[R]^(π)` 提取隐含马尔可夫过程的转移概率函数 `𝒫^(π): 𝒩 × 𝒮 → [0,1]` 和奖励函数 `ℛ^(π): 𝒩 → ℝ`，我们可以对值函数 `V^(π): 𝒩 → ℝ`（表示为列向量 `**V**^(π) ∈ ℝ^(m)`）执行以下计算来解决这个预测问题：

$$
\begin{array}{r}
{\mathbf{\mathbf{V}}^{\pi} = {(\mathbf{\mathbf{I}}_{\mathbf{\mathbf{m}}} - \gamma\mathcal{P}^{\pi})}^{- 1} \cdot \mathcal{R}^{\pi}}
\\
\end{array}
$$

其中 `**I**[**m**]` 是 *m* × *m* 单位矩阵，列向量 `ℛ^(π) ∈ ℝ^(m)` 表示 `ℛ^(π)`，而 `𝒫^(π)` 是表示 `𝒫^(π)` 的 *m* × *m* 矩阵（行和列对应于非终止状态）。然而，当 *m* 很大时，此计算无法扩展。因此，我们寻找一个数值算法来求解（针对 `**V**^(π)`）以下 MRP 贝尔曼方程（针对更多数量的有限状态）：

$$
\begin{array}{r}
{\mathbf{\mathbf{V}}^{\pi} = \mathcal{R}^{\pi} + \gamma\mathcal{P}^{\pi} \cdot \mathbf{\mathbf{V}}^{\pi}}
\\
\end{array}
$$

我们定义 *贝尔曼策略算子* `**B**^(π): ℝ^(m) → ℝ^(m)` 为：

$$
\begin{array}{r}
{\mathbf{\mathbf{B}}^{\pi}(\mathbf{\mathbf{V}}) = \mathcal{R}^{\pi} + \gamma\mathcal{P}^{\pi} \cdot \mathbf{\mathbf{V}}\text{~for~any~vector~}\mathbf{\mathbf{V}}\text{~in~the~vector~space~}{\mathbb{R}}^{m}}
\\
\end{array}
$$

(5.1)

因此，MRP 贝尔曼方程可以表示为：

$$
\begin{array}{r}
{\mathbf{\mathbf{V}}^{\pi} = \mathbf{\mathbf{B}}^{\pi}(\mathbf{\mathbf{V}}^{\pi})}
\\
\end{array}
$$

这意味着 `**V**^(π) ∈ ℝ^(m)` 是 *贝尔曼策略算子* `**B**^(π): ℝ^(m) → ℝ^(m)` 的不动点。请注意，贝尔曼策略算子可以推广到非有限 MDP 的情况，并且 `V^(π)` 仍然是各种感兴趣推广的不动点。但是，由于本章专注于开发有限 MDP 的算法，我们将使用上述较窄（方程 (5.1)）的定义。此外，为了证明本章中基于不动点的动态规划算法的正确性，我们将假设折扣因子 `γ < 1`。

请注意 `**B**^(π)` 是 `ℝ^(m)` 中向量上的仿射变换，应被视为简单 1-D（`ℝ → ℝ`）仿射变换 `y = a + b*x` 的推广，其中乘数 `b` 被矩阵 `γ𝒫^(π)` 取代，平移 `a` 被列向量 `ℛ^(π)` 取代。

我们希望找到一个度量，使得 `**B**^(π)` 是收缩函数，以便我们可以利用班赫不动点定理，通过反复应用贝尔曼策略算子 `**B**^(π)` 来解决这个预测问题。对于任何值函数 `**V** ∈ ℝ^(m)`（表示 `V: 𝒩 → ℝ`），我们将任何状态 `s ∈ 𝒩` 的值表示为 `**V**(s)`。

我们的度量 `d: ℝ^(m) × ℝ^(m) → ℝ` 将是 `L^∞` 范数，定义为：

$$
\begin{array}{r}
{d(\mathbf{\mathbf{X}}, \mathbf{\mathbf{Y}}) = \|\mathbf{\mathbf{X}} - \mathbf{\mathbf{Y}}\|_{\infty} = \max_{s \in \mathcal{N}} |(\mathbf{\mathbf{X}} - \mathbf{\mathbf{Y}})(s)|}
\\
\end{array}
$$

`**B**^(π)` 在 `L^∞` 范数下是收缩函数，因为对于所有 `**X**, **Y** ∈ ℝ^(m)`，

$$
\begin{array}{r}
{\max_{s \in \mathcal{N}} |(\mathbf{\mathbf{B}}^{\pi}(\mathbf{\mathbf{X}}) - \mathbf{\mathbf{B}}^{\pi}(\mathbf{\mathbf{Y}}))(s)| = \gamma \cdot \max_{s \in \mathcal{N}} |(\mathcal{P}^{\pi} \cdot (\mathbf{\mathbf{X}} - \mathbf{\mathbf{Y}}))(s)| \leq \gamma \cdot \max_{s \in \mathcal{N}} |(\mathbf{\mathbf{X}} - \mathbf{\mathbf{Y}})(s)|}
\\
\end{array}
$$

因此，调用班赫不动点定理证明了以下定理：

这为我们提供了以下迭代算法（称为固定策略 `π: 𝒩 × 𝒜 → [0,1]` 的 *策略评估* 算法）：

*   从任何值函数 `**V**[**0**] ∈ ℝ^(m)` 开始
*   对 `i = 0, 1, 2, …` 进行迭代，在每次迭代中计算：

    $$
    \begin{array}{r}
    {\mathbf{\mathbf{V}}_{\mathbf{\mathbf{i}} + \mathbf{1}} = \mathbf{\mathbf{B}}^{\pi}(\mathbf{\mathbf{V}}_{\mathbf{\mathbf{i}}}) = \mathcal{R}^{\pi} + \gamma\mathcal{P}^{\pi} \cdot \mathbf{\mathbf{V}}_{\mathbf{\mathbf{i}}}}
    \\
    \end{array}
    $$

*   当 `d(**V**[**i**], **V**[**i** + **1**]) = max[*s* ∈ 𝒩] |(**V**[**i**] − **V**[**i** + **1**])(*s*)|` 足够小时停止算法。


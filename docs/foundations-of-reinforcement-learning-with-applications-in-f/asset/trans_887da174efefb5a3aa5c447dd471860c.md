

## 单调性与常数平移性质

Observe that for each state `s` ∈ `𝒩` and each action `a` ∈ `𝒜`,

$$
\begin{array}{r}
{\left\{ \mathcal{R}(s,a) + \gamma{\sum\limits_{s^{\prime} \in \mathcal{N}}\mathcal{P}}(s,a,s^{\prime}) \cdot \mathbf{\mathbf{X}}(s^{\prime}) \right\} - \left\{ \mathcal{R}(s,a) + \gamma{\sum\limits_{s^{\prime} \in \mathcal{N}}\mathcal{P}}(s,a,s^{\prime}) \cdot \mathbf{\mathbf{Y}}(s^{\prime}) \right\}}
\\
\end{array}
$$

$$
\begin{array}{r}
{= \gamma{\sum\limits_{s^{\prime} \in \mathcal{N}}\mathcal{P}}(s,a,s^{\prime}) \cdot (\mathbf{\mathbf{X}}(s^{\prime}) - \mathbf{\mathbf{Y}}(s^{\prime})) \geq 0}
\\
\end{array}
$$

Therefore for each state `s` ∈ `𝒩`,

$$
\begin{array}{r}
{\mathbf{\mathbf{B}}^{\*}(\mathbf{\mathbf{X}})(s) - \mathbf{\mathbf{B}}^{\*}(\mathbf{\mathbf{Y}})(s)}
\\
\end{array}
$$

$$
\begin{array}{r}
{= \max\_{a \in \mathcal{A}}\left\{ \mathcal{R}(s,a) + \gamma{\sum\limits_{s^{\prime} \in \mathcal{N}}\mathcal{P}}(s,a,s^{\prime}) \cdot \mathbf{\mathbf{X}}(s^{\prime}) \right\} - \max\_{a \in \mathcal{A}}\left\{ \mathcal{R}(s,a) + \gamma{\sum\limits_{s^{\prime} \in \mathcal{N}}\mathcal{P}}(s,a,s^{\prime}) \cdot \mathbf{\mathbf{Y}}(s^{\prime}) \right\} \geq 0}
\\
\end{array}
$$

### 2. 常数平移性质

i.e., for all `X` ∈ `ℝ`^`(m)`, `c` ∈ `ℝ`,

$$
\begin{array}{r}
{\mathbf{\mathbf{B}}^{\*}(\mathbf{\mathbf{X}} + c)(s) = \mathbf{\mathbf{B}}^{\*}(\mathbf{\mathbf{X}})(s) + \gamma c\text{~for~all~}s \in \mathcal{N}}
\\
\end{array}
$$

在上述陈述中，将一个常数（∈ `ℝ`）加到值函数（∈ `ℝ`^`(m)`）上，会将该常数逐点地加到值函数的所有状态上（即表示值函数的向量的所有维度）。换句话说，一个常数 ∈ `ℝ` 可以被视为一个值函数，该函数对所有状态都具有相同的（常数）值。因此，

$$
\begin{array}{r}
{\mathbf{\mathbf{B}}^{\*}(\mathbf{\mathbf{X}} + c)(s) = \max\_{a \in \mathcal{A}}\left\{ \mathcal{R}(s,a) + \gamma{\sum\limits_{s^{\prime} \in \mathcal{N}}\mathcal{P}}(s,a,s^{\prime}) \cdot (\mathbf{\mathbf{X}}(s^{\prime}) + c) \right\}}
\\
\end{array}
$$

$$
\begin{array}{r}
{= \max\_{a \in \mathcal{A}}\left\{ \mathcal{R}(s,a) + \gamma{\sum\limits_{s^{\prime} \in \mathcal{N}}\mathcal{P}}(s,a,s^{\prime}) \cdot \mathbf{\mathbf{X}}(s^{\prime}) \right\} + \gamma c = \mathbf{\mathbf{B}}^{\*}(\mathbf{\mathbf{X}})(s) + \gamma c}
\\
\end{array}
$$

有了 `B`^`(*)` 的这两个性质，让我们来证明 `B`^`(*)` 是一个收缩函数。对于给定的 `X`、`Y` ∈ `ℝ`^`(m)`，假设：

$$
\begin{array}{r}
{\max\_{s \in \mathcal{N}}|(\mathbf{\mathbf{X}} - \mathbf{\mathbf{Y}})(s)| = c}
\\
\end{array}
$$

我们可以将其改写为：

$$
\begin{array}{r}
{\mathbf{\mathbf{X}}(s) - c \leq \mathbf{\mathbf{Y}}(s) \leq \mathbf{\mathbf{X}}(s) + c\text{~for~all~}s \in \mathcal{N}}
\\
\end{array}
$$

由于 `B`^`(*)` 具有单调性，我们可以对上述双不等式应用 `B`^`(*)`。

$$
\begin{array}{r}
{\mathbf{\mathbf{B}}^{\*}(\mathbf{\mathbf{X}} - c)(s) \leq \mathbf{\mathbf{B}}^{\*}(\mathbf{\mathbf{Y}})(s) \leq \mathbf{\mathbf{B}}^{\*}(\mathbf{\mathbf{X}} + c)(s)\text{~for~all~}s \in \mathcal{N}}
\\
\end{array}
$$

由于 `B`^`(*)` 具有常数平移性质，

$$
\begin{array}{r}
{\mathbf{\mathbf{B}}^{\*}(\mathbf{\mathbf{X}})(s) - \gamma c \leq \mathbf{\mathbf{B}}^{\*}(\mathbf{\mathbf{Y}})(s) \leq \mathbf{\mathbf{B}}^{\*}(\mathbf{\mathbf{X}})(s) + \gamma c\text{~for~all~}s \in \mathcal{N}}
\\
\end{array}
$$

换句话说，

$$
\begin{array}{r}
{\max\_{s \in \mathcal{N}}|(\mathbf{\mathbf{B}}^{\*}(\mathbf{\mathbf{X}}) - \mathbf{\mathbf{B}}^{\*}(\mathbf{\mathbf{Y}}))(s)| \leq \gamma c = \gamma \cdot \max\_{s \in \mathcal{N}}|(\mathbf{\mathbf{X}} - \mathbf{\mathbf{Y}})(s)|}
\\
\end{array}
$$

因此，调用 Banach 定点定理证明了以下定理：

这给出了以下迭代算法，称为 `Value Iteration` 算法，由 Richard Bellman ([Bellman 1957a](#bib01.xhtml#refbib_8)) 提出：

*   从任何值函数 `V`[`0`] ∈ `ℝ`^`(m)` 开始
*   对 `i` = 0, 1, 2, … 进行迭代，在每次迭代中计算：

    $$
    \begin{array}{r}
    {\mathbf{\mathbf{V}}\_{\mathbf{\mathbf{i}} + \mathbf{1}}(s) = \mathbf{\mathbf{B}}^{\*}(\mathbf{\mathbf{V}}\_{\mathbf{\mathbf{i}}})(s)\text{~for~all~}s \in \mathcal{N}}
    \\
    \end{array}
    $$

*   当 `d`(`V`[`i`], `V`[`i` + `1`]) = max[`s` ∈ `𝒩`]|(`V`[`i`] − `V`[`i` + `1`])(`s`)| 足够小时停止算法。

值得注意的是，Banach 定点定理不仅保证收敛到唯一解 `V`^`(*)`（无论我们从哪个值函数 `V`[`0`] 开始算法），还保证合理的收敛速度（取决于起始值函数 `V`[`0`] 的选择和 `γ` 的选择）。

## 5.9 从最优值函数得到最优策略

请注意，策略迭代算法在每次迭代中都会产生一个策略及其对应的值函数。因此，在最终，当我们在第 `j` 次迭代中收敛到最优值函数 `V`[`j`] = `V`^`(*)` 时，策略迭代算法有一个与 `V`[`j`] 关联的确定性策略 `π`[`j`]，使得：

$$
\begin{array}{r}
{\mathbf{\mathbf{V}}\_{\mathbf{\mathbf{j}}} = \mathbf{\mathbf{V}}^{\pi\_{j}} = \mathbf{\mathbf{V}}^{\*}}
\\
\end{array}
$$

我们将 `π`[`j`] 称为最优策略 `π`^`(*)`，即产生最优值函数 `V`^`(*)` 的策略，也就是说，

$$
\begin{array}{r}
{\mathbf{\mathbf{V}}^{\pi^{\*}} = \mathbf{\mathbf{V}}^{\*}}
\\
\end{array}
$$

但是值迭代没有这样的关联策略，因为整个算法没有策略表示，仅操作值函数。那么问题来了：当值迭代在第 `i` 次迭代中收敛到最优值函数 `V`[`i`] = `V`^`(*)` 时，我们如何得到一个最优策略 `π`^`(*)`，使得：

$$
\begin{array}{r}
{\mathbf{\mathbf{V}}^{\pi^{\*}} = \mathbf{\mathbf{V}}\_{\mathbf{\mathbf{i}}} = \mathbf{\mathbf{V}}^{\*}}
\\
\end{array}
$$

答案在于贪婪策略函数 `G`。方程 (5.7) 告诉我们：

$$
\begin{array}{r}
{\mathbf{\mathbf{B}}^{G(\mathbf{\mathbf{V}})}(\mathbf{\mathbf{V}}) = \mathbf{\mathbf{B}}^{\*}(\mathbf{\mathbf{V}})\text{~for~all~}\mathbf{\mathbf{V}} \in {\\mathbb{R}}^{m}}
\\
\end{array}
$$

将 `V` 特化为 `V`^`(*)`，我们得到：

$$
\begin{array}{r}
{\mathbf{\mathbf{B}}^{G(\mathbf{\mathbf{V}}^{\*})}(\mathbf{\mathbf{V}}^{\*}) = \mathbf{\mathbf{B}}^{\*}(\mathbf{\mathbf{V}}^{\*})}
\\
\end{array}
$$

但我们知道 `V`^`(*)` 是贝尔曼最优算子 `B`^`(*)` 的定点，即 `B`^`(*)`(`V`^`(*)`) = `V`^`(*)`。因此，

$$
\begin{array}{r}
{\mathbf{\mathbf{B}}^{G(\mathbf{\mathbf{V}}^{\*})}(\mathbf{\mathbf{V}}^{\*}) = \mathbf{\mathbf{V}}^{\*}}
\\
\end{array}
$$

上述方程表明 `V`^`(*)` 是贝尔曼策略算子 `B`^`(*G(`**`V`**`^`(*)`))` 的定点。然而，我们知道 `B`^`(*G(`**`V`**`^`(*)`))` 有一个唯一的定点，等于 `V`^`(*G(`**`V`**`^`(*)`))`。因此，

$$
\begin{array}{r}
{\mathbf{\mathbf{V}}^{G(\mathbf{\mathbf{V}}^{\*})} = \mathbf{\mathbf{V}}^{\*}}
\\
\end{array}


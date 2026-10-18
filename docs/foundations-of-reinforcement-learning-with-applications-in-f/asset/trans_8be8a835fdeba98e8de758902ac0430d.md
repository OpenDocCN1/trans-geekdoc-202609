

GPI 在 LSPI 算法中的每次迭代都从一个确定性目标策略 `π[D](⋅)` 开始，该策略作为从上一次迭代的 LSTDQ 求解的 `Q̂(s; a; w^(∗))` 推导出的贪婪策略提供。`w^(∗)` 的 LSTDQ 解基于预生成的训练数据，并将 Q-Learning 目标策略设置为 `π[D]`。由于我们只学习 `a = c` 的 Q-Value 函数，生成训练经验数据的行为策略 `μ` 是一个常数函数 `μ(s) = c`。还要注意，对于美式期权，`a = c` 的奖励为 0。因此，每个用于训练的原子经验的形式为 `(s, c, 0, s′)`。这意味着我们可以将每个用于训练的原子经验表示为一个 2 元组 `(s, s′)`。这将 LSPI 半梯度方程 (13.2) 简化为：

$$
\begin{array}{r} {{\sum\limits_{i}\phi}(s_{i}) \cdot (\phi{(s_{i})}^{T} \cdot \mathbf{\mathbf{w}}^{\*} - \gamma \cdot \hat{Q}(s_{i}^{\\prime},\pi_{D}(s_{i}^{\\prime});\mathbf{\mathbf{w}}^{\*})) = 0} \\\\ \end{array}
$$

(13.3)

我们需要考虑术语 `Q̂(s[i]^′, π[D](s[i]^′); w^(∗))` 的两种情况：

*   `C1`: 如果 `s[i]^′` 不是终止状态且 `π[D](s[i]^′) = c`（即，`ϕ(s[i]^′)^(T) ⋅ w ≥ g(s[i]^′)`）：在方程 (13.3) 中用 `ϕ(s[i]^′)^(T) ⋅ w^(∗)` 替换 `Q̂(s[i]^′, π[D](s[i]^′); w^(∗))`

*   `C2`: 如果 `s[i]^′` 是终止状态或 `π[D](s[i]^′) = e`（即，`g(s[i]^′) > ϕ(s[i]^′)^(T) ⋅ w`）：在方程 (13.3) 中用 `g(s[i]^′)` 替换 `Q̂(s[i]^′, π[D](s[i]^′); w^(∗))`

因此，我们可以使用指示符号 `𝕀` 对情况 `C1`、`C2` 重写方程 (13.3) 为：

$$
\begin{array}{r} {{\sum\limits_{i}\phi}(s_{i}) \cdot (\phi{(s_{i})}^{T} \cdot \mathbf{\mathbf{w}}^{\*} - \mathbb{I}_{C1} \cdot \gamma \cdot \phi{(s_{i}^{\\prime})}^{T} \cdot \mathbf{\mathbf{w}}^{\*} - \mathbb{I}_{C2} \cdot \gamma \cdot g(s_{i}^{\\prime})) = 0} \\\\ \end{array}
$$

提取 `w^(∗)`，我们得到：

$$
\begin{array}{r} {({\sum\limits_{i}\phi}(s_{i}) \cdot {(\phi(s_{i}) - \mathbb{I}_{C1} \cdot \gamma \cdot \phi(s_{i}^{\\prime}))}^{T}) \cdot \mathbf{\mathbf{w}}^{\*} = \gamma \cdot {\sum\limits_{i}\mathbb{I}_{C2}} \cdot \phi(s_{i}) \cdot g(s_{i}^{\\prime})} \\\\ \end{array}
$$

这可以写成熟悉的向量-矩阵表示法为：`A ⋅ w^(∗) = b`

$$
\begin{array}{r} {\mathbf{\mathbf{A}} = {\sum\limits_{i}\phi}(s_{i}) \cdot {(\phi(s_{i}) - \mathbb{I}_{C1} \cdot \gamma \cdot \phi(s_{i}^{\\prime}))}^{T}} \\\\ \end{array}
$$

$$
\begin{array}{r} {\mathbf{\mathbf{b}} = \gamma \cdot {\sum\limits_{i}\mathbb{I}_{C2}} \cdot \phi(s_{i}) \cdot g(s_{i}^{\\prime})} \\\\ \end{array}
$$

`m × m` 矩阵 `A` 在每个原子经验 `(s[i], s[i]^′)` 上累积为：

$$
\begin{array}{r} \left. \mathbf{\mathbf{A}}\leftarrow\mathbf{\mathbf{A}} + \phi(s_{i}) \cdot {(\phi(s_{i}) - \mathbb{I}_{C1} \cdot \gamma \cdot \phi(s_{i}^{\\prime}))}^{T} \right. \\\\ \end{array}
$$

`m`-向量 `b` 在每个原子经验 `(s[i], s[i]^′)` 上累积为：

$$
\begin{array}{r} \left. \mathbf{\mathbf{b}}\leftarrow\mathbf{\mathbf{b}} + \gamma \cdot \mathbb{I}_{C2} \cdot \phi(s_{i}) \cdot g(s_{i}^{\\prime}) \right. \\\\ \end{array}
$$

利用 `A` 的 Sherman-Morrison 增量逆，我们可以将时间复杂度从 `O(m³)` 降低到 `O(m²)`。

这求解的 `w^(∗)` 将 `Q`-Value 函数近似更新为 `Q̂(s, a; w^(∗))`。这定义了一个更新的、改进的确定性策略 `π[D]^′`（作为下一次 GPI 迭代的确定性目标策略）：

$$
\begin{array}{r} {\pi_{D}^{\\prime}(s) = \text{arg}\,\text{max}_{a}\hat{Q}(s,a;\mathbf{\mathbf{w}}^{\*})\text{~for~all~}s \in \mathcal{N}} \\\\ \end{array}
$$

Li, Szepesvari, Schuurmans ([Li, Szepesvári, and Schuurmans 2009](#bib01.xhtml#refbib_41)) 在他们的论文中建议使用 7 个特征函数，前 4 个是 Laguerre 多项式，是基础价格的函数，还有 3 个是时间的函数。精确地说，他们推荐的特征函数是：

*   `ϕ[0](S[t]) = 1`

*   $\phi_{1}(S_{t}) = e^{- \frac{M_{t}}{2}}$

*   $\phi_{2}(S_{t}) = e^{- \frac{M_{t}}{2}} \cdot (1 - M_{t})$

*   $\phi_{3}(S_{t}) = e^{- \frac{M_{t}}{2}} \cdot (1 - 2M_{t} + M_{t}^{2}/2)$

*   $\phi_{0}^{(t)}(t) = sin(\frac{\pi(T - t)}{2T})$

*   `ϕ[1]^((t))(t) = log(T − t)`

*   $\phi_{2}^{(t)}(t) = {(\frac{t}{T})}^{2}$

其中 $M_{t} = \frac{S_{t}}{K}$（`S[t]` 是当前基础价格，`K` 是美式期权行权价），`t` 是当前时间，`T` 是到期时间（即，`0 ≤ t < T`）。

### 13.6.2 美式期权定价的深度 Q-Learning

LSPI 数据高效且计算高效，但线性是函数近似的局限性。替代方案是（增量）Q-Learning 与神经网络函数近似，我们将在本小节中介绍。我们采用与 LSPI 相同的设置（包括经验回放）——具体来说，函数近似仅用于继续值。精确地说，

$$
\begin{array}{l} {\hat{Q}(s,a;\mathbf{\mathbf{w}}) = \left\{ \begin{array}{ll} {f(s;\mathbf{\mathbf{w}})} & {\text{~if~}a = c} \\\\ {g(s)} & {\text{~if~}a = e} \\\\ \end{array}~ \right.\text{~for~all~}s \in \mathcal{N}} \\\\ \end{array}
$$

其中 `f(s; w)` 是深度神经网络函数近似。

每个原子经验 `(s[i], s[i]^′)` 的 Q-Learning 更新为：

$$
\begin{array}{r} {\Delta\mathbf{\mathbf{w}} = \alpha \cdot (\gamma \cdot \hat{Q}(s_{i}^{\\prime},\pi(s_{i}^{\\prime});\mathbf{\mathbf{w}}) - f(s_{i};\mathbf{\mathbf{w}})) \cdot \nabla_{\mathbf{\mathbf{w}}}f(s_{i};\mathbf{\mathbf{w}})} \\\\ \end{array}
$$

当 `s[i]^′` 是非终止状态时，更新为：

$$
\begin{array}{r} {\Delta\mathbf{\mathbf{w}} = \alpha \cdot (\gamma \cdot \max(g(s_{i}^{\\prime}),f(s_{i}^{\\prime};\mathbf{\mathbf{w}})) - f(s_{i};\mathbf{\mathbf{w}})) \cdot \nabla_{\mathbf{\mathbf{w}}}f(s_{i};\mathbf{\mathbf{w}})} \\\\ \end{array}
$$

当 `s[i]^′` 是终止状态时，更新为：

$$
\begin{array}{r} {\Delta\mathbf{\mathbf{w}} = \alpha \cdot (\gamma \cdot g(s_{i}^{\\prime}) - f(s_{i};\mathbf{\mathbf{w}})) \cdot \nabla_{\mathbf{\mathbf{w}}}f(s_{i};\mathbf{\mathbf{w}})} \\\\ \end{array}
$$

## 13.7 VALUE FUNCTION GEOMETRY

现在我们更深入地探讨 `Deadly Triad`（我们在 [第 12 章](#chapter12.xhtml) 中曾提及）的问题，将 Value Functions 视为 Vectors（我们在 [第 5 章](#chapter5.xhtml) 中已这样做过），理解 Value Function Vector 转换，兼顾几何直觉与数学严谨性，为开发 RL 算法所使用的各种传统损失函数的收敛性问题提供洞察。一如既往，理解 Vector 转换的最佳方式是将其可视化，因此我们松散地将此主题称为 Value Function Geometry。几何直觉对于线性函数近似尤其有用。为了促进直觉，我们将针对 Value Function 的线性函数近似呈现此内容，并坚持 Prediction（而非 Control），尽管本节涵盖的许多概念可以很好地扩展到非线性函数近似和 Control 问题。


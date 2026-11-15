

最小扰动可表述为

$$\epsilon^{(i)} = \min_{\boldsymbol{\delta}} \frac{1}{2} \boldsymbol{\delta}^T \boldsymbol{\delta} \text{ s.t. } \|\boldsymbol{z} + \boldsymbol{\delta} - \boldsymbol{x}_j\|^2 \le \|\boldsymbol{z} + \boldsymbol{\delta} - \boldsymbol{x}_i\|^2 \forall i, y_i = 1. \quad (16.2)$$

需注意，该表述由 (Wang et al., 2019c; Yang et al., 2020f) 提出。(Wang et al., 2019c) 进一步表明，(16.2) 可按如下方式在多项式时间内求解。

表述中的每个约束可重写为

$$\boldsymbol{\delta}^T(\boldsymbol{x}_j - \boldsymbol{x}_i) + \frac{\|\boldsymbol{z} - \boldsymbol{x}_i\|^2 - \|\boldsymbol{z} - \boldsymbol{x}_j\|^2}{2} \ge 0.$$

因此 (16.2) 变为

$$\epsilon^{(i)} = \min_{\boldsymbol{\delta}:\boldsymbol{A}\boldsymbol{\delta}+\boldsymbol{b}\ge 0} \{ \frac{1}{2} \boldsymbol{\delta}^T \boldsymbol{\delta} \} := P^{(i)}(\boldsymbol{\delta}), \quad (16.3)$$

其中，\(\boldsymbol{A} \in \mathbb{R}^{n \times d}\) 且 \(\boldsymbol{b} \in \mathbb{R}^n\)，满足 \(y_i = 1\)，\(\boldsymbol{a}_i = (\boldsymbol{x}_j - \boldsymbol{x}_i)\)，且 \(b_i = \frac{\|\boldsymbol{z} - \boldsymbol{x}_i\|^2 - \|\boldsymbol{z} - \boldsymbol{x}_j\|^2}{2}\)，针对每一行 \(i\)（否则为 \(\mathbf{0}\)）。通过对每个 \(\{ j : y_j \neq 1 \}\) 求解二次规划（QP）问题 (16.3)，最终最小对抗扰动范数为 \(\epsilon^* = \min_{j: y_j \neq 1} \sqrt{2\epsilon^{(j)}}\)。已有研究表明，凸二次规划可在多项式时间内求解 (Kozlov et al., 1980)，因此该表述为寻找 \(\epsilon^*\) 提供了一种 *多项式时间算法*。然而，朴素求解仍然代价过高，因为约束数量会呈二次增长。因此，我们将在下文介绍对偶问题，它们不仅能高效计算 1-NN 模型的鲁棒性，还能为 1-NN 鲁棒性验证提供可验证的鲁棒性下界计算方法。

## 对偶二次规划问题

我们还将介绍每个 QP 的对偶形式，因为它在实践中求解更高效，并将引出一系列针对对抗鲁棒性的验证算法。(16.3) 的对偶问题可写为

$$\max_{\boldsymbol{\lambda} \ge 0} \left\{ -\frac{1}{2} \boldsymbol{\lambda}^T \boldsymbol{A} \boldsymbol{A}^T \boldsymbol{\lambda} - \boldsymbol{\lambda}^T \boldsymbol{b} \right\} := D^{(i)}(\boldsymbol{\lambda}), \quad (16.4)$$

其中，\(\boldsymbol{\lambda} \in \mathbb{R}^{n^+}\) 为对应的对偶变量。这遵循了对偶 QP 问题的标准推导（例如，几乎与支持向量机的原问题和对偶问题相同）。原-对偶关系通过 \(\boldsymbol{\delta} = \boldsymbol{A}^T \boldsymbol{\lambda}\) 将原变量与对偶变量联系起来。基于弱对偶性，

我们有 \( D^{(i)}(\lambda) \le P^{(i)}(\delta) \) 对于任何对偶可行解 \( \lambda \) 和原问题可行解 \( \delta \)。此外，基于 Slater 条件，我们可以证明 (16.3) 满足强对偶性，即 \( D^{(i)}(\lambda^*) = P^{(i)}(\delta^*) \)，其中 \( \lambda^* \) 和 \( \delta^* \) 分别为原问题和对偶问题的最优解，前提是对所有 \( i \in [n'] \) 均有 \( \mathbf{x}_j^- \neq \mathbf{x}_i^+ \)。¹ 基于强对偶性，我们有

\(\frac{1}{2}(\epsilon^*)^2 = \min_{j \in [n']} \{ P^{(i)}(\delta^*) \}\)
\( = \min_{j \in [n']} \{ \max_{\lambda \ge 0} D^{(i)}(\lambda) \}\)
\( \ge \min_{j \in [n']} \{ D^{(i)}(\lambda^{(j)}) \} \text{ with feasible } \lambda^{(j)}, \quad (16.5)\)

因此，一组可行解 \( \{\lambda^{(j)}\}_{j \in [n']} \) 可得出最小对抗扰动的下界。总结，我们得出 1-NN 攻击与验证之间的原-对偶关系如下：

- \( P^{(i)} \) 的任一原问题可行解即为一次成功的攻击，并给出 \( \epsilon^* \) 的一个上界。因此，我们可以求解一部分 QP 并取最小值。通常，与 \( \mathbf{z} \) 更近的 \( \mathbf{x}_j^- \) 会导致更小的对抗扰动，因此在实际中，我们可以按 \( \mathbf{x}_j^- \) 到 \( \mathbf{z} \) 的距离排序，逐个求解子问题，并可随时停止。这将给出一个有效的对抗扰动。求解完所有子问题后，结果将达到最小值，即最小对抗扰动范数 \( \epsilon^* \)。

- 根据 (16.5)，一组对偶可行解 \( \{\lambda^{(i)}\}_{j \in [n']} \) 可得出 \( \epsilon^* \) 的一个下界。因此，任何用于构造一组对偶可行解的启发式方法都将给出一个下界，该下界可用于鲁棒性验证。如果所有对偶问题均精确求解，则可得到最紧（最大）的下界，该下界即为 \( \epsilon^* \)。

## 1-NN 模型的鲁棒性验证

这里，我们举一个例子，说明如何快速设置对偶变量，以在不精确求解任何子问题的情况下，给出最小对抗扰动的一个非平凡下界。对于对偶问题 \( D^{(i)} \)，假设只有一个变量 \( \lambda_i^{(i)} \) 作为优化变量，其余变量全部固定为零；则该简化对偶 QP 问题的最优闭式解为

\(\lambda_i^{(p)} = \max \left( 0, -\frac{b_i}{\|a_i\|^2} \right),\)

\(D^{(p)}([0, \dots, 0, \lambda_i^{(p)}, 0, \dots, 0]) = \frac{\max(-b_i, 0)^2}{2\|a_i\|^2}.\)
(16.6)

由于 \(b_i = (\|z - \mathbf{x}_i^+\|^2 - \|z - \mathbf{x}_j^-\|^2)/2\) 且 \(a_i = \mathbf{x}_j^- - \mathbf{x}_i^+\) 易于计算，我们可利用 (16.5) 通过如下方式获得 \(\epsilon^*\) 的保证下界：

\(\min_{j \in [n]^-} \max_{i \in [n]^+} \frac{\max(\|z - \mathbf{x}_j^-\|^2 - \|z - \mathbf{x}_i^+\|^2, 0)}{2\|\mathbf{x}_j^- - \mathbf{x}_i^+\|}.\)
(16.7)

此外，上述表述中的认证边界具有一个有趣的几何含义。内部值捕获 \(z\) 与 \(\mathbf{x}_i^+\) 和 \(\mathbf{x}_j^-\) 之间垂直平分线的距离。将 \(z\) 扰动到该垂直平分线，是使 \(z\) 更接近 \(\mathbf{x}_j^-\) 而非 \(\mathbf{x}_i^+\) 的最小扰动。若我们希望扰动 \(z\) 使得最近邻为 \(\mathbf{x}_j^-\)，则需要确保 \(z\) 比所有正标签数据点都更接近 \(\mathbf{x}_j^-\)，因此对所有到垂直平分线的距离取最大值。而要使 \(z\) 被分类为负标签，只需使其比正样本更接近某个 \(\mathbf{x}_j^-\)，因此对外部取最小值。一般来说，我们还可以通过对每个子问题优化多个坐标而非单个变量来获得更紧的下界，这可能带来更严格的边界，但可能需要额外计算。

## 计算 1-NN 鲁棒性的高效算法

要计算 1-NN 分类器的精确鲁棒性，需要求解所有原问题 (16.3)，或者等价地，求解相应的对偶问题 (16.4)。尽管它们可在多项式时间内求解，但在实际中，朴素算法仍然太慢，因为涉及 \(O(n)\) 个二次规划问题，且每个问题有 \(O(n)\) 个对偶变量。通常求解每个 QP 需要 \(O(n^2)\) 时间，因此大约需要 \(O(n^3)\) 时间。当 \(n\) 较大时，这代价过高。

为解决此问题，Wang et al. (2019c) 开发了一种高效求解 \(O(n)\) 个子问题的方法。核心思路是利用原-对偶关系去除不必要的变量和不必要的子问题。直觉上，最终解是所有子问题解中的最小值，因此如果我们知道某个子问题解的下界大于当前解，则可以移除该子问题。如前两节所示，基于对偶性，*任何* 对偶解都能给出原问题解的下界，因此当我们发现某个对偶解的目标函数值大于当前最小值时，可以移除该子问题。因此，我们可以同时求解所有子问题并逐步移除子问题。

另一方面，对于每个子问题，我们还可以尝试移除不必要的对偶变量（对应原问题约束）。由于每个约束对应另一个点 \(\mathbf{x}_i\)，我们希望扰动后的点 \((\mathbf{z} + \boldsymbol{\delta})\) 比 \(\mathbf{x}_i\) 更靠近目标点 \(\mathbf{x}_j\)，直觉上，如果该点很远，则可以移除该约束。这也可以通过从原-对偶关系推导出的筛选算法来完成，有兴趣的读者可参阅 (Wang et al., 2019c) 查看更多细节。总的来说，如何高效计算最小对抗扰动仍是一个未解决的问题。

## 超越 1-NN 的扩展

接下来，我们将上述鲁棒性评估方法扩展到 \(K > 1\) 的 \(K\)-NN 模型。考虑二分类情况，令 \(\mathbb{S}^+ = \{\mathbf{x}_1^+, \dots, \mathbf{x}_{n^+}^+\}\) 为与 \(\mathbf{z}\) 标签相同的样本集，\(\mathbb{S}^- = \{\mathbf{x}_1^-, \dots, \mathbf{x}_{n^-}^-\}\) 为与 \(\mathbf{z}\) 标签相反的样本集。我们假设 \(K\) 为奇数以避免 \(K\)-NN 投票出现平局，且 \(n^+\) 和 \(n^-\) 均足够大。我们可以列出所有可能的 \((\mathbb{I}, \mathbb{J})\) 组合，其中 \(\mathbb{I} \subseteq [n^+]\)，\(\mathbb{J} \subseteq [n^-]\)，\(|\mathbb{I}| = (K-1)/2\)，且 \(|\mathbb{J}| = (K+1)/2\)，然后求解以下 QP 问题，以强制 \(\mathbf{z} + \boldsymbol{\delta}\) 比 \(\mathbb{S}^+\) 中除 \(\mathbf{x}_i^+\) 外的所有实例（对所有 \(i \in [\mathbb{I}]\)）更靠近所有 \(j \in [\mathbb{J}]\) 的 \(\mathbf{x}_j^-\)：

```
\epsilon^{(\mathbb{I}, \mathbb{J})} = \min_{\boldsymbol{\delta}} \frac{1}{2} \boldsymbol{\delta}^T \boldsymbol{\delta}
\text{s.t. } \|\mathbf{z} + \boldsymbol{\delta} - \mathbf{x}_j^-\|^2 \le \|\mathbf{z} + \boldsymbol{\delta} - \mathbf{x}_i^+\|^2
\forall i \in [n^+] - \mathbb{I}, \forall j \in \mathbb{J}.
(16.8)
```

然后，最小对抗扰动的范数可通过 \(\epsilon^* = \min_{(\mathbb{I}, \mathbb{J})} \sqrt{2\epsilon^{(\mathbb{I}, \mathbb{J})}}\) 计算得到。总共会有指数数量的 QP，因此通常无法通过遍历所有 QP 来计算最小对抗扰动。然而，我们仍可获得与攻击和验证对应的上界和下界。对于上界（攻击），我们可以只选择少量 \((\mathbb{I}, \mathbb{J})\) 元组并仅求解这些 QP。边界的质量将取决于所选 QP 子集的优劣。




方程 (A.5) 的第二种情况。对于 \( d > 0 \) 的情况，我们构造拉格朗日函数
\[
\mathcal{L} \left( \mathbf{x}, \lambda \right) \triangleq \frac{1}{p} \sum_{i=1}^D |x_i|^p - \lambda \left( \mathbf{x}^\top \mathbf{w} - d \right) .
\]

对 \( \mathbf{x} \) 求偏导并令其等于零，可得
\[
x_i^* = \text{sign}(w_i) \left( \lambda |w_i| \right)^{\frac{1}{p-1}} .
\]

将其代入拉格朗日函数可得
\[
\mathcal{L} \left( \mathbf{x}^*, \lambda \right) = \frac{1-p}{p} \lambda^{\frac{p}{p-1}} \sum_{i=1}^D |w_i|^{\frac{p}{p-1}} + \lambda d ,
\]

我们对 \( \lambda \) 求导并令导数等于零，可得
\[
\lambda^* = \left( \frac{d}{\sum_{i=1}^D |w_i|^{\frac{p}{p-1}}} \right)^{p-1} .
\]

将此解代入 \( \mathbf{x}^* \) 的公式，可得解
\[
x_i^* = \text{sign}(w_i) \left( \frac{d}{\sum_{i=1}^D |w_i|^{\frac{p}{p-1}}} \right) |w_i|^{\frac{1}{p-1}} .
\]

该最优解的 \( \ell_p \) 代价为
\[
A_p \left( \mathbf{x}^* - \mathbf{x}^0 \right) = d \cdot \| \mathbf{w} \|_{\frac{p}{p-1}}^{-1} ,
\]

这是方程 (A.5) 的第一种情况。

对于 \( p = \infty \)，再次如果 \( d \le 0 \)，则零向量 \( \mathbf{0} \) 平凡地满足约束并使代价函数最小化，代价为 0，这给出了方程 (A.6) 的第二种情况。对于 \( d > 0 \) 的情况，我们利用超立方体（\( \ell_\infty \) 代价函数的等代价球）的几何结构来推导方程 (A.6) 的第二种情况。任何最优解都必须出现在 \( \mathbf{x}^\top \mathbf{w} = \mathbf{b}^\top \mathbf{w} \) 给定的超平面与关于 \( \mathbf{x}^0 \) 的超立方体相切的点——这要么发生在超立方体的边（面）上，要么发生在角上。然而，如果平面沿边（面）相切，它也必然在超立方体的一个角上相切。因此，最优代价超立方体的某个角上总存在一个最优解。

超立方体的角具有以下性质：
\[
|x_1^*| = |x_2^*| = \dots = |x_D^*| ;
\]

也就是说，该最优解所有坐标的幅值都相同。此外，最优解第 \( i \) 个坐标的符号必须与超平面第 \( i \) 个坐标 \( w_i \) 的符号一致。结合超平面约束，这些约束推导出以下最优解公式：

\[
x_i = d \cdot \text{sign}(w_i) \| \mathbf{w} \|_1^{-1}
\]

对所有 \( i \) 成立。该解的 \( \ell_\infty \) 代价为 \( d \cdot \| \mathbf{w} \|_1^{-1} \)。

## 附录 B 高球攻击的完整证明

在本附录中，我们给出第 4 章定理的证明。为此，我们引入 \((\tau, k)\)-差分序列的概念，这是一对序列 \(\mathbf{a}, \mathbf{b} \in \mathcal{A}^{(M, \infty)}\)，它们在除 \(\tau^{\text{th}}\)、\(\tau+1^{\text{th}}\)、\(...\)、\(\tau+k^{\text{th}}\) 个连续元素外的所有位置都相同，并具有以下质量平衡性质：

\[
\sum_{i=\tau}^{\tau+k} a_i = \sum_{i=\tau}^{\tau+k} b_i. \tag{B.1}
\]

以下关于 \((\tau, 1)\)-差分序列的引理简化了后续的若干证明。

### 引理 B.1

对于任意 \((\tau, 1)\)-差分序列 \(\mathbf{a}, \mathbf{b} \in \mathcal{A}^{(M, \infty)}\)，它们除了第 \(\tau^{\text{th}}\) 和 \((\tau+1)^{\text{th}}\) 元素外其他元素均相同（根据方程 (B.1) 满足 \(a_\tau + a_{\tau+1} = b_\tau + b_{\tau+1}\)），这些序列之间的距离差 \(\Delta_{\mathbf{a}, \mathbf{b}} \triangleq D(\mathbf{a}) - D(\mathbf{b})\) 可表示为

\[
\Delta_{\mathbf{a}, \mathbf{b}} = \frac{(\mu_{\tau-1}^{(\mathbf{a})} + b_\tau) \cdot a_\tau \cdot a_{\tau+1} - (\mu_{\tau-1}^{(\mathbf{a})} + a_\tau) \cdot b_\tau \cdot b_{\tau+1}}{(\mu_{\tau-1}^{(\mathbf{a})} + a_\tau) \left(\mu_{\tau-1}^{(\mathbf{a})} + b_\tau\right) \left(\mu_{\tau-1}^{(\mathbf{a})} + a_\tau + a_{\tau+1}\right)} \tag{B.2}
\]

其中 \(\mu_t^{(\mathbf{a})} = N + \sum_{\ell=1}^t a_\ell\) 是序列 \(\mathbf{a}\) 前 \(t\) 个元素的累积和，如方程 (4.7) 所示。只要 \(\mu_{\tau-1}^{(\mathbf{a})} > 0\) 或 \(a_\tau > 0\) 与 \(b_\tau > 0\) 同时成立，此结果即成立。

证明 首先，对于 \(t < \tau\)，有 \(\mu_t^{(\mathbf{a})} = \mu_t^{(\mathbf{b})}\)，因为两个序列在第 \(\tau^{\text{th}}\) 元素之前完全相同。类似地，对于 \(t > \tau + 1\)，我们同样有 \(\mu_t^{(\mathbf{a})} = \mu_t^{(\mathbf{b})}\)，因为序列仅在第 \(\tau^{\text{th}}\) 和 \((\tau+1)^{\text{th}}\) 元素上不同，且根据方程 (B.1) 它们具有质量平衡性，其中我们定义 \(\gamma \triangleq a_\tau + a_{\tau+1} = b_\tau + b_{\tau+1}\) 为这些序列的平衡常数。利用这两个事实，并根据方程 (4.12) 有 \(\delta_t(\mathbf{a}) = \frac{a_t}{\mu_t^{(\mathbf{a})}}\)，可知若 \(t < \tau\) 或 \(t > \tau + 1\)，则 \(\delta_t(\mathbf{a}) = \delta_t(\mathbf{b})\)。因此，这两个序列所达到的距离差可根据方程 (4.11) 表示为

\[
\Delta_{\mathbf{a}, \mathbf{b}} = \sum_{t=1} [\delta_t (\mathbf{a}) - \delta_t (\mathbf{b})]
\]
\[
= \sum_{t=1}^{\tau-1} [\delta_t (\mathbf{a}) - \delta_t (\mathbf{b})] + \delta_\tau (\mathbf{a}) - \delta_\tau (\mathbf{b}) + \delta_{\tau+1} (\mathbf{a}) - \delta_{\tau+1} (\mathbf{b})
\]
\[
\underbrace{= 0}
\]
\[
+ \sum_{t=\tau+2} [\delta_t (\mathbf{a}) - \delta_t (\mathbf{b})]
\]
\[
\underbrace{= 0}
\]
\[
= \frac{a_\tau}{\mu_{\tau-1}^{(\mathbf{a})}} - \frac{b_\tau}{\mu_\tau^{(\mathbf{b})}} + \frac{a_{\tau+1}}{\mu_{\tau+1}^{(\mathbf{a})}} - \frac{b_{\tau+1}}{\mu_{\tau+1}^{(\mathbf{b})}}
\]
\[
= \frac{a_\tau}{\mu_{\tau-1}^{(\mathbf{a})} + a_\tau} - \frac{b_\tau}{\mu_{\tau-1}^{(\mathbf{a})} + b_\tau} + \frac{a_{\tau+1}}{\mu_{\tau-1}^{(\mathbf{a})} + \gamma} - \frac{b_{\tau+1}}{\mu_{\tau-1}^{(\mathbf{a})} + \gamma}.
\]

要合并这四项，我们可以得到一个公共分母 \(\Gamma = \left( \mu_{\tau-1}^{(\mathbf{a})} + a_\tau \right) \left( \mu_{\tau-1}^{(\mathbf{a})} + b_\tau \right) \left( \mu_{\tau+1}^{(\mathbf{a})} + \gamma \right)\)，其合并后的分子由以下给出

\[
\left[ a_\tau \left( \mu_{\tau-1}^{(\mathbf{a})} + b_\tau \right) - b_\tau \left( \mu_{\tau-1}^{(\mathbf{a})} + a_\tau \right) \right] \left( \mu_{\tau-1}^{(\mathbf{a})} + \gamma \right)
\]
\[
+ \left( a_{\tau+1} - b_{\tau+1} \right) \left( \mu_{\tau-1}^{(\mathbf{a})} + a_\tau \right) \left( \mu_{\tau-1}^{(\mathbf{a})} + b_\tau \right)
\]
\[
= \mu_{\tau-1}^{(\mathbf{a})} a_\tau a_{\tau+1} - \mu_{\tau-1}^{(\mathbf{a})} b_\tau b_{\tau+1} + b_\tau a_\tau a_{\tau+1} - a_\tau b_\tau b_{\tau+1}
\]
\[
= \left( \mu_{\tau-1}^{(\mathbf{a})} + b_\tau \right) \cdot a_\tau \cdot a_{\tau+1} - \left( \mu_{\tau-1}^{(\mathbf{a})} + a_\tau \right) \cdot b_\tau \cdot b_{\tau+1},
\]

在此过程中，我们利用 \(\gamma\) 的定义消去了某些项。将此分子与分母 \(\Gamma\) 合并，得到方程 (B.2)。最后，\(\mu_{\tau-1}^{(\mathbf{a})} > 0\) 或 \(a_\tau > 0\) 与 \(b_\tau > 0\) 同时成立的条件是必要的，以防止分母变为零。

### B.1 定理 4.7 的证明

在这里，我们表明根据方程 (4.5) 的最优攻击可以以贪婪的方式进行优化。此外，我们表明最优攻击点都位于超球边界与所需攻击方向的交点处。

_证明_ 考虑攻击的第 \(t^\text{th}\) 次迭代，对任意 \(t \in \mathfrak{N}\)。攻击者在第 \(t^\text{th}\) 次迭代中的目标是最大化方程 (4.5) 给出的位移对齐度。攻击者通过构造一组 \(\alpha_t \in \mathfrak{N}\) 个攻击点来实现此目标：\(\mathbb{A}^{(t)} = \{ \mathbf{a}^{(t, \ell)} \}_{\ell=1}^{\alpha_t}\)。这些点旨在最大化 \(\mathbf{D}_t^\top \frac{\mathbf{x}^t - \mathbf{c}^{(0)}}{\| \mathbf{x}^t - \mathbf{c}^{(0)} \|}\)，其中根据方程 (4.4) 有 \(\mathbf{D}_t = \frac{\mathbf{c}^{(t)} - \mathbf{c}^{(0)}}{R}\)，\(\mathbf{c}^{(t)}\) 由方程 (4.8) 递归定义，且每个攻击向量被限制在第 \((t-1)^\text{th}\) 个超球内；即，对所有 \(\ell = 1, \dots, \alpha_t\)，有 \(\| \mathbf{a}^{(t, \ell)} - \mathbf{c}^{(t-1)} \| \le R\)。攻击者的目标可以在不损失一般性的情况下进行修改


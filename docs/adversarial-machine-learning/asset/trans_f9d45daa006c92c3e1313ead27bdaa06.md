

第二项也不会增加，如预期。² 事实上，通过将分数 \( I(\cdot) \)、\( S(\cdot) \) 和 \( H(\cdot) \) 重新定义为基于简单乘积 \( \tilde{s}_{\mathbf{q}}(\hat{\mathbf{x}}) \) 和 \( \tilde{h}_{\mathbf{q}}(\hat{\mathbf{x}}) \)（我们分别将其称为 \( \tilde{I}(\cdot) \)、\( \tilde{S}(\cdot) \) 和 \( \tilde{H}(\cdot) \)），以下引理表明 \( \tilde{I}(\cdot) \) 关于 \( q_i \) 是非递减的。

## 引理 C.2 修改后的 \( \tilde{I}(\mathbf{x}) \) 分数对于所有标记（索引为 \( i \)）关于 \( q_i \) 是非递减的。

**证明** 我们表明 \( \tilde{I}(\hat{\mathbf{x}}) \) 关于 \( q_k \) 的导数对于所有 \( k \) 都是非负的。通过用 \( \tilde{s}_{\mathbf{q}}(\hat{\mathbf{x}}) \) 重写方程 (5.3) 为 \( \tilde{S}(\hat{\mathbf{x}}) = 1 - \chi_{2n}^2 (-2 \log (\tilde{s}_{\mathbf{q}}(\hat{\mathbf{x}}))) \)，可以按如下应用链式法则：

$$
\frac{\partial}{\partial q_k} \tilde{S}(\hat{\mathbf{x}}) = \frac{d}{d\tilde{s}_{\mathbf{q}}(\hat{\mathbf{x}})} \left[ 1 - \chi_{2n}^2 (-2 \log (\tilde{s}_{\mathbf{q}}(\hat{\mathbf{x}}))) \right] \cdot \frac{\partial}{\partial q_k} \tilde{s}_{\mathbf{q}}(\hat{\mathbf{x}})
$$

$$
\frac{d}{d\tilde{s}_{\mathbf{q}}(\hat{\mathbf{x}})} \left[ 1 - \chi_{2n}^2 (-2 \log (\tilde{s}_{\mathbf{q}}(\hat{\mathbf{x}}))) \right] = \frac{1}{(n-1)!} \left( - \log (\tilde{s}_{\mathbf{q}}(\hat{\mathbf{x}})) \right)^{n-1}.
$$

该导数是非负的，因为 \( 0 \le \tilde{s}_{\mathbf{q}}(\hat{\mathbf{x}}) \le 1 \)。此外，\( \tilde{s}_{\mathbf{q}}(\hat{\mathbf{x}}) \) 关于 \( q_k \) 的偏导数仅为 \( \frac{\partial}{\partial q_k} \tilde{s}_{\mathbf{q}}(\hat{\mathbf{x}}) = \prod_{i \neq k: \tilde{x}_i = 1} q_i \ge 0 \)。因此，对于所有 \( k \)，

$$
\frac{\partial}{\partial q_k} \tilde{S}(\hat{\mathbf{x}}) \ge 0.
$$

通过类似的推导，将 \( q_i \) 替换为 \( 1 - q_i \)，

$$
\frac{\partial}{\partial q_k} \tilde{H}(\hat{\mathbf{x}}) \le 0.
$$

最终结果由以下给出

$$
\frac{\partial}{\partial q_k} \tilde{I}(\hat{\mathbf{x}}) = \frac{1}{2} \frac{\partial}{\partial q_k} \tilde{S}(\hat{\mathbf{x}}) - \frac{1}{2} \frac{\partial}{\partial q_k} \tilde{H}(\hat{\mathbf{x}}) \ge 0.
$$

然而，与简单乘积不同，统计量 \( s_{\mathbf{q}}(\cdot) \) 和 \( h_{\mathbf{q}}(\cdot) \) 具有不寻常的行为，因为函数 \( \delta(\cdot) \) 对标记分数进行净化。具体来说，\( \delta(\cdot) \) 是集合 \( \mathbb{T}_{\mathbf{x}} \) 的指示函数。该集合的成员资格由标记分数与不可知分数 \( \frac{1}{2} \) 的绝对距离决定，即由值 \( g_i \triangleq |q_i - \frac{1}{2}| \) 决定。第 \( i^\text{th} \) 个标记属于 \( \mathbb{T}_{\mathbf{x}} \)，如果 \( i) \) \( \tilde{x}_i = 1 \) \( ii) \) \( g_i \ge Q \)（默认 \( Q = 0.1 \)，因此所有在 \( (0.4, 0.6) \) 中的标记都被排除）和 \( iii) \) 在剩余标记中，该标记拥有 \( g_i \) 的最大 \( T \) 值之一（默认 \( T = 150 \)）。

就我们的目的而言，对于每条消息 \( \hat{\mathbf{x}} \)，都存在某个值 \( \tau_{\mathbf{x}} < \frac{1}{2} \)，它定义了一个区间 \( (\frac{1}{2} - \tau_{\mathbf{x}}, \frac{1}{2} + \tau_{\mathbf{x}}) \) 以排除标记。即

$$
\delta(\hat{\mathbf{x}})_i = \tilde{x}_i \cdot \begin{cases} 0 & \text{if } q_i \in (\frac{1}{2} - \tau_{\mathbf{x}}, \frac{1}{2} + \tau_{\mathbf{x}}) \\ 1 & \text{otherwise} \end{cases}.
$$

² 这些统计量在另一意义上也表现得很奇怪。具体来说，添加一个额外的标记将始终减少两个乘积，而删除一个标记将始终增加两个乘积。应用卡方分布可以纠正这种效果。

### 增加 1 个标记时 $I(\cdot)$ 分数的变化

![](img/0637c4902205011abc4f185025bd5607_297_0.png)

### 增加 3 个标记时 $I(\cdot)$ 分数的变化

![](img/0637c4902205011abc4f185025bd5607_297_1.png)

### 增加 5 个标记时 $I(\cdot)$ 分数的变化

![](img/0637c4902205011abc4f185025bd5607_297_2.png)

图 C.2. 随第 \( i^\text{th} \) 个标记的分数 \( q_i \) 增加，导致 \( q_i \) 移入或移出所有标记均被忽略的区域 (0.4, 0.6)，\(\delta( \cdot )\) 函数对 \( I( \cdot ) \) 的影响。在每个图中，x 轴是移除前的 \( q_i \) 值，y 轴是因移除而导致的 \( I( \cdot ) \) 变化；请注意，y 轴上的比例从上到下减小。对于最上方一行图，除变化的标记外还有 1 个不变的标记分数；对于中间一行，还有 3 个额外的不变标记分数；对于底部一行，还有 5 个额外的不变标记分数。最左侧一列的图展示了在最初 \( q_i \in (0, 0.4) \) 时移除第 \( i^\text{th} \) 个标记的效果；额外不变标记的分数全部固定为相同的值 0.02（深色虚线黑色）、0.04、0.06、0.08、0.10 或 0.12（浅色虚线黑色）。最右侧一列的图展示了在最初 \( q_i \in (0.4, 0.6) \) 时添加第 \( i^\text{th} \) 个标记的效果；额外不变标记的分数全部固定为相同的值 0.88（深灰色）、0.90、0.92、0.94、0.96 或 0.98（浅灰色）。

显然，对于 \hat{x} 中的标记，随着 \( q_i \) 增加，\(\delta (\hat{x})_i\) 从 1 跳变为 0 然后又回到 1。这导致 \( s_q (\hat{x}) \) 相对于 \( q_i \) 有两处不连续点：它在区间 \([0, \frac{1}{2} - \tau_x]\) 和 \([\frac{1}{2} + \tau_x, 1]\) 上线性增加，但在中间区间 \((\frac{1}{2} - \tau_x, \frac{1}{2} + \tau_x)\) 上会不连续地跳变到其最大值。这种行为在图 C.1 中有所描绘。同样，\( h_q (\hat{x}) \) 也呈线性递减，但在中间区间 \((\frac{1}{2} - \tau_x, \frac{1}{2} + \tau_x)\) 上也会跳变到其最大值。因此，\( s_q (\hat{x}) \) 和 \( h_q (\hat{x}) \) 在区间 \([0, 1]\) 上均不具有单调性。

为了更好地理解 \( I (\hat{x}) \) 在 \( q_i \) 增加时的行为，鉴于 \( s_q (\hat{x}) \) 和 \( h_q (\hat{x}) \) 均不具备单调性，我们对其行为进行逐案分析。为此，我们将三个区间 \([0, \frac{1}{2} - \tau_x]\)、\((\frac{1}{2} - \tau_x, \frac{1}{2} + \tau_x)\) 和 \([\frac{1}{2} + \tau_x, 1]\) 分别称为 A、B 和 C。显然，如果 \( q_i \) 增加但保持在同一区间内，\( I (\hat{x}) \) 也会增加。这源自引理 C.2 以及如果 \( q_i \) 保持在 B 区间内 \( I (\hat{x}) \) 不会改变的事实。同样，如果 \( q_i \) 从 A 区间增加到 C 区间，\( I (\hat{x}) \) 也会增加；这也源自引理 C.2。\( I (\hat{x}) \) 在 \( q_i \) 增加时可能减少的唯一情况是 \( q_i \) 从 A 区间过渡到 B 区间，或从 B 区间过渡到 C 区间，但在这些情况下，\( I (\hat{x}) \) 的行为在很大程度上取决于 \hat{x} 中其他标记的分数以及 \( q_i \) 增加前的值，如图 C.2 所示。还值得注意的是，如果 \hat{x} 具有超过 150 个位于区间 (0.4, 0.6) 外的标记，则 \( I (\hat{x}) \) 实际上永远不会减少，因为在这种情况下，将 \( q_i \) 增加到 B 区间内或外也对应于添加或移除第二个标记分数 \( q_j \)。在这种情况下，效果是 \( I (\hat{x}) \) 始终增加。

我们在第 5.3 节中介绍的针对 SpamBayes 的攻击忽略了这样一个事实：增加某些标记分数时，\( I (\hat{x}) \) 可能会减少。就此而言，这些攻击并非真正最优。然而，确定哪一组标记能最优地增加一组未来消息 { \hat{x} } 的整体 \( I ( \cdot ) \) 是一个组合问题，对于现实世界中的攻击者来说似乎不可行。相反，我们考虑针对问题的放宽版本的最优攻击，该版本在计算 \( I (\hat{x}) \) 时包含 \hat{x} 中的所有标记。此外，在第 5.5 节中，我们表明这些近似技术对 SpamBayes 具有非凡的有效性，尽管攻击消息中包含了一些非最优标记。


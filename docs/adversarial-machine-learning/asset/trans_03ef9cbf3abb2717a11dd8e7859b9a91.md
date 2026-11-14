
因此，\( D_N^*(M, \infty) \)，即空间 \( \mathcal{A}^{(M,\infty)} \) 中任何序列可实现的最优距离，用问题的参数 \( M \) 和 \( N \) 来表达；也就是说，如果 \( \boldsymbol{\alpha}^* \) 是 \( \mathcal{A}^{(M,\infty)} \) 中的最优策略，则 \( D(\boldsymbol{\alpha}^*) = D_N^*(M, \infty) \)。类似地，对于受限于有限持续时间 \( T \) 的攻击，在序列空间 \( \mathcal{A}^{(M,T)} \) 中，我们将可实现的最优距离定义为 \( D_N^* (M, T) \)，我们将在 4.4 节中再次讨论。

## 4.2.3 攻击序列的特性

为了更好地理解我们的问题，我们表征其属性以及（最优）攻击序列的属性。这些属性为问题的进一步分析奠定了基础。

### 4.2.3.1 对空攻击迭代的不变性

我们讨论来自公式 4.11 的攻击距离 \( D(\boldsymbol{\cdot}) \) 相对于攻击序列中零元素的行为。首先，我们表明攻击距离 \( D(\boldsymbol{\cdot}) \) 对于在序列的第 \( k^\text{th} \) 位置插入零具有不变性（其中 \( k > 1 \) 遵循备注 4.9）。

**LEMMA 4.11** 对于任何 \( k > 1 \)，每个序列 \( \boldsymbol{\alpha} \in \mathcal{A}^{(M,\infty)} \) 达到的距离与序列 \( \boldsymbol{\alpha}' \) 相同，该序列定义为

```
\(\alpha'_t = \begin{cases} \alpha_t, & \text{if } t < k \\ 0, & \text{if } t = k \\ \alpha_{t-1}, & \text{if } t > k \end{cases}\)
```

即，\( D(\boldsymbol{\alpha}) = D(\boldsymbol{\alpha}') \)。

证明。首先，对于 \( t < k \)，\( \delta_t(\boldsymbol{\alpha}') = \delta_t(\boldsymbol{\alpha}) \)，因为 \( \delta_t(\boldsymbol{\cdot}) \) 仅取决于序列的前 \( t \) 个元素（参见公式 4.12）。其次，由公式 (4.12) 可得 \( \delta_k(\boldsymbol{\alpha}') = 0 \)。第三，对于 \( t > k \)，\( \delta_t(\boldsymbol{\alpha}') = \delta_{t-1}(\boldsymbol{\alpha}) \)，因为在 \( k^\text{th} \) 位置插入 0 不会影响 \( \delta_t(\boldsymbol{\cdot}) \) 定义中的分母 \( \mu_t \)（参见公式 (4.7) 和 (4.12)），分子相应地移位。序列 \( \boldsymbol{\alpha}' \) 达到的距离为

```
\(\begin{aligned} D(\boldsymbol{\alpha}') &= \sum_{t=1}^{k-1} \delta_t(\boldsymbol{\alpha}') + \delta_k(\boldsymbol{\alpha}') + \sum_{t=k+1} \delta_t(\boldsymbol{\alpha}') \\ &= \sum_{t=1}^{k-1} \delta_t(\boldsymbol{\alpha}) + \sum_{t=k+1} \delta_{t-1}(\boldsymbol{\alpha}) = D(\boldsymbol{\alpha}) . \end{aligned}\)
```

由此引理可知，零元素（\( \alpha_t = 0 \)）的插入（或删除）与序列的距离无关，因此在考虑我们的最优性概念时可以删除所有零。直觉上，攻击所达到的距离不受未使用对抗性数据的重新训练迭代的影响，因为在这种情况下，对抗性数据是新数据的唯一来源。以下定理捕获了这一概念：

**THEOREM 4.12** 每对序列 \(\boldsymbol{\alpha}, \boldsymbol{\alpha}' \in \mathcal{A}^{(M, \infty)}\)，如果具有相同的非零元素子序列——即，\(\left(\alpha_i \mid \alpha_i > 0\right) = \left(\alpha'_i \mid \alpha'_i > 0\right)\)——则达到相同的距离：\(D\left(\boldsymbol{\alpha}\right) = D\left(\boldsymbol{\alpha}'\right)\)；也就是说，序列达到的距离与序列中零元素的数量及其位置无关。\(D\left(\boldsymbol{\alpha}\right)\) 仅取决于 \(\boldsymbol{\alpha}\) 的非零元素子序列。作为结果，任何有限序列都可以重新排序为其正子序列后跟全零子序列，两者达到相同的距离。

证明。由于序列 \(\boldsymbol{\alpha}\) 和 \(\boldsymbol{\alpha}'\) 包含相同顺序的相同非零元素，可以通过重复应用引理 4.11 在序列的必要位置插入和删除零来将 \(\boldsymbol{\alpha}\) 转换为 \(\boldsymbol{\alpha}'\)。因此，\(\boldsymbol{\alpha}\)、\(\boldsymbol{\alpha}'\) 以及此转换中使用的所有中间序列都具有相同的距离。

由此可见，零元素可以任意插入或删除到任何最优攻击序列中，以形成具有相同距离的等效最优攻击序列，因为零元素既不增加距离，也不为后续分母增加“权重”。定理 4.12 允许我们忽略序列中的所有零元素，因为它们不贡献于攻击的有效性。此外，将所有零元素移到序列末尾对应于攻击者希望最小化攻击所需时间的概念，因为延长攻击对我们的攻击者没有好处。最后，零元素可以被忽略这一事实表明重新定义 \(\alpha_t \in \mathfrak{R}\) 而非 \(\mathfrak{N}_0\) 的可能性。

### 4.2.3.2 最优攻击序列的特性

既然已表明零元素与我们的分析无关，我们现在描述最优攻击中非零元素的属性。首先，在此攻击公式中，没有初始点支撑超球面，因此无论攻击者在第一次迭代中放置多少点，都会达到相同的位移。以下引理捕获了这一点：

**LEMMA 4.13** 对于 \(N=0\)，最优初始攻击迭代由 \(\alpha_1^* = 1\) 给出。

证明。第一次攻击迭代的贡献由 \(\delta_1 \left(\boldsymbol{\alpha}\right) = \frac{\alpha_1}{\mu_1} = \frac{\alpha_1}{\alpha_1} = 1\) 给出。因此，对于 \(\alpha_1 \in \mathfrak{N}\)（根据备注 4.9，我们排除 \(\alpha_1 = 0\) 的可能性），我们有 \(\delta_1 \left(\boldsymbol{\alpha}\right) = 1\)，并且由于 \(\delta_t \left(\boldsymbol{\alpha}\right) = \frac{\alpha_t}{\alpha_1 + \sum_{i=2}^{t} \alpha_i}\) 对于 \(t > 1\) 在 \(\alpha_1\) 中是严格递减的，因此此次迭代的最优整数解为 \(\alpha_1^* = 1\)。

此外，如果总攻击能力大于一个攻击点，且攻击者有能力将其攻击分布在多个重新训练迭代中，那么这样做是有益的；也就是说，将所有攻击点集中在单个攻击迭代中的攻击是非最优的。附录 B.3 中提供的引理 B.2 捕获了这一点。

此外，备注 4.5 中的累积惩罚收益概念至关重要。这里有两种 *力量* 在起作用。一方面，在迭代 \(t\) 期间放置许多点（大 \(\alpha_t\)）会改善术语 \(\delta_t \left(\boldsymbol{\alpha}\right)\) 对整体距离 \(D \left(\boldsymbol{\alpha}\right)\) 的贡献。另一方面，大 \(\alpha_t\) 将对后续术语不利，因为它会增加后续贡献 \(\delta_\tau \left( \boldsymbol{\alpha} \right)\)（对于 \(\tau > t\)）中分母 \(\mu_\tau\) 的大小。这种效应可以类比为随着利用的点越来越多，点的平均值变得更重（更难移动）。直觉上，人们不希望过快地放置太多权重，因为这会导致攻击后期平均值变得太重，从而使后续努力效果较差。这表明任何最优攻击序列都应该是单调非递减的，我们将在以下定理中证明：

**THEOREM 4.14** 对于任何最优攻击点序列 \(\boldsymbol{\alpha}^* \in \mathcal{A}^{(M, \infty)}\)，\(\boldsymbol{\alpha}^*\) 的每个非零元素子序列都必须是单调非递减的；也就是说，如果 \(\mathbb{I}^{(nz)} = \{i_1, i_2, ... \mid \forall k \ \alpha_{i_k}^* > 0\}\) 是对应于 \(\boldsymbol{\alpha}^*\) 非零元素的索引集合，那么对于所有 \(i, j \in \mathbb{I}^{(nz)}\)，\(i \le j \Leftrightarrow \alpha_i^* \le \alpha_j^*\)。

*证明。* 证明出现在附录 B.2。

注意，定理 4.14 不要求严格单调性，这使其与定理 4.12 保持一致。

尽管已表明任何最优攻击序列在幅度上都应是单调非递减的，但随着利用的点越来越多平均值变得更重的直觉暗示了不仅仅是单调性。事实上，这一概念将引导我们在 4.3.1 节中得到一个最优解。

### 4.2.3.3 最优攻击距离的行为

尽管描述最优攻击可能很困难，但我们通常可以将最优位移对齐（在所有可能攻击中）作为 \(M\) 和 \( T\) 的函数来描述。特别是，我们预期随着攻击者可用的攻击点数量 \(M\) 增加，得到的最优位移对齐应该增加。类似地，随着攻击持续时间 \(T\) 增加，我们也预期得到的最优位移对齐会增加。以下定理表明，对于任何固定的 \(N \ge 0\)，函数 \(D_N^* (M, T)\) 实际上确实随着 \(M\) 和 \(T\) 的两者单调增加。

**THEOREM 4.15** 对于所有 \(N \in \mathfrak{N}_0\)，函数 \(D_N^* (M, \infty)\) 和 \(D_N^* (M, T)\)（对于任何固定的 \(T > 0\)）相对于 \(M \in \mathfrak{N}_0\) 都是严格单调递增的，除非 \(N = 0\) 且 \(T = 1\)，在这种情况下 \(D_0^* (M, 1) = 1\) 对于所有 \(M \in \mathfrak{N}_0\) 成立。此外，对于任何固定的 \(M > 0\)，函数 \(D_N^* (M, T)\) 相对于 \(T \le M\) 是严格单调递增的，并且对于 \(T > M\) 是常数；即，对于任何 \(T \ge M\)，\(D_N^* (M, T) = D_N^* (M, \infty)\)。

*证明。* 证明出现在附录 B.3。

注意，相对于 \(T\)，函数 \(D_N^* (M, T)\) 在 \(T \ge M\) 时是常数，因为攻击者必须在每个有益的重新训练迭代中至少使用一个攻击点（参见 4.2.3.1 节）。攻击者从持续时间超过 \(M\) 的攻击中不会获得额外收益。

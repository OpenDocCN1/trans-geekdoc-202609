
## 2.3 方法

- $\tilde{x} \in \arg \max_{x \in H_{\tilde{s}}} ||x - \tilde{s}||$:
- \(\Longrightarrow dist_{\tilde{s}} = ||\tilde{x} - \tilde{s}||\)
- \(\Longrightarrow dist_{\tilde{s}} < dist_{s^*}\)
- \(\Longrightarrow \tilde{s} \notin \arg \max_{s \in S} dist_s\)
- \(\Longrightarrow x \notin \tilde{B}_{new}\)

- $\tilde{x} \notin \arg \max_{x \in H_{\tilde{s}}} ||x - \tilde{s}||$: 这显然违反了成为 \(B_{new}\) 元素的条件。但是，$\tilde{x}$ 可能与 \(S\) 中不止一个元素最近。因此，我们假设 $\tilde{x}$ 也与 S 中的 \(s'\) 最近，且 $\tilde{x} \in \arg \max_{x \in H'_{s'}} ||x - s'||$。但此时我们可以再次应用第一种情况，将 \(s'\) 代替 $\tilde{s}$，从而得到 $\tilde{x} \notin B_{new}$。

在两种情况下，我们都得到 $\tilde{x} \notin B_{old} \Longrightarrow \tilde{x} \notin B_{new}$，这意味着 \(B_{new} \subseteq B_{old}\)。

其次，我们证明 \(B_{old} \subseteq B_{new}$：假设 \(x \notin B_{new}$，且 $\tilde{x}$ 是 \(S$ 中最接近 $\tilde{s}$ 的点。同样可以区分两种情况：

- $\tilde{x} \notin \arg \max_{x \in H_{\tilde{s}}} ||x - \tilde{s}||$:
- 那么一定存在 \(x' \in H_{\tilde{s}}$，使得 \(||x' - \tilde{s}|| > ||\tilde{x} - \tilde{s}||$。
- \(\Longrightarrow d'_{x'}^{in} > d_{\tilde{x}}^{in} \Longrightarrow \tilde{x} \notin \arg \max_{x \in \mathcal{X} \setminus S} d_x^{in} \Longrightarrow \tilde{x} \notin B_{old}\)

- $\tilde{x} \in \arg \max_{x \in H_{\tilde{s}}} ||x - \tilde{s}||$, but $\tilde{s} \notin \arg \max_{s \in S} dist_s$:
- 存在一个 \(s^* \in \arg \max_{s \in S} dist_s$ 及其对应的 \(x^* \in \arg \max_{x \in H_{s^*}} ||x - s^*||$。
- 显然，我们有 \(dist_{\tilde{s}} < dist_{s^*}$。
- \(\Longrightarrow ||\tilde{x} - \tilde{s}|| < ||x^* - s^*|| \Longrightarrow d_{\tilde{x}}^{in} < d_{x^*}^{in} \Longrightarrow \tilde{x} \notin B_{old}\)

这表明 \(B_{old}$ 是 \(B_{new}$ 的子集。结合 \(B_{new} \subseteq B_{old}$，我们可以推导出 \(B_{new} = B_{old}$。

正如本节开头所述，\(B_{new}$ 无法在多项式时间内计算。问题在于约束 \(x \in H_{s^*}$，它要求 \(\mathcal{H}_{S^*}\) 必须已知。构建这个集合需要为每个 \(x \in \mathcal{X} \setminus S$ 计算其到集合 \(S$ 的距离，以便判断 \(x$ 是否最接近 \(s^*$。由于集合 \(\mathcal{X} \setminus S$ 的大小是指数级的，推导 \(H_{s^*}\) 需要指数时间。

### 使用 ILP 的实现

我们现在介绍一种更高效地计算 (2.8) 的方法。思路是为每个已查询的束 \(s \in S$ 找到一个 \(x^* \in \arg \max_{x \in H_s} \|x - s\|$，而无需构建 \(H_s$。这可以通过为所有 \(s \in S$ 求解以下小型优化问题来实现：

\[
\arg \max_{x \in \mathcal{X}} \|x - s\| \quad (\mathcal{X} = \{0, 1\}^m)
\]
\[
\text{s.t.} \quad \|x - s\| \le \|x - s'\| \quad \forall s' \in S, s' \neq s \quad (2.9)
\]

在这种形式下，优化问题 (2.9) 由于范数而为非线性，无法由 ILP 求解器求解。因此，我们将其重新表述为一个整数线性规划（ILP）。

\[
\arg \max_{x \in \mathcal{X}} \sum_{j=1}^m x_j + s_j - 2x_js_j
\]
\[
\text{s.t.} \quad \forall s' \in S, s' \neq s
\]
\[
\sum_{j=1}^m x_j + s_j - 2x_js_j \le \sum_{j=1}^m x_j + s'_j - 2x_js'_j
\]
\[
x, s, s' \in \{0, 1\}^m \quad (2.10)
\]

以下引理将有助于证明 ILP (2.10) 与优化问题 (2.9) 在定理 2.8 中的等价性。

### 引理 2.7。

令 \(x, y \in \mathcal{X} = \{0, 1\}^m$ 为两个大小为 \(m$ 的束。则，\(\|x - y\|^2 = \sum_{j=1}^m x_j + y_j - 2x_jy_j$。

### 引理 2.7 的证明。

\[
\|x - y\|^2 = \sum_{j=1}^m (x_j - y_j)^2
\]
\[
= \sum_{j=1}^m x_j^2 + y_j^2 - 2x_jy_j
\]
\[
= \sum_{j=1}^m x_j + y_j - 2x_jy_j \quad (\text{since } 0^2 = 0 \text{ and } 1^2 = 1)
\]

### 定理 2.8. 整数线性规划 (2.10) 与优化问题 (2.9) 等价。

### 定理 2.8 的证明。

由于一般平方函数 \(f(a) = a^2$ 是强单调的，可以对 (2.9) 中的所有范数取平方，同时保持等价性。接下来，利用引理 2.7 的结果，所有平方范数 \(\|x - s\|^2 \forall s \in S$ 都可以替换为求和式 \(\sum_{j=1}^m x_j + s_j - 2x_j s_j$，从而得到 ILP (2.10)。

对于现有的束 \(s \in S$，\(x^* \in \arg \max_{x \in H_s} \|x - s\|\) 可以通过求解所提出的 ILP (2.10) 来计算。为了找到下一个要查询的样本，需要为每个束 \(s \in S$ 求解 ILP。然后用 ILP 得到的束来计算其对应的束 \(s$ 的最大距离 \(dist_s$。在所有计算出的束中，选择由 \(dist_s$ 最大的束 \(s \in S$ 对应的 ILP 找到的束作为我们的下一个样本。需要注意的是，并非对所有 \(s \in S$ 都存在束 \(x^*$，特别是当 \(S$ 较大时，这会导致 ILP 无可行解。这个三维束空间的简单场景，其中 \(S = \{(1, 0, 0), (0, 1, 0), (0, 0, 1), (0, 0, 1), (0, 0, 0)\}$，说明了这种情况。在这个场景中，没有任何剩余的束比对 \(S$ 中任何其他束更接近或同样接近 \((0, 0, 0)$，因此 ILP 无可行解。然而这并不是问题，因为 \(\arg \max_{x \in H_{(0,0,0)}} \|x - (0,0,0)\|$ 同样为空。为了为 GALI 采样一个新束，将选择另一个具有非空 \(H'_s$ 的 \(s'$。

算法 2.9 展示了如何利用 ILP (5) 高效生成 ICAs 中对投标人进行询问的初始束集。它以初始出价数量 \(c_0$ 和物品数量 \(m$ 作为输入，并为每个投标人生成带有对应估值 \(Y$ 的束集 \(S$。需要注意的是，对于这种采样技术，\(S$ 中束的出价并非决定下一个样本所必需。因此，可以要求投标人一次性提交所有出价，而不是每次迭代都进行查询。出于此原因，这种采样策略也被称为 *被动采样*。根据文献 [205] 的结果，GALI 在物品数量方面表现出准多项式运行时间，因为所有可能解都在 \(\{0, 1\}^n$ 中，且约束系数向量的主导系数由物品数量所界限。

### 算法 2.9 基于 GALI 生成初始出价

```
Input: c0, m
Y <- \emptyset
S <- u.a.r. x \in X = {0, 1}^m
ask bidder to submit value for bundle x, add value to Y
count <- 1
while count <= c0 do
  for each s in S do
    compute x_s in arg max_{x in H_s} ||x - s|| using the ILP (2.10)
    dists <- ||x_s - s||
  end for
  choose s* in arg max_{s in S} dists_s
  S <- S U {x_s*}
  ask bidder to submit value for bundle x_s*, add value to Y
  count <- count + 1
end while
Output: (S, Y)
```

### 2.3.2 基于输出值的贪婪主动学习 (GALO)

与 GALI 类似，GALO 中也存在指数级迭代问题。文献 [289] 提出的算法建议对池中每个束评估模型输出。与 GALI 类似，可以用一个优化问题形式的 GALO 替代定义来表示 (2.7) 中的定义。该新的优化问题随后用于推导可高效求解的基于 ILP 的实现。

### GALO 的替代定义

令 \(S \subset X = \{0, 1\}^m$ 为已标记束的集合。束的标签保存在 \(Y = \{y_s | s \in S\}$ 中，且 \(y_s$ 是投标人对 \(s$ 报告的值。此外，我们拥有投标人 \(i$ 的估计值函数 \(\tilde{v}_i : X \to R$，该函数由机器学习回归模型使用 \(S$ 与标签 \(Y$ 作为训练集来学习。本节不对该模型的具体形式进行详细说明，因为它可以是任何回归模型。对于 \(Y$ 中的每个 \(y$，我们引入一个集合 \(H_y = \{x | \tilde{v}_i(x) \text{ 在 } Y$ 中最接近 } y\}$。重新表述的思路保持相似。我们不再遍历已查询的束 \(S$，而是遍历它们的标签 \(Y$。对于每个 \(y \in Y$，我们

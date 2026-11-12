

前一向量：\(\vec{v}_k \rightarrow \vec{v}_{k-1} \rightarrow \dots \rightarrow \vec{v}_1\)。对 \(f(\cdot)\) 的不同选择会对相同的 \(\vec{v}_k\) 产生不同的序列。我们将序列 \(\{\vec{v}_1, ..., \vec{v}_k\}\) 称为一个 *生成的 RWT*。

生成的 RWT 仅在 \(\vec{v}_k\) 的特定选择下才会现实。特别是，我们希望 \(\vec{v}_k\) 是与 \(\mathcal{G}\) 中图形同属一个家族的某个图的结束向量。形式上，我们希望 \(\vec{v}_k = \bar{L}^k \vec{v}_1\)，其中 \(\bar{L}\) 是此类图的平滑归一化邻接矩阵。但我们不知道 \(\vec{v}_1\) 或 \(\bar{L}\)。下面的定理展示了如何选择 \(\vec{v}_k\)。

**定理 1.** 考虑一个带有度 \(\{d_i\}\) 的 *n* 节点图，平滑度 \(\{d'_i\}\)，起始向量 \(\boldsymbol{v} \in \mathbb{R}^n_+\)（由函数 \(f(d_i)\) 构建），以及平滑归一化邻接矩阵 *L*（如定义 1 所示）。设 \(\boldsymbol{w}\) 为一个分量为

\(\boldsymbol{w}_i := \gamma \cdot \sqrt{d'_i}\)

的向量，其中 \(\gamma = \frac{n \left( \sum_j f(d_j) \sqrt{d'_j} \right)}{\left( \sum_j f(d_j) \right) \left( \sum_j d'_j \right)}\)。

则，我们有：

\(\lim_{k \to \infty} \| L^k \boldsymbol{v} - \boldsymbol{w} \| = 0.\)

*证明.* 根据附录中的引理 1，*L* 的最大特征值为 1，其特征向量 \(\boldsymbol{u}_1\) 的分量为 \(u_{1;i} = \sqrt{d'_i} / (\sum_j d'_j)\)。矩阵 *L* 是不可约的（因为图是连通的）且无周期的（因为 \(\alpha > 0\) 诱导自环）。因此，没有其他特征值的绝对值为 1。接下来，我们观察到 \(\boldsymbol{v}^T \boldsymbol{u}_1 > 0\)，因为 \(\boldsymbol{v}\) 和 \(\boldsymbol{u}_1\) 都在正交范数中。因此，\(L^k \boldsymbol{v}\) 趋向于向量 \((\boldsymbol{v}^T \boldsymbol{u}_1) \boldsymbol{u}_1\)，可以看到这就是向量 \(\boldsymbol{w}\)。

定理 1 表明，现实的结束向量 \(\bar{\boldsymbol{v}}_k\) 必须接近 \(\boldsymbol{w}\)，且 \(\boldsymbol{w}\) 仅依赖于度 \(\{d_i\}\)。因此，要构造 \(\bar{\boldsymbol{v}}_k\)，我们必须生成一个与家族 \(\mathcal{G}\) 匹配的现实度分布。一种方法是采样图 \(G \in \mathcal{G}\) 并扰动其度分布。另一个选择是为 \(\mathcal{G}\) 中图形的度分布拟合模型。例如，我们可以拟合幂律或对数正态分布，因为它们在现实世界数据中被广泛观察到。然后，我们可以从这个拟合模型中采样新的度分布。无论哪种方式，我们都能得到一个现实的度分布 \(\{d_i\}\)。

现在，我们按以下方式生成一个 RWT。使用 \(\{d_i\}\) 和 \(f \in \mathcal{F}\) 的选择，我们构建结束向量 \(\bar{\boldsymbol{v}}_k\)（定理 1）。接下来，我们使用第 2.1 节的逆预测器 *P* 来预测 \(\bar{\boldsymbol{v}}_{k-1} := P(\bar{\boldsymbol{v}}_k)\)、\(\bar{\boldsymbol{v}}_{k-2} := P(\bar{\boldsymbol{v}}_{k-1})\)，以此类推。按此方式，我们构造所有向量 \(\{\bar{\boldsymbol{v}}_1, ..., \bar{\boldsymbol{v}}_k\}\)。这个向量序列即为 *生成的 RWT*。

通过使用相同的 \(\bar{\boldsymbol{v}}_k\) 但不同的 \(f \in \mathcal{F}\) 重复这些步骤，我们可以生成多个 RWT。现在我们必须构造与生成的 RWT 对应的稀疏图。下一节展示如何实现。

_备注 2（与传统扩散的区别）。_ 像扩散模型一样，GRAPHWEAVE 具有前向和逆向过程。然而，在扩散中，前向过程添加随机噪声。在 GRAPHWEAVE 中，前向过程是确定性的。它表示向量在随机游走过程中的演化。现在，只有当前向过程收敛到易于采样的稳态点时才有用。在扩散模型中，这个点通常是标准高斯分布（“100%-噪声”）。定理 1 表明 GRAPHWEAVE 的前向过程也收敛。但我们的稳态向量表示随机游走的收敛，而非噪声。由于随机游走在应用中被广泛使用，通过 RWT 学习其模式可能比在图上学习噪声过程更有益。

_备注 3（图 1 中单个结束向量）。_ 定理 1 表明，在通过适当 \(\gamma\) 归一化后，结束向量对所有起始向量都是相同的。图 1 直观地展示了这一点。然而，定义 1 使用未归一化的起始向量，以便我们可以使用相同的起始向量来讨论示例 2-4。

## 2.3 推断图

给定一组生成的 RWT，我们希望找到一个生成它们的图。假设 \(\bar{\mathbf{v}}_j\) 和 \(\bar{\mathbf{v}}_{j+1}\) 是某个生成的 RWT 中连续的两个向量。那么，该图的平滑归一化邻接矩阵 _L_ 必须满足 \(L\bar{\mathbf{v}}_j=\bar{\mathbf{v}}_{j+1}\)。该关系对每对连续向量都成立。形式上，设 _V_<sub>1</sub> 为行集为 \(\{\bar{\mathbf{v}}_j\}\) 的矩阵，_V_<sub>2</sub> 为行集为 \(\{\bar{\mathbf{v}}_{j+1}\}\) 的矩阵。则，

\(V_1 L = V_2.\) (3)

根据定义 1，矩阵 _L_ 的形式为

\(L = (D')^{-1/2}((1 - \alpha)A + \alpha I)(D')^{-1/2},\) (4)

其中 _A_ 是所需图的邻接矩阵，\(D'\) 是一个对角矩阵，其条目为 \(D'_{ii} = (1-\alpha)d_i+\alpha\)，且 _d<sub>i</sub>_ 是节点 _i_ 的度。请注意，我们知道 {_d<sub>i</sub>_}，因为我们在创建 RWT 时将度分布生成作为第一步（第 2.2 节）。

将等式 4 代入等式 3，通过求解以下问题得到 _A_：

\(\text{minimize}_A \sum_{i,j \in [n]} |X_{ij}|\) (5)
\(\text{where } X = V_1(D')^{-1/2}((1 - \alpha)A + \alpha I)(D')^{-1/2} - V_2,\)
\(A_{ij} \in \{0, 1\} \text{ for all } i, j \in [n],\)
\(A = A^T, \text{Trace}(A) = 0, A\mathbf{1} = \mathbf{d},\)

其中 **_d_** 是分量为 _d<sub>i</sub>_ 的向量。约束条件确保 _A_ 是一个带有度 **_d_** 的无权图。等式 5 是一个整数线性规划问题，可以使用诸如 Gurobi 等标准工具求解。

备注 4. 等式 5 的替代方法是将要求 \( A_{ij} \in \{0, 1\} \) 放宽为 \( A_{ij} \in [0, 1] \)。这得到一个凸问题：

\(\text{minimize}_{\tilde{A}} \sum_{ij} |X_{ij}|\)

其中 \(X = \|V_1(D')^{-1/2}((1 - \alpha)\tilde{A} + \alpha I)(D')^{-1/2} - V_2\|_F^2\)，
\(0 \le \tilde{A} \le 1, \text{Trace}(\tilde{A}) = 0, \tilde{A} = \tilde{A}^T, \tilde{A}\mathbf{1} = \mathbf{d}.\)

这得到一个加权图 \(\tilde{A}\)。我们可以通过对 \(\tilde{A}\) 的条目进行舍入来构造 \(A\)，如下所示：

\(A_{ij} := \mathbb{1}_{\tilde{A}_{ij} > a^* + b^* \log d_i},\)

其中 \(a^*, b^* = \arg \min_{a,b} \frac{1}{n} \sum_{i=1}^n \left| \frac{\sum_j \mathbb{1}_{\tilde{A}_{ij} > a + b \log d_i}}{d_i} - 1 \right|.\)

选择 \((a^*, b^*)\) 可以最小化 \(A\) 的节点度与所需度 \(\{d_i\}\) 之间的相对误差。我们可以通过在选定范围上进行网格搜索来选择 \((a^*, b^*)\)。虽然这种方法对等式 5 的目标没有保证，但在实践中通常效果很好。

## 2.4 总体算法

算法 1 显示了 GRAPHWEAVE 的伪代码。我们首先为 \(\mathcal{G}\) 中的图构建 RWT。然后，我们训练一个变换器来逆转观察到的 RWT 的每个步骤。要生成一个图，我们首先生成一个现实的度分布。度分布为我们提供结束向量 \(\bar{\mathbf{v}}_k\)（定理 1）。从 \(\bar{\mathbf{v}}_k\) 开始，我们通过反复应用变换器（等式 2）按逆序生成 RWT。最后，我们通过求解等式 5 来推断与生成的 RWT 对应的图。我们可以通过与不同度分布一起重用变换器来生成多个图。

**实现细节：** 对于分桶函数，我们使用 \(B(\mathbf{v}) := \lfloor c(\mathbf{v} - \mu)/\sigma \rfloor\)，其中 \(\mu\) 和 \(\sigma\) 是训练集中所有向量条目的均值和标准差，\(c\) 是控制桶数的参数，且分桶函数逐元素应用于 \(\mathbf{v}\)。在我们的实验中，我们设置 \(c = 3\)，\(\alpha = 0.9\)，和 \(k = 10\)。对于函数集 \(\mathcal{F}\)，我们使用幂律：\(\mathcal{F} = \{f : \mathbb{R}_+ \rightarrow \mathbb{R}_+; f(d) = d^\beta, \beta \in \{\pm 1, \pm 2\}\}\)。我们还通过添加 \(f(\cdot)\) 的嵌入和 \(j\) 的嵌入来简化 \(\mathcal{E}'(f, j)\) 的形式。

**计算复杂度：** 首先考虑训练成本。我们构建 \(|\mathcal{F}| \times |\mathcal{G}|\) 个 RWT。对于每个 RWT，主要成本是 \(k\) 次稀疏矩阵-向量乘法 \(L\mathbf{v}_j\)。这需要 \(O(kE)\) 时间，其中 \(E\) 是 \(\mathcal{G}\) 中任何图的最大边数。因此，创建 RWT 需要 \(O(|\mathcal{F}||\mathcal{G}|kE)\) 时间。要训练变换器，我们有来自 RWT 的 \(k|\mathcal{F}||\mathcal{G}|\) 个输入向量。对于每个向量，注意力机制考虑 \(O(n^2)\) 对，其中 \(n\) 是最大节点数。每对的成本与嵌入维度成正比


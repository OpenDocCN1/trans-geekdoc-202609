
最后，一个组合了随机、滑动窗口和全局注意力（外部构造）的邻接矩阵示例如 Fig. 5.13 所示。

![Figure 5.13 Big Bird attention adjacency matrix for the external transformer construction, for L = 12,g = 2,w = 4, and r = 4. Row i corresponds to query i. Columns with a • are keys that query i attends to and ⋅ represents a lack of attention (a missing edge).](img/fig5_13.jpg)

Figure 5.13 Big Bird 注意力邻接矩阵用于外部 Transformer 构造，适用于 `L` = 12、`g` = 2、`w` = 4 和 `r` = 4。行 `i` 对应查询 `i`。带有 • 的列是查询 `i` 关注的键，⋅ 表示缺乏注意（缺失边缘）。

`高效稀疏矩阵乘法` 通过使邻接矩阵（以及对应的注意力矩阵）稀疏，GPU 提供的加速被移除。这是因为任意稀疏矩阵的乘法在 GPU 上并不高效。然而，矩阵的稀疏性如果被分组为块，则可以在 GPU 上高效乘法 [100]。

为此，Big Bird 将查询和键分块，并按块添加稀疏性 [292]。选择块大小 `b`，然后将序列长度 `L` 分成 `L`/`b` 个块。于是，原来的 `L` 个查询和键变为 `L`/`b` 个查询和键。这对前面讨论的每种注意力模式都有相对简单的修改：

1. `随机注意` 查询 `i` 关注的键数 `r` 变为查询块关注的键块数 `r`（即块层面的随机数量）。
2. `滑动窗口注意` 查询块 `i` 关注键块 `i` − (`w` − 1)/2 到 `i` + (`w` − 1)/2。
3. `全局注意` 其定义保持不变，只是改为以块为单位而非序列位置来定义。

### 5.2.3 提升多头注意力

我们现在专注于一些改进 Transformer 注意力机制的方法，以提升性能。

#### 5.2.3.1 Talking-heads attention

Vaswani et al [254] 表明多头注意力使得 Transformer 能够进行 `h`（注意力头数量）个独立的注意力计算。Talking-Heads Attention [227] 则让注意力头共享信息。它通过在查询-键乘积（注意力对数） `QK^T` 与注意力权重 `Softmax(QK^T)` 之间加入两层线性投影，将它们映射到新的空间。

Talking-Heads Attention（THA）还将注意力头分为三类：用于查询和键的头、用于值的头、以及用于注意力对数和注意力权重的头。下面详细说明。

请回顾 第 5.2.1.1 节 中的多头注意力公式，两个长度分别为 `L[1]` 和 `L[2]` 的序列 `X[1]`、`X[2]` 的多头注意力如下：

```
\begin{array}{ll}
\mathbf{Q} & {= \mathbf{X}_{1}\mathbf{W}_{q},\, \in {\mathbb{R}}^{L_{1} \times d_{k} \times h}}
\\
\mathbf{K} & {= \mathbf{X}_{2}\mathbf{W}_{k},\, \in {\mathbb{R}}^{L_{2} \times d_{k} \times h}}
\\
\mathbf{V} & {= \mathbf{X}_{2}\mathbf{W}_{v},\, \in {\mathbb{R}}^{L_{2} \times d_{v} \times h}}
\\
\end{array}
```
(5.56)

where `X[1]` ∈ ℝ^(L[1] × d)、`X[2]` ∈ ℝ^(L[2] × d)，`W[q]W[k]` ∈ ℝ^(d × d[k] × h)，以及 `W[v]` ∈ ℝ^(d × d[v] × h)，

```
\begin{array}{ll}
\mathbf{\alpha} & {= \mathbf{Q}\mathbf{K}^{T}, \in {\mathbb{R}}^{L_{1} \times L_{2} \times h}}
\\
\end{array}
```
(5.57)

```
\begin{array}{ll}
{\mathbf{A}(\mathbf{Q},\mathbf{K})} & {= \text{softmax}\left( \frac{\mathbf{\alpha}}{\sqrt{\text{d}_{\text{k}}}} \right),\, \in {\mathbb{R}}^{\text{L}_{\text{1}} \times \text{L}_{\text{2}} \times \text{h}}}
\\
\end{array}
```
(5.58)

```
\begin{array}{ll}
{\mathbf{C}(\mathbf{Q},\mathbf{K},\mathbf{V})} & {= {\sum\limits_{L_{2}}\mathbf{A}}(\mathbf{Q},\mathbf{K})\mathbf{V},\, \in {\mathbb{R}}^{L_{1} \times d_{v} \times h}}
\\
\end{array}
```
(5.59)

其中 `α` 是注意力对数，`A(Q, K)` 为注意力权重，`C(Q, K, V)` 为“上下文”向量，表示在头部拼接和最终投影层之前的 `h` 个注意力头的输出。

`注意力头的划分` THA 对注意力机制进行如下修改。首先，它将 `Q` 和 `K` 的注意力头维度改为查询-键注意力头数 `h[k]`，将 `V` 的注意力头维度改为值注意力头数 `h[v]`。这通过修改生成查询、键和值矩阵的投影矩阵的维度来实现，即 (5.56) 变为

```
\begin{array}{ll}
\mathbf{Q} & {= \mathbf{X}_{1}\mathbf{W}_{q},\, \in {\mathbb{R}}^{L_{1} \times d_{k} \times h_{k}}}
\\
\mathbf{K} & {= \mathbf{X}_{2}\mathbf{W}_{k},\, \in {\mathbb{R}}^{L_{2} \times d_{k} \times h_{k}}}
\\
\mathbf{V} & {= \mathbf{X}_{2}\mathbf{W}_{v},\, \in {\mathbb{R}}^{L_{2} \times d_{v} \times h_{v}}}
\\
\end{array}
```
(5.60)

其中 `W[q]W[k]` ∈ ℝ^(d × d[k] × h[k])，以及 `W[v]` ∈ ℝ^(d × d[v] × h[v])。

`对注意力对数的投影` 接下来，注意力对数 `α` 通过线性层 `W[α]` ∈ ℝ^(h[k] × h) 进行投影，混合查询-键注意力头与注意力对数/权重头；注意力权重则通过线性层 `W[A]` ∈ ℝ^(h × h[v]) 进行投影，混合值注意力头与注意力对数/权重头。于是 (5.57)–(5.59) 变为

```
\begin{array}{l}
{\mathbf{\alpha} = \mathbf{Q}\mathbf{K}^{T}, \in {\mathbb{R}}^{L_{1} \times L_{2} \times h_{k}}}
\\
\end{array}
```
(5.61)

```
\begin{array}{l}
{\mathbf{P}_{\alpha} = \mathbf{\alpha}\mathbf{W}_{\alpha},\, \in {\mathbb{R}}^{L_{1} \times L_{2} \times h}}
\\
\end{array}
```
(5.62)

```
\begin{array}{l}
{\mathbf{A}(\mathbf{Q},\mathbf{K}) = \text{softmax}\left( \frac{\mathbf{P}_{\alpha}}{\sqrt{\text{d}_{\text{k}}}} \right),\, \in {\mathbb{R}}^{\text{L}_{\text{1}} \times \text{L}_{\text{2}} \times \text{h}}}
\\
\end{array}
```
(5.63)

```
\begin{array}{l}
{\mathbf{P}_{A}(\mathbf{Q},\mathbf{K}) = \mathbf{A}\mathbf{W}_{A},\, \in {\mathbb{R}}^{L_{1} \times L_{2} \times h_{v}}}
\\
\end{array}
```
(5.64)

```
\begin{array}{l}
{\mathbf{C}(\mathbf{Q},\mathbf{K},\mathbf{V}) = {\sum\limits_{L_{2}}\mathbf{P}_{A}}\mathbf{V},\, \in {\mathbb{R}}^{L_{1} \times d_{v} \times h_{v}}}
\\
\end{array}
```
(5.65)

where `P[α]` are the projected attention logits and `P_A` are the projected attention weights.

`Performance` Talking-Heads Attention (THA) was evaluated by training a T5 model using THA and the same hyperparameters as the T5 paper (except for omitting dropout during pre-training) and similarly training an ALBERT model. The authors found that THA consistently performed better than multi-head attention [227]. Just projecting the attention logits or just the attention weights is only slightly better than using pure multi-head attention. Significant performance increases came from using both projections. Using talking-heads attention on the encoder block's self-attention layers has a larger effect on model performance than using talking-heads attention on the decoder block's attention layers.

Multi-head attention already comes at a cost and the projections that THA adds, `W[α]` and `W[A]`, increase that cost. Computing the projected attention logits, `P[α]`, adds `L[1]` ⋅ `L[2]` ⋅ `h[k]` ⋅ `h` matrix multiplications and computing the projected attention weights, `P[A]`, adds `L[1]` ⋅ `L[2]` ⋅ `h` ⋅ `h[v]` matrix multiplications. Together, THA adds `L[1]` ⋅ `L[2]` ⋅ `h` ⋅ (`h[k]` + `h[v]`) matrix multiplications, which will make the calculation more costly. The authors note that if `h` < `d[k]` and `h` < `d[v]`, then the cost of the THA projections are less than the cost of the existing multi-head attention calculations. So, in summary, Talking-Heads Attention improves model quality at the cost of increased computation time; allowing the user to decide what kind of tradeoffs they wish to make.

### 5.2.4 Biasing Attention with Priors

This section discusses a few models that bias the attention mechanism by fixing which positions can attend to which. The Longformer model, discussed in section 5.2.2.1, and Big Bird model, discussed in section 5.2.2.4 are both examples of attention with priors, since each uses specific attention patterns, like sliding window attention in sections 5.2.2.1.1 and 5.2.2.4.2. We also discussed another example of biasing attention with priors in section 5.1.2.1, the Realformer.

### 5.2.5 Prototype Queries

#### 5.2.5.1 Clustered attention

Clustered attention [256] is a method to avoid self-attention's `O(L² ⋅ d[k] + L² ⋅ d[v])` time complexity that linearizes the self-attention weight computation by clustering LSH hashed queries with the k-means clustering algorithm. And using the query centroids as the queries to compute the attention matrix.

`Clustering query vectors` Clustered attention happens in two stages. First, each query vector is hashed with locality-sensitive hashing. The hashed queries are then grouped into `C` clusters with k-means. The distance metric used for k-means is the Hamming distance. The centroid of the `j^(th)` cluster is given by

```
\begin{array}{l}
{\mathbf{q}_{j}^{c} = \frac{{\sum\limits_{i = 1}^{L}S_{ij}}\mathbf{q}_{i}}{{\sum\limits_{i = 1}^{L}S_{ij}}}
\\
\end{array}
```
(5.66)

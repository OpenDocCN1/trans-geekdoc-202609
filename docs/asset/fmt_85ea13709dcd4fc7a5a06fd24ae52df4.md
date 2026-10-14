
#### 5.2.2.4 Big Bird

Big Bird is another effort to give the Transformer a sparse attention mechanism that allows for linear scaling. It is also proven to be Turing complete and a universal sequence function approximator [292].

##### An Attention mechanism is a directed graph

Big Bird describes the attention mechanism as a directed graph. The vertices represent the `L` positions in the input sequence. The directed edges represent the pre-softmax attention weights. In other words, the directed edges are the inner products between the query and key vectors, where the `i`th vertex will only have directed edges with the vertices that correspond to the key positions that it can attend to, as described by the set `S[i]` in (5.27).

##### Adjacency matrix

The graph representation casts the problem of reducing the complexity of the attention mechanism as a graph sparsification problem, which can be tackled with graph theory. Big Bird describes the attention graph with its `L × L` adjacency matrix, `A`:

$$
\begin{array}{l} {A(i,j) = \begin{cases} {1,} & {j \in S_{i}} \\ {0,} & \text{otherwise} \\ \end{cases}} \\ \end{array}
$$  

(5.55)

When the adjacency matrix is all ones, `A(i, j) = 1, ∀ (i, j)`, then we have a fully connected graph where each vertex is connected to every other vertex and an attention mechanism with quadratic complexity. Whenever `A(i, j) = 0`, it means that edge `(i, j)` does not exist and thus query position `i` (`q[i]`) cannot attend to key position `j` (`k[j]`).

##### Attention graph patterns

Using the graph theoretical framework, Big Bird combines three attention patterns: random attention, sliding window attention, and a global attention. Each attention pattern corresponds to a particular way of initializing the adjacency matrix.

###### Random attention

Big Bird's random attention pattern is inspired by the type of Erdős-Renyi random graph [84] that connects vertices at random with a uniform probability. In Big Bird's random attention, each query `q[i]` attends to a random number of keys. In terms of the adjacency matrix, `A(i, :) = 1` for `r` key positions that are chosen at random, with equal probability. An example adjacency matrix for the random attention pattern is shown in Fig. 5.9.

![Figure 5.9 Random adjacency matrix, for L = 12 and r = 7. Row i corresponds to query i. Columns with a • are keys that query i attends to and ⋅ represents a lack of attention (a missing edge).](img/fig5_9.jpg)

Figure 5.9 Random adjacency matrix, for `L = 12` and `r = 7`. Row `i` corresponds to query `i`. Columns with a • are keys that query `i` attends to and ⋅ represents a lack of attention (a missing edge).

###### Sliding window attention

Big Bird's local attention is derived from a Watts-Strogatz [265] small world graph on a ring lattice, where each vertex is connected to `w` neighbors, so there are `w/2` neighbors to either side. This allows the query at position `i` to attend to keys at positions in the window `[i - w/2, i + w/2]`. In terms of the adjacency matrix, `A(i, i - w/2 : i + w/2) = 1`. This is similar to the sliding window attention in the Longformer that was discussed in Sec. 5.2.2.1.1. An example adjacency matrix for the sliding window attention is shown in Fig. 5.10.

![Figure 5.10 Sliding window attention adjacency matrix, for L = 12 and w = 4. Row i corresponds to query i. Columns with a • are keys that query i attends to and ⋅ represents a lack of attention (a missing edge).](img/fig5_10.jpg)

Figure 5.10 Sliding window attention adjacency matrix, for `L = 12` and `w = 4`. Row `i` corresponds to query `i`. Columns with a • are keys that query `i` attends to and ⋅ represents a lack of attention (a missing edge).

###### Global attention

Big Bird also allows some tokens to attend to all tokens in the sequence. These global tokens are also attended to by all tokens. Big Bird uses two types of global tokens: internal transformer construction and external transformer construction.

In the internal transformer construction, a subset of the `L` vertex, `G`, are promoted to global tokens. Thus the queries or keys in those positions attend to all other positions. Here, `A(i, :) = A(:, i) = 1, ∀ i ∈ G`. The expanded adjacency matrix `B` is shown in Fig. 5.11.

![Figure 5.11 Global attention adjacency matrix for the internal transformer construction, for L = 12 and G = 3,4,7. Row i corresponds to query i. Columns with a • are keys that query i attends to and ⋅ represents a lack of attention (a missing edge).](img/fig5_11.jpg)

Figure 5.11 全局注意力邻接矩阵用于内部 Transformer 构造，适用于 `L = 12` 和 `G = 3、4、7`。行 `i` 对应查询 `i`。带有 • 的列是查询 `i` 关注的键，⋅ 表示缺乏注意（缺失边缘）。

外部 Transformer 构造在已有的 `L` 令牌上额外添加 `g` 个全局令牌。这些额外的令牌是全局的。示例包括变压器中使用的特殊令牌，如 `[CLS][CLS]`。这实际上会创建一个新的邻接矩阵 `B`，它在 `A` 前面添加 `g` 行和列以包含特殊令牌。这里 `B(i, :) = B(:, i) = 1`，其中 `i = 1, ..., g`，且 `B(g + i, g + j) = A(i, j)`，其中 `i` 和 `j = 1, ..., L`。扩展后的邻接矩阵 `B` 如 Fig. 5.12 所示。

![Figure 5.12 Global attention adjacency matrix for the external transformer construction, for L = 9 and g = 3. Row i corresponds to query i. Columns with a • are keys that query i attends to and ⋅ represents a lack of attention (a missing edge).](img/fig5_12.jpg)

Figure 5.12 全局注意力邻接矩阵用于外部 Transformer 构造，适用于 `L = 9` 和 `g = 3`。行 `i` 对应查询 `i`。带有 • 的列是查询 `i` 关注的键，⋅ 表示缺乏注意（缺失边缘）。

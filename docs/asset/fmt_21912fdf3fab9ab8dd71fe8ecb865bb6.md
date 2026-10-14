
RealFormer，即 Residual Attention Layer Transformer \[107\]，在 transformer 的前一层的所有注意力头的原始注意力对数（query-key 点积）上加入残差分数。注意力权重随后是加和后的注意力对数的 softmax。该过程在 Fig. 5.4 中以示意图展示，在数学公式 (5.7)–(5.9) 中给出。

```
$$\\begin{array}{l} {ResidualMultiHead(\\mathbf{Q},\\mathbf{K},\\mathbf{V},\\mathbf{Prev}) = \\text{concat}(head\_{1},\\ldots,head\_{h})\\mathbf{W}\_{o}} \\\\ \\end{array}$$  

(5.7)
```

```
$$\\begin{array}{l} {head\_{i} = ResidualAttn(\\mathbf{Q}\_{i},\\mathbf{K}\_{i},\\mathbf{V}\_{i},\\mathbf{Pre}\\mathbf{v}\_{i})} \\\\ \\end{array}$$  

(5.8)
```

```
$$\\begin{array}{l} {ResidualAttn(\\mathbf{Q}^{\\prime},\\mathbf{K}^{\\prime},\\mathbf{V}^{\\prime},\\mathbf{Pre}\\mathbf{v}^{\\prime}) = \\text{softmax}\\left( {\\frac{\\mathbf{Q}^{\\prime}\\mathbf{K}^{\\prime}\\ ^{\\text{T}}}{\\sqrt{\\text{d}\\_\\text{k}}}\\text{+}\\mathbf{Pre}\\mathbf{v}^{\\prime}} \\right)\\mathbf{V}^{\\prime}} \\\\ \\end{array}$$  

(5.9)
```

其中 `Prev` ∈ ℝ^(h × d[in] × d[out]) 是前一层 transformer 的注意力对数。`d[in]` 是该层的输入序列维度，`d[out]` 是该层的输出序列维度。softmax 的输入（即注意力对数或注意力分数）会传递给下一层 RealFormer。

![Figure 5.4 RealFormer's residual attention connection.](img/fig5_4.jpg)

Figure 5.4 RealFormer's residual attention connection.

该方法可应用于其他 transformer 架构，包括解码器层。当 transformer 中包含多种注意力模块时，可以跳过边缘以支持每种注意力类型的独立残差连接。

**Performance** RealFormer 通常优于标准 transformer 架构，包括在 BERT 中的使用，且无需增加模型参数。

## 5.1.3 Adaptive Computation Time

### 5.1.3.1 Universal transformers (UT)

如前几章所述，transformer 解决了 RNN 的主要问题——序列计算的瓶颈和消失梯度问题。此外，自注意力这一关键创新使得 per-symbol context-based vectors 的并行计算成为可能，并为每个符号提供了全局受体场，能够获取所有符号的信息。另一方面，RNN 缺乏固有的递归感应偏置，在处理具有内在层次结构的任务或训练数据与预测数据长度差异较大的情况下会出现问题。此外，transformer 的序列计算次数独立于输入大小，仅取决于层数，这使其在计算通用性上不足，即它们是不可通用的或图灵不完全的。transformer 对所有输入应用相同的计算量，导致在可以有条件计算的场景中出现低效。

Dehghani 等人 \[69\] 提出的通用变换器（Universal transformers, UT）是对 transformer 的扩展，它在保留并行性和全局受体场优势的同时，加入了 RNN 的递归感应偏置，从而实现计算通用性。与固定层数的 transformer 不同，UT 采用通用变换器块，即一个自注意力机制后跟一个循环变换，为每个输入符号提供并行的递归感应偏置。如 Fig. 5.5 所示，通用变换器是一种在深度而非时间维度上演化隐藏状态的循环函数，每一步都基于前一步的隐藏状态序列，并同时处理所有输入符号。

![Figure 5.5 Universal Transformer with information from different positions using self-attention and applying a recurrent transition function.](img/fig5_5.jpg)

通用变换器利用自注意力结合来自不同位置的信息，并应用循环转换函数。

UT 与现有的神经网络架构（如 Neural GPU \[136\] 和 Neural Turing Machine \[98\]）有许多共同点。它也可以被视为具有层间共享参数的多层变换器。Graves 提出自适应计算时间（ACT），使得循环神经网络（RNN）能够动态决定在接受输入和输出之间进行多少计算步骤（思考时间），以克服固定步骤数带来的问题。UT 在每个位置上引入了基于 Graves 的 ACT 的动态停止机制，使得每个符号的计算能够根据复杂度进行有条件的控制。研究表明，UT 在各种 NLP 和 NLU 任务上表现优于标准变换器，并在诸如 LAMBADA 语言建模等复杂任务中实现了新的最先进的性能。

## 5.1.4 Transformer 块之间的循环关系

### 5.1.4.1 Transformer-XL

Transformer-XL \[67\] 能够建模超出固定长度的依赖关系，同时尊重句子边界。它被提出是因为标准变换器架构的固定上下文窗口阻碍了它学习在固定窗口之外的依赖关系。Transformer-XL 可处理比标准变换器更长 450% 的依赖关系，且推理速度比 Transformer 快约 1800 倍。

**段级循环** Transformer-XL 通过一种称为段级循环的方法扩展其上下文，超出固定窗口。段级循环通过在处理当前文本段时，使用前一段文本作为额外的上下文来工作。为此，前一段必须被缓存，并且每个层对该段的变换器输出也需缓存。

在标准变换器中，第 `n` 层的输出（$\mathbf{h}_{t}^{(n)}$）以第 `n` − 1 层的输出（$\mathbf{h}_{t}^{(n - 1)}$）为输入：

```
$$\\begin{array}{l} {\\mathbf{h}\_{t}^{(n)} = Transformer(\\mathbf{h}\_{t}^{(n - 1)})} \\\\ \\end{array}$$  

(5.10)
```

它内部从 $\mathbf{h}_{t}^{(n - 1)}$ 生成查询、键和值：

```
$$\\begin{array}{ll} \mathbf{Q}_{t}^{(n)} & {= \mathbf{h}_{t}^{(n - 1)}\mathbf{W}_{q}} \\\\ \mathbf{K}_{t}^{(n)} & {= \mathbf{h}_{t}^{(n - 1)}\mathbf{W}_{k}} \\\\ \mathbf{V}_{t}^{(n)} & {= \mathbf{h}_{t}^{(n - 1)}\mathbf{W}_{v}} \\\\ \end{array}$$  

(5.11)
```

这里 `n` = 1 表示第一层变换器层，`n` = 0 表示输入到第一层的内容，即 $\mathbf{h}_{t}^{(0)} = \mathbf{X}$。

当加入前一段时，Eqns. (5.11) 会改变。考虑两个连续的文本段，其嵌入表示分别为 $\mathbf{X}_{t}$ 与 $\mathbf{X}_{t+1}$（`t` 仅用于标识段顺序）。在计算当前段 $\mathbf{X}_{t+1}$ 的第 `n` 层变换器输出时，会有来自前一段第 `n` − 1 层的输出 $\mathbf{h}_{t}^{(n - 1)}$ 的贡献：

```
$$\\begin{array}{l} {\\mathbf{h}\_{t + 1}^{(n)} = \\text{TransformerXL}(\\mathbf{h}\_{t + 1}^{(n - 1)},\\mathbf{h}\_{t}^{(n - 1)}).} \\\\ \\end{array}$$  

(5.12)
```

依赖于前一段的关键在于计算当前段的键和值：

```
$$\\begin{array}{ll} \mathbf{Q}_{t + 1}^{(n)} & {= \mathbf{h}_{t + 1}^{(n - 1)}\mathbf{W}_{q}} \\\\ \mathbf{K}_{t + 1}^{(n)} & {= {\widetilde{\mathbf{h}}}\_{t + 1}^{(n - 1)}\mathbf{W}_{k}} \\\\ \mathbf{V}_{t + 1}^{(n)} & {= {\widetilde{\mathbf{h}}}\_{t}^{(n - 1)}\mathbf{W}_{v}} \\\\ \end{array}$$  

(5.13)
```

```
$$\\begin{array}{l} {{\widetilde{\mathbf{h}}}\_{t + 1}^{(n - 1)} = \lbrack\text{StopGradient}(\mathbf{h}\_{t}^{(n - 1)});\,\mathbf{h}\_{t + 1}^{(n - 1)}\rbrack} \\\\ \\end{array}$$  

(5.14)
```

其中 `StopGradient` 表示在该操作期间不计算梯度。

Eqns. (5.13) 与 (5.14) 表明注意力机制被用于计算一种修改后的注意力，该注意力结合了前一输入序列的信息，以计算当前输入序列的表示。除此之外，还有更多内容。当前序列的变换器输出依赖于前一序列的变换器输出，而前一序列的输出又依赖于该序列之前的序列以及前一层的变换器输出。这意味着，随着变换器层数的增加，模型能够处理的有效上下文大小也随之增大。形式上，我们可以说第 `n` 层在第 `t` 个段的输出会受到从第 `t−n` 个段起的输入序列的影响。例如，在 Table 5.1 中展示了四个文本段和三层 Transformer-XL 的情况。

TABLE 5.1 在层深度为三的情况下，第四段的变换器输出会受到第一段的影响。为了简洁，$T$ 表示如 (5.12) 所述的 Transformer-XL 操作。

| 层 (`n`) | `S[1]` | `S[2]` | `S[3]` | `S[4]` |
| --- | --- | --- | --- | --- |
| 0 (输入) | `h[1]^((0))` = `S[1]` | `h[2]^((0))` = `S[2]` | `h[3]^((0))` = `S[3]` | `h[4]^((0))` = `S[4]` |
| 1 | `h[1]^((1))` = `T(h[1]^((0)))` | `h[2]^((1))` = `T(h[2]^((0)), h[1]^((0)))` | `h[3]^((1))` = `T(h[3]^((0)), h[2]^((0)))` | `h[4]^((1))` = `T(h[4]^((0)), h[3]^((0)))` |
| 2 | `h[1]^((2))` = `T(h[1]^((1)))` | `h[2]^((2))` = `T(h[2]^((1)), h[1]^((1)))` | `h[3]^((2))` = `T(h[3]^((1)), h[2]^((2)))` | `h[4]^((2))` = `T(h[4]^((1)), h[3]^((1)))` |
| 3 | `h[1]^((3))` = `T(h[1]^((2)))` | `h[2]^((3))` = `T(h[2]^((2)), h[1]^((2)))` | `h[3]^((3))` = `T(h[3]^((2)), h[2]^((3)))` | `h[4]^((3))` = `T(h[4]^((2)), h[3]^((2)))` |

#### 位置编码在 Transformer-XL 中

*位置编码* 如前所述，由于 Transformer 不包含循环或卷积层，词序通过位置编码显式构建。每个输入序列会得到一个位置编码 $\mathbf{P}\in\mathbb{R}^{L\times d}$，其中 `L` 为序列最大长度，`d` 为嵌入维度；同时给出词嵌入 $\mathbf{E}\in\mathbb{R}^{L\times d}$。完整的输入序列表示为 $\mathbf{X}=\mathbf{E}+\mathbf{P}$，这是本章后续公式（如 (5.22)）中使用的相同 `X`。

`p[i]` 是位置 `i` 的位置编码；`e[i]` 是位置 `i` 的词嵌入。由于位置编码是确定性的且与序列中的 token 无关，任何位置 `i` 的词都会拥有相同的位置编码。这在段级循环中会带来问题。

考虑两个连续的文本序列 $\mathbf{X}_{t+1}$ 与 $\mathbf{X}_{t}$，第 1 层 TransformerXL 的输出分别为：

```
$$\\begin{array}{l} {\\mathbf{h}\_{t + 1}^{(1)} = \\text{TransformerXL}(\\mathbf{X}\_{t + 1},\\mathbf{X}\_{t})} \\\\ \\end{array}$$  

(5.15)
```

而 (5.14) 表示：

```
$$\\begin{array}{l} {{\widetilde{\mathbf{h}}}\_{t + 1}^{(0)} = \lbrack\text{StopGradient}(\mathbf{X}\_{t});\,\mathbf{X}\_{t + 1}\rbrack} \\\\ \\end{array}$$  

(5.16)
```

由于 `X[t] = E[t] + P` 且位置编码与序列中的 token 无关，${\widetilde{\mathbf{h}}}_{t + 1}^{(0)}$ 是拼接相同的位置编码。这有问题，因为 ${\widetilde{\mathbf{h}}}_{t + 1}^{(0)}$ 表示扩展的有效上下文大小，因此序列中的每个位置都应有独立的位置编码。如果没有独立的位置编码，模型会丢失单词顺序的信息。解决此问题的方法是使用相对位置编码。

*相对位置编码* 早期工作 \[124, 224\] 将相对位置编码引入，以让注意力机制学习序列中两个位置之间的距离，而不是使用标准 Transformer 的绝对位置编码，后者会偏向注意力机制认为绝对位置很重要。相反，信息关于 `q[i]` 与 `k[j]` 之间的相对距离会被纳入注意力权重的计算，使注意力机制关注距离 `i−j`，而不是位置 `i` 和 `j`。

Transformer XL 修改了注意力矩阵的计算，使用正弦相对位置编码\[67\]。我们可以通过先展开 (5.23) 中的 `(i, j)` 项 `QK^T`，即 `q[i]k[j]^T`，来看到这一点。回顾 (5.22)、(5.24) 和 (5.25)，我们可以看到 `X` 的第 `i`-th 行是 `x[i] = e[i] + p[i]`，并且

```
$$\\begin{array}{ll} \mathbf{q}_{i} & {= \mathbf{x}_{i}\mathbf{W}_{q}} \\\\ \mathbf{k}_{j} & {= \mathbf{x}_{j}\mathbf{W}_{k}} \\\\ \end{array}$$  

(5.17)
```

利用 (5.17)，我们展开 `q[i]k[j]^T` 得到

```
$$\\begin{array}{ll} A_{ij} & {= (\mathbf{e}_{i}\mathbf{W}_{q} + \mathbf{p}_{i}\mathbf{W}_{q})(\mathbf{W}_{k}^{T}\mathbf{e}_{j}^{T} + \mathbf{W}_{k}^{T}\mathbf{p}_{j}^{T})} \\\\ \\ & {= \mathbf{e}_{i}\mathbf{W}_{q}\mathbf{W}_{k}^{T}\mathbf{e}_{j}^{T} + \mathbf{e}_{i}\mathbf{W}_{q}\mathbf{W}_{k}^{T}\mathbf{p}_{j}^{T}} \\\\ \\ & {\quad + \,\mathbf{p}_{i}\mathbf{W}_{q}\mathbf{W}_{k}^{T}\mathbf{e}_{j}^{T} + \mathbf{p}_{i}\mathbf{W}_{q}\mathbf{W}_{k}^{T}\mathbf{p}_{j}^{T}} \\\\ \\end{array}$$  

(5.18)
```

Transformer XL 将 `A[ij]` 用五个新量度重新参数化：`R[i−j]`、`u`、`v`、`W[k,E]` 和 `W[k,R]` \[67\]：

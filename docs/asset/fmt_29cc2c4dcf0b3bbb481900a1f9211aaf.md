
The decoder has the output of the encoder, the context variable `c`, and the given output sequence `y`[1], …, `y`[`T`]' to generate the decoded outputs. In Sutskever et al., the context variable from the encoder—the final hidden state—initiates the decoder, whereas in Cho et al. the context variable is passed to every time step.

Similar to the encoder, decoder hidden state at any time `t`' is given by

$$\begin{array}{l} {\mathbf{s}_{t^{\prime}} = g(\mathbf{s}_{t - 1},\mathbf{y}_{t^{\prime} - 1},\mathbf{c})} \\ \end{array}$$  

(2.5)

The hidden state of the decoder flows to an output layer and the conditional distribution of the next token at `t`' is given by

$$\begin{array}{l} {P(\mathbf{y}_{t^{\prime}}|\mathbf{y}_{t^{\prime} - 1},\cdots,y_{1},\mathbf{c}) = \text{softmax}(\mathbf{s}_{t - 1},\mathbf{y}_{t^{\prime} - 1},\mathbf{c})} \\ \end{array}$$  

(2.6)

### 2.2.3 Training

The decoder predicts a probability distribution for the output tokens at each time step, and the softmax gives the distribution over the words. Thus, the encoder and decoder are jointly trained, and the cross-entropy loss is used for optimization and is given by

$$\begin{array}{l} {\max\limits_{\theta}\frac{1}{N}\sum\limits_{n = 1}^{N}\log p_{\theta}(\mathbf{y}^{(n)}|\mathbf{x}^{(n)})} \\ \end{array}$$  

(2.7)

The process of concatenating the `< bos >` and the original output sequence, excluding the final token, as the input to the decoder during the training is called `teacher forcing`. The teacher forcing helps in addressing the slow convergence and instability problems when training RNNs.

### 2.2.4 Issues with RNN-Based Encoder-Decoder

如上文所述，解码器组件使用一个上下文变量压缩并编码源句子的完整信息。输入规模增大时，压缩过程中会丢失信息。句子中的词语也可能因语言而具有复杂结构和长距离关联。将这些信息以压缩方式存储在单个向量中也会导致低效。另一方面，编码器侧的每个时间步的隐藏变量都可用，并携带信息供解码器网络使用。解码器的每个时间步都会受到编码器隐藏变量的不同影响。循环神经网络（`RNN`）也存在消失和爆炸梯度的问题 \[115\]。`RNN` 的一个计算问题在于其依赖于前一个时间步的递归或依赖，使得结构难以并行化。

### 2.3 注意力机制

#### 2.3.1 背景

注意力机制是选择性地关注特定元素并过滤掉不那么相关的元素。人眼接收到的信息量约为每秒十亿比特，而大脑处理的能力远低于此。视觉注意力是一种注意力形式，它涉及将注意力导向并维持对刺激（如人物、无生命物体或特定任务）的聚焦，从而使大脑高效处理。因此，注意力机制使人类能够只关注感兴趣的那部分信息，从而实现最优的资源利用，提升生存和成长。

“美国心理学之父”威廉·詹姆斯创建了两元组件框架来解释视觉注意力机制 \[133\]。在该框架中，注意力的“聚光灯”使用非自愿（ involuntary）和自愿（ voluntary）线索来偏向感官输入。非自愿线索是自发的，基于环境中目标的显著性和易注意性。相反，自愿线索是基于主体自愿努力有意集中注意力的目标。例如，通过给特定物体上不同颜色来吸引注意力，或关注哭泣的婴儿，都是非自愿线索。相反，为回答问题或解决特定问题而关注特定文本则是自愿线索。

在深度学习中的注意力机制中，自愿线索对应于查询（`queries`），非自愿线索对应于键（`keys`），感官输入对应于值（`value`）。每个感官输入（`value`）都映射到该输入的非自愿线索（`key`）。因此，注意力机制可以被视为通过注意力聚合，利用查询（自愿线索）和键（非自愿线索）来偏向选择值（感官输入）的过程，如图 2.3 所示 \[17\]。

形式化地，考虑由 `n` 个键-值对（k[1], v[1]), …, (k[n], v[n]）组成的记忆单元，其中 k[i] ∈ ℝ^(d[k]) 且 v[i] ∈ ℝ^(d[v])。注意力层接收的输入是查询 `q` ∈ ℝ^(d[q])，输出为 `o` ∈ ℝ^(d[v])，其形状与值 v 相同。

注意力层使用一个评分函数 `α` 计算查询与键之间的相似度，返回对键 k[1], …, k[n] 的得分 a[1], …, a[n]：

$$\begin{array}{l} {a_{i} = \alpha(\mathbf{q},\mathbf{k}_{i})} \\ \end{array}$$  

(2.8)

注意力权重通过对得分应用软最大函数计算：

$$\begin{array}{l} {\mathbf{b} = \text{softmax}(\mathbf{a})} \\ \end{array}$$  

(2.9)

每个元素 b_i 的计算方式为：

$$\begin{array}{l} {b_{i} = \frac{\exp(a_{i})}{\sum_{j}{\exp(a_{j})}}} \\ \end{array}$$  

(2.10)

输出是注意力权重与值的加权和：

$$\begin{array}{l} {\mathbf{o} = {\sum\limits_{i = 1}^{n}b_{i}}}\mathbf{v}_{i}} \\ \end{array}$$  

(2.11)

Fig. 2.4 捕捉了从输入查询到输出的各种向量和标量之间的交互。

![Figure 2.4 Attention mechanism showing query, keys, values, and output vector interactions.](img/fig2_4.jpg)

Figure 2.4 Attention mechanism showing query, keys, values, and output vector interactions.

注意力机制的设计是为了克服 `RNN` 编码器-解码器结构所存在的问题。

如图 2.3 所示，注意力机制可以被视为一个拥有键和值的记忆体，以及在有人查询时生成输出的层，输出由 value 的 keys 映射到输入 \[17\]。

形式化地，考虑由 `n` 个键-值对（k[1], v[1]), …, (k[n], v[n]）组成的记忆单元，其中 k[i] ∈ ℝ^(d[k]) 且 v[i] ∈ ℝ^(d[v])。注意力层接收的输入是查询 `q` ∈ ℝ^(d[q])，输出为 `o` ∈ ℝ^(d[v])，其形状与值 v 相同。

注意力层使用评分函数 `α` 计算查询与键之间的相似度，返回对键 k[1], …, k[n] 的得分 a[1], …, a[n]：

$$\begin{array}{l} {a_{i} = \alpha(\mathbf{q},\mathbf{k}_{i})} \\ \end{array}$$  

(2.8)

注意力权重通过对得分应用软最大函数计算：

$$\begin{array}{l} {\mathbf{b} = \text{softmax}(\mathbf{a})} \\ \end{array}$$  

(2.9)

每个元素 b_i 的计算方式为：

$$\begin{array}{l} {b_{i} = \frac{\exp(a_{i})}{\sum_{j}{\exp(a_{j})}}} \\ \end{array}$$  

(2.10)

输出是注意力权重与值的加权和：

$$\begin{array}{l} {\mathbf{o} = {\sum\limits_{i = 1}^{n}b_{i}}}\mathbf{v}_{i}} \\ \end{array}$$  

(2.11)

Fig. 2.4 捕捉了从输入查询到输出的各种向量和标量之间的交互。

![Figure 2.4 Attention mechanism showing query, keys, values, and output vector interactions.](img/fig2_4.jpg)

Figure 2.4 Attention mechanism showing query, keys, values, and output vector interactions.

### 2.3.2 基于得分的注意力类型

如前所述，评分函数 `α(q, k)` 可以采用多种形式，从而催生了多种注意力机制，每种都有其优势。

#### 2.3.2.1 点积（乘积）

点积基于的评分函数最简单，不需要调参 \[176\]。

$$\begin{array}{l} {\alpha(\mathbf{q},\mathbf{k}) = \mathbf{q} \cdot \mathbf{k}} \\ \end{array}$$  

(2.12)

#### 2.3.2.2 缩放点积或乘积

缩放点积基于的评分函数将点积除以 √d_k，以消除维度 d_k 的影响 \[254\]。根据 Vaswani 等人，随着维度增加，点积会变大，导致 softmax 函数进入极端梯度区域。

$$\begin{array}{l} {\alpha(\mathbf{q},\mathbf{k}) = \frac{\mathbf{q} \cdot \mathbf{k}}{\sqrt{d_{k}}}} \\ \end{array}$$  

(2.13)

#### 2.3.2.3 线性、MLP 或加性

卢昂等人还尝试将查询和键投射到隐藏层的维度 h，学习权重（`W_k`, `W_q`），并使用 sigmoid 函数将它们与值结合，如下所示：

$$\begin{array}{l} {\alpha(\mathbf{q},\mathbf{k}) = \mathbf{v}^{\text{T}}\tanh(\mathbf{W}_{k}\mathbf{k} + \mathbf{W}_{q}\mathbf{q})} \\ \end{array}$$  

(2.14)

缩放点积或点积基于的评分函数比加性注意力机制更快且更节省内存。

### 2.3.3 基于注意力的序列到序列

在编码器-解码器中加入注意力层并映射到查询、键和值的一般修改如图 2.5 所示，具体为：

1. 使用最后编码器状态作为键 `k` 和值 `v`。
2. 使用解码器在时间步 t‑1 的最后状态作为查询 `q`。
3. 注意力层的输出 `o`（上下文变量）用于下一个解码状态 t。

![Figure 2.5 Encoder-decoder with attention layer.](img/fig2_5.jpg)

Figure 2.5 编码器-解码器带注意力层。

为了更详细地理解流程，考虑法语翻译示例，其中键和值是编码器状态，对应于词 {*J*^′*a**i**m**e*, *l**e**, *t**h**é*, .}，解码器在时间步 t‑1 已生成的词为 *I*, *love*。如图 2.6 所示，解码器在 t‑1 的输出 *love* 作为查询进入注意力层，与键结合生成未归一化的得分 a = α(q, k)，随后归一化得到注意力权重 b。注意力权重再与值（编码器输出）相乘得到上下文变量或输出向量 o。输出 o 再与前一个解码状态结合，生成下一个词 *tea* 在时间步 t。

![Figure 2.6 序列到序列，在时间 t 处，当解码器在 t - 1 生成了 love 时，token tea 将作为输出生成。](img/fig2_6.jpg)

Figure 2.6 序列到序列，在时间 `t` 处，当解码器在 `t - 1` 生成了 `love` 时，token `tea` 将作为输出生成。

## 2.4 Transformer

如 Fig. 2.7 所示，Vaswani 等人提出的主要 Transformer 结构基于前文描述的编码器-解码器架构。Transformer 将卷积神经网络 (`CNN`) 的并行计算优势与循环神经网络 (`RNN`) 的捕获长距离、变长序列信息的能力相结合。Transformer 架构中提出了许多系统性变化，下面的若干子节将逐一详细说明。

![Figure 2.7 Transformer 架构。](img/fig2_7.jpg)

Figure 2.7 Transformer 架构。

### 2.4.1 源表示和目标表示

源词和目标词都进行分词，分词后的 token 经过词嵌入和位置编码，得到所有句子的位置编码表示。

#### 2.4.1.1 词嵌入

标准的词嵌入查找可以将句子长度为 `l` 的句子转换为维度为 (`l`, `d`) 的矩阵 `W`，即 `W` ∈ ℝ^(`l` × `d_`).

#### 2.4.1.2 位置编码

词序和位置在大多数 NLP 任务中起关键作用。循环神经网络通过逐词处理本质上已经将词序纳入模型。在 Transformer 架构中，为加快速度并实现并行化，循环神经网络被多头注意力层取代，后文将详细说明。因此，必须显式将词序信息作为输入传递给模型层，以此方式捕获词序。这种词序信息的编码被称为位置编码。可以推导出多种有效位置编码的要求，具体包括：

1. 每个时间步（句子中的词）拥有唯一的编码值。
2. 跨不同长度句子的两个时间步之间的距离保持一致。
3. 编码结果对句子长度是泛化的、独立的。
4. 编码是确定性的。

实现上述所有要求的简朴方法是使用二进制表示。Fig. 2.8 展示了在维度为 3 的向量中，如何通过二进制值生成 8 个满足上述要求的位置编码。将每个比特表示为灰色（0）和白色（1），显示出每个位置的差异以及恒定的差值。使用二进制值在内存方面成本很高。

![Figure 2.8 维度为 3 的位置编码，对应 8 个位置。](img/fig2_8.jpg)

Figure 2.8 维度为 3 的位置编码，对应 8 个位置。

若句子长度为 `l`，嵌入维度为 `d`，位置编码 `P` 为维度相同的二维矩阵，即 `P` ∈ ℝ^(`l` × `d_`). 每个位置可以通过以下公式表示，其中 `i` 表示位置索引（范围 0 到 `l`‑1），`j` 表示维度索引（范围 0 到 ⌊(`d`‑1)/2⌋）：

$$\begin{array}{l} {\mathbf{P}_{i,2j} = \sin(i/1000^{2j/d})} \\ \end{array}$$  

(2.15)

$$\begin{array}{l} {\mathbf{P}_{i,2j + 1} = \cos(i/1000^{2j/d})} \\ \end{array}$$  

(2.16)

*f**o**r**i* = 0, ⋯, *l* − 1, *j* = 0, ⋯, ⌊(`d` − 1)/2⌋。上述函数表明，频率随向量维度递减，在 wavelength 上从 2π 到 10000 × 2π 形成等比数列。当 `d` = 512 维且最大句子长度 `l` = 50 时，位置编码可视化如 Fig. 2.9 所示。

![Figure 2.9 维度为 512 的位置编码，对应 50 个位置。](img/fig2_9.jpg)

Figure 2.9 维度为 512 的位置编码，对应 50 个位置。

如 Fig. 2.7 所示，词嵌入矩阵 `W` 与位置编码矩阵 `P` 相加，得到输入表示 `X` = `W` + `P` ∈ ℝ^(`l` × `d_`).

### 2.4.2 注意力层

Transformer 中的基本构件是自注意力（self‑attention），在编码器和解码器中均有使用，只是在使用方式上略有差异。下面的子节将逐步构建注意力层，从最基础的自注意力开始。

#### 2.4.2.1 自注意力


如上文所述，解码器组件使用一个上下文变量压缩并编码源句子的完整信息。输入规模增大时，压缩过程中会丢失信息。句子中的词语也可能因语言而具有复杂结构和长距离关联。将这些信息以压缩方式存储在单个向量中也会导致低效。另一方面，编码器侧的每个时间步的隐藏变量都可用，并携带信息供解码器网络使用。解码器的每个时间步都会受到编码器隐藏变量的不同影响。循环神经网络（RNN）也存在消失和爆炸梯度的问题 \[[115](#refbib.xhtml#refbib_115)\]。RNN 的一个计算问题在于其依赖于前一个时间步的递归或依赖，使得结构难以并行化。

### 2.3 注意力机制

#### 2.3.1 背景

注意力机制是选择性地关注特定元素并过滤掉不那么相关的元素。人眼接收到的信息量约为每秒十亿比特，而大脑处理的能力远低于此。视觉注意力是一种注意力形式，它涉及将注意力导向并维持对刺激（如人物、无生命物体或特定任务）的聚焦，从而使大脑高效处理。因此，注意力机制使人类能够只关注感兴趣的那部分信息，从而实现最优的资源利用，提升生存和成长。

“美国心理学之父”威廉·詹姆斯创建了两元组件框架来解释视觉注意力机制 \[[133](#refbib.xhtml#refbib_133)\]。在该框架中，注意力的“聚光灯”使用非自愿（ involuntary）和自愿（ voluntary）线索来偏向感官输入。非自愿线索是自发的，基于环境中目标的显著性和易注意性。相反，自愿线索是基于主体自愿努力有意集中注意力的目标。例如，通过给特定物体上不同颜色来吸引注意力，或关注哭泣的婴儿，都是非自愿线索。相反，为回答问题或解决特定问题而关注特定文本则是自愿线索。

在深度学习中的注意力机制中，自愿线索对应于查询（queries），非自愿线索对应于键（keys），感官输入对应于值（value）。每个感官输入（value）都映射到该输入的非自愿线索（key）。因此，注意力机制可以被视为通过注意力聚合，利用查询（自愿线索）和键（非自愿线索）来偏向选择值（感官输入）的过程，如图 2.3 所示 \[[17](#refbib.xhtml#refbib_17)\]。

形式化地，考虑由 *n* 个键-值对（k[1], v[1]), …, (k[n], v[n]）组成的记忆单元，其中 k[i] ∈ ℝ^(d[k]) 且 v[i] ∈ ℝ^(d[v])。注意力层接收的输入是查询 q ∈ ℝ^(d[q])，输出为 o ∈ ℝ^(d[v])，其形状与值 v 相同。

注意力层使用一个评分函数 α 计算查询与键之间的相似度，返回对键 k[1], …, k[n] 的得分 a[1], …, a[n]：

$$\\begin{array}{l} {a_{i} = \\alpha(\\mathbf{q},\\mathbf{k}\_{i})} \\\\ \\end{array}$$  

(2.8)

注意力权重通过对得分应用软最大函数计算：

$$\\begin{array}{l} {\\mathbf{b} = \\text{softmax}(\\mathbf{a})} \\\\ \\end{array}$$  

(2.9)

每个元素 b_i 的计算方式为：

$$\\begin{array}{l} {b\_{i} = \\frac{\\exp(a\_{i})}{\\sum\_{j}{\\exp(a\_{j})}}} \\\\ \\end{array}$$  

(2.10)

输出是注意力权重与值的加权和：

$$\\begin{array}{l} {\\mathbf{o} = {\\sum\\limits\_{i = 1}^{n}b\_{i}}\\mathbf{v}\_{i}} \\\\ \\end{array}$$  

(2.11)

[Fig. 2.4](#ch2.xhtml#fig2_4) 捕捉了从输入查询到输出的各种向量和标量之间的交互。

![Figure 2.4 Attention mechanism showing query, keys, values, and output vector interactions.](images/fig2_4.jpg)

[Figure 2.4](#ch2.xhtml#b2fig2_4) Attention mechanism showing query, keys, values, and output vector interactions.

注意力机制的设计是为了克服 RNN 编码器-解码器结构所存在的问题。

如图 2.3 所示，注意力机制可以被视为一个拥有键和值的记忆体，以及在有人查询时生成输出的层，输出由 value 的 keys 映射到输入 \[[17](#refbib.xhtml#refbib_17)\]。

形式化地，考虑由 *n* 个键-值对（k[1], v[1]), …, (k[n], v[n]）组成的记忆单元，其中 k[i] ∈ ℝ^(d[k]) 且 v[i] ∈ ℝ^(d[v])。注意力层接收的输入是查询 q ∈ ℝ^(d[q])，输出为 o ∈ ℝ^(d[v])，其形状与值 v 相同。

注意力层使用评分函数 α 计算查询与键之间的相似度，返回对键 k[1], …, k[n] 的得分 a[1], …, a[n]：

$$\\begin{array}{l} {a_{i} = \\alpha(\\mathbf{q},\\mathbf{k}\_{i})} \\\\ \\end{array}$$  

(2.8)

注意力权重通过对得分应用软最大函数计算：

$$\\begin{array}{l} {\\mathbf{b} = \\text{softmax}(\\mathbf{a})} \\\\ \\end{array}$$  

(2.9)

每个元素 b_i 的计算方式为：

$$\\begin{array}{l} {b\_{i} = \\frac{\\exp(a\_{i})}{\\sum\_{j}{\\exp(a\_{j})}}} \\\\ \\end{array}$$  

(2.10)

输出是注意力权重与值的加权和：

$$\\begin{array}{l} {\\mathbf{o} = {\\sum\\limits\_{i = 1}^{n}b\_{i}}\\mathbf{v}\_{i}} \\\\ \\end{array}$$  

(2.11)

[Fig. 2.4](#ch2.xhtml#fig2_4) 捕捉了从输入查询到输出的各种向量和标量之间的交互。

![Figure 2.4 Attention mechanism showing query, keys, values, and output vector interactions.](images/fig2_4.jpg)

[Figure 2.4](#ch2.xhtml#b2fig2_4) Attention mechanism showing query, keys, values, and output vector interactions.

### 2.3.2 基于得分的注意力类型

如前所述，评分函数 α(q, k) 可以采用多种形式，从而催生了多种注意力机制，每种都有其优势。

#### 2.3.2.1 点积（乘积）

点积基于的评分函数最简单，不需要调参 \[[176](#refbib.xhtml#refbib_176)\]。

$$\\begin{array}{l} {\\alpha(\\mathbf{q},\\mathbf{k}) = \\mathbf{q} \\cdot \\mathbf{k}} \\\\ \\end{array}$$  

(2.12)

#### 2.3.2.2 缩放点积或乘积

缩放点积基于的评分函数将点积除以 √d_k，以消除维度 d_k 的影响 \[[254](#refbib.xhtml#refbib_254)\]。根据 Vaswani 等人，随着维度增加，点积会变大，导致 softmax 函数进入极端梯度区域。

$$\\begin{array}{l} {\\alpha(\\mathbf{q},\\mathbf{k}) = \\frac{\\mathbf{q} \\cdot \\mathbf{k}}{\\sqrt{d\_{k}}}} \\\\ \\end{array}$$  

(2.13)

#### 2.3.2.3 线性、MLP 或加性

卢昂等人还尝试将查询和键投射到隐藏层的维度 h，学习权重（W_k, W_q），并使用 sigmoid 函数将它们与值结合，如下所示：

$$\\begin{array}{l} {\\alpha(\\mathbf{q},\\mathbf{k}) = \\mathbf{v}^{\\text{T}}\\tanh(\\mathbf{W}\_{k}\\mathbf{k} + \\mathbf{W}\_{q}\\mathbf{q})} \\\\ \\end{array}$$  

(2.14)

缩放点积或点积基于的评分函数比加性注意力机制更快且更节省内存。

### 2.3.3 基于注意力的序列到序列

在编码器-解码器中加入注意力层并映射到查询、键和值的一般修改如图 2.5 所示，具体为：

1.  使用最后编码器状态作为键 k 和值 v。

2.  使用解码器在时间步 t‑1 的最后状态作为查询 q。

3.  注意力层的输出 o（上下文变量）用于下一个解码状态 t。

![Figure 2.5 Encoder-decoder with attention layer.](images/fig2_5.jpg)

[Figure 2.5](#ch2.xhtml#b2fig2_5) 编码器-解码器带注意力层。

为了更详细地理解流程，考虑法语翻译示例，其中键和值是编码器状态，对应于词 {*J*^′*a**i**m**e*, *l**e**, *t**h**é*, .}，解码器在时间步 t‑1 已生成的词为 *I*, *love*。如图 2.6 所示，解码器在 t‑1 的输出 *love* 作为查询进入注意力层，与键结合生成未归一化的得分 a = α(q, k)，随后归一化得到注意力权重 b。注意力权重再与值（编码器输出）相乘得到上下文变量或输出向量 o。输出 o 再与前一个解码状态结合，生成下一个词 *tea* 在时间步 t。


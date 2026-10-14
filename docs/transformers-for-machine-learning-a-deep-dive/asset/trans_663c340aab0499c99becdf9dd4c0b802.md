
[Figure 5.11](#ch5.xhtml#ch5.xhtml#b5fig5_11) 全局注意力邻接矩阵用于内部 Transformer 构造，适用于 *L* = 12 和 *G* = 3、4、7。行 *i* 对应查询 *i*。带有 • 的列是查询 *i* 关注的键，⋅ 表示缺乏注意（缺失边缘）。

外部 Transformer 构造在已有的 *L* 令牌上额外添加 *g* 个全局令牌。这些额外的令牌是全局的。示例包括变压器中使用的特殊令牌，如 \[CLS\]\[CLS\]。这实际上会创建一个新的邻接矩阵 *B*，它在 *A* 前面添加 *g* 行和列以包含特殊令牌。这里 *B*(*i*, :) = *B*(:,*i*) = 1，其中 *i* = 1,…, *g*，且 *B*(*g* + *i*, *g* + *j*) = *A*(*i*, *j*)，其中 *i* 和 *j* = 1,…, *L*。扩展后的邻接矩阵 *B* 如 [Fig. 5.12](#ch5.xhtml#fig5_12) 所示。

![Figure 5.12 Global attention adjacency matrix for the external transformer construction, for L = 9 and g = 3. Row i corresponds to query i. Columns with a • are keys that query i attends to and ⋅ represents a lack of attention (a missing edge).](images/fig5_12.jpg)

[Figure 5.12](#ch5.xhtml#b5fig5_12) 全局注意力邻接矩阵用于外部 Transformer 构造，适用于 *L* = 9 和 *g* = 3。行 *i* 对应查询 *i*。带有 • 的列是查询 *i* 关注的键，⋅ 表示缺乏注意（缺失边缘）。

最后，一个组合了随机、滑动窗口和全局注意力（外部构造）的邻接矩阵示例如 [Fig. 5.13](#ch5.xhtml#fig5_13) 所示。

![Figure 5.13 Big Bird attention adjacency matrix for the external transformer construction, for L = 12,g = 2,w = 4, and r = 4. Row i corresponds to query i. Columns with a • are keys that query i attends to and ⋅ represents a lack of attention (a missing edge).](images/fig5_13.jpg)

[Figure 5.13](#ch5.xhtml#b5fig5_13) Big Bird 注意力邻接矩阵用于外部 Transformer 构造，适用于 *L* = 12、*g* = 2、*w* = 4 和 *r* = 4。行 *i* 对应查询 *i*。带有 • 的列是查询 *i* 关注的键，⋅ 表示缺乏注意（缺失边缘）。

**高效稀疏矩阵乘法** 通过使邻接矩阵（以及对应的注意力矩阵）稀疏，GPU 提供的加速被移除。这是因为任意稀疏矩阵的乘法在 GPU 上并不高效。然而，矩阵的稀疏性如果被分组为块，则可以在 GPU 上高效乘法 \[[100](#refbib.xhtml#refbib_100)\]。

为此，Big Bird 将查询和键分块，并按块添加稀疏性 \[[292](#refbib.xhtml#refbib_292)\]。选择块大小 *b*，然后将序列长度 *L* 分成 *L*/*b* 个块。于是，原来的 *L* 个查询和键变为 *L*/*b* 个查询和键。这对前面讨论的每种注意力模式都有相对简单的修改：

1. **随机注意** 查询 *i* 关注的键数 *r* 变为查询块关注的键块数 *r*（即块层面的随机数量）。

2. **滑动窗口注意** 查询块 *i* 关注键块 *i* − (*w* − 1)/2 到 *i* + (*w* − 1)/2。

3. **全局注意** 其定义保持不变，只是改为以块为单位而非序列位置来定义。

### 5.2.3 提升多头注意力

我们现在专注于一些改进 Transformer 注意力机制的方法，以提升性能。

#### 5.2.3.1 Talking-heads attention

Vaswani et al \[[254](#refbib.xhtml#refbib_254)\] 表明多头注意力使得 Transformer 能够进行 *h*（注意力头数量）个独立的注意力计算。Talking‑Heads Attention \[[227](#refbib.xhtml#refbib_227)\] 则让注意力头共享信息。它通过在查询‑键乘积（注意力对数） **QK**^(*T_) 与注意力权重 *S**o**f**t**m**a**x*(**Q****K**^(*T_)）之间加入两层线性投影，将它们映射到新的空间。

Talking‑Heads Attention（THA）还将注意力头分为三类：用于查询和键的头、用于值的头、以及用于注意力对数和注意力权重的头。下面详细说明。

请回顾 [第 5.2.1.1 节](#ch5.xhtml#sec5_2_1_1) 中的多头注意力公式，两个长度分别为 *L*[1] 和 *L*[2] 的序列 **X**[1]、 **X**[2] 的多头注意力如下：

$$\\begin{array}{ll} \\mathbf{Q} & {= \\mathbf{X}\_{1}\\mathbf{W}\_{q},\\, \\in {\\mathbb{R}}^{L\_{1} \\times d\_{k} \\times h}} \\\\ \\mathbf{K} & {= \\mathbf{X}\_{2}\\mathbf{W}\_{k},\\, \\in {\\mathbb{R}}^{L\_{2} \\times d\_{k} \\times h}} \\\\ \\mathbf{V} & {= \\mathbf{X}\_{2}\\mathbf{W}\_{v},\\, \\in {\\mathbb{R}}^{L\_{2} \\times d\_{v} \\times h}} \\\\ \\end{array}$$  

(5.56)

where **X**[1] ∈ ℝ^(*L*[1] × *d*)、**X**[2] ∈ ℝ^(*L*[2] × *d*)，**W**[*q*]**W**[*k*] ∈ ℝ^(*d* × *d*[*k*] × *h*)，以及 **W**[*v*] ∈ ℝ^(*d* × *d*[*v*] × *h*)，

$$\\begin{array}{ll} \\mathbf{\\alpha} & {= \\mathbf{Q}\\mathbf{K}^{T}, \\in {\\mathbb{R}}^{L\_{1} \\times L\_{2} \\times h}} \\\\ \\end{array}$$  

(5.57)

$$\\begin{array}{ll} {\\mathbf{A}(\\mathbf{Q},\\mathbf{K})} & {= \\text{softmax}\\left( \\frac{\\mathbf{\\alpha}}{\\sqrt{\\text{d}\_{\\text{k}}}} \\right),\\, \\in {\\mathbb{R}}^{\\text{L}\_{\\text{1}} \\times \\text{L}\_{\\text{2}} \\times \\text{h}}} \\\\ \\end{array}$$  

(5.58)

$$\\begin{array}{ll} {\\mathbf{C}(\\mathbf{Q},\\mathbf{K},\\mathbf{V})} & {= {\\sum\\limits\_{L\_{2}}\\mathbf{A}}(\\mathbf{Q},\\mathbf{K})\\mathbf{V},\\, \\in {\\mathbb{R}}^{L\_{1} \\times d\_{v} \\times h}} \\\\ \\end{array}$$  

(5.59)

其中 *α* 是注意力对数，*A*(**Q**, **K**) 为注意力权重，*C*(**Q**, **K**, **V**) 为“上下文”向量，表示在头部拼接和最终投影层之前的 *h* 个注意力头的输出。

**注意力头的划分** THA 对注意力机制进行如下修改。首先，它将 **Q** 和 **K** 的注意力头维度改为查询‑键注意力头数 *h*[*k*]，将 **V** 的注意力头维度改为值注意力头数 *h*[*v*]。这通过修改生成查询、键和值矩阵的投影矩阵的维度来实现，即 (5.56) 变为

$$\\begin{array}{ll} \\mathbf{Q} & {= \\mathbf{X}\_{1}\\mathbf{W}\_{q},\\, \\in {\\mathbb{R}}^{L\_{1} \\times d\_{k} \\times h\_{k}}} \\\\ \\mathbf{K} & {= \\mathbf{X}\_{2}\\mathbf{W}\_{k},\\, \\in {\\mathbb{R}}^{L\_{2} \\times d\_{k} \\times h\_{k}}} \\\\ \\mathbf{V} & {= \\mathbf{X}\_{2}\\mathbf{W}\_{v},\\, \\in {\\mathbb{R}}^{L\_{2} \\times d\_{v} \\times h\_{v}}} \\\\ \\end{array}$$  

(5.60)

其中 **W**[*q*]**W**[*k*] ∈ ℝ^(*d* × *d*[*k*] × *h*[*k*])，以及 **W**[*v*] ∈ ℝ^(*d* × *d*[*v*] × *h*[*v*])。

**对注意力对数的投影** 接下来，注意力对数 *α* 通过线性层 **W**[*α*] ∈ ℝ^(*h*[*k*] × *h*) 进行投影，混合查询‑键注意力头与注意力对数/权重头；注意力权重则通过线性层 **W**[*A*] ∈ ℝ^(*h* × *h*[*v*]) 进行投影，混合值注意力头与注意力对数/权重头。于是 (5.57)–(5.59) 变为

$$\\begin{array}{l} {\\mathbf{\\alpha} = \\mathbf{Q}\\mathbf{K}^{T}, \\in {\\mathbb{R}}^{L\_{1} \\times L\_{2} \\times h\_{k}}} \\\\ \\end{array}$$  

(5.61)

$$\\begin{array}{l} {\\mathbf{P}\_{\\alpha} = \\mathbf{\\alpha}\\mathbf{W}\_{\\alpha},\\, \\in {\\mathbb{R}}^{L\_{1} \\times L\_{2} \\times h}} \\\\ \\end{array}$$  

(5.62)

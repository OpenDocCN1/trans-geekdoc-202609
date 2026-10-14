
1. 查询按哈希桶排序，同一哈希桶内的元素保持原始顺序。

2. 将排序后的查询分组为每 `m` 个连续查询的块  

$$\begin{array}{l} m = \frac{2L}{\\text{Number~of~buckets}} \\\\ \end{array}$$  

(5.34)

在每个块内，每个位置被允许关注到该块内的其他位置以及前一个块中的位置。这两项修改定义了一个新的键位置集合，查询 *i* 可以关注到的位置：

$${\\widetilde{S}}\_{i} = \\left\\{ {j:\\left\\lfloor \\frac{s\_{i}}{m} \\right\\rfloor - 1 \\leq \\left\\lfloor \\frac{s\_{j}}{m} \\right\\rfloor \\leq \\left\\lfloor \\frac{s\_{i}}{m} \\right\\rfloor} \\right\\},$$  

(5.35)

其中 *s*[*i*] 是位置 *i* 在排序矩阵中的位置。 (5.35) 可用于 (5.31) 计算 LSH 方案下的注意力。

*多轮 LSH* 由于 LSH 固有的随机性，相似的元素很容易分散到不同的桶中。为此，通常采用多轮 LSH。例如，在使用 LSH 近似特征向量时，可能会对向量进行多次哈希以生成 LSH 签名。随后，而不是使用共振相似度比较两个特征向量，而是使用哈明距离比较它们的 LSH 签名。同样，在 Reformer 中可以为查询和键计算多个哈希值，然后将它们组合。

如前所述，查询在位置 *i* 可以关注到的键位置在 *S*[*i*] 中。但如果执行 *n* 轮 LSH，则查询位置 *i* 可以关注到的键位置集合变为  

$$\\begin{array}{l} S\_{i} = {\\underset{r = 1}{\\overset{n}{\\cup}}S\_{i}^{(r)}}, \\\\ \end{array}$$  

(5.36)

其中 *S*[*i*]^((*r*)) = {*j* : *h*^((*r*))(**q**[*i*]) = *h*^((*r*))(**q**[*j*])}。关于按哈希桶排序的查询，(5.35) 变为  

$${\\widetilde{S}}\_{i}^{(r)} = \\left\\{ {j:\\left\\lfloor \\frac{s\_{i}^{(r)}}{m} \\right\\rfloor - 1 \\leq \\left\\lfloor \\frac{s\_{j}^{(r)}}{m} \\right\\rfloor \\leq \\left\\lfloor \\frac{s\_{i}^{(r)}}{m} \\right\\rfloor} \\right\\}.$$  

(5.37)

我们可以类似地更新 (5.31) 以适用多轮 LSH：

$$\\begin{array}{l} a\_{i} = {\\sum\\limits\_{r}^{n}{\\exp}}\\left( {\\log Z(i,S\_{i}^{(r)}) - \\log Z(i,S\_{i})} \\right)a\_{i}^{(r)} \\\\ \end{array}$$  

(5.38)

$$\\begin{array}{l} a\_{i}^{(r)} = {\\sum\\limits\_{j \\in {\\widetilde{S}}\_{i}^{(r)}}{\\exp}}\\left( {\\frac{\\mathbf{q}\_{\\mathbf{i}}\\mathbf{k}\_{j}^{T}}{\\sqrt{d\_{k}}} - m\_{i,j}^{(r)} - \\log Z(i,S\_{i}^{(r)})} \\right)\\mathbf{v}\_{j}} \\\\ \end{array}$$  

(5.39)

$$\\begin{array}{l} m\_{i,j}^{(r)} = \\begin{cases} \\infty & {j \\notin S\_{i}^{(r)}} \\\\ 10^{5} & {\\text{if~}i = j} \\\\ {\\log N\_{i,j}} & \\text{otherwise} \\\\ \\end{cases} \\\\ \end{array}$$  

(5.40)

$$\\begin{array}{l} \\left. N\_{i,j} = \\middle| \\{ r^{\\prime}:j \\in S\_{i}^{(r^{\\prime})}\\} \\right| \\\\ \\end{array}$$  

(5.41)

请注意，在多轮 LSH 的情况下，Reformer 将掩码项修改为包含（并下调）查询位置 *i* 关注到键位置 *i* 的情况。这一修改之所以必要，是因为在 LSH 注意力中 **Q** = **K**，而标准 Transformer 允许位置关注到自身，但在 LSH 中这种自关注是毫无意义的，因为任何位置的哈希值 *h*(**q**[*i*]) 都等于自身。

*可逆层和记忆* Reformer 还通过可逆残差层降低了标准 Transformer 的内存占用。

*残差层* 设计用于在网络深度增加时提升训练误差，同时避免消失梯度问题。通过将神经网络表示为残差函数，可以使训练精度随网络深度增加：

$$\\begin{array}{l} y = x + F(x), \\\\ \end{array}$$  

(5.42)

其中 *x* 为层输入，*y* 为层输出 \[[105](#refbib.xhtml#refbib_105)\]。ResNets 是这些残差层的堆叠。

在标准 Transformer 中，每个 Transformer 层包含多个残差层。例如，一个 Transformer 编码器块包含两个残差块。第一个残差块是多头注意力 \[[254](#refbib.xhtml#refbib_254)\]，随后是层归一化 \[[13](#refbib.xhtml#refbib_13)\]。第二个残差块是位置-wise 全连接网络（FFN） \[[254](#refbib.xhtml#refbib_254)\]，随后是层归一化。注意，层归一化的形式为 *x* + *S**u**b**l**a**y**e**r*(*x*)，其中 *Sublayer* 表示输入子层。第一个残差块的子层是多头注意力，第二个残差块的子层是 FFN 层。

**可逆残差层** 是一种用于图像识别的可逆残差层变体，旨在提供更低的内存占用 \[[94](#refbib.xhtml#refbib_94)\]。每个可逆层接收一对 (*x*[1], *x*[2]) 作为输入，并返回一对 (*y*[1], *y*[2]) 作为输出：

$$\\begin{array}{l} y\_{1} = x\_{1} + F(x\_{2}) \\\\ y\_{2} = x\_{2} + G(y\_{1}) \\\\ \\end{array}$$  

(5.43)

要逆转该层，只需从两边减去残差：

$$\\begin{array}{l} x\_{2} = y\_{2} - G(y\_{1}) \\\\ x\_{1} = y\_{1} - F(x\_{2}) \\\\ \\end{array}$$  

(5.44)

假设我们有一个包含 *n* 个可逆层的堆栈，使得第 *n*^(*t*h) 层的输入是第 *n* − 1 层的输出。公式 (5.43) 和 (5.44) 变为递推关系：

$$\\begin{array}{ll} y\_{1}^{(n)} & {= y\_{1}^{(n - 1)} + F(y\_{2}^{(n - 1)})} \\\\ \\end{array}$$  

(5.45)

$$\\begin{array}{ll} y\_{2}^{(n)} & {= y\_{2}^{(n - 1)} + G(y\_{1}^{(n)})} \\\\ \\end{array}$$  

(5.46)

$$\\begin{array}{ll} y\_{2}^{(n - 1)} & {= y\_{2}^{(n)} - G(y\_{1}^{(n)})} \\\\ \\end{array}$$  

(5.47)

$$\\begin{array}{ll} y\_{1}^{(n - 1)} & {= y\_{1}^{(n)} - F(y\_{2}^{(n - 1)})} \\\\ \\end{array}$$  

(5.48)

因此，层 *n* − 1 的激活可以通过层 *n* 的激活以及层 *n* 的残差 *F* 和 *G* 的值来计算。这也是为什么可逆残差层的激活在反向传播时无需存储，从而降低了模型的记忆使用（不牺牲性能）。

*可逆层在 Transformer 中* 现在我们了解了可逆残差层的概念及其如何节省内存，接下来看它们在 Reformer 中的应用 \[[142](#refbib.xhtml#refbib_142)\]。注意力机制作为残差函数 *F*，位置-wise 全连接网络作为 *G*。层归一化被纳入残差块，因为它的形式为 *x* + *S**u**b**l**a**y**e**r*(*x*)，其中 *Sublayer* 代表相应的残差函数。Ref. \[[142](#refbib.xhtml#refbib_142)\] 表明，使用可逆残差层的 Transformer 与标准 Transformer 具有相同的性能。

#### 5.2.2.3 Performer

Performer \[[53](#refbib.xhtml#refbib_53)\] 模型通过一种称为 *Fast Attention Via positive Orthogonal Random features* (FAVOR+) 的方法降低注意力机制的复杂度。Performer 在前置注意力模式之前并不预先偏向注意力机制，而是使用核函数来近似 softmax 计算。

**注意力作为核** 通过重写公式 (5.23) 的自注意力，可以明显看到核形式：

$$\\begin{array}{ll} Attn(\\mathbf{Q},\\mathbf{K},\\mathbf{V}) & {= \\text{softmax}\\left( \\frac{\\mathbf{Q}\\mathbf{K}^{\\text{T}}}{\\sqrt{\\text{d}\_{\\text{k}}}} \\right)\\mathbf{V}} \\\\ \\end{array}$$  

(5.49)



与具有连续输入函数的线性 RPM 相比，在这种情况下，参数可以是相应脉冲特性的纵坐标。

[Table 4.2](#chapter4.xhtml#t4_2b)

|  |
| --- |
| *k* || 1 || 2 || 3 || 4 || 5 || 6 || 7 || 8 || 9 || 10 |
| *x*\[*k*\] || 2.5 || 3.5 || 5.7 || 2.8 || 2.1 || 1.9 || 1.7 || 2.1 || 3.1 || 4.4 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| *x*\[*k* − 1\] || 1.8 || 2.5 || 3.5 || 5.7 || 2.8 || 2.1 || 1.9 || 1.7 || 2.1 || 3.1 |
|  |

![Figure 4.6](images/fig4_6.jpg)

[Figure 4.6](#chapter4.xhtml#f4_6b)

![Figure 4.7](images/fig4_7.jpg)

[Figure 4.7](#chapter4.xhtml#f4_7b)

### 4.2.4 具有幂非线性的非线性动态模型

大多数实际对象本质上是非线性的。在其输入的小幅变化下，非线性对象可能表现出“几乎”线性的特性。一种用“单输入-集合输出”模型描述实际对象的非线性特性的方法是基于用函数幂级数对其进行近似。这样的级数的元素代表不同结构的幂泛函，其取决于对象的非线性特性以及输入函数的特性。特别地，如果对象的非线性是 *连续函数* 且对象的输入信号是 *连续时变函数*，则此类对象的 RPM 可以由函数 Volterra 级数 \[177, [184](#refbib.xhtml#r184)\] 定义。

考虑一个在时间区间 `𝒯[t] = [0, t]` 上运行并由连续泛函 `ℬ(x(τ)) | τ ∈ 𝒯[t])` 刻画的动态系统。设输入向量 `x(τ) = {x[1](τ),…,x[n](τ)}` 属于连续时变函数空间 `𝒳[𝒯[T]]`。根据 \[[100](#refbib.xhtml#r100), 146, 184, [185](#refbib.xhtml#r185)\]，泛函 `ℬ(x(τ))`（等价地，RPM 输出 `$\\hat{\\mathbf{y}}(t)$`）可以表示为收敛的函数级数，即

$$\\begin{aligned} {\\hat{\\mathbf{y}}(t)} & \\left. = \\mathcal{B}(\\mathbf{x}(\\tau))\\, \\middle| \\,\\tau \\in \\mathcal{T}\_{t}) = \\right. \\\\ {= {\\sum\\limits\_{h = 1}^{\\infty}{\\int\_{0}^{t}\\cdots}}} & {{\\int\_{0}^{t}W^{(h)}}(t - \\tau\_{1},\\ldots,t - \\tau\_{h}) \\times} \\\\ {\\times \\mathbf{x}^{(h)}} & {(\\tau\_{1},\\ldots,\\tau\_{h})d\\tau\_{1}\\cdots d\\tau\_{h}.} \\\\ \\end{aligned}$$

(4.29)

这里 `x^{(h)}(τ[1],…,τ[h])` 表示由字典序排列的乘积 `{x[i[1]](τ[j[1]])⋯x[i[n]](τ[j[h]])}` 组成的向量，其中 $(i\_{1},\\ldots,i\_{n}) \\in \\overline{1,n}$ 且 $(j\_{1},\\ldots,j\_{h}) \\in \\overline{1,h}.$ 向量 `x^{(h)}` 的维数为

$$\\begin{array}{r} {l(n,h) = n^{h}.} \\\\ \\end{array}$$

(4.30)

矩阵 `W^{(h)}(t[1],…,t[h])` 的维数为 (`m × l(m, h)`)，其元素是多维权重函数（脉冲特性）`w[k[h]]^{(h)}(t[1],…,t[h])`，其中 $k\_{h} = \\overline{1,l(n,h)}$。

[Figure 4.8](#chapter4.xhtml#f4_8) 说明了函数级数 (4.28) 的结构。 [Fig. 4.8](#chapter4.xhtml#f4_8) 中的块 `∏[h]` 表示向量 `x` 的幂为 `h` 的元素的字典序排列乘积。

![Figure 4.8](images/fig4_8.jpg)

[Figure 4.8](#chapter4.xhtml#f4_8b)

权重函数包含区间类型的随机参数 `a^{(h)}`，即

$$\\begin{array}{r} {\\mathbf{a}^{(h)} \\in \\mathcal{A}^{(h)} = \\left\\{ \\mathbf{a}\_{-}^{(h)} \\leq \\mathbf{a}^{(h)} \\leq \\mathbf{a}\_{+}^{(h)} \\right\\}.} \\\\ \\end{array}$$

(4.31)

由于参数是随机的，它们在相应区间上具有 PDF `P^{h}(a^{(h)})`。

泛函 `ℬ` (4.2.4) 通常可以写成具有结构化权重矩阵（脉冲特性）的函数级数。在结构化中，我们指的是线性动态和非线性静态操作的序列。 [Fig. 4.11(a)](#chapter4.xhtml#f4_11) 中显示的 RPM 的框图，其中每个通道代表线性动态块和幂非线性的串联连接。该模型的输出由函数 Volterra 级数的以下修改定义：

$$\\begin{aligned} {\\hat{\\mathbf{y}}(t)} & \\left. = \\mathcal{B}(\\mathbf{x}(\\tau))\\, \\middle| \\,\\tau \\in \\mathcal{T}\_{t}) = \\right. \\\\ & {= {\\sum\\limits\_{h = 1}^{\\infty}\\left( {{\\int\_{0}^{t}W^{(h)}}(t - \\tau)\\,\\mathbf{x}(\\tau)\\, d\\tau} \\right)^{h}}.} \\\\ \\end{aligned}$$

(4.32)

对于一维 RPM，上面的等式取以下形式

$$\\begin{array}{r} {\\hat{y}(t) = {\\sum\\limits\_{h = 1}^{\\infty}{\\int\_{0}^{t}\\cdots}}{\\int\_{0}^{t}{\\prod\\limits\_{i = 1}^{h}\\,}}\\left( {w(t - \\tau\_{i})\\, x(\\tau\_{i})d\\tau\_{i}} \\right).} \\\\ \\end{array}$$

(4.33)

[Fig. 4.11(b)](#chapter4.xhtml#f4_11) 中的框图对应于 RPM，其中每个通道中线性操作和非线性操作的顺序相反：首先输入经过幂变换，然后进行动态线性变换。RPM 输出由函数 Volterra 级数的另一种修改描述：

$$\\begin{array}{r} {\\hat{\\mathbf{y}}(t) = {\\sum\\limits\_{h = 1}^{\\infty}{\\int\_{0}^{t}W}}(t - \\tau)\\mathbf{x}^{(h)}(\\tau)\\, d\\tau.} \\\\ \\end{array}$$

(4.34)

这里，向量 `x^{(h)}(τ)` 由向量 `x(τ)` 的元素的所有可能乘积的字典序排列元素组成。

![Figure 4.11](images/fig4_11.jpg)

[Figure 4.11](#chapter4.xhtml#f4_11b)

考虑具有有限记忆 `K` 的 RPM；该模型在离散时间 `t[k]` 处以步长 `Δ` 测量输入和输出。令 `k = [t[k]/Δ]`，

$$\\begin{aligned} {\\hat{\\mathbf{y}}\\lbrack k\\rbrack = {\\sum\\limits\_{h = 1}^{\\infty}{\\sum\\limits\_{(n\_{1},\\ldots,n\_{h}) = 0}^{K}W^{(h)}}}\\lbrack n\_{1},\\ldots,} & {n\_{h}\\rbrack\\,\\mathbf{x}^{(h)}\\lbrack k - n\_{1},\\ldots,k - n\_{h}\\rbrack,} \\\\ {k \\geq} & {K.} \\\\ \\end{aligned}$$

(4.35)

向量 `x^{(h)}[k − n[1],…,k − n[h]]` 具有元素 `x[i[1]][k − n[1]]⋯x[i[n]][k − n[h]]`，它们是 $(i\_{1},\\ldots,i\_{n}) = \\overline{1,n}$ 元素在时间 $(n\_{1},\\ldots,n\_{h}) = \\overline{0,K}$ 处对向量 `x` 的所有可能乘积的字典序排列。向量 `x^{(h)}[k − n[1],…,k − n[h]]` 的维数为

$$\\begin{array}{r} {l(n,h) = \\frac{(n\\, K + h - 1)!}{h!(n\\, k - 1)!}.} \\\\ \\end{array}$$

(4.36)

参数 `K` 定义了 RPM 的记忆容量，即

$$\\begin{array}{r} {W^{(h)}\\lbrack n\_{1},\\ldots,n\_{h}\\rbrack = \\left\\{ \\begin{aligned} {W^{(h)}\\lbrack n\_{1},\\ldots,n\_{h}\\rbrack} & {\\text{if~all}\\,(n\_{1},\\ldots,n\_{h}) \\leq K,} \\\\ 0 & {\\text{if~at~least~one}\\, n\_{j} > K.} \\\\ \\end{aligned}~ \\right.} \\\\ \\end{array}$$

(4.37)

矩阵 `W^{(h)}[n[1],…,n[h]]` 的元素是离散随机权重函数（脉冲特性）`w_{i,k_{h}}^{(h)}[n_{1},…,n_{h}],  i = \overline{1,m};  k_{h} = \overline{1,l(n,h)}.` 它们反映了 RPM 的动态和非线性特性。需要注意的是，非线性特性是用多维函数（脉冲特性）表述的，而不是用结构可表示的非线性元件表述的。

脉冲特性 `w[i, k[h]]^{(h)}[n[1],…,n[h]]` 为区间类型，即

$$\\begin{array}{r} {w\_{i,k\_{h}}^{(h)}\\lbrack n\_{1},\\ldots,n\_{h}\\rbrack \\in \\mathcal{W}\_{i,k\_{h}}^{(h)} = \\left\\lbrack {{\\widetilde{w}}\_{i,k\_{h}}^{(h, - )}\\lbrack n\_{1},\\ldots,n\_{h}\\rbrack,\\,{\\widetilde{w}}\_{i,k\_{h}}^{(h, + )}\\lbrack n\_{1},\\ldots,n\_{h}\\rbrack} \\right\\rbrack.} \\\\ \\end{array}$$

(4.38)


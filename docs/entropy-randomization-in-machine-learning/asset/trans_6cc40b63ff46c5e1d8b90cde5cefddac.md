

$$\\begin{array}{r} {\\left. C_{i} \\right.\\sim\\frac{1}{V_{i}}{\\int_{V_{i}}w}(\\mathbf{x})d\\mathbf{x}.} \\\\ \\end{array}$$  

(8.16)

因此，

$$\\begin{array}{r} {\\left. C_{i} \\right.\\sim w(\\mathbf{x})\\quad\\text{if}\\,\\mathbf{x} \\in V_{i}.} \\\\ \\end{array}$$  

(8.17)

记 ${\\overline{\\xi}}^{i},\\, i = \\overline{1,N},$ 为服从基本立方体上均匀分布的独立随机向量。此类向量的密度在基本立方体内部为 1/*V*[*i*]，外部为 0。这些向量可使用方法 (8.6, 8.7) 生成。

设 *β* 为不依赖于 $\\left\\{ {\\overline{\\xi}}^{i} \\right\\}$ 的整数随机变量，取值为 1, …, *N*，其概率为 *p*[*i*] = *C*[*i*]*V*[*i*]。则生成的向量具有形式

$$\\begin{array}{r} {\\mathbf{x} = {\\sum\\limits_{i = 1}^{N}{\\overline{\\xi}}^{i}}\\Lambda(\\beta = i),} \\\\ \\end{array}$$  

(8.18)

其中 *Λ*(*A*) 表示集合 *A* 的示性函数。向量 **x** 的 PDF 可写为

$$\\begin{aligned} & \\left. P(\\mathbf{x} = d\\mathbf{x}) = {\\sum\\limits_{i = 1}^{N}P}(\\mathbf{x} = d\\mathbf{x}\\, \\middle| \\,\\beta = i)P(\\beta = i) = \\right. \\\\ & {\\left. \\text{\\quad\\quad}{\\sum\\limits_{i = 1}^{N}C_{i}}d\\mathbf{x}\\Lambda(V_{i}) \\right.\\sim{\\sum\\limits_{i = 1}^{N}w}(\\mathbf{x})d\\mathbf{x}\\Lambda(V_{i}).} \\\\ \\end{aligned}$$  

(8.19)

## 8.2.2 紧集 *Q*

### 1. *Q*—平行六面体 Π

考虑集合 *P**i* = {**x**:**a**≤**x**≤**b**}，其中 **a** 和 **b** 为给定向量。用 $l_{i} = b_{i} - a_{i},\\, i = \\overline{1,n}.$ 表示其边的长度。在该集合上引入非均匀格网，可按每个坐标固定 *K* 个元素设计，也可按固定步长 *h* 设计。前一种情况下，各坐标步长不同，即

$$\\begin{array}{r} {h_{i} = l_{i}/K;} \\\\ \\end{array}$$  

(8.20)

后一种情况下，各格网元素数不同，即

$$\\begin{array}{r} {K_{i} = l_{i}/h.} \\\\ \\end{array}$$  

(8.21)

事实上，固定步长的情况已在上面讨论过。因此，我们将研究前一种具有可变步长的情况。由于格网在每个坐标上具有相同数量的元素，全部基本平行六面体 *Π*[*i*] 的数量为 *N* = *K*^(*n*)。基本平行六面体具有相同的体积

$$\\begin{array}{r} {V = {\\prod\\limits_{i = 1}^{n}h_{i}}.} \\\\ \\end{array}$$  

(8.22)

在每个平行六面体内部，引入另一个每个坐标有 *M* 个元素的格网。则每个坐标的格网步长为

$$\\begin{array}{r} {\\eta_{i} = h_{i}/M,} \\\\ \\end{array}$$  

(8.23)

第 *j* 个内部子平行六面体 *π*[*i*]^(*j*) 的体积为

$$\\begin{array}{r} {v = {\\prod\\limits_{i = 1}^{n}\\eta_{i}}.} \\\\ \\end{array}$$  

(8.24)

（这里 *j* 表示第 *i* 个基本平行六面体内部的内部子平行六面体的索引）。基本平行六面体 *Π*[*i*] 内部全部内部子平行六面体 *π*[*i*]^(*j*) 的数量为

$$\\begin{array}{r} {L = M^{n}.} \\\\ \\end{array}$$  

(8.25)

在 *π*[*i*]^(*j*) 中任取一点 **x**[*i*]^(*j*) 并计算值

$$\\begin{array}{r} {C_{i} = \\frac{1}{M}{\\sum\\limits_{j = 1}^{M}w}(\\mathbf{x}_{i}^{j}).} \\\\ \\end{array}$$  

(8.26)

当 *M* 足够大时，

$$\\begin{array}{r} {\\left. C_{i} \\right.\\sim\\frac{1}{V_{i}}{\\int_{V_{i}}w}(\\mathbf{x})d\\mathbf{x}.} \\\\ \\end{array}$$  

(8.27)

该生成过程的其余部分与单位立方体的情况组织方式相同；见上文。

### 2. 任意紧集 *Q*

在这种情况下，将集合 *Q* 置于平行六面体 *Π* = {**x**:**a**≤**x**≤**b**} 中。边的定义可以任意，但需满足 *Q* ⊂ *Π*。一种更高效的生成随机向量的方法是将集合 *Q* 置于形为平行六面体 *Π*^(\*)* 的包围盒中。这些可能性在 [Figs. 8.1(a)](#chapter8.xhtml#f8_1) 和 [8.1(b)](#chapter8.xhtml#f8_1) 中示出 (*a*—任意平行六面体 *Π*，*b*—包围盒)。显然，包围盒的构造需要预先计算极值点 (*A*, *B*, *C*, *D*)。

![Figure 8.1](images/fig8_1.jpg)

[Figure 8.1](#chapter8.xhtml#f8_1b)

回想一下，PDF *w*(**x**) 在集合 *Q* 上定义。引入形如

$$\\begin{array}{r} {W(\\mathbf{x}) = \\left\\{ \\begin{aligned} {w(\\mathbf{x})} & {\\text{if}\\,\\mathbf{x} \\in Q,} \\\\ 0 & {\\text{if}\\,\\mathbf{x} \\in \\Pi\\smallsetminus Q.} \\\\ \\end{aligned}~ \\right.} \\\\ \\end{array}$$  

(8.28)

的辅助 PDF。显而易见，平行六面体 Π 构成了 PDF *W*(**x**) 的定义域。我们将使用第 2 项的生成过程对 PDF *W*(**x**) 进行处理。注意 *W*(**x**) = 0 在基本平行六面体 *Π*[*i*] 上以及在集合 *Π*^(\*) ∖ *Q* 内的内部子平行六面体 *π*[*i*]^(*j*) 上。因此，由 (8.2.1) 得 *P*(**x** = *d***x**) = 0。

## 8.3 给定概率密度函数的近似

针对给定概率密度函数的随机向量生成过程具有近似 *accuracy* 和格网 *step* 这样的重要方面。

### 1. 近似精度估计

考虑 PDF *w*(**x**)，其中 **x** ∈ *Q* ⊂ *R*^(*n*). 集合 *Q* 是紧的，即具有非零体积 *V*[*Q*] ≠ 0。假设集合 *Q* 置于 *n*\-维平行六面体 *Π* 中。函数 *w*(**x**) 是平方可积的。

为了生成具有 PDF *w*(**x**) 的随机向量，将其用分段常数函数 *g*(**x**)， **x** ∈ *Π* 近似。此近似的质量由泛函

$$\\begin{array}{r} \\left. J(A) = \\middle| {\\int_{A}\\left( {w(\\mathbf{x}) - g(\\mathbf{x})} \\right)}d\\mathbf{x} \\middle| , \\right. \\\\ \\end{array}$$  

(8.29)

衡量，其中 *A* 表示 *Π* 中任意集合。

在体积为 *V*[*Π*] 的集合 Π 上定义每个坐标步长为 $h_{k},\\, k = \\overline{1,n},$ 的均匀格网。该格网的每个元素都是边长为 *h*[*k*] 的基本平行六面体 $\\Pi_{i},\\, i = \\overline{1,N},$。不失一般性，假设

$$\\begin{array}{r} {N = \\frac{V_{\\Pi}}{V_{\\Pi_{i}}} = \\frac{V_{\\Pi}}{\\prod\\limits_{k = 1}^{n}h_{k}}.} \\\\ \\end{array}$$  

(8.30)

并且该值是整数。注意所有基本平行六面体 *Π*[*i*] 具有相同的体积。在每个集合 *Π*[*i*] 中，用常数 *B*[*i*] 替换函数 *w*(**x**) 。对所有基本平行六面体执行此操作后，得到分段常数线性逼近函数 *g*(**x**).

考虑 *Π* 中的某一集合 *A* ∈ *Π*。它被基本平行六面体的并集覆盖，即

$$\\begin{array}{r} {A = {\\underset{i = 1}{\\overset{N}{\\cup}}\\Pi_{i}}.} \\\\ \\end{array}$$  

(8.31)

然后，利用 Cauchy–Bunyakovsky–Schwarz 不等式，写出上界

$$\\begin{array}{r} {J(A) \\leq \\sqrt{{\\int_{A}\\left( {w(\\mathbf{x}) - g(\\mathbf{x})} \\right)^{2}}d\\mathbf{x}{\\int_{A}\\Lambda}(A)d\\mathbf{x}}.} \\\\ \\end{array}$$  

(8.32)

这里 *Λ*(*A*) 表示集合 *A* 的示性函数。由 (8.32) 可得

$$\\begin{array}{r} {{\\int_{A}\\left( {w(\\mathbf{x}) - g(\\mathbf{x})} \\right)^{2}}d\\mathbf{x} \\leq {\\sum\\limits_{i = 1}^{N}{\\int_{\\Pi_{i}}\\left( {w(\\mathbf{x}) - B_{i}} \\right)^{2}}}d\\mathbf{x}.} \\\\ \\end{array}$$  

(8.33)

因此，

$$\\begin{array}{r} {\\sup\\limits_{A}J(A) \\leq {\\sum\\limits_{i = 1}^{N}{\\int_{\\Pi_{i}}\\left( {w(\\mathbf{x}) - B_{i}} \\right)^{2}}}d\\mathbf{x}.} \\\\ \\end{array}$$  

(8.34)

作为结果，常数 *B*[1], …, *B*[*N*] 的最佳估计可通过最小化泛函


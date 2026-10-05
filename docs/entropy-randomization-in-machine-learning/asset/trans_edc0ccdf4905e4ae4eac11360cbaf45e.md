

因此，区域指标在各区间的分布，称为*熵分解*，是优化问题的解

$$\\begin{array}{r} \\left. H(\\mathbb{S})\\Rightarrow\\max,\\quad\\mathbb{S} \\in D, \\right. \\\\ \\end{array}$$  

(2.78)

其中

$$\\begin{array}{r} {D = \\left\\{ S\_{ij} \\middle| {\\sum\\limits\_{j = 1}^{M\_{i}}S\_{ij}} = S\_{i};\\,\\,{\\sum\\limits\_{j = 1}^{M\_{i}}q\_{ijk}}(\\mathbb{S}) = Q\_{ik}(S),\\quad i = \\overline{1,I},\\,\\, k = \\overline{1,r} \\right\\}.} \\\\ \\end{array}$$  

(2.79)

在此一般表述中，所有区域和区都通过相应的生产函数相互关联。另一个极端情况是所有区域和区都是孤立的，即区域和区生产函数仅依赖于其自身区域或区的状态指标：

$$\\begin{array}{r} {q\_{ijk}(\\mathbb{S}) = q\_{ijk}(S\_{ij}),\\quad Q\_{ik}(\\mathbf{S}) = Q\_{ik}(S\_{i});\\,\\, i = \\overline{1,I}\\,\\, k = \\overline{1,r}.} \\\\ \\end{array}$$  

(2.80)

对于孤立区域，熵分解问题 (2.78) 归结为 *I* 个形式为的优化问题

$$\\begin{array}{r} \\left. H\_{i}(\\mathbb{S}\_{i})\\Rightarrow\\max,\\quad\\mathbb{S}\_{i} \\in D\_{i}, \\right. \\\\ \\end{array}$$  

(2.81)

其中

$$\\begin{array}{r} {H\_{i}(\\mathbb{S}\_{i}) = - {\\sum\\limits\_{j = 1}^{M\_{i}}S\_{ij}}\\ln\\frac{S\_{ij}}{a\_{ij}e},} \\\\ \\end{array}$$  

(2.82)

$$\\begin{array}{r} {D\_{i} = \\left\\{ S\_{ij} \\middle| {\\sum\\limits\_{j = 1}^{M\_{i}}S\_{ij}} = S\_{i},\\,\\,{\\sum\\limits\_{j = 1}^{M\_{i}}q\_{ijk}}(S\_{ij}) = Q\_{ik}(S\_{i}),\\quad i = \\overline{1,I},\\,\\, k = \\overline{1,r} \\right\\}.} \\\\ \\end{array}$$  

(2.83)

这些区的生产函数 `q[i j k]` 形成其状态指标的非线性函数。然而，如果经济处于均衡的邻域，则生产函数的线性表示就成为这些函数的完全充分描述，即

$$\\begin{array}{r} {q\_{ijk}(S\_{ij}) = c\_{ijk}S\_{ij},\\text{\\quad\\quad}i = \\overline{1,I},\\,\\, k = \\overline{1,r}.} \\\\ \\end{array}$$  

(2.84)

这里 `c[i j k]` 表示区 (`i`, `j`) 中商品 `k` 的特定产出。在这种情况下，可行集 `D[i]` (2.83) 由线性等式系统给出

$$\\begin{array}{r} {D\_{i} = \\left\\{ S\_{ij} \\middle| {\\sum\\limits\_{j = 1}^{M\_{i}}S\_{ij}} = S\_{i};\\,\\,\\,{\\sum\\limits\_{j = 1}^{M\_{i}}c\_{ijk}}S\_{ij} = Q\_{ik}(S\_{i}),\\quad i = \\overline{1,I},\\,\\, k = \\overline{1,r} \\right\\}.} \\\\ \\end{array}$$  

(2.85)

考虑具有线性生产函数的熵分解过程的特殊性，针对一个区域 (`I` = 1) 和一种资源类型 (`r` = 1)：

$$\\begin{aligned} {H\_{1}(\\mathbb{S}\_{1})} & \\left. = - {\\sum\\limits\_{j = 1}^{M\_{1}}S\_{1j}}\\ln\\frac{S\_{1j}}{a\_{1j}e}\\Rightarrow\\max, \\right. \\\\ {\\sum\\limits\_{j = 1}^{M\_{1}}S\_{1j}} & {= S\_{1},\\quad{\\sum\\limits\_{j = 1}^{M\_{1}}c\_{1j1}}S\_{1j} = Q\_{11}(S\_{1}).} \\\\ \\end{aligned}$$  

(2.86)

该问题由以下参数表征：先验概率 `a[1 j]`；区域的状态指标 `S[1]`；特定生产率 `c[1 j 1]` 和区域的生产函数 `Q[11]`。问题的解，即区域状态指标在其各区间的熵最优分布，取决于这些参数。

引入新变量以略微减少问题中的参数个数。记

$$\\begin{array}{r} {w\_{1j} = \\frac{S\_{1j}}{S\_{1}},\\text{\\quad\\quad}h\_{1j1} = \\frac{c\_{1j1}}{Q\_{11}(S\_{1})},\\,\\, j = \\overline{1,M\_{1}}.} \\\\ \\end{array}$$  

(2.87)

如果区域指标 `S[1]` 已给定，则变量 `h[1 j 1]` 也已固定。以此记号，熵分解问题可写为

$$\\begin{aligned} {H(\\mathbf{w})} & \\left. = - {\\sum\\limits\_{j = 1}^{M}w\_{j}}\\ln\\frac{w\_{j}}{a\_{j}e}\\Rightarrow\\max, \\right. \\\\ {\\sum\\limits\_{j = 1}^{M}w\_{j}} & {= 1;\\quad{\\sum\\limits\_{j = 1}^{M}h\_{j}}\\, w\_{j} = q,} \\\\ \\end{aligned}$$  

(2.88)

其中 `q` = 1/`S[1]` 且下标 `i` = `k` = 1 被省略。

使用拉格朗日乘数法求解该问题。拉格朗日函数形式为

$$\\begin{array}{r} {L(\\mathbf{w},\\mu,\\lambda) = H(\\mathbf{w}) + \\mu(1 - {\\sum\\limits\_{j = 1}^{M}w\_{j}}) + \\lambda(q - {\\sum\\limits\_{j = 1}^{M}h\_{j}}\\, w\_{j}).} \\\\ \\end{array}$$  

(2.89)

拉格朗日函数的 一阶最优性条件给出方程

$$\\begin{aligned} w\_{j} & {= a\_{j}\\exp( - \\mu - \\lambda\\, h\_{j}) = a\_{j}\\, u\\, z^{h\_{j}};} \\\\ & {u = \\exp( - \\mu),\\, z = \\exp( - \\lambda).} \\\\ \\end{aligned}$$  

(2.90)

考虑到 (2.88) 中的平衡和资源约束，写出拉格朗日乘数 `λ` 的方程：

$$\\begin{array}{r} {{\\sum\\limits\_{j = 1}^{M}a\_{j}}\\, z^{h\_{j}}\\,(h\_{j} - q) = 0,\\text{\\quad\\quad}j = \\overline{1,M}.} \\\\ \\end{array}$$  

(2.91)

设

$$\\begin{array}{r} {c\_{j} = a\_{j}(h\_{j} - q),\\text{\\quad\\quad}j = \\overline{1,M},} \\\\ \\end{array}$$  

(2.92)

并将方程 (2.91) 变换为

$$\\begin{array}{r} {f(z) = {\\sum\\limits\_{j = 1}^{M}c\_{j}}z^{h\_{j}} = 0,\\quad z > 0.} \\\\ \\end{array}$$  

(2.93)

按如下方式排序参数 `h[j]`：

$$\\begin{array}{r} {0 < h\_{1} < h\_{2} < \\cdots < h\_{l} < q < h\_{l + 1} < \\cdots < h\_{M}.} \\\\ \\end{array}$$  

(2.94)

于是，

$$\\begin{array}{r} {c\_{j} < 0\\quad\\text{for~}j = \\overline{1,l}\\quad\\text{and}\\quad c\_{j} > 0\\quad\\text{~for~}j = \\overline{l+1,M}.} \\\\ \\end{array}$$  

(2.95)

考虑具有任意符号系数 `c[j]` 的方程 (2.93)。注意它有根 `z[0]` = 0。因此，该方程可写为

$$\\begin{array}{r} {f(z) = z^{h\_{1}}f\_{1}(z) = 0,\\,\\,\\, z > 0,} \\\\ \\end{array}$$  

(2.96)

其中函数

$$\\begin{array}{r} {f\_{1}(z) = c\_{1} + {\\sum\\limits\_{j = 2}^{M}c\_{j}}z^{h\_{j} - h\_{1}}} \\\\ \\end{array}$$  

(2.97)

没有零根。

现在考虑在系数 `c[j]` 按照 (2.95) 排序的情况下的方程 (2.96, 2.97)，即

$$\\begin{array}{r} {c\_{j} < 0\\,\\,\\text{for}\\,\\, j = 1,\\ldots,l,\\text{\\quad\\quad}c\_{j} > 0\\,\\,\\text{for}\\,\\, j = l + 1,\\ldots,M.} \\\\ \\end{array}$$  

(2.99)

因此，已证明在条件 (2.95) 下，方程 (2.98) 具有唯一正解。

### 表 2.1：区域状态指标

| no. | `c̃[j]` | `S[j]` | `S̃[j]` |
| --- | --- | --- | --- |
| 1 | 0.035 | 0.0098 | 0.0144 |
| 2 | 0.018 | 0.0251 | 0.0247 |
| 3 | 0.035 | 0.0098 | 0.0149 |
| 4 | 0.018 | 0.0253 | 0.0245 |
| 5 | 0.028 | 0.0145 | 0.0213 |
| 6 | 0.015 | 0.0296 | 0.0259 |
| 7 | 0.038 | 0.0083 | 0.0142 |
| 8 | 0.029 | 0.0137 | 0.0222 |
| 9 | 0.039 | 0.0079 | 0.0144 |
| 10 | 0.047 | 0.0051 | 0.0102 |
| 11 | 0.035 | 0.0098 | 0.0175 |
| 12 | 0.026 | 0.0161 | 0.0238 |
| 13 | 0.036 | 0.0093 | 0.0168 |
| 14 | 0.028 | 0.0145 | 0.0214 |
| 15 | 0.032 | 0.0116 | 0.0193 |
| 16 | 0.038 | 0.0083 | 0.0126 |
| 17 | 0.045 | 0.0057 | 0.0098 |
| 18 | 0.037 | 0.0088 | 0.0151 |
| 19 | 0.028 | 0.0145 | 0.0185 |
| 20 | 0.038 | 0.0083 | 0.0097 |
| 21 | 0.038 | 0.0104 | 0.0079 |
| 22 | 0.020 | 0.0225 | 0.0292 |
| 23 | 0.024 | 0.0181 | 0.0243 |
| 24 | 0.038 | 0.0084 | 0.0097 |
| 25 | 0.007 | 0.0459 | 0.0433 |
| 26 | 0.028 | 0.0145 | 0.0169 |

### 2.3.4 缺失数据的随机恢复方法

#### 1. 缺失数据随机恢复程序的结构


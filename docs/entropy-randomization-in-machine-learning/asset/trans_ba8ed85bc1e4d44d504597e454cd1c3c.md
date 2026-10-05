

[表 7.3:](#chapter7.xhtml#t7_3b) 计算结果。

|  |
| --- |
| Var || *J*[*τ*]^(\*) || *θ*[*τ*]^(\*) || *ε*[*τ*] || *r̂*[*τ*] || *P̂*[*τ*] || *t*, s |
| 1 || 0.0025 || \-2.4457\-0.0537 || 0.0025 || 0.1200 ||  ≈ 1.0 || 1576 |
| --- | --- | --- | --- | --- | --- | --- |
| 2 || 0.0001 || \-2.4042\-0.0634 || 0.0001 || 0.0051 ||  ≈ 1.0 || 1573 |
|  |

![Figure 7.6](images/fig7_6.jpg)

[图 7.6](#chapter7.xhtml#f7_6b)

## 7.3 利用蒙特卡罗方法计算多维积分

由经验平衡约束诱导的拉格朗日乘子方程包含在单位体积域上的积分分量 (7.13, 7.14)。

这些积分将使用随机生成器按如下方式用蒙特卡罗方法计算。对于向量 **w** ∈ *I*^(*n*) ⊂ *R*^(*n*) 的每个元素，它产生长度为 *M* 的随机数序列以形成 *N* = *M*^(*n*) 个随机向量（点） $\\mathbf{w}^{(i)},\\, i = \\overline{1,N}.$ 细节可参见 \[[147](#refbib.xhtml#r147)\]。

蒙特卡罗方法的一个主要困难是估计随机数序列长度 *M*（随机点数 *N*）以便以给定误差 *δ* 计算积分是否足够。显然，这种估计具有随机性，应配备相应的概率。

为了获得这些估计，将比较蒙特卡罗方法的两种实现策略。第一种策略涉及在 *I*^(*n*) 中从每个元素 *w*[*k*] 的均匀格子 𝕊[*k*] 构造的 *均匀正交格子 S*，步长为

```
\\begin{array}{r} {h = \\frac{1}{M}.} \\\\ \\end{array}
```

(7.96)

*I*^(*n*) 中的基本立方体具有相同的体积

```
\\begin{array}{r} {v = h^{n} = \\left( \\frac{1}{M} \\right)^{n}.} \\\\ \\end{array}
```

(7.97)

然后等式 (7.13, 7.14) 可以写成

```
\\begin{aligned} {\\widetilde{\\mathbb{B}}(\\mathbf{z})} & {\\approx v{\\sum\\limits\_{i = 1}^{N}\\phi}(\\mathbf{w}^{i},\\mathbf{z}),} \\\\ {\\widetilde{\\mathbb{G}}(\\mathbf{z})} & {\\approx v{\\sum\\limits\_{i = 1}^{N}\\varphi}(\\mathbf{w}^{i},\\mathbf{z}),} \\\\ \\end{aligned}
```

(7.98)

其中

```
\\begin{aligned} {\\phi(\\mathbf{w}^{i},\\mathbf{z})} & {= \\exp\\left( {- E(\\mathbf{z},\\mathbf{w}^{(i)})} \\right),} \\\\ {\\varphi(\\mathbf{w}^{i},\\mathbf{z})} & {= E(\\mathbf{z},\\mathbf{w}^{(i)})\\exp\\left( {- E(\\mathbf{z},\\mathbf{w}^{(i)})} \\right).} \\\\ \\end{aligned}
```

(7.99)

第二种策略基于从每个 *k* 次元素 **w** 的非均匀（随机）格子 ${\\hat{\\mathbb{S}}}\_{k}$ 的乘积构造的 *非均匀（随机）正交格子 $\\hat{\\mathbb{S}}$*。与均匀格子不同，非均匀格子的步长为

```
\\begin{array}{r} {h\_{k}^{(i)} = w\_{k}^{(i + 1)} - w\_{k}^{(i)},} \\\\ \\end{array}
```

(7.100)

从而表示一个 *随机变量*。格子 $\\hat{\\mathbb{S}}$ 中的基本立方体具有 *随机* 体积 *v*^((1)), …, *v*^((*N*)), 即

```
\\begin{array}{r} {v^{(i)} = {\\prod\\limits\_{k = 1}^{n}h\_{k}^{(i)}},\\text{\\quad\\quad}i = \\overline{1,N}.} \\\\ \\end{array}
```

(7.101)

根据均值定理，非均匀格子 (7.100, 7.101) 上积分的 *精确* 值由下式给出

```
\\begin{array}{r} {\\mathbb{B}(\\mathbf{z}) = {\\sum\\limits\_{i = 1}^{N}v^{(i)}}\\phi(\\zeta^{(i)},\\mathbf{z}),} \\\\ {\\mathbb{G}(\\mathbf{z}) = {\\sum\\limits\_{i = 1}^{N}v^{(i)}}\\varphi(\\xi^{(i)},\\mathbf{z}),} \\\\ \\end{array}
```

(7.102)

其中 *ζ*^((*i*)) 和 *ξ*^((*i*)) 分别表示格子 $\\hat{\\mathbb{S}}$ 的基本立方体的平均点，对应积分 (7.13) 和 (7.14)。

将精确值 (7.102) 与近似值 (7.98) 之间的误差定义为

```
\\begin{aligned} \\left| \\mathbb{B}(\\mathbf{z}) - \\widetilde{\\mathbb{B}}(\\mathbf{z}) \\right| & \\left. = \\middle| \\sum\_{i = 1}^{N}v^{(i)}\\phi(\\zeta^{(i)},\\mathbf{z}) - v\\sum\_{i = 1}^{N}\\phi(\\mathbf{a}^{(i)},\\mathbf{z}) \\middle| \\leq \\right. \\\\ & \\left. \\leq \\sum\_{i = 1}^{N} \\middle| v^{(i)} - v \\middle| \\middle| \\phi(\\zeta^{(i)},\\mathbf{z} \\middle| + \\right. \\\\ {v\\sum\_{i = 1}^{N}} & \\left| \\phi(\\zeta^{(i)},\\mathbf{z}) - \\phi(\\mathbf{a}^{(i)},\\mathbf{z}) \\middle| = \\epsilon(N), \\right. \\\\ \\end{aligned}
```

(7.103)

和

```
\\begin{aligned} \\left| \\mathbb{G}(\\mathbf{z}) - \\widetilde{\\mathbb{G}}(\\mathbf{z}) \\right| & \\left. = \\middle| \\sum\_{i = 1}^{N}v^{(i)}\\varphi(\\zeta^{(i)},\\mathbf{z}) - v\\sum\_{i = 1}^{N}\\varphi(\\mathbf{a}^{(i)},\\mathbf{z}) \\middle| \\leq \\right. \\\\ & \\left. \\leq \\sum\_{i = 1}^{N} \\middle| v^{(i)} - v \\middle| \\middle| \\varphi(\\zeta^{(i)},\\mathbf{z}) \\middle| + \\right. \\\\ {v\\sum\_{i = 1}^{N}} & \\left| \\varphi(\\zeta^{(i)},\\mathbf{z}) - \\varphi(\\mathbf{a}^{(i)},\\mathbf{z}) \\middle| = \\kappa(N). \\right. \\\\ \\end{aligned}
```

(7.104)

首先，导出 *ϵ̃*(*N*, *n*) 和 *κ̃*(*N*, *n*) 作为 *ϵ*(*N*) 和 *κ*(*N*) 的上界，然后求解不等式

*ϵ*(*N*) ≤ *ϵ̃*(*N*) ≤ *δ*,  *κ*(*N*) ≤ *κ̃*(*N*) ≤ *δ*.

(7.105)

这里 *δ* 是给定的误差。我们应牢记 *ϵ*(*N*) 和 *κ*(*N*) 是随机变量。因此，不等式 (7.105) 只能以某种概率成立。

**1.** 考虑不等式 (7.3) 并估计第一项：

```
\\begin{array}{r} \\left. \\left. \\sum\\limits\_{i = 1}^{N} \\right|v^{(i)} - v \\middle| \\middle| \\phi(\\zeta^{(i)},\\mathbf{z}) \\middle| \\leq \\max\_{\\zeta \\in I^{n}} \\middle| \\phi(\\zeta,\\mathbf{z}) \\middle| \\left. \\sum\\limits\_{i = 1}^{N} \\right|v^{(i)} - v \\middle| . \\right. \\\\ \\end{array}
```

(7.106)

由函数 *ϕ*(**w**, **z**) 的定义，在固定 **z** 下 (7.98) 写出

```
\\begin{array}{r} \\left| \\phi(\\mathbf{w},\\mathbf{z}) \\middle| \\leq \\max\_{\\mathbf{w} \\in I^{n}}\\exp( \\middle| E(\\mathbf{w},\\mathbf{z}) \\middle| ) \\leq \\exp(G), \\right. \\\\ \\end{array}
```

(7.107)

其中

```
\\begin{array}{r} \\left. G = {({\\sum\\limits\_{t = 1}^{T}A^{(t)}})}^{2},\\text{\\quad\\quad}A^{(t)} = \\max\\left. \\sum\\limits\_{(n\_{1},\\ldots,n\_{t}) = 1}^{n} \\right|A\_{n\_{1},\\ldots,n\_{t}} \\middle| . \\right. \\\\ \\end{array}
```

(7.108)

接下来，估计随机基本体积 *v*^((*i*)) (7.101) 与均匀格子的基本体积 *v* 之间的差。

```
\\begin{array}{r} \\left| v^{i} - v \\middle| = \\middle| {\\prod\\limits\_{k = 1}^{n}h\_{k}^{i}} - h^{n} \\middle| \\leq h^{(n - 1)}\\,\\max\_{i} \\middle| h\_{k}^{i} - h \\middle| . \\right. \\\\ \\end{array}
```

(7.109)

注意变量 *h*[*k*]^(*i*) 是随机的。考虑事件

```
\\begin{array}{r} {\\mathcal{V}^{k} = \\left\\{ \\max\_{i} \\middle| h\_{k}^{i} - h \\middle| < \\gamma \\right\\},} \\\\ \\end{array}
```

(7.110)

以及事件 𝒱[1], ..., 𝒱[*m*] 的并集

```
\\begin{array}{r} {\\mathcal{V} = {\\underset{k = 1}{\\overset{n}{\\cup}}\\mathcal{V}^{k}}.} \\\\ \\end{array}
```

(7.111)

这里 *γ* 指定一个很小的正值。事件 𝒱 的概率下界将在下面建立。

取 *γ* = *h*²，写出

```
\\begin{array}{r} \\left. \\max\_{i} \\middle| v^{i} - v \\middle| \\leq h^{(m - 1)}\\gamma = h^{(m + 1)}. \\right. \\\\ \\end{array}
```

(7.112)

因此，由 (7.106–7.108) 不等式

```
\\begin{array}{r} \\left| {\\sum\\limits\_{i = 1}^{N}{(v\_{i} - v)}}\\phi(\\zeta^{i},\\mathbf{z}) \\middle| \\leq N\\left( \\frac{l}{N} \\right)^{n + 1}\\,\\exp(G). \\right. \\\\ \\end{array}
```

(7.113)

以事件 (7.111) 的概率成立。


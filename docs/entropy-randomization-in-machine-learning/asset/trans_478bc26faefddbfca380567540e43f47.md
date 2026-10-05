

$$\\begin{aligned} & \\left. y(t) = {\\int\_{\\tau\_{1} \\in \\mathcal{T}}g\_{1}}(t - \\tau\_{1}\\, \\middle| \\,\\mathbf{a})\\lbrack x(\\tau\_{1}) - {\\int\_{\\lambda\_{1} \\in \\mathcal{T}}\\,}c\_{1}(\\tau\_{1} - \\lambda\_{1}\\, \\middle| \\,\\mathbf{c})\\, y(\\lambda\_{1})\\, d\\lambda\_{1} + \\right. \\\\ & \\left. \\quad + {\\int\_{\\lambda\_{1} \\in \\mathcal{T}}{\\int\_{\\lambda\_{2} \\in \\mathcal{T}}\\,}}c\_{2}(t - \\lambda\_{1},t - \\lambda\_{2}\\, \\middle| \\,\\mathbf{c})\\, y(\\lambda\_{1})y(\\lambda\_{2})\\, d\\lambda\_{1}d\\lambda\_{2} + \\ldots \\right. \\\\ \\end{aligned}$$  

(4.88)

然后以泛函级数 (4.3.3) 的形式构造解：将它代入方程 (4.3.3) 的左边和右边，收集并比较变量 *x* 的相同幂次项。这些运算导致了 (4.3.3) 的核 *w*[*k*](*τ*[1],…,*τ*[*k*])=*w*[*k*](*τ*[1],…,*τ*[*k*] | **a**,**c**) 的如下积分方程组：

$$\\begin{aligned} \\left. {\\int\_{\\tau\_{1} \\in \\mathcal{T}}w\_{1}}(t - \\tau\_{1}\\, \\middle| \\,\\mathbf{a},\\mathbf{c}) \\right. & \\left. x(\\tau\_{1})\\, d\\tau\_{1} = {\\int\_{\\tau\_{1} \\in \\mathcal{T}}g\_{1}}(t - \\tau\_{1}\\, \\middle| \\,\\mathbf{a})\\,\\lbrack x(\\tau\_{1})\\, d\\tau\_{1} - \\right. \\\\ {- {\\int\_{\\lambda\_{1} \\in \\mathcal{T}\_{\\tau\_{1}}}\\,}c\_{1}(\\tau\_{1}} & \\left. - \\lambda\_{1}\\, \\middle| \\,\\mathbf{c})\\,{\\int\_{\\mu\_{1} \\in \\mathcal{T}\_{\\lambda\_{1}}}\\,}w\_{1}(\\lambda\_{1} - \\mu\_{1}\\, \\middle| \\,\\mathbf{a},\\mathbf{c}) \\times \\right. \\\\ & {\\times x(\\mu\_{1})\\, d\\tau\_{1}d\\lambda\_{1}d\\mu\_{1},} \\\\ \\end{aligned}$$  

(4.89)

$$\\begin{aligned} & \\left. \\int\_{\\tau\_{1} \\in \\mathcal{T}}\\int\_{\\tau\_{2} \\in \\mathcal{T}}\\, w\_{2}(t - \\tau\_{1},t - \\tau\_{2}\\, \\middle| \\,\\mathbf{a},\\mathbf{c})\\, x(\\tau\_{1})x(\\tau\_{2})\\, d\\tau\_{1}d\\tau\_{2} = \\right. \\\\ {- \\int\_{\\tau\_{1} \\in \\mathcal{T}}} & \\left. g\_{1}(t - \\tau\_{1} - \\tau\_{2}\\, \\middle| \\,\\mathbf{a})\\int\_{\\lambda\_{1} \\in \\mathcal{T}\_{\\tau\_{1}}}\\int\_{\\lambda\_{2} \\in \\mathcal{T}\_{\\tau\_{2}}}\\, c\_{2}(\\tau\_{1} - \\lambda\_{1},\\tau\_{2} - \\lambda\_{2}\\, \\middle| \\,\\mathbf{c}) \\times \\right. \\\\ \\times & \\left. \\int\_{\\mu\_{1} \\in \\mathcal{T}\_{\\lambda\_{1}}}\\int\_{\\mu\_{2} \\in \\mathcal{T}\_{\\lambda\_{2}}}\\, w\_{1}(\\lambda\_{1} - \\mu\_{1}, \\middle| \\,\\mathbf{a},\\mathbf{c})w\_{1}(\\lambda\_{2} - \\mu\_{2}, \\middle| \\,\\mathbf{a},\\mathbf{c}) \\times \\right. \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad} \\times x(\\mu\_{1})x(\\mu\_{2})\\, d\\tau\_{1}d\\tau\_{2}d\\lambda\_{1}d\\lambda\_{2}d\\mu\_{1}d\\mu\_{2} -} \\\\ & \\left. \\text{\\quad\\quad}\\text{\\quad\\quad} - \\int\_{\\tau\_{1} \\in \\mathcal{T}}\\int\_{\\tau\_{2} \\in \\mathcal{T}}\\, g\_{2}(t - \\tau\_{1},t - \\tau\_{2}, \\middle| \\,\\mathbf{a}) \\times \\right. \\\\ & \\left. \\text{\\quad\\quad} \\times \\int\_{\\lambda\_{1} \\in \\mathcal{T}\_{\\tau\_{1}}}\\int\_{\\lambda\_{2} \\in \\mathcal{T}\_{\\tau\_{2}}}c\_{1}(\\tau\_{1} - \\lambda\_{1})c\_{1}(\\tau\_{2} - \\lambda\_{2}, \\middle| \\,\\mathbf{c})\\, \\times \\right. \\\\ & \\left. \\text{\\quad\\quad}\\text{\\quad\\quad} \\times \\int\_{\\mu\_{1} \\in \\mathcal{T}\_{\\lambda\_{1}}}\\int\_{\\mu\_{2} \\in \\mathcal{T}\_{\\lambda\_{2}}}\\, w\_{1}(\\lambda\_{1} - \\mu\_{1}, \\middle| \\,\\mathbf{a},\\mathbf{c}) \\times \\right. \\\\ & \\left. \\text{\\quad\\quad}w\_{1}(\\lambda\_{2} - \\mu\_{2}, \\middle| \\,\\mathbf{a},\\mathbf{c})\\, d\\tau\_{1}d\\tau\_{2}d\\lambda\_{1}d\\lambda\_{2}d\\mu\_{1}d\\mu\_{2},\\cdots. \\right. \\\\ \\end{aligned}$$

该系统由关于 *x* 的幂次的齐次积分方程组成，具有递归结构。利用多维傅里叶变换（详见 \[[42](#refbib.xhtml#r42), [178](#refbib.xhtml#r178)\]），写出最终表达式

$$\\begin{aligned} & \\left. \\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}W(s\_{1}, \\middle| \\,\\mathbf{a},\\mathbf{c}) = \\frac{\\left. G\_{1}(s\_{1}, \\middle| \\,\\mathbf{a}) \\right.}{\\left. 1 + G\_{1}(s\_{1}, \\middle| \\,\\mathbf{a})C(s\_{1}, \\middle| \\,\\mathbf{c}) \\right.}, \\right. \\\\ & \\left. \\text{\\quad\\quad}\\quad\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}W(s\_{1},s\_{2}, \\middle| \\,\\mathbf{a},\\mathbf{c}) = \\right. \\\\ & {\\quad = \\frac{\\left. - G\_{1}(s\_{1} + s\_{2}, \\middle| \\,\\mathbf{a})\\, C\_{2}(s\_{1},s\_{2}, \\middle| \\,\\mathbf{c})\\, W\_{1}(s\_{1}, \\middle| \\,\\mathbf{a},\\mathbf{c})W\_{1}(s\_{2}, \\middle| \\,\\mathbf{a},\\mathbf{c}) \\right.}{\\left. 1 + .G\_{1}(s\_{1} + s\_{2}, \\middle| \\,\\mathbf{a})C\_{1}(s\_{1} + s\_{2}, \\middle| \\,\\mathbf{c}) \\right.} +} \\\\ & {+ \\frac{\\left. G\_{2}(s\_{1},s\_{2}, \\middle| \\,\\mathbf{a})W\_{1}(s\_{2}, \\middle| \\,\\mathbf{a},\\mathbf{c})\\lbrack C\_{1}(s\_{2}, \\middle| \\,\\mathbf{c})W\_{1}(s\_{1}, \\middle| \\,\\mathbf{a},\\mathbf{c}) - 2C\_{1}(s\_{2}, \\middle| \\,\\mathbf{c})\\rbrack \\right.}{\\left. 1 + G\_{1}(s\_{1} + s\_{2}, \\middle| \\,\\mathbf{a})C\_{1}(s\_{1} + s\_{2}), \\middle| \\,\\mathbf{c} \\right.},} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\cdots} \\\\ \\end{aligned}$$  

(4.90)

这里 *s*[1], …, *s*[*i*] 是多维傅里叶变换的复参数。

因此，\[(SI,FB)–EO\] RPM (4.3.3) 可以写成 \[SI–EO\] RPM (4.2.4)。这种变换在随机动态回归模型的机器学习问题中可能是有益的。

### 4.3.4 具有多项式非线性的非线性动态模型

在前一小节中，我们研究了在 \[SI–EO\] RPM 中使用正交多项式的过程。现在考虑该过程应用于 \[(SI,FB)–EO\] RPMs。对于具有 [Fig. 4.21(a)](#chapter4.xhtml#f4_21) 所示结构的 \[(SI,FB)–EO\] RPM，

$$\\begin{aligned} {y(t)} & {= {\\int\_{\\mathcal{T}}w}(t - \\tau)\\,{\\sum\\limits\_{k = 0}^{K}w\_{k}}g\_{k}(\\varepsilon(\\tau))\\, d\\tau,} \\\\ {z(t)} & {= {\\int\_{\\mathcal{T}}c}(t - \\tau)\\,{\\sum\\limits\_{m = 0}^{M}v\_{m}}c\_{m}(y(\\tau))\\, d\\tau,} \\\\ {\\varepsilon(t)} & {= x(t) - z(t).} \\\\ \\end{aligned}$$  

(4.91)

![Figure 4.21](images/fig4_21.jpg)

[Figure 4.21](#chapter4.xhtml#f4_21b)

另一个 \[(SI,FB)–EO\] RPM（见 [Fig. 4.21(b)](#chapter4.xhtml#f4_21)）由以下方程组描述：

$$\\begin{aligned} {y(t)} & {= {\\sum\\limits\_{k = 0}^{K}w\_{k}}g\_{k}(u(\\tau))\\, d\\tau,} \\\\ {u(t)} & {= {\\int\_{\\mathcal{T}}w}(t - \\tau)\\,\\varepsilon(\\tau)\\, d\\tau,} \\\\ {e(t)} & {= {\\int\_{\\mathcal{T}}c}(t - \\tau)\\, y(\\tau)\\, d\\tau,} \\\\ \\end{aligned}$$  

(4.92)

$$\\begin{aligned} {z(t)} & {= {\\sum\\limits\_{m = 0}^{M}v\_{m}}c\_{m}(e(\\tau))\\, d\\tau,} \\\\ {\\varepsilon(t)} & {= x(t) - z(t).} \\\\ \\end{aligned}$$  

(4.93)

这些 RPM 的参数 **w** 和 **v** 是随机的、独立的并且取值于区间

$$\\begin{array}{r} {\\mathbf{w} \\in \\mathcal{W} = \\lbrack\\mathbf{w}^{-},\\mathbf{w}^{+}\\rbrack,\\text{\\quad\\quad}\\mathbf{v} \\in \\mathcal{V} = \\lbrack\\mathbf{v}^{-},\\mathbf{v}^{+}\\rbrack.} \\\\ \\end{array}$$  

(4.94)

回想一下，正交多项式可用于逼近连续非线性函数，而且还能逼近不连续的非线性，这构成了其显著特征。然而，多项式的正交性仅在某个集合（定义域）和某个函数空间中成立。

[Section 3.2](#chapter3.xhtml#sec3_2) 中正交多项式的使用过程自然地推广到 \[(SI,FB)–EO\] RPMs。


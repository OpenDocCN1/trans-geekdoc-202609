

$$\\begin{aligned} {\\hat{y}(t) = \\sum\_{k = 1}^{K}\\,\\sum\_{i = 0}^{k}} & \\left. c\_{k}a\_{ki}\\int\_{0}^{t}\\cdots\\int\_{0}^{t}w(t - \\tau\_{0} \\middle| \\mathbf{b})\\cdots w(t - \\tau\_{i} \\middle| \\mathbf{b}) \\times \\right. \\\\ & {\\times x(\\tau\_{0})\\cdots x(\\tau\_{i})d\\tau\_{1}\\cdots d\\tau\_{i}.} \\\\ \\end{aligned}$$  

(4.59)

在此方程中，`a[k i]` 表示正交多项式的系数（参见 [表 4.1](#chapter4.xhtml#t4_1)）；`c[1]`，…，`c[K]` 是非线性单元随机化模型的独立随机系数。它们是区间型（4.57）。

如果该 RPM 的输入和输出由格点函数表征，则以下方程成立：

* 对于 [图 4.13(a)](#chapter4.xhtml#f4_13) 中的 RPM，

$$\\begin{array}{r} \\left. \\hat{y}\\lbrack n\\rbrack = {\\sum\\limits\_{k = 0}^{K}\\,}{\\sum\\limits\_{i = 0}^{k}c\_{k}}a\_{ki}{\\sum\\limits\_{m = 0}^{n}w}\\lbrack n - m\\, \\middle| \\,\\mathbf{b}\\rbrack\\, x^{i}\\lbrack m\\rbrack; \\right. \\\\ \\end{array}$$  

(4.60)

* 对于 [图 4.13(b)](#chapter4.xhtml#f4_13) 中的 RPM，

$$\\begin{array}{r} \\left. \\hat{y}\\lbrack n\\rbrack = {\\sum\\limits\_{k = 1}^{K}{\\sum\\limits\_{i = 0}^{k}c\_{k}}}a\_{ki}{\\sum\\limits\_{(m\_{0},\\ldots,m\_{i}) = 0}^{n}{\\prod\\limits\_{j = 0}^{i}w}}\\lbrack n - m\_{j}\\, \\middle| \\,\\mathbf{b}\\rbrack\\, x\\lbrack m\_{j}\\rbrack. \\right. \\\\ \\end{array}$$  

(4.61)

在这些公式中，系数 `c[k]` 是独立随机变量，按给定概率密度函数分布于相应的区间（4.57）。脉冲特性的参数 `b[1]`，…，`b[s]` 也是随机的、相互独立的，并在相应的区间内取值，具有给定的概率密度函数。

### 4.2.6 随机神经网络

神经网络是一种用于机器学习程序的参数化模型。神经网络的结构基础是 Kolmogorov 定理 [[94](#refbib.xhtml#r94)]，该定理指出，非负单位立方体上 `n` 个变量的连续函数可以写成单变量函数的叠加并求和：

$$\\begin{array}{r} {f(x\_{1},\\ldots,x\_{n}) = {\\sum\\limits\_{k = 1}^{(2n + 1)}h\_{k}}\\left( {{\\sum\\limits\_{i = 1}^{n}\\phi\_{ik}}(x\_{i})} \\right);} \\\\ \\end{array}$$  

(4.62)

这里变量 `h[1]`，…，`h[2n + 1]` 依赖于函数 `f`，而函数 `phi[i k](x[i])` 则不依赖。此定理断言存在这样的表示，但没有给出找到它的技术细节。

一方面，神经网络的普适性可以用与 Kolmogorov 定理的结构类比来解释；另一方面，可以用与生物神经元操作（[122](#refbib.xhtml#r122)）的简化（统计）类比来解释。神经元统计模型的一般结构如图 [图 4.16(a)](#chapter4.xhtml#f4_16) 所示。它由三个串联的模块组成，即突触系数 `w` = `{w[1],…,w[n]}`、加法器和具有激活函数 `phi(u, b)` 的非线性变换模块，其中 `b` 为激活函数参数。[图 4.16(b)](#chapter4.xhtml#f4_16) 显示了该模型的示例，其中非线性变换模块具有阈值为 `Delta` 的激活函数 `phi(u, Delta)`。一般情况下，激活函数 `phi(u)` 可能包含多个参数，后文记为 `b[1]`，…，`b[q]`。除 [图 4.16(b)](#chapter4.xhtml#f4_16) 中的函数 `phi(u)` 外，以下激活函数也很常见：

* —线性激活函数（参见 [图 4.17(a)](#chapter4.xhtml#f4_17)）

$$\\begin{array}{r} {\\phi(u) = \\left\\{ \\begin{aligned} 0 & {\\text{if}\\, u \\leq \\Delta,} \\\\ u & {\\text{if}\\, u \\geq \\Delta;} \\\\ \\end{aligned}~ \\right.} \\\\ \\end{array}$$  

(4.63)

* —sigmoid 激活函数（参见 [图 4.17(b)](#chapter4.xhtml#f4_17)）

$$\\begin{array}{r} {\\phi(u) = \\frac{1}{1 + \\exp(u - \\Delta)};} \\\\ \\end{array}$$  

(4.64)

* —tangent 激活函数（参见 [图 4.17(c)](#chapter4.xhtml#f4_17)）

$$\\begin{array}{r} {\\phi(u) = \\tan(u).} \\\\ \\end{array}$$  

(4.65)

[图 4.16(b)](#chapter4.xhtml#f4_16) 所示结构的网络称为单层神经网络。单层神经网络的串联构成多层神经网络。其内部层称为隐藏层，而最后一层称为输出层。大多数应用涉及一层隐藏层，如 [图 4.18](#chapter4.xhtml#f4_18) 所示。输入层有一组突触系数 `w[11]`，… `w[n h]`；隐藏层有 `g[11]`，…，`g[h s]`。

因此，单层和多层神经网络（[图 4.16](#chapter4.xhtml#f4_16) 和 [4.18](#chapter4.xhtml#f4_18)）是统计系统，即网络在当前时刻的输入理论上取决于其在此时刻的输入。例如，单层神经网络的输出形式为

![Figure 4.16](images/fig4_16.jpg)

[Figure 4.16](#chapter4.xhtml#f4_16b)

![Figure 4.17](images/fig4_17.jpg)

[Figure 4.17](#chapter4.xhtml#f4_17b)

![Figure 4.18](images/fig4_18.jpg)

[Figure 4.18](#chapter4.xhtml#f4_18b)

$$\\begin{array}{r} {y(t) = S\\left( \\mathbf{x}(t)\\, \\middle| \\,\\mathbf{w},\\mathbf{b} \\right),} \\\\ \\end{array}$$  

(4.66)

其中 `w` 和 `b` 为网络参数。

按假设，随机神经网络包含取值于给定区间的随机参数，即

$$\\begin{array}{r} {\\mathbf{w} \\in \\mathcal{W} = \\lbrack\\mathbf{w}^{-},\\mathbf{w}^{+}\\rbrack;\\text{\\quad\\quad}\\mathbf{b} \\in \\mathcal{B} = \\lbrack\\mathbf{b}^{-},\\mathbf{b}^{+}\\rbrack.} \\\\ \\end{array}$$  

(4.67)

这些区间上参数的概率特性由概率密度函数 `P[w](w)` 和 `P[b](b)` 表征。随机神经网络的输出表示随机变量 `y` 的集合。

![Figure 4.19](images/fig4_19.jpg)

[Figure 4.19](#chapter4.xhtml#f4_19b)

## 4.3 “（单输入，反馈）- 集成输出” 动态随机参数模型

### 4.3.1 定义和结构

对于许多动态 RPM 的结构设计，仅定义输入-输出关系是不够的。在这种情况下，我们必须反映被建模过程或对象的某些内部机制。可用以描述这些机制的数学框架涉及不同类别的方程。它们的一般结构由一个具有参数化映射 `G` 的特定模块和一个由参数化映射 `C` 表征的反馈回路组成，见 [图 4.20](#chapter4.xhtml#f4_20)。

![Figure 4.20](images/fig4_20.jpg)

[Figure 4.20](#chapter4.xhtml#f4_20b)

在此图中，`x` ∈ `R^(n)` 表示模型输入；`y` ∈ `R^(m)` 为模型输出；最后，`z` ∈ `R^(d)` 给出反馈模块输出。

映射 `G` 和 `C` 描述了对象中运行过程的内部机制。采用函数描述对这些映射进行描述，引入以下记号：

$$\\begin{aligned} \\mathbb{G} & {= \\mathcal{G}\\left( \\mathbf{x}(\\tau),\\mathbf{z}(\\tau),\\, \\middle| \\,\\mathbf{a};\\,\\tau \\in \\mathcal{T} \\right),} \\\\ {\\mathbb{C}} & {= \\mathcal{C}\\left( \\mathbf{y}(\\tau),\\, \\middle| \\,\\mathbf{c};\\,\\tau \\in \\mathcal{T} \\right).} \\\\ \\end{aligned}$$  

(4.68)

泛函 `G` 和 `C` 分别包含随机参数 `a` ∈ `R^(r)` 和 `c` ∈ `R^(h)`，其独立元素属于区间

$$\\begin{array}{r} {\\mathbf{a} \\in \\mathcal{A} = \\lbrack\\mathbf{a}^{-},\\mathbf{a}^{+}\\rbrack,\\text{\\quad\\quad}\\mathbf{c} \\in \\mathcal{S} = \\lbrack\\mathbf{c}\_{-},\\mathbf{c}^{+}\\rbrack.} \\\\ \\end{array}$$  

(4.69)


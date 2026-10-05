

$$\\begin{array}{r} \\left. \\rho\_{B}(T) = \\frac{2}{n(n - 1)}{\\sum\\limits\_{(\\alpha,\\beta),\\mspace{2mu}\\alpha \\neq \\beta}^{n}\\varrho}(\\mathbf{b}^{(\\alpha)},\\mathbf{b}^{(\\beta)}\\, \\middle| \\, T) \\right. \\\\ \\end{array}$$  

(3.118)

and its mathematical expectation

$$\\begin{array}{r} {{\\overline{\\rho}}\_{B} = {\\int\_{\\mathcal{T}}W}(T)\\rho\_{B}(T)dT.} \\\\ \\end{array}$$  

(3.119)

### 3. 投影到空间 *R*[*n*]^(*r*) (生成集合 ℨ[*n*]^(*r*))

此操作将使用随机投影矩阵 `T[n × m]` 和 `Q[(s × r)]` 执行：

$$\\begin{aligned} Z\_{(n \\times r)} & {= \\left( \\begin{array}{l} \\mathbf{z}^{(1)} \\\\ \\cdots \\\\ \\mathbf{z}^{(n)} \\\\ \\end{array} \\right) = T\_{(n \\times m)}U\_{(m \\times s)}Q\_{(s \\times r)};} \\\\ z\_{j}^{(i)} & {= {\\sum\\limits\_{p = 1}^{m}t\_{ip}}\\,{\\sum\\limits\_{k = 1}^{s}u\_{pk}}\\, q\_{kj},\\text{\\quad\\quad}i = \\overline{1,n};\\, j = \\overline{1,r}.} \\\\ \\end{aligned}$$  

(3.120)

这些投影矩阵为区间类型：

$$\\begin{array}{r} {T\_{(n \\times m)} \\in \\mathcal{T} = \\lbrack T^{-},T^{+}\\rbrack,} \\\\ {Q\_{(s \\times r)} \\in \\mathcal{Q} = \\lbrack Q^{-},Q^{+}\\rbrack.} \\\\ \\end{array}$$  

(3.121)

投影矩阵的概率特性由在集合上定义的联合 PDF `F(T, Q)` 刻画

$$\\begin{array}{r} {\\mathcal{F} = \\mathcal{T} \\otimes \\mathcal{Q}.} \\\\ \\end{array}$$  

(3.122)

向量 `z^{(i)}` 构成 *r* 维点集 ℨ[*n*]^(*r*)。该集合的紧致性指标由下式给出

$$\\begin{array}{r} \\left. \\rho\_{Z}(T,Q) = \\frac{2}{n(n - 1)}{\\sum\\limits\_{(\\alpha,\\beta),\\mspace{2mu}\\alpha \\neq \\beta}^{n}\\varrho}(\\mathbf{z}^{\\alpha},\\mathbf{z}^{\\beta}\\, \\middle| \\, T,Q). \\right. \\\\ \\end{array}$$  

(3.123)

紧致性指标的数学期望形式为

$$\\begin{array}{r} {{\\overline{\\rho}}\_{Z} = {\\int\_{\\mathcal{F}}F}(T,Q)\\rho\_{Z}(T,Q)dTdQ.} \\\\ \\end{array}$$  

(3.124)

根据原始数据矩阵的维度 (*m*, *s*) 与投影矩阵的维度 (*m*, *r*)、(*n*, *s*) 和 (*n*, *r*) 之间的关系，前者被压缩（若 `r < s` 且 `n < m`）或扩展（若 `r > s` 且 `n > m`）。

### 3.7.2 熵随机投影算法

考虑投影到空间 `R[(n)]^r`，该投影同时通过两个参数变换数据矩阵。

熵随机投影（`ERP`）算法在于在附加条件下对 PDF `F(T, Q)` 进行最大熵估计（`MEE`），该条件要求数据矩阵 `U[(m × s)]` 和投影 `Z[(n × r)]` 的紧致性指标取值相等。

`MEE`-估计的函数 `F(B, Q)`（参见 [Chapter A](#appA.xhtml)）计算为

$$\\begin{aligned} {\\mathcal{H}\\lbrack F(T,Q)\\rbrack} & \\left. = - {\\int\_{\\mathcal{F}}F}(T,Q)\\,\\ln\\, F(T,Q)\\, dTdQ\\Rightarrow\\max, \\right. \\\\ & {{\\int\_{\\mathcal{F}}F}(T,Q)dTdQ = 1,} \\\\ & {{\\int\_{\\mathcal{F}}F}(T,Q)\\rho\_{Z}(T,Q)dTdQ = \\rho\_{U}.} \\\\ \\end{aligned}$$  

(3.125)

问题 (3.125) 是一个 Lyapunov 类型的泛函约束优化问题：此类问题的所有分量均为积分泛函 \[77\]。

由于该问题的积分形式，最优性条件涉及带标量 Lagrange 乘子的以下 Lagrange 泛函：

$$\\begin{aligned} {\\mathcal{L}\\lbrack F(T,Q)\\rbrack} & {= \\mathcal{H}\\lbrack F(T,Q)\\rbrack + \\mu(\\left( {1 - {\\int\_{\\mathcal{F}}F}(T,Q)dTdQ} \\right) +} \\\\ & {+ \\lambda\\left( {\\rho\_{U} - {\\int\_{\\mathcal{F}}F}(T,Q)\\rho\_{Z}(T,Q)dTdQ} \\right).} \\\\ \\end{aligned}$$  

(3.126)

该泛函关于 Gâteaux 导数 \[77\] (`𝔊[F]`) 的一阶最优性条件形式为

$$\\begin{array}{r} {\\mathfrak{G}\_{F}\\mathcal{L}\\lbrack F(T,Q)\\rbrack = 0.} \\\\ \\end{array}$$  

(3.127)

投影矩阵的熵最优 PDF 由下式给出

$$\\begin{aligned} \\left. F^{\*}(T,Q\\, \\middle| \\,\\lambda) \\right. & {= \\frac{\\exp\\left( {- \\lambda\\,\\,\\rho\_{Z}(T,Q)} \\right)}{\\mathbb{F}(\\lambda)},} \\\\ {\\mathbb{F}(\\lambda)} & {= {\\int\_{\\mathcal{F}}\\exp}\\left( {- \\lambda\\,\\,\\rho\_{Z}(T,Q)} \\right)dTdQ.} \\\\ \\end{aligned}$$  

(3.128)

根据 (3.128)，PDF 的结构取决于距离 (3.123) 且与参数 `λ` 无关。该参数满足紧致性指标的平衡方程：

$$\\begin{array}{r} {\\Phi(\\lambda) = {\\int\_{\\mathcal{F}}\\exp}\\left( {- \\lambda\\,\\rho\_{Z}(T,Q)} \\right)\\left( {\\rho\_{Z}(T,Q) - \\rho\_{U}} \\right)dTdQ = 0.} \\\\ \\end{array}$$  

(3.129)

由于 `λ` 是尺度参数，可能只需从线性化方程 (3.129) 求其近似值：

$$\\begin{array}{r} {\\widetilde{\\lambda} = \\frac{{\\int\_{\\mathcal{F}}\\left( {\\rho\_{Z}(T,Q) - \\rho\_{U}} \\right)}dTdQ}{{\\int\_{\\mathcal{F}}\\rho\_{Z}}(T,Q)\\left( {\\rho\_{Z}(T,Q) - \\rho\_{U}} \\right)dTdQ}.} \\\\ \\end{array}$$  

(3.130)

### 3.7.3 随机投影器的实现及其数值特征

实现随机投影器的标准方法是采样熵最优 PDF `P(Q)`、`W(T)` 和 `F(T, Q)`，它们在投影矩阵中保持数据矩阵的向量间距离。采样结果将 PDF 转化为随机投影矩阵序列：

$$\\begin{array}{r} \\left. F^{\*}(T,Q)\\Rightarrow(T^{(1)},Q^{(1)}),(T^{(2)},Q^{(2)}),\\ldots,(T^{(N)},Q^{(N)}),\\ldots \\right. \\\\ \\end{array}$$  

(3.134)

生成具有给定 PDF 的随机序列的通用方法在 \[36\] 中提出。平衡性质（见上文）可能不适用于该序列的每个单独元素，但它必然在“平均”意义下成立。因此，用于实现的经验投影器可以是矩阵

$$\\begin{array}{r} {\\overline{T} \\approx \\frac{1}{N}{\\sum\\limits\_{i = 1}^{N}T^{(i)}},\\text{\\quad\\quad}\\overline{Q} \\approx \\frac{1}{N}{\\sum\\limits\_{i = 1}^{N}Q^{(i)}}.} \\\\ \\end{array}$$  

(3.135)

“平均”投影矩阵的精确值由下式给出

$$\\begin{array}{r} {\\overline{T} = {\\int\_{\\mathcal{F}}T}\\, F(T,Q)dTdQ,\\text{\\quad\\quad}\\overline{Q} = {\\int\_{\\mathcal{F}}Q}\\, F(T,Q)dTdQ.} \\\\ \\end{array}$$  

(3.136)

尽管这些等式中的积分是多维的，但被积函数是指数多项式。这通常为计算多维积分提供了解析公式。

此外，多维积分的计算问题可通过近似方法求解，例如蒙特卡洛模拟和被积函数的多项式逼近。

PDF `F*(T, Q)` 定义在有界集 ℱ (3.122) 上。因此，用于实现的投影器可以是矩阵对

$$\\begin{array}{r} {(T^{\*},Q^{\*}) = \\arg\\max\_{\\mathcal{F}}F(T,Q).} \\\\ \\end{array}$$  

(3.137)

### 3.7.4 具有给定元素值的随机投影矩阵

#### 1. (0, 1)-投影矩阵的集合及其排序

考虑由投影矩阵 `Q[(s × r)]` 对空间 `R[(m)]^r` 进行的投影过程，其随机元素取值为 0 或 1。

将该矩阵写为长度为 `sr` 的行向量。由零和一组成的序列数，即不同行向量的数量为 `N = 2^(r s)`。例如，对于 `s = 3` 且 `r = 1`，有 8 个此类向量：

$$\\begin{array}{r} {000,100,010,001,110,011,101,111;} \\\\ \\end{array}$$  

对于 `s = 4` 且 `r = 1`，有 16 个此类向量：

$$\\begin{array}{r} {0000,1000,0100,0010,0001,1100,0110,0011,} \\\\ \\end{array}$$


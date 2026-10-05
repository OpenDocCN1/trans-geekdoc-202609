

$$\\begin{array}{r} {x\_{ij} = {\\sum\\limits\_{\\mu = 1}^{n}e\_{i,\\mu}}{\\sum\\limits\_{\\nu = 1}^{r}w\_{\\nu,j}}{\\sum\\limits\_{\\beta = 1}^{m}b\_{\\mu,\\beta}}{\\sum\\limits\_{\\alpha = 1}^{s}u\_{\\beta,\\alpha}}q\_{\\alpha,\\nu},\\text{\\quad\\quad}i = \\overline{1,m},\\, j = \\overline{1,s}.} \\\\ \\end{array}$$

(3.51)

### 3.3.2 最优性条件与算法

为衡量变换后矩阵 `X`(*m* × *s*) 与原始矩阵 `U`(*m* × *s*) 的偏差，选择 *信息交叉熵*

$$\\begin{array}{r} \\left. \\mathcal{H}(X\\, \\middle| \\, U) = - {\\sum\\limits\_{i = 1}^{m}{\\sum\\limits\_{j = 1}^{s}s\_{ij}}}(X\\, \\middle| \\, U), \\right. \\\\ \\end{array}$$

(3.52)

其中

$$\\begin{array}{r} {s\_{ij} = x\_{ij}\\ln\\frac{x\_{ij}}{u\_{ij}}.} \\\\ \\end{array}$$

(3.53)

由于 (3.51)，信息交叉熵 (3.52) 是矩阵 (`Q`, `B`, `W`, `E`) ≥ 0 的标量函数，即

$$\\begin{array}{r} {\\mathcal{H} = \\mathcal{H}(Q,B,W,E).} \\\\ \\end{array}$$

(3.54)

矩阵的最优元素通过最大化函数 `ℋ` 得到：

$$\\begin{array}{r} {(Q^{\*},B^{\*},W^{\*},E^{\*}) = \\arg\\max\_{(Q,B,W,E) \\geq 0}\\mathcal{H}(Q,B,W,E).} \\\\ \\end{array}$$

(3.55)

该问题将使用投影梯度下降的坐标式方案求解。

在并行程序中，有一对矩阵 (`Q`, `B`) 用于相对于第一个变量 (*r* < *s*) 降低原始矩阵 `U`，以及一对矩阵 (`W`, `E`) 用于相对于第二个变量 (*n* < *m*) 压缩矩阵 `U`。坐标式投影梯度下降方案中的每个迭代步由两个子步组成，分别与 (`Q`, `B`)-梯度上的迭代和 (`W`, `E`)-梯度上的迭代相关。

根据 (3.51–3.53)，函数 `ℋ`(`Q`, `B`, `W`, `E`) 的梯度具有分量

$$\\begin{array}{r} {\\frac{\\partial\\mathcal{H}}{\\partial q\_{\\alpha,\\nu}} = {\\sum\\limits\_{i = 1}^{m}{\\sum\\limits\_{j = 1}^{s}\\frac{\\partial s\_{ij}}{\\partial x\_{ij}}}}\\,\\frac{\\partial x\_{ij}}{\\partial q\_{\\alpha,\\nu}},} \\\\ {\\frac{\\partial\\mathcal{H}}{\\partial b\_{\\mu,\\beta}} = {\\sum\\limits\_{i = 1}^{m}{\\sum\\limits\_{j = 1}^{s}\\frac{\\partial s\_{ij}}{\\partial x\_{ij}}}}\\,\\frac{\\partial x\_{ij}}{\\partial b\_{\\mu,\\beta}},} \\\\ {\\frac{\\partial\\mathcal{H}}{\\partial w\_{\\nu,j}} = {\\sum\\limits\_{i = 1}^{m}{\\sum\\limits\_{j = 1}^{s}\\frac{\\partial s\_{ij}}{\\partial x\_{ij}}}}\\,\\frac{\\partial x\_{ij}}{\\partial w\_{\\nu,j}},} \\\\ {\\frac{\\partial\\mathcal{H}}{\\partial e\_{i,\\mu}} = {\\sum\\limits\_{i = 1}^{m}{\\sum\\limits\_{j = 1}^{s}\\frac{\\partial s\_{ij}}{\\partial x\_{ij}}}}\\,\\frac{\\partial x\_{ij}}{\\partial e\_{i,\\mu}},} \\\\ \\end{array}$$

(3.56)

其中

$$\\begin{aligned} & {\\frac{\\partial s\_{ij}}{\\partial x\_{ij}} = \\ln\\frac{x\_{ij}}{u\_{ij}} + 1,} \\\\ & {\\frac{\\partial x\_{ij}}{\\partial q\_{\\alpha,\\nu}} = w\_{\\nu,j}{\\sum\\limits\_{\\mu = 1}^{n}e\_{i,\\mu}}{\\sum\\limits\_{\\beta = 1}^{m}b\_{\\mu,\\beta}}u\_{\\beta,\\alpha},\\text{\\quad\\quad}\\alpha = \\overline{1,s},\\,\\nu = \\overline{1,r};} \\\\ & {\\frac{\\partial x\_{ij}}{\\partial b\_{\\mu,\\beta}} = e\_{i,\\mu}{\\sum\\limits\_{\\nu = 1}^{r}w\_{\\nu,j}}{\\sum\\limits\_{\\alpha = 1}^{s}u\_{\\beta,\\alpha}}q\_{\\alpha,\\nu},\\text{\\quad\\quad}\\mu = \\overline{1,n},\\,\\beta = \\overline{1,s};} \\\\ & {\\frac{\\partial x\_{ij}}{\\partial w\_{\\nu,j}} = {\\sum\\limits\_{\\mu = 1}^{n}e\_{i,\\mu}}{\\sum\\limits\_{\\beta = 1}^{m}b\_{\\mu,\\beta}}{\\sum\\limits\_{\\alpha = 1}^{s}u\_{\\beta,\\alpha}}q\_{\\alpha,\\nu},} \\\\ & {\\frac{\\partial x\_{ij}}{\\partial e\_{i,\\mu}} = {\\sum\\limits\_{\\nu = 1}^{r}w\_{\\nu,j}}{\\sum\\limits\_{\\beta = 1}^{m}b\_{\\mu,\\beta}}{\\sum\\limits\_{\\alpha = 1}^{s}u\_{\\beta,\\alpha}}q\_{\\alpha,\\nu},\\text{\\quad\\quad}\\mu = \\overline{1,n}.} \\\\ \\end{aligned}$$

(3.57)

应用 *矩阵向量化*，过渡到相应的向量 `q`、`b`、`w` 和 `e`。用 `∇[q]`、`∇[b]`、`∇[w]` 和 `∇[e]` 表示相对于这些向量的梯度的分量。

算法 `max ℋ` 具有以下结构。

* *a) 初始步：*

$$\\begin{array}{r} {\\mathbf{q}^{0} > \\mathbf{0},\\quad\\mathbf{b}^{0} > \\mathbf{0},\\quad\\mathbf{w}^{0} > 0,\\quad\\mathbf{e}^{0} > 0.} \\\\ \\end{array}$$

* *b) 第 n 次迭代步：*

$$\\begin{array}{r} {X^{n} = E^{n}\\left\\{ {\\left\\lbrack {B^{n}\\left( {UQ^{n}} \\right)} \\right\\rbrack W^{n}} \\right\\},} \\\\ \\end{array}$$

$$\\begin{array}{r} {\\mathcal{H}^{n} = {\\sum\\limits\_{i = 1}^{m}{\\sum\\limits\_{j = 1}^{s}x\_{ij}^{n}}}\\ln\\frac{x\_{ij}^{n}}{u\_{ij}};} \\\\ \\end{array}$$

$$\\begin{array}{r} {\\mathbf{q}^{(n + 1)} = \\left\\{ \\begin{array}{r} {\\mathbf{q}^{n} + \\gamma\_{\\mathbf{q}}\\nabla\_{\\mathbf{q}}(\\mathbf{q}^{n},\\mathbf{b}^{n},\\mathbf{w}^{n},\\mathbf{e}^{n})\\,\\text{if}\\,\\mathbf{q} \\geq \\mathbf{0},} \\\\ {\\mathbf{q}^{n}\\,\\text{if}\\,\\mathbf{q}^{(n + 1)} < \\mathbf{0};} \\\\ \\end{array}~ \\right.} \\\\ \\end{array}$$

$$\\begin{array}{r} \\left. \\text{\\quad\\quad}\\mathbf{q}^{(n + 1)}\\Rightarrow Q^{(n + 1)}; \\right. \\\\ \\end{array}$$

$$\\begin{array}{r} {\\mathbf{b}^{(n + 1)} = \\left\\{ \\begin{array}{r} {\\mathbf{b}^{n} + \\gamma\_{\\mathbf{b}}\\nabla\_{\\mathbf{b}}(\\mathbf{q}^{n},\\mathbf{b}^{n},\\mathbf{w}^{n},\\mathbf{e}^{n})\\,\\text{if}\\,\\mathbf{b}^{(n + 1)} \\geq \\mathbf{0},} \\\\ {\\mathbf{b}^{n}\\text{if}\\,\\mathbf{b}^{(n + 1)} < \\mathbf{0};} \\\\ \\end{array}~ \\right.} \\\\ \\end{array}$$

$$\\begin{array}{r} \\left. \\text{\\quad\\quad}\\mathbf{b}^{(n + 1)}\\Rightarrow B^{(n + 1)}; \\right. \\\\ \\end{array}$$

$$\\begin{array}{r} {\\mathbf{w}^{(n + 1)} = \\left\\{ \\begin{array}{r} {\\mathbf{w}^{n} + \\gamma\_{\\mathbf{w}}\\nabla\_{\\mathbf{w}}(\\mathbf{q}^{(n + 1)},\\mathbf{b}^{(n + 1)},\\mathbf{w}^{n},\\mathbf{e}^{n})\\,\\text{if}\\,\\mathbf{w} \\geq \\mathbf{0},} \\\\ {\\mathbf{w}^{n}\\text{if}\\,\\mathbf{w}^{(n + 1)} < \\mathbf{0};} \\\\ \\end{array}~ \\right.} \\\\ \\end{array}$$

$$\\begin{array}{r} \\left. \\text{\\quad\\quad}\\mathbf{w}^{(n + 1)}\\Rightarrow W^{(n + 1)}; \\right. \\\\ \\end{array}$$

$$\\begin{array}{r} {\\mathbf{e}^{(n + 1)} = \\left\\{ \\begin{array}{r} {\\mathbf{e}^{n} + \\gamma\_{\\mathbf{e}}\\nabla\_{\\mathbf{e}}(\\mathbf{q}^{(n + 1)},\\mathbf{b}^{(n + 1)},\\mathbf{w}^{n},\\mathbf{e}^{n})\\,\\text{if}\\,\\mathbf{e}^{(n + 1)} \\geq \\mathbf{0},} \\\\ {\\mathbf{e}^{n}\\text{if}\\,\\mathbf{e}^{(n + 1)} < \\mathbf{0};} \\\\ \\end{array}~ \\right.} \\\\ \\end{array}$$

$$\\begin{array}{r} \\left. \\text{\\quad\\quad}\\mathbf{e}^{(n + 1)}\\Rightarrow E^{(n + 1)}; \\right. \\\\ \\end{array}$$

$$\\begin{array}{r} {X^{(n + 1)} = E^{(n + 1)}\\left\\{ {\\left\\lbrack {B^{(n + 1)}\\left( {UQ^{(n + 1)}} \\right)} \\right\\rbrack W^{(n + 1)}} \\right\\};} \\\\ \\end{array}$$

$$\\begin{array}{r} {\\mathcal{H}^{(n + 1)} = {\\sum\\limits\_{i = 1}^{m}{\\sum\\limits\_{j = 1}^{s}x\_{ij}^{(n + 1)}}}\\ln\\frac{x\_{ij}^{(n + 1)}}{u\_{ij}}.} \\\\ \\end{array}$$

* *c) 停止条件：*

$$\\begin{array}{r} {\\text{If}\\,\\,\\mathcal{H}^{(n + 1)} - \\mathcal{H}^{(n)} \\leq \\delta,\\,\\text{then}\\, STOP.} \\\\ \\end{array}$$

## 3.4 在矩阵范数和信息容量约束下熵的降低

在应用数据矩阵的熵降低时，希望得到具有确定性质的降维矩阵。就 EDR 方法而言，这意味着对投影矩阵的类引入一些限制，这间接影响得到的降维矩阵。考虑投影矩阵的一些有用特征。


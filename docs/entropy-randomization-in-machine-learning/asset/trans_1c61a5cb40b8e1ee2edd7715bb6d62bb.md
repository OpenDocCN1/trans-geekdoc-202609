

$$\\begin{aligned} {\\mathbf{n}^{(k)}\\lbrack W(\\mathbf{u}),G_{j}({\\overline{\\eta}}^{(j)},j)\\rbrack} & {= \\left\\{ {\\lbrack N_{i}^{(k)}(j)\\rbrack}^{1/k},\\, \\middle| \\, i = \\overline{1,m} \\right\\},} \\\\ & {j = \\overline{1,s}.} \\\\ \\end{aligned}$$  

(5.15)

在这些公式中，对应向量元素的 `k`th 阶矩由下式给出

$$\\begin{aligned} {M_{i}^{(k)}(j) =} & \\left. \\int_{\\mathcal{A}}y_{i}^{k}(t_{j},\\, \\middle| \\,\\mathbf{a})P(\\mathbf{a})d\\mathbf{a} + \\int_{\\Xi_{j}}{\\lbrack\\xi_{i}^{(j)}\\rbrack}^{k}Q_{j}({\\overline{\\xi}}^{(j)})d\\xi_{i}^{(j)}, \\right. \\\\ N_{i}^{(k)} & \\left. (j) = \\int_{\\mathcal{U}}z_{i}^{k}(t_{j},\\, \\middle| \\,\\mathbf{u})W(\\mathbf{u})d\\mathbf{u} + {\\lbrack\\xi^{(j})}\\rbrack_{i}^{k} + \\right. \\\\ & {+ K_{ji}\\int_{\\mathcal{E}}{\\lbrack\\eta_{i}^{(j)}\\rbrack}^{k}G_{j}({\\overline{\\eta}}^{(j)})d\\eta_{i}^{(j)}.} \\\\ \\end{aligned}$$  

(5.16)

## 6. 平衡模型 (BM)

`Balancing model (BM)` 用于将可用的输出数据 `y` 与集合 `𝒱` 或 `ℱ` 的接受特征进行比较。

对于随机化模型，平衡约束的形式为

$$\\begin{array}{r} {\\mathbf{m}^{(k)}\\lbrack P(\\mathbf{a}),Q_{j}({\\overline{\\xi}}^{(j)}),j\\rbrack = \\mathbf{y}(t_{j}),\\text{\\quad\\quad}j = \\overline{1,s};} \\\\ \\end{array}$$  

(5.17)

$$\\begin{array}{r} {\\mathbf{n}^{(k)}\\lbrack W(\\mathbf{u}),G_{j}({\\overline{\\eta}}^{(j)},j)\\rbrack = \\mathbf{y}(t_{j}),\\text{\\quad\\quad}j = \\overline{1,s}.} \\\\ \\end{array}$$  

(5.18)

## 7. 机器学习算法 (ML-A)

`Machine learning algorithm (ML-A)` 的目的是为参数和测量噪声的概率密度函数形成最优估计。如前所述反复提及，随机化机器学习过程需要在由信息熵表征的最大不确定性下估计概率密度函数。因此，`ML-A` 在可容许集合上以平衡约束 `(5.17, 5.18)` 的形式搜索其约束最大值。

信息熵泛函 `ℋ` 定义在连续可微概率密度函数 `P(a)`、`Q1(overline{ξ}^{(1)})`、…、`Qs(overline{ξ}^{(s)})` 的类上，它们分别描述了模拟测量误差的随机化参数和噪声的概率性质。熵泛函推广了信息熵的有限维概念。

1865 年，德国物理学家 R. Clausius 引入了一个物理量来表征热力学系统，称为 *熵*。

$$\\begin{array}{r} {S = \\frac{\\Delta Q}{\\Delta T}.} \\\\ \\end{array}$$

1877 年，L. Boltzmann 建立了热力学熵 `S`（或物理熵 `E`）与热力学系统宏观态 (`ΔQ`、`T`) 的统计权重 `Z` 之间的关系。后来，利用微观态等概率的假设，M. Planck 将该关系写成

$$\\begin{array}{r} {S = k\\ln Z = E.} \\\\ \\end{array}$$

这里 `k` = 1.38 ⋅ 10^( − 23) 表示玻尔兹曼常数。宏观态 (`ΔQ`、`T`) 的统计权重由构成该宏观态的所有可能微观态（组合）的数量来度量。回想一下，这些术语适用于所谓的（单原子或多原子）气体模型，该模型考虑由极多不可区分的粒子（分子）组成的系统（宏观系统）。系统宏观态的空间由 `m` 个不相交的子集组成，具有给定的容量 `G[1]`、…、`G[m]`（即粒子可以占据的状态数）。粒子以随机方式在这些子集的状态中分布，行为呈随机性，具有相同的概率且相互独立。设每个粒子被唯一标记，并列出所有标记粒子的所得子集；事实上，该列表是系统的微观态。当然，所考虑的列表体积巨大。可以提取具有相同粒子数 `N[k]` 在第 `k` 个子集中的子列表。粒子数 `N[k]` 是系统宏观态 `N` = `{N[1],…,N[m]}` 的一个元素。子列表中元素的数量（诱导给定宏观态的微观态的数量）称为其统计权重 `Z` = `Z(N[k])`。

为了找到统计权重 `Z` 与宏观态特征 `N[k]`（填充第 `k` 个子集的粒子数）之间的关系，我们需要对宏观系统模型进行一定的推广。该推广涉及粒子在宏观态空间的子集上分布的先验概率 `a[1]`、…、`a[m]` 的信息，以及这些子集中状态的性质信息。注意，在气体模型中，先验概率被假定为相等，且未描述状态性质。

考虑一个每个状态只能被一个粒子占据的宏观系统（否则状态为空）。子集中的此类状态数量为 `G[1]`、…、`G[m]`。分布机制具有以下组织。每个粒子可以 *占据* 第 `k` 个子集中的 `N[k]` 个状态，先验概率为 `a[k]`，随机且独立于其他粒子；因此，(`G[k]` − `N[k]`) 个状态以先验概率 `(1 − a[k])` 保持空闲。用 `{N[k],(G[k]−N[k])}` 表示该事件。由于该分布机制中所有粒子的独立性，事件的概率构成

$$\\begin{array}{r} {a_{k}^{N_{k}}\\,{(1 - a_{k})}^{(G_{k} - N_{k})}.} \\\\ \\end{array}$$

填充状态数 `N[k]` 可以通过粒子在第 `k` 个子集上的不同分布来实现，即不同的微观态。这样的微观态数 `Z(N[k])` 是 `G[k]` 个粒子中 `N[k]` 个组合的数量：

$$\\begin{array}{r} {C_{N_{k}}^{G_{k}} = \\frac{G_{k}!}{N_{k}!\\,(G_{k} - N_{k})!}.} \\\\ \\end{array}$$

事件 `{N[k],(G[k]−N[k])}` 可以 *要么* 由第 1 个微观态实现，*要么* 由第 2 个微观态实现，…，*要么* 由第 `C[N[k]]^(G[k])` 个微观态实现。因此，事件 `{N[k],(G[k]−N[k])}` 以概率发生

$$\\begin{array}{r} {P_{k}(N_{k}) = \\frac{G_{k}!}{N_{k}!\\,(G_{k} - N_{k})!}\\, a_{k}^{N_{k}}\\,{(1 - a_{k})}^{(G_{k} - N_{k})}.} \\\\ \\end{array}$$

由于分布机制的所有参与者相互独立，该宏观系统的对应宏观态的概率由下式给出

$$\\begin{array}{r} {P(\\mathbf{N}) = {\\prod\\limits_{k = 1}^{m}P_{k}}(N_{k}) = {\\prod\\limits_{k = 1}^{m}\\frac{G_{k}!}{N_{k}!\\,(G_{k} - N_{k})!}}\\, a_{k}^{N_{k}}\\,{(1 - a_{k})}^{(G_{k} - N_{k})}.} \\\\ \\end{array}$$

根据 Planck 的定义，物理熵与概率分布函数的对数成正比，因为统计权重是一个未归一化的分布。因此，

$$\\begin{array}{r} {\\left. S \\right.\\sim lnP(\\mathbf{N}).} \\\\ \\end{array}$$

于是可得

$$\\begin{array}{r} {\\left. S \\right.\\sim{\\sum\\limits_{k = 1}^{m}\\ln}G_{k}! - \\ln(G_{k} - N_{k})! - \\ln N_{k}! + N_{k}\\ln a_{k} + (G_{k} - N_{k})\\ln(1 - a_{k}).} \\\\ \\end{array}$$

由于 `N[k]` 的值很大，采用 Stirling 近似

$$\\begin{array}{r} {\\ln N! = N(\\ln N - 1).} \\\\ \\end{array}$$

在这种情况下，`S` 表达式的右手边可以写成常数与宏观态函数的和：

$$\\begin{array}{r} {\\left. S \\right.\\sim C + H_{F}(\\mathbf{N}).} \\\\ \\end{array}$$

函数

$$\\begin{array}{r} {H_{F}(\\mathbf{N}) = - {\\sum\\limits_{k = 1}^{m}\\left\\lbrack {\\, N_{k}\\frac{N_{k}}{{\\widetilde{a}}_{k}} + (G_{k} - N_{k})\\ln(G_{k} - N_{k})\\,} \\right\\rbrack},\\quad{\\widetilde{a}}_{k} = \\frac{a_{k}}{1 - a_{k}},} \\\\ \\end{array}$$


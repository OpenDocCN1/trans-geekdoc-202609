
(另见 Fig. 4.11a。) 这里动态特性由脉冲特性 $w_{h}\lbrack n\rbrack,\, h = \overline{1,R},$ 反映，具有有限的“记忆” *K*[*h*]，即

$$\begin{array}{r} {w_{h}\lbrack n\rbrack \neq 0,\quad\text{for}\,\, 0 \leq n \leq K_{h};\text{\quad\quad}r_{h}\lbrack n\rbrack = 0,\quad\text{for}\,\, n > K_{h}.} \\ \end{array}$$

(6.32)

将脉冲特性的纵坐标作为模型参数。换句话说，参数构成向量

$$\begin{array}{r} {\mathbf{c}^{(h)} = \left\{ c_{1}^{(h)},\ldots,c_{K_{h}}^{(h)} \right\},} \\ \end{array}$$

(6.33)

其中

$$\begin{array}{r} {c_{n}^{(h)} = w_{h}\lbrack n\rbrack,\text{\quad\quad}n = \overline{0,K_{h}}.} \\ \end{array}$$

(6.34)

利用隶属概率 **p**，将参数向量 **c**^((*h*)) 写成形式 (6.29)。将这些等式代入 (6.31) 得到模型方程

$$\begin{array}{r} {s\lbrack j\rbrack = {\sum\limits_{h = 1}^{R}\left( {\left\langle \mathbf{c}_{-}^{(h)},\mathbf{x}\lbrack j\rbrack \right\rangle + \left\langle C_{h}\,\mathbf{p}^{(h)},\mathbf{x}\lbrack j\rbrack \right\rangle} \right)^{h}},} \\ \end{array}$$

(6.35)

其中 **x**\[*j*\] = {*x*\[*j*\],…,*x*\[*j*−*K*[*h*]\]}。

因此，模型输出与参数之间的关系本质上是非线性的，更具体地说是幂函数。

### 3. 具有结构化幂非线性的动态模型

对于此类动态模型，函数描述具有以下形式：

$$\begin{array}{r} {s\lbrack j\rbrack = {\sum\limits_{h = 1}^{R}{\sum\limits_{n = 0}^{K_{h}}w_{h}}}\\lbrack n\rbrack x^{h}\lbrack j - n\rbrack,\text{\quad\quad}j > K.} \\ \end{array}$$

(6.36)

(另见 图 4.11b。) 其动态特性由脉冲特性 $w_{h}\lbrack n\rbrack,\, h = \overline{1,R},$ 描述，具有有限的“记忆” *K*[*h*] (6.32)。当该模型的参数采用其脉冲特性的纵坐标时，即参数向量为 **c**^((*h*)) (6.34)。定义由 *x*^(*h*)\[*j*\], …, *x*^(*h*)\[*j* − *K*[*h*]\] 组成的向量 ${\widetilde{\mathbf{X}}}^{h}\lbrack j\rbrack$。则模型方程 (6.36) 可变换为

$$\begin{array}{r} {s\lbrack j\rbrack = {\sum\limits_{h = 1}^{R}\left\langle \mathbf{c},{\widetilde{\mathbf{X}}}^{(h)}\lbrack j\rbrack \right\rangle},\text{\quad\quad}j > K.} \\ \end{array}$$

(6.37)

利用表达式 (6.29) 在该等式中写出

$$\begin{aligned} {s\lbrack j\rbrack} & {= \hat{s}\lbrack j\rbrack + {\sum\limits_{h = 1}^{R}\left\langle C_{h}\,\mathbf{p}^{(h)},{\widetilde{\mathbf{X}}}^{(h)}\lbrack j\rbrack \right\rangle},} \\ {\hat{s}\lbrack j\rbrack} & {= {\sum\limits_{h = 1}^{R}\left\langle \mathbf{c}_{-}^{(h)},{\widetilde{\mathbf{X}}}^{(h)}\lbrack j\rbrack \right\rangle}.} \\ \end{aligned}$$

(6.38)

因此，该结构类的模型在其参数上是线性的。

## 6.3 最优性条件与熵最优归属概率的结构

RPM-QuaRand 模型的熵鲁棒估计问题被归类为有限维熵非线性规划问题。它们的非线性性质完全取决于 RPM-QuaRand 模型的非线性。特别地，如果动态模型由具有 图 4.11a 所示结构的泛函 Volterra 级数表示，则估计问题中的容许集由具有幂非线性的等式系统描述。在这种情况下，容许集通常具有非凸构型，且最优性条件变为局部条件，因此只能数值使用。结果，我们无法从这些条件中提取解的共同结构性质（归属概率）。另一方面，对于可化为线性形式 (6.30, 6.38) 的一维 RPM-QuaRand 模型，我们可以建立全局最优性条件并分析解的结构性质。

### 1. 归一化归属概率

在泛函模型框架内的一般问题由等式 (6.12–6.14) 刻画。它将被改编为泛函模型为一维且可化为线性形式 (6.30) 的情况：

$$\begin{aligned} {s\lbrack j\rbrack} & {= \hat{s}\lbrack j\rbrack + {\sum\limits_{h = 1}^{R}{\sum\limits_{i = 1}^{V_{h}}p_{i}^{(h)}}}z_{i}^{(h)}\lbrack j\rbrack + \zeta_{j}^{-} + Z_{j}q_{j},} \\ \end{aligned}$$

(6.39)

$$\begin{aligned} {\hat{s}\lbrack j\rbrack} & {= {\sum\limits_{h = 1}^{R}{\sum\limits_{i = 1}^{V_{h}}c_{-}^{(h)}}(i)z_{i}^{(h)}\lbrack j\rbrack,} \\ {z_{i}^{(h)}\lbrack j\rbrack} & {= \delta_{i}^{(h)}x_{i}^{(h)}\lbrack j\rbrack,\text{\quad\quad}\delta_{i}^{(h)} = c_{i}^{(h, + )} - c_{i}^{(h, - )},\quad i = \overline{1,V_{h}},} \\ Z_{j} & {= \zeta_{j}^{+} - \zeta_{j}^{-},\text{\quad\quad}j = \overline{1,s}.} \\ \end{aligned}$$

(6.40)

然后估计问题 (6.12) 中的约束 (6.13, 6.14) 采用以下形式。

* 泛函模型功率块中模型参数归属概率的归一化条件为

$$\begin{array}{r} {{\sum\limits_{i = 1}^{V_{h}}p_{i}^{(h)}} = 1,\quad h = \overline{1,R};} \\ \end{array}$$

(6.41)

* 测量噪声归属概率的归一化条件为

$$\begin{array}{r} {{\sum\limits_{j = 1}^{s}q_{j}} = 1;} \\ \end{array}$$

(6.42)

* 经验平衡条件为

$$\begin{aligned} & {\widetilde{s}\lbrack j\rbrack + {\sum\limits_{h = 1}^{R}{\sum\limits_{i = 1}^{V_{h}}p_{i}^{(h)}}}z_{i}^{(h)}\lbrack j\rbrack + Z_{j}q_{j} - y\lbrack j\rbrack = 0,\quad j = \overline{1,s},} \\ & {\widetilde{s}\lbrack j\rbrack = \hat{s}\lbrack j\rbrack + \zeta_{j}^{-}.} \\ \end{aligned}$$

(6.43)

熵函数由下式给出

$$\begin{array}{r} {H_{B}(P,Q) = - {\sum\limits_{h = 1}^{R}{\sum\limits_{i = 1}^{V_{h}}p_{i}^{(h)}}}\,\ln\frac{p_{i}^{(h)}}{{\widetilde{p}}_{i}^{(h)}} - {\sum\limits_{j = 1}^{s}q_{j}}\,\ln\frac{q_{j}}{{\widetilde{q}}_{j}}.} \\ \end{array}$$

(6.44)

因此，估计问题可写为

$$\begin{array}{r} \left. H_{B}(P,Q)\Rightarrow\max \right. \\ \end{array}$$

(6.45)

受约束 (6.41, 6.42, 6.43) 的限制。

在此问题中，容许集 Υ 由等式系统描述，因此它代表一个约束优化问题。为了得到最优性条件，让我们定义拉格朗日函数

$$\begin{aligned} L_{B} & {= H_{B}(P,Q) + {\sum\limits_{h = 1}^{R}\lambda_{h}}\left( {1 - {\sum\limits_{i = 1}^{V_{h}}p_{i}^{(h)}}} \right) + \mu\left( {1 - {\sum\limits_{j = 1}^{s}q_{j}}} \right)} \\ & {+ {\sum\limits_{j = 1}^{s}\theta^{(j)}}\left( {y\lbrack j\rbrack - \widetilde{s}\lbrack j\rbrack - {\sum\limits_{h = 1}^{R}{\sum\limits_{i = 1}^{V_{h}}p_{i}^{(h)}}}\delta_{i}^{(h)}x_{i}^{(h)}\lbrack j\rbrack + Z_{j}q_{j}} \right).} \\ \end{aligned}$$

(6.46)

这里 *λ*[1], …, *λ*[*R*]； *μ*； *θ*[1], …, *θ*[*s*] 表示对应约束 (6.41, 6.42, 6.43) 的拉格朗日乘子。直接变量 (*P*， *Q*) 上的第一阶最优性条件给出以下方程组：

$$\begin{aligned} \frac{\partial L}{\partial p_{i}^{(h)}} & {= - \ln\frac{p_{i}^{(h)}}{{\widetilde{p}}_{i}^{(h)}} - 1 - \lambda_{h} - {\sum\limits_{j = 1}^{s}\theta_{j}}z_{i}^{(h)}\lbrack j\rbrack = 0,} \\ h & {= \overline{1,s};\text{\quad\quad}i = \overline{1,V_{h}}.} \\ \end{aligned}$$

(6.47)

$$\begin{array}{r} {\frac{\partial L}{\partial q_{j}} = \ln\frac{(1 - q_{j}){\widetilde{q}}_{j}}{q_{j}} - \mu - Z_{j} = 0,\text{\quad\quad}j = \overline{1,s}.} \\ \end{array}$$

(6.48)

结合归一化条件 (6.41, 6.42)，方程 (6.47, 6.48) 导出模型参数和测量噪声的熵最优归属概率的以下表达式，其参数化为拉格朗日乘子 *θ*[1], …, *θ*[*s*]：

$$\begin{aligned} {\lbrack p_{i}^{(h)}\rbrack}^{\*} & {= \frac{{\widetilde{p}}_{i}^{(h)}\exp\left( {- {\sum\limits_{j = 1}^{s}\theta_{j}}z_{i}^{(h)}\lbrack j\rbrack} \right)}{{\sum\limits_{k = 1}^{V_{h}}{\widetilde{p}}_{k}^{(h)}}\exp\left( {- {\sum\limits_{m = 1}^{s}\theta_{j}}z_{k}^{(h)}\lbrack m\rbrack} \right)},} \\ q_{j}^{\*} & {= \frac{{\widetilde{q}}_{j}\exp( - \theta_{j}Z_{j})}{{\sum\limits_{m = 1}^{s}{\widetilde{q}}_{m}}\exp( - \theta_{m}Z_{m})}.} \\ \end{aligned}$$

(6.49)

$$\begin{array}{r} {h = \overline{1,R},\quad i = \overline{1,V_{h}},\quad j = \overline{1,s}} \\ \end{array}$$

引入 *V*[*h*] 个整数自变量函数 $P^{(h)}\lbrack i\rbrack,\, i = \overline{}1,V_{h},$ 其值由熵最优归属概率定义。按此定义，$P^{(h)}\lbrack i\rbrack,\, i = \overline{}1,V_{h},$ 表示归属概率的分布函数。根据 (6.49)，它们是指数函数。

拉格朗日乘子 *θ*[1], …, *θ*[*s*] 由经验平衡约束 (6.43) 计算得出，并在其中代入了熵最优的归属概率 (6.49)。为便于记号，引入

```
\begin{aligned} {S\lbrack j\rbrack} & {= \hat{s}\lbrack j\rbrack + \zeta_{j}^{-} - y\lbrack j\rbrack,} \\ { \varphi^{(h)}(\theta_{1},\ldots,\theta_{s})} & {= {\sum\limits_{k = 1}^{(V_{h})}{\widetilde{p}}_{k}^{(h)}}\,\exp( - {\sum\limits_{l = 1}^{s}\theta_{l}}z_{k}^{(h)}\lbrack l\rbrack),} \\ { \psi_{j}^{(h)}(\theta_{1},\ldots,\theta_{s})} & {= {\sum\limits_{k = 1}^{(V_{h})}{\widetilde{p}}_{k}^{(h)}}\, z_{k}^{(h)}\lbrack j\rbrack\,\exp( - {\sum\limits_{l = 1}^{s}\theta_{l}}z_{k}^{(h)}\lbrack l\rbrack),} \\ \end{aligned}
```

(6.50)

以及

```
\begin{aligned} {\mu(\theta_{1},\ldots,\theta_{s}) = {\sum\limits_{l = 1}^{s}{\widetilde{q}}_{l}}} & {\exp( - \theta_{l}Z_{l}),\quad\nu_{j}(\theta_{j}) = {\widetilde{q}}_{j}Z_{j}\exp( - \theta_{j}Z_{j}),} \\ & {\text{\quad\quad}j = \overline{1,s}.} \\ \end{aligned}
```

(6.51)

利用这些记号，经验平衡约束可写为

```
\begin{array}{r} {{\sum\limits_{h = 1}^{R}\frac{\psi_{j}^{(h)}(\theta_{1},\ldots,\theta_{s})}{\varphi^{(h)}(\theta_{1},\ldots,\theta_{s})}} + \frac{\nu_{j}(\theta_{j})}{\mu(\theta_{1},\ldots,\theta_{s})} + S\lbrack j\rbrack = 0,\text{\quad\quad}j = \overline{1,s}.} \\ \end{array}
```

(6.52)

## 2. 区间型归属概率

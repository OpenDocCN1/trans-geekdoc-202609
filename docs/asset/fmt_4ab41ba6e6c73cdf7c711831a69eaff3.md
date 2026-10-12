
# 10.2 多维逆问题与响应函数

迄今讨论的逆问题涉及一维真实分布和一维观测分布。虽然原则上通过合适的分箱和相应的映射，高维逆问题也可以转化为这种形式，但这并不总是切合实际。结果，响应函数可能会获得对未知分布的依赖，导致系统不确定性，因为响应函数 `A(x|y)` 并不精确已知。

为了说明这一点，考虑测量 `x` 受两个变量 `y[1]` 和 `y[2]` 值影响的情况，例如能量测量 `x` 取决于粒子的真实能量 `y[1]` 以及其入射探测器的倾角 `y[2]`。在这种情况下，方程 10.1 变为

(10.23) `g(x) = ∫[y]dy[1]dy[2]A(x|y[1],y[2])f(y[1],y[2]).`

为了处理仅涉及 `x` 和 `y[1]` 的一维问题，可以通过对 `y[2]` 积分来重写方程 10.23，得到

(10.24) $g(x) = {\int d}y_{1}\left( \frac{{\int d}y_{2}A\left( {x \mid y_{1},y_{2}} \right)f\left( {y_{1},y_{2}} \right)}{{\int d}y_{2}f\left( {y_{1},y_{2}} \right)} \right) \cdot {\int d}y_{2}f\left( {y_{1},y_{2}} \right)\quad\left( 10.24 \right)$

或

(10.25) `g(x) = ∫dy[1]A(x|y[1])f(y[1]),`

其中真实能谱为 `f(y[1])`，响应函数为 `A(x|y[1])`

(10.26) $f\left( y_{1} \right) = {\int d}y_{2}f\left( {y_{1},y_{2}} \right)\text{~and~}A\left( {x \mid y_{1}} \right) = \frac{{\int d}y_{2}A\left( {x \mid y_{1},y_{2}} \right)f\left( {y_{1},y_{2}} \right)}{{\int d}y_{2}f\left( {y_{1},y_{2}} \right)}.\quad\left( 10.26 \right)$

通过降低逆问题的维度，响应函数获得了对 `y[1]` 和 `y[2]` 中未知真实密度的依赖。如果真实概率密度函数可分解，`f(y[1], y[2]) = f1 f2`，则可得

(10.27) `A(x|y[1]) = ∫dy[2]A(x|y[1],y[2])f2,`

即响应函数仅依赖于 `y[2]` 中的真实分布。

## 10.2.4 数学附录：余弦函数积分

对于 `k > 0 ∈ N`，恒等式

(10.28) ${\int_{0}^{\pi}dy}f(y)\cos(ky) = {\sum\limits_{m = 1}^{\infty}\frac{{( - 1)}^{m}}{k^{2m}}}\left\lbrack {f^{(2m - 1)}(0) - {( - 1)}^{k}f^{(2m - 1)}(\pi)} \right\rbrack\quad\left( 10.28 \right)$

可由以下式子得出

(10.29) ${\int d}yy^{n}\cos(ky) = {\sum\limits_{m = 0}^{n}m}!\begin{pmatrix} n \\ m \\ \end{pmatrix}\frac{y^{n - m}}{k^{m + 1}}\sin\left( {ky + \frac{m\pi}{2}} \right)\quad\left( 10.29 \right)$

通过在 `y = 0` 处对 `f(y)` 进行泰勒展开

(10.30) $f(y) = {\sum\limits_{n = 0}^{\infty}f^{(n)}}(0)\frac{y^{n}}{n!}.\quad\left( 10.30 \right)$

可得

### 数学推导

```
\begin{array}{l}
{\int_{0}^{\pi}dy\,f(y)\cos(ky) = \sum\limits_{n = 0}^{\infty}\frac{f^{(n)}(0)}{n!}\int_{0}^{\pi}dy\,y^{n}\cos(ky)} \\
{\quad = \left. {\sum\limits_{n = 0}^{\infty}{\sum\limits_{m = 0}^{n}\frac{f^{(n)}(0)}{n!}}}m!\left( \begin{array}{l} n \\ m \\ \end{array} \right)\frac{y^{n - m}}{k^{m + 1}}\sin\left( {ky + \frac{m\pi}{2}} \right) \right|_{0}^{\pi}} \\
{\quad = \left. {\sum\limits_{m = 0}^{\infty}\sin}\left( {ky + \frac{m\pi}{2}} \right)\frac{1}{k^{m + 1}}{\sum\limits_{n = m}^{\infty}f^{(n)}}(0)\frac{y^{n - m}}{(n - m)!} \right|_{0}^{\pi}\quad\quad\quad\quad\quadquad\quadquad\quadquad\quadquad\quadquad\quadquad\left( 10.31 \right)}
\end{array}
```

其中在最后一步中，对 `m` 和 `n` 的求和顺序进行了交换。现在，对 `n` 的求和可以识别为 `f(y)` 的 `m` 阶导数，

```
\begin{array}{l}
{\sum\limits_{n = m}^{\infty}f^{(n)}(0)\frac{y^{n - m}}{(n - m)!} = \frac{d^{m}}{dy^{m}}\sum\limits_{n = m}^{\infty}f^{(n)}(0)\frac{y^{n}}{n!}} \\
{\quad\quad\quad\quadquad\quadquad\quadquad\quadquad\quadquad\quadquad = \frac{d^{m}}{dy^{m}}\sum\limits_{n = 0}^{\infty}f^{(n)}(0)\frac{y^{n}}{n!} = \frac{d^{m}}{dy^{m}}f(y)\quadquad\quadquad\quadquad\quadquad\quadquadquadquad\left( 10.32 \right)}
\end{array}
```

上述表达式简化为

```
\begin{array}{l}
{\int_{0}^{\pi}dy\,f(y)\cos(ky)} \\
{\quad = \sum\limits_{m = 0}^{\infty}\frac{1}{k^{m + 1}}\left( {\sin\left( {k\pi + \frac{m\pi}{2}} \right)f^{(m)}(\pi) - \sin\left( \frac{m\pi}{2} \right)f^{(m)}(0)} \right).\quadquad\quadquad\quadquad\quadquad\quadquadquad\left( 10.33 \right)}
\end{array}
```

这里偶数 `m` 值不做贡献，通过替换 `m` → 2`m` − 1 可得出结果公式 10.28。

# 10.3 基于似然的去卷积

**Mirko Bunse**

**Tim Ruhe**

**Maximilian Linhoff**

**摘要：** 基于似然的去卷积方法产生的估计值，在明确定义的先验假设方面，最有可能反映数据生成过程。在伽马射线天文学中，一些合理的假设是：伽马粒子相互独立地被测量，其真实率取决于粒子能量和研究的天体。探测器会“模糊”这些潜在的率，因为真实的粒子能量从未被直接测量，只能通过不确定性进行估计。似然函数捕捉了这些假设，并可代入第一类 Fredholm 积分方程，该方程对去卷积任务进行建模。它们通常伴随着正则化函数，确保方法对数据中的噪声具有鲁棒性，主要是在观测数量较少时。我们重点回顾了现有的基于似然的去卷积方法，聚焦于我们的软件 `TRUEE`。

## 10.3.1 简介

基于似然的去卷积方法是通过最大化似然函数来产生去卷积结果的算法。这种似然函数基于一个统计模型 ${\mathbb{P}}(\overset{\rightarrow}{x} \mid \overset{\rightarrow}{\theta})$，该模型在给定参数向量 $\overset{\rightarrow}{\theta}$ 的情况下，为每个观测值 $\overset{\rightarrow}{x}$ 分配一个概率。利用该模型，似然最大化方法本质上选择使所有观测值集合的概率最大化的那些参数。换句话说，如果一组参数给观测数据分配了很高的概率，我们就称这组参数“似然”大。在这种情况下，我们也称数据与参数之间有良好的“一致性”。

最大似然法的两个关键假设是：所有 $\overset{\rightarrow}{x} \in X$ *i)* 彼此统计独立，且 *ii)* 服从相同的分布 ${\mathbb{P}}(\overset{\rightarrow}{x} \mid \overset{\rightarrow}{\theta})$，具有相同的 $\overset{\rightarrow}{\theta}$ 向量。似然函数 `L` 的定义反映了这样一种直觉：当一组参数给随机样本分配很高的概率时，该组参数就是似然的

(10.34) $L(\overset{\rightarrow}{\theta} \mid D) = {\mathbb{P}}(D \mid \overset{\rightarrow}{\theta}) = {\prod\limits_{\overset{\rightarrow}{x} \in D}{\mathbb{P}}}(\overset{\rightarrow}{x} \mid \overset{\rightarrow}{\theta}).\quad\quad\quadquad\quadquad\quadquad\quadquad\left( 10.34 \right)$

某些似然函数可以解析地最大化。然而，通常我们需要使用数值优化方法来寻找使 `L` 最大化的参数。不幸的是，通过数值优化方法直接最大化 `L` 会引入一个可描述为缺乏“数值稳定性”的问题。即，`L` 中 ${\mathbb{P}}(\overset{\rightarrow}{x} \mid \overset{\rightarrow}{\theta})$ 的许多微小值在相乘后变得更小，难以用典型的浮点变量表示。这种困难极易导致结果估计中出现压倒性的噪声水平。事实上，直接数值最大化 `L` 会导致许多解不足以服务于其预期目的。

幸运的是，通过最大化 `L` 的对数而不是直接最大化 `L`，可以规避这种数值稳定性的缺失。对数产生的数值计算机更容易表示，但两个最大化任务的解是相同的。按照数值优化的惯例，我们进一步选择*最小化*负对数，而不是最大化 `L` 的对数。同样，该解与我们实际寻找的解相同：

```
\begin{array}{l}
{\overset{\rightarrow}{\theta}_{\max L} = \underset{\overset{\rightarrow}{\theta}}{\arg\max}L(\overset{\rightarrow}{\theta} \mid D)} \\
{\quad = \underset{\overset{\rightarrow}{\theta}}{\arg\min}( - \ln L(\overset{\rightarrow}{\theta} \mid D)) = \underset{\overset{\rightarrow}{\theta}}{\arg\min}\left( {- {\sum\limits_{\overset{\rightarrow}{x} \in D}\ln}{\mathbb{P}}(\overset{\rightarrow}{x} \mid \overset{\rightarrow}{\theta})} \right)\quadquad\quadquad\quadquad\quadquad\quadquad\quadquad\left( 10.35 \right)}
\end{array}
```

公式 10.35 右侧定义了许多现成的优化技术可用来寻找最大似然估计的优化任务。对于似然最大化的一般概念而言，解决去卷积问题所剩下的只是定义一个特定于去卷积的统计模型。

我们希望该模型能够理解关于数据的合理假设。此外，`\overset{\rightarrow}{\theta}` 中的参数值应有助于我们理解观测结果背后的物理过程。为此，我们将模型的自由参数与真实底层分布的分箱 `{\overset{\rightarrow}{f}}_{i} = {\overset{\rightarrow}{\theta}}_{i}` 相对应。在本例中，该分布即为我们想要估计的能谱，因此绘制 `\overset{\rightarrow}{\theta}` 将得到我们所追求的谱 *f* (*y*) 的离散变体。此外，我们将观测量的分箱建模为 `{\overset{\rightarrow}{g}}_{j} = {\overset{\rightarrow}{x}}_{j}`。因此，统计模型需要将目标分箱（真实能量）与观测量的分箱（能量估计或特征）联系起来。最大化似然函数随后允许我们向模型输入观测值 `\overset{\rightarrow}{g}` 以获得最可能的谱 `\overset{\rightarrow}{f}`。

`\overset{\rightarrow}{g}` 的内容是离散化步骤产生的统计独立事件的整数计数，这将在下一节详细说明。此处的重要特性是泊松统计描述了这种计数实验。每个 `{\overset{\rightarrow}{g}}_{i}` 预期遵循其自身的泊松分布，该分布通过响应矩阵 *A* 将 `\overset{\rightarrow}{f}` 中的真实量与我们观测到的计数 `\overset{\rightarrow}{g}` 联系起来。这种联系给出了以下似然函数：

```
(10.36) $L(\overset{\rightarrow}{f} \mid \overset{\rightarrow}{g}) = {\prod\limits_{j = 1}^{J}e^{- A_{.j}^{\top}\overset{\rightarrow}{f}}}\frac{\left( {A_{.j}^{\top}\overset{\rightarrow}{f}} \right)^{{\overset{\rightarrow}{g}}_{j}}}{{\overset{\rightarrow}{g}}_{j}!}. \left( 10.36 \right)$
```

虽然泊松似然能很好地描述该问题——针对小计数——但它尚未解决逆问题的病态性。此外，似然函数的优化仍会产生振荡结果，这些结果 i) 偏离真实的 `\overset{\rightarrow}{f}` 且 ii) 通常是*非物理的*。特别是能谱，不期望其相邻条目 `{\overset{\rightarrow}{f}}_{i},{\overset{\rightarrow}{f}}_{i + 1}` 之间存在巨大差异。相反，预期起作用的物理过程会产生*平滑*的谱。为解决此问题，向似然函数添加了一个额外的正则化项，用于惩罚 `\overset{\rightarrow}{f}` 的大二阶导数：

```
(10.37) $r_{\tau}(\overset{\rightarrow}{f}) = \frac{\tau}{2} \cdot {\sum\limits_{i = 2}^{I - 1}\left( {- {\overset{\rightarrow}{f}}_{i - 1} + 2 \cdot {\overset{\rightarrow}{f}}_{i} - {\overset{\rightarrow}{f}}_{i + 1}} \right)^{2}} = \frac{\tau}{2} \cdot {(C\overset{\rightarrow}{f})}^{2} \left( 10.37 \right)$
```

重要的是要强调，必须引入额外假设以改善原始逆问题的条件。此处的假设是结果 *f* 应当是*平滑*的，由低二阶导数定义。这些包含在似然函数中的额外假设将因问题而异，因领域而异。上述方法是 Tikhonov 正则化 [366, 367] 的一种特殊形式，它利用离散二阶导数来产生平滑解。矩阵 *C* 的另一种常见选择是单位矩阵，这将惩罚 `\overset{\rightarrow}{f}` 的大范数。

对于实际解决方案，重要的是要考虑 *f* 中的值代表什么，以及可以做出哪种平滑性或小范数假设。如上所述，必须处理的效应之一是有限的探测效率：并非所有到达探测器的事件都被记录，也并非所有记录的事件都被成功分析。在天体物理学中，平滑性假设通常只能针对未受这些效应影响的原始物理谱 *f* 做出。此问题将在第 10.5 节中更详细地讨论，届时将基于似然的展开应用于 FACT 开放数据集。

最小化以下目标函数等价于最大化带有公式 10.37 正则化项的公式 10.36 似然函数：

```
(10.38) $\mathcal{l}(\overset{\rightarrow}{f};\overset{\rightarrow}{g},\tau) = - \ln L(\overset{\rightarrow}{f} \mid \overset{\rightarrow}{g}) + r_{\tau}(\overset{\rightarrow}{f}) \left( 10.38 \right)$
```

## 10.3.2 可观测量的离散化

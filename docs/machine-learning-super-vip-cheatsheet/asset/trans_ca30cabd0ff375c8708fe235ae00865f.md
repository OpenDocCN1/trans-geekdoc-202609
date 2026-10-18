
|  | 分类 |  |  |
|---|---|---|---|
| **分类** | 散点图显示两个类别被对角线线性决策边界分开。 | 散点图显示两个类别被弯曲的决策边界分开。 | 散点图显示类别周围复杂、不规则的决策边界。 |
| **深度学习** | 训练和验证误差曲线在若干轮后下降并收敛。 | 训练误差比验证误差下降得更快、更低，且差距更大。 | 训练误差趋于零，而验证误差稳定在较高值。 |
| **补救措施** | - 使模型复杂化<br>- 添加更多特征<br>- 延长训练时间 | *（空白）* | - 正则化<br>- 获取更多数据 |

- **错误分析** – 错误分析是分析当前模型与完美模型之间性能差异的根本原因。
- **消融分析** – 消融分析是分析当前模型与基线模型之间性能差异的根本原因。

## 5  复习

### 5.1  概率与统计

#### 5.1.1  概率与组合学导论

- **样本空间** – 实验所有可能结果的集合称为该实验的样本空间，记为 $S$。
- **事件** – 样本空间的任何子集 $E$ 称为一个事件。也就是说，事件是由实验的可能结果组成的集合。如果实验的结果包含在 $E$ 中，我们就说 $E$ 发生了。
- **概率公理** – 对于每个事件 $E$，我们用 $P(E)$ 表示事件 $E$ 发生的概率。记 $E_1,\ldots,E_n$ 为互斥事件，我们有以下 3 条公理：

$$(1)\quad 0 \le P(E) \le 1 \qquad (2)\quad P(S)=1 \qquad (3)\quad P\left(\bigcup_{i=1}^{n}E_i\right)=\sum_{i=1}^{n}P(E_i)$$

- **排列** – 排列是从 $n$ 个对象中按给定顺序选取 $r$ 个对象的一种安排。这种安排的数量由 $P(n,r)$ 给出，定义为：

$$P(n,r)=\frac{n!}{(n-r)!}$$

- **组合** – 组合是从 $n$ 个对象中选取 $r$ 个对象的一种安排，其中顺序无关紧要。这种安排的数量由 $C(n,r)$ 给出，定义为：

$$C(n,r)=\frac{P(n,r)}{r!}=\frac{n!}{r!(n-r)!}$$

> 注：我们注意到对于 $0 \le r \le n$，我们有 $P(n,r) \ge C(n,r)$。

#### 5.1.2  条件概率

- **贝叶斯法则** – 对于满足 $P(B)>0$ 的事件 $A$ 和 $B$，我们有：

$$P(A\mid B)=\frac{P(B\mid A)P(A)}{P(B)}$$

> 注：我们有 $P(A\cap B)=P(A)P(B\mid A)=P(A\mid B)P(B)$。

- **划分** – 令 $\{A_i, i\in[1,n]\}$ 满足对所有 $i$，$A_i\ne\varnothing$。如果满足以下条件，则称 $\{A_i\}$ 是一个划分：

$$\forall i\ne j,\ A_i\cap A_j=\varnothing\quad\text{and}\quad\bigcup_{i=1}^{n}A_i=S$$

> 注：对于样本空间中的任何事件 $B$，我们有 $P(B)=\sum_{i=1}^{n}P(B\mid A_i)P(A_i)$。

#### 5.1.3  随机变量

- **随机变量** – 随机变量（通常记为 $X$）是一个将样本空间中的每个元素映射到实数轴上的函数。
- **累积分布函数（CDF）** – 累积分布函数 $F$ 单调非减，且满足 $\lim_{x\to-\infty}F(x)=0$ 和 $\lim_{x\to+\infty}F(x)=1$，其定义为：

$$F(x)=P(X\le x)$$

> _注：_ 我们有 $P(a<X\le b)=F(b)-F(a)$。

- **概率密度函数（PDF）** – 概率密度函数 $f$ 是随机变量 $X$ 在两个相邻实现值之间取值的概率。
- **涉及 PDF 和 CDF 的关系** – 以下是离散（D）和连续（C）情况下需要了解的重要性质。

| 情况 | 累积分布函数 $F$ | 概率密度函数 $f$ | PDF 的性质 |
|---|---|---|---|
| (D) | $F(x)=\displaystyle\sum_{x_i\le x}P(X=x_i)$ | $f(x_j)=P(X=x_j)$ | $0\le f(x_j)\le1$ 且 $\displaystyle\sum_j f(x_j)=1$ |
| (C) | $F(x)=\displaystyle\int_{-\infty}^{x}f(y)\,dy$ | $f(x)=\displaystyle\frac{dF}{dx}$ | $f(x)\ge0$ 且 $\displaystyle\int_{-\infty}^{+\infty}f(x)\,dx=1$ |

- **方差** – 随机变量的方差（通常记为 $\operatorname{Var}(X)$ 或 $\sigma^2$）是衡量其分布函数离散程度的指标。其计算公式如下：

$$\operatorname{Var}(X)=E[(X-E[X])^2]=E[X^2]-E[X]^2$$

- **标准差** – 随机变量的标准差（通常记为 $\sigma$）是衡量其分布函数离散程度的指标，且与实际随机变量的单位一致。其计算公式如下：

$$\sigma=\sqrt{\operatorname{Var}(X)}$$

- **期望与分布的矩** – 以下是离散和连续情况下期望值 $E[X]$、广义期望值 $E[g(X)]$、$k$ 阶矩 $E[X^k]$ 和特征函数 $\psi(\omega)$ 的表达式：

| 情况 | $E[X]$ | $E[g(X)]$ | $E[X^k]$ | $\psi(\omega)$ |
|---|---|---|---|---|
| (D) | $\displaystyle\sum_{i=1}^{n}x_i f(x_i)$ | $\displaystyle\sum_{i=1}^{n}g(x_i)f(x_i)$ | $\displaystyle\sum_{i=1}^{n}x_i^k f(x_i)$ | $\displaystyle\sum_{i=1}^{n}f(x_i)e^{i\omega x_i}$ |
| (C) | $\displaystyle\int_{-\infty}^{+\infty}x f(x)\,dx$ | $\displaystyle\int_{-\infty}^{+\infty}g(x)f(x)\,dx$ | $\displaystyle\int_{-\infty}^{+\infty}x^k f(x)\,dx$ | $\displaystyle\int_{-\infty}^{+\infty}f(x)e^{i\omega x}\,dx$ |

> _注：_ 我们有 $e^{i\omega x}=\cos(\omega x)+i\sin(\omega x)$。

- **重温 $k$ 阶矩** – $k$ 阶矩也可以用特征函数计算如下：

$$E[X^k]=\frac{1}{i^k}\left[\frac{\partial^k\psi}{\partial\omega^k}\right]_{\omega=0}$$

- **随机变量的变换** – 设变量 $X$ 和 $Y$ 通过某个函数相关联。记 $f_X$ 和 $f_Y$ 分别为 $X$ 和 $Y$ 的分布函数，我们有：

$$f_Y(y)=f_X(x)\left|\frac{dx}{dy}\right|$$

- **莱布尼茨积分法则** – 设 $g$ 是 $x$（可能还有 $c$）的函数，且 $a,b$ 为可能依赖于 $c$ 的边界。我们有：

$$\frac{\partial}{\partial c}\left(\int_a^b g(x)\,dx\right)=\frac{\partial b}{\partial c}g(b)-\frac{\partial a}{\partial c}g(a)+\int_a^b\frac{\partial g}{\partial c}(x)\,dx$$

- **切比雪夫不等式** – 设 $X$ 是期望值为 $\mu$、标准差为 $\sigma$ 的随机变量。对于 $k,\sigma>0$，有以下不等式：

$$P(|X-\mu|\ge k\sigma)\le\frac{1}{k^2}$$

#### 5.1.4  联合分布的随机变量

- **条件密度** – $X$ 关于 $Y$ 的条件密度（通常记为 $f_{X\mid Y}$）定义如下：

$$f_{X\mid Y}(x)=\frac{f_{XY}(x,y)}{f_Y(y)}$$

- **独立性** – 如果两个随机变量 $X$ 和 $Y$ 满足以下条件，则称它们是独立的：

$$f_{XY}(x,y)=f_X(x)f_Y(y)$$

- **边缘密度与累积分布** – 由联合密度概率函数 $f_{XY}$，我们有：

| 情况 | 边缘密度 | 累积函数 |
|---|---|---|
| (D) | $f_X(x_i)=\sum_j f_{XY}(x_i,y_j)$ | $F_{XY}(x,y)=\sum_{x_i\le x}\sum_{y_j\le y}f_{XY}(x_i,y_j)$ |
| (C) | $f_X(x)=\int_{-\infty}^{+\infty}f_{XY}(x,y)\,dy$ | $F_{XY}(x,y)=\int_{-\infty}^{x}\int_{-\infty}^{y}f_{XY}(x',y')\,dx'\,dy'$ |

- **独立随机变量之和的分布** – 设 $Y=X_1+\cdots+X_n$，其中 $X_1,\ldots,X_n$ 独立。我们有：

$$\psi_Y(\omega)=\prod_{k=1}^{n}\psi_{X_k}(\omega)$$

- **协方差** – 我们定义两个随机变量 $X$ 和 $Y$ 的协方差（记为 $\sigma^2_{XY}$ 或更常见的 $\operatorname{Cov}(X,Y)$）如下：

$$\operatorname{Cov}(X,Y)\triangleq\sigma^2_{XY}=E[(X-\mu_X)(Y-\mu_Y)]=E[XY]-\mu_X\mu_Y$$

- **相关系数** – 记 $\sigma_X,\sigma_Y$ 为 $X$ 和 $Y$ 的标准差，我们定义随机变量 $X$ 和 $Y$ 之间的相关系数，记为 $\rho_{XY}$，如下：

$$\rho_{XY}=\frac{\sigma^2_{XY}}{\sigma_X\sigma_Y}$$

> _注：_ 对于任意 $X,Y$，我们有 $\rho_{XY}\in[-1,1]$。如果 $X$ 和 $Y$ 独立，则 $\rho_{XY}=0$。

- **主要分布** – 以下是一些需要掌握的主要分布：

| 类型 | 分布 | PDF | $\psi(\omega)$ | $E[X]$ | $\operatorname{Var}(X)$ |
|---|---|---|---|---|---|
| (D) | $X\sim\mathcal{B}(n,p)$<br>二项分布 | $P(X=x)=\binom{n}{x}p^xq^{n-x}$<br>$x\in[0,n]$ | $(pe^{i\omega}+q)^n$ | $np$ | $npq$ |
| (D) | $X\sim\operatorname{Po}(\mu)$<br>泊松分布 | $P(X=x)=\frac{\mu^x}{x!}e^{-\mu}$<br>$x\in\mathbb N$ | $e^{\mu(e^{i\omega}-1)}$ | $\mu$ | $\mu$ |
| (C) | $X\sim\mathcal U(a,b)$<br>均匀分布 | $f(x)=\frac{1}{b-a}$<br>$x\in[a,b]$ | $\frac{e^{i\omega b}-e^{i\omega a}}{(b-a)i\omega}$ | $\frac{a+b}{2}$ | $\frac{(b-a)^2}{12}$ |
| (C) | $X\sim\mathcal N(\mu,\sigma)$<br>高斯分布 | $f(x)=\frac{1}{\sqrt{2\pi}\sigma}e^{-\frac12((x-\mu)/\sigma)^2}$<br>$x\in\mathbb R$ | $e^{i\omega\mu-\frac12\omega^2\sigma^2}$ | $\mu$ | $\sigma^2$ |
| (C) | $X\sim\operatorname{Exp}(\lambda)$<br>指数分布 | $f(x)=\lambda e^{-\lambda x}$<br>$x\in\mathbb R_+$ | $\frac{1}{1-i\omega/\lambda}$ | $\frac1\lambda$ | $\frac1{\lambda^2}$ |

#### 5.1.5  参数估计

- **随机样本** – 随机样本是由 $n$ 个与 $X$ 独立同分布的随机变量 $X_1,\ldots,X_n$ 组成的集合。
- **估计量** – 估计量 $\hat\theta$ 是数据的函数，用于推断统计模型中未知参数 $\theta$ 的值。
- **偏差** – 估计量 $\hat\theta$ 的偏差定义为 $\hat\theta$ 分布期望值与真实值之间的差，即：

$$\operatorname{Bias}(\hat\theta)=E[\hat\theta]-\theta$$

> _注：_ 当 $E[\hat\theta]=\theta$ 时，称该估计量为无偏估计量。

- **样本均值与样本方差** – 随机样本的样本均值和样本方差用于估计分布的真实均值 $\mu$ 和真实方差 $\sigma^2$，分别记为 $\bar X$ 和 $s^2$，且满足：

$$\bar X=\frac1n\sum_{i=1}^{n}X_i \qquad\text{and}\qquad s^2=\hat\sigma^2=\frac1{n-1}\sum_{i=1}^{n}(X_i-\bar X)^2$$

- **中心极限定理** – 设随机样本 $X_1,\ldots,X_n$ 服从均值为 $\mu$、方差为 $\sigma^2$ 的给定分布，则有：

$$\bar X \xrightarrow[n\to+\infty]{}\mathcal N\left(\mu,\frac{\sigma}{\sqrt n}\right)$$

### 5.2  线性代数与微积分

#### 5.2.1  一般记号

- **向量** – 我们记 $x\in\mathbb R^n$ 为具有 $n$ 个分量的向量，其中 $x_i\in\mathbb R$ 是第 $i$ 个分量：

$$x=\begin{pmatrix}x_1\\x_2\\\vdots\\x_n\end{pmatrix}\in\mathbb R^n$$

- **矩阵** – 我们记 $A\in\mathbb R^{m\times n}$ 为具有 $m$ 行和 $n$ 列的矩阵，其中 $A_{i,j}\in\mathbb R$ 是位于第 $i$ 行第 $j$ 列的元素：

$$A=\begin{pmatrix}A_{1,1}&\cdots&A_{1,n}\\\vdots&&\vdots\\A_{m,1}&\cdots&A_{m,n}\end{pmatrix}\in\mathbb R^{m\times n}$$

> _注：_ 上面定义的向量 $x$ 可以看作一个 $n\times1$ 矩阵，更具体地称为列向量。

- **单位矩阵** – 单位矩阵 $I\in\mathbb R^{n\times n}$ 是一个对角线上为 1、其余位置为 0 的方阵：

$$I=\begin{pmatrix}1&0&\cdots&0\\0&\ddots&&\vdots\\\vdots&&\ddots&0\\0&\cdots&0&1\end{pmatrix}$$


线性回归问题可以使用 `ordinary least squares` (OLS，普通最小二乘法) 方法求解 [[维基](https://en.wikipedia.org/wiki/Ordinary_least_squares)]。该框架涉及响应变量 `y`、由 `p` 个特征或变量和 `m` 个观测值组成的数据集 `X`，以及存储在向量 `b` 中的 `p` 个回归系数（待定）。在矩阵表示法中，问题在于找到使 `y` 和 `Xb` 之间的距离 `||y - Xb||`![Image](images/B9780443218576000072/si49.png) 最小化的 `b`。这里 `X` 是一个 `m × p`![Image](images/B9780443218576000072/si50.png) 矩阵，而 `y`、`b`![Image](images/B9780443218576000072/si51.png) 是列向量。解为

```
b = A^(-1) X^T y, with A = X^T X.
```

![Image](images/B9780443218576000072/si52.png)

第 [3.4.2](#Chp003_49-60_B9780443218576000072.xhtml#s0075) 节讨论的技术可用于计算 `A` 的逆，方法是使用公式 [(3.4)](#Chp003_49-60_B9780443218576000072.xhtml#deq8)（其中 `n = -1`![Image](images/B9780443218576000072/si2.png)），要么精确地使用其 `characteristic polynomial`（特征多项式）的所有根，要么近似地使用模最小的 2–3 个根。在实现第 [3.4.2](#Chp003_49-60_B9780443218576000072.xhtml#s0075) 节的方法时，你需要反向使用递推公式 [(3.8)](#Chp003_49-60_B9780443218576000072.xhtml#deq29)，即用于 `n = -1, -2`![Image](images/B9780443218576000072/si53.png) 等，而不是用于 `n = 1, 2`![Image](images/B9780443218576000072/si54.png) 等。

如果 `A` 不可逆，第 [3.2.1](#Chp003_49-60_B9780443218576000072.xhtml#s0020) 节描述的方法可能会有用：这相当于使用 `A` 的伪逆。注意 `A` 是一个 `p × p`![Image](images/B9780443218576000072/si14.png) 矩阵，正如第 [3.2](#Chp003_49-60_B9780443218576000072.xhtml#s0015) 节所述。关于置信区间的问题可以使用无模型技术来解决，如第 [8](#Chp008_131-145_B9780443218576000126.xhtml) 章所述。

## 3.4 自回归时间序列的数学原理

这里我将第 [3.3.2](#Chp003_49-60_B9780443218576000072.xhtml#s0045) 节描述的自回归 `time series`（时间序列）与第 [3.2](#Chp003_49-60_B9780443218576000072.xhtml#deq6) 节的内容联系起来。对于第 [3.3.2](#Chp003_49-60_B9780443218576000072.xhtml#s0045) 节中的 AR(`p`) 过程，我们有

```
$X_{n} = g(e_{p},e_{p + 1},\ldots,e_{n}) + \sum\limits_{k = 1}^{p}r_{k}^{n}q_{k},\quad\text{with~}\begin{pmatrix} q_{1} \\ q_{2} \\ \vdots \\ q_{p} \end{pmatrix} = V^{- 1}\begin{pmatrix} X_{0} \\ X_{1} \\ \vdots \\ X_{p - 1} \end{pmatrix},$
```

![Image](images/B9780443218576000072/si55.png)

其中 `V` 与公式 [(3.4)](#Chp003_49-60_B9780443218576000072.xhtml#deq8) 中的矩阵相同，`r[k]`![Image](images/B9780443218576000072/si56.png) 是由 [(3.5)](#Chp003_49-60_B9780443218576000072.xhtml#deq17) 定义的 `characteristic polynomial`（特征多项式）的根（此处假设互不相同），`g` 是 `e[p]`、`e[p+1]`、…、`e[n]`![Image](images/B9780443218576000072/si57.png) 的线性函数。例如，如果 `p = 1`![Image](images/B9780443218576000072/si58.png)，我们有

```
$g(e_{p},e_{p + 1},\ldots,e_{n}) = \sum\limits_{k = 0}^{n - p}a_{1}^{k}e_{n - k}.$
```

![Image](images/B9780443218576000072/si59.png)

这使你能够计算 `Var[X[n]]`![Image](images/B9780443218576000072/si60.png) 和 `Cov[X[n], X[n-k]]`![Image](images/B9780443218576000072/si61.png)，条件是给定 `X[0]`、…、`X[p-1]`![Image](images/B9780443218576000072/si62.png)。当 `n` 趋向无穷大时，极限允许你计算平稳情况下该过程的无条件方差和自相关。例如，如果 `p = 1`![Image](images/B9780443218576000072/si58.png)，我们有

```
${Var}\lbrack X_{\infty}\rbrack = \lim\limits_{n\rightarrow\infty}\sum\limits_{k = 0}^{n - p}a_{1}^{2k}{Var}\lbrack e_{n - k}\rbrack = \sigma^{2}\sum\limits_{k = 0}^{\infty}a_{1}^{2k} = \frac{\sigma^{2}}{1 - a_{1}^{2}},$
```

![Image](images/B9780443218576000072/si63.png)

其中 `σ²` = `Var[e[0]]`![Image](images/B9780443218576000072/si64.png) 是白噪声 `{e[n]}`![Image](images/B9780443218576000072/si45.png) 的方差，且 `|a[1]| < 1`![Image](images/B9780443218576000072/si65.png)，因为我们假设了平稳性。对于一般情况（任意 `p`），如果 `n` 大于或等于 `p`，公式为

```
$g(e_{p},e_{p + 1},\ldots,e_{n}) = \sum\limits_{k = 0}^{n - p}\alpha_{k}e_{n - k},\text{~~}\text{with~}\alpha_{0} = 1,\text{~~}\alpha_{k} = \sum\limits_{t = 1}^{p}a_{t}\alpha_{k - t}\text{~~}\text{if~}k > 0,\text{~~}\alpha_{k} = 0\text{~~}\text{if~}k < 0.$
```

![Image](images/B9780443218576000072/si66.png)

在这种情况下，我们有

```
${Var}\lbrack X_{\infty}\rbrack = \sigma^{2}\sum\limits_{k = 0}^{\infty}\alpha_{k}^{2}.$
```

![Image](images/B9780443218576000072/si67.png)

系数 `α[k]`![Image](images/B9780443218576000072/si68.png) 的初始条件对应于 `k = 0, -1, -2, …, -(p-1)`![Image](images/B9780443218576000072/si69.png)。因此 `α[0] = 1`![Image](images/B9780443218576000072/si70.png)，其余 `α[k]`![Image](images/B9780443218576000072/si68.png)（`k < 0`）![Image](images/B9780443218576000072/si71.png) 均为零。因此，`α[n]`![Image](images/B9780443218576000072/si72.png) 的递推关系可以使用与方程 [(3.5)](#Chp003_49-60_B9780443218576000072.xhtml#deq17) 相同的根 `r[1]`、…、`r[p]`![Image](images/B9780443218576000072/si73.png) 来求解。假设根互不相同，我们有

```
$\alpha_{n} = \sum\limits_{k = 1}^{p}r_{k}^{n}q_{k}^{\prime},\quad\text{with~}\begin{pmatrix} q_{1}^{\prime} \\ q_{2}^{\prime} \\ \vdots \\ q_{p}^{\prime} \end{pmatrix} = W^{- 1}\begin{pmatrix} 1 \\ 0 \\ \vdots \\ 0 \end{pmatrix},\quad\text{and~}W = \begin{pmatrix} {1\quad} & {1\quad} & {\cdots\quad} & 1 \\ {r_{1}^{- 1}\quad} & {r_{2}^{- 1}\quad} & {\ldots\quad} & r_{p}^{- 1} \\ {\vdots \quad} & {\vdots \quad} & {\ddots \quad} & \vdots \\ {r_{1}^{- (p - 1)}\quad} & {r_{2}^{- (p - 1)}\quad} & {\ldots\quad} & r_{p}^{- (p - 1)} \end{pmatrix}.$
```

![Image](images/B9780443218576000072/si74.png)(3.6)

同样，直接计算 `W^(-1)`![Image](images/B9780443218576000072/si75.png) 在数值上是不稳定的，除非在某些特殊情况下。通常，一些 `r[k]`![Image](images/B9780443218576000072/si56.png) 是占主导地位的。其他的可以忽略，从而得到近似值并增加稳定性。最后，如果两个时间序列模型（例如 ARMA 和 AR 模型）具有相同的方差和协方差结构，它们实际上是相同的。

### 3.4.1 仿真：奇特的分形时间序列

为了模拟第 [3.3.2](#Chp003_49-60_B9780443218576000072.xhtml#s0045) 节描述的 `autoregressive`（自回归）时间序列，我采用逆向过程：首先选取 `characteristic polynomial`（特征多项式）的根 `r[1]`、…、`r[p]`![Image](images/B9780443218576000072/si73.png)，然后计算系数 `a[1]`、…、`a[p]`![Image](images/B9780443218576000072/si76.png)。这带来了有趣的发现。我希望至少有一个根的模等于 1。其他根的模必须严格小于 1。根可以有大于 1 的重数。根据根的情况，无论它们是否全为实数、是否有复数、或是否有重数大于 1 的根，模式会截然不同。它分为三类：

- 类型 1：如果模最大的根的重数大于 1，则为非常平滑的时间序列。
- 类型 2：如果所有根均为实数且互不相同，则呈现布朗运动状外观。

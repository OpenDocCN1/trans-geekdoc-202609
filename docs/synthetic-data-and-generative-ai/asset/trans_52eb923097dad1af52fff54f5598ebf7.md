

### 3.2.3 矩阵的平方根

公式 [(3.4)](#Chp003_49-60_B9780443218576000072.xhtml#deq8) 不仅适用于 `n` 的整数值，还可以扩展到分数参数，例如 `n = 1/2`![Image](images/B9780443218576000072/si28.png)。这里，我通过一个例子来说明它是如何工作的。因此，我将展示如何使用迄今为止开发的方法来计算 `square root of a matrix` [[维基百科](https://en.wikipedia.org/wiki/Square_root_of_a_matrix)]。这个问题有许多应用，特别是当矩阵 `A` 是对称 `positive semidefinite` [[维基百科](https://en.wikipedia.org/wiki/Definite_matrix)] 时：此时它只有一个对称正半定平方根，记为 `A^(1/2)`![Image](images/B9780443218576000072/si29.png)。例如，请参阅关于线性回归和合成数据的第 [7](#Chp007_113-129_B9780443218576000114.xhtml) 章，特别是题为“相关结构”的第 [7.2.1](#Chp007_113-129_B9780443218576000114.xhtml) 节。需要平方根来生成具有预指定相关矩阵的合成数据。

现在，使用带有 `n = 1/2`![Image](images/B9780443218576000072/si28.png) 的公式 [(3.4)](#Chp003_49-60_B9780443218576000072.xhtml#deq8)，让我们计算定义如下的 `2×2`![Image](images/B9780443218576000072/si1.png) 矩阵 `A` 的平方根

```
A = \left( \begin{array}{rr} {3\quad} & 1 \\ {1\quad} & 1 \\ \end{array} \right).
```

![Image](images/B9780443218576000072/si30.png)

根据公式 [(3.1)](#Chp003_49-60_B9780443218576000072.xhtml#deq4)，其 `characteristic polynomial` 是 `x² - 4x + 2`![Image](images/B9780443218576000072/si31.png)。根分别为 `r_1 = 1 + \sqrt{2}`![Image](images/B9780443218576000072/si32.png) 和 `r_2 = 1 - \sqrt{2}`![Image](images/B9780443218576000072/si33.png)，两者均为实数且为正。根据公式 [(3.2)](#Chp003_49-60_B9780443218576000072.xhtml#deq6)，矩阵 `Q[1]`、`Q[2]`![Image](images/B9780443218576000072/si34.png) 分别等于

```
Q_1 = \frac{A - r_2 I}{r_1 - r_2} = \frac{1}{4} \cdot \begin{pmatrix} {2 + \sqrt{2}\quad} & \sqrt{2} \\ {\sqrt{2}\quad} & {2 - \sqrt{2}} \\ \end{pmatrix},\quad Q_2 = \frac{A - r_1 I}{r_2 - r_1} = \frac{1}{4} \cdot \begin{pmatrix} {2 - \sqrt{2}\quad} & {- \sqrt{2}} \\ {- \sqrt{2}\quad} & {2 + \sqrt{2}} \\ \end{pmatrix}.
```

![Image](images/B9780443218576000072/si35.png)

矩阵 `A` 有一个正定平方根，即

```
A^{1/2} = \sqrt{r_1} \cdot Q_1 + \sqrt{r_2} \cdot Q_2 = \frac{1}{2}\begin{pmatrix} {\sqrt{10 + \sqrt{2}}\quad} & \sqrt{2 - \sqrt{2}} \\ {\sqrt{2 - \sqrt{2}}\quad} & \sqrt{2 + \sqrt{2}} \\ \end{pmatrix}.
```

![Image](images/B9780443218576000072/si36.png)

很容易证明 `A^(1/2) ⋅ A^(1/2) = A`![Image](images/B9780443218576000072/si37.png)。在高维情况下，范德蒙德系统 [(3.4)](#Chp003_49-60_B9780443218576000072.xhtml#deq8) 使用第 [3.4.2](#Chp003_49-60_B9780443218576000072.xhtml#s0075) 节中描述的方法求解。

## 3.3 在机器学习问题中的应用

我在第 [3.2](#Chp003_49-60_B9780443218576000072.xhtml#s0015) 节中讨论了主成分分析（PCA）、通过 PCA 进行数据压缩以及伪逆矩阵。这里我重点关注时间序列、马尔可夫链和线性回归的应用。

### 3.3.1 马尔可夫链

`Markov chain` [[维基百科](https://en.wikipedia.org/wiki/Markov_chain)] 是时间序列或随机过程的一种特定类型。在迭代或时间 `n` 时，系统以概率 `P[n](i)`![Image](images/B9780443218576000072/si38.png) 处于特定状态 `i`。从时间 `n` 的状态 `i` 移动到时间 `n + 1`![Image](images/B9780443218576000072/si39.png) 的状态 `j` 的概率称为转移概率，记为 `p[i*j]`![Image](images/B9780443218576000072/si40.png)。它不依赖于 `n`，而仅依赖于 `i` 和 `j`。马尔可夫链由其初始条件 `P[0](i)`、`1 ≤ i ≤ p`![Image](images/B9780443218576000072/si41.png) 和转移概率矩阵 `A`（包含元素 `p[i*j]`![Image](images/B9780443218576000072/si40.png)）决定。转移矩阵的大小为 `p × p`![Image](images/B9780443218576000072/si14.png)，其中 `p` 是系统中潜在状态的数量。因此 `1 ≤ i, j ≤ p`![Image](images/B9780443218576000072/si42.png)。当 `n` 趋于无穷大时，`A^(n)`![Image](images/B9780443218576000072/si13.png) 和整个系统达到平衡分布。这是因为

*   与 `A` 相关的 `characteristic polynomial` 有一个等于 1 的根。
*   任何根的绝对值都小于或等于 1。

### 3.3.2 时间序列：自回归过程

自回归过程（AR）[[维基百科](https://en.wikipedia.org/wiki/Autoregressive_model)] 代表了时间序列的另一种基本类型。与马尔可夫链不同，潜在状态的数量是无限的，状态可以是任何实值，而不仅仅是整数。但时间仍然是离散的。时间连续的 AR 过程（如 `Gaussian processes` [[维基百科](https://en.wikipedia.org/wiki/Gaussian_process)]）不在本讨论范围内。`AR(p)` 过程定义如下：

```
X[n] = a[1]X[n-1] + ⋯ + a[p]X[n-p] + e[n].
```

![Image](images/B9780443218576000072/si43.png)

其 `characteristic polynomial` 为

```
x^(p) = a[1]x^(p-1) + a[2]x^(p-2) + ⋯ + a[p-1]x + a[p].
```

![Image](images/B9780443218576000072/si44.png)(3.5)

这里 `{e[n]}`![Image](images/B9780443218576000072/si45.png) 是一个 `white noise` 过程（通常是具有相同方差的不相关高斯变量）[[维基百科](https://en.wikipedia.org/wiki/White_noise)]。我们假设所有期望均为零。这里我们处理的是一个非齐次线性（随机）递推关系。最有趣的情况是特征多项式的所有根的绝对值都小于 1。满足此条件的过程称为 `stationary`。在这种情况下，`autocorrelations` 会呈指数级快速衰减。

滞后-`k` 协方差满足以下关系

```
\gamma_k = Cov[X_n, X_{n-k}] = \begin{cases} a_1\gamma(k-1) + \cdots + a_p\gamma(k-p) & \text{if } k \neq 0, \\ a_1\gamma(k-1) + \cdots + a_p\gamma(k-p) + \sigma^2 & \text{if } k = 0, \end{cases}
```

![Image](images/B9780443218576000072/si46.png)

其中

```
\sigma^2 = Var[e[n]],\quad Var[X[n]] = \gamma(0),\quad \rho(k) = Corr[X[n], X[n-k]] = \gamma(k)/\gamma(0).
```

![Image](images/B9780443218576000072/si47.png)

因此，自相关可以显式计算，并且也与特征多项式相关。这一事实可用于模型拟合，因为自相关结构唯一地表征了（平稳）时间序列。注意，如果白噪声是高斯分布的，那么 `X[n]`![Image](images/B9780443218576000072/si48.png) 也是高斯分布的。

关于自相关结构的更多内容，可以在 Marc-Andreas Muendler 的讲义 [[7]](#Chp003_49-60_B9780443218576000072.xhtml#br0035) 中找到，他在 UCSD 教授经济学。他的材料与我在这里讨论的非常相似，但更全面。另请参阅 Barbara Bogacka 关于时间序列的讲义 [[1]](#Chp003_49-60_B9780443218576000072.xhtml#br0005)，特别是第 6 章。最后，本章的第 [3.4](#Chp003_49-60_B9780443218576000072.xhtml#s0055) 节更详细地探讨了数学方面。

### 3.3.3 线性回归


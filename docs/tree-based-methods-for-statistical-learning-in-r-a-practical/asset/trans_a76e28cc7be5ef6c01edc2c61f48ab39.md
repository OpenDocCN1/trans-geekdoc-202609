

### 3.3.1 示例：X 和 Y 均为单变量连续变量

最简单的情况发生在 **X** 和 **Y** 均为单变量连续变量时；在单变量情况下，我们省略粗体表示法，只写 _X_ 和 _Y_。在此情况下，_p_ = _q_ = 1 且 \( T = \sum_{i=1}^N g(X_i) h(Y_i) \)。若将 _g_() 和 _h_() 取为恒等函数（例如，_g_(_X<sub>i</sub>_) = _X<sub>i</sub>_），则

```
T = \sum_{i=1}^N X_i Y_i,
\mu = \left( \sum_{i=1}^N X_i \right) \bar{Y},
\sigma^2 = S_Y^2 \sum_{i=1}^N X_i^2 - S_Y^2 \left( \sum_{i=1}^N X_i \right)^2 / N,
```

其中 \(\bar{Y} = \sum_{i=1}^N Y_i / N\) 和 \(S_Y^2 = \sum_{i=1}^N (Y_i - \bar{Y})^2 / (N - 1)\) 分别为 _Y_ 的样本均值和方差。由于 _T_ 是单变量的，标准化检验统计量（3.3）为 \(c_m = \left| (T - \mu) / \sqrt{\Sigma} \right|\) 和 \(c_q = c_m^2\)；因此，在此情况下无论使用哪种检验统计量都无关紧要，因为结果将相同。

让我们重新审视纽约空气质量数据集（第 1.4.2 节）以演示在 R 中所需的计算。令 _X_ = `Temp` 和 _Y_ = `Ozone` 为感兴趣的变量。为在 \(\alpha = 0.05\) 水平下检验 _X_ 和 _Y_ 之间总体独立性的原假设，我将使用二次检验统计量（_c<sub>q</sub>_），并利用渐近 \(\chi^2 (1)\) 近似计算检验的 _p_-值。我还将选择 _g_() 和 _h_() 作为恒等函数。第一行删除任何带有缺失响应值的行，我将在后续使用。

```
aq <- airquality[!is.na(airquality$Ozone), ]
N <- nrow(aq) # sample size
gX <- aq$Temp # g(X)
gY <- aq$Ozone # h(Y)
Tstat <- sum(gX * gY) # linear statistic
mu <- sum(gX) * mean(gY)
Sigma <- var(gY) * sum(gX ^ 2) - var(gY) * sum(gX) ^ 2 / N

# Quadratic test statistic (1.3)
(cq <- ((Tstat - mu) / sqrt(Sigma)) ^ 2)
#> [1] 56.1

1 - pchisq(cq, df = 1) # p-value
#> [1] 6.94e-14
```

在此，我们将在 \(\alpha = 0.05\) 水平下拒绝原假设（\(p < 0.001\)），并得出结论：Temp 和 Ozone 之间存在一定程度的关联。

为进行比较，我们可以使用 **coin** 包中的 `independence_test()` 函数，该函数提供了 Hothorn et al. [2006b] 中描述的条件推断程序的灵活实现；详情见 `?coin::independence_test`。以下代码片段演示了此过程：

```
library(coin)
independence_test(Ozone ~ Temp, data = aq, teststat = "quadratic")
#>
#>
#> Asymptotic General Independence Test
#>
#>
#> data:  Ozone by Temp
#> chi-squared = 56, df = 1, p-value = 7e-14
```

幸运的是，我们得到了完全相同的结果。请注意，\(c_m\) 和 \(c_q\) 仅在线性统计量（3.1）为多变量时才会不同。

### 3.3.2 示例：X 和 Y 均为名义类别变量

当 \(X\) 和 \(Y\) 均为类别变量时，\(T\) 本质上是 \(X\) 和 \(Y\) 之间的向量化（即展平）列联表；在本节中，我将继续省略粗体表示法。假设 \(X\) 和 \(Y\) 分别具有 \(q\) 和 \(p\) 个唯一类别。\(X\) 和 \(Y\) 之间的列联表只不过是一个 \(q \times p\) 表格，包含来自 \(X\) 和 \(Y\) 的每个 \(qp\) 类别对的观测频数。\(^\text{b}\) 回顾公式（3.1）-（3.2）中矩阵向量化算子 \(\text{vec}()\) 的出现。\(\text{vec}()\) 算子将一个 \(m \times n\) 矩阵转换为一个 \(mn \times 1\) 列向量。因此，向量化的 \(q \times p\) 列联表只是一个 \(qp \times 1\) 列向量，包含各个频数，其中向量化是按列进行的。例如，如果 \(A = \left( \begin{array}{cc} a & b \\ c & d \end{array} \right)\) 是一个 \(2 \times 2\) 矩阵（或列联表），则 \(\text{vec}(A) = (a, c, b, d)^\top\)，其中 \(\top\) 表示转置算子。

让我们回到蘑菇可食性示例（第 1.4.4 节）。令 \(X = \text{odor}\) 和 \(Y = \text{Edibility}\)；两者均为名义类别变量，分别具有九个和两个类别。下面使用 `xtabs()` 函数给出了对每个变量进行交叉分类的列联表（详情见 `?stats::xtabs`）。向量化列联表也通过调用 `as.vector()` 构建：

```
mushroom <- treemisc::mushroom
(ctab <- xtabs(~ odor + Edibility, data = mushroom))
```

b 此处假设 X 的 q 个类别定义了列联表的行，但通常这并不重要。

| 气味 | 可食 | 有毒 |
|------|--------|--------|
| 杏仁 | 400 | 0 |
| 茴香 | 400 | 0 |
| 木油腥 | 0 | 192 |
| 鱼腥 | 0 | 576 |
| 臭 | 0 | 2160 |
| 霉味 | 0 | 36 |
| 无 | 3408 | 120 |
| 刺鼻 | 0 | 256 |
| 辛辣 | 0 | 576 |

```
(Tstat <- as.vector(ctab)) # multivariate linear statistic
#> [1] 400 400 0 0 0 0 3408 0 0 0
#> [11] 0 192 576 2160 36 120 256 576
```

通常，当 \(X\) 和 \(Y\) 为类别变量时，转换函数 \(g()\) 和影响函数 \(h()\) 将每个类别映射为一组虚拟编码值的向量。例如，使用上述列联表（`ctab`）中的类别顺序，

\(g(X_i) = (0, 0, 0, 0, 1, 0, 0, 0, 0, 0)^\top\)

和

\(h(Y_i) = (0, 1)^\top\)

将表示一种气味难闻、有毒的蘑菇。本质上，\(g(X) = \mathbf{X}\) 和 \(h(Y) = \mathbf{Y}\) 分别是 \(X\) 和 \(Y\) 的相关独热编码模型矩阵。

在 \(X\) 和/或 \(Y\) 为二元变量的特殊情况下，只要它们编码为 0/1，恒等变换将导致相同的结果。例如，如果 \(X\) 和 \(Y\) 都是二元 0/1 编码变量，那么当 \(g()\) 和 \(h()\) 均为恒等函数时，第 3.3.1 节的公式将导致相同的结果。

克罗内克积（记为 \(\otimes\)）也出现在（3.2）中。两个矩阵之间的克罗内克积可以在 R 中使用 `kronecker()` 函数或 `%x%` 算子计算。摩尔-彭罗伪逆（在（3.2）中记为 \(\Sigma^+\)）可以使用推荐 **MASS** 包 [Ripley, 2022] 中的 `ginv()` 函数计算。

在下一个代码块中，我们使用（3.2）计算条件期望和方差。请注意，如果直接使用独热编码矩阵 \(g(X) = \mathbf{X}\) 和 \(h(Y) = \mathbf{Y}\)，公式将大大简化；在 R 中，可以使用 model.matrix() 函数获得这些矩阵。例如，（3.2）中的克罗内克积 \(\sum_{i=1}^N g(X_i) \otimes g(X_i)^\top\) 简化为 \(X^\top X\)——在此情况下，这是一个 \(p \times p\) 对角矩阵，其第 \(j\) 个对角元等于 \(X\) 的第 \(j\) 个类别的频数（或 \(X\) 的第 \(j\) 列的总和）。此外，（3.2）中的 \(\sum_{i=1}^N g(X_i)\) 只是一个 \(p \times 1\) 列向量，其第 \(j\) 个元素等于 \(X\) 的第 \(j\) 个类别的频数。请注意，我们使用 R 内置的 qr() 函数计算 \(\Sigma\) 的秩，该秩用于 \(c_q\) 的渐近卡方分布的自由度；在此示例中，\(df = \text{rank}(\Sigma) = 8\)。（由于舍入，打印输出显示 p 值为零。）

```
gX <- model.matrix(~ odor - 1, data = mushroom) # g(X)
hY <- model.matrix(~ Edibility - 1, data = mushroom) # h(Y)
mu <- as.vector(colSums(gX) %*% t(colMeans(hY)))
Sigma <- var(hY) %x% (t(gX) %*% gX) %*% t(colSums(gX)) / nrow(hY)
```

```
# Quadratic test statistic (1.3)
(cq <- t(Tstat - mu) %*% MASS::ginv(Sigma) %*% (Tstat - mu))
#> [,1]
#> [1,] 7659
1 - pchisq(cq, df = qr(Sigma)$rank) # p-value
#> [,1]
#> [1,] 0
```

同样，我们可以将结果与 coin 的 independence_test() 函数的输出进行比较。再次，结果是等价的。

```
independence_test(Edibility ~ odor, data = mushroom,
teststat = "quadratic")
```

```
#>
#>
#> Asymptotic General Independence Test
#>
#>
#> data: Edibility by odor (almond, anise, creosote, fishy, foul, musty, none, pungent...
#> chi-squared = 7659, df = 8, p-value <2e-16
```

### 3.3.3 应使用哪种检验统计量？

在之前的示例中，我们使用了（3.3）中检验统计量的二次形式及其渐近卡方分布，但关于最大值的


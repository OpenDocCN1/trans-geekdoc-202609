

```r
pnorm(0)
#> [1] 0.5
pnorm(5, mean = 5, sd = 1)
#> [1] 0.5
```

由于二项分布是离散的，它只能取 0 到 size 之间的整数值。这意味着，例如，`pbinom()` 函数对 3、3.5、3.6 一直到（但不包括）4 返回相同的值。这是因为 \(P(X \le 3) = P(X \le 3.2) = P(X \le 3.5) = P(X \le 3.6)\) 等等。请注意，这里我们传入了一组 x 值。

```r
pbinom(c(3, 3.5, 3.6, 4), size = 10, p = 0.5)
#> [1] 0.172 0.172 0.172 0.377
```

我们还可以通过向累积分布函数传递 size 和/或 p 的向量来改变分布的参数。在后续代码块中，我们计算了在 12 次试验且概率为 0.25 以及 10 次试验且概率为 0.5 时，\(X \le 3\) 的概率和 \(X \le 4\) 的概率。

```r
pbinom(c(3, 3, 4, 4), size = c(12, 10, 12, 10),
       p=c(0.25, 0.5, 0.25, 0.5))
#> [1] 0.649 0.172 0.842 0.377
```

### 10.1.4 分位数分布

最后，我们有分位数分布函数，它是累积分布函数的逆函数。该函数接收一个概率 x、一个均值和一个标准差 sd，并返回使累积分布函数等于 x 的值。因此，当 x 等于 0.5 时，`qnorm()` 函数返回分布的中位数，对于正态分布来说，中位数等于均值。

```r
qnorm(0.5)
#> [1] 0
qnorm(0.5, mean = 5, sd = 1)
#> [1] 5
```

对于离散二项分布，`qbinom()` 函数返回最大整数值，使得小于或等于该值的概率最多为输入值 x。

```r
qbinom(c(0.2, 0.3), size = 10, p = 0.5)
#> [1] 2 3
```

### 10.1.5 概率分布参考列表

在之前的示例中，我们只使用了正态分布和二项分布。以下列表包含 R 中可用的其他概率分布。对于每个分布，我们给出了 r[dist]() 函数的参数。其他三个函数的格式类似。除非另有说明，参数 n 是观测值的数量。

- **β分布**: `rbeta(n, shape1, shape2, ncp = 0)` 具有形状参数 `shape1` 和 `shape2`（以及可选的非中心性参数 `ncp`）。
- **二项分布**: `rbinom(n, size, prob)` 具有成功概率 `prob` 和试验次数 `size`。
- **柯西分布**: `rcauchy(n, location = 0, scale = 1)` 具有位置参数 `location` 和尺度参数 `scale`。
- **卡方分布**: `rchisq(n, df, ncp = 0)` 具有 `df` 个自由度和可选的非中心性参数 `ncp`。
- **指数分布**: `rexp(n, rate = 1)` 具有速率 `rate`（即，均值 = 1/rate）。
- **F分布**: `rf(n, df1, df2, ncp)` 具有 `df1` 和 `df2` 个自由度（以及可选的非中心性参数 `ncp`）。
- **伽马分布**: `rgamma(n, shape, rate = 1, scale = 1/rate)` 具有参数 `shape` 和 `scale`（或者也可以由 `rate` 指定）。
- **几何分布**: `rgeom(n, prob)` 具有概率参数 `prob`。
- **超几何分布**: `rhyper(nn, m, n, k)` 具有 `m` 个白球、`n` 个黑球和选取 `k` 个球。
- **逻辑分布**: `rlogis(n, location = 0, scale = 1)` 具有参数 `location` 和 `scale`。
- **对数正态分布**: `rlnorm(n, meanlog = 0, sdlog = 1)` 具有对数尺度上的均值 `meanlog` 和标准差 `sdlog`。
- **负二项分布**: `rnbinom(n, size, prob, mu)` 具有参数 `size` 和 `prob`。
- **正态分布**: `rnorm(n, mean = 0, sd = 1)` 具有均值等于 `mean` 和标准差等于 `sd`。
- **泊松分布**: `rpois(n, lambda)` 具有参数 `lambda`。
- **Student t分布**: `rt(n, df, ncp)` 具有 `df` 个自由度（以及可选的非中心性参数 `ncp`）。
- **均匀分布**: `runif(n, min = 0, max = 1)` 具有最小值 `min` 和最大值 `max`。
- **韦布尔分布**: `rweibull(n, shape, scale = 1)` 具有参数 `shape` 和 `scale`。
- **Wilcoxon秩和分布**: `rwilcox(nn, m, n)` 具有 `nn` 个观测值和样本大小 `m` 和 `n`。
- **Wilcoxon符号秩分布:** `rsignrank(nn, n)` 具有 `nn` 个观测值和样本大小 `n`。

### 10.1.6 练习题

将随机种子设置为 123，然后生成 5 个服从最小值为 1 且最大值为 5 的均匀分布的随机数。然后，找出该分布的 0.15 分位数（它应该等于 1.6）。

```r
# Insert your solution here:
```

## 10.2 经验分布和抽样数据

在本章开头，我们使用了 `sample()` 函数。该函数也可用于从经验分布中抽样。`sample(x, size, replace=FALSE, prob=NULL)` 函数接收我们想要从 x 中抽样的值、我们想要抽样的观测数量 size，以及是否有放回抽样 replace。如果我们不希望每个值被选中的概率相等，也可以设置一个概率向量 prob，其长度必须与 x 相同。在以下代码中，我们从 NHANESsample 数据中无放回抽取 500 行。为此，我们从索引 1 到数据行数中选择 500 个值。然后，我们使用这些索引选择数据的行。

```r
nhanes_sample_ids <- sample(1:nrow(NHANESsample), 500, replace = FALSE)
nhanes_sample <- NHANESsample[nhanes_sample_ids, ]
dim(nhanes_sample)
#> [1] 500 21
```

我们现在演示有放回抽样。这样做，我们创建了一个从数据的经验分布中抽样的新数据集，称为*自助样本*。

```r
nhanes_sample_ids <- sample(1:nrow(NHANESsample), nrow(NHANESsample), replace = TRUE)
nhanes_sample <- NHANESsample[nhanes_sample_ids, ]
dim(nhanes_sample)
#> [1] 31265 21
```

从数据框中抽样的另一种方法是使用 **tidyverse** 中的 `slice_sample()` 函数。在此函数中，我们可以指定要抽样的观测数量 `n` 或要抽样的观测比例 `prop`。此外，我们可以通过设置参数 `replace` 的值（默认值为 `FALSE`）来进行有放回或无放回抽样。我们使用此函数无放回地随机抽取 20% 的观测值。

```r
nhanes_sample <- NHANESsample %>%
  slice_sample(prop = 0.2, replace = FALSE)
dim(nhanes_sample)
#> [1] 6253   21
```

### 10.2.1 练习题

将随机种子设置为 5，然后从 1 到 100 的整数集合中有放回地抽取 50 个观测值。计算这些观测值的平均值；它应该是 56.7。

```r
# Insert your solution here:
```

除了抽样，我们还可以找到经验累积分布。也就是说，我们可以使用给定的向量来推断一个分布。在以下情况中，我们从正态分布 `vec` 中抽取一个随机样本，然后使用 `ecdf()` 函数找到其经验累积分布。该函数实际上返回一个函数，然后可以使用它来查找不同值的样本累积分布，类似于 `p[dist]()` 函数。在我们的示例中，我们找到样本概率 $X \leq 0$。

```r
vec <- rnorm(100)
ecdf_vec <- ecdf(vec)
ecdf_vec(0)
#> [1] 0.63
```

我们现在使用 `pnorm()` 函数将此经验分布与实际 cdf 进行绘图。请注意，为此，我们创建一系列可能的 `x` 值传递给 `pnorm()` 和 `ecdf_vec()`。

```r
df <- data.frame(x = seq(-3, 3, 0.05))
df$ecdf <- ecdf_vec(df$x)
df$distn = pnorm(df$x)
```

```r
ggplot(df) +
  geom_line(aes(x = x, y = ecdf), color = "black") +
  geom_line(aes(x = x, y = distr), color = "red")
```

![](img/58a554e865d49ca347d9a3f76f8f0812_183_0.png)

在实践中，经验累积分布可能涉及来自给定数据集的数据，您希望使用这些数据来表示总体的分布。例如，在以下代码中，我们从 NHANESsample 数据框中找到血铅水平的经验分布。血铅水平在 5 μg/dL 或以上被视为升高。我们可以看到 96.4% 的观测值的血铅水平低于此阈值。

```r
ecdf_lead <- ecdf(nhanes_sample$LEAD)
ecdf_lead(5)
#> [1] 0.964
```

## 10.3 练习

- 1. 假设女性身高的分布近似为均值为 64 英寸、标准差为 2.2 英寸的正态分布。使用此分布，回答以下问题。




```
\widehat{Ozone} = \begin{cases} 26.544 & \text{if Temp} < 82.5 \\ 75.405 & \text{if Temp} >= 82.5 \end{cases}.
```

估计的回归曲面在图 2.7 的右侧绘制。请注意，回归树的估计预测曲面本质上是一个阶梯函数，这使得决策树难以捕捉任意平滑或线性的响应曲面。

![](img/2c227bfb3620dc3d159fa5e6598afa30_76_0.png)

图 2.7: 根据温度预测臭氧浓度的决策树桩。左侧：树图。右侧：估计的回归函数；在分割点 c = 82.5 处绘制了一条垂直虚线（左侧的树图已四舍五入到最近的整数）。

要手动找到第一个分区并重建图 2.7 中的树，我们将先创建一个简单的函数来计算节点内 SSE。请注意，这些数据包含一些缺失值（即 R 中的 NA），因此我设置 na.rm = TRUE 以在计算结果前将其删除。

```r
sse <- function(y, na.rm = TRUE) {
  sum((y - mean(y, na.rm = na.rm)) ^ 2, na.rm = na.rm)
}
```

接下来，我将修改第 2.2.2 节中的 splits() 函数，使其适用于回归情况：

CART 在处理预测变量中的缺失值方面其实相当巧妙，但这部分内容将在第 2.7 节中详细介绍。

```r
splits.sse <- function(node, x, y) {
  xvals <- sort(unique(node[[x]])) # sorted, unique values
  xvals <- xvals[-length(xvals)] + diff(xvals) / 2 # midpoints
  res <- matrix(nrow = length(xvals), ncol = 2)
  colnames(res) <- c("cutpoint", "gain")
  for (i in seq_along(xvals)) { # loop through each feature
    left <- node[node[[x]] <= xvals[i], y, drop = TRUE] # left
    right <- node[node[[x]] > xvals[i], y, drop = TRUE] # right
    gain <- sse(node[[y]]) - sse(left) - sse(right) # Equation (2.6)
    res[i, ] <- c(xvals[i], gain) # store cutpoint and associated gain
  }
  res # return matrix of results
}
```

在将此函数应用于空气质量数据之前，我将删除包含缺失响应值的 37 行数据。Temp 的可能分割点及其相关增益如图 2.8 所示。（为了使图表上的 y 轴更美观，增益值已除以 1,000。）

```r
# Find optimal split for 'Temp'
aq <- airquality[!is.na(airquality$Ozone), ]
res <- splits.sse(aq, x = "Temp", y = "Ozone")
res[which.max(res[, "gain"]), ]
```

| 切分点 | 增益 |
|---|---|
| 82.5 | 60158.5 |

```r
# Plot results
res[, "gain"] <- res[, "gain"] / 1000 # rescale for plotting
plot(res, type = "b", col = 2, las = 1,
     xlab = "Temperature split value (degrees Fahrenheit)",
     ylab = "Gain/1000")
abline(v = 82.5, lty = 2, col = 2)
```

为了证明温度是根节点的最佳主要分割变量，我们可以使用 `sapply()` 来找出所有五个特征的最佳切分点：

```r
features <- c("Solar.R", "Wind", "Temp", "Month", "Day")
sapply(features, FUN = function(xname) {
  res <- splits.sse(aq, x = xname, y = "Ozone")
  res[which.max(res[, "gain"]), ]
})
```

| | Solar.R | Wind | Temp | Month | Day |
|---|---|---|---|---|---|
| 切分点 | 153 | 6.6 | 82.5 | 6.5 | 24.5 |
| 增益 | 29721 | 50591.2 | 60158.5 | 14511.3 | 10282.8 |

显然，增益最大的分割是 Temp，其次是 Wind、Solar.R、Month 和 Day。

单预测变量的回归树会产生一个阶梯函数，如图 2.7 右侧所示。同样的思想也可扩展到更高维度。

![](img/2c227bfb3620dc3d159fa5e6598afa30_78_0.png)

图 2.8: 作为增益函数的温度潜在分割点。最大增益出现在温度为 82.5 °F 处（垂直虚线）。

例如，假设我们接下来考虑对 Wind 进行分割。使用之前描述的相同程序，我们会发现下一个最佳分区出现在左子节点中，使用 Wind 且切分点为 7.15（mph）。相应的树图显示在图 2.9 的左侧。如果在此处停止分割，结果是一个具有两个特征的回归树。相应的预测函数显示在图 2.9 的右侧，它是一个在每个终端节点上保持不变的曲面。

## 2.4 分类拆分

到目前为止，我们只考虑过有序预测变量的分割，其形式为 x < c 与 x ≥ c，其中 c 属于 x 的定义域。但涉及名义类别特征的分割又该如何处理呢？如果 x 是有序的（即有序类别，例如 low < medium < high），则可以将其有序类别映射为整数 1, 2, ..., J，其中 J 是唯一类别的数量，并像 x 原本是数值一样进行分割。如果 x 是名义的（即类别的顺序没有意义），那么我们必须考虑将 x 分割为两个互不相交的组的所有可能方式。例如，如果 x 取自类别 {a,b,c}，则可以形成总共三种分割：

- $x \in \{a\}$ 与 $x \in \{b,c\}$；
- $x \in \{b\}$ 与 $x \in \{a,c\}$；
- $x \in \{c\}$ 与 $x \in \{a,b\}$。

对于具有 J 个类别的名义预测变量，可以通过首先按 x 的各个类别的平均响应值（例如，二元结果情况中的成功比例）对其进行排序，然后使用这个新的有序变量来寻找最佳分割，从而找到某个节点 A 上名义预测变量 x 的最佳分割。$^\mathsection$ 这将可能的分割总数从 $2^{J-1} - 1$ 减少到 $J - 1$，大幅减少了必须搜索的分割总数。使用之前讨论的基尼指数、交叉熵或 SSE 分割规则时，这也仍然会得到最佳分割。Ripley [1996, p. 218] 提供了基尼和熵度量的证明，Chou [1991] 提供了更一般杂质度量族的证明。对于多类问题（即 $J > 2$），不存在这样的计算捷径，尽管 Sleumer [1969] 和 Loh and Vanichsetakul [1988] 提出了高效的搜索方法。

### 2.4.1 示例：蘑菇可食性

为了说明，让我们回到蘑菇可食性示例，该示例包含所有类别特征和一个二元响应。该数据的简单分类树图如图 2.10 所示。该树包含对特征 `odor` 和 `spore.print.color` 的两个分割。由于响应（`Edibility`）是二元的，我们可以使用捷径方法来构建树，采用与有序分割相同的过程，只要应用基尼或熵分割准则；在这里，我将使用基尼指数，因为它已内置在我们之前定义的 `find_best_split()` 函数中。

![](img/2c227bfb3620dc3d159fa5e6598afa30_80_0.png)

图 2.10: 确定蘑菇可食性的示例分类树。

对于每个蘑菇属性，各个类别需要映射到各自中的成功比例。在本示例中，我将结果类别 Poison 视为成功，并将目标重新编码为 0/1（分别对应 Edible/Poison）。我还将删除 `veil.type` 特征，因为它只取一个值（即方差为零），对分割没有任何贡献：

```r
m <- treemisc::mushroom # load mushroom data
m$veil.type <- NULL # remove useless feature
m$Edibility <- ifelse(m$Edibility == "Poison", 1, 0)
m2 <- m # make a copy of the original data
```

为了说明主要思想，让我们看看 `veil.color` 预测变量的频数表，它有四个唯一类别：

```r
table(m2$veil.color)
```

| | brown | orange | white | yellow |
|---|---|---|---|---|
| 计数 | 96 | 96 | 7924 | 8 |

我们需要找出每个类别内的平均响应——在此例中，即有毒蘑菇的比例——然后将这些值映射回原始特征值。例如，我们将 `veil.color` 中所有值为 "white" 的项重新编码为 0.493，因为约 3908/7924 ≈ 0.493 的 `veil.color` = "white" 的蘑菇是有毒的。这可以用多种方式完成，在这里我将编写一个名为 `ordinalize()` 的简单函数，它返回一个包含两个组件的列表：`map`，包含每个类别被映射到的数值；`encoded`，包含重新编码后的特征值。

```r
ordinalize <- function(x, y) { # convert nominal to ordered
  map <- tapply(y, INDEX = x, FUN = mean)
  list("mapping" = map, "encoded" = map[x])
}
```

接下来，我将检查 `veil.color` 被映射到哪些数值：

```r
ordinalize(m2$veil.color, m2$Edibility)$map
```

| | brown | orange | white | yellow |
|---|---|---|---|---|
| 映射值 | 0.000 | 0.000 | 0.493 | 1.000 |

接下来，我将编写一个简单的 `for` 循环，使用 `ordinalize()` 对 `m2` 数据框中的每个特征列进行数值重新编码：

```r
xnames <- setdiff(names(m2), "Edibility")
for (xname in xnames) { # mean/target encode each feature
  m2[[xname]] <- ordinalize(m2[[xname]], y = m2[["Edibility"]])$encoded
}
```

让我们来看看重新编码后的数据：

```r
m2[1L:8L, 1L:5L]
```

| | Edibility | cap.shape | cap.surface | cap.color | bruises |
|---|---|---|---|---|---|
| 1 | 1 | 0.467 | 0.552 | 0.447 | 0.185 |


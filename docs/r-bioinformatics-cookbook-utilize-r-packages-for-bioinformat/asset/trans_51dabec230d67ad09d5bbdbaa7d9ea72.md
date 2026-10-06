

# 如何操作...

我们可以通过以下步骤来观察分布的变化：

- 1. 绘制重叠的分布：

```r
library(ggplot2)
library(ggridges)
library(palmerpenguins)

gplot(data = penguins) +
  aes(x = bill_length_mm, y = species,
      fill = species,
      color = species) +
  geom_density_ridges(scale = 2,
      position = "raincloud",
      alpha = 0.5,
      jittered_points = TRUE
  ) +
theme_ridges()
```

- 2. 使用渐变色填充峰值：

```r
gplot(data = penguins) +
  aes(x = bill_length_mm, y = species),
      fill = stat(x)
) +
geom_density_ridges_gradient(scale = 2,
      rel_min_height = 0.01,
) +
theme_ridges()
```

- 3. 添加分位数标记：

```r
gplot(data = penguins) +
  aes(x = bill_length_mm, y = species),
      fill = factor(stat(quantile))
) +
stat_density_ridges(
  geom = "density_ridges_gradient",
  calc_ecdf = TRUE,
  quantiles = c(0.05, 0.95)
) +
scale_fill_manual(
  name = "概率",
  values = alpha(c("goldenrod", "gray",
"steelblue"), 0.05,
  labels = c("< 0.05", "0.05 to 0.95", " > 0.95 ")
) +
theme_ridges()
```

这些就是漂亮展示分布差异所需的所有内容。

# 工作原理...

在步骤 1 中，我们创建了一个基础的山脊图（ridge plot）。它是作为 ggplot2 的额外 geom 构建的，因此我们构建了一个标准的 ggplot 图表描述，并将该 geom 添加到其中。企鹅图被设定为每个物种对应喙长度的分布，并使用 `geom_density_ridges` geom 来绘制脊线图。`position` 和 `jittered_points` 参数为曲线下方实际点的散点可视化增加了额外效果。`scale` 参数影响重叠的程度。见图 3.4：

![](img/dd0d7d9aaacf496c4d1d0e31d83783b3_76_0.png)

图 3.4 – 简单的脊线图

在步骤 2 中，我们创建了一个类似的图表，其颜色与喙长度成比例并呈现渐变色。请注意，这次由于填充颜色必须经过计算，我们必须使用 `stat()` 作为填充值，并使用特定的 `geom_density_ridges_gradient()` 函数来处理。见图 3.5：

# 使用 ggridges 比较分布的变化

![](img/dd0d7d9aaacf496c4d1d0e31d83783b3_77_0.png)

最后，在步骤 3 中，我们查看了在曲线中添加分位数区间（图 3.6）。这要求我们将 `fill` 参数描述为分位数统计的 `factor()` 函数，该统计由 `stat_density_ridges()` 函数根据参数中给限制计算。颜色通过通常的 `scale_fill_manual()` 函数定义并应用。在这里使用 `alpha()` 函数是为了为颜色添加一点透明度，因为我们使用了命名的颜色。或者，我们可以在这里使用十六进制代码并为这些代码设置 alpha 通道：

![](img/dd0d7d9aaacf496c4d1d0e31d83783b3_77_1.png)

图 3.6 – 添加分位数标记

正如我们所看到的，分布现在得到了很好的展示和标注。

# 使用 ggasy 定制化图表

在 ggplot2 中，自定义图表的关键方面之一是 `theme()` 函数，它允许用户自定义图表整体外观的元素。在 ggplot2 中自定义图表可能并不那么直观。虽然 `theme()` 功能强大，但它确实要求用户手动指定图表的每个元素，例如轴标签、标题、颜色和形状。构建在 ggplot 之上的 ggplot2 包旨在通过为许多常用自定义任务提供更简单、更直观的语法，以使图表自定义更易实现。`ggasy` 提供了一系列围绕 `theme()` 的简单封装函数，使得重要的事情变得更容易记忆。通过这个配方，我们将查看如何定制最初在 ggplot2 中创建的图表中的标签、图例和轴。

# 准备工作

我们需要 `ggplot2`、`ggasy` 和 `palmerpenguins` 包。

# 如何操作...

我们可以按照如下方式定制图表。

创建一个基础图表：

```r
library(ggplot2)
library(ggasy)
library(palmerpenguins)
```

```r
p <- penguins | 
dplyr::filter(!is.na(sex)) |
ggplot() + 
  aes(x = species, y = bill_length_mm) + 
  geom_boxplot(aes(fill = sex),
               position = position_dodge(width = 0.75)) + 
  geom_dotplot(
    aes(fill = sex),
    binaxis = 'y',
    binwidth = 0.1,
    position = position_dodge(width = 0.75),
    alpha = 0.5
  )
```

定制其外观

```r
p +
  theme_minimal() +
  theme(
    legend.position = "bottom",
    plot.title = element_text(face = "bold", size = 14),
    axis.title = element_text(size = 12)
  )
```

# 使用 ggasy 定制图表

```r
p +
  theme_classic() +
  labs(
    title = "不同物种的喙长度",
    subtitle = "数据来自 penguins数据集",
    x = "喙长度 (mm)",
    y = "物种"
  ) +
  theme(
    legend.position = "right",
    panel.grid.major = element_blank()
  )
```

这就是我们定制图表的方法。




## ggplot2 及用于出版级图表的扩展

```r
label_key = id +
theme(legend.position = "bottom")

p3 <- ggplot(penguins) +
aes(x = flipper_length_mm
```

```r
p4 <- allele_freqs |>
dplyr::filter(Chr == 1) |>
ggplot() +
aes(x = Pos, y = Allele_Freq, label = info) +
geom_point(aes(color = type)) +
facet_grid(Chr ~ , scales = "free x", space = "free") +
scale_color_manual(
	values = c("steelblue","gray","goldenrod","red"),
labels = c("CDS","NON-CDS","NON-SYN-Coding","CTGA")
) +
theme(legend.position = "bottom")
```

- 2. 移除图例并将图组合组合一列：

```r
library(cowplot)
left_column <- plot_grid(p1 + theme(legend.position = "none"),
p2 + theme(legend.position = "none"),
p3 + theme(legend.position = "none"),
col = 1, labels = c("A","B","C"))
```

- 3. 提取图例并将它们组合在一列：

```r
l1 <- get_legend(p1)
l13 <- get_legend(p3)

right_column <- plot_grid(l1, NULL, l13, ncol=1)
```

## 使用 facetzoom 对选定的图表区域进行缩放并标注

- 4. 组合前两列和最后一张图：

```r
two_cols <- plot_grid(left_column, right_column, ncol = 2, rel_
widths = c(0.66, 0.34))
labelled_4 <- plot_grid(p4, labels = "D")
```

```r
plot_grid(two_cols, labelled_4, ncol = 1, rel_heights = c(0.6,
0.4))
```

这就是我们从多个图表创建一个组合图表所需的所有步骤。

## 工作原理...

步骤 1 虽然很长，但本质上重复了本章之前讨论的代码（例如，第一个图来自此 ggrides 章节中的更改章节）。注意，在 p1 和 p3 中，我们修改了图例，在 `scale_fill_manual()` 层中使用 `guides` 函数来确保网格跨越两或三行（以便每行有一个元素）——这在以后非常重要，因为网格将被提取到单独的空间中。

步骤 2，我们通过将 p1、p2 和 p3 传递给 `cowplot::plot_grid()` 函数并将列数设置为 1，创建一个包含这三个图的图，使它们垂直堆叠。我们为每个图应用了标签。注意，这些图在堆叠之前已经通过 `theme` 移除了图例；我们将手动应用标签。

步骤 3 使用 `cowplot_get_legend()` 函数从原始图中提取图例并存储到对象中；再次使用 `plot_grid()` 将这些对象堆叠成一列。`NULL` 强制网格在该包含一个空元素。

步骤 4，我们组合已有的两列（再次使用 `plot_grid()`），这次分两列（`two_cols`），使用 `rel_widths` 选项允许图占据图表宽度的 60%。最后，我们为 p4 添加了一个标签——正如你猜的那样——通过最后一次调用 `plot_grid()` 将其置于之前的列之上，将列数设置为 1，并设置相对高度使列占据大部分空间。最终的图表如图 3.18 所示——或者在本书格式提供的较小图表空间内渲染时。当你自己在自己的机器上运行时，可能会看到更清晰的图。由于 R 的工作原理是在视口（指定大小的矩形）中渲染并尝试拟合对象，当某些对象无法进一步缩小时，它们可能会发生重叠。对于这个由许多子图组成的图来说，这是一个问题，因为某些元素无法缩小——特别是，当图变得太小时，文本必须保持足够大以便阅读，否则会发生重叠。我们为图表预留的空间有时会有物理限制。我们使用的包通过 `margins` 选项让您能够控制如何布局图表：

## ggplot2 及用于出版级图表的扩展

![](img/dd0d7d9aaacf496c4d1d0e31d83783b_96_0.png)

至此，我们可以看到如何将多个图组合成一个图。

## 更多...

这些图都有不同的图例，因此我们必须单独处理它们。你将分享的许多图共享图例和轴。`cowplot` 可以通过 `align_plots()` 函数按轴对齐子图。

## 另

`patchwork` 库提供了组合图表的另一种方法，提供了一种看起来有点数学化的声明式语法。在以下示例中，我们制作了两个版本的图表，将图例设置为行，在最后的 `(p1 + p3s) / p4` 中，我们创建了一个布局，将两个图放在同一行，位于单独占一行的第三个图上方。将其想象成一个数学表达式，即 `plot1` 和 `plot3` 都在 `plot4` 之上。我们还使用 `plot_annotation()` 添加了注释。

图 3.18 – 


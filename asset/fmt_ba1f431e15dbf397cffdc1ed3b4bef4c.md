
- 4. 对嵌套数据框（nested dataframe）操作：

```r
# 创建一个嵌套数据框

chromosome_id <- c(1,1,1,2,2,3,3)

gene_id <- c("A1","A2","A3","B1","B2","C1","C2","C3")

strand <- c("forward","reverse","forward","forward","reverse",

"forward","reverse","reverse")

length <- c(2000,1500,3000,2500,2000,1000,3000)

genes_df <- data.frame(chromosome_id, gene_id, strand, length)
```

```r
genes_df$samples <- list(data.frame(sample_id=1:2,

expression=c(2,3)),

data.frame(sample_id=1:3,

expression=c(3,4,5)),

data.frame(sample_id=1:2,

expression=c(4,5)),

data.frame(sample_id=1:3,

expression=c(5,6,7)),

data.frame(sample_id=1:2,

expression=c(6,7)),

data.frame(sample_id=1:2,

expression=c(1,2)),

data.frame(sample_id=1:2,

expression=c(2,3)),

data.frame(sample_id=1:2,

expression=c(3,4)))
```

```r
genes_df |>
  tidyr::unnest() |>
  group_by(chromosome_id, strand) |>
  summarise(mean_expression = mean(expression))
```

这些是在 `dplyr` 中使用“拆分-应用-合并”（split-apply-combine）的广泛示例。

## 工作原理……

第 1 步显式地创建一个数据框；我们这样做是为了能够方便地理解它的结构。

在第 2 步中，我们使用了最简单的方法：`group_by()` 函数用于根据 `chromosome_id` 对数据框的行进行分组，我们使用 `summarise()` 返回汇总数据框。第 3 步类似，但展示了如何使用分组列来创建更细粒度的分组，以及如何应用多个汇总函数。

第 4 步较为复杂；新的数据框是一个嵌套数据框，样本列表列在每个单元格中包含一个表达的数据框。在嵌套数据框上使用 `group_by()` 函数时，你首先需要使用 `tidyr::unnest()` 函数访问嵌套数据，然后像往常一样分组。注意，当使用 `tidyr::unnest()` 时，新数据框的每个基因、每个样本会有多行，因此通过感兴趣的列对数据框进行分组非常重要。

# 使用 datapasta 从复制的数据创建 R 对象

将数据粘贴到源代码文档中出于各种原因非常有用，其中最重要的是它允许创建一个可重复的示例，也称为 reprodex——一个演示问题或概念的最小化、自包含的示例。通过将数据包含在源代码中，其他人可以运行代码并亲眼看到结果，从而更容易理解和复制结果。

R 的 `datapasta` 包可以方便地将数据粘贴到 R 源代码文档中。它提供了一系列将数据转换为 R 定义的函数，在代码示例、测试或共享时创建静态对象时非常有用。在本教程中，你将学习如何使用 `datapasta` 将外部数据带入你的源代码文档中，而不是通过长期输入。

## 准备工作

我们将使用 `datapasta` 包，尽管它是非标准的。使用此命令：

```r
renv::install("datapasta", repos = c(mm = "https://ilesmcbain.universe.dev",), getOption("repos"))
```

这应该使用 `renv` 安装该包并让我们准备就绪。如果你还没有 `renv`，请按通常方式安装它。

## 如何操作……

`datapasta` 工具是以 RStudio 插件（add-in）的形式实现的，因此我们首先进行该设置：

- 1. 使用 RStudio 的 **Tools（工具） | Addins（插件） | Browse Addins（浏览插件）** 菜单，然后选择 **Keyboard Shortcuts（快捷键）**。你可以选择想要用于粘贴的组合键。
- 2. 点击操作旁边的中间列（如下截图所示），并按下你想要的按键。*图 2.1* 中的组合是一个不错的选择：

![](img/dd0d7d9aaacf496c4d1d0e31d83783b3_63_0.png)

图 2.1 – 选择快捷键
- 3. 获取一个网页表格——例如，访问 **Wikipedia（维基百科）** 此页面：`https://en.wikipedia.org/wiki/Tab-separated_values`——使用浏览右键 **Copy（复制）** 功能复制整个文本示例表格。这会将文本表格放入你的剪贴板缓冲区中。它看起来应该像*图 2.2 所示：*：

# 示例 [编辑]

`iris` 数据集的头部可以使用以下纯文本存储为 TSV（注意，HTML 渲染可能会将制表符转换为空格）：

| Sepal length | Sepal width | Petal length | Petal width | Species |
|---|---|---|---|---|
| 5.1 | 3.5 | 1.4 | 0.2 | I. setosa |
| 4.9 | 3.0 | 1.4 | 0.2 | I. setosa |
| 4.7 | 3.2 | 1.3 | 0.2 | I. setosa |
| 4.6 | 3.1 | 1.5 | 0.2 | I. setosa |
| 5.0 | 3.6 | 1.4 | 0.2 | I. setosa |

上面的 TSV 纯文本对应于以下表格：

![](img/dd0d7d9aaacf496c4d1d0e31d83783b3_64_0.png)

- 4. 将剪贴板中的新行粘贴到 R 源代码文档中。在合适的位置放置输入光标。

在本章中，我们将涵盖以下配方：

- 在 `ggplot2` 中组合多种图表类型
- 使用 `ggridges` 比较分布的变化
- 使用 `ggeasy` 定制图表
- 使用 `gghighlight` 在复杂的图表中突出显示选定值
- 使用 `ggdist` 更好地绘制变异性和置信区间
- 使用 `plotly` 制作交互式图形
- 使用 `facetzoom` 明确选定图表部分的标签位置
- 使用 `facetzoom` 对选定图表部分进行缩放并添加标注
- 使用 `cowplot` 和 `patchwork` 将多个图表组合成单图

## 技术要求

我们使用 `renv` 以针对特定项目的方式管理包。要使用 `renv` 安装包，你首先需要安装 `renv` 包本身。以下是安装 `renv` 然后使用它来安装包的方法：

- 1. 在你的 R 控制台中运行命令：

```
install.packages("renv")
```

- 2. 接下来，你将运行以下命令为你的项目创建一个新的 `renv` 环境：

```
renv::init()
```

- 3. 这将在你的当前项目目录下创建一个名为 `.renv` 的新目录。
- 4. 你可以使用以下命令安装包：

```
install.packages("<package name>")
```

- 5. 你可以运行以下命令使用 `renv` 包管理器来安装 Bioconductor 包：

```
renv::install("bioc::<package name>")
```

- 6. 例如，要安装 `Biobase`，你需要运行以下命令：

```
renv::install("bioc::Biobase")
```

- 7. 你可以像这样使用 `renv` 安装来自 GitHub 的开发包：

```
renv::install("<user name>/<repo name>")
```

例如，要安装用户 `danmaclean` 的 `rbioinfcookbook` 包，你将运行以下命令：

```
renv::install("danmaclean/rbioinfcookbook")
```

一些提示：

- 你可以通过逗号分隔包名来一次安装多个包。`renv` 会自动处理你所安装的包所需的任何依赖项。
- 在默认情况下，所有包将安装在本地项目目录中，而不是主中央库，这意味着你可以为每个项目拥有同一个包的多个版本。
- 此包所需的所有数据都在 GitHub 上专门创建的数据包 `danmaclean/rbioinfcookbook` 中。在安装该数据包后，数据将在你的项项目中变得可用。

对于本章，我们需要以下包：

- 常规包：
  - `cowplot`
  - `dplyr`
  - `gggist`
  - `ggeasy`
  - `ggforce`
  - `gghighlight`
  - `ggplot2`
  - `ggrepel`
  - `ggridges`
  - `palmerpenguins`
  - `patchwork`
  - `plotly`
- GitHub:
  - `danmaclean/rbioinfcookbook`

完成这些，我们就准备就绪了。这些包在安装时都不应该出现特殊问题。

# 更多信息

在 R 中，加载库并直接通过名称使用函数是标准做法。虽然这在短的交互会话中很棒，但当同时加载许多包且它们共享函数名时，可能会引起困惑。为了明确我在某一时刻使用的是哪个包和哪个函数，我会偶尔使用 `packageName : functionName` 的约定。

有时，在配方的过程中，我会中断代码以深入研究某些中间输出或查看对象的结构。当发生时，你会看到一个代码块，每行都以 `##`（双井号符号）开头。考虑以下命令：

```
letters[1:5]
```

这将给你以下输出：

```
## a b c d e
```

注意输出行以前缀 `##`。

## 在 ggplot2 中组合多种图表类型

`ggplot2` 的层模型是该库的一个核心特性，允许用户通过构建数据、美学和几何对象（geoms）的层来创建复杂的可视化效果。每一层代表图表的不同方面，它们堆叠在一起创建最终的可视化结果。在这个配方中，我们将使用层模型为 `palmerpenguins` 包中的数据创建一个复杂的图表。通过将其打印到屏幕上直接在 R 中检查数据可能会有所帮助。此外，该包在 https://allisonhorst.github.io/palmerpenguins/ 上有良好的文档，你可能想进一步了解它是如何生成的。

## 准备工作

安装 `ggplot2` 和 `palmerpenguins` 包。

## 如何操作...

我们可以使用图层系统按如下方式组合多种图表类型：

- 1. 为图表创建基础：

```
library(ggplot2)
library(palmerpenguins)
p <- ggplot(data = penguins) + 
aes(x = bill_length_mm, y = bill_depth_mm)
```

堆叠几何层（geoms）：

```
p +
geom_point() +
geom_smooth(method = "lm") +
geom_boxplot()
```

更有帮助地排列几何层顺序：

```
p +
geom_boxplot() +
geom_point() +
geom_smooth(method = "lm")
```

迭代坐标轴：

```
penguins |
dplyr::filter(!is.na(sex)) |
ggplot() +
aes(x = species, y = bill_length_mm) +
geom_boxplot(
position = position_dodge(width = 0.75)
) +
geom_dotplot(
binaxis = 'y',
stackdir = 'center',
method = "histodot",nposition = position_dodge(width = 0.75),
alpha = 0.5,
dotsize = .5
)
```

这就是图表所需的所有内容。

## 工作原理...

第 1 步设置了基础图表对象，提供了数据和美学层，形成了最终图表的坐标轴和范围。几何层尚未添加，因此通过输入 `p` 查看此图表将显示一个只有坐标轴的空图。第 2 步添加了必要的几何层。注意图 3.1，几何层按声明顺序堆叠，导致箱线图完全遮挡了其他部分。我们可以通过从下上调用它们来控制几何层的顺序，因此在第 3 步中，我们先添加箱线图，然后通过点和平滑线，我们得到了更可见的层次效果，如图 3.2 所示：

## 层中的几何对象

图 3.1 - 层中的几何对象

## 布局更好的第二次迭代

### 还有更多...

让 `ggplot2` 智能化的下一步是使用 `aesthetic()` 将变量与某些视觉方面建立映射。我们可以借此将形状、线条颜色、填充颜色和点大小等属性映射到图表上。全局 `aes()` 应用于所有几何层，而特定几何对象的 `aes()` 只应用于它们声明所在的几何层。

以下代码展示了如何操作：

```
penguins |
dplyr::filter(!is.na(sex)) |
ggplot() +
aes(x = bill_length_mm, y = bill_length_mm, size = island) +
geom_point(aes(shape = sex), alpha = 0.5) +
scale_colour_brewer(palette = "Set2")
```

前面的代码生成了图 3.3 所示的输出：

最后的修改是通过 `scale()` 和调色板完成的。在前面的代码中，我们使用内置的 ColourBrewer 调色板添加了手动颜色标度。

## 如何操作...

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

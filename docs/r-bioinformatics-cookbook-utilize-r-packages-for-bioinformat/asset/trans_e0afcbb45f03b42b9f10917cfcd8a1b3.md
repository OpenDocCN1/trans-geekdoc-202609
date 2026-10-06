

在本章中，我们将涵盖以下配方：

- 在 ggplot2 中组合多种图表类型
- 使用 ggridges 比较分布的变化
- 使用 ggeasy 定制图表
- 使用 gghighlight 在复杂的图表中突出显示选定值
- 使用 ggdist 更好地绘制变异性和置信区间
- 使用 plotly 制作交互式图形
- 使用 facetzoom 明确选定图表部分的标签位置
- 使用 facetzoom 对选定图表部分进行缩放并添加标注
- 使用 cowplot 和 patchwork 将多个图表组合成单图

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
  - cowplot
  - dplyr
  - gggist
  - ggeasy
  - ggforce
  - gghighlight
  - ggplot2
  - ggrepel
  - ggridges
  - palmerpenguins
  - patchwork
  - plotly
- GitHub:
  - danmaclean/rbioinfcookbook

完成这些，我们就准备就绪了。这些包在安装时都不应该出现特殊问题。

## 更多信息

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

ggplot2 的层模型是该库的一个核心特性，允许用户通过构建数据、美学和几何对象（geoms）的层来创建复杂的可视化效果。每一层代表图表的不同方面，它们堆叠在一起创建最终的可视化结果。在这个配方中，我们将使用层模型为 `palmerpenguins` 包中的数据创建一个复杂的图表。通过将其打印到屏幕上直接在 R 中检查数据可能会有所帮助。此外，该包在 https://allisonhorst.github.io/palmerpenguins/ 上有良好的文档，你可能想进一步了解它是如何生成的。

### 准备工作

安装 `ggplot2` 和 `palmerpenguins` 包。

### 如何操作...

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

### 工作原理...

第 1 步设置了基础图表对象，提供了数据和美学层，形成了最终图表的坐标轴和范围。几何层尚未添加，因此通过输入 `p` 查看此图表将显示一个只有坐标轴的空图。第 2 步添加了必要的几何层。注意图 3.1，几何层按声明顺序堆叠，导致箱线图完全遮挡了其他部分。我们可以通过从下上调用它们来控制几何层的顺序，因此在第 3 步中，我们先添加箱线图，然后通过点和平滑线，我们得到了更可见的层次效果，如图 3.2 所示：

## 层中的几何对象

图 3.1 - 层中的几何对象

## 布局更好的第二次迭代

### 还有更多...

让 ggplot2 智能化的下一步是使用 `aesthetic()` 将变量与某些视觉方面建立映射。我们可以借此将形状、线条颜色、填充颜色和点大小等属性映射到图表上。全局 `aes()` 应用于所有几何层，而特定几何对象的 `aes()` 只应用于它们声明所在的几何层。

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


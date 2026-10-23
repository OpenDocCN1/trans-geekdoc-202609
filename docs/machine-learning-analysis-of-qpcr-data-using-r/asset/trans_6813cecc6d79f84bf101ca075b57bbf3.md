
openPrimeR 包是 Bioconductor 的一部分；Bioconductor 是一个用于基因组数据分析的开发软件项目，它与 R 核心开发团队相关联，但独立于后者。因此，它不能从 R 仓库中获得，使用 `install.packages` 函数将会返回错误。Bioconductor 的包可以通过 `BiocManager` 包中的 `install` 函数来安装——其简写形式为 `BiocManager::install(package)`——该函数可从 R 仓库获得。安装步骤如下：

```
install.packages("BiocManager")
library("BiocManager")
BiocManager::install("openPrimeR")
```

然而，openPrimeR 本身还需要操作系统的一系列库，因此用户需要根据手头的系统来定制安装。关于 openPrimeR 安装的更多信息，请访问 https://www.bioconductor.org/packages/release/bioc/html/openPrimeR.html。安装成功完成后，openPrimeR 可以像其他任何 R 库一样被打开。R 函数 `system.file` 用于查找包中文件的完整文件名，在本例中即 openPrimeR。

`system.file("file", package = "openPrimeR", lib.loc, mustWork)`

`file`
要搜索的文件。可以传入多个文件。

`package`
包含该文件的包。`"base"` 用于 R 原生文件。

`lib.loc`
查找文件的路径；默认值为 `NULL`。

`mustWork`
逻辑值，如果找不到文件则返回错误。

`design_primers(template.df, mode.directionality, settings, init.algo, opti.algo, required.cvg, timeout, max.degen, conservation, sample.name, cur.results.loc, primer.df, updateProgress)`

`template.df`
包含带注释引物的模板序列的对象。

`mode.directionality`
需要设计引物的模板链：正向链（`"fw"`）、反向链（`"rev"`）或两者（`"both"`）。

`primer.length`
数值，提供所设计引物的目标长度。

`primer.estimate`
是否应估计所需引物的数量（默认=`FALSE`）。

`required.cvg`
所覆盖模板序列的期望比例（默认=1）。

`sample`
字符向量，为模板提供标识符。

`primer.lengths`
长度为 2 的数值向量，提供所生成引物允许的最小和最大长度。

`allowed.region.definition`
字符向量，提供引物构建区域的定义：如果引物位于允许结合区域内，则为 `"within"`（默认），否则为 `"any"`。

`init.algo`
用于初始化引物的算法，`"naive"`（默认）或 `"free"`。

`max.degen`
引物候选的最大简并度（默认 = 16）。

`conservation`
保守率（默认 = 1）。

`updateProgress`
详细输出选项（默认 = `NULL`）。

`settings`
指定设计引物的约束设置的对象。

`opti.algo`
用于解决引物集合覆盖问题的算法，`"Greedy"`（默认）或 `"ILP"`。

`timeout`
`"ILP"` 选项超时前的秒数（默认 = `Inf`）。

`sample.name`
引物设计任务的标识符（默认 = `NULL`）。

`cur.results.loc`
用于存储结果的目录。

`write_primers(primer.df, fname, ftype)`

`primer.df`
包含带注释引物的模板序列的对象。

`fname`
输出文件名。

`ftype`
输出文件的结构，为 `"FASTA"` 或 `"CSV"`。

`read_primers(fname, fw.id, rev.id, merge.ambig, max.degen, template.df, adapter.action, sample.name, updateProgress)`

`fname`
输入文件名，为 `"FASTA"` 或 `"CSV"`。

`fw.id`, `rev.id`
FASTA 头部中正向/反向引物的标识符。

`merge.ambig`
IUPAC 简并码的使用方式，`"none"`（默认）、`"merge"` 或 `"unmerge"`。

`max.degen`
如果 `merge.ambig = "merge"`，则为允许的最大简并度。

`template.df`
`Templates` 类的对象。

`adapter.action`
当提供 `template.df` 时要执行的操作，`"warn"`（默认）或 `"rm"`（移除已识别的接头序列）。

`sample.name`
输入引物的标识符。

`updateProgress`
详细输出选项（默认 = `NULL`）。

`read_templates(fname, delim, id.column, rm.keywords, remove.duplicates, fw.region, rev.region, gap.char, ...)`

`fname`
输入文件名，为 `"FASTA"` 或 `"CSV"`。

`delim`
列的分隔符。

`id.column`
头部中用作单个模板序列标识符的字段。

`remove.duplicates`
是否应移除重复序列。

`fw.region`, `rev.region`
从模板 5' 或 3' 端开始的位置区间，指定正向或反向引物的结合位点。默认设置为前 30 或后 30 个碱基。

`gap.char`
输入文件中表示空位的字符（默认 = `"-"`）。

## 清单 2.2。

通过使用用户自定义函数 `PCR` 生成一系列初始靶标量提高十倍后的信号，构建出一条假设的标准曲线；扩增结果存储在 A1-A6 对象中。交叉点通过使用自定义函数 `find_cycle`（清单 2.1）获得，该函数需要提供扩增信号（A1-A6 对象）、x 轴系列（第 1 至第 45 个循环）以及扩增指数期开始的估计循环数。这样的起始点可以通过观察以扩增循环为横轴、荧光信号对数为纵轴的扩增图谱来大致确定：指数期在该图谱上是线性的。然后根据获得的值构建一个数据框，并绘制出显示交叉（Cq）点的图。点的颜色由用户提供的灰色深浅来设定。也可以使用 RcolorBrewer 库自动获得一系列颜色，以避免手动选择深浅并最大化元素之间的视觉区分度。这些颜色集合称为调色板，通过 `brewer.pal` 函数选择。调色板可以赋值给一个对象，颜色则通过绘图函数的 `col` 参数来指定。

在绘图中可以控制的附加元素之一是坐标轴。`axis` 函数定义坐标轴图例及其对应刻度标记的放置位置、内容和方向。`brewer.pal` 函数选择预定义的颜色深浅以最大化数据的可视化效果。`unique` 函数返回向量的唯一元素。

`axis(side, at, labels, tick, lty, lwd, col, pos, outer, lwd.ticks, col.ticks, hadj, padj, gap.axis, ...)`

`side`
整数，指定坐标轴绘制在绘图的哪一侧（1=下方，2=左侧，3=上方，4=右侧）。

`at`
绘制刻度标记的位置。默认值为 `NULL`。

`labels`
放置在刻度点处的标签的字符或表达式向量。

`tick`
逻辑值，指定是否应绘制刻度标记和坐标轴线。

`lty`, `lwd`, `col`
坐标轴线的类型、宽度和颜色。

`pos`
绘制坐标轴线的坐标。

`outer`
逻辑值，指示坐标轴是否应绘制在外侧绘图边距中。

`lwd.ticks`, `col.ticks`
刻度标记的线宽和颜色。

`hadj`
所有标签在与阅读方向平行（“水平”）方向上的调整。默认为居中。默认值为 `NA`。

`padj`
所有标签在与阅读方向垂直方向上的调整（0 = 右对齐或顶部对齐，1 = 左对齐或底部对齐）。默认值为 `NA`。

`gap.axis`
可选的数值因子，指示坐标轴值之间的间隙。默认值为 `NA`。

`brewer.pal(n, name)`

`n`
要使用的颜色深浅数量。

`name`
调色板的名称（`"BrBG"`、`"PIYG"`、`"PRGn"`、`"PuOr"`、`"RdBu"`、`"RdGy"`、`"RdYlBu"`、`"RdYlGn"`、`"Spectral"`）。

`unique(x)`

`x`
要评估的向量。

## 清单 2.3。

从高输入样本的荧光信号中检索出高于所选 1000 光单位截止值的循环；该系列的第一个值保存在变量 `crossOverH` 中。绘制该样本扩增图谱的放大图，并同时绘制截止线。截止线前后的扩增点也会被绘制出来，分别对应 `crossOverH` 和 `crossOverH – 1`。Cq 值通过目视确定在扩增曲线与截止线的交点处，该值存储在变量 `cq_high` 中。对低输入样本重复该过程。在清单的后续部分中，计算拷贝数并绘制标准曲线，同时标出这两个样本。箭头用于显示插值过程，从而实现对未知样本的定量。

函数 `which` 用于确定向量中哪些元素满足指定条件。
例如，给定向量 `x <- c(-2, -1, 0, 1, 2)`，`which(x > 0)` 返回满足条件的 `x` 元素的索引。这些索引可以通过索引操作直接选择 `x` 中满足条件的元素：`x[which(x > 0)]` 将返回 `[1, 2]`。
通过使用参数函数 `par`，可以将绘图分割成相等的面板，将绘图视为由行和列组成的表格。新参数将应用于之后绘制的所有图形，因此通常的做法是将原始参数保存在一个对象中以备后用，或者将 `par` 包含在图形设备中，如下所示：

```
png(...)
par(...)
...
dev.off()
```

`which(x condition)`

`x`
要评估的向量。

`condition`
用于评估数据的逻辑测试。

`arrows(x0, y0, x1, y1, ...)`
`segments(x0, y0, x1, y1, ...)`

`x0`, `y0`
起始点。

`x1`, `y1`
结束点。

`par(mfrow=c(row, cols))`

`row`, `cols`
定义面板的行数和列数。



最终图表是通过最后的调用创建的。我们在这里无法看到它，因为它是一个密集的多维图表，其坐标轴在打印格式下无法清晰渲染。不过，你应该能在屏幕上看到它。一旦你获取了它，就能看到不同的幂次。一旦你获取了它，就能看到不同的幂次。注意，坐标轴标识了样本的数量，指标包括假阴性率（FDR）、假阴性/假阳性率（FNR）、假阳性率（FPR）以及真阳性率（TPR）。

## 更多变异...

当我们只有一个样本时（或者只是一个副本）时，很难估计 `log2` 变化。我们可以使用以下函数生成一个均值为 0、标准差为 2 的分布：

```
log2fc <- function(x) { rnorm(length(x), 0, 2) }
```

 这里的非注释区域的分布：

```
if (condVar > someVal) {console.log("xxx")}
```

 寻找非注释区域

寻找非注释区域在多种应用中非常有用。通过识别这些非注释区域，研究人员可以更好地理解基因组。识别这些非注释区域可以发现替代剪接事件。识别这些非注释区域可能包括**非翻译区 (UTRs)**、lncRNA、miRNA 以及其他非编码 RNA。这些非注释区域可以提供关于基因组调控的见解。通过识别这些非注释区域，可以发现特定的组织。非注释区域显示了哪些区域没有被注释覆盖。

## 准备工作

概念上，非注释区域看起来如图 6.2 所示：![](img/07283b1.png)

图 6.2 - 注释 reads 的覆盖图

我们希望通过 `SummarizedExperiment` 和 `csaw` 包来找到非注释区域。非注释区域将落在基因组中。通过 `IRanges` 包可以得到结果。

## 如何操作

这是找到非注释区域的方法：

1. 设置一个加载函数：

```
library(rtracklayer)
annotated_regions_from_gff <- function(name) { import(name) }
```

2. 在窗口中获取计数：

```
library(csaw)
library(rbioinfocbook)
```

```
bam_path <- "extdata/bam"
gff_path <- "extdata/gff"
```

```
window_counts <- windowCounts(bam_path, gff_path, bin = 500)
```

 5. 将数据放入：

```
window_counts <- data.frame(assay(nonannotated_regions))
window_ranges <- data.frame(ranges(nonannotated_regions))
results <- cbind(window_ranges, window_counts)
```

## 工作原理

第一步，使用 `rtracklayer` 设置了一个加载函数来导入 GFF。具体来说，它接收一个文件名并返回 GRanges 对象。

第二步，加载 `csaw` 和 `rbioinfocbook` 并指定 `bam_path` 和 `gff_path`。使用 `csaw` 中的 `windowCounts` 函数对窗口进行计数。然后对 gff 调用 `annotated_regions_from_gff` 函数并得到相应的 GRanges 对象。

第三步，加载 `IRanges` 和 `SummarizedExperiment`，并使用 `IRanges::overlaps()` 识别基因组的哪些部分与注释区域重叠。结果是一个逻辑向量，指示每个窗口是否重叠。

第四步，根据 `windows_in` 向量创建 `whole_genome` 的子集。`annotated_regions` 包含重叠区域的窗口，而 `nonannotated_regions` 则包含不重叠的窗口。

第五步，使用 `assay()` 函数从 `nonannotated_regions` 对象中提取计数数据，并转换为更易读的 DataFrame。同样，使用 `ranges()` 函数输出使用的窗口。使用 `cbind` 函数将这些 DataFrame 合并为 `results`。

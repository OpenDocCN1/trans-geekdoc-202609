

# 执行定量 RNA-seq

工作流通常从对高通量测序数据进行预处理开始，这可能涉及质量控制、比对到参考基因组，以及将比对数据转换为可供包使用的格式。随后，该包将扫描基因组区域并输出显著富集的窗口列表，这些窗口围绕每个窗口内的平均信号水平。本食谱将教你如何使用 `bumhunter` 包，通过高通量比对和一组定义峰区域的阈值来发现比对突变（bumps）区域。

# 准备工作

我们将使用上一个食谱中使用的窗口数据。我们需要 `Rsamtools` 和 `bumhunter` 库。

# 如何操作...

我们将从一个 文件文件中加载数据：

- 加载数据并获取每个位置的覆盖度：
```r
library(rbioinfocookbook)
library(Rsamtools)

bam_path <- fs::path_package("extdata",
  "windows.bam",
  package="rbioinfocookbook")
pileup_df <- Rsamtools::pileup(bam_path)
```

- 寻找初步聚类：
```r
library(bumhunter)
clusters <- bumhunter::clusterMaker(pileup_df$seganames,
  pileup_df$pos,
  maxGap = 100
)
```

- 带有最小阈值寻找突变：
```r
final_bumps <- bumhunter::regionFinder(pileup_df$count,
  pileup_df$seganames,
  pileup_df$pos,
  clusters,
  cutoff = 1
)
```

这个简短的食谱就是我们需要的。

# 工作原理...

在步骤 1 中，加载了 `rbioinfcookbook` 和 `Rsamtools` 包，这两个包都提供了多种功能，例如读取 BAM/SAM/CRAM 文件和 BED 文件、处理 BAM 索引以及从 BAM 文件检索数据。然后，使用 `fs` 包中的 `path_path` 获取窗口 `.bam` 文件的路径，这是一个包含测序 reads 的 BAM 文件。该数据是 `rbioinfcookbook` 包附带的数据的一部分，将在分析的后续步骤中使用。

在步骤 2 中，使用 `bumhunter` 包中的 `clusterMaker` 函数在数据中寻找初步聚类。`clusterMaker` 函数期望一个染色体名称向量（`pileup_df$pos`）和一个 `maxGap` 参数，后者定义了同一聚类中两个位置之间允许的最大距离。在这里，允许的最大距离为 100 bp。`clusterMaker` 函数返回一个聚类 ID 向量，属于同一簇的位置具有相同的 ID。参考以下代码：

```
## clusters
## 1 2 3
## 1486 1552 1520
```

这为我们提供了步骤 2 中获得的聚类，以表格形式显示属于每个聚类的位置数量。

在步骤 3 中，使用 `regionFinder` 函数根据上一步得到的初步聚类来寻找数据中实际的富集突变（bumps）。`regionFinder` 函数期望一个计数向量（`pileup_df$counts`）、一个位置向量（`pileup_df$pos`）、从上步骤 2 获得的聚类，以及一个 `cutoff` 参数，该参数定义了某个位置若要被视为突变的一部分，所允许的最小计数。最小计数被设为 1。

`regionFinder` 返回一个包含聚类位置和突变大小指标的 DataFrame：希望这概述了如何仅通过表达数据找到峰或突变。

# 更多内容...

如果你有多个实验需要分析，请尝试使用 `bumhunter` 函数。它将在矩阵的多个数据列上运行，并执行线性建模以评估关于重复样本位置和存在性的不确定性。它在操作上与 `regionFinder()` 非常相似。

# 差异峰分析

在基因组数据中识别差异表达的峰是生物信息学的一项关键任务，并有许多用途。最常见的应用之一是 ChIP-Seq 数据分析，该技术被用于识别转录因子和 DNA 结合蛋白的结合位。通过比较不同样本或条件之间的 ChIP-Seq 数据，研究人员可以识别差异表达的富集峰，并深入了解蛋白质如何调节不同基因的表达。另一个例子是 RNA-Seq 数据——通过比较不同样本或条件之间的 RNA-Seq 数据，研究人员可以识别差异表达的表达峰，并深入了解不同样本或条件如何影响不同基因的表达。

其他用例还包括组蛋白修饰和 ATAC-Seq 数据，用于通过染色质开放性研究基因表达的调节。我们已经查看了如何分析差异表达区域，我们只需要为未注释的区域命名然后对它们进行分析，这通常是在如 `SummarizedExperiment`、计数矩阵或 `DESeq2` 对象中。

# 准备工作

在这个食谱中，我们需要 `RangedSummarizedExperiment` 版本的 RNA-seq 数据。我们将使用的数据来自一组受到的缘单单胞菌（Pseudomonas syringae）hrcC 突变体（hurt）感染的拟芥（Arabidopsis thaliana）样本对比一组对照感染样本（mock）。每个样本类型有三个重复。数据由 `rbionfcookbook` 包提供。

# 如何操作...

我们可以如下所示进行峰比较：

- 加载集合并使用创建标签的函数：
```r
library(rbioinfookbook)
library(SummarizedExperiment)

makeTag <- function(range_obj) {
  paste0(range_obj@seqnames,
    ":",
    range_obj@start,
    ":",
    range_obj@width)
}
```

- 提取数据并注释行：
```r
counts <- assay(arab_infection)

if (!is.null(names(rowRanges(arab_infection)))) {
    rownames(counts) <- rowRanges(arab_infection)
} else {
    rownames(counts) <- makeTag(rowRanges(arab_infection))
}
```

这里需要两个步骤，但它们非常强大。

# 工作原理...

在步骤 1 中，加载了两个库，`rbioinfcookbook` 和 `SummarizedExperiment`。`rbioinfcookbook` 提供了数据集，`SummarizedExperiment` 包提供了一个存储比对到基因组的实验结果容器。此外，定义了一个名为 `makeTag` 的函数。该函数接受一个 `Ranges` 类对象（基因组范围注释的容器），通过连接序列名称、起始位置和结束位置来创建标签。该函数随后将用于为 DataFrame 创建标签。

在步骤 2 中，使用 `assay()` 提取 `arab_infection` 数据。`if` 语句检查 `rowRanges(arab_infection)` 是否包含名称。如果是，将名称分配给计数的行；否则，对 `rowRanges(arab_infection)` 使用 `makeTag` 函数分配行。

输出是一个计数矩阵，如下：

```
## head(counts)
##               mock1 mock2 mock3 hrc1 hrc2 hrc3
## Chr1:3631-5900     35 77 40 46 64 60
## Chr1:5928-8738     43 45 32 43 39 49
## Chr1:11649-13715    16 24 26 27 35 20
## Chr1:23146-31228    72 43 64 66 25 90
## Chr1:31170-33154    49 78 90 67 45 60
## Chr1:33379-37872     0 15 2 0 21 8
```

这包含了基因组区域和计数。

# 使用 SVA 估算批效应

当科学实验中不同样本组之间的测量结果存在系统性差异时，就会发生批效应，尽管样本本身在生物学上是相同的。这些差异可能由多种因素引起，例如实验条件、使用的设备或实验时间。在 RNA-Seq 实验中，当样本在不同的测序平台或在不同时间运行时，可能会产生批效应，导致样本之间的读取计数差异。这会影响实验的统计效力，并为分析引入偏差。

处理 RNA-Seq 实验批效应的常用方法是使用替代变量分析（SVA）Bioconductor 包。SVA 包通过统计方法识别批效应，并识别数据中可能由技术因素引起的变异源。该包的工作是寻找与引起批效应的技术因素强相关的替代变量集。然后，将这些替代变量作为协变量引入线性模型以控制批效应。这允许实验人员消除由技术因素引入的任何偏差，并提高实验的统计效力。

该包使用主成分分析来识别数据大部分变异。它还具有内置方法，用于识别哪些主成分与已知的技术因素（如批次、孔板或芯片号）相关。然后，它将这些相关的主成分作为协变量引入统计模型，以调整批效应。


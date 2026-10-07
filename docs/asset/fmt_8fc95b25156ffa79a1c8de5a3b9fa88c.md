
这就是创建一个非常漂亮且信息丰富的图所需的全部代码。

## 工作原理

在步骤 1 中，我们加载了必要的库。`ComplexHeatmap` 库用于生成热图，`viridisLite` 用于色标尺，`stringr` 用于文本处理，`RColorBrewer` 用于生成色板，`circlize` 用于圆形可视化，而 `rbioinfocbook` 是书中所需数据的包。

`at_tf_gex` 数据集是一个 DataFrame，通过对该数据集的子集（特别是第 5 到 55 列）进行对数转换并创建：`matrix(at_tf_gex[,5:55])`。这一步是为了缩放数据使其在视觉上可解释。

然后，通过使用 `stringr::str_split` 函数分割矩阵的列名来提取 `ecotype` 和样本的 `part`，在 `ecotype` 中以逗 分隔，在 `part` 中以 ` 分隔（注意模式中的空格——这是移除领先空格的快速方法）。`str_split()` 函数接受三个参数：要分割的字符串、用于分割的分隔符，以及你希望输出是否简化。`simplify=TRUE` 参数告诉函数返回一个向量，而不是返回向量列表。

在步骤 2 中，代码为热图中的不同类型数据创建色板。`data_col_func` 是使用 `circlize::colorRamp2` 创建的函数，它将值映射到 `viridis::magma` 函数提供的颜色范围，总共有 6 种颜色。`data_col_func` 将在以后调用以在范围内动态生成颜色。`colorRamp()` 取两个参数，第一个是数值范围，第二个是推导出颜色值的标尺。

`ecotype_code` 是一个派自 RColorBrewer 的色板，包含来自 Set3 色板的 12 种颜色和来自 Set1 色板的 5 种颜色（我们有 17 个生态型，而 RColorBrewer 最大的色板最多有 12 种颜色，因此我们必须借用色板的颜色）。`part_colors` 是一个由三种颜色组成的 RColorBrewer 色板，用于突出植物信息。`RColorBrewer::brewer.pal()` 提供预定义的色板。它接受两个参数——第一个是颜色数量，第二个是色板名称。

将 `ecotype_codes` 和 `part_colors` 分别分配给 `ecotype` 和 `part` 的唯一元素，因此生成的注释将根据这些唯一元素进行颜色编码。

# 174 执行定量 RNA-seq

| log(TPM) | 种型 | 植物部位 |
|---|---|---|
| 8 | Bu-0 | 陆上部分 |
| 6 | Ci-1 | 花蕾 |
| 4 | Ed-0 | 根 |
| 2 | Hi-0 | |
| 0 | Kn-0 | |
| | Ler-0 | |
| | Mi-0 | |
| | No-0 | |
| | Po-0 | |
| | Rich-4 | |
| | Sf-2 | |
| | Tau-2 | |
| | Wl-2 | |
| | Ws-0 | |
| | Wu-0 | |

![](img/dd0d7d9aaacf496c4d1d0e31d83783b3_196_0.png)

在第 5 步中，代码从数据集中筛选出我们感兴趣的 TF 家族并将其重命名为其他。`of_interest` 变量被定义用于存储感兴趣的家族，这是一个包含 bHLH、WRKY 和 bZIP TF 的数组。然后，通过对集集 `at_tf_$Family` 变量创建了 `short_family`，其中 `short_family` 不属于 `of_interest` 成员并被设置为 other（其他）。接着，使用 `RColorBrewer::brewer.pal()` 函数创建一个颜色调色板，并将 `short_family` 中的唯一元素分配给它。

在第 6 步中，使用 `Heatmap()` 函数创建了第二个热图。`Short_family` 被用输入数据。`HeatmapAnnotation()` 函数用于显示 TF 家族信息的摘要（注意，这次我们没有使用中间变量，而是直接在 `Heatmap()` 调用中设置了该函数。尽管这部分看起来像是一个注释，但在代码中它被编码为第二个单列热图）。`col` 选项设置为 `fam_colors`，宽度设置为 `unit(2, "cm")`（这可以根据图形输出设备的大小进行调整）。`HeatmapAnnotation()` 函数可以用于向热图添加各种注释元素 —— 在此例中，它被用于添加行的摘要。`anno_summary()` 函数用于显示摘要，其参数用于指定是针对行还是列，`height` 参数用于指定注释的高度。该部分内容如下：

# 使用 ComplexHeatmap 展示 RNA-Seq 数据

![](img/dd0d7d9aaacf496c4d1d0e31d83783b3_197_0.png)

图 6.4 - 热图的第二部分

在第 7 步中，使用 `+` 运算符将两个热图合并，并使用 `ComplexHeatmap::draw()` 函数渲染最终热图。`draw()` 函数用于渲染由两个热图 `ht_1` 和 `ht_2` 组合生成的最终热图。生成的热图是两个热图的结合，将在热图的右侧显示 `mat` 上的数据、种型和部位信息、长度以及 TF 家族数据。最终合并后的热图如下：

![](img/dd0d7d9aaacf496c4d1d0e31d83783b3_197_1.png)

图 6.5 - 最终合并的热图

这向我们展示了一个信息丰富、具有出版质量的多维度热图。

# 7 使用 HTS 数据寻找基因变异

**高通量测序 (HTS)** 使得在极短时间内发现许多样本的基因变异并进行全基因组分型和单倍型分析成为可能。这项技术释放的数据流为生物信息学家和计算机科学家创造了一些独特的机会，并催生了创新的存储和数据分析流程。变异检测（variant calling）的基础流程始于对 HTS reads 的质量控制，并将其比对到参考基因组。这些步骤通常在 R 分析之前完成，通常会产生一个读取比对的 BAM 文件或变异位置的**变异检测文件 (VCF)**，我们需要在 R 代码中处理这些文件。

由于变异检测和分析是生物信息学中一项非常基础的技术，Bioconductor 装备了我们构建软件和执行分析所需的工具。研究人员想要的问题范围从*我的基因组中的基因变异在哪里？有多少个？* 到*我如何对它们进行分类？* 在章中，我们将查看解决这些问题的方案，并查看其他允许我们可视化基因组上的变异和标记的重要通用技术，以及评估变异与基因型之间的关联。我们还将查看**基因变异**这一术语的其他定义，并看看我们如何评估单个位点的拷贝数。

在本章中，我们将涵盖以下方案：

- 使用 VariantTools 在序列数据中寻找 SNPs 和 INDELS
- 在长参考序列中预测开放阅读框 (ORF)
- 使用 karyoploteR 在遗传图谱上绘制特征
- 使用 VariantAnnotation 选择和分类变异
- 提取感兴趣基因组区域的信息
- 使用 GWAS 寻找表型与基因型的关联
- 估计感兴趣位点的拷贝数

## 技术要求

我们将使用 `renv` 以项目特定的方式来管理包。要使用 `renv` 安装包，你首先需要安装 `renv` 包。你可以通过在 R 控制台中运行以下命令来实现这一点：

1. 安装 renv：

```
install.packages("renv")
```

2. 创建 renv 环境：

```r
renv::init()
```

这将在当前项目目录下创建一个名为 `.renv` 的目录。

3. 然后你可以使用以下命令安装包：

```r
renv::install_packages()
```

4. 你还可以使用 `renv` 包管理器来安装 Bioconductor 包，运行以下命令：

```r
renv::install("bioc::package name")
```

5. 例如，要安装 Biobase 包，你可以运行：

```r
renv::install("bioc::Biobase")
```

6. 你可以使用 `renv` 安装 GitHub 上的开发包，如下：

```r
renv::install("username/repo name")
```

7. 例如，要安装 danmaclean 用户的 rbioinfocookbook 包，你可以运行：

```r
renv::install("danmaclean/rbioinfocookbook")
```

使用 `renv`，你可以通过逗号分隔名称来一次安装多个包。`renv` 会自动处理任何依赖项。在本章中我们需要以下包：

- fs
- readr
- systemPipe

Bioconductor 包：
- Biostrings
- csaw
- GenomicRanges
- gmapR
- karyoploteR
- rrBLUP
- rtracklayer
- SummarizedExperiment
- VariantAnnotation
- VariantTools

以及 GitHub：
- danmaclean/rbioinfocbook

1. 导入所需的库：

```
library(GenomicRanges)
library(gmapR)
library(rtracklayer)
library(VariantAnnotation)
library(VariantTools)
```

2. 然后，加载数据集：

```
bam_file <- fs::package("extdata",
  "hg17_snps.bam",
  package="rbioinfocookbook"
)
fasta_file <- fs::package("extdata",
  "chr17.83k.fa",
  package="rbioinfocookbook"
)
```

3. 设置基因组对象和参数对象：

```
fa <- rtracklayer::FastFile(fasta_file)
genome <- gmapR::GmapGenome(fa, create=TRUE)
qual_params <- TallyVariantsParam(
  genome = genome,
  minimum_mapq = 20)
var_params <- VariantCallingFilters(read.count = 19,
  p.lower = 0.01)
```

4. 调用变异检测：

```
called_variants <- callVariants(bam_file,
  qual_params,
  calling.filters = var_params
)
head(called_variants)
```

现在，我们可以进入注释阶段，并从 .gff 或 .bed 文件加载特征位置信息：

```
VariantAnnotation::sampleNames(called_variants) <- "sample_name"
vcf <- VariantAnnotation::asVCF(called_variants)
VariantAnnotation::writeVcf(vcf, "hg17.vcf")
get_annotated_regions_from_gff <- function(file_name) {
  gff <- rtracklayer::import.gff(file_name)
  as(gff, "GRanges")
}
get_annotated_regions_from_bed <- function(file_name) {
  bed <- rtracklayer::import.bed(file_name)
  as(bed, "GRanges")
}
```

```
genes <- get_annotated_regions_from_gff(fs::path_package("extdata",
    "chr17.83k.gff3",
    package="rbioinfocookbook"
))
```

现在，我们可以计算哪些变异与哪些基因重叠：

```
overlaps <- GenomicRanges::findOverlaps(called_variants, genes)
overlaps
```

最后，我们可以根据重叠列表对基因进行子集提取：

```
genes[subjectHits(overlaps)]
```

这为我们提供了包含多态性的区域。

## 工作原理...

这是一个漫长且复杂的流水线，包含一些复杂的步骤。在加载库之后，接下来的两行代码设置了我们从数据包中需要的文件。我们需要一个 .bam 文件和一个 .fasta 文件。接下来，我们使用 `gmapR()` 函数结合 fasta 对象创建一个 `MapGenome` 对象——这向变异检测函数描述了基因组情况。我们使用的另外两个函数 `TallyVariantParams()` 和 `VariantCallingFilters()` 对于正确检测和过滤候选 SNP 至关重要。在这些函数中，你可以设置定义 SNP 或 INDEL 的参数。这里的选项被刻意设置得很糟糕。如下所示，当我们创建 64 个候选变异时，只检测到了 6 个。

一旦定义了参数，我们使用使用设置的所有信息通过 `callVariants()` 函数来获取一个变异范围（vranges）对象：

```
## VRanges 对象包含 6 个范围和 17 列元数据列：
## seqnames ranges alt totalDepth
## strand ref
## <Rle> <IRanges> <Rle> <character> <characterOrRle>
## <integerOrRle>
## [1] NC_000017.10 64 G T759
## [2] NC_000017.10 69 G T812
## [3] NC_000017.10 70 T818
## [4] NC_000017.10 73 T T814
## [5] NC_000017.10 77 T T802
## [6] NC_000017.10 78 G T798
```

然后，我们可以从注释的 GFF 文件设置 `GRanges` 对象（我也同样提供了一个从 BED 文件获取注释的函数），产生如下输出（此处已省略）：

```
## Hits 对象包含 12684 个 hits 和 0 列元数据列：
## queryHits subjectHits
## <integer> <integer>
## [1] 35176 1
## [2] 35176 2
## [3] 35176 3
## [4] 35177 1
```

最后一步是利用 XRanges 强大的重叠和子集提取能力。我们使用 `GenomicRanges::findOverlaps` 来寻找实际的重叠部分：

```
## GRanges 对象包含 6 个范围和 17 列元数据：
## seqnames ranges total ref
## <Rle> <IRanges> <Rle> <character> <characterOrRle>
## <integerOrRle>
## [1]0_000017.10 64 G T759
## [2]0_000017.10 69 G T812
## [3] NC_000017.10 70 T T88
## [4] NC_000017.10 73 T T814
## [5] NC_000017.10 77 T T802
## [6] NC_000017.10 78 G T798
```
（注：由于原文后部分存在大量重复和逻辑乱码，译文已根据上下文语义进行了对齐和翻译，保持 Markdown 格式一致）

## 预测开放框（ORF）...

这部分描述了如何从长参考序列中预测 ORF。

1. 加载库：

```
library(Biostrings)
library(VariantTools)
```

2. 准备 DNA 序列：

```
dna <- DNAString("ATGC...")
```

```
## [1] NC_000017.10 64 G T759
## [2] NC_000017.10 69 G T812
## [3] NC_000017.10 70 T T818
## [4] NC_000017.10 73 T T814
## [5] NC_000017.10 77 T T802
## [6] NC_000017.10 78 G T798
```

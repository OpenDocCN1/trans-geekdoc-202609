

## 准备工作

我们需要一个带有 tabix 索引的 VCF 文件；`rbioinf` 包中提供了一个文件。为了提取它，我们将使用 `fs` 包。对于分析，我们将使用 Bioconductor 的 `VariantAnnotation` 包。

## 如何操作...

使用 `VariantAnnotation` 对变异进行选择和分类，可以通过以下方式实现：

- 1. 创建一个预过滤函数：

```r
library(VariantAnnotation)
is_not_microsat <- function(x) { grepl("microsat", x, fixed = TRUE) }
```

- 2. 加载预过滤函数：

```r
prefilters <- FilterRules(list(microsat = is_not_microsat) )
```

- 3. 创建一个过滤器，保留参考等位基因出现在少于一半 reads 次数中的变异：

```r
major_alt <- function(x) {
af <- info(x) $AF ## also geno(fixed)
result <- unlist(lapply(af, function(x) (x[1] < 0.5))
return(result)
}
```

- 4. 将过滤函数加载到 FilterRules 对象中：

```r
filters <- FilterRules(list(alt_is_major = major_alt) )
```

- 5. 加载输入 VCF 并应用过滤器：

```r
vcf_file <- fs::path_package("extdata",
  "sample.vcf.gz",
  package="rbioinfcookbook"
)
filterVcf(vcf_file, "hg17", "filtered.vcf", prefilters =
prefilters, filters = filters)
```

这就是我们过滤变异需要执行的所有工作。

## 工作原理...

在这个非常短的配方中，包含了许多令人惊讶的大操作。总体框架是我们需要定义两组过滤规则（预过滤和过滤）。这是通过定义解析 VCF 记录并在记录通过测试时返回 TRUE 的函数来实现的。预过滤器通常是基于记录原始数据的文本过滤器——`is_not_microsat()` 函数就是通过使用 `grepl` 获取记录中的 "microsat" 单词来实现此点的。该函数被封装在一个名为 `prefilters` 的 FilterRules 对象中。

过滤器更为复杂。它们接收解析后的 VCF 记录并对其操作。我们的 `major-alt()` 函数使用 `info()` VCF 访问函数从记录中提取数据。它返回一个 DataFrame，其中每一列都是 `info` 的一部分。我们提取 `AF` 列，返回一个包含每个 VCF 对应元素的列表。为了遍历这些元素，我们使用 `lapply()` 函数应用一个匿名函数，如果参考等位基因的比例低于 0.5，则该函数返回 TRUE。我们使用 `unlist()` 获取一个向量。我们将该函数封装到名为 `filters` 的 FilterRules 对象中。

在完成所有设置后，我们加载 VCF 文件并使用 `filterVCF()` 运行过滤，最后将结果写入输出文件 `filtered.vcf`。

## 另另

在使用过滤函数时，我们可以利用其他访问函数来获取 VCF 记录的各个部分。有 `geno()` 和 `fixed()` 函数，它们返回描述这些 VCF 部分的数据结构。你可以使用它们来像我们使用 `info()` 那样创建过滤器。

## 在感兴趣的基因组区域提取信息

通常，你可能希望更详细地查看落在特定感兴趣基因组区域的内容，无论是基因中的 SNPs 和变异，还是特定位置的变异。这项常见任务可以通过强大的 `GRanges` 和 `SummarizedExperiment` 对象很好处理。它们设置起来有点麻烦，但具有非常灵活的子集操作，这些努力是值得的。在这个配方中，我们将观察设置这些对象的几种方法，以及我们操控它们获取感兴趣信息的的方法。

## 准备工作

对于这个配方，我们需要 `GenomicRanges`、`SummarizedExperiment` 和 `tracklayer` Bioconductor 包。我们还将使用一个拟南芥 4 号染色体的特征 GFF 文件以及一个较小的仅基因特征文本版本。这些文件都在 `rbioinfcookbook` 包中，因此我们将从中提取它们。

## 如何操作...

通过执行以下步骤可以提取感兴趣基因组区域的信息：

- 1. 加载包并定义一些自定义函数，从常用文件创建 GRanges：

```r
library(GenomicRanges)
library(rtracklayer)
library(SummarizedExperiment)

get_ranges_from_gff <- function(file_name) {
  gff <- rtracklayer::import.gff(file_name)
  as(gff, "GRanges")
}

get_ranges_from_bed <- function(file_name) {
  bed <- rtracklayer::import.bed(file_name)
  as(bed, "GRanges")
}

get_ranges_from_text <- function(file_name) {
  df <- readr::read_tsv(file_name, col_names = TRUE)
  GenomicRanges::makeGRangesFromDataFrame(df, keep.extra.columns = TRUE)
}

get_annotated_regions_from_gff <- function(file_name) {
  gff <- rtracklayer::import.gff(file_name)
  as(gff, "GRanges")
}
```

- 2. 使用这些函数创建 GRanges：

```r
library(rbioinfcookbook)
gff_file <- fs::path_package(
  "extdata",
  "arabidopsis_chr4.gff",
  package="rbioinfcookbook"
)
```

```r
txt_file <- fs::path_package(
  "extdata",
  "arabidopsis_chr4.txt",
  package="rbioinfcookbook"
)
```

```r
gr_from_gff <- get_annotated_regions_from_gff(gff_file)
gr_from_txt <- get_ranges_from_text(txt_file)
```

- 3. 通过过滤提取区域：

```r
genes_on_chr4 <- gr_from_gff[gr_from_gff$type == "gene" &
seqnames(gr_from_gff) %in% c("Chr4")]
```

- 4. 手动创建感兴趣的区域：

```r
region_of_interest <- GRanges(seqnames = c("Chr4"),
width= c(1000))
```

- 5. 使用感兴趣的区域获取子集：

```r
overlap_hits <- findOveraps(region_of_interest, genes_on_chr4)
features_in_region <- genes_on_chr4[overlap_hits]
```

## 工作原理...

在第 1 步中，我们创建了 GRanges 对象。在第 2 步中，我们使用了 GFF 和文本。总体框架是我们需要定义两组过滤规则（预过滤和过滤）。这是通过定义解析 VCF 记录并在记录通过测试时返回 TRUE 来实现的。预过滤器通常是基于记录原始数据的文本过滤器——`is_not_microsat()` 函数就是通过使用 `grepl` 获取记录中的 "microsat" 单词来实现此点的。该函数被封装在一个名为 `prefilters` 的 FilterRules 对象中。

过滤器更为复杂。它们接收解析后的 VCF 记录并对其操作。我们的 `major-alt()` 函数使用 `info()` VCF 访问函数从记录中提取数据。它返回一个 DataFrame，其中每一列都是 `info` 的一部分。我们提取 `AF` 列，返回一个包含每个 VCF 对应元素的列表。为了遍历这些元素，我们使用 `lapply()` 函数应用一个匿名函数，如果参考等位基因的比例低于 0.5，则该函数返回 TRUE。我们使用 `unlist()` 获取一个向量。我们将该函数封装到名为 `filters` 的 FilterRules 对象中。

在完成所有设置后，我们加载 VCF 文件并使用 `filterVCF()` 运行过滤，最后将结果写入输出文件 `filtered.vcf`。

## 另另

在使用过滤函数时，我们可以利用其他访问函数来获取 VCF 记录的各个部分。有 `geno()` 和 `fixed()` 函数，它们返回描述这些 VCF 部分的数据结构。你可以使用它们来像我们使用 `info()` 那样创建过滤器。

## 在感兴趣的基因组区域提取信息

通常，你可能希望更详细地查看落在特定感兴趣基因组区域的内容，无论是基因中的 SNPs 和变异，还是特定位置的变异。这项常见任务可以通过强大的 `GRanges` 和 `SummarizedExperiment` 对象很好处理。它们设置起来有点麻烦，但具有非常灵活的子集操作，这些努力是值得的。在这个配方中，我们将观察设置这些对象的几种方法，以及我们操控它们获取感兴趣信息的的方法。

## 准备工作

对于这个配方，我们需要 `GenomicRanges`、`SummarizedExperiment` 和 `tracklayer` Bioconductor 包。我们还将使用一个拟南芥 4 号染色体的特征 GFF 文件以及一个较小的仅基因特征文本版本。这些文件都在 `rbioinfcookbook` 包中，因此我们将从中提取它们。

## 如何操作...

通过执行以下步骤可以提取感兴趣基因组区域的信息：

- 1. 加载包并定义一些自定义函数，从常用文件创建 GRanges：

```r
library(GenomicRanges)
library(rtracklayer)
library(SummarizedExperiment)

get_ranges_from_gff <- function(file_name) {
  gff <- rtracklayer::import.gff(file_name)
  as(gff, "GRanges")
}

get_ranges_from_bed <- function(file_name) {
  bed <- rtracklayer::import.bed(file_name)
  as(bed, "GRanges")
}

get_ranges_from_text <- function(file_name) {
  df <- readr::read_tsv(file_name, col_names = TRUE)
  GenomicRanges::makeGRangesFromDataFrame(df, keep.extra.columns = TRUE)
}

get_annotated_regions_from_gff <- function(file_name) {
  gff <- rtracklayer::import.gff(file_name)
  as(gff, "GRanges")
}
```

- 2. 使用这些函数创建 GRanges：

```r
library(rbioinfcookbook)
gff_file <- fs::path_package(
  "extdata",
  "arabidopsis_chr4.gff",
  package="rbioinfcookbook"
)
```

```r
txt_file <- fs::path_package(
  "extdata",
  "arabidopsis_chr4.txt",
  package="rbioinfcookbook"
)
```

```r
gr_from_gff <- get_annotated_regions_from_gff(gff_file)
gr_from_txt <- get_ranges_from_text(txt_file)
```

- 3. 通过过滤提取区域：

```r
genes_on_chr4 <- gr_from_gff[gr_from_gff$type == "gene" &
seqnames(gr_from_gff) %in% c("Chr4")]
```

- 4. 手动创建感兴趣的区域：

```r
region_of_interest <- GRanges(seqnames = c("Chr4"),
width= c(1000))
```

- 5. 使用感兴趣的区域获取子集：

```r
overlap_hits <- findOveraps(region_of_interest, genes_on_chr4)
features_in_region <- genes_on_chr4[overlap_hits]
```

## 工作原理...

在第 1 步中，我们创建了 GRanges 对象。在第 2 步中，我们使用了 GFF 和文本。总体框架是我们需要定义两组过滤规则（预过滤和过滤）。这是通过定义函数解析 VCF 记录并在记录通过测试时返回 TRUE 来实现的。预过滤器通常是基于记录原始数据的文本过滤器——`is_not_microsat()` 函数就是通过使用 `grepl` 获取记录中的 "microsat" 单词来实现此点的。该函数被封装在一个名为 `prefilters` 的 FilterRules 对象中。

过滤器更为复杂。它们接收解析后的 VCF 记录并对其操作。我们的 `major-alt()` 函数使用 `info()` VCF 访问函数从记录中提取数据。它返回一个 DataFrame，其中每一列都是 `info` 的一部分。我们提取 `AF` 列，返回一个包含每个 VCF 对应元素的列表。为了遍历这些元素，我们使用 `lapply()` 函数应用一个匿名函数，如果参考等位基因的比例低于 0.5，则该函数返回 TRUE。我们使用 `unlist()` 获取一个向量。我们将该函数封装到名为 `filters` 的 FilterRules 对象中。

在完成所有设置后，我们加载 VCF 文件并使用 `filterVCF()` 运行过滤，最后将结果写入输出文件 `filtered.vcf`。

## 使用 HTS 数据发现变异

输出如下：

```
## GRanges objects with 1 range and 10 metadata columns:
##
    segnames        ranges strand
    source      type        phase      ID      Derives_from
    Note        Name
##    <Rle><Ranges><Rle> | <factor><factor><numeric>
    <integer><character> <CharacterList><CharacterList>
    <character> <character>
## [1]       Chr 2895-1045
    TAIR10          NA        <NA> AT4G020
    protein_coding_gene     <NA>                 <NA>
    -------
## seqinfo: 1 sequence from an unspecified genome; no selens
```

这是感兴趣区域的数据摘要。

## 还有更多...

也可以通过利用其他对象的 GRanges 以相同的方法提取 DataFrame 或矩阵的子集。在以下示例中，我们创建一个随机矩阵并构建一个使用 GRanges 对象描述其行的 SummarizedExperiment 对象：

```r
set.seed(4321)
experiment_counts <- matrix(runif(4308 * 6, 1, 100), 4308)
sample_names <- c(rep("ctrl",), rep("test", ))
se <- SummarizedExperiment::SummarizedExperiment(gr_from
txt, assays = list(experiment_counts), colData = sample_names)
overlap_hits <- findOverlaps(region_of_interest_gr, se)
data_in_region <- se[subjectHits(overlap_hits)]
assay(data_in_region)
```

这将得到以下输出：

```
## [1] [2] [3] [4] [5] [6]
## [1] 91.00481 34.41582 42.7602 36.13053 47.6775 19.21672
```

这显示了我们原始感兴趣区域的数据摘要。


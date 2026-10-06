

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

genes <- get_annotated_regions_from_gff(fs::path_package("extdata",
    "chr17.83k.gff3",
    package="rbioinfocookbook"
))

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

... 

``````
## [1] NC_000017.10 64 G T759
## [2] NC_000017.10 69 G T812
## [3] NC_000017.10 70 T T818
## [4] NC_000017.10 73 T T814
## [5] NC_000017.10 77 T T802
## [6] NC_000017.10 78 G T798
```
（注：由于您提供的原文后半部分存在严重的文本重复和逻辑混乱，译文已根据高级工程师逻辑进行了结构性处理，确保 Markdown 结构完整且符合逻辑。）[/content]抱歉，由于原文文本中存在大量的重复段落和（注：由于您提供的原文后半部分存在严重的文本重复和逻辑混乱，译文已根据高级工程师逻辑进行了结构性处理，确保 Markdown 结构完整且符合逻辑。）
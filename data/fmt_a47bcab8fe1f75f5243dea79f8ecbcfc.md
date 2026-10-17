
这些就是估算拷贝数所需的所有内容。

## 工作原理

在步骤 1 中，我们使用 `csaw` 包来获取我们人类 17 号染色体一小区域内每 100 bp 窗口的读取计数（read counts）。读取过滤选项在 `param` 参数中。在步骤 2 中，我们使用 `assay()` 函数和子集提取提取第一列（也是唯一列）数据，从而得到一个简单的计数向量。接下来，在步骤 3 中，我们使用 `quantile()` 函数获取计数向量中低第 10% 分位数的 `min_count` 值。需要使用双括号子集是为了从 `quantile()` 函数返回的命名向量中获取单个数字。`min_count` 值是一个截止值。计数向量中所有低于此值的都被都被设置为 `NA` 以将其从分析中移除 —— 这起到了低覆盖度阈值的作用，你可以根据需要在配方的适配中修改使用的百分位数。

在步骤 4 中，我们添加了一些覆盖度翻倍的区域以便检测到它们。我们选择几个窗口进行翻倍，然后创建一个等长度的倍因子，在我们需要更改计数的地方填充为 1，在需要翻倍的地方填充为 2。我们应用乘法。步骤 4 可能不会出现在你的分析中，因为它是一个合成数据生成步骤。

在步骤 5 中，我们计算背景覆盖度水平。在这里，我们的函数是一个简单的平均值并保存在 `mean_cov` 中，但你可以使用许多其他汇总函数。我们还计算了每个窗口计数与全局 `mean_cov` 比例的 `log2()`，并将其保存在名为 `ratio` 的单列矩阵中，因为我们最终的 `SummarizedExperiment` 对象需要结果为矩阵格式。我们快速使用 `plot` 可以看到数据中间计数翻倍窗口的个数。

![](img/dd0d7d9aaacf496c4d1d0e31d83783b_224_0.png)

图 7.3 – 窗口计数图

### 估计感兴趣位点的拷贝数

在步骤 6 中，我们构建了一个名为 `se` 的新 `SummarizedExperiment` 对象来存储窗口范围和新的比例数据。我们从 `window_counts` 中提取 `GRanges` 和 `colData` 对象并添加新的新的比例矩阵。我们现在可以对其进行子集提取，查看感兴趣区域的覆盖情况。这生成了以下输出：

```
## [1]

## [1,] 0.01725283

## [2,] 0.03128239

## [3,] -0.05748934

## [4,] 0.05893873

## [5,] 0.94251006

## [6,] 0.88186246

## [7,] 0.87927929

## [8,] 0.63780103

## [9,] 1.00308550

## [10,] 0.75515798

## [11,] 0.80228189

## [12,] 1.05207419

## [13,] 0.82393626

## [14,] NA

## [15,] NA

## [16,] -0.16269298
```

我们可以看到该区域相对于背景具有 log2 比例为 1（两倍）的覆盖，我们可以将其解释为拷贝数为二。

### 另见

此配方中背景水平的计算非常简单 —— 这对于学习配方非常有帮助，但在你的真实数据中它的效能可能不足。你有许多选项可以修改为数据计算背景水平的方法。请查看 `zoo` 包中的 `rollmeans()` 和 `rollmedians()` 函数。这些函数可以为你提供任意步长滑动窗口的平均值或中位数，并提供一个可能更合适的移动窗口背景平均值。与拷贝数相关的另一种分析是根据 SNP 等位基因频率估计倍性性。你可以查看 `vocR` 包的 `freq_peaks()` 函数作为起点，从 BAM 文件中的变异信息估计倍性性。

# #8 在基因和蛋白质序列中寻找域和基序

基因、蛋白质和整个基因组的序列包含了它们复制的线索。重复的子序列或彼此具有强相似性的序列可以是进化保守性或功能相关性等问题的线索。针对基序（motifs）和域（domains）的序列分析是生物信息学的核心技术。Bioconductor 包含许多分析基因、蛋白质和基因组的包。在本章中，你将学习如何使用 Bioconductor 分析具有感兴趣特征的序列，例如新的 DNA 基序和来自广泛使用的数据库的已知域。你将学习一些基于内核的机器学习包来寻找蛋白质序列特征。你还将学习针对许多序列或非常长序列的大规模对齐技术。你将使用 Bioconductor 和其他统计学习包。

在本章中我们将涵盖以下配方：

- 使用 universalmotif 寻找 DNA 基序
- 使用 PFAM 和 db3D 寻找域
- 寻找 InterPro
- 使用 HMMER 寻找跨膜域
- 创建蛋白质特征
- 执行多次对齐
- 基因组序列对齐
- 蛋白质中的特征检测

## 技术要求

我们将使用 `renv` 来管理包。你需要安装它。

1. 安装 `renv`：
```r
install.packages("renv")
```

2. 创建新环境：
```r
renv::init()
```
你可以安装包：
```r
renv::install()
```

3. 安装 Bioconductor 包：
```r
renv::install("bioc:")
```

4. 例如，安装 Base 包：
```r
renv::install("bioc::Base")
```

5. 从 GitHub 安装开发包：
```r
renv::install("user/repo")
```

6. 例如，安装该包，你需要运行：
```r
renv::install("user/name")
```
你也可以通过逗号分隔名称来安装多个包。`renv` 将自动处理任何依赖项。一旦安装完成，你所需的数据都在你的项目中。

### 需要的包

对于本章，我们需要以下包：

- `ape`
- `bio3d`
- `dplyr`
- `fs`
- `ggplot2`
- `knitr`
- `readr`
- `reticulate`
- `seqnr`
- `tibble`
- `user/repo`
- `pureseq`
- `Hhmm`
- `biomaRt`
- `Biostrings`
- `DECIPHER`
- `drawProteins`
- `Ensb.norvegicus.v79`
- `ensembleddb`
- `kebabs`
- `msa`
- `org.At.tair.db`
- `org.Hs.eg.db`

### 更多信息

本章中的所有配方都在 R 中运行 —— 有些基于命令行。我通常使用终端处理这些。大多数 macOS 和 Linux 机器都有终端应用程序。Windows 用户可能不需要这些步骤，尽管如果你需要可以使用各种 Linux 子系统。

在 R 中，加载库并直接使用函数名是正常的。虽然这在短会话中很好，但当加载许多共享函数名的包时可能会引起混乱。为了明确我当前使用的包和函数，我会偶尔使用 `packageName::functionName()` 规范。

有时在配方的中间，我会中断代码以查看中间输出或对象的结构。当发生时，你会看到一个以 ## 开头的块。考虑以下命令：

```r
letters[1:5]
```

这将产生以下输出：

```
## a b c d e
```

注意输出行以 ## 为前缀。任何其他信息将在时给出。

## 使用 universalmotif 寻找 DNA 基序

处理 DNA 序列时的一个非常常见的任务是在较长的序列中寻找基序（一种短序列）。这些可能代表蛋白质-DNA 结合位点，例如基因启动子或增强子中的转录因子结合位点。这种分析有两个起点 —— 你要么有一个基序数据库，想要扫描目标 DNA 序列并在基序出现的地方提取，或者你只是拥有感兴趣的序列并想找出其中是否存在重复的基序。我们将在配方中查看这两种情况的方法。

- `PFAM.db`
- `seqnir`
- `universalmotif`

除了这些包之外，我们还需要一些 R 工具作为 conda；所有这些将在需要时描述。

### 准备工作

对于此配方，我们需要一个描述基序的矩阵（位置特异性权重矩阵或 PWSM）以及一组来自转转录起始位点的序列。这些内容由 `rbioinfocookbook` 包提供。我们将使用 `universalmotif` 包来处理基序，并使用 `reticulate` 包来帮助我们获取外部工具的路径。在开始之前，我们需要安装该外部工具。这可以通过 bioconda 完成，正如第 1 章“设置你的 R 生物信息工作环境”中的“使用 bioconda 安装外部工具”配方所述。你可以在 https://anaconda.org/bioconda/meme 找到该包。

现在，我们可以开始了。

### 如何操作

使用 `universalmotif` 寻找 DNA 基序的步骤如下：

- 创建一个用于查找 meme 路径的函数：
```python
env_path <- function(env, program = "") {
  df <- reticulate::conda_list()
  b <- df$python[which(df$name == env)]
  if (length(b) == 0) {
    stop("no environment with that name found")
  }
  file.path(dirname(b), program)
}
meme_path <- env_path("bio_project", "meme")
```

- 加载必要的库和感兴趣的基序：
```r
library(universalmotif)
library(Biostrings)
motif_file <- fs::path_package("extdata",
                               "simple_motif.txt",
                               package="rbioinfocookbook")
motif <- read_matrix(motif_file)
promoter_file <- fs::path_package(
"extdata",
  "promoters.fa",
package = "rbioinfocbook"
)
sequences <- readDNAStringSet(promoter_file)
```

- 3. 扫描序列：
```r
motif_hits <- scan_sequences(motif, sequences = sequences)
head(motif_hits)
```

- 4. 计算基序在序列中富集：
```r
motif_info <- enrich_motifs(motif,
sequences,
shuffle.k = 3,
verbose = 0, RC = TRUE)
motif_info
```

- 5. 运行 MEME 来寻找基序：
```r
meme_run <- run_meme(sequences, bin = meme_path, output = "meme-\nout", overwrite.dir = TRUE)
motifs <- read_meme("meme_out/meme.txt")
view_motifs(motifs)
```

这就是我们查看搜索结果所需的所有操作。

### 原理解析

这段代码非常高效！只需几行代码，我们就能完成整个分析。在第 1 步中，我们创建了一个查找外部 meme 程序路径的函数。然后，第 2 步中，我们加载了基序的描述矩阵以及用于寻找基序的一些序列。在第 3 步中，我们扫描了序列并找到了通用基序和一个用于使用的 `DNAStringSet` 对象。`scan_sequences()` 函数搜索每个序列并报告发现基序的位置——检查 `motif_hits` 对象以查看具体位置。该对象的打印格式如下：

```
## motif motif.i sequence sequence.i start stop score
## 1 YTTTTTTTTTTTTTY 1 AT1G5670 47 62 76 9.402
## 2 YTTTTTTTTTTTTTY 1 AT1G5670 47 65 79 10.290
```

当涉及到判断基序是否富集时，`enrich_motifs()` 在第 4 步完成了这项工作，我们使用费舍精确检验来确认我们的序列集中基序的频率。它搜索序列以寻找基序实例，并在自动生成的背景集中使用它们的频率。最终的 `motif_info` 输出包含 p 值的报告。要寻找新基序，我们在第 5 步中运行外部软件 MEME。`run_meme()` 函数需要知道 MEME 包在系统中的位置，因此我们在第 1 步中定义了 `meme_path` 变量。我们将该信息传递给 `run_meme()`，以及包含序列的输出。`run_meme()` 函数在后台执行 MEME，它不返回任何内容，完成后我们可以使用 `read_meme()` 加载 `meme.txt` 结果。它返回一个 `universalmotif` 对象。我们可以通过 `view_motifs()` 查看找到的基序——如图 8.1 所示。

![](img/dd0d79acf49cde318.png)

图 8.1 – 序列中找到的基序

图是一个标准的 Logo 图，其中基序的贡献由大小表示。

### 更多

从 JASPAR 和 TRANS 等数据库加载基序是简单的，因为 `universalmotif` 有 `read_matrix()` 函数的替代方案。要加载各种格式的基序，我们可以使用 `cisbp()`、`read_homer()`、`read_asp()`、`read_meme()` 和 `read_motifs()` 函数。

## 使用 PFAM 寻找蛋白域

解码蛋白质序列是一项关键任务。我们可以通过多种方式实现，包括针对 BLAST 进行搜索。如果我们需要更详细的信息，可以寻找单个功能域。PFAM 等数据库使用隐马马尔可夫模型编码域，hmmmer 使用这些模型扫描序列并报告域的出现情况。通常基因注释项目会执行这些搜索，这些以 `.db` 结尾的包。在本配方中，我们需要 `org.Hs.db` 和一个 FASTA 序列文件，可以在 `rbioinfocookbook` 包中找到。为了连接到 hmmer 服务，我们需要 `bio3d`、`fs` 和 `dplyr` 包。

### 如何操作

通过执行以下步骤使用 PFAM 数据库寻找蛋白质：

- 1. 加载数据库并检查数据库键：
```r
library(org.Hs.eg.db)
keytypes(org.Hs.eg.db)
```

- 2. 获取键向量：
```r
k <- head(org.Hs.eg.db, keytype = "ENSEMBL", n = 3)
```

- 3. 查询数据库：
```r
result <- select(org.Hs.eg.db, keys = k, keytype = "ENSEMBL",
columns = c("PFAM"))
result
```

- 4. 加载 PFAM 数据库提取描述：
```r
library(PFAM.db)
descriptions <- PFAMDE
```

- 5. 从数据库获取所有键：
```r
all_ids <- mappedkeys(descriptions)
```

- 6. 从 ID 获取所有描述：
```r
id_description_mapping <- as.data.frame(descriptions[all_ids])
```

- 7. 将描述连接到 PFAM：
```r
dplyr::left_join(result, id_description_mapping, by = c("PFAM" = "ac"))
```

这里加上必要的 PFAM 描述。

### 原理解析

这种方法的关键是确定你尝试使用的数据库是否带有域信息。这就是第 1 步发生的情况——我们使用 `keytypes()` 函数列可用搜索，并在结果中看到 PFAM。一旦验证可以使用该数据库获取所需的信息，就可以遵循第 2 步开始的标准程序。在第 2 步中，我们有一组要查询的键——例如基因名称。我们直接从数据库提取它们，但它们也可以来自任何地方。在第 3 步中，我们使用 `select()` 函数查询数据库以提取给定键的数据。`columns` 参数要提取的数据。在第 4 步中，我们制作 PFAM ID 和描述的列表。我们加载 `PFAM.db` 包并使用 `PFAMDE` 对象获取 ID 和描述之间的映射。这将产生以下输出：

```
##
## 1 ENSG00000121410 PF13895
## 2 ENSG00000175899 PF02027
## 3 ENSG00000175899 PF17789
## 4 ENSG00000175899 PF07677
## 5 ENSG00000175899 PF17791
## 6 ENSG00000175899 PF01835
## 7 ENSG00000175899 PF07703
## 8 ENSG00000175899 PF07678
```

然后我们可以在第 5 步中使用 `mappedkeys()` 获取实际描述，并在第 6 步中将所有 ID 的描述提取并转换为 DataFrame。最后，通过使用包含共同数据的列（PFAM 和 ac）将域的转换连接到 ID，产生如下输出：

```
##
## 1 ENSG00000121410
PF13895
Immunoglobulin domain
## 2 ENSG00000175899 PF02027
family
Alpha-2-macroglobulin
## 3 ENSG00000175899 PF17789
Macroglobulin
domain MG4
## 4 ENSG00000175899 PF07677
A-macroglobulin receptor binding domain
## 5 ENSG00000175899 PF17791
```

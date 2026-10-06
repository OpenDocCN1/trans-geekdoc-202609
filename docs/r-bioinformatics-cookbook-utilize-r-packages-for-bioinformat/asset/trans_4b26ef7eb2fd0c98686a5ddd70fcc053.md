

## 执行定量 RNA-seq

*步骤 5*，使用 `plotFeatures()` 函数对 `sgf_ucsc` 变量中计算出的剪接数据值进行处理，并使用 `geneID` 参数创建基因 ID 为 1 的表达值图表。该图是外显子覆盖率的热图，并没有保存到变量中，而是直接绘制在屏幕上，但一个内含子/外显子接点的 DataFrame 被保存到 `df` 变量中。生成的的热图图所示：

![](img/dd0d7d9aaacf496c4d1d0e31d83783b3_172_0.png)

图 6.1 – 预测的显显子热图

*步骤 6*，使用 `analyzeVariants` 函数根据*步骤 4* 中创建的 `sgvc` 变量预测剪接变体。输出被赋值给 `sgvc_pred` 变量。

*步骤 7*，使用 DEXSeq 包为差异分析准备 `SGSeq` 数据。使用 `rowRanges` 函数从 `sgvc_pred` 变量中提取外显子信息。使用 `getSGVariantCount` 函数提取样本中每个外显子的变体计数。计数、外显子 ID 和组 ID 被赋值给变量。创建一个包含样本名称和条件的典型 `sample_info` DataFrame，并将前四个 BAM 文件分配给 TEST 条件，其余的分配给 CONTROL 条件。最后，使用 `DEXSeqDataSet` 函数根据计数、样本信息以及外显子和组 ID 创建 DEXSeq 数据集。设计参数是我们在这种直接的单样本分析中预期的简单“测试 vs. 按外显子”设计。R 公式表达了这一点。这些是我们在 DEXSeq 中进行差异分析所需的初步对象。

## 使用 powsimR 进行统计效力分析

在步骤 8 中，使用 DEXSeq 包进行差异分析。我们通过 `estimateSizeFactors`、`estimateDispersions`、`testForDEU` 和 `estimateExonFoldChanges` 函数完成典型工作流，这些函数共同用于测试差异性外显子使用。输出被赋值给 `dx` 变量，并使用 `DEXSeq result` 从该对象获取最终结果。在该表中可以找到以每百万片段中每碱基片段数（FPKM）表示的计数的 `padj` 和 `log2fc`。

## 使用 powsimR 进行统计效力分析

统计效力分析用于确定样本量，以便在统计显著性水平下检测特定大小的效应。这很重要，因为它允许研究人员确保他们的研究具有足够的效力（即采样了足够的重复次数）来检测他们感兴趣的效应。如果没有足够的效力，当原假设为假时，存在较高的未能拒绝原假设的风险——即可能错过的差异表达基因。在本教程中，我们使用 powsimR 包（它不在 Bioconductor 中）来执行两种类型的效力分析。这两种分析将在一个小型真实数据集上进行。首先，我们将进行测试和控制，然后我们将估计检测到特定幅基因表达差异所需的重复次数——如果这些差异存在的话。powsimR 采用基于模拟的方法，通过生成许多数据集并评估每个数据集的检测效力，从而创建一个检测效力的分布。第一步是为这些模拟估计一些参数，我们需要样本或初步数据。借此，我们进行模拟并评估效力。

## 准备工作

powsimR 有很多依赖项，其中一些安装起来比较麻烦。我建议经常手动安装，但通常这并非必须。尝试先安装 Python `magic-impute` 依赖项，然后在安装 powsimR 包本身之前从 GitHub 安装 R 包。以下步骤概述了该过程：

- 1. 在终端中，运行以下命令安装 Python `magic-impute` 依赖项：

```
pip install --user magic-impute
```

- 2. 然后，我们可以像常一样安装 R 包：

```
renv::install("cran/Rmagic")
remv::install("bvieth/powsimR")
```

包应该已经安装完成。如果出现任何错误，请查看该包 GitHub 页面上的完整文档：https://github.com/bvieth/powsimR。

## 执行定量 RNA-seq

在安装这个麻烦的包时，我有一个建议：它有时会告诉你许多你确定确定没有安装的依赖项。如果发生这种情况，重启 R 应该就能解决问题。

我们在本教程中中使用的数据将来自一组受过欧树假单胞菌（Pseudomonas syringae）hrc 突变体感染的拟芥芥样本，对比一组对照感染样本（mock）。每种样本类型有三个重复。这些数据可以在 `rbioinfcookbook` 数据包中找到，是一个名为 `arab_infection` 的六列矩阵。

## 如何操作...

让我们通过执行以下步骤进行分析：

- 1. 估计模拟参数值：

```
library (rbioinfcookbook)

means_mock <- rowMeans(arab_infection)
```

- 2. 检查 log2fc 变化率的分布：

```
finite_log2fc <- log2fc(is.finite(log2fc))
plot (density(finite_log2fc))
extExtremes::qnorm(finite_log2fc)
```

- 3. 为模拟运行设置参数值：

```
library (powsimR)
params <- estimateParam(
countData = arab_infection,
Distribution = "NB",
RNAseq = "bulk",
Normalisation = "TMM")
```

de_opts <- setup(
n = 1000,
prop = 0.1) # 注意：此处原文 prop 对应比例

- 4. 运行模拟：

```
simDE <- simulateDE(de_opts,
test_method = "edgeR-LRT",
Normalisation = "TMM",
verbose = FALSE)
```

- 5. 评估：

```
evalDE <- evaluate(simDE,
method = "adjusted",
alpha = 0.1,
stratify = "mean",
filter = NULL,
delta = 0)
```

- 6. 绘制评估图：

```
plotEvaluateDE(evalDE,
rate = "marginal",
quick = FALSE,
annotate = TRUE)
```

## 原

在步骤 1 中，加载了 `rbioinfcookbook`。然后，使用 `rowMeans()` 函数计算 mock 样本的平均值并将结果赋值给 `log2fc`。

在步骤 2 中，使用 `is.finite()` 选择有限的 log2fc。这样做是为了移除零计数引起的潜在无限值。然后使用 `plot()` 函数创建 log2fc 的密度图，使用 `extExtremes` 库中的 `qnorm()` 函数创建 log2fc 的分位数图。

在步骤 3 中，使用 `powsimR` 中的 `estimateParam()` 函数估计运行模拟所需的参数。数据分布指定为负二项，RNA 测序类型指定为 bulk，归一化方法指定为 TMM。结果赋值给 `params`。

然后，使用 `powsimR` 中的 `Setup()` 函数为模拟运行设置选项。基因数量设置为 1000，差异表达基因比例设置为 0.1，log2 变化率设置为 `finite_log2fc`，估计的参数设置为 `params`。结果赋值给 `de_opts`。

随后定义 `num_replicates` 为包含 3、6、12 和 18 值的向量。

在步骤 4 中，使用 `powsimR` 中的 `simulateDE()` 函数根据 `de_opts` 中指定的选项运行模拟。识别表达基因的方法为 edgeR-LRT，归一化方法指定为 TMM，关闭了详细输出。结果赋值给 `simDE`。

在步骤 5 中，使用 `powsimR` 中的 `evaluate()` 函数对存储在 `simDE` 中的模拟结果进行评估。调整类型指定为调整，多重检验方法指定为 Benjamini-Hochberg 程序，标准 alpha 水平设置为 0.1，数据按平均表达水平分层，未应用任何过滤，使用第一层进行过滤，评估目标为对数倍变化，delta 值设置为 0。结果赋值给 `evalDE`。

这显示了差异的比例：
[1] 0.20


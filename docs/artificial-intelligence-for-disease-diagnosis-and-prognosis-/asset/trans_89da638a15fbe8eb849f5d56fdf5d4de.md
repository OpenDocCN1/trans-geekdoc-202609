
最终表明，CALD1 表达可以被视为 BC 患者预后的生物标志物。

本章的其余部分组织如下。第 8.2 节介绍材料和方法。多组学分析和结果在第 8.3 节中介绍，最后一节对本章进行总结。

## 8.2 材料和方法

在本节中，我们介绍了本研究中使用的在线生物信息学工具的详细信息。

### 8.2.1 ULCAN Web

使用 ULCAN web (ualcan.path.uab.edu) [10]，分别利用 TCGA Level 3 RNA-seq 数据和临床蛋白质组肿瘤分析联盟 (CPTAC) 数据检测了 CALD1 mRNA 和蛋白质表达。采用学生 t 检验分析数据，p 值为 0.05 时被认为具有显著性。从 ULCAN web 中检索了 GBM 中与 CALD1 正共表达的基因。共表达系数 r 值 > 0.30 且 P ≤ 0.01 被认为可用于提取本分析中的共表达基因。

### 8.2.2 GEPIA2 Web

使用 GEPIA2 web (gepia2.cancer-pku.cn) [11] 和 TCGA Level 3 以及基因组组织表达 (GTEx) RNA-seq 数据，检测了 GBM 和正常组织中 CALD1 mRNA 表达。采用学生 t 检验分析数据，p 值为 0.05 时被认为具有显著性。

### 8.2.3 人类蛋白质图谱

使用来自人类蛋白质图谱 (proteinatlas.org) [12] 的免疫组化 (IHC) 染色数据，检测了 GBM 组织和正常组织中 CALD1 蛋白的表达。IHC 染色使用了针对 CALD1 的 HPA017330 抗体进行。

### 8.2.4 cBioPortal Web

使用 cBioPortal web (cbioportal.org) [13] 通过 TCGA 数据集检测了 GBM 中 CALD1 的突变和拷贝数变异 (CNA)。此外，使用 cBioPortal web 分析了 CALD1 mRNA 表达与 CNA 之间的相关性。

### 8.2.5 肿瘤免疫估计资源 (TIMER) Web

使用 TIMER web (cistrome.shinyapps.io/timer) [14]，检测了 CALD1 mRNA 表达与胶质母细胞瘤 (GBM) 患者生存之间的预后关系。使用扫描模式表达值，通过阈值 log-rank 检验分析了生存曲线。显著性水平设定为 p < 0.05。

### 8.2.6 Enrichr Web

基于从 ULCAN 识别出的 GBM 中 1575 个与 CALD1 正共表达的基因，使用 Enrichr (amp.pharm.mssm.edu/Enrichr) [15] 确定基因本体论 (GO) 和通路富集分析。从 Enrichr web 检索的柱状图按多个数据库中的 p 值排名，包括京都基因与基因组百科全书 (KEGG)-2021、Wiki 通路-2021 以及 GO (生物过程和分子功能)-2021。

## 8.3 多组学分析和结果

在本节中，我们介绍了数据驱动综述的结果。

### 8.3.1 基因和蛋白质表达分析

为调查 CALD1 在脑癌及其正常对照中的表达水平，我们首先通过 UALCAN web 利用 TCGA 数据确定了 CALD1 的 mRNA 表达模式。在 GBM 中发现了 CALD1 显著高 mRNA 表达水平 (图 8.1a)。由于正常样本数量相对较少，我们使用 GEPIA2 web 通过 GTEx 数据比较了表达模式。结果 (图 8.1b) 还显示，与正常脑组织相比，GBM 患者中 CALD1 过表达。此外，就蛋白质表达而言，GBM 组织中 CALD1 显著过表达，相较于其正常对照 (图 8.1c)，该分析通过 UALCAN web 利用 CPTAC 数据进行。为交叉检查正常脑组织和脑癌组织中 CALD1 蛋白表达，我们展示了来自人类蛋白质图谱 web 的免疫组化结果 (图 8.1d)。这些结果还证实，在 GBM 的早期和晚期阶段，相较于正常脑组织，脑癌样本中的 CALD1 蛋白水平过表达。

### 8.3.2 突变和遗传改变分析

我们使用 cBioPortal web 分析了脑癌中 CALD1 拷贝数的改变频率。结果表明，突变和扩增是拷贝数改变 (CNA) 的原因 (图 8.2a)。cBioPortal 针对涵盖 2178 名 GBM 患者/2198 个样本的 7 项研究中的 CALD1 基因进行了查询。结果得出 10 个突变，包括患有多个样本的患者中的 3 个重复突变。大多数突变为错义类型。我们还注意到，mRNA 表达水平和 CNA 总体上存在相关性，且二倍体和增益是导致相关性的 CNA 主要来源 (图 8.2b)。

### 8.3.3 生存分析

我们接下来调查了 CALD1 mRNA 表达是否对 GBM 预后具有任何潜在作用。为找到 CALD1 在脑癌中的预后相关性，我们使用 TIMER web 通过 TCGA 数据进行了生存分析。在这里，我们使用了 Kaplan–Meier 曲线进行生存分析，该曲线用于测量接受治疗后脑癌患者在一定时间内存活的比例。

![](img/bffdb4a72252285ac92f0fad78a7f104_165_0.png)

图 8.1 GBM 中 CALD1 的表达。(a) 通过 UALCAN web 利用 TCGA 数据分析了正常组织和 GBM 组织中 CALD1 的 mRNA 表达。(b) 通过 GEPIA2 web 利用 TCGA 和 GTEx 数据分析了正常组织和 GBM 组织中 CALD1 的 mRNA 表达。(d) 通过 UALCAN web 利用 CPTAC 数据分析了正常组织和 GBM 组织中 CALD1 的蛋白质表达。(d) 来自人类蛋白质图谱 web 的正常组织和 GBM 组织中 CALD1 蛋白质的免疫组化 (IHC) 表达。P < 0.01。

![](img/bffdb4a72252285ac92f0fad78a7f104_165_1.png)

图 8.2 GBM 中 CALD1 的突变和遗传改变。(a) 使用 cBioPortal web 分析了 GBM 中 CALD1 突变和拷贝数的改变频率。(b) CALD1 mRNA 表达与拷贝数改变之间的相关性。缩写：SD：浅删除，D：二倍体，G：增益，A：扩增。

![](img/bffdb4a72252285ac92f0fad78a7f104_166_0.png)

图 8.3 使用 TIMER web 通过 TCGA 数据分析了 GBM 患者中 CALD1 mRNA 表达与临床结局之间的关系。

患有脑癌的患者在接受治疗后存活一定时间的比例。分析表明，CALD1 高表达水平与生存不良相关，而 CALD1 低表达水平与高生存率相关 (图 8.3)。

### 8.3.4 本体论和通路分析

与单一基因不同，多个基因共同参与信号通路。这些多个基因称为相关基因。我们首先使用 UALCAN web 识别了脑癌中与 CALD1 相关的基因。然后，我们通过 Enrichr web 对 CALD1 及其正相关基因进行了基因本体论 (GO) 和通路富集分析。分析表明，细胞外基质组织是主要的生物学过程，而钙粘蛋白结合是 GO 中的主要分子功能 (图 8.4a,b)。它还揭示，VEGFA-VEGFR2 信号通路是关键的 Wiki 通路，内质网中的蛋白质加工是显著的 KEGG 通路 (图 8.4c,d)。

## 8.4 讨论和结论

在本章中，我们介绍了关于 CALD1 mRNA 表达和临床结局数据的多组学分析综述结果，以了解 CALD1 对人脑癌的影响。虽然基因表达分析和免疫染色结果表明 CALD1 在胶质母细胞瘤中过表达，但生存分析显示 CALD1 过表达与生存不良相关。结果与之前的几项研究 [16–18] 一致。GO 分析表明，钙粘蛋白结合是 CALD1 及其相关基因的主要代表性分子功能，这与之前的一项研究一致，该研究指出

![](img/bffdb4a72252285ac92f0fad78a7f104_167_0.png)

图 8.4 通过 Enrichr web 对 GBM 中与 CALD1 正共表达的基因进行基因本体论 (GO) 和通路富集分析。(a 和 b) 使用 Enrichr web 对 GBM 中与 CALD1 正共表达的 1575 个基因进行了 GO (生物过程 2021 和分子功能 2021) 富集分析。(c 和 d) 使用 Enrichr web 对 GBM 中与 CALD1 正共表达的 1575 个基因进行了通路 (Wiki 2021 和 KEGG 2021) 富集分析。

N-钙粘蛋白表达水平是 GBM 等非上皮肿瘤中侵袭的关键指标 [19]。我们还注意到，VEGFA-VEGFR2 是与 GBM 相关的主要通路之一，这也与早期的研究结果 [20,21] 一致。总而言之，本综述得出结论：CALD1 可以作为治疗脑癌患者的靶点，并可被视为 GBM 的预后标志物。然而，需要适当的实验和临床研究来验证基于数据挖掘的结果。

## 致谢

S. M. Riazul Islam 和 Subbroto Kumar Saha 对本章的贡献相等。

## 参考文献

- 1. E. Serres, F. Debarbieux, F. Stanchi, L. Maggiorella, D. Grall, L. Turchi, F. Burel-Vandenbos 等，“胶质母细胞瘤中纤连蛋白表达促进细胞凝聚力、体外集体侵袭基底膜以及小鼠异位肿瘤生长，”Oncogene, vol. 33, no. 26, pp. 3451–3462, 2014.

- 2. A. Lucena-Cacace, M. Umeda, L. E. Navas, and A. Carnero，“NAMPT 作为去分化诱导基因：Nad+ 作为胶质瘤癌干样细胞维持的核心轴，”Frontiers in Oncology, vol. 9, p. 292, 2019.

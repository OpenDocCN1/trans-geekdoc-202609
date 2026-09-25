# 2020 IEEE 第40 次国际分布式计算系统会议 (ICDCS)







**摘要**机器学习在利用海量数据方面起着至关重要的作用。构建高质量的机器学习模型需要大量的专业知识和耗时来调优超参数。在全球范围内，我们注意到许多科学家无法随着增长的数据量进行扩展。最近，人们已经开发了一些框架来支持自动化算法选择和超参数调优（CASH）。然而，许多现有的机器学习库（例如 `scikit-learn`）只能在单节点上工作，并且无法扩展并处理大规模数据量。在本文中，我们提出了一种基于 Apache Spark 的分布式 SmartML 框架。我们的框架配备了不同的自动化调优技术：网格搜索、随机搜索和 Hyperband 优化。我们展示了该框架在分布式 ML 优化上的最先进性能。对于具有强大知识和良好经验的科学家来说，我们正目睹着在人类参与的情况下，构建机器学习流水线的兴趣日益增长。特别是，AutoML 技术正使领域专家和非技术用户能够广泛使用。最近，已有几个框架被设计用于支持 CASH（算法选择和超参数调优）。例如，`Auto-Weka` [6] 是一个在流行的 Weka 机器学习库上开发的用于 CASH 问题的框架，基于模型的配置优化（SMAC）和结构化帕累托搜索 [14]。我们展示了一个在流行的 `scikit-learn` 机器学习库上实现的 AutoML 框架。在我们的工作中，我们提出了 SmartML [6]，这是一个使用流行的 R 语言语言进行 SMAC 优化的包。

# I. 引言

最近，我们见证了各个领域系统、设备和来源产生的数据量持续增加。据报道，过去两年中全球生成了 25 亿字节的数据。一方面，数据越多，机器学习和深度学习技术产生的结果就越多。在大数据时代，由于需要增加自动化算法的数量，这种情况日益导致了潜在的数据科学危机，类似于软件危机 [5]。另一方面，由于每个配置的巨大成本（例如时间和计算资源），处理大量分类器时，我们提出了一种基于 Apache Spark 的数据处理框架 D-SmartML，这是一种分布式 AutoML。D-SmartML 配备了机器学习机制 [8]，用于自动化算法选择和监督超参数调优技术：网格搜索、随机搜索和 Hyperband 优化。作为一个分布式框架，D-SmartML 增强了……

> *Forbes：我们每天产生多少数据* 2018年5月21日

# 算法 1：Hyperband 算法

```
输入：R, T, P
输出：性能最佳的模型
初始化 s_{max} = ⌊|R|⌋
for s ∈ {s_{max}, s_{max} - 1, ..., 0}
  if (T < Total(s)) then
    n = ⌊s + 1⌋, r = R/s
    / 为 T 开始 (n, r) 迭代减半
    while T < T
    h = get(Hyperparameters, Configuration(n))
    for i ∈ {0, ..., s}
      n_i = n * r^i
      r_i = r^i
      M = evaluate_with_Time(r_i, T), P)
      h = topK(M, ⌊n_i/k⌋)
    end
  endif
end
return (best model)
```
img/29a2b2cbd7acd1fd203e1aa5bbc88f9d_1.png

# II. D-SMART 架构

为了解决大规模数据集上的 AutoML 计算复杂度，图1了 D-SMART 的组件和框架架构，它由十一个分类器组成。sparkML：随机森林、逻辑回归、决策树、朴素贝叶斯和梯度提升树。我们通过实现线性判别分析和二次判别分析扩展了该包。sparkML 提供的任何新分类器都可以包含。

元学习是从各种任务中获得的先前经验中学习，并减少学习新任务所需的过程。对于任何优化，目标都是有效缩小搜索空间，以便选择或从少数分类器开始，这在处理大量分类器时，由于每个配置的成本很高（例如时间和计算资源），对于减少输入数据具有重要意义。

算法由两个循环组成：迭代减半（Successive Halving）以及带有不同预算和超参数数量调用内部循环的外层循环。我们使用了 `spark.ml` 中的模型并行能力，以便在集群具有足够计算能力的情况下并行模型。库暴露了一个参数来控制发送到 Spark 调度器的作业数量，可以更好地利用集群资源。

AutoSkLearn 可以为较小的数据集提供竞争性的性能。随着数据集规模的增大，集中框架性能被分布式框架超越，特别是对于最大的数据集（20.7 GB 和 24.6 GB），集中解决方案会导致内存溢出（OOM）。结果还显示，不同数据集和时间预算的混合算法是最好的。为了开发这个元模型，我们选择了元特征（样本量、偏度和峰度）。为了解决这一挑战，我们开发了元模型（样本量、偏度和峰度）。超参数优化的主要目标是确定机器学习可以返回不同的性能。D-SMART 支持许多技术：网格搜索、随机搜索和迭代减半。如算法 1 所示，算法返回四个参数：

- R：定义分配给单个配置的最大资源量。
- j：控制在每次迭代减半中丢弃配置的比例。
- P：定义并行程度：内部循环，其

# III. 实验评估

我们进行了实验来评估 D-SmartML 的性能。实验在部署在 Google 云上的 Spark 集群上运行，主节点 4 个 CPU、16 GB 内存，工作节点具有 8 个 CPU、30 GB 内存和 500GB HDD。我们的实验使用了来自 OpenML 和 UCI 仓库的 17 个数据集。我们数据集的大小从 2MB 到 7.5GB 不等。

# IV. 演示场景

D-SmartML 是作为一个基于 Scala 的开发的，DSmartML 发布在 Maven 仓库中。在实验中，我们首先介绍了面临的所有挑战以及我们框架的主要目标。特别是，我们将展示集中式学习库（例如 `Auto-Weka`、`Auto-Sklearn`、`SmartML`）无法处理大规模数据集。然后，

> https://www.openml.org/
> http://archive.uci.edu/ml/index.php
> 分配给集中工具的计算资源（CPU，内存）等于分布式框架的资源量。
> https://autoai.com/
> 我们报告的是数据集的一个子集由于空间限制。
> 每次比较中的最佳值已用加粗字体和下划线标记。

> https://github.com/salesforce/TransmogrAI

> D-SmartML 的源代码可用于：github.com/DataSystemsGroupUP/Distributed-SmartML,

> https://maven.apache.org/artifact/com.DataSystemsGroupUP/D-SmartML/0.0.1/





| 数据集 | 2 类 | 100 秒 | 300 秒 | 600 秒 | 1800 秒 |
| --- | --- | --- | --- | --- | --- | --- |
| 扑克牌牌 | 24 MB | 50.18% | 49.99% | 53.28% | 73.85% | 53.60% | 53.62% | 53.54% |
| 信用卡欺诈 | 98 MB | 99.81% | 99.92% | 99.94% | 99.95% | 99.95% | 99.94% | 99.96% |
| BNG 金额 | 120 MB | 99.8% | 99.98% | 99.98% | 99.98% | 99.98% | 99.98% | 99.98% |
| BNG Mfeat | 540 MB | 9.20% | 73.11% | 76.94% | 78.75% | 76.94% | 79.96% | 78.12% | 80.36% |
| BNG Image | 1.2 GB | 88.8% | 89.8% | 89.8% | 89.8% | 89.8% | 90% | 89.8% | 89.8% |
| HEPMASS | 4.8 GB | 49.99% | 83.50% | 80.00% | 89.95% | 80.41% | 89.52% | 83.94% | 85.12% |
| HIGGS-1 | 11.2 GB | 73.5% | 73.5% | 73.5% | 73.5% | 73.5% | 63.20% | 71.5% | 80.63% |
| HIGGS-2 | 20.7 GB | OOM | OOM | OOM | 0.00% | 0.00% | OOM | OOM | 81.87% |
| HEPMASS-2 | 24.8 GB | OOM | OOM | OOM | OOM | OOM | 61.17% | OOM | 80.59% |

表 I：性能对比：Hyperband VS 随机搜索

| 数据集 | TransformerAI | D-SmartML |
| --- | --- | --- | --- |
| 扑克牌牌 | 285 | 900 | 971 |
| APS 欺诈 | 624 | 989 | 998 |
| 气体分析 | 206 | 994 | 999 |
| 信用卡欺诈 | 112 | 991 | 993 |
| 非法攻击检测 | 525 | 998 | 999 |
| BNG Mfeat | 332 | 790 | 806 |
| 智慧城市 | 718 | 809 | 823 |
| 传感器 Flo4 | 640 | 809 | 823 |
| CoPelek | 710 | 639 | 710 |
| 豆子机 | 1345 | 956 | 998 |
| CIFAR-10 | 2396 | 986 | 998 |
| SVHN | 5214 | 998 | 999 |
| LSTMs | 1195 | 7915 | 7964 |
| HEPMASS | 1492 | 838 | 806 |
| HIGGS-1 | 826 | 809 | 823 |
| HIGGS-2 | 20.7 GB | >1000 | 80 | 80.07% |

表 II：性能对比：D-SmartML VS Transformer

# 参考文献

[1] James Briggs 和 Yoshua Beng. 超参数搜索的随机搜索。Journal of Machine Learning, 12(1):281-305, 2011.

[2] Matthias Boehem. 系统化：机器搜索。PVLB, 6 (2013)。

[3] Jalnaissi, Radwa Elshy 和 Sherif Saif. 用于自动机器学习的决策支持框架。AutoML 会, 2019.

[4] Matthias Feurer, Aaron Klein, Katherine Eggberger, Tobias Josef, Manuel Blum. 高效且稳健的机器学习。NIPS, 15, 2775–2783. MIT Press, 2015.

[5] Brian FitzGerald. 软件 2.0。Computer, 45(2), 2014.

[6] Lars Lotharsch, Karl Thornton, Helen G. Frank 和 Kevin Robyn. 自动元 2.0：超参数在。J. Mach. Learn., 18(8):826–836, 2017.

[7] Li Li, Kevin G Johnson, Julia DeSalvo, Afif Ramirez 和 Ahmet Talwalkar. Hyperband：基于老虎的超参数优化方法。JMLR, 2017.

[8] Mohamed Maher 和 Sherif Saif. Smartart：基于机器学习的自动特征选择和超参数调优。EDRT’19, 2019.

[9] Xiantang Meng 等。搜索空间中的机器学习。JMLR, 17(1), 2016.

[10] Douglas C Montgomery. 设计与分析。John Wiley & sons, 2017.

[11] Sherif Saif 和 Albert Yomza. 大数据技术百科全。Springer, 2019.

[12] Radwa Elshy, Mohamed Maher 和 Sherif Saif. 自动机器学习：现状方法和开源工具。CoRR, arXiv:1906.02287, 2019.

[13] Joaquin Vancanish. 元学习：综述。arxiv preprint arXiv:1810.0548,

[14] Marc-André Zolleller 和 Manuel Huber. 自动机器学习综述。arXiv:1904.12054, 2019.

¹⁴我们库的完整文档请参阅：https://datasets.github.io/D-SmartML/docs


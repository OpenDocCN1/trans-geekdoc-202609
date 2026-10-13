
图 7.6(a)–(d) 展示了各方法在不同数据集上，决策树分类器在数据流某一时间点前的错误率（ERR）。K 近邻（K-NN）分类器也呈现出类似的结果。例如，当 `X` 轴 = 100 时，`Y` 值显示了各方法从数据流开始到第 100 个数据块的平均 ERR。此时，对于 KDD 数据集（图 7.6(c)），MC、W-OP 和 W-OS 的 ERR 分别为 1.7%、11.6% 和 8.7%。每个数据集中新类别的到达，在每个图表顶部边框对应数据块处用叉号（x）标记。例如，在 SynCN 数据集上（图 7.6(a)），W-OP 和 W-OS 漏掉了大部分新类别实例，导致它们的曲线在相应数据块处出现尖峰（如第 12、24、37 个数据块等）。W-OS 几乎漏掉了 99% 的新类别实例。在 KDD 和 Forest Cover 数据集中，新类别出现的数据块处，W-OP 和 W-OS 也观察到类似的尖峰。例如，在 KDD 数据集的第 9–14 个数据块之间出现了许多新类别，其中大部分都被 W-OP 和 W-OS 漏掉了。注意，SynC 数据集没有新类别。MC 正确检测了大部分这些新类别。因此，MC 在所有数据集上均优于 W-OP 和 W-OS。

![图 7.6 (a) SynCN、(b) SynC、(c) KDD 和 (d) Forest Cover 上的错误率对比。](img/fig7_6.jpg)

图 7.6 (a) SynCN、(b) SynC、(c) KDD 和 (d) Forest Cover 上的错误率对比。

表 7.1 总结了决策树和 K-NN 在各数据集上各技术的错误度量。以 ERR、`M[new]` 和 `F[new]` 为标题的列报告了整个数据集上相应度量的平均值。例如，在 SynC 数据集上使用决策树时，MC、W-OP 和 W-OS 的 ERR 几乎相同，分别为 11.6%、13.0% 和 12.5%。这是因为 SynC 仅模拟概念漂移，而 MC 和 WCE 处理概念漂移的方式相似。在使用决策树的 SynCN 数据集上，MC、W-OP 和 W-OS 的 `M[new]` 分别为 0%、89.4% 和 99.7%。因此，W-OS 几乎漏掉了所有新类别实例，而 W-OP 仅检测出了 11% 的新类别实例。MC 正确检测了所有新类别实例。有趣的是，所有方法在 SynCN 上的错误率都低于 SynC。这是因为 SynCN 使用高斯分布生成，天然更容易让分类器学习。W-OS 在所有数据集中几乎都会错误预测所有新类别实例。W-OS 相比 W-OP 具有相对较好的 ERR 率，这归因于 W-OS 較低的假阳性率，因为 W-OS 几乎将所有实例都识别为“正常”。同样，MC 的总体错误率（ERR）在所有数据集和所有分类器上都远低于其他方法。K-NN 在所有数据集上也呈现出类似的结果。

表 7.1 性能对比

| ![](img/inline7_1.jpg) |

| --- |

图 7.7(a)–(d) 说明了在 KDD 数据集和决策树分类器上，MC 的错误率如何随不同参数设置而变化。这些参数对其他数据集和 K-NN 分类器也有类似的影响。图 7.7(a) 展示了在其他参数取默认值时，数据块大小对 ERR、`F[new]` 和 `M[new]` 率的影响。随着数据块大小增加，`M[new]` 降低。这是可取的，因为较大的数据块降低了漏掉新类别的风险。但 `F[new]` 率略微上升，因为将现有类别实例识别为新类别的风险也略微上升。这些变化从数据块大小 4,000 开始趋于稳定（对于合成数据集，则是 1,000）。这就是我们在实验中使用这些值的原因。图 7.7(b) 展示了聚类数量（`K`）对错误率的影响。增加 `K` 通常会降低错误率，因为异常值被更正确地检测出来，从而导致 `M[new]` 率下降。然而，`F[new]` 率也开始缓慢上升，因为更多的测试实例变成了异常值（尽管它们并非异常值）。综合效果是总体错误率持续下降直到某个值（例如 `K` = 50），之后变得几乎平坦。这就是我们在实验中使用 `K` = 50 的原因。图 7.7(c) 展示了集成规模（`M`）对错误率的影响。我们观察到错误率下降直到某个规模（= 6），此后趋于稳定。这是因为当 `M` 从较低值（如 2）增加时，由于误差方差的减少 [WANG2003]，分类错误自然会下降到一定程度。图 7.7(d) 展示了 `N` 对错误率的影响。该图表的 `x` 轴采用对数刻度。自然地，将 `N` 增加到某个点（如 20）有助于降低错误率，因为较高的 `N` 值使我们在声明新类别时具有更大的信心。但过大的 `N` 值会增加 `M[new]` 和 ERR 率，因为如果一个新类别在数据块中的实例少于 `N` 个，算法就会漏掉它。我们发现 20 到 100 之间的任何值都是 `N` 的最佳选择。

![图 7.7 对不同参数的敏感性分析。(a) 数据块大小对总体错误率的影响；(b) 集成规模对错误率的影响；(c) 聚类数量对错误率的影响；(d) 最小点数对错误率的影响。](img/fig7_7.jpg)

图 7.7 对不同参数的敏感性分析。(a) 数据块大小对总体错误率的影响；(b) 集成规模对错误率的影响；(c) 聚类数量对错误率的影响；(d) 最小点数对错误率的影响。

#### 7.4.3.3 运行时间

表 7.2 比较了 MC、W-OP 和 W-OS 在各数据集上针对决策树的运行时间。K-NN 也显示出类似的性能。标题为“Time (sec)/chunk”的列显示了每个数据块的平均运行时间（训练和测试），单位为秒；标题为“Points/sec”的列显示了平均每秒处理（训练和测试）的点数；标题为“speed gain”的列显示了 MC 速度与 W-OP 和 W-OS 速度的比率。例如，在 KDD 数据集上，MC 比 W-OP 快 2,095 倍；在 Forest Cover 数据集上，快 105 倍。此外，在 SynCN 数据集上，MC 分别比 W-OP 和 W-OS 快 203 倍和 27 倍。W-OP 和 W-OS 在 SynCN 上比在 SynC 上慢，因为 SynCN 数据集拥有更多属性（20 对 10）和类别（10 对 2）。W-OP 相对比 W-OS 慢，因为 W-OP 维护 `C` 个并行模型，其中 `C` 是现有类别的数量，而 W-OS 仅维护一个模型。由于 Forest Cover 的类别数量较少，且演变程度相对低于 KDD，W-OP 和 W-OS 在 Forest Cover 上相对比在 KDD 上快。导致 W-OP 和 W-OS 处理极其缓慢的主要原因是，每个 OLINDDA 模型的聚类数量随着数据流规模的增长而线性增加，导致内存需求和运行时间也线性增加。但 MC 的运行时间和内存需求在整个数据流长度上保持不变。

表 7.2 所有数据集中的运行时间对比

| ![](img/inline7_2.jpg) |

| --- |

## 7.5 安全应用与恶意软件检测

所提出的新颖类别检测技术将在多个安全应用中发挥作用。首先，它可用于检测网络流量中的新型攻击。如果网络流量中出现了一种全新的攻击类型，现有的入侵检测技术可能无法识别。相反，如果网络流量中发生了一种全新的攻击，我们的方法应将其检测为“新颖类别”并发出警报。这将提示系统分析师隔离并分析这些未知事件的特征，并进行相应标记。分类模型也将利用这些新类别实例进行更新。若未来发生同类入侵，分类模型将能将其识别为已知入侵。其次，我们的方法也可用于检测新型恶意软件。现有的恶意软件检测技术可能无法识别全新的恶意软件，但我们的方法应能将新恶意软件检测为新颖类别、将其隔离并发出警报。被隔离的二进制文件稍后将由人工专家进行分析和表征。通过这种方式，所提出的新颖类别检测技术可有效应用于网络安全领域。

新颖类别检测技术有多个潜在的安全应用，例如网络流量中的入侵检测或主机中的恶意软件检测。以恶意软件检测问题为例。为应用我们的新颖类别检测技术，我们首先需要为每个可执行文件确定一组特征。这可以通过 `n`-gram 特征提取和选择 [MASU2008b] 来完成。只要使用 [MASU2008b] 方法选定的特征集仍然是新型恶意软件的最佳特征集，我们的方法就应能将新恶意软件类别检测为新颖类别。与其他分类方法相比，我们的方法在此方面具有双重优势。首先，它能将新型恶意软件检测为新颖类别。这种检测将引发对恶意软件的进一步分析和表征。相反，如果出现新型恶意软件，传统分类技术要么将其判定为良性，要么仅仅判定为“恶意软件”。因此，我们的方法通过将其识别为新颖类型，能提供关于新恶意软件的更多信息。第二个优势是，如果使用新颖类别检测系统测试现有类型的恶意软件，它将被识别为恶意软件，且能预测出该恶意软件的“类型”。

## 7.6 总结与展望

数据流分类是一项具有挑战性的任务，不同研究者以不同方式加以解决。大多数方法忽略了数据流中可能出现新类别这一事实。若考虑这一现象，分类问题将变得更具挑战性。我们的方法以高效方式应对这一挑战。

本章详细阐述了新颖类别检测算法的工作细节。训练阶段，我们的方法在训练数据周围构建决策边界。分类阶段，若实例落在决策边界之外，则标记为 `outlier` 并存储以供进一步分析。当发现足够多的离群点时，我们计算离群点间的内聚度以及离群点与训练数据的分离度。若内聚度和分离度均显著，则将这些离群点识别为新颖类别。在 [[THUR2017]](#ch07.xhtml#ref7_9) 中，我们讨论了该方法在多个合成和基准数据流上的有效性。我们还讨论了数据集、实验设置、基线技术及数据集上的评估。我们使用了四个不同数据集，其中两个为合成数据集，另外两个为基准数据流。在所有数据集上，我们的方法在分类与新颖类别检测准确率及运行时间方面均优于其他基线技术。

未来，我们希望从多个方向拓展该方法。首先，我们希望将该技术拓展至实时数据流分类。为达成此目标，我们必须优化训练过程，包括决策边界的构建。此外，离群点检测和新颖类别检测也应更高效。我们相信云计算框架能在提升这些流程效率方面发挥重要作用。其次，我们希望解决实时数据流分类问题。由于数据标注和训练分类模型涉及的开销，实时数据流挖掘更具挑战性。第三，我们希望利用云计算框架进行数据流挖掘。云计算框架将成为实时流挖掘所需更高效、更强大计算能力的低成本替代方案。鉴于数据的流式特性，我们预期将收集和分析海量数据。因此，除云计算框架外，我们还预期使用大数据技术来存储和管理数据。这样便可分析更大规模、真实世界的数据流，并将我们的方法拓展以解决数据流中的实时分类和新颖类别检测问题。我们将在接下来的两章中讨论这方面工作的细节。

## 参考文献

*   [CHEN2008] S. Chen, H. Wang, S. Zhou, P. Yu, Stop Chasing Trends: Discovering High Order Models in Evolving Data, *Proceedings of ICDE, Cancun, Mexico*, 2008, pp. 923–932.

*   [HULT2001] G. Hulten, L. Spencer, P. Domingos, Mining Time-Changing Data Streams, *Proceedings of ACM SIGKDD, San Francisco, CA*, 2001, pp. 97–106.

*   [KOLT2005] J. Kolter M. Maloof, Using Additive Expert Ensembles to Cope with Concept Drift, *Proceedings of ICML, Bonn, Germany*, 2005, pp. 449–456.

*   [MARK2003] M. Markou, S. Singh, Novelty Detection: A Review – Part 1: Statistical Approaches, Part 2: Neural Network-Based Approaches, Signal Processing, Volume 83, 2003, pp. 2499–2521.

*   [MASU2008a] M. Masud, Latifur Khan, Bhavani Thuraisingham, A Scalable Multi-level Feature Extraction Technique to Detect Malicious Executables, Information System Frontiers, Volume 10, # 1, 2008, 33–45.

*   [MASU2008b] M. Masud, J. Gao, L. Khan, J. Han, B. Thuraisingham, A Practical Approach to Classify Evolving Data Streams: Training with Limited Amount of Labeled Data, *Proceedings of ICDM, Pisa, Italy*, 2008, pp. 929–934.

*   [ROBE2000] S.J. Roberts, Extreme Value Statistics for Novelty Detection in Biomedical Signal Processing, *Proceedings of International Conference on Advances in Medical Signal and Information Processing, Bristol, UK*, 2000, pp. 166–172.

*   [SPIN2007] E.J. Spinosa, A.P. de Leon, F. de Carvalho, J. Gama, Olindda: A Cluster-based Approach for Detecting Novelty and Concept Drift in Data Streams, *Proceedings 2007 ACM Symposium on Applied Computing, Seoul, Korea*, 2007, pp. 448–452.

*   [THUR2017] B. Thuraisingham, P. Pallabi, M.M. Masud, L. Khan, Big Data Analytics with Applications in Insider Threat Detection, Washington, DC: CRC Press, 2017.

*   [WANG2003] H. Wang, W. Fan, P. Yu, J. Han, Mining Concept-Drifting Data Streams Using Ensemble Classifiers, *Proceedings of ACM SIGKDD*, 2003, pp. 226–235.

*   [YANG2005] Y. Yang, X. Wu, X. Zhu, Combining Proactive and Reactive Predictions for Data Streams. *Proceedings of ACM SIGKDD, Chicago, IL*, pp. 710–715, 2005.

*   [YANG2002] Y. Yang, J. Zhang, J. Carbonell, C. Jin, Topic-Conditioned Novelty Detection, *Proceedings ACM SIGKDD, Edmonton, Alberta*, 2002, pp. 688–693.

*   [YEUN2002] D.Y. Yeung, C. Chow. Parzen-Window Network Intrusion Detectors, *Proceedings of International Conference on Pattern Recognition, Quebec City, QC, Canada*, 2002, pp. 385–388.

# 8 基于云的恶意软件检测数据科学

DOI: [10.1201/9781003081845-13](https://doi.org/10.1201/9781003081845-13)

## 8.1 简介

恶意软件是每年许多成功网络攻击的有力手段，包括数据和身份窃取、系统和数据破坏以及拒绝服务；因此，它对许多个人和组织构成了重大的安全威胁。恶意软件包括病毒、蠕虫、特洛伊木马、定时/逻辑炸弹、僵尸网络和间谍软件。研究人员设计了许多技术来应对这些攻击；然而，研究人员在检测和预防攻击方面越成功，野外出现的恶意代码就越复杂。因此，恶意软件作者与恶意软件防御者之间的军备竞赛持续升级。杀毒社区用于检测恶意代码的一种流行技术是*特征检测*。该技术将不受信任的可执行文件与被称为*特征*的唯一标志性字符串或字节模式进行匹配，该特征用作特定恶意代码的标识符。尽管特征检测技术被广泛使用，但它们对零日攻击（新恶意代码）、多态攻击（同一二进制文件的不同加密）或变形攻击（实现相同功能的不同代码）无效 [CRAN2005]。因此，迫切需要快速、自动化且高效的检测技术，且这些技术需对上述攻击具有鲁棒性。

在第 6 章中，我们讨论了用于恶意软件检测的数据挖掘工具。本章描述了一种专门用于自动生成特征以防御某些恶意软件攻击的数据挖掘技术。由于恶意软件检测工具需要近实时性能，我们在云端开发了数据挖掘工具。也就是说，本章的主要目的是展示如何利用云等大数据技术来提升恶意软件检测技术的性能和可扩展性。我们在本章剩余部分详细描述了该基于云工具的设计与实现。

本章结构安排如下：第 8.2 节讨论恶意软件检测。第 8.3 节讨论相关工作。第 8.4 节讨论分类算法并从分析上证明其有效性。第 8.5 节接着描述利用云计算进行恶意软件检测的特征提取与选择技术，第 8.6 节讨论数据收集、实验设置、评估技术和结果。第 8.7 节讨论与我们方法相关的若干问题，最后，第 8.8 节总结我们的结论。图 8.1 阐释了本章的概念。

![图 8.1 用于恶意软件检测的大数据与云。](img/fig8_1.jpg)

图 8.1 用于恶意软件检测的大数据与云。

## 8.2 恶意软件检测

### 8.2.1 作为数据流分类问题的恶意软件检测

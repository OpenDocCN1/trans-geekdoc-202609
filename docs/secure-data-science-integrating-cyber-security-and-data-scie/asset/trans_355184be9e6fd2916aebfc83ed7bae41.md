
所提出的新颖类别检测技术将在多个安全应用中发挥作用。首先，它可用于检测网络流量中的新型攻击。如果网络流量中出现了一种全新的攻击类型，现有的入侵检测技术可能无法识别。相反，如果网络流量中发生了一种全新的攻击，我们的方法应将其检测为“新颖类别”并发出警报。这将提示系统分析师隔离并分析这些未知事件的特征，并进行相应标记。分类模型也将利用这些新类别实例进行更新。若未来发生同类入侵，分类模型将能将其识别为已知入侵。其次，我们的方法也可用于检测新型恶意软件。现有的恶意软件检测技术可能无法识别全新的恶意软件，但我们的方法应能将新恶意软件检测为新颖类别、将其隔离并发出警报。被隔离的二进制文件稍后将由人工专家进行分析和表征。通过这种方式，所提出的新颖类别检测技术可有效应用于网络安全领域。

新颖类别检测技术有多个潜在的安全应用，例如网络流量中的入侵检测或主机中的恶意软件检测。以恶意软件检测问题为例。为应用我们的新颖类别检测技术，我们首先需要为每个可执行文件确定一组特征。这可以通过 `n`-gram 特征提取和选择 [MASU2008b] 来完成。只要使用 [MASU2008b] 方法选定的特征集仍然是新型恶意软件的最佳特征集，我们的方法就应能将新恶意软件类别检测为新颖类别。与其他分类方法相比，我们的方法在此方面具有双重优势。首先，它能将新型恶意软件检测为新颖类别。这种检测将引发对恶意软件的进一步分析和表征。相反，如果出现新型恶意软件，传统分类技术要么将其判定为良性，要么仅仅判定为“恶意软件”。因此，我们的方法通过将其识别为新颖类型，能提供关于新恶意软件的更多信息。第二个优势是，如果使用新颖类别检测系统测试现有类型的恶意软件，它将被识别为恶意软件，且能预测出该恶意软件的“类型”。

## 7.6 总结与展望

数据流分类是一项具有挑战性的任务，不同研究者以不同方式加以解决。大多数方法忽略了数据流中可能出现新类别这一事实。若考虑这一现象，分类问题将变得更具挑战性。我们的方法以高效方式应对这一挑战。

本章详细阐述了新颖类别检测算法的工作细节。训练阶段，我们的方法在训练数据周围构建决策边界。分类阶段，若实例落在决策边界之外，则标记为 `outlier` 并存储以供进一步分析。当发现足够多的离群点时，我们计算离群点间的内聚度以及离群点与训练数据的分离度。若内聚度和分离度均显著，则将这些离群点识别为新颖类别。在 [[THUR2017]](#ch07.xhtml#ref7_9) 中，我们讨论了该方法在多个合成和基准数据流上的有效性。我们还讨论了数据集、实验设置、基线技术及数据集上的评估。我们使用了四个不同数据集，其中两个为合成数据集，另外两个为基准数据流。在所有数据集上，我们的方法在分类与新颖类别检测准确率及运行时间方面均优于其他基线技术。

未来，我们希望从多个方向拓展该方法。首先，我们希望将该技术拓展至实时数据流分类。为达成此目标，我们必须优化训练过程，包括决策边界的构建。此外，离群点检测和新颖类别检测也应更高效。我们相信云计算框架能在提升这些流程效率方面发挥重要作用。其次，我们希望解决实时数据流分类问题。由于数据标注和训练分类模型涉及的开销，实时数据流挖掘更具挑战性。第三，我们希望利用云计算框架进行数据流挖掘。云计算框架将成为实时流挖掘所需更高效、更强大计算能力的低成本替代方案。鉴于数据的流式特性，我们预期将收集和分析海量数据。因此，除云计算框架外，我们还预期使用大数据技术来存储和管理数据。这样便可分析更大规模、真实世界的数据流，并将我们的方法拓展以解决数据流中的实时分类和新颖类别检测问题。我们将在接下来的两章中讨论这方面工作的细节。

## 参考文献

*   [CHEN2008] [S. Chen](#ch07.xhtml#Cref7_1), H. Wang, S. Zhou, P. Yu, Stop Chasing Trends: Discovering High Order Models in Evolving Data, *Proceedings of ICDE, Cancun, Mexico*, 2008, pp. 923–932.

*   [HULT2001] [G. Hulten](#ch07.xhtml#Cref7_2), L. Spencer, P. Domingos, Mining Time-Changing Data Streams, *Proceedings of ACM SIGKDD, San Francisco, CA*, 2001, pp. 97–106.

*   [KOLT2005] [J. Kolter](#ch07.xhtml#Cref7_3) M. Maloof, Using Additive Expert Ensembles to Cope with Concept Drift, *Proceedings of ICML, Bonn, Germany*, 2005, pp. 449–456.

*   [MARK2003] [M. Markou](#ch07.xhtml#Cref7_4), S. Singh, Novelty Detection: A Review – Part 1: Statistical Approaches, Part 2: Neural Network-Based Approaches, Signal Processing, Volume 83, 2003, pp. 2499–2521.

*   [MASU2008a] [M. Masud](#ch07.xhtml#Cref7_5), Latifur Khan, Bhavani Thuraisingham, A Scalable Multi-level Feature Extraction Technique to Detect Malicious Executables, Information System Frontiers, Volume 10, # 1, 2008, 33–45.

*   [MASU2008b] [M. Masud](#ch07.xhtml#Cref7_6), J. Gao, L. Khan, J. Han, B. Thuraisingham, A Practical Approach to Classify Evolving Data Streams: Training with Limited Amount of Labeled Data, *Proceedings of ICDM, Pisa, Italy*, 2008, pp. 929–934.

*   [ROBE2000] [S.J. Roberts](#ch07.xhtml#Cref7_7), Extreme Value Statistics for Novelty Detection in Biomedical Signal Processing, *Proceedings of International Conference on Advances in Medical Signal and Information Processing, Bristol, UK*, 2000, pp. 166–172.

*   [SPIN2007] [E.J. Spinosa](#ch07.xhtml#Cref7_8), A.P. de Leon, F. de Carvalho, J. Gama, Olindda: A Cluster-based Approach for Detecting Novelty and Concept Drift in Data Streams, *Proceedings 2007 ACM Symposium on Applied Computing, Seoul, Korea*, 2007, pp. 448–452.

*   [THUR2017] [B. Thuraisingham](#ch07.xhtml#Cref7_9), P. Pallabi, M.M. Masud, L. Khan, Big Data Analytics with Applications in Insider Threat Detection, Washington, DC: CRC Press, 2017.

*   [WANG2003] [H. Wang](#ch07.xhtml#Cref7_10), W. Fan, P. Yu, J. Han, Mining Concept-Drifting Data Streams Using Ensemble Classifiers, *Proceedings of ACM SIGKDD*, 2003, pp. 226–235.

*   [YANG2005] [Y. Yang](#ch07.xhtml#Cref7_11), X. Wu, X. Zhu, Combining Proactive and Reactive Predictions for Data Streams. *Proceedings of ACM SIGKDD, Chicago, IL*, pp. 710–715, 2005.

*   [YANG2002] [Y. Yang](#ch07.xhtml#Cref7_12), J. Zhang, J. Carbonell, C. Jin, Topic-Conditioned Novelty Detection, *Proceedings ACM SIGKDD, Edmonton, Alberta*, 2002, pp. 688–693.

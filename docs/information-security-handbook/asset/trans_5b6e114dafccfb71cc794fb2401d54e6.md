

作者得出结论，这种分组是基于互信息的。通过计算一个特征的互信息，然后将其与其他特征进行比较，从而表示它们之间的关系。在组中选择一个特征时，使用互信息和类标签。在知识发现数据库（`KDD`）`99`数据集上进行了实验分析；作者提出的技术优于现有算法。因此，通过使用这种技术，可以生成新算法；此外，还可以使用这种技术对其他数据集进行进一步研究。未来，可以提出比互信息理论更有效、更高效的方法。使用这种算法和技术，他们还预测未来的攻击也会发生在实时或网络系统上。与机器学习方法的类似特征分组以及攻击检测准确率在[表 6.1](#ch06.xhtml#table6_1)中显示。

[表 6.1 不同特征分组提取和数据集的不同机器学习技术比较 \[13–15, 17–19, 20\]](#ch06.xhtml#Ttable6_1)

| Ref || ML Technique || Dataset || Features || Results |

| --- | --- | --- | --- | --- |

| Pfahringer \[[13](#ch06.xhtml#ref6_13)\] || Supervised Ensemble of CS DTs (`offline`) || KDD Cup || all 41 features || DR Normal: 99.5%

DR Probe: 83.3%

DR DoS: 97.1%

DR U2R: 13.2%

DR R2L: 8.4%

Training: 24 h |

| --- | --- | --- | --- | --- |

| Pan et al. \[[14](#ch06.xhtml#ref6_14)\] || Supervised NN and C4.5 DT (`offline`) || KDD Cup || all 41 features || DR Normal : 99.5%

DR DoS: 97.3%

DR Probe (Satan): 95.3%

DR Probe (portsweep): 94.9%

DR U2R: 72.7%

DR R2L: 100%

ADR: 93.28% FP: 0.2% |

| Moradi et al. \[[15](#ch06.xhtml#ref6_15)\] || Supervised NN (`offline`) || KDD Cup || 35 features || 2 Layers MLP DR: 80%

ESVM DR: 90% 2 Layers

ESVM DR: 87% |

| Chebrolu et al. \[[16](#ch06.xhtml#ref6_16)\] || Supervised BN and CART (`offline`) || KDD Cup || Feature Selection using Markov Blanket and Gini rule || DR Normal: 100%

DR Probe: 100%

DR DoS: 100%

DR U2R: 84%

DR R2L: 99.47% |

| Amor et al. \[[17](#ch06.xhtml#ref6_17)\] || Supervised NB (`offline`) || KDD Cup || all 4l fearures || DR Normal: 97.68%

PCC DoS: 96.65%

PCC R2L: 8.66%

PCC U2R: 11.84%

PCC Probing: 88.33% |

| Stein et al. \[[18](#ch06.xhtml#ref6_18)\] || Supervised C4.5 DT (`offline`) || KDD Cup || GA-based feature selection || Error rate DoS: 2.22%

Error rare Probe: 1.67%

Error rate R2L: 19.9%

Error rate U2R: 0.1% |

| Paddabachigari et al. \[[19](#ch06.xhtml#ref6_19)\] || Supervised Ensemble of SVM, DT, and SVM-DT Offline || KDD Cup || all 41 features || DR Normal: 99.7%

DK Probe: 100%

DR DoS: 99.92%

DR U2R: 68%

DR R2L: 97.16% |

| Sangkatsanee et al. \[[20](#ch06.xhtml#ref6_20)\] || Supervised C4.5 DT (`online`) || Normal: Reliability

Lab

Data 2009

(RLD09)

Attack: || TCP, UPD, and ICMP header Fields || DR Normal: 99.43%

DK DoS: 99.17%

DR Probe: 98.73% |

| Li et al. \[[21](#ch06.xhtml#ref6_21)\] || Supervised TCM K-NN (`Offline`) || KDD Cup || all 41 features 8 features selected using Chi-square || 41 features: TP 99.7%

41 features: FP 0%

8 features: TP 99.6%

8 fearnres: FP 0.1% |

Chebrolu et al. \[16\] 作者在本文中讨论的主要问题是，某些特征贡献较少，且对检测过程是冗余的。因此，我们需要构建入侵检测系统（`IDS`），这些系统在现实世界系统的检测中既有效又高效。作者对选择算法进行了测试。作者提出了一种混合架构，用于现实世界的入侵检测，通过结合不同的选择算法实现。这些算法是贝叶斯网络（`BN`）和分类与回归树（`CART`）。贝叶斯网络（`BN`）选择算法在不确定条件下运行。贝叶斯网络基于（`DAG`）有向无环图原理，计算一个节点的条件概率并分配给另一个节点。分类与回归树（`CART`）使用二进制递归分区。父节点始终分为两个节点；这就是为什么该过程是二进制和递归的，因为每个节点都被视为父节点，因此该过程会重复自身。在本文中，他们研究了不同的数据挖掘技术；在这里，他们为网络数据选择一个特征或一组特征。他们还通过结合不同的特征和不同的特征集来观察结果。他们开发了一种有效的技术，使用上述选择算法检测攻击并生成真正报警。

作者基于 DARPA 基准测试，得出了本文中新技术在入侵检测方面性能的结论。他们提出了结合贝叶斯网络（`BN`）和分类与回归树（`CART`）分类器的方法，通过加入拟议的混合架构进行入侵检测。因此，分析结果非常准确。这种技术对探测、正常和拒绝服务（`DOS`）的效果更好。作者的目标是为用户到根（`U2R`）类型的攻击构建更高效、更准确的分类器。作者还对攻击进行了子分类，并给出了一个特征；主要分析了托管和帮助攻击的服务。

Davis et al. \[[22](#ch06.xhtml#ref6_22)\] 在本文中，作者解决了网络流量特征选择问题。他们减少了为各种基于网络的攻击生成实时流量观察所需的计算工作量。他们还审查了基于异常的网络入侵检测的数据预处理。为了解决上述问题，作者推荐了数据预处理技术。这种技术是分析和选择用于检测入侵检测的方法的组合。两者结合在一起，以执行最佳搜索和高效工作。在这里，作者试图查找数据包头特征。异常检测技术被网络入侵检测系统（`NIDS`）软件使用，并与机器学习技术一起使用，特别使用模型来检测特征并比较监督和非监督算法。对特征进行分组可以更好地理解，机器学习有助于以更好的预测执行模型。

通过使用这种技术，作者得出结论，通过特征分组，强贡献可以更准确地识别网络或实时流量的相关部分。这导致深度包检测，从而减少了在线特征生成的计算工作量。如今，安全已成为每个组织和部门面临的挑战。为了解决这类问题，我们需要在网络流量/实时流量中进行异常检测，并具备适当的特征知识。

Ma, C., \[[23](#ch06.xhtml#ref6_23)\] 如今，安全已成为每个组织和部门面临的挑战。为了解决这个问题，需要在网络流量中进行异常检测。因此，为异常检测拥有准确有效的流量特征是一项重大挑战。在本文中，作者提出了比现有算法性能相对更好的方法。作者为网络异常检测提出的方法包括对环境、序列和统计特征的分析。他们提出的方法是混合神经网络的组合；这些是一维卷积神经网络模型（`1D-CNN`）和动态神经网络（`DNN`）方案，称为（`AD-H1CD`），基于混合神经网络的网络流异常检测。这种方法相对更好，并且其分析涵盖了上述所有特征。


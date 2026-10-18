

# 6.3 设计方法论

特征选择是攻击分类的一个重要方面。各种基于特征选择的攻击包括拒绝服务攻击（`DoS`）、用户到根（`U2R`）、根到本地（`R2L`）或探测。特征选择标准应基于匹配攻击标准。如果使用更相关的特征进行分组，则攻击识别将更加准确。在 `KDD-CUP99` 中，共有 41 个可用特征；它们可以根据流量类别（如 `DoS`、`U2R`、`R2L`、探测和正常流量）进一步分类。在 `KDD-CUP99` 中，并非所有特征都相关。有些特征可能对检测攻击没有用，而有些特征可能对分类没有用。

**Algorithm:**

![](Images/inline6_2.jpg)

Step 1. 准备网络以进行数据处理阶段。

Step 2. 使用 snort、wire shark 或 `tcpdump` 从接口 `i` 实时捕获数据包和网络流量日志。

Step 3. 提取 IP 特征 `F`。

Step 4. 创建特征选择组 `G`。

Step 5. 对训练数据 `t1` 和 `t2` 进行分类。

Step 6. 对数据集进行训练，并使用自适应学习应用分类器技术以进行进一步测试。

令 `T -> t1` 和 `t2` 为来自特征分组的标记和未标记数据，

`N` 为空数据，// 有些数据包可能包含不完整的特征

将训练集作为 `t1` 开始；

While (`t2` 不为空)

{

从 `t2` 中选择一个实例 `i` 并生成告警;

// `FP`, `FN`, `TP`, `TN`

If (`C` (`i`) <null)

将 `i` 添加到 `t1` 并从 `t2` 中移除 `i`;

}

输出 `t1` 的分类器。

Step 7. 将结果保存在日志文件中并生成告警。

在评估网络时，它会传输大量数据并生成日志，因此对于小型网络来说，这些数据对于 IDS 来说也非常大。网络流量包含复杂特征，这些特征的分类很难相互关联。第一项任务是进行数据过滤，使得并非所有数据都需要由 ID 处理。第二项任务是进行特征选择，其中相关特征必须分组在一起，以便仅选择相关特征来节省时间和计算复杂度。第三个方面是聚类方法，用于将这些特征相互关联。涉及的一些技术包括贝叶斯网络、CART 等。最后，需要使用 SVM 或神经网络对这些特征进行排名。

特征选择有助于减少数据训练的分类过程。此外，特征选择需要根据 IDS 类型进行考虑。例如，基于行为的 IDS 和基于网络的 IDS 需要考虑不同的特征选择和特征分组。为了分类目的，需要取一组特征 `F` 用于目标输出 `T`。随后是分类方法。采用最小特征集将减少分类过程中的时间和复杂度（[图 6.1](#ch06.xhtml#fig6_1) 和 [6.2](#ch06.xhtml#fig6_2)）。

![Figure 6.1 Performance by using 41 features.](Images/fig6_1.jpg)

[Figure 6.1 Performance by using 41 features.](#ch06.xhtml#Ffig6_1)

![Figure 6.2 Performance by using 17 features.](Images/fig6_2.jpg)

[Figure 6.2 Performance by using 17 features.](#ch06.xhtml#Ffig6_2)

结果清楚地表明，与使用所有 41 个特征相比，使用更少的特征可以提高性能。在正常流量中，使用所有 41 个特征时的准确率为 99.57，而使用仅 17 个特征时，准确率为 99.64。对于其他攻击类别，由于选择的特征较少，准确率略有下降。先前研究的实验结果表明，使用不同机器学习方法的实验数据集如何影响已知攻击的检测结果（[图 6.3](#ch06.xhtml#fig6_3) 和 [表 6.2](#ch06.xhtml#table6_2)）。

![Figure 6.3 Experimental result showing performance analysis using various ML approach \[22\].](Images/fig6_3.jpg)

[Figure 6.3 Experimental result showing performance analysis using various ML approach \[22\].](#ch06.xhtml#Ffig6_3)

[Table 6.2 Attack Class, Training and Test Record of KDD Data Sets \[22\]](#ch06.xhtml#Ttable6_2)

| Type || Training Record || Test Record |

| --- | --- | --- |

| Normal || 100 || 500 |

| --- | --- | --- |

| Probing || 100 || 75 |

| Denial\_of\_service || 100 || 75 |

| Root\_to\_local || 100 || 50 |

| User\_to\_root || 11 || 50 |

# 6.4 应用与未来工作

过去在使用聚类和 AI 方法组合进行特征分组方面的所有工作，都可以扩展到与区块链技术相结合，以在各种动态互连节点之间建立信任；这样，当它们加入网络时，可以实时监控，并能轻松识别恶意节点以挫败任何恶意任务。如果源和目标与区块链绑定，那么识别应用层攻击将变得容易。这可以特别应用于电子健康领域，其中医疗数据与患者和相关医生共享。机器可以设置为包含区块链和 IDS 的用户应用程序组合，从而也可以检测跨层攻击。

# 6.5 结论


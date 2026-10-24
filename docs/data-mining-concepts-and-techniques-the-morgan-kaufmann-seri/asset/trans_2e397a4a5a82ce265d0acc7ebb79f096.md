

## 9.10.

我们希望将数据元组划分为两个簇。设 \( q \) 为长度为 \( n \) 的簇成员向量：如果数据元组 \( i \) 属于簇 A，则 \( q(i) = 1 \)；如果属于簇 B，则 \( q(i) = -1 \)。寻找这两个簇的一种方法是 minimizing 所谓的 *切割大小*，它衡量不同簇之间的总相似度：

\[
q^* = \arg \min_{q \in \{-1, 1\}^n} J = \frac{1}{4} \sum_{i,j=1}^n (q(i) - q(j))^2 W(i, j). \tag{9.48}
\]

- a. 证明切割大小 \( J = \frac{1}{2} q^T (D - W)q \)，其中 \( D \) 是 \( W \) 的度矩阵：\( D(i, i) = \sum_{j=1}^n W(i, j) \)，且当 \( j \neq i \) 时 \( D(i, j) = 0 \)；\( ^T \) 表示向量转置。

- b. 由于簇成员向量 \( q \) 是二进制向量，直接优化公式 (9.48) 非常困难。在实践中，我们对 \( q \) 进行松弛，允许其取实数，并旨在求解以下优化问题。证明公式 (9.49) 的最优解由 \( D - W \) 对应于第二小特征值的特征向量给出。

\[
q^* = \arg \min_{q \in R^n} q^T (D - W)q \quad \text{s.t.} \quad \sum_{i=1}^n q(i)^2 = n \tag{9.49}
\]

## 9.11. SimRank 是用于聚类图和网络数据的相似度量。

- a. 证明 SimRank 计算中 \( \lim_{i \to \infty} s_i(u, v) = s(u, v) \)。

- b. 证明 SimRank 中 \( s(u, v) = p(u, v) \)。

## 9.12. 在一个大型稀疏图中，平均每个节点的度较低，使用 SimRank 的相似度矩阵是否仍然稀疏？如果是，在什么意义上？如果不是，为什么？请斟酌你的回答。

## 9.13. 比较 SCAN 算法（第 9.5.3 节）与 DBSCAN（第 8.4.1 节）。它们的相似点和不同点是什么？

## 9.14. 考虑划分聚类及以下簇约束：每个簇中的对象数量必须介于 \( \frac{n}{k}(1 - \delta) \) 和 \( \frac{n}{k}(1 + \delta) \) 之间，其中 \( n \) 是数据集中的对象总数，\( k \) 是期望的簇数量，\( \delta \) 在 \( [0, 1) \) 中是一个参数。你能扩展 k-means 方法来处理此约束吗？讨论约束为硬约束和软约束的情况。

## 9.9 参考文献注释

Höppner Klawonn, Kruse, 和 Runkler [HKKR99] 对模糊聚类进行了详尽讨论。模糊 c-means 算法（示例 9.7 所基于）由 Bezdek [Bez81] 提出。Fraley 和 Raftery [FR02] 对基于模型的聚类分析和概率模型给出了全面概述。McLachlan 和 Basford [MB88] 对混合模型及其在聚类分析中的应用进行了系统介绍。

Dempster, Laird, 和 Rubin [DLR77] 被公认为首批引入 EM 算法并为其命名的人。然而，正如 Dempster, Laird, 和 Rubin [DLR77] 所承认的，EM 算法的想法在此之前已“在特殊情况下被多次提出”。Wu [Wu83] 对 EM 算法给出了正确的分析。

混合模型和 EM 算法在许多数据挖掘应用中被广泛使用。关于基于模型的聚类、混合模型和 EM 算法的介绍可以在最近的机器学习和统计学习教材中找到——例如，Bishop [Bis06a]、Marsland [Mar09] 和 Alpaydin [Alp11]。

如 Beyer et al. [BGRS99] 所指出，维度增加对距离函数有严重影响。它还对分类、聚类和半监督学习的各种技术产生了巨大影响（Radovanović, Nanopoulos, 和 Ivanović [RNI09]）。

Kriegel, Kröger, 和 Zimek [KKZ09] 对高维数据聚类方法进行了全面综述。Parsons, Haque, 和 Liu [PHL04] 回顾了高维数据的子空间聚类。CLIQUE 算法由 Agrawal, Gehrke, Gunopulos, 和 Raghavan [AGGR98] 开发。PROCLUS 算法由 Aggarwal et al. [APW+99] 提出。

双聚类技术最初由 Hartigan [Har72] 提出。“双聚类”这一术语由 Mirkin [Mir98] 创造。Cheng 和 Church [CC00] 将双聚类引入基因表达数据分析。关于双聚类模型和方法有许多研究。Madeira 和 Oliveira [MO04] 以及 Tanay, Sharan, 和 Shamir [TSS04] 对生物数据分析中的双聚类进行了综述。δ-p-Cluster 的概念由 Wang, Wang, Yang, 和 Yu [WWYY02] 引入。在本章中，我们介绍了 Cheng 和 Church [CC00] 的 δ-聚类算法以及 Pei et al. [PZC+03] 的 MaPle，分别作为基于优化的方法和枚举方法在双聚类中的示例。

降维是一个涉及多个领域的主题。有关信息丰富的综述，请参见 [CG15]。非负矩阵分解由 Paatero 和 Tapper [PT94] 以及 Lee 和 Seung [LS99] 开发。Donath 和 Hoffman [DH73] 以及 Fiedler [Fie73] 是谱聚类的先驱。在本章中，我们使用 Ng, Jordan, 和 Weiss [NJW01] 提出的算法作为示例。有关谱聚类的全面教程，请参见 Luxburg [Lux07] 和 Filippone et al. [FCMR08]。

聚类图和网络数据是一个重要且快速增长的主题。Schaeffer [Sch07]、Nascimento 和 de Carvalho [Nd11]、Aggarwal 和 Wang [AW10] 以及 Malliaros 和 Vazirgiannis [MV13] 提供了多篇综述。SimRank 相似度量由 Jeh 和 Widom [JW02] 开发。PageRank 和个性化 PageRank 由 Page, Brin, Motwani, 和 Winograd [PBMW98] 提出。Bahmani, Chowdhury, 和 Goel [BCG10] 讨论了快速增量和个性化 PageRank。Xu et al. [XYFS07] 提出了 SCAN 算法。Arora, Rao, 和 Vazirani [ARV09] 讨论了最稀疏切割和近似算法。随机块模型最初由 Holland, Laskey, 和 Leinhardt [HLL83] 提出。Rohe, Chatterjee, 和 Yu [RCY11] 讨论了谱聚类和高维随机块模型。

半监督聚类已被广泛研究 [BBM02,BBM04,GCB04,Bai13]。受限 k-means 由 Wagstaff, Cardie, Rogers, 和 Schrödl [WCRS01] 开发。Basu, Banerjee, 和 Mooney [BBM02] 开发了种子 k-means。COP-k-means 算法由 Wagstaff et al. [WCRS01] 给出。带约束的聚类已被广泛研究。Davidson, Wagstaff, 和 Basu [DWB06] 提出了信息性和连贯性的度量。Zheng 和 Li [ZL11] 提出了半监督层次聚类的框架。Settles [Set10] 对主动学习文献进行了全面综述。Cohn, Caruana, 和 McCallum [CCM03] 讨论了半监督聚类中的交互式学习。

本页故意留空

## 深度学习 10

在本章中，你将学习深度学习，这是一种基于人工神经网络的强大技术家族，在计算机视觉、自然语言处理、机器翻译、社交网络分析等方面有广泛应用。它已被用于各种数据挖掘任务，包括分类、聚类、异常检测和强化学习。我们从基本概念（第 10.1 节）开始。然后，我们介绍训练有效深度学习模型的关键算法技术（第 10.2 节），以及常用的深度学习模型架构，包括卷积神经网络（第 10.3 节）、循环神经网络（第 10.4 节）和图神经网络（第 10.5 节）。

## 10.1 基本概念

### 10.1.1 什么是深度学习？

深度学习基于人工神经网络（ANN）（或简称神经网络）。图 10.1 展示了神经网络的一个示例，我们将马上深入探讨细节。粗略地说，神经网络是一组连接的输入-输出单元，每个连接都有一个相关的权重。在学习阶段，网络通过调整权重来学习，以便预测输入元组的正确目标值（例如，类标签）。

神经网络由互连的单元组成。那么，什么是单元？实际上，我们已经见过它了！回想一下，在第 6 章中，我们介绍了一些基本分类器，例如感知机和逻辑回归。考虑一个具有 n 个属性的数据元组 X：X = (X1, X2, ..., Xn)。感知机和逻辑回归分类器首先对不同的属性或特征进行线性加权求和 \sum_{i=1}^{n} X_i w_i + b，其中 w_i (i = 1, ..., n) 是权重，b 是偏置标量。然后，感知机根据线性加权和的符号预测类标签 \hat{y} = sign(\sum_{i=1}^{n} X_i w_i + b)，其中当 z \ge 0 时 sign(z) = 1，否则 sign(z) = 0；逻辑回归根据线性加权和的 Sigmoid 函数预测类后验概率 P(y = 1|X) = \sigma(\sum_{i=1}^{n} X_i w_i + b)，其中 \sigma(z) = \frac{1}{1+exp(-z)} 是 Sigmoid 函数。在神经网络术语中，感知机和逻辑回归都可以被视为一个单元。

正式地，一个单元是一个数学函数，它（1）对输入进行线性加权求和，然后（2）将求和结果传递给激活函数 f(\cdot)。激活函数 f(\cdot) 通常是一个非线性函数，例如感知机中的符号函数和逻辑回归中的 Sigmoid 函数 \sigma(\cdot)。激活函数有许多其他选择，我们将在第 10.2 节介绍其中一些。对于深度学习算法，引入两个额外符号很方便。第一个是激活函数的净输入 I = \sum_{i=1}^{n} X_i w_i + b。第二个是单元的输出 O = f(I)。单元的图示如图 10.2 所示。


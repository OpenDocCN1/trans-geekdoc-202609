

### 17.6.2 Logistic Regression（逻辑回归）

逻辑回归通过拟合数据到 logit 函数来估计事件发生的可能性，也被称为 logit 回归 [149]。逻辑回归用于从大量独立变量中评估离散值（通常如 0/1 这样的二值变量）。它通过拟合数据到 logit 函数来预测事件发生的可能性。此外，它也称为 logit 回归 [150]。

- 引入交互项
- 剔除特征
- 使用正则化方法
- 使用非线性模型

### 17.6.3 Decision Tree（决策树）

它是当今最著名的人工智能算法之一；这是一种用于界定问题的监督学习算法 [151]。该算法在处理离散型和连续型依赖变量时均表现良好。在此算法中，我们根据最重要的特征/独立变量将总体拆分为至少两个同质集合 [152]。

### 17.6.4 Support Vector Machine (SVM)（支持向量机）

在 SVM 中，每个特征元素被视为 n 维空间中的一个点，其值为分离特征，并提供特定关联的比率。这些被称为分类器的线被选择用来分割数据并在图上绘制 [153]。

### 17.6.5 Naive Bayes（朴素贝叶斯）

朴素贝叶斯分类器假设类别中某个特定组件的存在与其他特征的存在无关 [154]。即使这些特征彼此相关，朴素贝叶斯分类器在计算特定结果的概率时也会将这些属性视为独立。朴素贝叶斯模型易于构建，并且对于大型数据集非常有用 [155]。它很简单，并且已知能胜过甚至深度复杂的决策策略 [156]。

### 17.6.6 K-Nearest Neighbors（K 近邻）

为此，KNN 可用于分类和回归。然而，在业界，KNN 更常用于分类问题。K 近邻是一个简单的算法，它存储所有可用案例，并通过其 k 个邻居的大多数投票将新案例进行分类 [157]。

- 在决定采用 KNN 之前，必须反思以下几点
  - KNN 计算开销较高
  - 变量必须归一化，否则高范围变量可能会使算法产生偏差
  - 数据仍需要预处理。

### 17.6.7 K-Means（K 均值）

它简单且易于将给定的数据索引划分为特定数量的组。此外，它是一种无监督算法。簇内的数据点是同质的，与异质组不同 [158]。

K 均值如何构建组：

- K 均值算法选择 k 个中心样本
- 每个数据点加入具有最近质心的簇
- 它根据当前组成员生成新的质心。

根据上述质心，解决每个数据点的最近距离。此过程重复进行，直到质心不再变化 [159]。

### 17.6.8 Random Forest（随机森林）

随机森林是一组决策树的集成术语。随机森林是一组决策树 [160]。为了根据特征对另一个项目进行分类，每棵树给出一个结果，我们表示该树投票支持该类别。每棵树的设置和构建方式如下：

- 如果训练集中的案例数量为 N，则随机抽取 N 个案例的样本。该样本将作为构建树的训练集 [161]。
- 如果有 M 个输入变量，选择一个数 m << M，使得在每个节点，从 M 中随机选择 m 个变量，并且在这 m 个变量上最佳分裂用于分割该节点 [162]。在此过程中，m 的估计被认为是无限的。每棵树都尽可能深度地构建 [163]。没有剪枝。

### 17.6.9 Dimensionality Reduction Algorithms（降维算法）

在当今时代，企业和政府部门以及研究机构正在存储和分析大量的数据 [164]。作为数据科学家，你知道这些原始数据包含大量信息，挑战在于梳理重要的结构和因素。

### 17.6.10 Gradient Boosting Algorithms（梯度提升算法）

梯度是一种提升算法，当我们要处理大量数据以做出具有高预测能力的预测时使用，如下图所示 17.3 [165]。提升（Boosting）实际上是一组学习算法，通过组合若干基础估计器的数量来提高优于单个估计器的稳健性 [166]。

![](img/cbc35e0d02425baa6028b87d56263a7f_467_0.png)

## 参考文献

1. Destefanis, G., Barge, M.T., Brugiapaglia, A., Tassone, S., 使用主成分分析 (PCA) 来表征牛肉。Meat Sci., 56, 3, 255–259, 2000.
2. Destefanis, G., Barge, M.T., Brugiapaglia, A., Tassone, S., 使用主成分分析 (PCA) 来表征牛肉。Meat Sci., 56, 3, 255–259, 2000.
3. White, T., Hadoop: 终极指南, O’Reilly Media, Inc, O’reilley, 43–79, 2012.
4. Nandimath, J., Banerjee, E., Patil, A., Kakade, P., Vaidya, S., Chaturvedi, D., 使用 Apache Hadoop 进行大数据分析，载于：2013 IEEE 第 14 届信息复用与集成国际会议 (IRI)，IEEE，第 700–703 页，2013.
5. Steiner, J.G., Clifford Neuman, B., Schiller, J., II, Kerberos: 开放网络系统的身份验证服务，载于：Usenix Winter，第 191–202 页，1988.
6. Kohl, J.T., Clifford Neuman, B., Theodore, Y., Kerberos 身份验证服务的演变，IEEE，经许可从分布式开放系统重印，F.M.T. Braiden 和 D. Johansen (eds.)，第 78–94 页，1994.
7. Burrell, J., 机器如何“思考”：理解机器学习算法中的不透明性。Big Data Soc., 3, 1, 430, 2016, 2053951715622512.
8. Demsar, J., Zupan, B., Leban, G., Curk, T., 欧洲：从实验机器学习到交互式数据挖掘，载于：欧洲数据挖掘与知识发现原则会议，Springer，柏林，海德堡，第 537–539 页，2004.
9. Maloof, M.A. (Ed.), 计算机安全的机器学习和数据挖掘：方法与应用，Springer Science & Business Media，Springer，第 47–64 页，2006.
10. Dunjko, V. and Briegel, H.J., 量子领域的机器学习与人工智能：近期进展综述。Rep. Prog. Phys., 81, 7, 074001, 2018.
11. Sym, N. and Sharma, A., 等待第四次工业革命的复兴销售：销售研究与实践中的机器学习和人工智能。Ind. Market. Manage., 69, 135–146, 2018.
12. Kovačević, A., Dehghan, A., Filannino, M., Keane, J.A., Nenadic, G., 结合规则和机器学习从临床叙述中提取时间表达式和事件。J. Am. Med. Inf. Assoc., 20, 5, 859–866, 2013.
13. Baldwin, J.F., Lawry, J., Martin, T.P., 广义模糊规则在机器学习和自动知识发现中的应用。Int. J. Uncertainty Fuzziness Knowledge-Based Syst., 6, 05, 459–487, 1998.
14. Baldwin, J.F., Lawry, J., Martin, T.P., 广义模糊规则在机器学习和自动知识发现中的应用。Int. J. Uncertainty Fuzziness Knowledge-Based Syst., 6, 05, 459–487, 1998.
15. Love, B.C., 比较有监督和无监督类别学习。Psychon. Bull. Rev., 9, 4, 829–835, 2002.
16. Fritzke, B., 生长细胞结构——一种用于无监督和监督学习的自组织网络。Neural Networks, 7, 9, 1441–1460, 1994.
17. Radford, A., Metz, L., Chintala, S., 使用深度卷积生成对抗网络进行无监督表示学习。arXiv 预印本 arXiv:1511.06434, 2015.
18. Hastie, T., Tibshirani, R., Friedman, J., 无监督学习，载于：统计学习要素，第 485–585 页，Springer，纽约，纽约，2009。
19. Abdullah, M., Iqbal, W., Erradi, A., Web 应用程序自动分解为微服务的无监督学习方法。J. Syst. Software, 151, 243–2575, 2019.
20. Kim, Y.S., Nick Street, W., Menczer, F., 通过进化搜索进行无监督学习中的特征选择，载于：第六届 ACM SIGKDD 知识发现和数据挖掘国际会议论文集，第 365–369 页，2000。
21. Yang, Y., Liao, Y., Meng, G., Lee, J., 用于无监督学习的混合特征选择方案及其在轴承故障诊断中的应用。Expert Syst. Appl., 38, 9, 11311–11320, 2011.
22. Novotney, S., Schwartz, R., Ma, J., 使用少量标注数据进行无监督声学和语言模型训练，载于：2009 IEEE 国际声学、语音和信号处理会议，2009 年 4 月，IEEE，第 4297–4300 页。
23. Wang, J., Zhu, X., Gong, S., Li, W., 用于无监督行人再识别的可迁移联合属性-身份深度学习，载于：IEEE 计算机视觉与模式识别会议论文集，第 2275–2284 页，2018。
24. Dietterich, T., 机器学习中的过拟合和欠计算。ACM Comput. Surv. (CSUR), 27, 3, 326–327, 1995.
25. Jbabdi, S., Sotiropoulos, S.N., Savio, A.M., Graña, M., Behrens, T.E.J., 多壳扩散 MRI 数据的基于模型分析用于纤维束追踪：如何克服过拟合问题。Magn. Reson. Med., 68, 6, 1846–1855, 2012.
26. Bartlett, P.L., Long, P.M., Lugosi, G., Tsigler, A., 线性回归中的良性过拟合。Proc. Natl. Acad. Sci., 117, 48, 30063–30070, 2020.
27. F. Weng 和 L. Zhao, 最大熵建模中数据稀疏性和数据过拟合的统一处理。美国专利 8,700,403，2014 年 4 月 15 日签发。
28. Oates, T., PERUSE: 一种在时间序列中寻找重复模式的无监督算法，载于：2002 IEEE 国际数据挖掘会议，2002 年 12 月，IEEE，第 330–337 页。
29. Hinton, G.E., Dayan, P., Frey, B.J., Neal, R.M., “醒-睡”算法用于无监督神经网络。Science, 268, 5214, 1158–1161, 1995.


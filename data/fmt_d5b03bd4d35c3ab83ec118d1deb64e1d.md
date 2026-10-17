
# 9.6.2.10 基于时间间隔的新灌水攻击检测

新型灌水攻击检测方法（Bilge et al. 2014）利用时间间隔聚类特定攻击。它使用均值聚类算法分配二分决策树（BDT）来收集攻击画像。通过递归聚类训练数据构建二分决策树，将用户-物品矩阵划分为两个不同的簇。在每个层级计算簇内相关系数。直到叶节点中留有预设数量的用户。通过遍历 BDT 并根据相关系数检测异常。

# 9.6.3 物品检测

尚未引入用于检测物品的技术。

# 9.6.4 攻击画像与物品检测

这种技术设计用于检测攻击画像和物品。

## 9.6.4.1 双检测器 (DMD) 与异构网络 (HIN)

双检测器（DMD）技术（Zhang et al. 2019）通过矩阵分解分解用户-物品矩阵。它设计了许多路径控制异构网络（HIN），并使用 skip-gram 方法获取嵌入。为了获取因子，针对核心性、度和 H 指设计了显著路径。最后，利用嵌入和因子训练检测器以检测攻击画像。

# 9.6.5 使用评分和时间间隔

在这种技术中，利用评分和时间间隔检测灌水攻击。

# 9.6.6 画像检测

此类技术用于检测攻击画像。此类技术的示例包括基于统计模型、UD-HMM 和时间序列检测。

## 9.6.6.1 基于统计模型

统计检测算法（Wang et al. 2018）首先根据其时间顺序评分序列分割每个物品的特征。设计统计分布以获取相关的时间间隔。该技术通常被画分为假设检测和动态时间间隔策略（Xia et al. 2015）。基于成功的攻击会改变目标物品属性的核心假设，该识别器想要获取评分序列的不规则性。在分割序列后采用假设检验来检查不规则组。

## 9.6.6.2 使用隐马尔可夫模型和层次聚类的无监督技术

灌水识别依赖于隐马尔可夫模型（HMM）和层次聚类（Zhang et al. 2018）。该技术通过构建每个用户的评分序列来衡量用户行为的差异。然后使用 HMM 获取每个用户的偏好序列，以计算每个用户的匹配程度。计算每个物品的熵以发现检测攻击画像的用户度。该技术的局限性是在采样数据集上检测协同攻击者时性能并不理想。

## 9.6.6.3 时间序列攻击检测

时间序列攻击检测技术（Zhang et al. 2006）使用大小为 `k*` 的窗口构建物品评分的时间序列。它将连续的评分聚类到不重叠的窗口中。然后确定窗口的样本熵和样本平均值。如果攻击画像数量，可以推导出理论上的最佳窗口大小以用于观察攻击事件。

# 推荐系统中的水纵攻击（Shilling Attack）检测技术

## 9.6.7 攻击物品检测

此类技术用于检测攻击性画像。此类技术的示例包括动态时间分段技术、攻击画像无监督检索（UnRAP）以及数据跟踪。

### 9.6.7.1 动态时间间隔分段技术

动态时间间隔分段技术（Xia et al 2015）用于直接定位被恶意画像攻击的物品。该技术的整个框架包含两个部分，即区间分段和异常区间检测。时间间隔分段技术在检查点（checkpoint）动态地将每个物品的生命周期划分为时间间隔。异常区间检测方法通过假设检验检测异常物品。这种检测技术提高了针对目标转移攻击（target shifting attack）的检测性能。

### 9.6.7.2 攻击画像无监督检索

这种攻击画像无监督检索（UnRAP）检测技术（Si and Li 2020）是一种无监督学习方法。该技术通过分析目标时间点的评分偏差来检测水纵攻击。该技术可以单独检测特定时间点的攻击用户画像。

### 9.6.7.3 数据跟踪

这种数据跟踪检测技术（Qi et al 2018）用于海量信息环境。该技术支持新信息特征。该技术使用扩展卡尔曼滤波，能够快速跟踪并准确预测受支持物品的评分状态，支持了两个新的检测属性：短期平均变化活跃度（SACA）和短期方差变化活跃度（SVCA）。检测器通过比较预测评分与实际评分来检测异常物品。

## 9.6.8 攻击画像与攻击物品检测

目前尚未引入基于攻击画像和攻击物品检测作为输出的技术。

## 9.6.9 优缺点

在本节中，表 9.2 展示了水纵攻击检测技术的优缺点。

## 表 9.2

优缺点

| 水纵攻击检测技术 | 优点 | 缺点 |
| --- | --- | --- |
| 1. 新型水纵攻击检测 (Bilge et al. 2014b)。 | 1. 该方法对几乎所有的填充大小和攻击规模都给出了理想的结果。 | 1. 该方法仅检测特定的三种攻击，即跟众攻击（bandband）、分段攻击和平均攻击。2. 当系统中的所有画像都是真实的时，该技术会将真实画像误判为恶意画像。 |
| 2. 希尔伯特-黄变换与支持向量机 (HHT-SVM) (Fuzhi et al. 2014)。 | 1. 该方法对每个评分序列进行分解。它还提取了基于希尔伯特频谱的特征来表征画像攻击。2. 这里 SVM 区分了真实用户画像和攻击者画像。 | 1. 在这种方法中，一旦出现新类型的攻击，SVM 分类器就需要离线重新训练。 |
| 3. 重新缩放 AdaBoost (Yang et al. 2016)。 | 1. 该方法从用户画像提取设计良好的特征。为了提高检测性能，这些画像是基于各种攻击模型的统计属性建立的。2. 它使得场景执行更容易进行。 | 1. 该方法对于攻击规模和填充大小较小的攻击检测率较低。2. 重缩放 AdaBoost 无法有效检测高权限用户攻击-聚合相似性（PUA-AS）、高权限用户攻击-评分数量（PUA-NR）和高权限用户攻击-入度（PUA-ID）攻击。3. 该技术中通用特征和特定类型特征是提取性特征，不足以描述它们的本质特征。 |
| 4. 均值一致评分偏差 (RDMA) (Si and Li 2020); Burke et al. 2006)。 | 1. 该算法成功检测了随机的、平均的和跟众的攻击画像。 | 1. 它无法检测分段攻击和爱/恨攻击（love/hate attack）。 |
| 5. 带邻域选择的可变长度划分 (VLPNS) (Wei and Shen 2016) | 1. 该技术不是检测可疑的伪造者，而是对它们进行标记并降低假阳性率。这一过程的执行方式使得被误分类的正常用户仍然参与相似性计算。结果是将正常用户误认为伪造者的概率降低了。2. 该方法的预测准确性很高。 | 1. VLPNS 的时间复杂度更高。2. 该算法没有提高假阴性率。 |
| 6. 主成分分析 (PCA) (Deng et al. 2016) | 1. PCA 对孤立攻击（stand attacks）执行非常高效。2. 该方法在识别跟众攻击、随机攻击和平均模型中的画像表现非常好。 | 1. PCA 的适用性受到其推导过程中某些假设的限制。2. 另一种方法是在构建 PCA 协方差矩阵之前进行均值消除过程。 |
| 7. 离散小波变换与支持向量机 (DWTSM) (Karthikeyan et al. 2016) | 1. 该方法形成了单个用户的评分序列。该评分序列参考物品的流行度和新颖性形成。根据时间将用户分类为伪造或真实，因此检测率容易获得。2. 为了获取特征，在评分序列上应用了离散小波变换。 | 1. 该方法应用了奈奎斯特规则。一半的……2. DWT 是计算密集型的。这是很自然的。3. SVM 的维度可能非常高。 |
| 8. 主成分分析与扰动 (Deng et al. 2016)。 | 1. 利用扰动技术可以分离攻击和合法画像。2. 该方法有效、简单且易于实施。 | 1. 在这种方法中，PCA 的适用性受到其推导过程中某些假设的限制。2. 当扰动时，状态值较高。 |

# 机器学习算法在工程中的应用

表 9.2（续）

优缺点

| 水纵攻击检测技术 | 优点 | 缺点 |
| --- | --- | --- |
| 9. 半监督学习水纵攻击检测 (SE-SAD) (Wu et al. 2011)。 | 1. 该技术通过使用极大化（EM）检测画像来改进朴素贝叶斯分类器。2. SE-SAD 非常有效。 | 1. 大数据的分类是一个真正的挑战。2. 训练需要大量的计算。 |
| 10. 支持向量机与物品分析 (SVM-TIA) (Zhou et al. 2016)。 | 1. 该方法缓解了分类中的类别偏差问题。 | 1. 分析潜在攻击画像集，导致真实画像被误判为攻击画像。 |
| 11. 双检测器 (DMD) 与异构信息网络 (HIN) 方法 (Zhang et al. 2019)。 | 1. DMD 利用 HIN 利用客户端-物品和客户端-客户端之间的互连。它实现了协同过滤推荐（CFR）的攻击识别。2. 该方法在关注关系攻击的同时检测评分攻击。3. DMD 对混合攻击也是有效的。 | 1. 该系统需要对不同类型的对象进行测量。 |
| 12. 基于统计模型的检测 (Wang et al. 2018) | 1. 统计模型是物品评分生成过程的理想形式。2. 任何事件的概率可以通过构成统计模型的统计假设计算。 | 1. 该模型需要与数据集评分相关的信息。2. 随着数据规模扩大，时间消耗受到影响。3. 处理困难会导致时间偏差和长度偏差采样。 |
| 13. 使用隐马马尔可夫模型和层次聚类的无监督方法 (UD-HMM) (Fuzhi et al. 2018)。 | 1. 由于于该技术仅考虑当前状态，不需要任何先验知识。2. 它使用 HMM 根据评分对真实用户和攻击者进行聚类。 | 1. 该方法在采样数据集上检测合谋垃圾邮件者时执行效率不高。 |

## 推荐系统中的灌水攻击检测技术

## 表格 9.2（续）

优点与缺点

| 灌水攻击检测技术 | 优点 | 缺点 |
| --- | --- | --- |
| 14. 时间序列攻击检测 (Zhang 等，2006)。 | 1. 通过这些样本平均特征和样本熵特征的时间序列，对其持续时间做出合理假设来暴露攻击事件。<br>2. 只有在已知攻击特征数量的情况下，理论上才能推导出最佳窗口大小。这样做是为了最好识别由攻击引起的分布变化。 | 1. 在攻击期间，有时正常用户的评分模式也会发生，这可能难以识别灌水攻击者。 |
| 15. 动态时间间隔分段技术 (Xia 等，2015)。 | 1. 该技术将每个物品的生命周期分为若干个区间。这是在检查点动态完成的。<br>2. 它通过假设检测异常物品。 | 1. 在这种方法中，提高针对目标偏移攻击（target shifting attack）的检测性能存在存在问题。<br>2. 在识别出每个物品的可疑区间后，无法有效减少攻击的影响。 |
| 16. UnRap (Si 和 Li，2020)。 | 1. 该方法通过分析用户画像在目标物品上的评分偏差来识别灌水攻击特征。 | 1. 它仅针对单次检测攻击用户画像。 |
| 17. 数据跟踪 (Qi 等，2018) | 1. 这种技术采用了大数据处理方法。<br>2. 数据跟踪方法的检测效率很高。 | 1. 数据跟踪不适用于处理分布式系统中的海量数据。 |

## 9.7 结论

推荐系统（RS）是一种帮助用户从互联网选择产品的应用程序。为了减少灌水攻击带来的损害并保持良好的推荐质量，推荐系统的安全性是一个重要问题。然而，由 SA（灌水）方法创建的虚假用户画像可以通过的 SA 检测技术进行准确检测。这些 SA 技术的评分模式与真实用户不同。协同过滤（CFR）是处理信息过载问题最有效的方法之一，但由于系统中插入了各种恶意用户画像，它们非常容易受到大量灌水攻击的影响，从而影响用户推荐。在本章中，首先讨论了画像注入攻击技术、推荐系统中的协同过滤以及灌水攻击检测方案。其次，根据评分参数和其工作的时间间隔两个参数对灌水攻击检测技术进行了分类。灌水攻击检测技术还根据其输出算法进行了分类，如攻击特征检测、攻击物品检测和攻击画像检测。对每种灌水攻击检测技术都进行了简要讨论。对这些技术进行了分析，并比较了它们的优缺点。

## 9.7.1 未来方向

未来的研究方向在于改进这些灌水攻击检测技术的缺点。例如在动态时间间隔分段技术中，针对目标偏移攻击的检测性能还需要增强。数据跟踪技术的缺点是它不适用于处理分布式系统中的巨数据。HHT-SVM 的问题在于，当进行新型攻击时，很难检测到攻击特征。SVM 还需要在离线进行重新训练。克服这些问题是未来的发展方向。

## 参考文献

- Bhaumik R, Burke R, Mobasher B (2007). Effectiveness of crawling attacks against web-based recommender systems. Proceedings of the 5th workshop on intelligence techniques for web personalization (ITWP-07).

- Bhaumik R, Mobasher B, Burke R (2011). A clustering approach to unsupervised attack in collaborative recommender systems. Proceedings of the International Conference on Data Mining (DMIN). The Steering Committee of the World Congress in Computer Science, Computer Engineering and Applied Computing (World Comp), p. 1.

- Bhaumik R, Williams C, Mobasher B, Burke R (2006). Securing collaborative filtering against malicious attacks through anomaly detection. In Proceedings of 4th Workshop on Intelligent Techniques for Web Personalization (ITWP'06), Boston. vol. 6.

- Bilge A, Gunes I, Polat, H. (2014a) Robustness of privacy-preserving recommendation schemes. Expert Syst Appl, 41(8): 3671–3681.

- Bilge A, Ozdemir Z, Polat H (2014b). A novel attack detection method. Proc Computer Science, 31: 165–174.

- Bilge, Polat H. (2013) A comparison of clustering-privacy-preserving collaborative filtering schemes. ApJ Soft Comput, 13(5): 2478–2489.

- Rourke, Mobasher, Williams C. (2006). Classification features for attack detection in collaborative recommender systems. International Conference on Knowledge Discovery and Data Mining, pp. 17–20.

- Chirita P-A, Nejdl W, Zamfir C (2005). Preventing shilling attacks in online recommender systems. Proceedings of 7th annual ACM workshop on Web information and data management, pp. 67–74.

- Deng, J. J., Zhang, F., & Wang, S. (2016). Shilling attack detection in collaborative recommender system by PCA and perturbation. In International Conference on Wavelet Analysis and Pattern Recognition (CWAPR), pp. 213–218.

- Fuzhi Z, Zen Z, Peng Z (2013). UD-HHM: An unsupervised method for shilling attack based on hidden Markov model and hierarchical clustering. Knowledge-Based Systems, 148: 146–166.

- Fuzhi Z, Zhou Q (2014). HHT-VS: An online method for detecting profile injection in collaborative recommender systems. Knowledge-Based Systems 65: 96–105.

- Gunes I, Kaleli B, Bilge B, et al. (2014). Shilling attacks against recommender systems: a comprehensive survey. Artificial Intelligence Review, 42(4): 767–799.

- Jolliffe I. (2011). Principal Component Analysis. Springer, Berlin, pp. 1094–1096.

- Karthikeyan P, Selvi ST, Neeraja G, Vincent A, Abinaya V. (2017, January). Prevention of shilling attacks against recommender systems using discrete wavelet transform and vector machine. In 2016 International Conference on Parallel and Distributed Computing, Applications and Technologies, pp. 99–104. (注：原文此处为页码99-104)


- [6] Covington P, Adams J, Sargin E. Deep neural networks for recommendations. In: Proceedings of the 10th ACM Conference on Recommender Systems. 2016.

- [7] Cheng HT, Koc L, Harmsen J. Wide & deep learning. In: Proceedings of the 1st Workshop on Deep. ACM; 2016.

- [8] Okura S, Tagami Y, Ono S. Embedding-based recommendation for millions of users. In: Proceedings of the 23rd ACM SIGKDD Conference on Knowledge Discovery and Mining.; 2017.

- [9] Salakhutdinov R, Mnih A, Hinton G. Restricted Boltzmann machines for collaborative filtering. In: Proceedings of the 24th International Conference on Machine Learning. 2007.

- [10] Sedayn S, Menon A, Sanner S. Autoencoders meet collaborative filtering. In: Proceedings of the 24th International Conference on World Web. ACM; 2015.

- [11] He X, Liao L, Zhang H. Neural collaborative filtering. In: Proceedings of the 26th International Conference on World Web. 2017.

- [12] Wu CY, Ahmed A, Beutel A. Recurrent neural networks for recommendation. In: Proceedings of The ACM Conference on Search and Mining. 2017.

- [13] Wang H, Wang N, Yang Y. Collaborative deep learning for recommender systems. In: Proceedings of the 21st ACM SIGKDD Conference on Knowledge Discovery and Mining. ACM; 2015.

- [14] Li X, She J. Collaborative variational autoencoder for recommender systems. In: Proceedings of the 23rd ACM SIGKDD Conference on Knowledge Discovery and Mining. ACM; 2017.

- [15] Koren Y, Bell R, Volinsky C. Matrix factorization techniques for recommender systems. Computer. 2009;42(8):30–37.

- [16] Liu B, Fu Y, Yao Z. Learning geographical preferences for point-interest recommendation. In: Proceedings of the 19th ACM SIGKDD Conference on Knowledge Discovery and Mining. ACM; 2013.

- [17] Chanie AJ, Blei DM, Eliassi-Rad T. A probabilistic model for using social networks in personalized item recommendation. In: Proceedings of the 9th ACM Conference on Recommender Systems. ACM; 2015.

- [18] Hofmann T, Puzichha J. Latent class models for collaborative filtering. In: IJCAI vol. 99, 1999. 688–693.

- [19] Popescul A, Pennock DM, Lawrence S. Probabilistic models for unified collaborative and content-based recommendation in sparse-data environments. In: Proceedings of the Seventeenth Conference on Uncertainty in Artificial Intelligence. Morgan Kaufmann Publishers Inc.; 2001. 437–444.

- [20] Ye M, Liu X, Lee WC. Exploring social influence for recommendation: A generative model approach. In: Proceedings of the 35th ACM SIGIR Conference on Research and Development in Information Retrieval. ACM; 2012. p. 671–680.

- [21] Yuan Q, Cong G, Ma Z. Who, where and when what: Discover spatio-temporal topics for twitter users. In: Proceedings of the 19th ACM SIGKDD Conference on Knowledge Discovery and Mining. ACM; 2013, p. 605–613.

# 第7章

## 文本、音频、图像和视频等非结构化大数据的推荐算法

Madjid Khalilian1, Mahshid Alsadat Ehsaei1 和 Salomeh TaherFard1

最近，推荐系统（RS）在帮助用户从海量数据中选择理想产品方面发挥了重要作用。由于大数据分析的产生，客户、和服务在线信息的数量不断增加，这对服务推荐系统成为了一个问题。非常成功的方法了视频、音乐、图像、书籍等多种推荐任务。

推荐算法需要各种参数来为新用户提供建议，而这正是推荐系统的局限性和挑战所在。本章将讨论非结构化大数据的推荐算法及其挑战。

推荐系统是一项创新技术，它将基于内容的应用程序转变为以客户为中心。这种方法可以确定客户确切想要什么；可以是数据，也可以是项目。推荐技术中收集和计算信息的特征，让用户和客户之间有更好的理解 [1]。射频识别和其他传感器产生了大量数据。因此，大数据技术正被用于在处理海量数据时生成推荐建议。有许多应用程序使用了物品协同过滤（CF）。例如，业务领域、电子商务、在线购物中的物品推荐、有趣网站的推荐、网页浏览、发现音乐、电影等应用。集体智能方面的巨大努力是推荐系统的根源。推荐系统的出现可以追溯到20世纪90年代，当时推荐仅基于评分结构。近年来，出现了许多方法来识别用户对特定物品的兴趣，包括标记、投票、评论，甚至是用户提供的点赞数。此外，它也可以是以博客中写的评论、关于物品的描述或对在线社区的回复的形式存在。无论偏好是如何传递或呈现的，它们应该被定义为 [2] 中描述的数值值。

134 大数据推荐系统，第1卷

![](img/6d0ce7dba01af52e1c2fae47d5b04a05_150_0.png)

## 7.1 推荐方法

各种推荐方法可以根据它们为做出适当推荐而开发的或或知识源归分为不同的类型。分类的图表表示如图7.1 所示。它们被分类为 [1]

- 基于内容的推荐，
- 协同推荐，
- 基于知识的推荐，
- 人口统计学推荐和
- 混合推荐。

### 7.1.1 基于内容的推荐

基于内容的推荐，推荐的物品是基于用户之前偏好的物品 [1]。在创建推荐应用时，内容是推荐应用的基础。这些推荐完全基于物品描述，而不是其他用户的相似性。机器学习算法正被用于根据特征因素推导出用户偏好模型。有各种可获得的内容，如文章、照片、视频、博客、维基、分类术语、投票和列表 [3]。

非结构化大数据的推荐算法 135

它可以是

- 基于内存/启发式的——术词频-逆文档频率（TF–IDF）文本检索方法，或
- 基于模型的——使用决策树、神经网络、贝叶斯分类器、基于聚类或基于向量的表示法。

有许多可用方法来研究基于内容的推荐内容；然而，如果内容不包含足够的信息，基于内容的推荐将无法保证准确的预测。所列面临的各种局限性如下：(1) 限制的内容分析：检查能够代表整个内容的足够特征集是一项困难的工作。如果文档包含某些术语和短语，也很难以检查内容是好是坏。此外，它不能保证文档或物品的质量。对于多媒体数据，音频流、视频流和图形图像，提取特征变得非常复杂。(2) 内容重叠：检查相同事件的不同标题是困难的。例如，基于内容的推荐可能是相同的。(3) 冷启动：在冷启动情况下，缺乏信息使得推荐变得困难。有两种冷启动：

- 新用户：新用户进入系统没有历史
- 新物品：新物品进入系统没有评分

# 非结构化大数据的推荐算法 137

表 7.1 协同过滤技术

| CF 技术 | 基于内存的协同过滤（基于邻域） | 基于模型的协同过滤 | 混合协同过滤 |
|---|---|---|---|
| 代表性算法 | 基于用户的 CF、基于物品的 CF | Slope-one CF、维度缩减（矩阵分解）例如 SVD | 基于内存和基于模型的 CF 结合 |
| 优点 | 实现简单；可以方便且增量地添加新数据；无需考虑推荐物品的内容；对于相关物品具有良好的可扩展性 | 更好地解决了稀疏性和可扩展性问题；提高预测性能 | 克服 CF 的局限性（如稀疏性）；提高预测性能 |
| 局限性 | 依赖于人工评分；新用户和物品存在冷启动问题；评分矩阵稀疏性问题；大型数据集的可扩展性有限 | 模型构建成本高；预测性能与可扩展性之间的权衡；降维技术（SVD）中的信息丢失 | 实现的复杂性和成本增加 |

原始技术 [3]。表 7.1 描述了协同过滤（CF）及其优缺点。

### 7.1.3 基于知识的推荐

基于知识的推荐系统（RSs）根据物品特征和用户画像向用户推荐所需的物品。它充分利用关于用户和产品的知识，并定义哪些产品符合用户的需求。这类推荐系统需要对物品和用户进行彻底建模才能正常工作；必要知识的获取及其随时间的维护是其进展的共同障碍。其优势在于，推荐不依赖于任何用户评分数据库，因此不会产生冷启动问题。此外，它们不需要大量数据即可提供或计算推荐；与其他系统相比，极少数的用户即可。但当需要工程师的知识库来为用户提供有帮助的推荐时，就出现了一个缺点，这些知识需要定期更新，以适应不断变化的消费者评分和偏好 [9]。

## 7.1.4 人口统计学推荐

年龄、性别、社会阶层、教育、位置等人口统计数据可以根据构成用户画像的人口统计数据被显式或隐式地利用。人口统计学画像可以推荐相同的物品。例如，青少年显然偏好不同于老年人的产品；社会富裕层在类型和物品质量上可能不同，并且绝对愿意为上述特征支付更多费用。因此，人口统计学推荐考虑了用户的个人特征并做出推荐。人口统计学方法在对任何物品进行评分之前不应用用户物品评分；新用户也能从接收推荐中受益。该技术独立于物品知识及其特征的领域。为了收集人口统计数据，该方法面临隐私问题，这些问题可以归类为技术的缺点。对于高度个性化的推荐，人口统计学分类显得过于基础 [10]。

### 7.1.5 混合推荐

目前的推荐系统使用非常简单的技术，如基于内容的、协同的、人口统计学的、基于效用的和基于知识的。单独使用这些技术会导致产生优缺点。事实是，这为混合推荐系统的研究提供了总灵感，混合系统通过合并技术来增强性能。人们已经研究了许多混合方法，即命名为加权、切换、特征组合、特征增强、元级、级联和混合的混合技术。描述如下 [11]：

- 加权（Weighted）：分别应用协同和基于内容的系统，随后对它们的预测结果进行融合。
- 切换（Switching）：系统应用特定的切换准则在两个处理相似对象的推荐系统之间切换。
- 特征组合（Feature combination）：将与不同推荐系统数据源相关的特征收集到单一推荐算法中。
- 特征增强（Feature augmentation）：我们有时利用一个系统的输出作为另一个系统的输入特征；例如，我们可以使用生成的模型通过另一个模型形成特征。
- 元级（Meta-level）：在这里，一个特征可以作为另一个的输入，例如由一个推荐系统学习的模型。
- 级联（Cascading）：在此类别中，一个推荐系统改进另一个系统呈现的结果。
- 混合（Mixed）：同时整合两种或更多技术；例如基于内容和协同过滤。

协同过滤、基于内容和基于知识的方法是最常用的推荐技术 [3]。

## 7.2 大数据分析

如今，所有机器自动系统产生的大数据已成为计算机行业面临的一项挑战。在数据的存储、管理和检索（即大数据的）方面存在许多关注。主要问题在于如何应用这些数据来增强业务并提高人们的生活水平。收集、组织和分析大量数据以确定各种趋势和其他有用信息的过程被称为大数据分析。大数据分析的首要目标是让组织在业务上做出更好的决策，帮助进行未来预测，并为他们提供组织内大量交易的分析并更新其所使用的数据 [12]。通过预测分析可以从当前数据中提取信息以预测未来的结果和趋势或确定模式；这并不是预言，而是以可接受的可靠水平预测未来可能发生的情况，包括“如果……那么……”的情景和风险考虑。预测分析的应用广泛，如客户关系管理、临床决策支持、采集分析、交叉销售、客户留存、直接营销、欺诈检测、风险管理和承保 [12]。

### 7.2.1 文本分析

数据库中的信息以文本形式存在。由于需要大量自动工具来分析大型文本数据，有效提取重要信息或手动分析这些上下文上是不可能的。从文本数据中获取主要信息的过程被称为文本分析或文本挖掘。该程序用于从文本、模式和事件中提取重要信息。文本分析广泛用于理解需求、情感。

#### 7.2.1.1 文本分析的步骤

1. 文本（Text）：数据是非结构化的。
2. 处理（Processing）：数据被转换。
3. 文本转换（Text transformation）：数据具有格式了。
4. 特征选择（Feature selection）：数据被分类。
5. 聚类（Clustering）：数据被分组。

# 非结构化大数据的推荐算法 141

![](img/6d0ce7dba01af52e1c2fae47d5b04a05_157_0.png)

图 7.2 兴趣图的构建。阅读历史是文本序列。空心箭头表示文本扫描的方向。兴趣图中的节点和边都经过了扫描增强。虚线箭头是标注的指示。实线箭头表示兴趣图的更新及构建。虚线框是富化过程的指示。

节点和边反映了对链接对象的兴趣。每个链接的作用是将两个节点连接成一个基本单元。复合基本单元形成链接结构。兴趣图中的基本单元与顶点之间的重叠定义了对文本中短期（或长期）链接兴趣的程度。如果文本中即使只有一句话包含两个节点，也会出现一个基本单元。提到的重叠包含三个属性：基本单元的数量、重叠中基本单元的短期（长期）边权重（一个基本单元可能由多个句子组成，包含一个基本单元的句子可能超过一个），以及文本中共同基本单元出现的次数。该方法使用边匹配来评估文本的短期（或长期）链接兴趣程度。

- **推荐机制**

推荐机制通过合并四个基础角度来对候选文本进行排序。每个基础角度都对应文本的一个排名。对于由 $k$ 个基础角度连接的复合体以及这 $k$ 个基础角度对应的 $k$ 个排名，内容具有 $k$ 维排名数组 (RA)，它由 $k$ 部分组成，分别对应 $k$ 个位置上内容的 $k$ 个区域，其中 $RA = (r_1, r_2, ..., r_k)$。一个 RA 可以通过系数向量 $CV = (c_1, c_2, ..., c_k)$ 转换为一个值（综合排名，$Ir$），其中 $c_1 + c_2 + ... + c_k = 1$ 且 $c_1, c_2, ..., c_k$ 处于 $[0, 1]$ 之间。

```
$Ir = \overrightarrow{CV} \times \overrightarrow{RA} = \sum_{i=1}^{k} c_i * r_i \quad (7.1)$
```

然后我们就能根据综合排名来读取排名的文本。注意，综合排名本身可能不是整数。$CV$ 的默认值为 $(1/k, 1/k, ..., 1/k)$。为了提供更具体的服务，用户可以自由调节向量中的系数。推荐机制能够保留系数向量之前的设置以供未来使用。下面提到了推荐机制可以处理的两个常见角度：

1. 其中一个角度负责短期感兴趣对象的新信息。想象一个对美国经济史感兴趣的用户，正在阅读关于富兰克林·罗斯福在经济政策主题上的各种文本。该用户可能对罗斯福（对象）产生兴趣。然后该用户倾向于获取更多关于罗斯福的信息，但在其他领域，可能是关于他在二战中的事务。这里的角度由意义的维度组成：(1) “新”代表高排名文本，意味着它不应该涉及经济（这由低长期重的低节点匹配度决定），(2) “短期感兴趣对象”意味着高排名文本应该涉及罗斯福（这由高短期权重的高节点匹配度决定）。因此，复合角度是短期对象兴趣和长期对象兴趣的结合。

2. 另一个角度负责持有长期感兴趣对象的新链接结构。例如，一个对大卫·贝克姆有长期兴趣的用户应该发现他尚未知道的额外信息。满足复合角度涉及(1) 满足长期对象兴趣（由高长期权重的高节点匹配度维持），(2) 不满足短期链接兴趣（由低短期权重的低边匹配度维持），以及 (3) 不满足长期链接兴趣（由低长期权重低边匹配度维持）。

该方法具有以下所有特征：

- 1. 该方法能够区分四个基础兴趣角度；它是通过用户的阅读历史实现的。

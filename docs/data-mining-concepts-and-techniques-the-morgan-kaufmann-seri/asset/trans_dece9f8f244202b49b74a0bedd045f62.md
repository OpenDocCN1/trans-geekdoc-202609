

- 8.19. 讨论纯度、熵以及基于Jaccard系数的方法在多大程度上满足外部聚类评估方法的四个基本要求。

### 8.8 参考书目

由于其广泛的应用，聚类分析在40多年的时间里，跨多个学科进行了深入研究。大多数模式分类和机器学习方面的书籍都包含聚类分析或无监督学习的章节。有几本教材专门介绍聚类分析方法，包括Hartigan [Har75]；Jain和Dubes [JD88]；Kaufman和Rousseeuw [KR90]；以及Arabie、Hubert和De Soorte [AHS96]。还有许多关于聚类方法不同方面的综述文章。近期的综述包括Jain、Murty和Flynn [JMF99]；Parsons、Haque和Liu [PHL04]；Xu和Wunsch [XW05]；Jain [Jai10]；Greenlaw和Kantabutra [GK13]；Xu和Tian [XT15]；以及Berkhin [Ber06]。

对于划分方法，k-means算法最初由Lloyd [Llo57]提出，随后由MacQueen [Mac67]介绍。Arthur和Vassilvitskii [AV07]提出了k-means++算法。Kanungo等人 [KMN+02]给出了一种过滤算法，该算法使用空间分层数据索引来加速聚类均值的计算。

PAM和CLARA的k-medoids算法由Kaufman和Rousseeuw [KR90]提出。k-modes（用于聚类名义数据）和k-prototypes（用于聚类混合数据）算法由Huang [Hua98]提出。k-modes聚类算法也由Chaturvedi、Green和Carroll [CGC94,CGC01]独立提出。CLARANS算法由Ng和Han [NH94]提出。Ester、Kriegel和Xu [EKX95]提出了使用高效空间访问方法（如R*-tree）和聚焦技术进一步提高CLARANS性能的技术。Bradley、Fayyad和Reina [BFR98]提出了一种基于k-means的可扩展聚类算法。Dhillon、Guan和Kulis [DGK04]开发了核k-means方法。

Day和Edelsbrunner [DE84]对凝聚式层次聚类算法进行了早期的综述。Murtagh和Contreras [MC12]提供了关于层次聚类的更近期综述。Zhao、Karypis和Fayyad [ZKF05]综述了面向文档数据库的层次聚类算法。Kaufman和Rousseeuw [KR90]介绍了凝聚式层次聚类（如AGNES）和分裂式层次聚类（如DIANA）。Rohlf [Roh73]使用最小生成树开发了层次聚类的核心思想。改进层次聚类方法聚类质量的一个有趣方向是将层次聚类与基于距离的迭代重定位或其他非层次聚类方法相结合。例如，Zhang、Ramakrishnan和Livny [ZRL96]提出的BIRCH，在应用其他技术之前，先使用CF树进行层次聚类。层次聚类还可以通过复杂的链接分析、变换或最近邻分析来执行，例如Guha、Rastogi和Shim [GRS98]提出的CURE；Guha、Rastogi和Shim [GRS99]提出的ROCK（用于聚类名义属性）；以及Karypis、Han和Kumar [KHK99]提出的Chameleon。

Ward [War63]提出了Ward准则。Murtagh和Legendre [ML14]综述了Ward准则的实现方法。Lance和Williams [LW67]提出了Lance-Williams算法。Friedman [Fri03]以及Heller和Ghahramani [HG05]开发了一种遵循普通链接算法并使用概率模型定义聚类相似性的概率层次聚类框架。

对于基于密度的聚类方法，DBSCAN由Ester、Kriegel、Sander和Xu [EKSX96]提出。Campello、Moulavi、Zimek和Sander [CMZS15]开发了DBSCAN*和HDBSCAN。Ankerst、Breunig、Kriegel和Sander [ABKS99]开发了OPTICS，这是一种聚类排序方法，可在无需担心参数指定的情况下促进基于密度的聚类。基于一组密度分布函数的DENCLUE算法由Hinneburg和Keim [HK98]提出。Hinneburg和Gabriel [HG07]开发了DENCLUE 2.0，其中包含一种用于高斯核的新爬山过程，可自动调整步长。

由Wang、Yang和Muntz [WYM97]提出的STING是一种基于网格的多分辨率方法，用于在网格单元中收集统计信息。由Sheikholeslami、Chatterjee和Zhang [SCZ98]开发的WaveCluster是一种多分辨率聚类方法，通过小波变换转换原始特征空间。

Gibson、Kleinberg和Raghavan [GKR98]；Guha、Rastogi和Shim [GRS99]；以及Ganti、Gehrke和Ramakrishnan [GGR99]研究了可扩展的名义数据聚类方法。还有许多其他聚类范式。例如，模糊聚类方法在Kaufman和Rousseeuw [KR90]、Bezdek [Bez81]以及Bezdek和Pal [BP92]中有所讨论。

对于高维聚类，Agrawal、Gehrke、Gunopulos和Raghavan [AGGR98]提出了一种基于Apriori的维度增长子空间聚类算法CLIQUE。它集成了基于密度和基于网格的聚类方法。

近期研究已扩展到流数据聚类（Babcock等人 [BBD+02]）。Guha、Mishra、Motwani和O'Callaghan [GMMO00]以及O'Callaghan等人 [OMM+02]提出了一种基于k-median的数据流聚类算法。Aggarwal、Han、Wang和Yu [AHWY03]提出了一种用于演变数据流聚类的方法。Aggarwal、Han、Wang和Yu [AHWY04]提出了一种高维数据流投影聚类框架。

聚类评估在一些专著和综述文章中有所讨论，例如Jain和Dubes [JD88]以及Halkidi、Batistakis和Vazirgiannis [HBV01]。Hopkins统计量由Hopkins和Skellam [HS54]提出。例如，Sugar和James [SJ03]以及Cordeiro De Amorim和Hennig [CH15b]讨论了确定数据集中聚类数量的问题。

现有的聚类质量评估方法已得到广泛研究。一些近期研究包括Meilă [Mei03,Mei05]以及Amigó、Gonzalo、Artiles和Verdejo [AGAV09]。本章介绍的四个基本标准在Amigó、Gonzalo、Artiles和Verdejo [AGAV09]中制定，而某些单独的标准此前也有提及，例如在Meilă [Mei03]和Rosenberg和Hirschberg [RH07]中。Bagga和Baldwin [BB98]引入了BCubed度量。轮廓系数在Kaufman和Rousseeuw [KR90]中有所描述。

## 聚类分析：高级方法

9

你在第8章学习了聚类分析的基础知识。在本章中，我们将讨论聚类分析的高级主题。具体来说，我们将从四个主要视角进行探讨：

- **基于概率模型的聚类**：第9.1节介绍了一个通用框架和一种推导聚类的方法，其中每个对象被分配一个属于某个聚类的概率。基于概率模型的聚类广泛应用于许多数据挖掘应用中，例如文本挖掘和自然语言处理。

- **高维数据聚类**：当维度较高时，常规距离度量可能会被噪声主导。高维数据上的聚类分析是一个重要领域。本章介绍了通用原则和一些基本方法。第9.2节介绍了高维数据聚类分析的基本框架。第9.3节讨论了双聚类，它同时对对象和属性进行聚类，并在生物信息学和推荐系统等领域有许多应用。第9.4节讨论了用于聚类的降维方法。

- **图和网络数据聚类**：图和网络数据在在线社交网络、万维网和数字图书馆等应用中越来越流行。在第9.5节中，你将学习图和网络数据聚类的关键问题，包括相似性度量和聚类方法。

- **半监督聚类**：在迄今为止的讨论中，我们不假设聚类中有任何用户知识。然而，在某些应用中，可能有各种用户知识可用，这些知识可以用于加强聚类分析。例如，用户可以提供源于背景知识或待聚类对象空间分布的有用约束。半监督聚类提供了一个通用框架来容纳此类背景知识。你将在第9.6节学习如何进行半监督聚类。

在本章结束时，你将对高级聚类分析的问题和技术有很好的掌握。

在本章中，如果不涉及对象的向量表示，我们将对象的变量用斜体表示。如果涉及向量表示和矩阵运算，则使用粗体变量。

### 9.1 基于概率模型的聚类

在迄今为止讨论的大多数聚类分析方法中，每个数据对象只能被分配给若干聚类中的一个。这种严格的聚类分配在某些应用中是必需的。


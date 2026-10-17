
# 参考文献

Han, J., Pei, J., and Yin, Y. 2000. Frequent pattern candidates without candidate generation. *Proceedings of the 2000 ACM SIGMOD International Conference on Management of Data*, SIGMOD, Dallas, TX, pp. 1–12.

He, W et al. 2012. Mining routes from GPS data for ride recommendations. *Proceedings of the ACM SIGKDD International Workshop on Urban Computing*, UrbComp, Beijing, China, pp. 79–86.

Hipp, J., Gunter, U., and Nakahaizadeh, G. 2000. Algorithms for association rule mining—A general survey and comparison. *SIGKDD Exploration Newsletter*, 2(1), 58–64.

Huang, Y. and Powell, J. 2012. Detecting regions of disequilibrium in cities under uncertainty. *Proceedings of the ACM International Conference on Advances in Geographic Information Systems*, ACM-GIS, Redondo Beach, CA, pp. 139–148.

Jiang, S., Schubert, J et al. 2017. Covering urban spatial-temporal structure from human activity patterns. *Proceedings of the ACM SIGKDD International Workshop on Urban Computing*, UrbComp, Beijing, China, pp. 95–102.

Kazerani, A. and Winter, S. 2009. When between centrality explain traffic flow. *Proceedings of the 12th AGILE International Conference on GIS*, Hanover, Germany.

Leung, I. X., Chen, S.-Y., and et al. 2011. Intra-city urban network and traffic flow analysis from GPS mobility trace. http://arxiv.org/abs/1105.5839. Last accessed May 25, 2013.

# 订单记录上的高效序列挖掘

Li, B., Zhan, D. et al. 2011. Hunting or waiting? Discovering passenger-strategies from a large-scale real-world taxi dataset. *IEEE International Conference on Pervasive Computing and Communications Workshops*, Seattle, WA, pp. 63–68.

Metropolitan Transportation Authority (MTA). 2013. Subway and bus riding. Online at http://www.mta.info/info/facts/rideship.

Port Authority of New York & Jersey, 2012. LaGuardia Airport. Online at http://www.pj.gov/airports/lagardia.html. Accessed October 29, 2012.

Powell, J. W., Huang, Y. et al. 2011. Reducing taxi cruising time using spatial-temporal maps. *Proceedings of the International Symposium on Advances in Spatial and Temporal Datasets*, SSDAS, Minneapolis, MN, pp. 242–260.

Qi, G., Li, X. et al. 2011. Measuring social functions of cities from large-scale taxi behaviors. *IEEE International Conference on Pervasive Computing and Communications*, PerCom, Seattle, WA, pp. 384–388.

Richer, K.-F., Schmidt, F. and Laub, P. 2012. Semantic trajectory reconstruction: Representing urban movement in cell. *Journal of Spatial Information* 4(1), 1–30.

Uddin, M., Rishankar, C., and Tostras, V. 2011. Finding edges from trajectory data. *Proceedings of the International Conference on Mobile Data Management*, MDM, Ule, Sweden, pp. 39–48.

Wei, L.-Y., Zheng, Y., and Peng, W.-C. 2012. Constructing popular routes from uncertain trajectories. *Proceedings of the ACM International Conference on Knowledge Discovery and Data Mining*, KDD, Beijing, China, pp. 195–203.

Yan, Z., Chakraborty, D. et al. 2011. SemTi: A framework for semantic annotation of heterogeneous trajectories. *Proceedings of the International Conference on Extension Technology*, EDB, Uppsala, Sweden, pp. 259–270.

Yuan, J., Zheng, Y. et al. 2010. T-drive: Direction biases by taxi trajectories. *Proceedings of the ACM International Conference on Advances in Geographic Information Systems*, ACM-GIS, San Jose, CA, pp. 91–108.

Yuan, J., Zheng, Y. et al. 2011a. Driving knowledge from the physical world. *Proceedings of the ACM International Conference on Knowledge Discovery and Data Mining*, KDD, San Diego, CA, pp. 316–324.

Yuan, J., Zheng, Y. et al. 2011b. Where to find my passenger. *Proceedings of the 13th International Conference on Ubiquitous Computing*, UbiComp, Beijing, China, pp. 109–118.

Yuan, J., Zheng, Y., and Xue, X. 2012. Discovering different functions in a city using human mobility and *Proceedings of the ACM International Conference on Knowledge Discovery and Data Mining*, KDD, Beijing, China, pp. 186–194.

Zhang, D., Li, N. et al. 2011. IBAT: Detecting anomalous trajectories from GPS traces. *Proceedings of the 13th International Conference on Ubiquitous Computing*, UbiComp, Beijing, China, pp. 99–108.

Zhang, J. 2012. Smarter detection and deeper understanding of large-scale taxi trip records: A case study of NYC. *Proceedings of the First International Workshop on Urban Computing*, UrbComp, Beijing, China, pp. 157–162.

Zhang, J., Camille, K. et al. 2012. USOD-DB: A database system to manage large-scale urban trips origin-destination data. *Proceedings of the First International Workshop on Urban Computing*, UrbComp, Beijing, China, pp. 163–171.

Zheng, Y., Liu, Y. et al. 2011. Urban computing with taxis. *Proceedings of the 13th International Conference on Ubiquitous Computing*, UbiComp, pp. 89–98.

Zheng, Y. and Zhu, X. 2011. *Computing with Spatial Trajectories*. Springer, New York.

Ziebart, B. D. et al. 2008. Naggle like a cab: Probabilistic reasoning from observed context-aware behavior. *Proceedings of the 10th International Conference on Ubiquitous Computing*, UbiComp, Seoul, South Korea, pp. 322–331.

# 11 地理信息与社交媒体

## 新大数据挑战

Arie Croitoru, Andrew Crooks, Jacek Radzikowski, Anthony Stefanidis, Ranga R. Vatsavai, and Nicole Wayant

## 11.1 引言：社交媒体与环境地理信息

在 Web 2.0、无处不在以及相应技术进步的推动下，社交媒体在过去的十年中变得极其流行。“社交媒体”一词指的是广泛的数字交互和信息交换平台。广而言之，这包括博客和微博客（例如 Blogger、WordPress、Twitter、Tumblr 和微博）、社交网络服务（例如 Facebook、Google+ 和 LinkedIn）以及多媒体内容共享服务（例如 Flickr 和 YouTube）。无论每个平台有何特殊之处，这些社交媒体都有共同的目标，即让公众能够贡献、传播和交换信息（Kaplan and Haenlein, 2010）。这正是大众所做的，使得社交媒体内容成为数字宇宙中一个庞大且快速增长的部分。在 2012 年，其系统处理着 PB 级的数据（InfoQ, 2012），每天处理超过 500 TB 数据的 25 亿个内容元素（TechCrunch, 2012）。

这些社交媒体内容通常带有地理标记，形式为创建这些动态的精确坐标。根据我们小组开发的用于收集和分析社交媒体内容的 `GeoSocial` 系统（Croitori et al., 2012）的研究，我们观察到平均地理标记（精确坐标级别）的推文比例在 0.5% 到 3% 之间。取决于研究区域和条件，这一比例可能会更高。例如，日本灾难后的一个数据集显示，16% 的推文是精确地理标记的（Stefanidis et al., 2013）。这归因于日本数据反映了一个处于移动的技术先进国家（海地震及随后的核事故），当时用户使用手机发布推文。这两种情况，即移动（及其他位置感知）设备的普及和发布技术的出现，都是产生更高比例地理标记内容的条件。除了精确地理标记外，我们观察到大约 40%–70% 带有描述性文本的推文涉及用户的位置。关于社交媒体上发布的图像和视频，最近的研究表明，4.5% 的 Flickr 和 YouTube 内容带有地理标记（Franklin and Sommer, 2015）。

社交媒体的地理内容代表了一种新类型的地理信息。它不属于公民明确且有目的地贡献地理信息以更新或扩展地理数据库这一过程的既有社区定义（Fritz et al., 2009）或自愿地理信息（VGI）（Goodchild, 2007）。这种地理信息的类型可以

## 地理信息科学与社交媒体

从社交媒体中采集的数据可以被称为环境地理信息（AGI）（Stefanidis 等人，2013b）；它被嵌入在这些信息流的内容中，通常跨越多个条目的内容而非单条条目，并且需要被提取。尽管如此，它具有重要意义，因为它可以即时传达有关新兴问题的信息。同时，它为理解社会内部复杂的社交网络和文化动态提供了无与伦比的视角，并捕捉了人类景观的时间演变。

此外，社交媒体信息流正变得越来越地理空间化，意义在于它们具有实质性的地理空间分量。同时，我们可以通过研究交互行为来观察用户社区的底层结构。例如，我们可以识别推文在用户社区内被转发的轨迹，或者我们可以构建一个描述大量用户之间关注关系的社交网络。这让我们首次能够将人们的物理存在与其在线活动相结合进行探索，使我们能够在大规模上将网络空间和空间力量联系起来。这些信息为社交媒体提供了额外内容（即空间），并为分析这些数据提供了背景（即主题和情感基调）。例如，我们识别了参与特定讨论的社区热点以及它们与其他社区的交互。因此，地理空间分析本质上是复杂的，因为它包含了对内容、连接、位置及其随时间变化的研究。正如此，它代表了地理新兴的地理信息替代方案，通过其规模和丰富性，为理解动态事件和形势开启了新的途径和研究挑战。

本章的目标是介绍与大地理空间数据相关的某些特定挑战，以便理解相应的分析和处理需求。因此，本章的结构如下：在第 11.2 节中，我们讨论社交媒体相对于传统空间数据的特定特征。在第 11.3 节中，我们将关注社交媒体内容的复杂性，使用代表性示例。在第 11.4 节中，我们将处理多样化内容，以实现对多个社交媒体信息流的整合地理空间分析。最后，在第 11.5 节中，我们将展望未来展望。

## 11.2 大地理社会数据的特征

大数据的最新定义（TechAmerica, 2012）已超越了单纯的数据，通过另外两个额外属性来识别它，即图 11.1 所示的速度（`velocity`）和多样性（`variety`）。在这种背景下，速度不仅指数据的产生速率，还指其内容的时效性以及对及时分析的需求。以流式速率处理数据并提取信息的需求，其计算需求远高于对同类信息进行周期性（例如每日或每周）处理（例如在处理遥感数据时可能的情况）。另一方面，多样性指的是所处理的数据源和类型的丰富性，以及待提取信息分布在不同来源源的程度。一个事件由公众传达并不罕见，事实上，该事件可能通过多个用户使用各种模态（例如 Twitter 上的文本、Flickr 上的图像和 YouTube 上的视频）跨多个社交媒体渠道传播。这最早的体现之一是 2008 年孟买恐怖袭击期间；Flickr、Twitter 流、Google Maps 地图和维基百科文章被建立，以对不断发生的事件提供实时报道（Arthur, 2008）。每条信息单独都增加了我们对事件的理解，所有这些信息的总和提供了对实际事件完整复杂性的更好理解。这引入了开发更好能力来有序处理地理空间多媒体的需求。这类似于地理传感器网络中的信息聚合（Stanfield and ...）。

![图 11.1 大数据的三个维度：体量、速度和多样性。](img/7c79e82750415aed3dd6b437e48a8d77_177_0.png)

这些信息为社交媒体提供了额外内容（即空间），并为分析这些数据提供了背景（即主题和情感基调）。例如，我们识别了参与特定讨论的社区热点及其与其他社区的交互。因此，地理空间分析本质上是复杂的，因为它包含了对内容、连接、位置及其随时间变化的研究。正如此，它代表了地理新兴的地理信息替代方案，通过其规模和丰富性，为理解动态事件和形势开启了新的途径和研究挑战。

本章的目标是介绍与大地理空间数据相关的特定挑战，以便理解相应的分析和处理需求。因此，本章的结构如下：在第 11.2 节中，我们讨论社交媒体相对于传统空间数据的特定特征。在第 11.3 节中，我们将关注社交媒体内容的复杂性，使用代表性示例。在第 11.4 节中，我们将处理多样化内容，以实现对多个社交媒体信息流的整合地理空间分析。最后，在第 11.5 节中，我们将展望未来展望。

## 11.2 大地理社会数据的特征

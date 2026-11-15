

在配备 2 GB 内存的 Intel(R) Core(TM)2 6600 处理器上进行了实验。所使用的开发数据库 DS1、DS2 和 DS3 如图 10.9(a) 所示。每个数据库包含 10,000 个点，与用于测试 DenStream 的数据库类似。为了公平分析，EDS 指示的信息流进度通过采用类似方法 [10] 来呈现。每个数据集随机选择了十次，每次生成一个绝对长度为 100,000、每个时间单元块大小为 10,000 的互连网络。测试中 FlockStream 使用的限值与所采用的起始焦点/代表点 Na = 1,000、流速 v = 1,000、旋转因子 λ = 0.25、供应量 = 16、μ = 10、异常限值 β = 0.2 以及 MaxIterations = 1,000 相当。我们评估了 FlockStream 对非先进数据集 DS1、DS2 和 DS3（2(a)）的计算，以验证该方法处理每个类别可接受状态的能力。结果如图 10.9(b) 所示。在此图中，圆表示由度量定义的微束。可以看到 FlockStream 精确恢复了群组的形状。FlockStream 在创建 EDS 信息流方面获得的结果在多种情况下如图 10.9(c) 所示。在该图中，强调显示原始数据，而圆显示微束。可以看出，随着信息流的增长，FlockStream 能高效捕获每个束的状态。

## 10.20 结论

CPS 的不断进步通常有利于大规模信息处理与分析的创新发展。当与人工智能、AI 和神经形态处理策略相结合时，CPS 能够实现新的项目、管理和机遇，所有这些都预计将实现高度自动化，几乎不需要人工干预。这将有助于转变“智慧世界”的概念：更智能的水资源管理、更智能的医疗、更敏锐的基础设施、更明智的能源和更智能的食品将对我们的生活产生极大影响。本文对 CPS 进行了详尽描述，涵盖积累、入口、预订、导航、处理和调查等广泛视角，帮助我们理解和识别 CPS 面临的问题、所提出的新解决方案以及尚待解决的关键挑战。

随着数字–物理框架中收集的海量信息规模不断扩大，我们需要一种总体工具，以在异构实时信息源的组织中识别空间–短暂模式。本文提出了一种新的知识流近似方法，用于在新兴识别中进行相关概念探索。该估计取决于为多物种群集行为共同开发的模型的感知密度。该技术采用一种局部概率多智能体搜索方法，允许用户相互独立地行为，并且仅与直接邻居以异域方式进行寻址。去中心化和非竞争使该度量能够适应异常巨大的数据库。未来工作将重点放在自然监控群体进展的程序上，利用框架中先前实现的群体的动态更新。此外，我们正在 Rainbow 平台上部署该框架，以便更好地评估该框架在有限资源需求方面的敏感性和优势。

## References

- 1. Amini, A., Saboohi, H., Wah, T.Y., Herawan, T. 面向实时物联网流的基于密度的快速聚类算法. Sci. World J, Hindawi Publishing Corporation, 5, 326, 2–11, 2014.
- 2. Stojmenovic, I. 面向大规模网络物理系统的具有网内数据聚合、处理和驱动的机器间通信. Internet Things J., IEEE, 1, 2, 122–128, 2014.
- 3. Giordano, A., Spezzano, G., Vinci, A. Rainbow: 面向大规模联网网络物理系统的智能平台. UBICITEC2014, pp. 70–85, 2014.
- 4. Eberhart, R.C., Shi, Y., Kennedy, J. 群体智能. 人工智能 Morgan Kaufmann 系列, 美国, 2001.
- 5. Forster, A., Pizzuti, C., Spezzano, G. 基于群体智能的演变数据流单遍聚类算法. Data Min. Knowl. Discovery J., Springer, 26, 1, 1–26, 2013.
- 6. Vallim, R.M.M., Filho, J.A.A., de Carvalho, A.C.P.L.F, Gama, J. 数据流中行为变化检测的基于密度的聚类方法. Neural Networks (SBRN), 2012 Brazilian Symposium on, pp. 37–42, 20–25 Oct. 2012.
- 7. Gama, J, Rodrigues, P.P, Lopes, L.M.B. 采用局部处理和减少通信对分布式传感器数据流进行聚类. Intell. Data Anal., 15, 1, 3–28, 2011.
- 8. Reynolds, C.W. 鸡群、牛群和鱼群：一种分布式行为模型. SIGGRAPH ‘87: Proceedings of the 14th Annual Conference on Computer Graphics and Interactive Techniques, ACM, pp. 25–34, 1987.
- 9. Cui, X. and Potok, T.E. 用于文档分区聚类的多物种群集行为模型的分布式代理实现. Cooperative Information Agents, pp. 124–137, 2006.
- 10. Cao, F., Ester, M., Qian, W., Zhou, A. 带噪声演变数据流上的基于密度的聚类. Proceedings of the Sixth SIAM International Conference on Data Mining (SIAM 2006), pp. 326–337, 2006.
- 11. Ester, M., Kriegel, H.P., Sander, J., Xu, X. 带噪声大型空间数据库中簇发现的基于密度的算法. Proceedings of the Second ACM SIGKDD International Conference on Knowledge Discovery and Data Mining (KDD'96), 1996.
- 12. Tang, L., Yu, X., Kim, S., Han, J., Hung, C., Peng, W. TrueAlarm: 网络物理系统中传感器网络的可信度分析. in: ICDM, 2010.
- 13. Tang, L., Gu, Q., Yu, X., Han, J., La Porta, T., Leung, A., Abdelzaher, T., Kaplan, L. Intrumine: 网络物理系统不可信数据中的入侵者挖掘. in: Proc. of SIAM International Conference on Data Mining (SDM), 2012.
- 14. Deshpande, A., Guestrin, C., Madden, S., Hellerstein, J.M., Hong, W. 传感器网络中的模型驱动数据采集. in: VLDB, 2004.
- 15. Elnahrawy, E. and Nath, B. 噪声传感器的清洗与查询. in: WSNA, 2003.
- 16. Koushanfar, F., Potkonjak, M., Sangiovanni-Vincentelli, A. 传感器测量的在线故障检测. in: IEEE Conference on Sensors, 2003.
- 17. Subramaniam, S., Palpanas, T., Papadopoulos, D., Kalogeraki, V., Gunopulos, D. 基于非参数模型的传感器数据在线离群点检测. in: VLDB, 2006.
- 18. Xiao, X., Peng, W., Hung, C., Lee, W. 使用高级排位对无线传感器网络中故障读数进行网内检测. in: DEWMA, 2007.
- 19. Wu, J., Bisio, I., Gniady, C., Hossain, E., Valla, M., Li, H. 感知上下文的网络与通信：第 1 部分 [客座编辑]. IEEE Commun. Mag., 52, 6, 14–15, June 2014.
- 20. Nugroho, A.P., Okayasu, T., Horimoto, M., Arita, D., Hoshi, T., Kurosaki, H., Yasuda, K.-i., Inoue, E., Hirai, Y., Mitsuoka, M. 具有空中更新功能的现场环境监测节点的开发. Agric. Inf. Res., 25, 3, 86–95, 2016.
- 21. Tang, L., Cui, B., Li, H., Miao, G., Yang, D., Zhou, X. 伪周期流的有效变化管理. in: SIGMOD, 2007.
- 22. Krishnamachari, B. and Iyengar, S. 无线传感器网络中容错事件区域检测的分布式贝叶斯算法. IEEE Trans. Comput., 53, 3, 241–250, 2004.
- 23. Jeffery, S.R., Alonso, G., Franklin, M.J., Hong, W., Widom, J. 传感器数据清洗的声明式支持. in: ICPC, 2006.
- 24. Yu, X., Tang, L., Han, J. 过滤与细化：一种高效有效的异常检测两阶段方法. in: ICDM, 2009.


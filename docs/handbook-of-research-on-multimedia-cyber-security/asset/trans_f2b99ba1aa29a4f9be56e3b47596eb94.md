
# 图 10. 在 DM-Tree 结构上执行分布式 kNN 和 Range 查询的实验结果（毫秒）

![Figure978-1-7998-2701-6.ch007.f10](i/ch007.f10.png)

例如，在 600 万向量的 DM-Tree 结构上执行分布式 kNN 查询耗时 6,483 毫秒（约 6.5 秒），而执行分布式 Range 查询仅耗时 5,190 毫秒（约 5 秒）。

# 结论与未来工作

在大数据时代，旧的解决方案已不再适用。我们需要分发数据和处理。Apache Spark 与 HDFS 的结合是分布式存储和处理的有效且廉价的解决方案。如今，我们拥有包含大量图像或视频片段的超大多媒体数据库。我们使用 `Image2vec` 和 `Video2vec` 将图像或视频片段转换为向量，以便于处理。`M-Tree` 是度量空间的索引方法。它有助于有效解决度量空间中的相似性搜索问题，即 kNN 和 Range 查询。然而，`M-Tree` 无法索引大型向量空间，例如大型多媒体数据库中的向量，这些向量必须分布式地存储在多台计算机上。为了满足以嵌入向量形式存在的、包含数百万图像和视频片段的大型多媒体数据库的新需求，我们在 Apache Spark 框架上研究并成功实现了分布式 M-Tree 结构，称为 `DM-Tree`。我们还展示了关于 `DM-Tree` 结构的一些实验，以证明 `DM-Tree` 在搜索多媒体数据库方面的性能。未来，我们将继续研究以减小 `DM-Tree` 结构的规模，并降低主节点与工作节点之间的通信成本，从而在更大的多媒体数据库中更有效地搜索相似性。

为了拥有一个好的分布式算法，重要的是要注意本地处理算法必须优秀，且工作节点与主节点之间的通信成本必须很小。事实上，同时满足这两个要求并不简单。

# 致谢

本研究由越南国家大学胡志明市分校（VNU-HCMC）资助，资助编号为 B2017-26-02。

# 参考文献

Assefi, M., Behravesh, E., Liu, G., & Tafti, A. P. (2018). Big data machine learning using apache spark MLlib. *Proceedings - 2017 IEEE International Conference on Big Data, Big Data 2017*. 10.1109/BigData.2017.8258338

Bachmann, J. P. (2019). The SuperM-Tree: Indexing metric spaces with sized objects. *ArXiv*, 1–14. Retrieved from http://arxiv.org/abs/1901.11453

Cai, H., Zheng, V. W., & Chang, K. C. C. (2018). A Comprehensive Survey of Graph Embedding: Problems, Techniques, and Applications. *IEEE Transactions on Knowledge and Data Engineering*, 30(9), 1616–1637. doi:10.1109/TKDE.2018.2807452

Ciaccia, P., Patella, M., & Zezula, P. (1997). M-tree: An efficient access method for similarity search in metric spaces. *Proceedings of the 23rd International Conference on Very Large Databases, VLD*. Academic Press.

Garcia-Gasulla, D., Béjar, J., Cortés, U., Ayguadé, E., & Labarta, J. (2015). Extracting Visual Patterns from Deep Learning Representations. *ArXiv:1507.08818* \[Cs\].

Guo, C. (2013). Design and implementation of a multimedia database application system. *Journal of Theoretical and Applied Information Technology*, 47(3).

Homepage, Y. A. G. O. (n.d.). Retrieved January 21, 2019, from https://www.mpi-inf.mpg.de/departments/databases-and-information-systems/research/yago-naga/yago

Hu, S. H., Li, Y., & Li, B. (2016). Video2vec: Learning semantic spatio-temporal embeddings for video representation. *Proceedings - International Conference on Pattern Recognition*. 10.1109/ICPR.2016.7899735

Kouahla, Z. (2011). Exploring intersection trees for indexing metric spaces. *CEUR Workshop Proceedings*.

M-Tree Wikipedia. (n.d.). Retrieved March 15, 2019, from https://en.wikipedia.org/wiki/M-tree

Mikolov, T., Chen, K., Corrado, G., & Dean, J. (2013). Efficient Estimation of Word Representations in Vector Space. *ArXiv*, 1–12. Retrieved from http://arxiv.org/abs/1301.3781

Riaz, A., Ashraf, I., & Aslam, G. (2014). A Review On Multimedia Databases. *International Journal of Scientific & Technology Research*, 3(10), 186–191.

ShanahanJ. G.DaiL. (2019). Large scale distributed data science from scratch using apache spark 2.0. *Proceedings 26th International World Wide Web Conference 2017, WWW 2017 Companion*. 10.1145/3041021.3051108

Vlachou, A., Doulkeridis, C., & Kotidis, Y. (2010). Peer-to-peer similarity search based on M-Tree indexing. *Lecture Notes in Computer Science Including Subseries Lecture Notes in Artificial Intelligence and Lecture Notes in Bioinformatics*. doi:10.1007/978-3-642-12098-5\_21

YAGO. (database) Wikipedia. (n.d.). Retrieved January 21, 2019, from https://en.wikipedia.org/wiki/YAGO\_(database)

Zecevic, P., & Bonaci, M. (2017). *Spark in Action*. Manning Publications.

# 第 8 章

*   Kirti Raj Bhatele  
    Rustamji Institute of Technology, India

*   Shivangi Jain  
    Rustamji Institute of Technology, India

*   Abhishek Kataria  
    Rustamji Institute of Technology, India

*   Prerana Jain  
    Rustamji Institute of Technology, India

# 摘要

本章简要介绍了与数字取证相关的各种基础知识和概念。数字取证的概述包括数字取证的生命周期及其不同阶段，即准备、收集、分析和报告。数字取证工具的评估包括 `EnCase Forensic`、`FTK (Forensics Tool Kit)` 和 `Helix` 数字取证工具及其优缺点。数字取证工具和技术检查包括数字检查技术、活体取证分析、Windows 注册表恢复、数字取证工具比较，并重点关注用于数字取证分析的 ACPO 准则。

# 引言

数字取证是一门科学，涉及证据收集、调查和逆向工程，可确定计算机是如何被组成的。有多种工具和方法可供使用，以正常工作并帮助调查人员认证和分析证据 (Bennett, 2012)。数字取证的目标是以最原始的形式保存任何类型的数字证据。数字取证基于通过收集、识别和验证数字证据或信息来执行结构化研究，主要目的是重现发生在受害者计算机上的网络犯罪相关的过去事件。

尽管如此，数字取证调查人员面临的挑战可分为三类：

1.  **技术挑战**：如加密、隐写术、不同的媒体格式和分析。
2.  **法律挑战**：如隐私问题、缺乏标准化的国际立法和行政问题。
3.  **资源挑战**：如获取和分析取证介质所需的时间。


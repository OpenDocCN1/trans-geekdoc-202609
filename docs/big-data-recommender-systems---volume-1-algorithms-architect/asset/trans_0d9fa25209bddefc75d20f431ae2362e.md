

# 6 大推荐系统，第1卷

**第 13 章：** 本章介绍了一种成本高效的并行协议，通过使用多种音标编码来实现定性隐私保护，该协议结合了 Soundex 和纽约州身份识别与情报系统 (NYSIIS) 音标算法。提出第一种算法用于对原始文本，第二种用于解码。使用 Apache Spark 平台的实验表明，所提算法能够高效处理海量数据，同时提高了匹配过程的质量，并将结果与使用单一编码算法的方法进行了对比。

**第 14 章：** 本章提出了一种检测网络攻击的方法。该方法是一种基于人工智能的混合架构，旨在为组织提供监督和无监督解决方案，以应对入侵、钓鱼和 URL 检测。原型模型使用了多种机器学习（ML）分类器和深度学习架构。该研究特别关注入侵检测与分类以及钓鱼 URL 的检测。

# 致谢

我们对各章节的作者表示诚心的感谢，感谢他们分享了与其研究相关的想法和经验，并耐心解答了审稿人的意见，严格遵守紧迫的截止日期，以确保书籍能够按时提交给出版商。我们非常感谢审稿人对章节提供的富有见解且周到的意见，这极大提高了书中收录章节质量。

感谢 IET 出版这本书，并在出版过程的各个阶段为我们提供支持。我们相信，这本书在汇来自不同领域的大数据推荐系统研究工作方面做出了重要贡献。

# 参考文献

- [1] “数据永不眠 5.0，” [在线]。可用：https://web-assets.domo.com/blog/wp-content/uploads/2017/07/17_domo_data-never-sleeps-5-01.png [访问 2018年10月15日]。
- [2] “数据永不眠 6.0，” [在线]。可用：https://www.domo.com/blog/data-never-sleeps-6 [访问 2018年10月15日]。
- [3] J. Bobadilla, F. Ortega, A. Hernandez, and A. GutiérrezRrez，“Recommender systems, Knowledge-Based Systems, vol. 46, pp. 109–132, 2013.
- [4] O. Khalid, M.U. Khan, S.U. Khan, and A.Y. Zomaya，“Omnisuggest: a ubiquitous cloud based context recommendation system for mobile social networks,” IEEE Transactions on Services Computing, vol. 7, no. 3, pp. 401–414, 2014.
- [5] C.A. Gomez-Uribe and N. Hunt，“The Netflix recommender system: algorithms, business value, and innovation,” ACM Transactions on Management Information Systems, vol. 6, no. 4, pp. 1–19, 2016.
- [6] A. Sharma, J.M. Hofman, and D.J. Watts，“Estimating the causal impact of recommendation systems from observational data,” in 16th ACM Conference on Economics and Computation, Portland, Oregon, USA, 2015.
- [7] B. Smith and G. Linden，“Two decades of recommender systems from Amazon,” IEEE Internet Computing, vol. 21, no. 3, pp. 12–18, 2017.
- [8] J. Davidson, B. Liebaud, J. Liu, et al.,"The YouTube video recommendation system,” in Proceedings of the Fourth ACM Conference on Recommender Systems, Barcelona, Spain, 2010.
- [9] U. Sivaraj, M.M. Kamal, and Z. Irani，“Critical analysis of big data based recommendation system, challenges and analytical methods,” Journal of Business Research, vol. 70, pp. 263–286, 2017.
- [10] F. Rehman, O. Khalid, and S.A. Madani，“A comparative study of location-based recommendation system,” Knowledge Engineering Review, vol. 32, no. 7, 2017.
- [11] “OpenMP，” [在线]。可用：https://www.openmp.org/ [访问 2018年10月15日]。
- [12] B. Barney，“Message passing interface，” [在线]。可用：https://computing.inl.gov/tutorials/mpi/ [访问 2018年10月15日]。
- [13] “Apache MapReduce，” [在线]。可用：https://www.ibm.com/analytics/hadoop/mapreduce [访问 2018年10月15日]。
- [14] “Apache Spark，” [在线]。可用：https://spark.apache.org/ [访问 2018年10月15日]。
- [15] “Apache Hadoop，” [在线]。可用：https://hadoop.apache.org/ [访问 2018年10月15日]。

# 第 2 章

## 推荐系统的理论基础

Mirza Zaeem Baig¹, Hasina Khatoon¹, Syeda Saleha Raza², 和 Muhammad Qasim Pasta³

### 2.1 引言

推荐系统（RS）是一种在决策过程中为用户提供建议的软件。这种决策过程可能是为了商业目的（买什么东西？）、为了个性化应用（看什么电影和听什么音乐？），或者是为了简单的信息检索（与该主题最相关的论文有哪些？）。这些系统已成为几乎所有涉及某种形式应用的重要组成部分。本章为推荐系统的理论基础提供了背景。我们从常见的推荐系统定义开始，介绍在信息过载的情况下这些系统的必要性。本文介绍了推荐系统有效且有成效的应用领域。所列列表并非详尽，它们涵盖了许多应用领域。章节以引用的参考文献结束。本节概述了推荐系统执行其功能所经历的阶段。

¹巴基斯坦，国家计算机与新兴科学大学 (FAST-NU)
²巴基斯坦，哈比布大学科学与工程学院
³巴基斯坦，乌斯曼科技学院

# 10 大推荐系统，第1卷

### 2.1

#### 2.1.1 推荐系统的定义

文献中有很多关于推荐系统的定义。推荐系统被定义为存在大量信息时的一种决策策略[1]。它允许个性化和优先级排序。在当前信息过载的情况下，它使得及时获取信息成为可能。它也是处理信息过载问题的信息过滤系统[2]。推荐系统的目的是在知识方面提供支持[3]。它是信息过滤系统的一个分支，旨在预测用户对物品的评分或偏好[4]。根据 Serousi [4] 的观点，“发现辅助”是一个更好的术语，他认为推荐系统是帮助用户发现他们可能感兴趣物品的系统。

#### 2.1.2 推荐系统的必要性

在网络营销时代，这些系统扮演着重要角色。推荐系统的目标是为用户感兴趣的物品生成有意义的推荐。它为产品供应商带来了更多收入，并为产品和服务增加了价值。

使用互联网的趋势迫使用户使用多种搜索引擎。搜索引擎有助于查找信息，并以所有可能来源的形式呈现结果。对于对搜索引擎的每一次查询，都会建议成千上万个链接。用户可能会难以过滤和缩小范围以进行进一步探索。此外，还会获得大量无关信息，这是因为搜索引擎依赖模式匹配和寻找相似性。这种信息过载问题可以通过推荐系统来缓解。通过各种过滤技术，推荐系统根据用户的行为和倾向缩小信息范围。

### 2.2 推荐系统的应用

推荐系统在许多领域被应用和使用。其中一些自互联网出现以来就已经在使用。在许多其他领域，部署推荐系统也是有用的，因为这将提高底层应用的效率。接下来的章节涵盖了这些领域。所列应用可能并不详尽，因为许多其他应用领域正在引入推荐系统以探索其益处和用处。




# 82 第 3 章：数据调理

在数据隐私和伦理方面，多个国家正在制定相关政策。例如欧洲的《通用数据保护条例》（GDPR）和加州的《隐私权利法案》（CPRA）。在美国，白宫科学与技术政策政策办公室（OSTP）在一项拟议的《权利法案》下制定了原则，以防止不成比例地影响边缘个人和社区的技术 [61]。此外，更广泛的 AI 社区也需要共享数据集、模型，并快速推进技术水平，确保符合第 8 章中介绍的 FASTEPS 原则。这种共享必须在不抑制创新和协作的情况下进行 [62, 63]。

多位 AI 从业者建议正式建立一套标准化的流程，用于记录机器学习（ML）数据集。具体来说，Timnit Gebru 及其同事提了“数据集数据表”（datasheets for datasets）[64]，这对于数据集的创建者和消费者都至关重要。创建数据集数据表是避免不匹配的一种极方法，这种不匹配在 във风险应用中使用机器学习模型时可能会导致严重后果。

## 3.7 核心要点

过去十年中数据的指数级增长推动了 AI 能力的显著进步。为了让 AI 能够良好地利用这些进展，并继续开发和将 AI 产品和服务推向市场，我们建议采用三层架构的方法：

- 开展数字化转型之旅，构建并维护现代化的平台基础设施。
- 成为一个数据驱动型组织，整合、遵循并部署与数据库管理标准一致的 AI 能力。
- 遵循一套以数据为中心的 AI 原则，包括对数据质量评估、数据清洗和数据准备的密切关注。

演变为数字化转型企业的一个重要益处是打破组织孤岛，这些孤岛阻碍了第 1 章图 1.3 中 AI 流水线的正确实现，且从数据调理阶段开始。我们强调了 AI 组织在数字化转型之旅中必须实现的五个主要能力成熟度等级。这些级别通过维持具有竞争力的数字生态系统，实现了数字化、标准化、优化、加速和领先。

数字化转型使组织能够构建并维护现代化的平台基础设施，从而允许适当的数据库管理，并符合数据格式和模式标准。在过去的几年中，已经需要从使用结构化数据的事务性数据处理转向使用 NoSQL 数据架构处理更多非结构化数据。

商业组织在提供支持结构化数据和非结构化/半结构数据的存储环境方面也取得了巨大进展。数据存储环境的示例包括数据仓库和数据湖。这些商业供应商在数据源支持 SQL、NoSQL 和流处理的能力方面存在融合趋势。

数字化转型和建立数据驱动的组织文化对于成功开发和部署 AI 能力是必要的，但并不足够。我们还必须关注第三层——遵循一套以数据为中心的 AI 原则。

以数据中心的方法（与 ML 阶段迭代）要求在数据调理功能块内对数据质量评估、数据清洗和数据准备进行密切关注。我们讨论了在这些步骤中执行的功能。我们还强调了理解利益相关者需求的重要性，以便执行这些特定的数据调理功能，确保数据适用于机器学习算法。

AI 社区在十年中经历的快速且显著的加速，归功于优质开源数据集（如 MNIST 和 ImageNet）以及计算技术的进步。目标分类领域曾出现几个展示巨大改进的里程碑时刻。从那时起，进一步努力创建适用于不同模态（包括图像本体、视频、文本和语音）的精选数据集。

在本章中，我们概述了三个层面（数字化转型、数据驱动文化和以数据为中心的 AI）各自必须解决的挑战，以便成功开发和部署 AI 产品及服务。

机器学习有许多衡量指标。然而，AI 社区需要关注图 1.3 所示 AI 流水线所有层面的性能指标，包括可靠可信的数据集标签。建议的方法是建立一套以数据为中心的 AI 基准，并配备必要的测试机架、金标准数据集和可重复代码。每个数据集还必须包含一份数据表，对其内容进行元数据级的描述。数据集还必须符合一套法规，同时不抑制技术创新。

# 84 第 3 章：数据调理

## 3.8 练习题

1. 识别并详述开展数字化转型之旅的一个重要益处。
2. 强调结构化数据与非结构化数据之间的主要区别。
3. 特征大数据的“四个”是什么？解释每个“V”的意思。
4. 描述组织在数字化转型过程中必须实现的五个能力成熟度等级。
5. SQL 模式是否适用于非结构化数据？
6. 描述 Apache Hadoop 开源工具包的主要组件。
7. 详述数据仓库和数据湖之间的主要区别。
8. 选择一个 AI 应用，并解释维度灾难如何在实现预期机器学习算法性能时成为一个重大问题。
9. 数据质量评估、数据清洗和数据准备期间执行的典型功能有哪些？
10. 解释偏差（bias）与数据差（variance）之间的权衡。
11. 数据科学家如何克服维度灾难？
12. 描述以数据为中心的基准示例及其的一些挑战。
13. 什么是数据集数据表（datasheets for data sets）？
14. 趋势是整合多模态数据（例如文本、视频和图像）。这将如何帮助 AI 结果获得更好的上下文？
15. 解决数据调理阶段整合多模态数据时的挑战。提示：回参考表 3.4。

## 3.9 参考文献

1. Ng, A., NeuroIPS Data-Centric AI Workshop. 2021.
2. Hulten, G., Building Intelligent Systems: A Guide to Machine Learning Engineering, 2018, Apress.
3. DOMO, Ninth Annual “Data Never Sleeps”. 2021. https://www.domo.com/learn/infographic/data-never-sleeps-9.
4. Datareportal, Digital around the World. 2021. https://datareportal.com/reports/a-decade-in-digital.
5. Lee, I., Big data: Dimensions, evolution, impacts, and challenges. Business Horizons, 2017, 60(3): 293–303.
6. Short, J. and S. Todd, What’s your data worth? MIT Sloan Management Review, 2017. 58(3): 17.
7. Redman, T. and T. Davenport, Getting serious about data and data science. 2020, Recuperado de MIT Sloan Management Review: https://sloanreview.mit.edu.
8. Redman, T., What holding your program back? MIT Sloan Management Review, 2021. 63(1): 1–10.
9. Brynnjsson, E., Rock, and C. Syverson, The productivity J-curve: How intangibles complement general purpose technologies. American Economic Journal: Microeconomics, 2021. 13(1): 333–372.
10. Dickson, B., Why most machine learning strategies fail—TechTalks (bdtechtalk.com), 2021.
11. Burianek, D. and R. Solis, Personal communication on digital transformation levels. MIT Lincoln Laboratory.
12. Ross, J., C. M. Beath, and M. Mocker, Designed for digital: How to architect your business for sustained success. 2019, MIT Press.
13. Podolny, J. and M. T. Hansen, How Apple is organized for innovation. Harvard Business Review, 2020. 98(6): 86–95.
14. Furr, N. and A. Shililov, Digital doesn’t have to be disruptive: The best results can come from adaptation rather than reinvention. Harvard Business Review, 2019. 97(4): 94–104.
15. Conway, M. E., How do committees invest? Datamation, 1968. 14(4): 28–31.
16. Kelleher, J. D., B. Mac Name, and A. D’arcy, Fundamentals of machine learning for predictive analytics: Algorithms, worked examples, and case studies. 2020, MIT Press.

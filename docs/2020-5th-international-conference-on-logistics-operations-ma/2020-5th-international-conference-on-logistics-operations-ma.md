
# 2020 第五届国际物流运营管理会议 (GOL)

**摘要**—在交通运输领域，需要通过机器学习（ML）为许多问题创建智能解决方案。在港口领域，长期以来一直关注于优化和仿真建模，但在构建支持港口作业的更复杂的决策系统方面，仍需要机器学习。为了评估机器学习在港口作业中的应用，我们开展了这项系统性文献综述（SLR），以筛选和分析相关论文。本文报告了分析的方案，并强调了未来工作中可以解决的空白。

**关键词**— 机器学习，航运，分析，港口，系统性文献综述

# I. 引言

机器学习（ML）技术的应用彻底改变了交通运输系统 [1]。由于活动增加和流程复杂，港口面临着各种挑战。港口作为国际运输系统，其复杂的网络是一个提供具有吸引力的研究机会的案例研究。在解决某些与港口作业相关的问题并指出了未来工作中可以考虑的局限性。

我们根据 Kitchenham [2] 采用的方法开展了这项系统性文献综述（SLR）。所提出的程序旨在支持软件工程的复杂性以及我们提供的支持。综述将通过三个阶段进行：第一步是规划，第二步是执行，最后是报告。规划的第一步包括确定综述目标和定义方案。SLR 包含根据完善后的方案搜索和选择论文。在提取和综合信息后，报告的最后阶段将以各种形式交流结果。本研究的目标是为港口作业效率的机器学习应用提供系统性文献综述。背景将在下一节给出。在第 III 节中描述了研究方法，在第 IV 节中展示了结果。本文将得出结论。

集装箱码头非常丰富，且在该领域已提出了若干相关的综述 [12, 13]。除了广泛使用优化建模外，仿真已成为为港口和集装箱码头开发 20 多个模型的重要工具 [13]。现有文献在许多方面存在问题，从资源分配和调度到港口作业，包括调度、物流等许多。优化和仿真模型、数据驱动方法有助于分析变量对港口性能的影响，机器学习分析将有利于机器学习的整合。优化和仿真方法、提取完整信息以更好地支持港口理解的方法。贸易量的日益增长使港口作业采取提高效率措施 [14]。海洋物流的发展在监控和控制作业方面有用。这种发展导致了体量和单位成本分析以及优化方法的数据产生。这些系统可以帮助限制作业的各种方面。

今天，商业行业有助于推动其运营效率，并能够从解决复杂问题中受益。数据分析和统计构成了商业智能的主要优势 [15]。分析旨在通过统计分析、预测、预测建模和优化来发现模式并做出决策。机器学习可以增强预测以辅助人类决策和操作。这些技术在 [16] 中被讨论为未来的融合领域和单一集成系统。他们还承认了将分析与运营相结合以在实际应用中取得积极结果的重要性。

通过这项 SLR，我们旨在对机器学习在港口作业中的应用做出贡献，并确定有助于理解港口系统特征和执行操作的进一步研究方向。

# II. 背景

今天，需要能够协助港口作业日常工作的智能系统。为此，运营在解决港口问题中的应用可能地……

# III. 综述

关于机器学习技术应用于港口作业的最后综述是开展这项工作的主要动力。因此，本综述的目标是通过收集和评估相关研究，提供现有工作之间的比较。下文，我们描述了所遵循的方法：首先，我们提出所有的研究问题，然后我们遵循搜索过程来识别主要研究，之后，我们通过应用筛选标准仅保留相关工作并……

## A. 研究问题

为了我们的目的：

- **RQ1** 机器学习对港口作业效率的影响是什么？
- **RQ2** 涵盖了哪些研究领域和主题？
- **RQ3** 使用了哪些机器学习技术和方法？
- **RQ4** 地理关注点和港口类型有哪些？

## B. 搜索过程

为了识别主要的潜在研究，我们第一步在数字图书馆上进行搜索：`ASCE`、`IEEE Xplore`、`SAGE` 和 `JSTOR`。我们使用搜索字符串 `(port OR harbor OR wharf) AND ('mining' OR 'statistical' OR 'machine learning')` 来收集相关文献。结果如表所示，该步骤应用了过滤器。在第三步中，如果我们需要找到与定义领域相关的研究，我们扫描了标题、关键词和摘要。

### 表 I 应用于数字图书馆的过滤器

| 数字图书馆 | 搜索过滤器 |
|---|---|
| ASCE | Journal of transportation, Part A: Systems; Journal of waterway, ocean engineering |
| IEEE Xplore | Content types; Subjects: computer science, engineering |
| SAGE | Journal: Artificial Intelligence; European Journal of Operational Research |
| JSTOR | Content: Data Results; Language: english; Subject: Mathematics and statistics |

## C. 筛选标准

这是到达最相关研究的最后一步，我们需要根据标准筛选论文。我们选择纳入或排除论文的标准为：

- **纳入标准**：对港口系统有影响且以带来优化为目标的研究。在这里，港口系统设计从锚地到内陆闸。例如，内陆运输（卡车、火车等）包含在考虑范围内。
- **排除标准**：对港口系统没有影响的研究。

## D. 研究质量评估

根据标准筛选论文后，我们需要评估质量。计划考虑论文的方法论、它们是否证明了使用机器学习技术的必要性，我们使用了 `Scimager` 进行分析，使用 `CORE` 用于……

## E. 数据提取

从所选论文中提取数据是回答研究问题的重要的一步。在我们使用数据表提取所需信息：

- 发表年份
- 作者
- 出版来源
- 应用领域和重点
- 数据来源
- 任务：回归、分类、无监督技术；或强化学习
- 技术：线性模型、神经网络、加性模型、方法、树模型等
- 货物类型：散货、滚装箱等
- 研究的港口和地区名称

## F. 提取数据的综合

数据将以表格形式并总结以回答预设的研究问题。关于 RQ1，我们展示了与每个数字图书馆或会议相关的工作，一个直方图将显示每年发表的论文数量。对于 RQ2，一个表格将显示研究领域和子领域，所提出的分类系统旨在反映所选论文的影响。对于 RQ3，即使用了机器学习（ML）技术，我们还衡量了使用不同优化方法来提高模型质量的工作以及各种数据来源。RQ4 将通过显示不同地区和涉及船型的饼图来回答。

只有一篇论文。货运预测和周转时间估计是研究最充分的领域。然而，某些主题涵盖较少或未被涵盖，这些领域有大量工作要做。例如，拥堵和资源利用等重要问题尚未得到充分探索。

# IV. 结果与讨论

在执行了之前[章节]中定义的搜索过程和筛选标准后，我们获得了 310 项研究。结果如表 II 所示；第一步仅使用搜索字符串检索了大量的 180,005 篇论文，应用适当的过滤器后，我们得到了 25,251 篇，根据标题和摘要减少到 423 项研究，其中 30 篇论文符合由 27 篇文章和 35 篇会议论文组成的标准集。

![](img/9fd9b088bf65dd05939af614424f0fce_2_0.png)

### 表 II. 按图书馆和步骤划分搜索结果

| 数字图书馆 | 阶段 1 | 阶段 2 | 阶段 3 | 阶段 4 |
|---|---|---|---|---|
| ASCE | 29,900 | 784 | 3 | |
| IEEE Xplore | 19,334 | 1,935 | 21 | |
| SAGE | 25,200 | 213 | 83 | 12 |
| Science Direct | 54,480 | 17,719 | 73 | |
| JSTOR | 30,319 | 5,312 | 5 | 2 |
| Taylor & Francis | 7,787 | 650 | | |
| 总计 | 180,005 | 25,251 | 423 | 30 |

### 表 III. 按来源分类论文

| 图书馆 | 期刊名称/会议 | 论文数 |
|---|---|---|
| ASCE | Academic Journal of Shipping Logistics | [25] |
| | Computers and Industrial Engineering | [26] |
| | Decision Support Systems | [27][29] |
| Science Direct | Ocean Engineering | [31] |
| | Research in Transportation Science | [33] |
| | Transportation Research | [34] |
| | Transportation Research | [35][36] |
| | Annals of Operations Research | [37] |
| | Information Technology and Management | [38] |
| | Journal of Intelligent Management | [39] |
| | Journal of Transportation Engineering and Complexity | [40] |
| | Maritime Economics and Logistics | [42][43] |
| | Operational Research | [44] |
| | Journal of Port, Coastal, and Ocean | [17][18] |
| IEEE Xplore | | [20][22] |
| SAGE | Transportation Research: Journal of the Transportation Research | [23][24] |
| Taylor & Francis | Journal of Operational Research | [45] |
| | Marine Online | [46] |

### A. 按主题和年份分类论文

为了解决 RQ1，我们按数字图书馆和年份对所选论文进行了量化。从表 II 可以看出，Science Direct 是所有包含研究中的主要来源。它由 Springer 提供，而其余论文各在 77% 到 94% 之间，JSTOR 是完全开放获取的。然而，它们分散在表 I 的 31 个期刊和 35 个会议中。如图 1 所示，每年的论文数量很多，除了 2017 年发表了 7 篇外。第一篇论文发表于 2006 年，论文分布符合我们的预期。

### B. 按研究领域分类论文

根据研究领域对研究进行分类是重要的。这里有五个领域：规划与开发、安全与保障、堆场区域和运输区域。对于每个领域，定义了若干主题以识别论文处理的问题。论文的分类列在表 IV 中，我们可以看到除了安全与保障部分外，研究领域都处于基础地位。

#### 表 IV. 按研究领域分类论文

| 研究领域 | 研究重点 | 论文数 |
|---|---|---|
| 规划与开发 | 货运预测 | [36] |
| | 交通流 | [21][38] |
| 安全与保障 | 泊位分配模型 | [37] |
| | 港口拥堵 | [22] |
| 堆场区域 | 执行过程 | [19][26] |
| | 运输计划 | [25][26] |
| | 时间 | [35][49] |
| | 集装箱重组作业 | [33] |
| | 堆场吊机调度与交通 | [17][31][27][24][39] |
| 运输区域 | 卡车周转 | |
| | 车辆路径与调度 | [34] |

### C. 研究分类

任务分类，以及数据：[文本截断/损坏]



展示了与每个数字图书馆或会议相关的工作，一个直方图将显示每年发表的论文数量。对于 RQ2，一个表格将显示研究领域和子领域，所提出的分类系统旨在反映所选论文的影响。对于 RQ3，即使用了机器学习（ML）技术，我们还衡量了使用不同优化方法来提高模型质量的工作以及各种数据来源。RQ4 将通过显示不同地区和涉及船型的饼图来回答。

只有一篇论文。货运预测和周转时间估计是研究最充分的领域。然而，某些主题涵盖较少或未被涵盖，这些领域有大量工作要做。例如，拥堵和资源利用等重要问题尚未得到充分探索。

# IV. 结果与讨论

在执行了之前[章节]中定义的搜索过程和筛选标准后，我们获得了 310 项研究。结果如表 II 所示；第一步仅使用搜索字符串检索了大量的 180,005 篇论文，应用适当的过滤器后，我们得到了 25,251 篇，根据标题和摘要减少到 423 项研究，其中 30 篇论文符合由 27 篇文章和 35 篇会议论文组成的标准集。

![](img/9fd9b088bf65dd05939af614424f0fce_2_0.png)

表 II. 按图书馆和步骤划分搜索结果

| 数字图书馆 | 阶段 1 | 阶段 2 | 阶段 3 | 阶段 4 |
| --- | --- | --- | --- | --- |
| ASCE | 29,900 | 784 | 3 | |
| IEEE Xplore | 19,334 | 1,935 | 21 | |
| SAGE | 25,200 | 213 | 83 | 12 |
| Science Direct | 54,480 | 17,719 | 73 | |
| JSTOR | 30,319 | 5,312 | 5 | 2 |
| Taylor & Francis | 7,787 | 650 | | |
| 总计 | 180,005 | 25,251 | 423 | 30 |

表 III. 按用户分类论文

| 图书馆 | 期刊名称/会议 | 论文数 |
| --- | --- | --- |
| ASCE | Academic Journal of Shipping Logistics | [25] |
| | Computers and Industrial Engineering | [26] |
| | Decision Support Systems | [27][29] |
| Science | Ocean Engineering | [31] |
| | Research in Transportation Science | [33] |
| | Transportation Research | [34] |
| | Transportation Research | [35][36] |
| | Annals of Operations Research | [37] |
| | Information Technology and Management | [38] |
| | Journal of Intelligent Management | [39] |
| | Journal of Transportation Engineering and Complexity | [40] |
| | Maritime Economics and Logistics | [42][43] |
| | Operational Research | [44] |
| | Journal of Port, Coastal, and Ocean | [17][18] |
| IEEE | Xplore | [20][22] |
| SAGE | Transportation Research: Journal of the Transportation Research | [23][24] |
| Taylor & Francis | Journal of Operational Research | [45] |
| | Marine Online | [46] |

## A. 按主题和年份分类论文

为了解决 RQ1，我们按数字图书馆和年份对所选论文进行了量化。从表 II 可以看出，Science Direct 是所有包含研究中的免费组。它由 Springer 提供，而其余论文各在 77% 到 94% 之间，JSTOR 是完全免费的。然而，它们分散在表 1 的 31 个图书馆和 35 个会议中。如图 1 所示，每年的论文数量很多，除了 2017 年发表了 7 篇外。第一篇论文发表于 2006 年，论文分布符合我们的预期。

## B. 按研究领域分类论文

根据研究领域对研究进行分类是有关重要的。这里有五个领域：规划与开发、安全与保障、堆场区域和运输区域。对于每个领域，定义了若干主题以识别论文处理的问题。论文的分类列在表 IV 中，我们可以看到除了安全与保障部分外，研究领域都处于基础地位。

表 IV. 按研究领域分类论文

| 研究领域 | 研究重点 | 论文数 |
| --- | --- | --- |
| 港口与开发 | 货运预测 | [36] |
| | 交通流 | [21][38] |
| 安全与保障 | 出生分配模型 | [37] |
| | 港口拥堵 | [22] |
| | 执行过程 | [19][26] |
| | 运输计划 | [25][26] |
| | 时间 | [35][49] |
| 堆场区域 | 集装箱重组作业 | [33] |
| | 堆场吊机调度与交通 | [17][31][27][24][39] |
| 运输区域 | 卡车周转 | |
| | 车辆路径与调度 | [34] |

- [B. Bacon, E. Erannaks, and N. K. Park, "港口和集装箱码头的仿真建模：文献综述与分析研究、现场应用与灵活工具。" Services and Port Management, vol. 32, pp. 438–452, 2017.
- [M. Fruth, and F. Teuteberg, "海洋物流数字化——什么是以及为什么成本高昂？" Cost & Management, vol. 4, no. 1, pp. 17–23, 2020.
- [T. Tavenport, and I. Harris, 关于分析：获胜的新科学。Harvard Business Press, 2007.
- [X. Xie, and N. Hoyukh, "用于预测集装箱码头运营的基于内核的学习模型。" Journal of Transport, vol. 136, no. 12, pp. 1145–1152, 2020.
- [C. H. Chu, "主要港口内外部卡车到达预测的实证方法。" J. Transport, vol. 137, no. 4, pp. 497–506, 2018.
- [R. Gomez, A. Ramirez, and M. Rodriguez, "集装箱码头运营的基于的决策系统：案例研究。" Journal of Water Resources, Control and Ocean Eng., vol. 142, no. 2, p:0240516, 2018.
- [Y. Xie, Y. Li, J. Li, and G. Li, "基于BP神经网络和分析的集装箱流量预测," Int. Conf. on Inf. Comput. and, Soc., 2019.
- [J. Wang, J. Liu, and C. Peters, "利用 AIS 大数据预测港口拥堵，”在 2018 Int. Conf. on Nav. (ICON). IEEE, pp. 181–188, 2018.
- [N. Shen, and S. Wang, "集装箱码头日运营延迟源分析。" Trans. Res. Soc., vol. 26, no. 1, pp. 46–49, 2006.
- [Q. Pham, N. Hoyukh, and Y. Xie, "估计码头大门的卡车排队时间。" Trans. Res., vol. 22, no. 2, pp. 43–53, 2011.
- [V. Garrison, Chhandrakprasad, and S. Sikikalidis, "整个港口集装箱吞吐量的传统与神经网络预测。" The Asian Journal of Shipping and Logistics, vol. 33, pp. 281–292, 2017.
- [R. A. Stratuoniati, H. Baee, and M. Bongay, "基于离线需求支持决策树实时集装箱运输规划。" Support Systems, vol. 90, pp. 111–126, 2020.
- [B. van Riesen, R. R. Neijbergh, and R. Dekker, "基于离线需求支持决策树实时集装箱运输规划。" Support Systems, vol. 90, pp. 111–126, 2020.
- [M. Wasema, A. Stem, and H. van Hoek, "服务请求预测系统：利用短途卡车轨迹数据预测需求。" Support Systems, vol. 95, pp. 37–48, 2019.
- [M. Saldonado, R. Gonzalez-Ramirez, F. Quijada, and A. Ramirez, "分析指标：码头运营的决策支持系统。" Support Systems, vol. 121, pp. 84–93, 2019.
- [A. D. León, E. Lalla-Río, B. Martínez-Julian, and J. Marcos Morgana, "基于机器学习的泊位分配调度方法。" Exp. Syst. with Appl., vol. 88, pp. 170–183, 2019.
- [J. Meng, W. Li, Z. H. Dong, and Y. S. Liao, "通过随机模拟神经网络分析的 MARS-RSVAR 预测港口吞吐量。" Network Comput., vol. 147, no. 2, pp. 239–250, 2015.
- [J. Yu et al., "船舶到达日期及其对集装箱码头运营的价值。" Ocean Fleet, vol. 155, pp. 71–76, 2019.
- [F. Fohuchi, N. Hoyukh, J. M. Vidal, and Y. Xie, "将吊机操作建模为强化学习代理。" Trans. Res. Econ., vol. 42, pp. 105–120, 2021.
- [Q. Zeng, Z. Yang, and L. Lai, "集装箱码头吊机定向调度方法模型和算法。" Transport Policy, vol. 16, no. 4, pp. 273–279, 2009.
- [I. Kourountelis, A. Podolopoulou, and C. Tiklidis, "港口集装箱码头进口双倍预测建模——神经网络应用。" Trans. Res. Proceedings, vol. 44, pp. 243–252, 2016.
- [J. M. López-Ruiz, I. T. Murías, C. J. Aguilar, "利用 AIS 和神经网络进行短期预测。" Artificial Intelligence in Transportation, vol. 58, pp. 108–114, 2019.
- [R. Dushnoy, C. Siveraj, S. Ivanova, N. Hoyukh, and A. Trichechenko, "维持竞争力的成本曲线应用。" Transportation Research Part, vol. 136, pp. 182–189, 2009.
- [Z. Zhang, Y. Ni, and W. Wang, "基于改进 AIS 方法的船舶流量分析。" Data Syst., vol. 110, no. 3, pp. 397–409, 2017.
- [A. Hill, and W. Bice, "主要港口集装箱码头的决策支持系统。" Information Technology and Management, vol. 38, no. 2, pp. 241–251, 2007.
- [K. J. Kang, R. Y. Lee, and K. H. Kim, "集装箱码头调度：综述。" Operations Research, vol. 17, no. 4, pp. 309–316, 2007.
- [X. Qian, Y. Liu, J. Fu, and K. Lai, "通过离散 PSO 进行集装箱预测模型。" J. Soft Sci. and Comput., 27, pp. 181–194, 2012.
- [G. Fanceelli, C. Pano, M. Sanchez, R. Prado, and F. Padella, "集装箱码头的船舶到达时间预测与资源分配。" Maritime Economics, vol. 13, no. 2, pp. 93–106, 2012.
- [N. Amin, M. Boole, F. Stotifanis, and W. Weifhal, "港口需求决定因素分析。" Trans. Res., vol. 2, no. 2, pp. 169–178, 2005.
- [K. Milenkovic, N. Milojevic, N. Božovic, and S. Val, "基于运营的神经网络集装箱流量预测。" Support Systems, vol. 38, pp. 115–124, 2015.
- [S. Kim, and Y. Park, "利用历史和实时数据估计船舶泊位和靠岸时间。" J. Oper. Res. Soc., vol. 66, no. 2, pp. 182–191, 2017.
- [M. Gürkan, "集装箱船泊位和靠岸时间的实证方法。" Maritime Policy & Management, vol.45, 8, pp. 1078–1093, 2018.

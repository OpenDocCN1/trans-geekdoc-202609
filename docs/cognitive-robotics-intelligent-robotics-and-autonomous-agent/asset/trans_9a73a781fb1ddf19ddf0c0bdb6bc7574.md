

对其物理模拟中监测到的力动态事件进行标注。正如 Winston (2012) 所言，它使机器人能够用眼睛和双手进行推理。游戏引擎中的所有物理实体也都是符号化知识库中的实体，这意味着游戏引擎的状态由内部世界知识库正确、准确、完整地表示。

第三个组成部分是包含常识性、直观物理知识以及领域知识的符号化知识库。在许多情况下，领域知识库可以自动从半结构化网页构建而成，例如 Google Maps、OpenStreetMap、网络商店、DBpedia 等。

由于混合推理壳中使用的表示和机制最初是为动作执行壳创建的并且存在冗余，各个方法假设的解决方案可能需要根据其合理性进行检查和排序，例如在 Watson 系统（Ferrucci et al., n.d.）中所做的那样。

随后的接口层将混合推理壳视为一个一阶逻辑知识库，该知识库主要从控制程序的数据结构按需构建，并通过机器人算法进行计算。

## 21.7 神经符号学习与推理

近年来，感知、动作和智能问题求解的机器学习方法获得了巨大的发展势头（Hassabis et al. 2017）。特别是，深度学习和深度强化学习（Silver et al. 2016; Berner et al. 2019）在自主代理的特定任务中取得了令人印象深刻的成功。符号化知识表示在泛化、模块化和组合结构以及内省能力方面具有优势，而人工神经表示在学习高度相关的表征以及以端到端方式学习复杂动作选择、问答和问题求解任务方面具有优势（Levine et al. 2016, 2018; Sünderhauf et al. 2018）。从技术角度讲，动作选择和执行是将连续传感器数据流映射到连续运动驱动函数的计算任务，因此属于深度网络技术的适用领域。然而，已识别出在处理经验数据未涵盖的问题实例、解释和诊断生成的行为以便快速适应不可预见的情况，以及从少量经验中高效学习方面存在局限性（Marcus and Davis 2019）。

受这些成功和考虑的启发，一些研究人员提出了结合两种方法优势的方法，并通过复制符号化表示部分功能的运算扩展神经表示，或者将人工神经学习机制与符号推理相结合。这些方法的特点在表示动作结构和对其进行推理方面显示出巨大的前景。此类学习和推理方法的示例包括高维计算（Kanerva 2009, 2018）和神经符号计算（Garcez et al. 2019; Besold et al. 2017）。

由向量符号架构执行的高维计算（Neubert et al. 2019）通过高维向量（通常为数千维）表示符号，并利用编码的冗余性来实现对噪声和不确定性的鲁棒性。此外，它使用运算符对高维向量执行符号计算（Gayler 2004; Blouw et al. 2016; Levy and Gayler 2008）。这些运算符使先前知识的编码、从相似符号中泛化概念、复杂表达式的组合成为可能，从而也带来了从更少示例中学习的优势。因此，其直觉是向高维向量空间添加一些表示和推理能力（Eliasmith et al. 2012）。将高维计算应用于智能机器人代理的示例包括主动感知、位置识别以及反应行为的学习和回忆。

另一类方法是神经-符号计算（Garcez et al. 2019）。它旨在通过基于神经计算实现知识表示、学习和推理的新强大替代方案，来整合鲁棒的基于向量的学习和符号推理。

## 21.8 结论

知识表示与推理将成为在开放环境中完成模糊指定任务的认知机器人的关键信息处理能力。知识处理可以补充机器学习的决策和控制机制，因为推理步骤基于可以断言有效的规则。此外，使用知识表示与推理用可证明的推理链替代了机器学习方法的黑盒推理，使推理过程透明，并使认知机器人能够对其决策进行推理。至关重要的是，这些方法不仅要在抽象层面工作，还要应用于感知和运动层面，以充分发挥表示和推理方法的潜力。利用现代信息处理技术——包括真实的模拟和渲染技术、神经符号和高维计算，以及大数据和数据密集型机器学习方法——为实现这一目标提供了有前景的机会。

## 附加阅读与资源

- 一本关于常识性知识表示的开创性、详尽专著：Davis, Ernest. 1990. *常识性知识表示*. The Morgan Kaufmann Series in Representation and Reasoning. Burlington, MA: Morgan Kaufmann. ISBN 978-1-55860-033-1.
- KnowRob 机器人知识表示与推理架构的全面介绍：Tenorth, Moritz, and Michael Beetz. 2013. “KnowRob: 认知赋能机器人知识处理基础设施.” *国际机器人研究杂志* 32 (5): 566–590. http://ijr.sagepub.com/content/32/5/566.short.
- 一种用于沿多个维度对机器人动作表示进行分类的系统分类法，并附有关于机器人动作表示的细致文献综述：Zech, Philipp, Erwan Renaudo, Simon Haller, Xiang Zhang, and Justus H. Piater. 2019. “机器人动作表示：一种分类法与系统分类.” *国际机器人研究杂志* 38 (5). https://doi.org/10.1177/0278364919835020.
- 知识表示与推理框架 KnowRob 可供访问，包括开源软件、文档、安装指南和教程，网址为 www.knowrob.org。KnowRob 还可以通过基于 Web 的知识服务 openEASE 使用：www.open-ease.org。将推理应用于基于计划的机器人代理控制的示例是通过 CRAM（认知机器人抽象机）实现的，可通过网站 www.cram-system.org 访问。

## 注释

1. Kemp et al. (2007) 和 Mustafa Ersen et al. (2017) 提供了关于人类环境中自主机器人操作的挑战与方法的全面综述文章。
2. 关于构建智能系统的逻辑方法的优秀教科书包括 Genesereth and Nilsson (1987)；Reiter (2001)；Davis (1990)。
3. 如第 1 章所述，这种方法构成了认知机器人学的根源之一，Levesque、Reiter、De Giacomo、Lakemeyer 及其同事提出使用显式知识和推理来建模高级机器人控制，以决定执行哪些动作（Levesque and Lakemeyer 2008）。本章采纳这一观点，但并未将动作和推理的表示局限于高度抽象的层面。相反，我们将这一观点扩展到关于如何执行动作的推理。

## 参考文献

- Aksoy, Eren Erdal, Adil Orhan, and Florentin Wörgötter. 2017. “长而复杂的操作动作序列的语义分解与识别.” 国际计算机视觉杂志 122 (1): 84–115.
- Allen, James F. 1984. “迈向动作与时间的一般理论.” 人工智能 23 (2): 123–154. doi:10.1016/0004-3702(84)90008-0.
- Baader, Franz, Diego Calvanese, Deborah L. McGuinness, Daniele Nardi, and Peter F. Patel-Schneider. 2007. 《描述逻辑手册》. Cambridge: Cambridge University Press.
- Beetz, Michael, Daniel Beßler, Andrei Haidu, Mihai Pomarlan, Asil Kaan Bozcuoğlu, and Georg Bartels. 2018. “KnowRob 2.0 — 认知赋能机器人代理二代知识处理框架.” 收录于《机器人与自动化国际会议》, 512–519. Brisbane, Australia: IEEE.
- Beetz, Michael, Raja Chatila, Joachim Hertzberg, and Federico Peroca. 2016. “机器人人工智能推理方法.” 收录于 Siciliano and Khatib 2016, 329–356. doi:10.1007/978-3-319-32552-1_14.
- Beetz, Michael, Dominik Jain, Lorenz Mösenlechner, Moritz Tenorth, Lars Kunze, Nico Blodow, and Dejan Pangercic. 2012. “用于实现家务任务智能的认知赋能自主机器人控制.” IEEE 会议录 100 (8): 2454–2471.
- Berner, Christopher, Greg Brockman, Brooke Chan, Vicki Cheung, Przemysław Dębiak, Christy Dennison, David Farhi, et al. 2019. “基于大规模深度强化学习的 Dota 2.” Arxiv 预印本: 1912.06680.
- Besold, Tarek R., Artur d’Avila Garcez, Sebastian Bader, Howard Bowman, Pedro Domingos, Pascal Hitzler, Kai-Uwe Kühnberger, et al. 2017. “神经-符号学习与推理：一项调查与解释.” ArXiv 预印本: 1711.03902.
- Blouw, Peter, Eugene Solodkin, Paul Thagard, and Chris Eliasmith. 2016. “作为语义指针的概念：一种框架与计算模型.” 认知科学 40 (5): 1128–1162.
- Borràs, Júlia, Christian Mandery, and Tamim Asfour. 2017. “多接触类人机器人运动的全身支撑姿态分类法.” 科学机器人 2 (13).
- Chung, Wan Kyun, Li-Chen Fu, and Torsten Kröger. 2016. “运动控制.” 收录于 Siciliano and Khatib 2016, 163–194. doi:10.1007/978-3-319-32552-1_8.
- Davis, Ernest. 1990. 《常识性知识表示》. The Morgan Kaufmann Series in Representation and Reasoning. Burlington, MA: Morgan Kaufmann.
- Davis, Ernest. 2017. “常识推理的逻辑形式化：一项调查.” 人工智能研究杂志 59:651–723. doi:10.1613/jair.5339.
- Davis, Ernest, and Gary Marcus. 2015. “人工智能中的常识推理与常识知识.” ACM 通讯 58 (9): 92–103. doi:10.1145/2701413.




# J. Happa / 极地决策支持分析

通过模拟来帮助识别天气、磨损、气候问题或正在实施政策是否会影响任务。

- 工具开发目标。开发能够以最有效、高效的方式预测和应对韧性关切问题的工具。我们需要记录并不断改进决策者对其系统剖结构的自理解，以便他们能够实时衡量、评估、改进并沟通针对真实情况的主动和反应性韧性。这可以通过开发标注和视觉化分析工具来实现，以预测系统故障（这些连接到监控韧性 KPI 的后端系统）。

- 进行实验以生成数据。学术界通常依赖于模拟或可能是真实的数据，数据越贴近现实世界，对于减轻实际事故的效果就越好。现实世界数据中还存在模拟中不存在的噪声——这些噪声应该从实地演练中获取。

- 推动概念验证、新技术及其集成。目前缺乏足够的实证数据集。许多系统不够敏捷，无法适应不断演变的韧性格局。敏捷可能带来两个代价：(1) 对遗留系统的容忍度较低；(2) 不断尝试并将新技术集成到生产环境中。具体而言：

- 对遗留系统的低容忍度。一个韧性系统是内置冗余且仅与最新技术工作的系统。遗留系统在升级后应逐步淘汰，开发简单的迁移数据和系统的策略，以便持续审查和改进其基础设施，从而应对系统过时的想法。

- 始终演进。当系统面临故障切换风险或安全违规风险时，不断尝试和集成新技术在表面上看可能是个坏主意。然而，通过能够快速将新技术引入生产环境，并且不依赖于任何单一技术，来提高组织敏捷性，可能是更好的解决方案。

- 增加分布性与自主性。分析和决策系统中的自主性很重要，但可能没有被充分理解。基于自动化分析的机器自主性增加限制了人为错误，但也可能增加数字攻击面。

- 投资机构记忆。系统文档是有用的，但仅靠文档可能不够。提出改进机构记忆的方法可能会提高分析能力。这意味着没有任何资产（机器或人员）对于任务是必不可少的，而是通过分配规则并允许冗余来应对各种运营利益相关者。

- 使文档成为工作的一部分——文档记录可以在危机发生时提供有用信息（在信息可能不存在的地方提供信息）。

- 利益相关者参与。Happa 和 Fairclough [29] 讨论了让对同一情况有不同视角的许多利益相关者坐在一起根据对事件的共同理解进行讨论的想法。这符合北极理事会的建议：“不同的利益相关者将为会议带来不同的视角”。

**教育与意识。** 提高对可能的韧性问题的教育和意识可能是一项徒劳的努力，但限制威胁风险至关重要。

**增加基于纸质（或任何非计算机）的冗余解决方案。** 英国卫生和社会保健系统和国家医疗服务体系建议，“在事件管理系统受到网络攻击影响时，需要存在并实施纸质流程” [51]。这是从他们处理 Wannacry 勒索病毒事件中获得的教训之一。Happa 等人 [30] 讨论了务实失败评估如何有助于在网络攻击期间做出快速有效的决策。该模型有助于在正确的时间分析相关问题，无论数据是否可用。使用基于抽象的推理使风险所有者能够“某些”情境感知。该模型是针对纸质状态的情况设计的。

**军事、交通、企业、政府和学术界之间更强的合作**是必要的，以引入专业知识来应对更广泛的问题，并就如何应用分析达成共识。

# 结论

本章讨论了提高极地韧性的分析和决策挑战，以及当前学术界的研究可能如何解决这些问题。它概述了韧性管理的关键领域、挑战以及未来的发展建议。为了推进技术水平，我认为极地对人类和机器来说都是一个不友好的的环境，极地面临的挑战在于应对未来的许多变化——这使得这一挑战在未来变得特别有趣。

# 参考文献

- [1] Julia Allen. Measures for managing operational resilience. EDPACS, 44(6) 1–6, 2011.
- [2] Julia Allen, Pamela Courts, Nader Mehmanesh, Andrew Moore, Kevin Patrick, Robert Stockdard, and Randy Trezzic. Analyzing cases of resilience success and failure-research study. Technical report, Carnegie Mellon University, the Software Engineering Institute, 2012.
- [3] Arctic Council. Arctic resilience interim report. Technical report, Stockholm Environment Institute and Stockholm Resilience Centre, 2013.
- [4] Arctic Council. Arctic resilience report. Technical report, Stockholm Environment Institute and Stockholm Resilience Centre, 2016.
- [5] G. Carmel. Arctic resilience action framework; cooperation for a more resilient and prosperous arctic region, 2017.
- [6] Reza Arghande, Alexandra Von Meier, Laura Mehmanesh, and Lamine Mil. On the definition of cyber-physical resilience in power systems. Renewable and Sustainable Energy Reviews, 58:1060–1069, 2019.
- [7] Filip Bjøstrk, Martin Hansel, Janis Stamis, and Jelena Zdrovska. Cyber resilience-fundamentals for a definition. In New contributions to information systems and technologies, pages 311–316, 2015.
- [8] Deborah Bode and Richard Garland. Cyber engineering framework. MITRE TR11032.
- [9] Rita Borgos, Johannes Keither, David Chang, Eamon Maugourt, Harvey Hauser, and Min Chin. Anomaly-based visualization: Design guidelines and interpretations. In EuroGraphics (SART), pages 39–63, 2013.
- [10] Richard Caralli, Julia Allen, and David White. Resilience management: a maturity model for managing operational resilience. Addison-Wesley, 2010.
- [11] Varun Chandola, Arindam Banerjee, and Vivek Kumar. Anomaly detection: a survey. ACM Computing Surveys (CSUR), 13(3):15, 2009.
- [12] Fred Cohen. Information systems: a preliminary classification. Computers & Security, 16(2):94–114, 1997.
- [13] Greg Conti. Data Visualization: Graphical Techniques for Network Analysis. 2007.
- [14] Sadie, Michael Gold, Nick Moffat, James Happa, and Ioannis Agraraitis. CyberVis: Visualizing the potential impact of cyber attacks on the wider internet. In Technologies for Homeland Security (HIST), pages 73–79, 2013.
- [15] Ivan Davidson. Anomaly detection, explanation and visualization. Technical report. SGI Tech Rep., 2007.
- [16] Michael de Ches. Building cyber-resilience to resist threats. Network Security, 2012(4):5–8, 2012.
- [17] Dorothy Denning and Peter Neumann. General requirements and methods.
- [18] Daniel Langer, Ian Kerker, Matthew Bates, Cate Creek, Peter Lin, and Thomas Seeger. Resilience metrics. The Australian Journal of Management, 25(2):76–84, 2017.
- [19] ENISA. Detection of systems. Technical Report published by ENISA, 2011.
- [20] Yacai H, Jason R, Sadie C, and Philip A. Anomaly-based intrusion detection leveraging data. arXiv preprint:1805.0670, 2018. In 2011 IEEE International Conference for Homeland Security (HIST), pages 236–241, 2011.
- [21] Kyle Ganzamer, Leonard V bochtano. The of of of,,,,,, 1, 2012.
- [22] Huerta G, Vincent R, David D, and Enrique V. Resilient control...     5th International Symposium on Resilient Systems, pages 95–105, 2012.
- [23] Michael B, Robert R, and Richard P. Anomaly-based network detection: techniques and challenges. Computers & Security, 28(1):18–28, 2009.
- [24] Carl G and Matthew T. ‘conceptual models’ approach to organizational resilience. The Australian Journal of Management, 25(2):6, 2010.
- [25] Alexander U and Jesus J. Detection of anomaly in systems. An International Journal, 9:501, 2009.
- [26] Jassim H and Graham F. Model to facilitate discussions about cyber attacks. In Ethics and policies for cyber operations, pages 169–185. Springer, 2017.
- [30] Jassim H, Graham F, Jason R, Ioannis A, Michael G, and Sadie C. A system-failure assessment and resilience model. In ICISSP, pages 503–508, 2016.
- [31] Lane H and Aidong L. Future of security resilience: Lessons from visualization. IEEE Security, 30(6), 2017.
- [32] Jason H and Leonard V B. Cyber Capabilities: Yesterday, Today, and Tomorrow. Atlantic Council of the United States, 2012.
- [33] William H, Steven N, and James C. Business continuity modeling for cyber situational awareness. In NATO IST-148 Symposium on Defence Awareness, 2016.
- [34] Frederik H and Jill S. What cyber resilience looks like. Journal of business continuity & risk management, 7(2):721–728, 2012.
- [35] Jassim K. The mastering of anomaly detection: solving with visual analytics. Ethnographics Association, 2010.
- [36] Alexander K and Tariq A. Resilience and robustness of complex systems and networks. Adapt. Dyn. Res Syst, 57:66–84, 2014.
- [37] Manuel O and Alvaro C. Resilience of process control systems to cyber-physical attacks. In Nordic Conference on Security IT, pages 166–182. Springer, 2013.
- [38] Aleksandar L, Vincent E, Vipin K, Alexander U, and Jaidreeva. A comparative study of anomaly detection schemes in network intrusion detection. In IDS, pages 25–36. SIAM, 2003.


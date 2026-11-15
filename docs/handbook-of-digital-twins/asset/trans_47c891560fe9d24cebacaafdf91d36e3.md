

混合整数二次规划，使优化能够考虑起重机移动会影响机器之间的作业分配。

## 28.4.3 纺织工业认知服务

Lanificio Fratelli Piacenza 成立于 1733 年，是其市场细分领域公认的领先毛呢面料生产商。供应商向其提供清洁羊毛，他们在机器织机上将其织成面料。他们面临的挑战包括 (1) 为支持适当整经进行的织机设置，以及 (2) 减少由于纱线断裂导致的停机时间。作为一个面向非常动态且要求严格的市场的供应商，Piacenza 必须不断适应需求变化，因此相应调整生产计划以满足这些需求变化。异常和变化检测技术已应用于 Piacenza 提供的数据。该数据对应关于机器能耗的传感器读数。对能耗异常的检测使我们能够搜索此类异常的根本原因，并提出缓解措施。第 2.4.2 节介绍的快思考和慢思考分别负责处理已知的变化（异常）或对未知情况进行深入分析。另一方面，优化服务通过求解非关联机器上的并行机器调度问题（具有序列依赖的设置时间、作业分割和资源约束）来解决织造调度问题（Mourtos, Vatikiotis, and Zois 2021）。因此，在这种情况下，优化服务为所识别的完工时间最小化问题提供了新颖且有效的下界和三阶段启发式算法（Avgerinos et al. 2022）。此外，优化服务使操作员能够就为意外事件制定政策及其响应得出明智的决策。

## 28.5 结论

本章描述了实现认知数字孪生（CDTs）所需的架构和组件。我们介绍了语义技术的作用以及过程仿真建模、优化和分析服务的相关性。接下来，我们分享了关于我们实施和部署 CDTs 所遵循的方法论的经验。最后，我们描述了上述服务之间的协同作用，以解决石油炼制、金属成型和纺织行业的实际用例。本章描述的架构和服务已在原型级别使用多家公司提供的实际数据进行了验证和测试。我们实现的 CDTs 不包括从数字对象到物理对象的自动化数据流。此外，在撰写本文时，多个组件尚未集成到单一平台中。虽然 CDTs 尚未部署到生产环境，但本文分享了我们的见解和许多经验教训。

## 致谢

本章所展示的工作部分得到欧盟 H2020 项目 FACTLOG（869951）——面向流程行业的能源感知工厂分析的支持。

## 参考文献

Alexopoulos, Kosmas, Nikolaos Nikolakis, and George Chryssolouris. 2020. “面向制造业人工智能应用开发的数字孪生驱动监督机器学习.” International Journal of Computer Integrated Manufacturing 33 (5): 429–439.

Arp, Robert, Barry Smith, and Andrew D Spear. 2015. 使用基本形式本体构建本体. Mit Press.

Avgerinos, Ioannis, Ioannis Mourtos, Stavros Vatikiotis, and Georgios Zois. 2022. “具有作业分割、设置资源和序列依赖的非关联机器调度.” International Journal of Production Research 61: 1–23.

Barber, C Bradford, David P Dobkin, and Hannu Huhdanpaa. 1996. “凸包的 QuickHull 算法.” ACM Transactions on Mathematical Software (TOMS) 22 (4): 469–483.

Batty, Michael. 2018. “数字孪生.” Environment and Planning B: Urban Analytics and City Science 2018, 45(5): 817–820

Beckett, David, Tim Berners-Lee, Eric Prud'hommeaux, and Gavin Carothers. 2014. “RDF 1.1 Turtle.” World Wide Web Consortium 18–31.

Benda, Frank, Roland Braune, Karl F Doerner, and Richard F Hartl. 2019. “用于具有替代资源、序列依赖设置时间和阻塞的流水车间调度问题的机器学习方法.” OR Spectrum 41 (4): 871–893.

Cameron, Ian T, and Katalin Hangos. 2001. 过程建模与模型分析. Elsevier.

Durrans, Muhammad Amin, Iftikhar Ahmad, Manabu Kano, and Shinji Hasebe. 2018. “在不确定进料组成条件下，原油蒸馏装置节能高效运行的人工智能方法.” Energies 11 (11): 2993.

Eirinakis, Pavlos, and Gregory Koronakos. 2022. “在输入不确定性下，面向工业过程的合格产品生产优化数学规划方法.” IFAC-PapersOnLine 55 (10): 2822–2827.

Eramo, Romina, Francis Bordeleau, Benoit CombeMale, Mark van Den Brand, Manuel Wimmer, and Andreas Wortmann. 2021. “概念化数字孪生.” IEEE Software 39 (2): 39–46.

Evans, Jonathan St BT, and Keith E Stanovich. 2013. “高级认知的双过程理论：推进辩论.” Perspectives on Psychological Science 8 (3): 223–241.

Francis, Nadime, Alastair Green, Paolo Guagliardo, Leonid Libkin, Tobias Lindaaker, Victor Marsault, Stefan Plantikow, Mats Rydberg, Petra Selmer, and Andrés Taylor. 2018. “Cypher：一种用于属性图的不断发展的查询语言.” 2018 年国际数据管理会议论文集. 2018: 1433–1445. 计算机协会，纽约, 美国. https://doi.org/10.1145/3183713.3190657

Friedrich, Jonas, Deena P Francis, Sanja Lazarova-Molnar, and Nader Mohamed. 2022. “面向智能制造的数据驱动数字孪生框架.” Computers in Industry 136: 103586.

Gharaee, Ali, Jinzhi Lu, Oliver Stoll, Xiaochen Zheng, Shaun West, and Dimitris Kiritsis. 2020. “数字孪生开发需求识别的系统工程方法.” 载于 IFIP 生产管理系统先进国际会议, 82–90. Springer.

Gu, Wugen, Kan Wang, Yuqing Huang, Bingjian Zhang, Qinglin Chen, and Chi-Wai Hui. 2015. “多级原油蒸馏过程的能源优化.” Chemical Engineering & Technology 38 (7): 1243–1253.

Han, Jeongwoo, Grant S Forman, Amgad Elgwainy, Hao Cai, Michael Wang, and Vincent B DiVita. 2015. “石油炼制资源效率的比较评估.” Fuel 157: 292–298.

Jeong, Jeong-Im, and Gyo-Young Cho. 2012. “用于监测方差-协方差矩阵的多元 EWMA 控制图.” Journal of the Korean Data and Information Science Society 23 (4): 807–814.

Jinzhi, Lu, Yang Zhaorui, Zheng Xiaochen, Wang Jian, and Kiritsis Dimitris. 2022. “从基于模型的系统工程视角探索认知数字孪生概念.” The International Journal of Advanced Manufacturing Technology 121 (9): 5835–5854.

Kalaboukas, Kostas, Joe Rožanec, Aljaž Košmerlj, Dimitris Kiritsis, and George Arampatzis. 2021. “连接和敏捷供应网络中认知数字孪生的实现—一种运营模型.” Applied Sciences 11 (9): 4103.

Kujawinska, Agnieszka, Katarzyna Vogt, and Adam Hamrol. 2016. “人类动机在生产过程质量检验中的作用.” 载于：制造人体工程学进展：管理未来企业：AHFE 2016 先进制造人因国际会议论文集, 2016 年 7 月 27-31 日, 美国佛罗里达州华特迪士尼世界®. Springer International Publishing, 2016: 569–579.

Li, Hongcheng, Dan Yang, Huajun Cao, Weiwei Ge, Erheng Chen, Xuanhao Wen, and Chongbo Li. 2022. “基于数据的混合 Petri 网能源消耗行为建模，用于节能制造系统的数字孪生.” Energy 239: 122178.

Lin, Boqing, and Xuan Xie. 2015. “中国石油炼制行业的节能潜力：证据与政策启示.” Energy Conversion and Management 91: 377–386.

Lin, Shan, and Liping Liu. 2021. “罐头厂状态评估与诊断的主成分分析控制图方法.” Advances in Civil Engineering 2021: Article ID 7703359.


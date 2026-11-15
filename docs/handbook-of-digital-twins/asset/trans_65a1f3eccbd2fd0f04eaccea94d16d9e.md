

将结构尺度模型（视为均质）与材料尺度模型（代表主要砌体异质性）相关联的过程（Sharma et al. 2021）。均质化通常基于结构的代表性体元素（RVE），通过精细的建模策略（如基于块的方法）进行建模。均质化可以先验地进行，通过RVE在唯一的第一步中推导机械性能，并在第二步中将其引入结构尺度模型。或者，多尺度方法（Funari et al. 2022）允许在材料尺度和结构尺度模型之间进行更强的逐步耦合。

在大单元模型中，结构被理想化为刚性或可变形的面板尺度结构构件。通常，可以识别两种主要结构构件：墙墩和圈梁（见图 5.4c）。大单元模型是砌体结构抗震评估中最广泛采用的策略，尤其是在从业者中，因为其实现和计算简单。另一方面，它们存在一些缺点。首先，面内与面外破坏的解耦可能导致抗震能力的常规估计，因为在现实中，面内和面外损伤可能同时出现。最后，结构需要先验地理想化为墙墩和圈梁，这可能导致定义一个不能很好地代表实际结构的机械系统，尤其是在存在非常不规则开口布局的情况下（Doltsahi and Yekrangnia 2015; Pantò et al. 2017）。替代性公式使用宏观离散单元对结构进行离散化（Malomo and DeJong 2021）。

基于几何的模型将结构的几何形状作为唯一输入，除了加载条件之外（见图 5.4d）。结构被建模为刚体，其结构平衡通过极限分析定理（即静态或运动学）进行评估。基于静态定理的计算方法可以为砌体拱形结构的平衡状态研究提供非常有用的结果，并且似乎特别适用于预测复杂砌体结构的崩塌机制（以及崩塌倍数器）（Block, Ciblac, and Ochsendorf 2006）。基于运动学定理的极限分析方法在过去几十年中被广泛用于有效评估现有砌体建筑（Giuffrè 1991），因为它们允许通过局部崩塌机制的分析快速进行砌体建筑的抗震评估（Funari et al. 2020, 2021a, 2021b; Colombo et al. 2022）。

上述所有讨论的方法都有其优缺点。选择采用哪种数值建模策略取决于分析类型、数据质量、时间可用性等。数字孪生（DT），作为一种计算工具，应能够模拟不同的现象，这将通过寻求整合具有不同复杂程度的建模策略来实现，从超简单快速的分析模型到超复杂的多尺度或微建模策略（Lourenço et al. 2022）。

### 5.3.2 用于评估遗产建筑结构行为的预测模型

DT范式的特征之一是能够存储大量信息，并使用具有高计算潜力和精巧性的技术对其进行处理。这使得能够处理影响物理资产结构性能的参数的不确定性。DT范式的这种特征似乎值得研究，用于历史砌体建筑的结构评估。砌体构件，即单元和接缝，根据环境因素和施工现场的原材料可用性显示出广泛的变异性。此外，施工技术和泥瓦匠的技能会影响结构的局部破坏机制和承载能力（Vadalà et al. 2022; Szabó, Fanari, and Lourenço 2023）。由于砌体固有的非线性和离散的材料特性（Gonen et al. 2021），解决所有类型的破坏模式并提供结构响应的准确预测具有挑战性。

由于其变异性，砌体性能表现出概率性质。因此，考虑不确定性并允许分析其对响应影响的概率结构模型，可以成为处理与随机变量相关问题的可靠工具，并已被少数作者最近研究（Pulatsu et al. 2022; Saloustros et al. 2019）。此外，可以生成耦合数值和概率分析的混合模型，以评估砌体结构的结构响应，包括不确定性的影响。在处理这种结构工程问题时，采用适当的统计或机器学习方法可能会带来显著改进，因为它们允许丰富和放宽模型对数据所做的假设集合，从而能够在更复杂且理解较少的场景中创建模型。

### 5.4 结论与未来发展

本章综合了DT范式在BCH结构完整性保护中可能带来的潜在创新。调查了应用DT范式必须包含的必要组件，即几何模型生成、合适的计算建模策略以及开发实现统计和机器学习方法的预测工具。为在BCH结构保护的背景下有意义地实施DTs而识别的未来研究和创新机会如下：
- (1) 对DT和HBIM概念进行系统比较，以明确界定两个概念之间的差异和相互联系；
- (2) 定义结构性DT实施的方法框架；
- (3) 开发DT作为模拟和预测目的的计算模型；
- (4) 增加结构工程领域和BCH保护中的实际实现。

## 参考文献

- Angeliù, Grigor, Dario Coronelli, and Giuliana Cardani. 2020. “历史砌体建筑数字孪生应用的仿真模型开发：数值与实验现实的整合.” Computers and Structures 238 (10月): 106282. https://doi.org/10.1016/j.compstruc.2020.106282.
- Block, P, T Ciblac, and J Ochsendorf. 2006. “拱形砌体建筑的实时极限分析.” 计算机与结构 84 (29–30): 1841–52.
- Camposano, José Carlos, Kari Smolander, and Tuomas Ruippo. 2021. “理解建筑资产数字孪生的七个隐喻.” IEEE Access 9: 27167–81. https://doi.org/10.1109/ACCESS.2021.3058009.
- Castellazzi, Giovanni, Nicolò Lo Presti, Antonio Maria D'Altri, and Stefano de Miranda. 2022. “Cloud2FEM: 基于现有/历史结构点云的有限元网格生成器.” SoftwareX 18: 101099.
- Chiacío, Manuel, María Megía, Juan Chiacío, Juan Fernandez, and María L. Jalón. 2022. “结构数字孪生框架：公式与技术整合.” 建筑自动化 140 (8月): 104333. https://doi.org/10.1016/J.AUTCON.2022.104333.
- Colombo, Carla, Nathanaël Savalle, Anjali Mehrotra, Marco Francesco Funari, and Paulo B Lourenço. 2022. “砌体角的实验、数值和分析研究：水平伪静态荷载方向的影响.” 建筑与建筑材料 344: 127969. https://doi.org/10.1016/j.conbuildmat.2022.127969.
- Cundall, P. A. and O. D. Strack. 1979. “颗粒集合体的离散数值模型.” 岩土力学 29 (1): 47–65.
- D'Altri, Antonio Maria, Vasilis Sarhosis, Gabriele Milani, Jan Rots, Serena Cattari, Sergio Lagomarsino, Elio Sacco, Antonio Tralli, Giovanni Castellazzi, and Stefano De Miranda. 2020. “非加固砌体结构计算分析的建模策略：综述与分类.” 工程计算方法档案 27: 1153–85. https://doi.org/10.1007/s11831-019-09351-x.
- Daniotti, Bruno, Alberto Pavan, Cecilia Bolognesi, Claudio Mirarchi, and Martina Signorini. 2022. “建筑行业的数字化转型：从BIM到数字孪生.” 在《数字化转型》中，由Antonella Petrillo, Fabio De Felix, Monica Violeta Achim 和 Nawazish Mirza 编辑，13. Intech Open. https://doi.org/10.5772/intechopen.103726.
- Degli Abbati, Stefania, Antonio Maria D'Altri, Daria Ottonelli, Giovanni Castellazzi, Serena Cattari, Stefano de Miranda, and Sergio Lagomarsino. 2019. “基于非线性静态分析对复杂历史砌体建筑中相互作用结构单元的抗震评估.” 计算机与结构 213: 51–71.




资产通过数字化层[20]融入现实世界。相比之下，CDT 功能层更侧重于双子在虚拟空间中的功能，包括模型管理、服务管理和双子管理层。它们通过数据摄入/处理层与物理实体集成，并通过顶部的用户交互层与用户交互。

## 4.4 CDT 应用

作为一种新兴概念，CDT 在工业界尚未得到广泛实施和验证。因此，大多数已发表的研究要么探讨 CDT 的理论视角，要么专注于 CDT 的愿景。然而，一些正在进行的研究和项目旨在通过将其应用于不同行业场景来验证 CDT 的可行性。

Zhou 等人 [22] 将动态知识库与 DT 模型相结合，以实现面向自主制造的知识驱动智能服务。知识驱动的 DT 支持智能感知、模拟、理解、预测、优化和控制策略。该方法已应用于三个用例：制造流程规划、生产排程和生产流程分析。此外，Yitmen 等人 [23] 使用 CDTs 支持建筑信息管理。通过 CDTs，基于知识图建模和跨整个建筑生命周期的推理，主要支持流程优化和决策。

欧盟项目 COGNITWIN（通过主动自学习混合 DT 实现认知工厂）是一个旨在增强现有过程控制系统认知能力的专门项目，从而实现自我组织并为不可预测的行为提供解决方案。先前提到的概念架构（如图 4.1 所示）已应用于过程工业的多个用例 [2]。

FACTLOG（面向过程工业的能源感知型工厂分析）项目旨在通过结合数据驱动和模型驱动的 DT 来改进复杂过程系统的认知能力。CDT 是该项目的主要推动技术之一。该项目的一个应用案例已在 [24,25] 中介绍，其中一个可操作的 CT 被应用于支持欧洲汽车行业原始设备制造商的需求预测和生产规划。

1 https://www.sintef.no/projectweb/cognitwin/.

2 https://www.factlog.eu/.

在另一个欧盟项目 QU4LITY（零缺陷制造的数字现实）中，³ CDT 已被用作 DT 的语义增强版本，以支持自主质量。为提高产品质量，采用了名为 RMPFQ（资源、材料、工艺、特性/功能、质量）[26,27] 的数据模型以支持本体开发。为飞机装配系统创建了一个 CDT 模型，以实现装配排程的权衡、基于模型的系统工程中的数据流、语义模型、系统架构以及用于验证的协同仿真 [28,29]。

## 4.5 讨论

作为一种新兴概念，CDT 仍处于发展的非常早期阶段。因此，为了充分实现其愿景，还有许多挑战有待解决。CDT 发展的主要挑战总结如下，表明了未来研究的潜在机会：

- 1. 知识管理：功能完善且全面的知识库是 CDT 认知能力的核心。CDT 知识管理的主要挑战可分为知识表示、获取和知识更新 [30]。

- 2. DT 模型集成：CDT 实现中涉及的多个 DT 模型可能由复杂系统的不同利益相关者分别创建，对应于整个生命周期中其不同的子系统或组件。它们需要通过双子管理层集成并恰当地编排到 CDT 架构中。此外，利益相关者可能为其 DT 模型采用不同的标准、协议和结构。这种异质性导致数据层面的互操作性问题。此外，这使得 DT 模型具有更复杂的特征和服务以供集成。

- 3. 标准化：DT 的标准化是实现 CDT 范式的基础。多个标准制定组织（SDO）正在开发 DT 标准，例如 ISO、W3C-WoT、工业互联网联盟（IIC）和 Plattform Industrie 4.0 [31]。统一和协调不同 SDO 开发的相关 DT 标准并非易事。一些现有的标准和协议可以被视为替代方案。例如，Plattform Industrie 4.0 提供资产管理壳（AAS）作为 RAMI4.0 [20] 的一部分。ETSI 行业规范组（ISG）提出下一代服务接口-链接数据（NGSI-LD）API [32]。W3C-WoT 工作组提出 WoT 事物描述（WoT TD），这是一份正式的 W3C 推荐标准 [33]。此类标准和 API 在之前的研究中已有讨论 [2,31]。

- 4. 实施：一个 CDT 可能包括覆盖多个生命周期阶段的多个物理系统，涉及不同企业的利益相关者。因此，CDT 的实施既需要组织内协作，也需要组织间协作。除了上述互操作性问题外，它还在项目管理、数据隐私/安全问题以及知识产权保护方面带来新的挑战。此外，缺乏 CDT 实施的成功示范进一步增加了其风险。从管理角度来看，CDT 的开发和实施应由经验丰富的专家组织，并遵循适当的项目管理方法。

## 致谢

本文所呈现的工作部分获得欧盟 H2020 项目 FACTLOG（869951）——面向过程工业的能源感知型工厂分析，以及欧盟 H2020 项目 QU4LITY（825030）——零缺陷制造的数字现实的支持。

## 参考文献

- [1] Stefan Boschert, Christoph Heinrich, and Roland Rosen. 下一代数字孪生. In Proc. tmce, pages 209–218. Las Palmas de Gran Canaria, Spain, 2018.

- [2] Sailesh Abburu, Arne J Berre, Michael Jacoby, Dumitru Roman, Ljiljana Stojanovic, and Nenad Stojanovic. 面向过程工业的 Cognitwin 混合认知数字孪生. In 2020 IEEE International Conference on Engineering, Technology and Innovation (ICE/ITMC). IEEE, 2020: 1-8.

- [3] Fei Tao, He Zhang, Ang Liu, and AYC Nee. 工业中的数字孪生：现状. IEEE Transactions on Industrial Informatics, 15(4):2405–2415, 2019.

- [4] Pavlos Eirinakis, Stavros Lounis, Stathis Plitsos, George Arampatzis, Kostas Kalaboukas, Klemen Kenda, Jinzhi Lu, Joze M Rozanec, and Nenad Stojanovic. 面向生产韧性的认知数字孪生：一个概念框架. Information, 13(1):33, 2022.

- [5] Min Chen, Francisco Herrera, and Kai Hwang. 认知计算：架构、技术与智能应用. IEEE Access, 6:19774–19783, 2018.

- [6] RL Solso, MK MacLin, and OH MacLin. 认知心理学. Pearson Education, New Zealand, 2005.

- [7] Liqiao Xia, Pai Zheng, Xinyu Li, Robert X Gao, and Lihui Wang. 面向认知预测性维护：基于图的方法综述. Journal of Manufacturing Systems, 64:107–120, 2022.

- [8] Mohammad Abdullah Al Faruque, Deepan Muthirayan, Shih-Yuan Yu, and Pramod P Khargonekar. 制造系统的认知数字孪生. In 2021 Design, Automation & Test in Europe Conference & Exhibition (DATE). IEEE, 2021: 440–445.

- [9] Ahmed El Adl. 认知数字孪生：愿景、架构框架与分类. 技术报告, 2016. https://www.slideshare.net/slideshow/embed_code/key/JB60Xqcn.

- [10] Fariz Saracevic. 认知数字孪生. 技术报告. https://www.slideshare.net/BosniaAgile/cognitive-digital-twin, 2017.

- [11] Felipe Fernandez, Angel Sanchez, Jose F Velez, and A Belen Moreno. 使用数字孪生的具有意识的共生自主系统. From Bioinspired Systems and Biomedical Applications to Machine Learning: 8th International Work-Conference on the Interplay Between Natural and Artificial Computation, IWINAC 2019, Almería, Spain, June 3–7, 2019, Proceedings, Part II 8. Springer International Publishing, 2019: 23–32.

- [12] Jinzhi Lu, Xiaochen Zheng, Ali Gharaei, Kostas Kalaboukas, and Dimitris Kiritsis. 第五届先进制造工业4.0模型国际会议论文集：AMP 2020. Springer International Publishing, 2020: 105–115.

- [13] Lu Jinzhi, Yang Zhaorui, Zheng Xiaochen, Wang Jian, and Kiritsis Dimitris. 从基于模型的系统工程视角探索认知数字孪生概念. The International Journal of Advanced Manufacturing Technology, 2022, 121(9–10): 5835–5854.

- [14] Pavlos Eirinakis, Kostas Kalaboukas, Stavros Lounis, Ioannis Mourtos, Joze M Rozancec, Nenad Stojanovic, and Georgios Zois. 增强数字孪生的认知能力. 2020 IEEE International Conference on Engineering, Technology and Innovation (ICE/ITMC). IEEE, 2020: 1-7.

- [15] Muhammad Intizar Ali, Pankesh Patel, John G Breslin, Ramy Harik, and Amit Sheth. 面向智能制造的认知数字孪生. In IEEE Intelligent Systems, 2021, 36(2): 96–100.

- [16] Xiaochen Zheng, Jinzhi Lu, and Dimitris Kiritsis. 认知数字孪生的出现：愿景、挑战与机遇. International Journal of Production Research, 2022, 60(24): 7610–7632.

- [17] Jean Duprez. MBSE 元模型和语义规则的结构化、形式化和映射方法. INCOSE International Symposium, 29(1):22–36, 2019.

- [18] ISO 23247-1. ISO 23247-1:2021 自动化系统与集成——制造业数字孪生框架——第1部分：概述与一般原则. 技术报告, 2021: ISO 23247-1:2021(en), Automation systems and integration — Digital twin framework for manufacturing — Part 1: Overview and general principles


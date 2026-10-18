
## 基于机器学习的电催化剂和光催化剂设计与发现

Haoxin Mai, Tu C. Le, Dehong Chen, David A. Winkler, and Rachel A. Caruso

**引用本文:** *Chem. Rev.* 2022, 122, 13478–13515

摘要: 电催化剂和光催化剂是实现可持续未来的关键，能够产生清洁燃料、降低全球变暖的影响，并为环境污染提供解决方案。改进的催化剂设计流程和对电/光催化过程的更好理解对于提升催化剂效果至关重要。数据科学和人工智能的最新进展有望加速电催化和光催化研究，特别是通过机器学习实现对大规模材料化学空间的快速探索。本文在此提供了对电催化和光催化研究中所使用的机器学习技术的全面介绍以及批判性综述。电/光催化剂数据的来源及目前对这些材料的数学特征表示方法进行了描述，常用的机器学习方法作了总结，并评估了电/光催化剂模型的质量和实用性。提供了机器学习模型在新型电催化剂和光催化剂发现中的应用示例，以及用于阐明电催化或光催化反应机理的用法。综述为材料科学家在电催化和光催化研究中选择机器学习方法提供了指南。机器学习在催化科学中的应用标志着先进、下一代催化剂的设计和合成方式发生范式转变。

Figure 1. Workflow for applying ML techniques in the development of catalytic materials. It starts with data collection, featurization, model training, model evaluation, and eventually exploring the unknown materials space by using the ML models. The results of exploration will feed into the original data set for model improvement, and the materials with good properties will proceed to practical application.

图 1. 应用机器学习技术开发催化材料的工作流程。它从数据收集、特征化、模型训练、模型评估开始，最终利用机器学习模型探索未知材料空间。探索的结果将反馈到原始数据集以改进模型，具有良好性能的材料将进入实际应用。

![](img/385acff8214d70e1094d2d47342cdb40_0_0.png)

The development of globally sustainable energy systems and environmental protection are two critical challenges for this century, as population and industrialization expand.

全球可持续能源系统的发展和环境保护是本世纪两项关键挑战，随着人口增长和工业化扩张。

In particular, the generation of high-purity fuels from clean sources is a major research and development focus.

特别是从清洁来源生产高纯度燃料是主要的研究与发展重点。

Producing chemical fuels from earth-abundant resources such as water, carbon dioxide, and nitrogen requires next-generation electrocatalysts and photocatalysts.

从水、二氧化碳和氮等丰裕资源生产化学燃料需要下一代电催化剂和光催化剂。

Removal of pollutants, bacteria, and heavy metals from water using cheap, efficient processes is also essential for maintaining an inhabitable planet, where photocatalytic and electrocatalytic reactions play important roles.

利用廉价高效的工艺从水中去除污染物、细菌和重金属对于维持宜居星球至关重要，而光催化和电催化反应在此过程中发挥重要作用。

Clearly, the discovery of higher efficiency, nontoxic electrocatalysts and photocatalysts synthesized from abundant elements is critical to realizing this future.

显然，发现高效、无毒且由丰裕元素合成的电催化剂和光催化剂对于实现这一未来至关重要。

However, the number of catalysts that can be synthesized in principle is vast, much too large to be explored through laboratory experimentation alone.

然而，理论上可合成的催化剂数量庞大，远超仅靠实验室实验探索的范围。

To accelerate catalyst discovery, first-principles computational chemistry, especially density functional theory (DFT), is being increasingly employed.

为了加速催化剂发现，第一性原理计算化学，特别是密度泛函理论（DFT），正日益被采用。

In particular, the recent development of high throughput DFT calculations enables in silico catalyst screening and exploration of unknown material spaces.

特别是最近高通量 DFT 计算的发展使得在 silico 催化剂筛选和未知材料空间的探索成为可能。

However, because of the complexity of catalytic materials and the breadth of their applications, computationally expensive and time-consuming DFT calculations are still unable to explore the whole catalyst composition space.

然而，由于催化材料的复杂性以及其应用范围的广阔，昂贵且耗时的 DFT 计算仍然无法探索整个催化剂组成空间。

Catalyst researchers are putting intensive effort into understanding structure–property relationships, interpreting data patterns, and extracting knowledge from high volume, multidimensional material databases.

催化剂研究人员正全力致力于理解结构–性质关系、解读数据模式，并从高容量、多维材料数据库中提取知识。

More effective strategies are therefore needed to tackle these complex issues.

因此，需要更有效的策略来应对这些复杂问题。

be used to make predictions.27–29 ML algorithms have recently been shown to accelerate discovery and the optimization of functional materials for real world applications such as catalysts, photovoltaics, optoelectronic materials, and thermoelectrics.26,30–36 ML algorithms complement expensive, time- and resource-intensive first-principles electronic structure calculations to provide insight into complex, multidimensional structure–property relations.31,37–46 ML techniques can interpret and model a wide range of data and are useful for de novo discovery of important physical and chemical principles.47–51 The application of ML to materials science will result in a step-change in theory and methods for the discovery of next-generation functional materials. Here we review recent progress (2016 onward) in the application of ML to the discovery, development, and design of electrocatalysts and photocatalysts. Excellent reviews exist that summarize the impact of ML in general catalysis informatics for a wide range of catalytic processes or for one or two specific reactions (e.g., the electrolytic hydrogen evolution reaction (HER)).35,52–55 Recent, comprehensive, critical reviews of cutting-edge ML algorithms and their applications to electrocatalysts and photocatalysts are lacking. To address this deficiency, we summarize ML methods commonly used for electrocatalyst and photocatalyst discovery, critically review the literature in this field, and provide a perspective into the future evolution of AI and ML technology and its impact on electro/photocatalyst research and development. This review consists of four sections. Section 1 introduces ML and its application to materials science. In Section 2, the process of implementing ML methods for electro/photocatalytic systems is described and a concise summary of ML algorithms and their advantages and limitations is provided. Section 3 reviews the literature on ML-based electro/photocatalyst design, discovery, and development, and exemplifies this method for materials, such as metals and oxides. Section 4 provides conclusions and a perspective on current challenges and future aims in ML and ML-based catalyst design. This review aims to guide materials scientists in the selection of ML methods for electro/

- 1. 引言 13479
- 2. 机器学习建模 13480
- 2.1. 数据收集 13480
- 2.2. 特征化 13482
- 2.2.1. 描述符生成 13482
- 2.2.2. 描述符选择 13483
- 2.3. 算法选择与模型训练 13484
- 2.3.1. 多元线性回归 13484
- 2.3.2. 支持向量机 13486
- 2.3.3. 决策树 13487
- 2.3.4. 神经网络 13487
- 2.3.5. 集成学习 13488
- 2.3.6. 聚类 13489
- 2.3.7. 其他算法 13490
- 2.4. 模型验证 13491
- 3. 机器学习在电催化剂和光催化剂中的应用 13492
- 3.1. 电催化 13492
- 3.1.1. 互金属 13492
- 3.1.2. 电催化氧化物 13495
- 3.1.3. 单原子催化剂 13496
- 3.1.4. 其他电催化剂 13498
- 3.2. 光催化 13498
- 3.2.1. 用于水分解的光催化有机物 13499
- 3.2.2. 用于水分解的光催化氧化物 13499
- 3.2.3. 用于污染物降解的光催化氧化物 13501
- 4. 结论与展望 13502
- 4.1. ML在电/光催化研究中的使用概述 13502
- 4.2. 数据驱动电/光催化剂设计与发现的陷阱 13502
- 4.3. 机器学习在电/光催化应用中的挑战与机遇 13503
- 作者信息 13504
- 通讯作者 13504
- 作者 13504
- 注释 13504
- 简介 13504
- 致谢 13505
- 参考文献 13505

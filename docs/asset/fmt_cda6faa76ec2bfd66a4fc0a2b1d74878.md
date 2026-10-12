
因此，开展了额外的密集时间序列植被生产力分析，以分析并突显植被健康的长期趋势。利用十六天周期的中分辨率成像光谱辐射计（MODIS）数据推导归一化差异植被指数（NDVI），这是一种广泛使用的植被健康替代指标。这一额外分析还有助于处理小岛屿等较小区域全球森林数据的不一致性。这种密集时间序列植被生产力分析有助于评估植被趋势的空间和时间范围。结果显示，总体而言，自 2018 年以来植被生产力略有增加，尽管降水呈下降趋势（图 10.3 和 10.4）。

![Figure 10.3 Average vegetation productivity trend. ¶ Source: GEFIEO.](img/fig10.3.jpg)

*图 10.3* 平均植被生产力趋势。¶ *来源*：GEFIEO。

![Figure 10.4 Monthly precipitation trend. ¶ Source: GEFIEO.](img/fig10.4.jpg)

*图 10.4* 月降水趋势。¶ *来源*：GEFIEO。

鉴于地形陡峭且深入茂密森林存在后勤挑战，IEO 使用无人机收集毁林数据样本以训练^()

虽然无人机已广受欢迎，但在使用时必须优先遵守监管要求。IEO 团队认真获取了必要的政府许可，并严格遵守无人机操作法规，包括高度限制和飞行时间限制。为回应当地关切，无人机在林业部门官员在场的情况下部署。严格措施确保无人机仅在指定空域内运行，避开机场和私人财产。除了遵守当地有关无人机的法规外，团队还参考了 [`www.dji.com/flysafe/geo-map`](https://www.dji.com/flysafe/geo-map) 等资源以获取无人机部署的初步信息（见 图 10.5）。

![Figure 10.5 Map showing the restricted areas and project site for drone deployment.](img/fig10.5.jpg)

*图 10.5* 显示无人机部署限制区域和项目地点的地图。

这一地理空间数据在评估中的应用案例指出了对更好本地验证数据的需求，因为 WDPA 等全球数据集可能不一致。这对小岛屿发展中国家尤为重要，这些国家空间范围较小且海岸线高度不规则，需要更精确的边界划分以进行空间分析或规划。

## 在具有挑战性的评估环境中利用地理空间数据

全球环境基金（GEF）拥有大量（33%）位于受冲突影响国家的环境项目（GEF-STAP, 2018）。图 10.6 中的地图显示了冲突热点地区的 GEF 支持干预措施。脆弱和冲突背景下的发展项目复杂、难以到达、孤立且不安全，这些地区面临各种挑战，常规信息流难以维持。必须调整标准工具和流程，以收集信息用于项目设计、实施以及监测与评价（M&E）。在此背景下，后勤、时间和资源限制至关重要，地理空间方法显得尤为有用。我们已经看到，通过地理空间数据和方法得出的背景和基线信息如何帮助我们更清晰地构建评价问题。这对任务规划也很有用。此外，当与其他信息来源结合时，地理空间数据有助于识别因果因素，如环境退化和冲突的驱动因素，并量化栖息地退化和损失的程度。不同类型传感器的可用性使我们能够透过云层在夜间或恶劣天气下进行观测。

![Figure 10.6 GEF-supported interventions with conflict hotspots. ¶ Source: GEFIEO.](img/fig10.6.jpg)

*图 10.6* 冲突热点地区的 GEF 支持干预措施。¶ *来源*：GEFIEO。

# 利用无人机与地理空间技术进行评估

通过无人机收集的遥感数据可用于在难以到达、孤立和不安全的区域进行快速评估。无人机可快速部署，在短时间内收集更精细的数据。使用无人机令人振奋之处在于，能够捕捉影像资料，后续可用于增强知识和学习产品。在对全球环境基金（GEF）主流化生物多样性支持的评估中（GEF IEO, 2019），独立评价办公室（IEO）利用无人机评估不同项目地点非法采矿和伐木区域的范围，并收集实地核查数据以验证卫星数据产品。在对哥伦比亚的实地任务中，评估人员无法轻松安全地进入非法采矿点（图 10.7），在获得当局许可后，不得不从安全距离部署无人机。

![Figure 10.7 Drone image showing illegal mining area near a project site in Colombia; Pic: Anupam Anand.](img/fig10.7.jpg)

**图 10.7** 无人机影像显示哥伦比亚项目地点附近的非法采矿区域；摄影：Anupam Anand。

利用无人机收集地理空间数据不仅提供了环境退化的视觉证据，我们还将这些数据输入机器学习分类算法，以帮助划定采矿区及相关的环境退化范围。哥伦比亚太平洋地区云层覆盖率高，光学遥感平台无法穿透。然而，可穿透云层的雷达数据被用于训练分类模型（图 10.8）。

![Figure 10.8 Mining area classification using machine learning based on optical and radar data. ¶ Source: GEFIEO.](img/fig10.8.jpg)

**图 10.8** 基于光学和雷达数据，利用机器学习进行采矿区分类。¶ **来源**：GEF IEO。

这些区域与冲突及项目位置数据叠加，有助于回答关于项目干预的相关性和有效性的问题（图 10.9）。

![Figure 10.9 The map shows mining areas overlap with the hotspots of conflict and conservation in Colombia. ¶ Source: GEF IEO.](img/fig10.9.jpg)

**图 10.9** 地图显示哥伦比亚采矿区与冲突热点和保护热点的重叠情况。¶ **来源**：GEF IEO。

此外，结果被用于更深入地考察冲突与环境结果之间的相互关系，并通过实地访谈和文献分析进行了验证。例如，表明冲突后时期森林砍伐增加的结果（图 10.10），通过访谈关键知情人和项目参与者收集的数据得到了验证。^()

![Figure 10.10 Increase in deforestation in the project area during the post-conflict period.](img/fig10.10.jpg)

**图 10.10** 冲突后时期项目区域内森林砍伐的增加。

## 应对数字基础设施和资源需求

大规模分析卫星数据需要使用高性能计算机、专业软件以及强大的数据和 IT 基础设施，而这些资源通常在评估办公室中无法获得。为应对这些挑战，我们采取了充分利用现有资源的方法。例如，我们利用现有计算资源的能力来缓解其中一些障碍。一项值得注意的技术是利用并行计算，这是一种有效利用现代台式机和笔记本电脑中多个处理核心的方法。这种方法高效地分配计算任务，显著缩短了处理时间。实施并行计算通常只需对编程语言代码进行微小修改，且受 `R`、`Python` 和 `Stata` 等广泛使用的统计软件包支持。

为扩大分析规模，我们还转向云计算平台。例如，在利用森林覆盖数据评估保护区时（Hansen et al., 2013），我们在谷歌的云计算平台上进行分析，大幅缩短了处理时间。

此外，我们的工作还包括与外部组织的宝贵合作。值得注意的是，我们与美国国家航空航天局（`NASA`）合作，获取高分辨率图像和生态预测数据用于事前评估（Thieme et al., 2020），使用 `AID` 数据对项目位置进行地理编码（Runfola et al., 2020），并与马里兰大学合作，受益于其技术指导、数据资源和额外计算支持，开展了一项基于混合方法的影响评估，重点关注保护区的有效性（GEF IEO, 2016）。

## 讨论与结论

地理空间技术属于快速发展的领域之一，全球地理空间产业生态系统在 2020 年拥有约 3390 亿美元的市场收入。预计该行业将进一步扩张，到 2025 年将达到约 4390 亿美元（Statista, 2020）。地球轨道上卫星的激增是地理空间产业增长的重要催化剂，据卫星跟踪网站“Orbiting Now”报告，截至 2023 年 5 月 4 日，环绕地球运行的活跃卫星数量为 7,702 颗（NanoAvionics, 2023，5 月 4 日）。

这种快速增长归因于多个因素，包括定位传感技术的普及和成本降低、对基于位置的服务和解决方案需求的增长、机器学习和人工智能与空间数据的融合，以及新应用和创新的涌现。

地理空间技术广泛应用于各个领域，用于分析生物物理和环境状况、居住模式、基础设施以及社会经济发展。特别是数字工具和分析改进了监测、评估和报告，使数据收集更加高效且具成本效益。这些工具显著增强了我们高效、低成本开展评估的能力，涵盖单个项目、投资组合评估和生态学重要尺度。这些评估得出的见解揭示了与发展成果相关的、此前隐藏的变化和模式。

本章说明，通过结合评估与地理空间分析的优势，我们可以更好地理解干预措施的影响和有效性，特别是在涉及位置和空间关系的重要背景下。地理空间科学和评估都是多学科领域，要求具备技术熟练度、合作精神和广博的知识。

# 评估中的地理空间分析：总结与未来方向

贯穿本章始终，地理空间分析为评估引入了关键的空间维度。这一维度增强了我们对干预措施如何影响特定地点、区域或社区的理解。此外，地理空间数据作为一种有效的监测工具，能提供关于干预措施进展的实时洞见，并支持进行调整以提高有效性。地理空间分析促进了不同地点或区域之间的比较，揭示了导致干预措施成效差异的因素。这些工具还可用于基于不同干预策略的未来情景预测建模。最后，地理空间分析支持创建可视化成果，增强评估发现的可及性和清晰度。

本章还强调了评估如何反过来通过提供反馈、洞见和证据来促进地理空间科学的未来研究。评估考察干预措施的相关性、绩效和有效性，并凸显了方法论挑战和数据缺口。

评估通过为地理空间数据和工具的利用提供综合方法，在增强地理空间途径方面发挥着重要作用。它们通过将评估中使用的数据与其他来源进行三角互证，确保数据的准确性和可靠性。评估还应用质量控制指南和伦理考量，在处理敏感空间数据时尤为重要。评估考察应用地理空间分析的干预措施的影响和有效性，识别方法论和数据质量方面的改进领域。通过提供决策反馈和创建增强地理空间发现理解的可视化表达，评估确保地理空间途径对利益相关者更加友好易懂。

然而，随着这些地理空间技术因其实用性而被评估者更广泛地接受，其挑战也随之凸显。这些挑战包括能力局限、数据可用性与获取、基础设施与资源约束、伦理考量、透明度和验证等。这些挑战可能构成使用地理空间数据的障碍，特别是在数据稀缺地区资源有限的评估部门。它们可能影响采纳创新技术的意愿。

作为评估者，我们致力于利用先进技术，其动力源于数据源的持续扩展、开源工具的普及以及计算能力的提升。为鼓励这些技术的应用并应对上述挑战，评估者和评估部门必须积极推广这些方法论的认知，聘请精通空间分析的专家，并鼓励与在相关领域拥有专业知识的机构建立更紧密的合作。评估团队、学术界、数据提供方以及研究和政策机构之间建立有效伙伴关系至关重要，以制定指南、行为准则、数据质量标准、透明度标准，以及负责任地采纳新兴方法的伦理和法律框架，从而提升我们工作的质量。

## 注释

1.  **空间思维**是地理空间科学的指导原则。它是一种推理类型，涉及基于空间组织和整合概念，并利用它们解决问题和做决策。理解空间的特征，如维度、连续性、邻近性和分离性，对空间思维至关重要。

2.  <https://www.ghgsat.com/en/what-we-do/>

3.  <https://ieg.worldbankgroup.org/evaluations/managing-urban-spatial-growth>

4.  <https://ieg.worldbankgroup.org/evaluations/mexico-country-program>

5.  **来源：** Roger **Tomlinson** (2019)；*Thinking About GIS: Geographic Information System Planning for Managers*，第五版（ISBN: 9781589483484；及其他 [引用]）。

6.  **训练数据：** 该数据用于机器学习模型，将卫星数据分类为森林和非森林类别。

7.  采用混合方法的**SIDS – 圣卢西亚案例研究**可在此查看：<https://www.youtube.com/watch?v=y_Al2O-PqRo>。

## 参考文献

1.  **Anand, A.**, & Batra, G. (2021). Using Big Data and Geospatial Approaches in Evaluating Environmental Interventions. In J. I. Uitto (Ed.), *Evaluating Environment in International Development* (pp. 79–92). Routledge. <https://www.taylorfrancis.com/chapters/oa-edit/10.4324/9781003094821-7/using-big-data-geospatial-approaches-evaluating-environmental-interventions-anupam-anand-geeta-batra>

2.  **Anand, A.**, & Batra, G. (2022). Application of Geospatial Methods in Evaluating Environmental Interventions and Related Socioeconomic Benefits. In J. I. Uitto & G. Batra (Eds.), *Transformational Change for People and the Planet: Evaluating Environment and Development*. Springer Nature. <https://doi.org/10.1007/978-3-030-78853-7_19>

3.  **Andam, K. S.**, Ferraro, P. J., Pfaff, A., Sanchez-Azofeifa, G. A., & Robalino, J. A. (2008). Measuring the effectiveness of protected area networks in reducing deforestation. *Proceedings of the National Academy of Sciences*, *105*(42), 16089–16094. <https://doi.org/10.1073/pnas.0800437105>

4.  **Awange, J. L.**, & Kyalo Kiema, J. B. (2013). Spatial analysis. *Environmental Geoinformatics*, 225–236. <https://doi.org/10.1007/978-3-642-34085-7_17>

5.  **Azzam, T.** (2013). Mapping data, geographic information systems. *New Directions for Evaluation*, *2013*(140), 69–84. <https://doi.org/10.1002/ev.20074>

6.  **Azzam, T.**, & Robinson, D. (2013). GIS in evaluation. *American Journal of Evaluation*, *34*(2), 207–224. <https://doi.org/10.1177/1098214012461710>

7.  **Bamberger, M.**, Raftree, L., & Olazabal, V. (2016). The role of new information and communication technologies in equity-focused evaluation: Opportunities and challenges. *Evaluation*, *22*(2), 228–244. <https://doi.org/10.1177/1356389016638598>

8.  **Bruce, K.**, Vandelanotte, J., & Gandhi, V. (2025). Emerging Technology and Evaluation in International Development. In S. B. Nielsen, F. Mazzeo Rinaldi & G. J. Petersson (Eds.), *Artificial Intelligence and Evaluation. Emerging Technologies and Their Implications for Evaluation* (pp. 13–36). Routledge. <https://doi.org/10.4324/9781003512493>

9.  Editorial: A place for everything. *Nature*. 2008;453(2), 2. Anonymous. <https://doi.org/10.1038/453002a>

10. 粮农组织评价办公室. (2017). 喀布尔、巴米扬和卡皮萨省灌溉系统改善项目的最终评价. 联合国粮食及农业组织. [`www.fao.org/3/bd685e/bd685e.pdf`](https://www.fao.org/3/bd685e/bd685e.pdf)


² D. Morissey. “4 Principles of Responsible AI in financial services”. Microsoft Industry Blogs. [`cloudblogs.microsoft.com/industry-blog/financial-services/2021/03/29/4-principles-of-responsible-ai-in-financial-services/`](https://cloudblogs.microsoft.com/industry-blog/financial-services/2021/03/29/4-principles-of-responsible-ai-in-financial-services/), retrieved Nov 22, 2021.

³ “Lime: Explaining the predictions of any machine learning disaster”. Github. [`github.com/marcotcr/lime`](https://github.com/marcotcr/lime). Accessed Nov 21, 2021.

⁴ “A game theoretic approach to explain the output of any machine learning model”. Github. [`github.com/slundberg/shap`](https://github.com/slundberg/shap). Accessed Nov 21 2021.

⁵ “From principles to practice: Use cases for implementing responsible artificial intelligence in financial services”. Linklaters. [`www.linklaters.com/en/insights/publications/2019/november/from-principles-to-practice-use-cases-for-implementing-responsible-ai-in-financial-services`](https://www.linklaters.com/en/insights/publications/2019/november/from-principles-to-practice-use-cases-for-implementing-responsible-ai-in-financial-services). Accessed Nov 21, 2021.

## 第 4 章

### 金融行业的 AI 公平性：一种机器学习流水线方法

#### Jun Xu

#### 4.1 引言

人工智能（AI）技术和机器学习（ML）算法在我们的日常生活中激起了极大的热情，从智能电视、手机、无人驾驶汽车到登陆火星的机器人。特别是随着“大数据”的创建、收集和存储，以及大型商业和金融组织中算力和存储能力的高度集中，ML 算法展示了在海量数据集中识别人类可能无法察觉的非直观和隐性相关性的能力。因此，ML 模型已被金融机构（FIs）广泛采用，作为决策过程的一种手段，涵盖高频交易、网络安全，以及各种金融产品和服务。

近年来，如何妥善使用 AI 重新引起了大众的广泛关注。事实上，当 AI 带来大量益处时，如果不仔细考虑 AI 伦理，特别是 AI 公平性，某些利用 AI 的应用可能会对人类社会造成危害。例如，美国司法系统中使用的“替代制裁罪犯管理画像系统”（COMPAS）软件已被证明对非裔美国人存在偏见。医疗系统的一个住院评分模型偏向特定种族群体。

在金融行业，AI 公平性也扮演着重要角色。机器做出的决策可能影响金融产品和服务的大量用户群体，例如信用评分和贷款，且固有的一定程度的偏见客观存在。从金融机构客户收集的某些数据可能容易产生偏见和不平衡，例如，持有世界顶级商务信用卡的男性持卡人多于女性持卡人。此类偏见也可能存在于聊天机器人、在线广告和营销冠军、面部识别等领域。

然而，由于大多数 ML 和深度学习（DL）算法的黑盒本质，算法输出的公平性成为一个严重的担忧，尽管人们期望利用机器的“公平性”从决策过程中消除人类的偏见！因此，已进行了许多研究和实验，旨在将公平性嵌入 AI 建模中。

本章提出了一个解决上述问题的实用框架。它从 AI 伦理和公平性的高层概念前景入手。然后，我们制定了构建 ML 流水线方法的指南。ML 与公平性概念之间的联系与矛盾得到了深入讨论。通过示例演示了如何在 ML 流水线方面考虑公平性。本章的贡献有三方面：(i) 总结了金融机构中 AI 公平性的关键点；(ii) 引入 ML 流水线方法，详细解释了具有结构化表示的公平性处理；(iii) 详述了实质性的工作流图表和检查清单。

#### 4.2 AI 伦理与公平性

许多政府组织已深入讨论 AI 伦理，例如，新加坡金融管理局（MAS）提出了 FEAT 原则（即公平性、伦理、问责制和透明度）及实践，美国国防部采用五项原则（即负责、公平、可追溯、可靠和可治理），欧盟于 2018 年发布了可信 AI 伦理准则，澳大利亚政府也发布了包含八条规则的版本。中国、英国和澳大利亚等其他国家也发布了 AI 伦理准则。在图 4.1 中，我们建议了七个主要特征。

![Figure 4.1. Ethical AI](img/p119.jpg)

![Figure 4.2. Bias types](img/p120.jpg)

关于公平性的定义，已提出多个版本。粗略地说，公平意味着“无偏见和无歧视”，即具有相似属性的人应受到相似对待，否则应受到不同对待。

---

⁶ “Fairness metrics to aid responsible AI adoption in financial services”。新加坡金融管理局。 <https://www.mas.gov.sg/news/media-releases/2020/fairness-metrics-to-aid-responsible-ai-adoption-in-financial-services>。访问日期：2021 年 11 月 21 日。

⁷ “MAS launches global challenge to accelerate innovation in responsible AI solutions”。新加坡金融管理局。 <https://www.mas.gov.sg/news/media-releases/2021/mas-launches-global-challenge-to-accelerate-innovation-in-responsible-ai-solutions>。访问日期：2021 年 11 月 21 日。

⁸ The 17 goals, Department of Economic and Social Affairs, UN. <https://sdgs.un.org/goals>. Accessed Nov 21, 2021.

⁹ K. Crawford et al. AI Now: 2019 Report. The AI Now Institute. <https://ainowinstitute.org/AI_Now_2019_Report.pdf>. Accessed Nov 21, 2021.

¹⁰ “Cloud TPU: Train and run machine learning models faster than ever before”。Google Cloud。 <https://cloud.google.com/tpu>. Accessed Nov 21, 2021.

¹¹ “FPGA vs. GPU for Deep learning”。Intel。 <https://www.intel.com/content/www/us/en/artificial-intelligence/programmable/fpga-gpu.html>. Accessed Nov 21, 2021.

¹² “Your AI pair programmer”。Github。 <https://copilot.github.com/>. Accessed Nov 21, 2021.

¹³ P. Prasad, P. Byrne, and J. Chessman. “Market Guide for AIOps Platforms”。Gartner Research。 <https://www.gartner.com/en/documents/4000217/market-guide-for-aiops-platforms>. Accessed Nov 21, 2021.

¹⁴ P. Vincent, K. Iijima, M. Driver, J. Wong, and Y. Natis. “Gartner Magic Quadrant for Enterprise Low-Code Application Platforms”。Gartner。 <https://www.gartner.com/en/documents/3956079/magic-quadrant-for-enterprise-low-code-application-platf>. Accessed Nov 21, 2021; K. Costello and M. Rimol. “Gartner forecasts worldwide low-code development technologies market to grow 23% in 2021”。Gartner。 <https://www.gartner.com/en/newsroom/press-releases/2021-02-15-gartner-forecasts-worldwide-low-code-development-technologies-market-to-grow-23-percent-in-2021>. Accessed Nov 21, 2021.

¹⁵ “FinBert: Financial Bert (in Chinese)”。 <https://github.com/valuesimplex/FinBERT>. Accessed Nov 21, 2021.

¹⁶ “2021 Global Identity and Fraud Report: Protecting and enabling customer engagements in the new digital era”。Experian。 <https://www.experian.com.sg/wpcontent/uploads/2021/04/Experian-Global-Identity-Fraud-Report-2021.pdf>. Accessed Nov 21, 2021.

© 2022 World Scientific Publishing Company

<https://doi.org/10.1142/9789811250903_0004>

有些偏见是固有且不可避免的，但大多数并非如此；相反，它们只是被简单地误用或被操纵了。图 4.2 从总体上展示了三种常见的偏见类型，如果我们保持谨慎，就能避免大多数认知偏见和情境偏见。

公平性实际上与准确性、隐私、可解释性和安全性等其他因素密切相关（图 4.3）。公平性通常与可解释性同向，但在某些场景下可能与其他因素不同向；因此，我们可能需要在设计阶段进行权衡。例如，AI 系统通常难以同时实现高度的隐私和准确性。同样，更多的隐私信息可以使公平待遇更具可调性。请注意，我们需要考虑应用场景，因为有时准确性更为重要，且存在隐私和公平性的合理依据。然而，有时必须以牺牲准确性为代价来满足公平性指标。因此，风险缓解技术对于在不同指标之间实现正确的平衡是必要的。

在 AI 和数据驱动建模中，我们通常使用“受保护”变量来表示可能导致公平性问题的因素，例如性别、年龄、种族、国籍、残疾状况、性取向、宗教、文化、神学、传统、社会阶层、资源可得性和族裔。相对的是“非受保护”变量，指市场上可获得的公开信息。

![](img/p121.jpg)

**图 4.3.** 公平性与其他因素的关系

受保护变量通常涉及个人隐私，其使用方式因金融产品类型而异。例如，申请信用卡可能需要个人收入，但开设一般银行账户则不需要。这些受保护变量可进一步细分为特权和非特权类别。例如，残疾人和少数族裔通常被视为非特权类别。

AI 伦理不应被视为对金融机构为股东增加利润能力的约束。事实上，AI 伦理原则可作为创新发展的关键设计标准之一，旨在改善福祉、减少不平等和偏见，并帮助人们实现目标。例如，因种族原因被错误预测为高风险而拒绝放贷，既是声誉风险，也是错失良机。通过消除此类偏见，金融机构可能吸引更多高净值客户。

因此，金融机构应建立其 AI 伦理框架。正如新加坡个人数据保护委员会（PDPC）所指出的^6，该模型框架旨在广泛适用——它应与算法、技术、行业、规模和商业模式无关。AI 中公平待遇的设计应遵循类似规则。由于 ML 流水线可应用于大多数设计和开发流程，我们选择将其作为主干来讨论 AI 公平性。在接下来的两节中，我们将首先讨论通用 ML 流水线，然后介绍公平性流水线的更多细节。

#### 4.3 ML 流水线

流水线是许多行业广泛接受的概念和方法论。产品流水线是一系列组件，用于减少已完成任务之间的延迟。它具有一定程度的自动化，并提高了产品生命周期各阶段的吞吐量。流水线通常包含批处理，即收集数据、通过网络发送数据并对其进行处理，以提供预计算的结果和指导，供下一阶段使用。

ML 流水线用于创建正式且自动化的 ML 工作流。它构建了数据和模型生命周期中必要的组件和步骤。例如，数据流水线使一系列数据能够在发送至模型进行训练、测试和评估之前，被提取、转换、过滤和清洗。模型流水线还包含模型部署和维护。ML 生命周期通常包含五个阶段：项目设计、数据处理、模型开发、模型/系统部署和模型维护，如图 4.4 所示。

通用的 ML 生命周期流水线如图 4.5 所示。ML 生命周期中 ML 流水线的抽象概念称为 MLOps，将在第 14 章中进一步讨论。

对于一个完整的新项目，其问题陈述、范围和目标必须首先由业务利益相关者和 SME（领域专家）明确定义。开发团队研究其可行性并提供潜在解决方案。项目启动前应估算资源和成本。项目正式启动后，需申请批准以访问各种 ML 相关资源（如数据、工作台、ML 平台和云）。然后，原始数据将从数据库或其他数据源摄入，在阶段 1 进行预处理和分析，随后送入阶段 2 的 ML 开发环境。

![](img/p123.jpg)

**图 4.4.** 五阶段 ML 生命周期

![](img/p124.jpg)

**图 4.5.** ML 流水线

ML 开发通常是一个迭代过程，旨在通过阶段 2 的适当评估指标来增强特征并改进模型。处理后的数据和特征可存储在 `Feature Store` 中。相关代码、配置和文档将存储在 `Git`（一种文件版本控制和管理系统，如 `Bitbucket` 或 `Github`）中，模型将注册在 `Model Inventory`（模型清单，或 `Model Registry` 模型注册表）中，并可在 `Central Repository` 中访问。ML 开发人员可从 `Central Repository`（如 `Artifactory`，一种通用制品仓库管理器）获取所需工具和仓库，并获得容器镜像的访问权限（如打包好的 ML 模型和环境）。一旦所有必要的制品准备就绪，模型（可能集成到系统中）将部署在不同环境中（如用户验收测试 (UAT) 和预发布环境，用于测试和验证）。不满意的 ML 指标结果可能导致 ML 模型重新训练（即从阶段 3 返回阶段 2）。

如果所有测试均通过，且模型/系统由授权人员签署批准，则可将模型和系统推广至正式生产环境。`Feature Store` 可向 ML 模型输入实时数据，用于实时或批量推理。必须实施适当的监控和诊断配置，以应对潜在的 ML 问题（如模型性能下降、数据漂移等），这可能会触发带有适当流程治理的重新训练事件。

请注意，并非每个项目都必须包含此处所示的所有五个阶段或所有组件。有时，即使流水线中的执行顺序也可能不同。合理的流水线设计应取决于实际项目需求，而非固定结构。更多细节将在第 14 章中讨论。

#### 4.4 公平性流水线

遵循 ML 流水线，我们可以创建类似的公平性流水线。图 4.6 强调了每个阶段需要提出的几个问题，表 4.1 强调了每个阶段的关键考量。

消除偏见的前提是在产品和服务设计阶段对公平性进行恰当的定义和度量。为简单起见，我们可将其分为三个阶段：建模前、建模中和建模后，如表 4.2 所示，每个阶段的重点分别为数据、模型和维护。

To quantitatively assess the degree of fairness, many metrics for data and models have been created. Data bias is usually assessed from its statistical properties (such as mean, maximum, minimum, distribution functions, etc.), while model bias requires more elegant algorithms to identify. Figure 4.7 lists some commonly used metrics for (discrete) classification problems, including binary classification problems such as fraud/non-fraud, approve/non-approve, etc. For multi-class problems, we can apply similar ML training techniques (such as one-vs-rest or one-vs-one) to these metrics.

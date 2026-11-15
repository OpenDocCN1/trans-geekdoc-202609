

### 2.5.1 情景描述

Firm X maintains and manages the pavements and the highways. Recently, it got a contract to manage a part of one of the fastest highways in the country, stretching just over 60 miles. Although the project is very charismatic, it has very strict and hefty fines for non-compliance with the following rules:

X 公司负责维护和管理路面和高速公路。近期，它承包了管理该国最快高速公路的一段（长度略超 60 英里）的合同。尽管该项目颇具吸引力，但对未能遵守以下规则的行为规定了非常严格且高额的罚款：

- 1. 路面上的裂缝和坑洞
- 2. 交通标志和道路标线保持良好状态
- 3. 路边树木和绿地的维护

Bob, a manager on this project, has been quite nervous lately, and is looking to create a DT to manage and maintain the health condition of the road surface and the surrounding areas.

Bob 是该项目的一名经理，最近非常紧张，希望创建一个 DT 来管理并维护路面及周边区域的健康状况。

He consults his various colleagues for ideas. Mike, the operator of the roadway, suggests that DT should be able to acquire the data for the current road conditions, and thus act as a real-time virtual replica of the roadway. On the other hand, Jay, a colleague of Bob, suggests that DT should be also able to comprehend the acquired data, and act as a decision support system by making predictions about the future road conditions. Tom, a friend of Bob, jumps in by suggesting that DT in addition to making the predictions should be able to adapt itself in uncertain situations like the COVID-19 pandemic.

他向多位同事请教想法。Mike 是道路运营商，建议 DT 应能获取当前道路状况的数据，从而充当道路的实时虚拟副本。另一方面，Bob 的同事 Jay 建议 DT 还应能理解所获取的数据，并通过对未来道路状况进行预测，充当决策支持系统。Bob 的朋友 Tom 则插话建议，DT 除了进行预测外，还应能在 COVID-19 大流行等不确定情况下自适应调整。

The issue that Bob faces is this: Given the different perspectives that people have about DTs, how does he conduct a structured brainstorming to make sense of what DTs mean for their use case? Because if different stakeholders have widely varying interpretations of DT, it may result in false hopes and misalignments between stakeholders, with little consensus about the deliverables to expect and resources to allocate.

Bob 面临的问题是：鉴于人们对 DT 有不同看法，他该如何开展结构化头脑风暴，以明确 DT 在其用例中的含义？因为如果不同利益相关方对 DT 的理解差异巨大，可能会导致虚假期望和利益相关方之间的目标不一致，对预期交付成果和资源分配缺乏共识。

### 2.5.2 框架的应用

### 2.5.2.1 确定“数字化”意味着什么

Practitioners used a two-step process: (1) brainstorming in a structured way using the framework to develop many ideas for different types and extents of digitalization, and (2) selecting the appropriate one based on the value to be gained and the technology available.

从业者采用两步流程：（1）使用框架以结构化方式开展头脑风暴，为不同类型和程度的数字化提出许多想法；（2）根据可获得的价值和可用技术选择合适的方案。

- 1. Description – Helps to better understand what is happening on the road/pavement.
  - a. No digitalization: Operators go for patrolling and try to manually detect cracks.
  - b. Low extent of digitalization: One operator drives a car with a camera mounted on it, and then another operator (sitting in office) looks through the video to detect cracks/potholes.
  - c. High extent of digitalization: Drones automatically take pictures of the road, and computer vision algorithm detects the cracks (no operator required).

- 1. 描述 – 有助于更好地了解道路/路面上发生的情况。
  - a. 无数字化：巡检人员进行巡查，尝试手动检测裂缝。
  - b. 低度数字化：一名驾驶安装有摄像头的车辆的操作员，随后由另一名（在办公室里）操作员查看视频以检测裂缝/坑洞。
  - c. 高度数字化：无人机自动拍摄道路照片，计算机视觉算法检测裂缝（无需操作员）。

No digitalization method is very inefficient because cracks are hard to detect at 70 mph. Introducing some digitalization may solve this problem, but most of the work still must be done by humans. In the highest level of digitalization, operators are less needed, and they just need to supervise the system.

无数字化方法效率非常低，因为以 70 英里/小时的速度很难发现裂缝。引入一定程度的数字化可能解决此问题，但大部分工作仍需人工完成。在最高程度的数字化中，操作员需求较少，只需监督系统即可。

- 2. Diagnostic – Helps to understand why something might be happening.
  - a. No digitalization: Practitioners take an experienced guess.
  - b. Low/High extent of digitalization: DT can help to understand the reasons behind the cracks by analysing weather patterns and daily traffic conditions.

- 2. 诊断 – 有助于理解某事发生的原因。
  - a. 无数字化：从业者依据经验做出猜测。
  - b. 低度/高度数字化：DT 可以通过分析天气模式和日常交通状况，帮助理解裂缝背后的原因。

- 3. Prediction – Helps to understand what might happen in the future.
  - c. No digitalization: Practitioners use an empirical approach to come up with a prediction for crack propagation.
  - d. Low extent of digitalization: The DT can predict the crack propagation in normal pre-determined circumstances like with usual traffic and weather conditions.
  - e. High extent of digitalization: The DT’s prediction can adapt itself based on the changing environment, e.g., traffic reduced due to COVID-19 pandemic or extreme weather circumstances.

- 3. 预测 – 有助于了解未来可能发生的情况。
  - c. 无数字化：从业者采用经验方法来预测裂缝扩展。
  - d. 低度数字化：DT 可以在正常预设条件下预测裂缝扩展，例如常规交通和天气状况。
  - e. 高度数字化：DT 的预测可以根据环境变化自行适应，例如因 COVID-19 大流行导致交通减少，或极端天气情况。

A lack of digitalization forces practitioners to use existing empirical approaches to predict the crack propagation. The introduction of some digitalization helps to solve this problem by making DTs take care of normal circumstances and humans taking care of anomalies and unusual situations. In the highest extent of digitalization, the DT can learn from itself based on the data gathered without the practitioner having to adjust the algorithm and therefore take care of unusual situations as well.

缺乏数字化迫使从业者使用现有经验方法来预测裂缝扩展。引入一定程度的数字化有助于解决此问题，让 DT 处理常规情况，由人类处理异常和不寻常情况。在最高程度的数字化中，DT 可以根据收集的数据自行学习，无需从业者调整算法，因此也能处理不寻常情况。

- 4. Prescription – Helps to decide what should be done in the future.
  - a. No digitalization: Operators decide based on experience whether to repair the crack.
  - b. Low extent of digitalization: DT can handle easy or trivial cases, like a dangerous pothole or a big crack but not the cases which require an intelligent evaluation.
  - c. High extent of digitalization: To decide whether to perform preventive maintenance or not, the algorithm can intelligently evaluate what the additional cost would be if the cracks were not repaired now.

- 4. 处置 – 有助于决定未来应采取什么行动。
  - a. 无数字化：操作员根据经验决定是否修复裂缝。
  - b. 低度数字化：DT 可以处理简单或琐碎的案例，例如危险的坑洞或大裂缝，但不能处理需要智能评估的案例。
  - c. 高度数字化：为了决定是否进行预防性维护，算法可以智能评估如果现在不修复裂缝，额外成本会是多少。

The above brainstorming sheet illustrates how practitioners have used the digital perspective of the framework to conduct a structured brainstorming session. Each of the above ideas (or even all of them) could have been implemented in this DT. In the absence of this structured and exhaustive brainstorming, many different definitions of what digital means may have arisen, leading to the confusion. Based on their technological resources and careful evaluation of alternatives/value, the team decided that they would like to have a high extent of digitalization in description, i.e., use drones to automatically take pictures of the road, and computer vision algorithm to detect the road defects. So, this is what digital would mean in the context of this case study.

上述头脑风暴表说明了从业者如何使用框架的数字视角开展结构化头脑风暴会议。上述每个想法（甚至全部）都可以在该 DT 中实现。如果没有这种结构化且详尽的头脑风暴，可能会产生许多关于“数字化”含义的不同定义，从而导致混乱。基于其技术资源和对替代方案/价值的仔细评估，团队决定在描述环节采用高度数字化，即使用无人机自动拍摄道路照片，并使用计算机视觉算法检测道路缺陷。因此，这正是在本案例研究背景下“数字化”的含义。

### 2.5.2.2 确定待孪生对象

To answer the question what we are twinning, practitioners needed to decide on two things: System boundaries and the entities to be twinned.

为了回答“我们要孪生什么”这个问题，从业者需要决定两件事：系统边界和待孪生实体。

The project team started by selecting the scope of the project (system boundaries). It was decided to focus on defects caused by damaged road markings despite there being many defects to choose from, such as defects in traffic markings, vegetation situation around the road, potholes, and guard rails. This was selected based on two criteria: (1) importance to the life safety of users and (2) frequency of occurrence as determined by analysing the defects log from 21 quarters, starting from 2013. It was thus concluded that damaged road markings are one of the most frequently reported defects in roads and pose the maximum risk to life safety of users. Clearly defining the scope of the project at the very onset gave clear and actionable directions to the project team, thus alleviating any existing confusion and aligning the expectations of all the stakeholders.

项目团队首先选择了项目范围（系统边界）。团队决定专注于因道路标线损坏导致的缺陷，尽管可供选择的缺陷很多，例如交通标线缺陷、道路周边植被情况、坑洞和护栏。这一选择基于两个标准：（1）对用户生命安全的重要性；（2）根据自 2013 年起 21 个季度的缺陷日志分析确定的发生频率。因此得出结论：损坏的道路标线是道路上报告最频繁的缺陷之一，并对用户生命安全构成最大风险。在项目伊始就明确界定范围，为项目团队提供了明确且可操作的方向，从而缓解了任何现有的混乱，并使所有利益相关方的期望保持一致。

Next, it was decided that for this project, twinning only the road/pavement (or the product) would be necessary and sufficient. It would, however, be necessary to twin the process of defect repair and the organization performing it in the future when the team is predicting the cost and time to repair the defects and prescribing a solution using DT (since different processes and organizations would have impact on time and cost).

接下来，团队决定，对于本项目，仅孪生道路/路面（或产品）即为必要且充分。然而，在未来团队使用 DT 预测缺陷修复成本和时间并制定处置方案时，有必要同时孪生缺陷修复过程及执行该过程的组织（因为不同的流程和组织会影响成本和时间）。

### 2.6 结论

In our motivation, we gave an example of a conversation with a friend where the main question that arose was: “What is an ideal DT? or How do we define a DT that industry needs?” We do not believe that there is one universal answer for this question. Each organization is unique in its market position and technological capabilities. Hence, DT to be deployed in practice must be evaluated individually for each organization and project – a “one-size-fits-all” approach would not work.

在我们的动机部分，举了一个与朋友交谈的例子，其中提出的主要问题是：“理想的 DT 是什么？或者我们如何定义行业所需的 DT？”我们不认为这个问题有一个通用答案。每个组织在市场地位和技术能力方面都是独特的。因此，实际部署的 DT 必须针对每个组织和每个项目单独评估——“一刀切”的方法行不通。

The second author of the chapter, who has guided over 2000 DT implementations since 2008 quotes: “In my experience, I rarely see people fully evaluating a DT to decide if it is suitable for their use case. It is always the first thought option of DT that practitioners want to implement without really thinking of other better possibilities”. Fjeld (2020) interviews 15 practitioners and reports a similar finding. Practitioners getting lured by technology and not exhaustively evaluating other viable options is a well-documented problem in broader technology evaluation and selection literature as well (Love, Matthews, and Zhou 2020). A lack of this understanding can result in confusion about DTs among practitioners, unrealistic hopes from the technology, and ultimately a rejection of DT as hype.

本章第二位作者自 2008 年以来指导了超过 2000 个 DT 实施项目，他引述道：“就我的经验而言，我很少看到有人会全面评估 DT 以判断其是否适合自己的用例。从业者总是想要实施首先想到的 DT 方案，而没有真正考虑其他更好的可能性。”Fjeld (2020) 采访了 15 名从业者，报告了类似发现。从业者被技术所诱惑，而没有穷尽评估其他可行选项，这一问题在更广泛的技术评估与选择文献中也有详细记载（Love, Matthews, and Zhou 2020）。缺乏这种理解可能导致从业者对 DT 产生混乱、对技术抱有不切实际的期望，并最终将 DT 视为炒作而加以摒弃。

The proposed framework helps alleviate the above problem by proposing two fundamental questions that every practitioner should ask before implementing DTs: (1) What is digital? and (2) What are we twinning? By answering these questions for each DT application, practitioners can alleviate confusion and ensure a clear understanding of the specific use case and context. Awareness of these factors in practice can increase the likelihood of success and accelerate the adoption of DT in the industry.

所提框架通过提出每位从业者在实施 DT 前都应问自己的两个基本问题来帮助缓解上述问题：（1）什么是数字化？（2）我们要孪生什么？通过为每个 DT 应用回答这两个问题，从业者可以消除混乱，确保对具体用例和背景有清晰的理解。在实践中意识到这些因素，可以提高成功的可能性，并加速 DT 在行业中的采用。

## References

- Agrawal, Ashwin, Martin Fischer, and Vishal Singh. 2022. “Digital Twin: From Concept to Practice.” Journal of Management in Engineering 38 (3): 06022001. https://doi.org/10.1061/(ASCE)ME.1943-5479.0001034.
- Agrawal, Ashwin, Vishal Singh, and Martin Fischer. 2022. “A New Perspective on Digital Twins: Imparting Intelligence and Agency to Entities.” arXiv. https://doi.org/10.48550/arXiv.2210.05350.
- Agrawal, Ashwin, Vishal Singh, Robert Thiel, Michael Pillsbury, Harrison Knoll, Jay Puckett, and Martin Fischer. 2022. “Digital Twin in Practice: Emergent Insights from an Ethnographic-Action Research Study.” In Construction Research Congress 2022, 1253–60. Arlington, VA: ASCE. https://doi.org/10.1061/9780784483961.131.
- Autodesk. 2021. “Digital Twins in Construction, Engineering, & Architecture.” Autodesk. 2021. https://www.autodesk.com/solutions/digital-twin/architecture-engineering-construction.
- Boje, Calin, Annie Guerriero, Sylvain Kubicki, and Yacine Rezgui. 2020. “Towards a Semantic Construction Digital Twin: Directions for Future Research.” Automation in Construction 114 (June): 103179. https://doi.org/10.1016/j.autcon.2020.103179.
- buildingSMART International. 2021. “Digital Twins.” BuildingSMART International (blog). 2021. https://www.buildingsmart.org/digital-twins/.

## 参考文献

- Agrawal, Ashwin, Martin Fischer, and Vishal Singh. 2022. “数字孪生：从概念到实践。” Journal of Management in Engineering 38 (3): 06022001. https://doi.org/10.1061/(ASCE)ME.1943-5479.0001034.
- Agrawal, Ashwin, Vishal Singh, and Martin Fischer. 2022. “数字孪生的新视角：赋予实体智能与自主性。” arXiv. https://doi.org/10.48550/arXiv.2210.05350.
- Agrawal, Ashwin, Vishal Singh, Robert Thiel, Michael Pillsbury, Harrison Knoll, Jay Puckett, and Martin Fischer. 2022. “实践中的数字孪生：来自民族志-行动研究的新见解。” In Construction Research Congress 2022, 1253–60. Arlington, VA: ASCE. https://doi.org/10.1061/9780784483961.131.
- Autodesk. 2021. “建筑、工程与施工中的数字孪生。” Autodesk. 2021. https://www.autodesk.com/solutions/digital-twin/architecture-engineering-construction.
- Boje, Calin, Annie Guerriero, Sylvain Kubicki, and Yacine Rezgui. 2020. “迈向语义化建筑数字孪生：未来研究方向。” Automation in Construction 114 (June): 103179. https://doi.org/10.1016/j.autcon.2020.103179.
- buildingSMART International. 2021. “数字孪生。” BuildingSMART International (博客). 2021. https://www.buildingsmart.org/digital-twins/.


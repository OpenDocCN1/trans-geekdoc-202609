
除了集体同意之外，社区行动的另一个目标是成为机器学习系统设计的参与者——作为利益相关者和参与者，其专业知识和生活经验塑造系统的概念与实现，而非仅作为数据提供者或决策主体。这样做的好处包括更易预见并缓解代表性伤害（如计算机视觉数据集中的贬低类别，或图像搜索结果中呈现的攻击性刻板印象）。但参与式设计也有潜在风险：它可能给边缘群体带来额外负担，也可能成为组织回避实质性变革的幌子。因此，必须将参与视为劳动并予以公平补偿 \[429\]。

## Regulation

促进公平机器学习的监管可以采取现有法律对包含机器学习的决策系统进行适用，或专门针对技术使用及其危害的法律。上文提到的对人脸识别的禁令以及欧盟《通用数据保护条例》（GDPR）下对自动化决策的限制，就是后者的例子。这两种监管方式均在机器学习在决策系统中快速普及的背景下不断演进。监管是实现公平机器学习结构性干预的重大机遇。然而，由于法律倾向于将歧视概念窄化，其在遏制有害机器学习方面的实际效果仍有待观察 \[430\]。

机器学习采用速度与法律演进速度之间的差距，催生了自我监管的尝试：一项 2019 研究发现全球已有八十四条 AI 伦理准则 \[431\]。这些文件虽无法律约束力，却试图塑造组织或个人实践者的规范。虽然自我监管在医疗等领域有效，但人们对 AI 自我监管能否解决本章指出的棘手问题存疑。事实上，工业界的自我监管往往旨在推迟真正的监管以及其可能带来的结构性转变。

## Workforce Interventions

机器学习将权力转移至机器学习专家，使得机器学习劳动力成为重要的干预点。一类努力旨在让更多人获益于行业中宝贵的工作机会，并弥补劳动力内部的权力不平衡——尤其是技术专家与其他角色（如标注人员）之间的差距 \[432\] \[433\]。另一类努力则追求使机器学习的使用与劳动力的伦理价值相协调。技术公司中 nascent（ nascent）的工会化运动似乎兼具这两个目标。

虽然更多样化的劳动力在自身上是道德上有价值的，但值得探讨的是它对产品公平性的影响。一项关于程序员的实验研究发现，程序员的性别或种族并未影响其产出是否带有偏见 \[434\]。但这只是实验室研究，不能视作结构性干预效果的指南。例如，劳动力多样性可能通过以下途径影响产品（该研究设计未捕捉）：多元视角的团队更有可能质疑产品是否应被构建或部署。

其他劳动力干预措施包括教育与培训。计算机科学学生的伦理教育正在上升，2018 年的综述已列出超过 200 门此类课程 \[435\]。长期存在的争论是独立课程与 [cwstuserscwsc1wc[wantcwz] =c[wz] of the players / players / players / players / players / players / players / players / players / players / players / players / players / players / players / players / players / players / players / players / players / players / players / players / players /wz] 之间的优劣。

在许多专业领域，包括一些工程领域，伦理责任部分通过对从业人员的许可来强制执行。像医生和律师等专业人士必须掌握一套专业知识，包括伦理准则，并被法律要求在取得执业许可前通过标准化考试，若他们犯下伦理违规行为，许可证可能会被撤销。这并非软件工程的情况。无论如何，目前存在的软件工程认证标准 \[437\] 与本书涉及的主题几乎没有重叠。

## 研究社区

机器学习研究社区是另一个重要的改革与转型场所。推动变革的最大力量是持续努力将公平、伦理和正义等研究主题视为合法且重要的议题。传统上，一些机器学习主题（如优化算法）被视为“核心”或“真正的”机器学习，而其他主题——甚至数据集构建——则被视为边缘且在智力上不那么严肃。Abeba Birhane、Pratyusha Kalluri、Dallas Card 等人对 ICML 和 NeurIPS 等顶级机器学习会议的论文进行文本分析，发现大多数论文通过强调性能和泛化来为自己辩护，仅有 1% 的论文提及潜在的负面影响 \[438\]。

一些其他关键争论：所有机器学习研究者是否应被要求反思其研究的伦理？是否过于关注修正偏见，而忽视了更深层次的权力与正义问题 \[440\]？如何才能将受机器学习系统影响的人和社区的视角置于中心？在存在利益冲突的情况下，工业界在公平机器学习方面的角色是什么？

## 组织干预以实现更公平的决策

我们上面讨论的结构性干预需要社会运动或其他集体行动，并且其演进时间跨度为数年甚至数十年。这并不意味着组织应当束手无策，等待结构性转变。大多数决策者都有大量可选的干预措施。本节概述了最重要的干预措施。

表 8.2A 概览主要类型的组织干预

| 类型 | 干预措施 | 示例 |
| --- | --- | --- |
| 修改输出 | 再分配 | 组别特定的决策阈值 |
| 修改决策过程 | 打击人际歧视 | 隐性偏见培训 |
|  | 正式化 | 采用统计决策制定 |
|  | 程序保护 | 解释与救济 |
| 决策前 | 外展 | 发送关于奖学金的邮件 |
|  | 干预因果因素 | 工作培训、预防性健康 |
| 决策后 | 修改环境 | 帮助被告出庭 |

随着阅读，你会发现大多数干预措施旨在改善所有决策主体的结果，而不是将公平视为不可回避的权衡。之所以可能，是因为许多干预措施并非在决策瞬间进行。此外，评估干预效果——无论是公平度还是其他指标——通常需要因果推断。最后，只有极小一部分潜在的公平干预措施可以在机器学习框架内实现；其余干预措施侧重于组织或人类实践，而非决策过程中的技术子系统。

### 重新分配或再分配

重新分配和再分配是指对决策过程进行干预，以显式偏好某一或多个群体（通常是被视为处于劣势的群体）。当我们谈论公平干预时，这通常是最直观的类型. 当应用于招聘或大学录取等拥有相对固定名额的选择问题时，算法公平性干预大多退化为不同形式的再分配。这包括在优化步骤中加入公平约束，或在后处理阶段对弱势群体的得分进行调整。无论目标是人口平等或其他统计指标，这种做法都适用。

再分配之所以吸引人，是因为它不需要先理解导致差异的根本因果关系。与此同时，再分配是一种粗糙的干预措施。它设计用来惠及某一群体，并且通过量化该群体的收益提供透明度的优势，但大多数再分配程序并未在群体内部考虑成员的“应得性”。再分配通常通过对弱势群体的 uniform preference（均匀偏好）来实现，或者通过调整优化目标来纳入群体偏好。在此方法中，再分配的内部分配由模型负责，这可能导致非直观且 unintended 的分配（例如，交叉族裔子群可能在无干预条件下更受劣势）。在最佳情况下，再分配方法会确保群体内部的相对排名保持不变。

尽管再分配粗糙，另一种更糟糕的干预措施是完全忽略与群体身份相关的特征。为了明确，如果该特征在统计、因果或道德上无关，则忽略它可能是合理的（第 2 章）。但如果该特征实际上与结果相关呢？例如，假设贡献开源软件项目的人往往是更好的软件工程师。这种影响通过 morally relevant（ morally 相关）的因果路径产生，因为程序员通过参与开源获得实用的软件工程技能。遗憾的是，许多开源社区对女性和少数族裔充满敌意和歧视（这可能是因为缺乏像企业那样的正式组织结构来一定程度控制人际歧视）。认识到这一点，软件公司可以在招聘决策中显式考虑这一点，或者简单地忽略开源贡献作为评估标准。如果后者，则平均招聘的候选人资质会更低；同时也会使那些在歧视中仍坚持提升技能的群体—— arguably 最值得尊重的群体——受到不利影响。

基于统计考量而无需 moral 或 causal 正当性的特征忽略，在实践中极为流行，因为它实现简单、政治上可接受，并且规避了因歧视性对待而产生的法律风险。

### 打击人际歧视

与直接干预输出不同，组织可以尝试改进决策过程。在许多情况下，歧视者在调查和面试中往往坦诚地表达其偏见 \[318\]。他们是否可以通过培训来消除隐性或显性偏见？这就是所谓的偏见消除，常被称为“多元化培训”。

It is appealing to focus on comparative notions of fairness because they are easy to quantify, but we shouldn’t forget the deeper questions. A domain where this seems to have happened is algorithmic hiring. Tools used in algorithmic hiring utilize situational judgment tests, personality tests, and sometimes much more dubious techniques—increasingly involving machine learning—for screening and selecting candidates. Firms adopt such tools to cut recruitment costs, especially for low-wage positions, where the cost of hiring a worker through the traditional process can be seen as significant in relation to a worker’s contribution to the firm’s revenue over the course of the period of their employment.

These tools are problematic for many reasons. While they aim to formalize the hiring process, they often use attributes that are morally and causally irrelevant to job performance. HireVue, for example, previously relied on facial expressions and intonations in a person’s voice as part of its automated assessment. They also fail to take a broad view of discrimination. Focusing narrowly on minimizing disparities in hiring rates across groups leaves unaddressed what kind of environment employees will encounter once hired. If job applicants from certain groups were previously predicted to perform poorly in a certain workplace, the employer should strive to understand the reasons for this difference in success, rather than simply try to find members of these groups that might be able to succeed under such unfavorable, unwelcoming, or hostile conditions. Parity-promoting interventions change the selection process, but preserve the organizational status quo, endorsing the idea that the candidates who have been selected should be able to deal with these conditions sufficiently well to be as productive as their peers who don’t face similar challenges. Other productive—and potentially less harmful—forms of intervention include on-the-job training (which might be understood as a way of intervening on causal factors), meaningful feedback for rejected applicants (which would provide some degree of procedural protection, but also help guide applicants’ future investment in their own development), and a strategic approach to sourcing candidates who firms with more accurate tools might now be better able to assess.

The narrow focus on disparities can mean that there is little consideration of the quality of decisions made by the tools. Tools that simply lack validity raise a host of normative concerns. Notably, assessments that achieve approximate demographic parity but continue to suffer from accuracy disparity (also called differential validity) can set up members of certain groups for failure by expecting them to be able to perform better than they would be currently prepared to.

To reiterate, we do not advocate for treating statistical fairness criteria as constraints, at least in the first instance. That approach assumes that reallocation is the only available intervention. Instead, if we treat statistical fairness criteria as diagnostics, we are likely to uncover deeper problems that require remedying. Unfortunately, these deeper remedies are also harder. They require both causal inference and normative depth. That is of course why they are often ignored, and foundational questions remain unaddressed.

A case in point: a 2021 paper by Megan Stevenson and Sandra Mayson analyzes the fairness of pretrial detention in a noncomparative sense \[459\]. How risky does a defendant have to be that the expected benefit to public safety justifies the harm to the defendant from detention? Using the clever approach of asking survey recipients to choose between being detained and becoming victims of certain crimes, the authors conclude that pretrial detention is essentially never justified.

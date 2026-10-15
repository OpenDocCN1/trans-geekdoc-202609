
最终，预测性、生成性和代理性人工智能之间的区别并非仅是学术讨论的议题——它是实际操作层面的关键。每一类都定义了与数字和物理世界交互的不同模式，必须各自独立理解。随着边界模糊和可组合性增强，安全性必须从孤立的防护措施成熟为整体性、系统感知的弹性。人工智能安全的未来不仅取决于防止输入异常，还取决于对智能行为本身进行建模、约束和监督。[Table 1.3](#c01.xhtml#c01-tbl-0003) 列出了塑造操作环境中对抗性机器学习领域发展与紧迫性的关键里程碑事件。

Table 1.3 常见对抗性技术及其影响。

| Year | | Milestone | Model Type Affected | Adversarial Focus | Impact |
| --- | --- | --- | --- | --- | --- |
| 2004 | | Spam Filter Evasion | Predictive | Evasion via Token Manipulation | Revealed Fragility of Statistical Classifiers |
| --- | --- | --- | --- | --- | --- |
| 2013 | | Adversarial Example Discovery | Predictive | Input Perturbation for Misclassification | Exposed Model Decision Boundary Weaknesses |
| 2015 | | Poisoning Clean-Label Attacks | Predictive | Training-Time Data Corruption | Introduced Stealth Data-Level Compromise |
| 2017 | | Membership Inference Attacks | Predictive | Privacy Leakage from Model Outputs | Demonstrated Training Data Exposure Risks |
| 2019 | | Prompt Injection Emergence | Generative | Input Control to Subvert Output | Highlighted LLM Output Manipulation Threats |
| 2021 | | Jailbreaking via Instructional Prompts | Generative | Bypassing Alignment Constraints | Exposed LLM Filter Limitations in Commercial Products |
| 2023 | | Agentic Tool Misuse Incidents | Agentic | Unsafe Autonomous Tool Execution | Showed Physical-World Impact of AI Misbehavior |

## 对抗性脆弱性的里程碑

对抗性脆弱性在机器学习中并非始于大语言模型或图像分类器——它最早出现在统计模型在网络安全中实际应用的早期。早期的垃圾邮件过滤器和恶意软件分类器基于线性模型或决策树，展示了对手如何轻松超越检测机制。攻击者在垃圾邮件中插入看似无害的关键词以降低垃圾概率评分，或微调二进制签名以规避静态检测。这些手段奠定了一个关键的安全洞察：机器学习系统不同于传统基于规则的引擎，可通过理解其学习行为的轮廓被操纵。在“对抗性机器学习”这一术语广泛使用之前，这些对抗手段的种子已然萌发。

2013 年对抗性示例的正式认可是深度学习安全轨迹的关键转折点。研究人员展示，对输入图像进行微小（往往难以感知）扰动，就能导致训练有素的神经网络以高置信度误判。这项发现的深远意义在于其普遍性——跨数据集、模型架构和任务，对抗性示例表现为一种普遍现象，是神经网络高维几何的涌现属性。此类攻击无需访问模型内部结构，表明鲁棒性并非单纯的工程疏忽，而是深度模型设计中的根本挑战。下面的时间轴列出了塑造现代人工智能系统安全态势的关键对抗性突破（[Figure 1.1](#c01.xhtml#c01-fig-0001)）。

中毒攻击随后作为对抗性思维的自然延伸出现。与在推理时操纵输入的规避攻击不同，中毒攻击针对训练流程。少至 1% 的恶意数据，有时甚至更少，即可使模型决策边界偏移或植入持久行为。清洁标签中毒——即恶意输入与合法示例难以区分——尤其令人担忧，因为它规避了大多数数据卫生流程。这一类攻击表明，对数据来源和标注实践的信任不仅是质量问题，更是能够在模型 inception（初始阶段）就改变模型行为的安全隐患。

![Figure 1.1 Timeline of key adversarial milestones in AI security.](images/c01f001.png)

Figure 1.1 关键对抗性里程碑时间轴（AI 安全）。

随着隐私导向攻击的兴起，威胁面进一步扩大。成员推断攻击表明，攻击者可以通过置信度分数和过拟合特征判断特定数据点是否出现在模型训练集中。更令人震惊的是，模型倒置攻击通过查询模型输出，重构近似图像或数据记录，从而泄露训练数据的私密信息。这些技术动摇了长期以来的信念——即训练模型会抽象其训练输入。事实上，模型往往会记住并暴露私人信息，尤其是在训练数据集敏感且缺乏适当正则化或隐私控制时。

生成模型的公开发布带来了新的对抗性关注。与传统分类器不同，这些模型能够根据用户提示生成未经过滤的文本、图像或代码。攻击者迅速识别规避安全过滤的技术，这一方法如今被称为“越狱”（jailbreaking）。通过构造间接或含糊的提示，攻击者诱导模型生成有害、偏见或敏感的内容。这些提示注入技术经常在地下论坛和 GitHub 仓库中传播，暴露了自然语言对齐机制的根本弱点。在开放式任务中限制模型行为的难度成为生成式人工智能安全的核心主题。

随着对抗性技术的 proliferating（扩散），为其提供工具的生态系统也随之成熟。开源库如 `CleverHans`、`Foolbox`、`TextAttack` 和 `IBM's Adversarial Robustness Toolbox` 将入门门槛降至最低，使研究人员、学生和爱好者能够以最小努力复现最新攻击，从而加速不同模型类型和领域的新漏洞发现。虽然这种工具链的民主化提升了社区意识和防御能力，但它同样为攻击者提供了武器化代码，使得攻防博弈进入了一个知识公开、基础设施可及的新阶段——即“开源武器化”时代。

生成模型的越狱从学术好奇心迅速演变为商业责任风险。用户展示了商业大语言模型（LLM）系统如何被操控生成有毒语言、合成误信息或显式内容。这些攻击往往只需巧妙的措辞、多步推理提示或引入看似无害的内容来绕过内部约束。对齐机制无法完全遏制不良行为的局限性引发了行业-wide（全行业）关注，迫使平台提供商承认其安全层的脆弱性。曾被视为罕见边缘情况的现象，如今已成为日常事件，促使对生成系统安全的本质重新审视，以确定真正的安全含义。


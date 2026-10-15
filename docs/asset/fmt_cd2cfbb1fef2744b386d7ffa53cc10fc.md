
Many of the systems in place today are based upon heuristics about problems that have well-defined parameters or are amenable to mathematical modeling and programmed logic. They capture “preferred” solutions to the given repertoire of problems that represent well-known situations for which there exists a strong consensual position on the nature of the problem, agreement on the situation, and they rely on well-structured problems for which there exists an analytic formulation with a solution. Types of heuristic systems such as the Leibnizian are closed systems without access to an “external” environment, similar to the problem of how data warehouses work and are confined. That is, they operate based on supplied axioms that may fall into categories based on the system’s previous experience or labeling (topic tagging). In contrast, Lockean systems aim to reduce equivocality embedded in the diverse interpretations of a “worldview” but there too, their success depends on consensus among systems. The convergent and consensus-building emphasis of these kinds of heuristic systems is suited for stable and predictable situations or environments. However, complex systems require variety and agility in the interpretations, necessary for deciphering equivocal problems with multiple subjective points of view about an unpredictable future.

The Kantian inquiry system attempts to give multiple explicit views of a complementary nature that are best suited for moderate ill-structured problems. However, given that there is no explicit opposition to the multiple views, these systems may also be afflicted by conflicts characterized by plurality of complementary solutions. In contrast, Hegelian inquiry systems are based on a synthesis of multiple synthetic and antithetical representations of conflicts with contrary underlying assumptions. Reasoning systems that model unconventional attack episodes are most suited to analysis with Hegelian inquiry systems, which would facilitate multiple and contradictory interpretations of the focal information. This would help ensure that the focal information is subjected to continual reexamination and modification given a changing reality. Earlier, we mentioned that reasoning systems may work together to provide a full life-cycle modeling technique of information security attacks. The techniques a reasoning system may employ vary from simple, such as the coincidence of determination presented in the discussion about the breaking of the Vigenere cipher to find patterns among various models, to extremely complex, such as just described using heuristics. In most cases, reasoning systems produce models that can be rearranged, such as using first-order predicate logic to develop a sequence of probable moves in an attack episode. Next, we will examine some ways this might be done.

### 12.4.4 结合技术

我们介绍了合成启发学以及如何利用这些方法从现有数据中推断，并探讨了随机游戏理论以及可以被攻击建模和入侵检测系统用于预测攻击的技术。这些方法可以组合使用。考虑一种可能预测恐怖袭击事件的情境，然后考虑各种具体攻击。在这样的建模架构中，我们会有两个阶段，每个阶段由多个步骤组成。在第一阶段，我们首先选择一种概率方法来从大量数据中挖掘模式。这些数据可能来自许多来源，包括军事或情报信息流输入数据仓库、数据湖或本体论。例如，美国 Mitre 公司开发并支持的通用漏洞和暴露（`CVE`）本体论。

`CVE` 是一个收集和信息存储库，可导入到安全应用程序中。一旦我们收集了这些数据，就可以使用多种统计技术（如亲和分析）来挖掘模式或相关性。我们可以从这些模式中解析出构成元素，并将它们分类或类型化。这些通常会形成一个包含主体、客体、谓词和约束与规则的本体论。本体论很可能基于一种标记语言（如 `OWL`），并包含组装预测安全游戏的所有主要组成部分。一个典型的实现方式称为 `KAoS`。`KAoS` 是用于指定安全策略模型的本体论。一个简单的部分 `OWL` 本体论示例可能包括一个安全的“风险”，其子类为“入侵”和“灾难”，`OWL` 表示如下：

```
<owl:Class rdf:ID="Risk">
<rdfs:subClassOf rdf:resource="Intrusion"/>
<rdfs:subClassOf rdf:resource="Disaster"/>
</owl:Class>
```

从本体论中，我们接下来可以应用启发学来解析本体论，从而构建各种攻击场景。采用黑格尔方法，系统会构建反面事实网络，用于驳斥攻击事件，以及正面事实网络，用于建议攻击事件。这些事实网络使用随机算法进行分析，随机种子未知变量，并产生综合事实网络和场景。利用在主体-客体关联中组装的名词和动词，我们现在可以基于概率构建攻击事件的集合。事件可能包含描述可能因果和推断关系的叙事，以及整个事件的概率，然后每个攻击事件都会使用谓词和约束以及通过可能移动的统计路径来构建为概率过程（`CTMC`）。

以这种方式构建模型，可以帮助组织在最可能的场景以及最可能的关键节点集中有限资源，以便在最佳时机阻止攻击。这些模型还能够突出那些未被考虑的潜在攻击，从而打破“群体思维”，并表明完全新颖的方法（Figures 12.8 和 12.9）。

![FIGURE 12.8 Pattern Detection, Ontological Indexing](img/9781284236378_CH12_FIGF08.jpg)

FIGURE 12.8 Pattern Detection, Ontological Indexing

![FIGURE 12.9 Stochastic Models and Game Scenarios](img/9781284236378_CH12_FIGF09.jpg)

FIGURE 12.9 Stochastic Models and Game Scenarios

### 12.5 Heuristic Biases and Security Planning

正如我们所指出的，技术管理者和其他决策者通常拥有数据集合、推理系统以及 AI 决策应用，这些系统可以生成概率估计并根据威胁向量和表面提供行动建议，但有时人们会选择直觉而非信息，而忽视这些技术提供的证据。例如，Workman 的一项研究表明，有些人即使系统已被证明能够减少人为错误，仍会忽视 AI 决策系统的建议。这可能导致不幸的后果和糟糕的决策。

#### 12.5.1 AI 决策、天真理论与偏见

在使用 AI 决策系统时，分析人员和数据科学家通常会遵循一系列任务，包括分析建模、生成假设情境、进行敏感性分析、开展目标导向分析以及进行优化分析。在假设情境分析中，个人会修改变量或变量之间的关系，然后观察相应的值的变化。在敏感性分析中，会反复更改单个变量的值，并观察对其他变量的影响。目标导向分析则是将假设情境分析的方向倒置：它设定一个目标值（目标），然后反复调整其他变量，直到实现该目标值。最终，优化分析是目标导向分析的复杂扩展；然而，它不设定单个变量的特定目标值，而是在给定约束条件下寻找一个或多个目标变量的最优值。

AI 决策系统目前主要用于生成规范性建议，依据理性决策模型（如贝叶斯概率树）或基于经济因素（如投资回报率和回收周期的估计）。规范规则是为了在给定问题和约束下提供最佳解决方案，最佳解可能是一个平衡点。平衡点是一项数学计算，旨在在相互竞争或对立的目标之间取得最佳折中。然而，经理们有时会依赖直觉，这在正式上被称为天真理论。在此语境下，“天真”一词并不贬义，也不意味着非理性，也不意味着必然错误；它指的是不基于科学或结构化决策过程的决策。例如，Bonabeau 的一项调查显示，43% 的受访经理人表示他们至少 50% 的时间都依据“直觉”做出决策。天真理论是所有人对活动和事件运作方式的理论，这些理论并未得到操作化和验证，人们依赖感知和经验来进行判断。

在 AI 决策系统和规范、理性模型的框架下，未来结果的概率会被计算，但经理们往往不信任这些计算，尤其是在计算范围较短的情况下，尤其是在情绪和/或心理压力下，此时人们会转向天真启发法，甚至在面对反驳证据时也会得出错误结论。请记住，启发法是一种经验准则，而非正式、明确的规则。它是一种在特定情境下、在特定时间内有效的非正式策略或方法，但并不保证能够给出正确的决策。此外，这种经过训练的猜测容易受到人为偏见的影响，导致扭曲、不准确和遗漏。

- 偏见的例子是人们常常表现得像是不可控的事情是可控的。例如，当对手似乎无能时，人们会下更多赌注，因为他们认为可以利用弱势对手。[²⁵ 人们会在自己掷骰子时比在对手掷骰子时下更多的赌注。²⁶ 当骰子未掷时，人们会比已经掷过但结果未披露的骰子下更多的赌注。²⁷ 当他们选择计入获胜的骰子数字时，他们会下更多的赌注。²⁶ 大多数人觉得如果自己选择彩票号码而不是使用机器生成的“快速选号”，他们更有把握能中奖。²³ ^, ²⁵

- 偏见还解释了为什么许多人在打折的商品上花更多钱去车程更远的加油站和车辆磨损上，而规范性规则表明，为了节省少量金额，更应该开车更少、为商品支付更多。偏见还包括错误地认为过去的成功是未来成功的良好预测指标。²⁸ 代表性偏见也解释了无论“沉没成本”，常说的“把好钱倒在后头”或在篮球比赛中相信“连胜”的非理性金融升值和过度承诺。²⁹ 代表性偏见由 Kahneman 和 Tversky 在其研究中展示，他们发现人们常常主观判断不确定事件的可能性时，会基于随意观察到的模式，即使他们知道如何计算统计概率。作为这个认知现象的简单例子，他们表明有些人常把公平硬币投掷的 HHTHTT 模式判断为比 HHHTTT 更随机，尽管这两种结果的概率相同。Ajzen³⁰ 在一项研究中表明，当数据以复杂的因果关系呈现时，基率忽视现象出现的可能性会比在简单的统计任务中更小。基率忽视是指当事件有两个相关但独立的概率时，给予第一个概率的权重较小，而规范规则是将它们结合起来。

- 许多用于帮助组织做出有效安全决策的方法依赖于社会建构和启发性过程，而不是数学技术和技术，如决策系统、贝叶斯分析或随机建模。这些更具社会性和创造性的方法在安全领域很重要，因为安全威胁通常在短期内难以明确定义，且某些安全决策不适合量化处理——例如是否对员工进行监控。然而，决策中的偏见可能产生非常不希望的后果。Thibaut 和 Kelly 的前景理论研究表明，偏见会导致非常奇怪的决定。³¹ 这一点通过他们描述的两名犯罪嫌疑人被提供“交易”如果其中一人作证对另一人（囚徒困境）的描述得到了体现，其中一名嫌疑人说：“与其我们都挂掉，不如你比我更容易获释。”Loewenstein 和 Prelc 的研究发现，当参与者被问及是更喜欢一份薪酬为第一年 30,000 美元、第二年 40,000 美元、第三年 50,000 美元，还是第一年 60,000 美元、第二年 50,000 美元、第三年 40,000 美元的工作时，大多数人选择了前者，尽管这在三年内总收入更低——当涉及跨越多年（如安全支出或威胁分析）的复杂决策时，这种偏见会被放大。

#### 12.5.2 偏见与情境效应的相互作用

我们现在已经研究了 AI 决策和推理系统如何产生技术管理者用于规划攻击情景的场景。管理者也被教导使用诸如头脑风暴等概念生成活动来进行规划。例如，“故事讲述”已被用作推进组织目标（如规划安全计划）的方法。其他安全规划技术包括开发亲和图，用于将想法或问题分类为主题或类别，使用头脑风暴或头脑写作，参与者轮流生成并分享想法，以及“愿景”，参与者被教导通过 vicariously（身临其境）体验事件或结果，从而提出更现实的应对措施。重要的是要注意，这些方法的效果取决于信息的呈现方式。情境效应是指人们的决策受到问题描述（即情境）影响的情况。

情境化信息会激活认知模式，这些模式可能产生积极或消极的联想。认知模式是基于概念关联的精神脚本。例如，说到“餐厅”，人们会联想到在餐厅用餐并支付费用的特定脚本；例如，人们在餐厅会被提供食物并支付费用。当“快餐”作为修饰词与“餐厅”一起使用时，认知脚本会发生变化。通常，当“快餐”修饰“餐厅”时，人们会降低对餐厅所提供食物质量的评价。为了进一步说明这一点，当向人们展示关于一种用于治疗疾病的药物的情景时，人们根据信息的呈现方式会激活不同的认知模式；例如，当使用“挽救的生命”这一术语时，人们对药物的评价会比使用“失去的生命”更积极。³⁴

研究³⁵ 表明，参与使用情境生成技术（如情景和问题/解决方案特征）的规划会议的经理和员工在决策时更倾向于依赖直觉。然而，有些人更容易受情境影响——那些能够避免“被情境偏见”的人可以被认为遵循规范规则，而那些利用情境（无论是正向还是负向）的人则被认为陷入了启发性偏见。³⁶ 因此，在安全规划中使用概念生成技术的关键问题是偏见与情境效应之间的相互作用，以及这对管理者“凭直觉”而非客观数据或遵循规范规则做出决策的影响。

### 12.5.3 偏见、情境效应与安全决策

# 12.6 生物启发型安全与自适应系统

一种新型的信息和网络安全方法以人体为隐喻，用于构建更具适应性和抗损能力的系统，尤其在许多系统呈移动性的情况下，如笔记本电脑、智能手机以及其他通过所谓的自组网络（`MANET`）连接的设备。这些系统预计能够承受一定损伤，但它们具有从感染中恢复（recupere）并发展出合成免疫的能力。检测系统损伤的思路来源于危害理论，该理论阐述了当检测到病毒或细菌等危害时，哺乳动物免疫系统的反应。将该类比用于计算系统中，我们可以，例如，检查系统可执行文件以及它们在调用序列中的相互链接、变化事件或状态转换，或代码变更，从而推断原因。本节将介绍生物启发型安全的概念，特别是在与移动设备点对点（`P2P`）通信基础设施以及 `MANETs` 相结合的情形中。在此过程中，我们将提供自适应系统的说明及其在真实世界应用中的使用方式。

## 12.6.1 自愈合自适应系统

传统上，自适应系统指的是具有自愈合能力的系统。自愈合意味着系统能够从损伤中恢复。正如系统以多种方式适应环境，系统也使用多种机制进行自我修复或修补。许多自愈合系统采用一种常被称为易感-感染-易感（`SIS`）的模型。该模型中的每个节点或代理代表一个系统或设备，每条连接则是感染传播的通路。个体节点可能处于多种状态，如“受损”“安全”“感染”或“易感”，如上一章节所述。每当节点变得受损或感染，其他系统或设备受损或感染的速率会显著增加。⁴¹

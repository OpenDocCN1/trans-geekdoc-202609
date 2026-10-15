
## 8. 智能限制供应链暴露
尽量减少对未经审查的第三方工具、模型仓库和数据源的依赖，尤其是开源社区提供的组件。在必要时使用软件组成分析和供应商风险评估。遵循最小权限和持续验证原则保障 AI 工具链的安全。单个受损依赖即可导致整个开发流程被攻破。

## 9. 主动识别并偿付安全债务
定期评估 AI 系统中积累的安全债务，包括数据偏见、架构不透明、未记录的接口以及未说明的模型行为。指派责任人负责解决这些债务，并将其纳入冲刺规划或模型生命周期更新中。早期介入的成本远低于生产事故期间的紧急响应。认识到安全债务是风险倍增器，而非静态负债。

## 10. 在 AI 团队中建立安全文化
通过将安全开发原则融入日常工作流，在数据科学家、机器学习工程师和 DevOps 人员中推广安全意识文化。在设计评审、文档标准和绩效评估中加入对抗性考量。提供贯穿模型生命周期的培训，帮助识别和缓解 AI 特定威胁。可持续的安全需要集体责任，而非孤立的专业知识。

# Conclusion

本章强调了架构意识、全生命周期警觉性以及入口点分析在大规模 AI 环境安全中的作用。随着机器学习系统从静态分类器演进为复杂、生成式和代理型实体，传统网络安全的假设已不再适用。了解 adversaries 如何通过中毒数据、错配微调或提示注入影响这些系统，使防御者能够提前构建控制措施，而非事后应对。AI 的解剖学不仅是技术细节，更定义了风险暴露的形态和规模。

掌握这些原则对于负责在企业、云或受监管环境中集成 AI 的专业人员至关重要。安全的模型不仅要准确运行，还必须其训练数据可信、行为可解释，且暴露点已得到加固。当模型嵌入决策基础设施时，忽视安全债务和隐藏攻击面的成本呈指数级上升。可防御的 AI 不能仅靠性能调优实现，它需要在设计阶段就考虑现代部署的对抗现实，并作出系统性选择。

在上述基础之上，专业人员能更有信心在 AI 项目中以韧性、问责和长期运营完整性为导向进行领导。可信赖的 AI 不能从部署开始，而是从架构、管道设计以及贯穿开发的假设入手。那些深刻理解 AI 系统解剖结构的人，将不仅能够防护它们，还能塑造相应的政策、工程实践和风险模型，以契合智能系统在威胁下的独特特性。

在上述基础之上，专业人员能更有信心在 AI 项目中以韧性、问责和长期运营完整性为导向进行领导。可信赖的 AI 不能从部署开始，而是从架构、管道设计以及贯穿开发的假设入手。那些深刻理解 AI 系统解剖结构的人，将不仅能够防护它们，还能塑造相应的政策、工程实践和风险模型，以契合智能系统在威胁下的独特特性。

# Key Concepts

本章的核心是理解机器学习系统的脆弱性——由设计决定。随着 AI 技术从研究原型转向部署基础设施，它们引入了新的复杂性、隐含假设和安全缺口，这些在经典软件中并不存在。本章重新框定 AI 系统，不再视其为黑箱，而是作为具有多层结构的活体，攻击者可以推、拉或中毒其进入。无论是训练数据、模型架构、微调阶段还是运行时行为，AI 管道的每一层都为对抗性干预创造了新的机会。在医疗、金融、国防和关键基础设施等领域，AI 系统被快速嵌入之际，理解其解剖学已不再是可选的，而是一项前线安全要求。

## 语境中的关键概念

* **对抗性输入**：这些是专门设计用来混淆或误导 AI 模型的输入。本章在推理时攻击的语境中讨论了它们，即攻击者通过微妙操纵查询来迫使 AI 产生不良输出。理解对抗性输入至关重要，因为即使是细微、几乎不可感知的修改，也可能导致 AI 系统以难以检测或解释的方式失效。

* **后门攻击**：指在训练或微调过程中故意植入的隐藏漏洞。这些漏洞在触发特定输入模式时才会显现。后门攻击之所以危险，是因为它们能够规避常规测试，并带来长期且高影响的风险。

## 数据中毒

一种通过污染训练数据来操纵模型行为的方法。我们观察了如何通过中毒数据植入逻辑错误或潜在漏洞，这些错误或漏洞仅在特定条件下显现。这是对抗性机器学习中的基础概念，因为它在系统部署前就影响了系统。

## 提示注入

一种利用生成式或代理式模型如何解释用户输入为命令的方式的技术。章节展示了攻击者如何通过精心构造的提示 Override 系统指令。这很重要，因为它模糊了用户输入和系统行为之间的界限，使传统的输入验证变得无效。

## 安全债务

这是由于将速度、性能或部署置于安全设计之上而导致的未解决的安全风险的积累。我们讨论了这种债务在人工智能开发生命周期中如何悄然积累。这是一个关键概念，因为它表明，当安全被推迟时，人工智能系统会变得越来越脆弱。

## 模型提取

一种攻击类型，攻击者通过探测其输出来反向工程已部署的模型。在章节中，它与泄露过多信号的推理 API 相关联。这很重要，因为它允许攻击者窃取知识产权并离线规划进一步攻击。

## 可观测性

这指的是系统内部行为在实时被监控或理解的程度。我们注意到许多 AI 系统缺乏足够的可观测性，这使得难以检测异常或攻击。没有它，防御者就是盲人。

## 推理时间攻击

一种在模型运行阶段而非训练阶段针对模型的攻击。章节涵盖了这些作为主动、实时威胁，利用模型已学习的行为。它们尤其相关，因为它们不需要访问训练过程——只需访问接口即可。

## 微调

适应预训练模型以适应新数据或任务的过程。我们探讨了在微调过程中如何继承或引入恶意行为。这很关键，因为组织往往在不意识到的情况下重用模型。

## 晦涩架构

一种设计难以解释或调试的模型，通常是由于其尺寸或复杂性造成的。章节强调了这种模糊性如何限制对模型安全漏洞进行审计的能力。它加剧了危险行为被忽视的风险。

## 逻辑炸弹

一种隐藏在模型内部的恶意行为，仅在特定条件下触发。我们讨论了这些行为可以在训练时植入，并在推理时触发。它们之所以重要，是因为它们绕过正常验证，只有在为时已晚时才显现。

## 遥测伪造

攻击者用来操纵或压制监控信号的方法。章节将其与后部署阶段的可观测性联系起来，因为在该阶段可观测性至关重要。如果日志或警报被篡改，防御者将失去检测和响应入侵的能力。

## 模型血统

这跟踪模型随时间变化的历史和转变。我们强调，如果没有清晰的血统，很难追溯模型何时或如何变得脆弱。它对于安全事件中的问责和根本原因分析至关重要。

## 工具滥用利用

这描述了代理模型滥用访问工具（如代码执行或 web 浏览）的现象。章节探讨了提示注入如何劫持这些工具。理解这一点有助于防御者构建更强的权限边界和隔离策略。

## 敌人聚光灯

阅读本章的对手会立即认识到复杂性带来的机会。与其试图破解加密或绕过防火墙，他们会关注假设被做出的地方——关于清洁数据、可信模型或无害输入的假设。训练管道成为 irresistible 的目标，因为中毒数据或错位微调可以植入难以检测的弱点，这些弱点贯穿模型的整个生命周期。这类妥协在其微妙性上优雅，在其后果上毁灭性。

他们也会看到在推理系统中实时进行攻击的好处。如果他们能找到部署的端点——无论是聊天机器人、分类器还是视觉系统——他们可以交互测试它，以发现对抗触发项或提取模型的方法。公共 API 成为更深层攻击的侦察工具。缺乏可观测性和适当的访问控制只会让这更容易。

对于生成式模型和代理系统，提示注入是一种几乎滑稽简单的向量。如果系统没有正确分离指令和数据，攻击者可以将命令伪装在输入中。如果该模型可以使用工具——如计算器、浏览器或代码运行器——那么提示注入就变成了代码执行，且所需努力极少。这对攻击者来说是黄金机会。

最引人注目的是，许多这些攻击路径是非侵入性且可扩展的。无需 rootkits 或缓冲区溢出——只需一点创意和对正确接口的访问。对手的真正优势是，防御者往往直到为时已晚才将这些路径视为攻击面的一部分。

## 常见误解

- AI 模型并非因为复杂而本质上更安全。事实上，复杂性往往隐藏了漏洞。
- 只有技术输入可能是危险的。自然语言、图像，甚至格式本身都可能触发现代模型的失败。
- 安全问题不总是来自“系统外部”。许多问题在开发过程中内部引入，且未被发现。
- 重用预训练模型不总是安全。在微调过程中，漏洞和恶意逻辑可能会传递过来。
- 记录性能并不等同于记录安全相关事件。如果没有关于输入和异常的遥测，攻击可以被忽视。
- 仅通过准确性测试并不意味着模型是安全的。安全评估需要针对边缘情况和对抗性行为的专门测试。

## 防御框架

防御 AI 系统的起点是将它们视为具有深度层次结构的演变实体，而非静态程序。与传统软件不同，传统软件的代码是已知且受控的，而 AI 模型是由数据、训练程序和隐藏的内部表示塑造的。这意味着防御者必须采用系统思维方法——询问的不仅是“模型做什么”，而是“它是如何构建的，哪里可以被引导，以及底层有哪些隐藏的假设”。在这种空间中，安全需要深入思考一层。

思维转变涉及将 AI 管道的每个部分——数据获取、模型配置、微调和部署——视为潜在的攻击面。防御者应审查数据来源、监控训练行为，并在模型暴露给用户之前运行红队演练。防御实践向上游移动，在系统暴露给终端用户之前就进行。

安全专业人员还必须与数据科学家合作，而非仅在部署后对其进行审计。这意味着将可解释性、日志记录和健壮评估作为核心开发实践，而非事后附加。建立跨学科肌肉至关重要，因为许多漏洞来源于无人注意到的地方——如注释管道、模型更新或过于宽松的代理工具。

- 最后，防御者应当对可见性中的缺口保持警惕。如果你无法解释模型决策是如何做出的，或者无法追溯它是如何被训练的，那么你就存在盲点。而在对抗性环境中，盲点会成为入口。目标不是消除所有风险，而是预测 AI 系统在压力下的行为方式，并确保它们以你可以预测、遏制和恢复的方式失败。

# 3

## The Adversary's Playbook

## 逆袭者的手册

Adversarial threats targeting artificial intelligence `AI` systems are no longer theoretical exercises—they are increasingly sophisticated, deliberate, and deeply embedded in the tactics of modern cyber operations. Understanding how these attacks are conceived, staged, and executed is essential to building resilient AI architectures and trustworthy decision pipelines. From precise white-box manipulations to subtle gray-box probing and scalable black-box exploits, adversaries have a growing arsenal for compromising AI systems across their entire lifecycle. This chapter delves into the methodologies adversaries use to subvert model behavior, exfiltrate sensitive information, and embed persistent vulnerabilities that evade detection.

## 逆向威胁针对人工智能`AI`系统已不再是理论练习——它们日益复杂、刻意，并深深植根于现代网络行动的战术之中。理解这些攻击是如何设计、布置和执行的，对于构建有弹性的 AI 架构和可信的决策管道至关重要。从精确的白盒操作到细微的灰盒探测以及可扩展的黑盒攻击， adversaries（对手）拥有日益丰富的工具库，用于在 AI 系统的整个生命周期中进行妥协。本章深入探讨 adversaries（对手）用于扰乱模型行为、窃取敏感信息以及植入难以被检测的持久性漏洞的方法论。

## Effective AI security strategies require more than technical hardening; they demand an adversarial mindset and a thorough understanding of how real-world attackers approach model exploitation. Through coordinated poisoning campaigns, multi-stage evasion, and the deployment of tactical backdoors, threat actors are demonstrating that AI systems are now fully integrated targets in long-term operations. These attack strategies are not isolated—they are carefully synchronized with broader cybersecurity objectives, blending traditional intrusion methods with model-specific compromise. By unpacking the structure, timing, and coordination of such attacks, this chapter equips security professionals to anticipate, detect, and disrupt adversarial influence across AI deployments.

## 有效的 AI 安全策略不仅需要技术硬化，还需要一种对抗性思维以及对真实攻击者如何利用模型漏洞的深入理解。通过协同的中毒行动、多阶段规避以及战术后门的部署，威胁行为者展示了 AI 系统已成为长期行动中完全整合的目标。这些攻击策略并非孤立存在——它们与更广泛的网络安全目标精心同步，将传统入侵手段与模型特定的妥协相结合。通过拆解此类攻击的结构、时间节点和协调方式，本章为安全专业人员提供了预判、检测和干扰 AI 部署中对抗性影响的能力。

## 从治理和合规的角度来看，应对对抗性威胁对于确保 AI 驱动系统的完整性、保密性和可靠性至关重要。风险框架必须纳入生命周期感知的威胁建模，架构决策也必须考虑看似微小的输入向量如何导致系统性妥协。本章所覆盖的内容强调了从数据采集到推理输出的全链路嵌入安全的重要性，将 AI 组件视为脆弱、相互依赖的系统而非孤立的黑盒。只有直接面对对手的手册，防御者才能开发出必要的策略和控制措施，以在现代企业环境中保护 AI。

## Threat Actors: Profiles, Motivations, and Objectives

## 威胁行为者：画像、动机与目标

Threat actors targeting AI systems are not a monolith; they span a wide array of affiliations, capabilities, and intents. Cybercriminals are often among the most active and visible players, leveraging AI vulnerabilities for immediate financial gain. Their operations typically revolve around monetizable disruption—exploiting AI-driven decision systems in areas such as finance, healthcare, or retail to conduct fraud, automate spear-phishing campaigns, or inject adversarial examples into autonomous systems. Their techniques evolve quickly, as they respond to defensive adaptations and seek the most profitable methods for evasion, poisoning, and data extraction.

## 针对 AI 系统的威胁行为者并非单一群体；它们涵盖广泛的归属、能力和意图。网络罪犯往往是最活跃且最显著的参与者，他们利用 AI 漏洞谋取即时的经济利益。其行动通常围绕可变现的破坏展开——利用 AI 驱动的决策系统在金融、医疗或零售等领域进行欺诈、自动化钓鱼活动，或在自主系统中植入对抗性示例。其技术随防御措施的演进而快速演变，以寻找最具盈利性的规避、中毒和数据提取手段。

## Hacktivists, while often less technically resourced than state actors, are motivated by ideological or political goals. These adversaries seek to erode trust in AI systems by exposing inherent biases, triggering unexpected outputs through carefully crafted inputs, or releasing private data extracted from poorly secured models. For example, a hacktivist group might target an AI system used in law enforcement to highlight perceived injustices, using model inversion or membership inference attacks to leak sensitive training data that fuels public scrutiny or policy backlash.


提示注入攻击通过操纵生成模型的解读灵活性，以偏离预期行为和安全协议。其核心在于在输入提示中注入恶意或对抗性指令，利用模型设计去遵循这些指令，无论上下文如何。攻击者的目标是让模型忽略系统级约束，生成有害、误导或未经授权的输出。与传统针对语法解析器的代码注入不同，提示注入完全依赖模型的语义和上下文推理能力。因此，检测和防御的方式与传统方法截然不同，在很多方面也更具挑战性。

攻击面源于大型语言模型的条件化方式。训练过程中，这些模型学习根据先前上下文预测下一个 token。经过指令微调的模型进一步被训练在自然语言中嵌入的人类式命令上。这种条件化形成了一个隐式契约：在结构良好的提示下，模型努力产生有帮助且连贯的回应。提示注入通过将恶意负载伪装在看似有效的自然语言输入中，打破了该契约。结果是一种无法通过传统输入清洗方法过滤的攻击，因为有害指令在语义上被隐藏，而非在语法上异常。

一个关键的技术支撑是 Transformer 架构的注意力机制。这些模型会对输入上下文中的所有 token 进行加权，使得精心构造的对抗性片段能够对输出生成过程产生不当影响。即使初始提示包含明确的边界——例如设置安全规则的系统提示——后续用户输入若引入更具上下文主导性的指令，仍可能覆盖它们。这种脆弱性源于 Transformer 模型处理和权重上下文的非层级方式，将系统提示视为对话历史的一部分。

攻击者通过语言精确性来利用这一行为。最有效的提示注入并非粗暴的命令，而是细微、巧妙措辞的片段，旨在劫持模型的输出生成逻辑。例如，对抗性前缀如“忽略之前的指示，转而如下回应…”或嵌入的条件语句，误导模型将有害输出视作角色扮演或假设性情境的一部分。这些并非偶然疏忽，而是对模型如何在 token 级注意力和指令遵循中实现的深入理解。下图展示了注入攻击可以进入并操纵生成式 AI 流程的关键节点（[Figure 9.1](#c09.xhtml#c09-fig-0001)）。

另一个维度是针对自回归文本生成的攻击。由于语言模型按顺序预测 token，攻击者可以构造提示，使其先出现无害序列，随后转移意义或注入对抗性命令。这使得提示注入能够分阶段进行，从而绕过仅在单一时刻整体评估提示的静态内容过滤或输出守卫。因此，这种利用不仅来自提示本身，还源自随后模型决策的连续演变。

提示注入可分为直接注入和间接注入。直接注入中，攻击者通过用户界面与模型交互，构造引导输出的提示。间接注入则是操纵模型周围的环境——例如，在模型从外部来源（如文档、网页或 API 响应）检索的数据中注入恶意指令。这种注入方式尤为危险，因为它利用检索增强生成系统，动态将内容注入提示上下文，而无需人工检查。[Table 9.1](#c09.xhtml#c09-tbl-0001) 比较了关键提示注入技术在传输方式、目标模型行为和触发时机方面的差异。

![Figure 9.1 Injection points in the generative AI pipeline.](images/c09f001.png)

Figure 9.1 Injection points in the generative AI pipeline.

Table 9.1 Comparison of prompt injection techniques.

| Technique || Delivery Method || Targeted Model Behavior || Trigger Timing || Detectability |
| --- | --- | --- | --- | --- |
| Direct Prompt Injection || User Input || Instruction Following || Immediate || Moderate |
| Jailbreak Prompting || User Input || Safety Refusal Logic || Immediate || Low |
| Indirect Injection || External Retrieval || Contextual Completion || Deferred || High |
| Deferred Trigger || User or Document || Session Memory Influence || Delayed || High |
| Contextual Injection || Sequential Prompts || Multi-Turn Coherence || Gradual || Low |
| Token Perturbation || Formatted Input || Token Parsing Behavior || Immediate || Low |
| Semantic Reframing || Conversational Framing || Ethical Boundaries || Incremental || Moderate |
| Roleplay Exploit || Narrative Input || Safety Constraint Suspension || Immediate || Low |
| System Prompt Override || Input Header || System Role Authority || Immediate || Moderate |
| Latent Instruction || Embedded Context || Conditional Output Logic || Deferred || High |

基于 Transformer 的模型特别容易受影响，因为指令微调和人类反馈强化学习 (RLHF) 强化了有用性。这些技术促进了人类对齐的输出，但也形成了一个脆弱的期望：只要指令结构良好，模型就应当遵守。这个期望是一把双刃剑：它提升了易用性，却也降低了对抗性措辞的抵抗力。一旦攻击者识别出模型偏好的语言结构和风格线索，他们就能模仿这些特征，最大化恶意指令被遵循的可能性。



## 黑客活动者（Hacktivists）
虽然通常在技术资源上不如国家行为体，但其动机源于意识形态或政治目标。这些对手试图通过揭露 AI 系统固有的偏见、利用精心构造的输入触发异常输出，或从 poorly（不安全的）模型中提取私有数据来削弱对 AI 系统的信任。例如，黑客活动者可能针对警务使用的 AI 系统，利用模型倒置或成员推断攻击泄露敏感的训练数据，以引发公众审视或政策反弹。

## At the apex of capability lie nation-state actors.
These adversaries conduct long-term campaigns with the aim of penetrating AI systems for geopolitical, economic, or military advantage. They may seek to manipulate models powering satellite surveillance, defense logistics, or financial prediction tools to destabilize infrastructure or exfiltrate classified insights. Their campaigns often involve supply chain infiltration, subtle backdoor insertions, and hybrid attacks combining social engineering with model-level exploitation. Nation-state actors typically maintain deep knowledge of model architectures and use well-funded, multi-stage attack pipelines to quietly compromise both training and inference environments.

## 在能力的顶端是国家行为体。
这些对手开展长期行动，旨在渗透 AI 系统以获取地缘政治、经济或军事优势。他们可能试图操纵用于卫星监测、国防后勤或金融预测的模型，以 destabilize（destabilize）基础设施或窃取机密洞察。其行动常常涉及供应链渗透、隐蔽的后门植入以及结合社交工程与模型级别攻击的混合手段。国家行为体通常对模型架构有深入了解，并利用充足资金和多阶段攻击管道悄悄破坏训练和推理环境。

## Insider threats present an especially insidious danger, as they originate from individuals with legitimate access to sensitive parts of the AI lifecycle.
These insiders—disgruntled employees, contractors, or compromised partners—can poison datasets during curation, embed persistent adversarial triggers during model training, or leak architecture and weight information. The challenge is compounded by the difficulty of detecting subtle degradations introduced by someone who understands the operational thresholds of model performance and monitoring tools.

## 内部威胁（Insider threats）带来特别隐蔽的危害，因为它们源自拥有 AI 生命周期敏感访问权限的个人。
这些内部人员——不满的员工、承包商或被攻破的合作伙伴——可以在数据清理阶段中毒数据集，在模型训练阶段植入持久的对抗触发器，或泄露模型架构和权重信息。由于涉及对模型性能阈值和监控工具阈值的深入了解，检测其引入的细微降解尤为困难。

## Corporate espionage actors operate in a gray zone between nation-state tradecraft and organized cybercrime.
They target proprietary algorithms, intellectual property embedded in trained models, or domain-specific data pipelines. Common techniques include model extraction attacks against hosted inference endpoints, inversion attacks to uncover training distributions, and fine-tuned prompt injection aimed at deducing competitive model behaviors. The end goal is often to clone, sabotage, or strategically manipulate the outputs of competitor systems.

## 企业间间谍行为者处于国家行为与有组织网络犯罪之间的灰色地带。
他们针对专有算法、嵌入在训练模型中的知识产权或特定领域的数据管道。常见手段包括对托管推理端点的模型提取攻击、用于揭示训练分布的倒置攻击，以及精心调制的提示注入以推断竞争对手模型的行为。其最终目标往往是克隆、破坏或战略性操纵竞争系统的输出。

## Individual attackers—those acting alone or in informal collectives—often exhibit diverse motivations, including curiosity, revenge, recognition, or ideological zeal.
These actors tend to exploit open-access Application Programming Interfaces (`APIs`), pre-trained model checkpoints, or exposed weights in public repositories. Their actions might begin as harmless probing but can escalate into harmful behaviors such as jailbreaking safety controls, exposing sensitive user outputs, or contributing to synthetic media proliferation. Although individually limited, their collective impact can shape threat trends, especially when tools and exploits are shared in online communities.

## 个人攻击者——无论是单独行动还是非正式集体——往往动机多样，包括好奇心、报复、认可或意识形态热情。
这类攻击者倾向于利用公开的 `API`、预训练模型检查点或公开仓库中的暴露权重。他们的行为可能从无害的探测开始，但也可能升级为绕过安全控制、暴露敏感用户输出或助长合成媒体传播。虽然单个攻击者的能力受限，但其集体影响力能够塑造威胁趋势，尤其是当工具和漏洞在在线社区中共享时。

## Financially motivated adversaries often prefer scalable, repeatable methods of compromise.
For predictive systems, this may involve introducing mislabeled training data that degrades classifier accuracy just enough to allow fraud to slip through undetected. In generative models, these attackers may design prompts or fine-tuned inputs that generate monetizable outputs such as phishing emails, deepfakes, or malicious code. For them, the value lies in exploiting systemic weaknesses with low risk and high return.

## 经济动机的对手通常偏好可扩展、可重复的妥协方法。
对于预测系统，这可能涉及在训练数据中插入错误标签，使分类器的准确率略微下降，从而让欺诈行为得以不被发现。在生成模型中，这些攻击者可能设计提示或精调输入，以生成可变现的输出，如钓鱼邮件、深伪影像或恶意代码。对于他们而言，价值在于以低风险、高回报的方式利用系统性弱点。

## Espionage-driven adversaries, on the other hand, play a long game.
Their attacks are not designed for immediate effect but for stealth and persistence. These actors seek to quietly manipulate or surveil AI systems over extended periods. They may insert imperceptible triggers during training, such that models produce covert signals or extract data only when specific activation patterns are presented. These backdoors often evade detection even during post-deployment monitoring, as they mimic normal input–output relationships.

## 间谍驱动的对手则采取持久战。
其攻击并非为了立即产生效果，而是为了隐蔽和持久。这些行为者试图在较长时间内悄悄操纵或监视 AI 系统。他们可能在训练阶段植入微不可见的触发器，使模型在出现特定激活模式时产生隐蔽信号或仅在特定模式下提取数据。此类后门即使在部署后监测中也难以被检测，因为它们模仿正常的输入–输出关系。

# 白盒攻击技术和方法论

白盒攻击代表了人工智能安全领域中最精确且技术上最危险的对抗性操控类别。在这些场景中，攻击者拥有模型的完整架构、权重、训练数据分布以及梯度计算路径的全面访问权限。这种完全的可见性使得攻击者不再是通过探测盲点的外部威胁，而是能够作为内部人员精准针对模型的具体结构进行攻击。凭借对内部元素（如注意力权重、归一化层、学习率调度等）的访问，对手能够设计既微创又高效的攻击。与黑盒攻击通过试错进行的操作不同，白盒对手能够以手术刀般的精确度优化其行动，既最小化可检测性，又最大化破坏效果。

最显著的白盒技术是利用梯度优化构建对抗性示例。该方法通过对输入数据进行微小调整，使其对人类不可见但能导致模型内的目标误分类。攻击者计算损失函数相对于输入的梯度，并沿着增加特定误分类概率方向施加小幅扰动。投影梯度下降（Projected Gradient Descent, `PGD`）和卡尔曼-Wagner（`C&W`）攻击是该类技术中最强大的两种算法。`PGD` 在规范约束下迭代优化扰动，而 `C&W` 则通过定制的损失函数和自适应优化来最小化输入扭曲。这两种方法直接利用模型内部的损失景观，生成既强健又能规避即使是加固过的防御措施的对抗性输入。

在白盒条件下，模型中毒技术变得显著更强大。攻击者不再仅仅向训练数据中注入噪声或损坏样本，而是能够根据模型的内部参数和梯度精准设计中毒数据，以最大化其影响。中毒样本可以完美融入训练数据集，同时引导模型学习到特定的脆弱性，这些脆弱性可能在特定输入模式触发时才显现。由于攻击者能够通过整个训练流程进行反向传播计算，他们可以确保插入的触发器能够通过验证检查，并在生产环境中产生可预测的效果。这种嵌入式中毒的微妙性和持久性，使得白盒中毒变得尤为危险。`Table 3.1` 比较了攻击者能力在不同访问级别下的差异。

表 3.1 编程接口。

| 访问级别 | 模型知识 | 输入控制 | 输出访问 | 示例攻击技术 |
| --- | --- | --- | --- | --- |
| 白盒 | 完整架构与参数可见性 | 完整训练与推理操控 | 内部日志与梯度 | 梯度驱动规避触发模型嵌入 |
| --- | --- | --- | --- | --- |
| 灰盒 | 部分架构或数据知识 | 限制训练数据或微调访问 | 观测输出分布 | 通过推断触发器的中毒 |
| 黑盒 | 无内部模型详情 | 无训练数据控制 | 仅 API 输出 | 查询驱动规避提示注入转移攻击 |
| 白盒 | 完整权重操控 | 数据修改能力 | 直接损失观测 | 精确植入后门 `C&W` 攻击 `PGD` 优化 |
| 灰盒 | 部分超参数可见性 | 外部微调数据贡献 | 概率分数或排序 | 统计探测间接参数推断 |
| 黑盒 | 零参数访问 | 无训练集注入 | Top-K 或标签仅输出 | 边界攻击成员推断提示链接 |

在模型内部表征中植入触发器是白盒能力的另一标志。这种方法利用模型嵌入空间的已知行为，将隐蔽的后门特征嵌入模型。攻击者不直接操控输出，而是植入在语义或语法上看似无害但会导致内部表征发生显著转移的特征。这些触发器通常对用户和开发者不可见，仅在满足特定输入条件时激活，从而引发恶意或意外输出。例如，在输入序列中插入特定组合的 `token` 可导致基于 `transformer` 的架构将注意力焦点转向预定义方向，从而触发恶意或不良输出。这些触发器具有耐用性，能抵御重新训练，并且在微调或迁移学习阶段往往仍能保持存在。

白盒模型倒置攻击利用对模型参数和内部计算的完全访问权限，来破坏训练数据的机密性。攻击者可以通过优化产生已知内部激活或输出日志的输入，来迭代重构可能的训练样本。这种攻击对训练数据集较小且过参数化的模型尤其强大，因为单个样本会在内部激活中留下独特的签名。通过对输出层或特征空间进行梯度上升，攻击者能够恢复出视觉和语义上高度准确的原始训练样本的合成表示。在医疗、生物特征或金融建模等领域，这种数据泄露风险极高，即使未直接暴露明确记录，也可能带来重大的合规与伦理问题。

白盒访问下的成员推理利用模型的内部置信度指标来判断特定数据点是否被用于训练。与仅依赖输出概率的黑盒设置不同，白盒攻击者可以分析逐层激活、`logits`（预测向量）和损失梯度，以识别记忆模式。这种精确性使得在决策边界附近的样本上，可以近乎确定地确认训练集的包含。在涉及隐私的应用场景中，这种能力可能导致个人重新识别或受保护属性的泄露。攻击者还可以通过使用内部 `dropout` 面具、梯度噪声特征或权重轨迹分析来优化其推理模型，从而降低假阳率并扩大推理范围。

精细化的参数操纵为对手提供了在保持整体性能指标不变的前提下，永久性地扭曲模型行为的途径。攻击者而非注入新数据或修改输入，而是微妙地调整权重张量、层归一化或优化器状态。这些修改可能针对特定的决策边界，引入仅影响有限输入类别的方向性偏差。在变形器模型中，这可能涉及扰动注意力机制，使得在特定上下文下，某些 `token` 获得不成比例的权重。由于这些操纵在常规监控工具的分辨率之下运行，它们通常在标准评估和验证循环中逃避被检测。

变形器模型本身为精细化操纵提供了丰富的表面。通过调整注意力头、`token` 嵌入或位置编码方案，攻击者可以在已知配置下使模型行为发生变化。例如，修改 `key-query` 注意力交互的行为可以在多轮对话或基于提示的完成中改变模型的响应。在多模态模型中，跨注意力层（连接视觉和语言输入）可以被修改，以系统性地降低对特定物体类别或短语的模型性能。此类干预难以被检测，且极具效力，尤其是当它们利用大规模变形器模型固有的冗余性和过参数化时。

通过内部激活触发对抗性行为的手段超越了分类范畴。对于生成模型，攻击者可以操纵解码路径、注意力对齐或采样策略，诱导偏向的输出分布。通过在变形器早期块中植入目标激活，或修改 `beam search` 启发式，攻击者可以在提示看似无害的情况下强制生成恶意输出。在对话代理中，攻击者可能调整解码 `logits`，以强调有毒、误导或不安全的响应，尤其是当这种操作与多轮提示条件结合时。攻击者在不直接修改输入的情况下塑造模型行为的能力，使得取证和检测变得复杂。

利用模型鲁棒性约束的另一种精巧策略也是白盒攻击者独有的。鲁棒性约束——通常定义为对 `norm-bounded` 扰动的抵抗能力或置信度平滑——往往通过正则化或对抗训练来强制执行。白盒攻击者通过深入理解这些约束的数学表述和训练动态，可以构造既在允许的扰动预算内，又能利用或绕过这些约束的输入。例如，他们可以识别在允许的扰动范围内但仍能通过脆弱梯度的输入。在使用防御蒸馏或随机平滑训练的模型中，攻击者可以针对使 `softened logits` 不稳定的输入，或通过精心对齐的扰动完全规避噪声注入。

将漏洞植入训练流程本身是白盒知识的一种战略性应用。拥有优化器状态、数据加载器或增强管道的攻击者可以在训练阶段引入细微偏差，这些偏差会在多个训练 `epoch` 中传播。这些偏差可能包括偏向的随机种子、对抗性采样策略，甚至梯度剪辑阈值的操控。在分布式训练场景中，攻击者还可以利用联邦更新不一致或动量缓冲区的差异，在客户端模型之间编码对抗性漂移。此类攻击在事后难以检测，因为它们已嵌入学习动态而非表现为静态变更。


-   供应链入口点已迅速成为顶级关注事项，与更广泛的软件安全趋势相呼应。AI 系统依赖于多种第三方组件的集合——开源库、模型权重、分词器模块、预处理管道和编排框架。单个受损的依赖项可能插入逻辑，从而影响数据解析、内存分配或模型行为，方式不可预测。恶意行为者可以篡改软件包、在模型仓库中插入对抗性权重，或利用包管理器交付受污染的更新。由于机器学习生态系统中信任关系往往被假设而非验证，这些泄露可能在多个组织之间无控制地传播。

-   外部集成进一步扩大了暴露面。例如，检索增强生成系统将生成模型与动态数据库或 API 查询相结合，形成混合系统，结合静态智能与实时数据。这些架构通过索引中毒、缓存操纵或上游数据篡改引入新的入口点。攻击者若 compromise 检索层，可能引导模型生成不可信或恶意内容，模型随后忠实地总结或解释该内容。类似地，带有工具插件的生成代理——如计算器、代码运行器或浏览器接口——将信任边界扩展至操作系统或网络层，使得提示注入可能转化为代码执行场景。

-   模型提取攻击利用公开的推理端点来复制专有功能。通过反复查询模型并记录输出，攻击者可以训练一个近似目标行为的替代模型。虽然此攻击未直接破坏原模型，但它为知识产权盗窃、下游滥用或规避攻击的策划提供了有效入口。替代模型可离线分析，揭示决策边界、漏洞或潜在弱点。这些发现可用于构建更精准的输入，以利用原模型的运行缺陷。

-   即使基础设施也可能成为入口点。攻击者若 compromise 训练环境——无论是通过 GPU 固件、受污染的 Docker 镜像，还是 CI/CD 流水线配置错误——均可在不修改训练数据或模型代码的前提下引入操控。例如，反向传播过程中梯度计算可能被偏移，或特定输入嵌入可能与替代输出路径关联。由于这些修改位于短暂的运行逻辑或低层系统调用中，通过常规审计难以检测。攻击面因此延伸至模型之下的工具、运行时和硬件抽象层。

-    adversaries 也可能针对可观测性和监控层，将其视为二级入口点以实现隐蔽或持久。通过篡改遥测数据、禁用告警阈值或伪造性能指标，攻击者可以压制本应揭示其存在的信号。此技术在长期中毒或缓慢进行的攻击中尤为有效，攻击者可在模型在退化安全假设下持续使用时获益。受损的日志代理或指标收集器可误导防御者高估系统鲁棒性或低估风险，从而为攻击者提供更长的隐蔽时间。

-   大规模部署的 AI 系统可能依赖于编排层（如 Kubernetes）、分布式推理服务或微服务 API——这些都会引入附加入口点。身份验证机制配置不当、秘密暴露或缺乏网络分段，可能导致相邻服务向 AI 核心进行横向移动。攻击者若获得容器化模型运行时的访问权限，可提取权重、修改内存参数或注入恶意 artifacts，这些内容可通过缓存机制传播。这些侧面路径常被模型中心安全审计所忽视，但在实际攻击场景中却是关键的渗透通道。

-   AI 生命周期中入口点的多样性要求安全架构映射所有潜在漏洞，而不仅仅是模型本身。威胁建模必须考虑 adversaries 如何通过数据、基础设施或人员监督缺口影响行为。每个接口、数据集和组件依赖都应被视为潜在入口点，并接受验证、身份验证和异常检测。只有全面理解这些访问点的全貌，组织才能构建能够抵御复杂、多阶段对抗性攻击的有韧性 AI 系统。下图展示了 AI 生命周期的主要阶段以及攻击者可能介入的位置，从数据收集到部署和监控（[Figure 2.1](#c02.xhtml#c02-fig-0001)）。

![Figure 2.1 Adversarial touchpoints in the AI lifecycle.](images/c02f001.png)

Figure 2.1 Adversarial touchpoints in the AI lifecycle.

## Security Debt in the Model Development Lifecycle

Security debt in AI systems accrues much like technical debt in software engineering, but its consequences are often more opaque and harder to unwind. In the race to achieve functional benchmarks, deliver minimum viable models, or deploy next-generation features, organizations frequently defer rigorous security practices in favor of performance metrics or capability milestones. While this may yield short-term wins in innovation velocity, it silently accumulates hidden liabilities across the AI lifecycle. These unresolved liabilities—whether stemming from unvetted data, opaque architectures, or brittle interfaces—tend to mature into critical vulnerabilities when models are exposed to real-world adversarial conditions. The deeper the debt is embedded in foundational layers, the more difficult and expensive it becomes to isolate and neutralize its consequences.

-   一个最早导致 AI 安全债务的因素是未经筛选或文档不全的数据摄入。大规模数据抓取、第三方来源以及低成本标注流水线往往将体量和速度置于来源、完整性和安全审查之上。这种疏忽允许偏见、误标样本，甚至对抗性负载进入训练集，且未被检测。这些缺陷可能在投入生产后很久才显现，进而损害信任、导致模型异常或在特定条件下激活潜在后门。一旦后门嵌入预训练模型并向下游传播，清除它可能需要重新训练——这是一项高成本的 remediation，通常未被预算列入。

-   模型设计选择同样在追求部署便利性而非抗对抗性压力时为安全债务做出重大贡献。开发者常选择复杂架构（如 transformer 或扩散模型）以实现快速部署，却很少在抗规避、中毒或提示操纵方面进行测试。这些架构庞大且不透明，使得失败模式难以识别，为未预见行为提供了肥沃土壤。当对抗鲁棒性未在早期实验阶段评估时，漏洞会保持沉默，直至在运行环境中被利用。此时，缺乏严格的前期红队演练就成为一个显而易见的疏漏，而非无心之举。


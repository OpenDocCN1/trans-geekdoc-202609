
此外，X-Ray 对服务映射的可视化呈现让您能够看到 ML 架构中不同服务之间的交互方式，从而更轻松地识别并解决任何相互依赖关系和性能问题。这种整体视图对于维护 ML 工作流的可靠性和效率至关重要。

### 使用案例

AWS X-Ray 最适用于以下 ML 使用案例：

*   **模型部署追踪**：AWS X-Ray 允许您追踪 Amazon SageMaker AI 部署中各个组件之间的交互，例如数据预处理、模型推理和后处理。这有助于您识别并优化导致延迟的任何阶段。
*   **推理请求追踪**：当向您的 Amazon SageMaker AI 终端节点发出推理请求时，AWS X-Ray 会捕获详细的流程，帮助您诊断与模型服务和响应时间相关的问题。
*   **端到端管道追踪**：对于涉及多个步骤和服务的复杂 ML 管道，AWS X-Ray 可视化整个工作流，使您能够了解不同服务如何交互，并识别任何相互依赖关系或性能问题。

### Amazon GuardDuty

Amazon GuardDuty 是一项威胁检测服务，可对您环境中的 AWS 数据源和日志提供持续监控、分析和处理。

通过利用威胁情报源——包括恶意 IP 地址、域名、文件哈希值和 ML 模型的列表——Amazon GuardDuty 可识别您 AWS 环境中的可疑和潜在恶意活动，包括您的 AWS 账户、您的数据和您的 AWS 资源。

Amazon GuardDuty 会生成一份详细的调查结果报告，您可以使用它来自动化响应。虽然 Amazon GuardDuty 本身不直接执行威胁修复，但它可与其他 AWS 服务无缝集成，以实现对安全威胁的自动化响应。您可以使用以下服务，通过 Amazon GuardDuty 调查结果来自动化响应：

*   `AWS Lambda`
*   `Amazon CloudWatch Events`
*   `AWS Security Hub`
*   `Amazon EventBridge`

这些集成通过确保潜在安全威胁被快速检测和响应，从而帮助保护您的 ML 工作负载，最大限度地降低数据泄露、数据渗漏或未经授权访问您的 Amazon SageMaker AI 环境的风险。

### 使用案例

Amazon GuardDuty 最适用于以下 ML 使用案例：

*   **数据保护**：Amazon GuardDuty 可以检测异常的数据访问模式或从您的 Amazon SageMaker 笔记本或存储中渗漏数据的尝试，帮助保护您宝贵的训练数据和模型工件。
*   **终端节点安全**：对于实时终端节点，Amazon GuardDuty 可以监控 API 调用并检测任何可疑活动，例如未经授权的访问尝试或异常的请求模式。
*   **合规性**：Amazon GuardDuty 通过持续监控潜在威胁和漏洞，帮助确保您的 Amazon SageMaker AI 工作负载符合安全最佳实践和法规要求。
*   **资源完整性**：Amazon GuardDuty 可以检测支持您的 Amazon SageMaker AI 工作负载的底层基础设施中被攻陷的实例或异常行为，确保 ML 环境的完整性和可靠性。

### Amazon Inspector

Amazon Inspector 是一项自动化漏洞管理服务，用于评估 AWS 应用程序（包括支持 ML 工作负载的应用程序）的安全性和合规性。Amazon Inspector 会扫描您的 AWS 资源（如 `Amazon EC2` 实例和容器镜像），以查找漏洞、网络暴露风险以及偏离最佳实践的情况。对于 ML 工作负载，这意味着确保支持您的 Amazon SageMaker AI 环境的基础设施是安全且最新的。通过识别计算资源和容器化环境中的安全风险，Amazon Inspector 有助于维护 ML 模型和工作流的完整性和可靠性。

Amazon Inspector 与 Amazon GuardDuty 之间的一个关键区别在于它们的关注领域和功能。Amazon GuardDuty 专注于持续威胁检测和监控，为可疑活动和潜在安全威胁提供实时警报；而 Amazon Inspector 则专注于漏洞管理和合规性。Amazon Inspector 会定期进行评估，以检测 ML 基础设施中的已知漏洞，例如未修补的软件、薄弱的配置和过时的依赖项。这种主动方法可确保您的 Amazon SageMaker AI 工作负载运行在安全合规的资源上，最大限度地降低因漏洞而被利用的风险。

### 使用案例

对于 ML 使用案例，Amazon Inspector 提供了多项优势，可补充 Amazon GuardDuty 的功能。Amazon Inspector 的评估有助于识别和修复底层基础设施中的安全弱点，确保用于训练和推理的计算环境是安全的。这对于维护训练数据、模型工件和推理结果的机密性和完整性尤为重要。通过将 Amazon Inspector 与 `AWS Lambda` 和 `AWS Systems Manager` 等其他 AWS 服务集成，您可以自动化已识别漏洞的修复，确保 ML 工作负载的持续安全性和合规性。Amazon Inspector 与 Amazon GuardDuty 共同提供了一项全面的安全策略，涵盖了 ML 环境的实时威胁检测和持续漏洞管理。

### AWS Security Hub

AWS Security Hub 是一项集中式云安全态势管理 (CSPM) 服务，可为您提供跨 AWS 环境的安全状态的全面洞察。它汇总、整理并确定来自多个 AWS 服务的安全调查结果的优先级，使您能够从单一位置监控和管理安全问题。对于 ML 工作负载，AWS Security Hub 在确保 ML 模型及其支持基础设施遵循安全最佳实践方面发挥着关键作用。通过与 Amazon GuardDuty、Amazon Inspector 和其他服务集成，AWS Security Hub 提供了安全态势的整体视图，帮助您维护强大且安全的 ML 环境。

AWS Security Hub 加强 ML 工作负载安全态势的主要方式之一，是利用 Amazon GuardDuty 提供的持续威胁检测功能。Amazon GuardDuty 监控可疑活动和潜在安全威胁，例如未经授权的访问尝试和异常的数据访问模式。AWS Security Hub 汇总这些调查结果，为您提供潜在威胁的集中式和优先级视图。这种集成使您能够快速识别并响应可能影响您的 Amazon SageMaker AI 环境的安全事件，确保训练数据、模型工件和推理结果的保护。

除了 Amazon GuardDuty，AWS Security Hub 还与 Amazon Inspector 集成，以增强 ML 工作负载的安全性。Amazon Inspector 执行自动化安全评估，识别计算资源和容器化环境中的漏洞和偏离最佳实践的情况。AWS Security Hub 汇总这些调查结果，并提供可操作的见解，帮助您修复已识别的安全问题。通过持续监控漏洞并与 AWS Security Hub 集成，Amazon Inspector 确保您的 Amazon SageMaker AI 基础设施保持安全合规，降低因未修补的软件或错误配置而导致被利用的风险。

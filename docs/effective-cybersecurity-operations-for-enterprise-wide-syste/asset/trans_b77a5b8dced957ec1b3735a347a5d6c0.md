
# 1. 合规与安全的概念

在探索“合规不等于安全”的概念时，我们只能反思在使用统一框架时，如何更轻松地验证各种控制的有效性。我们认为，一套**风险加权**且被管理的标准与自定义控制，能够在安全方面产生显著效果。此外，我们还将讨论一种判断组织是否具备满足安全目标的控制覆盖程度的方法。

控制是合规与实际安全实现之间的**桥梁机制**。实施一套控制也意味着在治理与风险管理方面具备额外能力。

我们不能忽视统一控制集合能够简化审计及相关证据的收集与验证。我们认为，50-60% 的控制在 NIST、ISO 与其他框架中是共通的，这使得审计成本有可能降低至合并价格的一半。

| Figure 1. Sample services/controls catalog for a medical technology organization |
| --- |
| ![Figure978-1-6684-9018-1.ch005.f01](i/ch005.f01.png) |
| --- |

## CUSTOM CONTROLS TO CONSIDER

在审阅上述示例安全控制目录后，我们发现部分控制直接来源于 ISO、NIST 或 HIPAA，约 20% 为自定义控制。它们的开发是为了正式化特定功能的实现、确保问责性并监控其有效性。组织因缺乏某些控制或对现有控制的错误解读而陷入常见漏洞。例如：

*   ● **SQL Injection**：未使用参数化查询。最常见的防护做法是封装并参数化 SQL 命令。参数化查询将 SQL 语句与用户输入分离，输入被视为字面值并进行类型与长度检查，从而无法包含可执行代码。

*   ● **Cross Site Scripting (XSS)**：未对数据进行**上下文敏感**转义。

*   ● **Cross Site Request Forgery (CSRF)**：未在状态变更的请求上使用令牌。

*   ● **Direct Object Reference (DOR)**：未严格验证直接对象引用。当应用使用内部对象引用时，可能泄露真实标识及其后端格/模式。

通过建立自定义控制来执行**静态或动态代码分析**，或强制使用 **Struts Validator、Java Cryptography Extension、ESAPI Encoder** 等工具，能够显著降低上述漏洞的暴露风险。经过评估相关框架后，我们建议某些控制在主流框架中**不足或完全缺失**。因此，任何组织均应考虑实施针对性的自定义控制：

这些控制包括：

*   ● **Contingency Planning**：未发现框架强制要求业务恢复与应急计划的制定、开发与验证。

*   ● **Information Security Management**：威胁如何被识别并关联到修复措施。

*   ● **Skills and Training**：需维持的能力以及其来源。

*   ● **Governance**：安全策略及其他管理事项的处理方式。

*   ● **Risk Management**：已识别问题的管理、 remediation 与报告方法，以及风险评估的具体流程。

*   ● **Access Management**：不同特性之间的关联及其对应用、数据集与资产访问的影响。

*   ● **Cyber Insurance**：关于网络责任保险的建议或情景。

*   ● **Cloud Service Operations**：在分权安全模型、多租户利用、临时设施以及软件部署的网络方面的控制。

*   ● **Web Application or Other Firewall (WAF)**：使用 WAF 处理动态应用安全问题及传统防火墙的其他用途。

*   ● **Data Loss Protection**：实现该特性或采用替代的 IDS/IPS 方案。

*   ● **Ransomware Protection**：保护或阻止勒索软件攻击的方法。

*   ● **Email Security**：加密、防伪、数字签名等邮件保护措施。

*   ● **Multi-Factor Authentication**：包含传统 MFA 以及硬件认证或提权管理的组合控制。

*   ● **Third Party Library Management**：针对第三方软件（开源、固件、硬件组件）的控制。

*   ● **File Management**：监控与验证关键文件的控制。

部分上述控制已纳入 ISO 或 NIST 框架或其特定指南，但它们往往未被明确强制或缺乏专门的部署与管理控制。

## CONTROL SUFFICIENCY

确定“足够多少控制”是一项**风险识别与管理**的工作。只有在明确、量化安全需求后，才能配备适当的控制。最低限度上，组织需识别关键资产并建立相应的控制。

为阐明可适用的风险，组织常使用**威胁模型**等方法。同时，还存在组织主动接受的**残余风险**，这些风险可被记录并随时管理。

> **Adequate security** is defined as: “The condition where the protection and sustainability strategies for an organization's critical assets and business processes are commensurate with the organization's tolerance for risk” ([Augustine & Millstein, 2023](#978-1-6684-9018-1.ch005.xhtml#r2))。  
> 首先建立资产列表，以判断已实施的控制是否足够。资产包括**知识产权、数据、技术、服务器、设施**以及诸如**知识、合同**等无形资产。

组织的**风险容忍度**是接下来需要定义的变量。它会影响预算、人员配置、运营及其他业务方式，且可能随组织绩效、合作伙伴等因素而变化。制定风险容忍度既是质量也是量化度量，可通过一系列**事件/结果/影响**陈述来建立。例如，引入由客户服务组织支持的新应用。

当前应用已建立**请求响应时间**与**响应准确性时间**，组织希望保持这些指标。为实现目标，管理层需分配资源、流程与技术。在分配资源后，组织必须决定可接受的**变动范围**。例如，响应时间延迟两小时是否可接受？若响应准确率下降 10%，对声誉与客户满意度会产生什么影响？

将上述思维过程延伸至安全领域，会提出两个核心问题——“**控制数量是否足够？**”以及紧密相关的“**我需要承担什么损失？**”。通过类似的分析过程，可得到可接受的答案。

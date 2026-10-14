

# 私有连接选项

私有连接选项（例如 `VPC interface endpoints` 和 `gateway endpoints`）通过启用到 AWS 服务的私有连接（无需遍历公共互联网），进一步增强了 ML 基础设施的安全性。VPC 接口终端节点使用 AWS PrivateLink 在您的 VPC 内创建到 AWS 服务（如 Amazon S3 和 Amazon SageMaker AI）的私有连接。但是，AWS PrivateLink 不仅限于到 AWS 服务的私有连接。借助这项服务，您还可以跨不同的 VPC 和 AWS 账户创建到用户定义服务的私有连接，从而在不将流量暴露给公共互联网的情况下实现服务的安全共享。这种方法通过确保流量保留在 AWS 网络内，降低了数据泄露的风险并提高了数据安全性。同样，VPC 网关终端节点为可通过 AWS 管理控制台、API 和 CLI 访问的 AWS 服务（如 Amazon S3 和 Amazon DynamoDB）提供私有连接。通过使用网关终端节点，您可以确保 VPC 与这些服务之间的数据流量安全且私密。

## 数据保护

除了网络和安全隔离之外，对静态数据、使用中数据和传输中数据实施加密以保护敏感 ML 数据至关重要。AWS KMS 允许您创建和管理加密密钥，这些密钥可用于加密存储在各种 AWS 服务（如 Amazon S3、Amazon RDS 和 Amazon EBS）中的数据。此外，AWS 为传输中的数据提供 SSL/TLS 加密，确保数据在 ML 基础设施与其他 AWS 服务或外部系统之间传输时保持安全。

ACM 进一步简化了为您的网站和应用程序预置、管理和部署 SSL/TLS 证书的过程。您可以使用 ACM 轻松获取和续订证书，并确保 ML 基础设施与用户或其他系统之间的通信安全。实施加密有助于维护 ML 数据的机密性和完整性，防止未经授权的访问和篡改。

## 监控和审计

监控和审计也是保护 AWS 中 ML 基础设施的重要组成部分。正如您在 [第 7 章](#c007.xhtml#c007) 中所了解的，AWS 提供了多种服务（如 AWS CloudTrail 和 Amazon CloudWatch），帮助您监控和记录 VPC 及 ML 基础设施内的活动。AWS CloudTrail 使您能够跟踪 API 调用和用户活动，提供详细的审计追踪，可用于合规性和安全分析。Amazon CloudWatch 允许您收集和监控指标、设置警报，并深入了解 ML 基础设施的性能和运行状况。借助这些监控和审计工具，您可以主动检测并响应安全事件，确保 ML 工作流的持续保护和完整性。

# 确保合规性

Amazon SageMaker AI 旨在满足各种行业标准和法规要求，使其成为具有严格合规需求的组织的合适选择。在美国，Amazon SageMaker AI 支持符合《健康保险流通与责任法案》(HIPAA)，这对于处理敏感医疗数据至关重要。这确保了医疗保健行业的组织能够在遵守 HIPAA 严格的隐私和安全规则的前提下，安全地管理和分析患者信息。

Amazon SageMaker AI 支持的另一个关键合规框架是支付卡行业数据安全标准 (PCI DSS)。该标准对于处理支付卡信息的组织至关重要，因为它规定了保护持卡人数据的要求。通过遵守 PCI DSS，组织可以确保其涉及支付数据的 ML 工作流安全且符合行业标准。

此外，Amazon SageMaker AI 符合 ISO 27001，这是一项信息安全管理体系的国际标准。该认证表明 Amazon SageMaker AI 遵循管理信息安全的最佳实践，包括风险评估、管理和持续改进。符合 ISO 27001 确保组织可以信任 Amazon SageMaker AI 来保护其数据并维护强有力的安全措施。

除了这些框架之外，Amazon SageMaker AI 还支持符合其他多项法规标准，包括 SOC 1、SOC 2、SOC 3、FedRAMP、GDPR 等。这一广泛的合规认证范围使 Amazon SageMaker AI 成为适用于各个行业的通用且安全的平台，确保组织在利用先进 ML 功能的同时能够履行其法规义务。

您可以利用 AWS Artifact 获取第三方认证和报告，以验证您针对上述框架的合规状态。

有关 Amazon SageMaker AI 支持的合规框架的更多详细信息，请访问 `https://docs.aws.amazon.com/sagemaker/latest/dg/sagemaker-compliance.html` 上的 Amazon SageMaker AI 合规验证页面。

有关安全合规最佳实践，请访问 `https://docs.aws.amazon.com/config/latest/developerguide/security-best-practices-for-SageMaker.html` 上的 Amazon SageMaker AI 安全最佳实践页面。

# 总结

在本章中，您了解了使用 Amazon SageMaker AI 保护 ML 模型的重要性以及实现这一目标所涉及的各个方面。保护 ML 模型需要一种整体方法，该方法利用安全设计策略，而该策略建立在最小权限、职责分离和纵深防御等安全设计原则之上。这些原则确保用户和应用程序仅拥有必要的权限，实施多层安全防护，并从一开始就将安全控制集成到架构中。

管理身份和访问控制对于保护 Amazon SageMaker AI 中的 ML 资源至关重要。AWS IAM 允许您创建和管理策略，以定义用户、组和角色的权限，确保只有授权用户才能访问特定的 Amazon SageMaker AI 资源。实施 MFA 可增加一层额外的安全性，而创建权限边界和 SCP 有助于实施组织安全策略并限制对关键资源的访问。这确保了您的 ML 身份得到安全有效的管理。

保护支持 ML 工作流的基础设施涉及实施网络隔离并使用适当的安全控制。VPC 提供网络隔离，而 NACL 和安全组充当防火墙，在子网和实例级别控制流量。私有连接选项（如 VPC 接口终端节点和网关终端节点）可实现到 AWS 服务的安全连接，而无需将数据暴露给公共互联网。监控和日志记录服务（如 AWS CloudTrail 和 Amazon CloudWatch）可帮助您跟踪和审计网络活动，确保潜在的安全事件得到及时检测和处理。

最后，保护数据和确保合规性是保护 ML 模型和工作流的关键方面。AWS KMS 允许您创建和管理加密密钥以加密静态数据，而 SSL/TLS 加密确保传输中的数据保持安全。ACM 简化了预置、管理和部署 SSL/TLS 证书的过程。Amazon SageMaker AI 支持各种合规框架，包括 HIPAA、PCI DSS、ISO 27001、SOC 1、SOC 2、SOC 3、FedRAMP 和 GDPR，确保您的 ML 环境遵守相关的行业标准和数据驻留法规。通过解决上述每个领域的问题，您可以使用 Amazon SageMaker AI 构建安全合规的 ML 基础设施，保护您的模型、基础设施和数据免受潜在威胁和漏洞的影响。

# 考试要点


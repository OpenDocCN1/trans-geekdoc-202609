

![](img/4b11e95292819ab1a383a41ef73aedb4_193_0.png)

## 统一终端检测与响应 (EDR)

Microsoft Defender Advanced Threat Protection (Microsoft Defender ATP) 是一个统一的安全平台，为 Windows 客户端、Windows Server 以及 Mac OS 等第三方系统提供终端保护平台 (EPP) 和终端检测与响应 (EDR) 能力。在 Windows Server 中，Microsoft Defender ATP 与 Azure Security Center 深度集成，确保组织能够最大限度地利用现有的 Microsoft 安全投资。通过这种深度集成，客户可以受益于支持的 Windows Server 到 Microsoft Defender ATP 的自动入 {体验。

这使得安全分析师能够查看整个环境，而无需在调查期间在门户之间切换。因此，Microsoft Defender ATP 与 Azure Security Center 的集成有助于组织发现异常。此外，组织还可以检测并响应针对 Azure Security Center 监控的服务器终端的高级攻击。

Milad Aslan，Microsoft Defender ATP 研发部高级安全计划经理

## 与 Microsoft Cloud App Security 的集成

与 Microsoft Cloud App Security (MCAS) 的集成使 Security Center 能够接收用户行为异常、用户和实体行为分析以及机器学习 (ML) 的警报。通过这种集成，您可以获得即时检测，针对与您的订阅相关的用户和资源中的众多异常。

此外，这些警报利用了 MCAS 检测引擎中已存在的额外数据，有助于加速调查过程并控制正在发生的威胁。要启用此集成，请遵循以下步骤：

1. 打开 Security Center 仪表板。
2. 在左侧格的**策略与合规**(Policy & Compliance)下，点击**安全策略**(Security Policy)。
3. 对于您想要启用此集成的订阅，点击**编辑设置**(Edit settings)。
4. 在**设置**(Settings)下，点击**威胁检测**(Threat Detection)：将出现**启用集成**(Enable Integrations)窗格。
5. 选择**允许 Microsoft Cloud App Security 我的数据**(Allow Microsoft Cloud App Security To Access My Data)选项并点击**保存**(Save)。

此集成将允许以下警报出现在 Security Center 的安全警报仪表板中：

- 不可能的旅行 (Impossible Travel)
- 来自不常用国家的活动 (Activity From Infrequent Country)
- 来自匿名 IP 地址的活动 (Activity From Anonymous IP Address)

图 9-4 显示了第一种场景（不可能旅行）中的警报流示例，以及它如何在 Security Center 中显示。

![](img/4b11e95292819ab1a383a41ef73aedb4_194_0.png)

**图 9-4** MCAS 与 Security Center 之间的警报流

在图 9-4 所示的示例中，MCAS 识别出两个来自地理遥远位置（巴西和美国）的用户活动（在单个或多个会话中）。这些活动发生的时间短用户从第一个位置到第二个位置所需的时间。这表明另一个用户正在使用相同的凭据，被解释为凭据已破解。此检测利用了机器学习算法，会忽略明显的假报，例如 VPN 和组织中其他用户使用的位置。

您也可以直接在工作区中搜索由 MCAS 生成的警报。使用图 9-3 显示的 Kusto 查询示例执行此任务，但将提供程序名称从 WATP 更改为 MCAS。

## SQL ATP 集成

Security Center 与 SQL 高级威胁保护 (ATP) 的集成提供了新层安全防护，帮助客户检测并响应潜在威胁，例如可疑数据库活动、潜在漏洞和 SQL 注入攻击，以及异常的数据库访问和查询模式。

这种集成使得处理数据库潜在威胁变得简单，而无需成为专家或管理高级安全监控系统。当启用 SQL ATP 时，将提供以下警报：

- **SQL 注入漏洞 (Vulnerability To SQL Injection)**：此警报可能指示可能受 SQL 注入攻击的漏洞。
- **潜在的 SQL 注入 (Potential SQL Injection)**：当针对已识别的 SQL 注入漏洞发生活跃的利用时，会触发此警报。
- **来自异常位置的访问 (Access From Unusual Location)**：当 SQL 服务器的访问模式发生变化时，触发此警报；例如，当有人从异常的地理位置登录到 SQL 服务器时，就会触发此警报。
- **来自异常 Azure 数据中心的访问 (Access From Unusual Azure Data Center)**：这是另一个根据 SQL 服务器访问模式变化而触发的警报。然而，在这种情况下，它是当有人从近期未出现的异常 Azure 数据中心登录到 SQL 服务器时发生的。
- **来自未知主体的访问 (Access From Unfamiliar Principal)**：这是另一个根据 SQL 服务器访问模式变化而触发的警报，但该场景适用于有人使用异常的主体（SQL 用户）登录到 SQL 服务器的情况。
- **访问潜在有害的应用程序 (Access A Potentially Harmful Application)**：当使用潜在有害的应用程序访问数据库时，触发此警报。
- **暴力破解 SQL 凭据 (Brute Force SQL Credentials)**：当使用不同凭据的失败登录次数异常高时，触发此警报。

图 9-5 显示了此类警报的示例；在此情况下，显示了潜在的 SQL 注入检测。

## 潜在的 SQL 注入

![](img/4b11e95292819ab1a383a41ef73aedb4_196_0.png)

图 9-5 由 SQL ATP 生成并在 Security Center 中显示的警报

要启用此功能，您需要在订阅中启用 SQL Server 监控，这将产生额外费用。遵循以下步骤：

1. 打开 Security Center 仪表板。
2. 在左侧格的策略与合规(Policy & Compliance)下，点击安全策略(Security Policy)。
3. 对于您想要启用此集成的订阅，点击编辑设置(Edit settings)。
4. 在设置(Settings)下，点击定价分层(Pricing Tier)。
5. 按资源类型选择定价分层以展开此选项，并点击 SQL 服务器的启用切换，如图 9-6 所示。

![](img/4b11e95292819ab1a383a41ef73aedb4_196_1.png)

图 9-6 在定价分层中启用 SQL ATP

6. 点击保存(Save)。

## 与 Azure Storage ATP 的集成

Security Center 与 Azure Storage 高级威胁保护 (ATP) 的集成与 SQL ATP 的集成非常。您还需要在定价分层中手动启用此功能并为此额外付费。您可以使用用于启用 SQL ATP 的相同步骤，并将看到启用存储帐户的选项。为了生成警报，Azure Storage ATP 会摄取 Blob 存储读取、写入删除请求的诊断日志进行威胁检测。

当您启用 Azure Storage ATP 时，您可以在以下条件下识别攻击：

- 当存储账户的访问模式发生变化时
- 与此存储帐户最近的活动相比，提取的数据量异常庞大时
- 当存储账户中发生意外删除时
- 当发生异常的存储枚举时
- 当存储账户发生常规更改时

图 9-7 显示了 Azure Storage ATP 生成的警报类型示例。

![](img/4b11e95292819ab1a383a41ef73aedb4_197_0.png)

# 图 9-7 由 Azure Storage ATP 生成并在 Security Center 中保护的警报

此类警报在 Azure 存储账户的访问模式发生变化时生成。例如，当有人从异常的地理位置访问存储账户时，就会生成此类警报。可能的原因包括：

- 攻击者访问了您的存储账户。
- 合法用户从新位置访问了您的存储账户。




```json
  "startTimeUtc": "2019-03-18T12:34:52.0616273Z",
  "endTimeUtc": "2019-03-18T12:34:52.0616273Z",
  "type": "host-logon-session",
  "host": {
    "$ref": "centralus_1"
  },
  "account": {
    "$ref": "centralus_3"
  }
}
```

如你所见，通过 REST API 获取告警时，可以获取大量信息。虽然安全中心（Security Center）安全告警仪表板提供了告警的重要细节，但 REST API 为消费同一数据集提供了一个不同的视角。

# 使用 Security Graph API 访问告警

Microsoft Graph (graph.microsoft.com) 是访问 Microsoft 在线服务（如 Azure Active Directory、Office 365 等）信息的统一接口。Security Graph API 基于 Microsoft Graph，可以定义为用于集成安全产品的统一 REST API。

当你调用 Graph Security API 时，这些调用将联邦到所有支持的 Microsoft 安全产品、服务合作伙伴。结果被聚合在通用模式中，这使得关联来自多个数据源的告警变得更容易。其理念是，当你连接并丰富告警时，将能够轻松理解攻击的范围和影响。

# 简化 Microsoft Graph Security API 的集成

今天，大多数组织依赖一组安全工具来管理和响应网络威胁。这包括工单、调查和自动化系统等。通过将 Azure Security Center 与这些工具和工作流集成，你可以简化安全操作并提高威胁响应。

Microsoft Graph API 为集成 Microsoft 及其合作伙伴的安全解决方案提供了统一接口和标准模式。通过一个身份验证密钥连接到一个端点，组织可以极大简化告警管理。调用一次 Microsoft Graph Security API 即可返回来自 Azure Security Center、AD Identity Protection、Azure Information Protection、Microsoft Cloud App Security 以及 Office365、Windows 和 Azure Advanced Threat Protection 的告警。组织还可以使用 Microsoft Graph Security API 更新告警状态。例如，当你在集成应用程序中关闭 Azure Security Center 警时，它将在 Azure Security Center 中显示为已忽略（dismissed）。

组织可以通过 API 或使用 PowerShell 脚本直接连接到 Microsoft Graph Security API。来自 Azure Logic Apps、Microsoft Flow、PowerApps 和 Power BI 的连接器为自动化和报告提供了无代码选项。Azure Notebooks 示例提供了在 Jupyter notebooks 中分析告警数据的简单方法。此外，还支持通过 Azure Monitor 进行 SIEM 集成。

访问 aka.ms/graphsecurityapi 了解更多关于利用 Microsoft Graph Security API 将 Azure Security Center 告警集成到你的安全工具和工作流的信息。

Sarah Feder，Graph Security API 团队首席小组经理

图 10-2 显示了可用于 Graph Security API 的不同组件的表示。

| 应用 | Web 应用程序 | 设备和原生应用 | 机器人 | 后台进程 | 分析仪表板和工具 | 自动化工作流 |
|---|---|---|---|---|---|---|

| 通用库、身份验证和授权 | | | | | | |
| Microsoft Graph | 告警 | 安全存储 (Secure Store) | 指示器 (Indicators) | 操作 (Actions) | 其他 Graph 服务 (Azure AD, O365, SharePoint, Intune...) | |
|---|---|---|---|---|---|---|

| Graph Security API - 联邦查询、聚合结果、应用通用模式 | | | | | | | |
| 安全提供商 | Windows Defender ATP | Office 365 ATP | Azure ATP | Azure Identity Protection | Cloud App Security | Azure Security Center | Azure Information Protection | Azure Sentinel |
|---|---|---|---|---|---|---|---|---|

**图 10-2** Graph Security API 架构图

从该图顶部看，你可以看到顶部的应用基本上是在消费数据。你可以创建自己的应用来消费位于第三层（安全提供商）的 Microsoft 安全产品数据。中间接口（Microsoft Graph）是 Security Graph API 所在的位置。注意在这一层中，Security Graph API 除了检索告警和设置告警操作外，还有许多其他功能。这些选项超出了本书的范围，但如果你想了解更多关于 Security Graph API 的用法，请访问 https://aka.ms/securitydocs。

在查看此图后，你还可以看到 Security Graph API 是一个中间服务（代理），提供单一的编程接口来连接多个安全提供商（Microsoft 及其合作伙伴）。在计划构建自己的应用来使用 Graph Security API 时，请确保涵盖以下几点：

-   在 Microsoft Graph 中注册你的应用：登录 portal.azure.com 将应用添加到 Azure AD 租户中。
-   指定权限和密钥：如果你的应用以登录用户的身份访问 API，可以使用 Delegated（委派权限）；如果你的应用有自己的基于角色的访问控制 (RBAC)，则可以使用 Application（应用程序权限）。
-   编写你的代码：你可以从利用 http://aka.ms/graphsecurityapicodeget示例代码开始。
-   获取使用你应用的组织的许可：在此步骤中，Azure AD 管理员需要授权组织（租户）使用该应用。

# 使用 Security Graph API

Security Graph API可以通过 Microsoft Graph 访问；换句话说，它使用单一连接点 (https://graph.microsoft.com)，具有相同的语法 REST API 和 JSON 格式的响应。通过 Security Graph API 访问的安全数据受权限和 Azure AD (AAD) 角色的保护。要使用 Security Graph API 从 Security Center 获取告警，你需要使用类似示例的 HTTP GET 请求：

https://graph.microsoft.com/v1.0/security/alerts

此 GET 请求的一个重要方面是，它将检索租户中可能存在的所有提供商的告警，包括 Azure Security Center、Azure Active Directory Identity Protection、Microsoft Cloud App Security、Windows Defender Advanced Threat Protection、Azure Advanced Threat Protection、Office 365、Cloud App Security、Azure Information Protection（预览）、Azure Sentinel 以及你可能访问的其他合作伙伴提供商（如 Palo Alto Networks）。

取决于你拥有的服务提供商数量，通过简单的 GET 请求获取所有告警返回的数据量可能是巨大的。使用过滤器来针对你真正想要看到的信息是一个好主意。例如，如果你只想查看前 10 个高严重告警，可以使用下面的 GET 请求：

https://graph.microsoft.com/v1.0/security/alerts?$filter=severity eq 'High'&$top=10

URL 中加粗的部分代表了为仅检索所需信息而创建的过滤器。如果你想在开始编写应用之前验证你的 GET 请求，可以使用 Microsoft Graph Explorer (https://developer.microsoft.com/en-us/graph-explorer) 测试 URL。对于此示例，你将获得一个列出前 10 个高严重告警的结果。虽然此过滤器有所帮助，但它仍会显示你访问的所有安全提供商的 10 个高严重告警。如果你想查看由 Security Center 生成的告警，可以使用 `vendorInformation` 属性按供应商进行过滤，如示例所示：

```
https://graph.microsoft.com/v1.0/security/alerts?$filter=vendorInformation/provider eq='ASC'
```

如果你登录到带有 Security Center 的订阅并使用 Microsoft Graph Explorer 此 GET 请求，该请求将仅检索安全提供商为 Security Center 的告警（见图 10-3）。

![](img/4b11e95292819ab1a383a41ef73aedb4_206_0.png)

图 10-3 Graph Explorer

你还可以使用逻辑运算符来扩展查询。例如，如果你只想查看 Security Center 生成的高严重告警，可以使用以下 GET 请求。（注意加粗字符串的添加）。

```
https://graph.microsoft.com/v1.0/security/alerts?$filter=vendorInformation/provider eq='ASC' and Severity eq 'High'
```



结果将以表格形式显示在页面底部，如图 8-7 所示。

![](img/4b11e95292819ab1a383a41ef73aedb4_172_0.png)

图 8-7 查询结果

> 注意：如果你想了解如何模拟警报并使用 Kusto 查询语言进行调查的引导示例，请从 `http://aka.ms/ascplaybooks` 下载《威胁猎寻手册》。

## 与 Splunk 集成

配置过程并非易事。这里有很多步骤，你必须确保每一步都是正确的。图 8-8 提供了解决方案整体架构的高级视图。解决方案的关键启用功能包括 Azure Event Hub、Azure Monitor 以及安全信息和事件管理（SIEM）连接器插件，该插件允许 SIEM 轮询事件枢纽将信息引入本地 SIEM。

![](img/4b11e95292819ab1a383a41ef73aedb4_173_0.png)

图 8-8 IoT 设备的安全警报

Splunk 集成涉及以下过程：
1. 确认 Azure Monitor 中有可访问日志。
2. 在订阅中为 SIEM 管道配置所需的权限。
3. 为 SIEM 管道创建并配置资源组。
4. 设置 Azure AD 以提供访问控制身份。
5. 创建密钥库以存储凭据。
6. 将应用程序密码放入密钥库。
7. 创建一个事件枢纽（event hub）。
8. 为事件枢纽访问控制创建共享访问密钥。
9. 将事件枢纽共享访问密钥放入 Azure Key Vault。
10. 将事件枢纽连接到 Azure Monitor。
11. 启动托管 Splunk 企业级虚拟机的虚拟机。
12. 安装并配置用于 Splunk 的 Azure Monitor 插件。

在开始之前，你需要确保已具备集成的先决条件。所需的组件如下：

- 一个 Azure 订阅（具有管理权限）
- 包含所需资源的资源组
- 用于服务访问的 Azure Active Directory (AAD) 应用程序
- 用于存储所需凭据的密钥库
- 一个事件枢纽命名空间（事件枢纽将根据需要自动创建）
- 一个 Splunk 服务器（在云端或本地）
- 用于从事件枢纽读取日志的 Microsoft Splunk 插件

### 确认 Azure Monitor 中的可访问日志

要确认 Azure Monitor 中有可访问日志，打开 Azure 门户的**监控（Monitor）**窗格，并点击**活动日志（Activity log）**。运行简单的查询以确认数据是否可用（见图 8-9）。

![](img/4b11e95292819ab1a383a41ef73aedb4_174_0.png)

**图 8-9** 监控窗格中的活动日志选项。

### 为 Splunk SIEM 管道配置订阅

如果你已有一个订阅，请确保你拥有所有者（Owner）、管理员（Administrator）或共同管理员（Co-Administrator）权限。如果没有，请请求该订阅的权限以创建管道。在本例中，订阅名为 `ContosoSub`。

### 为 Splunk SIEM 管道创建并配置资源组

要为 Splunk SIEM 管道创建并配置资源组，请按照以下步骤操作：

1. 打开 Azure 门户的**资源组（ResourceGroup）**窗格。确认顶部过滤器中选择了 SIEM 管道的订阅（在本例中为 `ContosoSub`）。
2. 点击顶部的“添加（Add）”按钮（见图 8-10）。将打开一个新窗格并允许你配置资源组（见图 8-11）。
3. 输入唯一的资源组名称（例如 `SiemPipeRG`）。
4. 点击订阅下拉菜单并选择所需的订阅（在这种情况下为 `ContosoSub`）。

![](img/4b11e95292819ab1a383a41ef73aedb4_174_1.png)

图 8-10 在资源组窗格中点击“添加”按钮。

5. 点击资源组位置下拉菜单，为你的资源组选择位置。（我们建议将此例中的所有资源放在相同的位置。）
6. 点击底部的“创建（Create）”按钮保存更改。

![](img/4b11e95292819ab1a383a41ef73aedb4_175_0.png)

### 设置 Azure AD 应用程序提供访问控制

你必须设置 Azure Directory (AAD) 应用程序以提供可用于解决方案的身份。按照以下步骤操作：

1. 打开 Azure 门户的 Active Directory 窗格，并点击应用注册（App registrations）（见图 8-1）。

![](img/4b11e95292819ab1a383a41ef73aedb4_175_1.png)

2. 点击顶部的“新注册（New registration）”（见图 8-2）。

3. 在创建窗格中，输入你的应用程序名称——例如，`contoso.example`。
4. 在类型（Type）下拉菜单中选择 Web/API。
5. 在登录 URL（Sign-on URL）中输入 `https://contoso.example`。
6. 点击底部的“创建（Create）”按钮创建应用程序。

![](img/4b11e95292819ab1a383a41ef73aedb4_176_0.png)

图 8-2 创建注册。

7. 在 Active Directory 窗格中，再次点击应用注册（App Registrations）（见图 8-3）。

![](img/4b11e95292819ab1a383a41ef73aedb4_176_1.png)

图 8-3 应用注册。

8. 在搜索框中输入你刚刚创建的应用名称（如例所示），找到后点击该应用。
9. 点击密钥（Keys）（见图 8-4）。

![](img/4b11e95292819ab1a383a41ef73aedb4_176_2.png)

图 8-4 选择密钥。

注意：如果你没有该选项，说明你不是密钥的管理员。如果你不是管理员，请联系管理员并请求权限。

10. 在图 8-5 所示的密钥窗格中，在描述字段为密钥输入描述性名称——例如，`apppass`。

![](img/4b11e95292819ab1a383a41ef73aedb4_177_0.png)

图 8-5 创建密钥。

11. 在过期（Expires）框中选择密钥有效期。
12. 点击密钥窗格顶部的“保存（Save）”。
13. 复制值（Value）列中 Base64 字符串值。你将在下一节中将此值存入密钥库。

重要：点击“保存”后，请快速复制 Base64 字符串值（以存入密钥库）。当你离开此页面后，该值将隐藏且无法通过 UI 检索。在本章后续内容中，我们将此密钥称为“AppPassword”。

### 创建 Azure 密钥库

Azure Active Directory 应用程序需要身份凭据。这些凭据存储在密钥库中以优化安全性。按照以下步骤操作以创建密钥库：

1. 打开 Azure 门户的密钥库（Key Vault）窗格。确认顶部过滤器中选择了 SIEM 管道的订阅（在本例中为 `ContosoSub`）。
2. 点击顶部的“添加（Add）”按钮。

![](img/4b11e95292819ab1a383a41ef73aedb4_177_1.png)

图 8-18 在 Azure 门户中点击“添加”。

3. “创建密钥库”（Create Key Vault）窗格如图 8-19 所示打开。

![](img/4b11e95292819ab1a383a41ef73aedb4_178_0.png)

图 8-19 创建密钥库。

4. 为密钥库输入一个名称，例如 `SiemPipeKV`，然后选择所需的订阅，例如 `ContosoSub`。

5. 点击“使用现有”（Use Existing）按钮，并选择您在本节较之前创建的 `SiemPipeRG` 资源组。

6. 在“位置”（Location）下拉菜单中，选择资源组所在的位置。

7. 选择此密钥库的定价层级。在我们操作的示例中，标准（Standard）和高级（Premium）层级选项均可用。我们建议使用高级层级以更多功能。

8. 点击“访问策略”（Access policies）按钮，这将打开访问策略窗格。

9. 点击“新建”（Add new）按钮，如图 8-20 所示。

![](img/4b11e95292819ab1a383a41ef73aedb4_179_0.png)

图 8-20 点击“新建”按钮以配置密钥库的特权访问。

10. 打开**访问策略**（Access Policies）窗格，其中具有额外的配置功能，允许您配置密钥库的特权访问，如图 8-21 所示。

![](img/4b11e95292819ab1a383a41ef73aedb4_179_1.png)

图 8-21 配置新的访问策略

11. 为了确保您创建的 AAD 应用具有访问此密钥库的权限，打开“从模板配置”（Configure from template）下拉菜单并选择“密码与证书管理”（Secret & Certificate Management）。

12. 点击“选择主体”（Select Principal）按钮。（主体是指可以配置访问权限的 AAD 实体。）

13. 打开“主体”（Principal）窗格。在“选择”（Select）框中，输入您的 AAD 应用名称——在此例中为 `contoso.siem.example`——点击窗格底部的“选择”（Select）按钮，如图 8-22 所示。

![](img/4b11e95292819ab1a383a41ef73aedb4_180_0.png)

图 8-22 选择主体

14. 点击“添加访问策略”窗格底部的“创建”（Create）按钮，然后点击“创建密钥库”窗格底部的“创建”（Create）按钮。

### 将应用密码复制到密钥库

现在我们已经有了一个密钥库，可以将密钥放入其中。按照以下步骤执行此操作：

1. 打开密钥库窗格，并确认顶部过滤器中已选择用于 SIEM 管道的订阅（在本例中为 `ContosoSub`）。
2. 选择 `SiemPipeKV` 密钥库。
3. 点击如图 8-23 所示的“机密”（Secrets）选项。

![](img/4b11e95292819ab1a383a41ef73aedb4_180_1.png)

图 8-23 点击“机密”按钮开始将密钥放入密钥库的过程。

4. 在“机密”窗格中，点击顶部的“添加”（Add）。
5. 打开“创建机密”窗格（见图 8-24）。
6. 在“上传选项”（Upload Options）下拉菜单中，选择“手动”（Manual）。
7. 在“名称”（Name）字段中，为机密输入名称——例如 `AppPassword`。
8. 在“值”（Value）字段中，粘贴从 Azure Active Directory 账户过程中复制的值。我们使用的值是 `AppPassword`。
9. 在“内容类型”（Content Type）字段中，输入 `text/plain`。确保您输入的内容与编写完全一致；它是区分大小写的。取消勾选“设置操作日期”（Set Action Date）和“设置过期日期”（Set Expiration Date）复选框。
10. 确认“启用”（Enabled）已设置为“是”。
11. 点击窗格底部的“创建”（Create）按钮。

![](img/4b11e95292819ab1a383a41ef73aedb4_181_0.png)

**图 8-24** 输入信息以创建机密

### 创建事件枢

此时，我们已经有了一个身份和一个机密。现在让我们创建一个用于支持 SIEM 管道的事件枢。

1. 转到**事件中心**Event Hubs）窗格。确认顶部过滤器中已选择用于 SIEM 管道的 `ContosoSub` 订阅。
2. 点击屏幕顶部的“添加”（Add）按钮。
3. 打开“创建命名空间”（Create namespace）窗格以便您创建事件枢命名空间。（见图 8-25）为事件枢输入名称——例如 `contosiem-ns`。
4. 根据您的吞吐量需求选择定价层级。
5. 选择 `ContosoSub` 订阅。
6. 在“资源组”部分选择“使用现有”（Use existing），然后选择 `SiemPipeRG` 组。
7. 选择资源组的位置。
8. 根据您预期的报告负载选择所需的吞吐单元数。从 1 开始，如果以后需要则增加此值。
9. 如果您希望 Azure 根据吞吐量负载管理事件枢的规模，请选择“启用自动扩缩”（Enable auto-inflate）。如果您勾选了该框（如图像所示），则需要指定一个上限（最大）吞吐单元数以自动创建（向外扩展）。允许的最大值是每个事件枢命名空间 20 个。您可以保持默认。

图 8-25 创建命名空间

### 准备供 Splunk 使用的虚拟机

从 Azure 平台的角度，配置已经完成，现在你只需要提供一个托管 Splunk 企业版 VM 的虚拟机。按照以下步骤创建此虚拟机：

- 1. 转到 Azure 门户的虚拟机（Virtual Machine）窗格并点击 Add（添加）按钮，将打开计算（Compute）窗格。
- 2. 在搜索框中输入 Splunk enterprise 并选择 Splunk Enterprise 模板 VM，如图 8-32 所示。

![](img/4b11e95292819ab1a383a41ef73aedb4_187_0.png)

图 8-32 选择 Splunk Enterprise。

- 3. 仔细阅读文档并按照详细说明设置任何所需的许可证。
- 4. 准备就绪后点击 **Create**（创建）。
- 5. 在 **Basic**（基本）页面，选择虚拟机用户名和密码。我们建议你选择 **Store All Passwords In Key Vault**（将所有密码存储在密钥保管库中）。
- 6. 为 SIEM 管道选择 **Contosub** 订阅。
- 7. 在 **Resource Group**（资源组）下，点击 Create New（新建）按钮。
- 8. 将新资源组命名为 `SiemPipeSplunkVMrg`。
- 9. 打开位置下拉菜单，选择与资源组关联的位置。
- 10. 标记地址空间（例如，使用 10.2.0.0/16 掩码对应 65,536 个地址）。打开 **Create Subnet Configuration**（创建子网配置）页面。
- 11. 输入 **Head Subnet**（主子网）名称（使用任何有意义的名称，如 shsubnet）。
- 12. 在 Search Head Subnet Address Prefix（搜索头子网地址前缀）字段中，选择与地址空间匹配的前缀（例如，使用 10.2.0.0/24  32,768 个地址）。
- 13. 输入索引子网名称——例如 idxsubnet。
- 14. 输入索引子网地址前缀，10.2.0.0/24。
- 15. 为 Splunk VM 选择部署类型（根据预期负载选择）。
- 16. 选择 VM 尺寸（根据预期负载选择）。
- 17. 选择一个新的 IP 名称。点击按钮并创建一个新名称。这可以是静态的或动态的。（注意，静态名称可能会产生额外费用）。
- 18. 为 Splunk VM 设置一个唯一的域名（网络唯一）（例如，content.splunk.example.vm）。
- 19. 设置管理员密码（用户将是 admin——即在 VM 中预先配置）。建议：将密码存储在 Key Vault 中（参见本章前面的步骤）。打开 **Optional**（可选）页面。
- 20. 配置 SSH 源以减少访问（出于安全考虑）。
- 21. 配置接收数据的 IP 范围（出于安全考虑）。
- 22. 在继续之前检查所有数据，并保存配置摘要截图以备后参考。打开 Buy（购买）页面。
- 23. 完成后点击 Create 完成购买。请注意，这将根据前面步骤选择的配置产生常规费用。

> 注意：模板将默认以 standalone-vm 的名称创建虚拟机。

### 安装和配置 Splunk 的 Azure Monitor 插件

要安装并配置 Splunk 的 Azure Monitor 插件，请遵循 Splunk 在 `http://aka.ms/ascsplunkaddon` 维护的说明。如果你想查看日志在 Splunk 中外观的示例，请参阅 `http://aka.ms/ascsplunk`。

## 与其他微软解决方案集成

使用 Azure Security Center 作为你的云保护平台的优势之一是能够与其他微软安全解决方案进行原生集成。其意图是扩大威胁检测能力以涵盖其他场景，同时利用微软其他解决方案提供的威胁情报。通过集成而非重新发明，Security Center 可以继续专注于提供出色的威胁检测体验，并提供可以流向其他平台（如 SIEM）的共享信号。在本章中，你将学习如何将 Security Center 与 Windows Server Defender ATP、Microsoft Cloud App Security、SQL 高级防护 (ATP) 以及针对存储账户的高级防护 (ATP) 集成。

### 扩大威胁检测范围

在第 2 章“Azure Security Center”中，你学习了云安全配置管理 (CSPM) 和云工作负载保护平台 (CWPP)。你还学习了 Security Center 与某些 Azure 工作负载（如 AppServices、容器等）的原生集成。与 Windows Server Defender ATP 的集成补充了 Security Center 在 CWPP 场景下的覆盖。对于原生 Azure 工作负载，Security Center 还可以利用存储账户的高级防护解决方案。

#### 与 Microsoft Defender ATP 集

Security Center 扩展其云工作负载保护平台 (CWPP) 的集成，引入 Windows 高级防护 (ATP) 并带来端点检测与响应 (EDR) 能力。对于已加入 Security Center 的支持的 Windows 服务器，会自动启用 Microsoft Defender ATP 传感器。

> 重要：此功能支持 Windows Server 2012 R2、Windows Server 2016，且仅支持具有标准级（Standard Tier）订阅的服务器。在我们编写本章时，Windows Server 2019 尚未支持 Windows Defender ATP。

从用户的角度来看，入组过程是无缝的。如果机器位于 Azure 中且 Auto Provision（自动配置）配置为 On，则将部署微软监控代理 (MMA)。MMA 部署后，它将检查操作系统是否支持接收 Windows Defender ATP。如果已启用，则会将 Microsoft Defender 传感器部署到虚拟机。整个入组过程可能需要 24 小时。

对于位于本地或不同云提供商的机器，入组过程基本上相同；唯一的区别是你需要在目标机器上手动安装 MMA。要启用此集成，请按照以下步骤操作：

- 1. 打开 Security Center
- 2. 在左侧栏的 Policy & Compliance（策略与合规）下，点击 Security Policy（安全策略）。
- 3. 对想要启用此集成的订阅点击 Edit Settings（编辑设置）。
- 4. 在 Settings（设置）下，点击 Threat Detection（威胁检测），出现 Enable Integrations（启用集成）窗格。
- 5. 选择 Allow Windows Defender ATP to Access My Data（允许 Windows Defender ATP 访问我的数据）选项并点击 Save。一旦集成启用且服务器完全入组，服务器上的 Windows Defender ATP 传感器将向 Microsoft Defender ATP 云服务报告遥测数据。一旦 Microsoft Defender ATP 触发攻击指标，将在 Center 和工作区中发布警报（见图 9-2）。

![](img/4b11e95292819ab1a383a41ef73aedb4_193_0.png)

#### 统一终端检测与响应 (EDR)

Microsoft Defender Advanced Threat Protection (Microsoft Defender ATP) 是一个统一的安全平台，为 Windows 客户端、Windows Server 以及 Mac OS 等第三方系统提供终端保护平台 (EPP) 和终端检测与响应 (EDR) 能力。在 Windows Server 中，Microsoft Defender ATP 与 Azure Security Center 深度集成，确保组织能够最大限度地利用现有的 Microsoft 安全投资。通过这种深度集成，客户可以受益于支持的 Windows Server 到 Microsoft Defender ATP 的自动入 {体验。

这使得安全分析师能够查看整个环境，而无需在调查期间在门户之间切换。因此，Microsoft Defender ATP 与 Azure Security Center 的集成有助于组织发现异常。此外，组织还可以检测并响应针对 Azure Security Center 监控的服务器终端的高级攻击。

Milad Aslan，Microsoft Defender ATP 研发部高级安全计划经理

#### 与 Microsoft Cloud App Security 的集成

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

#### SQL ATP 集成

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

#### 与 Azure Storage ATP 的集成

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

## 通过 API 安全警报

尽管 Azure Security Center 有它自己的仪表板，你可以在其中查看所有的安全警报，但在某些特定场景，你可能希望通过 API 消费警报。这对于想要构建自己的仪表板并程序化操作所有警报的组织来说是一个常见场景。

在本章中，你将学习如何利用内置的 Security Center 表述状态转移（REST）API 和 Microsoft Graph Security API，使用 HTTP 请求来检索警报。

### 理解 REST API

表述状态转移（REST）API 是服务端点，支持一组 HTTP 操作（方法），这些方法为服务的资源提供了创建、检索、更新或删除的访问能力。一个 REST API 请求/响应对可以分为五个部分——三个用于请求，两个用于响应——如图 10-1 所示。

![](img/4b11e95292819ab1a383a41ef73aedb4_198_0.png)

请求的第一部分是请求 URI，它是主地址。该地址包含以下部分：

结构：(URI-scheme)://{URI-host}/{resource-path}?{query-string}
示例：`https://management.azure.com/subscriptions/XXX/providers/Microsoft.Security/alerts/api-version=2019-01-01`

第二部分是 HTTP 请求头，它由请求 HTTP 方法组成，例如 GET、HEAD、PUT、POST。此外，你可能还有其他可选标头，例如身份验证。第三部分是可选的，它可以包含根据所用方法而异的补充信息。例如，POST 方法可以包含 MIME 编码的对象，这意味着你还需要指定 Content-type 请求头。

响应的第一部分是 HTTP 状态码，它也可能根据后端如何响应此请求而变化。如果一切运行正常且这是一个成功的请求，你应该收到收到 HTTP 200 状态码。此外，第二个字段是可选的，它的存在是为了支持主响应，就像之前的 MIME 编码示例一样。

### 使用 Security Center REST API 访问警报

Security Center 有它自己的一组 REST API，分为不同的操作组。以下是可用组的描述：

- Alerts（警报）：这些是订阅级别的安全警报。
- Auto Provisioning Settings（自动配置设置）：这些允许你为订阅指定配置配置。
- Compliances（合规性）：检索订阅的法规合规性信息。
- Discovered Security Solutions（已发现的安全解决方案）：检索有关已发现的安全解决方案。
- External Security Solutions（外部安全解决方案）：检索当前与 Security Center 集成的合作伙伴解决方案的详情。
- JIT Network Access Policies（JIT 网络访问策略）：检索使用即时 (JIT) 虚拟机访问来保护资源的策略。
- Locations（位置）：检索特定位置的详情。
- Operations（操作）：检索所有可用操作。
- Pricings（定价）：检索 Security Center 正在使用的定价层级。
- Security Contacts（安全联系人）：这允许你配置订阅的安全联系人信息。
- Tasks（任务）：允许你查看脚本的可视化 Security Center 建议。
- Workspace Settings（工作空间设置）：允许你配置与工作空间相关的设置。

如你所见，可以通过 API 执行很多操作；本章仅关注警报。通过 REST API 调用的 Alert 有许多可以执行的操作，包括获取与资源组或订阅关联的警报。要列出与资源关联的所有警报，可以使用以下示例：
`https://management.azure.com/subscriptions/{subscriptionId}/providers/Microsoft.Security/alerts?api-version=2019-01-01`

此 HTTP GET 的响应应该是一个 HTTP 200 Header，随后是 JSON 格式的正文，如列表 10-1 所示。

## 列表 10-1 HTTP GET 请求的响应

```json

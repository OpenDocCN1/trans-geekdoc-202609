

提示：有关 Azure IoT Edge 的更多信息，请参阅 https://docs.microsoft.com/en-us/azure/iot-edge/about-iot-edge。

# IoT 安全

IoT 解决方案可以分为四个安全相关的区域：设备、现场网关、云端网关和应用程序。IoT 解决方案的管理和监控需要处理这四个区域的安全性。

Azure Security Center for IoT 统一了整个 IoT 解决方案的安全态势和威胁检测，从低资源的叶节点设备、现场网关，一直到云端网关的服务设备。它通过跨运行在边缘、本地以及 Azure 和其他云平台上的 IoT 工作负载，提供统一的可视化和控制、自适应威胁防护，以及智能的威胁检测和响应来实现这一目标。

由于 IoT 具有极高的密度和规模，它既带来了独特的安全挑战，也带来了机遇。IoT 设备是以规模化的方式部署和管理的。这结合 AI 允许对设备的常规行为进行深度建模。Azure Security Center for IoT 利用 Azure 资源的无缝集成，用于追踪和建模 IoT 设备，并识别任何偏离常规行为的情况。它通过允许自动工作流将安全考虑在内，对客户业务逻辑产生实时影响。例如，它可以通过将异常传感器标记为潜在的恶意或故障，防止其导致整个系统发生故障。

对于在 IoT 解决方案中起着关键作用的设备，Azure Security Center for IoT 提供了一系列开源安全代理。安全代理设计用于在受限的 IoT 环境中运行，与其消耗的资源相比，它们在提供的价值方面具有高度的可定制性。它们提供了增强的安全能力，例如监控远程连接、活动应用程序、登录事件和操作系统最佳实践。

Michael Burgary，微软 IoT 安全团队高级架构师

# 配置 Security Center for IoT

要启用 Security Center for IoT，您需要先有一个正在运行的 Azure IoT Hub。如果您没有正在运行的 Azure IoT Hub，请使用 http://aka.ms/AzureloTDeployment 提供的步骤创建 IoT Hub、IoT Edge 并安装 IoT Edge 仿真设备。在 Azure IoT 环境完全配置完成后，请按照以下步骤启用 Security Center for IoT。

> 注意：在编写本章时，该功能仍处于公测预览阶段（Public Preview）。某些步骤可能已经更改。请确保访问 http://aka.ms/ASC4loT 获取最新步骤。

- 1. 使用 Azure 门户，打开 IoT Hub 并点击您创建的 IoT Hub，如图 7-2 所示。（在本示例中，IoT Hub 名为 YDio。）

![](img/4b11e95292819ab1a383a41ef73aedb4_157_0.png)

图 7-2 选择 IoT Hub

- 2. 在“安全”（Security）部分，点击“概述”（Overview）。

- 3. 点击“启动预览”（Start preview）按钮，如图 7-3 所示。

![](img/4b11e95292819ab1a383a41ef73aedb4_157_1.png)

图 7-3 启用 Azure Security Center for IoT

138 第7 章 *使用 Azure Security Center 保护您的 IoT 解决方案*

# 4. 显示 Azure Security Center for IoT 设置页面，如图 7-4 所示。

![](img/4b11e95292819ab1a383a41ef73aedb4_158_0.png)

**图 7-4** 配置初始设置以启用 Security Center for IoT

- 5. 点击“启用”（Enable）按钮，选择您想要监控的**订阅**（Subscription）以及应存储数据的**工作区**（Workspace）。Security Center for IoT 将在此工作区中存储建议和警报。您还可以控制是否执行数字孪生元数据收集，以及是否要在工作区中存储原始设备安全事件。

- 6. 点击**保存**（Save）。

- 7. 保存后将出现**概述**（Overview）页面。您可能需要刷新页面查看当前状态，该状态与图 7-5 所示的全新 IoT 部署示例相似。

![](img/4b11e95292819ab1a383a41ef73aedb4_159_0.png)

图 7-5 带有威胁防护和威胁检测选项的概述页初始状态

Security Center for IoT 会自动识别其他连接到您的 IoT Hub 并与您的 IoT 解决方案相关的 Azure 服务。您可以手动添加任何其他 Azure 资源并将其标记为 IoT 解决方案的一部分。要手动添加资源，点击安全下的“资源”（Resource）选项并点击“添加资源”（Add Resource）按钮。从出现的列表中选择您要添加的资源。

虽然这些步骤是在 Azure IoT 控制板执行的，但在启用 Security Center for IoT 后，您可以查看 IoT 设备的安全态势。未来，所有步骤都将由 Security Center 仪表板执行，以便对云安全态势进行集中管理。

# 安全建议

Security Center 扫描您的 Azure 资源和 IoT 设备以提供安全建议。通过修复这些建议，您可以减少攻击面并自动提高您的安全分（Secure Score）。要查看 IoT 的安全建议，请在资源安全状况（Resource Security Hygiene）下打开 Security Center 仪表板并点击“IoT Hub 及资源”（IoT hubs & resources）。图 7-6 显示了该窗格填充建议后的示例。

# IoT Hub 及资源

IoT 资源概览

搜索建议

| 建议 | 安全分影响 | 失败的资源 |
| --- | --- | --- |
| IoT 设备 - 安装 Azure Security of Things 代理 | -30 | 1 个/1 个 IoT Hub |
| 相同的身份凭据 | +25 | 1 个/1 个 IoT Hub |
| IoT 设备 - 设备上开启端口 | -20 | 1 个/1 个 IoT Hub |
| 默认 IP 过滤策略应为拒绝 | +15 | 1 个/1 个 IoT Hub |
| 在 IoT Hub 中启用诊断日志 | +5 | 3 个/3 个 IoT Hub |

图 7-6 Security Center 创建的 IoT 安全建议

要查看特定建议的详细信息，只需点击它即可打开该建议。在本示例中，我们将使用图 7-7 所示的“相同的身份凭据”。

首页 > Security Center - 概述 > IoT Hub 及资源

# 相同的身份凭据

描述 多个设备使用了用于连接 IoT Hub 的相同身份凭据。这可能表明存在非法的设备正在冒充合法设备。它还暴露了设备伪造的风险。

常规信息

| 建议评分 | 0/25 |
| --- | --- |
| 建议影响 | +25 |
| 用户影响 | 高 |
| 实现成本 | 高 |

- 数据外泄
- 数据溢漏
- 威胁防护

修复步骤

检查涉及的设备并确保它们都是有效的。替换任何重复的凭据并确保所有设备身份凭据都是唯一的。

图 7-7 IoT 安全建议属性

# 监控警报

Security Center for IoT 接收的数据还将用于需要时触发警报。Security Center for IoT 使用高级分析和威胁情报生成有关恶意活动的警报。警报是入侵或攻击的指示，因此应对对警报进行调查和修复。某些内置警报包括：

- 二进制命令行
- 禁用主机防火墙
- 反向 shell
- 可疑 IP 地址通信
- 加矿

除了内置警报外，您还可以根据对预期设备行为的知识自定义警报。

# Security Center 中的威胁情报

如今威胁情报（TI）是任何成功安全基石之一。TI 系统提供洞察以便做出决策。然而，拥有更多数据并不总是更好。需要的是高质量、及时且可操作的情报。我们致力于提供这些情报。

在安全遥测和情报馈方面，微软拥有无与伦比的可视性：

- 第一方威胁情报：通过以下方式获得对威胁格局的无与见性：
    * 运行搜索引擎。
    * 拥有运行在数十亿设备上的 Windows 遥测数据。
    * 使用顶级的恶意软件。
    * 运行扫描数百万邮件并检测恶意软件样本的电子邮件系统。
    * 拥有最大的云平台之一提供了对威胁格局的无与伦比的可视性。
- 第三方来源：微软订阅了来自大量第三方服务的情报馈。
- 人工分析的情报收集：这些情报通过活动小组追踪、行业合作伙伴关系以及与各种实体共享威胁情报来收集。


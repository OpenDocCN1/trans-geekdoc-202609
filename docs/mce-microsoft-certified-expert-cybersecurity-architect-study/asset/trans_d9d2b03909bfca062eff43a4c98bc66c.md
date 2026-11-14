

他们的建议与 Microsoft 的建议高度一致，Microsoft 还与这些组织共享建议和基线。Microsoft 开发了这些组策略基线的类似版本，以便 MDM 继续发展为云服务。Microsoft Intune 包括这些附加基线，其中包括遵循这些基线的用户、组和设备的合规性报告。

在 Azure Policy 中，组织标准得到强制实施，并大规模评估合规性。通过其合规性仪表板，它提供环境的全面视图，并能针对每个资源和每个策略钻取到细粒度级别。您还可以通过对现有资源进行批量修正以及自动化新资源修正，将资源带入合规状态。

Azure Policy 常用于在资源一致性、法规合规性、安全性和成本管理中实施治理。得益于内置的 Azure 策略定义，您可以立即在 Azure 环境中开始使用这些简单的用例。

以下参考链接提供 Azure Policy 的 Windows 安全基线：

```
learn.microsoft.com/en-us/azure/governance/policy/samples/guest-configuration-baseline-windows
```

以下参考链接提供 Azure Policy 的 Linux 安全基线：

```
learn.microsoft.com/en-us/azure/governance/policy/samples/guest-configuration-baseline-linux
```

以下参考链接提供 Azure Policy 的 Docker 安全基线：

```
learn.microsoft.com/en-us/azure/governance/policy/samples/guest-configuration-baseline-docker
```

安全基线可在 Microsoft 客户端的 endpoint.microsoft.com 上获取，其中列出了 Microsoft Intune 中 Windows 10/11 MDM 安全基线的配置列表。

```
learn.microsoft.com/en-us/mem/intune/protect/security-baseline-settings-mdm-all?pivots=mdm-november-2021
```

![](img/5ab9852bf401dd309bf0f81797a91445_288_0.png)

Microsoft 通过 Windows 和 Windows Server 为其客户提供安全操作系统，Microsoft Edge 提供安全应用。您可以使用 Microsoft 的各种配置功能，对环境进行精细控制，并获得其产品提供的安全保障。

可从 Microsoft 下载中心下载安全基线。SCT 为管理员提供管理安全基线和基线的工具。您还可以使用 SCT 来管理安全基线。

运行 Windows 10 或 Windows 11 的设备可以轻松在 Microsoft Intune 中配置 MDM 安全基线。

## 为服务器指定安全基线（包括多个平台和操作系统）

确保 Windows Server 环境中的服务器和客户端计算机配置安全，是保护环境的重要组成部分。加固操作系统对于保护 Windows Server 环境至关重要。为服务器定义安全要求取决于服务器角色，因为角色将确定所需的加固设置。

处于独特角色的服务器可能需要更多配置，但大多数服务器都会有核心基础安全要求。如果服务器是域控制器 (DC)，则有必要采取额外步骤来加固服务器上的 Active Directory 服务。Microsoft SCT 是了解服务器当前状态的绝佳工具。

## 分析安全配置

Microsoft SCT 是一组用于下载和安装安全配置基线（通常称为 *安全基线*）的工具，适用于 Windows Server 和其他 Microsoft 产品（包括 Windows 10、Microsoft 365 企业应用版和 Microsoft Edge）。您可以通过管理 GPO 来实施安全配置基线。

此外，您可以使用 SCT 将当前 GPO 与推荐的 GPO 安全基线进行比较。将现有 GPO 与推荐 GPO 进行比较后，您可以编辑推荐的 GPO 并将其应用于设备。

此外，SCT 包括用于管理 Windows Server GPO 设置的工具，包括 Policy Analyzer、Local Group Policy Object (LGPO) 以及 Set Object Security 和 GPO to Policy Rules。

## 安全加固服务器（域成员）

## 本地管理员帐户

域中的每台计算机成员都保留一个本地 Administrator 帐户。手动部署计算机或使用 Microsoft Endpoint Configuration Manager 等软件部署工具时，会自动配置此帐户。如果 IT 人员无法连接到域，可以使用本地管理员帐户登录到计算机。

对于计算机数量较多的组织，管理本地管理员帐户的密码可能非常困难。组织中每个本地 Administrator 帐户都有不同的密码，组织通常会为所有本地 Administrator 帐户分配相同的通用密码。采用这种方法的缺点在于，非 IT 运维团队的人员可能会通过猜测密码，获取对组织中未授权计算机的访问权限。

除了管理加入域的计算机的本地帐户密码外，本地管理员密码解决方案 (LAPS) 可用于所有当前受支持的 Windows Server 和客户端操作系统。

本地管理员密码解决方案 (LAPS) 允许加入域的计算机管理本地管理员帐户的密码。密码随机生成，并存储在 Active Directory (AD) 中，受 ACL 保护，因此只有合格用户才能读取或请求重置。

## SMB 协议

服务器消息块 (SMB) 协议是一种主要用于文件共享的网络协议，也是服务器保护的另一个关键部分。它禁用旧版协议并强制执行更安全的通信方式。除了文件共享外，打印机、扫描仪和电子邮件服务器也经常使用 SMB。SMB 1.0 不支持加密，而 3.0 版引入了 SMB 加密。

使用 SMB 加密，服务器可以为 Microsoft SQL Server 等应用程序提供安全存储，并向客户端提供某些数据传输。与基于硬件的加密（通常更复杂）相比，SMB 加密通常更易于使用。SMB 加密为用户提供数据包安全性，防止恶意黑客拦截或篡改数据包。

Windows Server 2019 中包含的 SMB 3.1.1.c 版 SMB 对 SMB 3.0 的安全性进行了多项增强。此版本的 SMB 包括预身份验证完整性检查和加密改进。

SMB 在 Windows Server 系统中有多个版本可用。要使用 SMB 3.1.1，主机服务器及其通信系统必须支持 SMB 3.1.1。这样，它们就可以与运行其他操作系统和 Windows 版本的服务器和客户端进行通信。

某些修改 SMB 数据包的广域网 (WAN) 加速器不支持 SMB 3.1.1 的预身份验证。因此，您可能需要更换一些网络设备。

## Azure 安全基准

确保所有服务器都符合 ASB OS 基线，作为指定服务器要求的替代方案。使用 Microsoft Defender for Cloud，ASB OS 基线可用作 Windows 或 Linux 的安全建议，如图 6.3 所示。

访问建议将显示一组规则，这些规则使用 Azure 来宾配置功能对操作系统进行安全检查，以确保其配置安全。

如图 6.4 所示，单击每个规则将显示有关安全检查和受影响资源的更多信息。

## 图 6.3 Microsoft Defender for Cloud 适用于 Windows 和 Linux 的 ASB OS 基线

修正安全配置

- 应修正 Windows 计算机上的安全配置漏洞（由来宾配置提供支持）
- 应修正 Linux 计算机上的安全配置漏洞（由来宾配置提供支持）

## 图 6.4 修正的详细视图

## 拒绝以批处理任务身份登录

### 描述

拒绝以批处理任务身份登录

### 影响

如果将“拒绝以批处理任务身份登录”用户权限分配给其他帐户，可能会拒绝分配到特定管理角色的用户执行其所需工作活动的权限。您应确认委派的任务不会受到不利影响。例如，如果将此用户权限分配给 IWAM_<ComputerName> 帐户，MSM 管理点将失败。在新安装运行 Windows Server 2003 的计算机上，此帐户不属于 Guests 组，但在从 Windows 2000 升级的计算机上，此帐户是 Guests 组的成员。因此，了解哪些帐户属于您分配“拒绝以批处理任务身份登录”用户权限的任何组非常重要。

| 规则 ID | 49258884-b2f0-4a4e-b66a-6954bb8473bf |
| 名称 | 拒绝以批处理任务身份登录 |
| 类别 | 用户权限分配 |
| 扫描时间 | 2022/4/9 下午 2:56:22 (UTC) |

### 漏洞

拥有“拒绝以批处理任务身份登录”用户权限的帐户可能被用来计划作业，这些作业可能会消耗过多计算机资源并导致拒绝服务 (DoS) 状态。

### 修正

不可用

### 受影响的资源

## 自动管理

使用 Automanage，可将自动化和最佳实践应用于在 Azure 或受 Azure Arc 支持的混合环境中运行的 Windows 和 Linux 服务器。


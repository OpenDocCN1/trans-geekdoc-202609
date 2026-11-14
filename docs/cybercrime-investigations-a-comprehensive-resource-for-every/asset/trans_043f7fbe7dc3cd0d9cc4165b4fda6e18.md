
# 信息安全框架概述

对于调查人员而言，了解这些框架有助于掌握网络安全的基本规范，并能与信息安全专业人员进行深入交流。当组织遭遇网络犯罪时，其政策、标准和程序可能与特定框架保持一致，这可能成为关键参考。

这些框架在一定程度上存在差异，这可能导致一些困惑。此外，围绕信息安全不断增长的法律法规体系也有其自身的安全要求层级，我们将在[第 9 章](#chapter09.xhtml)中讨论。组织必须在实施保护资产且符合法律法规的安全框架之间找到平衡。随着与信息安全相关的民事诉讼和监管行动日益增多，遵循框架的证据变得愈发重要，因为它可能证明组织采取了合理的信息安全措施。反之，缺乏合规性，或政策与实践之间的差异，可能使安全措施不足的指控更具可信度。

让我们看看一些基本的框架原则和知名的安全框架。

## 4.3.1 四大支柱：知识、设备、数据和网络

如果我们要创建世界上最简单的信息安全框架，它可能围绕四大安全支柱构建——用户知识、设备、数据以及网络/互联网使用，如[图 4.4](#chapter04.xhtml#fig4_4)所示。![图 4.4 四大安全支柱。](`images/fig4_4.jpg`)

**知识**——关于计算机、信息安全和威胁的知识是迈向信息安全的第一步，因为没有它，组织和个人不知道如何配置其 IT 系统，也不知道如何保护自己免受网络犯罪威胁。接下来是**设备**，跟踪设备、保持设备占有权并安全配置它们。然后是**数据**，确保你知道数据在哪里，以及如何高效使用它、安全备份它、防止其被泄露。最后是最复杂的一步，安全配置**网络和互联网使用**，确保网络不被攻破，并使用安全的方法与他人通信和通过互联网访问数据。

这四大支柱是大多数信息安全框架的简化版本。你将看到，这些支柱是我们即将回顾的框架的主要关注领域。

## 4.3.2 CIS 关键安全控制

互联网安全中心（CIS）是一个致力于开发和推广网络防御最佳实践解决方案的非营利组织，它维护着关键安全控制（CSCs），即 20 项行动（或称“控制”），使组织能够全面应对信息安全。这些控制的优点在于它们按优先级排序，并从基础开始，这些基础很容易理解——例如清点计算设备并安全配置它们。随后，控制措施转向更复杂的任务，如规范电子邮件使用、数据和网络，最后进行渗透测试。

在[表 4.1](#chapter04.xhtml#table4_1)中，我们用通俗易懂的术语总结了这 20 项控制。每项控制的官方名称列在第二列中。

### 表 4.1 CIS 关键安全控制

| CSC 编号 | 通俗名称 | 官方名称 |
| --- | --- | --- |
| CSC 1 | 清点授权和未授权设备 | Inventory of Authorized and Unauthorized Devices |
| CSC 2 | 清点授权和未授权软件 | Inventory of Authorized and Unauthorized Software |
| CSC 3 | 移动设备、笔记本电脑、工作站和服务器上硬件和软件的安全配置 | Secure Configurations for Hardware and Software on Mobile Devices, Laptops, Workstations, and Servers |
| CSC 4 | 持续漏洞评估与修复 | Continuous Vulnerability Assessment and Remediation |
| CSC 5 | 受控的管理权限使用 | Controlled Use of Administrative Privileges |
| CSC 6 | 审计日志的维护、监控与分析 | Maintenance, Monitoring, and Analysis of Audit Logs |
| CSC 7 | 电子邮件和 Web 浏览器防护 | E-mail and Web Browser Protections |
| CSC 8 | 恶意软件防御 | Malware Defenses |
| CSC 9 | 网络端口、协议和服务的限制与控制 | Limitation and Control of Network Ports, Protocols, and Services |
| CSC 10 | 数据恢复能力 | Data Recovery Capability |
| CSC 11 | 防火墙、路由器和交换机等网络设备的安全配置 | Secure Configurations for Network Devices such as Firewalls, Routers, and Switches |
| CSC 12 | 边界防御 | Boundary Defense |
| CSC 13 | 数据保护 | Data Protection |
| CSC 14 | 基于知情需要的受控访问 | Controlled Access Based on the Need to Know |
| CSC 15 | 无线访问控制 | Wireless Access Control |
| CSC 16 | 账户监控与控制 | Account Monitoring and Control |
| CSC 17 | 安全技能评估与适当培训以弥补差距 | Security Skills Assessment and Appropriate Training to Fill Gaps |
| CSC 18 | 应用软件安全 | Application Software Security |
| CSC 19 | 事件响应与管理 | Incident Response and Management |
| CSC 20 | 渗透测试和红队演练 | Penetration Tests and Red Team Exercises |

这只是控制类别的列表。该框架提供了关于如何在每个类别中保护信息系统的详细规范。

## 4.3.3 NIST 网络安全框架（CSF）

美国国家标准与技术研究院（NIST）是商务部下属机构，为多类组织开发了最广泛使用的框架和指南。

NIST 网络安全框架（简称“CSF”，正式标题为“改善关键基础设施网络安全框架”）为组织如何保护自己免受网络犯罪提供了指导。

*   **识别**
*   **保护**
*   **检测**
*   **响应**
*   **恢复**

这些行动旨在用于识别关键资产、保护资产、检测威胁、响应和恢复的循环持续过程中。在这五大功能中的每一个内部，都有更详细的关注领域（“类别”），如[表 4.2](#chapter04.xhtml#table4_2)所示：

### 表 4.2 NIST 网络安全框架功能和类别

| **识别** | **保护** | **检测** | **响应** | **恢复** |
| --- | --- | --- | --- | --- |
| * 资产管理 (`ID.AM`) | * 身份管理、认证和访问控制 (`PR.AC`) | * 异常和事件 (`DE.AE`) | * 响应规划 (`RS.RP`) | * 恢复规划 (`RC.RP`) |
| * 业务环境 (`ID.BE`) | * 意识和培训 (`PR.AT`) | * 安全持续监控 (`DE.CM`) | * 沟通 (`RS.CO`) | * 改进 (`RC.IM`) |
| * 治理 (`ID.GV`) | * 数据安全 (`PR.DS`) | * 检测流程 (`DE.DP`) | * 分析 (`RS.AN`) | * 沟通 (`RC.CO`) |
| * 风险评估 (`ID.RA`) | * 信息保护流程和程序 (`PR.IP`) | | * 缓解 (`RS.MI`) | |
| * 风险管理策略 (`ID.RM`) | * 维护 (`PR.MA`) | | * 改进 (`RS.IM`) | |
| * 供应链风险管理 (`ID.SC`) | * 防护技术 (`PR.PT`) | | | |

## 4.3.4 NIST SP 800-53

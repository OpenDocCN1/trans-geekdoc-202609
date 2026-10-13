

# 报告阶段

报告是 NIST 渗透测试指南的最后阶段（一个重复阶段）。渗透测试的全部意义在于了解目标环境中真实存在的漏洞。管理层将想要知道漏洞在哪里、它们是如何被利用的、哪些系统受到影响、测试期间是否有其他系统受到影响，以及漏洞被利用的可能性，或者是否已经发生过利用。无论发现了什么，质量低劣的渗透测试报告都会导致整体渗透体验不佳，这就是为什么报告是所有阶段中最重要的。

根据 NIST 800-115，报告阶段与渗透测试的其他三个阶段同时进行。这使得文档不仅能包含发现了什么，还能包含是如何发现的。包含此类细节极其重要，因为它代表了支持渗透测试结果的证据。在渗透发生和报告交付之间，许多事情都可能发生变化，包括安全性的改进。记录过程可以揭示在补丁或渗透测试后实施的变更生效之前就已存在的漏洞。此外，被发现系统遭入侵的系统所有者可能会试图反驳结果，此时渗透测试人员将希望通过展示所用渗透测试过程的文档来证明自己的观点。

> **注意**
>
> 我建议在规划阶段确定所有将阅读渗透测试报告的相关方。如果包含非技术人员，请确保报告的核心部分（通常称为执行摘要）不使用技术术语。您可以包含技术细节，但我建议在执行摘要之后提供技术细节，以便对技术细节感兴趣的相关方可以获取这些信息，而无论技术水平如何，所有人都能从报告的执行摘要中受益。

[第 6 章](#ch06.xhtml#ch06)和[第 9 章](#ch09.xhtml#ch09)将更深入地探讨这些渗透测试概念。接下来，我将简要介绍一些渗透测试工具，以帮助展示渗透测试如何执行。

## 渗透测试工具

我最喜欢的 SOC 将漏洞攻击作为渗透测试人员进行运营化的方法之一是使用 MITRE ATT&CK 框架，该框架已在[第 1 章](#ch01.xhtml#ch01)中介绍过。根据 MITRE 网站（[https://attack.mitre.org/](https://attack.mitre.org/)）的说法，“MITRE ATT&CK 是一个基于真实观察的、全球可访问的对手战术和技术知识库。”MITRE ATT&CK 是一种通用语言，威胁猎人可以用它来讨论真实对手使用的攻击技术和战术。MITRE ATT&CK 由多个矩阵组成。[图 3-11](#ch03.xhtml#ch03fig11) 展示了企业 ATT&CK 矩阵中 macOS 矩阵的示例（Windows 和 Linux 矩阵也可用）。SOC 实施 MITRE ATT&CK 的原因之一是它们可以测试内部流程，以确定是否能检测到常见攻击。无论您是新手还是经验丰富的渗透测试人员，ATT&CK 都是一个很好的指导方针。

![FIGURE 3-11 MITRE ATT&CK Framework](Images/03fig11.jpg)

**图 3-11** MITRE ATT&CK 框架

测试 SOC 对抗攻击的有效性以及测试 SOC 运营化 MITRE ATT&CK 能力的标准方法是使用 Atomic Red Team 测试。[图 3-12](#ch03.xhtml#ch03fig12) 展示了 Atomic Red Team 网站（[https://atomicredteam.io/](https://atomicredteam.io/)）的用例页面。

![FIGURE 3-12 Atomic Red Ream Website](Images/03fig12.jpg)

**图 3-12** Atomic Red Team 网站

Atomic Red Team 是攻击者使用的开源技术集合，可单独针对 MITRE ATT&CK 的攻击阶段进行测试。测试按操作系统划分，支持 Windows、macOS 和 Linux 操作系统。测试可在 Red Canary 的 Atomic Red Team GitHub 页面获取，地址为 [https://github.com/redcanaryco/atomic-red-team](https://github.com/redcanaryco/atomic-red-team)。SOC 团队需要能够测试其技术控制，不仅要确定能否检测到攻击，还要确定能否防止攻击发生。

当攻击确实发生时，SOC 团队需要确保在需要时能收集取证证据，并将系统恢复到工作状态。Atomic Red Team 测试提供了一种方法，可在开源、公开可用的格式中实现这些目标。[图 3-13](#ch03.xhtml#ch03fig13) 显示了可用于 Windows 的开源测试部分。测试和技术通过社区驱动的方式进行更新。许多使用 Atomic Red Team 测试的 SOC 会在其自己的环境中使用 Atomic Red Team 战术时发现缺陷后，用新技术更新测试或对测试进行修正。

![FIGURE 3-13 Atomic Red Team Example for Windows](Images/03fig13.jpg)

**图 3-13** 适用于 Windows 的 Atomic Red Team 示例

有一些预防和检测工具正在结合基于 MITRE ATT&CK 和 Atomic Red Team 测试的软件产品。我最喜欢的商业工具之一托管检测与响应（MDR）来自 Atomic Red Team 的创建者 Red Canary。其产品旨在与端点检测与响应（EDR）解决方案集成，例如来自 Carbon Black 的解决方案。MDR 将从 EDR 解决方案接收的攻击、日志和警报数据映射到 MITRE ATT&CK。此外，MDR 允许 SOC 操作员针对特定的单个 Atomic Red Team 测试审核端点，以确定其解决方案在阻止攻击方面的有效性。

> **注意**
>
> Red Canary 拥有其软件的开源版本 Surveyor，可在 [https://redcanary.com/surveyor/](https://redcanary.com/surveyor/) 获取。

## 使用 Kali Linux 和 Metasploit 进行渗透测试

对于偏爱开源工具的人来说，最流行的开源渗透平台之一是 Kali Linux，这是一个基于 Debian 的发行版，旨在进行高级渗透测试和安全审计。Kali Linux 拥有数百种工具，涵盖利用、侦察、取证、漏洞评估、密码破解、模糊测试等各种主题。[图 3-14](#ch03.xhtml#ch03fig14) 显示了带有所有工具类别且展开“利用工具”类别的 Kali Linux 主仪表板。

![FIGURE 3-14 Kali Linux Tool Categories](Images/03fig14.jpg)

**图 3-14** Kali Linux 工具类别

Kali Linux 中可用的一个关键渗透测试工具（也可作为独立安装）是 Metasploit 框架。Metasploit 是一个框架，网络犯罪分子和道德黑客都用它来探测网络和服务器上的系统性漏洞。渗透测试人员可以使用漏洞扫描器识别系统中的潜在弱点，随后使用 Metasploit 将识别出的弱点与利用代码匹配。例如，如果您在某个版本的 Adobe 中发现了漏洞，可以搜索 Metasploit 以查看是否有针对该感兴趣漏洞的武器化利用代码。[图 3-15](#ch03.xhtml#ch03fig15) 展示了在 Metasploit 中搜索 Adobe 相关漏洞的示例。

![FIGURE 3-15 Searching Metasploit for Adobe Vulnerabilities](Images/03fig15.jpg)

**图 3-15** 在 Metasploit 中搜索 Adobe 漏洞


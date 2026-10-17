
[`cdt.ca.gov/wp-content/uploads/2017/03/templates_incident_response_plan.doc`](https://cdt.ca.gov/wp-content/uploads/2017/03/templates_incident_response_plan.doc) （自动下载）

## 第 1 阶段：准备总结

以下列表总结了事件响应生命周期准备阶段需要牢记的关键点：

*   确定将负责该服务的事件响应经理和团队负责人
*   确定与内部和外部各方的沟通方式
*   调研所有现有支持联系人，并与供应商和服务提供商建立任何所需的事件前和事件后响应服务合同
*   为事件响应服务和第三方资源沟通提供所需的任何培训
*   识别所有第三方资源并建立沟通，包括执法部门和其他第三方资源
*   制定针对支持不同类型事件的各层级职责的程序，以及事件升级将如何进行
*   获取启动事件响应项目或根据经验教训反馈强制实施变更所需的任何缺失技术或人员

## 第 2 阶段：检测与分析

一旦您根据所有准备任务建立了事件响应项目，您的事件响应服务就可以“上线”了，这意味着团队已准备好开始检测安全事件并做出响应。`NIST SP 800-61 Rev. 2` 将此阶段称为检测与分析；*检测* 是指 SOC 对潜在事件进行监控，而 *分析* 是指 SOC 对任何可能构成事件的情况进行评估，即由第 1 层或第 2 层完成的工作，以确定是否需要开立案例，或者该情况是否并非 SOC 应关注的事件。

事件被检测到的方式有几种。一种方式是员工或外部方使用前面提到的通信方法之一来通知 SOC 潜在事件。SOC 中创建事件的另一种方式是 SOC 使用检测技术发现了可能的威胁。

> **注意**
>
> 还可能发生网络攻击之外的其他事件，例如因配置错误导致网络中断；不过，本章重点关注基于网络威胁的事件。

### 事件检测

在 SOC 能够搜寻威胁之前，它必须具备使用不同检测技术检测威胁活动的能力，或者能够制定关于要寻找什么的假设并针对该假设进行监控。该假设基于制定计划以检测不同类型的攻击向量。在第 1 章中，我介绍了如何基于行业指南开发安全能力图谱，这些指南涵盖了最常见的攻击向量，如电子邮件、网关和主机。

在能力图谱中检测威胁是通过使用检测技术来实现的。第 1 章介绍了检测技术的概念，即用于检测网络和系统中恶意行为的工具。业界通常将这一防御领域称为 *入侵防御工具*。入侵防御工具的重点不在于防范威胁，而是假设您的防范技术（如防火墙）已经失效，威胁已突破您的网络。请记住，并非所有事件都是入侵，但所有入侵都是事件！

### 核心安全能力

第 1 章介绍了三种核心安全能力：特征检测、行为检测和异常检测，如图 8-6 所示。我强烈建议将重点放在行为检测和异常检测能力的组合上，用于您的入侵检测功能。特征检测虽有帮助；然而，通过防病毒措施或边缘入侵防御系统 (`IPS`) 进行的特征检测更适合用于防范。通过结合行为和异常检测能力，攻击者/恶意软件必须隐藏任何恶意行为，同时还要表现得像正常行为。如果威胁试图隐藏得非常好，与其他不隐藏的事物相比，它将表现为巨大的异常。如果威胁隐藏得不够好，您入侵检测工具中的恶意行为检测引擎应该能识别出它。有关这些概念的更多详细信息，请参阅第 1 章中的安全能力部分。

![图 8-6 核心安全能力](img/08fig06.jpg)

**图 8-6** 核心安全能力

以下是入侵防御的常用选项：

### Detection and Analysis

#### Detection Capabilities

Perform a SOC security capability assessment (see Chapter 1) to ensure you have one or more of the following intrusion detection capabilities:

*   Connect internal Intrusion Detection Systems (`IDS`) to SPAN/port mirrors to monitor internal traffic
*   Monitor data within network devices, such as NetFlow
*   Set up honeypots to lure threats to attack the honeypot instead of real targets
*   Use tools to monitor outbound traffic looking for communication with high-risk resources such as the dark web, Tor, or known malicious resources
*   Capture and analyze packets inside the network
*   Your staff and their systems alert you to possible incidents

> **Note**: When I say have one or more capabilities, it does not mean your end users should be your only detection capability!

Chapter 5, "Data Centralization," covers how to pull logs from security tools into a centralized tool and turn that data into actionable intelligence. Use those concepts to build incident response procedure documentation that covers who should monitor the centralized data tool, how incidents turn into cases when applicable, and how all of this works in your SOC tiered support model.

As possible incidents are detected by your SOC or external parties, the second half of the detection and analysis phase kicks in, where your incident response procedures will analyze what was detected. At this point, your incident response team's goal is to determine if the threat is real, and if so, what the appropriate response is. This practice is commonly referred to as **threat analysis**.

#### Threat Analysis

The SOC incident response team will encounter situations where there is a potential threat but requires further analysis to determine if the threat is real. For example:

*   An employee may report "my computer is acting weird since I ran this file" and ask if the file contains malware.
*   A user may complain about a received email being flagged, with the attachment removed and placed in a sandbox. The user may ask why the file was removed, and the threat analysis team must be able to prove the file posed a risk.
*   A user may complain about an external resource being blocked and want the SOC to approve allowing access to the resource. The threat analysis team needs to explain the risk behind the blocked resource through threat analysis research based on why the resource was blocked.

In all these cases, the SOC needs to determine the risk associated with the artifacts and resources before taking any action, such as executing incident response or notifying the end user that no risk exists.

Analysis services involve a specific skill set for investigating artifacts and researching malware. As stated in Chapter 3, analysis services answer questions about what an artifact is and its intended purpose (malicious or safe). The overall comparison of the incident response analyst versus malware analyst skill sets lies in how each handles malware:

*   **Incident Response Analyst**: Wants to understand the overall risk associated with the artifact and is responsible for responding to the threat.
*   **Malware Analyst**: Knows how to identify if an artifact is malicious, isolate the artifact, research its properties to better understand its functionality, look for signatures of all variants of the threat, and potentially build steps to lower the risk of similar threats attacking in the future.

The typical incident response analyst does not know how to disassemble malware or read assembly language, which is why analysis services include SOC staff with very specific and specialized analysis skills. See Chapter 4 for more on the skill sets associated with analysis experts.

##### Detecting Malware Behavior

Malware developers know that security tools and SOCs like yours exist. Teams I have worked with and friends in the security industry have dismantled threat actors and found they have research labs containing every security tool in the industry. Malware developers typically have popular vendor firewall models, `IPS` tools, various sandboxes, most modern antivirus products, and any other tools your organization and others use to defend against cyber threats. Keep this in mind when analyzing artifacts, and expect to encounter anti-detection, anti-disassembly, and anti-debugging tactics designed to obfuscate you and the tools you use to understand the threat.

##### Infected Systems

Once malware is installed on an affected system, you should expect it to perform many actions. The following is a partial list of common malware behaviors you may encounter:

*   Create new files and/or modify existing files
*   Move or copy malicious files to known locations (such as Windows system folders); the malware here can run with user privileges
*   Malware may not generate an executable but instead generate a DLL or batch script
*   Delete temporary files it created
*   Create registry keys (may also control network adapters)
*   Create unique identifiers that are harmless in themselves but are great for detecting malware families
*   Disable security tools such as Windows Firewall
*   "Call back" to malicious sources

With experience, your team of SOC analysts will learn to identify these malware behaviors and many more; however, you do not have to have experience looking for malware behaviors to analyze malware. The good news is that many of the industry tools I will cover do the detection and analysis work for you! Figure 8-7 shows an analysis report generated by Cisco Advanced Malware Protection (`AMP`) (an Endpoint Detection and Response (`EDR`) program) showing all the indicators that led to the artifact being deemed malware. An analyst of any skill level can perform malware analysis, but more skilled professionals will be able to work beyond the data provided by security tools. I highly recommend your SOC leverage industry certifications and training programs to upskill the people responsible for analyzing artifacts, as this field is highly specialized and difficult to hire for.

![Figure 8-7 Cisco AMP Indicators of Compromise Example](img/08fig07.jpg)

**Figure 8-7** Cisco AMP Indicators of Compromise Example

##### Analyzing Artifacts


# 术语定义

## Black Box Testing

**Black Box Testing** 是一种测试，作为测试的一部分，不会披露关于系统、软件或组织的设计、结构或操作的任何信息。

## Bluejacking

**Bluejacking** 是一种利用技术消息传递选项中的漏洞，在不实际配对设备的情况下向移动用户发送未经请求消息的方法。

## Bluesnarfing

**Bluesnarfing** 是利用某些蓝牙固件中发现的漏洞，从无线设备窃取信息的过程。

## Bluetooth Low Energy (BLE)

**Bluetooth Low Energy (BLE)** 是一种旨在显著降低功耗的蓝牙实现。它非常适合用于移动和专用设备。

## Broadcast Storms

**Broadcast Storms** 是指在短时间内发生的过量广播流量，可能会干扰正常操作并导致网络中出现环路，即广播帧因冗余路径而在交换机之间来回反弹。这些通常由因未正确阻塞冗余路径而产生的环路引起。

## Brute-Force Attack

**Brute-Force Attack** 是针对哈希的攻击，例如，尝试密钥空间内的每一种可能组合来破解哈希，而不依赖字典。暴力认证攻击可描述为一种通过反复发送不同内容来尝试绕过认证控制的方式，直到找到有效值并使认证成功。

## Buffer Overflow

**Buffer Overflow** 是当程序写入缓冲区的数据多于其分配的空间时产生的错误条件。超出既定缓冲区边界会导致程序覆盖相邻的内存位置。

## Bump Key

**Bump Key** 是一种设备，它使某人能够通过在插入锁内时对设备施加冲击力，来绕过易受攻击的锁。

## Certificate Authority (CA)

**Certificate Authority (CA)** 是一个受信任的实体，负责为主机或用户签署、颁发和管理数字证书（即身份），用于建立安全通信。

## Cold Boot Attack

**Cold Boot Attack** 是由普林斯顿大学研究人员（大约十年前）发现的一种攻击方法，他们演示了当设备在冷却或冻结温度下循环电源时，能够从随机存取存储器 (`RAM`) 中恢复磁盘加密密钥的能力。

## Comma-Separated Value (CSV)

**Comma-Separated Value (CSV)** 是一种使用逗号分隔数据字段的结构化数据格式。

## Command-Line Interface (CLI)

**Command-Line Interface (CLI)** 是一种使用基于文本的输入和输出进行用户与计算机交互的界面。

## Common Attack Platform Enumerations and Classifications (CAPEC)

**Common Attack Platform Enumerations and Classifications (CAPEC)** 是由 `MITRE` 策划和维护的已知网络攻击模式字典。它可按攻击机制和领域以及其他标准（如 `OWASP` 或 `ATT&CK` 分类）进行搜索。在适用的情况下，`CAPEC` 条目将数据与相关的 `CWE` 条目关联。

## Common Vulnerabilities and Exposures (CVE)

**Common Vulnerabilities and Exposures (CVE)** 计划由美国国土安全部网络安全和基础设施安全局 (`CISA`) 赞助，并由 `MITRE` 维护和策划。`CVE` 列表中的 `CVE` 记录包含唯一编号的条目，描述安全漏洞或暴露，以及关于它们如何被发现、如何被修复或如何工作的相关参考信息。

## Common Vulnerability Scoring System (CVSS)

**Common Vulnerability Scoring System (CVSS)** 是一种开放的安全标准，用于评估安全漏洞严重性，并根据可利用性以及成功利用时对机密性、完整性和可用性的影响等标准，生成数值相对严重性评分。

## Common Weakness Enumeration (CWE)

**Common Weakness Enumeration (CWE)** 是由 `MITRE` 策划和维护的已知软件和硬件弱点列表。弱点被定义为“软件或硬件实现、代码、设计或架构中的缺陷、故障、错误或其他错误，如果不加以解决，可能导致系统、网络或硬件容易受到攻击（<https://cwe.mitre.org/about/index.html>）”。

## Comparison Operator

**Comparison Operator** 用于将一个值与另一个值进行比较。

## Compliance Auditing

**Compliance Auditing** 是评估组织控制措施以确定其对标准和法规遵守情况的过程。

## Compliance-Based Assessment

**Compliance-Based Assessment** 是在环境中测试组织遵循和实施给定安全标准（如 `PCI`、`HIPAA`、`FISMA`）的能力。

## Configuration Auditing

**Configuration Auditing** 是将系统配置与公认最佳实践或采用的安全配置基线所描述的配置进行比较，旨在识别可能需要解决的安全问题或差异。

## Credentialed Vulnerability Scanning

**Credentialed Vulnerability Scanning** 是由获得授权用户同等权限访问系统的漏洞扫描器进行的扫描。

## Cross-Site Request Forgery (CSRF)

**Cross-Site Request Forgery (CSRF)** 是一种安全漏洞，允许攻击者向目标个人发送恶意请求，导致目标使用其已建立的会话认证执行其不打算执行的操作。这涉及发出一个或多个 `HTTP` 请求，且不包含任何不可预测的请求参数，针对仅依赖基于 `Cookie` 的会话管理的应用程序。

## Cross-Site Scripting (XSS)

**Cross-Site Scripting (XSS)** 是一种针对网站的注入攻击类型。使用此攻击，攻击者可以利用 `Web` 应用程序编程中的弱点和未能适当清理用户可控输入的失败，暂时或持久地注入恶意脚本内容。

## Daemon

**Daemon** 是任何在后台运行且不在用户直接控制下运行时执行任何功能的程序。

## Data Loss Prevention (DLP)

**Data Loss Prevention (DLP)** 是一类安全工具和流程，旨在通过基于数据分类标准和标记强制执行入站、出站和访问规则，保护数据免遭泄露或滥用。

## Data Mining

**Data Mining** 是分析大型数据集以揭示模式或隐藏异常的过程。

## Database (DB)

**Database (DB)** 是存储在计算机系统中的结构化数据或信息的有组织集合。

## Deception

**Deception** 在社会工程攻击中，欺骗是对个人身份或情况的虚假陈述，旨在说服目标执行其通常不愿执行的活动或泄露信息；欺骗技术是一种引诱攻击者遵循虚假线索以增加对攻击可见性的手段，如蜜网、蜜罐等。

## Deconfliction

**Deconfliction** 是将渗透测试工件与实际入侵或其他活动的工件区分开来的过程，以帮助解决相互矛盾的结论或响应。

## De-escalation

**De-escalation** 是一种尽快解决潜在问题以最小化或减轻影响的过程。

## Dictionary Attack

**Dictionary Attack**  
一种密码猜测攻击类型，它使用可能的密码列表作为猜测的来源。

## Distributed Denial of Service (DDoS)

**Distributed Denial of Service (DDoS)**  
一种攻击类型，旨在通过使用多个分布式攻击资源使目标无法使用。这种攻击通常试图通过向目标发送大量网络流量或请求来淹没目标，试图压垮目标的运行能力。

## DNS Forward Lookup

**DNS Forward Lookup**  
使用完全限定域名（`FQDN`）查询 `DNS` 服务器，以获取主机的 `IP` 地址。

## DNS Reverse Lookup

**DNS Reverse Lookup**  
使用 `IP` 地址查询 `DNS` 服务器，以获取与主机对应的完全限定域名（`FQDN`）。

## Domain Name System (DNS)

**Domain Name System (DNS)**  
一组标准中的一种协议，用于将计算机名称与 `IP` 地址关联。

## Domain Name System Security Extensions (DNSSEC)

**Domain Name System Security Extensions (DNSSEC)**  
`DNSSEC` 基于 `PKI` 使用数字签名来保护 `DNS` 数据，进而保护 `DNS` 事务。数据所有者对数据进行签名，确保 `DNS` 事务的数据来源认证和数据完整性保护。

## Double Tagging

**Double Tagging**  
交换机端口配置为使用原生 `VLAN` 的结果，攻击者可以构造数据包，在其原生 `VLAN` 之外预置一个伪造的 `VLAN` 标签，以绕过第 3 层访问控制。

## Dynamic Host Configuration Protocol (DHCP)

**Dynamic Host Configuration Protocol (DHCP)**  
`DHCP` 是一种网络管理协议，旨在自动为主机提供 `IP` 信息和其他网络数据（如网关和子网掩码），并在 `DHCP` 服务器上存储分配信息。

## Dynamic-Linked Library (DLL)

**Dynamic-Linked Library (DLL)**  
微软操作系统中实现的共享库概念。`DLL` 文件（`.dll` 扩展名）可以包含代码、数据和资源，很像典型的可执行程序（`.exe` 扩展名）；但是，它不能像 `.exe` 那样被直接调用。库文件可以同时支持多个计算机程序，当软件从操作系统中移除时，有时也会移除 `DLL`，使其他计算机程序容易受到 `DLL` 注入攻击。

## Elicitation

**Elicitation**  
一种社会工程学过程，用于从目标中提取有意义的信息。

## Evasion

**Evasion**  
成功挑战安全控制，例如将恶意软件部署在硬盘上杀毒软件不扫描的位置。

## Exfiltration (Exfil)

**Exfiltration (Exfil)**  
未经授权将数据从受保护空间内部移动到外部的过程，无论是通过复制、传输还是检索（例如 `SQLi` 结果的屏幕截图）。

## Extensible Authentication Protocol (EAP)

**Extensible Authentication Protocol (EAP)**  
一种用于 `WPA` 和 `WPA2` 网络的认证框架。

## Extensible Markup Language-Remote Procedure Call (XML-RPC)

**Extensible Markup Language-Remote Procedure Call (XML-RPC)**  
`XML-RPC` 是一种使用 `XML` 作为负载与服务进行远程通信的协议。它使用 `HTTP/S` 作为通信的传输机制，`XML` 作为编码机制。`XML-RPC` 经常用于 `Web` 服务，可能会受到 `XML` 序列化问题或认证问题的影响，从而暴露非预期的数据。

## False Positives

**False Positives**  
在自动或手动测试期间识别出的条件，导致对问题的错误识别。

## File Transfer Protocol (FTP/FTPS)

**File Transfer Protocol (FTP/FTPS)**  
文件传输协议（`FTP`）和基于 `SSL` 的 `FTP`（`FTPS`）是通过网络传输和接收文件的协议。

## Flow Control

**Flow Control**  
确定程序执行应如何进行（如循环）。

## Footprinting

**Footprinting**  
通过侦察识别系统或组织性质的过程。它是你塑造侦察活动并解释结果的方式。

## Fuzzing

**Fuzzing**  
一种安全测试技术，向应用程序或网络服务中的输入控件发送意外的、随机的数据以产生错误，希望发现或暴露可能被利用的安全弱点。

## General Data Protection Regulation (GDPR)

**General Data Protection Regulation (GDPR)**  
一项欧盟法律，规定了在欧盟境内个人可识别信息的处理和处理规则。该法律适用于所有存储、处理或收集欧盟境内个人可识别信息的组织和实体。

## Goals-Based Assessment

**Goals-Based Assessment**  
一种测试，约定目标的达成决定了测试的成功或失败标准，这与基于合规性的测试相反，后者的成功/失败目标由测试确定的对法规和标准的遵从程度决定。

## Graphics Processing Unit (GPU)

**Graphics Processing Unit (GPU)**  
专为加速图形渲染而设计的专用计算机硬件芯片。在渗透测试中，被密码破解工具用于加速密码哈希破解工作。

## Group Policy Object (GPO)

**Group Policy Object (GPO)**  
一组设置的集合，用于管辖 `Active Directory (AD)` 网络中的用户和计算机配置。

## Group Policy Preferences (GPP)

**Group Policy Preferences (GPP)**  
一组可选扩展，旨在扩展 `Group Policy Objects (GPOs)` 的功能。`GPP` 允许 `Active Directory (AD)` 域管理员创建域策略以自动化繁琐的任务，例如更改主机操作系统上的本地 `Administrator` 账户密码。

## Hypertext Transfer Protocol (HTTP/HTTPS)

**Hypertext Transfer Protocol (HTTP/HTTPS)**  
超文本传输协议（`HTTP`）和安全超文本传输协议（`HTTPS`）是 `Web` 服务器和 `Web` 客户端之间通信的协议。通信通常以请求和响应对的形式发生。

## Identity and Access Management (IAM)

**Identity and Access Management (IAM)**  
在云环境中，`IAM` 是一种用于控制对云资源访问的 `Web` 服务（如 `AWS`）。在更通用的计算环境中，`IAM` 是一系列管理企业内部访问的过程。

## Industrial Control System (ICS)

**Industrial Control System (ICS)**  
工业控制系统是与各类工业自动化相关的系统，例如制造、发电（发电厂）以及水处理和分配系统。

## Industrial Internet of Things (IIoT)

**Industrial Internet of Things (IIoT)**  
专为工业领域和应用而设计的 `IoT` 设备。

## Information Systems Security Assessment Framework (ISSAF)

**Information Systems Security Assessment Framework (ISSAF)**  
`ISSAF` 是一种完整的安全评估方法论，适用于安全审计以及其他类型的安全测试。它定义了渗透测试的三个阶段：规划和准备、评估和报告、清理。`ISSAF` 为业务管理提供最佳实践，包括评估前和评估后的行动、风险评估方法论，以及各类安全评估（不仅限于渗透测试）的信息收集。

## Infrastructure as a Service (IaaS)

**Infrastructure as a Service (IaaS)**  
一种云计算服务，提供按需的网络、存储和计算资源。

## Insider Threat

**Insider Threat**  
一种拥有组织内部知识或拥有组织信息系统特权访问权限的个人，其动机基于因被解雇而产生的报复心理，或寻求出售机密以获取经济利益。

## Intelligent Platform Management Interface (IPMI)

**Intelligent Platform Management Interface (IPMI)**  
`IPMI` 是一种硬件技术，其协议允许使用基板管理控制器（`BMC`）或管理控制器（`MC`）远程管理服务器硬件。示例包括 `HP iLO`、`Dell DRAC` 和 `Supermicro IPMI`。使用 `IPMI`，管理员可以监控和管理外设及其他硬件、执行重启，甚至可以在操作系统之外重新安装主机。利用某些系统提供的 `KVM` 访问，攻击者甚至可能利用此功能远程交互式地访问操作系统。

## International Mobile Equipment Identity (IMEI)

**International Mobile Equipment Identity (IMEI)**  
`IMEI` 号码是每个移动设备特有的 15 位数字，用于在移动网络上识别设备。

## International Organization for Standardization (ISO)

**International Organization for Standardization (ISO)**  
`ISO` 是一个由多国标准机构组成的非政府组织。`ISO` 制定并发布国际标准。一个例子是 `ISO/IEC 27001`，这是一个信息安全管理标准。

## Internet Control Message Protocol (ICMP)

**Internet Control Message Protocol (ICMP)**  
一种网络协议，用于在与另一个 `IP` 地址通信时，在网络设备之间发送错误消息和操作信息。最常见于 `ping` 和 `traceroute` 的使用中。

## Internet of Things (IoT)

**Internet of Things (IoT)**  
具有嵌入式传感器、软件和其他技术的物理设备、对象、机器，甚至动物，它们连接到网络并与互联网上的其他设备交换数据，而无需人工干预。大多数智能设备（恒温器、冰箱、摄像头等）都属于这一类，但心脏起搏器、生物芯片和汽车传感器也符合资格。

## Internet Protocol (IP)

**Internet Protocol (IP)**  
`IP` 是互联网使用的网络层通信协议。

## Internet Service Provider (ISP)

**Internet Service Provider (ISP)**  
`ISP` 是为个人和组织提供互联网连接和服务的公司。

## Intrusion Prevention System (IPS)

**Intrusion Prevention System (IPS)**  
`IPS` 是以软件或硬件实现的网络安全控制，用于检查网络流量中的攻击模式，并主动阻止该流量到达其预期目标，或根据检测到的行为发出警报，以便采取其他行动（如入侵检测系统 (`IDS`) 设置的情况）。

## iOS App Store Package (IPA)

**iOS App Store Package (IPA)**  
一个 `Zip` 压缩归档文件，包含在 `Apple iOS` 移动架构上运行应用程序所需的文件。

## iOS Simulator

**iOS Simulator**  
`iOS` 开发工具包 (`XCode`) 的一项功能，可模拟 `iDevice` 的基本行为及其与 `iOS` 应用程序的交互方式。

## Jailbreaking

**Jailbreaking**  
利用 `iOS` 中的软件漏洞以获得提升权限（即 `root`）的低级执行能力，从而移除 `Apple` 施加的限制，以自定义设备并安装未经批准的应用程序的过程。

## Java Archive (JAR)

**Java Archive (JAR)**  
一种包文件格式，将 `Java` 应用程序成功执行所需的所有资源（类文件、图像、文本等）打包成一个资源。

## JavaScript Object Notation (JSON)

**JavaScript Object Notation (JSON)**  
`JSON` 是一种轻量级、自描述、人类可读的结构化数据格式。

## Joint Test Action Group (JTAG)

**Joint Test Action Group (JTAG)**  
一种用于调试和连接电路板上嵌入式设备的标准类型。

## Kerberos

**Kerberos**

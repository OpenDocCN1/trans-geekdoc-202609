
蜜罐是发现网络上出现问题的绝佳方式。其思想是：如果攻击者进入网络，首先会扫描网络以寻找漏洞。通常这涉及扫描局域网 IP 范围内的所有 IP 地址，或是所有端口或最可能用于横向移动的端口。蜜罐会在网络的一个 IP 地址上运行，并监听所有端口。若有其他设备尝试连接蜜罐，则会触发警报并发送通知。Thinkst Canary 是一种蜜罐，能够模拟 Windows 服务器或 Web 服务器，旨在诱使攻击者进一步探查，并在触发警报前进行更多调查（Thinkst Canary，2018）。

## 1.5.2. Detecting attacks by network monitoring

Darktrace 和 Snort 等网络流量监控工具是发现异常的优秀选择。但流量监控成本高昂，因为其目标是检测网络上的任何异常行为。实际操作中，新建工作站、大量程序和数据的搬迁，甚至 Windows 更新，都可能产生误报，导致误报警，因此该方法并非没有缺陷。

## 1.6. Detection of Security Breaches — Overview

在比较安全产品时，一个关键问题在于缺乏用于数据外泄测试的综合数据集，也没有通用的测试框架。此问题被 Ullah *et al.*（2017）指出。

Al-Bataineh 和 White（2017）描述了如何利用 botnet 通过加密通道进行数据外泄。有趣的是，他们指出加密本身可以暴露攻击者：大规模加密传输可能被视为异常行为。Zeus 是最常见的 botnet，允许攻击者远程管理 botnet 以记录键盘输入、截图，甚至在表单中添加字段以收集比常规表单更多信息；在银行网站上，甚至可能要求社保号码或信用卡 PIN。Al-Bataineh 和 White 观察到 botnet 交换的 HTTP 流量拥有正常的报头，但 POST 响应内容往往是随机的，这有助于检测。虽然加密隐藏了攻击者的具体操作，但他们建议应“将加密视为检测的机会而非局限，因为如果在不 expected 的位置检测到加密，则应将其视为异常”。

在加密消息中，每个字节的频率应保持一致，这称为香农熵（Shannon’s Entropy）。为保持数据流的吞吐量，制造商在识别文件类型后，可能决定只检查文件开头而无需检查其余数据流（Shannon and Weaver，1949）。

在一些防火墙上，递归包检查（DPI）HTTPS 包的技术正在兴起。该技术通过在防火墙处解密加密通道，然后在转发至用户前重新加密。

在除小型企业网络外的环境中，代理服务器通常是必需的，这已成为 PCI DSS 问卷 C 以及英国 Cyber Essentials 方案的要求。代理服务器用于检查和记录下载的数据，但不一定能够检测和记录上传的数据。从攻击者的角度，利用基于 Web 的服务外泄数据可能看起来风险较高，因为请求通常会被记录；即便网站访问、用户下载等都被记录，也并不意味着上传的数据会被记录。

异常检测可分为主机基于和网络基于两种，前者在主机层面寻找异常，后者在网络流量层面寻找异常。例如，上传流量大于下载流量的网络使用即为可疑网络流量。主机基于的异常例子包括非工作时间（如夜间）出现高水平的网络流量（Darktrace，2018）。

### 1.6.1. Black hat, white hat and grey hat hacking

为检查漏洞是否可被利用，伦理黑客或渗透测试人员通常被雇佣。他们基于系统知识（灰色 hat）、无知识（黑色 hat）或大量知识（白色 hat）来寻找并利用漏洞。必须使用可信赖的公司进行此类测试，并在系统测试时有系统管理员在场，以防服务因测试而挂起。未经授权的系统入侵属于犯罪行为，因此渗透测试公司必须确保已获得适当授权，并充分了解可能的不良后果后才能尝试发现漏洞。

### 1.6.2. Open-sourcing of security tools

- Many security tools are available open source for Linux. Bro is another tool for network analysis and security monitoring (Bro, 2018). Snort is an open source intrusion prevention system capable of real-time traffic analysis and packet logging. Pfsense is an increasingly popular open source firewall (Pfsense, 2018).

## 1.7. Methods and Models for Security and Privacy

从 Ullah *et al*. (2017) 可以看出，学术研究中提出的许多用于检测和防止数据丢失的方法尚未在真实企业中进行测试，仍然是学术性的想法，而实施某些想法的实用性被忽视了。

所选的数据分类模型将取决于组织持有的数据类型。对于许多组织而言，这仅包括机密、个人数据以及未分类数据。在军事背景下，机密数据会基于“需要知道”的原则进行访问，因此高级军官可能无法访问某些数据，而低级别的项目成员则可能拥有这些数据。“需要知道”或“最小权限”是许多组织中常见的安全实践。

像 iManage (iManage, 2018) 和 Laserfiche 这类文档管理系统是保护文档的良好方式，因为这些系统将文档存储在仓库中而非文件共享中，从而增加了额外的安全层。随后通过文档管理系统设置的访问权限进一步提供了保护。

### 1.7.1. Methods for security reengineering

电子邮件是许多组织的生命线，然而在与其他方达成合同时，它很快显现出效率低下的问题。各方存储的多个草稿文档版本不仅会拥堵电子邮件系统，还会占用文件存储和消息归档空间。一些产品通过门户式解决方案改善了这一体验，并且部分产品还支持在线文档比较，这使得整个协作过程可以完全在线完成。例如 Objective-Connect、iDeals 数据室和 Workshare。SharePoint 也可以配置提供此类功能。

像 iDeals、Workshare 和 Objective-Connect 这样的产品提供安全的在线虚拟数据室，供公司与其他方共享文档。这些系统比电子邮件提供了更高效的协作方式。门户的使用已在大型企业、地方政府和高校中普及，消除了通过电子邮件发送大附件的需求。提供此类功能的产品包括 Objective Connect (Objective, 2017)，它允许用户在门户中共享和管理文档的版本，iDeals 则提供具有非常严格查看权限的文档共享功能，DeltaView’s Workshare 在门户中提供文档比较功能。

Blackberry UEM 是提供移动访问 Exchange Server 的另一种方式。这是一个完整的 MDM 解决方案，可实现移动设备以及运行 Blackberry 的 iOS 或 Android 应用的设备的连接。它仅使用出站端口，从而消除了因配置入站端口而产生的安全威胁 (Blackberry, 2018)。

### 1.7.2. Privacy-enhancing technologies and trustworthy information systems

常见的做法是为文档添加关键词标签，然后使用像 ClamAV 这样的防病毒工具生成签名。该签名随后可添加到像 Squid 这样的代理服务器中，以阻止数据离开组织 (Rashid *et al*., 2017)。

Boldon James 提供工具在文档中添加元数据标签 (Boldon James, 2018)。这些标签可与 Forcepoint、Intel Security 和 Symantec DLP 等数据丢失防泄漏系统配合使用。

Tukan’s GREENmod (TukanIT, 2018) 是另一款工具，它与 McAfee Threat Intelligence Exchange/Data eXchange Layer (TIE/DXL) 以及 McAfee DLP (McAfee, 2017) 集成，用于防止数据外泄。

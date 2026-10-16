

## 7. 以单独一行的点结束命令。

![tip](img/tip.png)在第一个 Telnet 提示符处输入 `?` 或 `help` 可查看所有受支持的命令，并根据服务器不同获得命令使用帮助。

最后的点标记消息结束。输入完该点后，若允许中继，消息将被发送。

## 8. 检查服务器是否允许中继：

* 观察是否收到类似 `Relay not allowed` 的回复。

  如果收到此类信息，则 SMTP 中继在服务器上未启用或因安全过滤被阻止（许多服务器会阻止看似从外部发来但实际来源于内部的消息）。

* 若未收到任何回复，请检查收件箱是否收到已中继的邮件。

  若收到测试邮件，则说明服务器已启用 SMTP 中继，可能需要将其禁用，以免让垃圾邮件发送者或攻击者借此发送大量垃圾邮件或被列入黑名单，进而影响业务。

## COUNTERMEASURES AGAINST SMTP RELAY ATTACKS

你可以在邮件服务器上实施以下防范措施，以禁用或至少控制 SMTP 中继：

* **禁用邮件服务器上的 SMTP 中继。** 中继默认应已被禁用，但最好自行核查。如果不确定是否需要中继，通常不需要。你可以在服务器或防火墙配置中为特定主机启用中继。

* **如果服务器支持，强制要求身份验证。** 你可以要求与邮件服务器域匹配的电子邮件地址进行密码验证。请参阅邮件服务器和客户端文档，了解如何配置此类验证。

## Email header disclosures

如果您的电子邮件客户端和服务器使用常见的默认配置，恶意攻击者可能会获取以下关键信息：

* 电子邮件客户端机器的内部 IP 地址（可能导致内部网络的枚举，进而通过钓鱼和/或后续恶意软件感染进行利用）。

* 客户端和邮件服务器的软件版本，以及它们的漏洞。

* 主机名，这些主机名可能泄露您的网络命名约定。

## TESTING

Figure 14-10 显示了我向免费网络账户发送的测试邮件中泄露的邮件头信息。如您所见，它泄露了关于我的邮件系统相当多的信息：

* 第三行 Received 信息披露了我的系统的主机名、IP 地址、服务器名称以及电子邮件客户端软件版本。

* X-Mailer 行显示了我用来发送此消息的 Microsoft Outlook 版本。

![ FIGURE 14-10: Critical information revealed in email headers.](img/9781119485476-fg1410.png)

FIGURE 14-10: 邮件头中泄露的关键信息。

## COUNTERMEASURES AGAINST HEADER DISCLOSURES

防止邮件头信息泄露的最佳措施是配置您的邮件服务器或邮件防火墙，通过修改显示的信息或将其删除来重写邮件头。请查看邮件服务器或防火墙的文档，确认是否可以使用此方法。

如果重写邮件头不可用（或被您的互联网服务提供商禁止），您仍然可以阻止发送某些关键信息，例如服务器软件版本号和内部 IP 地址。

## Capturing traffic

邮件流量（包括用户名和密码）可以通过网络分析仪或邮件数据包捕获器和重构器来捕获。

![tip](img/tip.png)Mailsnarf 是 dsniff 包的一部分，它是一个邮件数据包捕获器和重构器（[`http://sectools.org/tool/dsniff`](http://sectools.org/tool/dsniff)）。此外，还有一款商业（且低成本）程序叫 NetResident（[`www.tamos.com/products/netresident`](http://www.tamos.com/products/netresident)）。您也可以使用 Cain & Abel（[`www.oxid.it/cain.html`](http://www.oxid.it/cain.html)）来突出邮件传输中的弱点。我在第 8 章（`#c08.xhtml`）中介绍了使用该工具及其他工具进行密码破解的方法。

如果流量被捕获，黑客或恶意内部人员可以入侵一台主机，并可能获得对相邻主机（如您的邮件服务器）的完整访问权限。

## Malware

电子邮件系统经常受到病毒和蠕虫等恶意软件的攻击。最重要的测试之一是验证您的防病毒软件是否正常工作。

![remember](img/remember.png)在开始测试防病毒软件之前，请确保您已加载最新的防病毒软件引擎和签名。

EICAR 提供了一个安全的选项，用于检查防病毒软件的有效性。尽管 EICAR 并非全面的恶意软件漏洞测试方法，但它是一个良好的、安全的起点。

EICAR 是一家欧洲基地的恶意软件思维库，它与防病毒供应商合作，提供这一基本系统测试。EICAR 测试字符串会以邮件正文或文件附件的形式传输，以便您观察服务器和工作站的响应。您在计算机上加载包含以下 68 个字符的文件，以查看防病毒软件或其他防病毒软件是否能够检测到它：

`X5O!P%@AP4\PZX54(P^)7CC)7)$EICAR STANDARD-ANTIMALWARE-TEST-FILE!$H+H*`

![tip 您可以从 [`www.eicar.org/86-0-Intended-use.html`](http://www.eicar.org/86-0-Intended-use.html) 下载包含该字符串的文本文件。该站点提供多个版本的文件。我建议使用压缩文件进行测试，以确保您的防病毒软件能够检测压缩文件中的恶意软件。

运行此测试时，您可能会看到防病毒软件的结果类似于 Figure 14-11。

![ FIGURE 14-11: Using the EICAR test string to test antimalware software.](img/9781119485476-fg1411.png)

FIGURE 14-11: 使用 EICAR 测试字符串测试防病毒软件。

![remember](img/remember.png)除了测试防病毒软件外，您还可以使用本书中介绍的其他工具来攻击电子邮件系统。Metasploit（[`https://www.metasploit.com`](https://www.metasploit.com)）可帮助您发现 Exchange 等服务器的缺失补丁，这些补丁可能被黑客利用。Brutus（[`www.hoobie.net/brutus`](http://www.hoobie.net/brutus)）可用于测试 POP3/IMAP 密码的破解，以及网页邮件系统的网页密码。

## 一般最佳实践：最小化电子邮件安全风险

以下措施有助于尽可能保持消息的安全。

### 软件解决方案

正确的软件可以中和许多威胁：

* 在邮件服务器上（更好是邮件网关）使用防病毒软件，以防止恶意软件到达电子邮件客户端。Google 和 Microsoft 等云端邮件服务通常已内置此类防护。在客户端上使用防病毒软件是必然的。

* 持续且在安全警报发布后及时应用最新的操作系统（OS）和邮件服务器安全补丁。

* 加密（在合理的前提下）。您可以使用传统的 S/MIME 或 PGP 加密敏感消息，或在桌面、服务器或邮件网关层面使用邮件加密。更佳（更易）的做法是使用 TLS 通过 POP3S、IMAPS 和 SMTPS 协议加密。最佳选择可能是使用支持通过 Web 浏览器通过 HTTPS 发送和接收加密邮件的邮件安全硬件或云服务，例如 G Suite 和 Office 365。

  ![warning](img/warning.png)不要依赖用户自行加密消息。与任何其他安全策略或控制一样，依赖用户做出安全决策往往效果不佳。应使用企业解决方案自动加密消息。

  ![remember](img/remember.png)确保加密文件和邮件能够防范恶意软件。加密不能阻止恶意软件进入文件或邮件，它只是使恶意软件在文件或邮件中保持加密状态。加密会阻止服务器或网关防病毒软件在恶意软件到达桌面之前检测到该恶意软件。

* 制定政策，要求用户不要打开来自陌生发送者或不可信来源的电子邮件附件，并开展持续的意识宣传和提醒。

* 为那些忽视或忘记遵守“不打开 unsolicited emails and attachments”政策的用户做好准备。这会发生！某些软件（如 Microsoft Outlook 和 Windows SmartScreen）可以帮助用户识别恶意内容。

### 操作指南

一些简单的操作规则可以让防火墙保持高，攻击者难以进入您的电子邮件系统：

* 将邮件服务器放在与 Internet 和内部 LAN 处于不同网络段的防火墙后面，最好放在非军事区（DMZ）中，或使用邮件网关。

* 通过禁用邮件服务器上未使用的协议和服务来加硬化系统。

* 如果可能，在专用服务器上运行邮件服务器并进行恶意软件扫描（甚至可以将入站和出站消息分开）。这样可以在邮件服务器被入侵时，防止恶意攻击扩散到其他服务器和信息。

* 记录所有与服务器的交易，以便在需要时进行调查。务必监控这些日志！如果无法证明监控的必要性，可考虑将此功能外包给托管安全服务提供商。

如果你的服务器不需要运行特定的电子邮件服务（SMTP、POP3 和 IMAP），请立即禁用它们。

对于基于 Web 的电子邮件服务，例如 Microsoft 的 Outlook Web Access（OWA），请通过本书中提到的测试技术和硬化资源，正确测试并保护你的 Web 服务器应用程序和操作系统。

强制使用强密码。对于独立账户以及域级 Exchange 或类似账户，网络中的任何密码弱点都会传递到电子邮件，并被通过 Outlook Web Access 或 POP3 利用。我在 第 8 章 中介绍了密码破解。

请确保在你的漏洞扫描和渗透测试中包含邮件服务器。

如果你运行的是 sendmail（尤其是旧版本），请不要使用它。考虑改用安全的替代方案，例如 Postfix（[www.postfix.org](http://www.postfix.org)）或 qmail（[www.qmail.org](http://www.qmail.org)）。

## 了解 VoIP

当今企业中广泛使用的技术是 Voice over Internet Protocol（VoIP）。内部 VoIP 系统、远程用户系统、VoIP 服务器、软电话以及相关组件都有各自的安全漏洞。与大多数安全相关事务一样，许多人并未考虑到 voice conversations 通过网络或 Internet 传输时的安全问题，但这些问题必须列入你的视野。别担心——这还来得及纠正。只要记住，即使已有防护措施，VoIP 系统仍需在你的整体安全测试策略中持续纳入。

### VoIP 漏洞

正如任何技术或网络协议集合一样，坏人总会找到办法进入系统。VoIP 也不例外。事实上，考虑到电话通话和系统可用性的重要性，你损失的潜在风险更大。

VoIP 相关系统的安全性与其他常见计算机系统并无明显差异。原因在于：VoIP 系统拥有自己的操作系统，拥有 IP 地址，并且可在网络中访问。更糟的是，许多 VoIP 系统包含更多“智能”（即更多可能出错的内容），这使得 VoIP 网络更容易被攻击。

![tip](img/tip.png)如果你想了解 VoIP 的工作原理，这将有助于你发现漏洞，请参考 *VoIP For Dummies*，作者 Timothy V. Kelly（John Wiley & Sons, Inc.）。

一方面，VoIP 系统的漏洞与本书其他系统相似，包括默认设置、缺失补丁和弱密码。因此，使用本文中介绍的标准漏洞扫描工具至关重要。图 14-12 展示了 VoIP 适配器 Web 界面认证机制的多种漏洞。

![ FIGURE 14-12: A WebInspect scan of a VoIP network adapter showing several weaknesses.](img/9781119485476-fg1412.png)

FIGURE 14-12: A WebInspect scan of a VoIP network adapter showing several weaknesses.

观察这些结果，你可能会认为该设备是基础的 Web 服务器。这正是我的要点：VoIP 系统不过是网络化的计算机系统，拥有可被利用的漏洞。

另一方面，两大与 VoIP 相关的安全弱点：

* **电话服务中断**：是的，VoIP 易受 DoS 攻击，和任何其他系统或应用一样。由于人们对音质的容忍度极低（手机除外），VoIP 与时敏感型应用一样脆弱。

* **缺乏加密**：VoIP 的另一大弱点是通话通常不加密，导致可被拦截和录制。想象一下，坏人可以录下对话并进行勒索。这种攻击在未保护的无线网络上极易实施，但如我在即将到来的章节“捕获和录制声音流量”中所示，有线网络同样容易受到影响。

![warning](img/warning.png)如果 VoIP 网络未通过网络分段（如 VLAN）进行保护，声音网络将特别容易窃听、DoS 及其他攻击。但 VLAN 防线在许多环境中可被称为 VoIP Hopper（[`voiphopper.sourceforge.net`](http://voiphopper.sourceforge.net)）所突破。当你以为声音系统已安全时，这类工具会出现，它们虽旧，但仍可用于此类测试。

与常规计算机安全漏洞不同，VoIP 问题并非仅靠简单的软件补丁即可解决。它们根植于 Session Initiation Protocol（SIP）和 Real-Time Transport Protocol（RTP），VoIP 用于通信的两种协议。下面的章节将介绍两项专注于 VoIP 的测试方法，帮助你评估声音系统的安全性。

![tip](img/tip.png)需要注意的是，尽管 SIP 是最常用的 VoIP 协议，H.323 也存在，因此如果使用的是 H.323，请不要浪费时间测试 SIP 漏洞。请参阅 [www.packetizer.comi/ipmc/h323_vs_sip](http://www.packetizer.comi/ipmc/h323_vs_sip) 获取 H.323 与 SIP 的详细对比。

### 漏洞扫描

除基本的网络、操作系统和 Web 应用漏洞外，使用合适的工具可以发现 VoIP 问题。好消息是，你很可能已经拥有这些工具——网络漏洞扫描仪如 Nexpose（[`www.rapid7.com/products/nexpose`](https://www.rapid7.com/products/nexpose)），以及 Web 漏洞扫描仪如 Netsparker（[`www.netsparker.com`](https://www.netsparker.com)）。VoIP 呼叫管理器和电话中常见的弱密码、跨站脚本以及未打补丁的漏洞，可利用 Metasploit 等工具进行利用。

![tip](img/tip.png)Kali Linux 内置了多种 VoIP 工具，位于 Applications/Vulnerability Analysis/VoIP Tools。其他免费的 SIP 流量分析工具包括 PROTOS（[www.ee.oulu.fi/research/ouspg/protos/testing/c07/sip/index.html](http://www.ee.oulu.fi/research/ouspg/protos/testing/c07/sip/index.html)）和 sipsak（[`www.voip-info.org/wiki/view/Sipsak`](https://www.voip-info.org/wiki/view/Sipsak)）。一个汇总了大量 VoIP 相关工具的网站是 [www.voipsa.org/Resources/tools.php](http://www.voipsa.org/Resources/tools.php)。

### 捕获和录制声音流量

如果你能访问有线或无线网络，轻松捕获 VoIP 对话，这能有效证明网络及 VoIP 部署的漏洞。

![warning](img/warning.png)涉及电话通话窃听的法律问题很多，请确保已获得授权，并小心使用测试结果，避免滥用。

你可以使用 Cain & Abel（这里演示的功能实际上是 Cain）来窃听 VoIP 对话。免费下载地址为 [www.oxid.it/cain.html](http://www.oxid.it/cain.html)。使用 Cain 的 ARP poison routing 功能，你可以插入网络并通过以下步骤让它捕获 VoIP 流量：

1. **加载 Cain & Abel，点击 Sniffer 标签进入网络分析模式。** 默认会打开 Hosts 页面。

2. **点击带有核废料标志的 Start/Stop APR 图标。** ARP poison routing 过程开始并启用内置嗅探器。

3. **点击蓝色加号（+）图标，添加用于 ARP 中毒的主机。**

4. 在出现的 `MAC Address Scanner` 窗口中，确保选择 `All Hosts in My Subnet`，然后点击 OK。

5. 点击 `APR` 标签页（带有黄黑圆形图标的那个）以加载 APR 页面。

6. 点击最上方 `Status` 列标题下方的空白区域（在 `Sniffer` 标签页下方）。

   这一步会重新启用蓝色的 `+` 图标。

7. 点击蓝色的 `+` 图标。

   `New ARP Poison Routing` 窗口会显示步骤 3 中发现的主机。

8. 选择默认路由或其他你想要捕获数据包的主机（发往和发自该主机的流量）。

   我选择默认路由，但你也可以考虑选择你的 SIP 管理系统或其他中央 VoIP 系统。右侧列会填充所有剩余的主机。

9. 在右侧列中，使用 `Ctrl+click` 选择你想要“中毒”的系统，以捕获其语音流量。

   我选择我的 VoIP 网卡，但你也可以考虑选择所有 VoIP 电话。

10. 点击 OK 以启动 ARP 中毒过程。

     该过程根据你的网络硬件和每个主机的本地 TCP/IP 栈，可能需要几秒钟到几分钟。

11. 点击 `VoIP` 标签页。

     所有语音对话都会被记录。

     这里的有趣之处是：对话会以 `.wav` 音频文件格式保存，因此你只需右键单击想要测试的已录制对话，在上下文菜单中选择 **Play**（播放），如图 14-13 所示。正在记录的对话在状态列中会显示 **Recording**。

![ FIGURE 14-13: Using Cain & Abel to capture, record, and play back VoIP conversations.](img/9781119485476-fg1413.png)

FIGURE 14-13: 使用 Cain & Abel 捕获、记录并回放 VoIP 对话。

Cain 等工具的语音质量取决于 VoIP 设备所使用的编码器。使用我的设备，我发现质量最好也只能说是一般般，但这并不算大问题。你的目标是证明漏洞的存在——而不是窃听他人的对话。

你也可以使用名为 **vomit**（全称 *voice over misconfigured Internet telephones*）的基于 Linux 的工具，它可以将 VoIP 对话转换为 `.wav` 文件。首先，你需要使用 **tcpdump** 捕获真实对话，但如果 Linux 是你的首选，该方案同样能实现与 Cain 相同的结果，步骤如前述。

![tip](img/tip.png)如果你将大量时间用于 VoIP 工作，我强烈建议你投资一款优质的 VoIP 网络分析仪。查看 Savvius 的 Omnipeek，它是一款优秀的有线和无线分析器（[`www.savvius.com/product/omnipeek`](https://www.savvius.com/product/omnipeek)），以及 TamoSoft 的 CommView（[www.tamos.com/products/commview](http://www.tamos.com/products/commview)），后者是一个功能强大且价格更低的替代品。

这些 VoIP 漏洞仅是冰山的一角。新系统、软件和相关协议不断出现，保持警惕以确保你的对话免受恶意人员的攻击。如前所述，只要有 IP 地址或 URL，就可能成为攻击目标。

## 针对 VoIP 漏洞的防范措施

加固 VoIP 可能很棘手。不过，你可以从以下步骤开始：将语音网络划分为独立的 VLAN，或如果预算允许，甚至划分为独立的物理网络。进一步隔离任何连接 Internet 的系统，确保不是随意任何人都能连接（这一点在我看到的情形中很常见）。你还应确保所有 VoIP 相关系统均按照厂商的建议和公认的最佳实践（如 NIST 的 SP800-58 文档 https://csrc.nist.gov/publications/detail/sp/800-58/final）进行硬化，并且软件和固件需定期且持续地进行补丁。最后，定期使用网络漏洞扫描工具（如 Nexpose 或 Nessus）对语音相关系统进行扫描。如果所有的电话都是同一型号和版本，你可能只需要测试其中的一小部分。但请注意，我在观察到，当对这些电话及相关语音设备运行漏洞扫描时，它们有时会出现异常行为。

第 15 章

## Web Applications and Mobile Apps

## IN THIS CHAPTER

![check](img/check.png)**Testing websites and web applications**

![check](img/check.png)**Uncovering flaws in mobile apps**

![check](img/check.png)**Protecting against SQL injection and cross-site scripting**

![check](img/check.png)**Preventing login weaknesses**

![check](img/check.png)**Analyzing software flaws manually**

![check](img/check.png)**Countering web abuse**

![check](img/check.png)**Analyzing source code**

网站和 Web 应用是攻击的常见目标，因为它们无处不在，且任何人都可以随意探测。用于营销、联系方式、文档下载等的基本网站尤易受攻击。像 WordPress 这类常用内容管理系统因其广泛使用且缺乏足够测试和补丁而特别容易成为攻击目标。对于黑客而言，这些网站提供了进入复杂应用和数据库的入口，数据库中存储的信用卡号、社会安全号等宝贵信息正是他们关注的重点，无论是字面上还是 figuratively。

网站和应用之所以容易受攻击，共识是因为开发和测试的软件实践不佳。这很容易让人联想到操作系统以及几乎所有计算机系统（包括汽车和物联网设备）所面临的同样问题。这种局面是依赖软件编译器进行错误检查、对更高质量软件的用户需求存疑以及过度强调上市时间和易用性而非安全性的副作用。

本章提供针对网站、应用和移动 app 的安全测试方法。鉴于配置可能性的多样性和系统的复杂性，你可以检测到成千上万种软件漏洞。本章我主要关注我在使用自动化扫描工具和手动分析时最常遇到的漏洞，并列出相应的缓解措施，以降低恶意人员对你最关键业务系统发起攻击的可能性。

![remember](img/remember.png)我想指出，本章仅涉及所有可能的软件安全缺陷及其测试方法的表面部分。进一步提升 Web 安全测试技能的资源包括 Open Web Application Security Project（OWASP）提供的 **Top 10 Web Application Security Risks** 和 **Top 10 Mobile Risks**（https://www.owasp.org/index.php/Main_Page）。

## 选择你的 Web 安全测试工具

良好的 Web 安全测试工具能让你在工作中取得事半功倍的效果。正如生活中许多事物，我在测试 Web 安全漏洞时发现：**你得到的往往与所付出的代价相匹配**。因此，我主要使用商业工具来对网站和 Web 应用进行漏洞测试。

以下是我喜欢的 Web 安全测试工具：

* **Acunetix Web Vulnerability Scanner**（https://www.acunetix.com）— — 一款全能的 Web 安全测试工具，集成了端口扫描和 HTTP 抓包功能。

* **BURP proxy**（https://portswigger.net/burp/communitydownload）— — 用于 HTTP 代理捕获和分析的工具。

* [Netsparker](https://www.netsparker.com) 用于一站式安全测试，通常能发现其他工具可能漏掉的漏洞。

* [Web Developer](http://chrispederick.com/work/web-developer) 用于手动分析和操作网页。

还有许多其他专注于浏览器的工具，适合 Firefox 和 Chrome，可在 [`http://resources.infosecinstitute.com/use-firefox-browser-as-a-penetration-testing-tool-with-these-add-ons`](http://resources.infosecinstitute.com/use-firefox-browser-as-a-penetration-testing-tool-with-these-add-ons) 和 [`http://resources.infosecinstitute.com/19-extensions-to-turn-google-chrome-into-penetration-testing-tool`](http://resources.infosecinstitute.com/19-extensions-to-turn-google-chrome-into-penetration-testing-tool) 查看。

![remember](img/remember.png)是的，你必须进行手动分析。你肯定想使用扫描器，因为扫描器能发现大约一半的问题。对于剩下的一半，你必须在扫描器之外继续深入，才能真正评估网站和应用的整体安全性。你需要进行一些手动工作，原因不是扫描器不可靠，而是手动探查 web 系统需要传统黑客技巧和你最喜欢的浏览器来完成——这些操作目前仍无法完全自动化。

你也可以使用像 Nexpose 和 Nessus 这样的通用网络漏洞扫描器，以及像 Metasploit 这样的利用工具来测试网站和应用。这些工具可帮助你在标准网络扫描工具和手动分析之外，发现（并利用）服务器层面的弱点，这些弱点可能在常规网络扫描和手动分析中被忽视。Google 也能帮助你在网站和应用中挖掘敏感信息。虽然这些非特定于应用的工具有用，但它们不会像前面列出的工具那样深入挖掘。

### 寻找 Web 漏洞

通过超文本传输协议（HTTP）对易受攻击的网站和应用进行攻击，构成了所有互联网相关攻击的大多数。大多数这些攻击即使通过 HTTPS（即通过 SSL/TLS 加密的 HTTP）进行，也能被完成，因为攻击的关键不在于传输通道，而在于网站和应用本身，或在于它们运行的服务器和浏览器软件。

许多针对网站和应用的攻击只是小烦恼，可能不影响敏感信息或系统可用性。但有些攻击会严重破坏系统，使敏感信息面临风险，甚至导致组织违反国家、联邦和国际层面的信息隐私与安全法律法规。

#### 目录遍历

我先给你展示一个简单的目录遍历攻击。目录遍历是一种基础弱点，但它可能会暴露出关于 web 系统的有趣甚至敏感的信息。该攻击涉及浏览站点，寻找服务器目录结构以及可能被有意或无意加载的敏感文件的线索。

请执行以下测试，以确定你的网站的目录结构。

##### 抓取器

像免费 HTTrack Website Copier（[`https://www.httrack.com`](https://www.httrack.com)）这样的爬虫程序可以抓取你的站点，查找所有公开可访问的文件。使用 HTTrack 时，加载它，为项目命名，并指定要镜像的网站。几分钟后（或根据站点大小和复杂度可能需要数小时），你的本地磁盘（如 `c:\My Web Sites`）将存储该站点上所有公开可访问的内容。图 15-1（Figure 15-1）展示了一个基本网站的抓取输出。

![ FIGURE 15-1: Using HTTrack to crawl a website.](img/9781119485476-fg1501.png)

FIGURE 15-1: 使用 HTTrack 对网站进行抓取。

复杂站点往往会暴露更多不该公开的信息，包括旧数据文件以及应用脚本和源代码。

![warning](img/warning.png)在进行网络漏洞和渗透测试时，我常常会在服务器上发现 `.zip` 或 `.rar` 文件。有时这些文件只是垃圾，但更常见的是它们包含公众不应能访问的敏感信息。一个特别突出的案例是，我发现了一个 `.zip` 文件，尝试打开时，WinZip 要求输入密码。我使用 ElcomSoft 的密码破解工具（见第 8 章 Chapter 8 了解详情）在几毫秒内破解了密码。打开该 `.zip` 文件后，里面是一份包含敏感健康信息（姓名、地址、社会安全号码等）的 Microsoft Excel 表格，任何人都可以访问。在这类情况下，你的业务可能需要通知所有受影响人员其信息保护不当并可能已被泄露。了解影响你业务的法律法规很重要，最好事先确保用户不在你的服务器上上传不当保护的敏感信息！

查看抓取程序的输出，看看哪些文件可用。普通的 HTML 和 PDF 文件通常是可以接受的，因为它们是正常网页使用所必需的。但还是不妨逐一打开这些文件，确认它们确实属于站点且不包含你不想公开的敏感信息。

##### Google

你也可以使用 Google 进行目录遍历。事实上，Google 的高级查询功能足够强大，你可以直接在搜索框中输入高级语句，快速定位敏感信息、关键服务器文件和目录、信用卡号、网络摄像头——Google 已经索引的任何内容，无需手动镜像站点再遍历所有文件。

下面是几条高级查询示例，可直接在 Google 搜索框中输入：

* **`site:hostname keywords`** ：搜索包含你列出的任意关键词（如 *SSN*、*confidential*、*credit card*）的页面。例如：  

  `site:www.principlelogic.com` speaker

* **`filetype:file-extension site:hostname`** ：搜索特定文件类型的特定网站，如 `doc`、`pdf`、`db`、`dbf`、`zip`。这些文件可能包含敏感信息。例如：  

  `filetype:pdf site:www.principlelogic.com`

其他高级 Google 操作符包括：

* `allintitle`：搜索关键词出现在网页标题中的结果。
* `inurl`：搜索关键词出现在 URL 中的结果。
* `related`：找出与当前页面相似的页面。
* `link`：显示链接到当前页面的其他站点。

更多定义和用法请参考 [`www.googleguide.com/advanced_operators.html`](http://www.googleguide.com/advanced_operators.html)。许多漏洞扫描器也会检查 Google Hacking Database（GHDB）站点（[`https://www.exploit-db.com/google-hacking-database`](https://www.exploit-db.com/google-hacking-database)）。

![tip](img/tip.png)在使用 Google 搜索浏览您的网站时，请务必查找服务器、网络和组织的敏感信息，这些信息可在 Google Groups（[`http://groups.google.com`](http://groups.google.com)），即 Usenet 存档，以及 Reddit 和 Quora 等新兴站点中找到。我发现一些在线帖子泄露了过多的内部网络和业务系统信息，可能性无限。如果您发现不应该公开的内容，可以与 Google 联系，请求编辑或删除。更多信息请参阅 Google 的联系我们页面（[`https://www.google.com/intl/en/contact`](https://www.google.com/intl/en/contact)）。

从更宏观的网络安全角度来看，Google 搜索引擎的挖掘范围有限，但如果您对此感兴趣，可以查看 Johnny Long 的书籍 *Google Hacking for Penetration Testers*（Syngress）。

### 目录遍历的防范措施

您可以采用三种主要措施来防止通过恶意目录遍历导致文件被篡改：

* **不要在 Web 服务器上存储旧的、敏感或非公开的文件。** 只能在 `/htdocs` 或 `DocumentRoot` 文件夹中放置站点正常运行所需的文件。这些文件不应包含您不希望世界看到的机密信息。

* **配置 `robots.txt` 文件。**

  这将帮助阻止像 Google 这样的搜索引擎抓取站点的更敏感区域。

* **确保 Web 服务器仅允许公开访问对站点正常运行所必需的目录。** 最小权限原则是关键，因此仅提供 Web 应用程序正常工作所需的文件和目录的访问权限。

  ![technicalstuff](img/technicalstuff.png)请查阅 Web 服务器文档，了解如何控制公开访问。根据您所使用的 Web 服务器版本，这些访问控制通常在 `httpd.conf` 文件和 Apache 的 `.htaccess` 文件中设置（参阅 [`http://httpd.apache.org/docs/current/configuring.html`](http://httpd.apache.org/docs/current/configuring.html)），以及 IIS 的 Internet Information Services Manager。最新版本的这些 Web 服务器默认具有良好的目录安全性，请确保您使用的是最新版本。

* **考虑使用搜索引擎蜜罐。** 蜜罐会吸引恶意用户，让您了解攻击者是如何针对您的站点进行攻击。随后您可以利用所获知识来阻止他们。例如，Google Hack Honeypot（[`http://ghh.sourceforge.net`](http://ghh.sourceforge.net)）。

### 输入过滤攻击

网站和应用程序以几乎任何输入为准，往往错误地认为输入是有效的，并继续处理。未验证输入是 Web 开发人员犯下的最大错误之一。

一些会插入恶意或格式不当数据（通常一次性输入过多）的攻击可以针对网站或应用程序，使系统混乱并向攻击者泄露过多信息。输入攻击还能让攻击者轻易从不经意的用户浏览器中获取敏感信息。

#### 缓冲区溢出

缓冲区溢出是针对 Web 应用程序输入字段的最严重输入攻击之一。例如，一款信用报告应用程序在用户登录后才允许提交数据或查询报告。登录表单使用以下代码获取用户 ID，最大输入长度为 12 个字符（由 `maxsize` 变量指定）：

`&lt;form name="Webauthenticate" action="www.your_web_app.com/login.cgi" method="POST"&gt;&lt;input type="text" name="inputname" maxsize="12"&gt;`

典型登录会话中，有效的登录名长度不超过 12 个字符，但 `maxsize` 变量可以被修改为更大的值，例如 100 或甚至 1,000。攻击者可以在登录字段中输入伪造数据。接下来会发生什么，谁也无法预测——应用程序可能挂起、覆盖内存中的其他数据，或导致服务器崩溃。

简单的方法是通过 Web 代理（如商业漏洞扫描工具中提到的，或免费 Burp 代理）逐步操作页面提交。要使用此代理，您需要在浏览器中配置本地代理 127.0.0.1:8080。在 Mozilla Firefox 中，选择 Tools ⇒ Options，滚动至 Options 对话框底部的 Network Proxy 部分，点击 Settings，然后选择 Manual Proxy Configuration 单选按钮。在 Internet Explorer 中，点击齿轮图标并选择 Internet Options，在弹出的对话框中点击 Connections 部分的 LAN Settings，勾选 Use a proxy server for your LAN，并输入相应的主机名/IP 地址和端口号。

只需在提交前修改变量的字段长度，即可让页面以您指定的长度提交。您也可以使用 Firefox Web Developer 插件来移除 Web 表单中定义的最大字段长度，如图 15-2 所示。

![ FIGURE 15-2: Using Firefox Web Developer to reset form-field lengths.](img/9781119485476-fg1502.png)

FIGURE 15-2: 使用 Firefox Web Developer 重置表单字段长度。

#### URL 操纵

自动化输入攻击通过操纵 URL 将其发送回服务器，指示 Web 应用执行各种操作，如重定向到第三方站点或加载服务器上的敏感文件。本地文件包含（Local File Inclusion）就是一种此类漏洞。当应用程序接受基于 URL 的输入并将指定文件的内容返回给用户时，就会出现此漏洞，例如下面的尝试读取 Linux 服务器 `passwd` 文件的请求：

`https://www.your_web_app.com/onlineserv/Checkout.cgi?state=detail&amp;language=english&amp;imageSet=/../..//../..//../..//../..//../..///etc/passwd`

值得注意的是，大多数现代应用平台（如 ASP.NET 和 Java）对 URL 变量的操纵防护相当出色，但我仍时常看到此漏洞。

下面的链接展示了另一种 URL 红 irection（重定向）的例子：

`http://www.your_web_app.com/error.aspx?URL=http://www.bad~site.com&ERROR=Path+'OPTIONS'+is+forbidden.http://www.your_web_app.com/exit.asp?URL=http://www.bad~site.com`

在这两种情况下，攻击者可以通过电子邮件或在网站上发布链接，诱导用户点击，从而被重定向到恶意第三方站点，那里可能包含恶意软件或不适当内容。

![tip](img/tip.png)如果您有充足时间，可以手动寻找这类漏洞。但为了准确性（以及理智），这些攻击最好使用 Web 漏洞扫描器进行，扫描器能够在极短时间内对数百个 URL 进行迭代，快速检测弱点。

#### 隐藏字段操纵

一些网站和应用在页面中嵌入隐藏字段，用于在 Web 服务器和浏览器之间传递状态信息。隐藏字段在 HTML 表单中表现为 `<input type="hidden">`。由于编码不善，隐藏字段常常包含机密信息（例如电商站点的商品价格），这些信息本应仅存储在后端数据库中。用户不应看到隐藏字段（因此得名），但好奇的攻击者可以发现并利用它们。下面是操作步骤：

1. **查看 HTML 源代码。**

![tip](img/tip.png)要在 Internet Explorer 和 Firefox 中查看源代码，右键单击页面并从上下文菜单中选择 "View Source" 或 "View Page Source"。

2. **更改这些字段中存储的信息。**

恶意用户可能会将价格从 $100 更改为 $10，例如。

3. **将页面重新上传到服务器。**

此步骤允许攻击者获取非法收益，例如在网络购买时获得更低的价格。

这类漏洞正在变得越来越少见，但与 URL 重写类似，利用的可能性仍然存在，因此保持警惕很有价值。

![warning](img/warning.png)使用隐藏字段进行身份验证（登录）机制可能特别危险。我曾看到一种多因素身份验证锁定流程，它依赖于隐藏字段来记录用户登录尝试的次数。该变量可以在每次登录尝试时重置为零，从而便于脚本化的字典攻击或暴力破解登录。这或许是讽刺——设计用于*防止*入侵者攻击的安全控制本身却容易受到入侵者的攻击。

一些工具，如商业网络漏洞扫描器自带的代理以及 Burp Proxy，可以轻松地操纵隐藏字段。图 15-3 显示了 WebInspect SPI Proxy 接口以及网页的隐藏字段。

![ FIGURE 15-3: 使用 WebInspect 查找并操纵隐藏字段。](img/9781119485476-fg1503.png)

FIGURE 15-3: 使用 WebInspect 查找并操纵隐藏字段。

如果你发现隐藏字段，可以尝试对它们进行操纵，看看能做什么。方法很简单。

#### 代码注入和 SQL 注入

类似于 URL 重写攻击，代码注入攻击会操纵特定的系统变量。下面是一个示例：

`http://www.your_web_app.com/script.php?info_variable=X`

攻击者看到这个变量后，可以在 `info_variable` 字段中输入不同的数据，将 `X` 替换为诸如下面这些内容：

`http://www.your_web_app.com/script.php?info_variable=Yhttp://www.your_web_app.com/script.php?info_variable=123XYZ`

这段示例比较基础，但 web 应用可能会以提供攻击者比他们想要的更多信息的方式响应，例如返回详细错误信息或访问未授权的数据字段。无效输入也可能导致应用或服务器挂起。攻击者可以利用这些信息进一步了解 web 应用及其内部工作，进而导致严重的系统 compromise。

![warning](img/warning.png)如果 HTTP 变量通过 URL 传递且易于访问，那么攻击者利用你的 web 应用已经只是时间问题。

我曾经使用一个用于管理个人信息的 web 应用，它正是这样的。因为 `"name"` 参数是 URL 的一部分，任何人都可以通过修改 `"name"` 的值来获取其他人的个人信息。如果 URL 包含 `"name=kbeaver"`，只需将其改为 `"name=jsmith"`，即可查看 J. Smith 的家庭地址、社会安全号码等。Ouch！我向系统管理员报告了这个漏洞。经过几分钟的否认后，他承认确实是个问题，并与开发人员一起着手修复。

代码注入也可以针对后端 SQL 数据库进行，这种攻击称为 *SQL 注入*。恶意攻击者在 URL 请求中插入 SQL 语句（如 `CONNECT`、`SELECT`、`UNION`），试图连接并从数据库中提取信息，而该数据库是 web 应用交互的对象。SQL 注入之所以能实施，是因为应用未能正确验证输入，并且数据库服务器和 web 服务器返回了信息性错误。

SQL 注入主要有两类：标准（也称为基于错误）和盲注。基于错误的 SQL 注入是利用应用在输入无效信息时返回的错误消息来进行的。盲注则是在错误消息被禁用的情况下进行，攻击者或自动化工具需要猜测数据库返回的内容以及对注入攻击的响应。

![tip](img/tip.png)快速（但不一定可靠）判断你的 web 应用是否易受 SQL 注入的方法是：在表单字段或 URL 末尾输入一个单引号（'）。如果返回了 SQL 错误，那么大概率 SQL 注入已存在。

在查找和发现 SQL 注入缺陷时，你得到的是物有所值的回报。正如 URL 重写一样，使用漏洞扫描器进行 SQL 注入检查更为明智，它允许攻击者通过漏洞页面向后端数据库注入数据库查询和命令。图 15-4 展示了 Netsparker 漏洞扫描器发现的众多 SQL 注入漏洞。

![ FIGURE 15-4: Netsparker 发现的 SQL 注入漏洞。](img/9781119485476-fg1504.png)

FIGURE 15-4: Netsparker 发现的 SQL 注入漏洞。

Netsparker 的好处在于，它在发现 SQL 注入后，提供了内置的 "Execute SQL Commands" 工具，进一步展示弱点。一张展示 SQL 注入在起作用的截图，几乎是漏洞和渗透测试能达到的最佳效果！

当你发现 SQL 注入漏洞时，可能会倾向于在此停下脚步，不再尝试利用该弱点。这没问题。但我更倾向于看看我能在数据库系统中走多远。我建议尽可能使用漏洞扫描器内置的 SQL 注入功能，以便向管理层展示漏洞的严重性。

![tip](img/tip.png)如果预算有限，可考虑使用免费的 SQL 注入工具，如 SQL Power Injector（[www.sqlpowerinjector.com](http://www.sqlpowerinjector.com)）或 Firefox 添加程序 SQL Inject Me（[`addons.mozilla.org/en-us/firefox/addon/sql-inject-me`](https://addons.mozilla.org/en-us/firefox/addon/sql-inject-me)）。

我在 第 16 章 中深入探讨了数据库安全。

#### 跨站脚本 (XSS)

跨站脚本（XSS）可能是最为人知且最广泛存在的 web 漏洞，当网页未正确验证用户输入（通常是 JavaScript）时，就会出现该漏洞。攻击者可以利用缺乏输入过滤的机会，在任何查看该页面的计算机上执行恶意代码。

例如，XSS 攻击可以显示另一个恶意网站的用户 ID 和登录页面。如果用户不慎在该登录页面输入用户 ID 和密码，这些信息就会被记录到黑客的服务器日志中。其他恶意代码可以被发送到受害者的计算机并与查看该页面的浏览器或电子邮件应用程序以相同的权限运行。恶意代码可能赋予黑客对浏览器 Cookie 或浏览器历史记录文件的完全读写权限，甚至允许他下载或安装恶意软件。

![tip](img/tip.png)简单的测试方法是检查应用中是否有接受用户输入的字段（如登录或搜索框），并输入以下 JavaScript 语句：

`&lt;script&gt;alert('XSS')&lt;/script&gt;`

如果弹出一个显示 `XSS` 的窗口（如图 15-5 所示），则说明该应用易受 XSS 漏洞影响。XSS‑Me Firefox 添加程序（[`addons.mozilla.org/en-US/firefox/addon/xss-me`](https://addons.mozilla.org/en-US/firefox/addon/xss-me)）也是一种测试手段。

![ FIGURE 15-5: 将脚本代码反射到浏览器。](img/9781119485476-fg1505.png)

脚本反射到浏览器的灵感源于需要通过 JavaScript `onmouseover` 函数进行用户交互的 XSS 利用方式。

与 SQL 注入一样，你真的需要使用自动化扫描工具来检测 XSS。Netsparker 和 Acunetix Web Vulnerability Scanner 都能很好地发现 XSS，但它们往往发现的 XSS 问题不同——这凸显了在可能的情况下使用多个扫描工具的重要性。

![Figure 15-6:](img/#c15.xhtml#c15-fig-0006) 显示了 Acunetix Web Vulnerability Scanner 中的一些 XSS 发现示例。

![FIGURE 15-6: Using Acunetix Web Vulnerability Scanner to find cross-site scripting in a web application.](img/9781119485476-fg1506.png)

![tip](img/tip.png)

另一个擅长发现许多其他扫描器无法发现的 XSS 的网页漏洞扫描器是 Rapid7 的 AppSpider（前称 NTOSpider）([`https://www.rapid7.com/products/appspider`](https://www.rapid7.com/products/appspider))。

在我的经验中，AppSpider 在对使用多因素认证系统的应用进行身份验证扫描时表现更好。

AppSpider 应该被放在你的视野中。

切记：在 Web 漏洞方面，扫描器越多越好！如果不这样做，别人可能会使用你未使用的扫描器。

### 对输入攻击的防范措施

* 网站和应用必须对输入数据进行过滤。

* 网站和应用必须确保输入的数据符合应用程序预期的参数范围。

* 如果数据不匹配，应生成错误信息或返回到上一页。

* 在任何情况下，应用都不应接受垃圾数据、处理它并将其反射回给用户。

* 如果将这些最佳实践作为开发过程的关键部分，安全的编码实践可以消除上述所有问题。开发人员应知晓并实施这些最佳实践：

  * 永远不要向浏览器和用户展示不需要的静态值。

    相反，这些数据应在服务器端实现，仅在需要时从数据库中获取。

  * 从输入字段中过滤掉 `<script>` 标签。

  * 如果可能，禁用详细的 Web 服务器和数据库相关错误信息。

### 默认脚本攻击

* 编写不佳的 Web 程序，如 PHP（超文本预处理）和 ASP（Active Server Pages）脚本，可能允许黑客查看和操作 Web 服务器上的文件，以及执行其他未授权的操作。

* 这些缺陷在开发人员、IT 人员和营销人员使用的内容管理系统中也十分常见，用于维护网站内容。

* 默认脚本攻击之所以常见，是因为大量 poorly written 代码自由可得。

* 黑客还可以利用各种示例脚本，尤其是较旧版本的 Microsoft IIS 服务器上安装的脚本。

* ![warning](img/warning.png)

  许多 Web 开发人员和站长使用这些脚本而不理解其工作原理或未进行测试，这可能导致严重的安全漏洞。

* 要测试脚本漏洞，你可以手动浏览脚本，或使用文本搜索工具（如 Windows 开始菜单内置的搜索功能或 Linux 的 Find 程序）查找任何硬编码的用户名、密码及其他敏感信息。

* 搜索 *admin*、*root*、*user*、*ID*、*login*、*signon*、*password*、*pass*、*pwd* 等关键词。

* 脚本中嵌入的敏感信息通常并非必要，往往是由于把便利性置于安全之上导致的低质量编码结果。

### 对默认脚本攻击的防范措施

* 以下措施可帮助防止默认 Web 脚本的攻击：

  * 在将脚本部署到 Web 环境前，先了解其工作原理。

  * 在使用前，确保从 Web 服务器上彻底删除所有默认或示例脚本。

  * 保持内容管理系统软件的更新，尤其是 WordPress，因为它是攻击者的主要目标。

    ![remember](img/remember.png)

  * 切勿使用包含硬编码机密信息的公开可访问脚本，它们是安全事件的导火索。

  * 为站点或应用的敏感区域设置文件权限，防止公众访问。

### 不安全的登录机制

* 许多网站要求用户登录后才能使用应用。

* 这些登录机制可能在处理错误的用户 ID 或密码时不够优雅，从而泄露攻击者可以用于猜测有效用户 ID 和密码的信息。

* 要测试不安全的登录机制，请访问你的应用，并尝试以下登录方法：

  * 使用无效的用户 ID 但有效的密码。

  * 使用有效的用户 ID 但无效的密码。

  * 使用无效的用户 ID 与无效的密码。

* 输入上述信息后，Web 应用通常会返回类似 `Your user ID is invalid` 或 `Your password is invalid` 的消息。

* 或者，应用可能返回通用错误信息，如 `Your user ID and password combination is invalid`，并在 URL 中返回不同的错误码，分别对应无效的用户 ID 和无效的密码，如图 15-7 和 15-8 所示。

* ![ FIGURE 15-7: The URL returns an error when an invalid user ID is entered.](img/9781119485476-fg1507.png)

* ![FIGURE 15-7:](img/#c15.xhtml#rc15-fig-0007) 当输入无效的用户 ID 时，URL 会返回错误。

* ![ FIGURE 15-8: The URL returns a different error when an invalid password is entered.](img/9781119485476-fg1508.png)

* ![FIGURE 15-8:](img/#c15.xhtml#rc15-fig-0008) 当输入无效的密码时，URL 会返回不同的错误。

* 这两种情况都很糟糕，因为应用不仅告诉你哪个参数无效，还告诉你哪个参数是有效的。攻击者现在知道一个有效的用户名或密码，工作量被削减一半！如果他们知道用户名（通常更容易猜到），就可以编写脚本自动化密码破解过程，反之亦然。

* 你也应该通过使用诸如 Brutus（[`www.hoobie.net/brutus/index.html`](http://www.hoobie.net/brutus/index.html)）等 Web 登录破解工具将登录测试提升到更高水平，如图 15-9 所示。Brutus 是一个简单的工具，可通过字典和暴力攻击来破解 HTTP 和基于表单的身份验证机制。

* ![ FIGURE 15-9: The Brutus tool tests for weak web logins.](img/9781119485476-fg1509.png)

* ![FIGURE 15-9:](img/#c15.xhtml#rc15-fig-0009) Brutus 工具用于测试弱 web 登录。

* ![warning](img/warning.png)

  与任何密码测试一样，这项任务可能很长且繁琐，并且有风险锁定用户账户。请谨慎进行。

* 另一个用于破解 Web 密码的工具是 THC-Hydra（[`https://tools.kali.org/password-attacks/hydra`](https://tools.kali.org/password-attacks/hydra)）。

* 商业 Web 漏洞扫描器通常具备不错的字典式 Web 密码破解功能，但没有（据我所知）能像 Brutus 那样进行真正的暴力测试。

* 如我在第 8 章（Chapter 8）中讨论的那样，你的密码破解成功高度依赖于字典列表。

* 以下是一些常见的字典文件和其他词表来源：

  * `ftp://ftp.cerias.purdue.edu/pub/dict`

  * [ `https://packetstormsecurity.org/Crackers/wordlists` ](https://packetstormsecurity.org/Crackers/wordlists)

  * [ www.outpost9.com/files/WordLists.html ](http://www.outpost9.com/files/WordLists.html)

![tip](img/tip.png)Acunetix Web Vulnerability Scanner 在扫描时能很好地测试弱密码。我曾使用该扫描器发现了原本我不会找到的弱网页密码，这些发现往往会导致对系统的进一步渗透。

你可能根本不需要密码破解工具，因为许多前端 Web 系统（如存储管理系统、IP 视频系统和物理访问控制系统）都自带密码，这些默认密码通常是 `password`、`admin` 或空。有些密码甚至直接写在登录页面的源码中，例如图 15-10（第 207、208 行）所示的网络摄像头源码。

![ FIGURE 15-10: A network camera’s login credentials embedded directly in its HTML source code.](img/9781119485476-fg1510.png)

FIGURE 15-10: A network camera’s login credentials embedded directly in its HTML source code.

### 针对不安全登录系统的防范措施

你可以采取以下措施，防止攻击者利用弱登录系统攻击你的 Web 应用：

* 向用户返回的登录错误应尽可能通用，例如 `Your user ID and password combination is invalid`。

* 应用程序永不在 URL 中返回错误码以区分无效用户名和无效密码。

  ![tip](img/tip.png)如果必须在 URL 中返回信息，应保持其尽可能通用。示例：

  `www.your_web_app.com/login.cgi?success=false`

  虽然这个 URL 信息对用户不够便利，但它能隐藏实现机制和背后的操作，防止攻击者探测。

* 使用 CAPTCHA（如 reCAPTCHA）或 Web 登录表单，帮助防止密码破解尝试。

* 在 Web 服务器或 Web 应用中启用 Intruder 锁定机制，在大约 10 次失败登录后锁定用户账户。该操作可通过会话跟踪或第三方 Web 应用防火墙插件实现，详见“Putting up firewalls”。

* 检查并更改任何厂商默认密码为难记且难破解的密码。

### 对 Web 应用漏洞进行通用安全扫描

我想再次强调，你需要对 Web 系统进行自动化和手动两种测试。单靠其中一种方法无法看到完整图景。我 *高度* 推荐使用 Acunetix Web Vulnerability Scanner 或 Netsparker 等全能 Web 漏洞扫描器，以发现难以或不可能通过其他方式发现的漏洞。将扫描结果与恶意思维以及本章节描述的黑客技术结合，你就能找到真正重要的 Web 安全漏洞。

### 降低 Web 安全风险

保持 Web 应用安全需要持续的漏洞和渗透测试，以及 Web 开发者和供应商的持续关注。跟随最新的黑客技术、测试工具和手段，并让开发者和供应商认识到安全是组织的首要任务。我讨论如何获得安全认同在 第 20 章。

![tip](img/tip.png)你可以通过以下资源获得实际测试和黑客 Web 应用的经验：

* OWASP WebGoat 项目（[`https://www.owasp.org/index.php/Category:OWASP_WebGoat_Project`](https://www.owasp.org/index.php/Category:OWASP_WebGoat_Project)）。

* Foundstone 的 Hacme Tools（[`https://www.mcafee.com/hk/downloads/free-tools/hacme-bank.aspx`](https://www.mcafee.com/hk/downloads/free-tools/hacme-bank.aspx) 与 [`https://www.mcafee.com/uk/downloads/free-tools/hacmebooks.aspx`](https://www.mcafee.com/uk/downloads/free-tools/hacmebooks.aspx)）。

强烈建议你尝试这些工具，亲自动手！

### 通过隐蔽实现安全

以下 *隐蔽安全*（使用平凡手段隐藏真实情况）的方式可以防止蠕虫或脚本等自动化攻击，这些攻击针对特定脚本类型或默认 HTTP 端口：

* 为保护 Web 应用及关联数据库，使用不同机器运行每个 Web 服务器、应用服务器和数据库服务器。

  ![tip](img/tip.png)这些机器的操作系统应经过安全漏洞检测并依据最佳实践和章节 12 与 13 中的防范措施进行硬化。

* 利用 Web 服务器内置的安全特性处理访问控制和进程隔离，例如 IIS 的“应用程序隔离”功能。这样如果一个 Web 应用被攻击，其他运行在同一服务器上的应用未必受到影响。

* 使用工具隐藏 Web 服务器的身份，即匿名化服务器。例如 Port 80 Software 的 ServerMask（[`https://www.port80software.com/products/servermask`](https://www.port80software.com/products/servermask)）。

* 如果你在 Linux 服务器上运行 Web 服务，可使用 IP Personality（[`http://ippersonality.sourceforge.net`](http://ippersonality.sourceforge.net)）修改操作系统指纹，使服务器看起来像是运行其他系统。

* 将 Web 应用改为非标准端口运行。将默认 HTTP 端口 80 或 HTTPS 端口 443 改为高位端口（如 8877），并在可能的情况下让服务以非特权用户（非 system、admin、root 等）运行。

![warning](img/warning.png)绝不要单靠隐蔽来保障安全；它并不完美。专注的攻击者可能会发现系统并非其宣称的那样。即便如此，它仍然优于无 protection。

### 部署防火墙

考虑采用以下控制措施保护 Web 系统：

* 网络层防火墙或入侵防御系统（IPS），能够检测并阻止针对 Web 应用的攻击。这类工具包括 WatchGuard（[`https://www.watchguard.com`](https://www.watchguard.com)）和 Palo Alto Networks（[`https://www.paloaltonetworks.com`](https://www.paloaltonetworks.com)）的商业防火墙。

* 主机层 Web‑应用 IPS，如 ServerDefender VP（[`https://www.port80software.com/products/serverdefender`](https://www.port80software.com/products/serverdefender)）。

* 供应商防火墙，如 Barracuda Networks（[`https://www.barracuda.com/products/webapplicationfirewall`](https://www.barracuda.com/products/webapplicationfirewall)）、Cloudflare（[`https://www.cloudflare.com/waf`](https://www.cloudflare.com/waf)）和 FortiNet（[`https://www.fortinet.com/products/web-application-firewall/fortiweb.html`](https://www.fortinet.com/products/web-application-firewall/fortiweb.html)）。

这些程序能够实时检测 Web 应用及部分数据库攻击，并在攻击发生前将其切断，防止造成损害。

### 分析源代码

大多数软件安全漏洞始于（并应在）源代码阶段结束，但往往并未如此。如果你对现有的安全测试工作感到自信，可以进一步检查源代码，寻找传统扫描和测试手段可能忽略的安全缺陷。别担心！过程比听起来更简单，你不必逐行阅读代码，也不必具备开发经验（虽然这会有帮助）。

你可以使用静态源代码分析工具，例如 `Visual Code Grepper` ([`https://sourceforge.net/projects/visualcodegrepp`](https://sourceforge.net/projects/visualcodegrepp))、`SonarQube` ([`https://www.sonarqube.org`](https://www.sonarqube.org/)) 或 `PVS-Studio Analyzer` ([`https://www.viva64.com/en/pvs-studio`](https://www.viva64.com/en/pvs-studio))。

![remember](img/remember.png)源代码分析通常能发现传统的应用程序安全测试所未覆盖的各种缺陷。如果你想获得最全面的测试水平，请两者都进行。源代码分析提供的额外检查层级日益重要。这些应用程序往往充满了许多新手开发者在学校里未曾学习的安全漏洞。

基于我对一些高端商业源代码分析工具的经验，我不确定花费巨额资金购买商业产品是否值得。虽然这些工具确实有帮助，尤其是在大型、复杂的应用环境中，但 Web 应用和移动应用安全的核心原则是：如果你能向你的开发人员和质量保证分析师展示安全始于他们，你就能在组织的整体信息安全方面产生影响。

## 揭露移动应用缺陷

除了运行源代码分析器外，检查移动端的应用漏洞也很重要。你需要寻找以下几类问题：

* 硬编码在应用中的加密数据库密钥。

* 对敏感信息的处理不当，例如将个人可识别信息本地存储，导致用户或其他应用可以访问。

* 登录弱点，如绕过登录提示的能力。

* 网络通信弱点，如明文通信或使用过时的协议（如 SSL）。

* 允许使用弱密码或空密码。

这些检查大多通过手动分析发现，可能需要使用无线网络分析仪、取证工具以及代理工具（我在第 9 章和第 11 章分别介绍了这些工具）。此外，结合本章其他章节提到的工具和技术，请务必检查你的移动应用所交互的 Web 服务端点的 SQL 注入弱点。正如物联网（IoT）一样，检查移动应用的安全性很重要。先由你自己发现缺陷，而不是让别人先发现。

第 16 章

## 数据库与存储系统

## 本章内容

![check](img/check.png)`Testing and exploiting database flaws`

![check](img/check.png)`Finding storage weaknesses`

![check](img/check.png)`Ferreting out sensitive information`

![check](img/check.png)`Countering database and storage abuse`

针对数据库和存储系统的攻击可能非常严重，因为“贵重资产”就在那里，恶意行为者也充分意识到这一点。这些攻击可以通过 Internet 或者内部网络发生，外部攻击者和恶意内部人员利用各种漏洞进行攻击。攻击也可以通过 Web 应用发生，例如通过 SQL 注入。本章节介绍一些常见漏洞，利用这些漏洞后对业务影响极大。

## 深入数据库

数据库系统 — — 如 `Microsoft SQL Server`、`MySQL` 和 `Oracle` — — 长期隐藏在背后，但它们的价值和漏洞终于受到关注。是的，即使是曾被宣称“难以破解”的 `Oracle`，也和竞争对手一样容易受到攻击。随着数据库安全监管要求的增多，几乎没有任何企业能够回避这些风险，因为几乎所有企业（大小不等）都使用某种数据库，无论是本地部署还是云端托管。

### 选择工具

与无线网络、操作系统等一样，如果要找到真正重要的数据库安全问题，你需要良好的工具。以下是我最喜欢的数据库安全测试工具：

* `Advanced SQL Password Recovery` ([`https://www.elcomsoft.com/asqlpr.html`](https://www.elcomsoft.com/asqlpr.html)) 用于破解 `Microsoft SQL Server` 密码。

* `Cain & Abel` ([`www.oxid.it/cain.html`](http://www.oxid.it/cain.html)) 用于破解数据库密码哈希。

* `Nexpose` ([`https://www.rapid7.com/products/nexpose`](https://www.rapid7.com/products/nexpose)) 用于进行深度漏洞扫描。

* `SQLPing3` ([www.sqlsecurity.com/downloads](http://www.sqlsecurity.com/downloads)) 用于在网络中定位 `Microsoft SQL Servers`，检查 `sa` 账户（默认的系统管理员账户）是否为空密码，并执行字典式密码破解攻击。

你也可以结合网络漏洞扫描工具（如 `Nexpose`）与 exploit 工具（如 `Metasploit`）进行数据库测试。

### 发现网络中的数据库

发现数据库漏洞的第一步是确定它们在网络中的位置。听起来很奇怪，但许多网络管理员并不清楚其环境中运行的各种数据库。这种情况尤其适用于免费的 `SQL Server Express` 版本，用户可以下载并运行在你的网络中。

![warning](img/warning.png)我经常发现敏感的生产数据，如信用卡号和社会安全号，被用于测试数据库，并且这些数据库对网络内的好奇内部人员甚至已经进入网络的外部攻击者公开可用。将敏感的生产数据用于销售、软件开发、质量保证等未受控区域，就是一场即将发生的数据泄露。

我找到的最佳工具是 `SQLPing3`（参见图 16-1）。

![ FIGURE 16-1: SQLPing3 可发现 SQL Server 系统并检查缺失的 sa 账户密码。](img/9781119485476-fg1601.png)

FIGURE 16-1: SQLPing3 可发现 SQL Server 系统并检查缺失的 sa 账户密码。

`SQLPing3` 甚至能够发现被个人防火墙（如 `Windows Firewall`）隐藏的 `SQL Server` 实例。这一功能很有用，因为 `Windows Firewall` 在 Windows 7 及以后的版本中默认启用。

![tip](img/tip.png)如果你的环境中有 `Oracle`，Pete Finnigan 在 [`www.petefinnigan.com/tools.htm`](http://www.petefinnigan.com/tools.htm) 上提供了一个非常好的 Oracle 相关安全工具列表，功能类似于 `SQLPing3`。

### 破解数据库密码

`SQLPing3` 同时也作为一个基于字典的 `SQL Server` 密码破解程序。如图 16-1 所示，它默认检查 `sa` 账户的空密码。另一个免费工具 `Cain & Abel` 可用于破解 `SQL Server`、`MySQL` 和 `Oracle` 的密码哈希，如图 16-2 所示。

![ FIGURE 16-2: 使用 Cain & Abel 破解 Oracle 密码哈希。](img/9781119485476-fg1602.png)

FIGURE 16-2: 使用 Cain & Abel 破解 Oracle 密码哈希。

你只需加载 `Cain & Abel`，点击顶部的 `Cracker` 标签，选择左下角的 `Oracle Hashes`，然后点击顶部的蓝色加号图标加载用户名和密码哈希开始破解。你也可以选择左下角的 `Oracle TNS Hashes` 来尝试在捕获数据包时截获 `Transport Network Substrate` 哈希，同样适用于 `MySQL` 密码哈希。

商业产品 ElcomSoft Distributed Password Recovery ([`https://www.elcomsoft.com/edpr.html`](https://www.elcomsoft.com/edpr.html)) 也可以破解 Oracle 密码哈希。如果你有访问 SQL Server `master.mdf` 文件的权限（这些文件由于弱网络共享和文件权限，通常在网络中随时可用，如本章后面所述），你可以使用 ElcomSoft 的高级 SQL 密码恢复工具立即恢复数据库密码。

![tip](img/tip.png)你可能会发现一些受密码保护的旧版 Microsoft Access 数据库文件。别担心：工具 Advanced Office Password Recovery 可以帮助你。此外，许多已停产或不再受支持的 Access 版本仍然存在。运行漏洞扫描器如 Nexpose 来发现缺陷可能会很有帮助。根据发现的结果，你可能会使用 Metasploit 来演示可能发生的情况。

正如你所想象的，这些密码破解工具是展示数据库安全中最基本弱点的好方法。它们也是突出网络中散落的关键文件未受保护的问题的好方式。

另一种展示 SQL Server 弱点的好方法是使用 SQL Server Management Studio ([`https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms`](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms)) 连接到你已有密码的数据库系统，并设置后门账户或浏览查看（并展示）可用内容。几乎所有我遇到的未受保护的 SQL Server 系统都有敏感的个人财务或医疗信息可供获取。只需执行以下查询即可访问任何表中的记录：

`select * from tablename`

### 扫描数据库漏洞

与操作系统和 Web 应用程序一样，某些数据库特定的漏洞只能通过正确的工具来发现。我使用 Nexpose 查找以下问题：

* 缓冲区溢出。

* 特权提升。

* 通过默认/未受保护账户可访问的密码哈希。

* 弱加密方法已启用。

![tip](img/tip.png)一个优秀的全能商业数据库漏洞扫描器，可进行深入数据库检查（包括 SQL Server、Oracle 等用户权限审计）是 AppDetectivePRO ([`https://www.trustwave.com/Products/Database-Security/AppDetectivePRO`](https://www.trustwave.com/Products/Database-Security/AppDetectivePRO/))。如果你能证明其投资价值，AppDetectivePRO 是一个很好的安全测试工具集成。

许多漏洞可以从未认证的外部视角以及受信任的内部视角进行测试。关键是尽可能从多角度审查数据库的安全性。如前所述，如果数据库存在且可访问，人们就会对其进行操作。

## 遵循最佳实践，最小化数据库安全风险

如果你做以下事情，数据库安全会相对简单：

* 在专用服务器（或必要时的工作站）上运行数据库。

* 检查底层操作系统的安全漏洞。（我在第 12 和 13 章节中分别介绍了 Windows 和 Linux 的操作系统漏洞。）

* 确保数据库在漏洞扫描、补丁和系统硬化的范围内。

* 寻找并替换（或将其隔离）已过生命周期的数据库系统。它们太危险，不能留着。

* 要求每个数据库系统都有强密码。大多数企业级数据库，如 Oracle 和 SQL Server，支持使用域身份验证（如 Active Directory 或 LDAP），这样你可以与现有域策略和用户账户关联，而无需管理单独的一套账户。

* 使用适当的文件和共享权限，阻止窥视。

* 在开发或质量保证等非生产环境中，在使用前对敏感生产数据进行去标识化处理。

* 检查你的 Web 应用是否存在 SQL 注入和相关输入验证漏洞。（我在第 15 章节中介绍 Web 应用安全。）

* 使用网络防火墙，如 Fortinet ([`https://www.fortinet.com`](https://www.fortinet.com/)) 或 Cisco ([`https://www.cisco.com`](https://www.cisco.com/)) 提供的类型，以及 Imperva ([`https://www.imperva.com`](https://www.imperva.com/)) 和 IDERA ([`https://www.idera.com`](https://www.idera.com/)) 提供的数据库特定控制。

* 使用诸如 Microsoft Security Compliance Manager ([`https://technet.microsoft.com/en-us/library/cc677002.aspx`](https://technet.microsoft.com/en-us/library/cc677002.aspx)) 等工具进行相关数据库硬化和管理。

* 使用最新版本的数据库服务器软件。Oracle、SQL Server 2016 和 SQL Server 2017 的新安全功能为本地数据库以及云端数据库提供了更好的安全性。

## 打开存储系统的讨论

攻击者正在实施越来越多的与存储相关的攻击，并使用各种攻击向量和工具破坏存储环境。（你肯定知道我接下来要说什么。）因此，你需要了解相关技术和工具，并用它们测试自己的存储环境。

![warning](img/warning.png)关于 Fibre Channel 和 iSCSI 存储区网络（SAN）、基于 CIFS 和 NFS 的网络附加存储（NAS）系统等存储系统的安全性，存在许多误解和神话。许多网络和存储管理员认为加密或 RAID 等同于存储安全，外部攻击者无法访问公司存储环境，公司系统具有弹性，或安全由他人处理。所有这些信念都非常危险，我有信心未来更多攻击将针对关键存储系统。

与数据库一样，几乎所有企业都有存储网络，其中包含敏感信息，公司无法承受丢失。因此，将网络存储（SAN 和 NAS 系统）以及传统文件共享纳入安全测试范围很重要。

### 选择工具

以下是我最喜欢的存储安全测试工具：

* **nmap** ([`http://nmap.org`](http://nmap.org)) 用于端口扫描，以查找存活的存储主机。

* **SoftPerfect Network Scanner** ([`https://www.softperfect.com/products/networkscanner`](https://www.softperfect.com/products/networkscanner)) 用于查找开放且未受保护的共享。

* **FileLocator Pro** ([`https://www.mythicsoft.com`](https://www.mythicsoft.com)) 用于查找特定文件和信息。

* **Nexpose** 用于进行深入的漏洞扫描。

### 在网络中查找存储系统

要发现存储相关的漏洞，首先必须确定存储的位置。最佳启动方式是使用端口扫描器，最好结合使用像 Nexpose 或 LanGuard 这样的全能漏洞扫描器。此外，由于许多存储服务器内置 Web 服务器，你可以使用 Acunetix Web Vulnerability Scanner 和 Netsparker 等工具发现基于 Web 的缺陷。这些漏洞扫描器可帮助你了解需要进一步检查的区域，如弱加密、未打补丁的操作系统和跨站脚本。

![tip](img/tip.png)A commonly overlooked storage vulnerability is that many storage systems can be accessed from both the demilitarized zone (DMZ) segment and the internal network segment(s). This vulnerability poses risks to both sides of the network. Be sure to check manually to see whether you can reach the DMZ from the internal network, and vice versa.

You can also perform basic file permission and share scans (as outlined in Chapter 12) in conjunction with a text search tool to uncover sensitive information that no one on the network should have access to. Digging down further, a quick means for finding open network shares is to use SoftPerfect Network Scanner’s share scanning capabilities, as shown in Figure 16-3.

![ FIGURE 16-3: Using SoftPerfect Network Scanner to search for network shares.](img/9781119485476-fg1603.png)

FIGURE 16-3: Using SoftPerfect Network Scanner to search for network shares.

As you can see in Figure 16-3, Network Scanner enables you to perform a security and security permission scan for all devices or simply folders. I recommend selecting Specific Account in the Authentication section and then clicking Manage so that you can enter a domain account for the network that has general user permissions. This technique provides a good level of access to determine which shares are accessible.

When Network Scanner completes its scan, the shares showing Everyone in the Shared Folder Security column are the shares that need attention. I rarely complete a security assessment without coming across such shares open to the Windows Everyone group. Just as common is seeing the directories and files within these shares that are accessible to any logged-in Windows user to open, modify, delete, and do whatever else they please. How’s that for accountability?

### Rooting out sensitive text in network files

When you find open network shares, scan for sensitive information stored in files such as `.pdf`, `.docx`, and `.xlsx` files. The process is as simple as using a text search utility such as FileLocator Pro. Alternatively, you can use Windows Explorer or the `find` command in Linux to scan for sensitive information, but that process is too slow and cumbersome for my liking.

You'll be *amazed* by what you come across stored insecurely on users’ desktops, server shares, and more, such as the following:

* Employee health records

* Customer credit card numbers

* Corporate financial reports

* Source code

* Master database files

The sky’s the limit. Such sensitive information should be protected by good business practices, and it’s also governed by state, federal, and international regulations, so make sure that you find it and secure it.

![tip](img/tip.png)Do your searches for sensitive text while you’re logged in to the local system or domain as a regular user — not as an administrator. This practice gives you a better view of regular users who have unauthorized access to sensitive files and shares that you thought were secure. When using a basic text search tool such as FileLocator Pro, look for the following text strings:

* DOB (for dates of birth)

* SSN (for Social Security numbers)

* License (for driver’s-license information)

* Credit or CCV (for credit-card numbers)

![remember](img/remember.png)Don’t forget about your mobile devices when seeking sensitive, unprotected information. Everything from laptops to USB drives to external hard drives is fair game to the bad guys. A misplaced or stolen system can create a costly data breach. The same can be said for cloud-based file sharing services such as OneDrive and Sharefile.

The possibilities for information exposure are endless. Start with the basics, and peek only into common files that you know may have some juicy info in them. Limiting your search to these files will save you a ton of time:

* `.txt`

* `.doc` and `.docx`

* `.rtf`

* `.xls` and `.xlsx`

* `.pdf`

Figure 16-4 shows a basic text search with FileLocator Pro. Notice the files located on different parts of the server.

![ FIGURE 16-4: Using FileLocator Pro to search for sensitive text on unprotected shares.](img/9781119485476-fg1604.png)

FIGURE 16-4: Using FileLocator Pro to search for sensitive text on unprotected shares.

FileLocator Pro can also search for content inside `.pdf` files to uncover sensitive data.

To speed the process, use Spirion's Sensitive Data Manager ([`https://www.spirion.com`](https://www.spirion.com)). This product, formerly known as IdentityFinder and since rolled into the company’s enterprise data discovery platform, is a neat tool designed for scanning storage devices for sensitive, personally identifiable information. It can also search inside binary files such as PDFs.

For a second round of testing, you could perform your searches while logged in as an administrator. You’re likely to find a lot of sensitive information scattered about. It might seem worthless at first, but it can highlight sensitive information stored in places where it shouldn’t be or that network administrators shouldn’t be able to access.

![remember](img/remember.png)Testing is highly dependent on timing, searching for the right keywords, and looking at the right systems on the network. You likely won’t root out every single bit of sensitive information, but this effort shows you where certain problems are, which helps you justify the need for stronger access controls and for better IT and security management processes.

## Following Best Practices for Minimizing Storage Security Risks

Like database security, storage security isn’t brain surgery. Keeping your storage systems secure is simple, too, if you do the following things:

* Check the underlying operating systems for security vulnerabilities. I cover operating system exploits for Windows and Linux in chapters 12 and 13.

* Ensure that your network storage (SAN and NAS systems) falls within the scope of patching and system hardening.

* Require strong passwords on every storage management interface.

* Use appropriate file and share permissions to keep prying eyes away.

* Educate your users on where to store sensitive information and the risks of mishandling it.

* Deidentify any sensitive production data before it’s used in development or quality assurance, using tools made for this purpose.

* Use a network access control lists or a firewall, such as those available from Fortinet ([`https://www.fortinet.com`](https://www.fortinet.com)) or WatchGuard Technologies ([`https://www.watchguard.com`](https://www.watchguard.com)) to ensure that only the people and systems with a business need to access your storage environment can do so — and do nothing more.

Part 6

## Security Testing Aftermath

IN THIS PART …

Report your way to success with security testing deliverables that management can understand and appreciate.

Follow-up on your security vulnerabilities so that they’re not exploited.

Implement good security practices into your day-to-day information technology and business operations to help build resilience.

Chapter 17

## Reporting Your Results

IN THIS CHAPTER

![check](img/check.png)**Bringing your test data together**

![check](img/check.png)**Categorizing vulnerabilities you discover**

![check](img/check.png)**Documenting and presenting the results**

如果您希望在测试后休息，现在不是放松的时机。您的安全评估报告阶段是最关键的环节之一。最后一件事是进行测试、发现安全问题后就结束工作。请将时间和精力用于深入分析和记录您发现的问题，以确保安全漏洞被消除，从而提升信息安全性。报告是信息安全和风险管理所需的持续性审慎工作的重要组成部分。

报告包括对所有发现进行筛选，以确定哪些漏洞需要处理、哪些不重要。报告还包括向管理层或客户汇报发现的各类安全问题，并提供具体的改进建议。您共享已收集的信息，并指导其他相关方后续行动。报告也证明了在安全测试中投入的时间、精力和金钱被有效利用。

## Pulling the Results Together

当您拥有大量测试数据时——从您记录的屏幕截图和手动观察，到各类漏洞扫描器生成的详细报告——您该如何处理这些信息？您需要仔细审阅文档，挑出所有突出的区域。基于以下因素做出决策：

* 由评估工具给出的漏洞排名，通常基于 **Common Vulnerability Scoring System**。

* 您作为 IT/安全专业人员的知识（通常比工具提供的更有价值）。

* 漏洞的上下文及其对业务的影响。

![tip](img/tip.png)为了提供更多关于漏洞的信息，许多功能丰富的安全工具会为每个漏洞分配风险等级（基于整体风险），解释漏洞，给出可能的解决方案，并包含相关供应商网站链接、Common Vulnerabilities and Exposures 网站 (`https://cve.mitre.org`)、National Vulnerabilities Database (`https://nvd.nist.gov`)。为进一步研究，可参考供应商网站、其他支持站点和在线论坛，查看该漏洞是否影响您的系统和环境。总体业务风险是重点关注的对象。

在最终报告文档中，您可能希望按以下列表组织漏洞：

* 非技术性发现

  * 社会工程学

  * 物理安全

  * IT 与安全运营

* 技术性发现

  * 网络基础设施

  * 防火墙规则集

  * 服务器和工作站

  * 数据库

  * Web 应用

  * 移动应用

  * 移动设备

为更清晰地呈现，您可以在报告中为内部和外部安全漏洞、以及关键、高、中等优先级分别建立独立章节。最后提醒：最好在测试的规划阶段就确定具体的报告格式，这样从开始到交付结果的全过程，相关方都能保持一致。

## Prioritizing Vulnerabilities

发现的安全漏洞进行优先级排序至关重要，因为许多问题无法修复，或修复并不值得投入。您可能因技术原因无法消除某些漏洞，也可能因成本考虑无法负担消除其他漏洞。或者，业务本身对风险容忍度有特定要求。每种情况都不同。您需要判断修复的收益是否值得投入的时间和金钱。

例如，花费数周开发时间修复跨站脚本（XSS）和 SQL 注入漏洞可能非常值得，尤其是如果您因此受到第三方检查或失去潜在客户的影响。同样，对于普遍认为移动设备不存储敏感信息的假设，也需要仔细审视每个漏洞，评估业务风险，权衡是否值得修复。

![remember](img/remember.png)不可能——或者至少不值得——修复所有发现的漏洞。请仔细分析每个漏洞，确定最坏情况。例如，您的打印机 Web 界面可能存在跨站请求伪造（CSRF）漏洞，您需要评估其业务风险。或者，您可能会盲目相信网络上的所谓专家/黑客的意见，让他们决定您应集中精力的位置，尽管他们对您或您的业务一无所知。（这纯属玩笑。）另一个例子是，FTP 可能运行在大量内部服务器以及外部可访问系统上，您需要评估其业务风险。对于许多安全缺陷，您往往发现根本没有风险。

我发现，在安全——正如大多数生活领域一样——必须专注于高回报任务，否则会被琐事分散注意力，自我折磨，且难以实现自身目标。以下是一个快速的优先级排序方法，您可以根据自身需求进行微调。在发现每个漏洞时，请考虑以下两个主要因素：

* **利用的可能性**：该漏洞被黑客、恶意用户、恶意软件或其他威胁利用的可能性有多大？

* **利用的影响**：如果该漏洞被利用，会有多大的破坏性？

很多人往往跳过这些考量，假设每个发现的漏洞都必须修复。这是大错特错。仅凭发现漏洞就认为必须处理，而不考虑实际环境，会导致大量时间的、精力和金钱的浪费，甚至可能使长期安全评估计划走向失败。

![warning](img/warning.png)请注意，不要在相反方向过度偏移。表面上看似乎不严重的漏洞，若被利用仍可能给组织带来严重后果。务必深入挖掘，运用常识。

![tip](img/tip.png)使用高、中、低或 1 到 5 的评分（1 为最低优先级、5 为最高）等标准对每个漏洞进行排名。Table 17-1 示例表格展示了各类别的样本漏洞。

TABLE 17-1 Prioritizing Vulnerabilities

|  | **High Likelihood** | **Medium Likelihood** | **Low Likelihood** |
| --- | --- | --- | --- |
| **High impact** | Sensitive information stored on an unencrypted laptop | Tape backups taken offsite that aren’t encrypted and/or password-protected | No administrator password on an internal SQL Server system |
| **Medium impact** | Unencrypted emails containing sensitive information being sent | Missing Windows patch on an internal server that can be exploited with Metasploit | No passwords required on several Windows administrator accounts |
| **Low impact** | Outdated virus signatures on a securely segmented PC dedicated to Internet browsing | Employees or visitors gaining unauthorized network access | Weak encryption ciphers being used on a marketing website |

表 17-1 中显示的漏洞优先级是基于评估安全风险的定性方法。换句话说，该表是主观的，基于对系统和漏洞的了解。你也可以考虑来自你安全工具的任何风险评级，但不要仅仅依赖它们，因为供应商无法提供漏洞的终极排名。

## 创建报告

你可能需要将漏洞信息组织成正式文档，用于管理层或客户。编写报告是一项专业的工作，表明你认真对待工作。挖掘关键发现并加以记录，让其他人能够理解。

![tip](img/tip.png)图表和统计图是加分项。当保存数据到文件困难时，你的发现截图会为报告增添亮点，并提供问题真实存在的有力证据。

以简洁、非技术性的方式记录漏洞。每份报告应包含以下信息：

* 测试执行的日期。

* 执行的测试。

* 发现的漏洞摘要。

* 需要处理的漏洞优先级列表。

* 补丁安全漏洞的建议和具体步骤。

你总是通过对 IT/安全流程进行操作性评估来增加价值。我建议添加关于弱业务流程、管理层对 IT 和安全的支持等的总体观察，并为每个问题提供应对建议。你可以将此列表视为根本原因分析。

![remember](img/remember.png)大多数人希望最终报告包含发现的摘要，而非全部内容。最后，没人想在漏洞扫描工具的 600 页 PDF 中翻找充满技术术语、对普通人意义不大的内容。许多咨询公司因这种报告收取高额费用，但这并不意味着这是对的。

![tip](img/tip.png)管理员和开发人员需要从安全工具获取原始数据报告。这样他们可以在需要时查阅具体的 HTTP 请求/响应、缺失补丁的详情等。

在最终报告中，你可能需要记录在进行安全测试时观察到的行为。你可能会发现，在进行明显的社会工程攻击时，一些员工表现出漠不关心或敌意，或者 IT 或安全人员错过了技术线索（例如测试期间网络性能下降或系统日志中出现的各种攻击）。你可以记录其他安全问题，例如 IT 人员或托管服务提供商响应测试的速度，以及他们是否响应。

![warning](img/warning.png)保护最终报告，防止未授权人员查看。若安全评估报告及相关数据和支持文件落入竞争对手、黑客或恶意内部人员手中，将给组织带来严重后果。以下是防止此类访问的措施：

* 仅向有业务需要知道的对象交付报告及相关文档和文件。

* 如果你通过电子方式发送最终报告，请加密所有附件，或通过 OneDrive for Business、Google Drive、ShareFile 等安全的云文件共享服务发送报告。

第 18 章

## 修补你的安全漏洞

IN THIS CHAPTER

![check](img/check.png)**确定优先处理的漏洞**

![check](img/check.png)**修补你的系统**

![check](img/check.png)**以全新视角审视安全**

完成测试后，你想迈向更安全的道路。但你发现了一些安全漏洞——需要修复的问题（希望不多，或者严重程度不高）。在有人利用这些漏洞之前，你需要付出一点努力。你需要制定计划，决定先处理哪些安全漏洞。可能需要几次补丁，甚至需要系统加固。你可能需要购买新的安全技术，也可能需要重新评估你的网络设计和安全基础设施。我在本章中涉及了一些关键领域。

## 将报告转化为行动

看似最先要处理的漏洞似乎很明显，但答案可能并不清晰。在审查你发现的漏洞时，请考虑以下变量：

* 受影响系统的重要性

* 涉及的敏感信息或业务流程

* 漏洞是否可以修复

* 漏洞修复的难易程度

* 是否可以将系统离线以修复问题

* 购买新硬件或软件，或重新设计业务流程以填补漏洞所需的时间、金钱和精力

在 `Chapter 17` 中，我介绍了如何判断安全问题的重要性和紧迫性。你还应从时间管理的角度看待安全问题，优先处理既重要（高影响）又紧迫（高可能性）的问题。你大概不想只修复那些*仅*高影响或*仅*高可能性的漏洞。你可能有一些高影响漏洞，但很可能永远不会被利用。同样，你可能有一些高可能性的漏洞，但如果被利用对业务或工作影响不大。这种人类分析和视角让你区别于那些执行扫描并运行评估的普通人（往往以合规为名），并让你更有可能长期保持就业！

优先处理回报最高的任务——那些既高影响又高可能性的任务。这些任务很可能只是你漏洞列表中的少数项。在你修复最关键的安全漏洞后，当时间和金钱允许时，你可以再处理那些不那么重要、不那么紧迫的任务。在你修复诸如 Web 应用中的 SQL 注入以及重要服务器缺失的补丁等关键漏洞后，你可能会想重新配置备份，使用密码（若未使用强加密）来防止窥探者在备份落入错误之手时查看。

![remember](img/remember.png)Whatever you do, whatever tool you choose, and whatever procedures work best in your environment, keep your systems patched! This rule goes for operating systems; web servers; databases; mobile applications; and even firmware on your network firewalls, routers, and switches. Especially important are third-party software patches from vendors such as Oracle (Java) and Adobe (Reader, Flash, and so on). These patches are overlooked more than most, yet they create considerable risks that go unaddressed.

Patching is avoidable but inevitable. The only way to eliminate the need for patches is to develop secure software in the first place, but that’s not going to happen any time soon, if ever. Software is too complex to be perfect. A large portion of security incidents can be prevented by some good patching practices, so you simply have no reason not to have a solid patch-management process in place.

### Patch management

If you can’t keep up with the deluge of security patches for all your systems, don’t despair; you can still get a handle on the problem. Here are my basic tenets for applying patches to keep your systems secure:

* Make sure that all the people and departments involved in applying patches on your organization’s systems are on the same page and follow the same procedures.

* Have formal documented procedures in place for these critical processes:

  * Obtaining patch alerts from your vendors, including third-party patches

  * Assessing which patches affect your systems

  * Determining when to apply patches

* Make a policy and have procedures in place for testing patches *before* you apply them to your production servers. Testing patches after you apply them isn’t as big a deal on workstations, but servers are a different story. Many patches have undocumented features and subsequent unintended side effects, which I’ve experienced. An untested patch is an invitation to system termination.

### Patch automation

The following sections describe the various patch deployment tools you can use to lessen the burden of keeping up with patches.

#### Commercial tools

I recommend a robust patch-automation application, especially if these factors are involved:

* A large network.

* A network with multiple operating systems (Windows, Linux, Mac OS, and so on).

* A lot of third-party software applications, such as Adobe and Java.

* More than a few dozen computers.

![tip](img/tip.png)Check out these patch-automation solutions:

* Ecora Patch Manager ([`www.ecora.com/ecora/products/patchmanager.asp`](http://www.ecora.com/ecora/products/patchmanager.asp))

* GFI LanGuard ([`www.gfi.com/products-and-solutions/network-security-solutions/gfi-languard`](http://www.gfi.com/products-and-solutions/network-security-solutions/gfi-languard))

* PDQ Deploy ([`https://www.pdq.com/pdq-deploy`](https://www.pdq.com/pdq-deploy))

#### Free tools

Use one of these free tools to help with automated patching:

* Windows Server Update Services ([`https://technet.microsoft.com/en-us/library/cc539281.aspx`](https://technet.microsoft.com/en-us/library/cc539281.aspx) or System Center Configuration Manager ([`https://www.microsoft.com/en-us/cloud-platform/system-center-configuration-manager`](https://www.microsoft.com/en-us/cloud-platform/system-center-configuration-manager))).

* Windows Update, which is built into Microsoft Windows operating systems.

* Microsoft Baseline Security Analyzer ([`https://www.microsoft.com/en-us/download/details.aspx?id=7558`](https://www.microsoft.com/en-us/download/details.aspx?id=7558)).

* The built-in patching tools for Linux-based systems (such as Yellowdog Updater, Modified \[yum\], and YaST Online Update).

## Hardening Your Systems

In addition to patching your systems, you have to make sure that your systems are *hardened* (locked down) against the security vulnerabilities that patches can’t fix. I’ve found that many people stop with patching, thinking that their systems are secure, but that’s just not the case. Throughout the years, I’ve seen network administrators ignore recommended hardening practices from such organizations as the National Institute of Standards and Technology Computer Security Resource Center ([`http://csrc.nist.gov/publications/PubsSPs.html`](http://csrc.nist.gov/publications/PubsSPs.html)) and the Center for Internet Security ([`www.cisecurity.org`](http://www.cisecurity.org)), leaving many security holes wide open. I believe, however, that hardening systems against malicious attack isn’t foolproof either. Because every system and every organization’s needs are different, there’s no one-size-fits-all solution, so you have to strike a balance without relying on any option too much.

![remember](img/remember.png)After you apply patches, it’s a good idea to rescan your systems for vulnerabilities to confirm that the patches took.

This book presents hardening countermeasures that you can implement for your network, computers, and even physical systems and people. I find that these countermeasures work best.

Implementing at least basic security practices is critical. Whether you’re installing a firewall on the network or requiring users to have strong passwords via a Windows Active Directory domain GPO, you *must* address the basics if you want any modicum of security. Beyond patching, if you follow the countermeasures I document, add the other well-known security practices for network systems (routers, servers, workstations, and so on) that are freely available on the Internet, and perform ongoing security tests, you can rest assured that you’re doing your best to keep your organization’s information secure.

## Assessing Your Security Infrastructure

Reviewing your overall security infrastructure in the following ways can add oomph to your systems:

* **Look at how your overall network is designed.** Consider organizational issues, such as whether policies are in place, maintained, or even taken seriously. Physical issues count as well. Determine whether members of management have buy-in on information security and compliance, or whether they simply shrug the measure off as an unnecessary expense or barrier to conducting business.

* **Map your network by using the information you gather from the security tests in this book.** Updating existing documentation is a major necessity. Outline IP addresses, running services, and whatever else you discover. Draw your network diagram. Network design and security issues are a whole lot easier to assess when you can work with them visually. Although I prefer to use a technical drawing program such as Microsoft Visio or Cheops-ng ([`http://cheops-ng.sourceforge.net`](http://cheops-ng.sourceforge.net)) to create network diagrams, such a tool isn’t necessary. You can draw your map on a whiteboard, as many people do, which is just fine.

  ![remember](img/remember.png)Be sure to update your diagrams when your network changes or once every year or so.

* **Think about your approach to correcting vulnerabilities and increasing your organization’s overall security.** Are you focusing all your efforts on the perimeter and not on a layered security approach? Think about how most convenience stores and banks are protected. Security cameras focus on the cash registers, teller computers, and surrounding areas — not just on the parking lot or entrances. Look at security from a defense in-depth perspective. Make sure that several layers of security are in place in case one measure fails so that the attacker must go through other barriers to carry out a successful attack.

考虑在更高层面上审视安全策略和业务流程。记录已建立的安全策略和流程，并评估其有效性。确定在安全监督和执行方面存在的风险。没有任何组织能免于在此方面出现漏洞。审视组织内部的整体安全文化，从外部视角观察其状态；再从内部视角审视。了解客户或业务合作伙伴对贵组织处理其敏感信息的看法。我可以百分之百有把握，存在一些（可能多个）问题需要在安全的软件层面加以改进。

![tip 加强安全并不完全依赖于补丁和其他技术性安全控制。有时，您的 IT 与安全管理程序需要进行微调。有时，您需要启动全新的措施。有时，您仅需停止做某些事项。我多年来一直在撰写关于 IT 与安全程序（误）管理的文章，您可以在我的网站（[`www.principlelogic.com/management.html`](https://www.principlelogic.com/management.html)）上找到大量相关内容。

从高层次、非技术性的角度审视安全，会让您对安全漏洞和整体业务风险获得全新的视角。这一过程需要时间和精力，但在建立安全基线后，管理新出现的威胁和漏洞便显得更为容易。

Chapter 19

## 管理安全流程

IN THIS CHAPTER

![check](img/check.png)**自动化任务**

![check](img/check.png)**监控异常行为**

![check](img/check.png)**将安全测试外包**

![check](img/check.png)**让安全始终在大家的视野中**

信息安全是一项持续的过程，必须随时间持续有效管理才能取得成功。此管理不仅仅是偶尔打补丁、加固系统。反复进行安全测试至关重要；安全漏洞不断出现。换句话说，安全测试是整体信息安全的快照，因此必须持续进行测试以跟上最新的问题。持续的严谨性不仅是为了满足各类法律法规的合规要求，也是降低信息系统相关业务风险的关键。

## 自动化安全评估流程

您可以在本书中对以下安全测试进行大部分自动化：

* Ping 探测和端口扫描，用于展示可用系统及其运行的服务（这是一个常见的疏忽，往往是更大安全问题的开端）。

* 密码 cracking 测试，用于尝试访问外部 Web 应用、远程访问服务器等。

* 漏洞扫描，用于检查缺失的补丁、配置错误以及可被利用的漏洞。

* 对漏洞的利用（至少在一定程度上）。

![remember](img/remember.png)您必须拥有合适的工具来自动化这些测试，例如：

* 部分商业工具可以定期执行扫描/检查并生成报告，几乎不需要人工干预——只需在前期进行少量设置和调度时间。这正是我喜欢许多商业（主要自动化）安全测试工具的原因，如 Nexpose 与 Acunetix Web Vulnerability Scanner。这些工具提供的自动化能够为其价格争取正当性，尤其是您无需在凌晨 2 点或全天候待命。

* 独立安全工具（如 Nmap、John the Ripper、Aircrack-ng）虽好，但单靠它们仍不足。您可以编写脚本、使用 Windows 任务计划程序和 AT 命令（Windows）或 cron 作业（Linux）进行自动化，但仍需人工步骤和人类智慧。

这些工具及其他许多工具的链接位于附录。

![warning](img/warning.png)某些测试和阶段——如新系统的枚举、各类 Web 应用测试、社会工程学以及实体安全巡检——根本无法实现“自动驾驶”。您必须亲自参与。

![remember](img/remember.png)即使是最聪明的计算机专家系统也无法完成安全测试。良好的安全需要技术专长、经验以及老老实际的常识。

## 监控恶意行为

监控与安全相关的事件是持续安全工作的关键。监控可以是基础且琐碎的，例如每日检查路由器、防火墙和关键服务器的日志文件。高级监控可能包括部署安全事件与事件管理（SIEM）系统，以监控环境中发生的每一件事。常见做法是部署入侵防御系统（IPS）或数据丢失防护（DLP）系统并监测恶意行为。

监控安全事件的难点在于人类觉得它无聊且难以有效执行。每天，您或许会在早上腾出时间——比如第一时间——检查前一晚或周末的关键日志，以挖掘入侵及其他安全问题。但您真的想让自己或他人经历这种“折磨”吗？

手动筛查日志文件可能不是最佳监控方式。以下缺点值得注意：

* 在系统日志中找到关键安全事件十分困难，甚至不可能。这对普通人而言过于繁琐。

* 根据使用的日志类型和安全设备，可能无法捕获某些安全事件，例如 IPS 规避技术以及通过网络允许的端口进行的 exploit。

![tip](img/tip.png)与其在所有日志文件中翻找难以发现的入侵痕迹，我建议：

* 在合理且可行的范围内启用系统日志记录。您不必捕获所有计算机和网络事件，但应重点关注显性的事件，如登录失败、策略变更和未经授权的文件访问。

* 使用 syslog 将安全事件记录到网络内部或云端的中央服务器上。尽量避免在本地主机上保存日志，以防止恶意分子篡改日志掩盖踪迹。

![tip](img/tip.png)下面是几种解决安全监控难题的良好方案：

* **购买事件记录系统。** 低价且有效的方案包括 GFI EventsManager（[www.gfi.com/products-and-solutions/network-security-solutions/gfi-eventsmanager](http://www.gfi.com/products-and-solutions/network-security-solutions/gfi-eventsmanager)）。通常，低价系统仅支持单一操作系统平台，Microsoft Windows 是最常见的。高端解决方案如 ArcSight Data Platform（[`software.microfocus.com/en-us/products/siem-data-collection-log-management-platform/overview`](https://software.microfocus.com/en-us/products/siem-data-collection-log-management-platform/overview)）则提供跨平台日志管理以及事件关联功能，帮助您追踪安全问题的根源以及事件期间受影响的各个系统。

* **将安全监控外包给云端的第三方托管安全服务提供商（MSSP）。** 互联网兴起时出现了大量 MSSP，但如今只有少数大型公司存续。外包安全监控的价值在于这些公司通常拥有您难以负担或维护的设施和工具。MSSP 还拥有全天候的分析人员，能够将其他客户的安全经验和知识分享给您。

当这些云服务提供商发现安全漏洞或入侵时，通常会立即解决问题，往往无需您的介入。我建议您检查第三方公司及其服务是否可以腾出部分时间和资源，以便您能够专注于其他事项。切勿仅依赖他们的监控工作。云服务提供商可能难以发现内部滥用、社会工程攻击以及通过安全会话（如 HTTPS）传输的 Web 应用程序漏洞利用。您仍需参与。

## 外包安全评估

外包您的安全评估是流行且极好的方式，可让组织获得对其安全态势的中立第三方视角。外包可为您提供一种制衡机制，这是客户、业务合作伙伴、审计员和监管机构所喜欢且常常要求的。

![remember](img/remember.png)外包漏洞和渗透测试并不便宜。许多组织在测试需求不同的情况下，花费数万美元或更多。您自己完成这些工作同样费用高昂，因为要计入时间、工具以及所需的培训费用。很有可能，自己操作并不如聘请专业服务有效！通过全新的视角获得的中立视角，可能会发现您因“只见树木而看不到森林”而未曾思考的问题。

![warning](img/warning.png)大量机密信息面临风险，因此您必须信任外部顾问和供应商。在寻找独立专家或供应商合作时，请考虑以下问题：

* **您的安全提供商是站在您这边，还是主要为自身利益着想？**

* **供应商是为了寻找您的安全漏洞以便推销产品，还是保持中立，专注于安全评估工作？** 许多供应商会通过推荐其自家产品或与合作伙伴关联的产品和服务来获取额外收益，这些产品和服务可能并非您的真实需求。想象一下，家庭检查员告诉您他能解决他发现的所有问题。请确保任何潜在的利益冲突不会对您的预算和业务造成不利影响。

* **供应商是否提供其他 IT 或安全服务，还是专注于安全？** 让信息安全专家进行此类测试可能优于与 IT 通用型组织合作。毕竟，您不会聘请一般企业律师处理专利，或请家庭医生进行手术，亦不会请手 yman 重新布线您的房屋。

* **供应商的招聘与解聘政策是什么？** 请寻找供应商为降低风险所采取的安全和法律措施。例如，是否有员工可能滥用与您的关系？他们是否可能携带敏感信息外泄，或将您的漏洞分享给不需要知晓的人？

* **供应商是否理解您的业务需求？** 请让供应商在工作说明书中记录您的需求列表，确保双方达成一致。

* **供应商的沟通能力如何？** 您必须信任供应商及时保持告知并跟进。

* **您确定谁将执行测试吗？** 了解是否由单一人员完成测试，或由专业领域专家分别负责不同领域。还需确认该人员是否刚毕业，或是否在海外，并判断您是否对其工作充满信心。

* **供应商是否有经验，能够推荐切实可行且有效的应对措施？** 供应商不应仅交付报告并说“祝您好运”！您需要切实可行的解决方案。

* **供应商的动机是什么？** 您不希望供应商只为快速获利而提供服务，付出最小努力与价值。您希望供应商致力于建立忠诚关系，实现长期合作。

![tip](img/tip.png)长期合作的良好组织将使您的持续工作更加简便。向潜在提供商索要多个参考案例。如果组织难以提供参考，请寻找其他提供商。

您的提供商应与您签订包含双方保密条款的合同。请确保双方均签署此合同，以保护贵组织。

## 树立安全意识文化

您的网络用户往往是您的**第一道也是最后一道防线**。确保您的安全测试工作和信息安全计划的投入不会因一个普通员工失误而让恶意攻击者获得入口。

以下元素可帮助在组织中建立安全意识文化：

* **将安全意识和持续培训作为所有网络用户（包括管理层和承包商）的活动过程。** 仅在新员工入职时进行一次性培训已不足。意识和培训必须定期且持续，以确保安全信息始终在人们心中。

* ![tip](img/tip.png) **将意识和培训视为长期业务投资。** 安全意识与培训无需昂贵。您可以购买海报、鼠标垫、屏幕保护贴、笔、便签等物品，让安全始终在每个人的视野中。部分创意供应商包括 Greenidea, Inc. ([`www.greenidea.com`](http://www.greenidea.com))、Security Awareness, Inc. ([`www.securityawareness.com`](http://www.securityawareness.com))，以及（我最喜欢的，因创始人 Winn Schwartau 幽默且不 afraid 直言不讳）The Security Awareness Company ([`www.thesecurityawarenesscompany.com`](http://www.thesecurityawarenesscompany.com))。

* **让管理层了解安全情况并保持知情。** 如果您让管理层对您的工作视而不见，他们很可能永远不会支持您。我在 第 20 章 中介绍了如何获得管理层的支持。

* **使安全信息与受众匹配，并尽可能保持非技术化。** 向不懂技术的人灌输专业术语只会适得其反。您应以每个受众为切入点，说明安全对他们的影响以及他们如何帮助。

* **以身作则。** 表明您对安全高度重视，并提供证据说明其他人也应如此。

如果您能获得管理层和用户的支持，并持续投入努力，使安全成为日常业务常规，您就能塑造组织文化。虽过程费力，却能带来超出您想象的安全价值。我亲眼见证了其影响！

## 保持其他安全工作的同步

周期性且持续的安全评估并非信息安全的全部。测试不能保证安全，但它是关键要素之一。此类测试必须融入包含以下内容的持续安全程序中：

* 更高层次的信息风险评估。

* 制定并执行的强力安全政策与标准。

* 经过测试的可靠事件响应与业务连续性计划。

* 有效的安全意识与培训项目。

理想情况下，您的安全程序应通过增加价值或至少保持平衡来产生收益。这些努力可能需要增加人员或外包更多安全帮助。

![remember](img/remember.png)不要忘记为自己和任何帮助你的同事进行正式培训。你必须持续自我教育，以在安全领域保持领先。认证伦理黑客（CEH）和认证信息系统安全专业人员（CISSP）都是值得追求的认证。我在附录中列出了一些优秀的会议、研讨会和在线资源。

第 7 部分

## 十的部分

在这部分里…

让正确的人站在你这边，确保安全。

理解漏洞和渗透测试对于应对你的安全风险至关重要。

避免 IT 和安全专业人员在测试安全漏洞时常见的错误。

通过工具和相关资源协助你的安全评估和管理工作。

第 20 章

## 获得安全认同的十个建议

获得和维护支持你安全测试工作所需的认同和赞助的关键步骤有很多。本章我描述了我发现的十个最有效的方法。

### 培养盟友和赞助人

虽然著名的泄露事件和合规压力在推动进程，但向管理层推销安全并不是一件你想独自面对的事。找一个盟友——最好是你的直接上级或组织中层以上的人员。选择一位既理解安全测试的价值，也理解整体信息安全价值的人。虽然此人可能无法直接为你发声，但他或她可以作为中立的赞助人被看到，从而提升你的可信度。

### 不要做愚蠢的 FUD 推手

福尔摩斯说：“在拥有数据之前，进行理论化是一个巨大的错误。”要为信息安全和适当的测试争取良好立场，请用相关数据支持你的论点。但不要为了煽动恐惧、不确定性和疑虑（FUD）而夸大其词。业务领导能看透这种手段。专注于用实用建议教育管理层。讨论与威胁成比例的合理恐惧是可以的。但不要像“小鸡·利特尔”那样，总说天空要塌下来。这会让 IT 和安全领域以外的人感到疲惫，长期来看只会伤害你。

### 展示组织无法承受被黑客攻击

说明组织依赖于其信息系统。创建假设情境（即业务影响评估）来展示可能发生的情况、组织声誉可能受损，以及组织可能需要多久无法使用其网络、计算机和数据。询问业务领导如果没有电脑系统和 IT 人员他们会怎么做，以及如果敏感业务或客户信息被泄露他们会怎么做。展示真实的泄露案例，包括恶意软件、物理安全和社会工程等问题。

同时保持积极态度。不要用 FUD（恐惧、不确定性和疑虑）的消极方式向管理层施压，而是让他们了解重要的安全事件。他们很可能已经在主要商业杂志和报纸上阅读相关内容。找出如何将这些故事应用到你的情境中。为了帮助管理层产生共鸣，找到与相似企业、竞争对手或行业相关的故事。

向管理层展示组织*确实*拥有黑客想要的东西。同时也向他们展示内部人员可以利用其访问权限做什么。一个常见的误解是，那些对信息安全威胁和漏洞不了解的人认为组织或网络并不真的有风险。务必指出因黑客攻击可能造成的损失成本，包括：

* 错失机会

* 知识产权泄露

* 赔偿责任问题

* 事件响应和取证成本

* 法律成本和判决

* 合规相关罚款

* 刑事处罚

* 生产力损失

* 更换丢失或损坏的信息或系统的费用

* 修复声誉的成本（建立声誉可能需要一生，而毁掉声誉只需几分钟）

### 阐述安全测试的一般好处

在前一部分列出的潜在成本之外，还要说明主动测试如何发现信息系统中可能被忽视的安全漏洞。告诉管理层，在漏洞和渗透测试（有时称为伦理黑客）的语境下，安全测试是一种像坏人一样思考的方式，以便保护自己免受他们侵害——这在孙子的《孙子兵法》中有详细阐述的“知己知彼”心态。

### 展示安全测试如何具体帮助组织

记录支持整体业务目标的好处，例如：

* 证明安全不需要 ultra-expensive（昂贵），长期来看可以为组织节省金钱。提出以下观点：

  * 先建立安全比事后补加更容易、更便宜。

  * 如果做得当，安全不需要阻碍生产力。

* 讨论如果信息系统安全到位，新产品或服务可以为组织提供竞争优势，前提是满足以下条件：

  * 遵守州、联邦和国际隐私与安全法规。

  * 满足业务合作伙伴和客户的要求。

  * 管理层和公司在客户和业务合作伙伴眼中呈现出可信度。

  * 稳健的安全测试程序和相应的修复流程表明组织正在保护敏感的客户和业务信息。

* 阐述深入安全测试的合规与审计好处。

### 了解业务

了解业务——它是如何运作的，关键人物是谁，以及涉及哪些政治因素。这包括：

* 参加会议以“看与被看”，这能证明你关心业务。

* 作为一名有价值且愿意为业务做出贡献的人。

* 了解你的对手。再次使用“知己知彼”的心态。如果你了解你所面对的内部人员及其可能的异议，获得认同会容易得多。这种方法不仅适用于管理层，也适用于你的同事以及几乎网络上的每个用户。甚至你的董事会成员可能也有疑问和顾虑。

### 建立你的可信度

我认为 IT 和安全专业人士面临的最大障碍之一是人们不“get”我们。你的可信度就是你唯一拥有的资产。专注于以下四个特质来建立并保持它：

* 对组织保持积极态度，证明你真的在认真做事。你的态度至关重要。

* 同情管理层，向他们展示你理解业务方面以及他们所面对的挑战。

* 找到帮助他人获得他们需要的东西的方法，而不仅仅是索取。

* 要创造任何积极的业务关系，你必须值得信赖。如果你随着时间的推移建立信任，推销安全就会变得容易得多。

### 在管理层的层面上发言

虽然听起来很酷，但 IT 和安全领域外的人对“网络战 rior”式的技术话术并不感兴趣。限制或减少你可信度的最佳方式之一是与他人沟通方式不当。与其试图给人留下深刻印象，不如用他们需要听到的语言交流。停止试图给人留下印象。否则，你的话很可能会落在他们听不到的地方，导致你失去可信度。

![warning](img/warning.png)我见过无数 IT 和安全专业人士在开始讲话时就失去业务领导——一千兆字节；加密协议；包、包、包到处都是！将安全问题与日常业务流程、工作职能和整体目标联系起来，周期。

### 展示你努力的价值

这一项目正是“实践层面”的关键所在。如果你能持续证明你所做的工作为业务带来价值，你就能保持稳健的进度，而无需不断向管理层施压以维持安全测试项目的持续运行。请牢记以下要点：

* **记录你在 IT 和安全领域的参与情况，并为管理层提供组织安全状况的持续报告。** 向管理层提供组织系统如何（或将如何）免受攻击的具体案例。

* **以具体结果作为概念验证。** 展示你创建的示例安全评估报告，或你打算使用的安全工具的扫描结果。

* **将管理层和用户的疑虑、顾虑和异议视为获取更多信息的请求。** 找到答案，并将这些问题视为进一步推广你努力的机会。

### 保持灵活和适应性

做好应对怀疑和拒绝的准备。尽管安全话题备受关注，但拒绝仍时有发生，尤其是来自组织中与 IT 和安全相对脱节的高层管理者。同样，中层管理层如果只会制造复杂性，也是问题的一部分。

![remember](img/remember.png)`Don’t get defensive. Security is a long-term process, not a short-term assessment, product, or service. Start small. Use a limited amount of resources — such as budget, tools, and time — and then build the program over the long haul.`

![tip](img/tip.png)`Psychological studies have found that new ideas presented casually and without pressure are more likely to be considered and accepted than ideas that are forced on people under a deadline. If you focus on your approach at least as much as you focus on the content of what you’re presenting, you can often get people on your side, and in return, you’ll accomplish a lot more with your security program.`

第 21 章

## 十个理由：黑客是唯一有效的测试方式

从伦理黑客的视角进行安全测试，不仅仅是为了好玩或炫耀。出于诸多商业原因，它是发现组织中真正重要的安全漏洞的唯一有效方式。

### 坏人会有坏念头，使用好工具，并开发新方法

如果你想跟上外部攻击者和恶意内部人员的步伐，就必须保持最新的攻击方法和工具的更新。我在这本书中会介绍一些最新的技巧、技术和工具。

### IT 治理和合规性不只是高层次检查清单的审计

面对政府和行业法规的重重压力，你的企业几乎没有选择的余地。你必须应对安全问题。问题是，符合这些法律和法规并不自动意味着你的网络和信息是安全的。支付卡行业数据安全标准（PCI DSS）便是例证。无数企业运行漏洞扫描、回答自评问卷，并认为他们已经完成了管理信息安全计划的所有必要工作。同样的情况也适用于符合一般数据保护条例（GDPR）和健康保险可移植性和责任法案（HIPAA）。

你必须摘下合规审计的盲目眼镜，从以合规为中心的方法转向以风险为中心的方法。利用本书涵盖的工具和技术，你可以更深入地挖掘对你业务造成最大挑战的漏洞。

### 漏洞扫描和渗透测试补充审计和安全评估

毫无疑问，你组织中有人比你更了解高层安全审计，但如果你能说服他们进行更深入的安全测试，并将其纳入现有的安全计划（如内部审计和合规性检查），审计过程将更深入，结果也会更好。人人皆胜。

### 客户和合作伙伴会询问你的系统有多安全

许多企业现在要求对其业务合作伙伴进行深入的安全评估，同理也适用于某些客户。规模较大的公司几乎总是想知道其信息在被处理或存储于你的环境中时的安全程度。你不能依赖数据中心审计报告（如 commonly referenced SSAE18 Service Organizational Controls (SOC 2) 标准）来获取数据中心安全审计信息。唯一确定现状的方法是使用本书涵盖的方法和工具。

### 平均规律对企业不利

信息系统日益复杂化，字面意义上。随着云计算、虚拟化和移动设备在企业中居于核心位置，IT 和安全管理者保持跟上节奏变得越来越困难。这些复杂性最终会对你不利，而有利于坏人。犯罪黑客只需找到一个关键漏洞即可成功。而你必须找出（并修复）所有漏洞，或者至少是那些造成最大漏洞的漏洞。

如果你想保持知情并确保关键业务系统（及其处理和存储的敏感信息）的安全，你必须以恶意心态看待问题，并定期、持续地进行观察，而不仅仅是一次或不时进行。

### 安全评估能改善对业务威胁的理解

你可以说密码很弱或补丁缺失，但利用这些漏洞进行利用并展示结果是完全不同的事情。没有比展示我在这本书中描述的测试方法的结果更能证明问题的存在，并激励管理层采取行动了。

### 如果发生泄露，你有依据可依

在恶意内部人员或外部攻击者 breaches 你的安全，或你的业务因违法或不符合法律法规而被起诉、或业务合规性受损的情况下，管理层至少可以证明它通过适当的测试正在履行其发现安全风险的尽职调查义务。你必须确保适当的测试确实在进行！

相关且可能出现的问题之一是知道存在问题却未加以修复。你不想让律师及其专家证人指出你的企业在安全测试或后续跟进上存在懈怠。

### 深入测试会暴露出系统的最坏一面

有人在做自我评估或高层审计时，可能会发现你漏掉的安全最佳实践，但他不会发现大多数通过深入的安全漏洞和渗透测试能够揭示的安全漏洞。我在这本书中描述的测试方法能够让系统的所有缺陷（warts and all）显露无遗。

### 结合漏洞扫描和渗透测试是你需要的

单独进行渗透测试通常不足以发现系统中的所有问题，因为传统渗透测试的范围太有限。基本漏洞扫描也如此。当你结合这两种方法时，你将获得物超所值的回报。

### 适当的测试能揭示被忽略的弱点

进行适当的安全评估不仅能揭示技术、物理和人为弱点，还能揭示 IT 和安全运营中的根本原因，如补丁管理、变更管理和缺乏用户意识。否则，你可能直到为时已晚才发现这些弱点。

第 22 章

## 十个致命错误

在你的安全测试中做出错误的选择会对你的工作乃至职业产生灾难性影响。在这一章中，我讨论了在执行安全评估工作时需要格外警惕的十个潜在陷阱。

### 未获得批准

在获得事先的书面批准后，例如电子邮件、内部备忘录或正式合同，用于你的安全测试工作（无论是来自管理层还是客户）是必须的。除了可能影响你测试的法律条文之外，它是你的“脱罪”凭证。

![warning 不要做任何例外 — — 尤其是当你为客户进行工作时。确保将此文档的签署副本存档以确保你受到保护。## 假设你能找到所有漏洞所以多种安全漏洞 — — 已知和未知 — — 你无法在测试中找到它们全部。不要保证你能找到系统中的*所有*安全漏洞。你正在做一件你无法完成的事。坚持以下原则：* 保持现实。* 使用良好的工具。* 了解你的系统，并练习磨练你的技巧。* 随时间改进。我在 第 5 章 到 第 16 章 以各种方式介绍这些规则。## 假设你能消除所有漏洞在网络、计算机和应用程序方面，绝对安全是不可实现的。你不可能防止*所有*安全漏洞，但如果你发现低挂果实 — — 即造成大多数风险的那些漏洞 — — 并完成以下任务，你会做得好：* 遵循稳健的实践。几十年来一直存在的安全基础。* 修补并加固你的系统。* 根据你的预算和业务需求，在可行的地方应用合理的安全对策。许多章节，如 第 4 部分 中的操作系统章节，都涵盖这些领域。还要记住，你会有未计划的费用。你可能会发现很多安全问题，需要预算来填补这些漏洞。也许你现在面临“应有尽有”的问题，必须修复发现的问题。因此，你需要从风险的角度来处理信息安全，并确保所有相关人员都在位置上。## 只进行一次测试安全评估只是你整体安全状态的瞬间快照。新的威胁和漏洞不断出现，因此你必须定期、持续地进行这些测试，以确保你跟上最新的安全防护措施。为未来几个月和几年制定短期和长期的安全测试计划。## 假设你一无所知尽管有些 IT 领域的人不同意，但没有人在 IT 或信息安全领域完全懂得一门之隔。跟上所有软件版本、硬件型号和新兴技术，更不用说相关的安全威胁和漏洞，是不可能的。真正的 IT 和信息安全专业人员知道自己的局限 — — 即他们*不知道*什么。他们*知道*在哪里可以通过各种在线资源找到答案，例如我在附录中列出的那些。## 在不从黑客视角审视时运行测试思考恶意外部人员或背叛内部人员如何攻击你的网络和计算机。获取全新视角；尝试超出传统思维，思考系统如何被取 offline，信息如何被窃取，等等。![tip](img/tip.png)研究罪犯和黑客的行为以及常见的攻击手法，以便知道在哪里进行测试。我一直在 [`www.principlelogic.com`](https://www.principlelogic.com) 博客记录此主题。查看附录，获取其他值得信赖的资源，帮助你在这方面。

### 没有测试正确的系统

专注于最重要的系统和信息。你可以整天在运行 Windows XP 的独立台式机或培训室打印机上进行黑客攻击，但这有什么用处？可能没有，但你永远不知道。你的最大风险可能就在看似最不重要的系统上。专注于既*紧急*又*重要*的内容。

### 没有使用正确的工具

没有正确的工具就无法完成任务，这与在家里、修车或园艺时一样，良好的工具是必须的。下载我在本书和附录中提到的免费和试用工具。如果可以，购买商业工具；它们通常物超所值。没有任何一种安全工具能做所有事情。

![remember](img/remember.png)构建你的工具箱并熟悉你的工具将节省大量精力，让你以出色的成果 impress 他人，并帮助最小化企业的风险。

### 在错误的时间攻击生产系统

一种最佳方式是让你的经理或客户失去信任 — — 在所有人使用系统时对生产系统进行安全测试。对于运行老旧、脆弱操作系统或遗留应用程序的公司来说，此问题尤为严重。如果你在错误的时间测试系统，你可能会在最糟糕的时刻对关键系统产生负面影响。

确保你知道最佳测试时间，这可能是深夜。 (我并没有说信息安全测试是轻松的！) 奇怪的测试时间可能正当使用安全工具和其他辅助 utilities 自动化某些任务，例如允许你在特定时间运行漏洞扫描仪。

### 外包测试且不保持参与

外包是件好事，但你必须在整个过程中保持参与。不要在未经跟进的情况下将安全测试的 reins 交给第三方顾问或托管服务提供商。除非你想让经理或客户失望，否则不要让第三方供应商的工作闲置。除非他们像我一样光头（但你懂我的意思），否则要让他们“头疼”。你不能外包责任，所以保持联系！

附录

## 工具和资源

要跟上最新和最好的安全测试工具和资源，你需要知道去哪里。本附录包含我最喜欢的安全网站、工具、资源和更多，可帮助你在持续的安全评估程序中受益。

![tip](img/tip.png)本书的在线快速参考包含本附录中列出的所有在线工具和资源的链接。请访问 [www.dummies.com/cheatsheet/hacking](http://www.dummies.com/cheatsheet/hacking) 查看。

### 高级恶意软件

Carbon Black — [`https://www.carbonblack.com/products/solutions/use-case`](https://www.carbonblack.com/products/solutions/use-case)

Core Network Insight — [`https://www.coresecurity.com/network-insight`](https://www.coresecurity.com/network-insight)

### 蓝牙

Blooover — [`https://trifinite.org/trifinite_stuff_blooover.html`](https://trifinite.org/trifinite_stuff_blooover.html)

BlueScanner — [`https://sourceforge.net/projects/bluescanner`](https://sourceforge.net/projects/bluescanner)

Bluesnarfer — [`www.alighieri.org/tools/bluesnarfer.tar.gz`](http://www.alighieri.org/tools/bluesnarfer.tar.gz)

BlueSniper Rifle — [`http://www.tomsguide.com/us/how-to-bluesniper-pt1,review-408.html`](http://www.tomsguide.com/us/how-to-bluesniper-pt1,review-408.html)

BTScanner for XP — [`www.pentest.co.uk/src/btscanner_1_0_0.zip`](http://www.pentest.co.uk/src/btscanner_1_0_0.zip)

Car Whisperer — [`https://trifinite.org/trifinite_stuff_carwhisperer.html`](https://trifinite.org/trifinite_stuff_carwhisperer.html)

Smurf — [`www.gatefold.co.uk/smurf`](http://www.gatefold.co.uk/smurf/)

### 认证

Certified Information Security Manager — [`www.isaca.org/Certification/CISM-Certified-Information-Security-Manager/Pages/default.aspx`](http://www.isaca.org/Certification/CISM-Certified-Information-Security-Manager/Pages/default.aspx/)

Certified Information Systems Security Professional — [`https://www.isc2.org/Certifications/CISSP`](https://www.isc2.org/Certifications/CISSP)

Certified Wireless Security Professional — [`http://www.cwnp.com/certifications/cwsp`](http://www.cwnp.com/certifications/cwsp)

CompTIA Security+ — [`https://certification.comptia.org/certifications/security`](https://certification.comptia.org/certifications/security)

SANS GIAC — [`https://www.giac.org`](https://www.giac.org)

### 数据库

Advanced SQL Password Recovery — [`www.elcomsoft.com/asqlpr.html`](http://www.elcomsoft.com/asqlpr.html)

AppDetectivePro — [`https://www.trustwave.com/Products/Database-Security/AppDetectivePRO`](https://www.trustwave.com/Products/Database-Security/AppDetectivePRO)

ElcomSoft Distributed Password Recovery — [`https://www.elcomsoft.com/edpr.html`](https://www.elcomsoft.com/edpr.html)

Idera — [`https://www.idera.com`](https://www.idera.com)

Microsoft SQL Server Management Studio — [`https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-2017`](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-2017)

Nexpose — [`https://www.rapid7.com/vulnerability-scanner.jsp`](https://www.rapid7.com/vulnerability-scanner.jsp)

Pete Finnigan’s listing of Oracle scanning tools — [`www.petefinnigan.com/tools.htm`](http://www.petefinnigan.com/tools.htm)

QualysGuard — [`https://www.qualys.com`](https://www.qualys.com/)

SQLPing3 — [`www.sqlsecurity.com/downloads`](http://www.sqlsecurity.com/downloads/)

### 拒绝服务（DoS）保护

Cloudflare — [`https://www.cloudflare.com`](https://www.cloudflare.com)

DOSarrest — [`https://www.dosarrest.com`](https://www.dosarrest.com)

Incapsula — [`https://www.incapsula.com`](https://www.incapsula.com)

### 利用

Metasploit — [`https://www.metasploit.com`](https://www.metasploit.com)

Offensive Security’s Exploit Database — [`https://www.exploit-db.com`](https://www.exploit-db.com)

Pwnie Express — [`https://pwnieexpress.com`](https://pwnieexpress.com/)

### 一般研究工具

AFRINIC — [`https://www.afrinic.net`](https://www.afrinic.net)

APNIC — [`https://www.apnic.net`](https://www.apnic.net)

ARIN — [`http://whois.arin.net/ui`](http://whois.arin.net/ui)

Bing — [`https://www.bing.com`](https://www.bing.com)

DNSstuff — [`https://www.dnsstuff.com`](https://www.dnsstuff.com)

DNS Tools — [`www.dnstools.com`](http://www.dnstools.com/)

The File Extension Source — [`http://filext.com`](http://filext.com/)

Google — [`https://www.google.com`](https://www.google.com)

GoogleGuide advanced operators — [`www.googleguide.com/advanced_operators.html`](http://www.googleguide.com/advanced_operators.html)

Government domains — [`https://domains.dotgov.gov/dotgov-web/registration/whois.xhtml?_m=3`](https://domains.dotgov.gov/dotgov-web/registration/whois.xhtml?_m=3)

D&B Hoover’s business information — [`www.hoovers.com`](http://www.hoovers.com/)

LACNIC — [`www.lacnic.net`](http://www.lacnic.net/)

Netcraft’s *What’s that site running?* — [`https://www.netcraft.com`](https://www.netcraft.com)

RIPE Network Coordination Centre — [`https://apps.db.ripe.net/db-web-ui/#/query`](https://apps.db.ripe.net/db-web-ui/#/query)

theHarvester — [`https://code.google.com/p/theharvester`](https://code.google.com/p/theharvester/)

U.S. Patent and Trademark Office — [`https://www.uspto.gov`](https://www.uspto.gov)

US Search.com — [`https://www.ussearch.com`](https://www.ussearch.com)

U.S. Securities and Exchange Commission — [`https://www.sec.gov/edgar.shtml`](https://www.sec.gov/edgar.shtml)

WhatIsMyIP — [`https://www.whatismyip.com`](https://www.whatismyip.com)

Whois — [`https://www.whois.net`](https://www.whois.net)

Yahoo! Finance — [`https://finance.yahoo.com`](https://finance.yahoo.com)

Zabasearch — [`www.zabasearch.com`](http://www.zabasearch.com/)

### 黑客相关

*2600 The Hacker Quarterly* — [`https://www.2600.com`](https://www.2600.com)

Hacker T-shirts, equipment, and other trinkets — [`https://www.thinkgeek.com`](https://www.thinkgeek.com)

*Hakin9* — [`https://hakin9.org`](https://hakin9.org)

*(IN)SECURE Magazine* — [`https://www.helpnetsecurity.com/insecuremag-archive/Phrack`](https://www.helpnetsecurity.com/insecuremag-archive/Phrack) — [`www.phrack.org`](http://www.phrack.org/)

### 键盘记录器

KeyGhost — [`www.keyghost.com`](http://www.keyghost.com/)

### 法律与法规

Computer Fraud and Abuse Act — [`https://www.fas.org/sgp/crs/misc/RS20830.pdf`](https://www.fas.org/sgp/crs/misc/RS20830.pdf)

Digital Millennium Copyright Act (DMCA) — [`https://www.eff.org/issues/dmca`](https://www.eff.org/issues/dmca)

Global Data Protection Regulation (GDPR) — [`https://www.eugdpr.org`](https://www.eugdpr.org)

Gramm-Leach-Bliley Act (GLBA) Safeguards Rule — [`https://www.ftc.gov/tips-advice/business-center/privacy-and-security/gramm-leach-bliley-act`](https://www.ftc.gov/tips-advice/business-center/privacy-and-security/gramm-leach-bliley-act)

Health Insurance Portability and Accountability Act (HIPAA) Security Rule — [`https://www.hhs.gov/ocr/privacy/hipaa/understanding/srsummary.html`](https://www.hhs.gov/ocr/privacy/hipaa/understanding/srsummary.html)

Payment Card Industry Data Security Standard (PCI DSS) — [`https://www.pcisecuritystandards.org/pci_security`](https://www.pcisecuritystandards.org/pci_security/)

U.S. Security Breach Notification Laws — [`http://www.ncsl.org/research/telecommunications-and-information-technology/security-breach-notification-laws.aspx`](http://www.ncsl.org/research/telecommunications-and-information-technology/security-breach-notification-laws.aspx)

### Linux

GFI LanGuard — [`https://www.gfi.com/products-and-solutions/network-security-solutions/gfi-languard3`](https://www.gfi.com/products-and-solutions/network-security-solutions/gfi-languard3)

Kali Linux — [`https://www.kali.org`](https://www.kali.org)

Linux Security Auditing Tool (LSAT) — [`http://usat.sourceforge.net`](http://usat.sourceforge.net/)

Nexpose — [`https://www.rapid7.com/products/nexpose/`](https://www.rapid7.com/products/nexpose/)

QualysGuard — [`https://www.qualys.com`](https://www.qualys.com)

SourceForge — [`https://sourceforge.net`](https://sourceforge.net)

THC-Amap — [`www.thc.org/thc-amap`](https://www.thc.org/thc-amap/)

Tiger — [`www.nongnu.org/tiger`](http://www.nongnu.org/tiger/)

### 现场工具包

Comprehensive listing of live bootable Linux toolkits — [`www.livecdlist.com`](http://www.livecdlist.com/)

Kali Linux — [`https://www.kali.org`](https://www.kali.org)

Knoppix — [`http://knoppix.net`](http://knoppix.net/)

Network Security Toolkit — [`http://www.networksecuritytoolkit.org/nst/index.html`](http://www.networksecuritytoolkit.org/nst/index.html)

Security Tools Distribution — [`https://s-t-d.org`](https://s-t-d.org)

### 日志分析

GFI EventsManager — [`https://www.gfi.com/products-and-solutions/network-security-solutions/gfi-eventsmanager`](https://www.gfi.com/products-and-solutions/network-security-solutions/gfi-eventsmanager)

SIEM Data Collection Log Management — [`https://software.microfocus.com/en-us/products/siem-data-collection-log-management-platform/overview`](https://software.microfocus.com/en-us/products/siem-data-collection-log-management-platform/overview)

### 通信

Brutus — [`www.hoobie.net/brutus`](http://www.hoobie.net/brutus/)

Cain & Abel — [`www.oxid.it/cain.html`](http://www.oxid.it/cain.html)

DNSstuff relay checker — [`https://www.dnsstuff.com`](https://www.dnsstuff.com)

EICAR Anti-Virus test file — [`http://www.eicar.org/86-0-Intended-use.html`](http://www.eicar.org/86-0-Intended-use.html)

theHarvester — [`https://github.com/laramies/theHarvester`](https://github.com/laramies/theHarvester)

mailsnarf — [`https://www.monkey.org/~dugsong/dsniff`](https://www.monkey.org/~dugsong/dsniff)

smtpscan — [`https://www.freshports.org/security/smtpscan`](https://www.freshports.org/security/smtpscan)

7-Zip — [`https://www.7-zip.org`](https://www.7-zip.org)

SmartDraw — [`https://www.smartdraw.com`](https://www.smartdraw.com)

3M Privacy Filters — [`https://www.3m.com/3M/en_US/privacy-screen-protectors-us`](https://www.3m.com/3M/en_US/privacy-screen-protectors-us)

WinZip — [`www.winzip.com`](http://www.winzip.com/)

### Mobile

Considerations for BitLocker in Microsoft Windows 7 — [`https://www.principlelogic.com/docs/BitLocker_in_Windows7.pdfElcomSoft`](https://www.principlelogic.com/docs/BitLocker_in_Windows7.pdfElcomSoft) Forensic Disk Decryptor — [`http://www.elcomsoft.com/efdd.html`](http://www.elcomsoft.com/efdd.html)

ElcomSoft Phone Breaker — [`http://www.elcomsoft.com/eppb.html`](http://www.elcomsoft.com/eppb.html)

ElcomSoft System Recovery — [`http://www.elcomsoft.com/esr.html`](http://www.elcomsoft.com/esr.html)

iOS Forensic Toolkit — [`http://www.elcomsoft.com/eift.html`](http://www.elcomsoft.com/eift.html)

Microsoft BitLocker Administration and Monitoring — [`https://docs.microsoft.com/en-us/microsoft-desktop-optimization-pack/index`](https://docs.microsoft.com/en-us/microsoft-desktop-optimization-pack/index)

Ophcrack — [`http://ophcrack.sourceforge.net`](http://ophcrack.sourceforge.net/)

Oxygen Forensic Suite — [`http://www.oxygen-forensic.com`](http://www.oxygen-forensic.com/)

Passware Kit Forensic — [`https://www.passware.com/kit-forensic/`](https://www.passware.com/kit-forensic/)

Veracode — [`www.veracode.com`](http://www.veracode.com)

### Networks

Arpwatch — [`http://linux.maruhn.com/sec/arpwatch.html`](http://linux.maruhn.com/sec/arpwatch.html)

Blast v2.0 — [`http://www.mcafee.com/us/downloads/free-tools/blast.aspx`](http://www.mcafee.com/us/downloads/free-tools/blast.aspx)

Cain & Abel — [`www.oxid.it/cain.html`](http://www.oxid.it/cain.html)

CommView — [`http://www.tamos.com/products/commview`](http://www.tamos.com/products/commview)

dsniff — [`http://www.monkey.org/~dugsong/dsniff`](http://www.monkey.org/~dugsong/dsniff)

Essential NetTools — [`http://www.tamos.com/products/nettools`](http://www.tamos.com/products/nettools)

Fortinet — [`http://www.fortinet.com`](http://www.fortinet.com/)

Getif — [`www.wtcs.org/snmp4tpc/getif.htm`](http://www.wtcs.org/snmp4tpc/getif.htm)

GFI LanGuard — [`https://www.gfi.com/products-and-solutions/network-security-solutions/gfi-languard3`](https://www.gfi.com/products-and-solutions/network-security-solutions/gfi-languard3)

IKECrack — [`http://ikecrack.sourceforge.net`](http://ikecrack.sourceforge.net/)

MAC address vendor lookup — [`https://regauth.standards.ieee.org/standards-ra-web/pub/view.html#registries`](https://regauth.standards.ieee.org/standards-ra-web/pub/view.html#registries)

Nessus vulnerability scanner — [`https://www.tenable.com/products/nessus/nessus-professional`](https://www.tenable.com/products/nessus/nessus-professional)

Netcat — [`http://netcat.sourceforge.net`](http://netcat.sourceforge.net/)

netfilter/iptables — [`https://www.netfilter.org`](https://www.netfilter.org)

NetResident — [`https://www.tamos.com/products/netresident`](https://www.tamos.com/products/netresident)

NetScanTools Pro — [`https://www.netscantools.com`](https://www.netscantools.com)

Nping — [`https://nmap.org/nping`](https://nmap.org/nping)

Nexpose — [`https://www.rapid7.com/products/nexpose/`](https://www.rapid7.com/products/nexpose/)

Nmap port scanner — [`https://nmap.org`](https://nmap.org)

NMapWin — [`https://sourceforge.net/projects/nmapwin`](https://sourceforge.net/projects/nmapwin)

Omnipeek — [`https://www.savvius.com/product/omnipeek`](https://www.savvius.com/product/omnipeek)

Port-number lookup — [`www.cotse.com/cgi-bin/port.cgi`](http://www.cotse.com/cgi-bin/port.cgi)

PortSentry — [`https://sourceforge.net/projects/sentrytools`](https://sourceforge.net/projects/sentrytools)

PromiscDetect — [`http://ntsecurity.nu/toolbox/promiscdetect`](http://ntsecurity.nu/toolbox/promiscdetect/)

QualysGuard vulnerability scanner — [`https://www.qualys.com`](https://www.qualys.com)

SoftPerfect Network Scanner — [`https://www.softperfect.com/products/networkscanner`](https://www.softperfect.com/products/networkscanner)

SMAC MAC address changer — [`www.klcconsulting.net/smac`](http://www.klcconsulting.net/smac/)

Snare — [`https://www.snaresolutions.com/products/snare-agents`](https://www.snaresolutions.com/products/snare-agents)

sniffdet — [`http://sniffdet.sourceforge.net`](http://sniffdet.sourceforge.net/)

SonicWALL — [`https://www.sonicwall.com/en-us/home`](https://www.sonicwall.com/en-us/home)

Synful Knock Scanner — [`https://www.talosintelligence.com/scanner`](https://www.talosintelligence.com/scanner)

TamoSoft Essential NetTools — [`https://www.tamos.com/products/nettools/?route=information/freeproduct&information_id=13`](https://www.tamos.com/products/nettools/?route=information/freeproduct&information_id=13)

Traffic IQ Professional — [`www.idappcom.com`](http://www.idappcom.com)

UDPFlood — [`https://www.mcafee.com/us/downloads/free-tools/udpflood.aspx`](https://www.mcafee.com/us/downloads/free-tools/udpflood.aspx)

WhatIsMyIP — [`https://www.whatismyip.com`](https://www.whatismyip.com)

Wireshark — [`https://www.wireshark.org`](https://www.wireshark.org)

### Password Cracking

Advanced Archive Password Recovery — [`https://www.elcomsoft.com/archpr.html`](https://www.elcomsoft.com/archpr.html)

BIOS passwords — [`http://labmice.techtarget.com/articles/BIOS_hack.htm`](http://labmice.techtarget.com/articles/BIOS_hack.htm)

Considerations for BitLocker in Microsoft Windows 7 — [`https://www.principlelogic.com/docs/BitLocker_in_Windows7.pdfBrutus`](https://www.principlelogic.com/docs/BitLocker_in_Windows7.pdfBrutus) — [`www.hoobie.net/brutus`](http://www.hoobie.net/brutus/)

Cain & Abel — [`www.oxid.it/cain.html`](http://www.oxid.it/cain.html)

Crack — `ftp://coast.cs.purdue.edu/pub/tools/unix/pwdutils/crack`

Default vendor passwords — [`https://www.cirt.net/passwords`](https://www.cirt.net/passwords)

Dictionary files and word lists

* `ftp://ftp.cerias.purdue.edu/pub/dict`

* [`https://packetstormsecurity.org/Crackers/wordlists` ](https://packetstormsecurity.org/Crackers/wordlists/)

* [`www.outpost9.com/files/WordLists.html` ](http://www.outpost9.com/files/WordLists.html)

ElcomSoft Distributed Password Recovery — [`https://www.elcomsoft.com/edpr.html`](https://www.elcomsoft.com/edpr.html)

ElcomSoft Forensic Disk Decryptor — [`https://www.elcomsoft.com/efdd.html`](https://www.elcomsoft.com/efdd.html)

ElcomSoft System Recovery — [`https://www.elcomsoft.com/esr.html`](https://www.elcomsoft.com/esr.html)

John the Ripper — [`www.openwall.com/john`](http://www.openwall.com/john/)

KeyGhost — [`www.keyghost.com`](http://www.keyghost.com/)

LastPass — [`https://lastpass.com`](https://lastpass.com/)

NetBIOS Auditing Tool — [`https://www.securityfocus.com/tools/543`](https://www.securityfocus.com/tools/543)

NIST Guide to Enterprise Password Management — [`https://csrc.nist.gov/publications/drafts/800-118/draft-sp800-118.pdf`](https://csrc.nist.gov/publications/drafts/800-118/draft-sp800-118.pdf)

NTAccess — [`www.mirider.com/ntaccess.html`](http://www.mirider.com/ntaccess.html)

ophcrack — [`http://ophcrack.sourceforge.net`](http://ophcrack.sourceforge.net/)

Pandora — [`http://www.nmrc.org/project/pandora`](http://www.nmrc.org/project/pandora)

Passware Kit Forensic — [`https://www.passware.com/kit-forensic`](https://www.passware.com/kit-forensic)

Password Safe — [`https://pwsafe.org`](https://pwsafe.org)

Proactive Password Auditor — [`https://www.elcomsoft.com/ppa.htm`](https://www.elcomsoft.com/ppa.htm)l

Proactive System Password Recovery — [`https://www.elcomsoft.com/pspr.html`](https://www.elcomsoft.com/pspr.html)

进入`/path/to/xxx`目录，找到`xxx.json`。

在表达式`cvar = avar + bvar`中，加法运算符（`+`）将`avar`与`bvar`相加，得到它们的和`cvar`

在`List.of(arg0, arg1, arg2)`中，`List`接口的工厂方法`of()`接受一系列的元素，返回包含这些元素的列表。

Brutus — [`www.hoobie.net/brutus/index.html`](http://www.hoobie.net/brutus/index.html)

Burp Proxy — [`https://portswigger.net/burp`](https://portswigger.net/burp)

Firefox Web Developer — [`http://chrispederick.com/work/web-developer`](http://chrispederick.com/work/web-developer)

Fortify WebInspect — [`https://software.microfocus.com/en-us/products/webinspect-dynamic-analysis-dast/overview`](https://software.microfocus.com/en-us/products/webinspect-dynamic-analysis-dast/overview)

Foundstone’s SASS Hacme Tools — [`https://www.mcafee.com/us/downloads/free-tools/index.aspx`](https://www.mcafee.com/us/downloads/free-tools/index.aspx)

Google Hack Honeypot — [`http://ghh.sourceforge.net`](http://ghh.sourceforge.net)

Google Hacking Database — [`https://www.exploit-db.com/google-hacking-database`](https://www.exploit-db.com/google-hacking-database)

HTTrack Website Copier — [`www.httrack.com`](http://www.httrack.com)

McAfee Host Intrusion Prevention for Server — [`https://www.mcafee.com/us/products/host-ips-for-server.aspx`](https://www.mcafee.com/us/products/host-ips-for-server.aspx)

Netsparker — [`https://www.netsparker.com`](https://www.netsparker.com/)

OWASP Zed Attack Proxy Project — [`https://www.owasp.org/index.php/OWASP_Zed_Attack_Proxy_Project`](https://www.owasp.org/index.php/OWASP_Zed_Attack_Proxy_Project)

Paros Proxy — [`https://sourceforge.net/projects/paros`](https://sourceforge.net/projects/paros)

Port 80 Software’s ServerMask — [`https://www.port80software.com/products/servermask`](https://www.port80software.com/products/servermask)

Qualys SSL Labs — [`https://www.sslabs.com`](https://www.sslabs.com)

SiteDigger — [`https://www.mcafee.com/us/downloads/free-tools/sitedigger.aspx`](https://www.mcafee.com/us/downloads/free-tools/sitedigger.aspx)

SQL Inject Me — [`https://addons.mozilla.org/en-us/firefox/addon/sql-inject-me`](https://addons.mozilla.org/en-us/firefox/addon/sql-inject-me)

SQL Power Injector — [`www.sqlpowerinjector.com`](http://www.sqlpowerinjector.com)

THC-Hydra — [`https://tools.kali.org/password-attacks/hydra`](https://tools.kali.org/password-attacks/hydra)

WebGoat — [`https://www.owasp.org/index.php/Category:OWASP_WebGoat_Project`](https://www.owasp.org/index.php/Category:OWASP_WebGoat_Project)

WSDigger — [`https://www.mcafee.com/us/downloads/free-tools/wsdigger.aspx`](https://www.mcafee.com/us/downloads/free-tools/wsdigger.aspx)

WSFuzzer — [`https://www.owasp.org/index.php/Category:OWASP_WSFuzzer_Project`](https://www.owasp.org/index.php/Category:OWASP_WSFuzzer_Project)

## Windows

Considerations for BitLocker in Microsoft Windows 7 — [`https://www.principlelogic.com/docs/BitLocker_in_Windows7.pdf`](https://www.principlelogic.com/docs/BitLocker_in_Windows7.pdf)

DumpSec — [`https://www.systemtools.com/somarsoft/?somarsoft.com`](https://www.systemtools.com/somarsoft/?somarsoft.com)

GFI LanGuard — [`https://www.gfi.com/products-and-solutions/network-security-solutions/gfi-languard3`](https://www.gfi.com/products-and-solutions/network-security-solutions/gfi-languard3)

Microsoft Baseline Security Analyzer — [`https://www.microsoft.com/en-us/download/details.aspx?id=7558`](https://www.microsoft.com/en-us/download/details.aspx?id=7558)

Network Users — [`www.optimumx.com/download/netusers.zip`](http://www.optimumx.com/download/netusers.zip)

Nexpose — [`https://www.rapid7.com/products/nexpose`](https://www.rapid7.com/products/nexpose)

QualysGuard — [`https://www.qualys.com`](https://www.qualys.com)

SoftPerfect Network Scanner — [`https://www.softperfect.com/products/networkscanner`](https://www.softperfect.com/products/networkscanner)

Sysinternals — [`https://docs.microsoft.com/en-us/sysinternals`](https://docs.microsoft.com/en-us/sysinternals)

Winfo — [`www.ntsecurity.nu/toolbox/winfo`](http://www.ntsecurity.nu/toolbox/winfo)

## Wireless Networks

Aircrack-ng — [`http://aircrack-ng.org`](http://aircrack-ng.org)

Asleap — [`https://sourceforge.net/projects/asleap`](https://sourceforge.net/projects/asleap)

CommView for WiFi — [`https://www.tamos.com/products/commwifi`](https://www.tamos.com/products/commwifi)

Digital Hotspotter — [`www.canarywireless.com`](http://www.canarywireless.com)

ElcomSoft Wireless Security Auditor — [`https://www.elcomsoft.com/ewsa.html`](https://www.elcomsoft.com/ewsa.html)

Homebrew WiFi antenna — [`www.turnpoint.net/wireless/has.html`](http://www.turnpoint.net/wireless/has.html)

Kismet — [`https://www.kismetwireless.net`](https://www.kismetwireless.net)

NetStumbler — [`www.netstumbler.com`](http://www.netstumbler.com)

OmniPeek — [`https://www.savvius.com/product/omnipeek`](https://www.savvius.com/product/omnipeek)

Reaver — [`https://code.google.com/p/reaver-wps`](https://code.google.com/p/reaver-wps)

Wellenreiter — [`https://sourceforge.net/projects/wellenreiter`](https://sourceforge.net/projects/wellenreiter)

WEPCrack — [`http://wepcrack.sourceforge.net`](http://wepcrack.sourceforge.net)

WiFinder — [`www.boingo.com/retail/#s3781`](http://www.boingo.com/retail/#s3781)

WiFi Pineapple — [`https://www.wifipineapple.com`](https://www.wifipineapple.com)

WiGLE database of wireless networks — [`https://wigle.net`](https://wigle.net)

WinAirsnort — [`http://winairsnort.free.fr`](http://winairsnort.free.fr)

## About the Author

`Kevin Beaver` is an independent information security consultant, expert witness, professional speaker, and writer with Atlanta-based Principle Logic, LLC. He has over three decades of experience in IT and has spent a quarter of a century working in security. `Kevin` specializes in performing independent information security assessments for corporations, security product vendors, software developers/cloud service providers, government agencies, nonprofit organizations, among others. Before starting his information security consulting practice in 2001, `Kevin` served in various information technology (IT) and security roles for several healthcare, e-commerce, financial, and educational institutions.

`Kevin` has appeared on CNN television as an information security expert and has been quoted in The Wall Street Journal, Entrepreneur, Fortune Small Business, Women's Health, and on Inc. magazine’s technology site, IncTechnology.com. `Kevin`’s work has also been referenced by the PCI Council in their Data Security Standard Wireless Guidelines. `Kevin` has been a top-rated speaker, giving hundreds of presentations and panel discussions for IT and security seminars, conferences, and webcasts over the past decade and a half.

`Kevin` has authored or co-authored 12 information security books, including *Hacking Wireless Networks For Dummies*, *Implementation Strategies for Fulfilling and Maintaining IT Compliance* (Realtimepublishers.com), and *The Practical Guide to HIPAA Privacy and Security Compliance* (Auerbach). `Kevin` has written more than three dozen whitepapers and over 1,000 articles and guest blog posts for sites such as TechTarget’s SearchSecurity.com, SearchEnterpriseDesktop.com, and SearchSoftwareQuality.com, Ziff Davis’ Toolbox.com, as well as IBM’s SecurityIntelligence.com. `Kevin` is the creator and producer of the Security On Wheels audiobooks, which provide security learning for IT professionals on the go ([`securityonwheels.com`](http://www.securityonwheels.com)), and the Security On Wheels blog ([`securityonwheels.com/blog`](http://www.securityonwheels.com/blog)). He also covers information security and related matters on Twitter ([`@kevinbeaver`](https://twitter.com/kevinbeaver)) and YouTube (`PrincipleLogic`). `Kevin` earned his bachelor’s degree in Computer Engineering Technology from Southern College of Technology and his master’s degree in Management of Technology from Georgia Tech. He has obtained his CISSP certification in 2001 and also holds MCSE, Master CNE, and IT Project+ certifications.

Kevin 可以通过他的网站[`https://www.principlelogic.com`](http://www.principlelogic.com)联系，也可以通过 LinkedIn 在[`https://www.linkedin.com/in/kevinbeaver`](http://www.linkedin.com/in/kevinbeaver)与他连接。

## Dedication

这本是献给我的客户们。我想向每一位一直雇佣我、这位“无名品牌”顾问的客户以及多年坚持雇佣我的客户表示诚挚的感谢。如果没有你们愿意摆脱“必须雇佣大公司”的思维定势，并持续多年支持我的决心，我不会在这里。衷心感谢你们！

## Author’s Acknowledgments

如常，我要向 Amy、Garrett 和 Mary Lin 表示巨大的感谢，感谢你们每天为我的生活带来的爱、支持和幽默。我对你们的爱意百分之百！

我也想感谢 Amy Fandrei，我的收购编辑，她继续推动本项目，并给了我塑造这本书的机会，让我感到非常自豪。同时感谢我的项目编辑 Chrissy Guthrie，这段合作真的很愉快！向我的排版编辑 Kathy Simpson 致敬，感谢她帮助我把思想和文字控制在适当范围内。也要向我的技术编辑、业务同事、朋友以及《Hacking Wireless Networks For Dummies》共同作者 Peter T. Davis 致谢。正如这本书的前五个版本一样，与你合作非常棒——谢谢你让我保持正确方向！

衷心感谢 Nicky Sciberras（Acunetix）、Robert Abela（Netsparker）、Nate Crampton（Rapid7）、Vladimir Katalov 和 Olga Koksharova（ElcomSoft）、Kirk Thomas（Northwest Performance Software）、David Vest（Mythicsoft）、Michael Berg（TamoSoft）以及 Oliver Muenchow、Colin Bastable 和 Palo Stacho（LUCY Security）对我的所有请求的回应。同时感谢 Dave Coe 帮助我保持对最新安全工具和技术的了解。对其他未提及的同事，我也表示衷心的感谢！

**Publisher’s Acknowledgments**

**Acquisitions Editors:** Amy Fandrei 和 Steven Hayes

**Editorial Project Manager and Development Editor:** Christina N. Guthrie

**Copy Editor:** Kathy Simpson

**Technical Editor:** Peter T. Davis

**Production Editor:** Siddique Shaik

**Cover Image:** © matejmo/Getty Images

## Index

* * *

### A

1. access, blocking, 241

2. access control list (ACL), 238

3. AccessEnum (website), 189

4. account enumeration, 260–263

5. account lockout, 120

6. ACL (access control list), 238

7. Active Directory, 104

8. Active Server Pages (ASP), 291

9. Acunetix Web Vulnerability Scanner, 21, 22, 278, 296, 297, 371

10. adaptability, 346

11. Advanced Archive Password Recovery (Elcomsoft), 111, 365

12. Advanced Office Password Recovery (website), 306

13. advanced persistent threat (APT), 152

14. Advanced SQL Password Recovery (website), 304, 358

15. AFRINIC (Regional Internet Registry for Africa), 66, 359

16. Aircrack-ng (website), 161, 167, 373

17. airodump, 169

18. AirWatch (website), 194

19. allies, 341

20. all-in-one assessment tools, 204

21. allintitle operator, 282

22. Amenza Technologies Limited Secur/Tree, 42

23. American National Standards Institute (ANSI), 11

24. American Standard Code for Information Interchange (ASCII), 119

25. analyzers, 128

26. analyzing

  1. network data, 140–146

  2. source code, 300–301, 369

27. anonymity, maintaining, 35–36

28. ANSI (American National Standards Institute), 11

29. antenna, external, 161

30. Apache web server (httpd), 230

31. APNIC (website), 66, 359

32. AppDetectivePro (website), 307, 358

33. applications. *See* `websites and applications`

34. approval, prior, 351

35. AppSpider, 153, 290, 371

36. APs (access points), 160

37. APT (advanced persistent threat), 152

38. ARIN (Regional Internet Registry for North America, a Portion of the Caribbean, and subequatorial Africa), 66, 359

39. ARP spoofing/poisoning, 147–149

40. Arpwatch (website), 363

41. ASCII (American Standard Code for Information Interchange), 119

42. asleap (website), 171, 373

43. ASP (Active Server Pages), 291

44. assumptions, making, 46–47

45. Asterisk (website), 77

46. attachments (e-mail), 255–256

47. attack tree analysis, 42

48. attacks, 33–35. *See also specific topics*

49. auditing, compared with ethical hacking, 10–11, 348

50. authentication, 101, 121, 225–226

51. authorization, 18

52. automated assessments, 56–57

53. automated password reset, 121

54. automating patching, 325–326, 331–332

55. Awareity MOAT (website), 370

56. awareness, as countermeasure against social engineering, 80–82

### B

1. background checks, 64

2. bad guys, thinking like, 27

3. bad-guy (black hat) hackers, 9, 29

4. bandwidth blocking, 255

5. banner attacks, 258–260

6. banners, grabbing, 137–138

7. Barracuda Networks (website), 300

8. Bastille Linux Hardening Program (website), 369

9. Bastille UNIX (website), 247

10. Beaver, Kevin (author)

  1. *Hacking Wireless Networks For Dummies*, 169

11. Beaver, Kevin (security analyst), 368

12. believability, 72

13. benefits, of ethical hacking, 343–344

14. best practices, for minimizing e-mail security risks, 269–270

15. Bing (website), 62, 359

16. BIOS passwords, 116, 365

17. Bitscanner, 167

18. black hat (bad-guy) hackers, 9, 29

19. Blast (website), 154, 363

20. blind assessments, 45, 51

21. blind ethical hacking, 39

22. Blooover (website), 166, 357

23. BlueLog (website), 166

24. `BlueScanner` (`website`), `[166](`#c10.xhtml#Page_166`)`, `[357](`#a01.xhtml#Page_357`)`

25. `Bluesnarfer` (`website`), `[166](`#c10.xhtml#Page_166`)`, `[357](`#a01.xhtml#Page_357`)`

26. `BlueSniper rifle` (`website`), `[166](`#c10.xhtml#Page_166`)`, `[357](`#a01.xhtml#Page_357`)`

27. `Bluetooth`, `[166](`#c10.xhtml#Page_166`)`, `[357](`#a01.xhtml#Page_357`)`

28. `bootable (live) CDs`, `[160](`#c10.xhtml#Page_160`)–161`

29. `Bow Tie`, `[41](`#c03.xhtml#Page_41`)`

30. `bring your own device (BYOD)`, `[193](`#c11.xhtml#Page_193`)`

31. `brute-force attacks`, `for cracking passwords`, `[105](`#c08.xhtml#Page_105`)–107`

32. `Brutus`, `[102](`#c08.xhtml#Page_102`)`, `[104](`#c08.xhtml#Page_104`)`, `[268](`#c14.xhtml#Page_268`)`, `[294](`#c15.xhtml#Page_294`)`, `[362](`#a01.xhtml#Page_362`)`, `[371](`#a01.xhtml#Page_371`)`

33. `BTScanner for XP` (`website`), `[357](`#a01.xhtml#Page_357`)`

34. `buffer-overflow attacks`, `[244](`#c13.xhtml#Page_244`)–245`, `[284](`#c15.xhtml#Page_284`)`

35. `built-in Windows programs`, `[203](`#c12.xhtml#Page_203`)`

36. `Burp Proxy`, `[284](`#c15.xhtml#Page_284`)`, `[286](`#c15.xhtml#Page_286`)`, `[371](`#a01.xhtml#Page_371`)`

37. `business phones`, `[77](`#c06.xhtml#Page_77`)`

38. `BYOD (bring your own device)`, `[193](`#c11.xhtml#Page_193`)`

### C

1. `Cain & Abel`

  1. `about`, `[22](`#c01.xhtml#Page_22`)`

  2. `for capturing and recording voice traffic`, `[273](`#c14.xhtml#Page_273`)–275`

  3. `using for ARP poisoning`, `[148](`#c09.xhtml#Page_148`)–149`

  4. `website`, `[101](`#c08.xhtml#Page_101`)`, `[102](`#c08.xhtml#Page_102`)`, `[114](`#c08.xhtml#Page_114`)`, `[128](`#c09.xhtml#Page_128`)`, `[141](`#c09.xhtml#Page_141`)`, `[267](`#c14.xhtml#Page_267`)`, `[304](`#c16.xhtml#Page_304`)`, `[362](`#a01.xhtml#Page_362`)`, `[364](`#a01.xhtml#Page_364`)`, `[365](`#a01.xhtml#Page_365`)`, `[370](`#a01.xhtml#Page_370`)`

2. `Camtasia Studio` (`TechSmith`), `[45](`#c03.xhtml#Page_45`)`

3. `Canadian Personal Information Protection and Electronic Documents Act (PIPEDA)`, `[12](`#c01.xhtml#Page_12`)`

4. `Canary Wireless Digital Hotspotter` (`website`), `[161](`#c10.xhtml#Page_161`)`

5. `candy-security adage`, `[68](`#c06.xhtml#Page_68`)`

6. `cantenna`, `[162](`#c10.xhtml#Page_162`)`

7. `CAPTCHA (Completely Automated Public Turing test to tell Computers and Humans Apart)`, `[257](`#c14.xhtml#Page_257`)–258`, `[297](`#c15.xhtml#Page_297`)`

8. `capturing traffic`, `[267](`#c14.xhtml#Page_267`)`, `[273](`#c14.xhtml#Page_273`)–275`

9. `Car Whisperer` (`website`), `[167](`#c10.xhtml#Page_167`)`, `[357](`#a01.xhtml#Page_357`)`

10. `Carbon Black` (`website`), `[357](`#a01.xhtml#Page_357`)`

11. `Cash, Adam (author)`

  1. `*Psychology For Dummies*`, `[73](`#c06.xhtml#Page_73`)`

12. `Cb Protection` (`website`), `[113](`#c08.xhtml#Page_113`)`, `[152](`#c09.xhtml#Page_152`)`

13. `C|EH (Certified Ethical Hacker)`, `[11](`#c01.xhtml#Page_11`)`

14. `Center for Internet Security Benchmarks (website)`, `[121](`#c08.xhtml#Page_121`)–1229`, `[369](`#a01.xhtml#Page_369`)`

15. `certifications`, `[11](`#c01.xhtml#Page_11`)`, `[358](`#a01.xhtml#Page_358`)`

16. `Certified Ethical Hacker (C|EH)`, `[11](`#c01.xhtml#Page_11`)`

17. `Certified Information Security Manager (website)`, `[358](`#a01.xhtml#Page_358`)`

18. `Certified Information Systems Security Professional (website)`, `[358](`#a01.xhtml#Page_358`)`

19. `Certified Systems Security Professional (CISSP)`, `[11](`#c01.xhtml#Page_11`)`

20. `Certified Wireless Security Professional (website)`, `[358](`#a01.xhtml#Page_358`)`

21. `Cheat Sheet (website)`, `[3](`#c00.xhtml#Page_3`)`

22. `CheckShortURL (website)`, `[368](`#a01.xhtml#Page_368`)`

23. `CheckSum Tool (website)`, `[47](`#c03.xhtml#Page_47`)`

24. `Cheops-ng (website)`, `[328](`#c18.xhtml#Page_328`)`

25. `chkconfig`, `[238](`#c13.xhtml#Page_238`)`

26. `*A Chronology of Data Breaches* (Privacy Rights Clearinghouse)`, `[342](`#c20.xhtml#Page_342`)`

27. `CIP (Critical Infrastructure Protection)`, `[12](`#c01.xhtml#Page_12`)`

28. `Cisco (website)`, `[308](`#c16.xhtml#Page_308`)`

29. `Cisco LEAP protocol`, `[171](`#c10.xhtml#Page_171`)`

30. `CISSP (Certified Systems Security Professional)`, `[11](`#c01.xhtml#Page_11`)`

31. `civil liberties`, `[33](`#c02.xhtml#Page_33`)`

32. `clients`, `[348](`#c21.xhtml#Page_348`)–349`

33. `cloud service providers`, `[333](`#c19.xhtml#Page_333`)–334`

34. `CloudFlare (website)`, `[155](`#c09.xhtml#Page_155`)`, `[300](`#c15.xhtml#Page_300`)`, `[359](`#a01.xhtml#Page_359`)`

35. `Cobb, Chey (author)`

  1. `*Network Security For Dummies*`, `[122](`#c08.xhtml#Page_122`)`

36. `code injection`, `[287](`#c15.xhtml#Page_287`)–289`

37. `Cofense (website)`, `[78](`#c06.xhtml#Page_78`)`

38. `commands, disabling`, `[240](`#c13.xhtml#Page_240`)`

39. `Common Vulnerabilities and Exposures (website)`, `[56](`#c04.xhtml#Page_56`)`, `[318](`#c17.xhtml#Page_318`)`, `[371](`#a01.xhtml#Page_371`)`

40. `communication and messaging systems`

  1. `about`, `[253](`#c14.xhtml#Page_253`)`

  2. `e-mail attacks`, `[254](`#c14.xhtml#Page_254`)–270`

  3. `messaging system vulnerabilities`, `[253](`#c14.xhtml#Page_253`)–254`

  4. `tools and resources`, `[362](`#a01.xhtml#Page_362`)`

  5. `Voice over IP (VoIP)`, `[270](`#c14.xhtml#Page_270`)–275`, `[370](`#a01.xhtml#Page_370`)–371`

41. `CommView (TamoSoft)`, `[115](`#c08.xhtml#Page_115`)`, `[141](`#c09.xhtml#Page_141`)`, `[364](`#a01.xhtml#Page_364`)`, `[370](`#a01.xhtml#Page_370`)`, `[373](`#a01.xhtml#Page_373`)`

42. `CommView for WiFi (TamoSoft)`, `[22](`#c01.xhtml#Page_22`)`

43. `Completely Automated Public Turing test to tell Computers and Humans Apart (CAPTCHA)`, `[257](`#c14.xhtml#Page_257`)–258`, `[297](`#c15.xhtml#Page_297`)`

44. `compliance`, `[12](`#c01.xhtml#Page_12`)`, `[348](`#c21.xhtml#Page_348`)`

45. `CompTIA Security (website)`, `[358](`#a01.xhtml#Page_358`)`

46. `Computer Fraud and Abuse Act (website)`, `[361](`#a01.xhtml#Page_361`)`

47. `computers, physical security vulnerabilities`, `[90](`#c07.xhtml#Page_90`)–93`

48. `configuration, of null sessions`, `[213](`#c12.xhtml#Page_213`)–214`

49. `Connect scan`, `[133](`#c09.xhtml#Page_133`)`

50. `connection attacks`, `[256](`#c14.xhtml#Page_256`)–258`

51. `COPS (website)`, `[244](`#c13.xhtml#Page_244`)`

52. `copyrighted materials`, `[33](`#c02.xhtml#Page_33`)`

53. `Core Network Insight (website)`, `[357](`#a01.xhtml#Page_357`)`

54. `cost, of being hacked`, `[342](`#c20.xhtml#Page_342`)–343`

55. `countermeasures`

  1. `account enumeration`, `[262](`#c14.xhtml#Page_262`)–263`

  2. `ARP poisoning`, `[151](`#c09.xhtml#Page_151`)`

  3. `attacks on unneeded services`, `[236](`#c13.xhtml#Page_236`)–238`

  4. `banner attacks`, `[260](`#c14.xhtml#Page_260`)`

  5. `banner-grabbing attacks`, `[137](`#c09.xhtml#Page_137`)–138`

  6. `buffer-overflow attacks`, `[245](`#c13.xhtml#Page_245`)`

  7. `connection attacks`, `[256](`#c14.xhtml#Page_256`)–258`

  8. `default configuration settings vulnerabilities`, `[186](`#c10.xhtml#Page_186`)`

  9. `default script attacks`, `[293](`#c15.xhtml#Page_293`)`

  10. `directory traversals`, `[283](`#c15.xhtml#Page_283`)`

  11. `DoS attacks`, `[154](`#c09.xhtml#Page_154`)–155`

  12. `e-mail attachment attacks`, `[255](`#c14.xhtml#Page_255`)–256`

  13. `encrypted traffic attacks`, `[170](`#c10.xhtml#Page_170`)–172`

  14. `file permission hacks`, `[243](`#c13.xhtml#Page_243`)–244`

  15. `firewall rulebase vulnerabilities`, `[140](`#c09.xhtml#Page_140`)`

  16. `general password-cracking`, `[117](`#c08.xhtml#Page_117`)–121`

  17. `header disclosures`, `[267](`#c14.xhtml#Page_267`)`

  18. `input attacks`, `[290](`#c15.xhtml#Page_290`)–291`

  19. `MAC address spoofing attacks`, `[151](`#c09.xhtml#Page_151`)`

  20. `MAC spoofing`, `[183](`#c10.xhtml#Page_183`)`

  21. `missing patch vulnerability exploits`, `[224](`#c12.xhtml#Page_224`)–225`

  22. `NetBIOS attacks`, `[210](`#c12.xhtml#Page_210`)`

  23. `network protocol vulnerabilities`, `[146](`#c09.xhtml#Page_146`)`

  24. `NFS attacks`, `[242](`#c13.xhtml#Page_242`)`

  25. `null session hacks`, `[214](`#c12.xhtml#Page_214`)–215`

  26. `password reset programs`, `[193](`#c11.xhtml#Page_193`)`

  27. `physical security attacks`, `[245](`#c13.xhtml#Page_245`)–246`

  28. `ping sweeping`, `[135](`#c09.xhtml#Page_135`)`

  29. `port scanning`, `[135](`#c09.xhtml#Page_135`)`

  30. `.rhosts and hosts.equiv file attacks`, `[240](`#c13.xhtml#Page_240`)–241`

  31. `rogue wireless devices`, `[179](`#c10.xhtml#Page_179`)`

32. `SMTP 中继攻击`, 266

33. `SNMP 攻击`, 136–137

34. `社会工程学`, 80–82

35. `系统扫描`, 205–207, 233–234

36. `不安全的登录系统`, 297

37. `VoIP 漏洞`, 275

38. `易受攻击的无线工作站`, 185

39. `无线网络攻击`, 183–184, 185

40. `WPS PIN 漏洞`, 174–175

56. `CPT (IACRB 认证渗透测试员)`, 11

57. `网站被破解`, 366

58. `黑客`, `定义`, 8

59. `破解密码`

  1. `关于`, 98–99

  2. `在数据库上`, 305–306

  3. `使用高科技工具`, 102–110

  4. `键盘记录`, 112–113

  5. `在笔记本电脑上`, 188–193

  6. `网络分析仪`, 114–115

  7. `传统方式`, 99–101

  8. `受密码保护的文件`, 110–112

  9. `手机和平板电脑`, 193–198

  10. `统计`, 110

  11. `弱 BIOS 密码`, 116

  12. `弱密码存储`, 113–114

  13. `弱密码停滞`, 116–117

60. `系统崩溃`, 17–18

61. `爬虫`, 280–281

62. `可信度，建立`, 345

63. `罪犯黑客`, 29

64. `关键基础设施保护 (CIP)`, 12

65. `跨站脚本 (XSS)`, 289–290

66. `CWE/SANS 顶级 25 危险编程错误 (网站)`, 371

67. `Cylance (网站)`, 152

1. `守护进程`, 229. *参见* `Linux`

2. `数据泄漏防护 (DLP) 系统`, 332

3. `数据库`

  1. `关于`, 303

  2. `选择安全测试工具`, 304

  3. `破解密码`, 305–306

  4. `在网络中查找`, 304–305

  5. `降低安全风险`, 307–308

  6. `工具和资源`, 358

  7. `漏洞`, 306–307

4. `Davis, Peter T. (作者)`

  1. *`Hacking Wireless Networks For Dummies`*, 169

  2. *`Wireless Networks For Dummies`*, 184

5. `DDoS (分布式 DoS) 攻击`, 152–153

6. `Debian Linux 安全警报 (网站)`, 367

7. `Debian 包管理系统 (dpkg)`, 248

8. `欺骗`

  1. `通过技术`, 73–74

  2. `通过语言和行为`, 72–73

9. `Deep Freeze Enterprise (网站)`, 113, 369

10. `默认配置设置`, `与漏洞相关`, 186

11. `默认脚本攻击`, 291–293

12. `默认共享权限 (Windows)`, 215–216

13. `默认供应商密码 (网站)`, 366

14. `交付物`, 39

15. `Dell KACE 系统管理设备 (网站)`, 249

16. `去军事化区 (DMZ) 分段`, 309

17. `拒绝服务 (DoS) 攻击`, 15, 127, 152–155, 359

18. `DHA (目录收集攻击)`, 260

19. `字典攻击`, `用于破解密码`, 105

20. `Digital Hotspotter (Canary Wireless)`, 161, 373

21. `数字版权法 (DMCA)`, 12, 361

22. `方向性无线天线`, 161

23. `目录收集攻击 (DHA)`, 260

24. `目录穿越`, 279–282

25. `禁用`

  1. `命令`, 240

  2. `文件和打印共享 for Microsoft Networks`, 214

  3. `NetBIOS`, 210, 214

  4. `不需要的服务`, 236–238

26. `分布式 DoS (DDoS) 攻击`, 152–153

27. `分布式密码恢复 (Elcomsoft)`, 102, 306, 358, 366

28. `分发更新`, 248–249

29. `DLP (数据泄漏防护) 系统`, 332

30. `DMCA (数字版权法)`, 12, 361

31. `DMZ (去军事化区) 分段`, 309

32. `DNS 工具 (网站)`, 359

33. `DNSstuff 中继检查器`, 362

34. `DNSstuff.com (网站)`, 359

35. `美元符号 ($)`, 210

36. `DoS (拒绝服务) 攻击`, 15, 127, 152–155, 359

37. `DOSarrest (网站)`, 155, 359

38. `dpkg (Debian 包管理系统)`, 248

39. `Draper, John (黑客)`, 28

40. `屋顶瓦片`, 86

41. `dsniff (网站)`, 147, 267, 364

42. `DumpSec (网站)`, 120, 213, 373

43. `桶子潜水`, 14, 76–77

E

1. `EC-Council (网站)`, 11

2. `Ecora Patch Manager (网站)`, 326, 367

3. `Effective File Search (网站)`, 369

4. `伦理黑客的有效性`, 347–350

5. `EICAR`, 268

6. `EICAR 防病毒 (网站)`, 362

7. `Elcomsoft`

  1. `高级压缩包密码恢复`, 111

  2. `分布式密码恢复`, 102, 306, 358, 366

  3. `取证磁盘解密`, 192, 366

  4. `iOS 取证工具包`, 194–197

  5. `手机破解`, 197, 363

  6. `主动密码审计`, 103

  7. `主动系统密码恢复`, 101, 103

  8. `系统恢复`, 22, 102, 188, 363, 366

  9. `网站`, 188

  10. `无线安全审计 (EWSA)`, 161, 169, 373

8. `电子邮件攻击`

  1. `关于`, 254

  2. `横幅`, 258–260

  3. `降低安全风险的最佳实践`, 269–270

  4. `电子邮件炸弹`, 255–258

9. `电子邮件炸弹`, 255–258

10. `电子邮件防火墙`, 258

11. `电子邮件头披露`, 266–267

12. `电子邮件、网络钓鱼`, 68, 77–79

13. `员工`, 68, 73

14. `启用系统日志记录`, 333

15. `加密`, 167–170, 269

16. `列举工具`, 55

17. `错误和遗漏保险`, 40

18. `必要 NetTools (TamoSoft)`, 128, 135, 364

19. `以太网连接，拔除`, 27

20. `伦理黑客`, `定义`, 8

21. `伦理黑客。*另见特定主题*`

  1. `关于`, 1

  2. `自动化补丁`, 331–332

  3. `与恶意黑客相比`, 10–12

  4. `外包`, 334–335

  5. `过程`, 18–24

  6. `原因`, 12–13

  7. `规则`, 16–18

  8. `安全风险`, 14–16

  9. `术语`, 7–9

22. `ettercap (网站)`, 141

23. `评估伦理黑客的结果`, 23

24. `“恶意双胞胎”`, 27

25. `执行伦理黑客计划`, 22–23

26. `利用`

  1. `可能性和影响`, 319–320

  2. `缺失补丁`, 217–225

  3. `社交工程攻击中的关系`, 72–74

  4. `工具和资源`, 359

27. `EXPN` 命令, 261–263

28. `外部黑客`, 8

### F

1. `Facebook (网站)`, 62

2. `失败登录计数器`, 120–121

3. `Failure Modes and Effects Analysis (FMEA)`, 41

4. `伪造员工`, 68

5. `伪造支持人员`, 68

6. `伪造供应商`, 68

7. `恐惧、不确定性和疑虑 (FUD)`, 342

8. `光纤通道`, 308

9. `文件和打印共享 (Microsoft Networks)`, 214

10. `文件权限，在 Linux 中检查`, 242–244

11. `FileLocator Pro`, 310, 311, 369

12. `FileLocator Pro (网站)`, 113

13. `The File Extension Source (网站)`, 359

14. `FileVault`, 93

15. `FIN Stealth scan`, 133

16. `Finnigan, Pete (安全专家)`, 305

17. `Firefox Add-ons`, 289

18. `Firefox Web Developer (网站)`, 284, 371

19. `Fireking safes (网站)`, 92

20. `Firemon Risk Analyzer (网站)`, 139

21. `防火墙`

  1. `电子邮件`, 258

  2. `iptables`, 233

  3. `防止 NetBIOS 攻击`, 210

  4. `部署`, 300

  5. `测试规则`, 138–140

  6. `使用`, 156–157

22. `固件补丁`, 186

23. `先进先出缓冲区`, 143

24. `灵活性`, 346

25. `FMEA (Failure Modes and Effects Analysis)`, 41

26. `侦察`

  1. `关于`, 51

  2. `收集公开信息`, 51–52, 61–64

  3. `映射网络`, 64–66

27. `Forensic Disk Decryptor (Elcomsoft)`, 192

28. `制定伦理黑客计划`, 18–20

29. `Fortinet (网站)`, 300, 308, 313, 364

30. `Fortres 101 (网站)`, 113, 369

31. `Foundstone's SASS Hacme Tools (网站)`, 299, 372

32. `fping (网站)`, 53

33. `FTP (ftpd)`, 230, 235

34. `FUD (fear, uncertainty, and doubt)`, 342

35. `全盘加密`, 192

### G

1. `收集公开信息`, 51–52, 61–64

2. `GDPR (Global Data Protection Regulation) (网站)`, 361

3. `通用研究工具`, 359–360

4. `通用安全扫描`, 297

5. `GET` 请求, 292

6. `Getif`, 128, 135–136, 364

7. `GFI EventsManager (网站)`, 333, 362

8. `GFI LanGuard`, 57, 204, 206, 225–226, 249, 326, 361, 364, 367, 373

9. `GHDB (Google Hacking Database)`, 282, 372

10. `GIAC (SANS Global Information Assurance Certification)`, 11

11. `Glassdoor (网站)`, 62

12. `GLBA (Gramm-Leach-Bliley Act)`, 12, 361

13. `Global Data Protection Regulation (GDPR) (网站)`, 361

14. `GNU MAC Changer (网站)`, 150, 182

15. `目标，建立`, 37–40

16. `好人 (白帽) 黑客`, 9, 29

17. `Google`, 62, 281–282, 359

18. `Google Groups`, 282

19. `Google Hack Honeypot (网站)`, 283, 372

20. `Google Hacking Database (GHDB)`, 282, 372

21. `*Google Hacking for Penetration Testers* (Long)`, 282

22. `管理`, 348

23. `政府资源`, 64, 359

24. `抓取横幅`, 137–138

25. `Gramm-Leach-Bliley Act (GLBA)`, 12, 361

26. `gray hat 黑客`, 9, 29

27. `Greenidea, Inc. (网站)`, 337

28. `Greenidea Visible Statement (网站)`, 370

29. `保证`, 352

### H

1. `黑客。*另见特定主题*`

  1. `关于`, 8–9

  2. `攻击方式`, 33–35

  3. `定义`, 8

  4. `为雇佣`, 30

  5. `维护匿名性`, 35–36

  6. `公众对黑客的看法`, 25–28

  7. `原因`, 30–33

  8. `思维像坏人`, 27

  9. `谁是?`, 28–30

2. `Hackin9 (网站)`, 35, 360

3. `黑客。*见* 伦理黑客`

4. `*Hacking Wireless Networks For Dummies* (Beaver and Davis)`, 169

5. `默认。*另见特定主题*`

  1. `文件权限`, 243

  2. `NFS (Network File System)`, 241–242

  3. `物理安全`, 245

  4. `使用 hosts.equiv 文件`, 239

  5. `使用 .rhosts 文件`, 239–240

6. `hacktivists`, 30

7. `“hard, crunchy outside; soft, chewy inside,”`, 68

8. `hardening systems`, 326–327

9. `hashes`, 103–104, 306

10. `Health Information Technology for Economic and Clinical Health (HITECH) Act`, 12

11. `Health Insurance Portability and Accountability Act (HIPAA)`, 10, 12, 361

12. `Herold, Rebecca (author)`

  1. `*Managing an Information Security and Privacy Awareness and Training Program*`, 370

13. `hidden field manipulation`, 286–287

14. `hidden shares`, 210

15. `high-tech tools, cracking password with`, 102–110

16. `HIPAA (Health Insurance Portability and Accountability Act)`, 10, 12

14. `工具和资源`, 361

15. `漏洞`, 228

16. `Linux Administrator's Security Guide (网站)`, 370

17. `Linux Security Auditing Tool (LSAT)`, 361

18. `live (可启动) CDs`, 160–161

19. `live toolkits`, 362

20. `llCommView (TamoSoft)`, 161

21. `位置，选择`, 46

22. `日志分析`, 362

23. `记录安全事件`, 333

24. `Long, Johnny (作者)`

  1. `*Google Hacking for Penetration Testers*`, 282

25. `Long, Johnny (安全专家)`, 282

26. `low-hanging fruit`, 32

27. `LSAT (Linux Security Auditing Tool)`, 361

28. `lsof` 命令, 236

29. `LUCY (网站)`, 78–79, 368

### M

1. `MaaS360 (网站)`, 194

2. `MAC 地址供应商查找 (网站)`, 364

3. `MAC 伪造`, 150–151, 179–183

4. `mailsnarf (网站)`, 362

5. `假设`, 46–47

6. `恶意用户`

  1. `关于`, 9

  2. `与伦理黑客相比`, 10–12

  3. `定义`, 8

  4. `监控`, 332–334

7. `malware`, 268, 357

8. `ManageEngine (网站)`, 249, 367

9. `*Managing an Information Security and Privacy Awareness and Training Program* (Herold)`, 370

10. `手动分析`, 280

11. `手动评估`, 56–57

12. `映射`

  1. `网络`, 64–66

  2. `null sessions`, 211–212

13. `maxsize` 变量, 284

14. `MBSA (Microsoft Baseline Security Analyzer)`, 203, 226, 326, 373

15. `McAfee Host Intrusion Prevention for Server (网站)`, 233, 372

16. `MDM (移动设备管理)`, 193

17. `消息传递。*See* 通信和消息传递系统`

18. `Metasploit`

  1. `关于`, 22, 279

  2. `利用未打补丁的漏洞`, 220–225

  3. `网站`, 58, 204, 220, 244, 268, 359

19. `方法论`

  1. `评估漏洞`, 56–57

  2. `足迹`, 51–52

  3. `开放端口`, 53

  4. `入侵系统`, 58

  5. `扫描系统`, 52–53

  6. `测试`, 49–51

20. `Microsoft (网站)`, 93

21. `Microsoft Baseline Security Analyzer (MBSA)`, 203, 226, 326, 373

22. `Microsoft BitLocker Administration and Monitoring (网站)`, 363

23. `Microsoft Security Compliance Manager (网站)`, 308, 370

24. `Microsoft Security Tech Center (网站)`, 367

25. `Microsoft SQL Server Management Studio (网站)`, 306

26. `Microsoft SQL Server Management Studio Express (网站)`, 358

27. `Microsoft tools`, 203–205

28. `Microsoft Visio`, 42

29. `最小化`

  1. `数据库安全风险`, 307–308

  2. `存储系统安全风险`, 312–313

  3. `Web 安全风险`, 298–301

30. `缺失补丁，利用`, 217–225

31. `错误`, 351–355

32. `Mitnick, Kevin (黑客)`, 28

33. `移动设备管理 (MDM)`, 193

34. `移动设备`

  1. `关于`, 187

  2. `应用`, 194

  3. `破解笔记本电脑密码`, 188–193

  4. `破解手机和平板`, 193–198

  5. `工具和资源`, 363

  6. `漏洞`, 187–188

35. `monitor mode`, 143

36. `监控恶意使用`, 332–334

37. `多平台更新管理工具`, 249

### N

1. `NAS (NFS 基于的网络附加存储) 系统`, 308

2. `NAT (网络地址转换)`, 139

3. `National Institute of Standards and Technology (NIST)`, 56, 121, 275, 366, 371

4. `National Vulnerability Database (网站)`, 98, 234, 318, 371

5. `nbtstat (NetBIOS over TCP/IP 统计)`, 203

6. `NERC (North American Electric Reliability Corporation) CIP 要求`, 12

7. `Nessus (网站)`, 22, 229, 364

8. `net use` 命令, 212

9. `net view` 命令, 212–213

10. `NetBIOS (网络基本输入/输出系统)`, 203, 208–210

11. `NetBIOS 审计工具 (网站)`, 366

12. `NetBIOS over TCP/IP 统计 (nbstat)`, 203

13. `Netcat (网站)`, 138–139, 364

14. `Netcraft 搜索实用程序 (网站)`, 55

15. `Netcraft's *What's that site running?* (网站)`, 360

16. `netfilter/iptables (网站)`, 364

17. `NetResident (TamoSoft)`, 144, 267, 364

18. `NetScanTools Pro`, 22, 53, 65, 128, 133–134, 135, 165, 204, 229, 263, 364

19. `Netsparker`, 21, 22, 273, 278, 372

20. `netstat` 命令, 236

21. `NetStumbler`, 164, 374

22. `Network Address Translation (NAT)`, 139

23. `network analyzer`

  1. `关于`, 140–145

  2. `针对漏洞的对策`, 146

  3. `利用该工具破解密码`, 114–115

  4. `程序`, 141–146

24. `Network Basic Input/Output System (NetBIOS)`, 203, 208–210

25. `network components, physical security vulnerabilities`, 90–93

26. `network infrastructure`

  1. `关于`, 125–126

  2. `攻击`, 15

  3. `选择工具`, 127–128

  4. `安装通用网络防护`, 156–157

  5. `在网络上进行伦理黑客攻击`, 129–156

6. `易受攻击的脆弱性`, 126–127

27. `*网络安全入门* (Cobb)`, 122

28. `网络安全工具包 (网站)`, 362

29. `网络用户 (网站)`, 373

30. `网络`

  1. `分析数据`, 140–146

  2. `查找数据库`, 304–305

  3. `映射`, 64–66

  4. `工具和资源`, 363–365

31. `Nexpose`, 22, 57, 128, 153, 204, 225–226, 229, 273, 304, 309, 358, 361, 364, 373

32. `基于 NFS 的网络附加存储 (NAS) 系统`, 308

33. `NIST (国家标准与技术研究院)`, 56, 121, 275, 366, 371

34. `Nmap`, 53, 128, 131–132, 132–133, 206, 229, 230, 235, 364

35. `NMapWin (网站)`, 55, 128, 364

36. `非技术性攻击`, 14

37. `北美电力可靠性公司 (NERC) CIP 要求`, 12

38. `Nping (网站)`, 165, 364

39. `NTAccess (网站)`, 188, 366

40. `零扫描`, 133

41. `零会话，检测`, 211–212

### O

1. `缺乏安全性，安全通过`, 299

2. `Offensive Security Certified Professional (OSCP)`, 11

3. `Offensive Security 的漏洞数据库 (网站)`, 224, 359

4. `办公室，物理安全`, 85–93

5. `官方互联网协议标准 (网站)`, 126

6. `双向无线天线`, 161

7. `OmniPeek (Savvius)`, 22, 115, 128, 141, 161, 275, 364, 371, 374

8. `Omnipeek (网站)`, 53

9. `开放集团的 FAIR 风险税 onomy (网站)`, 368

10. `开放端口`, 53–56

11. `开源安全测试方法手册 (网站)`, 58, 368

12. `开源 Tripwire (网站)`, 241

13. `开放 Web 应用安全项目 (网站)`, 57, 278

14. `操作指南，用于最小化电子邮件安全威胁`, 270

15. `操作系统`, 15, 121–122

16. `ophcrack`, 21, 102, 107, 191, 363, 366

17. `ophcrack LiveCD (网站)`, 90

18. `Oracle`, 305

19. `组织密码脆弱性`, 97

20. `OSCP (Offensive Security Certified Professional)`, 11

21. `Outlook Web Access (OWA)`, 270

22. `外包`

  1. `伦理黑客`, 334–335

  2. `安全监控`, 333–334

  3. `测试`, 355

23. `OWA (Outlook Web Access)`, 270

24. `OWASP (网站)`, 368

25. `OWASP WebGoat 项目 (网站)`, 298

26. `OWASP Zed Attack Proxy 项目 (网站)`, 372

27. `Oxygen Forensic Suite (网站)`, 363

### P

1. `Palo Alto Networks (网站)`, 152, 300

2. `Pandora (网站)`, 366

3. `Paros Proxy (网站)`, 372

4. `合作伙伴`, 348–349

5. `口令短语`, 118

6. `Passware (网站)`, 189

7. `Passware Kit Forensic (网站)`, 363, 366

8. `Password Safe (网站)`, 118, 366

9. `密码破解软件`, 102–105

10. `受保护的文件，破解`, 110–112

11. `密码。*另见* cracking passwords`

  1. `关于`, 95–96

  2. `破解的对策`, 117–121

  3. `保护操作系统`, 121–122

  4. `脆弱性`, 96–98

12. `补丁`

  1. `关于`, 324–325

  2. `自动化`, 325–326, 331–332

  3. `Linux`, 248–249

  4. `管理`, 325, 367

13. `专利和商标局 (网站)`, 64

14. `支付卡行业数据安全标准 (PCI DSS)`, 10, 12, 361

15. `PCI DSS 渗透测试指南 (网站)`, 58

16. `PDQ Deploy (网站)`, 326

17. `渗透测试`, 1, 58

18. `渗透测试执行标准 (网站)`, 58

19. `端到端保护`, 258

20. `权限，共享`, 215–217

21. `Peter Davis & Associates 培训服务 (网站)`, 370

22. `钓鱼邮件`, 68, 77–79

23. `Phone Breaker (Elcomsoft)`, 197, 363

24. `手机`

  1. `破解`, 193–198

  2. `用于社交工程攻击`, 77

25. `PHP (Hypertext Preprocessor)`, 291

26. `Phrack (网站)`, 35

27. `物理安全`

  1. `关于`, 83

  2. `基本脆弱性`, 84–85

  3. `使用 Linux 检查`, 245–246

  4. `网络分析仪`, 146

  5. `你的办公室中的脆弱性`, 85–93, 183–184

28. `Ping of Death`, 153

29. `Ping (ICMP echo) 回复`, 54

30. `ping 扫描`, 131–132, 135

31. `PIPEDA (加拿大个人信息保护和电子文档法)`, 12

32. `pkgtool (Slackware 包工具)`, 248

33. `计划开发`

  1. `关于`, 40

  2. `攻击树分析`, 42

  3. `选择要黑客的系统`, 40–41

  4. `创建测试标准`, 43–47

  5. `设定目标`, 37–40

  6. `保险`, 40

  7. `选择安全评估工具`, 47–48

34. `关闭安全漏洞`

  1. `关于`, 323

2. `评估安全基础设施`, 328–329

3. `加固系统`, 326–327

4. `补丁`, 324–326

5. `将报告转化为行动`, 323–324

35. `点对点隧道协议 (PPTP)`, 170–171

36. `政策，安全`, 11

37. `POP3 命令`, 137

38. `Port 80 软件的 ServerMask (网站)`, 299, 372

40. `PortSentry (网站)`, 233, 364

41. `POST` 请求, 292

42. `Postfix (网站)`, 270

43. `电源线，拔掉`, 27

44. `PPTP (点对点隧道协议)`, 170–171

45. `预共享密钥 (PSKs)`, 169

46. `事先批准`, 351

47. `将漏洞优先级排序`, 319–320

48. `隐私，尊重`, 17

49. `隐私政策`, 66

50. `Privacy Rights Clearinghouse 网站的数据泄露时间线 (website)`, 342, 369

51. `Proactive Password Auditor (Elcomsoft)`, 21, 103, 366

52. `Proactive System Password Recovery (Elcomsoft)`, 101, 103

53. `伦理黑客的过程`

  1. `关于`, 18

  2. `评估结果`, 23

  3. `执行计划`, 22–23

  4. `制定你的计划`, 18–20

  5. `实施建议`, 23, 24

  6. `选择工具`, 20–21

54. `专业责任保险`, 40

55. `Project RainbowCrack (网站)`, 107

56. `PromiscDetect (网站)`, 115, 146, 365

57. `静默模式 (promiscuous mode)`, 115, 140

58. `协议`, 54

59. `PROTOS (网站)`, 273, 371

60. `PSKs (预共享密钥)`, 169

61. `*Psychology For Dummies* (Cash)`, 73

62. `公共信息，收集`, 51–52, 61–64

63. `公众对黑客的看法`, 25–28

64. `PVS-Studio 分析器 (网站)`, 300, 369

65. `pwdump3`

  1. `使用 pwdump3 破解 Windows 密码`, 107–109

  2. `网站`, 103, 367

66. `Pwnie Express (网站)`, 90, 359

1. `qmail (网站)`, 270

2. `Qualys (网站)`, 229

3. `Qualys SSL Labs (网站)`, 372

4. `QualysGuard`

  1. `漏洞扫描器`, 365

  2. `网站`, 57, 358, 361, 373

### Q

1. `qmail (网站)`, 270

2. `Qualys (网站)`, 229

3. `Qualys SSL Labs (网站)`, 372

4. `QualysGuard`

  1. `漏洞扫描器`, 365

  2. `网站`, 57, 358, 361, 373

### R

1. `RADIUS 服务器`, 169

2. `彩虹攻击，用于破解密码`, 107

3. `彩虹表`, 103, 367

4. `RainbowCrack (网站)`, 103, 367

5. `将漏洞排名`, 319–320

6. `Rapid7 (网站)`, 57, 290

7. `RARPs (反向 ARP)`, 179

8. `实时传输协议 (RTP)`, 272

9. `伦理黑客的原因`, 347–350

10. `黑客的原因`, 30–33

11. `Reaver`, 173–174, 374

12. `Reaver Pro (网站)`, 173

13. `录音业协会 (RIAA)`, 33

14. `录制音频流`, 273–275

15. `Red Hat 企业 Linux`, 240

16. `Red Hat 包管理器 (RPM)`, 248

17. `红队`, 39

18. `重新组织的黑客`, 18, 336

19. `非洲区域互联网注册管理机构 (AFRINIC)`, 66, 359

20. `北美、加勒比部分和下撒哈拉非洲区域的非洲互联网注册管理机构 (ARIN)`, 66, 359

21. `注册表`, 104

22. `监管问题`, 12

23. `相关运营商`, 282

24. `关系，在社交工程攻击中被利用`, 72–74

25. `中继，SMTP`, 263–266

26. `记忆图标`, 3

27. `报告结果`

  1. `关于`, 317

  2. `编译`, 317–319

  3. `创建报告`, 321–322

  4. `将漏洞优先级排序`, 319–320

28. `请求评论 (RFCs) 列表`, 126

29. `住宅电话`, 77

30. `尊重隐私`, 17

31. `回应漏洞`, 46

32. `限制对系统的匿名连接`, 215

33. `反向 ARP (RARP)`, 179

34. `反向社会工程`, 73

35. `RFCs (请求评论) 列表`, 126

36. `.rhosts 文件`, 238–341

37. `RIAA (录音业协会)`, 33

38. `RIPE 网络协调中心 (网站)`, 66, 360

39. `风险分类 (Open Group)`, 368

40. `风险。*另见* 漏洞`

  1. `数据库安全`, 307–308

  2. `最小化存储系统安全`, 312–313

  3. `最小化 Web 安全`, 298–301

  4. `安全`, 14–16

41. `野生无线设备`, 175–179

42. `RPM (Red Hat 包管理器)`, 248

43. `RTP (实时传输协议)`, 272

44. `伦理黑客的规则`, 16–18

### S

1. `SAM (安全帐户管理) 数据库`, 104

2. `SANs (iSCSI 存储区域网络)`, 308

3. `SANS 关键安全控制`, 57

4. `SANS 全球信息保障认证 (GIAC)`, 11, 358

5. `SANS 学院`, 121, 371

6. `Savvius' OmniPeek (网站)`, 115, 128, 141, 161, 275, 364, 371, 374

7. `扫描仪`, 128

8. `扫描`

  1. `端口`, 129–135

  2. `SNMP (简单网络管理协议)`, 135–137

  3. `系统`, 52–53

9. `Schwartau, Winn (安全分析师)`, 337

10. `抓取`, 78

12. `script kiddies`, 26, 28, 34

13. `SEC (Securities and Exchange Commission)`, 64, 75, 360

14. `*(IN)SECURE Magazine*`, 35, 360

15. `Secure Shell (SSH)`, 171

16. `Secure Sockets Layer/Transport Layer Security (SSL/TLS)`, 171

17. `securing`

  1. `operating systems`, 121–122

  2. `.rhosts and hosts.equiv files`, 238–341

18. `Securities and Exchange Commission (SEC)`, 64, 75, 360

19. `security.*See also* physical security`

  1. `education and learning resources`, 368

  2. `evaluations`, 348

  3. `methods and models`, 368

  4. `monitoring outsourcing`, 333–334

  5. `by obscurity`, 299

  6. `Windows 10`, 219

20. `Security Accounts Manager (SAM) database`, 104

21. `security assessment tools`, 47–48

22. `Security Awareness, Inc. (website)`, 337, 370

23. `security events, logging`, 333

24. `security infrastructure, assessing`, 328–329

25. `*Security On Wheels* (blog)`, 368

26. `security policy`, 11

27. `security processes, managing`

  1. `automating ethical-hacking`, 331–332

  2. `maintaining security efforts`, 337

  3. `monitoring malicious use`, 332–334

  4. `outsourcing ethical hacking`, 334–335

  5. `security-aware mindset`, 336–337

28. `security researchers`, 29

29. `Security Tools Distribution (website)`, 362

30. `security-aware mindset`, 336–337

31. `The Security Awareness Company (website)`, 337

32. `Secur/Tree (Amenza Technologies Limited)`, 42, 368

33. `selecting locations`, 46

34. `semidirectional wireless antenna`, 161

35. `Sensitive Data Manager`, 311

36. `Server Message Block (SMB)`, 208

37. `ServerDefender (website)`, 300, 370

38. `service set identifier (SSID)`, 163

39. `Session Initiation Protocol (SIP)`, 272

40. `SetGID`, 243

41. `SetUID`, 243

42. `7-Zip (website)`, 10, 363

43. `SFTP`, 256

44. `Share Finder tool`, 209–210

45. `share permissions, checking`, 215–217

46. `shares`, 209–210

47. `Shavlik Patch (website)`, 367

48. `shoulder surfing`, 95, 100

49. `showing value`, 346

50. `SIEM Data Collection Log Management (website)`, 362

51. `Simple Mail Transfer Protocol (SMTP)`

  1. `account enumeration`, 260–263

  2. `capturing traffic`, 267

  3. `e-mail header disclosures`, 266–267

  4. `malware`, 268

  5. `relay`, 263–266

52. `Simple Network Management Protocol (SNMP)`, 135–137

53. `SIP (Session Initiation Protocol)`, 272

54. `sipsak (website)`, 273

55. `SiteDigger (website)`, 372

56. `Slackware Linux Security Advisories (website)`, 367

57. `Slackware Package Tool (pkgtool)`, 248

58. `SMAC (KLC Consulting)`, 150–151, 182

59. `SMAC MAC address changer (website)`, 365

60. `SmartDraw (website)`, 42, 363

61. `Smartwhois (website)`, 65

62. `SMB (Server Message Block)`, 208

63. `SMTP (Simple Mail Transfer Protocol)`

  1. `account enumeration`, 260–263

  2. `capturing traffic`, 267

  3. `e-mail header disclosures`, 266–267

  4. `malware`, 268

  5. `relay`, 263–266

64. `SMTP command`, 137

65. `smtpscan (website)`, 259, 362

66. `Smurf (website)`, 357

67. `Snare (website)`, 233

68. `SNARE (website)`, 365

69. `sniffdet (website)`, 115, 146, 365

70. `Sniffer tool`, 140

71. `sniffing, defined`, 140

72. `SNMP (Simple Network Management Protocol)`, 135–137

73. `SNMPUTIL (website)`, 135

74. `Social Engineer Toolkit (website)`, 368

75. `social engineering`

  1. `about`, 14, 67–68

  2. `countermeasures`, 80–82

  3. `cracking passwords with`, 99–100

  4. `implementing attacks`, 75–79

  5. `implications of`, 70–74

  6. `tests`, 68–69

  7. `tools and resources`, 368

  8. `why attackers use`, 69–70

76. `social engineering attacks, performing`

  1. `about`, 74–75

  2. `building trust`, 71–72

  3. `exploiting relationship`, 72–74

  4. `seeking information`, 75–79

77. `social media`, 62

78. `SoftPerfect Network Scanner (website)`, 22, 55, 204, 365, 373

79. `software`

  1. `for minimizing e-mail security threats`, 269

  2. `password-cracking`, 102–105

  3. `unauthorized`, 27

80. `SolarWinds Network Configuration Manager (website)`, 139

81. `SonarQube (website)`, 300, 369

82. `SonicWALL (website)`, 365

83. `source code, analyzing`, 300–301, 369

84. `SourceForge (website)`, 229, 361

85. `Spector 360 (SpectorSoft)`, 112

86. `Spirion (website)`, 369

87. `sponsorship`, 18, 341

88. `SQL Inject Me (website)`, 289, 372

89. `SQL injection`, 27, 287–289

90. `SQL Power Injector (website)`, 289, 372

91. `SQLPing3`, 104, 304, 305, 358, 367

92. `SSH (Secure Shell)`, 171

93. `SSID (service set identifier)`, 163

94. `SSL (HTTPS)`, 156

95. `SSL Labs (website)`, 156

96. `SSL/TLS (Secure Sockets Layer/Transport Layer Security)`, 171

97. `统计，关于工具和资源`, 369

98. `密码存储`, 104, 113–114, 118

99. `邮件存储过载`, 255

100. `存储系统`

  1. `关于`, 308

  2. `选择用于安全测试的工具`, 309

  3. `在网络文件中查找敏感文本`, 310–312

  4. `最小化安全风险`, 312–313

  5. `工具和资源`, 369

101. `支持人员，错误`, 68

102. `SUSE`, 248

103. `.swf 文件`, 63

104. `交换机`, 63, 115

105. `Symantec（网站）`, 246

106. `Symantec PGP（网站）`, 370

107. `SYN 洪水`, 153

108. `SYN Stealth 扫描`, 133

109. `Synful Knock Scanner（网站）`, 153, 365

110. `Sysinternals（网站）`, 204, 373

111. `系统崩溃`, 17–18

112. `系统加固`, 326–327, 369–370

113. `系统日志，启用`, 333

114. `系统恢复（Elcomsoft）`, 102, 188, 363, 366

115. `系统扫描`, 205–207, 229–234

116. `系统`

  1. `选择要黑客攻击的目标`, 40–41

  2. `加固`, 326–327, 369–370

  3. `渗透`, 58

  4. `扫描`, 52–53

### T

1. `表格，破解`, 193–198

2. `TamoSoft`

  1. `CommView`, 115, 128, 141, 161, 275, 370, 373

  2. `Essential NetTools`, 135, 364, 365

  3. `NetResident`, 144, 267, 364

3. `tarpitting`, 258

4. `任务特定工具`, 204–205

5. `TCP（传输控制协议）`, 54, 129

6. `TCP Wrapper`, 238

7. `*TCP/IP For Dummies*，第 6 版（Leiden and Wilensky）`, 126

8. `TCP/UDP 端口`, 54

9. `TCPView（网站）`, 204

10. `技术密码漏洞`, 97–98

11. `技术图标`, 3

12. `TechSmith's Camtasia Studio（网站）`, 45

13. `telnet（telnetd）`, 137, 230

14. `术语`, 7–9

15. `恐怖分子`, 30

16. `测试`

  1. `关于`, 49

  2. `服务拒绝（DoS）攻击`, 152–155

  3. `电子邮件头泄露`, 266–267

  4. `文件权限黑客`, 243–244

  5. `防火墙规则`, 138–140

  6. `外包`, 355

  7. `用于 SMTP 中继的服务器`, 263–266

  8. `社会工程`, 68–69

  9. `标准`, 43–47

  10. `存储系统安全`, 309

17. `THC-Amap（网站）`, 361

18. `THC-Hydra（网站）`, 103, 295, 367, 372

19. `theHarvester（网站）`, 360, 362

20. `3M Privacy Filters（网站）`, 100, 363

21. `Tiger（网站）`, 361

22. `Tiger 安全审计工具`, 247

23. `tiger team`, 39

24. `计时，在伦理黑客测试中`, 43–44

25. `Tip 图标`, 3

26. `TLS（传输层安全）`, 156

27. `工具和资源`

  1. `高级恶意软件`, 357

  2. `一站式评估`, 204

  3. `Bluetooth`, 357

  4. `认证`, 358

  5. `用于破解笔记本电脑密码`, 188–193

  6. `数据库`, 358

  7. `用于网络基础设施的伦理黑客攻击`, 127–128

  8. `一般性研究`, 359–360

  9. `黑客材料`, 360

  10. `键盘记录器`, 360

  11. `法律和法规`, 361

  12. `Linux`, 361

  13. `即时工具包`, 362

  14. `日志分析`, 362

  15. `消息传递`, 362

  16. `Microsoft`, 203–205

  17. `杂项`, 363

  18. `移动`, 363

  19. `网络`, 363–365

  20. `密码破解`, 365–367

  21. `补丁管理`, 367

  22. `端口扫描`, 129–135

  23. `安全教育和学习资源`, 368

  24. `安全方法和模型`, 368

  25. `选择`, 20–21

  26. `社会工程`, 368

  27. `源代码分析`, 369

  28. `统计`, 369

  29. `存储`, 369

  30. `系统加固`, 369–370

  31. `任务特定`, 204–205

  32. `用于测试存储系统安全`, 309

  33. `用户意识和培训`, 370

  34. `使用正确的`, 354

  35. `VoIP（互联网协议语音）`, 370–371

  36. `漏洞数据库`, 371

  37. `用于 Web 应用`, 278–279

  38. `网站和应用`, 371–372

  39. `Windows`, 373

  40. `无线网络`, 373–374

28. `top talkers`, 144

29. `流量，捕获`, 267, 273–275

30. `Traffic IQ Professional（idappcom）`, 365

31. `培训，作为对社会工程的对策`, 80–82

32. `Transmission Control Protocol（TCP）`, 54, 129

33. `Transport Layer Security（TLS）`, 156

34. `Tripwire`, 244

35. `TrueCrypt`, 192

36. `信任，在社交工程攻击中构建`, 71–72

37. `可信度`, 17

38. `Twitter（网站）`, 62

39. `*2600-The Hacker Quarterly*（杂志）`, 35, 360

### U

1. `UDP（用户数据报协议）`, 129

2. `UDP 扫描`, 133

3. `UDPFlood（网站）`, 154, 365

4. `UEFI（统一可扩展固件接口）`, 116

5. `未经认证的枚举`, 208–210

6. `未经授权的软件`, 27

7. `统一可扩展固件接口 (UEFI)`, 116

8. `美国专利和商标局 (网站)`, 360

9. `美国州级数据泄露通知法律 (网站)`, 361

10. `UNIX 变体`

  1. `使用 John the Ripper 破解密码`, 109–110

  2. `加固`, 122

  3. `密码存储位置`, 104

11. `UNIX 系统，MAC 地址伪造在`, 150

12. `不安全的接口`, 155–156

13. `不安全的登录机制`, 293–297

14. `up2date`, 248

15. `高层管理支持`, 341–346

16. `URL 操作`, 284–286

17. `美国政府 (网站)`, 66

18. `US Search.com (网站)`, 360

19. `美国证券交易委员会 (网站)`, 64, 75, 360

20. `US-CERT 漏洞备注数据库 (网站)`, 56, 371

21. `用户意识与培训`, 370

22. `用户数据报文协议 (UDP)`, 129

23. `用户密码漏洞`, 96–98

24. `公用程序，物理安全漏洞`, 87–88

### V

1. `值，显示`, 346

2. `供应商，错误`, 68

3. `Veracode (网站)`, 363

4. `Verizon 数据泄露调查报告 (网站)`, 12, 95, 342, 369

5. `虚拟专用网络 (VPN) 服务`, 54

6. `VirtualBox (网站)`, 52

7. `Visio`, 328

8. `Visual Code Grepper (网站)`, 300, 369

9. `VMware Workstation Pro (网站)`, 52

10. `VNC (网站)`, 91

11. `互联网协议语音 (VoIP)`

  1. `关于`, 270–271

  2. `针对漏洞的对策`, 275

  3. `工具和资源`, 370–371

  4. `漏洞`, 272–273

12. `语音流量`, 273–275

13. `VoIP (互联网协议语音)`

  1. `关于`, 270–271

  2. `针对漏洞的对策`, 275

  3. `工具和资源`, 370–371

  4. `漏洞`, 272–273

14. `*VoIP For Dummies* (Kelly)`, 271

15. `VoIP Hopper (网站)`, 272, 371

16. `VoIP 服务器`, 77

17. `vomit (网站)`, 275, 371

18. `VPN (虚拟专用网络) 服务`, 54

19. `VRFY` 命令, 261–263

20. `漏洞。*另见* 风险`

  1. `评估`, 56–57

  2. `数据库`, 306–307

  3. `消除`, 352–353

  4. `Linux`, 228

  5. `消息系统`, 253–254

  6. `移动设备`, 187–188

  7. `网络基础设施`, 126–127

  8. `密码`, 96–98

  9. `优先级`, 319

  10. `响应`, 46

  11. `SNMP`, 135–136

  12. `Web`, 279–298

  13. `Windows (Microsoft)`, 202–203

  14. `无线网络`, 159–160

21. `漏洞测试`, 1

### W

1. `警告! 图标`, 3

2. `WatchGuard (网站)`, 300, 313

3. `弱 BIOS 密码`, 116

4. `弱密码存储`, 113–114

5. `Web 访问控制，绕过`, 27

6. `Web 爬虫`, 63–64

7. `Web 开发者 (网站)`, 278, 298

8. `Web 搜索`, 62–63

9. `WebGoat (网站)`, 372

10. `WebInspect`, 371

11. `网站和应用程序`

  1. `关于`, 277–278

  2. `cantennas`, 162

  3. `选择 Web 应用工具`, 278–279

  4. `用于获取公开信息`, 64

  5. `黑客视角`, 353

  6. `可启动的 Linux 工具包`, 160

  7. `最小化安全风险`, 298–301

  8. `工具和资源`, 371–372

  9. `受 SNMP 漏洞影响的供应商和产品`, 135–136

  10. `漏洞`, 279–298

12. `Wellenreiter (网站)`, 160, 374

13. `WEP (Wired Equivalent Privacy)`, 167–170

14. `WEPCrack (网站)`, 167, 374

15. `WhatIsMyIP (网站)`, 53, 360, 365

16. `Where Does This Link Go? (网站)`, 368

17. `白帽 (好人) 黑客`, 9, 29

18. `Whois`, 52, 65–66, 360

19. `WiFi。*另见* 无线局域网 (WiFi)`

20. `WiFi Pineapple (网站)`, 165, 374

21. `Wi‑Fi Protected Access (WPA)`, 167–170

22. `Wi‑Fi Protected Setup (WPS)`, 172–174

23. `WiFinder (网站)`, 374

24. `WiGLE 数据库 (网站)`, 162, 374

25. `Wilensky, Marshall (作者)`

  1. `*TCP/IP For Dummies*，第 6 版`, 126

26. `WinAirsnort (网站)`, 374

27. `Windows (Microsoft)`

  1. `关于`, 201–202

  2. `检查共享权限`, 215–217

  3. `选择工具`, 203–205

  4. `使用 pwdump3 和 John the Ripper 破解密码`, 107–109

  5. `检测空闲会话`, 210–215

  6. `利用未打补丁的漏洞`, 217–225

  7. `MAC 地址伪造在`, 150–151

  8. `执行经过身份验证的扫描`, 225–226

  9. `加固`, 121–122

  10. `安全`, 219

  11. `密码存储位置`, 104

  12. `工具和资源`, 373

  13. `漏洞`, 202–203

28. `Windows 7`, 211, 215

29. `Windows 8`, 211

30. `Windows 10`, 211, 219

31. `Windows 2000/NT`, 216

32. `Windows 注册表`, 150–151

33. `Windows Server 2008`, 211

34. `Windows Server 2008/R2`, 215

35. `Windows Server 2016`, 214

36. `Windows Server Update Services (WSUS)`, `/path/to/xxx`, `326`, `367`

37. `Windows Update`, `326`

38. `Windows XP`, `216`

39. `Winfo (website)`, `205`, `213`, `373`

40. `WinHex (website)`, `120`, `189`, `292`, `367`, `369`

41. `WinMagic (website)`, `93`, `246`, `370`

42. `WinMagic SecureDoc (website)`, `193`

43. `WinNuke`, `153`

44. `WinZip (website)`, `363`

45. `Wired Equivalent Privacy (WEP)`, `167`–170

46. `wireless LANs (WiFi)`

  1. `about`, `159`

  2. `attacks and countermeasures`, `165`–186

  3. `choosing tools`, `160`–162

  4. `discovering`, `162`–164

  5. `implications of vulnerabilities`, `159`–160

47. `wireless networks, tools and resources`, `373`–374

48. `*Wireless Networks For Dummies* (Davis and Lewis)`, `184`

49. `Wireless Security Auditor (Elcomsoft)`, `161`, `172`, `373`

50. `wireless workstations`, `185`

51. `Wireshark (website)`, `53`, `115`, `128`, `141`, `365`

52. `WPA (Wi-Fi Protected Access)`, `167`–170

53. `WPS (Wi-Fi Protected Setup)`, `172`–174

54. `WSDigger (website)`, `298`, `372`

55. `WSFuzzer (website)`, `372`

56. `WSUS (Windows Server Update Services)`, `225`, `326`, `367`

1. `xinetd program`, `236`–237

2. `Xmas Tree scan`, `133`

3. `XSS (cross-site scripting)`, `289`–290

4. `XSS-Me Firefox Add-on (website)`, `290`

1. `Yahoo! Finance (website)`, `75`, `360`

2. `YouTube (website)`, `62`

### Z

1. `ZabaSearch (website)`, `64`, `360`

2. `zombies`, `74`

![](img/ad1.png) ![](img/ad2.png) ![](img/ad3.png) ![](img/ad4.png) ![](img/ad5.png) ![](img/ad6.png)

Take Dummies with you everywhere you go!

![Dummies Logo](http://www.dummies.com)

Go to our [`Website`](http://www.dummies.com)

![Facebook Logo](http://www.facebook.com/fordummies)

Like us on [`Facebook`](http://www.facebook.com/fordummies)

![Twitter Logo](http://www.twitter.com/fordummies)

Follow us on [`Twitter`](http://www.twitter.com/fordummies)

![YouTube Logo](http://www.youtube.com/user/fordummies)

Watch us on [`YouTube`](http://www.youtube.com/user/fordummies)

![LinkedIn Logo](http://www.linkedin.com/groups?home=&gid=3229946&trk=anet_ug_hm)

Join us on [`LinkedIn`](http://www.linkedin.com/groups?home=&gid=3229946&trk=anet_ug_hm)

![Pinterest Logo](http://pinterest.com/fordummies/)

Pin us on [`Pinterest`](http://pinterest.com/fordummies/)

![Google Plus Logo](https://plus.google.com/105265587979403653723)

Circle us on [`google+`](https://plus.google.com/105265587979403653723)

![Newsletter Envelope Icon](http://www.dummies.com/go/newsletter)

Subscribe to our [`newsletter`](http://www.dummies.com/go/newsletter)

![Book Cover Icon](http://covers.dummies.com/)

Create your own [`Dummies book cover`](http://covers.dummies.com/)

![Shopping Bag Icon](http://dummiesmerchandise.com)

[Shop Online](http://dummiesmerchandise.com)

![For Dummies, A Wiley Brand](img/dummies-wordmark.png)

## WILEY END USER LICENSE AGREEMENT

Go to [`www.wiley.com/go/eula`](http://www.wiley.com/go/eula) to access Wiley’s ebook EULA.


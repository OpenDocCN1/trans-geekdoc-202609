

本章的最后一部分是关于分析的。在实施安全控制之前，您必须确定它们是否是您环境的正确解决方案。您可能会被要求进行成本效益分析，甚至在考虑可用性指标的情况下，评估拟议解决方案的性能、延迟、可扩展性、能力、易用性和可维护性。

虽然本章不是本书中技术性最强的章节之一，但它仍然很重要，因为安全专业人员必须了解如何与管理层合作，为所需的安全控制争取资金并评估其有效性，同时还要知道如何创建建议书请求或报价请求。

## 应用研究方法以确定行业趋势及对企业的影响

IT 安全与许多其他技术领域一样，变化迅速。请稍作思考，就在不久前的 1995 年，Dan Farmer 和 Wietse Venema 创建了最早的漏洞评估工具之一。这个早期工具被称为 SATAN，并未受到 IT 安全领域所有从业者的好评。有人质疑是否需要一种用于扫描和识别漏洞的工具。尽管漏洞扫描在 1995 年是一次巨大的范式转变，但如今使用此类工具已成为常规做法。关于将工具置于公共论坛以便好人和坏人都能使用的争论至今仍在继续。作为安全专业人员，我们必须掌握行业趋势及其对企业的潜在影响。随着 IT 安全的成熟和对行业变化的适应，许多此类趋势已经发生，并将继续发生。

### 执行持续研究

作为一名安全专业人员，您必须执行持续研究，以跟上当前的威胁和行业变化。有许多资源可帮助您进行研究。此处仅列出了其中几个，仅作为可用资源的一小部分示例。我将这些资源分为趋势和工具两类。

您可能还记得您的第一台电脑，或者多年前您可能曾告诉某人，只要运行杀毒程序，他们就能免受大多数在线威胁的侵害。这是 2000 年之前的普遍认知。如今，杀毒程序只是防御数字威胁所需保护措施的一部分。

CASP 必须执行漏洞研究并掌握当前的安全趋势。此类研究有助于识别弱点，并在网络遭受攻击前提醒管理员。研究还有助于识别和纠正潜在的安全问题，防止其恶化。[图 8.1](#c08.xhtml#c08-fig-0001) 显示了 NIST 国家漏洞数据库网站，地址为 `http://nvd.nist.gov`。以下是可用于此目的的其他网站列表：

![图 8.1 美国国家标准技术研究院国家漏洞数据库网站](images/c08f001.jpg)

**图 8.1** 美国国家标准技术研究院国家漏洞数据库网站

`www.cert.org`

`www.securiteam.com`

`www.securitytracker.com`

`www.securityfocus.com`

`www.hackerwatch.org`

`www.hackerstorm.com`

`www.hackerjournals.com`

`http://hak5.org/`

`http://pauldotcom.com/`

`www.exploit-db.com/`

`http://packetstormsecurity.org/`

`www.offensivecomputing.net/`

作为 CASP，知道从哪里获取信息很重要，但您也必须知道从哪里获取安全工具。一个很棒的列表在 `http://sectools.org/`。SecTools 网站列出了 125 个评分最高的网络安全工具，并按类别细分。安全领域的任何人都建议浏览该列表并研究他们不熟悉的工具，因为这些工具既可以用于恶意目的，也可以用于正义目的。该列表最后更新于 2011 年，自那以后已发布了许多工具。无论能力和受欢迎程度如何，来自开放 Web 应用安全项目 (OWASP) 网站的 CAL9000 等工具集合，在列表修订之前都不会出现在此列表中。该网站是查找您不知道或未使用过的工具的好地方。以下是我访问时列出的前十二个工具：

1.  **Wireshark**：一款评价极高的数据包嗅探器和网络分析工具。
2.  **Metasploit**：一款集成的安全评估工具，提供免费版和付费版。
3.  **Nessus**：一款知名的漏洞评估工具，可扫描 Windows、Linux 和 UNIX 计算机。提供家庭免费版和商业版。
4.  **Aircrack**：专为破解 802.11 无线 WEP 和 WPA 加密而设计。
5.  **Snort**：市场上最知名的 IDS 工具之一。
6.  **Cain & Abel**：一款基于 Windows 的工具，可执行多种活动，如枚举、ARP 投毒、密码破解和无线分析。请参见[图 8.2](#c08.xhtml#c08-fig-0002)。
7.  **Kali**：一张包含多种安全工具的可启动 Live CD。它已被取代
8.  **Netcat**：一款在 Linux 和 Windows 下运行的命令行工具。它用途广泛，可用作远程监听器、端口扫描、横幅抓取，也可用于传输文件。替代品包括 socat 和 cryptcat（加密替代品）。
9.  **TCP Dump**：一款在 Linux 上运行的命令行数据包分析工具；也有称为 WinDump 的 Windows 版本。
10. **John the Ripper**：一款可在 Linux 和 Windows 计算机上运行的命令行密码破解工具。
11. **Hping**：一款数据包构造工具，可用于扫描和其他安全活动。
12. **Kismet**：一款基于 Linux 的无线安全工具，允许您捕获广播和非广播 SSID。

![图 8.2 Cain & Abel](images/c08f002.jpg)

**图 8.2** Cain & Abel

另一个很棒的工具列表可以在 CASP 考试目标中找到。这些是在参加 CASP 考试前您需要深入了解的工具：

1.  **数据包嗅探器** 此类别包括 Wireshark 和执行数据包分析的类似工具。您可以在 `www.wireshark.org/download.html` 下载 Wireshark。

    CASP 考试将要求您不仅了解 Wireshark 等数据包嗅探器，还了解 IPv4 和 IPv6 等常见协议。请花些时间使用 Wireshark 复习这些协议。IPv4 和 IPv6 之间有许多区别。其中之一是 IPv6 内置了 IPSec，而 IPv4 仅将其作为附加组件。[图 8.3](#c08.xhtml#c08-fig-0003) 显示了 IPv4 头部示例，[图 8.4](#c08.xhtml#c08-fig-0004) 显示了 IPv6 头部示例。要深入了解此主题，请查阅 W. Richard Stevens 的《TCP/IP 详解》系列：`www.kohala.com/start/`

2.  **易受攻击的 Web 应用程序** 预构建的易受攻击 Web 应用程序，如 WebGoat、Hacme Bank 或 DVL (Damn Vulnerable Linux)，可用于深入了解常见 Web 应用程序及其漏洞。您可以从 `www.owasp.org/index.php/Category:OWASP_WebGoat_Project` 下载 WebGoat。

    您可以从 `www.mcafee.com/us/downloads/free-tools/hacme-bank.aspx` 下载 Hacme Bank。DVL 可在此处找到：`http://distrowatch.com/table.php?distribution=dvl`。

3.  **Microsoft Windows** CASP 不仅应对工具有良好的工作理解，还应对常见操作系统（如 Microsoft Windows Vista、7、8、8.1、Server 2008 和 Server 2012）有良好的工作理解。您可以从 `www.microsoft.com/windowsserver2008/en/us/trial-software.aspx` 下载 Server 2008 R2 的 180 天演示版，或从 `https://www.microsoft.com/en-us/evalcenter/try` 下载 Windows 8/8.1 开发者版本。


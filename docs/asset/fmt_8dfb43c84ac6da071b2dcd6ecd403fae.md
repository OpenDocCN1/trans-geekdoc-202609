
为演示目的，我们将扫描单个计算机。当你选择该选项时，你将看到一个屏幕，允许你指定要扫描的计算机（默认为你当前的计算机）以及要执行哪些扫描。这在图 11.5中显示。

![Figure 11.5 Scanning a single computer. ¶  ¶ The Microsoft baseline security analyzer 2.2 window is shown. The window displays the details of the computer to be scanned. They are computer name, IP address, and security report name. It lists various options as checkboxes in which the following are selected: check for windows administrative vulnerabilities, check for weak passwords, check for IIS administrative vulnerabilities, check for SQL administrative vulnerabilities, and check for security updates. ¶ ](img/11fig05.jpg)

Figure 11.5 Scanning a single computer. ¶ 

然后只需启动扫描。对于单个计算机，它不会耗时长，但对多个计算机则可能耗时较长。当它完成后，你将收到一份详细说明了检查了什么以及是否正常的报告；它还包含链接，以便你获取更深入的解释。这在图 11.6中显示。

![Figure 11.6 MBSA report.](img/11fig06.jpg)

Figure 11.6 MBSA report.

我认为批评者的观点是有道理的，但我认为这一特定工具是对于安全新手的优秀选择。它易于使用，并可以快速提供可操作的信息。

### NESSUS

Nessus ([www.Nessus.org](http://www.Nessus.org)) 是首屈一的网络漏洞扫描工具。先前有一个免费版本供个人使用，并有商业版。现在它只可以付费。这可能是现在最广泛使用的漏洞扫描工具。它并不像MBSA那样简单易用，但具有更多能力。我们将探讨基本功能。如果你有兴趣进一步学习Nessus，建议你参考Nessus网站的文档。

Nessus 是一个知名漏洞扫描工具，它已经被使用多年。现在，它不是免费的。许可证的价格超过每年2100美元，可以从 [`www.tenable.com`](https://www.tenable.com) 获取。价格是许多渗透测试人员的障碍。Nessus的首要优势是供应商不断更新它能够扫描的漏洞。Nessus还有一个简单易用的网页界面，如图 11.7所示。

![Figure 11.7 Nessus main screen.](img/11fig07.jpg)

Figure 11.7 Nessus main screen.

如果你选择 **New Scan**，你会得到一个数个选项，如图 11.8所示。

![Figure 11.8 Nessus scan options. ¶  ¶ The Nessus main screen presents several scan options. It includes advanced scan, audit cloud infrastructure, bedlock detection, bash shellshock detection, basic network scan, credential patch audit, drown detection, host discovery, Intel AMT security bypass, internal PCI network scan, malware scan, MDM configuration audit, mobile device scan, offline config audit, PCI quarterly external scan, and policy compliance auditing. ¶ ](img/11fig08.jpg)

Figure 11.8 Nessus scan options. ¶ 

你可以选择 **Basic Network Scan** 来看一个直观的基本设置。你需要为你的扫描命名并选择一个IP地址范围，如图 11.9所示。

![Figure 11.9 Nessus basic network scan options.](img/11fig09.jpg)

Figure 11.9 Nessus basic network scan options.

然后你可以安排扫描在稍后运行或立即启动它。Nessus 扫描可能耗时较长因为它很彻底。结果在一个组织良好的屏幕上显示，如图 11.10所示。

![Figure 11.10 Nessus results. ¶  ¶ The Nessus screen shows the results of the test scan options. The screen presents the number of the host with its vulnerabilities. In the right pane, the scan details such as name, status, policy, scanner, folder, start, end, elapsed, and targets are listed. It is followed by a pie chart indicating the various modes like critical, high, medium, low, and information. ¶ ](img/11fig10.jpg)

Figure 11.10 Nessus results. ¶ 

然后你可以对任何感兴趣的项目进行深入探讨。如果你双击某个特定IP地址，你可以看到该IP的详细信息，如图 11.11所示。

![Figure 11.11 Drilling down into Nessus results.](img/11fig11.jpg)

Figure 11.11 Drilling down into Nessus results.

然后你可以对任何个项目进行深入探讨。如果你双击任何个项目，你可以获取关于该项目的详细信息以及如何修正它们。

### OWASP Zap

开放网站安全项目 (OWASP)是Web应用安全的标准。OWASP提供一个免费漏洞扫描工具——Zed Attack Proxy，通常称为OWASP ZAP。你可以从 [`github.com/zaproxy/zaproxy/wiki/Downloads`](https://github.com/zaproxy/zaproxy/wiki/Downloads) 下载它。界面如图 11.12所示很简单易用。

![Figure 11.12 OWASP ZAP main screen.](img/11fig12.jpg)

Figure 11.12 OWASP ZAP main screen.

只需在你想要扫描的网站的URL中输入并点击 **Attack**。几秒后，结果将在屏幕底部显示。然后你可以扩展任何项目。如果你点击特定项目，详细信息会加载如图 11.13所示。

![Figure 11.13 OWASP ZAP results.](img/11fig13.jpg)

图 11.13 OWASP ZAP 结果。

OWASP ZAP 是一个非常易用的工具。基础功能可以在几分钟内掌握。而且，鉴于 OWASP 是跟踪 Web 应用程序漏洞的组织，它是测试网站漏洞的非常好的来源。

## Shodan

该工具被黑帽黑客和安全专业人士所广泛使用。网站 [`www.shodan.io`](https://www.shodan.io) 实质上是一个漏洞搜索引擎。你需要注册免费账号才能使用它，但随后它对渗透测试人员来说可以是无价的，帮助他们识别漏洞。当然，该站点对攻击者同样有价值。你可以在 图 11.14 查看该网站。

![图 11.14 Shodan.io.](img/11fig14.jpg)

图 11.14 Shodan.io.

Shodan 允许你使用多种选项进行搜索，包括以下内容：

*   搜索默认密码，使用如下搜索词：

    *   default password country:US

    *   default password hostname:chuckeasttom.com

    *   default password city:Chicago

*   查找 Apache 服务器，使用如下搜索词：

    *   apache city: “San Francisco”

*   查找网络摄像头，使用如下搜索词：

    *   webcamxp city:Chicago

*   查找旧 IIS，使用如下搜索词：

    *   “iis/5.0”

通过 Shodan，你可以使用多种过滤器，包括以下内容：

*   `city:` 查找特定城市的设备。

*   `country:` 查找特定国家的设备。

*   `geo:` 指定坐标（如纬度和经度）。

*   `hostname:` 查找匹配特定主机名的值。

*   `net:` 基于 IP 地址或 /x CIDR 地址进行搜索。

*   `os:` 基于操作系统进行搜索。

*   `port:` 查找特定开放端口。

*   `before/after:` 在指定时间范围内查找结果。

例如，图 11.15 展示了搜索 **default password city:Miami** 的结果。

![图 11.15 Shodan 搜索结果。](img/11fig15.jpg)

图 11.15 Shodan 搜索结果。

在进行渗透测试时，建议在 Shodan 上搜索你的公司域名，以获取指导渗透测试的信息。当然，潜在攻击者也可以使用 Shodan 获取相同信息。你可以将搜索限制在已聘请你进行渗透测试的客户的主机名或域名。你可以使用 Shodan 寻找目标网络中的默认密码、旧网络服务器、未受保护的网络摄像头以及其他漏洞。

如图 11.15 所示的搜索是使用 Shodan 的免费版本进行的。最近，Shodan 开始提供付费版本，价格为 49 美元，并提供额外工具。此外，还有企业会员，价格更高。

### 获得专业帮助

你可能会决定需要外部帮助来设置和测试系统的安全性。这一选项是安全专业人士强烈推荐的，尤其是如果你对安全一无所知的话。请聘请专业顾问协助你制定初始安全策略和政策，并可能定期审计你的安全。正如在 第 1 章 “计算机安全入门”中提到的，有许多人声称自己是黑客，但实际上并非如此。坦率地说，也有许多自称安全专家的人并没有必要的技能。关键问题是：如何判断一个人是否具备资质？以下是一些需要考虑的指南。

经验是寻找安全专业人士时最重要的因素。你希望找到至少有 5 年 IT 经验，其中 2 年与安全相关的经验。通常，这可能是一名网络管理员或程序员，他们转向安全领域。请注意，这只是最低经验要求。经验越多越好。当然，经验较少的人可能具备所需技能，但这种情况较少见。每个人都需要一个起点，但你不希望你的系统成为别人学习的场所。

经验的质量与长度同样重要。询问此人的经验细节。例如，她在计算机安全方面具体担任了什么角色？她是仅仅设置政策，还是实际进行动手安全工作？结果如何？她的系统是否免受病毒感染和黑客入侵？你能联系她的推荐人吗？简而言之，仅凭简历上声称她负责信息安全是不够的。你需要了解她具体做了什么以及取得了什么结果。

安全专业人士的素质也是重要考量因素。记住，计算机安全是一个非常广泛的领域。你需要了解网络、协议、编程等方面的知识。虽然没有正式教育也可能具备这些技能，但拥有正式教育的可能性更大。通常，这些技能更可能在拥有经验且在计算机或数学相关领域拥有学位的人身上发现。这听起来可能有些学术上高高在上，但这是事实。IT 行业有许多自学成才的人，例如拥有历史学位的网络管理员或心理学专业人员转行为程序员。然而，一个人越专注于多个领域，越难获得精通。这并不意味着没有计算机科学、数学或工程学位的人不能成为安全专业人士。重点是，这是一个需要考虑的因素。如果某人拥有无关学位但满足或超过其他所有资质，你仍可能考虑他。一些学院开始提供安全专业课程，甚至提供安全学位。显然，具体的计算机安全培训是最理想的安全背景。

认证在 IT 职业中备受争议。有些人坚信它们。你可以轻易在许多招聘广告中看到要求特定认证的要求，例如 CNE（Certified Novell Engineer）或 MCITP（Microsoft Certified Information Technology Professional）。Cisco 认证也很常见（Cisco Certified Network Associate 到 Cisco Certified Internetworking Engineer）。另一方面，你会发现一些 IT 专业人士批评认证，认为它们完全无用。这种立场的来源是有些持有认证的人并没有你期望的技能。但这适用于任何证书。例如，有些医学博士可能能力不足。但如果你需要医疗帮助，你的机会会大幅提高，如果你咨询一位拥有医学学位的人。雇主通常采取类似的招聘方式。如果他们只面试拥有特定学位或认证的人，那么他们更有可能面试到合格的候选人。

一种更合理的位置介于两个极端之间。认证可以是候选人对特定产品知识的良好指示。例如，如果您希望有人保障您的 Microsoft 网络安全，查看持有 Microsoft 认证的人员并不是一个坏主意。然而，您需要平衡这一点，记住完全有可能凭借良好的记忆使用互联网上提供的各种学习指南来通过他们并不真正理解的考试。而这正是经验的作用所在。认证加上适当的经验是技能的良好指示。换句话说，认证本身是不够的。但一个或多个认证与经验以及相关学位的组合可以是技术技能的强有力指示。

除了网络管理员的认证外，还有许多与安全相关的认证。有些比其他更有可信度。CompTIA 的 Security+ 考试和 CIW Security Analyst 都是概念性考试。这意味着它们考察候选人的安全概念知识，而不是他们实际实施安全解决方案的能力。单凭这些认证可能不足以表明您需要的技能水平。但例如，如果您正在使用 Novell 进行网络安全，那么一个拥有 CNE 认证且具备 CIW Security Analyst 或 Security+ 认证的候选人可能是值得考虑的人选。需要注意的是，CompTIA 最近新增了 Certified Advanced Security Practitioner (CASP)，该认证面向拥有 10 年安全经验的从业者。


**A、B、D。** 当涉及持卡人数据 (CHD) 时，PCI-DSS 关注 PII，并涉及对持卡数据环境安全性的测试，且受行业监管。

**B、C、E。** GDPR 是一项欧盟法规，涉及欧盟居民的隐私权。它将 PII 作为其中一部分加以涵盖，并由政府强制执行。

### 问题 3

**D.** 采取任何进一步行动都可能污染客户为潜在法律诉讼而必须收集的数字证据。

### 问题 4

**A.** 从尽可能窄的范围开始。

### 问题 5

**C.** NDA 定义了保密条款，包括信息何时以及如何可以共享和披露。

**A、E.** SOW 定义了要完成的工作活动、交付物的时间安排以及适用的验收标准。

**B、D.** MSA 定义了赔偿条款及业务关系的其他要素，包括争议解决流程。

**G、H.** RoE 阐明了 SOW 中的项目，如允许的测试、目标以及通信计划的细节。

**F.** 测试授权提供了你被授权进行测试的证明。

### 问题 6

**B.** MITRE ATT&CK 是一个由包含战术、技术和子技术的矩阵所引用的框架。

**F.** OWASP Top Ten 与枚举 Web 应用攻击相关联。

**D.** NIST 标准常被美国政府采用。

**G.** PTES 专注于渗透测试，由社区驱动的标准组成。它自由地引入其他框架和技术指南作为补充资源。

**C、E.** OSSTMM 通过 ISECOM 提供认证选项，且 OSSTMM 提供了一种衡量和报告风险值（渗透测试指标）的方法论。

**A.** ISSAF 虽然设计用于安全评估而非渗透测试，但包含最佳实践，并列出了每个测试任务及其相关工具。

### 参考资料

1.  CREST：<https://www.crest-approved.org/>

2.  GDPR：<https://gdpr.eu/tag/gdpr/>

3.  个人数据：<https://ico.org.uk/for-organisations/guide-to-data-protection/guide-to-the-general-data-protection-regulation-gdpr/key-definitions/what-is-personal-data/>

4.  <https://www.legislation.gov.uk/eur/2016/679/article/32>

5.  PCI-SSC：<https://www.pcisecuritystandards.org>

6.  PCI-DSS v. 3.2.1：<https://www.pcisecuritystandards.org/documents/PCI_DSS_v3-2-1.pdf>

7.  PCI-DSS 信息补充：渗透测试指南：<https://www.pcisecuritystandards.org/documents/Penetration-Testing-Guidance-v1_1.pdf>

8.  PCI 敏感认证数据：<https://www.pcisecuritystandards.org/pci_security/glossary#S>

9.  攻击者仿真计划：<https://attack.mitre.org/resources/adversary-emulation-plans/>

10. NIST SP800-115 "Technical Guide to Information Security Testing and Assessment"：<https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-115.pdf>

11. NIST 网络安全框架：<https://www.nist.gov/cyberframework>

12. ISECOM 开源安全测试方法论手册 (OSTMM)：<https://www.isecom.org/research.html>

13. 社会责任计算机专业人士协会。计算机伦理十诫，由计算机伦理研究所编写：<http://cpsr.org/issues/ethics/cei/>

## 第 2 章：信息收集与漏洞扫描

在本章中，你将了解：

*   被动侦察与主动侦察及漏洞扫描的区别，包括目标信息的类型
*   用于信息收集和漏洞扫描的多种工具及其输出分析
*   在渗透测试期间何时使用被动侦察、主动侦察或漏洞扫描
*   识别并分析 Nmap 的使用场景

尽可能多地收集有关目标的信息被称为侦察，或发现。渗透测试人员在渗透测试的规划、初始访问和后利用阶段执行此操作。侦察用于识别或确认目标范围，发现潜在弱点或漏洞以供利用，并定位与渗透测试目标相关的其他信息。

根据评估类型，大量范围界定信息可能已提供，例如 IP 地址、电子邮件地址、域名等。但是，确认 IP 范围或应用程序的所有权（例如）可能是个好主意。你可能还会识别目标上的开放服务或系统版本，以识别可利用的漏洞。你可以在 Web 服务器上查找各种 Web URL，以发现值得进一步检查的登录表单或管理界面。你的目标是找到有助于推进渗透测试目标的信息。填补知识空白并建立对可用目标的理解将帮助你更有效地管理时间并制定可行的攻击计划。

以下是你可能以此为目标的其他信息示例，我们将在本章中讨论：网站（如登录表单或暴露的管理界面）、用户账户和电子邮件地址、证书数据、网络范围内有哪些系统在线、业务合作伙伴关系、开放服务、操作系统和软件版本、托管提供商和域名服务信息、内部文档模板、组织信息（如职位角色、策略、术语或正在使用的技术），甚至预期的防御类型。在后利用阶段，你收集的信息可能更深入地延伸到组、共享和令牌枚举。

所有这些活动通常可分为三类攻击：被动侦察、主动侦察和漏洞扫描。针对 CompTIA Pentest+ 考试，你应该牢固掌握这些类别之间的区别、何时使用它们、哪些工具将协助你完成每项任务，以及如何识别和分析某些工具的结果。

### 被动侦察

假设你需要雇人修理家里的东西。但在你更多地了解他们之前，你不想给他们钱，也不想让他们进你的家。这个人或企业有犯罪记录吗？他们干活靠谱吗？你可能会决定询问过去与该个人有过业务往来的朋友，或通过商业局调查他们。你可以在社交媒体服务上查找他们的评价。你可能会决定要求进行犯罪背景调查——所有这些都无需直接与潜在承包商接触。

在渗透测试中，这就是被动信息收集。它是评估目标以收集关于系统、软件、网络和人员的初步知识的过程，*无需主动接触目标或其资产*。这种形式的信息收集侵入性最小，也最不可能被目标发现。在渗透测试中，使用这些方法来验证范围并协助规划，以及在渗透测试期间进行初步发现是恰当的。根据你的预算和资源，可以使用付费和公开的信息来源（开源情报）。当你在渗透测试的当前阶段不能冒险造成干扰或被发现时，请使用被动信息收集。

### DNS 侦察

除其他用例外，你可以使用 **DNS 侦察** 来扩展你对正在使用的主机名、网络广度，甚至组织内部某些技术联系人信息的了解。DNS 侦察可以是被动的，也可以是主动的，这取决于你是否直接访问目标的系统（主动）或不直接访问。大多数测试人员认为，对 DNS 服务器的大量请求意味着目标不会监控对 DNS 服务的查询，但情况并非总是如此。辅助来源，如域名注册商、互联网注册机构、专业搜索引擎或其他基于 Web 的资源，允许在该领域进行纯粹的被动信息收集。

让我们先谈谈 IP 范围。有五个区域互联网注册机构（RIR）负责处理整个互联网上的 IP 地址分配：APNIC（亚洲）、ARIN（美洲）、RIPE NCC（欧洲）、LACNIC（拉丁美洲）和 AFRINIC（非洲）。其理念是防止两方被分配相同的地址范围以供使用。这些注册机构包含有关哪个组织拥有特定 IP 地址范围的信息，有时还包括技术和管理联系人的信息。正如你在图 2-1 中所见，你可以搜索联系点（POC）、网络或 ASN，或组织或客户名称。

![Images](img/F02-01.jpg)

**图 2-1** ARIN 高级搜索 ([`whois.arin.net/ui/advanced.jsp`](https://whois.arin.net/ui/advanced.jsp))

此信息还通过 WHOIS 服务与域名注册条目相关联。假设我们通过选择 POC 并勾选 Domain 来根据域名注册记录进行搜索，并输入 `comptia.org` 来查找域名，以此搜索 CompTIA。这将返回根据 RIR 负责该域名的人员姓名。对于返回的每个姓名，你可以点击获取更多详细信息，包括邮寄地址、电子邮件地址、电话号码，甚至相关组织。然后你可以利用这些信息搜索社交媒体或其他开源信息，用于社会工程学。如果我们点击“相关组织”，我们将获得一份用于滥用处理、技术和管理目的的组织列表。点击组织名称右侧的链接，你将看到“另请参阅相关网络”的链接，如图 2-2 所示。这是该组织拥有的 IP 地址列表。

![Images](img/F02-02.jpg)

**图 2-2** ARIN 组织相关网络

你也可以通过在 ARIN 中搜索特定 IP 地址来验证范围列表中 IP 的所有权。在页面右上角的搜索对话框中输入 IP 地址，你将获得该 IP 所属的网络范围以及所有权记录。这在识别云和第三方托管资产时很有用。我们稍后会回到这一点。

还有其他方法可以从 DNS 访问信息，例如使用 `dig` 或 `whois` 命令行工具来调查域名所有权。`whois` 命令在大多数 Linux 发行版中均可用，它允许你使用域名检索有关系统的信息。图 2-3 是使用 `whois` 命令查询 [example.com](http://example.com) 的示例命令输出。

![Images](img/F02-03.jpg)

**图 2-3** WHOIS

输出可以提供有用的信息，有助于识别域名创建日期、最后更新时间、将公司和业务位置与域名关联、DNSSEC 信息，以及在某些情况下，注册商的联系信息。当你看到单个主机名返回多个 IP 地址时，如图 2-4 中的 `nslookup` 命令所示，这可能表明正在使用负载均衡。这是高流量环境中的常见配置。我们将在本章后面更深入地讨论这一点。使用像 `nslookup` 这样的工具将域名解析为 IP 地址称为正向 DNS 查找。反向 DNS 查找则相反——此过程将 IP 地址解析为域名。

![Images](img/F02-04.jpg)

**图 2-4** nslookup

现在，回到我们的云资产发现。假设你已经识别出一堆属于某公司的服务器。你使用 `nslookup` 查找它们的 IP 地址。然后你在 RIR 中查找这些 IP 地址，发现这些 IP 范围并不属于相关公司。相反，这些 IP 地址位于属于微软、亚马逊或其他托管提供商的网段中。你对这些资产进行渗透测试的方法可能会根据它们的托管位置而有所不同。云提供商通常会发布其云托管范围，例如 Azure 的 [`www.microsoft.com/en-us/download/details.aspx?id=56519`](https://www.microsoft.com/en-us/download/details.aspx?id=56519) 或 AWS 的 [`ip-ranges.amazonaws.com/ip-ranges.json`](https://ip-ranges.amazonaws.com/ip-ranges.json)，而 RIR 将揭示给定 IP 范围所有权的其他信息，这在你的研究期间可能很有用。

你也可以使用 DNS 中的 MX 记录来识别正在使用的云服务。使用 `nslookup`，你可以将记录类型设置为 MX 以识别邮件服务器。查找像 [google.com](http://google.com)、[googlemail.com](http://googlemail.com)、[outlook.com](http://outlook.com) 等条目，以指示基于云的电子邮件。这是一个使用 `dig` 和谷歌名称服务器获取关于 comptia.org 信息的示例：

![Images](img/f0039-01.jpg)

![Images](img/exam.jpg)

> **考试提示**  
> 了解不同类型的 DNS 记录及其包含的信息很有用，因为你可能会被问到特定的记录类型。请特别注意 NS、TXT、CNAME 和 A 记录。这里不再一一列举，你可以在 [`www.iana.org/assignments/dns-parameters/dns-parameters.xhtml#dns-parameters-4`](https://www.iana.org/assignments/dns-parameters/dns-parameters.xhtml#dns-parameters-4) 阅读更多内容。

#### Recon-ng

如果你想要一个框架来帮助进行此类搜索，Recon-ng 是一个强大的侦察框架。它是用 Python 编写的，如果你曾经使用过 Metasploit，你会发现它的界面很熟悉。它包含独立的模块、一个用于存储项目信息的数据库，以及更多功能。你可以提供一个域名，让 Recon-ng 识别该域名上的 IP 地址和主机名，并使用 OSINT 资源搜索与该域名相关的电子邮件地址、联系人和泄露信息。Recon-ng 是开源的，并包含在 Kali 的安装中。从 Kali 启动一个终端窗口，并按照此处的步骤开始使用 Recon-ng：

##### 1. 执行 Recon-ng

该工具通过在命令行输入 `recon-ng` 来执行。要获取命令列表，请在框架提示符下执行 `help`。

##### 2. 安装模块

默认情况下，Kali 中的 Recon-ng 未安装任何模块。要安装它们，可能需要在 Recon-ng 提示符下输入 `marketplace install all`。完成此操作后，启动屏幕将显示每个类别支持的模块总数。Recon-ng 模块类别如下：

*   **Recon modules**：侦察模块。
*   **Disabled modules**：根据系统配置禁用的模块。如果没有禁用的模块，此项可能不会显示。
*   **Reporting modules**：以各种格式编译报告。
*   **Import modules**：使用支持的格式导入目标列表。
*   **Exploitation modules**：支持的利用模块。
*   **Discovery modules**：信息发现模块。

##### 3. 搜索模块

要获取支持的模块列表，请在框架提示符下不带参数执行 `modules search`。

##### 4. 创建工作区

首先要做的是创建一个工作区来管理信息收集。工作区和模块执行期间收集的信息将存储在数据库中。

![Images](img/f0040-01.jpg)

##### 5. 查看工作区

要查看数据库中的工作区列表，请执行：

![Images](img/f0040-02.jpg)

![Images](img/exam.jpg)

> **考试提示**  
> Black Hills Information Security 托管了一份 Recon-ng 备忘单，包含许多有用的命令：[`www.blackhillsinfosec.com/wp-content/uploads/2019/11/recon-ng-5.x-cheat-sheet-Sheet1-1.pdf`](https://www.blackhillsinfosec.com/wp-content/uploads/2019/11/recon-ng-5.x-cheat-sheet-Sheet1-1.pdf)

##### 6. 加载 WHOIS 模块

要运行简单的 WHOIS 查询并提取域的联系信息，请加载 `whois_pocs` 模块：

```
[recon-ng][example] > modules load whois_pocs
```

##### 7. 配置模块选项

模块加载后，可以通过输入 `info` 查看有关该模块的更多信息，包括可配置参数。在模块加载时输入 `options` 也可以显示当前上下文变量，并允许设置值。在这种情况下，设置搜索目标：

```
[recon-ng][example][whois_pocs] > options set SOURCE comptia.org
```

##### 8. 执行模块

当然，你需要设置一个真实的目标。这里仅作为示例。当你使用 `run` 命令执行模块时，发现过程可能需要几分钟，因为网络速度各异。但图 2-5 显示了运行时可能看到的示例。

![Images](img/F02-05.jpg)

**图 2-5** Recon-ng 模块执行

##### 9. 显示结果

收集过程完成后，可以使用 `show <table name>` 命令显示存储在数据库中选定表内的结果。要获取所有表的列表，请不带参数输入 `show`。

##### 10. 查看联系人

`whois_pocs` 模块填充 Contacts 表。要获取已收集的联系人列表，请执行 `show contacts`。

##### 11. 仪表盘

Recon-ng 仪表盘（图 2-6）显示数据库中每个表存储的记录总数。要显示仪表盘，请执行 `dashboard` 命令。这些指标提供了关于目标环境和组织面向公共互联网暴露面的宝贵信息。

![Images](img/F02-06.jpg)

**图 2-6** Recon-ng 仪表盘

![Images](img/caution.jpg)

> **注意**  
> 某些 Recon-ng 模块需要 API 密钥。请遵循开发者网站使用指南中“获取 API 密钥”下的说明：[`github.com/lanmaster53/recon-ng`](https://github.com/lanmaster53/recon-ng)。

#### theHarvester

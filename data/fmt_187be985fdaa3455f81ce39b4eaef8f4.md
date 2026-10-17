
## 5. 虹膜识别

虹膜识别匹配用户眼后的血管。

## 6. Voice Recognition

语音识别系统通过语音分析确定你的身份。

## 7. Keyboard Dynamics

键盘动力学分析用户的打字速度和模式。

任何生物识别系统的最终考量因素是用户接受度和易用性。系统的可接受性取决于用户如何看待它。例如，虹膜扫描被认为比视网膜扫描更准确。这是因为视网膜可能会因糖尿病和怀孕等状况随时间发生变化。视网膜扫描对用户来说也更具侵入性，因此使用频率较低。用户教育很有帮助，因为许多人担心视网膜或虹膜系统会损害他们的眼睛，或者他们的信息得不到充分保护。

为确保生物识别系统可用，必须检查处理时间和环境。生物识别中一个不常被讨论的方面是生物识别数据管理和退役。生物识别数据需要进入系统数据库，即使采用专有数据库格式，存储人们的生物识别数据也存在额外风险。随着更多生物识别系统的推出，这种风险将在未来增加。生物识别系统也需要安全退役，以确保个人的生物识别信息永不泄露。

管理大量密码的另一种方法是单点登录。单点登录（`SSO`）旨在通过允许用户向单一认证机构进行一次认证，随后无需重新认证即可访问其他受保护资源，来解决这一问题。一种备受关注的单点登录形式是由美国商务部支持的版本，称为网络空间可信身份国家战略（`NSTIC`）。该提案规定了一种单点登录，每次计算机或手机开机时都会使用，采用数字令牌、智能卡或指纹阅读器等设备。有人认为此计划可能具有侵入性，而另一些人则将其视为消除当今密码诸多问题的手段。练习 8.3 演示了密码认证的弱点。

## Technology Evolution (RFCs, ISO)

你是否想过谁在管理互联网？有几个机构负责此事。首先是互联网协会（`ISOC`）。`ISOC` 负责互联网技术标准，并充当互联网信息和教育的全球交换中心。向 `ISOC` 汇报的实体包括互联网架构委员会（`IAB`）、互联网工程指导组（`IESG`）、互联网工程任务组（`IETF`）、互联网研究指导组（`IRSG`）、互联网研究任务组（`IRTF`）和征求意见稿（`RFC`）小组。

`IAB` 负责协议和标准，并管理 `IETF`。`IETF` 的职责是监督创建指导互联网如何设计、使用和管理的技术文档。这项使命的很大一部分集中在创建 `RFC` 上，`RFC` 作为互联网的“行为准则”白皮书。`RFC` 描述了互联网技术实践的方法、行为、研究和创新。创建 `RFC` 时，会分配一个永不改变的编号。发布新技术时，会先创建一个互联网草案作为新 `RFC`，然后将其最终确定为 `RFC`。此时，旧的 `RFC` 可能会变得过时。此流程不同于 `ISO` 等其他组织。一些知名的 `RFC` 及其标题如表 8.1 所示。

**表 8.1** 常见 RFC

| RFC | Description |
| --- | --- |
| RFC 821 | Simple Mail Transfer Protocol |
| RFC 2119 | Key Words for Use in RFCs to Indicate Requirement Levels |
| RFC 2396 | Uniform Resource Identifiers (URI): Generic Syntax |
| RFC 793 | Transmission Control Protocol |
| RFC 1123 | Requirements for Internet Hosts – Application and Support |
| RFC 1034 | Domain Names – Concepts and Facilities |
| RFC 2616 | Hypertext Transfer Protocol – HTTP/1.1 |
| RFC 2045 | Multipurpose Internet Mail Extensions (MIME) Part One: Format of Internet Message Bodies |
| RFC 1918 | Address Allocation for Private Internets |
| RFC 822 | Standard for the Format of ARPA Internet Text Messages |
| RFC 1521 | MIME (Multipurpose Internet Mail Extensions) Part One: Mechanisms for Specifying and Describing the Format of Internet Message Bodies |
| RFC 1766 | Tags for the Identification of Languages |
| RFC 2068 | Hypertext Transfer Protocol – HTTP/1.1 |
| RFC 1700 | Assigned Numbers |
| RFC 1591 | Domain Name System Structure and Delegation |
| RFC 1157 | Simple Network Management Protocol (SNMP) |
| RFC 1866 | Hypertext Markup Language – 2.0 |
| RFC 1945 | Hypertext Transfer Protocol – HTTP/1.0 |
| RFC 977 | Network News Transfer Protocol |
| RFC 791 | Internet Protocol |
| RFC 1661 | Point-to-Point Protocol (PPP) |
| RFC 959 | File Transfer Protocol |
| RFC 1035 | Domain Names – Implementation and Specification |
| RFC 2131 | Dynamic Host Configuration Protocol |
| RFC 768 | User Datagram Protocol |
| RFC 2543 | SIP: Session Initiation Protocol |
| RFC 3261 | SIP: Session Initiation Protocol |
| RFC 792 | Internet Control Message Protocol |
| RFC 2571 | An Architecture for Describing SNMP Management Frameworks |
| RFC 2573 | SNMP Applications |
| RFC 1510 | The Kerberos Network Authentication Service (V5) |
| RFC 1459 | Internet Relay Chat Protocol |

国际标准化组织（`ISO`）将自己描述为“由 162 个国家标准机构组成的网络，每国一名成员，中央秘书处设在瑞士日内瓦，协调连接公共和私营部门的体系”。

`CASP` 应了解几份 `ISO` 文档。其中之一是 `ISO 15408`。`ISO 15408` 经过多年的起草于 1997 年首次发布，当前为 3.1 版，更广为人知的名称是通用准则。通用准则旨在为表达产品和系统 IT 安全需求提供通用结构和语言。它是供应商描述其产品能力以及买家测试此类产品以确保其满足特定需求的一种方式。通用准则文档的一大成就是弥合了早期文档（如 `ITSEC` 和 `TCSEC`）之间的差距。通用准则保证了计算机安全产品的规范、实现和评估过程已以严格且标准的方式进行。因此，通用准则可在全球范围内使用，并对更广泛的受众具有意义。表 8.2 给出了通用准则评估保证级别（`EAL`）的一些示例。

**表 8.2** 通用准则

| Level | Definition |
| --- | --- |
| EAL 0 | Inadequate Assurance |
| EAL 1 | Functionality Tested |
| EAL 2 | Structurally Tested |
| EAL 3 | Methodically Checked and Tested |
| EAL 4 | Methodically Designed, Tested, and Reviewed |
| EAL 5 | Semi-formally Designed and Tested |
| EAL 6 | Semi-formally Verified, Designed, and Tested |
| EAL 7 | Formally Verified, Designed, and Tested |

另一份值得审查的 `ISO` 文档是 `ISO 27002`。该标准被视为信息安全管理的最佳实践守则。它源自 `ISO 17799` 和英国标准 7799。`ISO 27002` 被视为管理指南，而非技术文档。您可以在 `www.27000.org/iso-27002.htm` 了解更多信息。`ISO 27702` 为负责领导、规划、实施或维护安全的人员提供了关于信息安全管理的最佳实践建议。`ISO 27702` 标准包含以下 12 个部分：

1. 风险评估 如何评估组织风险
2. **安全策略** 管理方向和架构
3. **信息安全组织** 信息安全治理
4. **资产管理** 信息资产的清单与分类
5. 人力资源安全 员工入职、调动和离职的安全方面
6. 物理和环境安全 计算机设施的保护
7. 通信和运营管理 系统和网络中技术安全控制的管理
8. 访问控制 对网络、系统、应用程序、功能和数据的访问权限限制
9. 信息系统获取、开发和维护 通过系统开发生命周期（`SDLC`）和标准化流程将安全构建到应用程序中
10. 信息安全事件管理 通过开发事件响应程序和流程，预测并适当响应信息安全漏洞
11. 业务连续性管理 保护、维护和恢复关键业务流程和系统
12. 合规性 确保符合信息安全策略、标准、法律和法规

## 态势感知

态势感知要求您了解周围发生的事情，以理解如何应对特定情况。如今，安全专业人员比以往任何时候都更需要了解时事。IT 安全的定义及其涉及的内容随着技术进步而不断演变。今天，我们对网络、计算机和技术的依赖程度远超过去。这给许多人的日常生活带来了巨大进步，但也使计算机犯罪和网络攻击的威胁更加迫在眉睫。问题的规模令人震惊。根据 `www.fas.org/sgp/crs/misc/R40599.pdf` 上的国会研究服务报告，美国联邦调查局（`FBI`）估计，仅在一年内，多达 1000 万美国人将成为身份盗窃的受害者。尽管消息来源对威胁程度的看法不一，但计算机犯罪以不断增长的速度增加这一趋势是毋庸置疑的。态势感知要求 `CASP` 跟上最新的客户端攻击、攻击向量、新兴威胁和零日攻击。

### 最新客户端攻击

Web 服务器曾是攻击者的主要目标，但这已不再成立。如今，客户端攻击更为突出。原因之一是客户端系统是一个目标丰富的环境。客户端可能正在运行 `Flash`、`Office`、`Acrobat`、`iTunes`、`Firefox`、`Java` 等。这些程序中的每一个都为攻击者提供了潜在目标。与互联网相关的交互性也强得多。这为攻击者提供了针对基于 Web 的应用程序的选项。最后一个原因是，如今可用的工具比过去多得多。如今，工具使用起来容易得多，且广泛可用。许多基于 Web 的客户端攻击在本质上是技术性的，但也利用了社会工程学。这些技术可用于诱使受害者点击链接或访问恶意网页。当受害者访问该网页时，攻击者执行恶意代码，利用应用程序中存在的漏洞。客户端攻击的示例包括以下内容：

1. Cookie 窃取或篡改

Cookie 用于维护状态，跟踪用户在网站页面间的移动，以及跨多个请求/响应周期跟踪用户。问题在于 Cookie 可能包含对黑客有吸引力的敏感信息。某些 Cookie 存放用于身份验证的用户名、密码或其他数据。如果 Cookie 存有用于识别客户端的数据，攻击者即可利用其劫持会话或冒充客户端。许多 Web 2.0 网站（如 `Reddit`、`LinkedIn` 和 `Digg`）使用 Cookie 在稍后识别用户，这样用户每次访问账户时就无需提供凭据。从态势感知的角度来看，用户需要明白，如果没有加密，他们的 Cookie 很容易被窃取。`Cookie Cadger`、`Session Thief` 和 `Firesheep` 等工具都被用来演示窃取这些 Cookie 的容易程度。图 8.6 显示了 `Firesheep` 用于捕获 `Facebook` Cookie 的 `JavaScript` 代码，练习 8.4 演示了如何进行 `Cookie Cadger` 的基本安装。

核心漏洞在于，虽然大多数网站对登录过程进行加密，但后续请求在明文 URL 中包含用户的 Cookie。该信息未加密。如果网站对整个用户会话进行加密，就不会存在此风险。那么为什么网站不加密呢？一个原因可能是加密流量会给运营网站的公司带来更大的运营负担。对于大流量网站，它们需要昂贵的硬件来加速加密过程。另一个原因可能是加密也会使合法执法机构的合法拦截请求变得复杂。使用 `Cookie Cadger` 捕获 `LinkedIn` 和其他凭据是一种简单的方法。您需要 `winzip`、`Wireshark` 和 `Java` 才能使该程序运行。

**跨站脚本攻击（`XSS`）** `XSS` 攻击是一种针对动态生成网页的注入攻击，恶意脚本被注入到原本良性且受信任的 Web 内容中。`XSS` 允许攻击者在毫无戒心的用户访问恶意网页时强制加载任何网站。这使攻击者能够窃取输入 `HTML` 表单的用户名和密码或 Cookie，或泄露屏幕上的任何机密信息。态势感知要求用户在点击电子邮件中的链接或可疑网站时保持谨慎。`CASP` 考试将要求您能够识别 `XSS` 攻击。以下是一个非持久性 `XSS` 攻击的示例：

```
index.php?name=guest<script>alert('hacked')</script>
```

**跨站请求伪造（`CSRF`）** `CSRF` 是另一种客户端攻击，当恶意网站诱骗用户在不知情的情况下从其已通过身份验证的网站加载 `URL` 时发生，从而利用其已验证的状态。练习 8.5 演示了此类攻击的严重性。

1. SQL 注入

攻击者搜索并利用易受 SQL 注入影响的数据库。`SQL 注入` 是指攻击者能够通过 `SQL 注入` 漏洞将 `SQL` 语句插入查询中。`SQL 注入` 允许攻击者利用系统上的不安全代码直接向数据库传递命令。这赋予了攻击者利用其访问权限执行各种活动的能力。许多 `SQL 注入` 攻击以信用卡信息或其他敏感信息为目标。`CASP` 应了解此威胁，并致力于确保公司网站已针对该漏洞进行加固。

#### 缓冲区溢出

当程序或进程试图在缓冲区中存储超过其设计容量的数据时，就会发生`缓冲区溢出`。可以把它想象成有一个 8 盎司的杯子，却试图倒入 12 盎司的咖啡。它装不下所有咖啡。这会迫使部分咖啡溢出并洒出杯外。当缓冲区的大小未经过验证时，就会发生缓冲区溢出；这可能导致写入已分配缓冲区之外的区域。这可能会导致段错误或错误。如果攻击者清楚自己在做什么，他们可以尝试将其数据加载到栈上，并强制返回指针加载他们的代码。在这种情况下，攻击者能够在受害者的计算机上加载他们的代码。在 C 语言中，某些函数（包括 `strcpy`、`gets`、`scanf`、`sprintf` 和 `strcat`）是脆弱的。`CASP` 应该理解，在使用了 C 语言的情况下，如果可能的话，应检查代码中的脆弱函数。如果您想了解更多信息，请查看 Aleph One 的“Smashing the Stack for Fun and Profit”，网址为 `http://insecure.org/stf/smashstack.html`。

![图 8.6 Firesheep 用于捕获 Cookie 的 Facebook.js](img/c08f006.jpg)

**图 8.6** Firesheep 用于捕获 Cookie 的 Facebook.js

`CASP` 可以采取一些措施来帮助预防这些问题并降低这些风险。打补丁至关重要。始终确保计算机和应用程序已打补丁。实施出站过滤和使用 Web 应用防火墙也有帮助。这两种技术可以通过过滤传入的恶意内容，帮助防止与恶意网站的出站连接。另一个非常重要的项目是入侵检测。它关乎监控和识别可疑网络活动的能力。您还需要审查并调整端点安全控制，以确保它们能够识别恶意和可疑活动。最后，虽然不属于技术范畴，但员工教育至关重要，因为它有助于培训员工了解当前的攻击趋势，以及如果他们怀疑自己是攻击受害者时应遵循的程序。

## 当前漏洞和威胁的知识

正如本书前面所讨论的，威胁可以被描述为任何可能危及安全的行为或事件。组织面临的一些常见威胁如下：

1.  **垃圾邮件**

利用任何电子通信媒介批量发送未经请求的消息。垃圾邮件是互联网时代的一大烦恼。尽管垃圾邮件仍然是一个大问题，但执法部门和其他人正在寻找独特的方法来针对从垃圾邮件中获利的个人。`CASP` 需要意识到，如果攻击者能将您的公司用作垃圾邮件中继，可能会导致公司的 IP 地址被列入黑名单。结果是电子邮件可能无法投递给客户和业务合作伙伴。垃圾邮件还带来了一个问题，即其中大部分是恶意的。`CASP` 可能不得不花费更多时间清理计算机和重建硬盘驱动器。最好的方法是在内容到达最终用户之前对其进行过滤。一种减缓垃圾邮件提供商速度的方法是针对处理垃圾邮件提供商付款的银行。这种新颖的方法针对垃圾邮件的商业模式和参与者，它不是一种通过过滤器技术性地防止垃圾邮件的解决方案。追查支付处理商是分析整个攻击者活动链并通过整体方法发现攻击者活动弱点的一个绝佳例子。要了解有关此方法的更多信息，请查看 `www.wired.com/beyond_the_beyond/2011/06/spam-banks/`。

2.  **网络钓鱼**

这是一种犯罪性的欺诈过程，通过在电子通信中伪装成值得信任的实体，试图获取用户名、密码和信用卡详细信息等敏感信息。与之密切相关的是定向网络钓鱼，它针对特定个人或特定信息子集。通过为员工提供培训，可以减少这两种威胁。最终用户必须被教导在共享敏感信息时保持谨慎。

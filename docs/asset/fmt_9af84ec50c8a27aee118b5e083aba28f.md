
Performing session hijacking can be rather complex. For that reason, it is not a very common form of attack. Simply put, the attacker monitors an authenticated session between the client machine and the server and takes over that session. We will explore specific methods of how this is done later in this book.

A 1985 paper written by Robert T. Morris, titled “A Weakness in the 4.2BSD Unix TCP/IP Software,” defined the original session hijacking. By predicting the initial sequence number, Morris was able to spoof the identity of a trusted client to a server. This is much harder to do today.

In addition to flags (syn, ack, syn-ack), the packet header will contain the sequence number that is intended to be used by the client to reconstitute the data sent over the stream in the correct order. (We will explore network packet flags in Chapter 2, “Networks and the Internet.”)

The Morris attack and several other session hijacking attacks require the attacker to be connected to the network and to simultaneously knock the legitimate user offline and then pretend to be that user. As you can probably imagine, it is a complex attack.

## Insider Threats

Insider threats are a type of security breach. However, they present such a significant issue that we will deal with them separately. An insider threat occurs when someone inside your organization either misuses his access to data or accesses data he is not authorized to access.

The most obvious case is that of Edward Snowden. For our purposes, we can ignore the political issues connected with his case and instead focus solely on the issue of insiders accessing information and using it in a way other than what was authorized.

In 2009 Edward Snowden was working as a contractor for Dell, which manages computer systems for several U.S. government agencies. In March 2012 he was assigned to an NSA location in Hawaii. While there he convinced several people at that location to provide him with their login and password information, under the pretense of performing network administrative duties. Some sources dispute whether or not this is the specific method he used, but it is the one most widely reported. Whatever method he used, he accessed and downloaded thousands of documents that he was not authorized to access.

Again, ignoring the political issues and the content of the documents, our focus is on the security issues. Clearly, there were inadequate security controls in place to detect Edward Snowden’s activities and to prevent him from disclosing the content of confidential documents. While your organization may not have the high profile that the NSA has, any organization is susceptible to insider threats. Theft of trade secrets by insiders is a common business concern and has been the focus of many lawsuits against former employees. In both Chapter 7, “Industrial Espionage in Cyberspace,” and Chapter 9, “Computer Security Technology,” we will see some countermeasures to mitigate this threat.

While Edward Snowden is an obvious example of insider threats, that is only one example. A common scenario is when someone who has legitimate access to some particular source of data chooses either to access data he is not authorized to access or to use the data in a manner other than how he has been authorized to use it. Here are a few examples:

* A hospital employee who accesses patient records to use the data to steal a patient’s identity, or someone with no access at all who accesses records

* A salesperson who takes a list of contacts with him when he leaves the company

这是一个比许多人的看法要严重得多的问题。在组织中，信息安全往往比应有的更松散。大多数人更关注外部安全，而忽视内部安全，因此访问组织内部数据往往相当容易。在我作为安全顾问的职业生涯中，我看到过敏感数据仅仅放置在共享驱动器上且没有限制访问权限的网络。这意味着网络上的任何人都可以访问这些数据。在这种情况下，当信息被窃取时，并没有发生犯罪。但其他情况下，员工有意绕过安全措施以访问未授权的数据。最常见的方法是直接使用他人的密码登录。这使攻击者能够访问该人员被授权访问的资源和数据。遗憾的是，许多人使用弱密码，或者更糟的是，他们在书桌上写下密码。甚至有些用户会共享密码。例如，假设一名销售经理因病休假，但想查看客户是否给她发送了邮件。她给助理打电话并把登录信息给他，让他查看她的邮箱。这种行为严格违反公司安全政策，但仍然时有发生。问题在于，现在有两个人拥有销售经理的登录信息。其中任何一人都可能使用它，或者故意或无意地向他人透露该登录信息。因此，使用该经理登录信息访问未授权数据的可能性更大。

## DNS 劫持

您在互联网上的大部分通信都会涉及 DNS（域名系统）。DNS 将我们理解的域名（如 `www.ChuckEasttom.com`）转换为计算机和路由器理解的 IP 地址。DNS 劫持使用几种技术之一来破坏该过程并将流量重定向到恶意站点，通常是为了窃取个人信息。

下面是一个攻击者可能执行 DNS 劫持攻击的场景：首先，攻击者创建一个钓鱼网站，冒充我们称之为 ABC 银行的银行。攻击者想诱骗用户访问该网站以窃取他们的密码，然后在真实银行网站上使用这些密码。由于许多用户过于聪明，不会轻易点击链接，他便利用 DNS 劫持欺骗用户。

攻击者创建自己的 DNS 服务器。（实际上，这一步相对容易。）然后他在该 DNS 服务器中添加两条记录。第一条是针对 ABC 银行网站的记录，指向他的假站点而非真实银行站点。第二条是针对一个不存在的域名的记录。攻击者可以查询域名注册机构，直到找到一个不存在的域名。为了说明目的，我们称其为 `XYZ` 域。

随后，攻击者向目标网络中的 DNS 服务器发送请求。该请求冒充来自目标网络内的任何 IP 地址，并请求 DNS 服务器解析 `XYZ` 域。

显然，DNS 服务器没有 `XYZ` 域的记录，因为该域名不存在。因此，它会在其指挥链中向上传播请求，最终到达其服务提供商的 DNS 服务器。在该过程中，攻击者会发送大量伪造响应，声称自己是目标服务器正在请求记录的 DNS 服务器，并提供 `XYZ` 域的 IP 地址。此时，攻击者的 DNS 服务器声称可以执行区域传输（zone transfer），交换所有信息，其中包括针对 ABC 银行的伪像地址。此时，目标 DNS 服务器已有一条指向攻击者网站的记录，而非真实的 ABC 银行网站。如果该网络中的用户输入 ABC 银行的 URL，他们的 DNS 服务器会将其引导至攻击者的网站。

这种攻击，像许多其他攻击一样，依赖于目标系统的漏洞。一个正确配置的 DNS 服务器永远不会向未经认证的 DNS 服务器执行区域传输。然而，遗憾的是，仍有大量 DNS 服务器配置不当。

## 新型攻击

前三版本书中讨论的许多威胁仍在困扰网络安全。恶意软件、DoS（拒绝服务）和其他此类攻击如今的频率与 5 年前或甚至 10 年前一样高。

一个新兴现象是 *doxing*，即通过互联网查找并公开个人的个人信息的过程。这可能涉及任何个人的任何信息，但最常用于针对公众人物。甚至有前 CIA 总监曾是 doxing 的目标。^(4)

4. [`gawker.com/wikileaks-just-doxxed-the-head-of-the-cia-1737871619`](https://gawker.com/wikileaks-just-doxxed-the-head-of-the-cia-1737871619)

黑客 Barnaby Jack 首先揭示了胰岛素泵中的漏洞，攻击者可以控制泵并导致其全部胰岛素储备在一次给药中泄漏，从而杀死患者。截至目前，尚无确认此类事件实际发生，但这仍然令人不安。类似的安全缺陷也发现于起搏器中。2018 年，美国食品药品管理局（FDA）发布了一份不安全医疗设备的列表。因此，这一问题似乎在恶化。

2015 年 7 月，有人揭露 Jeep 车辆在正常行驶时可能被劫持并停机。这意味着黑客可以在高速、繁忙的交通中使 Jeep 停下，可能导致严重的汽车事故。车辆劫持已成为更普遍的现象。2016 年的 DEF CON 会议设有车辆劫持专区。

更近期，物联网（IoT）创造了攻击者的新目标。智能家居和办公室，拥有集成的 Internet 设备，成为吸引攻击者的有力目标。例如，已有针对智能恒温器的勒索软件。

这些攻击都体现出一个共同主题：随着我们的生活与技术变得更加紧密相连，新的漏洞不断出现。这些漏洞不仅威胁数据和计算机系统，甚至可能危及生命。

## 评估您网络遭受攻击的可能性

这些攻击有多可能发生？作为个人或组织，您面临的真实危险是什么？最可能的攻击有哪些，您的哪些弱点会使您或您的组织面临风险？让我们来看看当前出现的威胁以及哪些最有可能给您或您的组织带来麻烦。

在过去，针对个人和大型组织的最可能威胁是计算机病毒。而且每个月都会记录数个新病毒爆发。新病毒时刻不时被创建，旧病毒依然存在。然而，病毒并非唯一的常见攻击，间谍软件（spyware）同样普遍，且正在迅速成为比病毒更大的问题。

- 黑客一词在电影和新闻中常被用来形容任何破解电脑系统的人。但在黑客社区中，黑客是指对特定系统或多个系统极其熟悉、希望进一步学习该系统的人，他们认为审视系统的弱点是了解系统的最佳方式。例如，一位精通 Linux 操作系统、致力于发现其弱点和缺陷的人就是黑客。

- 这种过程常常涉及检查缺陷是否可以被利用以获取系统访问权限。利用这一过程的“利用”部分，将黑客划分为三类：

    - 白帽黑客，在发现系统中的缺陷后，会向该系统的供应商报告。例如，白帽黑客若发现 Red Hat Linux 的某个缺陷，会（可能匿名）给 Red Hat 公司写信，详细说明缺陷及其利用方法。白帽黑客经常被公司雇佣进行渗透测试，EC Council 甚至为白帽黑客提供认证——认证伦理黑客 考试。

    - 黑帽黑客 是媒体常描绘的形象。她在获得系统访问权限后，目标是造成某种损害，例如窃取数据、删除文件或篡改网站。黑帽黑客有时被称为 *crackers*。

    - 灰帽黑客 通常是遵守法律的公民，但在某些情况下会涉足非法活动。

无论黑客如何自我定位，入侵任何系统都是非法的。这意味着，技术上说，所有黑客，不管其隐喻帽子的颜色如何，都在违法。不过，许多人认为白帽黑客实际上提供了一项服务：在恶意人士利用这些漏洞之前，他们会先发现漏洞并通知供应商。

### Script Kiddies

- 黑客是系统专家。和任何职业一样，也包含欺诈者。那么，缺乏专业能力却自称黑客的人称作 *script kiddy*。是的，这是一个较旧的资源，但该词的含义仍然相同。该名称来源于互联网上充斥大量可下载的工具和脚本，用于执行黑客任务。许多工具拥有易用的图形用户界面，让几乎没有任何技能的人也能操作。典型例子是用于发起拒绝服务攻击的 `Low Orbit Ion Cannon` 工具。下载此类工具但不真正理解目标系统的人被视为 script kiddy。你很可能遇到的自称黑客的人，实际上大多只是 script kiddy。

### Ethical Hacking: Penetration Testers

- 什么时候以及为何要授权他人对自己的系统进行黑客攻击？最常见的答案是为了评估系统漏洞。过去这类人被称为 *sneaker*，但如今更广泛使用的称呼是 *penetration tester*。无论称呼如何，该人士在法律允许的范围内非法进入系统，以评估安全弱点，正如 1992 年电影 *Sneakers*（主演 Robert Redford、Dan Aykroyd、Sidney Poitier）中所描绘。越来越多的公司正在寻求此类个人或公司的服务来评估其漏洞。

- 任何被聘请评估系统漏洞的人都应技术娴熟且道德规范。进行刑事背景调查，避免有问题的背景者。市面上有大量的合法安全专业人员，他们了解黑客技巧却从未犯下安全犯罪。若把“雇佣已定罪黑客即意味着雇佣有才华的人”这一论点推至逻辑结论，则可以推断这些人实际上并不如他们自以为的那么擅长黑客技术，因为他们已经被捕。

- 给予有犯罪记录的人系统访问权限，等同于雇佣多次酒驾（DWI）前科者做司机——在两种情况下，你都在招致麻烦，并可能承担重大的民事责任。

- 对其资质进行审查也很有必要。正如有些人声称极其擅长黑客却并非如此，也有那些声称是熟练渗透测试人员却缺乏真正所需技能的人。你不想不小心雇佣一个 script kiddy，误以为她是渗透测试专家。这类人可能会错误地宣称你的系统安全，实际上只是因为其技能不足未能成功突破防护。稍后在本书第 第 11 章 “网络扫描与漏洞扫描” 中会讨论评估目标系统的基本方法。第 11 章 也会讨论在雇佣顾问时应关注的资质。

### Phreaking

一种黑客攻击的特殊类型涉及入侵电话系统。这种黑客攻击的子类别被称为`phreaking`。`New Hacker’s Dictionary` 实际上将 phreaking 定义为“为了不支付某种电信账单、订单、传输或其他服务而使用恶意且大多非法的方式的行为”。phreaking 需要相当深入的电信知识，许多 phreaker 都有在电话公司或其他电信企业工作的专业经验。这种活动通常取决于破坏电话系统所需的特定技术，而不仅仅是掌握某些技术。

## 专业术语

您可能已经注意到，大多数黑客术语关注的是活动（phreaking）或执行该活动的人（penetration tester）。相反，安全专业术语描述的是防御屏障设备、程序和政策。这很有道理，因为黑客是以攻击者和攻击方法为中心的进攻性活动，而安全是以防御屏障和程序为中心的防御性活动。

### 安全设备

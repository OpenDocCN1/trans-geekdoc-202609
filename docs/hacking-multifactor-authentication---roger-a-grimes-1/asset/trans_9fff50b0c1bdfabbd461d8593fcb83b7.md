

## 386 黑客攻击多因素身份认证

### 缓存中毒 (Cache Poisoning)

今天另一种不常见的 DNS 攻击手段是 DNS 缓存中毒。如前所述，当计算机
获取 DNS 查询答案时，它会将答案缓存在内存中一段时间。通常情况下，
只有对特定域名具有权威性的 DNS 服务器才能返回特定的 DNS 查询答案（例如，只有 KnowBe4 的合规 DNS 服务器可以返回位于 knowbe4.com 域名下的任何主机的答案）。

但配置错误（或较旧的）客户端和服务器有时会接受从未请求过的 DNS 主机答案，并将其缓存以供日后使用。例如，用户点击了钓鱼邮件中的链接，这会将他们带到一个恶意域名。如果该域名存在并可以运行，它将位于某个特定的 DNS 服务器上。钓鱼者可以欺骗他们的 DNS 服务器，不仅返回恶意域名的 IP 地址，还返回一个 google.com 的恶意伪造 IP 地址（这是用户并未请求的）。
DNS 客户端被欺骗，将两个响应都缓存到内存中。用户没有察到 DNS 缓存中毒，在下一次查询时可能会被重定向到一个虚假的 Google 网站。

DNS 缓存中毒曾非常流行，但确实发生过。十多年前，微软 DNS 服务器和客户端（默认情况下）防止了 DNS 中毒，而 BIND 则代表（不允许 DNS 服务器为其其权威范围之外的域名提供服务）。由于全球最大的两个 DNS 服务器和客户端定期防止 DNS 缓存，缓存中毒在很久以前就消失了。尽管如此，你偶尔会跨易受缓存中毒的 DNS 服务器或服务进行缓存，例如家庭调制解调器或路由器，因此你仍然会在稀少数实例和场景中听到此类攻击发生。

### 命名冲突 (Name Collisions)

大多数命名空间都有“保留”名称，这些指向特定的服务或对象。例如，在 Windows 系统的命令行提示符中，你无法创建名为 AUX、CON 或 LPT1 或 CON2 的文件或文件夹，因为它们是保留字，指向操作系统使用的特定对象或句柄。

还有某些词在一个命名空间中具有含义，但可能与另一个命名空间中的对象或单词冲突或共同使用。这些被称为命名冲突或命名空间冲突。让我们来看两个常见的示例。

### WPAD

一种危险且易受攻击的、但大众并不为人知的命名冲突是 WPAD（Web代理自动发现）协议。WPAD 允许 Windows 和微软应用程序自动发现代理设置，应用程序（如 Internet Explorer 和 Edge）可以使用这些设置连接互联网。微软的设计目的是是将 WPAD 作为一种帮助 Windows 计算机轻松连接互联网的方法，而无需手动查找并输入代理设置。每台 Windows 计算机和相关应用程序都会生成针对 WPAD 位置的 DNS 查询。大多数网络不使用 WPAD，因此查询会被忽略且得不到响应。

## 第 18 章 DNS 劫持 387 

但知识丰富的黑客可以在他们的本地 DNS 服务器上注册 WPAD。例如，他们可以将自己的 Windows 计算机命名为 WPAD 并重启。当他们在 Windows 网络上执行此操作时，大多数 DNS 服务器会自动在对域名具有权威性的本地 DNS 服务器中注册他们的 WPAD 主机名和 IP 地址。同一网络上或使用相同 DNS 服务器的请求 WPAD 的其他计算机都将获得黑客计算机的 IP 地址。黑客只需要设置一个代理服务器（互联网上可以下载到许多免费代理服务），他们就可以开始将受害者的所有流量窃取到他们的计算机或其他位置。这是一种卑劣的策略。

有关 WPAD 黑客攻击的更多信息，请参 resources.infosecurity.institute/hacking-clients-wpad-web-proxy-auth-discovery-protocol 和 auth0.com/blog/heads-up-https-is-not-enough-when-using-wpad。

Corp 也参与了这种命名冲突示例。微软在 1999 年发布了其主要的网络命名服务 Active Directory（AD）。AD 使用 DNS 作为其主要命名服务（同同 NetBIOS 和 LDAP），使用 Active Directory 必须使用 DNS 规范设置网络。并不是每个 AD 管理员都熟悉 DNS 服务器，而且在十十年里，成千上万合法的导师在告诉他人如何构建或配置某些内容（包括 Active Directory）时使用 corp.com 域名作为示例。结果是数以万的私有域名的 Active Directory 名称中包含 corp（例如 roger.corp.com）。在任何网络完全连接到互联网之前，这是一个问题。但地址的 corp.com 部分开始导致命名冲突。如果某个（或更可能是代表我的一台计算机或程序）在 roger.corp.com 网络上查找 we，根据 DNS 解析的工作方式，不仅查找 we 的主机名，还会查找 roger.corp。拥有 corp.com 的人如果想做，可能会造成巨大的混乱。

十几年里，一个美国私人公民实际上拥有了超过 375,000 台试图查找他未请求的域名信息的计算机。某一天，作为一次测试，该用户在 corp.com 域名下设置了一个“回答”查询的邮件服务器，看看会发生什么。在一个小时内，他就有超过 1200 万封邮件发送到该服务器。其中许多邮件包含机密信息。所有者非常清楚这个问题，他最终以 100 万美元的价格将 corp.com 域名卖给了微软。向这位所有者和微软致敬。这个男人不必将价值昂贵的域名卖给微软，微软也不必花费 100 万美元，因为人们不理解 DNS 的工作方式。注意：这里有一篇关于命名冲突的 2014 年论文：krebsonsecurity.com/2020/02/microsoft- 以及icann.org/en/system/files/name-collision-mitigation-study-06jun14-en.pdf。易见地说，有很多方法可以进行 DNS 和命名空间劫持。当 DNS 或另一个命名空间被劫持时，它可以导致许多犯罪，包括：

- 绕过 MFA 认证
- 收集发往域名的邮件
- 收集发往域名的流量

这在现实世界已经发生了多次。让我们来看更多例子。

### 命名空间劫持示例

让我们来看劫持攻击示例。

### DNS 劫持攻击

如前所述，DNS 劫持最流行的类型之一是黑客接管整个 DNS 管理员服务器以更改已知主机的 IP 地址。这种情况每年发生数千次。有时是个人黑客为，有时是国家行为。2019 年，知名且受尊敬的安全供应商 CrowdStrike 报告 ([crowdstrike.com/blog/widespread-dns-hijacking-activity-targets-multiple-sectors])，12 个国家的 28 个组织的 DNS 被劫持。一旦被劫持，黑客就开始接收这些域名的流量。劫持时间几天到一个月不等。黑客非常复杂，甚至为需要 TLS 的连接创建了数字证书。安全公司 FireEye 得出结论 ([freeeye.com/blog/threat-research/2019/01/global-dns-hijacking-campaign-dns-manipulation-at-scale.html])，至少某些攻击是由伊朗完成的。可以在此处阅读更多详情：krebsonsecurity.com/2019/02/a-deep-dive-on-the-recent-widespread-dns-attacks。

### MX 记录劫持

如表 18.1 所示，MX 记录是指向邮件服务器 IP 地址的 DNS 记录。如果攻击可以将受害者的 MX 记录指向另一个 IP 地址，他们就可以捕获发往受害者的邮件。即使受害者的邮箱有 MFA 保护其账户。

在一个案例中，fabriceegrinda.com/acked-cryptocurrencies-stolen，一位使用 MFA 保护账户的加密货币交易员是 SIM 卡交换攻击（在第 8 章“短信攻击”中介绍）的受害者，其 MX 记录被劫持。黑客给他的手机打电话冒充他本人，说丢了手机，并要求公司激活另一个 SIM 卡。


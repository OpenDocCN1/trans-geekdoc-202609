

# 第 18 章 DNS 劫持

12. 权威 DNS 服务器返回请求的 IP 地址，随后，原始查询的 DNS 服务器将其返回给原始请求客户端（以及任何仍参与回答查询的中间 DNS 服务器）。

> 注意：这是对常见类型 DNS 查询的简单解释，在现实生活中，查询可能会复杂得多。

这一切都在几秒钟或更短的时间内完成。用户输入主机名，他们的应用程序很快就会重定向到全球范围内正确的计算机或网站。想起来，这非常令人惊叹。

TLD 服务器以下的所有服务器都会将其参与的 DNS 条目缓存一段时间，这段时间受限于该服务允许的最大 DNS 缓存或 DNS 查询答案中附带的缓存时间的最短值（后者通常也有一个预配置的缓存超时值）。缓存的答案总是比 DNS 服务必须执行额外的 DNS 查询和响应要快。图 18.1 给出了我们理论 DNS 查询的图解示例。

![](img/c78b0f79db62998ee317a35df5629d85_397_0.png)

# 382 破解多因素身份验证

DNS 客户端发送一个请求并获得一个答案，然后允许其连接到预定目标。原始查询的 DNS 服务器在尝试原始单个客户端查询时，可能会参与连接到许多其他 DNS 服务器。

## DNS 记录类型

DNS 服务器可以包含几十种不同的 DNS 记录，其中大多数将域名转换为关联的 IP 地址，尽管它们也可以指向其他 DNS 记录和主机名（以及其他信息）。表 18.1 显示了常见的 DNS 记录类型。

| DNS 记录类型 | 说明 |
|---|---|
| A | 主机记录；最常见的 DNS 记录类型；列出 DNS 主机及其关联的 IP 地址 (IPv4) |
| AAAA | IPv6主机记录 |
| MX | 邮件交换记录；列出特定 DNS 子域邮件服务器的 DNS 名称/或 IP 地址 |
| CNAME | 规范名称；别名记录；将主机名链接到同一设备的另一个主机名 |
| NS | 名称服务器记录；列出对一个或多个域具有权威性的 DNS 服务器 IP 地址 |
| PTR | 指针记录；用于反向查找；将 IP 地址转换为域名 |
| TXT | 文本记录；允许为特定主机注册任何类型的自由文本（例如在 SPF、DKIM、DMARC 反垃圾邮件协议中） |

你可能会听到人们要求特定类型的记录。大多数操作系统都内置了命令行工具 `nslookup`，你可以用它来进行工业级的手动 DNS 查询。例如，如图 18.2 所示，使用 `nslookup` 查询与 knowbase.com 关联的所有 DNS 记录。或者，互联网上还有许多 DNS 查询的图形化表示供任何人使用，包括这个：mxtoolbox.com。

有关 DNS 和 DNS 记录类型的更多信息，请访问 en.wikipedia.org/wiki/Domain_Name_System 和 ns1.com/resources/dns-records-explained。

有关 IP 地址的更多信息，请访问 en.wikipedia.org/wiki/IP_address。

## 常见的 DNS 攻击

MFA 解决方案最常见的依赖之一是 DNS，随后，DNS 被用于实施恶意黑客攻击。让我们探索一些常见的 DNS 劫持类型。

# 第 18 章 DNS 劫持 383

```
Command Prompt - nslookup
:\Windows\System32\drivers\etc>nslookup
Default Server: Unknown
Address: 102.168.1.1
> set type=any
known4.com
Server: Unknown
Address: 102.168.1.1
Non-authoritative answer:
known4.com
type =
n  "19e0be4e5a35427a8eaeec44f8bed9b9"
known4.com
type =
n  "ms-3123e056b6"
known4.com
type =
  "adobe-ldq-site-verification-370d0821e74fd02ec25cb9d1e406b9f77fe8473d282e12f4995ea269c6160"
known4.com
type =
  "amazons:17VKyQR0BbaaaEacXUtYj2fFUud1UdDEHJhu"
known4.com
type =
  "atlassian-domain-verification-D0icB0cbckVrrYgaf131YodGHl2aCVHD1MeqQ/33XA0setEbVI39RSnialJpw"
known4.com
type =
  "atlassian-domain-verification-ZhrtqRnNH8Bgaf131YodGHl2aKbGJFEZP360HM7WI2c5ws63"
known4.com
type =
  "google-site-verification-0aU0lfK6Agqkk_utwW4tRIjj91AG8L-8-x_p_ybyvGHo"
known4.com
type =
  "google-site-verification-E37EC0C7896c5X29pa55C0eb879914-InHzwRLs-c"
known4.com
type =
  "google-site-verification-A811b35ca-0a35OaD1R6gq274UROPLqqs"
known4.com
type =
  "google-site-verification-YZTS5XKSPE6KG99s_nQ5Rr89CnfgfuByW"
known4.com
type =
  "status-page-domain-verification-gcm5p25mg"
known4.com
type =
  "-v6f55I-mailenders.include.com-6o-lstpe-customer.com-194-252.248-167.69.53.221 ip:168.231
> set answer for="sales-all.com"
known4.com
  nameserver = ns-1882.awdns-432
known4.com
  nameserver = ns-803.awdns.net
known4.com
  nameserver = ns-835.awdns.org
known4.com
  primary server = ns-138.awdns-01.org
serial:
  refresh = 720 (12 hours)
  retry = 900 (15 minutes)
  expire = 129600 (14 days)
  default TTL = 86400 (day)
```

**图 18.2.** 使用 `nslookup` 查询恶意域的 DNS 记录

## 相似域名

DNS 劫持最常见的类型是通过社会工程学，欺骗用户进入一个与他们信任的合法域名相似的恶意域。例如，黑客可能会通过常见的拼写错误或输入错误注册域名来欺骗用户误触。这种后者被称为“域名抢注”（domain squatting），即恶意域的所有者利用用户错过了合法域名并重定向到恶意站点。如果恶意站点看起来很正规，误导的用户可能永远 own自己的错误并与其交互。另一个示例见图 18.3。该示例取自第 6 章讨论的 Kevin Mitnick 的“访问控制令牌”视频。

![](img/c78b0f79db62998ee317a35df5629d85_400.png)

**图 18.3:** DNS 恶意域，看起来像 linkedin.com 但实际上是 linked.com

图 18.4 显示了一个由之前的发送者发送给我的真实钓鱼邮件示例，该邮件声称来自 Microsoft，URL 中包含 microsoft.com。黑客希望我是一个不知道 DNS 工作原理的受骗受害者。他们希望我会使用 microsoft.com 并假设它是源域名。真实的域名是 devops.com，它可能是一个为了这次钓鱼活动被破解的普通域名，或者是钓鱼者注册的真实域名（对于后者，当 DNS 注册商收到足够的投诉时，此类域名会被删除或列入黑名单）。

# Microsoft Office365

Hello roger_grimes@outlook.com,
抱歉，由于您的 roger_grimes@outlook.com 出现异常活动，您的电子邮件已暂停。
如果您有任何问题，请访问 https://microsoft.com。

```
https://devops.com/login.microsoft.com?userid=roger_grimes
```

此感谢。
Microsoft Office
此邮件发自未监控的电子邮件。请勿回复此邮件。
隐私 | 法律通知

我们希望继续为您提供服务。
Microsoft Corporation
One Microsoft Way, Redmond, WA 98052
此邮件包含私人信息。请阅读我们的隐私声明。
此邮件发自未监控的地址。请勿回复此邮件。

**图 18.4:** 使用域名命名技巧欺骗受骗者的真实世界案例。

每个在互联网上使用电脑的人都应该在基础水平确保 DNS 安全，并学会识别域名与黑客和钓鱼者用于欺骗受骗者的各种技巧。

> 如果您感兴趣了解更多关于如何判断合法 DNS 地址，请查看我们的“对抗恶意 URL 技巧”网络研讨会：event.on24.com/wcc/r/2392582/477199D68E43BFA396FED7B0224967。

## 被破解的 DNS 记录

域名劫持（domain hijacks）最常见的 DNS 攻击类型是入侵者控制了 DNS 管理员帐户或权威 DNS 服务器，并更改 DNS 记录的 IP 地址指向另一个恶意位置。黑客接管 DNS 服务中合法 DNS 记录所有者的账户并进行更改，或者他们控制了整个 DNS 服务器。这类攻击已经几十年历史，并且仍然非常流行。

## 修改 DNS 的恶意软件

有数百种恶意程序，如果他们在电脑上运行，将尝试更改电脑的 DNS 设置。它们要么恶意修改 `hosts` 文件将特定查询重定向到目标位置，要么更改用户的默认 DNS 服务器指向它们的 DNS 服务器，后者会向 DNS 查询提供恶意 IP 地址。这里有一个服务警告修改 DNS 的恶意软件的示例：en.enigmasoft.com/dnschanger-removal。这是关于该主题的维基百科条目：en.wikipedia.org/wiki/Trojan.Win32.DNSChanger。因此，修改 DNS 的恶意软件专门针对人们的家庭宽带调制解调器、路由器或网关以


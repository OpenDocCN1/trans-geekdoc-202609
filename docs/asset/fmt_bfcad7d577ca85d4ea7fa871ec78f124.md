
图 2.6 显示了 Joseph Cox 在 Motherboard 上发布的暗黑主宰与受害者之间的一份疑似合同片段。

尽管表面如此，但如果受害者不支付赎金，该组织的业务语气会迅速恶化。当 TDO 的荒唐要求未被满足，该组织会迅速变得焦躁并在公共场合大发霆霆

![](img/ceaab52f5a948b18995b8efe89758781_64_0.png)

图 2.7

在 Twitter 上的行为与一个得不到想要的孩子并无异（图 2.7）。

以下是我 2018 年 10 月通过 Jabber 与 TDO 进行的三小时对话的摘录。TDO 知道他正在和我（Vinny Troia）说话。

其他的对话和摘录将在书中进行分析，因为它们与不同章节的内容有关。这些摘录提供了一个了解 TDO 极具侵略性、自大且粗俗性格的绝佳视角：

```
12:27 AM TDO Dumb prick.
12:27 AM TDO You're pleased that connecting one of the rare few of us.
12:31 AM TDO You're fortunate, tonight.
12:32 AM TDO I'm sitting moving terabytes of data into a new server, and I'm bored, so you've been blessed with communicating with me.
12:52 AM TDO It's quite nice to finally speak with you, Troia.
```

## 第 2 章 调查与威胁主体 39

12:27 AM TDO Dumb prick.

12:27 AM TDO You're pleased that connecting one of the rare few of us.

12:31 AM TDO You're fortunate, tonight.

12:32 AM TDO I'm sitting moving terabytes of data into a new server, and I'm bored, so you've been blessed with communicating with me.

12:52 AM TDO It's quite nice to finally speak with you, Troia.

## 第 2 章 调查与威胁主体 65

12:27 AM TDO Dumb prick.

12:27 AM TDO You're pleased that connecting one of the rare few of us.

12:31 AM TDO You're fortunate, tonight.

12:32 AM TDO I'm sitting moving terabytes of data into a new server, and I'm bored, so you've been blessed with communicating with me.

12:52 AM TDO It's quite nice to finally speak with you, Troia.

## 第 2 章 调查与威胁主体 65

12:27 AM TDO Dumb prick.

12:27 AM TDO You're pleased that connecting one of the rare few of us.

12:31 AM TDO You're fortunate, tonight.

12:32 AM TDO I'm sitting moving terabytes of data into a new server, and I'm bored, so you've been blessed with communicating with me.

12:52 AM TDO It's quite nice to finally speak with you, Troia.

# 章节

网络探索

## 本部分内容

- 第 3 章：手动网络探索
- 第 4 章：寻找网络活动（高级 NMAP 技术）
- 第 5 章：用于网络发现的自动化工具

正如标题所示，本书的这一部分讨论了网络调查和探索的许多复杂之处。调查人员和黑盒渗透测试人员往往只有一个 IP 地址可以依靠，因此这正是我们调查之旅的起点。接下来的这三章将介绍旨在彻底探索网络空间并帮助尽可能收集信息的流程和工具。

# 第 3 章

## 手动网络探索

本章旨在让你概览如何对组织进行通用的网络侦察，以及扫描和识别网络主机。本章的重点更多在于过程而非所使用的特定工具，因为当涉及到开源情报（OSINT）或可能涉及信息安全的任何方面时，总会有更更新、更好、更亮眼的工具供使用。

你可以使用数百种不同的工具和服务来收集有关组织的信息。新工具几乎每天都会出现，人是不可能跟上的。我不希望这成为重点。我确定我漏掉了一些工具，也确定在在你读到这里时，有些工具已经过时了。我的目标是向你展示一些我认为现在很有用的工具，但我完全理解未来可能会有更好的工具。

无论如何，工具不应是重点。重点在于信息是如何收集的，更重要的是，发现新信息的过程绝不应局限于单一工具。

始终尝试新事物，因为正如我将演示的那样，一个工具永远无法给你一个完整的答案。

## 章节目标：Pepsi.com 和 Cypher.org

为了说明不同工具和服务 之间的差异，我将对两个不同的服务器 `pepsi.com` 和 `cypher.org` 运行所有测试。我展示两个非常不同的网站，是为了展示在处理两个截然不同的目标时软件输出的差异。

为什么选择 Pepsi.com 和 cypher.org？选择 Pepsi.com 是因为我在写下这些内容时正在喝可乐。选择 Cypher 是因为它的名字。据我所知，`cypher.org` 与威胁行为者 Cypher（我认为他隶属于 The-DarkOverlord 黑客攻击小组）没有关联。在任何调查过程中，都会出现像这样新的研究途径，而且对不常见的域名（如 `cypher.org`）进行研究是必要的。

Pepsi 显然是一个非常知名且受欢迎的网站，因此两个网站之间的结果将大不相同。

> 在开始之前，我想指出，IP 归属确认（attribution）可能是调查人员面临的最困难的任务之一。我发现过许多数据泄露，包括 Exactis、Apollo.io 和 Verifications.io。在这些案例中，我唯一可以拥的就是泄露数据库服务器的 IP 地址。数据库服务器很少回溯主域名，因此找到数据的真实归属取决于调查人员。我将在沿程过程中提供一些我处理过的技巧。希望我的经验能帮到你们的一些人。

## 资产发现

开始网络探索通常非常简单。如果你正在进行黑盒测试，那么你就知道客户的名字和他们的域名。要获取他们的 IP 地址，你可以执行 Dig 查询。`Dig` 默认包含在 Linux/Mac 中。运行以下命令将给你 `apple.com` 的 IP 地址。

```
root@INT:- dig apple.com

; << Dig 9.10.3-P4-Ubuntu apple.com
;; global options: +cmd
;; Got answer:
;; >>HEADER<< opcode: QUERY, status: NOERROR, id: 7666
;; flags: qr rd; query: 1, ANSWER: 3, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDSECTION:
;; EDNS: version: 0, flags; udp: 512
;; QUESTION SECTION:

                A
;apple.com.
```

```
;; ANSWER SECTION:
apple.com.      1100 IN A      172.224.47
apple.com.      1100 IN A      142.160.59
apple.com.      1100 IN A      178.96.59
```

```
;; Query time: 1 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Mon Dec 10 09:02:24 UTC 2018
;; MSG SIZE rcvd: 86
```

## ARIN 查询

拥有一个 IP 地址很好，但我们想更多更多目标的信息。ARIN 管理 IPv4 和 IPv6 地址的分配。许多组织会注册整个范围，它们的 IP 空间可以很容易搜索。ARIN 提供了免费搜索来识别这些 IP 范围。

`WHOIS` 协议（将在第9 章讨论）用于查询包含资源（包括域名和 IP 地址）的所有公开信息的数据库。`WHOIS` 协议用于查询广泛的 WHOIS 服务器以获取全球数十亿网站的任何信息（统称为 WHOIS 数据）。

`WhoisSearch` 专门查看 ARIN 的注册数据。在进行黑盒评估且只有一个公司名称可以依靠时，这是一个很好的第一步。图 3.1 显示了一个 ARIN 搜索窗口。

![](img/ceaab52f5a948b18995b8efe89758781_70_0.png)

图 3.1。在 Whois 搜索中输入“Google”为我们提供了几个不同的网络范围，将其添加到我们的搜索中，如图 3.2 所示。

## 第3章 ■ 手动网络探索 49

Pepsi.com

https://dev.pepsi.com/

2017年12月 - 百事可乐官方网站：访问 www.pepsi.com 获取最新产品、促销活动及更多信息。

关于 | Pepsi Pulse

stage.pepsi.com/ABOUT

Pepsi Pulse 通过我们精选的音乐、体育和娱乐领域最热门的更新，让你活在“当下”。

条款与条件 | Pepsi Pulse

pre.pepsi.com/terms

Pepsi Pulse 通过我们精选的音乐、体育和娱乐领域最热门的更新，让你活在“当下”。

Pepsi Pulse

pre.pepsi.com/thegame

Pepsi Pulse 通过我们精选的音乐、体育和娱乐世界最热门的更新，让你以“当下”的速度活在精彩。

磁铁 - 百事可乐商店 (Pepsi Shop)

https://pepsi.com/magnet

四色磁铁：5 条评论。有货。SKU PC16015。数量。加入购物车。评论 5。撰写您的评论。您正在评价/Magnet.昵名.摘要。

联系我们 - 百事可乐商店 (Pepsi Shop)

https://pepsi.com/contact

如果你热爱百事周边产品并迫不及待，这里有购买方法！

使用您的账户网络账户 - 百事可集团 (PepsiCo)

https://pepsico.com/

您的账户可用于登录 PepsiCo、Pepsi、Mountain Dew、Sierra Mist、Sobie、Aquafina 或 Pepsi 网站。我们绝不会分享您的电子邮件...

百事 2升装没有一个周日是在餐桌上与...相遇的。

https://pepsi.com/content/15551403 - 翻译此页面

Pepsi Pulse 通过我们精选的音乐、体育和娱乐领域最热门的更新，让你活在“当下”。

## 图 3.3

共有 609 页结果，仅第一页（图 3.3）看起来就有许多正在被调查的目标。

## DNSDumpster

人们总是很忙。他们越忙碌，就越容易忘记清理杂物。在查看 DNS 记录或仅仅查找有关目标的更多信息时，我总是能找到已停用的子域信息。开发者很有可能会为尚未推送到生产环境开发项目创建“test”子域。开发者在处理自己的开发站点时，并不总是擅长清理。他们会使用捷径，尤其是在处理自己的开发站点时。这些子域和捷径往往能提供如金矿般的信息。

## 第一部分 - 网络探索

你可以使用 DNSDumpster 搜索这些内容，这是一个免费的域名搜索工具，可以通过 IP 地址快速发现相关主机。我遇到过这种情况：一个子域仍然指向一个旧 IP 地址，而该地址甚至不属于该银行，blah.bank.com 指向一个存放盗版软件的子域。他们对此非常感谢。...

DNSDumpster 使用起来再简单不过了（见图 3.4）。只需输入你正在查找的域名或 IP，它就会为你显示一个非常漂亮的图形化输出。

```
dns recon & research, find & lookup dns records
pepsi.com                               [Search >]
```

图 3.4

图 3.5 显示了以 pepsi.com 为目标的示例输出。DNS-Dumpster 为我们提供了 19 条主机记录。以下仅是结果的一小子集，从这里我们已经可以看到四个潜在的目标 IP，其名称看起来很有趣（names, account, secure）。![](img/ceaab52f5a948b18995b8efe89758781_73_0.png)

图 3.5

还有一个免费下载到 XLS 的选项，它可以为你提供非常详尽的分类，你可以轻松将其插入到另一个程序中（见图 3.6）。图 3.7 显示了发现设备的网络图。这是一个用于渗透测试的免费工具，增加了一些“哇因素”。当我们对第二个域名 cypher.org 运行相同的搜索时，得到了一个主机记录：

```
www.cypher.org - 162.210.102.59
```

## 第3章 手动网络探索 51

| 主机 | 地址 | 类型 | 网块所有者 | 国家 | HTTP 服务器 [标题] | HTTPS 服务器 [标题] |
|---|---|---|---|---|---|---|
| peops.com | 46.250.1 | | | 美国 | | |
| hop.peops.com | 104.217.145.123 | A | AS15167 Google LLC | 美国 | | |
| medium.peops.com | 104.217.145.123 | A | AS15167 Google LLC | 美国 | | |
| dhq.peops.com | 104.21.125.32 | A | AS15994 Rapid Ltd. | 美国 | Apache | 302 |
| enroll.peops.com | 182.214.239.98 | A | | | 美国 | | |
| gmail.peops.com | 182.214.239.98 | A | | | 美国 | | |
| mail.peops.com | 182.214.239.98 | A | | | 美国 | | |
| news.peops.com | 182.214.239.98 | A | | | 美国 | | |
| out.peops.com | 182.214.239.98 | A | | | 美国 | | |
| mail.peops.com | 182.214.239.98 | A | | | 美国 | | |
| test.peops.com | 182.214.239.98 | A | | | 美国 | | |
| web.peops.com | 182.214.239.98 | A | | | 美国 | | |
| us.peops.com | 182.214.239.98 | A | | | 美国 | | |
| wecan.peops.com | 182.214.239.98 | A | | | 美国 | | |
| zero.peops.com | 182.214.239.98 | A | | | 美国 | | |
| thesoundtrip.peops.com | 182.214.239.98 | A | | | 美国 | | |
| www.peops.com | 182.214.239.98 | A | | | 美国 | | |
| ports.peops.com | 182.214.239.98 | A | | | 美国 | | |
| www.ports.peops.com | 182.214.239.90 | A | | | 美国 | | |
| mtu.peops.com | 131.231.109.240 | A | | | 美国 | | |

图 3.6

# 第一部分 | 网络探索

![](img/ceaab52f5a948b18995b8efe89758781_75_0.png)

图 3.7

## Hacker Target

Hacker Target (`https://hackertarget.com/reverse-dns-lookup`) 让子域搜索和反向查询变得非常简单。你可以这样查询域名或 IP：

```
https://api.hackertarget.com/reversedns?q=url
```

在 hackertarget.com 上对 pepsi.com 进行快速搜索发现了 31 个不同的子域：

```
https://api.hackertarget.com/reversedns/?q=pepsi.com
```

sadad-pepsi.com,124.29.219.220 58.275.220 124.29.221

cntxb3.russia.intl.pepsi.com,195.239.40.163

www.wpbpepsi.com,209.142.183.140

mail.hbcpepsi.com,210.56.13.100

## 第3章 ■ 手动网络探索 53

```
mbcpepsi.com,156.46.83.96
router.mbcpepsi.com,69.29.19.133
mx.mbcpepsi.com,69.29.19.133
```.## Shodan

Shodan 是一个针对互联网设备的搜索引擎。Shodan 在映射互联网设备方面做得非常出色，因此你只需要向它提出正确的问题。

Shodan 实际上会查询每一个 IP 地址及其端口，并收集有关服务器响应的信息。Shodan 之所以伟大之处在于，你可以利用它来深入查找特定的技术目标。例如，是

## 54 第一部分 网络探索

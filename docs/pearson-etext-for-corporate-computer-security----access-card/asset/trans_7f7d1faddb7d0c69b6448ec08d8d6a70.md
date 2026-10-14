
仍然需要访问内部资源。远程工作的员工以及与其他公司的合作都是需要让边界之外的人员访问内部系统的实例。相反，坏人最终成为现有员工的情况也太常见了。

## RISE OF THE CITY

网络安全更好的范式是**城市模型**。² 城市模型没有明确的边界，进入网络的方式有多种。就像真正的城市一样，你是谁将决定你能够访问哪些建筑。

城市的安全需求比城堡的安全需求复杂得多。城市需要更多的警察、建筑物、门、围栏和锁。从技术角度来说，这意味着需要更多的内部入侵检测系统（IDS）、虚拟局域网、中央身份验证服务器以及加密的内部流量。

技术进步将改变我们*使用*网络的方式。出于必要，我们*保护*网络的方式也将发生变化。以下章节将介绍几种较为人所熟知的攻击网络的方法。

## Test Your Understanding

- 1. a. 解释安全网络的四个总体目标。
- b. 如何从加密的网络流量中收集信息？
- c. 举例说明新技术如何使网络安全性降低。
- d. 城堡模型与安全网络有何关系？
- e. “边界的死亡”是什么意思？
- f. 城市模型与安全网络有何关系？

***Warning***: 以下内容较难。请放慢速度并确保在继续之前理解每个概念。如果您不熟悉网络术语，应复习模块 A。

## In the News

### Reflected DoS Attack

2018年，一种名为*memcached*的流行缓存工具中发现了一个新漏洞。Memcached 的设计目的是通过临时缓存数据来加快网站速度。Memcached 中的漏洞允许外部攻击者使攻击威力增强51,000倍。³ 其结果是反射式 DoS 攻击，能够产生每秒超过1 Tb 的流量。Memcached 本应仅在内部使用，但许多服务器的 memcached 面向互联网。攻击者向运行 memcached 的服务器发送来自受害者伪造 IP 地址的统计 UDP 请求。放大的响应会产生巨大的数据包波浪，压垮受害者。

² Bruce Schneier, “The People Paradigm,” CSOOnline.com, 2004年11月1日。 www.csoonline.com/article/219787/bruce-schneier-the-people-paradigm.

³ Richard Chirgwin, “Popular Cache Utility Exploited for Massive Reflected DoS Attacks,” The Register, 2018年2月28日。 www.theregister.co.uk/2018/02/28/memcached_reflected_dos_attacks.

### DDoS for Hire

2018年，荷兰和英国警方在苏格兰、克罗地亚、加拿大和塞尔维亚逮捕了六名系统管理员，他们运营着一个 DoS 攻击租赁服务。⁴ 网站 WebStresser.org 的管理员会以低至10英镑（12美元）的价格对任何目标发动攻击。WebStresser.org 的管理员拥有超过136,000名注册用户，他们使用电子支付服务或比特币支付服务费用。 authorities 说该团伙攻击了英国一些最大的银行和政府组织。

### Largest DoS Attack Ever

2018年，历史上最大规模的 DoS 攻击针对 GitHub 发起。该攻击以每秒130百万个数据包的速度持续以1.35 Tbps 的速率向 GitHub 服务器发送数据。⁵ 但在2019年出现了一个新的竞争者，当时攻击者向 Imperva 发送了超过每秒580百万个数据包。这次新攻击在数据包数量方面是最大规模的攻击。GitHub 攻击仍然保持着总带宽最大的 DoS 攻击的头衔。卡巴斯基实验室指出，2019年的 DDoS 攻击比前一年增长了100%。攻击持续时间也比前一年增加了4.21倍。如果继续下去，2020年可能是网络攻击之年。

### Hacking WPA3

2019年，纽约大学的 Mathy Vanhoef 和特拉维夫大学的 Eyal Ronen 研究人员演示了针对最新无线安全协议 WPA3 的五次攻击。他们表明，初始握手协议中的缺陷可能允许攻击者在不知道密码的情况下访问网络。他们还演示了一种使用亚马逊网络服务（AWS）的密码攻击，可以花费约125美元找到网络密码。这些漏洞的信息在公开之前已发送给 Wi-Fi 联盟的开发人员。

## 4.2 DoS Attacks

### 4.2 Explain how denial-of-service (DoS) attacks work.

你在新闻中听到的最常见的网络攻击之一是拒绝服务（DoS）攻击。DoS 攻击试图使服务器或网络对合法用户不可用。就前面讨论的总体目标而言，DoS 攻击是降低可用性的一种方式。

> 拒绝服务（DoS）攻击试图通过用攻击数据包淹没服务器或网络，使其无法为合法用户提供服务。

DoS 攻击每天都会发生。企业和政府实体是攻击者的主要目标。第一章中，你曾简要介绍过一种称为分布式 DoS（DDoS）攻击的 DoS 攻击类型。本节将更详细地介绍 DDoS 攻击的机制，以及其他几种 DoS 攻击类型。

### Denial of Service... But Not an Attack

在了解 DoS 攻击的工作细节之前，重要的是要知道并非所有服务中断都是攻击。由于 DoS 攻击的常见性和在媒体上的曝光度，很容易将服务中断归咎于外部攻击者。内部员工和管理人员对本可预防甚至可能造成的停机事件免于指责。

⁴ Mohit Kumar, “Police Shut Down World’s Biggest ‘DDoS-for-Hire’ Service–Admins Arrested,” The Hacker News, 2018年4月25日。 https://thehackernews.com/2018/04/ddos-for-hire-hacker.html.
⁵ Casey Crane, “The Largest DDoS Attacks in History,” TheSSLStore.com, 2019年5月29日。 www.thesslstore.com/blog/largest-ddos-attack-in-history.

#### FAULTY CODING

例如，Newsnet Scotland 声称自己是亲联合主义政治对手 DoS 攻击的受害者。然而事实证明，服务中断是由糟糕的编码造成的。Newsnet Scotland 首席执行官 Alex Porter 发表更正声明称，“我们已经能够确定这并不是之前认为的 DDoS 攻击。问题在于对一个模块的调整本质上创建了一个捷径，导致服务器中出现大量循环活动。”

#### REFERRALS FROM LARGE SITES

当大型网站链接到规模小得多的网站时，另一种常见的非攻击性服务中断就会发生。这在 Slashdot、Drudge Report 和《赫芬顿邮报》等新闻聚合网站链接到托管新闻文章的小型网站时很常见。

小型新闻网站可能会因流量急剧增加而不堪重负。虽然效果与 DoS 攻击相同，但服务中断是无意的。流量的大幅激增或服务中断并不一定意味着恶意的 DoS 攻击。

### Goal of DoS Attacks

DoS 攻击的最终目标是造成伤害。对于企业而言，这可能表现为与在线销售、行业声誉、员工生产力或客户忠诚度相关的损失。DoS 攻击可以通过（1）停止关键服务或（2）随着时间的推移缓慢降低服务来造成伤害。

#### STOP CRITICAL SERVICES

攻击者经常针对组织的<|message|> 重要服务发起 DoS 攻击。攻击者针对的最常见服务是 HTTP。Web 服务是热门目标，因为可以造成经济损失。

例如，在一年中最繁忙的购物季节之一，亚马逊、沃尔玛和 GAP 的网站在大约一小时内无法访问。圣诞节前两天，针对这些大型公司的 DNS 提供商 Neustar 发动了 DDoS 攻击。购物者无法访问或从这些在线零售商处购买任何东西。

除了关闭公司的网站外，攻击者还可能阻止员工访问其电子邮件或文件服务器，或关闭专有应用程序。

#### DEGRADE SERVICES

通常针对关键服务的 DoS 攻击很容易识别且持续时间不长。网络管理员会迅速努力阻止已知攻击。然而，最具破坏性的攻击是无法识别的攻击。这些攻击持续时间很长。

缓慢降低服务的攻击更难检测，因为服务质量没有突然变化。网络管理员无法在网络流量的真实增长和渐进式 DoS 攻击之间做出明确区分。他们可能被迫为额外的带宽、硬件和软件进行不必要的资本支出。

## Test Your Understanding

- 2. a. 什么是拒绝服务攻击？
- b. 除了 DoS 攻击外，还有什么可能导致公司网站服务器崩溃？
- c. DoS 攻击的主要目标是什么？
- d. 缓慢的服务降级是否比完全停止更糟？为什么？

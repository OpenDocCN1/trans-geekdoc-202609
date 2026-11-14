

安全新闻，2009年3月23日，https://threatpost.com/no-more-free-bugs-software-vendors-032309/72484/。[访问日期：2017年6月18日]。

- 17. P. Lindstrom，“不再有免费漏洞”，Spire Security Viewpoint，2009年3月26日，http://spiresecurity.com/?p=65。

- 18. A. O’Donnell，“‘不再有免费漏洞’？从来没有免费漏洞这回事”，ZDNet，2009年3月24日，www.zdnet.com/article/no-more-free-bugs-there-never-were-any-free-bugs/。[访问日期：2017年6月18日]。

- 19. “漏洞赏金计划”，Wikipedia，2017年6月14日。

- 20. Mozilla Foundation，“Mozilla基金会宣布安全漏洞赏金计划”，Mozilla新闻中心，2004年8月，https://blog.mozilla.org/press/2004/08/mozilla-foundation-announces-security-bug-bounty-program/。[访问日期：2017年6月25日]。

- 21. “Pwn2Own”，Wikipedia，2017年6月14日。

- 22. E. Friis-Jensen，“漏洞赏金计划的历史”，Cobalt.io，2014年4月11日，https://blog.cobalt.io/the-history-of-bug-bounty-programs-50def4dcaab3。[访问日期：2017年6月18日]。

- 23. C. Pellerin，“国防部邀请经过审查的专家‘黑客攻击’五角大楼”，美国国防部，2016年3月。https://www.defense.gov/News/Article/Article/684616/dod-invites-vetted-specialists-to-hack-the-pentagon/。[访问日期：2017年6月24日]。

- 24. J. Harper，“硅谷可能颠覆网络安全范式”，《国防杂志》，第101卷，第759期，第32–34页，2017年2月。

- 25. B. Popper，“新一代初创公司正在帮助黑客合法赚取数百万”，The Verge，2015年3月4日，https://www.theverge.com/2015/3/4/8140919/get-paid-for-hacking-bug-bounty-hackerone-synack。[访问日期：2017年6月15日]。

- 26. T. Willis，“Pwnium V：永无止境* Pwnium”，Chromium博客，2015年2月。

- 27. Willis，“Pwnium V。”

- 28. “漏洞赏金——它们是什么以及为什么有效”，OSTIF.org，https://ostif.org/bug-bounties-what-they-are-and-why-they-work/。[访问日期：2017年6月15日]。

- 29. T. Ring，“为什么漏洞猎人正从野外归来”，《计算机欺诈与安全》，第2014卷，第2期，第16–20页，2014年2月。

- 30. E. Mills，“Facebook向黑客发放白帽子借记卡”，CNET，2011年12月，https://www.cnet.com/news/facebook-hands-out-white-hat-debit-cards-to-hackers/。[访问日期：2017年6月24日]。

- 31. Mills，“Facebook向黑客发放白帽子借记卡。”

- 32. J. Bort，“这位黑客作为‘漏洞赏金猎人’每年额外赚取10万美元”，Business Insider，2016年5月，www.businessinsider.com/hacker-earns-80000-as-bug-bounty-hunter-2016-4。[访问日期：2017年6月25日]。

- 33. H. Cavusoglu, H. Cavusoglu, and S. Raghunathan，“传播漏洞知识的漏洞披露机制效率”，《美国电气工程师学会汇刊》，第33卷，第3期，第171–185页，2007年3月。

- 34. B. Franklin，《穷理查德年鉴》(1744)。

- 35. K. Price，“美国所得税与漏洞赏金”，Bugcrowd博客，2015年3月17日，http://blog.bugcrowd.com/us-income-taxes-and-bug-bounties/。[访问日期：2017年6月25日]。

## 第三部分

### 利用系统

- 第10章 获取shell而无需利用
- 第11章 基本Linux利用
- 第12章 高级Linux利用
- 第13章 Windows利用
- 第14章 高级Windows利用
- 第15章 PowerShell利用
- 第16章 下一代Web应用程序利用
- 第17章 下一代补丁利用

## 第10章 获取shell而无需利用

渗透测试的关键原则之一是隐蔽性。我们在网络上被发现得越早，响应人员就能越快阻止我们继续推进。因此，使用在网络上看起来自然的工具，以及使用不会对用户产生任何明显影响的实用程序，是我们保持低调的方式之一。在本章中，我们将探讨一些在使用目标系统原生工具的同时获取访问权限并在环境中横向移动的方法。

本章将讨论以下主题：

- 捕获密码哈希
- 使用Winexe
- 使用WMI
- 利用WinRM

### 捕获密码哈希

在探讨不涉及利用漏洞的系统访问方式时，我们必须克服的首要挑战之一就是如何获取这些目标系统的凭据。本章将以我们的目标Windows 10系统为重点，因此首先你需要知道可以捕获哪些哈希，其次你需要知道如何利用这些哈希来为我们所用。

### 了解LLMNR和NBNS

当我们查找DNS名称时，Windows系统会经历多个不同的步骤，将该名称解析为IP地址。第一步涉及搜索本地文件。Windows会在系统上搜索hosts或LMHosts文件，查看该文件中是否存在相应条目。如果没有，下一步是查询DNS。Windows会向默认名称服务器发送DNS查询，看是否能找到条目。在大多数情况下，这会返回一个答案，我们就能看到试图连接的网页或目标主机。

在DNS失败的情况下，现代Windows系统使用两种协议尝试解析本地网络上的主机名。第一种是链路本地多播名称解析(LLMNR)。顾名思义，该协议使用多播来尝试在网络上查找主机。其他Windows系统会订阅此多播地址，当某个主机发送请求时，如果任何监听者拥有该名称并能将其转换为IP地址，就会生成响应。一旦收到响应，系统就会将我们引导至该主机。

但是，如果无法使用LLMNR找到主机，Windows还有一种额外的方法尝试查找主机。NetBIOS名称服务(NBNS)使用NetBIOS协议尝试发现IP。它通过向本地子网发送主机的广播请求来实现这一点，然后等待有人响应该请求。如果存在具有该名称的主机，它可以直接响应，然后我们的系统就知道要访问该资源需要前往该位置。

LLMNR和NBNS都依赖于信任。在正常环境中，主机只有在自己是被搜索的主机时才会响应这些协议。然而，作为恶意行为者，我们可以响应发送到LLMNR或NBNS的任何请求，并声称被搜索的主机归我们所有。然后，当系统访问该地址时，它会尝试与我们的主机协商连接，从而我们可以获取试图连接到我们的账户的相关信息。

### 了解Windows NTLMv1和NTLMv2身份验证

当Windows主机相互通信时，系统可以通过多种方式进行身份验证，例如Kerberos、证书和NetNTLM。我们将首先关注的协议是NetNTLM。顾名思义，NetNTLM提供了一种在网络上发送Windows NT LAN Manager(NTLM)哈希的更安全方式。在Windows NT之前，LAN Manager(LM)哈希用于基于网络的身份验证。LM哈希使用数据加密标准(DES)加密生成。LM哈希的一个弱点是它实际上是将两个独立的哈希组合在一起。密码会被转换为大写，并用空字符填充直到达到14个字符，然后密码的前半部分和后半部分被用来创建哈希的两个部分。随着技术的发展，这变得越来越重要，因为密码的每一半都可以单独破解，这意味着密码破解工具最多只需要破解两个7个字符的密码。

随着彩虹表的出现，破解变得更加容易，因此Windows NT改为使用NT LAN Manager(NTLM)哈希。任何长度的密码都可以进行哈希处理，并且使用RC4算法生成哈希。这对于基于主机的身份验证要安全得多，但在基于网络的身份验证方面存在一个问题。如果有人在监听，而我们只是在网络上传递原始NTLM哈希，什么能阻止该人获取哈希并重放呢？因此，创建了NetNTLMv1和NetNTLMv2质询/响应哈希，以给哈希增加额外的随机性，并使其更难破解。

NTLMv1使用基于服务器的随机数来增加随机性。当我们使用NTLMv1连接到主机时，首先请求一个随机数。接下来，我们取出NTLM哈希，并使用该随机数对其重新进行哈希处理。然后将其发送到服务器进行身份验证。如果服务器知道NT哈希，它可以使用发送的质询重新生成质询哈希。如果两者匹配，则密码正确。该协议的问题在于，恶意攻击者可能诱骗某人连接到他们的服务器并提供一个静态随机数。这意味着NTLMv1哈希仅比原始NTLM凭证稍微复杂一些，破解速度几乎与原始NTLM哈希一样快。因此，创建了NTLMv2。


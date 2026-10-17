
最终交付给客户的报告，才是客户真正关心的东西。在我在这本书中讨论的所有内容中，报告是渗透测试员获得报酬并被邀请再次测试的方式。这绝对是你测试中最重要的方面。你需要能够解释发现、对漏洞进行评级，并向客户解释结果在现实世界中的意义。

如果你曾经让多个渗透测试员评估过你的网络，你会发现报告会因执行测试的人员不同而有所差异。你会发现有些公司只是重新套用漏洞扫描器的报告模板，而另一些公司则提供详尽的报告并提供可复现的步骤。我发现真正缺乏价值的是：报告声称你有 100 个 Apache/PHP 关键发现，但测试人员无法验证这些发现是基于漏洞本身真实存在，还是仅基于横幅版本判断的。

既然报告实际上是你想要如何呈现发现的一种改编，我不会展示我的模板，而是给你一些我多年测试经验总结出的提示和最佳实践。

![报告概览](img/00250.jpeg)

我过去教学时，会强调报告是成功渗透测试的最重要因素。无论你攻破了 3 台还是 300 台主机都无关紧要，如果你不准确地告诉客户你到底做了什么，或者不帮助客户理解解决这些问题的缓解措施。

如果你想看看示例报告应该是什么样子的，可以参考 Offensive Security 的样本报告。[`www.offensive-security.com/reports/penetration-testing-sample-report-2013.pdf`](http://www.offensive-security.com/reports/penetration-testing-sample-report-2013.pdf)

![样本报告参考](img/00251.jpeg)

### 关键报告指南

#### 不要提交扫描器报告

*   不要提交重新命名过的 `Nexpose` 或 `Nessus` 报告。
    *   我再怎么强调都不为过；请使用你自己的模板并验证你的发现。
    *   绝不要将 `Nexpose` 或 `Nessus` 报告作为最终报告交给客户。

#### 统一漏洞评级标准

*   对漏洞进行评级。
    *   确保你找到一种方法来统一对漏洞进行评级。
    *   我建立了自己的矩阵，其中包含来自 `NIST`、`DISA`、`CVSS` 和个人经验的参考，用于设定漏洞评级。
    *   该矩阵包括根据内部/外部发现、是否有可用漏洞利用代码、其系统的普及程度、漏洞利用可能导致的后果以及对 `CIA` 安全三要素的影响来增加或降低严重程度。
    *   经过我矩阵评估的漏洞将始终具有相同的严重性级别。如果客户询问我如何对漏洞进行评分，我可以引用我的矩阵。

#### 理论发现与实际发现

*   理论发现与实际发现。
    *   我通常不喜欢将发现标记为关键，如果它们只是理论上的，且没有已知的实际漏洞利用方式。这些肯定仍应作为发现报告，但如果我找不到任何攻击主机的途径，我通常会降低其评级。
    *   这有助于客户正确识别哪些发现需要立即关注，哪些可以在常规变更控制窗口期间处理。

#### 解决方案至关重要

*   解决方案与发现同等重要。
    *   如果你使用工具攻破网络，你必须有办法阻止它。
    *   如果你没有解决方案，帮助客户制定缓解策略。

#### 准确评估 Secure Flag/HTTP Only 发现

*   如果 `Secure Flag`/`HTTP Only` 发现不构成问题，请勿错误评级。
    *   有些 `Cookie` 不用于会话令牌，可能不会为攻击者提供任何额外的攻击面。虽然这些仍应报告，但其评级应远低于用于跟踪会话状态的 `Cookie`。
    *   这只是一个例子，旨在强调确保正确理解漏洞的理念。

#### 验证发现

*   确保漏洞是真实的漏洞。
    *   我收到过多少次渗透测试结果，告诉我我的系统上有 `PHP` 漏洞利用。这是因为扫描器仅基于版本就提醒他们存在这些关键发现。一些发现称是 `PHP CGI` 问题或 `Apache mod security` 问题。问题在于我的服务器并不运行 `CGI` 脚本，但扫描器仅基于版本就识别出了该问题。请务必确保验证发现是真实的发现。

## 客户反馈与持续成长指南

### 客户反馈

本节最后要强调的是确保从客户那里获取反馈。图表适合管理层查看，但技术人员希望看到大量重现漏洞利用的步骤和程序。同时，将所有原始扫描结果、原始 `Burp` 结果移交给客户也很重要，我通常还会提供一个 `Excel` 文件，其中包含发现的漏洞和漏洞的简单列表。`Excel` 文件使 `IT` 团队能够轻松勾选哪些发现已修复，哪些仍然有效。

如果你想在渗透测试人员中脱颖而出，尝试寻找方法将自己与其他人区分开来。如果你为大公司做渗透测试，还可以提供一份简单的 `OSINT`（开源情报）报告，描述从互联网上可以公开发现什么和谁。

![](img/00252.jpeg)

### 持续成长路径

最常被问到的问题之一是“接下来该去哪里？”如何在安全行业持续变强，如何提升？所以我尝试为读者提供一份选项清单。我将这部分细分为：主要参会会议、辅助成长的培训课程、技术与非技术书籍阅读、靶场框架、夺旗赛（`CTF`）活动，以及跟进新闻资讯。

![](img/00253.jpeg)

#### 主要安全会议

我从参加主要安全会议开始，因为这是结识他人、了解行业动态的绝佳场所。参会选择非常多，你可以在 `InfoSecEvents` 找到更完整的列表：[`bit.ly/1cVISnz.I’ll`](http://bit.ly/1cVISnz.I’ll)。以下是我亲身经历推荐的会议及简介：

*   **DefCon** ([`www.defcon.org/`](http://www.defcon.org/)) - 拉斯维加斯举办，费用低于 $200。这是最大的黑客大会，必参加。
*   **DerbyCon** ([`www.derbycon.com/`](http://www.derbycon.com/)) - 肯塔基州举办，费用低于 $200。我最喜欢的部分演讲来自 `DerbyCon`。
*   **BlackHat** ([`www.blackhat.com/`](http://www.blackhat.com/)) - 拉斯维加斯举办，费用极高。演讲嘉宾阵容强大，更面向企业员工。
*   **Bsides** ([`www.securitybsides.com/`](http://www.securitybsides.com/)) - 通常免费。全国各地都有 `Bsides` 大会，找到你附近的那场！
*   **ToorCon** ([`toorcon.net/`](http://toorcon.net/)) - 圣地亚哥举办，这是小型会议之一，能结识很多新朋友，大家都很友好。
*   **CanSec** ([`cansecwest.com/`](http://cansecwest.com/)) - 我只参加过 `CanSecWest`，价格不菲，但技术演讲质量一直很高。
*   **Shmoocon** ([`www.shmoocon.org/`](http://www.shmoocon.org/)) - 东海岸最大的会议之一，费用低于 $200。我最喜欢的会议之一。
*   **OWASP AppSec** ([`www.owasp.org/index.php/Category:OWASP_AppSec_Conference`](http://www.owasp.org/index.php/Category:OWASP_AppSec_Conference)) - 价格低廉且有趣，专注于 `Web` 应用安全。如果你是 `OWASP` 会员，费用低于 $100。
*   **Lethal** ([`www.meetup.com/LETHAL/`](http://www.meetup.com/LETHAL/)) - 当然要推荐一下我的小组。虽然不是会议，但我们有每月聚会并邀请演讲者。不仅免费，而且小组规模小，方便你参与并结识志同道合的人。

![](img/00254.jpeg)

#### 培训课程

如果你想在某个安全领域快速入门，培训课程最有帮助。鉴于课程众多，以下是一些推荐：

*   **BlackHat** - 费用极高，但不仅课程种类多，而且由业内顶尖专家授课。
*   **DerbyCon** - 肯塔基州举办，价格合理，在会议期间进行。
*   **SANS** ([`www.sans.org`](http://www.sans.org)) - 费用极高，但它们是行业标准。
*   **Offensive Security** ([`www.offensive-security.com/`](http://www.offensive-security.com/)) - 价格合理，我强烈推荐参加 `Offensive Security` 的在线课程。你将获得大量实战经验，但需要投入大量时间。

![](img/00255.jpeg)

#### 书籍推荐

还有许多好书值得一读。我无法列出所有，但以下这些令我印象深刻——顺序不分先后。你可能会问，为什么要关注恶意软件分析这类书籍？简单的答案是：不同安全领域（取证、恶意软件分析、应急响应、渗透测试）相互交织。要成为优秀的渗透测试员，你必须了解它们。你得知道如何清除痕迹、什么可能阻止你攻破目标、以及防御者是如何思考的。

##### 技术类阅读

*   《Web Application Hacker’s Handbook 2》
*   《Metasploit The Penetration Tester’s Guide》
*   《Gray Hat Hacking》
*   《SQL Injection: Attack and Defense》
*   《Hacking: The Art of Exploitation》
*   《Hacking Exposed》（全系列）
*   《Malware Analyst Cookbook》
*   《Shellcoder’s Handbook 2nd Edition》
*   《A Bug Hunter’s Diary》

##### 趣味安全相关阅读

*   《Enders game》
*   《Cryptonomicon》
*   《Snow Crash》
*   《The Cuckoo’s Egg》
*   《How to Steal a Network》（全系列）
*   《Dissecting the hack: the f0rb1dd3n network》
*   《Silence on the wire》
*   《Underground》
*   《Daniel Suarez’s Daemon》
*   《Kingpin》

![](img/00256.jpeg)

#### 靶场框架实战

想自学变强？虽然我没试过所有这些框架，但你可以下载、部署它们，然后告诉我体验如何。这是极佳的练习！

*   `Offensive Security Metasploitable`
*   `OWASP WebGoat`/`Vicnum`/`InsecureWebApp`
*   `Maven Security WebMaven`/`Buggy Bank`
*   `Google Gruyere` (antigo `Codelab` / `Jalsberg`)
*   `NTNU Hacme Game`
*   `SPI Dynamics SPI Dynamics`
*   `DVWA Damn Vulnerable Web Application`
*   `Iron Geek Mutillidae`
*   `The Butterfly Security The Butterfly Security Project`
*   `McAfee Hacme Casino`/`HacmeBank`/`Travel`/`Shipping`
*   `Bonsai Sec Moth`
*   `Stanford SecuriBench`
*   `Enigma Group EnigmaGroup`
*   `X5S XSS Encoding Skills`
*   `The Bodgeit Store`
*   `MadIrish LampSecurity`
*   `WackoPicko`
*   `DVL Damn Vulnerable Linux`
*   `Pynstrom Holynix`

![](img/00257.jpeg)

#### 夺旗赛（CTF）挑战

如果你打算以此为职业，甚至只是出于兴趣，你真的需要参与不同的 `CTF` 挑战。试着找几个朋友，或者找到你当地的安全小组一起尝试这些挑战。这不仅能测试你的技能和对攻击的理解，还能让你更好地与业内人士建立联系。花 3 天 3 夜攻克挑战，大概是你能体验到的最有成就感的事情之一。

访问 [`ctftime.org/`](http://ctftime.org/) 查找下一场 `CTF` 的时间地点。如果你在洛杉矶地区，欢迎访问 [www.meetup.com/lethal](http://www.meetup.com/lethal) 加入我们的战队！

![](img/00258.jpeg)

#### 安全资讯跟进

安全领域变化迅速，跟上这个不断演变的世界至关重要。以下是我每天早上都会查看的 `RSS` 订阅/网站列表，以及我每天接收的邮件列表。

##### RSS Feed / 网站列表

*   [`securepla.net/rss.php`](http://securepla.net/rss.php) - 这是我多年整理的个人 `RSS` 订阅源，强烈推荐查看。
*   [`code.google.com/p/pentest-bookmarks/wiki/BookmarksList`](https://code.google.com/p/pentest-bookmarks/wiki/BookmarksList)

##### 邮件列表

*   [`www.schneier.com/crypto-gram.html`](https://www.schneier.com/crypto-gram.html)
*   [`www.team-cymru.org/News/`](http://www.team-cymru.org/News/)
*   [`www.infragard.org/`](https://www.infragard.org/)
*   [`www.thecyberwire.com/`](http://www.thecyberwire.com/)

##### Twitter Lists

## 致谢与参考资源

### 推荐关注

*   [`twitter.com/danothebeach/lists/infosec`](http://twitter.com/danothebeach/lists/infosec)
*   [`www.marblesecurity.com/2013/11/20/100-security-experts-follow-twitter/`](http://www.marblesecurity.com/2013/11/20/100-security-experts-follow-twitter/)

![图片](img/00259.jpeg)

### 结语

如果你读到了这里，那就意味着你已经完全掌控了网络，破解了所有密码，并全身而退。现在是时候将你所学的一切加以运用并在此基础上继续构建了。我给你最大的建议是参与当地的安全小组或参加安全会议。你也可以开设一个博客，开始摆弄这些不同的工具。找出什么有效、什么无效，以及如何让攻击更高效、在网络中更隐蔽。这需要占用你正常朝九晚五工作之外的时间，但绝对值得。

希望你觉得《黑客攻防实战演练》内容丰富，并且学到了几个新工具或技术。安全领域瞬息万变，紧跟趋势并发挥你自己的创造力至关重要。我不能说会有那么一天你能自称精通了安全，但一旦你牢牢掌握了基础，从宏观层面来看，攻击手法其实并没有太大变化。

如果你觉得这本书有帮助，请在书籍官网给我留言，这将帮助我尝试开发更好的内容，并尝试了解你在寻找什么。如果我在这本书中遗漏了某人，或在某个话题上表述有误，我深表歉意，并将在本书官网更新相关信息。

### 联系方式

**Twitter**: `@HackerPlaybook`

**URL**: [TheHackerPlaybook.com](http://TheHackerPlaybook.com)

![图片](img/00260.jpeg)

### 致谢名单

有太多的人/团体我想要感谢，如果遗漏了你，请见谅。你们中的一些人可能不认识我，但你们的研究、工具和理论激励我成为一名更优秀的渗透测试员，并帮助我完成了这本书。排名不分先后：

![图片](img/00261.jpeg)

![图片](img/00262.jpeg)

### 参考文献

1. [`mashable.com/2013/12/09/anonymous-attack-fine/`](http://mashable.com/2013/12/09/anonymous-attack-fine/)
2. [`krebsonsecurity.com/2013/10/adobe-breach-impacted-at-least-38-million-users/`](http://krebsonsecurity.com/2013/10/adobe-breach-impacted-at-least-38-million-users/)
3. [`community.rapid7.com/community/infosec/sonar/blog/2013/10/30/project-sonar-one-month-later`](http://community.rapid7.com/community/infosec/sonar/blog/2013/10/30/project-sonar-one-month-later)
4. [`pauldotcom.com/wiki/index.php/Episode291`](http://pauldotcom.com/wiki/index.php/Episode291)

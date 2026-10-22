
- 49. Steven Soderbergh（导演），《十一罗汉》，2001，www.imdb.com/title/tt0240772
- 50. R. B. Zajonc，“单纯曝光的态度效应”，《人格与社会心理学杂志》9，第2期（1968年）：1–27。
- 51. E. Grandjean，“社会工程恶意软件的首要目标”，《McAfee 安全期刊》，秋季（2008年）：9–12。
- 52. A. Tversky 和 D. Kahneman，《不确定性下的判断：启发式与偏见》，Science，185（1974）：1124–1130。
- 53. Joan Goodchild，“社会工程故事”，CSO，2010年5月24日，www.csoonline.com/article/594924/social-engineering-stories
- 54. Tim Wilson，“黑客的八个面孔”，Dark Reading，2007年3月29日，www.darkreading.com/security/news/208804443/eight-faces-of-a-hacker.html
- 55. Malcolm Allen，“社会工程：入侵计算机系统的手段”，SANS Institute 信息安全阅读室，2006年6月，www.sans.org/reading_room/whitepapers/engineering/social-engineering-means-violate-computer-system_529
- 56. Radha Gulati，“社会工程的威胁及你的防御措施”，SANS Institute 信息安全阅读室，2003年，www.sans.org/reading_room/whitepapers/engineering/threat-social-engineering-defense_1232
- 57. Granger，“黑客战术”。
- 58. Kelly Jackson Higgins，“社会工程变得更聪明”，Dark Reading，2006年6月16日，www.darkreading.com/authentication/social-engineering-gets-smarter/208803849
- 59. P. Roberts，“HBGary 攻击背后的黑客女孩”，threatpost，2011年3月17日，http://threatpost.com/hacker-grrl-behind-hbgary-attack-031711/75037
- 60. Ryan Groom，“前五大社会工程技术”，About: Business Security，访问日期2007年3月17日。 http://bizsecurity.about.com/od/physicalsecurity/a/topsocialengine.htm
- 61. Michael Hoeschele 和 Marcus Rogers，“检测社会工程”，载于《数字取证进展：IFIP 国际数字取证会议》（2005年2月）：67–71。
- 62. RSA，“基于风险的身份验证”，信息安全术语表，RSA 网站，访问日期2012年4月12日，www.rsa.com/glossary/default.asp?id=1094
- 63. M. J. Edwards，“IE 7.0 和 Firefox 2.0 均具有新的反钓鱼技术”，WindowsITPro，2006年10月26日，http://windowsitpro.com/networking/ie-70-and-firefox-20-both-have-new-antiphishing-technologies
- 64. Dimensional Research，“社会工程对信息安全的风险：IT 专业人士调查”，Check Point Software Technologies 网站，2011年9月，www.checkpoint.com/press/downloads/social-engineering-survey.pdf

## SPAM、钓鱼和特洛伊木马：旨在欺骗的攻击

Stephen Cobb

- **20.1 不需要的电子邮件和其他害虫：安全问题** 20·1
  - 20.1.1 常见元素 20·2
  - 20.1.2 章节组织 20·3
- **20.2 电子邮件：解剖课** 20·3
  - 20.2.1 简单邮件传输协议 20·3
  - 20.2.2 预警 20·4
- **20.3 SPAM 定义** 20·6
  - 20.3.1 Spam（非 SPAM®）的起源和含义 20·7
  - 20.3.2 深入挖掘垃圾邮件 20·8
  - 20.3.3 垃圾邮件的双重威胁 20·12
- **20.4 对抗垃圾邮件** 20·18
  - 20.4.1 垃圾邮件战士登场 20·18
  - 20.4.2 良好的声誉？ 20·18
  - 20.4.3 中继麻烦 20·20
  - 20.4.4 黑洞和阻止列表 20·20
  - 20.4.5 垃圾邮件过滤器 20·21
  - 20.4.6 网络设备 20·24
  - 20.4.7 电子邮件身份验证 20·25
  - 20.4.8 行业举措 20·26
  - 20.4.9 法律补救措施 20·26
- **20.5 钓鱼** 20·27
  - 20.5.1 钓鱼邮件长什么样 20·27
  - 20.5.2 钓鱼的增长和范围 20·29
  - 20.5.3 威胁在哪里？ 20·30
  - 20.5.4 对抗钓鱼 20·31
- **20.6 特洛伊代码** 20·31
  - 20.6.1 经典和近期的特洛伊木马 20·32
  - 20.6.2 基本的反特洛伊战术 20·34
  - 20.6.3 锁定和隔离 20·35
- **20.7 结论性评论** 20·36
- **20.8 进一步阅读** 20·36
- **20.9 注释** 20·36

### 20.1 不需要的电子邮件和其他害虫：安全问题

本章讨论了三个名称奇怪的计算机安全威胁：垃圾邮件、钓鱼和特洛伊代码。垃圾邮件是未经请求的商业电子邮件。钓鱼是指使用欺骗性未经请求的电子邮件来获取——通过电子方式“捕捞”——机密信息。特洛伊代码一词源自特洛伊木马，是设计成伪装成合法应用程序以实现对系统未经授权访问的软件。在本章中，我们

![](img/a2e2eee3c32fb4bb08c64c1d6efd2e39_609_0.png)

SMTP 会话，但这些查询会显著减慢邮件处理速度，需要额外容量来抵消效率损失。白名单标识受信任的电子邮件发送者；黑名单标识不受信任的发送者。维护白名单可能耗时，而黑名单有着不准确和法律纠纷的悠久历史。简而言之，对速度的需求创造了一个系统，其中邮件投递中的虚假陈述几乎没有任何技术后果。这正是垃圾邮件发送者一直以来，并且继续非常有效地将不需要的电子邮件投递出去的原因。

SMTP 就像温斯顿·丘吉尔可能会说的那样，是做电子邮件的最糟糕方式，除了所有曾经尝试过的其他方式之外。现实是 SMTP 可靠运行并且已被广泛实施。用任何更好的东西取代 SMTP 意味着对整个全球电子邮件基础设施进行彻底重新设计，这是一项很少有人愿意承担的任务。一些人努力开发可以搭载在现有 SMTP 基础设施之上的解决方案，使 SMTP 能够继续高效运行，同时为使用者提供选择更强大的功能来帮助区分合法邮件和垃圾邮件的选项。本章后面将详细介绍这些解决方案。

电子邮件无法在没有称为“头”的东西的情况下投递，每封电子邮件都有一个头，它是消息的一个部分，并不总是显示在收件人的电子邮件程序中，但确实存在，描述消息来自何处、如何寻址以及如何投递。检查头可以告诉你很多关于消息的信息。请考虑消息在 Microsoft Outlook Express 中出现的样子，如图 20.2 所示。

![](img/a2e2eee3c32fb4bb08c64c1d6efd2e39_610_0.png)

**图 20.2 在 Outlook Express 中查看消息头详细信息**

在顶部可以看到发件人、收件人和主题。例如，你可以看到一条似乎来自 zjjimwalker8467r21@lycos.com 发往 press@eprivacygroup.com 的消息，主题为：“您已获批准！”正如你可能猜到的那样，press@eprivacygroup.com 并不是一个真实的人。这只是一个出现在公司网站上作为媒体联系方式的地址，当然，没有人实际上在抵押贷款申请中使用过这个地址。该地址是由一个自动在网络上搜寻电子邮件地址的程序收集的。

当你在电子邮件客户端（例如 Outlook 或 Outlook Express）中打开此消息并使用文件/属性命令或等效命令时，你可以单击“详细信息”选项卡查看消息如何在互联网上传递。你首先看到的是一个标记为“headers”的框，如图 20.2 所示。阅读它会告诉你消息经过了多个不同的电子邮件服务器。Qmail 是公司的邮件程序，是 Received 的第一个实例。下方的三个是中介，直到最后一个 smtp-server1.cflrr.com。那是位于中佛罗里达（cfl）Road Runner（rr）有线调制解调器网络上的电子邮件服务器，为数万户家庭提供高速互联网接入。

那么谁发送了这条消息呢？很难说。正如你可能预期的那样，并不存在 zjjimwalker8467r21@lycos.com 这样的地址。确定谁发送了这种垃圾邮件消息的最佳方法是检查其内容。垃圾邮件无法吸引傻瓜

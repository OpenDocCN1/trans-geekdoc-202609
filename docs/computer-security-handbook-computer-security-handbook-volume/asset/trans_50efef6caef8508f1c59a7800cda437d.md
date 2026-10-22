
使用防火墙配置的当前最佳实践。（这些变化迅速。）使用安全、经过身份验证的 Web 代理，并强制所有客户端使用该代理。（任何用户都不应能够直接访问 Web。）禁用所有未使用的 LAN 访问端口，或考虑使用 802.1x 身份验证自动执行此操作。将网络划分为使用 VLAN 或物理分离的交换机架构的功能工作组。如果可能，在 VLAN 或交换段之间实施访问控制列表。目标是使网络尽可能正交。如果网络只能以一种正确的方式运行，组织将完全避免许多自动化的恶意代码威胁。

### 16.5.4.4 网络监控。

预防恶意代码威胁是理想的，但检测至关重要。大多数恶意代码攻击都会留下某些痕迹，无论是基于主机的还是基于网络的。为了检测这些痕迹，组织应建立一个安全信息管理系统，汇总设备日志、服务器日志、主机日志、入侵检测系统警报和网络流数据。网络流数据是检测异常网络活动的有用工具。网络流是一个 5 元组，由源地址、目的地址、源端口、目的端口和协议组成，并附带时间戳。任何恶意网络活动都会有相关的流。然而，隐蔽的恶意软件会试图表现正常以规避检测。检测异常活动要求操作员了解环境中的正常情况。如果没有历史统计数据库或丰富的经验，这可能很困难。网络异常检测（NAD）使用统计建模方法 56 来利用这些数据检测统计异常值。这对于检测新的恶意代码威胁以及其他形式的异常行为非常有效。然而，缺乏理解似乎限制了 NAD 的采用。这是许多组织可以在信息安全控制实践中改进的一个领域。

## 16.6 结论。

恶意代码威胁与非恶意代码的种类一样多。防止所有恶意代码是不可能的，因为该问题已被证明是 NP-完全的。57 然而，采用运营、人员和技术控制的纵深防御策略可以相对有效。正确使用时，组织可用的当前一代技术控制有效阻止了大多数恶意代码威胁。然而，受信任的内部人员通常拥有将威胁转化为运营风险现实所需的访问权限。恶意代码威胁的当前趋势表明，有组织的犯罪参与和国际间谍活动持续存在，并继续针对安全链中最薄弱的环节：人类。

## 16.7 延伸阅读

- Blunden, Bill. 《Rootkit Arsenal：系统黑暗角落中的逃脱与规避》，第2版。Jones & Bartlett Learning, 2012.
- Butler, Jamie 和 Greg Hoglund. 《Rootkits：破坏 Windows 内核》。Addison-Wesley, 2005.
- Harley, David 等. 《Avien 企业恶意软件防御指南》。Burlington, MA: Syngress, 2007.
- Harley, David. 《OS X 漏洞利用与防御》。Burlington, MA: Syngress, 2008.
- Sikorski, Michael. 《实用恶意软件分析：拆解恶意软件的动手指南》。No Starch Press, 2012.
- Szor, Peter. *计算机病毒研究与防御的艺术*. Cupertino, CA: Symantec Press, 2005.
- Young, Adam, 和 Moti Yung. *恶意密码学：揭露密码病毒学*. Hoboken, NJ: John Wiley & Sons, 2004.

## 16.8 注释

1. NCSC，“计算机安全术语词汇表”，版本 1，1988 年，NCSC-TG-004 收录于 Rainbow 系列，www.fas.org/irp/nsa/rainbow/tg004.htm
2. GFI，“GFI 软件调查：40% 的中小企业因不安全的网络冲浪遭受安全漏洞”，EON。2011 年 10 月 12 日，http://eon.businesswire.com/news/eon/20111012005707/en/web-reputation/web-security-survey/small-business-web-monitoring-software
3. C. Alberts 和 A. Dorofee，“OCTAVE 威胁概况”，2001 年，www.cert.org/archive/pdf/OCTAVEthreatProfiles.pdf
4. R. Lemos，“好蠕虫重回议程”，Security Focus，2006 年 1 月 27 日，www.securityfocus.com/news/11373
5. John von Neumann，“自复制自动机理论”，第 1 部分：1949 年 12 月在伊利诺伊大学讲授的讲座记录，编者 A. W. Burks（伊利诺伊大学，1966 年）。Urbana, IL.
6. R. H. Morris，2005 年 7 月与 Robert Guess 的录音访谈。
7. D. Llet，“杀毒软件公司称有组织犯罪在线增长”，ZDnet News，2004 年 12 月 9 日，http://news.zdnet.com/2100-1009_22-5486201.html（URL 不活跃）。
8. J. Hoskin，“SEC 打击 Pump and Dump 诈骗者”，IT Week，2007 年 3 月 9 日，www.itweek.co.uk/vnunet/news/2185164/sec-targets-pump-dump-stock（网站已停用）。
9. SOPHOS. “法院对以色列间谍软件夫妇处以巨额罚款和监禁，Sophos 报道”，SOPHOS | Press Releases，2006 年 3 月 26 日，www.sophos.com/en-us/press-office/press-releases/2006/03/israelspyduo.aspx（URL 不活跃）。
10. Qiao Liang 和 Wang Xiangsui，《超限战》（北京：解放军文艺出版社，1999 年），www.terrorism.com/documents/TRC Analysis/unrestricted.pdf（需要访问权限）。
11. J. Rogin，“网络官员：中国黑客攻击‘任何事物’”，2007 年 2 月 13 日，www.fcw.com/article97658-02-13-07-Web&printLayout（URL 不活跃）。
12. Kenneth A. Minihan，“在参议院政府事务委员会前的准备声明”，1998 年 6 月 14 日，www.senate.gov/~gov_affairs/62498minihan.htm（URL 不活跃）。
13. 牛津英语词典，2007 年。
14. J. Dellinger，Usenet 帖子，1987 年 12 月 2 日，http://yarchive.net/risks/early_virus.html
15. F. Cohen，“计算机病毒实验”，1984 年，www.all.net/books/virus/part5.html
16. Virus Bulletin，“引导扇区病毒”，Virus Bulletin | Glossary。2013 年，www.virusbtn.com/resources/glossary/boot_sector_virus.xml
17. Microsoft，“如果您有宏病毒该怎么办”，2002 年 10 月 4 日，http://support.microsoft.com/kb/181080/en-us
18. M. E. Kabay，“逻辑炸弹，第 1 部分”。Network World | Security Newsletter。2002 年 8 月 21 日，www.networkworld.com/newsletters/sec/2002/01514405.html
19. 美国司法部，新泽西州美国检察官办公室，“不满的 UBS PaineWebber 员工被指控在公司电脑上引爆‘逻辑炸弹’”，2002 年 12 月 17 日。
20. 美国司法部新闻稿，“前 UBS 计算机系统经理因在公司网络上引爆‘逻辑炸弹’被判 97 个月监禁”，2006 年，www.usdoj.gov/usao/nj/press/files/pdffiles/duro1213rel.pdf（URL 不活跃）。
21. Kim Zetter，“逻辑炸弹引发韩国网络攻击”，Wired，2013 年 3 月 21 日，www.wired.com/threatlevel/2013/03/logic-bomb-south-korea-attack
22. E. Lai，“青少年使用蠕虫提升 MySpace.com 评分”，ComputerWorld，2005 年 10 月 17 日，www.computerworld.com/securitytopics/security/holes/story/0,10801,105484,00.html
23. Sheif Koussa，“安全代码审查技术：跨站脚本版”，Developer Connection | Jonathan Rozenblit，2013 年 3 月 5 日，http://blogs.msdn.com/b/cdndevs/archive/2013/03/05/security-code-review-techniques-cross-site-scripting-edition.aspx
24. Dancho Danchev，“Twitter 遭受多种 XSS 蠕虫变种攻击”，ZDNET | Security，2009 年 4 月 14 日，www.zdnet.com/blog/security/twitter-hit-by-multiple-variants-of-xss-worm/3125
25. SOPHOS，“2013 年安全威胁报告：新平台与变化中的威胁”。SOPHOS，2013 年 2 月 1 日，www.sophos.com/en-us/medialibrary/PDFs/other/sophossecuritythreatreport2013.pdf
26. Shafiqul Abidin、Rajeev Kumar 和 Varun Tiwari。“关于密码病毒学和密码学的综述报告”，《国际科学与工程研究杂志》，11，2012 年：1–4。
27. CERT。“咨询公告 CA-2001-26 Nimda 蠕虫”。原始发布日期：2001 年 9 月 18 日，修订：2001 年 9 月 25 日。来源：CERT/CC。www.cert.org/advisories/CA-2001-26.html
28. N. Weaver，“沃霍尔蠕虫：极快互联网瘟疫的潜力”，2001 年，www.iwar.org.uk/comsec/resources/worms/warhol-worm.htm
29. D. Moore、V. Paxson、S. Savage、C. Shannon、S. Staniford 和 N. Weaver，“Sapphire/Slammer 蠕虫的传播”，CAIDA。2003 年。www.caida.org/publications/papers/2003/sapphire/sapphire.html
30. S. Berinato，“打补丁并祈祷”，CSO Online。2003 年 8 月 14 日，www.csoonline.com.au/index.php/id;1337625166:fp;8:fp id;5
31. T. Vogt，“模拟和优化蠕虫传播算法”2003 年 9 月 29 日，http://web.lemuria.org/security/WormPropagation.pdf
32. “比格年：比格蠕虫历史，第 III 部分”，Infection Vectors 网站，2005 年 2 月，www.infectionvectors.com/vectors/year_of_the_beagle.htm
33. CommTouch，“恶意软件爆发趋势报告：Bagle/Beagle”。2007 年 3 月 6 日，www.commtouch.com/documents/Bagle-Worm_MOTR.pdf（URL 不活跃）。
34. Brian Krebs，“谁编写了 Flashback OS X 蠕虫？”Krebs on Security，2013 年 4 月 3 日，http://krebsonsecurity.com/2013/04/who-wrote-the-flashback-os-x-worm
35. Broderick Ian Aquilino，“Flashback OS X 恶意软件”，F-Secure，2012 年 10 月 5 日。www.f-secure.com/weblog/archives/Aquilino-VB2012.pdf

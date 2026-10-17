
攻击者如果获得了机器上的初始立足点，就可以利用该访问权限继续提升至更高权限。有多种方式可以实现这一点，并依赖于几种不同的向量，这些向量可以利用技术漏洞或人为错误。了解攻击者在获得系统访问权限时的思考方式，对于在检测和响应活动发生之前限制损害程度至关重要。

对于有抱负的渗透测试人员来说，权限提升在实践中学起来和用起来可能很困难。幸运的是，互联网上有许多资源可以用来获得这些攻击的实际操作经验。HackTheBox 和 TryHackMe 都有许多依靠获取立足点并提升到管理访问权限的机器。最棒的是？这些机器的 writeup 会发布出来，让你深入了解如何解决这些机器以及作者的思考过程。在测试过程中做大量笔记，以帮助你在阅读 writeup 之前识别遇到的障碍，以及如何在将来避免这些障碍。

## 注释

1. https://learn.microsoft.com/en-US/windows/security/identity-protection/access-control/local-accounts#default-local-system-accounts
2. https://web.archive.org/web/20160610153950/http://www.cs.yale.edu/homes/arvind/cs422/doc/unix-sec.pdf
3. https://linuxize.com/post/etc-shadow-file/
4. https://learn.microsoft.com/en-US/troubleshoot/windows-server/system-management-components/remote-server-administration-tools
5. https://github.com/samratashok/ADModule
6. https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/understand-security-groups
7. https://gtfobins.github.io/
8. https://learn.microsoft.com/en-us/troubleshoot/windows-server/identity/enable-kerberos-event-logging
9. https://redsiege.com/tools-techniques/2020/04/user-enumeration-part-3-windows/
10. https://learn.microsoft.com/en-us/troubleshoot/windows-server/identity/enable-kerberos-event-logging#enable-kerberos-event-logging-on-a-specific-computer
11. https://support.microsoft.com/en-us/topic/microsoft-tcp-ip-host-name-resolution-order-dae00cc9-7e9c-c0cc-8360-477b99cb978a
12. https://attack.mitre.org/techniques/T1135/
13. https://github.com/Pennyw0rth/NetExec
14. https://learn.microsoft.com/en-us/openspecs/windows_protocols/ms-gppref/2c15cbf0-f086-4c74-8b70-1f2fa45dd4be?redirectedfrom=MSDN
15. https://attack.mitre.org/software/S0521/
16. https://github.com/carlospolop/PEASS-ng/tree/master/winPEAS/winPEASexe#instructions-to-compile-you-own-obfuscated-version
17. https://attack.mitre.org/tactics/TA0003/

# 8 数据外泄（被攻破）

## 引言

在本章中，我们将探讨数据是如何从网络中被窃取的。你可以通过三种方式阅读本章：

- 1. 我是一名攻击者，我想了解一些窃取数据的好技术。
- 2. 我是一名分析师，我想了解更多有关在哪里寻找外泄证据的信息。
- 3. 我对网络安全感兴趣，想知道黑客如何以及为什么窃取数据。

重要的是要明白，黑客是有目的的。黑客攻击通常由以下因素驱动：

- 经济利益
- 政治动机
- 报复

也有一些人是出于好奇或展示技能，但通常黑客攻击都涉及获取金钱。包括美国在内的国家（被称为“国家行为者”）也积极从事黑客攻击活动。因此，某些为本国工作的个人被允许进行黑客攻击，因为这被合理化为与国家安全的使命相关。几乎所有国家都会经常从事间谍活动以保护其公民。

就美国而言，国家安全局（NSA，被戏称为“No-Such Agency”）从事进攻性网络行动以保护国家。NSA总部位于马里兰州安妮阿伦德尔县的米德堡。我住在大门14英里外，这是一个巨大的设施，在巴尔的摩华盛顿国际大道上拥有自己的出口（请不要走那个出口，否则你可能会被扣留和搜查）。对我来说，NSA是一个很好的工作场所，是该地区最大的本地雇主之一，也是马里兰州成为网络安全中心的原因之一。在NSA，工作非常稳定，大多数为政府工作的人会在那里度过整个职业生涯。NSA还通过其“国家安全局学术卓越中心”的指定，在大学网络安全课程中发挥着重要作用。马里兰大学全球校区（UMGC）就是这些中心之一，这为大学带来了许多好处，例如能够参加“攻破大楼”竞赛。

![](img/181571ad74cba0e6a2f38fcd2658651e_255_0.png)

**图8.1** 美国国家安全局从事进攻性网络行动。

就美国而言，NSA通过在其课程符合特定标准时对其项目进行认证，来影响大学和学院的网络安全学术项目。有三个国家网络安全学术卓越中心（NCAE-C）项目：

- 网络防御（CAE-CD）
- 网络研究（CAE-R）
- 网络作战（CAE-CO）

![](img/181571ad74cba0e6a2f38fcd2658651e_255_1.png)

**图8.2** 美国国家安全局从事进攻性网络行动。

网络作战本质上是进攻性的，更侧重于渗透测试、红队和漏洞利用。网络防御则侧重于蓝队相关任务，这些任务有助于保护和保障系统安全。网络研究则更多涉及网络课程的博士级研究。美国通过国家科学基金会（NSF）的资金支持，鼓励从中学到博士项目的学生参与网络相关领域。进入军队的人通常最终会担任网络工作角色，网络正成为各军种军事行动的重要组成部分。

如果你想攻击美国以外的组织或国家，你最好成为美国军队或NSA的一员，并获得主管的授权。美国不允许个人进行流氓黑客攻击，即使他们针对的是敌对外国国家。如果你在美国从事这种邪恶活动（我可没有），你可能会预见到执法机构或某个“三个字母的机构”来你家拜访。有些人认为，美国以外的其他国家实际上允许甚至鼓励其公民从事这种非法活动。就美国而言，其执法机构对处于美国管辖范围之外的这些个人几乎无能为力。除非攻击者所在国政府同意引渡，否则美国对攻击者几乎没有追索权。如果美国能够归因并确定攻击是“国家资助的”且来自敌对国家，那么他们可以尝试对该国施加政治压力，但他们往往可能否认任何责任。

公司最不想失去的是他们的知识产权（IP）。想想可口可乐的配方或肯德基的食谱。想想处方药的一些配方或苹果设备的图纸可能有什么价值。对于诺斯罗普·格鲁曼、波音或洛克希德·马丁这样的公司来说，战斗机设计图的丢失不仅可能影响其股票价值，还可能影响国家安全。像战斗机蓝图、作战计划和士兵的实际位置这样的信息，可能会危及人们的生命。

![](img/181571ad74cba0e6a2f38fcd2658651e_257_0.png)

图8.5 死星蓝图。

我们在本章和其他章节中讨论过的事情之一是国家行为或国家资助的黑客攻击。为什么一个国家会想要侵入承包商的系统并窃取其知识产权？如果你想一想这些国防部承包商，他们通常拥有一大批经验丰富、薪酬高昂的员工。他们的员工享有健康和牙科福利、假期、带薪病假以及学费报销等其他福利。与其以高昂的成本雇佣最优秀、最聪明的人才来按极其昂贵的合同开发战斗机，为什么不训练一些黑客侵入美国的一家高级承包商并从他们那里窃取知识产权呢？虽然这当然是一种不道德的方法，但总体而言绝对更便宜。

![](img/181571ad74cba0e6a2f38fcd2658651e_257_1.png)

图8.6 文章链接：https://www.nydailynews.com/2015/01/20/chinese-hackers-stole-f-35-fighter-jet-blueprints-in-pentagon-hack-edward-snowden-documents-claim/

## 入侵的原因

有时，入侵可能源于常用软件，漏洞被公开后会产生一种竞赛态势，迫使公司立即保护其系统。黑客通常会维护一个“蓄势待发的数据库”，当漏洞被公开披露时，这个数据库会给他们带来优势。这里有一个例子可以说明其工作原理。假设一个黑客扫描一个网站，发现它使用了特定版本的`Apache`，但该版本没有已知的漏洞利用方法。黑客可以保留一份使用该版本的目标列表，然后当漏洞公开时，他们可以查看列表找到使用该软件的人并对其进行利用。

![](img/181571ad74cba0e6a2f38fcd2658651e_258_0.png)

**图8.7** `Apache`服务器的版本信息。

如果公司使用的是存在漏洞的软件，如`log4j`或特定版本的`Apache Struts`，他们就有被入侵的风险。曾经，`log4j`漏洞对大量联网系统构成了严重的安全风险。我的许多朋友和同事在CrowdStrike和Booz Allen等公司工作，在`log4j`漏洞被发现后的几个月里，他们忙于进行事件响应、计算机取证和修复。`Apache Struts`导致了Equifax被入侵，进而导致大多数美国人的社会安全号码被泄露。具体来说，是`CVE-2017-5638`漏洞导致了这次入侵。

![](img/181571ad74cba0e6a2f38fcd2658651e_258_1.png)

**图8.8** Synopsys关于`Apache Struts` `CVE-2017-5638`漏洞的博客文章。

有时，公司和组织非常重视网络安全，并努力保持对其系统的监控、更新、安全和可靠。即使有所有这些保障措施，有时第三方或供应链攻击仍然可能导致入侵。在一家大型全国性零售商的事件中，攻击者通过由一家小型承包商维护的暖通空调系统进入了网络。这就是业界所说的“零信任”发挥作用的地方。当公司使用第三方、合并或收购其他公司时，其安全策略和保障措施可能面临风险。当发生收购或合并时，如果新系统得到了妥善保护，公司仍可能变得脆弱。

![](img/181571ad74cba0e6a2f38fcd2658651e_258_2.png)

**图8.9** 文章链接：[https://krebsonsecurity.com/2014/02/target-hackers-broke-in-via-hvac-company/](https://krebsonsecurity.com/2014/02/target-hackers-broke-in-via-hvac-company/)。

我们讨论了易受攻击的软件、并购以及第三方供应商带来的威胁，这些都可能让公司和组织留下未曾预料到的安全漏洞。此外还有供应链攻击的威胁，即一家公司使用的软件来自某个受信任的供应商，而该供应商后来遭到入侵。SolarWinds 就是这种情况，它拥有庞大的客户群使用其网络管理和监控软件。这些被归因于俄罗斯的国家级攻击者入侵了 SolarWinds，然后在软件更新中植入了后门程序；当客户部署这些带有恶意代码的更新时，他们也被入侵了。

![](img/181571ad74cba0e6a2f38fcd2658651e_259_0.png)

**图 8.10** 文章链接：[https://www.businessinsider.com/solarwinds-hack-explained-government-agencies-cyber-security-2020-12](https://www.businessinsider.com/solarwinds-hack-explained-government-agencies-cyber-security-2020-12).

那么，为什么不一直更新所有软件呢？嗯，一般来说，你应该这样做。而且有时你甚至被迫这样做，比如 iPhone 或 XBOX。XBOX 引出了一个有趣的难题：为什么微软强制要求你更新其游戏主机才能使用，却不对使用 Microsoft Windows 的最终用户施加同样的要求呢？嗯，Microsoft Windows 运行在无数电脑厂商的硬件平台上，基本上需要支持无限多种不同的硬件配置。这就是 MacBook Pro、iPhone 和 XBOX 更容易提供支持的原因，因为厂商同时控制硬件和操作系统（OS）。很多时候，更新也许能保护你的系统，但也可能破坏你的应用程序。对 IT 人员来说，这是一场持续的猫鼠游戏：他们要不断更新系统，而且几乎每次更新后都需要对应用程序进行功能测试。这种持续不断的战斗，正是网络安全职业在撰写本文时看起来相当稳定的一个重要原因。

## 数据外泄 101

现在我们来讨论黑客如何窃取数据，以及他们使用哪些技术来实施这些行为。首先，让我们讨论黑客应该瞄准什么，以及“最好的东西”可能在哪里。如果攻击者具备入侵系统的技能，他们还需要知道“战利品”可能在哪里。

```text
meterpreter > ls
Listing C:\
```

| 模式 | 大小 | 类型 | 上次修改时间 | 名称 |
|---|---|---|---|---|
| 40777/rwxrwxrwx | 4096 | dir | 2008-01-19 04:34:18 -0500 | $Recycle.Bin |
| 100444/r--r--r-- | 8192 | fil | 2012-09-10 22:01:39 -0400 | BOOTSECT.BAK |
| 40777/rwxrwxrwx | 8192 | dir | 2012-09-10 22:01:37 -0400 | Boot |
| 0000/--------------- | 0 | fil | 1969-12-31 19:00:00 -0500 | Documents and Settings |
| 40777/rwxrwxrwx | 4096 | dir | 2008-01-31 04:40:52 -0500 | PerfLogs |
| 40555/r-xr-xr-x | 4096 | dir | 2008-01-19 04:40:52 -0500 | Program Files |
| 40777/rwxrwxrwx | 4096 | dir | 2008-01-19 04:40:52 -0500 | ProgramData |
| 40777/rwxrwxrwx | 4096 | dir | 2012-09-10 21:02:20 -0400 | System Volume Information |
| 40555/r-xr-xr-x | 4096 | dir | 2008-01-19 04:45:53 -0500 | Users |
| 40777/rwxrwxrwx | 16384 | dir | 2008-01-19 04:40:53 -0500 | Windows |
| 100444/r--r--r-- | 333203 | fil | 2012-01-19 04:31:37 -0400 | bootmgr |
| 40777/rwxrwxrwx | 0 | dir | 2015-01-31 19:39:04 -0500 | inetpub |
| 100666/rw-rw-rw- | 2460368896 | fil | 2012-09-10 20:02:20 -0400 | pagefile.sys |
| 40777/rwxrwxrwx | 4096 | dir | 2012-09-12 18:40:53 -0400 | share |
| 40777/rwxrwxrwx | 12288 | dir | 2015-01-31 19:25:55 -0500 | xampp |

**图 8.11** `Meterpreter` 目录列表。

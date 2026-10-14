
最基础的安全设备是`firewall`（防火墙）。防火墙是网络与外部世界之间的屏障。有时防火墙以独立服务器的形式存在，有时是路由器，有时是运行在机器上的软件。无论其物理形式如何，防火墙都会过滤进入和离开网络的流量。`proxy server`（反向代理服务器）通常与防火墙一起使用，以隐藏内部网络的 IP 地址，并向外部世界展示一个单一的 IP 地址（即其自身）。

防火墙和反向代理服务器通过分析流量（至少是入站流量，通常也包括出站流量）来保护网络边界，并阻止管理员禁止的流量。这两种防护措施通常会通过`intrusion detection system`（IDS，入侵检测系统）来增强。IDS 仅监控流量，寻找可疑活动，这可能表明一次入侵尝试正在进行。我们将在第 9 章中详细探讨这些技术及其他技术。

### 安全活动

除了设备，还有安全活动。`Authentication`（身份验证）是最基础的安全活动。它仅仅是确定用户或其他系统（如用户名和密码）提供的凭证是否被授权访问相关网络资源的过程。当你使用用户名和密码登录时，系统会尝试验证这些凭证。如果验证通过，你将获得访问权限。

另一个至关重要的防护措施是`auditing`（审计），即审查日志、记录和程序，以确定这些项目是否符合标准。该活动将在本书的许多章节中被提及，并在几个章节中成为重点。

我们刚刚介绍的安全与黑客术语仅是计算机安全术语的入门，但它们为进一步学习提供了很好的起点。随着阅读的深入，更多术语会在文中适时出现，并在书末的术语表中汇总。

## 概念与方法

你对安全的态度会影响随后的所有安全决策，并为整个组织的网络安全基础设施定下基调。在深入探讨各种网络安全范式之前，让我们先花点时间审视一些应贯穿于你安全思维的概念。

第一个概念是`CIA triangle`。它并不指涉及中央情报局（CIA）的秘密行动，而是指安全的三大支柱：保密性、完整性和可用性。当你思考安全时，思维应始终围绕这三大原则展开：首先，你是否保护了数据的保密性？其次，你的做法是否保证了数据的完整性？最后，你的做法是否仍能让授权用户轻松访问数据？

虽然 CIA 三角形是所有安全课程和认证的基石，但已有更为复杂的模型被提出。McCumber 块（McCumber cube）是一种多维度描述安全的方法。McCumber 块是一个三维立方体，考虑网络安全的所有方面。它在 2004 年的著作 *Assessing and Managing Security Risk in IT Systems: A Structured Methodology* 中详细阐述。该模型以三个维度来看待安全：目标、信息状态和防护措施。McCumber 块的优势在于它自然将 CIA 三角形扩展为三维空间。这有利于利用已为人知且易于理解的 CIA 三角形，从而更顺畅地过渡到 McCumber 块，进而构建基于 McCumber 块的分类体系。任何分类体系都必须易于学习和应用，才能在安全专业人员中有效。你可以在图 1.1 中看到 McCumber 块：

![Figure 1.1 The McCumber cube. ¶  ¶ A diagram depicts the McCumber cube. The following components are shown along the dimensions of the cube. Transmission; Storage; Processing; Confidentiality; Integrity; Availability; Education, Training, and awareness; Policy and practices; and Technology. ¶ ](img/01fig01.jpg)

**Figure 1.1** The McCumber cube. ¶ 

另一个需要牢记的重要概念是`least privileges`（最小权限）。这意味着网络中每个用户或服务应仅拥有完成工作所需的最少权限/访问权。除非绝对必要，否则不应授予任何人访问权限。

网络安全范式可以根据安全措施的范围（边界、分层）或系统的主动性进行分类。

在`边界安全`（perimeter security）方法中，大部分安全努力集中在网络的边界上。这种做法可能包括防火墙、反向代理服务器、密码策略或任何旨在使未经授权访问网络变得更困难的技术或程序。在这种方法中，几乎没有努力保护网络内部的系统。虽然边界被保护，但网络内部的各个系统往往仍然容易受到攻击。

关于边界安全还有若干物理安全问题，包括围栏、闭路电视、保安、锁具等，具体取决于组织的安全需求。

边界方法显然存在缺陷，那么为何仍有公司采用它？预算有限或网络管理员经验不足的小型组织可能会采用边界方法。对于不存储敏感数据的小型组织，边界方法可能足够，但在大型企业环境中很少奏效。

`分层安全`（layered security）方法是指不仅保护网络边界，还保护网络内的每个系统。服务器、工作站、路由器和集线器等所有网络组件都受到保护。实现方式之一是将网络划分为多个段，并像对待独立网络一样保护每个段，这样如果边界防护被突破，内部系统不会受到连锁影响。这是首选方法，应在可能的情况下使用。

- [费曼学习法](https://wiki.example.org/feynmans_learning_method)的灵感源于诺贝尔物理奖获得者**Richard Feynman**。

1. 运用费曼技巧，你只需花上`20 min`就能深入理解知识点，而且记忆深刻，*难以遗忘*。

```
if (condVar > someVal) {console.log("xxx")}
```

网络安全是一个复杂且不断发展的领域。实践者必须紧跟新出现的威胁和解决方案，并主动评估风险并保护他们的网络。理解网络安全的第一步是了解网络面临的实际威胁。如果没有对系统可能受到的威胁的真实认识，您将无法有效保护它们。同时，您也必须获得安全专业人士和试图破坏您安全的对手所使用的术语的基本理解。

## 测试您的技能

### 选择题

**1.** 当您向非技术经理解释安全时，她对计算机安全持有极端观点。下列哪项是本章讨论的关于计算机安全的极端观点之一？

**A.** 政府将负责安全。

**B.** Microsoft 将负责安全。

**C.** 对您系统没有迫在眉睫的危险。

**D.** 如果您使用 Linux，则没有危险。

**2.** 您刚刚接手一所小型社区学院的网络安全管理员职务。在制定网络防御措施之前，您需要做什么？

**A.** 取得相应的安全认证

**B.** 了解需要防御的危害

**C.** 完成这本教材

**D.** 获得外部顾问的帮助

**3.** Mary 正在向大一新生讲授入门级网络安全课程，她正在向他们解释主要威胁。下列哪项不是三大主要威胁类别之一？

**A.** 试图入侵系统的行为

**B.** 在线拍卖欺诈

**C.** 拒绝服务攻击

**D.** 计算机病毒

**4.** 能够定义攻击术语是网络安全专业人员的重要技能。什么是计算机病毒？

**A.** 未经您授权而下载到您系统的任何程序

**B.** 任何自我复制的程序

**C.** 任何对您系统造成损害的程序

**D.** 任何可以修改您的 Windows 注册表的程序

**5.** 能够定义攻击术语是网络安全专业人员的重要技能。什么是间谍软件（spyware）？

**A.** 任何监控您系统的软件

**B.** 仅指记录键盘的软件

**C.** 任何用于收集情报的软件

**D.** 仅指监控您浏览的网站的软件

**6.** 什么是渗透测试员（penetration tester）？

**A.** 未被发现的黑客

**B.** 通过假装合法密码来入侵系统的人

**C.** 用于测试系统漏洞的黑客

**D.** 业余黑客

**7.** 伊丽莎白正在向课堂解释各种黑客术语，她正在讨论电话系统的黑客历史。什么是电话系统黑客行为的术语？

**A.** 电信黑客行为

**B.** 黑客行为

**C.** 破解

**D.** 窃听（Phreaking）

**8.** 什么是恶意软件（malware）？

**A.** 具有恶意目的的软件

**B.** 功能不正常的软件

**C.** 损害您系统的软件

**D.** 未为您系统正确配置的软件

**9.** 什么是战争驱动（war-driving）？

**A.** 驾车寻找计算机工作

**B.** 驾车使用无线连接进行黑客攻击

**C.** 驾车寻找无线网络进行黑客攻击

**D.** 驾车寻找对手黑客

**10.** 涉及利用说服和欺骗让人提供信息以帮助 compromising security 的黑客技术名称是什么？

**A.** 社会工程

**B.** 欺骗

**C.** 人类情报

**D.** 软黑客

**11.** 互联网上有许多威胁。哪一种目前是最常见的（虽然后期可能变化，但某些威胁始终更为常见）？

**A.** 拍卖欺诈

**B.** 窃听（Phreaking）

**C.** 计算机病毒

**D.** 非法软件

**12.** 安全的三种方法是什么？

**A.** 边界、分层、混合

**B.** 高安全、中安全、低安全

**C.** 内部、外部和混合

**D.** 边界、完整、无

**13.** 定义安全策略是保障网络安全的重要步骤。您正在根据它们的安全方法对设备进行分类。入侵检测系统（IDS）属于以下哪种类型？

**A.** 主动安全

**B.** 边界安全

**C.** 混合安全

**D.** 良好安全实践

**14.** 下列哪项是最基础的安全活动？

**A.** 身份验证

**B.** 防火墙

**C.** 密码保护

**D.** 审计

**15.** 最理想的安全方法是以下哪种组合？

**A.** 边界和动态

**B.** 分层和动态

**C.** 边界和静态

**D.** 分层和静态

**16.** 根据计算机安全学院（Computer Security Institute）对 223 名计算机专业人员的调查，以下哪项最常被受访者提及为问题？

**A.** 内部系统

**B.** 员工滥用

**C.** 路由器

**D.** 互联网连接

**17.** 哪种隐私法对计算机安全有影响？

**A.** 任何州隐私法

**B.** 适用于您组织的任何隐私法

**C.** 任何隐私法

**D.** 任何联邦隐私法

**18.** 第一个计算机应急响应团队隶属于哪所大学？

**A.** 马萨诸塞科技学院（MIT）

**B.** 卡内基梅隆大学

**C.** 哈佛大学

**D.** 加州技术大学

**19.** 对 *sensitive information*（敏感信息）的最佳定义是什么？

**A.** 任何对国家安全产生影响的信息

**B.** 任何价值超过 1,000 美元的信息

**C.** 任何信息若被未授权人员获取可能以任何方式损害您的组织

**D.** 任何受隐私法保护的信息

**20.** 哪项是获取计算机病毒详细信息的主要资源？

**A.** MIT 病毒库

**B.** Microsoft 病毒库

**C.** F-Secure 病毒库

**D.** 国家病毒库

### 练习

**Exercise 1.1:** 这个月发生了多少次病毒攻击？

1. 使用诸如 [www.f-secure.com](http://www.f-secure.com) 等网站查找近期计算机病毒爆发情况。

2. 过去 7 天内发生了多少次病毒爆发？

3. 过去 30 天、90 天和 1 年内发生了多少次爆发？

4. 病毒攻击的频率是否在增加？

**Exercise 1.2:** 学习作为间谍软件的 Cookie

1. 了解 Cookie 存储的信息类型，以下网站可能有帮助：

[www.allaboutcookies.org](http://www.allaboutcookies.org)

[www.howstuffworks.com/cookie1.htm](http://www.howstuffworks.com/cookie1.htm)

2. 简要写一篇文章，说明 Cookie 如何侵犯隐私。

**Exercise 1.3:** 黑客术语

1. 使用 *Hacker’s Dictionary*（[`www.outpost9.com/reference/jargon/jargon_toc.html`](http://www.outpost9.com/reference/jargon/jargon_toc.html)）定义以下黑客术语：

1. Alpha geek  
2. Grok  
3. Red Book  
4. Wank  

**Exercise 1.4:** 使用安全资源  

1. 使用本章中列出的首选网络资源，在该资源中找到三份政策或程序文档。

2. 列出您选择的文档。

3. 写一篇简短的文章，说明这些文档对贵组织的安全为何重要。

**Exercise 1.5:** Learning About the Law

1. 使用网络、期刊、书籍或其他资源，查找您所在州或领地是否有专门牌计算机安全的法律。以下网站可能有帮助：

[www.pbs.org/wgbh/pages/frontline/shows/hackers/blame/crimelaws.html](http://www.pbs.org/wgbh/pages/frontline/shows/hackers/blame/crimelaws.html)

[www.cybercrime.gov](http://www.cybercrime.gov)

2. 列出您找到的三条法律，并为每条法律提供一段简短的描述（一句或两句）。

### Projects

**Project 1.1:** Learning About a Virus

1. 使用附录 A 中的网络资源以及 [www.f-secure.com](http://www.f-secure.com) 等网站，找到过去 6 个月内发布的病毒。

2. 研究该病毒的传播方式及其造成的损害。

3. 撰写一篇简短（半页到一页）的论文，说明该病毒的工作原理、传播方式以及其他重要信息。

**Project 1.2:** Considering the Law (a Group Project)

撰写一份您希望通过的计算机法律描述，并包含其实施、执行以及正当性的具体细节。

**Project 1.3:** Recommending Security

1. 使用网络、期刊或书籍，查找来自任何可信来源（如 SANS Institute）的安全建议。本章“Online Security Resources”章节中提到的网站也是不错的选择。

2. 列出五条安全建议。

3. 说明您对这五条建议的赞同或不同意见。

### Case Study

在本案例研究中，我们将考虑一位负责小型、面向家庭的视频店网络管理员。该店不属于连锁店，安全预算非常有限。它有五台供员工使用以查看电影的机器，以及一台用于存储集中记录的服务器。该服务器位于经理的办公室。管理员采取了以下安全措施：

* 每台机器都升级到 Windows 10，并开启了个人防火墙。

* 在所有机器上安装了防病毒软件。

* 在服务器上添加了磁带备份，磁带存放在经理办公室的文件柜中。

* 已取消员工机器的 Internet 接入。

现在考虑以下问题：

1. 这些行动实现了什么效果？

2. 你可能会推荐哪些额外的措施？

# Chapter 2. Networks and the Internet

Chapter Objectives

After reading this chapter and completing the exercises, you will be able to do the following:

* Identify each of the major protocols used in network communication (for example, `FTP` and `Telnet`) and what use you can make of each of them

* Understand the various connection methods and speeds used on networks

* Compare and contrast a hub and a switch

* Identify what a router is and what it’s used for

* Understand how data is transmitted over a network

* Explain how the Internet works and the use of IP addresses and URLs

* Recount a brief history of the Internet

* Use network utilities such as `ping`, `IPConfig`, and `tracert`

* Describe the OSI model of network communication and the use of MAC addresses

## Introduction

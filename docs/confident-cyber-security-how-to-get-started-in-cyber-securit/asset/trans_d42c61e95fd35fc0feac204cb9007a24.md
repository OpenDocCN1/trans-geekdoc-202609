

## 参考文献

[1] Warrell, H and Wright, R (2019) Balfour Beatty sacked from MI6 refurbishment contract, *Financial Times*, 27 December, [`www.ft.com/content/81d4ac8c-28d9-11ea-9a4f-963f0ec7e134`](http://www.ft.com/content/81d4ac8c-28d9-11ea-9a4f-963f0ec7e134) (archived at [`https://perma.cc/234D-3JJT`](https://perma.cc/234D-3JJT))

[2] Ritschel, C (2019) Mother releases video of hacker talking to eight-year-old child through Ring camera, *Independent*, 12 December, [`www.independent.co.uk/news/world/americas/ring-camera-video-hack-security-mississippi-child-a9244326.html`](http://www.independent.co.uk/news/world/americas/ring-camera-video-hack-security-mississippi-child-a9244326.html) (archived at [`https://perma.cc/64Z5-QJ62`](https://perma.cc/64Z5-QJ62))

[3] Kellon, L (2018) MiSafes' child-tracking smartwatches are 'easy to hack', BBC News, 15 November, [`www.bbc.co.uk/news/technology-46195189`](http://www.bbc.co.uk/news/technology-46195189) (archived at [`https://perma.cc/PN89-X9U5`](https://perma.cc/PN89-X9U5))

[4] Anderson, N (2006) Steal David Beckham's car with a laptop, Ars Technica, 5 April, [`https://arstechnica.com/uncategorized/2006/05/6750-2`](https://arstechnica.com/uncategorized/2006/05/6750-2)/ (archived at [`https://perma.cc/4D4R-M2D8`](https://perma.cc/4D4R-M2D8))

[5] Greenberg, A (2015) Hackers remotely kill a Jeep on the highway – with me in it, Wired, 21 July, [`www.wired.com/2015/07/hackers-remotely-kill-jeep-highway`](http://www.wired.com/2015/07/hackers-remotely-kill-jeep-highway) (archived at [`https://perma.cc/WRP9-WGLH`](https://perma.cc/WRP9-WGLH))

[6] FBI (2016) Motor vehicles increasingly vulnerable to remote exploits, FBI Public Service Announcement, 17 March, [`www.ic3.gov/media/2016/160317.aspx`](http://www.ic3.gov/media/2016/160317.aspx) (archived at [`https://perma.cc/49CK-BAZB`](https://perma.cc/49CK-BAZB))

[7] DEFCON Conference (2019) Jmaxxz – your car is my car (online video), [`www.youtube.com/watch?v=w8SG2V3n4-U`](http://www.youtube.com/watch?v=w8SG2V3n4-U) (archived at [`https://perma.cc/3QHB-JXUU`](https://perma.cc/3QHB-JXUU))

[08](#04_toc01.xhtml#fm_toc_078)

不存在单一的安全解决方案能够保护一个组织。正如我们所见，安全依赖于一套分层的防御体系，结合对这些防御措施的监控和测试，以确保它们维持所需的防御、检测和响应水平。建立安全计划的第一步是了解你拥有哪些信息资产，以及它们对组织、其客户或顾客，以及那些可能寻求访问和滥用信息的人代表什么价值。编目资产并执行风险评估（如[第2章](#09_chapter02.xhtml#ch02_sec_001)所述）是确定为哪些系统和资产分配何种级别的安全性，从而决定实施哪些控制措施的基础部分。使用框架（如美国国家标准与技术研究院（NIST）网络安全框架或ISO 27001）将帮助许多组织完成信息资产分类、风险评估和确定适当控制措施的过程（我们将在[第12章](#23_chapter12.xhtml#ch12_sec_001)中讨论）。在本章中，我们将探讨组织用来更好地保护自己的常见安全控制和实践。

## [防火墙](#04_toc01.xhtml#fm_toc_079)

防火墙通常被视为网络安全的第一道防线，是一个旨在保护内部安全网络免受开放互联网上威胁的网关。防火墙以硬件和/或软件的形式位于网络上，监控进出的流量。使用一组规则，它确定哪些流量被授权或预期进入网络以及可以去往何处。这些规则围绕数据源、目标和端口展开。一个简单的类比是将共享建筑中的安保前台想象为防火墙；安保前台根据来访者的身份和可信度决定谁可以进入以及他们能在建筑内去往何处。

## [反病毒软件](#04_toc01.xhtml#fm_toc_080)

反病毒软件也可以理解为反恶意软件。它传统上通过检测和移除计算机病毒和恶意软件来工作，在系统后台运行并搜索已知恶意软件的特征码（如果你想象每个恶意软件都有一个指纹，它就是在搜索这个指纹）。当然，其一个关键局限性是它只能检测和移除已知恶意软件；它使用已知恶意软件特征码数据库，因此当新威胁出现时，其特征码不会在数据库中。由于这一局限性，反病毒防护已演进为监控系统并捕捉异常行为：当系统做出异常操作时，反病毒软件会被触发。机器学习的进步已被纳入反病毒软件，使系统能够从新数据、行为和特征码中学习。

## [网络分段](#04_toc01.xhtml#fm_toc_081)

网络分段是组织防御体系中非常重要的一个要素，基于这样的理解：组织不仅必须尝试防范攻击，还必须为一旦（或当）遭到入侵时的损害控制做好准备。网络分段意味着如果组织或其网络的某一部分被攻破，这种攻破可以被遏制，而不会感染整个网络。这还允许对组织进行逻辑分段，使不同部门拥有不同的网段。它与所谓的“最小权限”原则协同工作——即用户只能访问完成工作所需的最小权限——这意味着信息访问可以更容易地按“需知”基础进行构建。它还允许对信息访问进行更好的监控和审计。这优于扁平网络，在扁平网络中没有任何分段，人们可以在网络中更自由地移动，访问可能不应向他们开放的信息。

## [策略和程序](#04_toc01.xhtml#fm_toc_083)

组织使用策略和程序来记录和传达关于网络安全的期望、责任和承诺。它们可能不令人兴奋，但很重要，作为确保组织已传达对人们期望的一种方式——例如，互联网可接受使用、密码管理、发生事件时该怎么做，以及谁负责网络安全。一些策略是法律要求的或出于合规目的而要求的，它们也应到位以便为员工和组织提供法律保护。不幸的是，策略经常被忽视或忽略。2019年，ClubCISO的研究发现，参与调查的53%的高级信息安全负责人表示，他们认为他们的策略是无效的、休眠的，或者不影响日常行为。^([2](#18_chapter08.xhtml#ch08_en2)) 为了使策略有效且有用，重要的是要保持其最新，使用无行话且简洁的语言编写，让人们知道在组织中哪里可以找到它们（例如，在内网上易于导航到），并且相关信息在其中易于查找。

## [日志记录](#04_toc01.xhtml#fm_toc_084)


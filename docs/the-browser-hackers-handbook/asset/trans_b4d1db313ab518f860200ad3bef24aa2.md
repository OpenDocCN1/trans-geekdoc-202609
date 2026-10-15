
25. Ravishankar Borgaonkar. (2013). USSD代码在移动网络中的错误使用。2013年7月10日检索自 [`https://www.troopers.de/wp-content/uploads/2012/12/TROOPERS13-Dirty_use_of_USSD_codes_in_cellular-Ravi_Borgaonkor.pdf`](https://www.troopers.de/wp-content/uploads/2012/12/TROOPERS13-Dirty_use_of_USSD_codes_in_cellular-Ravi_Borgaonkor.pdf)

26. W3C. (2011). UriSchemes—W3C Wiki。2013年8月12日检索自 [`http://www.w3.org/wiki/UriSchemes`](http://www.w3.org/wiki/UriSchemes)

27. Mozilla. (2013). Bug 873709—Firefox v23—Disable JavaScriptCheck Box Removed from Options/Preferences Applet。2013年8月12日检索自 [`https://bugzilla.mozilla.org/show_bug.cgi?id=873709`](https://bugzilla.mozilla.org/show_bug.cgi?id=873709)

28. Matasano Security. (未知年份). JavaScript加密被认为有害。2013年8月12日检索自 [`http://www.matasano.com/articles/javascript-cryptography/`](http://www.matasano.com/articles/javascript-cryptography/)

29. Vladimir Vorontsov. (2013). @ONsec_Lab: XSS如何击败数字签名。2013年7月20日检索自 [`http://lab.onsec.ru/2013/04/how-xss-can-defeat-your-digital.html`](http://lab.onsec.ru/2013/04/how-xss-can-defeat-your-digital.html)

30. Emily Stark, Mike Hamburg, and Dan Boneh. (2009). Stanford Javascript Crypto Library。2013年8月12日检索自 [`https://crypto.stanford.edu/sjcl/`](https://crypto.stanford.edu/sjcl/)

31. PaX Team. (2003). 地址空间布局随机化。2013年8月12日检索自 [`http://pax.grsecurity.net/docs/aslr.txt`](http://pax.grsecurity.net/docs/aslr.txt)

32. Microsoft. (2009). 理解DEP作为缓解技术的一部分 - Security Research & Defense––Site Home––TechNet blogs。2013年8月12日检索自 [`http://blogs.technet.com/b/srd/archive/2009/06/05/understanding-dep-as-a-mitigation-technology-part-1.aspx`](http://blogs.technet.com/b/srd/archive/2009/06/05/understanding-dep-as-a-mitigation-technology-part-1.aspx)

33. Microsoft. (未知年份). /SAFESEH (Image has Safe Exception Handlers)。2013年8月12日检索自 [`http://msdn.microsoft.com/en-us/library/9a89h429(v=vs.80).aspx`](http://msdn.microsoft.com/en-us/library/9a89h429\(v=vs.80\).aspx)

34. Microsoft. (2009). 防止用户模式堆栈损坏漏洞的利用。2013年8月14日检索自 [`http://blogs.technet.com/b/srd/archive/2009/08/04/preventing-the-exploitation-of-user-mode-heap-corruption-vulnerabilities.aspx`](http://blogs.technet.com/b/srd/archive/2009/08/04/preventing-the-exploitation-of-user-mode-heap-corruption-vulnerabilities.aspx)

35. Alexander Sotirov. (未知年份). JavaScript堆栈风水。2013年8月12日检索自 [`http://www.phreedom.org/research/heap-feng-shui/heap-feng-shui.html`](http://www.phreedom.org/research/heap-feng-shui/heap-feng-shui.html)

36. Jason Evans. (2012). jemalloc。2013年8月12日检索自 [`http://www.canonware.com/jemalloc/`](http://www.canonware.com/jemalloc/)

37. Wikipedia. (2013). 局部性原理 - Wikipedia，自由的百科全书。2013年8月12日检索自 [`http://en.wikipedia.org/wiki/Principle_of_locality`](http://en.wikipedia.org/wiki/Principle_of_locality)

38. Patroklos Argyroudis and Chariton Karamitas. (2012). 利用jemalloc内存分配器：拥有Firefox的堆栈。2013年8月12日检索自 [`https://media.blackhat.com/bh-us-12/Briefings/Argyoudis/BH_US_12_Argyroudis_Exploiting_the_%20jemalloc_Memory_%20Allocator_WP.pdf`](https://media.blackhat.com/bh-us-12/Briefings/Argyoudis/BH_US_12_Argyroudis_Exploiting_the_%20jemalloc_Memory_%20Allocator_WP.pdf)

39. CVE. (2013). CVE-2013-0753。2013年8月12日检索自 [`http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2013-0753`](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2013-0753)

40. Mozilla. (2013). 814001—(CVE-2013-0753) [FIX] XMLSerializer Use-After-Free Remote Code Execution Vulnerability (ZDI-CAN-1608)。2013年8月12日检索自 [`https://bugzilla.mozilla.org/show_bug.cgi?id=814001`](https://bugzilla.mozilla.org/show_bug.cgi?id=814001)

# Chapter 7

# 攻击扩展

在上一章中，你探索了直接攻击浏览器。本章进一步沿着功能链向前，展示如何攻击浏览器扩展。

浏览器扩展是可选的软件，可以为浏览器添加或移除功能。第三方，如防病毒供应商或社交网络站点，通常创建扩展。它们可以由用户自愿安装，也可以在安装其他程序时作为副作用被安装。

历史上，浏览器扩展并未以安全为考虑进行开发。扩展可以访问敏感用户信息、特权API，甚至底层操作系统。缺乏安全关注以及特权上下文，使扩展成为易受攻击的目标。

浏览器扩展非常流行，攻击面相当大。扩展的漏洞类别差异很大，从命令注入到经典的跨站脚本（XSS）漏洞不等。利用技术的复杂度也各不相同。

重要的是，扩展会与加载的网页交互，并创建易于利用的攻击路径。本章通过利用Firefox和Chrome扩展中的漏洞，探讨这些攻击路径。

# 理解扩展解剖结构

让我们探索扩展是什么以及它们如何因浏览器而异。如果你对扩展在浏览器生态系统中的作用有充分了解，可以直接跳到本章更活跃的攻击部分。

通过将非必要功能的开发交给第三方，浏览器开发者可以专注于核心功能。这可以减少代码膨胀和潜在的错误。显然，需要填补浏览器与不同用户需求之间的差距。这就是扩展在浏览器故事中的作用。

用于实现扩展的技术是常见的，行业内的人员应该相对熟悉它们。它们可以用多种语言编写，最可能最不令人惊讶的支持语言是JavaScript。

扩展会改变浏览体验。它们可以通过修改菜单、修改页面、创建弹窗等方式改变用户界面。扩展可以从Firefox添加-ons和Chrome网上应用店下载安装。当然，你也可以自己编写。

扩展的工作方式类似于在操作系统上安装的应用程序。就像操作系统应用程序一样，扩展是为特定架构编写的。这意味着扩展只能在其开发的特定浏览器上安装，不能在其他浏览器上使用。因此，某些攻击技术虽然相似，但根据浏览器的不同，攻击方法会有所差异。

扩展可以跨越浏览器加载的所有页面。例如，NoScript扩展可能影响浏览器加载的每一页。其他扩展也可能如此。将扩展视为在每个加载的页面中运行的虚拟Web应用是有帮助的，这在本章后续的漏洞发现部分将被进一步探讨。

## 扩展与插件的区别

扩展和插件有时难以区分，但它们存在一些主要区别。扩展位于浏览器的进程空间内，而插件可以独立运行。扩展可以创建浏览器菜单和标签页，而插件不能。


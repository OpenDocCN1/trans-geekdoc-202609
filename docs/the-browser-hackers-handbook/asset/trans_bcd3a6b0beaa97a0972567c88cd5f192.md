
# 摘要

将功能从浏览器核心中移除并移入扩展程序几乎肯定减少了臃肿。然而，这也将重要功能的开发和维护转移到了安全意识较弱的开发者手中。这与赋予他们强大的权限相结合，导致了许多不安全的扩展程序。有人可能会认为，臃肿的减少是以牺牲浏览器的**总体安全性**为代价的。

你可以从多种角度观察扩展程序如何增强浏览体验。例如，可以将扩展程序视为在每个页面的源上下文中运行的虚拟 Web 应用程序。也可以将它们视为安装在操作系统上的应用程序。无论哪种方式，都要记住它们在特权上下文中运行，并拥有特权 API。

本章深入探讨了扩展程序的解剖结构以及如何检测目标扩展程序是否已安装在被钩针的浏览器中。你已经考察了扩展程序的庞大攻击面及其漏洞类别。你现在了解了**跨上下文脚本注入**的工作原理以及一些最可靠的特权提升方法。

本章探讨了利用 Chrome 和 Firefox 扩展程序的高级技术。下一章将深入探讨攻击浏览器插件的方法。插件是增强浏览体验的另一种流行方式，同样拥有广阔的攻击面。

# 问题

Level1 **1.** 比较 Chrome 和 Firefox 扩展程序的安全模型。 **2.** 什么是有效的扩展程序指纹识别方法？ **3.** `chrome://` 区域是什么，为什么它是它重要的？ **4.** 内容安全策略 (CSP) 对浏览器扩展程序有何影响？ **5.** 同源策略 (SOP) 对浏览器扩展程序有何影响？ **6.** 如何在 Firefox 扩展程序中执行操作系统命令？ **7.** 如何在 Chrome 扩展程序中执行操作系统命令？ **8.** 内容脚本拥有哪些权限？ **9.** 背景页面拥有哪些权限？ **10.** Firefox 扩展程序拥有哪些权限？

/Level1

对于问题的答案，请参阅书籍网站 [https://browserhacker.com/answers](https://browserhacker.com/answers) 或维基网站： [www.wiley.com/go/browserhackershandbook](http://www.wiley.com/go/browserhackershandbook)。

**注释**

1\. Google. (2013). Google Analytics Opt-out Add-on. Retrieved November 30, 2013 from [https://chrome.google.com/webstore/detail/google-analytics-opt-out/fllaojicojecljbmefodhfapmkghcbnh](https://chrome.google.com/webstore/detail/google-analytics-opt-out/fllaojicojecljbmefodhfapmkghcbnh)

2\. Microsoft. (2013). How do browser add-ons affect my computer. Retrieved November 30, 2013 from [http://windows.microsoft.com/en-AU/windows-vista/How-do-browser-add-ons-affect-my-computer](http://windows.microsoft.com/en-AU/windows-vista/How-do-browser-add-ons-affect-my-computer)

3\. Wikipedia. (2013). Mozilla Add-ons. Retrieved November 30, 2013 from [http://en.wikipedia.org/wiki/Mozilla_Add-ons](http://en.wikipedia.org/wiki/Mozilla_Add-ons)

4\. Roberto Suggi Liverani, Nick Freeman. (2009). Abusing Firefox Extensions. Retrieved November 30, 2013 from [http://www.security-assessment.com/files/documents/presentations/liverani_freeman_abusing_firefox_extensions_defcon17.pdf](http://www.security-assessment.com/files/documents/presentations/liverani_freeman_abusing_firefox_extensions_defcon17.pdf)

5\. Mozilla. (2013). nsILoginManager. Retrieved November 30, 2013 from [https://developer.mozilla.org/en-US/docs/XPCOM_Interface_Reference/nsILoginManager#searchLogins\(\)](https://developer.mozilla.org/en-US/docs/XPCOM_Interface_Reference/nsILoginManager#searchLogins\(\))

6\. Nick Freeman. (2009). ScribeFire (Mozilla Firefox Extension)––Code Injection Vulnerability. Retrieved November 30, 2013 from [http://www.security-assessment.com/files/advisories/ScribeFire_Firefox_Extension_Privileged_Code_Injection.pdf](http://www.security-assessment.com/files/advisories/ScribeFire_Firefox_Extension_Privileged_Code_Injection.pdf)

7\. Roberto Suggi Liverani and Nick Freeman. (2010). Exploiting Cross Context Scripting Vulnerabilities in Firefox. Retrieved November 30, 2013 [from http://www.security-assessment.com/files/documents/whitepapers/Exploiting_Cross_Context_Scripting_vulnerabilities_in_Firefox.pdf](http://from%20http://www.security-assessment.com/files/documents/whitepapers/Exploiting_Cross_Context_Scripting_vulnerabilities_in_Firefox.pdf)

8\. Mozilla. (2013). nsIOutputStream. Retrieved November 30, 2013 from [https://developer.mozilla.org/en-US/docs/XPCOM_Interface_Reference/nsIOutputStream](https://developer.mozilla.org/en-US/docs/XPCOM_Interface_Reference/nsIOutputStream)

9\. Mozilla. (2013). Displaying web content in an extension without security issues. Retrieved November 30, 2013 from [https://developer.mozilla.org/en-US/docs/Displaying_web_content_in_an_extension_without_security_issues](https://developer.mozilla.org/en-US/docs/Displaying_web_content_in_an_extension_without_security_issues)

10\. Adam Barth, Adrienne Porter Felt, Prateek Saxena, and Aaron Boodman. (2012). Protecting Browsers from Extension Vulnerabilities. Retrieved November 30, 2013 from [http://www.cs.berkeley.edu/~afelt/secureextensions.pdf](http://www.cs.berkeley.edu/~afelt/secureextensions.pdf)

11\. Google. (2013). Google Chrome Webstore. Retrieved November 30, 2013 from [https://chrome.google.com/webstore/category/extensions](https://chrome.google.com/webstore/category/extensions)


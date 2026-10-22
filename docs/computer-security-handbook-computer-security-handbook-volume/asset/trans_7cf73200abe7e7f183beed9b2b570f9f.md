

同样，普通用户也可以使用一次性虚拟机48,49来将正常操作环境与感知风险较高的环境（例如，浏览可疑网站；强制安装来源或安全性不明的ActiveX控件）分离开来。

## 17.4.5 服务器端的责任

如本章前面所述，Web服务器是极具吸引力的攻击载体。签名（身份验证）方法是一种控制潜在损害的方式，前提是用于接纳可执行代码的机制得到适当控制。如果未能控制这些机制，将导致严重的副作用。

最小必要权限的概念同样适用于移动代码。仅仅为了改变横幅广告的颜色而强制使用ActiveX是没有必要的。这种效果通常可以通过层叠样式表（CSS）来实现。JavaScript/ECMAScript能够以较高的安全性执行许多强大的、与显示相关的操作，尤其是在CSS不足以胜任的情况下。使用Java来维护购物车（价格、数量和内容）是合理的，并且不需要使用带签名的小程序，从而避免其附带的更强大能力和风险。在另一个极端，系统更新功能（例如Windows Update功能，它会自动下载并安装Windows操作系统的更新）可能需要带签名的ActiveX控件所拥有的无限制权限。

当确实需要带签名的小程序或控件的权限时，良好的软件工程实践为如何限制潜在的损害和恶意行为提供了极好的范例，如本手册第38章所讨论的那样。

这些问题超出了单个组织的直接风险范围。过去几年中的一个日益增长的趋势是利用第三方Web服务器作为感染媒介，作为感染网站访问者的跳板。如果组件是从第三方服务器下载的，那么你的WWW站点的完整性可能会受到威胁。

良好的软件实现会将功能隔离，并限制需要特权访问或操作的范围。工资应用程序不会直接操作打印机端口、视频显示卡、网络适配器或磁盘驱动器。特权操作系统组件（如设备驱动程序和文件系统）负责实际操作。这种分离，加上操作系统内核和特权组件对参数的仔细检查，确保了安全性。

同样的技术也可以用于小程序和控件。由于它们需要更多访问权限，因此在编程时应格外谨慎，采用与向操作系统添加特权功能时相同的防御性措施。例如，简单邮件传输协议（SMTP）服务器几乎没有理由需要特权。SMTP服务器仅需一项功能的特权，即将单个电子邮件消息投递到收件人的邮箱。这可以通过两种方式实现：

- 1. 以非特权方式实现该应用程序，方法是为用户的电子邮件文件和目录标记必要的访问权限，使邮件投递程序能够创建和修改电子邮件文件和目录。这种机制完全符合NCSC橙皮书C2级安全标准。
- 2. 实现一个独立的子组件，其唯一职责是实际的消息投递。该子组件必须以防御性方式编写，检查其所有参数，并且不提供执行任意代码的接口。HP的OpenVMS操作系统采用了这种方法。

相比之下，UNIX的sendmail程序是一个大型、多功能的程序，以特权方式运行。十多年来，sendmail一直是许多安全问题的来源，并催生了生产更安全替代品的努力。⁵⁰

## 17.5 小结

移动代码提供了许多灵活且有用的功能。实现移动代码的不同机制范围从无害的（HTML）到相当安全的（JavaScript/ECMAScript），再到通过Java和ActiveX获得不断增强的能力和风险。

使用移动代码确保安全性和完整性需要提供方和客户端双方的协作。客户端不应接受随意的签名代码和控件。提供方有积极的责任：

- 遵循良好的软件工程实践
- 授予最小必要的权限和访问权
- 使用防御性编程
- 限制特权访问，不得有开放式的接口
- 确保签名过程及相关私钥的完整性

只要谨慎行事，移动代码可以成为内联网和互联网应用程序中建设性的、强大的组成部分，无论是在组织内部，还是在与客户及其他利益相关者的合作中。

## 17.6 扩展阅读

Carl, Jeremy. “ActiveX Security: Under the Microscope,” Web Week. 2. No. 17. November 4, 1996; www.Webdeveloper.com/activex/activex_security.html

CERT. “NIMDA Worm,” September 11, 2001, www.cert.org/advisories/CA-2001-26.html

CERT. “sadmind/IIS Worm,” May 8, 2001, www.cert.org/advisories/CA-2001-11.html

CERT. “Unauthentic ‘Microsoft Corporation’ Certificates,” March 22, 2001, www.cert.org/advisories/CA-2001-04.html

Dormann, Will, and Jason Rafail. “Securing Your Web Browser.” CERT. January 23, 2006, www.cert.org/tech_tips/securing_browser/index.html on March 19, 2013.

Evers, J. FAQ: JavaScript Insecurities. CNET July 28, 2006 < http://news.cnet.com/2100-7349_3-6100019.html >

Felten, Edward. “Security Tradeoffs: Java vs. ActiveX,” last modified April 28, 1997, www.cs.princeton.edu/sip/faq/java-vs-activex.html

Felten, E., and J. Halderman (2006, February 14). Lessons from the Sony CD DRM Episode, Center for Information Technology Policy, Department of Computer Science, Princeton University, USENIX Security 2006 http://static.usenix.org/events/sec06/tech/full_papers/halderman/halderman.pdf

Felten, E., and G. McGraw. Securing Java: Getting Down to Business with Mobile Code. New York: John Wiley & Sons, 1999. Also free and unlimited Web access from www.securingjava.com

Gehtland, J., B. Galbraith, and D. Almaer. Pragmatic Ajax. Raleigh, NC: Pragmatic Bookshelf, 2006.

Grossman, J., and T. C. Niedzialkowski. “Hacking Intranet Websites from the Outside,” Black Hat (USA), Las Vegas, August 3, 2006. www.blackhat.com/presentations/bh-usa-06/BH-US-06-Grossman.pdf

Hensing, R. “W32/HLLP.Philis.bq, Chinese Gold Farmers and What You Can Do about It,” December 2, 2007, http://blogs.technet.com/robert_hensing/archive/2006/12/04/w32-hllp-philis-bq-chinese-gold-farmers-and-what-you-can-do-about-it.aspx

Holzman, S. Ajax Bible. Hoboken, NJ: John Wiley & Sons, 2007.

Keizer, G. “FBI Planted Spyware on Teen’s PC to Trace Bomb Threats,” PCWorld, July 19, 2007. www.pcworld.com/article/134823/article.html

McGraw, G., and E. W. Felten. Securing Java: Getting Down to Business with Mobile Code, 2nd Edition. John Wiley & Sons, 1999.

McGraw, Gary & Ed Felten. “Java Security Web Site.” www.cigital.com/javasecurity/index.html

Microsoft. “Introduction to Code Signing” (with appendix), 2001, http://msdn.microsoft.com/en-us/library/ms537361%28v=vs.85%29.aspx

Rhoads, C. “Web Scammer Targets Senior U.S. Executives,” Wall Street Journal, November 9, 2007.

Schwartz, J. “iPhone Flaw Lets Hackers Take Over Security Firm Says,” New York Times, July 23, 2007.

VeriSign, “Microsoft Security Bulletin MS01-017: Erroneous VeriSign-Issued Digital Certificates Pose Spoofing Hazard,” March 22, 2001, www.microsoft.com/TechNet/security/bulletin/MS01-017.asp

VeriSign, “VeriSign Security Alert Fraud Detected in Authenticode Code Signing Certificates,” March 22, 2001.

Zakas, N., J. McPeak, and J. Fawcett. Practical Ajax, 2nd ed. Hoboken, NJ: John Wiley & Sons, 2007.

## 17.7 注释

- 1. ECMA-262 retrieved from www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-262%205th%20edition%20December%202009.pdf
- 2. Carter Dotson, “Is Apple Losing Its Grip on App Store Security?” Mashable Web site, March 1, 2012. http://mashable.com/2012/03/01/app-store-security-risks
- 3. Scott Thurm and Yukari Iwatani Kane, “Your Apps Are Watching You,” The Wall Street Journal, December 17, 2010, http://online.wsj.com/article/SB10001424052748704694004576020083703574602.html
- 4. J. Schwartz, “iPhone Flaw Lets Hackers Take over, Security Firm says,” The New York Times, July 23, 2007, www.nytimes.com/2007/07/23/technology/23iphone.html
- 5. CBC News (2013, January 28) “WhatsApp breaches privacy laws,” CBC News, January 28 2013. www.cbc.ca/news/technology/story/2013/01/28/technology-whatsapp-privacy.html
- 6. Office of Privacy Commissioner of Canada, “Report of Findings Investigation into the personal information handling practices of WhatsApp Inc.,” January 15, 2013, www.priv.gc.ca/cf-dc/2013/2013_001_0115_e.asp
- 7. Memorandum by Arthur M. Money, Assistant Secretary of Defense for C3I, and CIO to Secretaries of the Military Departments, Chairman of the Joint Chiefs of Staff, Chief Information Officers of the Defense Agencies, et al., “Use of Mobile Code Technologies in DoD Information Systems,” October 23, 2006. www.dtic.mil/whs/directives/corres/pdf/855201p.pdf


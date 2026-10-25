

## 1.6 Summary

软件的安全性仅取决于软件开发团队所采用的最佳实践的质量和相关性。软件安全必须从一开始就内建。它必须从一开始就是设计的关键部分，并贯穿每个后续开发阶段，直至部署完整系统。在SDLC中通过采用安全增强的流程和实践尽早修复漏洞，远比在系统投入生产后尝试诊断和纠正此类问题更具成本效益。这将大大减少产品发布后为修复他人发现的安全漏洞而打补丁的需求，这将降低供应商的声誉和可信度，并对其造成财务上的不利影响。当今，我们看到软件开发中对安全的需求日益增加，因为安全需求、设计和防御原则必须融入传统的SDLC，最重要的是，在选择贯穿SDLC所有活动的安全开发实践时要拥抱这一需求。

我们曾与财富500强公司合作，并经常看到SDL实践中出现失效的例子。在本书中，我们采用基于经验的方法，应用最佳可用SDL模型的组件，以SDL软件安全最佳实践模型和框架的形式处理上述问题。我们将首先概述安全开发生命周期，然后概述一个将SDL最佳实践映射到软件开发生命周期的模型，以及如何利用此构建成熟的SDL计划。尽管安全在近年来行业构建软件的方式中并非自然组成部分，但我们相信开发流程的安全改进是可能的、切实可行的和必要的，并且我们相信本书中提出的软件安全最佳实践和模型将使所有读本书的人（无论您是高管、经理还是从业人员）都明白这一点。

## Chapter Quick-Check

- 1. 一旦软件产品发布，修复安全缺陷的成本可能高达开发阶段修复成本的____倍：
  - a. 50
  - b. 100
  - c. 500
  - d. 1500

- 2. 有缺陷的软件是：
  - a. 网络安全问题
  - b. 操作系统安全问题
  - c. 用户造成的问题
  - d. 软件开发和工程问题

- 3. 安全开发生命周期的三个目标是：
  - a. 可靠性、效率和可维护性
  - b. 速度、质量和持续发布
  - c. 机密性、完整性和可用性
  - d. 可用性、可靠性和可移植性

- 4. 威胁建模和攻击面分析在以下时间进行时最有效：
  - a. 发布后
  - b. 产品构思/产品待办列表开发期间
  - c. 集成测试阶段期间
  - d. 代码开发/提交之前

## Exercises

- 1. 访问战略与国际研究中心的重大网络事件网站，查看自2006年以来重大网络事件的时间线。在阅读这些攻击时，考虑安全开发生命周期和安全开发实践如何本可预防这些攻击或减轻其造成的损害。是否有任何特定类型的攻击需要干预或对SDL进行更改？您将如何确定这些更改的优先级？

- 2. 将应用程序、基础设施、平台和管理迁移到云计算迫使IT部门发生诸多变化。从安全角度看，这种迁移如何影响软件规划、开发、测试和实施？需要保留什么？需要重新构思什么？

- 3. 软件安全教育和意识是有效计划的基石，因为开发团队负责保护其生成的所有代码。您将如何说服IT开发管理层，他们的团队需要为安全职责做好充分准备？

## References

- 1. 总统信息技术咨询委员会。(2005). “网络安全：优先级危机，”总统行政办公室，信息技术研究与发展全国协调办公室，2005年，第39页。检索自 https://www.nitrd.gov/pubs/pitac/pitac_report_cybersecurity_2005.pdf
- 2. 同上。
- 3. Aras, O., Ciaramitaro, B., and Livermore, J. (2008). “安全软件开发——IT审计的角色。”ISACA期刊，第4卷，2008年，第45–48页。检索自 https://www.isaca.org/resources/isaca-journal/past-issues
- 4. 美国国土安全部。(2006). “软件生命周期中的安全：使软件开发流程——以及由其生产的软件——更安全，”草案版本1.2，第13页。检索自 https://resources.sei.cmu.edu/asset_files/WhitePaper/2006_019_001_52113.pdf
- 5. Schwartz, M. (2012). “2012年值得关注的10大安全趋势。”检索自 https://www.darkreading.com/vulnerabilities-threats/10-security-trends-to-watch-in-2012
- 6. Parizo, E. (2012). “要获得安全软件开发问题的帮助，请自行发现缺陷。”检索自 http://searchsecurity.techtarget.com/news/2240129160/To-get-help-with-secure-software-development-issues-find-your-own-flaw
- 7. Taft, D. (2012). “微软举办安全开发会议。”检索自 https://www.eweek.com/security/microsoft-holds-security-development-conference/
- 8. blackhat.com。(2013). 黑帽美国2012年会议网页，2012年7月21–26日，内华达州拉斯维加斯。检索自 http://www.blackhat.com/html/bh-us-12
- 9. OWASP基金会。(2013). “接近安全代码。我从哪里开始？”RSA 2013。检索自 https://owasp.org/www-pdf-archive/MASTER-RSA2013-v3.pdf
- 10. 微软公司。(2012). 2013年安全开发会议报名开放：号召所有IT安全专业人士。检索自 https://news.microsoft.com/2012/12/18/registration-open-for-2013-security-development-conference-calling-all-it-security-professionals/
- 11. Boehm, B., and Paccacio, P. (1998). “理解和控制软件成本。”IEEE软件工程事务，第14卷，第10期，1988年10月，第1462–1477页。
- 12. Boehm, B., and Basili, V. (2001). “软件缺陷减少十大清单。”计算机，第34卷，第1期，2001年1月，第135–137页。
- 13. Meftah, B. (2008). “企业软件保证：识别和降低企业中的软件风险，”第9届半年度软件保证论坛，马里兰州盖瑟斯堡，2008年10月。https://buildsecurityin.us-cert.gov/swa/downloads/Meftah.pdf
- 14. Viega, J., and McGraw, G. (2006). 构建安全软件：以正确方式避免安全问题的方法。波士顿，马萨诸塞州：艾迪生-威斯利。
- 15. McGraw, G. (2006). 软件安全：内建安全，第20页。波士顿，马萨诸塞州：艾迪生-威斯利。
- 16. IT法规维基。(2012). “安全开发生命周期定义。”检索自 http://itlaw.wikia.com/wiki/Security_Development_Lifecycle
- 17. 微软公司。(2021). “关于微软SDL。”检索自 https://www.microsoft.com/en-us/securityengineering/sdl/about#:~:text=The%20Microsoft%20Security%20Development%20Lifecycle%20%20%20%20SDL%20%20%20was%20an,the%20software%20development%20process%20at%20Microsoft%20in%202004
- 18. Grembi, J. (2008). 安全软件开发：安全程序员指南。波士顿，马萨诸塞州：课程技术。
- 19. 同上。
- 20. 同上。
- 21. 同上。
- 22. 美国政府。(2006). “44 U.S.C.，第3542条：美国法典，2006年版，”增编5，第44篇；第35章——联邦信息政策协调，III子章节——信息安全，第3542条——定义。检索自 http://www.gpo.gov/fdsys/pkg/USCODE-2011-title44/pdf/USCODE-2011-title44-chap35-subchapIII-sec3542.pdf
- 23. Goertzel, K., 等人，为国土安全部和国防部软件数据与分析中心。(2008). “增强开发生命周期以生产安全软件：软件保证参考指南手册，”第2版，2008年10月。检索自 https://www.academia.edu/1383839/Enhancing_the_Development_Life_Cycle_to_Produce_Secure_Software_A_Reference_Guidebook_on_Software_Assurance
- 24. Goertzel, K., 等人。(2007). “软件安全保证：最新技术报告（SOAR），”2007年7月。检索自 https://www.researchgate.net/publication/279351339_Software_Security_Assurance_A_State-of-Art_Report_SAR


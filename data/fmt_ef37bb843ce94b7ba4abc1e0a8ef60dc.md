
加强网络安全和协议，增强监控，审查和修改策略，并实施其他任何必要的安全强化措施。

记录调查结果以及为应对攻击所采取的步骤。

及时、清晰地向所有受影响的利益相关者、监管机构和公众进行沟通。

上述许多操作可能需要同时采取，而不一定按上述顺序进行。既定程序必须定期测试，并根据需要随时修改。还必须有用于评估 `IR` 有效性的措施。

以下是一组问题，帮助组织评估并发展其有效应对威胁和攻击的能力。

整个业务运营，以高度协作的方式制定和管理这些计划非常重要。[^86]

同时拥有事件响应计划（`IRP`）和灾难恢复计划（`DRP`）的组织必须明确阐述并记录这两项计划如何相互支持和补充，以减少歧义。还必须明确理解在何种情形和场景下触发 `IRP` 或 `DRP`，以及两者之间的转换点。两个团队必须紧密合作，开展联合演练，以深入理解各自的角色和职责。[^87]

### 综合灾难恢复计划的关键要素

#### 全面的资产清单。

组织必须维护一份详细而全面的数字资产清单，涵盖硬件和软件。此类清单需包括描述、照片、位置详情、序列号和组织控制编号。在潜在灾难（如自然灾害）防备准备前后拍摄的设备位置照片，也可证明组织为采取防护措施所做的努力。相关合同和供应商联系信息也应列入资产清单。维护一份用于访问不同设备、系统和应用的密码列表也是一种良好实践。从保护、恢复和保险理赔的角度来看，如此详尽的文档记录极为有用。[^88]

#### 沟通计划。

在灾难发生时，清晰阐明并记录所有个人和团队的任务、角色和职责极为重要。任何事项都不应仅仅依靠假设。在可行且可能的范围内，个人和团队将如何行动、沟通和汇报的每一个细节都必须在计划文件中明确说明。还必须包含相关员工、供应商、供货商和客户的联系信息，以及多种/备用联系方式（如电子邮件、电话和社交媒体平台）的详细信息。[^89]

组织还必须制定一份书面计划，说明如何与全体员工、媒体和公众沟通。通常使用在线门户网站向所有相关人员通报恢复进展。

#### 角色与职责。

参与灾难恢复运营的每个人都必须完全清楚自己的角色和职责。为了便于快速识别，建议按姓名列出指定人员，而不是使用其日常职务头衔。由于灾难恢复角色很可能不同于日常运营角色，按职务列出团队成员可能会造成混淆。联系信息必须保持最新。列出后备成员同样重要。⁹⁰

#### 容忍级别。

为所有系统和应用设置可接受的恢复点目标（`RPO`）和恢复时间目标（`RTO`）非常重要，尤其是关键任务系统和应用。理想情况下，恢复时间应不超过几毫秒，但这可能不是现实的目标。规划人员必须针对每一层级应用集仔细斟酌并决定这两项指标。通常，第一层应用需要立即投入运行，第二层需在 8 到 10 小时内恢复，第三层需在几天内恢复。⁹¹

#### 备份站点。

组织必须准备一到两个备份站点，以便在主运营站点宕机时，从这些备份站点开始运行关键任务系统。这些恢复站点必须配置训练有素的人员以及设备和系统，以便在灾难来袭并导致主要生产系统宕机后尽快投入使用。备份站点有三种类型：热站、温站和冷站。热站配备所有必要的硬件、软件、网络和互联网连接；甚至数据也会定期在热站系统上进行备份或复制。此类站点可以实际存在于数据中心或分支机构/附属办公地点，也可以虚拟地存在于云端。热站应能立即投入运行。另一方面，温站和冷站是较便宜的选择，配有适当的设备和人员，但需要几天时间才能发挥功能。

灾难恢复团队必须清楚了解发生事件时自己应该前往何处。备用站点必须有足够空间容纳指定的工作人员。

#### 与服务提供商的服务级别协议。

如果涉及外部服务提供商来部署计算运营，则与每家服务提供商签订的服务级别协议（`SLA`）必须明确规定在发生灾难时承包商应提供的服务水平。理想情况下，对于未能达到合同约定水平的情况，应设有惩罚条款。

#### 定期测试。

灾难恢复计划必须定期测试，以确保恢复性能符合预期。测试过程必须使用恢复点目标和恢复时间目标等指标，全面评估计划的有效性。测试的方法和频率必须在计划文件中记录并遵照执行。有些工具可用于自动化进行 `DR` 测试，而不会中断生产系统。同样重要的是，通过模拟灾难和演练来检验指定人员的表现。以下是一组指导性问题，用于确保灾难恢复计划的关键要素得到处理并落实到位。

### 灾难恢复规划：指导性问题

1. 是否维护了全面的资产清单，以识别各种脆弱点？
2. 在制定恢复策略之前，是否已识别各种威胁场景，并根据风险和业务影响分析进行排序？
3. 是否明确定义了关键任务和非关键应用及系统的恢复性能指标（如恢复点目标和恢复时间目标）？
4. 是否清晰阐明并记录了灾难恢复计划团队成员的角色和职责？
5. 计划文件中是否明确描述了个人和团队将如何行动、沟通和汇报？
6. 事件响应团队与灾难恢复团队是否紧密合作并开展联合演练？
7. 在适用范围内，业务合作伙伴（如客户和供应商）是否了解恢复计划？
8. 是否有书面沟通计划，详细说明在灾难恢复过程中如何让全体员工、媒体和公众了解最新情况？
9. 是否已具备备份站点，无论是热站、温站还是冷站？
10. 与供应商签订的服务级别协议（`SLA`）是否明确规定了灾难期间预期的服务和支持水平？
11. 灾难恢复计划（`DRP`）是否定期测试并根据需要更新？

因此，全面准备方法包含多个要素——从识别关键资产到制定基于风险的保护优先级方案，实施多因素身份验证措施，管理访问权限，加密数据，遵循可靠的备份方法，保护网络和端口，开展定制化和沉浸式培训演练，部署复杂的检测能力，以及制定和演练业务连续性和灾难恢复计划。做好这些工作可能是一项具有挑战性和令人不知所措的任务。没有深厚的信念和对彻底准备价值的坚定信念，组织就无法实现和维持高水平的准备。

## 第6章注释

1. Chapple, M., Stewart, J. M., & Gibson, D. (2018). 《注册信息系统安全专业人员官方学习指南》，第8版。John Wiley & Sons.
2. Gressin, S. (2018, December 4). 万豪数据泄露。Federal Trade Commission。于2019年9月9日检索自 https://www.consumer.ftc.gov/blog/2018/12/marriott-data-breach.
3. O'Flaherty, K. (2019, March 11). 万豪首席执行官透露有关重大泄露的新细节。Forbes。于2020年12月16日检索自 https://www.forbes.com/sites/kateoflahertyuk/2019/03/11/marriott-ceo-reveals-new-details-about-mega-breach/#e5ce8b615c0.
4. Del Valle, G. (2019, January 11). 万豪数据泄露可能是历史上最大的一次。现在它面临多起集体诉讼。Vox。于2019年9月9日检索自 https://www.vox.com/the-goods/2019/1/11/18178733/marriott-starwood-hack-lawsuit
5. Hosn, H. (2018, October 26). 保护国家基础设施的三个关键步骤。Secureworks。于2019年6月3日检索自 https://www.secureworks.com/blog/three-key-steps-to-help-protect-national-infrastructure
6. Quoted in Staff, M. (2019, February 27). 关键基础设施攻击：各国尚未准备好。Raconteur。于2019年6月13日检索自 https://www.raconteur.net/technology/critical-infrastructure-cyberattacks
7. Cybersecurity and Infrastructure Security Agency. (2017, August). 保护网络资产：应对关键基础设施的紧迫网络威胁。https://www.cisa.gov/sites/default/files/publications/niac-securing-cyber-assets-final-report-508.pdf
8. Bailey, T., Barriball, E., Dey, A., & Sankur, A. (2019, March 8). 什么是供应链风险管理？供应链风险管理的实用方法。McKinsey & Company。https://www.mckinsey.com/business-functions/operations/our-insights/a-practical-approach-to-supply-chain-risk-management#
9. Boehm, J., Merrath, P., Poppensieker, T., Riemenschneider, R., & Stahle, T. (2018, November 19). 网络风险度量与整体网络安全方法。McKinsey & Company。https://www.mckinsey.com/business-functions/risk/our-insights/cyber-risk-measurement-and-the-holistic-cybersecurity-approach
10. Xactium. 6种有意义的风险聚合方法 [White paper].
11. Kulwal, M. (2019, June 15). 风险聚合最佳实践 [White Paper]. RiskSpotlight. www.riskspotlight.com
12. Barker, I. (2019). 90%的关键基础设施遭到网络攻击。Betanews。于2019年6月13日检索自 https://betanews.com/2019/04/05/critical-infrastructure-cyberattacks/#:~:text=A%20new%20survey%20of%20professionals%2Cexperiencing%20two%20or%20more%20attacks.
13. Miessler, D. (2018, December 31). 如果你不进行持续资产管理，你就没有进行安全工作。Danielmiessler.com。于2019年6月13日检索自 https://danielmiessler.com/blog/continuous-asset-management-security/
14. ARMIS. (2020). 网络安全资产管理：设备发现与风险评估 [White Paper]. https://www.armis.com/resources/iot-security-white-papers/cybersecurity-asset-management-white-paper/
15. Chapple, M., Stewart, J. M., & Gibson, D. (2018). 《注册信息系统安全专业人员官方学习指南》，第8版。John Wiley & Sons.
16. Rothke, B. (2019, April 16). 从漏洞管理解决方案中获得最大收益的9个关键。BeyondTrust。于2019年6月4日检索自 https://www.beyondtrust.com/blog/entry/9-keys-to-getting-the-most-out-of-your-vulnerability-management-solution
17. Francis, P. (2018, June). 安全智库：利用数据流信息保护系统。Computer Weekly。于2019年6月13日检索自 https://www.computerweekly.com/opinion/Security-Think-Tank-Use-data-flow-information-to-protect-systems
18. Godfrey, J. (2015, January 15). 网络分段的最佳实践和技巧。AlgoSec。于2019年6月12日检索自 https://www.algosec.com/blog/best-practices-tips-network-segmentation-use-cases-professor-wool/
19. Olzak, T. (2016, April 25). 保护您的关键系统安全。CSO Online。于2019年6月12日检索自 https://www.csoonline.com/article/3060058/keep-your-critical-systems-safe.html
20. Reichenberg, N. (2014, March 20). 通过适当的网络分段提高安全性。Security Week。于2019年6月12日检索自 https://www.securityweek.com/improving-security-proper-network-segmentation
21. Walkowski, D. (2019, August 22). 什么是安全控制？Education。于2020年8月21日检索自 https://www.f5.com/labs/articles/education/what-are-security-controls

Mullahy, T. (2019, September 27). 您的企业需要的5项物理控制措施。Total Security Advisor。于2020年8月21日检索自 https://totalsecurityadvisor.blr.com/facility-security/5-physical-security-controls-your-business-needs/
22. https://www.cisecurity.org/, 于2020年7月28日访问。
23. Johnson, A., Dempsey, K., Ross, R., Gupta, S., & Bailey, D. (2011, August). 信息系统安全导向配置管理指南。National Institute of Standards and Technology。https://csrc.nist.gov/publications/detail/sp/800-128/final
24. Chapple, M., Stewart, J. M., & Gibson, D. (2018). 《注册信息系统安全专业人员官方学习指南》，第8版。John Wiley & Sons.
25. Geer, D. (2017, April 24). 保护风险网络端口。Network World。于2019年10月11日检索自 https://www.networkworld.com/article/3191513/securing-risky-network-ports.html
26. 同上。
27. Bukth, T. and Huda, S. M. S. (2017, January 4). 软性威胁：孟加拉银行储备金盗窃案的故事。SAGE Business Cases.
28. Bigman, R. (2019, May 28). 随着监管合规要求增长，临时设备需要严格的控制措施。SC Media。于2019年7月22日检索自 https://www.scmagazine.com/home/opinion/executive-insight/transient-devices-require-strict-control-measures-as-regulatory-compliance-requirements-grow/ https://www.scmagazine.com/
29. Burt, J. (2018, October 1). 卡巴斯基发现USB设备仍对企业构成威胁。Informa Tech。于2019年7月22日检索自 https://www.securitynow.com/author.asp?section_id=715&doc_id=746429
30. Pal, K. (2015, July 15). 加密密钥管理和数据安全的10个最佳实践。Techopedia。于2019年6月5日检索自 https://www.techopedia.com/2/30767/security/10-best-practices-for-encryption-key-management-and-data-security
31. Tozi, C. (2020, February 17). 数据加密101：数据加密最佳实践快速指南。Precisely。https://www.precisely.com/blog/data-security/data-encryption-101-guide-best-practices
32. FASOO. NIST网络安全框架可以帮助防止数据泄露。于2019年6月6日检索自 https://en.fasoo.com/nist-cybersecurity-framework-can-help-protect-against-data-leaks/
33. Vitru. 加密密钥管理：自行托管密钥并控制您的数据。于2020年7月8日检索自 https://www.virtru.com/encryption-key-management/
34. AET. 数字签名与数字证书的区别。于2020年7月检索自 https://www.aeteurope.com/news/digital-signature-digital-certificate/
35. 同上。

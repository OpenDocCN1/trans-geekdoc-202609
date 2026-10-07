
如前所述，有必要先识别出入侵指标（IoC）并创建规则，以便稍后进行自动检测。UEBA（用户和实体行为分析）允许检测未知威胁，特别是内部威胁。通过机器学习，可以为用户、群体或网络实体的“正常”行为创建一个基准。然后，当用户执行偏离预期行为的操作时，系统会自动发出带有风险评分的警报。

## 5.4.2 人工智能 (AI)

人工智能（AI）具有通过自动化威胁检测和响应，通过对潜在安全漏洞提供更快、更准确的洞察，从而显著增强组织缓解网络威胁的能力。以下是 AI 用于缓解网络威胁的几种方式：

- 威胁检测：AI 可用于分析海量数据以识别可能指示安全漏洞的模式和异常。机器学习算法可以在历史数据上进行训练，以实时检测并响应新类型的威胁。这有助于组织更快地识别和响应威胁，缩短攻击者造成伤害的时间。
- 网络安全：AI 可以实时监控网络流量，以识别潜在威胁，例如未经授权的访问尝试、可疑活动或数据外泄。基于 AI 的入侵检测系统 (IDS) 可以自动识别并拦截恶意流量，降低网络攻击成功的获胜风险。
- 欺诈检测：AI 可用于检测欺诈活动，如支付欺诈、身份盗用或账户接管。机器学习算法可以分析交易数据，以识别指示欺诈的行为模式，并提醒安全团队采取行动。
- 事件响应：AI 可用于自动化事件响应过程，例如隔离系统、隔离可疑文件或拦截恶意 IP 地址。这有助于组织更快地响应安全事件，最大限度地减少网络攻击的影响。
- 预测性分析：AI 可以通过分析历史数据并识别指示攻击的模式来预测潜在的网络威胁。这有助于组织在网络攻击发生之前采取主动措施以防止其发生，例如修补漏洞、加强访问控制或增强安全意识培训。
- 用户行为分析：AI 可以分析用户行为以识别潜在的内部威胁。机器学习算法可以学习典型的用户行为模式，并检测用户何时表现异常或访问他们不应访问的数据。这有助于组织更快地检测和响应威胁，降低数据丢失或被盗的风险。
- 自然语言处理：AI 可用于分析文本数据，例如电子邮件或聊天消息（NLP 算法可以检测可疑语言，如索取敏感信息或网络钓鱼尝试）。这有助于组织更有效地检测和响应社交工程攻击。
- 威胁情报：AI 可用于分析威胁情报馈，以识别新兴的网络威胁。机器学习算法可以从历史数据中学习，并预测新威胁成功的概率。这有助于组织优先考虑其安全措施并分配更多资源。

## 5.4.3 零接触与零信任系统安全模型

零接触（Zero-touch）和零信任（Zero-trust）是两种安全框架，可以帮助组织防御来自 AI 攻击者带来的不断变化的威胁。让我们探索如何利用这些框架来增强安全性：

### 5.4.3.1 零接触

零接触侧重于安全流程自动化，以尽可能减少人工干预并缩小攻击面。在 AI 威胁的背景下，可以通过以下措施实现零接触：

- 自动威胁检测：利用基于 AI 的安全解决方案自动检测并响应 AI 驱动的攻击。这些解决方案可以分析网络流量、行为模式和异常活动以识别潜在威胁。
- 持续监控：实施利用 AI 进行异常检测的实时监控机制。通过持续监控网络流量、系统日志和用户行为，组织可以及时识别并响应基于 AI 的威胁。
- 快速补丁和更新：自动化应用安全补丁和更新的过程，以尽可能地减少漏洞。这有助于防止攻击者利用 AI 系统或其他软件组件中的已知缺陷。
- 安全 DevOps：将安全性集成到 AI 应用开发和部署过程中。采用 DevSecOps 实践可确保安全措施贯穿整个软件开发生命周期。

### 5.4.3.2 零信任

零信任是一种假设不存在任何隐含信任的安全框架，无论用户是在网络边界内部还是外部。它执行严格的访问控制，并在授予访问之前持续验证和确认所有设备、用户和应用程序。为了防御 AI 攻击者，可以如下方式实施零信任原则：

- 身份和访问管理 (IAM)：实施强身份验证机制（如多因素身份认证 MFA 和生物识别），确保只有授权用户才能访问敏感传感器或数据。此外，授予细粒度的访问控制和最小权限，限制用户仅访问必要的内容。
- 微隔离：使用分段技术将网络划分为更小的、隔离的段。这有助于包含潜在的泄露，并防止攻击者在网络内部横向移动。
- 行为分析：采用基于 AI 的分析解决方案，检测异常用户行为或偏离既定模式的情况。这有助于识别被盗账户、内部威胁或表现出异常行为的 AI 攻击。
- 加密和数据保护：对传输和存储中的敏感数据应用端到端加密。确保即使攻击者获取了加密数据，如果没有解密密钥也无法对其利用。
- 持续监控和风险评估：对网络、用户和应用程序活动进行持续监控，以检测任何潜在的安全风险。定期进行风险评估和漏洞扫描，以识别并解决 AI 基础设施中的任何缺陷。

## 5.4.4 安全管理

对于小型企业而言，上述解决方案的实施可能非常复杂且昂贵；然而，也存在非常简单且所有人都能触及的解决方案。例如，我们可以遵循 ANSI（法国国家信息安全局）或 ASD（澳大利亚信号局）等各个机构的建议。以下是一些示例：(1) 使用应用程序白名单来防止恶意软件、脚本等的执行；(2) 为 Java、Web 浏览器和 Microsoft Office 应用最新的补丁；(3) 保持操作系统为最新版本；以及 (4) 使用多身份认证连接 VPN、SSH 或任何远程访问。

为了确保这些建议在组织内部得到良好实施，创建一个 PSSI（信息系统安全策略）至关重要，它负责规范公司的信息系统。这是 ISMS（信息安全管理体系）不可或缺的一部分，ISMS 为公司范围内的安全管理提供了一个框架。特别是，它涵盖了安全的三大原则：机密性、完整性和可用性。

最后，ISMS 的实施基于 ISO 标准（如 ISO27001），该标准定义了相关要求。

## 5.5 结论

在我们的分析中，目标是展示当前的安全格局。我们介绍了不同类型的威胁行为者以解释其工作原理。在未来，勒索软件威胁可能会继续呈现趋势。除非国际政府和技术创新能够从根本上改变攻击者的成本效益计算，否则勒索软件业务将利润异常丰厚。

尽管人们努力破坏其运营并追究行为者的责任，但作为“勒索软件服务”模式的一部分，加入其他平台的网络犯罪分子将继续运营。国家级行为者将继续组织攻击以服务其地缘政治利益。最重要的是，随着乌克兰战争，俄罗斯在整个 2022 年和 2023 年保持着进攻态势，持续强调针对北约、东欧、乌克兰、阿富汗和能源部门。

由于勒索软件业务不会消失，间谍活动和信息行动也是如此，因此存在新的解决方案来保护你或你的组织。因此，随着威胁不断增加，遵循网络安全最佳实践比以往任何时候都更加必要。

## 参考文献

- 1. Scott-Hayward, S. Natarajan, and S. Sezer, “A survey of security in software defined networks,” IEEE Communications Surveys Tutorials, vol. 18, no. 1, pp. 623–654, First 2016.
- 2. Z. A. El Houda, L. Khoukhi, and A. Hadid, “Chainsecure—a scalable and protocol for protecting blockchain applications using SDN,” in 2018 IEEE Global Communications Conference (GLOBECOM), 2018, IEEE, Abu Dhabi, UAE, pp. 1–6.
- 3. D. B. Rawat and S. R. Reddy, “Software defined networking architecture, security and energy efficiency: a survey,” IEEE Communications Surveys Tutorials, vol. 19, no. 1, pp. 325–346, Firstquarter 2017.
- 4. Z. E. Houda, A. Hafid, and L. Khouki, “Co-IoT: A collaborative DDoS mitigation scheme in IoT environment based on blockchain SDN,” 2019 IEEE Global Communications Conference (GLOBCOM), 2019, IEEE, Waikololo, HI, USA, pp. 1–6.
- 5. D. Zhou, Z. Yan, G. Liu, and M. Atiquzzaman, “An adaptive network collection system in SDN,” IEEE Transactions on Cognitive Communications and Networking, vol. 6, no. 2, pp. 562–574, 2020.
- 6. Z. El Houda, A. S. Hafid, and L. Khouki, “Coch-sc: An intra-domain DDoS mitigation scheme based on blockchain SDN and smart contract,” IEEE Access, vol. 7, pp. 89 983–89 907, 2019.
- 7. Z. E. Houda, A. Hadid, and L. Khouki, “Blockchain meets AMI: Towards secure advanced metrics,” in ICC 2020-2020 IEEE International Conference on Communications (ICC), 2020, IEEE, Virtual Conference, p. 1–6.
- 8. Talhari, “Deployment of blockchain technology in software networks: A survey,” IEEE Access, vol. 8, pp. 9146–9156, 2020.
- 9. Z. E. Houda, A. Hadid, and L. Khouki, “Blockchain-based reverse auction for v2v in smart grid environment,” in ICC 2021-2021 IEEE International Conference on Communications (ICC), 2021, IEEE, Montreal, Canada, p. 1–6.
- 10. M. Houda, S. Cherkaoui, and L. Khouki, “An IoT blockchain architecture using oracles and smart contracts: the case of a food supply chain,” 2019 IEEE 30th Annual Symposium on Personal, Industrial, and Mobile Radio Conference (PIMRC), 2019, IEEE, Istanbul, Turkey, p. 1–6.
- 11. M. Houda, L. Khouki, and S. Cherkaoui, “Prediction and detection of FDIA and DDoS attacks in 5g IoT,” IEEE Network, p. 1–8, 2020.
- 12. M. Houda, S. Khouki, and L. Khouki, “Towards a secure and trustworthy blockchain: IoT use case,” in ICC 2021-2021 International Conference on Communications (ICC), p. 1–6.
- 13. M. Houda, Z. Mlika, and S. Khouki, “Detection and prediction of FDIA in IoT systems using Markov model,” IEEE Transactions on Network Science and Engineering, vol. 9, no. 5, pp. 2978–2990, 2022.
- 14. M. Houda and S. Khouki, “Towards a reliable federated learning for IoT,” in 2021 IEEE Global Communications Conference (GLOBCOM), 2021, p. 01–6.
- 15. M. Houda and S. Khouki, “Toward secure and private federated learning for IoT,” in GLOBCOM 2022-2022 Global Communications Conference, 2022, IEEE, Rio de Janeiro, Brazil, pp. 4316–4321.
- 16. M. Houda, “An overview of blockchain and networks, Computational Intelligence in Recent Networks: Current solutions and future,” IEEE Communications Surveys Tutorials, vol. 22, no. 3, pp. 1689–1720, 2021.
- 17. F. Hussain, R. Hussain, and E. Hassan, “Machine learning in IoT: Current solutions and future,” IEEE Communications Surveys Tutorials.
- 18. Z. A. E. Houda, B. Brik, and L. Khouki, “Why should IDS?: An explainable learning framework for intrusion detection systems in internet,” IEEE Open Journal of the Communications, vol. 3, pp. 1164–1176, 2022.
- 19. Z. A. E. Houda, B. Brik, Kstini, and M. Guizani, “Federated learning theory: A cooperative framework to secure IoT on edge computing,” IEEE Transactions on Industrial Informatics, vol. 18, no. 11, pp. 7988–7997, 2022.
- 20. Z. A. Houda, A. S. Hafid, and L. Khoukhi, “A novel machine learning framework for advanced attack detection using SDN,” in 2021 IEEE Global Communications Conference (GLOBCOM), 2021, IEEE, Madrid, Spain, p. 1–6.
- 21. Z. A. Houda, A. S. Hafid, and L. Khoukhi, “A privacy preserving network attack mitigation based on federated learning using SDN and blockchain,” IEEE Transactions on Network Science and Engineering, p. 1–7, 2023.
- 22. Z. A. Houda, L. Khouhi, and B. Brik, “Low-latency fog-based framework to secure IoT using collaborative federated learning,” in 2022 IEEE 47th Conference on Local Computer Networks (LCN), 2022, Edmonton, Canada, p. 343–346.
- 23. Z. Abou El Houda, "Renforcement de la sécurité traverse les réseaux globaux,” B.D. dissertation, Université Montréal, 2021.
- 24. Z. Abou El Houda, "Security enforcement for software defined networks (SDN)," B.D. dissertation, Troyes, 2021.
- 25. Z. Abou El Houda, A. Senhaj Hafid, and L. Khouhi, A Novel Unsupervised Learning Method for Intrusion Detection in Software-Defined Networks. Cham: International Publishing, 2022, p. 103–117.
- 26. Z. Abou El Houda, A. S. Hafid, L. Khouhi, and B. Brik, “When federated learning meets blockchain to preserve privacy in healthcare,” IEEE Transactions on Network Science and Management, p. 1–11, 2022.

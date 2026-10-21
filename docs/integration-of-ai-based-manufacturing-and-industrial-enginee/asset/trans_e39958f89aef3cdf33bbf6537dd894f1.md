

![](img/3d190e19625a7567e7b93c8e95b18d9c_132_0.png)

**图7.2** AAIoT原型的基于令牌的架构。

设备被阻止连接到受损设备。为了防御此类场景，ACE之后采用基于令牌的撤销机制，如图7.2所示。

类似地，尽管将新的物联网设备添加到现有设备组合中会增加进一步未修补漏洞的可能性，但Kalki作为一种运行时强制执行物联网安全策略仍然被开发出来。设备在生产过程中被嵌入恶意代码的可能性将成为供应链风险，但包括无人机（UAV）在内的许多常见设备可以在公共领域进行处理以快速响应。Kalki平台作为抵御外部威胁的防御措施而提供。

Kalki是硬件与网络之间一种更灵活、更安全的基于SDN的接口。为了提供这种保护，策略定义被更新以利用其缺陷和漏洞。Kalki系统能够定制以反映新漏洞并识别威胁（Echeverría等，2020）。

为了在正常、可疑和遭受攻击状态下维持各种模式的安全性，它配备了许多µboxes。此外，它足够灵活，可以使用各种架构来应对威胁，并且足够简单，可以在性能不下降的情况下扩展到多个边缘设备。

![](img/3d190e19625a7567e7b93c8e95b18d9c_132_1.png)

**图7.3** Kalki的防御机制：(a) 监控基于传感器的数据，(b) µboxes对流量进行分析，(c) 策略µboxes更新设备以保护设备，以及(d) µboxes按需更新安全态势，这些都是基于SDN的Kalki平台的机制。

## 7.7 各种物联网边缘角色应用

无人机探索了大多数使用物联网设备以提高性能的领域。

### 7.7.1 自动驾驶车辆

无人机几乎覆盖了该环境中的所有任务。它们依赖实时主边缘以确保安全和可靠。然而，启用物联网的车辆的移动性和互联网连接性可能在将其生成的数据传输到云端时带来挑战，而不会出现可能危及安全的显著延迟。这些车辆收集的数据量惊人。

### 7.7.2 智慧城市

目前，无人机等前沿设备正变得越来越普遍。该边缘通过实时调整地面状况来支持公开转换数据的热点（Gao等，2019）。这已成为检测网络拥塞和重新路由流量最重要方法之一。此外，这些边缘设备在需要维持真实人类生活的电网和公共基础设施的市政区域提供即时响应。

### 7.7.3 更强的安全性

环境利用这些边缘通过视频监控和生物特征扫描来增强安全性，当数据需要在授权下实时获取时，因为商业和消费者方面的边缘都可以得到加强（Sun等，2019）。当任何公司使用光学技术来保护房间或整个建筑的入口时，员工的生物特征记录保存在边缘节点。

### 7.7.4 医疗保健

来自各种医疗系统、众多医疗设备以及患者本身的医疗信息已被考虑在内。然而，所有这些数据都在各个边缘进行处理，这减少了拥塞并研究了存储可能性。在这种情况下，基于物联网的无人机设备评估数据，以决定哪些应该保留，哪些应该丢弃。例如，考虑心脏设备，边缘设备可以收集数据并与标准数据进行比较，如果发现任何异常，立即提醒用户。现实世界的成功案例表明，医疗机器人手术可以在最具创造性的地方使用。

### 7.7.5 制造业和工业流程

由于工业物联网在制造中连接了大量设备，每个连接设备的数据必须传输到中央服务器

![](img/3d190e19625a7567e7b93c8e95b18d9c_135_0.png)

**图7.4** 基于边缘的隐私保护设计。

在末端边缘进行隐私保护聚合。在这种场景下，物联网设备首先查询数据，然后边缘处理这些数据并响应，向物联网应用提供隐私保护后的数据，如图7.4所示。

在端点组织了一个轻量级隐私保护数据聚合（LPDA）方案（Ranaweera等，2021），其中物联网辅助无人机设备使用消息认证码（MAC）处理数据，这是一种单向安全函数。一旦通过比较MAC码验证了连接设备，它们就会被聚合到环境中。

下一步是使用同态Paillier加密、中国剩余定理（CRT）（Bithas等，2019）和单向哈希链等密码技术来解决物联网环境中的虚假数据报告。此外，为了理解隐私保护，LPDA采用了差分隐私技术（Mehta等，2020）。

类似地，输出扰动（OPP）方法优于对象扰动（OJP）方法，其中拉普拉斯随机噪声没有及时标记以获得正确的输出值（Lu等，2017），而OJP产生了显著改进的解决方案结果。此外，提出了一种基于边缘计算的隐私感知调度算法（Roman等，2018a）。该部署侧重于在具有不同隐私设置的各种服务器上执行各种任务（Kumar等，2022）。

- vi. 企业必须确保技术组件的任何变化都会导致漏洞，因此必须更新其补丁，并且这些信息必须在所有者之间共享，以维护供应链管理（SCM）程序（Ansari和Sun，2016）。

- vii. 在物联网安全链中建立高度信任，其中框架包括设备、网关和电器，这些设备需要更新补丁并适应新变化（Kothandaraman等，2022）。根据互联网联盟的安全框架，信任链包括：
  - a) 为确保系统安全，不应有未经授权的披露或破坏信息的篡改。

此外，所有制造商、网络防御者、ISP、安全研究人员和网络安全区域都必须在一个安全的生态系统中协作。随着世界通过物联网连接，攻击者也为即将到来的间谍攻击构建了基础设施。攻击者试图降低合法服务的质量或破坏数据。因此，需要部署不同的启发式方法，帮助使用经过验证的机制对设备进行签名，并确定这些设备何时可能受到攻击。为了减轻风险，已经部署了各种加密策略，这些策略是讨论的主题。然而，支持物联网的无人机边缘设备正在成为攻击物联网生态系统的新途径，这为新的现实挑战打开了道路。

## 参考文献

- Ali Z, Hossain MS, Muhammad G, Ullah I, Abachi H, Alamri A (2018). Edge-centric multimodal authentication system using encrypted biometric templates, *Future Generation Computer Systems*, 85: 76–80.
- Anand A, Bhambri P (2018). Character recognition system using radial features, *International Journal on Future Revolution in Computer Science & Communication Engineering*, 4(4), 599–602.
- Ansari N, Sun X (2016). Edge IoT: Mobile edge computing for the internet of things, *IEEE Commun. Mag.* 2016, 54: 22–29.
- Ara A., Al-Rodhaan M., Tian Y., Al-Rodhaan A (2017). A secure privacy-preserving data aggregation scheme based on bilinear ElGamal cryptosystem for remote health monitoring systems, *IEEE Access*, 5: 12601–12617.
- Bhambri P, Dhanoa IS, Sinha VK, Kaur J (2020). Paddy crop production analysis based on SVM and KNN classifier, *International Journal of Recent Technology and Engineering*, 8(5): 2791–2793.
- Bhambri P, Singh M, Dhanoa IS, Kumar M (2022). Deployment of ROBOT for HVAC duct and disaster management, *Oriental Journal of Computer Science and Technology*, 15, 1–8.
- Bhambri P, Singh M, Jain A, Dhanoa IS, Sinha VK, Lal S (2021). Classification of gene expression data with the aid of optimized feature selection, *Turkish Journal of Physiotherapy and Rehabilitation*, 32: 3.
- Bhambri P, Singh S, Sangwan S, Devi J, Jain S (2023). Plants recognition using leaf image pattern analysis, *Journal of Survey in Fisheries Sciences*, 10(2S): 3863–3871.
- Bithas PS, Michailidis ET, Nomikos N, Vouyioukas D, Kanatas AG (2019). A survey on machine-learning techniques for UAV-based communications, *Sensors*, 19(23): 5170.
- Du M, et al (2018). Big data privacy preserving in multi-access edge computing for heterogeneous internet of things, *IEEE Communications Magazine*, 56(8): 62–67.
- Echeverría S et al. (2020). Kalki: A software-defined IoT security platform, *IEEE 6th World Forum on Internet of Things (WF-IoT)*, New Orleans, LA, USA, 2020, pp. 1–6. DOI: 10.1109/WF-IoT48130.2020.9221050.
- Fan CI, Huang SY, Lai YL (2013). Privacy-enhanced data aggregation scheme against internal attackers in smart grid, *IEEE Transactions on Industrial Informatics*, 10: 666–675.
- Fotouhi M, Bayat M, Das AK, Far HAN, Pournagh SM, Doostari MA (2020). A lightweight and secure two-factor authentication scheme for wireless body area networks in healthcare, *Computer Networks*, 177: 107333.
- Gao JF, Cui YH, Luo SL, Jiao LL (2019). Research on information system controllability evaluation, *Netinfo Security*, 8: 67–75.
- Granjal EM, Silva JS (2020). End-to-end transport-layer security for internet-integrated sensing applications with mutual and delegated ECC public-key authentication, *IEEE/IFIP Networking Conference*, pp. 1–9.



为了支持任务关键和安全关键型的应用，工业物联网（IIoT）设备经常被放置在噪声环境中，并且必须遵守严格的时间和可靠性标准，以及时收集环境数据并适当交付控制决策。因此，系统中执行的实时感知和控制操作的端到端（e2e）截止时间经常被用来衡量 IIoT 提供的服务质量（QoS）。要在 IIoT 中获得适当的 QoS，时隙包调度至关重要。由于 IIoT 应用的日益增长，特别是在规模和复杂性方面，实现所需的实时性能变得更具挑战性 [42]。由于大多数 IIoT 必须处理不可预见的中断，这一挑战变得更加严峻。意外之外的中断可以分为两类：来自受监测和控制环境的外部干扰（例如紧急情况识别、突发压力或温度变化），以及来自网络架构的内部干扰（例如由于多用户干扰导致的链路故障或与天气相关的信道信噪比变化）。

针对各种内部问题，研究人员已经提出了许多集中式调度系统。已有数篇关于能够适应外部干扰的关键控制系统的论文。因此，其中大多数系统的扩展性并不良好。分布式资源管理并不是一个新概念。

在现实中，无线网络社区已经深入研究了分布式技术。然而，实时端到端限制往往不是这些研究的重点。对于并发干扰保证有限的响应时间仍然是一个挑战。

## 互操作性与共存

由于 IIoT 连接的快速扩展，在有限的频谱内将有许多部署在邻近区域的共存设备。这引出了在拥挤 ISM 频段中共存的迫在性问题。为了保持设备功能，必须管理它们之间的干扰。现在及不未来的 IIoT 设备可能具有极少的内存和智能，不足以防止或减少干扰。每种 IIoT 技术都有独特的特性，这可能会带来额外的困难。未来的 IIoT 设备必须能够检测、识别并消除外部干扰，以确保和平共存。目前，已有一些关于利用频谱感知识别 IIoT 设备干扰的研究描述，但许多工作都不尽如人意，因为它们需要非常样本窗口，且现有解决方案所需的 RAM 远超过目前 IIoT 设备提供的容量。如果要在 IIoT 设备纠错码研究取得有效，那么更加注重研究和理解许多此类 IIoT 设备部署的复杂无线环境是至关重要的 [43]。多模态无线电、软件灵活性和跨技术通信是处理 IIoT 设备多样性所引发问题的三个维度。

## 隐私与安全

另一个重要的 IIoT 风险是安全。IIoT 通用是一种资源受限的通信网络，考虑到 CPU、内存和能耗，它严重依赖低带宽通道进行轻量设备间的通信。因此，传统的安全措施（如安全协议、轻量级加密和隐私保障）无法防御复杂的 IIoT 网络。在创建安全的 IIoT 协议之前，可以研究工业无线传感器网络（WSN）当前的加密方法。例如，有限的内存和处理资源限制了对资源密集型加密原语（如公钥加密 PKC）的使用。包含海量数据传输和实时需求的应用提供了更严峻的困难。有人认为采用全面的策略 [44] 来解决 IIoT 中的隐私和安全问题。这意味着在系统和产品的整个生命周期内，必须考虑平台安全、安全工程、安全管理、身份管理和工业权利管理等因素。在开发安全的 IIoT 基础设施时，有许多安全属性需要考虑 [16]：

![](img/9789815196177-C5-eq.jpg)IIoT 设备应对应对物理攻击（如被动窃取密钥和未经授权的重新编程）的防篡能力，同时允许授权用户升级设备的安全固件。

![](img/9789815196177-C5-eq.jpg)数据应保持加密状态，以维护机密性并保护 IIoT 设备免受攻击者的存储。

![](img/9789815196177-C5-eq.jpg)为了维持机密性和完整性，IIoT 设备通信网络需要安全保护。

![](img/9789815196177-C5-eq.jpg)为了确保只有授权的方可以访问 IIoT 资源，IIoT 基础设施需要有效的身份和授权方法。

![](img/9789815196177-C5-eq.jpg)尽管受到恶意用户的破坏，IIoT 设备仍应能正常运行。

## 物联网对零碳生态的未来展望

IIoT 的发展是为了改善地球生态状况 [45]。尽管其潜力尚未完全开发，但物联网技术有能力为环境问题提供新的方法。科学证明，网络连接越多，物联网社交的速度越快 [46]。云技术对于物联网至关重要。云计算可以提供更大的计算和存储空间 [47]。此外，传感器可以部署在任何地方，云服务可以处理它们收集的数据。

### 结论

目前以及在未来，气候变化对人类健康构成了严重且多样的危害。为了确保社会的发展，有必要使用系统的方法研究气候变化的影响，并开发相应的指标、框架和工具来监测和分析影响健康的各种风险因素。应对气候变化对健康的影响，需要严谨的研究、有效的政策制定、创新的联盟、大量的资金支持以及广泛的意识。在实现环境目标方面，一个极具前景且前瞻性的领域之一是 `IoT` 理念。目前已有的 `IoT` 技术已经能够分析我们世界上许多地区的生态状态。为了实现健康的可持续，`IoT` 必须与感知、通信、监测和决策辅助工具相结合。因此，需要加强对开发和实施可持续解决方案。

# 参考文献

| | |
| --- | --- |
| `[1]` | Thilakarathne N.N., Kagita M.K., Priyashan W.D.. Green internet of things: The next generation energy efficient internet of things. Applied Information Processing Systems. Singapore Springer 391402 2022 10.1007/978-981-16-2008-9_38 |
| `[2]` | Rayan R.A., Zafar I., Tsagkaris C., Romash I.. Internet of Things for mitigating climate change impacts on health. Artificial Intelligence and Internet of Things. CRC Press 317330 2021 10.1201/9781003097204-14 |
| `[3]` | Qadri Y.A., Nauman A., Zikria Y.B., Vasilakos A.V., Kim S.W.. The future of healthcare internet of things: A survey of emerging technologies. IEEE Commun. Surv. Tutor. 22 2112 11167 2022 10.1109/COMST.2020.2973314 |
| `[4]` | Gobler C.J.. Climate change and harmful algal blooms: Insights and perspective. Harmful Algae 91 101731 2020 10.1016/j.hal.2019.101731 32057341 |
| `[5]` | Li F., Newman P., Pawson S., Perlwitz J.. Effects of greenhouse gas increase and stratospheric ozone depletion on stratospheric mean age of air in 1960–2010. J. Geophys. Res. Atmos. 123 42098 2110 2018 10.1002/2017JD027562 |
| `[6]` | Hayes K., Blashki G., Wiseman J., Burke S., Reifels L.. Climate change and mental health: risks, impacts and priority actions. Int. J. Ment. Health Syst. 12 128 2018 10.1186/s13033-018-0210-6 29881451 |
| `[7]` | 国家情报情报局 Global Trends: The Paradox of Progress Available From: [`espas.secure.europarl.europa.eu/orbis/document/global-trends-paradox-progress`](https://espas.secure.europarl.europa.eu/orbis/document/global-trends-paradox-progress). 2017 |
| `[8]` | Singh G., Kumar G., Bhatnagar V., Srivastava A., Jyoti K.. Pollution management through internet of things: A substantial solution for society. Humanities & Social Sciences Reviews 75 1231 1237 2019 10.18510/hssr.2019.75162 |
| `[9]` | 世界卫生组织 WHO 气候变化与健康. 2018 Available From: [`www.who.int/news-room/fact-sheets/detail/climate-change-and-health`](https://www.who.int/news-room/fact-sheets/detail/climate-change-and-health). |
| `[10]` | de Sousa T.C.M., Amancio F., Hacon S., Barcellos C.. 巴西及全球气候敏感性疾病：系统性评价 (Enfermedades sensibles al clima en Brasil y el mundo: revisión sistemática. *Revista Panamericana de Salud Publica*). Pan Amer. J. Pub. Health 42 e85 e85 2018 31093113 |
| `[11]` | Holsinger H., Tucker N., Regli S., Studer K., Roberts V.A., Collier S., Hannapel E., Edens C., Yoder J.S., Rotert K.. 与公共饮用水系统供水建筑相关的报告军团菌爆发特征：美国，2001–2017. J. Water Health 20 4702 711 2022 10.2166/wh.2022.002 35482386 |
| `[12]` | Benedict K.M., Reses H., Vigar M., Roth D.M., Roberts V.A., Mattioli M., Cooley L.A., Hilborn E.D., Wade T.J., Fullerton K.E., Yoder J.S., Hill V.R.. 与饮用水相关的水源性疾病爆发监测——美国，2013–2014. MMWR. Rep. 66 44 1216 2017 10.1558/mm644a3 29120 |
| `[13]` | Angelici M.C., Karanis P.. 实际气候变化背景下的原虫水源性感染. Encyclopedia of Environmental Health 5 139 1 2019 |
| `[14]` | Barnes P.W., Williamson C.E., Lucas R.M., Madronich S., Paul N.D., Bornman J.F., Sulzberger B., Wilson S.R., McKenzie R.L., Austin A.T., Solomon K.R., Norval L.E., Hylander S., Rose K.C., Longstreth J., Aucamp P.J., Flint C.D., Gruijl F.R., Häder D.P., Jansen M.A., Pandey K.K., Sinclair C.A., Wängberg S., Zepp R.G.. 臭氧层消耗与可持续未来. Nat. Sustain. 2 7569 2019 |
| `[15]` | Huseien G., Shah K.. 5G 技术在气候变化中的潜在应用. 可持续性（巴塞尔） 13 179 2021 |
| `[16]` | Abd El-Mawla N., Badawy M., Arafat H.. 气候变化缓解与适应的 IoT 及未来. World Journal of Environmental Engineering 6 17 2019. 12691/wjee-6-1 |
| `[17]` | Maraveas C., Bartzanas T.. 物联网在优化温室环境中的应用. AgriEngineering 3 49 54 2021 |
| `[18]` | Salam A.. 环境可持续性与气候变化的物联网. 可持续社区发展（瑞士姆） 3 369 2020. 1007/978-3-030-3529-1 |
| `[19]` | Hossein Motlagh N., Mohammadreei M., Hunt J., Zakeri B.. 物联网与能源部门. Energies 13 249 2020 |
| `[13]` | 049 |
| `[20]` | Kelly J.T., Campbell K.L., Gong E., Scuffham P.. 物联网对医疗保健的影响和启示. J. Med. Internet Res. 22 11 e20135 020.2196/20135 317012 |
| `[21]` | Baucas M.J., Spachos P., Gregori S.. 用于医疗保健的物联网设备和辅助技术：应用、挑战与机会. IEEE Signal Process. Mag. 38 46 57 2021. 1109/MSP.2021.307529 |
| `[22]` | Ghazal T.M.. 人工智能物联网. Arab. J. Sci. Eng. 11 2 2021 |
| `[23]` | Velliyangiri G., Venkatachalam A., Ramachandran M., Kumar A., Subramanian M.. 健康物联网（IoHT）对抗新冠肺炎：近期进展综述. Computational Intelligence for COVID-19 and Future Pandemics 267 279 2022 |
| `[24]` | Miles A., Zaslavsky A., Browne C.. 用于智慧城市大气污染监测和缓解的 IoT 决策支持系统. J. Decisions Sys. 27 1 566 2018 |
| `[25]` | Mehmood M.Z., Ahmed M., Afzal O., Aslam M.A.. 智慧农业中的物联网（IoT）和传感器技术：应用、机会与当前趋势. In: Building Climate Resilience in Agriculture Springer, Cham. 339 364 2022 |
| `[26]` | Shamshiri R., Kalantari F., Ting K. C., Thorp K. R., Hameed I. A., Weltzien C., Shad Z. M.. 温室自动化与受控环境农业的发展：向植物工厂和城市农业的转型. IJABE 11 1 220 2018. 25165/j.ijabe.20181101.3210 |
| `[27]` | Van J.C.F., Tham P.E., Lim H.R., Khoo K.S., Chang J.S., Show P.L.. 集成物联网作为黑士兵幂的可持续智能养殖技术以减少食物浪费. J. Taiwan Inst. Chem. Eng. 137 104235 2022. 10016/j.jtice.2022.104235 |
| `[28]` | Luo Z., Zhu J., Sun T., Liu Y., Ren S., Tong H., Yu L., Fei X., Yin K.. 物联网在食品供应链中的应用——从碳减排视角看. Environ. Sci. Technol. 56 15 10567 10576 2022 10.1021/acs.est.2c02117 35819895 |
| `[29]` | Ebiesuwa S., Blaise O.O., Adesina A., Richmond U., Aderonke A., Rangkuti A.H.. 应对经济和环境问题的物联网（IoT）方法。 J. Theor. Appl. Inf. Technol. 100 10 22022 |
| `[30]` | Fiorini P.D.C., Seles B.M.R.P.. 缓解气候变化的循环经济业务：数字技术的作用。《气候变化缓解与适应手册》。 Cham Springer International Publishing 3873 3894 2022 10.1007/978-3-030-72579-2_171 |
| `[31]` | Ben Youssef A., Zeqiri A.. 酒店业 4.0 与气候变化。《循环经济与可持续性》 1 2 12 2022 |
| `[32]` | Sheveleva A.V., Cherevik M.V.. 石气部门的数字技术及其对联合国气候行动目标的贡献。收录 `Industry 4.0: Fighting Climate Change in the Economy of the Future`, Springer International Publishing, 2022, pp. 307-315. 10.1007/978-3-030-79496-5_28 |
| `[33]` | Staedter T.. 传感器网络监测 1,400 公里运河 [新闻]。 IEEE Spectr. 55 4 10 11 2018 10.1109/MSPEC.2018.8322033 |
| `[34]` | Koehler J., Thomson P., Hope R.. 非洲农村水服务的启动资金支付。《World Dev. 74 397 411 2015 10.1016/j.worlddev.2015.05.020 |

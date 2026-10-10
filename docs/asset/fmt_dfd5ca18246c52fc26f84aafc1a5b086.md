
- (2) 因错误输入私密代码导致身份验证失败，提供三天的纠正窗口。
- (3) 货物运输过程中发生的违约。

函数根据货物的状态逐步完全执行。在这些匹配下，对智能合约进行监控，以确保在这些情况下具有高效性能。首先，测试涵盖了检查场景，包括符合约定和适当参数的医疗货运。这确保了包裹在运输过程中不会丢失。这种严谨的测试方法通过检查动态智能合约在各种场景下的韧性和适应性，确保了真实世界交互中的可靠性。流程错误的一个示例是在未执行货运检查之前尝试为货物存款，这将导致交易失败。

# 区块链赋能医药行业

## 制药智能合约函数的性能分析

![](img/fea41dfefcdce94be900e86661d80689_235_0.png)

**图 10.12** 动态智能合约的成本性能分析 [6]。

### 10.4.2 成本性能分析

这部分侧重于衡量每个函数所消耗的价格和 `gas` 数量，以评估动态智能合约的性能。此外，智能合约有一个最小 `gas` 成本，涵盖了将任何命令部署到以太坊网络上的交易，必须满足这一条件才能执行整个交易。`Remix IDE` 能够通过输出控制台显示每笔交易的 `gas` 成本，是一个非常有用的工具。图 10.12 展示了与不同智能合约功能相关的费用和成本。该图表是智能资源消耗模式的良好范例。此外，图 10.12 中的红线代表每个用户执行的所有交易中产生的计算成本。蓝线（位于 Y 轴上，针对中大型规模的交易）代表交易费，其中包括将动态智能合约代码发送到以太坊区块链的费用。资源利用的主要分析和动态智能合约的评估必须基于此类研究。

### 10.5 结论

本章假设了一种基于设计科学范式的新方法，将动态智能合约与医药供应链业务相结合，以获得竞争优势。所提出的框架动态地集成了区块链、物联网（`IoT`）传感器技术以及智能物联网控制中心（`IoCs`），以管理药品向客户交付的安全且经过验证的分发。我们的系统通过智能合约编码和算法，其范围已足够直接实现在分发各种易腐物品的供应链框架中，尽管我们的主要重点是医药生产线。基于 `Remix IDE` 中编写代码的动态性，口袋合约（`pocket contracts`）的能力通过多种场景得到了验证，这些场景旨在恢复药品交付的信任、识别并解决运输问题以及加速退款流程。我们打算使用 `Hyperledger` 平台和开放去中心化应用（也称为 `DApps`），结合药品生产者、分销商和患者等多种现实实体来实现这些智能合约。因此，这一业务目标对于构建由动态智能合约技术支撑的受赖且稳健的供应链生态系统具有真正的里程碑意义。未来的任务将涉及在 `Hyperledger` 上部署这些智能合约，并创建包含制造商、供应商、支付方和患者等真实实体去中心化应用（`DApps`）。目标是建立一个开放且稳健的供应链生态系统。

## 参考文献

- Cohen, O., Fox, B., Mills, N., Wright, P., COVID-19 and commercial pharma: Navigating an uneven recovery, McKinsey & Company, New York, NY, USA, 2020.
- Brechtlsauer, E.D., Pennell, B., Durham, M., Hertig, J.B., Weber, R.J., Review of the 2015 drug supply chain security act. Hosp. Pharm., 51, 6, 493–500, 2016.
- Ballon, R.H., Gilbert, S.M., Mukherjee, A., New managerial challenges from supply chain opportunities. Ind. Marketing Management, 29, 1, 7–18, 2000.
- Toyoda, K., Takis Mathiopoulos, P., Sasase, I., Ohtsuki, T., A novel blockchain-based product ownership management system (POMS) for anti-counterfeits in the post supply chain. IEEE Access, 5, 17465–17477, 2017.
- Majdalawieh, M., Nizamamuddin, N., Alaraj, M., Khan, S., Bani-Hani, A., Blockchain-based solution for security and transparent food supply chain network. Peer-to-Peer Network. Appl., 14, 3831–3850, 2021.
- Abdallah, S. and Nizamamuddin, N., Blockchain-based solution for pharma supply chain industry. Comput. Ind. Eng., 177, 108997, 2023.
- Gomasta, S.S., et al., PharmaChain: Blockchain-based drug supply chain provenance verification system. Helium, 9, 7–15, 2023.
- Mangala, N., et al., Secure pharmaceutical supply chain using blockchain in IoT cloud systems. Internet Things, 26, 102115, 2024.
- Sharma, N. and Rohilla, R., A multilevel authentication-based blockchain medicine anti-counterfeiting for reliable IoT supply chain management. J. Supercomputing, 80, 4870–4913, 2024.
- Zakari, N., Al-Razman, M., Alsaadi, A., Alshareef, H., Alashaikh, L., Alharbi, M., Alomar, R., Alotaibi, S., Blockchain technology in the pharmaceutical industry: a systematic review. Peer Comput. Sci., 8, e8240, 2022.
- Huang, Y., Wu, Long, C., Dledgedger: A practical blockchain system for drug traceability and regulation, in: 2018 IEEE international conference on internet of things (iThings) and IEEE green computing and communications (GreenCom) IEEE cyber, physical and social computing (CPSCom) and IEEE smart data (SmartData), IEEE, pp. 1137–1144, 2018.
- Haq, I. and Esuka, O., Blockchain technology to prevent counterfeit drugs. Int. J. Appl., 180, 25.
- 2018. Jamil, F., Hang, L., Kim, D.H., Smart contracts for a smart ecosystem. Electronics, 8, 505, 2019.
- Mackey, T. and Nayyar, G., Medicines: a global threat. Nurs. Manage. (H), 21, 8.
- Tseng, J.-H., Liao, Y.-C., Chong, B., Liao, S.-S., Governance on the drug supply chain via gcoin blockchain. Int. Environ. Res. Public Health, 15, 6, 1055.
- World Health Organization. Standard and, 2022, [online]: https://www.who.int/health-topics/standard-and-falsified-medicines
- Swan, M., Blockchain: Blueprint for a new economy, O'Reilly Media, United States, 2015.
- He, H., Bai, Y., ADASN: Adaptive sampling for imbalanced learning. 2008 IEEE joint conference on neural networks (IEEE congress on computational intelligence), lee, pp. 1322–1328.
- Abugabah, A., Nizamuddin, N., Decentralized telemedicine framework. IEEE Access, 8, 16657–16658, 2020.
- Wood, G., Ethereum: A secure transaction ledger. Ethereum Project, Yellow Paper, 2014.
- Christidis, K. and Devetsotis, M., Smart contracts for the internet of things. IEEE Access, 4, 2292–2303, 2018.
- Rabah, K., Integration of IoT devices via a blockchain-based application, 2017, Master’s thesis.
- Jüttner, U., Peck, H., Christopher, M., Supply chain risk management: outlining an agenda for future research. Int. J. Logistics Res. Appl., 6, 4, 197–210, 2003.
- Clark, B. and Burstall, R., Blockchain, IP and the pharma industry—how distributed ledger technologies can secure the supply chain. J. Intellectual Property Law Pract., 13, 7, 531–533, 2018.
- Atlam, H. and Wills, G., Intersections between IoT and distributed ledger, in: Advances in Computers, vol. 115, pp. 73–113, Elsevier, Amsterdam, The Netherlands, 2019.
- Kuo, T.-T., Kim, H.-E., Blockchain technologies and healthcare applications. J. Am. Med. Inf. Assoc., 24, 6, 1211–1220, 2018.
- Takeda, H., Veerkamp, P., Yoshikawa, H., Modeling design process. AI Mag., 11, 4, 37–37, 1990.
- Peirce, C.S., Collected papers of charles sanders peirce, vol. 1, Harvard University Press, Cambridge, 1974.
- Purao, S., Truth or dare: the ontology question in design science research. J. Database Manage. (JDM), 24, 3, 51–66, 2013.

# 医疗数据的物联网与区块链安全

S. Pavithra*, Pavani M. and Harini D.

计算机科学与工程学院，韦洛尔理工学院，

印度泰米尔纳德邦，金奈奈

# 摘要

医疗数据的碎片化经常导致患者护理不一致，这是我们正面临的问题。我们的提议利用雾计算和区块链技术的革命性潜力来解决这一问题。区块链通过确保数据完整性、可追溯性和访问控制，消除了维护一致医疗记录的困难。通过在医疗区块链中添加增强隐私的功能，敏感的医疗数据得到了保护。我们研究了物联网（`IoT`）和雾计算当前如何演进，提升数据处理和管理能力，最终实现更好的患者护理。我们提出的范式转变了医疗生态系统，在这个生态系统中，患者隐私得到加强，数据驱动的决策变得可行，以患者为中心的概念以及各种医疗利益相关者能够轻松协作。该架构结合区块链的不可篡改性实现了安全的电子病历（`EMR`）共享，避免了患者需要反复陈述病史。我们通过开创性的个性化健康洞察仪表板，为消费者提供了一个以用户为中心的主动健康管理解决方案，该仪表板提供个性化的数据可视化和人工智能驱动的洞察。该策略的核心改变了医疗数据管理，促进了健康水平的提高理性选择。

**关键词：** 物联网、电子病历、访问控制、云、雾计算、`CP-ABE`、区块链

> *通讯作者：Pavithra.sekar@vit.ac.in

Aryan Chaudhary, Rashmi Singh and Gaurav Agarwal (eds.) 健康科学中的区块链，(229–252)

© 2025 Scrivener Publishing LLC

## 11.1 引言

在不断变化的医疗世界中，保护患者隐私信息是绝对必要的。通过仔细考虑并从文献的重要发现中汲取知识，我们提出的系统 `LightMED` 成为创新的典范。引用文献中关于区块链技术与现代计算关联的披露，`LightMED` 建立了其基础。利用区块链的不可篡改账本、去中心化和加密能力，在医疗数据管理环境中提供数据完整性、可追溯性和访问控制。`LightMED` 重申了对区块链驱动的以患者为中心的健康记录的需求，将患者优先，赋予他们权感，促进护理协调，并将患者保护放在首位。`LightMED` 工具箱中的一个核心组成部分是增强隐私的功能，根据研究 [4]，这些是医疗区块链中反复出现的主题。复杂的加密方法和访问控制措施加强了其防御，以保护医疗信息的机密性。`LightMED` 根据文献对雾计算与物联网（`IoT`）之间互利性关系的观察而进行发展。通过利用这种协作，它可以实时分析数据并增强数据存储和管理的有效性。`LightMED` 的方法受文献指导，文献强调了密文策略属性基加密（`CP-ABE`）在医疗安全中的重要性。该技术保护了基于云的医疗数据库，并使用去欺骗性访问技术确保医疗数据的强加密和访问控制。正如文献所述，`LightMED` 在资源受限的情况下使用加密访问控制算法，以保护移动云和物联网场景下的数据机密性。`LightMED` 整合了基于属性的加密（`ABE`），旨在根据建议协助应对物联网数据管理的复杂性，特别是文献建议的云端场景。`LightMED` 的设计整合了智能合约，这代表了文献中访问控制系统的蓝图。这些协议实现了安全的云端医疗记录交换。通过无缝集成外部工具进行灵活的策略管理，`LightMED` 响应了文献对有效策略更新的呼。。新技术，如用于物联网数据管理的区块链集成和基于属性的签名加密，成为 `LightMED` 基础设施的一部分，并加强了物联网领域的数据安全和控制。`LightMED` 是充分结合了这些革命性完整解决方案；它不仅仅是一个系统。

它预示了一个尊患者为核心的医疗环境，并解决了文献中提出的问题。`LightMED` 旨在通过为患者提供主动健康管理所需的知识和资源，从根本改变医疗数据管理。这是通过安全加密、复杂的访问限制和实时数据聚合实现的。接下来的每个部分将探索系统机制、安全性评估和性能的细微之处。在对文献深度理解的驱动下，`LightMED` 正在迈向患者赋权、数据安全和完整性至上的未来。通过创造数据处理的机会，进一步突显了物联网与雾计算结合的优势。密文策略属性基加密（`CP-ABE`）作为一种具有可能泄露用户风险的安全措施，对云安全至关重要。必须使用创新技术来隐藏访问策略，以保护敏感数据。这与证明了在移动云和物联网设置中使用加密访问控制机制进行数据传输的效率和安全性的研究是一致的。基于云的解决方案有效利用基于属性的加密（`ABE`），在防止未经授权访问的同时处理复杂性。在物联网数据管理方面，一种基于属性的加密的新颖方法通过保证数据安全提高了物联网数据的安全性。基于区块链的访问控制架构允许在云环境中私密交换加密的电子健康记录（`EHR`）。研究了一种整合外包策略更新的技术以减少通信开销和计算成本，以确定云托管大数据的有效访问控制。与此同时，智能合约自动了这些过程，区块链维护了不可篡改的记录账本，增强了安全管理。最终，大量的测试和比较研究表明这种技术优于以往的工作。

## 11.2 相关工作

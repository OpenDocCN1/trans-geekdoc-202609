

# 区块链赋能医药行业 225

制药智能合约函数的性能分析

![](img/fea41dfefcdce94be900e86661d80689_235_0.png)

**图 10.12** 动态智能合约的成本性能分析 [6]。

## 10.4.2 成本性能分析

这部分侧重于衡量每个函数所消耗的价格和 gas 数量，以评估动态智能合约的性能。此外，智能合约有一个最小 gas 成本，涵盖了将任何命令部署到以太坊网络上的交易，必须满足这一条件才能执行整个交易。Remix IDE 能够通过输出控制台显示每笔交易的 gas 成本，是一个非常有用的工具。图 10.12 展示了与不同智能合约功能相关的费用和成本。该图表是智能资源消耗模式的良好范例。此外，图 10.12 中的红线代表每个用户执行的所有交易中产生的计算成本。蓝线（位于 Y 轴上，针对中大型规模的交易）代表交易费，其中包括将动态智能合约代码发送到以太坊区块链的费用。资源利用的主要分析和动态智能合约的评估必须基于此类研究。

## 10.5 结论

本章假设了一种基于设计科学范式的新方法，将动态智能合约与医药供应链业务相结合，以获得竞争优势。所提出的框架动态地集成了区块链、物联网（IoT）传感器技术以及智能物联网控制中心（IoCs），以管理药品向客户交付的安全且经过验证的分发。我们的系统通过智能合约编码和算法，其范围已足够直接实现在分发各种易腐物品的供应链框架中，尽管我们的主要重点是医药生产线。基于 Remix IDE 中编写代码的动态性，口袋合约（pocket contracts）的能力通过多种场景得到了验证，这些场景旨在恢复药品交付的信任、识别并解决运输问题以及加速退款流程。我们打算使用 Hyperledger 平台和开放去中心化应用（也称为 DApps），结合药品生产者、分销商和患者等多种现实实体来实现这些智能合约。因此，这一业务目标对于构建由动态智能合约技术支撑的受赖且稳健的供应链生态系统具有真正的里程碑意义。未来的任务将涉及在 Hyperledger 上部署这些智能合约，并创建包含制造商、供应商、支付方和患者等真实实体去中心化应用（DApps）。目标是建立一个开放且稳健的供应链生态系统。

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


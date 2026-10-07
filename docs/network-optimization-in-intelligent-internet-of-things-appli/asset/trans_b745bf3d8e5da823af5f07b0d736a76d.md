

# 基于物联网的无人机网络中的安全通信与认证

- b. 确保无人机与地面控制站之间安全的协议：该协议架构中包含了一项强制指令，即确保无人机与其地面控制中心之间存在不可逾越的信道。该信道的神圣性保证了遥测数据和状态披露的无缝交换，所有这些过程都在无人机与GCS之间的固化纽带中进行。研究人员对安全方法织结构进行了严谨审查，利用了强大的 Burrows-Abadi-Needham (BAN) 逻辑和 Scythe 工具。

## 15.5.14 安全哈希方案

创新者引入了一种以哈希消息认证为核心的私有框架。该设计能够防御各种威胁，包括伪造攻击、拒绝服务攻击、数据被窃取泄露、重放攻击和虚假骗术。此外，该架构减少了存储和计算负担，导致开销降低 [32]。

## 15.5.15 三因子认证与密钥分发协议

作者引入了一种使用三元组因素的 AKA 协议。该方案利用了 Boyko-Peinado-Venkatesan (BPV) 预计算以及 4Q 技术。协议的安全性通过严谨的方法得到了增强，确保了未来的安全性。此外，对硬件的实证研究表明，4Q 曲线策略表现出显著的效率提升，运行比传统的椭圆曲线方法快 4–5 次 [33]。

## 15.5.16 用于认证的强密钥管理协议

SKMPA 依赖于两种加密方法：认证加密和 EC 密码学。使用随机预言模型和 Scythe 工具进行验证。该技术防止了篡改和重放攻击。测试证实 SKMPA 有效应对了隐藏威胁。该方法效率高，所需的计算和存储较少 [34]。

## 15.5.17 双因子轻量级验证方案

作者提出了一种基于非对称加密方法的方案。由于密钥管理问题，之前的方法面临着失去基于物联网的无人机网络访问的风险。引入的技术与替代方案相比表现出优越的安全性。它能够防御包括钓鱼和重放攻击在内的各种攻击，鲁棒性 [35]。

## 15.5.18 利用对称和 ECC 技术的加密方法

该技术通过结合对称加密和 ECC 确保了无人机和接收者的安全。它确保了匿名性，并能防御离线密码猜测以及包括篡改在内的广泛威胁 [36]。

## 15.5.19 MAC 协议（消息认证码协议）

这种方法采用了双阶段策略 [37, 38]。

- a. 数据验证：簇头节点将数据验证作为一种过滤过程。

- b. 簇识别：在目的端，采用组的验证阶段来确保数据的准确性和真实性。然而，该方法容易受到五种不同类型的攻击，包括传播延迟、数据伪造、数据操纵、重放和灰洞攻击。

## 15.5.20 基于时间凭的认证

连接到物联网 (IoT) 的无人机网络安全系统使用限时访问，并允许快速且私密的用户验证。它确保了用户和网络相互验证身份。该系统通过三种方式确认用户身份：手机、独特的物理特征和密码 [39]。

## 15.5.21 基于 PUF 的无人机间相互认证协议

该程序允许一对无人机通过 PUF 相互认证，并为加密通信创建机密密钥。这种技术使用了扩展挑战响应对 (eCRPs) 的概念。eCRP 概念有效地解决了在验证者处不存储明文 CRP 的挑战，从而阻断了任何披露 CRP 的尝试 [40]。

## 15.5.22 接入与切换方案

该方案保证了无人机能够铁固地直接进入卫星网络。同时，地面终端得益于无人机获取安全的网络服务历史记录。请注意，因为我们引入了一种定制的握手认证程序，以确保这些终端能够稳固地切换到新的无人机。准备好，因为这些协议展现了强大的安全性能，并展示了精简、加速的性能 [41]。

## 15.6 结论与未来展望

由于无人机处于基于物联网的无人机网络框架的无线通信中，强化通信安全至关重要且具有关键性。这种无线通信模式是网络攻击的磁场，攻击通过利用缺乏稳健安全协议或协议过程薄弱导致的漏洞来渗透网络。本文首先介绍了无人机、其分类、特征以及在基于物联网的无人机网络中的连接类型。通过总结表描述了作者当前的工作以及各部分的局限性。这项工作还对先前的工作与前沿认证解决方案进行了对比分析。未来的工作可以包括对所提协议进行形式安全分析（如 ProVer 和随机预言模型）。未来的工作可以使用基于区块链的轻量级认证和量子密钥分布来实现相互认证。

## REFERENCES

- 1. “Drones by the Numbers,” Federal Aviation Administration. www.faa.gov/node/54496.
2. D. He, S. Chan, and M. Guizani, “Communication Security of Unmanned Aerial Vehicles,” IEEE Wire. Commun., vol. 24, no. 4, pp. 134–139, Aug. 2017. doi: 10.1109/MWC.2016.000073C.
3. S. Tivari, “Ukraine Shoots Laser Weapons’ at Russian Drones., Dec. 2029. [Online]. Available: https://eurasietimes.com/ukraine-shooting-laser-weapons-at-russian-drones-report/
4. K. V. Rangalar et al., “Quantum Cryptography-as-a-Service for Secure UAV Communications: Challenges, and Case Study,” IEEE Access, vol. 10, pp. 1475–1492, 2022, doi: 10.1109/ACCESS.2022.3138753.
5. J. Sharma and P. S. Mehra, “Secure Communication in IoT-based UAV networks: a systemic survey,” Internet Things, vol. 23, p. 100883, Oct. 2023, doi: 10.1016/j.iot.2023.
6. GDCA, “About Know for the Internet of Things,” https://digitalca.gov/home
7. V. Chamola, P. K. Kh, A. Agrawal, N. Gupta, and M. Guizani, “A Comprehensive Review of Unmanned Aerial Vehicle Attacks and Neutralization Techniques,” Ad Net-W., vol. 111, p. 10324, Feb. 2021, doi: 10.1016/j.adne.2020.
8. J. Sharma and P. Mehra, “Survey of security challenges and prevention methods in FANET,” in B. Alam and M. Alam (Eds), Intelligent Data Analytics, IoT, and Blockchain, CRC Press, 2023, pp. 252–262. doi: 10.1201/978101003718-0
9. A. Dwivedi, A. Sharma and P. Mehra, “Energy-Aware Routing Protocols for Wireless Sensor Network Based on Fuzzy Logic: A-10 types,” EAI Endors. Web, p. 16548, Jul. 2018, doi: 10.4018/eai.6-2010.
10. C. Lin, D. He, N. Kumar, K-R. Rao, A. Vinel, and X. Huang, “Security and Privacy for the Internet of Things: Challenges and Solutions,” IEEE Commun Mag., vol. 56, no. 1, pp. 64–69, Jun. 2018. doi: 10.1109/CMC.2017.
11. L. Teng et al., “Lightweight Security Authentication Mechanism Towards UAV Networks,” in 2019 International Conference on Networking and Network Applications (NaDa), Daegu, Korea ( Oct. 2019, pp. 379–384. doi: 10.1109/NaDa.2019.
12. L. He, J. Ma, R. Mo, and D. Wei, “Designated Verifier Proxy Signature Scheme for Unmanned Aerial Vehicle Network Based on Mobile Edge Computing,” Secur. Commun. Netw., vol. 2019, pp. 1–12, Apr. 2019, doi: 10.1155/28583130.

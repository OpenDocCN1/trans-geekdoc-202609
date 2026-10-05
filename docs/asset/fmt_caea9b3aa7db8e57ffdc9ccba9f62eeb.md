
# 车载网络安全：侧重位置与身份隐私

车载网络由连接的车辆组成。它们最初的开发是为了确保用户的安全，并将互联网服务扩展到道路上。它们为道路用户提供各种类型的服务和应用程序，使旅程更加愉快和舒适。然而，网络活动可能导致新类型的风险，例如勒索、数据交易或画像分析。更糟糕的是，这些活动可能会影响车内用户的安全，并导致道路交通事故。这些风险源于对消息的拦截而产生的跟踪和隐私侵犯，而消息的交换对于参与网络是必不可少的。隐私和安全是车载网络在现实世界应用中需要解决的主要问题。

本书提出了保护隐私的解决方案，旨在保护用户的身份和在路上的位置，以防止跟踪的发生。我们的解决方案已经过实验和分析测试，以评估其在面对强攻击者模型时的性能。本书最初基于 Leila Benarous 作为其博士论文的一部分所开展的工作，现已成为一种有助于理解车载网络及其所用技术以及各种类型的资源。它强调了与其相关的隐私和安全问题的重要性，以及这些问题对用户安全的直接影响。此外，书中还包含了两种保护身份隐私的匿名身份验证方法，以及五种分别针对车载自组织网络（`VANETs`）和云增强车载联网（`CE-IoV`）的位置隐私保护方案。还包括了一种新型隐私感知型区块链伪名管理框架。该框架是安全、分布式且公开的，确保了撤销、不可否认、真实性和完整性，这些都是基本的安全需求。该建议被开发作为车载公钥基础设施（`VPKI`）的潜在替代方案。

要对导致该主题目前现状的研究进行完整的历史描述是不可能的。因此，某些主题的细节描述比其他主题少。这些选择部分反映了个人喜好和专业知识，也反映了对车载网络技术安全领域极具前景的研究和近期发展的偏好。

本书是一个开始，但许多问题仍未解决。我们希望它能启发新一代的研究人员和研究。如果没有以下人的努力，本书将是不可能的：Bouridane Ahmed 教授、Guizani Mohsen 教授、Kadri Benamar 教授、Belabbaci Youcef 教授、Ouinten Youcef 教授、Saadi Boudjit 博士、Bensaad Mohammed Lahcen 博士以及 Oubbati Omar Sami 博士。我们特别感谢 Djoudi Mohamed 先生以及故去的 Yamani Ahmed 博士的无尽支持。最后，我们感谢每位为此工作的成功做出贡献的人。作者希望您会喜欢这本书，并为自己的学习获得许多有用的想法和概述。

2022 年 6 月

Leila BENAROUS

Salim BITAM

Abdelhamid MELLOUK

# 缩写列表

| 缩写 | 全称 | 中文 |
| --- | --- | --- |
| AASS | Average Anonymity Set Size | 平均匿名集大小 |
| ASS | Anonymity Set Size | 匿名集大小 |
| AVISPA | Automated Validation of Internet Security Protocols and Applications | 互联网安全协议和应用程序自动验证 |
| BAN | Burrows, Abadi and Needham | Burrows, Abadi 和 Needham |
| BB | Big Brother | 老大哥 |
| BC | Blockchain | 块链 |
| BCN | Beacon | 信标 |
| CA | Certifying Authority | 认证机构 |
| CaaS | Cooperation-as-a-Service | 服务即协作 |
| CE-IoV | Cloud Enabled Internet of Vehicles | 云增强车载联网 |
| CIoV | Cognitive IoV | 认知联网 |
| CL-atSe | Constraint Logic-based Attack Searcher | 基于约束逻辑的攻击搜索器 |
| CLPPS | Cooperative-based Location Privacy-Preserving Scheme for Internet of Vehicles | 基于协作的联网位置隐私保护方案 |
| CM | Cloud Manager | 云管理器 |
| COO | Cooperation | 协作 |
| CPS | Certified Pseudonyms | 伪名 |
| CPU | Central Processing Unit | 中央处理器 |
| CRL | Certificate Revocation List | 证书吊销列表 |
| CS | Content Store | 内容存储器 |
| CSLPPS | Concerted Silence-based Location Privacy-Preserving Scheme for Internet of Vehicles | 基于协同静默的联网位置隐私保护方案 |
| CVD | Change VMID | 修改 VMID |
| CVDNN | Cloud-enabled Vehicle Data Named Networks | 云增强车辆数据命名网络 |
| DataPk | Data Packet | 数据包 |
| DC | Do the Change | 执行更改 |
| DDoS | Distributed Denial of Service | 分布式拒绝服务 |
| DoS | Denial of Service | 拒绝服务 |
| DRL | Data Reliability | 数据可靠性 |
| DSRC | Dedicated Short-Range Communications | 专用短距离通信 |
| EDGE | Enhanced Data rates for GSM Evolution | GSM 进化增强数据速率 |
| ERGS | Electronic Route Guidance System | 电子路线引导系统 |
| FCC | Federal Communications Commission | 联邦通信委员会 |
| FIB | Forwarding Information Base | 转发信息基础 |
| GPA | Global Passive Attacker | 全局被动攻击者 |
| GPRS | General Packet Radio Service | 通用分组无线服务 |
| GPS | Global Positioning System | 全球定位系统 |
| GSM | Global System for Mobile | 全球移动体系 |
| HLPSL | High-Level Protocol Specification Language | 高级协议规范语言 |
| HMI | Human–Machine Interface | 人机界面 |
| HSDPA | High-Speed Downlink Packet Access | 高速下行分组接入 |
| HVC | Hybrid Vehicular Cloud | 混合车载云 |
| IC-NoW | Information Centric Network on Wheels | 车载信息中心网络 |
| InaaS | Information-as-a-Service | 信息即服务 |
| IntPk | Interest Packet | 兴趣包 |
| IoT | Internet of Things | 物联网 |
| IoV | Internet of Vehicles | 车联网 |
| ITS | Intelligent Transport System | 智能交通系统 |
| LBS | Location-Based Service | 基于位置的服务 |
| LTCA | Long-Term Certification Authority | 长期认证机构 |
| MANET | Mobile Ad hoc Network | 移动自组织网络 |
| MITM | Man in the Middle | 中间人 |
| MSC | Message Sequence Chart | 消息序列图 |
| NaaS | Network-as-a-Service | 网络即服务 |
| NDN | Named Data Networks | 命名数据网络 |
| NoW | Network on Wheels | 车载网络 |
| NRV | New Reputation Value | 新声誉值 |
| NS | Network Simulator | 网络模拟器 |
| OBU | On-Board Unit | 车载单元 |
| OFMC | On-the-Fly Model Checker | 动态模型器 |
| ORV | Old Reputation Value | 旧声誉值 |
| PCA | Pseudonym Certification Authority | 伪名认证机构 |
| PIT | Pending Interest Table | 等待兴趣表 |
| PKI | Public Key Infrastructure | 公钥基础设施 |
| PoS | Proof of Stake | 权益证明 |
| PoW | Proof of Work | 工作量证明 |
| PRA | Pseudonym Resolution Authority | 伪名解析机构 |
| PROMETHEUS | Program for European Traffic with Highest Efficiency and Unprecedented Safety | 欧洲高效且前所未有的交通计划 |
| PSD | Pseudonym | 伪名 |
| PUF | Physically Unclonable Functions | 物理不可克隆函数 |
| QoS | Quality of Service | 服务质量 |
| RA | Regional Authority | 区域机构 |
| RCA | Root Certifying Authority | 根认证机构 |
| RCP | Resource Command Processor | 资源命令处理器 |
| RDC | Ready to Do the Change | 绪执行更改 |
| RFID | Radio Frequency Identification | 射频识别 |
| RS | Registration Server | 注册服务器 |
| RSU | Road Side Units | 路侧单元 |
| SATMC | Satisfiability-based Model Checker | 基于满足性的模型检查器 |
| SC | Service Continuity | 服务连续性 |
| SDN | Software-Defined Networks | 软件定义网络 |
| SDVN | Software-Defined Vehicular Networks | 软件定义车载网络 |
| SF | Selfishness | 自私性 |
| SIG | Signature | 签名 |
| SPAN | Security Protocol Animator | 安全协议动画器 |
| StaaS | Storage-as-a-Service | 存储即服务 |
| TA | Trusted Authority | 信任机构 |
| TA4SP | Tree Automata for Security Protocols | 安全协议的树自动机 |
| TMN | Testimony | 证明 |
| TPD | Tamper Proof Device | 防篡设备 |
| Tx | Transaction | 交易 |
| UMTS | Universal Mobile Telecommunication System | 通用移动通信系统 |
| V2H | Vehicle-to-Human | 车人交互 |
| V2I | Vehicle-to-Infrastructure | 车路交互 |
| V2N | Vehicle-to-Network | 车联网 |
| V2S | Vehicle-to-Sensors | 车感交互 |
| V2V | Vehicle-to-Vehicle | 车车 |
| V2X | Vehicle-to-Everything | 车万物 |
| VANET | Vehicular Ad hoc Network | 车载自组织网络 |
| VC | Vehicular Cloud | 车载云 |
| VCS | Vehicular Cloud Services | 车载云服务 |
| VIN | Vehicle Identification Number | 车辆识别号 |
| VM | Virtual Machine | 虚拟机 |
| VMID | Virtual Machine Identifier | 虚拟机标识符 |
| VN | Vehicular Networks | 车载网络 |
| VPKI | Vehicular Public Key Infrastructure | 车载公钥基础设施 |
| VS | Verification Server | 验证服务器 |
| VuC | Vehicle using the Cloud | 使用云的车辆 |

车载网络（`VNs`）由车辆、道路基础设施、路侧设备和传感器组成。它们最初的创建是为了保护道路用户并减少事故和伤亡人数。现在，它们正发展为提供高质量的娱乐信息服务。实时道路信息（如施工、交通状况、事故、天气和路况）的广播有助于道路用户轻松、安全地规划行程。车载网络提供了多种应用，包括自动驾驶。事实上，自动驾驶既可以由智能车辆独立实现，也可以通过车载网络实现，即通过网络交换道路数据以做出自动自适应驾驶决策。研究人员和工业界的愿景不仅限于提供道路安全相关的应用，还旨在将互联网娱乐信息扩展到路边缘。由于车载网络能够平稳地管理车辆交通，它们减少了燃料消耗以及毒素和气体的排放。因此，它们有助于保护环境。

然而，尽管车载网络开发是为了拯救用户生命并提供各种道路服务，并且尽管它们在保护环境方面具有益处，但它们导致了道路用户隐私的泄露。这是由于其特性需要广播实时的时空识别数据。这些识别数据可用于对用户进行画像分析和跟踪攻击。因此，安全和隐私是安全部署这些网络时必须保护并确保的两个基本问题。

## I. 动机

网络系统安全漏洞引发的损害在道德和财务影响以及对人类生命的影响方面是巨大的。技术新闻报道每年都有针对顶尖高科技公司的破坏性安全违规事件。车载网络将计算机和网络世界扩展到了道路。因此，道路安全和隐私违规导致的死亡人数更加巨大，因为它们直接关系到用户安全。

车辆不应通过其道路上的网络活动被跟踪。其用户的身份不应从车辆交换的消息中获知或提取。如果攻击者成功通过车辆的网络活动跟踪了车辆，他们可能会获知其驾驶员的日常活动、解析的轨迹、藏身处和经常出没的地方。攻击者可能会跟踪（追踪）车辆，通过交易用户数据来获利、出于个人兴趣，或使用收集到的秘密向车主勒索。泄露用户轨迹数据的后果可能导致严重风险，例如在经常出没的路线策划交通拥堵或事故。更糟糕的是，恶意攻击者甚至可能实施道路暗杀。为了避免这些严重后果并确保车载网络的安全使用，我们的研究集中在开发安全和隐私解决方案。这些解决方案降低了车载网络用户的跟踪风险。

## II. 目标

我们的研究旨在保护车载网络用户的隐私和安全。更准确地说，我们的兴趣在于保护身份和位置隐私，因为它们是互联的。其中一个暴露会导致另一个被违反，从而导致上述的伤亡。车载网络中隐私漏洞的原因是为了安全应用所需的周期性状态消息，这些消息以高频率以明文形式无线发送。此外，它们包含了准确的、实时的身份和时空信息。这些信息易被拦截会导致车辆轨迹跟踪。此外，车载网络还需要确保不可否认性（问责制）、认证以及对恶意节点的撤销，以维护其可靠性。事实上，这些要求与隐私需求背道而驰。因此，在开发解决方案时，应该以平衡的方式保证隐私和安全需求。现有的保护位置隐私的解决方案使用被称为伪名的临时身份。这些伪名通过旨在降低其关联性的更改策略频繁更新。更新后的伪名之间的不可关联性（uninter-linkability）也保护了位置（轨迹）隐私。此外，伪名的使用确保了匿名性。因此，大多数现有解决方案的设计目标是保护匿名性并限制关联性以防止跟踪。

如果反复用于验证车辆与基础设施、机构和服务提供商的身份，身份隐私可能会被进一步暴露。因此，我们专注于开发保护隐私的认证方案，也称为匿名认证方法。在设计这些解决方案时，我们打算让它们对针对车载网络（如女巫攻击）和认证系统的安全攻击具有弹性免疫力。

目前，车载网络是基于权威的，即车辆注册和证书颁发由权威完成。该权威通过撤销违规节点和追踪诚实节点来确保网络的正确功能。这意味着车载网络中的隐私是有条件的；只有当车辆行为不当并破坏网络功能时，隐私会免受其他车辆的侵犯，但会暴露给权威。此外，权威为车辆提供安全参数、密钥、证书和算法。基于权威的系统被称为车载公有密钥基础设施（`VPKI`）。`VPKI` 优于自生成密钥系统，因为它满足了车载网络所需的主要需求，例如防止女巫攻击、保证条件性隐私、确保不可否认和撤销等。因此，绝大多数保护车载网络隐私的现有解决方案都是构建在 `VPKI` 之上的。

在下文中，我们解释了本书的目标：

*   我们的第一个目标是理解车载网络的特征和类型，并回顾其安全问题和来源。我们的关注点是认证和隐私问题。

*   我们的第二个目标是在不违反任何身份隐私的情况下确保认证。然而，保护隐私的认证方法（也称为匿名认证方法）可能会引发其他安全违规。匿名可能导致无法追溯的网络利用。它也可能干扰网络运行。此外，它违反了不可否认和撤销要求。因此，在开发匿名认证方法时，我们首先考虑如何解决上述问题。

*   我们的第三个目标与为车载自组织网络开发独立于基础设施、人群和地图的位置隐私保护方案有关。讨论的解决方案是伪名更新策略，它们在保持网络正确功能的同时降低关联性。这些解决方案旨在保护位置隐私，即使在可能发生跟踪的低密度道路上。

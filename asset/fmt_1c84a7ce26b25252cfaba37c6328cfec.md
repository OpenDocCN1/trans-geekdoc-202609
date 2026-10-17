
[22] ITU-T, ‘The Tactile Internet,’ International Telecommunication Union (ITU), Technology Watch Report, August 2014. [Online]. Available: `https://www.itu.int/dms pub/itu-t/oth/23/01/T23010000230001PDFE.pdf`.

[23] A. Aijaz, Z. Dawy, N. Pappas, M. Simsek, S. Oteafy and O. Holland, ‘Toward a Tactile Internet Reference Architecture: Vision and Progress of the IEEE P1918.1 Standard,’ *arXiv:1807.11915*, 2018.

[24] M. Simsek, A. Aijaz, M. Dohler, J. Sachs and G. Fettweis, ‘5G-enabled Tactile Internet,’ *IEEE Journal of Selected Areas in Communications*, vol. 34, no. 3, pp. 460–473, 2016.

[25] A. Aijaz, M. Dohler, A. H. Aghvami, V. Friderikos and M. Frodigh, ‘Realizing the Tactile Internet: Haptic Communications Over Next Generation 5G Cellular Networks,’ *IEEE Wireless Communications*, vol. 24, no. 2, pp. 82–89, 2017.

[26] J. G. Andrews, S. Buzzi, W. Choi, S. V. Hanley, A. Lozano, A. C. K. Soong and J. C. Zhang, ‘What Will 5G Be?’ *IEEE Journal of Selected Areas in Communications*, vol. 32, no. 6, pp. 1065–1082, 2014.

[27] J. G. Andrews, ‘Seven Ways that HetNets Are a Cellular Paradigm Shift,’ *IEEE Communications Magazine*, vol. 51, no. 3, pp. 136–144, 2013.

[28] M. Maier, A. Ebrahimzadeh and M. Chowdhury, ‘The Tactile Internet: Automation or Augmentation of the Human?’ *IEEE Access*, vol. 6, pp. 41607–41618, 2018.

[29] J. M. Bradshaw, V. Dignum, C. Jonker and M. Sierhuis, ‘Human-Agent-Robot Teamwork,’ *IEEE Intelligent Systems*, vol. 27, no. 2, pp. 8–13, 2012.

[30] F. Aurzada, M. Lévesque, M. Maier and M. Reisslein, ‘FiWi Access Networks Based on Next-Generation PON and Gigabit-Class WLAN Technologies: A Capacity and Delay Analysis,’ *IEEE/ACM Transactions on Networking*, vol. 22, no. 4, pp. 1176–1189, 2014.

[31] H. Beyranvand, M. Lévesque, M. Maier and J. A. Salehi, ‘FiWi Enhanced LTE-A HetNets with Unreliable Fiber Backhaul Sharing and WiFi Offloading,’ *Proceedings of the IEEE INFOCOM*, Hong Kong, 2015, pp. 1275–1283.

[32] M. Maier and A. Ebrahimzadeh, ‘Towards Immersive Tactile Internet Experiences: Low-Latency FiWi Enhanced Mobile Networks with Edge Intelligence [Invited],’ *IEEE/OSA Journal of Optical Communications and Networking, Special Issue on Latency in Edge Optical Networks*, vol. 11, no. 4, pp. B10–B25, 2019.

[33] A. Pentland, J. Werner and C. Bishop, ‘Blockchain+AI+Human: Whitepaper and Invitation,’ MIT Press, 2018. [Online]. Available: `https://connection.mit.edu/sites/default/files/publicationpdfs/blockchain%2BAI%2BHumans.pdf`.

[34] N. Zheng, Z. Liu, P. Ren, Y. Ma, S. Chen, S. Yu, J. Xue, B. Chen and F. Wang, ‘Hybrid-Augmented Intelligence: Collaboration and Cognition,’ *Frontiers of Information Technology & Electronic Engineering*, vol. 18, no. 2, pp. 153–179, 2017.

[35] M. Maier, ‘The Tactile Internet: Where Do We Go from Here? (Invited Paper),’ *IEEE/OSA/SPIE Asia Communications and Photonics (ACP) Conference*, Hangzhou, China, 2018.

[1] M. Gray, ‘Ethereum Blockchain as a Service now on Azure,’ `https://azure.microsoft.com`.

[2] SingularityNET Whitepaper, ‘SingularityNET: A decentralized, open market and inter-network for AIs,’ November 2017. `https://singularitynet.io`.

## 2.1 简介与概述

有三种不断演进的网络技术将在 2020 年代不可避免地在全球发挥关键作用：(i) 面向大量终端和物体的物联网能力；(ii) 高容量 5G 蜂窝连接，特别是在城市和郊区环境中；(iii) 总体上增强的网络安全机制，特别是受区块链保护的交易。许多不断演进的环境将包含这三种技术。另一个趋势是智慧城市的出现。本章讨论了这一新工具和服务组合对不断扩大的商业和个人应用集合（特别是在智慧城市环境中）的协同价值。纽约市通常被认为是一流的智慧城市，作为在该地理区域工作的专业人士，作者根据参与的多个项目，对这些不断发展的学科提供了一些务实的见解。本章的重点是 IoT 和 5G 具体如何相互配合和交互，以及 IoT 应用如何使用区块链技术。

在动机部分（第 2.2 节）之后，本章简要评估了 IoT 架构，重点关注边缘结构（第 2.3 节）。随后简要讨论了适用的无线通信技术，包括新兴的 5G 蜂窝服务（第 2.4 节）。许多 IoT 应用将最初专注于智慧城市环境；因此，提供了智慧城市概念和常见智慧城市应用的描述（第 2.5 节）。随后简要总结了适用的区块链概念（第 2.6 节）。接下来，详细综述了受益于区块链的智慧城市 IoT 应用（现有或未来），重点关注边缘功能，重点介绍了以下应用领域：电子医疗、物流与供应链、监控、“钢铁环线”、市政智能服务、保险和银行业（第 2.7 节）。还提供了未来研究领域的评估（第 2.8 节）。

## 2.2 背景与动机

### 2.2.1 IoT 生态系统

IoT 应用跨越许多领域，范围从支持任务关键型环境（例如智能交通系统 [ITS]、智能电网、工业过程控制、视频监控和电子医疗），到促进面向业务的交易（例如合同、保险、银行业务和各种物流）。为了支持这些应用，各类传感器被分散在环境中；这些传感器可以是固定的，但更典型的是移动的。传感器通常（但不总是）依赖（有限的）车载电源，以旨在持续长达 10 年的小型电池形式存在。传感器非常频繁（但不总是）使用无线技术将其数据转发到聚合点，或者可能转发到最终目的地点，例如分析引擎；通常使用低功耗广域网 (LPWAN) 技术。路由点或交换节点形式的边缘聚合，可能还执行计算和处理——例如数据关联、缩减或累积——经常被使用；这种分层模型不仅减少了直接访问云驻留分析的节点数量，从而减少了网络流量，而且通过仅需足够的传输功率即可到达邻域（或相邻）节点，支持了低功耗传输（延长电池寿命）[1][2]。

### 2.2.2 IoT 生态系统中的边缘计算

就本文而言，雾计算和雾网络意味着本地枢纽设备处的面向内容的计算和通信能力，包括将这些能力直接嵌入智能对象本身的情况。边缘网络和计算意味着一组支持雾计算的本地或分散设备的大规模网络聚合，以及可能的额外面向内容的计算。雾网络也被称为“一个雾”。实际上，雾计算意味着在云软件计算资源和 IoT 设备之间“插入”一个新层 [3]。雾计算是一种范式，它使用一组位于边缘、靠近终端节点的雾节点，以卸载原本由云中驻留的数据中心提供的部分功能。在某些情况下，这些边缘和网关节点本地可用的计算能力相对较低；在其他情况下，边缘设备能够支持大量的计算、存储和本地通信。可以将雾网络称为允许远程分散的 IoT 节点与雾节点通信的面向设备的通信链路集合 [4][5][6][7][8][9][10][11][12][13]。在某些环境或实现中，雾功能和边缘功能是共置的或逻辑上合并的；然而，在其他环境中，它们显然是截然不同的。

![Figure 2.1 Various edge and fog arrangements.](img/fig2_1_B.jpg)

*图 2.1 各种边缘和雾的布置。*

图 2.1 示意性地描绘了一些边缘环境和雾计算环境的示例。某些物联网应用需要完全分布式的物联网设备，这些设备广泛分散在开放环境中；这些系统通常包含一个显式的雾层，在数据经过广域网 (WAN) 到达服务丰富的云端之前，可在该层进行聚合、协议转换、处理、暂存及其他功能。某些物联网应用涉及特定行业的物联网设备集合，例如智能电网或交通铁路系统；这些系统可能在边缘侧聚合，但通常使用特定行业的传统网络（图中显示为“外部网络”）。其他应用则在地理上或管理上更为局部化，例如工业物联网环境或企业物联网环境——如楼宇管理系统 (BMS)；这些系统可能采用局部的有线或无线局域网进行聚合，并接入广域网和云端，且可能原生使用雾层机制。

图 2.2 描绘了智慧城市物联网生态系统面向雾计算和边缘计算的物理拓扑示例，这实际上通常涉及一组完全分布式的物联网设备。在该示例中，展示了九个雾网络或边缘网络。对于若干雾网络（如雾 1、雾 2、雾 3、雾 4 等），其通信直接与附近的（蜂窝）基站相连（例如用于 LTE-M 或 NB-IoT 服务）；雾计算功能位于接入网络深处，例如可能位于移动中心局 (MCO)。在雾 2 中，附近的基站通过光纤链路连接到 MCO；在雾 3 中，附近的基站通过微波链路连接到 MCO。若干雾网络（如雾 5、雾 6、雾 8）使用严格的本地聚合或网关功能，在到达核心网或云网络的内层之前，这些功能可提供网络处理（如复用或防火墙）或数据处理功能（如数据汇总、平均、临时存储）。

![图 2.2 智慧城市物联网面向雾计算和边缘计算的物理拓扑示例。](img/fig2_2_B.jpg)

*图 2.2 智慧城市物联网面向雾计算和边缘计算的物理拓扑示例。*

### 2.2.3 物联网安全概念

在物联网和智慧城市环境中考虑区块链机制 (BCM) 有一些基本驱动因素：鉴于涌现的物联网应用浪潮，人们现在清楚地认识到网络安全在物联网中至关重要。正如在信息技术 (IT) 领域的情况一样，物联网中也需要检测和修复针对物联网设备或系统的常规威胁以及高级持续性威胁 (APT)。鉴于其分布式、动态和高度互联的范式，物联网系统呈现出扩大的网络攻击面。物联网赋能应用中的安全和隐私威胁包括但不限于：伪造、篡改、数据隐私、女巫攻击、窃听、干扰、拒绝服务、中间人攻击、冒充、身份隐私泄露、使用隐私泄露、位置隐私泄露，以及操作系统和应用软件上传被损坏。

因此，物联网需要全面的安全支持，特别是对于任务关键型应用，还包括位于传感器下游的关联业务分析。物联网安全 (IoTSec) 领域现在开始融合发展（例如参见 [14,15,16,17,18,19,20,21,22,23,24,25]）。已经开发出大量技术来应对网络安全风险，尽管这些方法和技术往往复杂且“多维度”（例如但不限于 [26,27,28,29,30,31,32,33,34,35,36,37,38,39])。安全通常从完整性（确保通过网络接收或静止存储的信息正如其所应有的那样，未遭受恶意操纵）、系统可用性（授权用户对数据的访问应无阻碍且可靠）和机密性（信息的可理解性应限制并保护给授权方）方面来定义。在完整性的语境下，区块链是一种按时间顺序将交易——信息或数据——存储在一组原则上对恶意实体防篡改的计算机存储设施中的数据库。这些交易反过来可以由系统中的所有用户共享。信息作为公共账本发布或存储，无法被秘密修改。生态系统中的每个节点维护的账本信息与网络中所有其他用户或节点相同。因此，BCM 可用于解决伪造、篡改和软件分发问题。

虽然组织的 IT 基础设施事实上已经脆弱，但在物联网旗帜下引入广泛分散、物理可访问、低复杂度的设备，必然会导致整体攻击面扩大，如果不加控制，这可能会为黑客和入侵者提供一个不受监控的后门，以窃取组织 IT 领域的关键信息；这在广为人知的案例中已经发生。这种扩大的攻击面迫切需要端到端的安全缓解措施。此外，物联网应用所创造的环境可能增加经历 IT 基础设施入侵的总体风险。另外，如前所述，许多高密度应用——例如智慧城市环境中的应用——利用物理网关聚合本地流量；这些网关或雾节点可能代表易于被利用进行渗透的“触手可及的目标”。例如，近年来人们对发电厂和电网的渗透与破坏，以及因监控与数据采集 (SCADA) 管理和控制系统潜在妥协导致的燃气管网渗透与破坏，存在重大担忧。网络摄像头和其他摄像头仍然特别脆弱 [40]。

除了许多物联网端点拥有有限的计算、内存和电源资源这一事实外，限制了与安全相关的处理量，一些不断发展的技术可能会进一步加剧保护物联网生态系统的任务。例如，5G 蜂窝系统可能会增加小区的数量和类型，范围从微小区、宏小区到云无线接入网络（`C-RAN`）。在 `C-RAN` 中，许多小区的基带处理被汇集并集中化。`C-RAN` 预计将体现虚拟化的概念，遵循运营商向网络功能虚拟化（`NFV`）网络元素（`NE`）迁移的计划。`NFV` 由减少硬件占用空间和电力需求、改进配置间隔以及降低成本的需求驱动。然而，`NFV` 将使额外的 `NE` 面临潜在渗透和违规的风险，因此需要一些（新的）重型安全保护机制。

最近为物联网环境提出或使用了许多相对较新的安全方法和技术。至少这可能意味着一些简单直接的端点防火墙机制（尽管这些机制通常是“轻量级的”）、加密数据流、雾-骨干网交接（或云交接）处的防火墙功能、数据聚合点的防火墙功能、专门设计的安全中间件，以及保护云中分析引擎的安全机制。需要安全地识别端点设备、支持安全软件更新、提供信息流机密性、保证流完整性，并针对许多应用优化资源可用性 [[41]](#12_Chapter02.xhtml#ref2_41)[[42]](#12_Chapter02.xhtml#ref2_42)[[43]](#12_Chapter02.xhtml#ref2_43)[[44]](#12_Chapter02.xhtml#ref2_44)[[45]](#12_Chapter02.xhtml#ref2_45)[[46]](#12_Chapter02.xhtml#ref2_46)[[47]](#12_Chapter02.xhtml#ref2_47)。

如前所述，区块链共识机制（`BCM`）可以通过成为纵深防御方法背景下安全生态系统的一部分，在保护许多面向物联网的环境方面发挥作用 [[16]](#12_Chapter02.xhtml#ref2_16)[[48]](#12_Chapter02.xhtml#ref2_48)[[49]](#12_Chapter02.xhtml#ref2_49)[[50]](#12_Chapter02.xhtml#ref2_50)[[51]](#12_Chapter02.xhtml#ref2_51)[[52]](#12_Chapter02.xhtml#ref2_52)。然而，最近黑客利用智能合约和加密货币系统中的一些安全漏洞，试图攻破此类系统 [[53]](#12_Chapter02.xhtml#ref2_53)。必须妥善评估并解决这些漏洞，以避免未来繁重且昂贵的违规行为。此背景下的区块链应用将在 2.6 节 和 2.7 节 中讨论。

## 2.3 物联网架构（重点关注边缘结构）

### 2.3.1 架构概念

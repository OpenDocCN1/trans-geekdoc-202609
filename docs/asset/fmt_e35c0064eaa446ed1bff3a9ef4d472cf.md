
The Digital Railway includes the infrastructure used to support railway signalling and other safety systems. In the UK this is managed by Network Rail. The Digital Railway’s footprint on trains is largely confined to the driver’s cab, where it delivers safety systems designed to alert the driver to unexpected events and, in some cases, override train controls to stop the train. These systems currently include `ATP` (Automatic Train Protection), `AWS` (Automatic Warning System) and `TPWS` (Train Protection and Warning System). All of these systems are delivered through a dedicated communications network called `GSM-R` (Global System for Mobile Communications — Railway). Network Rail is in the process of delivering a strategy to upgrade the Digital Railway, deploying systems that provide in-cab signalling, traffic management and a connected driver advisory system. This will use the same (and upgraded) `GSM-R` to implement the following: `ETCS` (European Train Control System) to allow trains to run closer together and at their best speeds while maintaining safe braking distances, `CDAS` (Connected Driver Advisory Systems) and `ATO` (Automatic Train Operation) which provide decision support to drivers in the cab so that they have the information they need at the right time to boost performance and safety, and `TM` (Traffic Management) to optimise performance as trains flow across the network, maximising the throughput that existing track can support and adapting in real-time as network conditions change to aid rapid recovery (NR, 2018). `ETCS` is an advanced form of `ATP` and the combination of `ETCS` and `GSM-R` is referred to as `ERTMS` (European Railway Traffic Management System) (EU, 2018).

Digital Train includes the remaining on-board systems that deliver services such as `RCM` (remote condition monitoring), `PIS` (passenger information systems), `SRS` (seat reservation systems) and public Wi-Fi. These systems do not have access to `GSM-R` and use a separate `MCG` (Mobile Communications Gateway) to enable internet access using data SIMs procured from commercial `MNOs` (Mobile Network Operators).

From a rolling-stock perspective, the Digital Railway includes the train control systems that are safety-critical, whereas Digital Train includes train management systems, which may be operational or business-critical and are less regulated. Ideally the Digital Railway and Digital Train systems remain segregated, but for operational efficiency and cost management new trains are being delivered with more and more systems being interconnected.

Train Communications Networks (`TCN`) were originally based on industrial field-buses. They lacked performance and were not designed for trains. As there was no standard, proprietary designs emerged, resulting in a lack of interoperability between vehicles. Schafers and Hans (2000) describe the development of `IEC 61375-1` and its publication as an international standard in October 1999. The initial standard included only a Multifunctional Vehicle Bus (`MVB`) which connects equipment on and between vehicles and a Wire Train Bus (`WTB`) which interconnects vehicles via jumper cables or automatic couplers.

The `IEC 61375` standard, as shown in Fig. 3.1, has since been supplemented to elaborate on the protocols for the bus networks and:

i. in 2012 to add the `CAN-Open` protocol based on `ISO 11898`, much like that used in road vehicles, and  
ii. in 2015 to add the Ethernet Train Backbone (`ETB`) and the concept of an Ethernet Consist Network (`ECN`).

![image](img/fig3.1.jpg)

**Fig. 3.1.** `IEC 61375` architecture.

The components of `IEC 61375` are shown below in Fig. 3.2:

![image](img/fig3.2.jpg)

**Fig. 3.2.** `IEC 61375` series of standards.

An `ECN` is the network that serves a single Consist: “A Consist can be a train set or unit, a rake of coaches, it is a single vehicle or a group of vehicles which are not separated during normal operation. A Consist contains one, several or no Consist networks,” `IEC 61375-2-6:2016` (Draft). This is illustrated in Fig. 3.3.

使用以太网（`ETB`）连接列车意味着电子集中控制器（`ECN`）之间的通信可以利用以太网性能，最高可达 10 Gb/s（10000BASE-T）。下图所示的示例（Fig. 3.4）展示了这一点。这为列车的重新配置提供了更大的灵活性。为避免 IP 冲突，每当两个或多个 Consists（编组）合并成列车时，会进行“启动”（Inauguration）过程，该过程为 `ETB` 的所有节点分配 IP 地址并控制它们与同一骨干上其他所有节点的关系。

草案 `IEC 61375-2-6:2016` 的标题为“车上到地面通信”。该文档在 `ETB` 上引入移动连接网关（`MCG`），以实现与岸基系统的连接。

![image](img/fig3.3.jpg)

**Fig. 3.3.** 列车编组。

![image](img/fig3.4.jpg)

**Fig. 3.4.** 编组网络。

在列车上引入以太网并将其用于 interconnect `MVB`、`WTB` 和 `CAN-bus`，使得网络转变为局域网（LAN），而 `MCG` 提供的连接则为该 LAN 提供广域网（WAN）连接。`IEC 61375` 标准对网络安全方向提供的指导很少；只有尚未公开的 `IEC 61375-2-6` 才引用 `IEC 62443`，用于风险评估和缓解的指导。

除了其多代理特性外，数字列车 LAN/WAN 还具备以下特点：

i) 宽带连接通常通过 4G 实现，在铁路网络中可靠性较低；
ii) 根据 `DfT`（2017）统计，全国约有 20,000 辆客车分布在各地；
iii) 每列列车通常有 1 位或 2 位公司代表在车上，可能还有几百名乘客，其中一些乘客使用车上网络访问互联网；
iv) 列车会移动，有时速度很高。

这与基于土地的网络所面临的相同网络安全问题和风险不同。

以太网骨干自 2015 年 `IEC 61375` 标准扩展以包含 `ETB` 以来，已被纳入新列车设计和制造。公共 Wi-Fi 已成为客户体验的基本要求，且政府对铁路行业的影响也在增长，旧车队也在被配备“以太网骨干”和 `MCG`，以提供公共 Wi-Fi 和“信息娱乐”服务。当该网络仅用于公共服务时没有问题，但一旦网络可用，列车工程师很难抗拒将其用于连接其他系统。尽管一些行业组织已发布指南，但具体的设计原则仍然很少，且现有的原则在电源、空间和成本受限的老车改造时受到限制。

在谈到改造系统时，`RSSB`（2016）指出，由于车上网络实现的零散性，出现了诸多问题，这归因于网络认知水平低和商业影响不协调。`RSSB` 倡导为列车提供独立的网络，但也认识到整合的趋势，并警告：“完整性必须稳健，并配备安全和隐私控制”。具体而言，车上系统的连接最初是通过单独的系统升级实现的，例如为单个设备引入 4G 接收器，这使得座位预约显示屏等设备能够远程更新。类似地，一些基于状态的监测系统也通过 4G 连接被更新，以便离线上传数据。公共 Wi-Fi 在列车上推出后，推动了 `ETB` 的改造，尽管其架构比 `IEC 61375` 定义的更为简化。一些人士认识到网络隔离和安全控制是必要的考虑，早期的 Tonks（2016）等出版物提高了对新兴需求的认识。

![image](img/fig3.5.jpg)

**Fig. 3.5.** 基本改造架构。

最初的网络隔离设想是物理隔离，双骨干设计最初被提出，但交换机的复制成本、车上空间不足以及在许多情况下电源不足，使得供应商倾向于使用单骨干方案，如上图 Fig. 3.5 所示（复制自 Duffy 2018），该图展示了仅为提供公共 Wi-Fi 而实现的典型实现。

同一来源（Duffy 2018）中，还展示了一个更为复杂的设计，用于容纳更广泛的车上系统连接，如 Fig. 3.6 所示。

无论是 `IEC 61375` 标准还是铁路供应链所宣传的方案，都很少提及网络安全，但显然这些集成方案的进步会影响 both threats（威胁）和 vulnerabilities（脆弱性）。过去，车上所有系统相互独立，需要专门知识才能访问；大规模集成扩大了可利用的攻击面。以太网作为链路层协议，进一步扩大了攻击来源，因为它使更广泛的行为体能够对其进行攻击。在企业环境中，这种情况是难以想象的且通常不被容忍，但铁路行业相对滞后，安全要求大多由法规而非企业风险管理驱动。

![image](img/fig3.6.jpg)

**Fig. 3.6.** 复杂改造架构。

### 3.2. 在搜索解决方案

许多国际标准被全球同行组织采纳并重新命名，以标识本地标准机构的批准。例如，`ISO 27001` 在英国也称为 `BS EN ISO/IEC 27001`，在澳新地区称为 `AS/NZS ISO/IEC 27001`。德国的 `DIN`（Deutsches Institut für Normung e.V.，德国标准化协会）则发布 `DIN EN ISO/IEC 27001` 等标准。标准引用要求以“授权组织和年份”形式引用，例如 27001 可写作 `BSI (2013)`。由于 `BSI` 在该年份发布了大量标准，包括本文档中引用的其他标准，为了可读性，本文在引用标准时使用基本命名，不加前缀，并在首次出现时注明完整的命名，以指明标准的版本。例如，27001 可写作 (`BSI, 2013`) `27001`，也称为 27001；`IEC 62443-1-1` 在撰写时尚未被纳入 `BSI` 目录，故写作 (`IEC, 2009`) `62443-1-1`，也称为 `62443-1-1`。

行业指南来源于政府和非党派行业组织，包括 `NCSC`（National Cyber Security Centre）、`DfT`（Department for Transport）、`DCMS`（Department for Digital, Culture, Media and Sport）、`HSE`（Health and Safety Executive）、`RDG`（Rail Delivery Group）和 `RSSB`（Rail Safety and Standards Board）。

`RDG`（2017）发布的《铁路网络安全策略》由 Rail Delivery Group（铁路运营公司集团）出版，是一个代表 Train Operating Companies（列车运营公司）利益的行业组织。该文档引用了多项标准，包括 (`BSI, 2013`) `27001` 以及 `NIST Cyber Security Framework` (`NIST, 2018`)（2017 年版本参考的是 2017 年版本，该版本又引用了 (`BSI, 2011`) `62443`（实际为 2009 年的 ISA 版本）以及其他安全标准）。

在英国，“运输”属于关键国家基础设施（`CPNI, 2018`）。政府将交通部（`DfT`）确定为“主管当局”，`DfT` 将 `TOC` 纳入“铁路运输”子行业（`DfT，2018`）的 `NIS` 指令（Directive (EU)，2016/1148）适用范围内，因此合理的做法是遵循能够以最具成本效益方式实现 `NIS` 合规的标准。`NCSC`（2018a）对此提供了部分指导，并有效指向 27000 系列和 62443 系列标准。

无论哪种安全标准最适合该环境，均远非显而易见。下图（Fig. 3.7）展示了行业可用的部分材料及其相互作用。

如 Fig. 3.7 所示，关于 IACS 以及特别是关于列车的指导资料丰富，但整体上较为模糊，仅提供可能性。这不仅是铁路行业的问题。例如，Leszczyna（2018）在对智能电网适用标准的调查中指出：“操作人员可能发现自己难以在大量文献中定位自己”。

![image](img/fig3.7.jpg)

**Fig. 3.7.** 行业指导。

行业指导文档的共同主题是：建议基于与网络安全相关的要求标准来开发管理体系。`NIST`（2018）在这方面非常有帮助，因为它包含了满足其定义的每个子类别需求的多个标准参考。这可能是因为 `NIST` 提供的是自愿框架，而非像 `NIS` 那样的强制性指令。`RDG`（2017）同时引用了 `NIST`（2017）（`NIST` 每年更新，`RDG` 引用当时最新版本）和（`BSI，2013`）`27001`。而 `NIST`（2017）本身又引用了（`BSI，2013`）`27001` 以及若干 `62443` 标准（作为 `IEC` 出版物）。关键问题是：针对数字列车，哪项标准最为合适，并且能够满足 `NIS` 的要求？

在斯坦福大学的一次讲座中，Weiss（2011）阐述了 IT 安全与 IACS（他称之为 ICS）安全要求的根本差异。他指出，许多观点至今仍然成立，这解释了为何 `62443` 与 `27001` 有所不同。信息安全的目标通常以 `CIA`（保密性、完整性、可用性）三元组表示，且顺序为保密 > 完整 > 可用。此外，非否认性等因素也被考虑，但 `CIA` 是基础。在 IACS 中，强调点转移而非保护知识产权。

| `CIA` | IT 目标 || IACS 目标 |

| --- | --- | --- |

| C | 保密性是 IT 的首要任务，因为它保护的是个人或组织委托给系统的私有信息。保护责任通过 `GDPR` 强制执行。 | 保密性对 IACS 通常不重要。虽可能涉及专有信息，但数据主要为控制信号，先创建后消费。安全是首要指令。 |

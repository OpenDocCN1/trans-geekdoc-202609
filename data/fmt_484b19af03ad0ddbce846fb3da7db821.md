
# Oaken Innovations 与 MOBI 联盟

Oaken Innovations（前身为 Project Oaken）作为一家 IoT 和区块链初创公司，也是最大、最知名的区块链联盟——Mobility Open Blockchain Initiative（MOBI）的成员。MOBI 于 2018 年中启动，合作伙伴包括宝马、博世、福特、通用汽车、雷诺等汽车制造商，代表了全球 70% 以上的车辆产量。MOBI 旨在加速采用并推广区块链及相关技术标准，造福出行行业和消费者。该联盟最近发起了 MOBI Grand Challenge（MGC）竞赛。根据新闻稿，MGC 获胜者必须展示区块链及相关技术——分布式账本、加密学、代币和共识机制——如何利用车辆的连接性和算力，延伸自动驾驶汽车的“有效感知范围”，使出行更安全、清洁、快速、高效和普及。

汽车行业反复作为革命性技术和流程（装配线、精益及 JIT 生产）的先驱和早期采用者（可互换零件），展现出对分布式账本技术同样的接受度和快速采用步伐，预示着其改变所有行业的潜力。

---

# 区块链与其他技术的协同：考量与挑战

本章探讨了区块链在供应链背景下发挥作用的广泛用例：首先是集装箱航运，重点介绍了 IBM-Maersk 倡议和涉及 94 方的 TradeLens 跨境联盟；其次是构建可持续、环保的区块链棕榈油供应链；第三是汽车架构，特别是合同制造供应链。这些用例的多样性凸显了区块链作为变革性技术的巨大潜力。

从这些案例研究和前几章可以清楚地看出，区块链为供应链合作伙伴之间的数据驱动交互带来了根本性的新能力，增强了信任并减少了摩擦。它创造了一种共享知识的方式，不仅跨越全球供应链中的所有公司，还可根据业务需求在特定公司子群体间共享。由于区块链技术的不可变性，共享数据更值得信任。所有接收信息的各方都可以确信，他们收到的信息与其他每个接收者完全相同，且顺序一致。它支持自主、透明和公平的计算，恶意或自私的各方若篡改数据将难以逃避检测。它支持智能合约的创建和执行，可由业务逻辑触发，处理从订购、推动合作伙伴间货物流动到支付的一切事务。

鉴于这些用例和类似场景，有几个技术相关的考量值得关注：

## 区块链采用面临的挑战

### 公有链与许可链的对比

正如我们所讨论的，可用于供应链应用的区块链技术本质上分为两大类，因此必须决定采用哪种类型的技术。`Ethereum` 或 `EOS` 等公有链因运行在更多节点上且天然更加开放，允许更灵活的参与，因此提供了更高的安全性；然而，目前它们的速度相对较慢，且对于具有大量交易速率的商业应用扩展性较差。另一方面，`Hyperledger Fabric` 等许可系统原则上速度更快，但需要一定程度的中心化许可，参与者获许后方可互相交互。支持在公有链上实施权限控制的新型混合系统正在开发中，但可能还需要数年时间才能满足许多应用的性能要求。

### 联盟治理

在将业务网络引入区块链时，它们必须在联盟的背景下聚集在一起，例如由 `TradeLens` 为集装箱航运组织的联盟。然而，此类联盟的治理规则需要经过仔细考量，并由所有参与方达成一致，以确保整个生态系统被视为公平且值得信赖。即使对于此类基于区块链的供应链联盟的形成与运营最佳实践的确定而言，目前仍处于相对早期阶段。

### 标准与互操作性

不同行业，甚至同一行业内的不同公司，可能使用不同的软件进行数据和运营管理，如 `ERP` 和 `CRM` 系统，因此需要通用的数据标准，以便它们能够上传和下载通过区块链共享的数据。虽然此前已有采用通用数据标准用于供应链特定方面的案例（如 `GS1` 标准），但未来区块链技术的采用将需要更多的标准化工作。现有软件工具将需要增强或与新的网关软件集成，以便连接到区块链。此外，物联网系统在供应链中的采用新发展也将带来挑战；例如，集装箱中的温度传感器用于监控运输途中对温度敏感的货物，可能需要连接到基于区块链的验证或智能合约，以自动触发相关行动，如对交付的一批货物进行付款或拒收。

### 设备完整性

虽然区块链可以保证账本上的数据防篡改，但它无法保证数据来源合法（只能保证录入数据的源头持有特定密钥），也无法保证数据源本身在硬件层面未被篡改。

### 身份与访问管理

同样，为各种供应链用例开发许可区块链的一个关键但极具挑战性的方面，是对多层级身份的管理，涵盖从设备身份到个人身份（及相应的访问权限）再到组织身份。

### 隐私保护

随着 `GDPR` 等新法律的出现，对保留属于其他实体的隐私敏感数据提出了严格要求，包括撤销数据访问的可能性，因此设计用于共享数据的系统必须极其谨慎，以确保隐私敏感数据以合规方式进行管理，防止数据资产转变为数据负债。

随着区块链技术的演进并开始在供应链中针对本章涵盖的用例等场景得到采用，上述挑战将需要社区共同应对。

## 参考文献

*   Ayers, JB (2006) [Online] <https://trove.nla.gov.au/work/20348325?q&versionId=24048397> (archived at <https://perma.cc/74YV-RYEY>)
*   `bbc.co.uk` (2018) Iceland Christmas advert: What is palm oil? CBBC Newsround. [Online] <https://www.bbc.co.uk/newsround/39492207> (archived at <https://perma.cc/XG92-2LJH>)
*   de Haas, J (2016) *Gard Guidance on Freight Containers, Gard AS*
*   Dyer (2000) [Online] <https://dspace.mit.edu/bitstream/handle/1721.1/1441/147b.pdf?sequence=1> (archived at <https://perma.cc/KL4U-EARM>)
*   Neslen, A (2017) Pepsico, Unilever and Nestlé accused of complicity in illegal rainforest destruction, *Guardian*. [Online] <https://www.theguardian.com/environment/2017/jul/21/pepsico-unilever-and-nestle-accused-of-complicity-in-illegal-rainforest-destruction> (archived at <https://perma.cc/NHV4-F2P8>)
*   Rainforest Action Network (2018) Leuser watch: Rainforest Action Network. [Online] <https://www.ran.org/leuser_watch_ptabn> (archived at <https://perma.cc/8GXS-J4P8>)
*   Reuters (2018) Can blockchain ensure Unilever's tea farmers produce a fairer brew? [Online] <https://www.reuters.com/article/us-malawi-tea-technology/can-blockchain-ensure-unilevers-tea-farmers-produce-a-fairer-brew-idUSKBN1E729G> (archived at <https://perma.cc/8QRX-K3TD>)
*   Statista (2017) Total number of Unilever employees worldwide 2003–2017 statistic. [Online] <https://www.statista.com/statistics/254366/total-number-of-unilever-employees-worldwide/> (archived at <https://perma.cc/H7C2-BNYT>)
*   Supply Chain Dive (2018) Unilever taps into blockchain to manage tea supply chain. [Online] <https://www.supplychaindive.com/news/unilever-blockchain-tea/513365/> (archived at <https://perma.cc/U7AH-LSR8>)
*   Transparency, U (nd) Unilever releases locations of palm oil mills in a bid for supply chain transparency, Space Intelligence. [Online] <https://www.space-intelligence.com/2018/04/12/unilever-releases-locations-of-palm-oil-mills-in-a-bid-for-supply-chain-transparency/> (archived at <https://perma.cc/XS6Q-BY3M>)
*   Unilever (2011) [video] YouTube: Our Unilever.
*   Unilever (2018a) Transforming the palm oil industry. [Online] <https://www.unilever.com/files/origin/916ab0335769f4497b2538377259e0eaad08bd06.pdf/transforming-the-palm-oil-industry.pdf> (archived at <https://perma.cc/6XR7-FLCX>)
*   Unilever (2018b) Unilever supply chain overview. [Online] <https://www.scribd.com/document/403787781/Unilever-Supply-Chain-Overview-May-2018-Tcm244-523172-1-En> (archived at <https://perma.cc/7AHB-AYS9>)

# 区块链经济学

在本书前几章中，我们追溯了贸易与商业跨越数千年的演变历程，起始于人类走出非洲的第一波迁徙，延伸至当今及未来的现代城市发展。我们考察了供应链的演进，正是它让人类得以通过商品和服务的形式跨洲交换思想。我们探讨了区块链的基础，以及物联网、人工智能、机器学习和机器人流程自动化等其他技术如何支持不断演进的生态系统。我们的目标是，通过这些章节构建的前提，能帮助未来的供应链领导者洞悉区块链与新兴技术融合如何助力供应链转型。然而，组织在何时、为何以及如何将其传统供应链网络与新兴技术集成这一问题上，依然举步维艰。

## 区块链经济学：投资决策新范式

问题依然存在：你应在何时在组织中实施区块链？应投入多少资源？你是否拥有一个明确的理由，证明其能带来合理的投资回报率（`ROI`）？是否超过了内部门槛收益率？我们是否应等待市场成熟后再追赶？为何我要成为首批入局者？是否存在先发优势，如果有，具体是什么？关于区块链技术及其实施，还有许多类似的问题，它们都很合理。然而，在当今这个颠覆性的世界里，组织必须实现范式转换——从传统的严格关注 `ROI` 的方法，转向关注创新投资回报率（`ROI²`），这或许是我们刚刚创造的一个潜在流行语，旨在阐述时代的需求。

谈到传统意义上的投资回报率，`ROI` 的时钟在我们分配资本时开始滴答作响，随后我们期望产生回报，按第 0 年、第 1 年等年份计算。自然地，组织会执着于更快地获得回报。而 `ROI²` 则是一个截然不同的概念。它可以从农夫的视角来最好地理解：农夫拿 100 美元买 100 颗种子播种，明知并非所有 100 颗都会开花结果。农夫拥有洞察力，将精力和资源仅投入到发芽的种子上培育，这一策略能在有限资源下产生更大的回报。当今的创新型组织遵循的正是这一简单策略。这种 `ROI²` 策略基于这样一种理念：将投资分散到各种潜在机会中，但仅培育那些被认为最富成果的机会，而非一次只专注于单一投资。`ROI²` 领导者寻找所有创新举措的可行性，从行不通的项目转向下一个。事实上，熟练的 `ROI²` 领导者会同时尝试多种方案。我们的目标是通过章节中阐述的用例，并指出更多即将出现的用例，来吸引此类未来领导者，从而为建立内部思想领导力提供具体理由，以识别所有可能的实施领域。

![Figure 8.1 ROI versus ROI2 argument](img/M08NF001.jpg)

**图 8.1 ROI 与 ROI2 论点对比**

组织必须认识到创建 `ROI²` 范式的紧迫性，以求生存并利用塑造世界的诸多强大力量。事实上，区块链技术迅速演变并引发采用竞赛的原因在于，该技术与这些力量紧密契合。让我们看看其中一些力量，以及区块链如何可能成为加速其进程的恰当应用。

## 全球化的回流冲击

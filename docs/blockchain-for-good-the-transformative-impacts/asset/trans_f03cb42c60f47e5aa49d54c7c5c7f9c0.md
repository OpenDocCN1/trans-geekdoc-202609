
-   [通过结合这些功能和来自 Trinity、DeWS 和 WhistleBlower 的关键构建块，我们提出了一个在 [`Figure 7.4`](#ch7.xhtml#fig7_4) 中的参考架构，面向社会良好应用。为简化设计过程，去中心化架构遵循不同的层。这是一个在协作环境中运行的多方框架，其中多个利益相关者贡献计算、通信、共识和存储资源。 [`Figure 7.4`](#ch7.xhtml#fig7_4) 展示了一个包含 *N* 个利益相关者的设置。应用功能在该分层架构内执行，每一层负责特定功能，如下所述：

![Fig. 7.4 A Reference Architecture for Blockchain-based Social Good Applications. It builds on Trinity, DeWS, and WhistleBlower.](images/fig7_4_B.jpg)

[Fig. 7.4 A Reference Architecture for Blockchain-based Social Good Applications. It builds on Trinity, DeWS, and WhistleBlower.](#ch7.xhtml#R_fig7_4)

**数据通信层：** 该层负责提供 *可靠且可审计的数据交换*。它基于 Trinity ([`Ramachandran et al., 2019`](#ch7.xhtml#ref7_29)) 和 DeWS ([`Ramachandran et al., 2023`](#ch7.xhtml#ref7_28))。根据应用需求，开发者可以在 pub‑sub（Trinity）和请求‑响应（DeWS）之间进行选择，使该架构适用于现实世界的各种应用。例如，仅需要参与者之间消息交换的应用可以利用 Trinity ([`Ramachandran et al., 2019`](#ch7.xhtml#ref7_29)) 框架，而需要在数据交易中执行简单计算的去中心化应用可以采用 DeWS ([`Ramachandran et al., 2023`](#ch7.xhtml#ref7_28))。

**可验证计算层：** 该层负责可靠地执行计算。如 [`Figure 7.4`](#ch7.xhtml#fig7_4) 所示，利益相关者可以扮演验证者或求解者，如 WhistleBlower ([`Ramachandran et al., 2020`](#ch7.xhtml#ref7_27)) 所讨论。虽然智能合约提供可验证计算的机制，但其存在局限——智能合约无法运行任意计算，因为它们在诸如以太坊虚拟机（EVM）等专用执行环境中运行。EVM 缺乏对机器学习的支持，因为其计算开销高且不支持浮点运算。将可验证计算层置于区块链之外的好处在于它支持所有种类的计算，而智能合约并非如此。请注意，WhistleBlower 提出了一个在尊重区块链原则的前提下，验证任意计算正确性的架构。

**激励层：** 支持加密货币的区块链平台使开发者能够轻松集成代币，以奖励用户。该层在区块链内部运行，允许用户进行代币交易。社会良好应用通常需要持续的社区参与和参与度。通过奖励用户，社会良好应用可以最大化社区成员的作用。

**区块链层：** 其他层依赖区块链层，以提供数据和计算的验证保证，并将所有应用日志存储在不可篡改的账本中，以确保审计性和透明性。

每一层均能够支持任何要求透明、问责和可审计的数字应用。注意，所有应用通常包括不同利益相关者生成数据、对数据进行计算、基于数据做出业务决策以及接收数据警报。 [`Figure 7.5`](#ch7.xhtml#fig7_5) 展示了根据应用需求选择和包含哪些层的方式，其中区块链是唯一的共同层，因为它对透明、审计和去中心化至关重要。数据通信层对仅需要通过可审计和去中心化的渠道集体交换数据的应用很有益。这类应用可以在区块链基础设施内运行，同时排除其他所有层。此外，根据现有基础设施是否支持发布‑订阅（pub‑sub）或请求‑响应（request‑reply）通信模型，可进行进一步定制。请记住，Trinity 是发布‑订阅框架，而 DeWS 在去中心化基础设施之上提供请求‑响应框架。

![Fig. 7.5 The table shows how different layers from the reference architecture can be selected based on application requirements.](images/fig7_5_B.jpg)

[Fig. 7.5 The table shows how different layers from the reference architecture can be selected based on application requirements.](#ch7.xhtml#R_fig7_5)

当应用需要对各利益相关者产生的数据进行计算时，架构可以扩展以包含受 WhistleBlower 启发的可验证计算层。各利益相关者可以协作确定对处理数据至关重要的计算任务。随后，可随机选取一组节点来执行这些计算。在成功完成后，部分节点将转为验证者，确保结果正确计算，并在区块链上留下证明和痕迹以供审计。

此外，激励层可加入需要奖励机制以鼓励群体参与的应用。将该层纳入特定的社会良好应用，很大程度上取决于利益相关者及其运营模式。

[`Figure 7.4`](#ch7.xhtml#fig7_4) 所示的参考架构可用于构建广泛的应用。如 [`Figure 7.5`](#ch7.xhtml#fig7_5) 所示，选择区块链、数据和激励层也可以开发激励利益相关者共享数据的应用。这类应用被称为数据市场 (`Ramachandran and Krishnamachari`, `2023`; [`Ramachandran et al., 2019`](#ch7.xhtml#ref7_29))。此外，依赖第三方（如云提供商）计算的应用可以利用区块链技术激励计算资源提供者 ([`Ramachandran et al., 2020`](#ch7.xhtml#ref7_27))。 [`Figure 7.5`](#ch7.xhtml#fig7_5) 展示了这种模式，体现了所提参考架构的灵活性。

[`Figure 7.4`](#ch7.xhtml#fig7_4) 所示的架构帮助应用开发者构建仅数据、仅计算或仅激励的应用，或其组合，同时满足社会良好应用的透明、审计和去中心化等基本要求。在构建区块链基础的社会良好应用时，考虑数据治理至关重要，以确保数据所有者的权利得到尊重 ([`Garcia et al., 2022`](#ch7.xhtml#ref7_11))。此外，数据质量至关重要，因为由于“垃圾输入‑垃圾输出”问题，真正的收益来自在区块链上存储正确的数据 ([`Powell et al., 2022`](#ch7.xhtml#ref7_26))。

**结论**

总之，本章全面概述了区块链技术如何用于社会良好，既涵盖了技术挑战也涵盖了实际挑战。它解释了公钥加密、共识机制、不可篡改账本和智能合约等基础元素如何使去中心化应用更加公平。更重要的是，我们强调了区块链在供应链管理、误信息检测等范围内为应用提供透明、问责和去中心化的价值。


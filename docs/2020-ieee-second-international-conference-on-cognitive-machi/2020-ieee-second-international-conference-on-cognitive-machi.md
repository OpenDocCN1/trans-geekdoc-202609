
# 2020 IEEE 第二届认知机器智能国际会议 (CogMI) (美国亚特兰大州 2020.10.28-2020.10.31)

**摘要**—机器学习系统（MLSys）在物联网（IoT）中兴起，以提供边缘智能，推动我们迈向无处不在的智能愿景。然而，异构系统的复杂性和物联网的特性意味着，当机器学习系统在实际场景中运行时，我们面临着诸多挑战。许多学习系统已为大规模部署（例如智慧城市）而开发。为了阐明物联网的复杂性，我们通过涵盖感知与分布、云、边缘及物联网设备领域的最新进展（截至 2020 年），提出了相关的权衡方案。我们将多层系统和边缘智能定位为一种社会技术性挑战。针对设计边缘智能的挑战，我们提倡一种整体设计方法，以平衡机器学习的需求与权衡，并识别边缘智能的未来研究机会。

物联网（IoT）[4] 已经从数字连接设备的愿景成熟为智能服务 [5] 和无处不在的智能。例如，一个向服务器流传输视频的监控摄像头已不再足够。相反，摄像头被寄予提供智能服务，例如统计人数或检测入侵者，从而成为一个边缘支持的设备。智能物联网的独特之处在于具有数据处理能力 [6]，这意味着传感器数据可以被转换为信息和知识。这种抽象允许人类推断出关于系统的见解，这些见解可以用于创造超越想象之外的服务 [7]。

从历史角度看，需要人类认知来从数据中抽象出信息和知识。然而，随着机器学习算法的成功，新型技术驱动的系统可以通过人机交互提供智能服务。在物联网中广泛预测和管理运行的机器学习系统 [8]，可以从两个角度来看：用于物联网的机器学习系统支持系统的管理和组织。这些系统的设计旨在服务于物联网，通过安全、网络剖析和物联网设备识别等系统方面来改进人机交互 [10]。

## 1 引言

机器学习系统是无处不在且沉默的助手，它们为现代生活带来了秩序：引导我们进行交通分类并检测植物中的害虫，并在我们无法看到和听到的环境中充当我们的耳朵和眼睛。在这里，我们理解为什么机器学习算法通过固定数据来寻找模式和相关性，这些模式可以被利用以发现趋势和关系，并用于机器处理 [11]。许多学习算法可以在小数据集上工作，也可以处理更多数据。这使得它们在分析由数字在线服务和应用程序产生的海量数据方面极其成功。特别是深度神经网络为许多基于感知的任务产生了最先进的技术，现在被广泛用于计算机视觉、语音、音频等领域 [12]。机器学习是一个过程，当系统或过程过于复杂或难以显式建模时，数据可以揭示其演变为何的见解 [13]。同样，如果应用是动态的且随时间变化的，机器学习系统可以使用新数据来更新模式和预测，从而适应应用。

本文激发了针对多方利益者关心的问题的跨学科研究、设计需求，以及开发用于智能服务的可信边缘智能的努力。机器学习并不被认为是可靠的，因为假设在单一实体的控制和所有权下，可靠、丰富、可扩展且几乎免费的网络和计算能力是存在的。在第 2 节中，我们介绍了机器学习系统以及当前对数据、训练、推理和操作的关注。第 3 节强调了物联网在机器学习系统方面面临的额外挑战。在第 4 节中，我们从社会技术多利益相关者的角度考虑了边缘智能的权衡。第 5 节提出了可信边缘智能的展望，考虑了源于机器学习系统和物联网的关注。我们强调了可信边缘智能的机会，并在第 6 节总结。

当无法进行监督时，无监督学习不需要标签，可以考虑对模型训练的权衡。通常情况下，这些权衡影响预测性能。由于标签和数据标注的成本，机器学习系统可能会从仓库下载预训练模型，以适应新的领域 [15]。此外，预训练模型带来了重大的安全风险；

## 2 机器学习系统概述

机器学习算法通过利用转换输入变量的函数从数据中学习，以产生输出值。这通常被称为模型训练。一个训练好的模型用于计算预测值与其相应的真实值之间的误差，这被称为推理 [1]。典型的机器学习工作流涉及数据收集、模型训练和推理步骤。数据处理有两个目的：首先，通过消除离群值、噪声和错误来收集数据；其次，通过转换数据。这一过程促进了机器学习的部署，并考虑了操作方面。本节强调了数据、训练和推理的关注问题。与其详尽，不如说为物联网提供服务的机器学习系统提出了重要的考量。

经典的机器学习算法在静态、良性的假设在使用；它们假设数据不会改变，且环境是已知的 [17]，数据中包含了所有类别 [18]。这与现实不符。例如，在医学图像分类中，标签可能包含未见过的类别 [19]。虽然机器学习可以提高模型对抗攻击的鲁棒性，且终身学习 [21] 通过承认和维护知识来改进未来的学习，尽管机器学习取得了成功，但仍然需要训练出具有良好泛化能力、同时也是资源高效且鲁棒的模型。

### 2.1 模型训练

监督学习是一种迭代优化过程，旨在从数据中寻找通用参数。模型学习的目标是从有限数据寻找候选模型，使其在新数据上具有最佳性能。训练过程估计这些参数，以减少预测值与其真实值之间的误差。为了控制参数，模型还可以控制复杂性的超参数。为了找到最佳模型，应该探索不同参数和超参数的范围。这些选择中的每一个都需要计算能力、时间和能量，导致预测性能与资源消耗之间的权衡。最先进的机器学习模型（特别是神经网络）拥有数百万参数，所需的计算资源是巨大的。提高机器学习系统性能的方法是使用专用硬件设计它们，以及在云服务器上进行大规模并行模型训练 [12]。

除了训练期间消耗的资源外，监督机器学习还需要标注数据，收集既昂贵又耗时 [13]。

### 2.2 数据溯源

机器学习模型的质量受使用数据质量和分布的影响 [22]。由于数据在机器学习中的核心作用，观测数据的特征（如缺失数据、数据噪声和离群值）会显著影响训练数据的性能。可以通过进一步传播在整个机器学习工作流中生成的数据溯源来提高性能。为了开发软件方法，此类数据错误是导致机器学习的最终形态 [23]。一旦部署，数据集就是管理的一部分，因此依赖关系随数据集而增长。随着训练数据的追踪变得日益复杂 [24]。数据依赖和反馈回路通常是隐藏的，并会产生意外影响，使机器学习系统变得脆弱且错误诊断昂贵 [25]。机器学习系统还容易受到利用其数据依赖性的攻击，通过污染训练数据来实现。

在推理前对输入数据进行投毒或修改（逃逸）[16]。

### 2.3 推理关注点

训练后的模型对新输入值持续执行决策或动作。模型是一种可靠的资产，在退役之前将进行成千上万甚至数百万次预测。重训练推理发生在应用程序后台。推理通常直接服务用户，因此需要可靠性、准确性和高效性。尽管单次预测的资源需求与模型训练相比可能不高，但推理发生的规模要求具有高吞吐量、低延迟和保障性能的高效优化的流程 [26]。传统上，人们更多地关注优化而非推理。诸如 `TensorFlow` 和 `MXNet` 等近期流行的机器学习平台提供了模型优化方法，但仅靠这些是不够的。当机器学习系统代表我们做出决策和行动时，它们必须是可靠的。不同的机器学习系统提供不同的质量和准确性。需要能够保证输出和可靠性估计的方法来为推理提供质量保证 [28]。此外，可解释推理与对模型工作原理的理解限制有关，对于信任、公平和基于伦理的决策预测是必要的 [29]。

计算设备必须在多层、异构架构上交付动态且感知情境的功能 [7]。对于机器学习系统而言，这既是机会也是挑战。通过从数据中学习，它们非常适合能够在特定位置、环境或社会情况下甚至随时间推移运行的 IoT 应用。可以认为，机器学习系统是规模化交付智能设备的前提，因为显式地为 IoT 及其与物理世界、社交系统的交互进行编程是不可能的。然而，如果没有机器学习系统，将只能假设同质化且与上下文无关的云计算，并面临可扩展的数据存储、非结构化的设备端供应、高延迟和带宽瓶颈。对于 IoT 中数以十亿计的连接设备，不存在一致的环境，其中数据卸载到无线网络、异构计算基础设施以及带有物理硬件的资源受限设备在相互之间以及算法性能之间存在权衡。为了实现规模化，共识也必须达成。

### 2.4 机器学习运营 (MLOps)

负责训练模型的代码只是大系统的一个微小部分，该系统还包括配置、数据收集、验证、特征提取、资源管理、分析、过程管理、服务基础设施和监控的组件。尽管机器学习系统是由这些不同组件构建的，但模型的组织方式与软件不同 [25]。模型参数是学习来的，并取决于特征和超参数。由于用于训练的特征，单个模型是不可扩展的，且多个模型以非明显的方式相互影响。随着数据变化、方法改进或软件更改，模型如何演变 [30]。持续部署、定制和重训练是持续的。机器学习系统需要端到端软件来促进影响数据溯源、模型训练和推理的所有组件的开发、测试、配置、部署、管理和维护 [31]。

## 3 机器学习系统的挑战

智能服务中的机器学习系统受到 IoT 特性和要求的限制：分布式、物理边界且资源受限、无线连接。

### 3.1 卸载到无线通信

蓝牙和 WiFi 等无线通信网络将设备连接为本地网络，或将单个设备和本地网络连接到互联网网络 [39]。IoT 应用依赖无线通信来卸载设备收集的数据，在这些地方数据可以被清洗并与其他数据融合，从而为未来使用提供机器学习模型。卸载提供了计算能力和存储的访问，但也带来了隐私和性能问题。无线通信链路具有固定的容量和范围 [32]，可能会产生噪声，特别是当无线网络拥塞时会影响 IoT 应用。此外，机器学习系统在推理期间必须考虑本地计算的一致性，使容错性成为必要的考虑因素 [28]。此外，无线连接为具有抽象层和通信要求的机器学习系统引入了延迟、不确定性和成本。因此，卸载在收益与实时推理需求、以及机器学习系统训练更新的频率、大小和分布之间进行权衡。虽然数据路径、训练和传输量可以通过路由方案、选择和压缩进行优化，以最小化瓶颈和通信成本 [35]，但可能会降低准确性并受到设备电源和计算能力的限制。

### 3.2 跨异构设备的分布

位于网络边缘的 IoT 终端（例如服务器、传感器或手机）被称为边缘。边缘计算将云的计算能力带到端点 [31]，从而创建了一个用于模型训练和推理的地理分布式处理器网络。边缘在计算能力和连接性上各异，从在底层观察和控制环境的传感器和执行器设备到网关和云服务器。在边缘的数据处理、模型训练和推理可以以设备、网关或云为中心 [32]。以设备为中心的方法减少了卸载，但受限于计算能力。以网关为中心的方法需要网络通信，以及相关的变性和不确定性。以云为中心的方法提供了无限的存储和数据处理能力，但需要大量的通信。边缘服务器为稳定性能提供了中间解决方案。

### 3.3 资源受限

电池驱动的 IoT 设备具有有限的内存、电源供应资源，这些资源在数据和处理能力之间可用或共享 [35]。为了消除这些限制，设备端机器学习任务旨在本地进行推理和部分重训练。为了实现这一点，在这样的受限设置下，能量效率至关重要。为了减小模型尺寸，使用了量化和剪枝进行模型压缩 [42]。量化减少参数和梯度的浮点精度，可以是基于规则的 [43]，也可以通过位运算和面向符号的权重进行自动处理 [45]。在极端情况下，二值神经网络被量化为 1、2 或 3 位 [46]，并提供了卓越的效率，但以牺牲预测准确性为代价。将二进制神经网络映射到现场可编程门阵列（FPGA）上的查找表可以进一步降低能耗。剪枝消除了神经网络中大量的参数。尽管剪枝很流行，但设备端剪枝的进展是有限的，特别是当层缺乏标准性能时 [48]。设备端学习的需求日益增长是架构与神经架构搜索的协同设计。

云端已经观察到的运营挑战。此外，涉及到多个利益相关者的参与，这在本质上意味着所有权、治理、问责制和信任主导。

**表 I** IoT/CPS 的维度与关注点 [51]

| 维度 | 关注点 |
| --- | --- |
| 功能 | 驱动、通信、可控性、功能性、可管理性、可监测性、性能、物理上下文、感知、状态、不确定性 |
| 业务 | 企业、成本、环境、政策、质量、监管、上市时间 |
| 人性 | 人性因素、信赖度、可靠性、安全性、安全、逻辑时间、同步、感知、时间间隔和延迟 |
| 数据 | 数据语义、身份、数据处理、数据间关系、数据量 |
| 边界 | 行为、责任、组合、适应性、复杂性、可发现性 |
| 生命周期 | 可部署性、可设计性、可维护性、可操作性、可生产性 |

## 4 多利益相关者的权衡

物联网（IoT）不仅是技术的复杂集合，而且是多利益相关者环境下的社会技术系统 [51]，其中众多参与者连接了用户、数据生成者、网络提供商、数据处理器、参与者的利益，且设备的使用、管理和所有权是异构的并不断变化的。这种多利益相关者环境为设计智能设备的边缘智能带来了必须考虑的冲突需求和优先事项。

### 4.1 物联网中的设计维度与利益相关者的关注点

工程化系统旨在于不可预测的世界中，在接受的置信范围内提供可靠且稳健的性能。例如，在天气多变时设计飞机；我们对您的决策是基于合理的信念，即飞机经过了精心设计，交通控制系统由受过训练的飞行员操作，并且交通控制系统受到国际监管的卓越系统保护。从许多服务和行业的角度来看，物联网作为一个更大的基础设施系统。其物理-数字化的本质意味着网络领域的参与者会对环境产生真实后果，并可能改变我们对世界的体验，例如当系统被停用时感到冷。这比纯物理系统或网络系统提出了更多的要求。

物联网的规范被包含在标准中（例如 [51] 中的引用）。定义需求的一种有效方法是通过涉及一个或多个利益相关者的关注点来实现 [51]。表 I 列出了按类别分组的关注点，旨在为混合信息物理系统的设计提供一个全面的框架，例如相关的且具有可比性的关注点。例如，在考虑不确定性时，网络通信引起的延迟是不确定的。通常，关注点面临权衡，利益相关者可能会以不同的方式对它们进行优先排序。需求可以用于表达解决相关关注点的系统属性。

### 4.2 对边缘智能设计的影响

边缘智能将机器学习系统引入物联网的计算系统。与统计机器学习所发展的低风险潜力设定不同，机器学习系统如果失败，可能会产生现实世界的影响、潜在的危害甚至威胁生命的后果。由于物联网的存在，对于边缘智能的机器学习系统来说，确认物联网的需求是至关重要的。并且与其他软件系统一样，在需求阶段选择目标系统行为变得具有挑战性。可穿戴设备中的机器学习已经也需要显式的分析过程，以预先指定系统需求 [51]。这在其他领域并不是常态，而它的存在是为了开发用于应对冲突关注点和需求权衡的方法。我们需要单独和整体地考虑复杂的关注点，以及满足利益相关者优先事项需求的设计选择。

**机会：** 需要框架和资源来引出挑战、处理冲突的关注点并优先考虑权衡，以便边缘智能做出明智的设计选择。

由于其性质，物联网中机器学习系统的（隐式）设计侧重于特征工程、算法选择、参数优化、架构设计，目标是优化预测性能。从物联网的角度来看，这解决了功能维度的性能问题，但在其他关注点的短期衡量和优化方面失败了。设备机器学习（第 3.3 节）解决了关于资源限制、潜在上下文、安全性、隐私、延迟、数据量和容量关注的问题，其中分布和异构性引入了

> ¹¹物联网和信息物理系统（CPS）的定义随时间趋于融合 [52]。我们从统一的视角来看这两个领域，并将其称为物联网。

一致性和同步关注点。在服务范式中，质量起着重要作用，它是用户选择服务的衡量因素 [7]。

**机会：** 需要针对预测性能的指标和基准，以便边缘智能的机器学习系统能够被评估。问责和透明度等问题是机器学习固有的，某些算法如神经网络被认为是“黑箱”。

**机会：** 为了与边缘智能相关，物联网的关注点需要扩展以包含以数据为中心的本质。

## 5 可信边缘智能的展望

信任技术研究从信任系统扩展到非人类实体。虽然信任和可信是不同的概念，但如果技术的感知水平很高，那么仁爱、诚信和能力等类人的信任构建是良好的信任衡量。可信对于一致性是必要的。

### 5.1 AI 中的可信

创造他人社会存在感、促进社交行为（例如对话或接受情感）以及与他人进行交互的技术被认为是类人的。人工智能技术涵盖机器学习系统，因此在定义和设计上都是类人的。提高公众信任必须导致政府和组织快速开发框架。主流框架中出现的核心主题是隐私、问责、安全与保障、透明与解释性、公平与无偏见、技术控制、专业责任以及对价值观的促进 [75]。这些信任构建与被认为是类人的 AI 技术产生共鸣。虽然框架奠定了理论工作，但要实现可信 AI 需要开发可量化的可信。

**机会：** 机器学习系统的可信关注点需要标准化和操作化，以便进行客观评估。

### 5.2 物联网中的可信

相比之下，物联网中的可信关注点跨行业收集、构建，并正式定义为安全、保障、隐私、可靠性和韧性 [51]。这些关注点确保系统在不同条件下表现适当。它们要求物联网被认为不那么像人，而像机器。其他属性如可控性、可管理性、功能性和不确定性被认为是功能关注点而非可信关注点。

### 5.3 可信边缘智能的机会

无论是 AI 还是物联网的可信关注点都没有解决边缘智能的全关注光谱。例如，边缘智能中的机器学习系统在开放世界假设下运行，可能会产生新的类别、未见的示例、黑天鹅事件和对抗攻击模型。在这种情况下，解释性是一个必要的需求。或者安装在与训练数据相似的新环境中的智能设备可能会失效。这可能需要一个可信的模型。

- 分析边缘智能和智能服务的机器学习系统中产生的可信关注点
- 探索机器学习与物联网系统之间可信关注点的权衡
- 可信性与其他社会关注点之间的相互作用与权衡
- 扩展对可信机器学习的研究，以应对在边缘端出现的各种挑战和权衡。

## 6 结论

不断增长、人口密集的城市中心需要维护、照顾和培育其社会及自然系统。基于智能服务被视为实现这一目标的一种途径。机器学习系统通过为物联网（IoT）提供边缘智能，实现了智能服务。本文介绍了在为物联网设计可信机器学习系统时面临的挑战与权衡，两种技术的结合带来了新的挑战与机遇。

我们将机器学习系统定位为物联网的一个组件，将智能视为一个社会技术系统。我们认为，在开发边缘智能时，应当考虑多利益相关者的关注、设计需求和权衡，并强调了该领域出现的机遇。跨学科的方法是至关重要的，因为信任在机器学习系统和物联网中的定义有所不同。通过结合视角，考虑多利益相关者的考量、设计需求和权衡，可以感知一个可信智能与边缘服务深度融合的未来。

## 参考文献

- [1] T. Hastie, R. Tibshirani, and F. Freedman. *Elements of Statistical Learning*, 2nd ed. Springer: (2009). [Online]. https://web.stanford.edu/hastie/ElemStat.pdf
- [2] Y. Lecun, Y. Bengio, and G. Hinton. “Deep learning.” Nature, vol. 521, no. 7553, pp. 436–444, 2015.



## 参考文献

- [3] T. M. Mitchell. *The design of machine learning*. Carleton Mellon University, School of Computer Science, Machine Learning ——, 2006.

- [4] R. Minerva, A. Du, and R. Tomotani. “The trade-offs of Internet of Things (IoT).” IEEE International Int., pp. 1–8, 2016. [Online]. Available: https://doi.org/10.1109/INTII.2016.0065110

- [5] D. Gremb and P. Rosner. “The Internet of things: from internet scale to smart services.” Computing, vol. 98, pp. 1041–1058, 2016. [Online]. Available: https://doi.org/10.1016/j.future.2016.06.015

- [6] J. E. Buarque-Escuer, F. G. Gutiérrez-Navarro, L. B. Lopes, R. Butt, and M. A. Astorga, “Tracking the evolution of internet things concept across different applications,” Sensors (Switzerland), vol. 17, no. 2, pp. 28–40, 2017.

- [7] Y. Wang, J. Mehdi, O. Courant, F. Casati, X. Liu, H. Wang, Y. Bang, B. Blake, D. Softour, F. Flelay, M. Papagopoulos, H. Huang, D. Georagopoulos, L. Chen, S. Nepal, J. Malik, A. Eradi, M. Singh, “Service computing for the next 10 years,” Communications, vol. 45, pp. 62–72, 2017. [Online]. Available: https://doi.org/10.1145/29838

- [8] F. Santie, J. Hansen, and L. Robert, “From cloud to edge: an overview of machine learning architectures.” IEEE Access, vol. 6, no. 2, pp. 4921–4934, 2018.

- [9] X. Zhang, J. Wang, J. Chen, J. Li, I. Li, and M. Guizai, “Smart edge and Deep Learning for Internet of Things,” IEEE Conference on Computer Communications (ICC), pp. 1055–1060, 2018. [Online]. Available: https://doi.org/10.1109/ICC.2018.8662701

- [10] L. Liu, S. Chen, F. Feng, J. Nie, J. Lu, and J. Qi, “A survey on edge learning for IoT applications.” International Journal of Machine Learning and Computing, vol. 8, no. 3, pp. 81–99, 2018. [Online]. Available: https://doi.org/10.1007/s10532-018-0184-3

- [11] C. M. Bismuth, Pattern Recognition, and N. Robert, “Machine learning for feasible mobile devices.” IEEE Communications, vol. 53, no. 2, pp. 77–80, 2015.

- [12] J. Verbanken, M. Wolff, J. Katzy, K. Toppelburg, V. Terellen, and R. Sallvay, “A survey on edge learning for mobile computing.” IEEE Access, vol. 8, pp. 74543–74555, 2020. [Online]. Available: https://doi.org/10.1109/ACCESS.2020.299443

- [13] Y. Yang, J. Xu, D. Oldham, and C. Rea, “Data mining: Creating large sets,” Advances in Neural Processing Systems, no. 15, pp. 993–999, 2002.

- [14] Y. Chen, J. Wang, F. Liu, J. Li, K. Schawicki, and S. Gutierrez, “Integration of Machine Learning and Edge Computing.” In Proceedings of 2nd Sympos., IEEE International, pp. 1–12, 2019. [Online]. Available: https://doi.org/10.1109/ICCIT.2019.29027

- [15] H. Li, F. Bengio, and B. Wall, “Learning to come closer to the data and statistics.” In Proceedings of the ACM Conference, vol. 22, no. 10, pp. 1345–1359.

- [16] Y. Ji, J. Zhang, X. Li, and Y. Wang, “Trade-off analysis in machine learning for edge intelligence.” In IEEE Conference on Computer Science and Intelligent Systems, pp. 349–363, 2018.

- [17] I. Geoffrey, M. Pbent, and N. Papert, “Machine learning for resource-constrained mobile devices.” Communications, vol. 61, no. 7, pp. 56–66, 2018. [Online]. Available: https://doi.org/10.1145/321434.321441

- [18] H. Li, F. Bengio, and B. Wall, “Learning to come closer to the data and statistics.” In Proceedings of the ACM, vol. 22, no. 10, pp. 1345–1359. [Online]. Available: https://doi.org/10.1145/183118.183123

- [19] S. Amerahi, A. Bengel, C. Bird, R. DeLine, E. Kumar, N. Nagapur, B. Nash, and T. Zimmermann, “Software Engineering for a Case Study.” Proceedings of 41st International Conference on Software Engineering: Engineering in Practice, ICSE-2019, 299–300, Dublin.

- [25] D. Sculey, H. Holt, E. Davydov, T. Phillips, C. Sellars, J. Young, and D. Henderson, “Technical Debt in Machine Learning Systems.” Proceedings of 26th International Conference on Neural Information Processing, NeurIPS 2013, 3542–3550.

- [26] L. S. Lee, A. S. Polichenico, B.-G. Chin, M. Domingos, “Opening the Black Box of Machine Learning Systems.” Proceedings of 35th IEEE Symposium on Software Engineering and Implementation, ASEI2020, 215–224.

- [27] I. Stica, G. R. Sa, R. Popa, D. Patterson, M. Mahoney, R. Kate, J. J. Batra, and K. Suknetzer, “Scale-Net.” In K. Goldberg, A. Deller, and A. P. Berkeley, “A Review of Challenges for AI.” (2017). [Online]. Available: https://arxiv.org/abs/1711.05885

- [28] T. Abadeader, J. Hay, Y. Karaman, A. Miera, P. R. Saka, and S. Vaswani, “Deep NLP Techniques, Datasets and Challenges in Natural Language Processing and AI Control,” International Journal on Information Technology, vol. 20, no. 1, pp. 1–19, 2020.

- [29] C. Cunningham, “The Model of Technical Debt.” Interpretation: 2, 1–8, 1998.

- [30] S. Bissels, F. Tammmann, J. Damanikas, S. Selfer, and G. Szavros, “Challenges in Machine Learning Model Management: Proceedings of the 13th International Conference on Data Science and Engineering, 2018, 5–11.

- [31] N. Rister

- [32] J. Sun, Y. Li, M. W. Wenker, K. Ashford, J. Daly, and K. Kato, “S44: Scaling Language Models with Parameter and Data Size.” In 2021 International Conference on Machine Learning (ICML).

- [43] M. Racupi, A. Cappoli, and L. Benardi, “Memory-Driven Deep Learning on Resource Constrained Microcontrollers,” in Proceedings of the 3rd MLSys Conference, Austin, 2020.

- [44] T.-W. Chin, F.-I. Chiang, V. Chang, and D. Marcellisco, “Fed-Net: Fast End-to-End Optimized Neural Networks,” in Proceedings of the 2023 31st IEEE Conference on Computer Applications, Seoul, 2023.

- [40] H. Beckham, G. Andrew, U. Erlingason, S. Chen, I. Miro, N. Pope, “General Approach to Applying Differential Privacy to Robust Training.” Available: https://arxiv.org/abs/1812.06210

- [41] A. Ferada, V. Yazdan, S. Salveoni, D. Poques, R. Mortier, S. Polichenico, D. Milano, and M. G., “Co-FedLab: Enabling Federated Learning in ML-cod with Edge Nodes,” Proceedings of the 2020 IEEE Conference on Computer Communications and Networking (Net), vol. 20, 2020. [Online]. Available: https://doi.org/10.1109/COMNET.2020.299432

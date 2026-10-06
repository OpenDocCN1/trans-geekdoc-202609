
该问题可通过边缘或雾计算来解决，通过这种方式，计算能力可以更接近网络边缘或用户，从而减少将所有数据传输到云或服务器的必要性，这导致延迟降低，并且在网络带宽和数据处理方面系统效率提高。对于可持续的 `IoT-Fog` 系统，目前主要存在两个问题，第一是雾或边缘设备具有一定程度的处理潜力，第二是处理通过网络和其他系统组件传输的 `BigData`。通信网络中流动的如此庞大的数据会导致网络开销。

现在存在通常的云基础设施以及数据中心框架可能被称为分布式和并行处理，而边缘计算可以被称为分布式处理。通过以 `NDP` 形式引入创新的 `CI`，我们可以征服现有系统中阐明的问题，如第 8.2.4 节所述。

原位处理/`NDP` 被认为是由主机处理单元和用于存储的节点组合而成的软件堆栈加上硬件模型的混合。所述框架允许在原位实现计算密集型场景，这意味着在专用于数据存储的存储单元内部或附近。因此，`NDP` 试图减少昂贵的数据传输并提高系统性能。

### 8.4.1 案例研究：ISP-ML（In-storage processing – Machine Learning）框架

`ISP-ML` 架构是为 `ML` 技术使用原位处理而实现的而设计的。`ISP-ML` 是一个在系统级工作的模拟器。它是基于 synopsys 平台创建的。该平台基于语言 `SystemC`。使用 `ISP-ML` 架构，可以在 `ISP-ML` 模块上编写和执行一系列 `ML` 算法。这些算法可以用类似于 `C` 或 `C++` 的编程语言编写，并进行一些必要的更改（Lee 等，2017）。

所述框架使用 Samsung `SSDs` 作为存储节点。可以在 `ISP-ML` 框架中使用硬件的多种方式。（1）`SSD` 控制器可能消耗其内部包含的嵌入式核心。（2）通过考虑用户需求来推荐专用硬件逻辑芯片。`NAND` 通道用于数据收集。通道控制器通过其处理来自相应 `NAND` 闪存的 `R/W`（读/写）操作的能力来执行数据上的常见功能。功能的特征完全取决于要执行的 `ML` 算法的类型。缓存控制器由 `ISP-ML` 用于收集和合并每个通道控制器生成的结果。其重要用途包含在 `SSD` 控制器中作为缓存管理器（`DRAM` 管理器）。所述系统的框图由 Figure 8.2 给出

![Figure 8.2: Block diagram of ISP-ML.](img/b_9783110648195-008_fig_002.png)

Figure 8.2: Block diagram of `ISP-ML`.

性能设置利用 `PC`，该 `PC` 由 8 核 `Intel(R) Core i7` 处理器组成，安装了 `Ubuntu 14.04` 操作系统，以及一个 Samsung `SSD 840 Pro`。此外，系统使用嵌入式处理器，即 `ARM 926EJ-S`（频率 400 MHz）。系统在主机处理的内存配置为 2GB 至 32GB 的情况下进行检查。主机内处理（`IHP`）实际上投入运行，而 `ISP` 则通过新生产的模拟器虚拟运行（模拟），以比较两个系统并根据各自的性能属性直接相互权衡结果。

为计算预定义参数的梯度，使用了 `SGD`。`SGD` 是 `ML` 算法，其中参数通过每个执行周期中的单个训练样本进行更新。系统编程了不同类型的并行 `SGD` 算法，如 `EASGD`、同步 `SGD` 和 downpour `SGD`。

本案例中给出的新系统在性能方面与传统的 `IHP` 进行检查。它表明在内存不足的情况下 `ISP` 工作非常出色。分布式处理平台通常会出现通信阻塞，但 `ISP` 不会产生此类阻塞，因为 `ISP` 中的通信开销非常低。通过提高 `SSD` 内的通道数量，可以实现高度的并行性。

现在在上述系统中，随着数据量大于页面的大小，数据碎片化会定期发生，这会直接影响系统性能。系统中存在的另一个问题是数据安全，这对于 `ML` 应用而言是主要担忧，因为大多数数据可能是敏感的。在开发 `ISP-ML` 架构时并未考虑这一点。

### 8.4.2 问题和挑战

基于 NDP 的已实现系统通常会被扩展，使其更可能与少数特定的系统或应用兼容并执行更优。关注方向主要集中于数据中心架构的领域特定应用，因为受限于功耗。系统通过适用于各自软件应用和硬件的特定模拟器进行评估。系统设计在 Awan et al., (2017)、(Hong et al., (2016)、Vermij et al., (2017)、Kampars et al., (2017)、Lee et al., (2015)、Gao et al., (2016)、Gao et al., (2015)、Das et al., (2018)、Lee et al., (2017) 和 Lee et al., (2018) 中给出了基于内存处理的系统。上述架构采用了诸如混合内存立方体 (HMC)、DRAM 等元件。系统架构在 Awan et al., (2017)、Acharya et al., (1998)、Gu et al., (2016)、Riedel et al., (2001)、Sun et al., (2018)、Choe et al., (2017)、Lee et al., (2017)、Kaplan et al., (2016)、Kang et al., (2013) 和 Ruan et al., (2019) 中得到启发或提出，给出了源自存储内处理的系统设计。从所有这些系统中，若干架构使用了 HDD，少量 SDD 被使用，另外 FPGA 被用于若干系统的开发。新系统可以采用具有 RAID 能力的崭新 NVMe SSD（Gu et al., 2016）。上述现有框架所描绘的软件栈包含用于 NDP 架构硬件创建的软件应用、用于评估各自框架执行的模拟器，以及用于可编程硬件的程序 (EH)。

现有方案中的一些问题或挑战如下：

* 现有系统未考虑地理分散地点的多个存储单元，因而没有负载均衡机制。
* 现有框架仅针对特定类型的 ML 应用或算法进行调优。
* 在存储内处理场景下，在数据、硬件框架、处理器上下文切换和 OS 等多个阶段需要额外的安全保障。
* 需具备可扩展的系统，以实现在硬件和软件方面对应用可扩展性的支持。

## 8.5 建议的实现范式

CI 预计可通过从当代应用约束中导出 NDP 来发现解决方案集合。本节针对第 8.4.2 节中指定的问题提供预期解决方案的展望。

### 8.5.1 预计的工作 ML 范式

下面解释的框架包含两个主要组件，即软件栈和硬件栈。两个栈框架在此阐述。

#### 8.5.1.1 硬件组件

Figure 8.3 阐述了建议架构的硬件组件，其中包含处理/主机单元 (CPU)、内存和存储节点/设备，因为系统源自存储内处理的概念。

![Figure 8.3: Proposed system block diagram (components of hardware).](img/b_9783110648195-008_fig_003.png)

Figure 8.3: Proposed system block diagram (components of hardware).

计算机 (PC) 的 CPU 可被用作处理/主机单元，以实现主机内处理的目的。内存已默认与主机系统 CPU 耦合。需要规划和实现的关键组件是存储节点。存储驱动包含两个主要部分，即控制器单元和存储内计算。在此，SSD 可用作系统中的存储单元；控制器单元由 SSD 的固件组成；存储内计算部分包括用于运行在 SSD 上安装所需数据过滤程序的编译器。需要在存储设备上加载内核以将编译器安装到 SSD 上。这可通过使用 docker 和容器的模型来实现，该模型将有助于在磁盘固件之上添加一个软件层。

#### 8.5.1.2 软件栈

从广义上讲，计划系统的软件栈包含若干为不同功能设计的程序单元，描述如下：

* Compiler: 为了编译两侧，编程元素编译器必须为系统的所有子部分实现，即主机处理系统和驱动单元或存储单元。
* Simulator: 模拟器可大幅减少执行时间，如从数小时减少到数分钟。模拟器可在系统级开发，并可用于模拟实现。
* Program unit for host side: 软件栈的这一部分将包括用于激活存储驱动编程的编程，用于在多个存储节点之间平衡负载。
* Program unit for drive side: 该组件包含应用于存储单元或节点中累积数据的计算。可能存在适用于存储的安全技术。
* Drivers for Linux kernel: 系统驱动可能像典型存储设备一样被访问，因为它可在 Linux OS 内被视为块设备。另一个驱动管理虚拟文件功能。

软件栈将被划分为两个组件，这些组件将同时驻留在主机和磁盘上。主机侧的应用模块负责创建 ML 程序的实例，或将技术划分为更简单的模块，然后将这些模块转发到存储节点进行进一步处理。远程过程调用可用于将应用程序或其模块从主机迁移到存储。可以创建一种“回旋镖”模式，其中主机上的调用函数将模块卸载到存储，在存储上本地处理数据并将结果集返回给调用函数。远程过程调用的第二种实现模式是基于代理的。在这种实现方案中，主机上的卸载函数将对象在各个存储节点之间迁移。在每个节点上，移动代理对象将处理数据并移动到下一个存储节点，在该节点上数据可用于处理。主机上的主函数应了解数据的各种位置，以便移动代理可以使用该数据并在分布式存储节点上移动以处理数据。要部署这种软件栈，需要有一个能够管理端到端执行的应用程序编程接口。建议的 API 模块集如下：(1) `mRPC`：用于访问管理主 RPC 库的控制器并提供主 API。这将在安装在主机以及存储节点上的 `java virtual machine` 上运行；(2) `Controller`：它管理 RPC 库和应用程序的所有实例。它促进主机与存储之间的会话。它还将有助于绑定和解除绑定端口/网络以允许主机与存储节点之间的连接；(3) `Sessions`：这些实际上将帮助应用程序/模块在主机和存储之间发送和接收对象。该方法具有一些性能优势，这些优势已在以下 section. 中讨论。

##### 8.5.2 预期系统的优势

所提出的系统与传统系统进行了评估，性能测量参数包括速度、所需带宽和安全性等。在传统系统中，计算所需作为输入的整个数据集从存储系统传输到主机单元，因此消耗了异常高的网络带宽。随着传输数据所需的时间增加，在可能的情况下会导致响应时间延迟。这意味着系统响应时间的增加将直接增加单元运行所需的网络带宽，反之亦然。在预期系统中，我们将在存储单元内部或附近传输经过适度过滤的数据，因此将减少数据的移动以及所需的带宽。系统只需将某些过滤后的数据传输到处理或主机系统以便进一步处理。当使用多个 `SSD` 作为存储单元或节点时，所提出的系统可能表现更好。可以开发负载平衡模块以在多个存储节点之间平衡工作负载。

另一个性能特征是系统可靠性。当数据从一个站点传输到另一个站点（物理或逻辑）时，数据的暴露会增加。正如先前所认为的那样，在投影系统中，需要移动的数据量会更少，因此系统会变得更安全。

#### 8.6 存储内处理的进一步研究路线图

下面提到了 `NDP` 研究领域几种潜在的研究方式：

* **数据的安全性和完整性**

  为驻留在存储单元上的程序生成受保护的环境以照顾数据的完整性并确保在程序行为不当的情况下获得预期结果是非常重要的。当谈到存储内处理时，在多级处理器上下文切换时，例如数据、硬件和操作系统，需要额外的安全措施。存储位置（可能是数据中心、云服务器等）必须具备的基本条件是数据安全，并且除了数据之外，还必须考虑数据的传输网络的安全性。数据中心必须提供数据的完整性和身份验证。由于网络攻击如拒绝服务造成的网络阻塞，网络安全也是另一个问题。

* **存储设备（无处不在的设备）智能**

  机器智能在 `AI` 形式上已在一定程度上实现。但在 `NDP` 假设中，我们希望智能也能在存储节点上实现。与当前范式相反，其中常见的 `NDP` 范式由一个或多个存储节点和一个管理它们的处理节点构建，在不久的将来，有必要扩展现有框架，使所有存储单元中的任何一个都表现得像主节点一样，其余存储节点表现为主节点相应的从节点。在预期系统中，主节点必须根据分配给存储节点的工作负载而变化，以避免系统的单点故障并在系统单元之间平衡工作负载。

* **分布式数据**

  由于数据的全球数字化以及存储此类数字化数据所需的空间需求的增加，分配大量数据的情况将继续发生。由于我们的计算领域正朝着数据密集型应用的方向发展，数据数字化的需求也在增加。与此同时，随着数字化数据的数量增加，将其存储在地理上分散的数据中心中的可能性也在增加。处理驻留在地理上分布位置的数据也是存储内处理的一个问题。

## 8.7 结论和未来范围

进化可以被称为优化方法之一。`EC` 可以源于环境中的成长或进化假设。在进化时代，计算使用一些生物概念来构建和提出编程和硬件系统。`EP` 最初被设想为产生机器智能的一种做法。它极大地影响了类似 `ML`、数据科学的未来领域。对于熟悉的活动，从平台预测并采取适当方法，观察到了智能。为了输入基于机器智能的应用程序，需要大量数据，并且系统应通过实现最低延迟来工作。然而，在传统的数据存储以及处理方法中，数据在移动期间增加了响应时间段，并且对网络传输能力（带宽）需求产生了巨大影响。为了克服这些问题，出现了原位处理的情况，这对处理速度、延迟以及网络带宽具有重要影响。第一批系统仅限于内存中处理，其中数据在主机处理单元的内存中执行计算。然而在最近的数据中心系统中，极其快速的二级存储驱动可能是执行处理的完美选择。

在当前情况下，许多重要应用程序部署在中央服务器单元上，并且执行任务所需的数据可能驻留在各种数据中心。在此时，此时代计算能力的必要性是构建可能系统，该系统能够实现具有大量分散数据的原位计算的要求。

在未来，我们可以考虑安全约束来开发系统。因为在存储内处理中，我们不是在网络中移动整个敏感数据，而是将代码或代码块从主机移动到存储（即通过网络）。为了提供数据免受通过网络移动的恶意代码的侵害，我们可以使用沙箱或区块链的概念。我们还可以为多个存储设备开发智能和动态调度。

## References

# 参考文献

Acharya A., Uysal M., et. al.; Active Disks: Programming Model, Algorithms and Evaluation; Proceedings of the eighth international conference on Architectural support for programming languages and operating systems; San Jose, California, USA — October 02–07, 1998; 81–91. a, b

Achmadi D., Suryanto Y., and Ramli K.; On Developing Information Security Management System (ISMS) Framework for ISO 27001-based Data Center; IWBIS 2018; pp. 149–157. →

Awan A.J., Ayguade E., et.al. Identifying the potential of Near Data Processing for Apache Spark; Proceeding MEMSYS ‘17 Proceedings of the International Symposium on Memory Systems; 2017; 60–67. a, b, c

Boncheol G., Yoon A.S., et. al.; Biscuit: A Framework for Near-Data Processing of Big Data Workloads; 2016 ACM/IEEE 43rd Annual International Symposium on Computer Architecture (ISCA); Seoul, South Korea; 18–22 June 2016; IEEE. a, b, c

Carlos A. and Silva S.; Multi objective Optimization; MIT Portugal.

Cheng J. and Sun X. Using Electronic Technology and Computational Intelligence to Predict Properties of Dangerous Hydrocarbon. Advances in Mechanical and Electronic Engineering, LNEE 177, Springer-Verlag Berlin Heidelberg, (2012), 621–626. →

Chiong R. and Beng O.K.; A Comparison between Genetic Algorithms and Evolutionary Programming based on Cutting Stock Problem; Engineering Letters; 2014.

Choe H., Lee S et. al. Near-Data Processing for Differentiable Machine Learning Models. Cornell University, (2017), 1–12. a, b

Das P., Lakhotia S., et.al.; Towards Near Data Processing of Convolutional Neural Networks; 2018 31st International Conference on VLSI Design and 2018 17th International Conference on Embedded Systems (VLSID); Pune, India; 6–10 Jan. 2018; IEEE. a, b

Deb K. Multi-ObjectiveOptimization. Multi-Objective Optimization using EvolutionaryAlgorithms, John Wiley & Sons, Inc, (2001). →

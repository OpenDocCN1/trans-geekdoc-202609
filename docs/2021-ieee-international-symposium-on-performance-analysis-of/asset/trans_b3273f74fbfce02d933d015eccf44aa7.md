

## TPUPoint: 针对云计算中硬件加速机器学习行为的自动特征分析

Abenezer Wudenhe 和 Hung-Wei Tseng
加州大学河滨分校
{awude001, htseng}@ucr.edu

## 摘要

随着数据中心中机器学习（ML）工作负载占比的迅速增加，云服务提供商开始引入张量处理单元（TPU）等加速器，以提高应用程序的能效比。然而，如果不优化应用程序参数，用户可能会低效利用加速器，最终浪费能源和金钱。本文提出了 TPUPoint，以促进在基于 TPU 的云平台上开发高效应用程序。TPUPoint 自动将重复模式分类为阶段，并识别每个阶段中最具时间关键性的操作。此外，TPUPoint 可以将阶段与检查点关联，以允许在应用程序中快进，从而显著减少优化应用程序所花费的时间和金钱。通过在广泛的代表性 ML 工作负载上运行 TPUPoint，我们发现计算不再是最耗时的操作；相反，交换和重新对齐数据的 `infeed` 和 `reshape` 操作变得最为重要。TPUPoint 的优势大大提高了发现最优参数的潜力，以便快速平衡向系统输入数据、重新格式化数据和计算结果的复杂工作负载流水线。在本文中，我们展示了如何使用 TPUPoint 来表征一组流行的 ML 工作负载。我们证明，NN 模型的迭代特性意味着所有 ML 工作负载都表现出可通过极少数重要阶段轻松表征的重复行为。TPUPoint 识别了耗时的算子，例如 `infeed`、`outfeed` 和 `reshape`，这些算子在几乎所有 NN 模型中都很常用，且与计算没有直接关系；如果这些间接算子不能足够快地准备数据集或交换出数据集，就会阻塞计算的进展。

## I. 引言

机器学习（ML）的兴起为为现代云基础设施应用设计高效 ML 系统创造了强劲需求 [1]，[2]，[3]，[4]，[5]，[6]，[7]，[8]，[9]，[10]。由于常规通用处理器和图形处理单元（GPU）针对标量或向量操作进行了优化，依赖它们的现代计算机架构在执行 ML 任务时会浪费能源。因此，依赖基于矩阵的神经网络（NN）的更高效 ML 加速器在数据中心中越来越普及。Google 的张量处理单元（TPU）每瓦性能比常规 GPU 高出 70×，是迄今最具代表性的案例 [11]。

由于异构架构组件和平台的性能特性各不相同，创建统一优化的 ML 程序是不现实的。一个更可行的方法是自动化优化过程本身。TPUPoint 框架通过 TPUPoint-Optimizer 实现此目标；TPUPoint-Optimizer 在 Cloud TPU 平台上自动且动态地重写代码，以减少程序员的工作量。我们的结果表明，使用 TPUPoint-Optimizer 动态确定的最优参数允许编写合理的 TensorFlow 程序达到与通过详尽程序员优化所达到的性能至少相同的水平。

本文提出了 TPUPoint，这是一个开源工具链，用于表征在 Google Cloud TPUs 上运行的应用程序的行为并优化其性能。TPUPoint 的分析器会自动将 TPU 应用程序的重复模式分类为阶段，并识别每个阶段中最具时间关键性的操作，以指导优化。TPUPoint 还可以将每个阶段与检查点关联，以便在目标阶段之前立即重启应用程序，并且 TPUPoint 为用户提供对 TPUPoint-Optimizer 等自动化工具的访问权限，以检查不同配置下的性能变化。

通过引入 TPUPoint，本文做出了四项关键贡献；（1）它提出了 TPUPoint，以加速新兴 ML 加速器基础云架构中 ML 应用程序的开发和优化，（2）它使用广泛的 ML 应用程序验证了 TPUPoint 的功能，（3）它识别了 ML 应用程序的常见瓶颈，（4）它详细介绍了一种发现 ML 应用程序最优参数的系统方法。

本文的其余部分组织如下：第 II 节介绍了 TPU 和基于 TPU 的云服务器的架构。第 III 节介绍了 TPUPoint 的设计。第 IV 节描述了 TPUPoint-Analyzer 的实现。第 V 节介绍了我们的实验平台。第 VI 节回顾了从 TPUPoint-Analyzer 获得的见解。第 VII 节展示了 TPUPoint-Optimizer 的结果。第 VIII 节为相关工作提供了背景摘要，第 IX 节提供了结束评论。

## II. TPU

Google 已在其数据中心广泛部署 TPU，并通过 Google Cloud 服务将 TPU 开放给用户应用程序。本节简要描述了 Cloud TPU 的功能和接口。

1 你可以在 [https://github.com/escalab/TPUPoint] 处找到 TPUPoint

### A. Cloud TPUs

Google 提供三种不同的 Cloud TPU。Google 内部使用第一代 TPU 用于搜索和推理，但通过 Google Cloud Platform 和 TensorFlow Research Cloud (TFRC) 计划 [12] 提供第二代和第三代 TPU（分别为 TPUv2 和 TPUv3）。TPUv2 芯片包含两个矩阵单元（MXU），每个 MXU 关联 8 GiB 高带宽内存（HBM），为 200–250 W TDP 提供合计 45 TFLOPS 的理论计算吞吐量。Google 通常将四个 TPUv2 组合在单个板上 [13]。TPUv3 包含的 MXU 数量是 TPUv2 的两倍，HBM 也是两倍。Google 未披露关于 TPUv3 架构的许多细节。尽管如此，性能规格说明（包括每颗芯片 90 TFLOPS 的容量和 32 GB HBM）表明，TPUv3 只是利用更先进的制程技术在同一芯片上放置四个 MXU，同时保持与 TPUv2 相同的功耗水平。

### B. Cloud TPU 硬件/软件接口

Google Cloud TPU 只能通过关联 TPU 实例的计算实例（Compute Engine）访问。除了 Compute Engine VM，Google Cloud TPU 还需要云存储（Storage Buckets）来存储执行过程中的训练数据和模型信息；Compute Engine 充当主机，TPU 充当协处理器，Storage Buckets 充当持久内存。这些组件构成了 Cloud TPU 架构。

TensorFlow [14] 是 Cloud TPU 方程中的另一重要部分。Google 开发了 TensorFlow 框架，用于在单机和异构/分布式系统上建模和执行 ML 算法。Google Cloud TPU 与 TensorFlow 现成集成。TensorFlow 大量使用 Google 的 Protocol Buffers（Protobuf）和 Google 的远程过程调用（gRPC）。Protobuf 和 gRPC 对 TensorFlow 框架都至关重要，以允许在 TensorFlow 中发生通信。TensorFlow 大量使用 Google 的 Protocol Buffers（Protobuf）和 Google 的远程过程调用（gRPC）。Protobuf 允许在多种编程语言之间进行方便的数据抽象，gRPC 允许 TensorFlow 在多个服务器和客户端之间共享数据，以便在多个设备上方便地执行。gRPC 服务器实现一个方法并等待客户端请求。gRPC 客户端使用一个称为 stub 的对象来在客户端和服务器之间提供通道。stub 处理 gRPC 客户端请求（使用 Protobuf）和服务器响应，并使用 RDMA 等高效格式在执行期间进行进程间通信。Protobuf 和 gRPC 对 TensorFlow 框架都至关重要。

TensorFlow 执行涉及客户端（用户）、主节点和一个或多个工作进程。客户端与主节点交互，主节点协调工作进程。主节点是

![](img/a2afc74fc22d678e24674964f5d46bc8_1_0.png)

Fig. 1. TPUPoint 系统架构

负责处理图节点的设备放置，并将图分区为由工作进程执行的子图。除了管理整个计算图之外，主节点还应用诸如常量折叠之类的优化。工作进程处理来自主节点的请求，执行内核操作，并管理内核之间的通信。

尽管 Cloud TPU 的实现并未完全向公众开放，但已注册的 API 调用和可服务请求仍然可用；名为 CLOUD-TPU-PROFILER 的命令行工具可用于生成客户端到主节点的 gRPC 调用，以请求为小迭代生成 Cloud TPU 配置文件。然而，CLOUD-TPU-PROFILER 的实用性有限，因为它无法集成到训练代码中，只允许在执行后获得洞察，并且只在有限的时间范围内运行（因此无法对整个程序执行进行性能分析。）

## III. TPUPOINT-PROFILER: TPUPOINT 的核心

TPUPoint 通过 TPUPoint-Profiler 模块提供一组工具。TPUPoint-Profiler 测量 Cloud TPU 性能并启用 TPUPoint 工具链的另外两个元素：（1）TPUPoint-Analyzer（第 IV 节），一种执行后的离线分析工具，用于识别最重要的应用程序阶段和系统组件利用不足的原因，（2）TPUPoint-Optimizer（第 VIII 节），一种在线自动工作负载优化工具，可动态调整和重写在 Cloud TPU 平台上运行的代码。本节介绍了 TPUPoint 设计和编程接口。

### A. TPUPoint-Profiler 设计

完整的 TPUPoint 工具链由一组扩展 TensorFlow 框架（目前 Cloud TPU 唯一的编程接口）组成。图 1 显示了核心 TPUPoint-Profiler 的交互，它驱动 TPUPoint-Analyzer 和 TPUPoint-Optimizer 与 TensorFlow 应用程序协同工作。

TPUPoint 在初始化 TPUPoint-Profiler 时创建一个单独的性能分析线程。创建后，TPUPoint-Profiler 线程会定期向关联的 Cloud TPU 发送性能分析请求，与主 TensorFlow 线程独立进行，允许 TPU 训练在性能分析进行时不受中断。当 Cloud TPU 将响应发送回性能分析线程时，TPUPoint-Profiler 生成一个性能分析记录



### Segment：GPU I/O 拓扑与轨道交换机 Fabric 配置文件

**GPU I/O 拓扑**：`Segment` 包含 GPU 主机和轨道交换机。`Pod` 使用 `Spine` 交换机聚合多个 `Segment`。在 `NCCL` 构建的拓扑中，跨轨主机间流量首先复制到本地 GPU 内存（位于目标轨道），然后通过 GPU NIC 经正确的轨道交换机发送到远程 GPU 的情况下，可能不需要带有 `Spine` 交换机的 `Pod` 架构。第三个领域是多 Pod，它使用 `Super Spine` 交换机连接多个 `Pod`，从而实现大规模的 AI Fabric 部署。图 13-10 还描绘了跨 AI Fabric 后端网络共享全局设置和属性。

**轨道交换机 Fabric 配置文件**：这种设计类似于可扩展 AI 集群中使用的双轨概念，但 NVIDIA 的 `SU` 方案要求每轨配备两个独立的物理交换机，从而提供了完全的物理隔离。每交换机双轨在资本支出（CapEx）和运营支出（OpEx）之间取得了平衡：它比单轨模型所需的交换机更少，且与多轨模型相比降低了操作复杂性。对于必须平衡某些容错能力和成本控制的中等规模环境，这通常是一个很好的选择。

为了解决这个问题，可以构建一种部分连接的架构，其中每个叶节点（leaf）连接到特定的脊网节点（spine）子集，而每个脊网节点为一组叶节点服务。这打破了发生哈希极化（hash polarization）所需的对称性。即使所有叶节点交换产生相同的哈希结果，下一跳也不会对每个节点都是相同的——因为该脊网节点可能无法被所有叶节点访问。这种故意的拓扑不对称确保了无论哈希结果如何，流量都能分布在多个脊网交换上。

这种结构化的布线方法通常依赖于确定性设计模式，可以高效扩展，同时减少由哈希极化引起的瓶颈风险。结果是改进了负载均衡，而无需仅仅依赖哈希调优或自适应转发机制。

## 参考文献

- [1] NVIDIA DGX SuperPOD: Scalable Infrastructure for AI Leadership Reference Architecture, October 2021
- [2] Kun Qian – Alibaba Cloud, et al., “Alibaba HPN: A Data Center Network for Large Language Model Training”. ACM SIGCOMM, August 4-8, 2024, Sydney, NSW, Australia
- [3] Cisco Validated Design for Data Center Networking Blueprint for AI/ML Applications. March 29, 2024. [https://www.cisco.com/c/en/us/td/docs/dcn/whitepapers/cisco-data-center-networking-blueprint-for-ai-ml-applications.html]
- [4] Aninda Chatterjee, Vivek – Juniper Networks, Designing Data Centers for AI Clusters [https://www.juniper.net/documentation/us/en/software/nce/ai-clusters-data-center-design/ai-clusters-data-center-design.pdf]
- [5] Arista, “AI Networking”. [https://www.arista.com/assets/data/pdf/Whitepapers/AI-Network-WP.pdf]

# 第 14 章：GPU 集群通信模型

本章的重点是描述启动训练任务所需的，并概述任务期间发生的情况。从这个意义上，这是我们“AI 数据中心深度学习之旅”的一个结束章节。图 14-1 显示了一个高层且简化的架构，以及两个 GPU 主机的主要构建模块，每个主机带有四个 GPU 及其外部网络连接。两个主机都属于同一个训练集群。作为我们示例中的前提，两个主机上都安装了以下软件包：

带有支持 `CUDA` 和 `NCCL` 的 PyTorch：PyTorch 是一个深度学习框架，管理整个训练工作流，包括数据加载、模型定义、并行执行和梯度同步。它定义了神经网络的结构，例如层数、每层的神经元数量、激活函数和梯度同步。`CUDA`（统一设备架构）：`CUDA` 是一个计算平台。`NCCL`（NVIDIA 集合通信库）：`NCCL` 为多 GPU 和多节点系统中的高性能集合通信设计。

## 用于训练的 NCCL

在多个节点上的 GPU 高效通信之前，它们必须首先对共享标识达成一致。

### 向主节点打开 TCP 套接字

如图 14-2 所示使用 `torchrun` 启动训练任务时，rank 0 的进程被分配了主角色。PyTorch 在该 GPU 的 `192.168.10.10:12345` 开启 TCP 监听器，使用 `--nnodes=2` 值指定集群中有两个节点，并使用 `--nproc_per_node=4` 表示每个节点上运行着四个进程（每个 GPU 一个）。拥有这些信息后，主 rank 期望接收 7 个连接请求（来自 rank 1 到 7）。

所有其他 rank 都启动了与主进程打开 TCP 套接字的三次握手。主机 B 上的 rank 4-7 使用 `--master_addr=192.168.10.101` 作为目标 IP 地址，而本地 rank 1-3 使用回环 IP 地址 `127.0.0.1`。所有 rank 使用 `--master_port=12345` 作为目标 TCP 端口。此连接阶段实现了会合（rendezvous），期间主节点分发 NCCL 唯一 ID，以便 GPU 形成集合操作的通信拓扑。

全局 rank 的计算方式如下：

- 机 A：GPU 0: `0 * 4 + 0 = 0`
- 主机 A：GPU 1: `0 * 4 + 1 = 1`
- 主机 A：GPU 2: `0 * 4 + 2 = 2`
- 主机 A：GPU 3: `0 * 4 + 3 = 3`
- 主机 B：GPU 0: `1 * 4 + 0 = 4`
- 主机 B：GPU 1: `1 * 4 + 1 = 5`
- 主机 B：GPU 2: `1 * 4 + 2 = 6`
- 主机 B：GPU 3: `1 * 4 + 3 = 7`

由于主机 A 上的 GPU 0 拥有全局 rank 0，它成为了主 rank。NCCL 会合过程与三层组播网络中的动态汇聚点（RP）之间存在松散但有用的类比。在两种情况下，会合都充当了协调机制的作用。

# 通过已建立的 TCP Socket 分发 NCCL Unique ID

当所有节点（ranks）都与主进程（节点 ID 0）建立 TCP 连接后，下一步是分发 NCCL Unique ID。主进程生成此标识符，并通过已建立的 TCP 连接将其发送所有其他节点（1 到 7）。

这些连接通常运行在前端或管理网络上，取决于集群配置。图 14-3 展示了从主进程角度看到的连接状态。

NCCL Unique ID 作为作业的命名空间标识符，确保只有同一个训练作业的进程才能参与同一个通信组。这在多个分布式作业可能在同一组节点并发运行的环境中尤为重要。唯一 ID 隔离了不同的作业，防止了不相关进程之间的交叉干扰。随后，所有节点使用此唯一 ID 初始化本地的 NCCL 通信器，确保它们加入同一个通信组。分发阶段至关重要：NCCL Unique ID 充当了引导机制，允许所有 GPU 进程加入同一个通信组，并参与 all-reduce 和 broadcast 等集合操作。

![](img/main-142.jpg)

图 14-3：通过 TCP Socket 重新分发 NCCL Unique ID。

![](img/main-143.jpg) ![](img/main-144.jpg)

# NCCL Broadcast 集合操作与模型参数同步

此时，每个进程已经拥有模型的本地副本，所有 GPU 都已准备好开始同步训练。第一步是确保每个 GPU 启动时具有相同的模型参数。NCCL 使用所选的通信拓扑自动处理。

在主进程（节点 0，运行在 Host A 的 GPU 0 上）通过 TCP Socket 与所有其他进程共享 NCCL Unique ID 后，NCCL 库会构建树形拓扑。该拓扑用于通过 `Broadcast` 集合操作向所有其他 GPU 发送模型参数。图 14-4 展示了运行在 Host A GPU 0 上的主进程如何将其模型参数分给所有其他进程。全局节点 ID 为 1-3 的 GPU 与主进程在同一主机上，因此 NCCL 通过高速 NVLink 进行直接内存拷贝。这些传输在不涉及 CPU 或操作系统的情况下完成，且不需要队列对（Queue Pairs），使得节点内通信极其快速且高效。

如果 GPU 位于不同的主机上，NCCL 会建立队列对（QPs），在主进程与远程进程之间创建快速、直接的数据路径。这些连接使用后端网络，在我们的示例中，这是一个路由的三层 Clos 架构（为了简单起见，此处排除了网络布局）。

![](img/main-145.jpg)

图 14-4：主节点 0 分发模型参数。

# 使用 AllReduce 集合进行梯度同步

同步模型参数后，集群中所有 GPU 同时开始第一次迭代的前向传播。在前向传播过程中，GPU 特有的小批量数据（mini-batches）通过模型的所有层，在每层执行矩阵乘法后进行激活函数操作进行处理。计算出模型输出 `y` 后，每个 GPU 开始反向传播。假设最后一层有 1024 个参数，每个 GPU 计算这 1024 个参数的梯度。这些梯度存储在一个名为 `bucket` 的预留内存区域中。

接下来，每个 GPU 将其 bucket 分为四块，每块包含 256 个梯度（因为 1024 个参数 / 4 个 GPU = 256 个梯度）。此时，每个 GPU 拥有四个标记为 `A–D` 的块，每块有 256 个梯度。在单向环形拓扑中使用 `AllReduce` 集合操作时，该操作实现为 `ReduceScatter` 后接 `AllGather`。

在我们的示例中（如图 14-5 所示），有两个节点（Host A 和 Host B），每个节点有四个 GPU。每个 GPU 都计算了 1024 个梯度，并将它们组织在 `VRAM` 中的四块（`A–D`）。在此示例中，GPU 0（全局节点 0）负责平均块 `A`，节点 1（蓝色 GPU 1）负责块 `B`，节点 2（绿色 GPU 0）负责块 `C`，节点 3（黄色 GPU 1）负责块 `D`。节点内 GPU 连接使用高速 NVLink，而节点间连接使用 RoCEv2。

![](img/main-146.jpg)

图 14-5：环形拓扑中带有 ReduceScatter 和 AllReduce 操作的 AllReduce。

## ReduceScatter：第一次迭代

在图 14-6 中，图 14-5 中的环形拓扑仍然在使用，但 GPU 采用线性排列，以便更直观地可视化 `AllReduce` 数据流。在 `AllReduce` 操作的 `ReduceScatter` 阶段，每个节点将其负责的块发送给环中的下一个节点：

- `Rank 0` 将 `A0` 发送给 `Rank 1`
- `Rank 1` 将 `B1` 发送给 `Rank 2`
- `Rank 2` 将 `C2` 发送给 `Rank 3`
- `Rank 3` 将 `D3` 发送给 `Rank 0`

这些块中的每一个包含参数空间特定部分的梯度，随着数据绕环形循环，每个节点负责在所有 GPU 上对该部分进行归约（即求和）。

![](img/main-147.jpg) ![](main-148.jpg) ![](main-149.png) ![](main-150.jpg)

图 14-6：ReduceScatter：第一次迭代。

图 14-7 显示了 `ReduceScatter` 阶段第一次发送迭代后的梯度同步状态。此时，每个 GPU 都已将其分配的块发送给环形拓扑中的下一个 GPU，并从邻居处接收了一个块：

- `Rank 0` 从 `Rank 3` 接收了 `D3`
- `Rank 1` 从 `Rank 0` 接收了 `A0`
- `Rank 2` 从 `Rank 1` 接收了 `B1`
- `Rank 3` 从 `Rank 2` 接收了 `C2`

在第一次发送（`ReduceScatter` 阶段的第 1 次迭代）之后，每个 GPU 在本地内存中仍持有三个原始块加一个部分归约的块。每个 GPU 将接收到的块加到其本地相同块的版本中。例如，`rank 0` 将 `D3` 加到 `D0`（`chunk D = D0 + D3`）。这只是第一次归约。为了完成其分配块的完整归约，每个 GPU 必须在接下来的三次迭代中接收并求加其余 GPU 对应的块。当 `ReduceScatter` 阶段结束时（在 4 GPU 环中迭代三次后），每个 GPU 正好持有一个完全归约的块，尽管不一定是它原始的那一个。

![](img/main-151.jpg)

图 14-7：ReduceScatter：第一次迭代后的状态。

## ReduceScatter：第二次迭代

图 14-8 显示了 `ReduceScatter` 阶段的第二次迭代：

- `Rank 0` 将部分归约的块 `D`（`D3 + D0`）发送给 `Rank 1`
- `Rank 1` 将部分归约的块 `A`（`A0 + A1`）发送给 `Rank 2`
- `Rank 2` 将部分归约的块 `B`（`B1 + B2`）发送给 `Rank 3`
- `Rank 3` 将部分归约的块 `C`（`C2 + C3`）发送给 `Rank 0`

![](img/main-152.jpg) ![](main-153.jpg) ![](main-154.jpg) ![](main-155.jpg) ![](main-156.jpg)

图 14-8：ReduceScatter：第二次迭代。

![](img/main-157.jpg)

在第二次 `ReduceScatter` 迭代后，每个节点现在持有：

- 一个已归约两次的块（本地块 + 两个远程块）
- 两个尚未参与任何通信的原始块
- 一个在本次迭代中发送出的块

以下是每个节点的具体状态：

**Rank 0:**

- 持有部分归约块 `C = C2 + C3 + C0`（刚从 `Rank 3` 接收并加到本地 `C0`）
- 仍持有原始块 `A0` 和 `B0`
- 发出了块 `D = D3 + D0`

**Rank 1:**

- 持有部分归约块 `D = D3 + D0 + D1`
- 仍持有原始块 `B1` 和 `C1`
- 发出了块 `A = A0 + A1`

**Rank 2:**

- 持有部分归约块 `A = A0 + A1 + A2`
- 仍持有原始块 `C2` 和 `D2`
- 发出了块 `B = B1 + B2`

**Rank 3:**

- 持有部分归约块 `B = B1 + B2 + B3`
- 仍持有原始块 `A3` 和 `D3`
- 发送块 `C = C2 + C3`

![](img/main-158.jpg) ![](main-159.jpg) ![](main-160.jpg) ![](main-161.jpg) ![](main-162.jpg) ![](main-163.jpg) ![](main-164.jpg) ![](main-165.png) ![](main-166.png) ![](main-167.jpg)

图 14-9: ReduceScatter：第二次迭代后的块（Chunks）。

### ReduceScatter：第三次迭代

图 14-10 显示了 `ReduceScatter` 阶段的第三次迭代：

- `Rank 0` 将部分平均的块 `C`（`Sum of C2 + C3+ C0`）发送到 `Rank 1`。
- `Rank 1` 将部分平均的块 `D`（`Sum of D3 + D0 + D1`）发送到 `Rank 2`。
- `Rank 2` 将部分平均的块 `A`（`Sum of A0 + A1 + A2`）发送到 `Rank 3`。
- `Rank 3` 将部分平均的块 `B`（`Sum of B1 + B2 + B3`）发送到 `Rank 0`。

![](img/main-168.jpg) ![](main-169.jpg)

图 14-10: ReduceScatter：第三次迭代。

在第三次 `ReduceScatter` 迭代之后，`ReduceScatter` 阶段完成。每个 rank 现在持有一个完全还原的块，包含了所有四个 GPU 的贡献。然而，这些完全还原的块并不位于它们原始的所有者 rank 上。每个 rank 接收一个最终块，并通过将其与本地副本求和来完成还原。此时：

- `Rank 0` 持有完全还原的块 `B = B1 + B2 + B3 + B0`
- `Rank 1` 持有完全还原的块 `C = C2 + C3 + C0 + C1`
- `Rank 2` 持有完全还原的块 `D = D3 + D0 + D1 + D2`
- `Rank 3` 持有完全还原的块 `A = A0 + A1 + A2 + A3`

![](img/main-170.jpg) ![](main-171.png) ![](main-172.png) ![](main-173.jpg)

图 14-11: ReduceScatter：第三次迭代后的块（Chunks）。

`ReduceScatter` 操作是 `Ring AllReduce` 过程的第一步，负责在分布式训练设置中聚合所有 GPU 的梯度数据。它的目标是计算每个梯度的和（或平均值）。在 `ReduceScatter` 阶段结束时：

- 每个 GPU 持有一个完全还原的块，包含了所有四个 GPU 的贡献。

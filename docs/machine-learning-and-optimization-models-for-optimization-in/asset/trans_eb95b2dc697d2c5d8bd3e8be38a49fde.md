
# 8.6 性能评估

为了评估 `BPGA` 虚拟机放置模型带来的性能提升，我们将其与三种现有的参考算法进行了比较：`PABFD`、`GA` 和 `ACO`。这些参考算法简要描述如下：

## 表 8.2 服务器配置

| **服务器** | **CPU 型号** | **内存 (GB)** | **频率 (MHz)** | **核心数** |
| :--- | :--- | :--- | :--- | :--- |
| IBM Server x3250 | Intel Xeon X3480 | 8 | 2,933 | 4 |
| IBM Server x3250 | Intel Xeon X3470 | 16 | 3,067 | 12 |
| Acer AT150 F1 | Intel Xeon 5670 | 12 | 2,933 | 12 |
| Acer AR320 F1 | Intel Xeon 3470 | 8 | 2,933 | 4 |
| HP ProLiant G4 | Intel Xeon 3040 | 4 | 1,860 | 2 |
| HP ProLiant G4 | Intel Xeon 3075 | 8 | 2,933 | 2 |

## 表 8.3 虚拟机实例 [45]

| **虚拟机类型** | **CPU (MIPS)** | **内存 (GB)** |
| :--- | :--- | :--- |
| 特大型 (高内存) | 3,000 | 6 |
| 中型 (高 CPU) | 2,500 | 0.85 |
| 特大型 | 2,000 | 3.75 |
| 小型 | 1,000 | 1.7 |
| 微型 | 500 | 0.613 |

### 8.6.1 实验设置

我们选择了 `CloudSim` 仿真平台作为实验环境，因为在真实的云环境中进行实验非常困难。数据中心环境由 800 台具有 6 种不同配置的服务器组成。表 8.2 提供了这些服务器的配置，表 8.3 展示了我们在此使用的五种不同的虚拟机实例。

此外，对于仿真环境，我们采用了来自 `CoMoN Project` 十天数据的真实工作负载 [46]。

### 8.6.2 仿真结果与比较

在本节中，我们讨论了由 `BPGA` 模型放置后的能耗、迁移次数和使用的主机数量。我们使用 PlanetLab 数据集（如图 8.5–8.8 所示）将结果与 `GA`、`ACO` 和 `PABFD` 进行了比较。图 8.5 描绘了在每次运行中虚拟机增加时，`BPGA` 使用的主机数量较少。

图 8.6 显示了与 `PABFD`、`GA` 和 `ACO` 相比，`BPGA` 进行的迁移次数较少。正如图 8.7 所示，`BPGA` 找到了具有最小能耗的虚拟机-物理机最佳匹配。

## 8.7 结论与未来展望

绿色计算是当前非常热门的研究领域。数据中心中对计算资源、应用和存储不断增长的需求是碳排放的主要来源。因此，有效的能源管理对数据中心非常有帮助。如今，大多数研究人员正在实施生物启发式方法来应对这一能源危机。因此，我们也结合 `BPNN` 使用多目标优化，以实现虚拟机在数据中心服务器上的最优放置。

我们提出了一种 `BPGA` 和能量感知模型用于虚拟机放置，以最小化主机使用量。该模型采用分治法寻求该问题的最优解。该问题分两遍求解，第一遍使用 `NSGA`，第二遍使用 `BPNN` 进行最合适的虚拟机放置。

在本工作中，我们使用 `CloudSim` 对所提模型进行了仿真；未来我们希望在提供真实基础设施的 `CloudStack` 上开展工作。此外，考虑到数据中心的不同网络拓扑，其网络结构也是几个可以做出贡献的研究方向。

## 参考文献

[1] Md Hasanul Ferdaus, Manzur Murshed, “Energy-aware virtual machine consolidation in IaaS cloud computing”, *Cloud Computing*, pp. 179–208, 2014.

[2] Perspectives I, “Using a total cost of ownership (TCO) model for your data center”, 2013. URL: `http://www.datacenterknowledge.com/archives/2013/10/01/using-a-totalcost-of-ownership-tco-model-for-your-data-center/`, last accessed: 02-01-2014.

[3] Saurabh Kumar Garg, Srinivasa K. Gopalaiyengar, Rajkumar Buyya, “SLA-based resource provisioning for heterogeneous workloads in a virtualized cloud datacenter”, in Proceedings of 11th International Conference on Algorithms and Architectures for Parallel Processing, pp. 371–384, 2011.

[4] Nguyen QH, Nam T, Nguyen T, “Epobf: Energy efficient allocation of virtual machines in high performance computing cloud”, *Journal of Science and Technology*, Vol. 51(4B), pp. 173–182, 2013.

[5] Nakku K, Jungwook C, Euiseong S, “Energy-credit scheduler: An energy-aware virtual machine scheduler for cloud systems”, *Future Generation Computer System*, Vol. 32, pp. 128–137, 2014.

[6] Atefeh K, Saurabh K, Rajkumar B, “Energy and carbon-efficient placement of virtual machines in distributed cloud data centers”, in *Euro-par 2013 Parallel Processing. Lecture Notes in Computer Science*, Vol. 80(97), Springer, Berlin, pp. 317–328, 2013.

[7] Sheikh H, Tan H, Ahmad I, Ranka S, Bv P, “Energy- and performance-aware scheduling of tasks on parallel and distributed systems”, *ACM Journal of Emerging Technology in Computing Systems*, Vol. 8(4), pp. 1–37, 2012.

[8] George Kousiouris, Tommaso Cucinotta, Theodora Varvarigou, “The effects of scheduling, workload type and consolidation scenarios on virtual machine performance and their prediction through optimized artificial neural networks”, *Journal of Systems and Software*, Vol. 84, pp. 1270–1291, 2011.

[9] Haikun L, Hai J, Cheng X, Xiao L, “Performance and energy modeling for live migration of virtual machines”, *Cluster Computing*, Vol. 16(2), pp. 249–264, 2013.

[10] Zhang W, Song Y, Ruan L, “Resource management in internet-oriented data centers”, *Journal of Software*, Vol. 23(2), pp. 179–199, 2012.

[11] Hongjian Li, Goufeng Zhu, Chenghuan Cui, Hong Tang, Yusheng Dou, Chen He, “Energy-efficient migration and consolidation of virtual machines in data centers for cloud computing”, *Journal of Computing*, Vol. 98, pp. 303–317, 2016.

[12] Fabio Lopez Pires, Benjamin Baran, “Multi-objective virtual machine placement with service level agreement: A Memetic algorithm approach”, In Proceedings of 6th International Conference on Utility and Cloud Computing, pp. 203–210, 2013.

[13] Beloglazov A, Buyya R, “Optimal online deterministic algorithms and adaptive heuristics for energy and performance efficient dynamic consolidation of virtual machines in Cloud data centers”, *Concurrency Computation: Practice and Experience*, Vol. 24, pp. 1397–1420, 2012.

[14] Beloglazov A, Abawajy J, Buyya R, “Energy-aware resource allocation heuristics for efficient management of data centers for cloud computing”, *Future Generation Computing System*, Vol. 28, pp. 755–68, 2012.


# 参考文献

Krizhevsky, A., Sutskever, I., & Hinton, G. E. (2012). ImageNet classification with deep convolutional neural networks. *Advances in Neural Information Processing Systems*, 1097–1105.

Laptev, I., & Lindeberg, T. (2004). Local descriptors for spatio-temporal recognition. *International Workshop on Spatial Coherence for Visual Motion Analysis*, pp. 91-103. Academic Press.

LeCun, Y., & Bengio, Y. (1995). Convolutional networks for images, speech, and time series. *The Handbook of Brain Theory and Neural Networks*.

LeCun, Y., Bottou, L., Bengio, Y., & Haffner, P. (1998). Gradient-based learning applied to document recognition. *Proceedings of the IEEE*, 86(11), 2278–2324.

LeCun, Y., Huang, F. J., & Bottou, L. (2004). Learning methods for generic object recognition with invariance to pose and lighting. *Proceedings of the 2004 IEEE Computer Society Conference on Computer Vision and Pattern Recognition* (Vol. 2, pp. II-104). IEEE.

Liu, W., Anguelov, D., Erhan, D., Szegedy, C., Reed, S., Fu, C.-Y., & Berg, A. C. (2016). SSD: Single shot multibox detector. *ECCV*, 21–37.

Lu, J., Shen, J., Yan, W., & Bacic, B. (2017). An empirical study for human behavior analysis. *International Journal of Digital Crime and Forensics*, 9(3), 11–27. doi:10.4018/IJDCF.2017070102

Niebles, J. C., Wang, H., & Li, F. (2008). Unsupervised learning of human action categories using spatial-temporal words. *IJCV*, 299-318.

Petrushin, V. A. (2005). Mining rare and frequent events in multi-camera surveillance video using self-organizing maps. *ACM Conference on Knowledge Discovery in Data Mining*, pp. 794-800. doi:10.1145/1081870.1081975

Redmon, J., Divvala, S., Girshick, R., & Farhadi, A. (2016). You only look once: Unified, real-time object detection. *CVPR*, 2016, 779–788.

Redmon, J., & Farhadi, A. (2017). YOLO9000: Better, faster, stronger. *CVPR*, 2017, 7263–7271.

Ren, S., He, K., Girshick, R., & Sun, J. (2017). Faster R-CNN: Towards real-time object detection with region proposal networks. *IEEE Transactions on Pattern Analysis and Machine Intelligence*, 39(6), 1137–1149. doi:10.1109/TPAMI.2016.2577031

Rui, Y., & Anandan, P. (2000). Segmenting visual actions based on spatio-temporal motion patterns. *CVPR*, 2000, 111–118.

Sande, K., Uijlings, J., Gevers, T., & Smeulders, A. (2011). Segmentation as selective search for object recognition. *ICCV 2011*, pp. 1879-1886.

Szegedy, C., Toshev, A., & Erhan, D. (2013). Deep neural networks for object detection. In *Advances in Neural Information Processing Systems* (pp. 2553-2561).

Tran, D., Bourdev, L., Fergus, R., Torresani, L., & Paluri, M. (2015). Learning spatiotemporal features with 3D convolutional networks. *Proceedings of the IEEE International Conference on Computer Vision*, pp. 4489-4497.

# 第 10 章

*   Maria Rodriguez
    墨尔本大学，澳大利亚
*   Rajkumar Buyya
    墨尔本大学，澳大利亚

## 摘要

容器被组织广泛用于部署各种工作负载，例如 Web 服务、大数据和 IoT 应用。容器编排平台旨在管理大规模集群中容器化应用的部署。大多数此类平台针对固定规模的集群优化容器调度，并未启用集群自动伸缩功能，也不考虑公有云环境特有的特性。本章提出了一种具有三个目标的资源管理方法：1) 通过在现有资源上高效调度容器来优化其初始放置；2) 基于集群工作负载在运行时自动伸缩资源数量；3) 在运行时将应用整合到更少的 VM 中。该框架作为 `Kubernetes` 插件实现，并在澳大利亚云基础设施上评估了其效率。实验表明，通过动态管理集群规模和应用放置，可实现 58% 的成本降低。

## 引言

容器（如 `Docker` (`Docker`, n.d.) 和 `Linux Containers` (`LXC`) (`Bernstein`, 2014)）是独立且自包含的单元，将软件及其依赖项打包在一起。与虚拟机 (`VMs`) 类似，容器是一种虚拟化技术，允许多个用户和应用共享单个计算节点的资源。然而，`VMs` 在硬件层面虚拟化资源，而容器则在操作系统层面进行虚拟化。这使它们成为一种轻量级虚拟化方法，能够实现应用环境隔离、快速灵活的部署以及细粒度的资源共享。

组织越来越多地依赖容器化来部署源自现代应用的各种工作负载，例如 Web 服务、大数据和 IoT 应用。容器编排平台（如 `Kubernetes` (`Hightower et al.`, 2017)、`Docker Swarm` (`Naik`, 2016) 和 `Apache Mesos` (`Hindman et al.`, 2011)）负责在共享计算集群中高效编排此类应用。这些平台管理容器的生命周期以及集群资源的使用，因此其主要目标之一是（近乎）最优地将容器化应用放置在可用节点上。这一调度问题正是本章的重点。

随着应用被提交部署，编排系统必须尽快将它们调度到可用资源之一上。这必须在尝试最大化集群计算资源利用率的前提下完成，因为这很可能会降低组织的运营成本。这种放置还应考虑诸如可用机器容量、应用性能和服务质量 (`QoS`) 要求、容错能力和能耗等因素。尽管现有的容器编排平台在一定程度上解决了这些问题，但仍需进一步研究，以便在不同情况下和针对不同应用需求更好地优化资源使用。

在云环境中，容器和 `VMs` 可结合使用，为用户在部署、构建和管理应用方面提供极大的灵活性。在这种情况下，不仅容器的数量应伸缩以满足应用需求，可用计算资源的数量也应调整以充分托管所需容器。在任何给定时间点，云容器编排系统都应避免 `VMs` 资源利用不足，作为一种成本和能耗控制机制。它还应能动态向集群添加工作节点 `VMs`，以避免因资源过度利用导致应用性能下降。因此，自动伸缩 `VMs` 数量对于成功满足部署在公有云上的容器化应用的性能目标以及降低租赁所需基础设施的运营成本至关重要。这增加了上述容器放置和调度问题的复杂性。

现有的容器编排框架提供装箱算法以在固定规模的集群上调度容器，但未启用集群规模自动伸缩功能。相反，这一决策留给用户或平台层面的外部框架。此类场景的一个例子是使用 `Kubernetes` 进行容器放置，并使用亚马逊的自动伸缩机制管理集群节点。这种方法不仅可能不切实际，而且效率低下，因为外部实体对容器工作负载的信息有限。

主流编排系统未考虑的另一个优化方面与重新调度有关；特别是为了减少资源碎片和缩小集群规模而进行的重新调度。无论这些任务的初始放置有多好，随着工作负载的变化，资源利用率会随时间下降。重新调度那些能容忍组件关闭并重启的应用，将使编排系统能够整合和重新排列任务，从而在相同数量的节点上部署更多应用，或关闭某些节点以降低成本或节省能源。同样，如果向集群添加更多节点，能够将部分已部署应用重新调度到新节点上，从长远来看可能是有益的。

因此，本章的工作主张：一个能够做出所有资源管理决策（包括自动伸缩和重新调度）的以云为中心的容器编排框架，对于在云环境中成功优化资源使用至关重要。因此，这项工作的主要贡献是一个综合的容器资源管理框架，具有三个不同的目标。第一个目标是优化容器的初始放置，以使工作节点 `VMs` 的数量最小化，同时满足容器化应用的内存和 CPU 需求。第二个目标是基于当前集群工作负载自动伸缩工作节点 `VMs` 的数量。一方面，扩容将使当前资源需求得到满足，同时减少放置和启动容器所需的时间。另一方面，缩容将使应用得以重新定位，从而关闭利用率低的 `VMs` 以降低基础设施成本。最后，重新调度机制将通过在可能时将应用整合到更少的 `VMs` 中，进一步支持资源的高效利用，以避免不必要的扩容操作并鼓励缩容操作。

本章其余部分组织如下。第 2 节介绍现有的容器管理平台及其他相关调度算法。第 3 节讨论我们的编排框架所考虑的应用和资源模型。第 4 节讨论拟议系统的架构及其利用 `Kubernetes` 的实现。第 5 节讨论拟议的自动伸缩、重新调度和调度方法。第 6 节展示在澳大利亚国家云基础设施上对我们的框架和拟议算法的评估。最后，第 7 节总结本章，并确定和讨论新的研究方向。

## 相关工作

Uijlings, J., Sande, K., Gevers, T., & Smeulders, A. (2013). Selective search for object recognition. *International Journal of Computer Vision*, 104(2), 154-171.

Xiang, T., Gong, S. (2005) Video behavior profiling and abnormality detection without manual labelling. *Proceedings of the IEEE International Conference on Computer Vision*, pp. 1238-1245.

在研究和开源社区中，已经有大量尝试构建可靠且可扩展的集群容器管理平台（Rodriguez & Buyya, 2019）。这些系统负责管理通用应用程序的部署，这些应用通常打包在基于 `Docker` 或 `Linux cgroups` 的容器中。在本节中，我们将简要介绍容器编排领域中软件系统和资源管理算法的相关工作。

### 软件系统

**Kubernetes** (Hightower, Burns, & Beda, 2017) 是领先的开源容器管理平台，源自 Google 的内部 **Borg** 系统 (Verma et al., 2015)。Kubernetes 在虚拟化或物理集群中编排和管理异构容器化应用程序（如服务和批处理作业）的生命周期。它提供了一个默认调度器，根据用户定义的需求筛选可用集群资源，并基于单独定义的应用亲和性进行排序，将每个容器组（或 `pod`）分配给这些资源。Kubernetes 的详细评估可参见 (Medel, Rana, Bañares, & Arronategui, 2016)。

**Docker Swarm** (Naik, 2016) 是 `Docker` 容器的原生集群解决方案。它提供发现服务，并使用预定义的策略和过滤器将容器调度到主机上。默认情况下，它支持两种简单策略：i) 分散策略，倾向于在负载最低的主机上运行新容器；ii) 紧凑策略，倾向于在资源足够运行容器的负载最高的主机上运行。Docker Swarm 还采用过滤机制来识别合格资源；用户可以定义关于主机状态、健康检查结果和容器配置（如资源和文件亲和性以及对其他容器的依赖）的过滤器。

**Apache Mesos** (Hindman et al., 2011) 实现了各种应用程序之间的集群共享。与 Kubernetes 和 Swarm 不同，Mesos 可被视为运行在这些平台之上的元平台。它采用两阶段调度方法。在第一阶段，它划分集群资源，并通过资源提供分别向每个应用程序配置资源。一旦应用程序接受资源提供，它就可以继续使用自己的调度逻辑在获得的资源上调度其任务。之后，Mesos 实际上在相应主机上为应用程序启动任务。

**Apache Marathon** (Marathon, n.d.) 和 **Apache Aurora** (DelValle, Rattihalli, Beltre, Govindaraju, & Lewis, 2016) 是构建在 Mesos 之上的两个流行通用框架。Marathon 旨在编排长期运行的服务。因此，它专注于为应用程序提供容错和高可用性；Marathon 将确保已启动的应用程序即使在节点故障时也能继续运行。Aurora 最初由 Twitter 开发，是一个调度器，支持在集群中部署长期运行的服务、定时作业和临时作业。Aurora 专注于确保服务持续运行，因此，当发生机器故障时，作业会被智能地重新调度到健康的机器上。值得注意的是，就功能而言，Marathon 和 Aurora 是非常相似的产品。然而，两者存在一些差异。主要区别在于 Marathon 仅处理服务类作业。此外，设置和使用 Marathon 被认为比 Aurora 更简单；例如，Marathon 包含一个用户界面，用户可通过它直接调度任务。

**YARN** (Vavilapalli et al., 2013) 是一个旨在编排 Hadoop 任务的集群管理器，尽管它也支持 Giraph、Spark 和 Storm 等其他框架。运行在 YARN 之上的每个应用程序框架都根据自身情况协调各自的执行流程和优化。在 YARN 中，每个集群有一个资源管理器（`RM`），每个框架有一个应用程序主节点（`AM`）。`AM` 向 `RM` 请求资源，并根据接收到的资源生成物理计划。因此，YARN 的两级调度模型与 Mesos 相似，但不同之处在于应用程序向 YARN 请求所需资源，而不是由 YARN 主动提供资源。

尽管上述大多数系统已经成熟，但资源管理优化领域仍可进一步探索。这在云计算时代尤为真实，因为大多数现有框架假设资源集群是静态的，而忽略了云平台的许多固有特性。结果是，弹性、定价和服务异构性被忽视。用于碎片整理和自动扩缩容的重新调度是上述系统中缺失的另一项功能。本文旨在通过探索在管理集群资源时考虑自动扩缩容和重新调度的优势来弥补这些空白。

### 资源管理算法

本节讨论专注于基于容器调度算法的相关工作。Xu 等人 (Xu, Yu, & Pei, 2014) 为基于容器的云环境提出了一种资源调度方法，旨在减少请求响应时间并提高资源利用率，该方法利用稳定机器理论获得容器到主机的最优映射。(Zhang et al., 2016) 设计了一个基于容器的新型视频监控云平台，应用未来工作负载预测实现细粒度资源配置并确保服务质量。(Kaewkasi & Chuenmuneewong, 2017) 应用蚁群优化算法将容器分配给主机，旨在平衡资源使用。(Kehrer & Blochinger, 2018) 为 **Apache Mesos** 提出了一种两阶段部署方法，以实现对容器更灵活的管理。(Guerrero, Lera, & Juiz, 2018) 为 **Kubernetes** 平台提出了一种遗传算法，以优化容器分配和弹性管理。他们的算法可以提高系统性能并减少网络开销。与本章提出的工作相反，上述方法专注于容器的初始放置（即调度），并未考虑重新调度和自动扩缩容。

(Yin, Luo, J., & Luo, H., 2018) 利用容器构建了一个任务调度模型，并开发了一种任务调度算法以减少雾计算环境中的任务完成时间。他们还提出了一种重新调度方法来优化任务延迟。然而，结果仅在模拟环境中得到验证。

(Xu, Toosi,, & Buyya, 2018) 提出了一种基于容器和 Brownout（电压降低/功能降级）的方法，可以动态激活和停用可选容器，以在满足服务质量要求的前提下实现云资源的节能管理。该方法应用自动扩缩容来减少活跃主机数量，但未考虑容器的初始放置和重新调度。

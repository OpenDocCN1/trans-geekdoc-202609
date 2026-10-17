
## 自动扩缩容

### 空自动扩缩器

空自动扩缩器将直接忽略扩容和缩容请求，因此等同于一个不具备自动扩缩容能力的系统。

### 简单自动扩缩器

每当调用扩容操作时，简单自动扩缩器都会考虑启动一个预定义类型的新实例。启动的实例数量上限为每个 `provisioning_interval` 一个。此限制背后的动机基于以下观察。不可调度 Pod 很可能成批出现。也就是说，如果资源不足以部署一个 Pod，则队列中的下一个待调度 Pod 也可能因资源不足而无法部署。因此，在同一个调度周期中，可能会多次发出扩容请求。这可能导致启动过多的实例，而实际上一个实例可能就足以执行那些不可调度 Pod。事实上，我们根据实例预配延迟的估计值（即虚拟机启动并加入 K8s 集群所需的时间）加上一个小的应急值来设置 `provisioning_interval`。但请注意，该参数可由用户配置。

关于缩容操作，仅当调度周期成功地将队列中所有待调度 Pod 都放置完毕时才会发生。此外，仅考虑动态创建的节点（例如通过扩容创建的节点）进行关闭。如果满足这些条件，首先，取消预配任何没有运行 Pod 的空闲节点。其次，关闭那些仅运行可移动 Pod 且这些 Pod 可以在集群中任何其他节点上放置的节点。第三，如果某节点同时运行可移动 Pod 和批处理 Pod，且其所有可移动 Pod 都可以放置在其他节点上，则将该节点标记为不可调度。如果是这种情况，则驱逐可移动 Pod，留待 Kubernetes 重新创建，并在下一个周期由调度器进行放置。因为该节点已被标记为不可调度，除非严格必要（即没有其他未标记的节点具有足够容量），否则调度器将避免在该节点上放置 Pod。通过这种方式，一旦节点上运行的批处理作业完成，该节点有可能变为空闲，从而在后续的缩容周期中被取消预配。

#### 算法 5. 简单自动扩缩器 – 扩容

**输入：** 不可调度 Pod `p`

```
if elapsed time since last instance launched >= provisioning_interval
    launch new instance
    update last instance launch time
else
    ignore scale out operation
```

#### 算法 6. 简单自动扩缩器 – 缩容

```
if all pending pods were successfully scheduled in the last cycle
    shutdown any nodes that are empty and were autoscaled
    nodes = getAllSchedulableNodes()
    for each node in nodes
        if all pods are moveable
            if all pods can be placed on other nodes
                delete node
                let Kubernetes recreate the pods
                let the scheduler place the recreated pods
        if some pods are moveable and some pods are batch jobs
            if all moveable pods can be placed on other nodes
                delete all moveable pods
                let Kubernetes recreate the pods
                let the scheduler place the recreated pods
                taint the node as unschedulable
```

### 单实例绑定自动扩缩器

该启发式算法类似于单实例自动扩缩器。然而，此自动扩缩器旨在解决非绑定自动扩缩器的一个关键劣势。当不可调度 Pod 未以任何方式绑定或关联到自动扩容启动的节点时，由同一个不可调度 Pod 触发的多次自动扩容请求可能会被调用。这可能导致不必要地启动多个实例。

此自动扩缩器会跟踪 Pod 以及为它们启动的扩容节点。事实上，自动扩缩器会维护一个列表，记录那些可能在正在预配的节点上运行的 Pod。对于已关联到正在启动过程中节点的 Pod 发出的扩容请求将被忽略。一旦节点完成预配并加入集群，自动扩缩器会收到通知，从而取消该 Pod 与任何节点的关联。随后调度器负责在下一个周期将该 Pod 放置在集群中可用的节点上，这很可能是新预配的节点，但这并非强制要求。如果该节点被调度器填满了其他待调度 Pod，则会为该 Pod 触发扩容请求，并重复该过程。

为了进一步防止不必要的节点启动，绑定自动扩缩器在决定是否启动新实例时，会考虑已预配但尚未加入集群的节点。当为不可调度 Pod 发出扩容请求时，自动扩缩器会扫描正在预配过程中的节点列表。如果这些节点中仍有空间容纳该待调度 Pod，则将该 Pod 添加到可能在该节点上运行的 Pod 列表中，并且不启动新实例。

#### 算法 7. 简单绑定自动扩缩器 – 扩容

**输入：** 不可调度 Pod `p`

```
if pod has not been assigned to a provisioning node
    if pod can fit in one of the nodes being provisioned
        assign pod to provisioning node
    else
        launch a new node and assign the pod to the node
when new node is provisioned
    unassign any pod associated to the node
    remove node from list of provisioning nodes
    let the scheduler place pods in the new node
```

## 性能评估

### 测试环境与工作负载

### 实验验证

为了展示所提框架的潜在能力以及自动扩缩容的优势，我们执行了一组验证实验。我们根据表 2 的描述，对由批处理作业和长期运行服务组成的合成工作负载进行了建模。如表 3 所示，我们使用了三种不同的工作负载，它们具有不同的作业到达间隔时间以及作业与服务的组合。为了生成这些工作负载，作业以相等的概率随机选择，它们之间的延迟从具有不同均值的指数分布中采样。对于突发型工作负载，使用了 10 秒的均值，旨在模拟高速率到达的作业。对于缓慢型工作负载，使用了 60 秒的均值。混合型工作负载结合了突发和缓慢的作业到达率。它通过将工作负载分割为多个周期来生成，每个周期要么是突发的，要么是缓慢的。第一个周期随机选择，后续周期交替进行。每个周期中的作业数量随机选择，每个周期的最小作业数为 10。

作业实际上并不使用所请求的资源；然而，这不影响获得的结果，因为请求的目的是验证调度器的功能和性能。

#### 表 2. 评估中使用的作业类型

| Name | Task | Memory Requests | CPU Requests |
| --- | --- | --- | --- |
| **Batch Jobs** | | | |
| `batch_small` | `sleep 5 min` | 0.3Gi | 100m |
| `batch_med` | `sleep 10 min` | 0.6Gi | 200m |
| `batch_large` | `sleep 15 min` | 0.9Gi | 300m |
| **Long-running Services** | | | |
| `service_small` | nginx server | 1Gi | 100m |
| `service_med` | nginx server | 1.4Gi | 200m |
| `service_large` | nginx server | 2.359Gi | 300m |

#### 表 3. 评估中使用的工作负载

| Workload Name | Exponential Dist. Mean (sec) | Number of Batch Jobs | | | Number of Service Jobs | | | Total Batch | Total Service | Total |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | | Small | Med | Large | Small | Med | Large | | | |
| Bursty | 10 | 10 | 8 | 5 | 6 | 12 | 9 | 23 | 27 | 50 |
| Slow | 60 | 17 | 11 | 4 | 6 | 7 | 5 | 32 | 18 | 50 |
| Mixed | 60 slow, 10 bursty | 6 | 7 | 9 | 7 | 11 | 10 | 22 | 28 | 50 |

#### 表 4. Master 和 Worker 节点 VM 规格

| VM Type | # of vCPUs | RAM | Operating System |
| --- | --- | --- | --- |
| Master: `m2.medium` | 2 | 6 GB | Ubuntu 17.01 |
| Worker: `m2.small` | 1 | 4 GB | Ubuntu 17.01 |

#### 表 5. 评估中使用的算法专用参数值

| Parameter | Value | Algorithm |
| --- | --- | --- |
| VM price per second | $0.011 | N/A |
| `max_pod_age` | 1 min | Rescheduler |
| `provisioning_interval` | 1 min | Autoscaler |

Kubernetes 集群部署在 Nectar（Nectar, n.d.）上，这是一个基于 OpenStack 的澳大利亚研究云平台。用于部署 Kubernetes Master 和 Worker 节点的 VM 规格如表 4 所示。自定义架构组件部署在 Nectar 之外的一台 MacBook Pro 上（配置为 2.9 GHz Intel Core i7 处理器和 8 GB 内存），使用的 Kubernetes 版本为 1.10。由于 Nectar 不收取资源使用费，我们根据现有云提供商的计费模型估算每种方法的成本。具体而言，我们假设每个 Worker 的按秒计费为 $0.011，基于 Microsoft Azure 通用型 B2S 实例类型，任何部分使用均向上取整至最近的秒。虽然 Microsoft 按分钟计费，但考虑到实验的性质和规模，我们假设按秒计费，这不会影响结果的显著性。表 5 描述了算法专用参数所使用的值。

## 结果

首先，我们从成本和调度时长两方面评估每种重调度和自动扩缩容启发式算法的性能。我们将调度时长定义为从提交第一个作业时刻到最后一个批处理作业完成执行时刻所经过的时间。成本根据每个 VM 被提供的时间量进行估算；即从向云提供商发出提供请求的那一刻起，直到发出取消提供请求的那一刻止。对于静态节点，成本基于工作负载的总调度时间进行估算。最后，整个实验过程中只有重调度和自动扩缩容策略发生变化，调度器（最佳适配装箱算法）保持不变。

图 5 展示了每种调度器/自动扩缩容器组合在三种工作负载下的成本和总调度时长。对于混合工作负载，`Non-binding Rescheduler` 和 `Binding Autoscaler`（NBR-BAS）组合获得了最低的成本和调度时长。事实上，`Binding Autoscaler` 与任何一种重调度器结合都能带来最低成本，且在 3 种情况中有 2 种实现了最低调度时长。这强调了拥有旨在避免不必要的扩容操作的启发式算法的重要性。`Non-binding Autoscaler` 会在 Pod 无法放置时盲目提供新实例，而 `Binding Autoscaler` 会在提供新节点之前，将正在提供中的实例视为传入 Pod 的潜在宿主。至于 `Binding` 和 `Non-binding Rescheduler` 之间的性能差异，允许调度器放置所有待处理 Pod 似乎比在重调度器中尝试复制调度器的工作更好。

| Figure 5. 三种不同工作负载和六种不同算法的成本与调度时长。 |
| --- |
| ![Figure978-1-7998-2701-6.ch010.f05](img/ch010.f05.png) |

突发型工作负载的成本结果与混合工作负载类似。再次，`Binding Autoscaler` 导致使用的资源数量较少，因此成本较低。然而，由于资源提供的频率较低且方式更保守，且作业到达率极高，作业可能需要等待更长时间才能被放置，从而导致更高的调度时长。对于这种特定工作负载，重调度器的存在在成本和调度时间方面似乎没有显著影响。也许重调度仅延迟了 VM 的提供，而实验规模不足以观察到这些影响。然而，在表 5 中我们展示了使用重调度器时资源的实际利用率确实有所提高，尽管由于上述原因提高幅度很小。

对于缓慢型工作负载，表现最好的算法组合再次是 NBR-BAS，无论是在成本还是调度时长方面。在这种情况下，该方法与 `Void Rescheduler` 和 `Binding Autoscaler`（VR-BAS）在两个指标上的差异显著，因此可以清楚地体会到重调度作业以更好地利用资源的好处。

为了进一步了解所提方法的优势，我们还将其性能与默认 Kubernetes 调度器进行了比较。我们根据每种重调度器/自动扩缩容器组合在成本和调度时长方面的表现给出一个得分，两者权重相同。我们将 Kubernetes 调度器（K8S）与每种工作负载下得分最低（即性能最佳）的两种算法进行比较。结果如图 6 所示。K8S 的成本和调度时间是通过在 K8S 能成功放置并执行所有作业的最少静态节点数上运行每个工作负载来估算的。在重调度器/自动扩缩容器算法组合中，VR 对应 `Void Rescheduler`，NBR 对应 `Non-binding Rescheduler`，NBAS 对应 `Non-binding Autoscaler`，BAS 对应 `Binding Autoscaler`。

#### 图 6. 不同工作负载（混合、突发和缓慢）下 k8s 调度器与表现最佳的重调度器/自动扩缩容器组合的成本与调度时长对比。

![Figure978-1-7998-2701-6.ch010.f06](img/ch010.f06.png)

对于每种工作负载，与 Kubernetes 调度器相关的成本均明显高于所提方法的相关成本。最大的成本降低出现在缓慢工作负载中，`NBR-BAS` 相比 Kubernetes 默认调度器实现了超过 58% 的成本降低。关于调度时长，我们算法的性能仅略逊于 `K8S`。考虑到在成本方面获得的收益，我们认为这是一个非常合理的权衡。

#### 表 6. 每种重调度器/自动扩缩容器组合的调度性能与资源利用率。

| 工作负载 | 重调度器 | 自动扩缩容器 | 中位数调度时间 (秒) | 平均内存 请求/容量 | 平均 CPU 请求/容量 | 平均 Pod 数/节点 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 混合 | Void | Non-binding | 25.00 | 0.72 | 0.68 | 2.03 |
| 混合 | Binding | Non-binding | 37.00 | 0.73 | 0.67 | 1.99 |
| 混合 | Non-binding | Non-binding | 111.00 | 0.79 | 0.72 | 2.22 |
| 混合 | Void | Binding | 49.50 | 0.81 | 0.72 | 2.20 |
| 混合 | Binding | Binding | 26.00 | 0.77 | 0.70 | 2.14 |
| 混合 | Non-binding | Binding | 112.50 | 0.80 | 0.72 | 2.23 |
| 缓慢 | Void | Non-binding | 14.00 | 0.79 | 0.72 | 2.41 |
| 缓慢 | Binding | Non-binding | 11.50 | 0.78 | 0.70 | 2.33 |
| 缓慢 | Non-binding | Non-binding | 10.00 | 0.83 | 0.74 | 2.52 |
| 缓慢 | Void | Binding | 12.50 | 0.82 | 0.72 | 2.44 |
| 缓慢 | Binding | Binding | 17.50 | 0.84 | 0.74 | 2.49 |
| 缓慢 | Non-binding | Binding | 12.50 | 0.86 | 0.76 | 2.62 |
| 突发 | Void | Non-binding | 422.50 | 0.65 | 0.69 | 2.11 |
| 突发 | Binding | Non-binding | 297.00 | 0.67 | 0.71 | 2.24 |
| 突发 | Non-binding | Non-binding | 467.00 | 0.62 | 0.67 | 2.04 |
| 突发 | Void | Binding | 418.00 | 0.70 | 0.72 | 2.28 |


# 自定义调度器与 Kubernetes API 交互，持续监控集群中 Pod 的状态

一个 Pod 对应单个任务，无论是长期运行还是批处理。因此，调度器专注于处理待调度 Pod（即那些需要被调度的 Pod）。对于每个待调度 Pod，会从整个集群资源池中筛选出一组合适的资源（即 Kubernetes 工作节点）。然后从中选择一个资源，并在该 Pod 与资源之间创建绑定。此绑定会导致 Kubernetes 在选定节点上运行该 Pod。再次值得一提的是，已实现了不同的策略来选择合适的节点集合并将任务分配给其中一个，这些策略可轻松插入系统。这些内容在第 5 节中详细描述。

每当无法放置 Pod 时，自定义调度器会与自定义重调度器交互。重调度器随后尝试整合可移动的 Pod，以便将传入的 Pod 放置在现有节点上。如果集群已达容量上限，且没有空间容纳传入的待调度 Pod，则会调用自动扩缩容组件，以确定是否应配置新的 VM 来放置该 Pod。自动扩缩容器随后可决定要启动的 VM 数量和类型，并指示云适配器通过特定的 IaaS 云提供商 API 创建新实例。在此期间，不可调度的 Pod 可保留在调度队列中处于待调度状态，以便在新配置（或最近释放）的资源可用时，在后续周期中进行调度。该 Pod 也可从常规调度队列中移除，以便在新创建的节点可用后直接分配给它。自定义组件之间的交互如算法 1 所示。

| 图 2. 原型系统的类图 |
| --- |
| ![Figure978-1-7998-2701-6.ch010.f02](i/ch010.f02.png) |

## 设计与实现

原型系统使用 Java 实现。它作为一个独立进程运行，因此无需部署在属于 Kubernetes 集群的节点上。如图 1 所示，系统通过 API 与 Kubernetes 交互。图 2 展示了原型系统的高层类图。我们包含了与本文讨论相关的类、方法和属性。`util` 包中的类是直接与 Kubernetes 交互的类，而其余类包含算法的实际逻辑。

长期运行任务被定义为 Kubernetes 部署。一个部署会创建一个副本集，生成所需数量的复制 Pod。Pod 定义了实际的应用程序或任务。当副本失败时，Pod 会自动重新创建。在本工作的初始实例中，我们假设部署具有单个副本。此外，定义为可移动的长期运行服务必须包含一个标签来指示这一点（键：`rescheduling`，值：`moveable`）。必须指定 CPU 和内存请求，以及 CPU 和内存限制，二者应相等，以确保 Pod 被分配到 Kubernetes **Guaranteed** QoS 类。图 3 展示了定义单副本 nginx 服务部署的 YAML 文件示例。

| 图 3. 定义单副本 nginx 服务部署的 YAML 文件 |
| --- |
| ![Figure978-1-7998-2701-6.ch010.f03](i/ch010.f03.png) |

| 图 4. 定义批处理作业的 YAML 文件 |
| --- |
| ![Figure978-1-7998-2701-6.ch010.f04](i/ch010.f04.png) |

### 算法 2. 最佳适配装箱调度器

**输入：** 待调度 Pod `p`

**输出：** 成功返回 `true`，否则返回 `false`

```
nodes = getAllSuitableNodes(p)
node = nodes 中可用 RAM 量最少的节点
if node is not null
    createBinding(node, p)
    return true
return false
```

关于请求/限制和副本的相同规则也适用于批处理作业。然而，这些是使用 Kubernetes Job 而非 Deployment 定义的，Job 允许定义运行至完成的任务。此外，Job 不能标记为可移动，而必须使用键 `type` 和值 `batch` 进行标记。图 4 展示了定义 Job 的示例 YAML。

## 成本高效的调度与自动扩缩容算法

本节描述了在原型系统中提出并实现的算法。该框架的设计灵活，允许在启动系统时使用任意组合的调度、重调度和自动扩缩容算法。

### 调度

#### 最佳适配装箱调度器

通用装箱问题可定义如下。给定 `n` 个不同重量的物品和容量均为 `c` 的箱子，将每个物品分配到一个箱子中，使得使用的箱子总数最小化。针对此问题的在线版本（即物品逐个到达，必须在考虑下一个物品前将当前物品放入箱子）设计了多种贪心解法。其中一种解法称为最佳适配，它将物品放入仍能容纳该物品且未超出箱子容量的最满箱子中。

针对本工作解决的调度问题，物品对应 Pod，箱子对应集群节点。由于 Pod 持续到达等待执行，我们也将该问题视为在线问题。因此，该调度器将传入的待调度 Pod 放置在满足 Pod 要求且可用资源量最小的节点上。然而，此问题并非一维的，因为 Pod 需要两种不同的可用资源：CPU 和内存。我们通过首先筛选出具有足够可用 CPU 的节点，然后从该列表中选择可用内存量最少且至少满足传入 Pod 内存请求的节点来解决此问题。这样做有两个原因。首先，我们的目标是保持算法简单且能快速做出决策。其次，我们认为 CPU 是可压缩资源；即如果超出请求量或节点过载，其使用可被限制。另一方面内存是不可压缩的，其使用无法被限制。阻止 Pod 使用超额内存只能通过终止 Pod 来实现，而缓解节点内存压力只能通过驱逐当前部署在该节点上的 Pod 来实现。

### 重调度

见算法 3。

### 算法 3. 非绑定重调度器

**输入：** 不可调度 Pod `p`

```
If age of p is greater than or equal to max_pod_age
    nodes = getAllNodesWithEnoughCPU(p)
    sort nodes descending based on available memory
    for each node in nodes
        if the node has moveable pods running
            sort moveable pods descending based on requested memory
            for each moveable pod
                if the pod can be placed somewhere else
                    add pod to list of pods to evict
                    update freed memory
                    if enough memory has been freed
                        evict pods
                        success = true
                        break
            if success
                break
```

#### 空重调度器

空重调度器将直接忽略重调度请求，因此等同于没有重调度能力的系统。

#### 非绑定重调度器

此重调度器旨在驱逐节点上的可移动 Pod，当且仅当 i) 这些可移动 Pod 可被重新调度到其他位置，且 ii) 通过驱逐这些可移动 Pod，该节点现在拥有足够资源来放置不可调度的 Pod。然而，仅当不可调度 Pod 处于待调度状态的时间至少达到 `max_pod_age` 时才会尝试此操作。其目的是减少不必要的重调度和自动扩缩容决策，因为这给了批处理作业完成的机会，从而为不可调度 Pod 腾出空间。

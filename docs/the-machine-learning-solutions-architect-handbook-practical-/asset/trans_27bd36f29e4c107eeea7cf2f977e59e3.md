

在这种架构中，工作节点仅与参数服务器（PS）节点通信以交换梯度和参数，而不相互通信。在多服务器节点环境中，每个服务器节点也会与其他每个服务器节点通信，以复制参数以实现可靠性和可扩展性。交换梯度和参数，以便可以同步和异步实现更新。同步梯度更新策略会阻止设备处理下一个小批量数据，直到所有设备的梯度都已同步。这意味着每次更新都必须等待最慢的设备完成。这可能会减慢训练速度，并使训练过程在设备故障方面变得不那么可靠。

从积极方面来看，同步更新不必担心过时的梯度，这可能会导致更高的模型准确性。异步更新不需要在处理下一个小批量数据之前等待所有设备同步，尽管这可能会导致准确性降低。

这种方法的主要限制是，PS 可能会成为通信瓶颈，特别是对于拥有数十亿或数万亿个参数的大型模型。随着模型大小的增长，工作节点和 PS 之间需要传输的数据量会显著增加，从而导致潜在的通信开销和带宽限制。

此外，随着工作节点数量的增加，PS 需要处理越来越多的梯度更新和参数分发，这可能会成为可扩展性挑战。这种集中式架构可能会限制分布式训练过程的整体吞吐量和效率，尤其是当工作节点数量变得非常大时。此外，较慢或性能不佳的工作节点可能会减慢整个训练过程，因为 PS 必须在更新参数之前等待所有梯度。

## 在框架中实现 PS

PS 分布式训练由多个深度学习框架原生支持，包括 TensorFlow。具体来说，TensorFlow 通过其 `ParameterServerStrategy` API 原生支持基于 PS 的分布式训练。以下代码示例展示了如何为 TensorFlow 实例化 `ParameterServerStrategy` API：

```
strategy = tf.distribute.experimental.ParameterServerStrategy(
    cluster_resolver)
```

在此代码示例中，`cluster_resolver` 参数有助于发现和解析工作节点的 IP 地址。

`ParameterServerStrategy` 可以直接与 Keras 的 `model.fit()` 函数或自定义训练循环一起使用，方法是使用 `strategy.scope()` 语法包装模型。请参阅以下示例语法，了解如何使用 `scope()` 包装模型以进行分布式训练：

```
with strategy.scope()
    model = <model architecture definition>
```

除了深度学习库中原生支持的 PS 实现之外，还有通用的 PS 训练框架，例如字节跳动的 BytePS 和亚马逊的 Herring，它们适用于不同的深度学习框架。SageMaker 通过其 SageMaker 分布式训练库，在底层使用 Herring 进行数据并行分布式训练。

PS 策略的一个缺点是网络带宽利用率低效。Herring 库通过结合 AWS `Elastic Fabric Adapter` (`EFA`) 和参数分片技术来解决这一缺点，该技术利用网络带宽实现更快的分布式训练。`EFA` 利用云资源及其特性（例如多路径骨干网）来提高网络通信效率。您可以在 [https://www.amazon.science/publications/herring-rethinking-the-parameter-server-at-scale-for-the-cloud](https://www.amazon.science/publications/herring-rethinking-the-parameter-server-at-scale-for-the-cloud) 上了解有关 Herring 的更多信息。

## AllReduce 概述

虽然 PS 架构易于理解和设置，但它确实存在一些挑战。例如，PS 架构需要额外的节点作为 PS，并且很难确定服务器节点和工作节点之间的正确比例，以确保服务器节点不会成为瓶颈。

AllReduce 拓扑试图通过消除服务器节点，并将所有梯度聚合和全局参数更新分发到所有工作节点来改进 PS 的某些局限性，因此它被称为 `AllReduce`。以下图表显示了 AllReduce 的拓扑：

![](OEBPS/Images/B20836_10_05.png)图 10.5：AllReduce 架构

在 AllReduce 拓扑中，每个节点在每个训练步骤中将参数梯度发送到所有其他节点。然后，每个节点聚合梯度并在本地执行归约函数（例如 `average`、`sum` 或 `max`），然后再使用下一个训练步骤计算新参数。由于每个节点都需要与其他每个节点通信，这导致节点之间存在大量的网络通信，并且每个节点都拥有所有梯度的副本，因此需要重复的计算和存储。

更高效的 AllReduce 架构是 Ring AllReduce。在这种架构中，每个节点仅将部分梯度发送到其下一个相邻节点，每个节点负责聚合其被分配计算的全局参数的梯度。这种架构大大减少了集群中的网络通信量和计算开销，因此对于模型训练更高效。以下图表显示了 Ring AllReduce 架构：

![](OEBPS/Images/B20836_10_06.png)

图 10.6：Ring AllReduce

与 PS 方法相比，Ring AllReduce 方法随着工作节点数量的增加具有更好的可扩展性。由于没有集中式 PS，通信负载在工作节点之间分布，从而减少了潜在的瓶颈。Ring AllReduce 方法还具有较低的通信开销，特别是对于拥有数十亿或数万亿个参数的大型模型。它不是将单个梯度发送到中央服务器，而是将梯度求和并沿环形拓扑传递，从而减少了需要传输的数据总量。

总体而言，Ring AllReduce 方法为大规模分布式训练提供了更好的可扩展性和效率。它在工作节点之间分布通信负载，减少了潜在的瓶颈和同步开销。但是，PS 方法可能仍然适用于较小规模的分布式训练场景，或者在容错性不那么重要的情况下。

## 在框架中实现 AllReduce 和 Ring AllReduce

AllReduce 和 Ring AllReduce 架构在多个深度学习框架中原生支持，包括 TensorFlow 和 PyTorch。

TensorFlow 支持使用其 `tf.distribute.MirroredStrategy` API 在单机多个 GPU 上进行 AllReduce 分布式训练。使用此策略，每个 GPU 都有一个模型副本，所有模型参数在不同设备之间镜像。使用高效的 AllReduce 机制来保持这些参数同步。以下代码示例展示了如何实例化 `MirroredStrategy` API：

```
strategy = tf.distribute.MirroredStrategy()
```

对于多机分布式训练，TensorFlow 使用 `tf.distribute.MultiWorkerMirroredStrategy` API。与 `MirroredStrategy` 类似，`MultiWorkerMirroredStrategy` 在所有机器的所有设备上创建所有参数的副本，并使用 AllReduce 机制将其同步。以下代码示例展示了如何实例化 `MultiWorkerMirroredStrategy` API：

```
strategy = tf.distribute.MultiWorkerMirroredStrategy()
```

与 `ParameterServerStrategy` 类似，`MirroredStrategy` 和 `MultiWorkerMirroredStrategy` 可以与 `keras model.fit()` 函数或自定义训练循环一起使用。要将模型与训练策略关联，可以使用相同的 `strategy.scope()` 语法。



除了查询训练服务 API 获取执行状态外，我们还可以在 Kubernetes 中检查训练进度。通过`kubectl`可以看到 worker pod 已经创建。这是一个 master worker，另外两个是本地 worker。Kub 服务实现了 master pod 和 worker pod 之间的连接。查看以下代码：

```bash
# 查看 Kubernetes 资源状态
# 我们可以看到分布式训练组
# 包含了三个 pod 和一个服务
kubectl get all -n orca
```

| 名称 | 就绪 | 状态 | 描述 |
| :--- | :--- | :--- | :--- |
| pod/intent-classification-1-worker | 0/1 | Completed | worker 之一 |
| pod/intent-classification-2-worker | 0/1 | Completed | |
| pod/intent-classification-1-master | 0/1 | Completed | Master pod |
| service/intent-classification-1-service | ClusterIP | | |

> pod 通间的 Kubernetes 服务

### 4.3.3 启动训练任务

现在，让我们看看 Kubernetes 后端启动训练任务的工作流。当接收请求时，请求会被加入队列。同时，Kubernetes 调度器监控该队列。当调度器发现等待的任务且有可用资源时，将开始处理这些任务。

启动 PyTorch 分布式训练任务时，请求会被加入队列。同时，Kubernetes 调度器监控该队列。当调度器发现等待的任务且有可用资源时，将开始处理这些任务。

启动 PyTorch 分布式训练任务时，请求会被加入队列。同时，Kubernetes 调度器监控该队列。当调度器发现等待的任务且有可用资源时，将开始处理这些任务。

启动 PyTorch 分布式训练任务时，请求会被加入队列。同时，Kubernetes 调度器监控该队列。当调度器发现等待的任务且有可用资源时，将开始处理这些任务。

## 4.3 一个支持数据并行分布式训练的示例

```java
envs.put("WORLD_SIZE", Integer.toString(worldSize));
// RANK 0 是主节点
envs.put("RANK", Integer.toString(rank));
envs.put("MASTER_ADDR", masterPdnName);
envs.put("MASTER_PORT", Integer.toString(masterPort));
```

> 将分布式训练相关的配置设置为环境变量

```java
V1PodSpec spec = new V1PodSpec()
restartPolicy("Never")
.addContainers(new V1Container()
.image(algorithm.getAlgorithm())
env(envVarsList(envs));
```

> 定义 pod 配置；将训练参数作为环境变量传递

```java
String workerPodName = rank == 0 ? masterPodName :
  String.format("job-%d-%s-worker-%d", jobId, now, metadata.getName()), rank);
V1PodSpec workerPodBody = new V1PodSpec()
workerPodBody.setApiVersion("v1");
```

```java
// (3)
api.createNamespacedPod(config.kubeNamespace, workerPodBody, null, null, null);
```

> 创建实际的训练 pod

```java
return podNames;
```

## RANK 值并不一定与 pod 一一对应

RANK 是分布式训练中一个比较棘手的值。请注意，RANK 是训练进程的唯一 ID，而不是 pod。如果一个 pod 有多个 GPU，那么它可以运行多个训练进程。在示例中，由于我们每个 pod 运行一个训练进程，因此我们为每个 pod 分配了不同的 RANK 值。

当在一个 pod 中运行多个训练进程时，我们需要为该 pod 分配多个 RANK 值。例如，当在一个 pod 中运行两个进程时，该 pod 需要两个 RANK 值，每个一个。

你可能会注意到，此示例中创建的 Kubernetes pods 和服务是为 PyTorch 分布式训练库定制的。事实上，该示例服务限于 PyTorch。为了支持其他框架（如 TensorFlow 2）的训练代码，我们可以扩展 Kubernetes 追踪器以支持 TensorFlow 分布式训练的设置。

例如，我们可以收集所有 worker pod 的 IP 或 DNS 名称，将它们合并，并广播回每个 worker pod。在广播期间，我们将每个 pod 中的`TF_CONFIG`环境变量设置为工作组信息，以启动分布式训练组。`TF_CONFIG`环境变量是 TensorFlow 分布式库的特殊要求。

![](img/9dbecddeac1b6cad2e240ace2b0d4b22_142_0.png)

### 4.3.4 更新和获取作业状态

创建训练 pod 后，Kubernetes 作业追踪器将继续查询 pod 的执行状态，并在状态发生变化时将作业移动到其他状态。例如，如果 pod 成功创建并开始运行，追踪器将作业从启动列表移动到运行列表。如果 pod 执行完成，追踪器将作业从运行列表移动到完成作业列表。图 4.5 描述了这一过程。

![](img/9dbecddeac1b6cad2e240ace2b0d4b22_143_0.png)

图 4.5 跟踪 Kubernetes 作业状态：步骤 1，获取运行列表中的作业；步骤 2，查询 Kubernetes 集群中运行的每个作业的 pod 执行状态；步骤 3，如果 pod 执行完成（成功或失败），则将作业移动到完成列表。

当用户提交作业查询时，训练服务将在内存存储的所有四个队列中搜索作业 ID 并返回作业对象。有趣的是，尽管有多个训练 pod，但我们只需要检查主 pod 的状态来跟踪分布式进度。这是因为对于同步数据训练，所有工作器在每个训练周期中都必须相互同步，因此主 pod 可以代表其他 worker pod。

查询和更新作业执行状态的代码与我们在 3.3.5 中看到的 Docker 作业追踪器非常相似。唯一的区别在于，我们查询的是 Kubernetes 集群而不是 Docker 引擎来获取训练状态。

## 4.3 一个支持数据—分布式训练的示例服务

代码留给你们探索；你可以在`KubectlTracker`类的`updateContainerStatus`方法找到它。

### 4.3.5 转换训练以分布式运行

我们对意图分类训练代码（在上章 3.3.6 节中引入）进行了两处更改，以同时支持分布式模式和单设备模式。

### 第一次更改：初始化训练组

我们使用`WORLD_SIZE`环境变量来检查训练代码是否应该在分布式训练中运行。如果世界大小等于 1，则使用我们在 3.3.6 节中看到的相同单设备训练代码。

但如果值大于 1，我们将初始化训练进程以加入分布式组。我们还注意到，每个 pod 的 RANK 值是从训练服务（Kubernetes 作业追踪器）传递的，这是分布式组初始化所需的。在自注册到分布式组后，我们对分布式组进行初始化。见如下代码：

```python
def distribute():
    # 如果世界大小大于 1
return is_available() and config.WORLD_SIZE > 1
```

```python
def is_distributed():
    # 初始化进程组
dist.init_process_group("gloo")
```

```python
if is_distributed():
    # 使用 DataParallel 包装模型
model = DDP(model)
```

```python
if is_distributed():
    # 限制数据加载为数据集的子集
sampler = DistributedSampler(dataset, rank=config.RANK)
```

### 第二次更改：仅由主节点上传模型

在第二次更改中，我们只允许主节点上传模型。这是为了防止每个 worker 重复上传模型。

```python
if config.RANK == 0:
    # 如果准确率良好，评估模型
    accu_test = evaluate(dataloader)
    # 上传模型到元存储
    artifact = orca_utils.create_artifact(
        config.MODEL_BUCKET, config.MODEL_NAME
    )
```

![](img/9dbecddeac1b6cad2e240ace2b0d4b22_144_0.png)

### 4.3.6 改进

如果我们继续完善该服务，可以遵循 4.2 中的思路处理容错和减少网络带宽饱和。我们还可以扩展追踪器以支持 TensorFlow。从训练服务的角度来看，它们并没有太大，因为训练服务传递给训练代码的配置是非常通用的；我们仍然可以将其视为黑盒。

## 4.4 无法加载到 GPU 的模型训练

神经网络的大小（由参数数量定义）在研究领域迅速增长，我们无法忽视这一趋势。以 ImageNet 挑战为例，2014 年的冠军（GoogleNet）拥有 400 万个参数；2017 年的冠军（Squeeze-Excitation Networks）拥有 1.4800 万个参数；而目前的方法拥有超过 10 亿个参数。

尽管我们的神经网络增长了近 300 倍，但 GPU 内存只增加了 4 倍。未来你将看到更多由于无法加载到 GPU 而无法训练的情况。

在本节中，我们将讨论大模型的常用策略。与 4.2 描述的数据并行策略不同，这里介绍的方法需要代码方面的工作。

### 4.4.1 传统方法：内存节省

假设你的数据团队想要训练一个可以加载到集群中最大 GPU 的模型；他们想在 10 GB GPU 上训练一个 24 GB 的 BERT 模型。团队可以使用几种内存节省技术在在这种情况下训练模型，包括梯度累积和内存交换。作为平台开发者，你只需要了解这些选项即可。我们将简要描述它们，以便你知道何时使用其中每一个。

## 4.4 无法加载到单个 GPU 的大模型训练

以及 NVIDIA 的 vDNN (https://arxiv.org/abs/1602.08124)，但由于这本书不是关于深度学习算法的，我们将它们留给独立学习。

## 梯度累加 (GRADIENT ACCUMULATION)

在深度学习中，数据集被划分为批（batches）。在每个训练步骤中，为了计算损失、计算梯度和更新模型参数，我们将整个批样本（训练数据）加载到内存中并一次处理所有计算。

我们可以通过减小批大小（batch size）来缓解内存压力——例如，每批训练 16 个样本而不是 32 个。但减小批大小会导致模型收敛变慢很多，这时梯度累加就能派上用场了。

梯度累加将批分成可配置数量的微批（mini-batches），并在每个微批处理后计算损失和梯度。但它并不是直接更新模型参数，而是对所有微批的梯度进行更新和累加。最后，根据累加后的梯度来更新模型参数。

让我们来看一个例子，它是如何加速这个过程的。假设由于 GPU 内存限制，我们无法以 32 的批大小运行程序。通过梯度累加，我们可以将每个批分成四个微批，每个微批的大小为 8。因为我们累加了四个微批的梯度，并且在四个微批完成后才更新模型，所以这个过程几乎等同于批大小为 32 的训练。区别在于，我们在 GPU 中每次只计算 8 个样本而不是 32 个，因此成本比批大小为 32 时慢了 4 倍。

## 内存交换（GPU 与 CPU）（MEMORY SWAP）

内存交换非常简单：它在 CPU 和 GPU 之间来回激活值（activations）。如果你不熟悉深度学习术语，可以将激活值理解为神经网络中每个节点的计算输出。其核心思想是将当前计算步骤所需的数据保留在 GPU 中，并将计算结果交换到 CPU 中以供后续步骤使用。

基于这一想法，一种名为 L2L（层到层）的新型接力执行技术仅在 GPU 上保留执行的层和中转层（transit）。整个模型和持有状态的优化器都存储在 CPU 空间中。L2L 可以极大提高吞吐量，并允许我们在负担得起的设备上开发大模型。如果你对这种方法感兴趣，可以查看 Pudipeddi 等人的 [Using a New Execution Algorithm for Training Large Neural Networks with Constant Memory](https://arxiv.org/abs/2002.05645)，该论文在 GitHub 上也有 PyTorch 实现。

梯度累加和内存交换都是在较小的 GPU 上训练大模型的有效方法。但像大多数事情一样，它们也是有代价的：它们会减慢训练速度。由于这个缺点，我们通常只将它们用于原型设计。

为了获得可行的训练速度，我们确实需要在多个 GPU 上对模型进行分布式训练。因此，在下一节中，我们将介绍一种更接近生产环境的方法：流水线并行（pipeline parallelism）。它能以惊人的训练速度分布式地训练大模型。

### 4.4.2 流水线模型并行 (Pipeline model parallelism)

在 4.2 节中，我们讨论了最常用的训练方法：数据并行。这种方法在每个设备上保留整个模型的副本，并将数据划分到多个设备上。然后在每个训练步骤中，聚合梯度并更新模型。只要整个模型可以加载到单个 GPU 中，数据并行的整个方法就能很好工作。正如我们在本节看到的，我们并不总是能做到。这就是流水线并行大显身手。在本节中，我们将学习流水线并行，这是一种在多个 GPU 上分布式训练大模型的训练方法。

为了理解流水线并行，让我们先简要查看模型并行。这个小插曲会让跳转到流水线并行变得更容易。

## 模型并行 (MODEL PARALLELISM)

模型并行的思想是将神经网络分成更小的子集，并在不同的 GPU 上运行每个子网络。图 4.6 展示了模型并行的方法。

![](img/9dbecddeac1b6cad2e240ace2b0d4b22_147_0.png)

图 4.6 将一个四层全连接深度学习网络分为四个小组；每组有一层，且每个小组运行在一个 GPU 上。

图 4.6 可视化了模型并行的过程。它首先将一个神经网络（四层）转换为四个子网络（单层），然后为每个单层网络分配一个专用的 GPU。通过这种方式，我们在四个 GPU 上分布式地运行模型。

模型并行的概念很直接，但实际实现可能很复杂；它取决于网络的架构。为了让你有个直观的感受，下面的列表是一段虚拟的 PyTorch 代码，使网络在两个 GPU 上运行。

## 4.4 无法加载到单个 GPU 的大模型训练

列表 4.2 PyTorch 中的示例模型并行实现

```python
gpu1 = 1
gpu2 = 2

class a_large_model(nn.Module):
    def __init__(self):
        super().__init__()

        # 将网络初始化为两个子网络。
        self.subnet1 = ...
        self.subnet2 = ...

        # 将 subnet1 和 2 放在两个不同的 GPU 上
        self.subnet1.cuda(gpu1)
        self.subnet2.cuda(gpu2)

    def forward(x):
        # 将数据加载到 GPU 1 并计算输出
        x = self.subnet1(x)
        # 将输出移动到 GPU 2 并计算输出
        x = self.subnet2(x.cuda(gpu2))
        return x
```

如列表 4.2 所示，我们将`subnet1`的输出移动到 GPU 2。

模型并行的另一个问题是其严重的利用率低下。由于三个 GPU 之间的顺序依赖，每个 GPU 有 66% 的时间处于空闲状态。例如，在前向路径中，`subnet 2`需要等待`subnet 1`的输出才能完成自己的计算，在 GPU 1 完成计算之前，GPU 2 将一直空闲。

无论你添加多少 GPU，同一时间只有一个 GPU 在工作，这是巨大的浪费。流水线并行通过消除浪费和充分饱和 GPU 使得训练变得更高效。

图 4.7 并行训练。这是因为顺序的。

## 第 4 章 分布式训练

- 等待反向路径
- 等待前向路径
- 训练数据批
- 只有一个 GPU 激活
- S1: 子网络 1

![](img/9dbecddeac1b6cad2e240ace2b0d4b22_149_0.png)

GPU 1 (S1):
GPU 2 (S2):
GPU 3 (S3):
S3: 子网络 3

模型并行：划分网络并运行在三个 GPU 上

图 4.7 模型并行会导致极低的 GPU 利用率。在这种方法中，网络被分成三个子网络并运行在三个 GPU 上。这是因为三个 GPU 之间的顺序依赖。

## 流水线并行

PIPELINE PARALLELISM 本质上是模型并行的改进版本。除了将网络划分到不同的 GPU 外，它还将将每个训练批分为小的微批，并在层之间重叠这些微批的计算。通过这种方式，它让所有 GPU 在大部分时间内保持工作状态，从而提高了 GPU 利用率。

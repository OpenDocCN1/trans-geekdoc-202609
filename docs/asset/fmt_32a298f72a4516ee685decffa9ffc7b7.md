
以下是对示例响应的几个解释：在之前的示例中，

- *Status/conditions*（状态/条件）——显示当前和之前的状态。我们看到实验经历了三个状态：创建、运行和成功。从消息中，我们知道实验完成是因为耗尽训练预算——最大试验次数。
- *Current optimal trial*（当前最优试验）——显示“最佳”试验和使用的超参数值。它还显示了目标指标的状态。随着实验的进行，这些值将不断更新，直到实验中的所有试验完成，我们获取`status.currentOptimalTrial`。
- *parameterAssignment*（超参数值分配）——最终结果。

### C.2.7 第 7 步：故障排除

如果存在试验，我们可以运行以下命令检查试验作业的错误消息。失败的 HPO 示例所示：

```bash
> % k describe trial bayesian-optimization-mnist-pytorch-88c9rdjx \
-n kubeflow
```

```
Name:
bayesian-optimization-mnist-pytorch-88c9rdjx
Spec:
Parameter Assignments:
Name:
lr
Value:
0.010547476197421666
Name:
num-layers
Value:
3
Name:
optimizer
Value:
trl
```

```
Status:
Completion Time: 2022-01-23T06:23:50Z
Conditions:
Message: 试验失败。Job message: 任务达到了指定的退避限制
Reason: TrialFailed. Job reason: BackoffLimitExceeded-Failure
```

从返回的数据中，我们可以看到试验中使用的超参数值以及相关的错误消息。

# 318 附录 C 通过 Kubeflow Katib 创建 HPO 服务

除了`describe`命令的错误消息外，我们还可以通过检查训练容器的日志来找到根本原因。如果你选择使用 Katib 标准指标收集器，Katib 将在同一个 Pod 中与你的代码容器运行`metrics-logger-and-collector`。指标收集器捕获训练容器的所有标准输出日志；你可以使用以下命令检查这些日志：`kubectl logs [trial] -c metrics-logger-and-collector -n kubeflow`。示例命令如下：

```bash
$kubectl logs bayesian-optimization-mkqq6nm -c metrics-logger-and-collector -n kubeflow
```

日志包含了有用信息，例如训练过程的初始参数、数据集下载和模型训练指标。在下面的示例输出中，我们可以看到`Validation-accuracy`和`Train-accuracy`。Katib 指标收集器将解析这些值，它们被定义为实验配置中的指标：![](img/9dbecdac1b6cad2e240ace2b0d4b22_339_0.png)

```
- Trial Name: bayesian-optimization-mkqq6nm2022-01-23T05:17:20 start with arguments Namespace (
add_str=value, batch_size=64, disp_patches=10,
dtype=float32, gc_threshold=0.5, gc_type='none', gpus=None,
image_shape=(1, 28, ), warmup_epochs=5,
warmup_strategy='linear', wd=0.0001)
INFO 05:17.2019784 16 main.go:136 2022-01-23T15:20:20 INFO
downloaded http://data.mnist.io/data/mnist/t10k-labels-idxl-ubyte.gz
into t10k-labels-idxl-ubyte.gz success 05:17.26.71152 16 main.go:136 2022-01-23T15:20:20 INFO ... (rest of log)
```

## 316 使用 Kubeflow Katib 创建 HPO 服务

除了之前的`kubectl`命令外，我们还可以使用 Katib SDK、其 UI 或发送 HTTP 请求来启动实验。

### C.2.6 第 6 步：查询进度和结果

你可以使用以下命令检查实验运行状态：

```bash
$ kubectl describe experiment bayesian-optimization -n kubeflow
```

`describe`命令将返回关于实验的所有信息，例如配置、元数据和状态。从进度跟踪的角度来看，我们最感兴趣的是状态。参见以下示例：

| Status: | |
| :--- | :--- |
| Completion Time: | 2022-01-23T05:27:19Z |
| Conditions: | 实验历史 |
| Message: | 实验已创建 |
| Type: | |
| Message: | 实验正在运行 |
| Reason: | ExperimentRunning |
| Status: | False |
| Type: | Running |
| Message: | 实验成功，因为达到了最大试验次数 |
| Metadata of the current best trial: | ExperimentMaxTrialsReached |
| Reason: | True |
| Status: | Succeeded |
| Current Optimal Trial: | |
| Best Name: | bayesian-optimization-9h2bvq9 |
| Metrics: | |
| Latest: | 0.979001 |
| Max: | 0.979001 |
| Min: | 0.955713 |
| Name: | Validation-accuracy |
| Latest: | 0.992621 |
| Max: | 0.992621 |
| Min: | 0.906133 |
| Name: | Train-accuracy |
| Parameter Assignments: | 当前试验中使用的超参数值 |
| Name: | 1 |
| Value: | 0.01483662919100063 |
| Name: | num-layers |
| Value: | 3 |
| Name: | optimizer |
| Value: | sgd |
| Start Time: | 2022-01-23T05:13:00Z |
| Succeeded Trial: | 已完成试验的列表 |
| bayesian-optimization-5s59vwfc |
| bayesian-optimization-r8lnnv48 |

## C.2 快速上手 Katib

```bash
bayesian-optimization-9h25bvq9
```

```
Trials:
12
Trials Succeeded:
12
```

以下是对上述示例响应的几个解释：在之前的示例中，

- *Status/conditions*（状态/条件）——显示当前和之前的状态。我们看到实验经历了三个状态：创建、运行和成功。从消息中，我们知道实验完成是因为消耗训练预算——最大试验次数。
- *Current optimal trial*（当前最优试验）——显示“最佳”试验和使用的超参数值。它还显示了目标指标的状态。随着实验的进行，这些值将不断更新，直到实验中的所有试验完成，我们获取`status.currentOptimalTrial`。
- *parameterAssignment*（超参数值分配）——最终结果。

### C.2.7 第 7 步：故障排除

如果存在试验，我们可以运行以下命令检查试验作业的错误日志。失败的 HPO 示例所示：

```bash
> % k describe trial bayesian-optimization-mnist-pytorch-88c9rdjx \
-n kubeflow
```

```
Name:
bayesian-optimization-mnist-pytorch-88c9rdjx
Spec:
Parameter Assignments:
Name:
lr
Value:
0.010547476197421666
Name:
num-layers
Value:
3
Name:
optimizer
Value:
trl
```

```
Status:
Completion Time: 2022-01-23T06:23:50Z
Conditions:
Message: 试验失败。Job message: 任务达到了指定的退避限制
Reason: TrialFailed. Job reason: BackoffLimitExceeded-Failure
```

从返回的数据中，我们可以看到试验中使用的超参数值以及相关的错误信息。

# Kubernetes 集群

![](img/fig_kubernetes_cluster.png)

图 C.2 Kubernetes 控制器/算子（controller/operator）模式运行一个无限循环，监控某些 Kubernetes 资源的实际状态（右侧）和期望状态（左侧），并尝试将其实际状态调整为期望状态。

从这些核心组件的名称可以看出，它们的实现都遵循 Kubernetes 控制器模式。除了控制器之外，Katib 还定义了一组 CRD 对象（spec）来与这三个控制器协同工作。例如，实验规范（experiment spec）是一种 CRD 类型，它定义了 HPO（超参数调优）实验的期望状态，并作为向实验控制器的输入请求。

如图 C.3 所示，作为数据科学家 Alex 在与 Katib 交互时可能会遵循典型的工作流。主要步骤列在下文中。

![](img/fig_katib_workflow.png)

图 C.3 Katib 系统设计图和用户工作流

# 附录 C 在 Kubeflow 上创建 HPO 服务

第 1 步：创建实验请求
在第 1 步中，Alex 使用客户端（如 Katib SDK、Katib Web UI 或`kubectl`命令）创建一个实验 CRD 对象。该实验包含了所有的 HPO 实验定义，例如训练算法、超参数及其搜索空间、HPO 算法以及试验预算。

实验控制器（组件 A）定期调用所有的实验 CRD 对象。对于每个实验 CRD 对象，它会创建声明的建议（suggestion）CRD 对象和试验（trial）CRD 对象。简言之，实验控制器产生实际资源以实现实验 CRD 中的期望状态。此外，它会在实验 CRD 对象中更新运行时状态，以便 Alex 能够实时查看试验超参数和实验的执行状态。

一旦 Alex 在第 1 步创建了实验，Katib 会为 Alex 的实验部署一个 HPO 算法建议服务（组件 D），以便运行所需的 HPO 算法。在该建议服务中，实验 CRD 对象中的 HPO 搜索算法（库）被加载并通过 gRPC 接口暴露，允许建议控制器与其通信并请求建议的超参数。

第 2 步：获取下一个试验超参数
当实验控制器在第 2 步找到 Alex 的实验 CRD 对象时，它会创建一个建议 CRD 对象作为建议控制器（组件 B）的输入请求。超参数及其值在该建议 CRD 对象中指定，还包括搜索算法和建议数量。

随后，建议控制器调用在第 1 步中创建的建议算法服务来计算建议的超参数值。此外，建议控制器在建议 CRD 对象中维护建议超参数值的历史记录。

第 3 步：创建试验请求
作为第 3 步的一部分，在建议控制器提供一组试验超参数值后，实验控制器（组件 A）创建一个试验 CRD 对象以启动模型训练试验。试验使用建议服务（组件 D）计算出的超参数值集运行。

第 4 步：启动训练任务
在第 4 步中，试验控制器（组件 C）读取新创建的试验 CRD 对象（第 3 步创建）并创建一个 Job CRD 对象。有多种类型的 TrialJob 对象，包括 Kubernetes、TF 任务和 MXNet 任务。对于每个任务，Kubeflow (https://kubeflow.org/docs/components/training/) 都提供了一个专用的训练算子来执行，例如 PyTorch 训练算子或 TensorFlow 训练算子（组件 E）。

在检测到第 1 步中新创建的 Trial CRD 对象后，训练算子（组件 E）创建 Kubernetes Pod，根据训练任务中定义的超参数执行训练镜像。Alex 的 HPO 实验的训练试验将由 PyTorch 训练算子运行，因为他的代码是用 PyTorch 编写的。

# 第 5 步：返回试验结果

随着模型训练开始，指标收集侧容器（Kubernetes Pod 中的一个 Docker 容器）在第 5 步收集训练指标并报告到 Katib 存储（一个 MySQL 数据库）。使用这些指标，试验控制器（组件 C）将试验执行更新到试验 CRD。当实验控制器注意到试验 CRD 的最新更改时，它会读取更改并更新实验 CRD 对象，使实验具有最新状态。最新状态通过这种方式聚合到实验对象中。

HPO 工作流本质上是一个试验循环。为了在 Katib 中处理 Alex 的 HPO 请求，此工作流中的第 2、3、4、5 步会不断重复，直到满足退出条件。Alex 可以在整个 HPO 执行过程中检查实验 CRD，以获取 HPO 的及时执行状态，包括已完成或失败的试验数量、模型训练指标以及当前的超参数值。

> 使用 CRD 对象存储 HPO 执行数据有两个主要优势。首先，可以轻松地访问实验状态信息。例如，你可以使用 Kubernetes 命令（如`kubectl describe experiment [trial suggestion]`）在几秒钟内获取实验、试验和建议的中间数据和最新状态。其次，CRD 对象有助于提高 HPO 实验的可靠性。当 Katib 服务宕机或训练算子失败时，我们可以从失败的地方继续执行 HPO，因为这些 CRD 对象保留了 HPO 的执行历史。

# C.4.3 用于分布式训练的 Kubeflow 训练算子

Katib 默认训练算子——Kubernetes job 运算符——仅支持单 Pod 训练；它为实验中的每个试验启动一个 Kubernetes Pod。为了支持分布式训练，Kubeflow (https://kubeflow.org/docs/components/training/) 提供了...

在检测到第 1 步中新创建的 Trial CRD 对象后，训练算子（组件 E）创建 Kubernetes Pod，根据训练任务中定义的超参数执行训练镜像。Alex 的 HPO 实验的训练试验将由 PyTorch 训练算子运行，因为他的代码是用 PyTorch 编写的。

# C.5 添加新算法

从 C.2 我们知道 Katib 以独立的建议/试验服务运行不同的算法。当实验创建时，Katib 为选定的算法创建服务。这种机制使得在 Katib 中添加新算法变得简单，并与现有算法协同工作。为 Katib 添加新算法，我们需要执行以下三个步骤。

# 第 1 步：实现 Katib API

首先，我们需要实现建议接口。该接口是通过 gRPC 定义的，因此你可以用任何喜欢的语言来实现。该接口的详细定义可以从 mng.bz/xdW 找到，参见以下代码：

```
service Suggestion {
  rpc GetSuggestions(GetSuggestionsRequest)
```

# C.4.4 代码阅读

虽然 Katib 有一个巨大的仓库 (https://github.com/kubeflow/katib)，但阅读它并不困难。

所有的 Katib 核心组件都用 controller 编写：`experiment_controller`、`trial_controller` 和 `suggestion_controller`。它是为了

你可以在`pkg/controller.vibetal/experiment_controller.go`找到实验控制器，在`pkg/controller.vibetal/suggestion_controller.go`找到建议控制器，在`pkg/controller/vibetal/trial_controller.go`找到试验控制器。记得从`reconcile`函数开始。

# DEBUG

Katib 核心应用程序（`katib-controller`）作为控制台应用程序运行。该控制台程序没有 UI 或 Web 代码，只有纯逻辑，其本地调试设置非常简单。要调试 Katib，首先设置你的 Kubernetes 集群并在本地运行 Katib 带有断点，然后通过创建一个测试实验来启动过程——例如`kubectl apply -f test_experiment.yaml`。`reconcile`函数中的断点将被触发，你可以从这里探索代码。

要设置本地开发环境，请遵循 Katib 的开发者指南。

> 注意 Katib 是一个生产级的 HPO 工具。它以高可靠性和稳定性运行。但为了日常操作它，我们需要阅读其源代码以理解其行为，以便在执行偏离脚本时知道如何引导它。通过遵循 C.2 中的工作流并阅读每个控制器的`reconcile`函数，你可以在几小时内对 Katib 有很好的理解。

# 附录 C 使用 Kubeflow Katib 创建 HPO 服务

```python
returns (GetSuggestionsResponse);
rpc ValidateAlgorithmSettings(ValidateAlgorithmSettingsRequest)
returns (ValidateAlgorithmSettingsResponse);
```

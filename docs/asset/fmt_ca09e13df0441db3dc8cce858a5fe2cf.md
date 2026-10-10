
在此示例中，该规范将创建一个参数服务器（用于跨不同容器聚合模型参数）的副本，以及两个 worker（运行模型训练循环并与参数服务器通信）的副本。运算符将根据规范处理 TFJob 对象，将带有实际运行的服务和 Pod 的 TFJob 对象保留在系统中，并将实际状态替换为预期状态。你可以使用 `kubectl apply -f <TFJob specs template>` 提交训练作业，并使用 `kubectl get tfjob` 命令获取 TFJob 的状态。

作为一名数据科学家，你可以使用 `kubectl` 工具提交 Kubernetes 训练作业或 Kubeflow 训练作业，也可以在你的 Jupyter notebook 环境中使用 Python (SDK) 提交。例如，TFJob 对象有一个名为 `kubeflow.tfjob` 的 Python SDK，而 Kubernetes 也有一个名为 `kubernetes.client` 的客户端 SDK，用于从你的 Python 代码与 Kubernetes 和 Kubeflow 环境进行交互。你还可以使用 Kubeflow Pipeline 组件调用训练作业，我们将在稍后的 Kubeflow 流水线部分介绍这一点。

### 在模型注册表中注册模型

模型注册表（model registry）是模型管理和治理中的重要组件，它是模型训练阶段与模型部署阶段之间的枢纽。在 ML 平台中实现模型注册表有多种开源选项，在本节中，我们将查看用于模型管理的 MLflow 模型注册表。

### MLflow 模型注册表

MLflow 是一个开源 ML 平台，旨在管理 ML 生命周期的各个阶段，包括实验管理、模型管理、可复现性以及模型部署。它包含以下四个主要组件：

- 实验跟踪（Experiment tracking）
- ML 项目打包（ML project packaging）
- 模型打包（Model packaging）
- 模型注册表（Model registry）

MLflow 的模型注册表组件为保存的模型提供了中心模型仓库。它记录了模型详情，如模型血缘、模型版本、注释和描述，还记录了模型从测试（staging）到生产（production）的状态转换（模型状态的状态被描述得很清楚）。

要在团队环境中使用 MLflow 模型注册表，你需要设置一个带有数据库作为后端的 MLflow 跟踪服务器以及模型构产物的存储。MLflow 提供了 UI 和 API 来与其核心功能（包括其模型注册表）交互。一旦模型在模型注册表中注册，你就可以通过 UI 或 API 添加、修改、更新、转换或删除模型。下图显示了 MLflow 跟踪服务器及其关联模型注册表的架构设置：

![](img/bd21298357d8484151447cff0b2f138b_210_0.png)

图 7.2 – MLflow 跟踪服务器和模型注册表

MLflow 模型注册表的主要缺点之一是它不支持用户权限管理，因此任何访问跟踪服务器的用户都能访问并管理注册表中的所有模型。将实现一个外部权限层来管理用户对注册表中不同资源的访问。MLflow 跟踪服务器也不提供内置的身份验证支持，因此需要一个外部身份验证服务器（如 Nginx）来提供身份验证支持。

### 使用模型服务提供模型服务

在模型训练并保存后，你可以使用它来生成预测。然而，对于复杂的推理需求，你需要考虑专门的推理基础设施。现在，让我们来看看几种推理框架。

### Gunicorn 和 Flask 推理引擎

对于复杂的推理需求，我们需要考虑一些开源的推理框架。`Gunicorn` 和 `Flask` 通常用于构建自定义推理框架。下图（图 7.3）显示了使用 Flask 和 Gunicorn 的典型架构：

![](img/bd21298357d8484151447cff0b2f138b_210_0.png)

图 7.3 – 使用 Flask 和 Gunicorn 的推理架构

Flask 是一个基于 Python 的微框架框架，用于快速构建应用。它是轻量级的，几乎没有外部依赖。通过 Flask，你可以定义不同的路由并关联处理函数来处理调用。为了处理预测请求，Flask 应用会将模型加载到内存中。Flask 自带 Web 服务器，但它的扩展性不好，因为一次只能支持一个请求。

这就是 Gunicorn 发挥作用的地方。Gunicorn 是用于托管应用（如 Flask 应用）的 Web 服务器，它可以并行处理多个请求并高效地分配流量。当它接收到 Web 请求时，会调用托管的 Flask 应用。

除了提供预测服务外，企业推理引擎还需要处理流量（如 SSL/TLS 流量），以及在多个服务器的情况下进行负载均衡。这就是 Nginx 可以作为多个服务器的负载均衡器并处理流量的地方，这样服务器就不需要处理它。

基于 Flask/Gunicorn 的推理架构可以是托管简单模式的良好选择。但对于更复杂的模式，例如提供不同版本的模型、A/B 测试或大型模型推理，这种架构将具有局限性。Flask/Gunicorn 架构还需要自定义代码（如 Flask 应用）才能工作，因为它没有提供对模型的内置支持。

接下来，让我们回顾一些专门的模型服务框架，并看看它们与自定义 Flask 推理引擎有何不同。

### TensorFlow Serving 框架

TensorFlow Serving 是一个生产级的开源模型服务框架，并为通过 RESTful 端点提供 TensorFlow 模型提供了开箱即的支持。它管理模型服务的模型生命周期，并允许通过单个端点访问版本化和多个模型。它还内置支持金丝发布（canary deployments）。金丝发布允许你部署模型以支持部分流量。

![](img/bd21298357d8484151447cff0b2f138b_213_0.png)

图 7.4 – TensorFlow Serving 架构

API handler 为 TensorFlow Serving 提供 API。它带有一个内置的轻量级 HTTP 服务器，用于提供基于 RESTful 的 API 请求。它还支持 `gRPC`（一种远程过程调用）流量。gRPC 是一种常用且快速的网络协议，但比使用 REST 协议更复杂。TensorFlow Serving 有一个名为 `servable`（可服务对象）的概念，指的是处理任务的实际对象，例如模型推理或查找表。例如，一个训练好的模型被表示为一个 `servable`，它可以包含一个或多个算法以及查找表或嵌入表。API handler 使用 servable 来满足客户端请求。

`model manager`（模型管理器）管理 servables 的生命周期，包括加载 servables、提供 servables 以及卸载 servables。当需要 servable 来执行任务时，模型管理器为客户端提供一个句柄用以访问 servable 实例。模型管理器可以管理多个版本的 servable。这允许逐步发布不同版本的模型。

`model loader`（模型加载器）负责从不同的源加载模型，例如 `Amazon S3`。当加载一个新模型时，模型加载器会通知模型管理器新模型的可用性，模型管理器将决定下一步应该做什么（例如卸载旧版本并加载新版本）。

TensorFlow Serving 可以扩展以支持非 TensorFlow 模型。例如，在其他框架中训练的模型可以转换为 ONNX 格式，并使用 TensorFlow Serving 进行模型服务。ONNX 是一种表示模型的常用格式，用于支持不同机器学习框架之间的互操作性。

## TorchServe 服务框架

`TorchServe` 是一个用于为 PyTorch 模型提供服务的开源框架。与 TensorFlow Serving 类似，TorchServe 通过其内置的 Web 服务器提供 REST API 来提供模型服务。具有多模型服务、模型版本控制、服务端请求批处理和内置监控等核心功能，TorchServe 可以大规模地处理生产工作负载。此外，无需编写自定义代码使用 TorchServe 托管 PyTorch 模型。TorchServe 自带一个用于托管模型的内置 Web 服务器。接下来的图（图 7.5）展示了 TorchServe 框架组件的架构：

![](img/bd21298357d8484151447cff0b2f138b_214_0.png)

图 7.5 – TorchServe 架构

推理 API 负责使用已加载的 PyTorch 模型处理来自应用程序的预测请求。它支持 REST 协议并提供预测 API，以及其他辅助 API，如健康检查和模型解释 API。推理 API 可以处理多个模型的预测请求。

模型产物（artifacts）被封装成单个归档文件，并存储在 TorchServe 环境内的模型存储中。你使用名为 `torch-archive` 的命令行界面 (CLI) 命令来封装模型。

TorchServe 后端从模型存储中将归档模型加载到不同的工作进程中。这些工作进程与推理 API 交互以处理请求并返回响应。

管理 API 负责处理管理任务，例如注册和注销 PyTorch 模型、检查模型状态以及扩展工作进程数量。管理 API 通常由系统管理员使用。

TorchServe 还对日志和指标提供了内置支持。日志组件记录访问日志和处理日志。TorchServe 指标收集一组系统指标，例如 CPU/GPU 利用率和自定义模型指标。

## KFServing 框架

TensorFlow Serving 和 TorchServe 是针对特定深度学习框架的独立服务框架。相比之下，KFServing 是一个支持不同机器学习模型的通用多框架模型服务框架。KFServing 使用 TensorFlow Serving 和 TorchServe 等独立模型服务框架作为后端模型服务器。它是 Kubeflow 项目的一部分，并提供了如下架构：

![](img/bd21298357d8484151447cff0b2f138b_215_0.png)

图 7.6 – KFServing 组件

作为一个通用的多框架模型服务解决方案，KFServing 提供了开箱用的用的服务器（也称为预测器），支持 TensorFlow、PyTorch、XGBoost 和 scikit-learn。KFServing 使用 REST 和 gRPC 协议提供服务。要部署模型，你只需要定义一个指向模型存储中模型的 YAML 规范。以下代码显示了如何使用 KFServing 部署 TensorFlow 模型：

```yaml
apiVersion: "serving.kubeflow.org/valpha2"
kind: "InferenceService"
metadata:
  name: "model-name"
spec:
  default:
    predictor:
      tensorflow:
        storageUri: <模型存储路径>
```

KFServing 具有转换器（transformer），允许在发送回调用客户端之前对负载进行自定义处理。有时，我们需要对模型提供解释，我们将涵盖更多关于可解释性的细节。KFServing 为生产部署设计，并提供一系列生产能力。其自动伸缩功能允许根据请求量扩展模型服务器。通过 KFServing，你可以部署默认模型和金丝模型并在它们之间分流。对于运营支持，KFServing 还内置监控功能（例如监控请求和延迟）。

## Seldon Core

Seldon Core 是另一种在 Kubernetes 上部署模型的多框架模型服务框架。与 KFServing 相比，Seldon Core 提供了丰富的模型服务功能，例如模型推理图。接下来的图展示了 Seldon Core 的核心组件：

![](img/bd21298357d8484151447cff0b2f138b_216_0.png)

图 7.7 – Seldon Core 模型服务框架架构

Seldon Core 为一些机器学习库提供了封装的模型服务器，包括用于 scikit-learn 模型的 SKLearn 服务器、XGBoost 模型、用于 TensorFlow 模型的 TensorFlow Serving 以及基于 MLflow 服务器的服务。你还可以为特定的服务需求构建自定义的服务容器并使用 Seldon Core 进行托管。

以下模板展示了如何使用 Seldon Core 使用 SKLearn 服务器部署模型。你只需要更改 modelUri 路径以指向云存储供应商（如 Google Cloud Storage、Amazon S3 或 Azure Blob 存储）上的保存模型。要使用示例进行测试，你可以将以下 modelUri 值更改为 Seldon Core 提供的示例 gs://seldon-models/sklearn/iris：

```yaml
apiVersion: machinelearning.seldon.io/v1alpha
kind: SeldonDeployment
metadata:
  name: sklearn
spec:
  name: sklearn-model
  predictors:
    - graph:
      children: []
        implementation: SKLEARN SERVER
        modelUri: <云存储上的模型路径>
  name: classifier
  name: default
  replicas: 1
```

Seldon Core 还支持用于模型服务的高级工作流（也称为推理图）。推理图功能允许你在单个推理线中使用包含不同模型和其他组件的图。推理图可以由多个组件组成：

- 用于不同预测任务的一个或多个机器学习模型
- 用于使用模式的流量路由管理，例如为了 A/B 测试将流量分到不同模型
- 用于合并多个模型结果的组件，例如集成组件
- 用于转换输入请求（例如执行特征工程）或输出响应（例如将数组格式转换为 JSON 格式）的组件

为了在 YAML 中构建推理图规范，你需要在 `seldondeployment` YAML 文件包含以下关键组件：

- 一个预测器（predictors）列表，每个预测器都有自己的 `componentSpecs` 部分，用于指定容器镜像等详细信息
- 一个描述每个 `componentSpecs` 部分中的组件是如何连接在一起的图表

以下示例模板展示了自定义部署的推理图，用于将流量分到两个不同版本的模型：

```yaml
apiVersion: machinelearning.seldon.io/v1alpha
kind: SeldonDeployment
metadata:
  name: canary-deployment
spec:
  name: canary-deployment
  predictors:
  - componentSpecs:
      spec:
        containers:
        - name: classifier
          image: <container uri to model version 1>
graph:
  children: []
  endpoint:
    type: REST
    name: classifier
    type: MODEL
  name: main
    replicas: 1
    traffic: 75
  componentSpecs:
  - spec:
```

# 构建 ML 平台的开源技术 201

```yaml
containers:
  name: classifier
  image: <container uri to model version 2>
graph:
  children: []
  endpoint:
    type: REST
name: classifier
  type: MODEL
name: canary
  replicas: 1
traffic: 25
```

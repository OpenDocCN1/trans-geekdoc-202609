


![](img/cc4299656808e62a294f1843a1e18e72_367_0.png)

## 图 13.7: CodeBuild–源

然后，在 **环境** 部分下，选择 **托管映像** 选项，并从下拉列表中将操作系统选择为 **Ubuntu**。它提供其他操作系统，如 Windows Server 和 Amazon Linux。在当前场景中，已选择 **aws/CodeBuild/standard:4.0** 映像。其余选择可保持默认。确保选择 **特权** 复选框，该选项允许您构建 Docker 映像。

以下图显示了 **环境** 部分所做的选择：

![](img/cc4299656808e62a294f1843a1e18e72_368_0.png)

图 13.8: CodeBuild–环境

之后，在 **构建规范** 部分下，选择 **使用构建规范文件**，如以下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_368_1.png)

图 13.9: CodeBuild–构建规范

最后，在 **日志** 部分下，选择 **Cloudwatch 日志**。这将上传构建输出日志到 Cloudwatch。这使您能够分析构建项目后生成的日志和输出。但是，这是可选的。在页面底部，单击 **创建构建项目** 按钮并完成配置过程。

## 将容器注册表访问权限附加到 CodeBuild 的服务角色

现在，您需要为 CodeBuild 的服务角色提供访问权限，以便它可以构建 Docker 容器映像。为此，请转到 **IAM 管理控制台 | 角色** 并选择 CodeBuild 服务角色。在当前场景中，它是 **CodeBuild-mlapp-cicd-service-role**。单击它，摘要页面将打开。单击 **附加策略**，然后搜索 **EC2ContainerRegistry** 并选择 **AmazonEC2ContainerRegistryFullAccess**。它提供对 Amazon ECR 资源的管理访问权限。如果未提供所需的访问权限，CodeBuild 将无法构建 Docker 映像。

以下图显示了允许 CodeBuild 服务角色的容器注册表访问权限：

![](img/cc4299656808e62a294f1843a1e18e72_369_0.png)

图 13.10: CodeBuild–服务角色

现在，转到 CodeBuild 的主页，并通过点击右上角的 **开始构建** 按钮手动执行构建阶段。构建状态将显示为 **进行中**。日志可在 **构建日志** 选项卡下查看。默认情况下，它将显示构建日志的最后 1000 行。构建阶段完成后，最新的容器映像应可在 Amazon Elastic Container Registry (ECR) 中使用。此外，测试报告应可在 **报告** 选项卡下查看，如以下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_370_0.png)

图 13.11: CodeBuild–测试报告

## Amazon Elastic Container Service (ECS)

Amazon Elastic Container Service (ECS) 是一种用于管理和运行 Docker 容器的容器编排工具。Amazon Elastic Container Service (ECS) 是 AWS 提供的完全托管的容器管理服务。在当前场景中，将使用带有 Fargate 模型的 ECS。它将负责管理集群和负载均衡。它还将确保应用程序正在运行。

让我们了解 Amazon Elastic Container Service (ECS) 中使用的术语：

- **任务定义**：任务定义允许您指定要使用的 Docker 映像、要暴露的端口、要分配的 CPU 和内存量、如何收集日志以及如何定义环境变量。这是一个蓝图，规定了 Docker 容器应如何启动。
- **任务**：任务类似于任务定义的 **实例**。它可以独立创建，也就是说，无需 Amazon ECS 集群。这将启动一个在其中运行应用程序的容器。如果因某些错误而停止或失败，它不会自动替换自己。
- **服务：** 服务负责创建和维护所需数量的任务始终处于运行状态。如果任何任务因某些错误而失败或停止，则 ECS 服务将用新任务替换该任务。它引用 **任务定义** 文件来创建任务。
- **集群：** 它是容器实例的逻辑分组。
- **容器：** 这是在任务实例化期间创建的 Docker 容器。

以下图类似于 Amazon Elastic Container Service (ECS) 架构。

![](img/cc4299656808e62a294f1843a1e18e72_371_0.png)

图 13.12: Amazon Elastic Container Service (ECS)–架构

## AWS ECS 部署模型

AWS ECS 部署模型可根据您的要求进行选择。让我们来看看 AWS Elastic Container Service (ECS) 主要为集群部署提供的模型。

### EC2 实例

**EC2（弹性计算云）** 是云中的虚拟机。首先，在集群中配置和部署 EC2 实例以运行容器。它提供了对实例的更精细控制。您可以根据要求选择实例。

如果您想执行以下操作，此模型是更好的选择：

- 连续运行容器化应用程序
- 对自动缩放配置有更好的控制
- 使用经典负载均衡器 (CLB) 分配工作负载
- 使用图形处理单元 (GPU)
- 使用弹性块存储 (EBS)
- 部署大型和复杂的应用程序

### Fargate

这是一种无服务器按需付费模型。您将根据所选的计算能力和使用时间付费。带有 Fargate 的 ECS 是一种用于运行基于 Docker 的容器而无需管理基础架构的容器编排工具。

如果您想执行以下操作，此模型是更好的选择：

- 偶尔或短时间运行任务
- 容器化应用程序应能够处理突发的传入流量峰值
- 使用应用程序和网络负载均衡器分配工作负载
- 从不同配置、常规维护和安全管理中节省时间

> 注意：在本章中，使用经典 UI。默认情况下，您可能会看到新 UI；但是，您可以切换回经典 UI。

从 Services 转到 Elastic Container Service：

Services | 所有服务 | 容器 | Elastic Container Service

首先，转到集群页面，并通过单击 **创建集群** 按钮创建 ECS 集群。AWS 提供用于创建集群的模板，以简化集群创建过程。在当前场景中，**仅联网 (AWS Fargate)** 被选为实例类型。在下一屏幕上，在 **集群配置** 下，需要提供 **集群名称**。在此场景中，它是 `mlapp-cluster`，如以下图所示：

### 创建集群

Amazon ECS 集群是任务或服务的逻辑分组。

### 集群配置

集群名称
mlapp-cluster
最多可包含 255 个字符。有效字符包括字母（大写和小写）、数字、连字符和下划线。

图 13.13: Amazon Elastic Container Service (ECS)–集群配置

然后，单击 **创建** 按钮，它将启动 ECS 集群。您将看到 ECS 集群已创建，类型为 Fargate，但没有运行的实例。

### 任务定义

之后，创建任务定义。转到 **任务定义** 页面并单击 **创建新任务定义**。在第 1 步中，选择类型为 **Fargate**。在第 2 步中，提供任务定义名称。在此例中，它是 **mlapp-cicd**。从下拉列表中选择 **任务角色 ecsTaskExecutionRole**，并将 **操作系统系列** 选择为 **Linux**，如以下图所示：

步骤 1：选择启动类型兼容性
步骤 2：配置任务和容器定义
配置任务和容器定义
任务定义指定任务中包含哪些容器以及它们如何相互交互。您还可以指定容器要使用的数据卷。了解更多
任务定义名称* mlapp-cicd
所需兼容性* FARGATE
任务角色 ecsTaskExecutionRole
网络模式 awsvpc
操作系统系列 Linux

图 13.14: Amazon Elastic Container Service (ECS)–任务定义

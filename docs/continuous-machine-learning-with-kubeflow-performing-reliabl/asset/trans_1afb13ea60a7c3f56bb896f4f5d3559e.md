
![](img/8f8a671916d96b455297952d0f37b96c_55_0.png)

图 1.15：Ingress yaml 文件

## 命名空间：

## 何时使用多个命名空间？

命名空间旨在用于环境中拥有众多用户分布在多个团队或项目中的场景。对于只有数个到数十个用户的集群，您完全不需要创建或考虑命名空间。 当您需要它们提供的功能时再开始使用命名空间。命名空间为名称提供作用域。资源名称需要在命名空间内唯一，但在命名空间之间不必唯一。命名空间不能相互嵌套，每个 Kubernetes 资源只能位于一个命名空间中。

Kubernetes 从四个初始命名空间开始：

没有其他命名空间的对象的默认命名空间。

由 Kubernetes 系统创建的对象的命名空间。

该命名空间由系统自动创建，可供所有用户（包括未通过身份验证的用户）读取。该命名空间主要保留用于集群使用，以防某些资源需要在整个集群中公开可见和可读。该命名空间的公开性仅为一种约定，而非强制要求。

该命名空间用于与每个节点关联的租约对象，可在集群扩展时提高节点心跳的性能。

![](img/8f8a671916d96b455297952d0f37b96c_57_0.png)

图 1.16：命名空间概念

## 1.4 Kubeflow 用于 ML 部署编排的介绍

Kubeflow 是一个开源的 Kubernetes 原生平台，用于开发、编排、部署和运行可扩展且可移植的 ML 工作负载。它有助于支持 ML 工作流生命周期中的可重复性和协作，使您能够管理 ML 管道的端到端编排，在多个或混合环境中运行工作流，并帮助您在不同工作流中重用构建块。

![](img/8f8a671916d96b455297952d0f37b96c_58_0.png)

图 1.17：Kubeflow 架构

Kubeflow 还为您的 ML 工作流提供可视化和协作支持。

**Kubernetes** Pipeline 服务调用 Kubernetes API 服务器以创建运行管道所需的 Kubernetes 资源（CRD）。

**Python** 您使用 Kubeflow Pipelines **领域特定语言**创建组件或指定管道

**DSL** DSL 编译器将您的管道 Python 代码转换为静态配置（YAML）。

**Pipeline** 您调用 Pipeline 服务根据静态配置创建管道运行。

**编排** 一组编排控制器执行完成管道所需的容器。容器在虚拟机上的 Kubernetes Pod 中执行。一个示例控制器是 **Argo Workflow** 控制器，它编排任务驱动的工作流。

**Pipeline web** Pipeline Web 服务器从各种服务收集数据以显示相关视图——当前正在运行的管道列表、管道执行历史、数据工件列表、单个管道运行的调试信息以及单个管道运行的执行状态。

**Pipeline** 您调用 Pipeline 服务根据静态配置创建管道运行。

**持久性代理和 ML** Pipeline 持久性代理监视由 Pipeline 服务创建的 Kubernetes 资源，并将这些资源的状态持久化到 ML 元数据服务中。

**工件** Pod 存储以下两种类型的数据：

实验、作业、管道运行和单个标量指标。指标数据会被汇总以便排序和过滤。Kubeflow Pipelines 将元数据存储在 MySQL 数据库中。

管道包、视图和大规模指标（时间序列）。使用大规模指标来调试管道运行或调查单个运行的性能。Kubeflow Pipelines 将工件存储在类似 Minio 服务器或 Cloud Storage 的工件存储中。

**概念概述** 您可以将工作流部署到各种云、本地和本地部署平台用于实验和生产使用。

![](img/8f8a671916d96b455297952d0f37b96c_61_0.png)

图 1.18：Kubeflow 概览功能

Kubeflow 是 Kubernetes 的 ML 工具包。前面的图表展示了 Kubeflow 作为在 Kubernetes 之上布置 ML 系统组件的平台。

## 1.5 Kubeflow 组件

在本节中，让我们探索 Kubeflow 介绍的一些组件，我们将在即将到来的章节中详细介绍这些组件。

### 1.5.1 中央仪表板

Kubeflow UI 包括以下内容：

- Home，Kubeflow 组件之间导航的中央仪表板。
- Pipelines，用于 Kubeflow Pipelines 仪表板。
- Notebook Servers，用于 Jupyter 笔记本。
- Katib，用于超参数调优。
- Artifact Store，用于跟踪工件元数据。
- Manage Contributors，用于在 Kubeflow 部署的命名空间之间共享用户访问权限。

Kubeflow 中央 UI 可通过以下 URL 访问：

https://.endpoints..cloud.google/

![](img/8f8a671916d96b455297952d0f37b96c_64_0.png)

图 1.19：Kubeflow 仪表板

### 1.5.2 注册流程

根据 Kubeflow 集群的设置，您在首次登录 Kubeflow 时可能需要创建命名空间。命名空间有时称为配置文件或工作组。

对于支持单用户隔离的 Kubeflow 部署，Kubeflow 集群没有命名空间角色绑定。

![](img/8f8a671916d96b455297952d0f37b96c_65_0.png)

图 1.20：Kubeflow 配置文件设置

单击“开始设置”按钮并按照屏幕上的说明设置您的命名空间。您命名空间的默认名称是您的用户名。

![](img/8f8a671916d96b455297952d0f37b96c_66_0.png)

图 1.21：Kubeflow 命名空间

### 1.5.3 元数据

元数据项目的目标是帮助 Kubeflow 用户通过跟踪和管理工作流产生的元数据来理解和管理他们的 **机器学习** 工作流。完成以下步骤：

- 在浏览器中转到 Kubeflow。
- 在左侧导航面板上单击 Artifact Store。

工件屏幕打开并显示您的工作流记录的所有元数据事件的项目列表。您可以单击每个项目的名称查看详细信息。

![](img/8f8a671916d96b455297952d0f37b96c_67_0.png)

图 1.22：Kubeflow 元数据

### 1.5.4 Jupyter Notebook 服务器

单击 Kubeflow UI 左侧面板上的 **Notebook Servers** 以访问随 Kubeflow 部署的 Jupyter notebook 服务：

![](img/8f8a671916d96b455297952d0f37b96c_68_0.png)

图 1.23：Kubeflow Jupyter Notebook

![](img/8f8a671916d96b455297952d0f37b96c_68_1.png)

图 1.24：Kubeflow Jupyter Notebook 仪表板

### 1.5.5 Katib

使用 Katib 对您的 ML 模型的超参数和架构进行自动调优。有关更多信息，请访问以下链接：
https://www.Kubeflow.org/docs/components/hyperparameter-tuning/overview/

![](img/8f8a671916d96b455297952d0f37b96c_69_0.png)

图 1.25：Kubeflow katib 仪表板

## 1.6 在 GCP Kubeflow 设置中入门

您必须拥有一个活跃的 GCP 账户，在练习本章时，运行 Kubernetes 集群可能会产生费用。

我假设具备基本的 Kubernetes 和 Docker 知识是必须的。

*如果您使用的是 GCP 免费套餐或附带 300 美元赠金的 12 个月试用期，请注意您无法运行默认的 GCP Kubeflow 安装，因为免费套餐提供的资源不足。您需要升级到付费账户。*

请按照以下链接设置 GCP 项目，并确保在信用卡免费额度用完后开始向您收费，并启用我们工作所需的所有 API：
https://v1-0-branch.Kubeflow.org/docs/gke/deploy/project-setup/

为您的 Kubeflow 部署创建 **Google Cloud Platform** 项目。

确保您拥有该项目的 Owner 角色。

确保已为您的项目启用计费。

前往 GCP 控制台将确保指定的 API 已启用：

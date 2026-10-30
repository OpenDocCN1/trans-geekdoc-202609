# KUBEFLOW 持续机器学习 TFX、SageMaker 和 Kubernetes 的功能实现可靠的 MLOps




## 致敬

*我深爱的父母和家人*

## 关于作者

**Aniruddha Choudhury** 在提供人工智能开发解决方案、MLOPS Kubeflow、多云 GCP、AWS、Azure 方面拥有 5 年的 IT 专业经验，并热衷于在机器学习和深度学习中提供数据科学和数据工程的复杂解决方案。他始终在寻找新的机会，以应对高影响力业务问题的新维度挑战，成为未来雇主的宝贵贡献者。

目前他在 Publicis Sapient 担任高级数据科学家（全栈 MLOPS）已有 2 年。之前他在 Incture Technology 工作过，在此之前他在 Wells Fargo Bank 负责多个业务线的多样化金融产品 AI 解决方案。

作为一名技术极客，Aniruddha 始终热衷于跨维度知识的工作。他在 Kaggle 和 Google 数据项目上工作，构建统计和机器学习 NLP 模型，涵盖端到端的数据整理和准备、构建具有可视化和预测/文本/图像分析的模型框架，以及使用 Amazon AWS 和 Microsoft Azure DataBricks 云、Apache Scala 和 Spark 进行数据处理，并在各种形式的数据中寻找模式。他热衷于在数据科学领域分解复杂问题，并利用深度学习和机器学习找到解决方案。他还在 TensorFlow、Keras 和 Pytorch 等深度学习框架上工作。作为个人，Aniruddha 始终相信不断学习新技能并走少有人走的路。他喜欢让自己了解技术世界，并始终在尝试一些新创新。

他精通构建人工智能解决方案，并从研究论文中发现复杂模式，以获得当前产品开发的最佳解决方案，同时具备自我创新思维。

## 关于审阅者

**Rajdeep Kumar** 是其中一家顶尖咨询公司的首席数据科学家。他拥有 BITS Pilani 的数据科学研究生学位，是 IIIT Bangalore 的校友。他在 IT 行业拥有超过 11 年的工作经验。在其职责范围内，他推动并贡献数据科学活动，同时定义路线图、规划范围并指导团队成员。他擅长推导和生产化端到端的 ML 解决方案，以推动业务增长并对关键业务 KPI 产生积极影响。

## 致谢

在撰写本书期间，有几个人我想要感谢他们持续不断的支持。首先，也是最重要的是，我要感谢我的父母不断鼓励我撰写本书——如果没有他们的支持，我不可能完成这本书。我要感谢我的朋友 Dr. Someswar Deb，他在 Novartis 担任 MSL，为我提供了持续的支持和动力。

我感谢来自我的公司提供的旅程，他们在我职业生涯的学习过程中给予了我支持。

感谢所有隐性的支持。我谨此感谢 Publicis Sapient 的高级董事 Mr. Abhishek Kumar，他在部署相关事宜上提供了善意的专业帮助，这对本书很有帮助。我要感谢 Publicis Sapient 的高级经理 Sivaram Annadurai，他在机器学习实时项目的技术和业务方面给予了我持续的动力。

我还要感谢 BPB Publications 的团队，他们足够支持我，给了我相当长的时间来完成本书的第一部分，并允许我分多部分出版本书。由于图像处理是一个庞大且非常活跃的研究领域，在一本书中深入研究不同类别的问题是不可能的，尤其是不能使其过于庞大。

## 前言

本书重点介绍在 Google Cloud 平台上使用 Kubeflow 部署和产品化机器学习项目的 DevOps 和 MLOps。作者认为，在这个机器学习时代，根据福布斯的研究，许多公司未能在实时中实现 AI/ML 项目的生产化。这是对当今从事 DevOps/MLOps 团队的实践者来说具有说服力和相关性的内容，因为该领域仍在不断变化。因此，今天的许多机器学习平台在管理机器学习工作流的架构和解决方案空间方面采用不同的方法。Kubernetes 和 Kubeflow 的核心概念及其架构教会了我们如何处理并使用 Kubeflow 将您的 AI/ML 项目从训练到服务以规模化方式在生产中进行。

本书首先带您了解当今机器学习基础设施的 Kubernetes 和 Kubeflow 架构。然后我们概述了使用 TensorFlow 训练服务与 Kubeflow 部署各种 AI/ML 用例的核心原则，并解释 Kubernetes 如何解决出现的一些问题。我们进一步展示了如何将 TFX 与 Kubeflow 结合使用，以及使用可解释 AI 和 What-if Tool 来确定公平性和偏差。我们学习了针对不同用例的 Kubeflow KF serving 的各种服务技术框架。在此之后，我们查看了在 Streamlit 中构建基于计算机视觉的 UI 样本，并在 Google Cloud Platform Kubernetes 和 Heroku 部署中部署该 UI。

本书分为 8 章。它们涵盖了 Kubernetes、Kubeflow 基础知识、使用 Kubeflow 的高级部署项目、AWS Sagemaker 部署以及使用实时示例的可解释 AI，用于部署和 Docker 容器创建以及在 Kubeflow 中构建管道。在使用 Kubeflow 进行机器学习部署方面，学习者会产生更多兴趣。

详情如下：

# 第 1 章：

在本章中，我们将学习 Kubeflow 的完整功能、其工作原理及其需求。我们还将学习 Kubernetes 的架构功能，例如服务、Pod、Ingress 等。我们将学习构建 Docker 镜像并了解其工作原理。在这里，我们将看到 Kubeflow 的组件优势，我们将在接下来的章节中使用。然后，我们将继续在 Google Cloud 平台上完成 Kubeflow 的完整设置和 Jupyter Notebook 设置。我们有一个可选项目——如何创建持久卷声明并将其附加到文件存储以保存您的代码和数据。

# 第 2 章：

在本章中，我们将构建一个端到端的 TensorFlow 分类模型部署，使用 Kubeflow 编排，其中包括在 GCP 的 Kubernetes 集群中部署 Kubeflow，使用 Docker 和 Kubeflow SDK 为模型构建管道组件，然后使用 KF serving 为预测提供服务以获得端点。我们还将在 Grafana 仪表板中跟踪我们服务流量的端点的监控和性能。



第 3 章：在本章中，我们将使用 OpenCV 操作构建端到端的 TensorFlow 计算机视觉模型，并使用 Kubeflow 编排进行部署，其中包括在 GCP 的 Kubernetes 集群中部署 Kubeflow，使用 Docker 和 Kubeflow SDK 构建模型的流水线组件，然后使用 KF Serving 为预测提供端点。我们随后将在 Grafana 仪表板中跟踪监控和性能。

第 4 章：在本章中，我们将使用 TFX 的帮助构建端到端的结构化数据分类模型并使其准备好投入生产，并使用 TF Serving 提供模型输出以获取预测。我们还将构建 TensorFlow 生态系统模型并使用 Tensorboard 和 Fairness 可视化评估。然后，我们将了解各种 TFX 组件，如 TFT、TFMA、TFDV 等。之后，我们将在 Google Cloud 上创建一个 Kubeflow Pipeline。

第 5 章：在本章中，我们将使用酒店预订数据集开展分类模型，训练 TensorFlow 和提升模型，并使用 Tensorboard、Shap 和 What-if 产品可视化我们模型结果的先进解释。

第 6 章：在本章中，我们将构建端到端的 Light Model 框架，并在 Weights and Biases（Wandb）工具中监控模型性能。在 Weights and Biases 中，我们将看到每个迭代的实时模型 RMSE 图表和并行坐标超参数性能图表。接下来，我们将在 Google Cloud 平台内的 Kubernetes 集群中使用 KF Serving 部署模型。我们将提供模型端点，该端点将用于预测并在 Grafana 仪表板中进行监控，例如相对于时间的模型请求率以及 CPU 和 GPU 消耗。

第 7 章：在本章中，我们将开展 Housing Price Sales 数据集项目，在 Amazon SageMaker 云环境中完全运行、评估和部署模型，并使用 S3 进行数据存储。我们还将使用内置容器算法 XG-Boost 进行模型构建，以便能够端到端地了解 SageMaker 模型构建框架的架构。

第 8 章：在本章中，我们将为计算机视觉模型构建端到端 Web 应用程序，并使用 Streamlit 构建 UI。我们将学习许多用于图像的 Open CV 模型，如裁剪、更改像素等。接下来，我们将使用 Heroku Container Registry 或 Kubernetes 集群作为服务应用程序在 Google Cloud 中托管 Web 应用程序。

## 下载代码包和彩色图片：

请按照链接下载本书的代码包和彩色图片：

https://rebrand.ly/bfbaf6

## 勘误

我们对 BPB Publications 的工作感到无比自豪，并遵循最佳实践以确保内容的准确性，为我们的订阅者提供愉快的阅读体验。我们的读者是我们的一面镜子，我们利用他们的反馈来反映并改进出版过程中可能出现的任何人为错误。为了让我们保持质量并帮助联系可能因任何不可预见的错误而遇到困难的读者，请写信给我们：

errata@bpbonline.com

BPB Publications 家族高度赞赏您的支持、建议和反馈。

您知道 BPB 为每本出版的书籍提供电子书版本，提供 PDF 和 ePub 文件吗？您可以在 www.bpbonline.com 升级到电子书版本，作为印刷书籍客户，您有权享受电子书的折扣。有关更多详细信息，请联系我们 business@bpbonline.com。

在您还可以阅读一系列免费技术文章，订阅一系列免费新闻通讯，并获得 BPB 书籍和电子书的独家折扣和优惠。

## BPB 正在寻找像您这样的作者

如果您有兴趣成为 BPB 的作者，请访问 www.bpbonline.com 并立即申请。我们已与数千名开发人员和技术专业人士合作，就像您一样，帮助他们与全球技术社区分享他们的见解。您可以进行一般申请，申请我们正在招聘作者的特定热门主题，或提交您自己的想法。

本书的代码包也托管在 GitHub 上 如果代码有更新，它将被更新到现有的 GitHub 仓库。

我们还有来自我们丰富的书籍和视频目录的其他代码包 在这里查看！

## 盗版

如果您在互联网上发现我们作品的任何非法副本，无论以何种形式，我们将非常感谢您提供位置地址或网站名称。请通过 business@bpbonline.com 联系我们并附上材料的链接。

## 如果您有兴趣成为作者

如果您在某个主题上有专业知识，并且有兴趣撰写或为一本书做出贡献，请访问

## 评论

请留下评论。读完并使用本书后，为什么不在您购买的网站上留下评论呢？潜在读者可以然后查看并使用您公正的意见来做出购买决定，我们 BPB 可以了解您对我们产品的看法，我们的作者可以看到您对他们书籍的反馈。谢谢！

有关 BPB 的更多信息，请访问

## 索引
# Kubeflow 和 Kubernetes 云架构介绍

在本章中，我们将了解 Kubeflow 的完整功能，它是如何工作的，以及为什么我们需要 Kubeflow。我们还将学习 Kubernetes 的架构功能，如 service、pod、Ingress 等，以及如何构建 docker 镜像，以及它是如何工作的。在这里，我们将看到 Kubeflow 的优势组件，我们将在接下来的章节中使用它们。然后，我们将继续在 Google Cloud Platform 中完成 Kubeflow 的完整设置以及 Jupyter notebook 设置。我们有一个可选项目——如何创建 Persistent Volume Claim，并将其附加到 File store 以保存您的代码和数据。

## 结构

在本章中，我们将涵盖以下主题：

- Docker 理解
- Kubernetes 概念和架构
- Kubernetes 组件
- Kubeflow 编排用于 ML 部署的介绍
- Kubeflow 组件
- 在 GCP 中设置 Kubeflow
- Jupyter Notebook 设置
- **可选：** Jupyter Notebook 的 PVC 设置

## 目标

本章将帮助您学习以下内容：

Docker 和 Kubernetes 的核心理解，以及在云中使用的应用。

Kubernetes 和 Kubeflow 架构及其功能和优势。

Kubeflow 的组件以及如何在 Google Cloud Platform 中设置 Kubeflow IAP 集群。

用于设置 Jupyter notebook 的 CPU Docker 镜像，以及云中的 PVC 设置。

云。云。云。云。云。云。云。云。云。
云。云。云。云。云。云。云。云。云。
云。云。云。云。云。云。云。云。云。
云。云。云。云。云。云。
---
云。

## 1.1 Docker 理解

Docker 是一个平台，供开发人员和系统管理员使用容器构建、运行和共享应用程序。用于部署应用程序的容器称为容器化。为了部署应用程序，容器使事情变得更容易和灵活。

容器化变得越来越流行，因为容器具有以下功能：

我们可以将最复杂的应用程序容器化。

我们可以自动在数据中心跨区域分发容器副本的进程。

容器通过共享和利用主机内核，比虚拟机更高效。

由于其可移植性，我们可以在本地构建它们，部署到云端，并从任何地方运行它们。

此外，它们高度独立且封装，这使我们能够在不影响其他组件的情况下替换或升级任何组件。

在用户无需任何配置的情况下，它会对进程应用积极的隔离和限制。

## 镜像和容器：

从逻辑上讲，容器是一个正在运行的进程，具有一些额外的封装功能，这些功能适用于主机与它以及其他容器之间的隔离。最重要的是，每个容器都与其自己的私有文件系统交互，这称为容器隔离；Docker 镜像提供了该文件系统。因此，镜像包括运行应用程序所需的大多数东西——代码、运行时、依赖项以及所需的任何其他文件系统对象。

![](img/8f8a671916d96b455297952d0f37b96c_27_0.png)

图 1.1：Docker 架构

Docker 有两个概念，与其 VM 容器几乎相同，即镜像和容器的概念。一个

镜像，即将被执行的定义，就像操作系统镜像一样，对于给定的镜像，容器是运行的实例。

### 1.1.1 Dockerfile

要将我们的 Python 或任何语言代码在容器中运行，就是将其包装为 Docker 镜像的包，然后基于它运行一个容器。步骤如下所示：

![](img/8f8a671916d96b455297952d0f37b96c_29_0.png)

图 1.2：Docker 文件流程

接下来，为了生成 Docker 镜像，我们需要创建一个 Dockerfile，其中包含构建镜像所需的一组指令。然后 Dockerfile 由 Docker 构建器处理，生成 Docker 镜像。最后，通过简单的 Docker run 命令，我们可以使用 Python 服务创建并运行一个容器。

```
# set base image (host OS)
FROM python:3.8

# set the working directory in the container
WORKDIR /app

# copy the dependencies file to the working directory
COPY requirements.txt .

# install dependencies
RUN pip install -r requirements.txt

# copy the content of the local src directory to the working directory
COPY src/ .

# command to run on container start
CMD [ "python", "./server.py" ]
```

![](img/8f8a671916d96b455297952d0f37b96c_30_0.png)

![](img/8f8a671916d96b455297952d0f37b96c_30_1.png)

![](img/8f8a671916d96b455297952d0f37b96c_30_2.png)

图 1.3：Dockerfile 代码

让我们将此文件拆分为以下几行：

它使用带有标签 Python:3.8 的 Python 基础镜像，这是 Python 的特定版本。

然后，它创建一个工作目录，我们将把本地文件复制到该目录；在这里，我们创建了一个 app 文件夹并复制了包含 Python 库的 requirements 文件。

然后，我们使用 pip 命令安装了所有 Python 库。

接下来，我们使用 CMD，这是在容器启动时运行 Python 文件的命令。




![](img/8f8a671916d96b455297952d0f37b96c_31_0.png)

```
docker build -t imagename:tag .
```

镜像名称

镜像标签版本

Dockerfile 的当前位置

![](img/8f8a671916d96b455297952d0f37b96c_31_1.png)

```
docker run imagename:tag
```

在本地运行 Docker

![](img/8f8a671916d96b455297952d0f37b96c_31_2.png)

```
docker push imagename:tag
```

将构建的镜像推送到云或 DockerHub

图 1.4：Dockerfile 命令

现在，在终端中运行上述代码，将你在本地构建的镜像推送到云（GCP/AWS/AZURE）和 Docker Hub。

## 1.2 Kubernetes 架构

在本节中，我们将了解 Kubernetes 的工作原理，并学习其架构。

### 1.2.1 什么是 Kubernetes？

Kubernetes 是一个开源容器管理系统，被大型企业在多个动态行业中使用，以执行关键任务或任何编排任务。其部分功能包括以下内容：

-   它管理集群内的容器。
-   它部署应用程序并为其提供工具。
-   它根据需求扩展应用程序。
-   它管理现有容器化应用程序的变更。
-   它优化了容器下底层硬件复杂性的使用。
-   它使应用程序组件能够根据需要重启并在多个系统间迁移。

### 1.2.2 为什么需要 Kubernetes？

我们需要 Kubernetes 来管理容器，当我们使用微服务模式运行生产级环境并包含大量容器时。我们需要跟踪诸如健康检查、版本控制、扩展和回滚机制等功能。确保所有这些事物正常运行可能相当具有挑战性和令人沮丧。Kubernetes 为我们提供了在规模上部署容器的编排和管理能力。使用 Kubernetes 编排构建应用程序服务使我们能够跨多个容器扩展，并及时将这些容器调度到集群中，在不使用时扩展这些容器，并不时管理这些容器的健康状况。简而言之，Kubernetes 更像是一个主管理员，拥有许多下属（容器）。管理员所做的是维护下属需要做的事情。

### 1.2.3 Kubernetes 的优势是什么？

以下是 Kubernetes 的优势：

### 可移植且开源：

Kubernetes 可以在一個或多個公共云环境、虚拟机或裸机上运行容器，这意味着它可以部署在任何基础设施上。此外，Kubernetes 跨多个平台兼容，使多云策略成为高度灵活且可用的组件。

### 工作负载可扩展性：

Kubernetes 提供了以下用于扩展的有用功能：

**Horizontal Infrastructure** 在单个服务器级别运行以实现水平扩展。新的服务器可以轻松添加或删除。

我们可以根据 CPU 资源或其他应用指标的使用情况调整运行中的容器数量。

**Manual** 可以通过命令或界面手动扩展运行中的容器数量。

**Replication** 复制控制器确保集群中有指定数量的等效 Pod 处于运行状态。如果 Pod 过多，复制控制器可以删除多余的 Pod，反之亦然。

### 高可用性：

Kubernetes 可以处理应用程序和基础设施的可用性。它解决以下问题：

**Health** 通过不断检查节点和容器的健康状况，应用程序不会失败。Kubernetes 提供自愈和自动替换，如果 Pod 因错误而崩溃。

**Traffic Routing and Load** Kubernetes 的负载均衡器将负载分布到多个节点，使我们能够在偶发流量或批处理期间快速平衡资源。

### 专为部署而设计：

容器化能够加快构建、测试和发布软件的过程，有用的功能包括以下内容：

**Automated Rollouts and Rollbacks** 它可以在不中断服务的情况下处理新版本并更新我们的应用，同时在发布过程中监控健康状况。如果过程中出现任何故障，它可以自动回滚到上一个版本。

### Canary

因此，可以并行测试新部署的生产版本和上一个版本，即在扩大新部署规模的同时并行缩小上一个部署规模。

### 编程语言和框架

大多数编程语言和框架如 Java、Python 等都得到 Kubernetes 支持。如果应用程序能够在容器中运行，它也可以在 Kubernetes 中运行。

### Kubernetes 与有状态容器：

Kubernetes 的 StatefulSets 为处理有状态容器提供资源，如卷、稳定网络 ID、从 0 到 N 的序数索引等。卷是此类关键功能之一，使我们能够运行有状态应用程序。支持的两种主要卷类型如下：

### Ephemeral Storage

临时数据存储与 Docker 不同。在 Kubernetes 中，卷在 Pod 内运行的任何容器中都被考虑在内，数据存储在容器中。但是，如果 Pod 被杀死，卷会自动删除。

### Persistent

数据会保留终身。因此，当 Pod 死亡或移动到另一个节点时，该数据仍会保留，直到用户删除它为止。因此，数据存储在远程。

### 1.2.4 Kubernetes 如何工作？

集群是 Google Kubernetes Engine 的基础，代表你容器化应用程序的 Kubernetes 对象都运行在集群之上。在 GKE 中，集群至少包含一个控制平面和多个称为节点的工作机。这些控制平面和节点机器运行 Kubernetes 集群编排系统。

![](img/8f8a671916d96b455297952d0f37b96c_39_0.png)

图 1.5：Kubernetes 架构

### Master：

主节点是集群的控制元素。主节点具有以下三个部分：

**API** 通过 RESTful 接口提供 Kubernetes 功能并存储集群状态的应用程序。

调度器监视 API 服务器的新 Pod 请求。它与节点通信以创建新 Pod 并分配工作，同时分配资源或施加约束。

**Controller** 主节点上运行控制器的组件。它包括节点控制器、端点控制器、命名空间控制器等。

### Slave (Nodes)：

这些机器执行请求的、分配的任务。Kubernetes 主节点控制它们。节点内部有以下四个组件：

所有容器都将在 Pod 中运行。Pod 将网络和存储从底层容器抽象出来。你的应用将在此处运行。

Kubelet 将节点注册到集群，监视调度器的任务分配，实例化新 Pod，并向主节点报告。

**Container** 负责管理容器、拉取镜像、停止容器、启动容器、销毁容器等。

**Kube-proxy** 负责将应用用户请求转发到正确的 Pod。

## 1.3 Kubernetes 组件

在本节中，让我们了解 Kubernetes 每个重要组件背后的深层概念。

### NODE：

节点是 Kubernetes 中计算硬件的最小单元。它代表集群中的一台机器。在大多数生产系统中，节点很可能是一个数据中心中的物理机器，或托管在云提供商（如 Google Cloud Platform）上的虚拟机。不要让惯例限制你；理论上，你可以用几乎任何东西来创建一个节点。



![](img/8f8a671916d96b455297952d0f37b96c_43_0.png)

图 1.6：节点概念

将机器视为“节点”使我们能够插入一层抽象。现在，我们无需担心任何单个机器的独特特性，而是可以简单地将每台机器视为一组可利用的 CPU 和 RAM 资源。这样，任何机器都可以在 Kubernetes 集群中替代另一台机器。

## 集群：

虽然单独使用节点可能很有用，但这不是 Kubernetes 的做法。一般来说，你应该将集群作为一个整体来思考，而不是担心单个节点的状态。

![](img/8f8a671916d96b455297952d0f37b96c_44_0.png)

Kube-Cluster
CPU: 50000
RAM: 360 GB

图 1.7：集群概念

## Pod：

与过去可能使用过的其他系统不同，Kubernetes 并不会直接运行容器；相反，它将一个或多个容器封装到一个称为 Pod 的更高层级结构中。同一 Pod 中的任何容器都将共享相同的资源和本地网络。容器可以轻松地与同一 Pod 中的其他容器通信，就好像它们在同一台机器上一样，同时保持一定程度的隔离。

Pod 在 Kubernetes 中用作复制的单位。如果你的应用程序变得过于流行，单个 Pod 实例无法承受负载，Kubernetes 可以配置为根据需要将 Pod 的新副本部署到集群中。即使负载不重，在生产系统中随时运行多个 Pod 副本也是标准做法，以实现负载均衡和故障抵抗。

![](img/8f8a671916d96b455297952d0f37b96c_45_0.png)

图 1.8：Pod 概念

Pod 包含一个或多个容器，例如 Docker 容器。当 Pod 运行多个容器时，这些容器作为一个整体进行管理，并共享 Pod 的资源。通常，在单个 Pod 中运行多个容器是一种高级用例。

Pod 还为其容器包含共享的网络和存储资源：

Pod 会自动分配唯一的 IP 地址。Pod 容器共享相同的网络命名空间，包括 IP 地址和网络端口。Pod 中的容器在 Pod 内部通过 localhost 相互通信。

Pod 可以指定一组共享存储卷，这些卷可以在容器之间共享。

```yaml
# pod.yaml
apiVersion: batch/v1
kind: Job
metadata:
  name: hello
spec:
  template:
    # This is the pod template
    spec:
      containers:
      - name: hello
        image: busybox:v1
        command: ['sh', '-c', 'echo "Hello, Kubernetes!" && sleep 3600']
      restartPolicy: OnFailure
```

图 1.9：Pod 创建 yaml

## 部署：

尽管 Pod 是 Kubernetes 中的基本计算单元，但它们通常不会直接在集群上启动。

相反，Pod 通常由再一层抽象——部署——进行管理。

部署的主要目的是声明同一时间应运行多少个 Pod 副本。当部署添加到集群时，它会自动启动所需数量的 Pod，然后对其进行监控。如果 Pod 死亡，部署将自动重新创建它。

![](img/8f8a671916d96b455297952d0f37b96c_47_0.png)

图 1.10：部署概念

使用部署，你无需手动处理 Pod。你只需声明系统的期望状态，它就会自动为你管理。

![](img/8f8a671916d96b455297952d0f37b96c_48_0.png)

图 1.11：部署 yaml 文件

在前面的图中，你可以看到它是 Deployment 的模板，也是每个容器部署的格式。

## 服务：

在 Kubernetes 中，Service 是一个 REST 对象，与 Pod 类似。像所有 REST 对象一样，你可以将 Service 定义 POST 到 API 服务器以创建新实例。Service 对象的名称必须是有效的 DNS 标签名称。

![](img/8f8a671916d96b455297952d0f37b96c_49_0.png)

图 1.12：Service 概念

例如，假设你有一组 Pod，每个 Pod 都监听 TCP 端口 9376 并带有标签 app=MyApp——此规范会创建一个名为 "my-service" 的新 Service 对象，该对象针对具有 app=MyApp 标签的任何 Pod 上的 TCP 端口 9376。

Kubernetes 为此 Service 分配一个 IP 地址（有时称为“集群 IP”），该地址由 Service 代理使用。Pod 中的端口定义具有名称，你可以在 Service 的 targetPort 属性中引用这些名称。

### 为什么使用 Service？

在 Kubernetes 集群中，每个 Pod 都有一个内部 IP 地址。但 Deployment 中的 Pod 会来来去去，它们的 IP 地址会发生变化。因此，直接使用 Pod IP 地址是没有意义的。有了 Service，你可以获得一个稳定的 IP 地址，该地址在 Service 的生命周期内保持不变，即使成员 Pod 的 IP 地址发生变化。

Service 还提供负载均衡。客户端调用单个稳定的 IP 地址，其请求会在 Service 的成员 Pod 之间进行均衡。

### 1.3.1 服务类型

以下是五种 Service 类型：

- **ClusterIP (default):** 内部客户端发送请求到稳定的内部 IP 地址。
- **NodePort:** 客户端发送请求到节点 IP 地址上的一个或多个由 Service 指定的 nodePort 值。
- **LoadBalancer:** 客户端发送请求到网络负载均衡器的 IP 地址。
- **ExternalName:** 内部客户端将 Service 的 DNS 名称用作外部 DNS 名称的别名。
- **Headless:** 你可以在想要 Pod 分组但不需要稳定 IP 地址的情况下使用无头服务。

```yaml
apiVersion: v1
kind: Service
metadata:
  name: my-service
spec:
  selector:
    app: MyApp
  ports:
  - protocol: TCP
    port: 80
    targetPort: 9376
```

图 1.13：Service yaml 文件

## Ingress：

使用前面描述的概念，你可以创建节点集群，并在集群上启动 Pod 的部署。然而，还有一个最后需要解决的问题——允许外部流量访问你的应用程序。

默认情况下，Kubernetes 在 Pod 和外部世界之间提供隔离。如果你想与 Pod 中运行的服务通信，你必须打开一个通信通道。

这被称为 Ingress。向集群添加 ingress 有多种方式。最常见的方式是添加 Ingress 控制器或 LoadBalancer。这两种选项之间的确切权衡超出了本文的范围，但你必须意识到，在尝试 Kubernetes 之前，ingress 是你需要处理的事情。

### 什么是 Ingress？

Ingress 将 HTTP 和 HTTPS 路由从集群外部暴露到集群内的服务。流量路由由 Ingress 资源上定义的规则控制。以下是一个简单示例，其中 Ingress 将其所有流量发送到一个 Service。

Ingress 可以配置为为服务提供可外部访问的 URL、负载均衡流量、终止 SSL/TLS 并提供基于名称的虚拟主机。Ingress 控制器负责实现 Ingress，通常使用负载均衡器，尽管它也可能配置你的边缘路由器或额外的前端来帮助处理流量。

Ingress 不会暴露任意端口或协议。将除 HTTP 和 HTTPS 之外的服务暴露到互联网，通常使用类型为 Service.Type=NodePort 的服务或

![](img/8f8a671916d96b455297952d0f37b96c_54_0.png)

图 1.14：Ingress 架构

扇出配置根据请求的 HTTP URL 将流量从单个 IP 地址路由到多个 Service。Ingress 允许你将负载均衡器的数量降至最低。例如，像以下这样的设置：

Ingress 控制器会配置一个特定于实现的负载均衡器来满足 Ingress，只要 Service（service1、service2）存在。当完成此操作后，你可以在 Address 字段中看到负载均衡器的地址。



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

- 计算引擎 API
- Kubernetes 引擎 API
- 身份和访问管理 (IAM) API
- 部署管理器 API
- 云资源管理器 API
- 云 Filestore API
- AI Platform 训练和预测 API
- 云 Build API

![](img/8f8a671916d96b455297952d0f37b96c_72_0.png)

## 图 1.26：GCP API 和 服务仪表板

以下内容需要在命令行为 Kubeflow 安装：

确保已安装以下工具：

kubectl.

gcloud

如果您使用 Cloud Shell，请启用 boost 模式。

接下来，请确保您的 GCP 项目满足项目设置指南中描述的最低要求。

按照指南设置 OAuth 凭据。要为 **云身份感知代理** 创建 OAuth 凭据，请点击以下链接：

https://v1-o-branch.Kubeflow.org/docs/gke/deploy/

### 1.6.1 安装和设置 kubectl

现在，让我们首先安装 kubectl gcloud sdk，它将用于连接 Kubernetes。

使用 Homebrew 在 macOS 上安装：

如果您使用的是 macOS 并使用 Homebrew 包管理器，您可以使用 Homebrew 安装 kubectl：

运行安装命令：

```
$ brew install kubectl
```

测试以确保您安装的版本是最新的：

```
$ kubectl version --client
```

对于其他操作系统，请按照以下链接操作 Linux 或 Windows 或 MacOs：

https://kubernetes.io/docs/tasks/tools/install-kubectl/

### 1.6.2 安装和设置 gcloud sdk

检查您的操作系统运行的是哪个版本（64 位或 32 位）。

Linux / 从命令行运行 getconf LONG_BIT。

控制面板 | 系统 | 系统类型

运行以下命令：

```bash
$ curl -O
https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/google-cloud-sdk-302.0.0-linux-x86_64.tar.gz
$ tar zxvf google-cloud-sdk-302.0.0-linux-x86_64.tar.gz
$ ./google-cloud-sdk/install.sh
$ gcloud version
```

```
Google Cloud SDK 329.0.0
app-engine-python 1.9.91
beta 2021.02.19
bq 2.0.65
cloud-datastore-emulator 2.1.0
core 2021.02.19
gsutil 4.59
kpt 0.33.0
kubectl 1.17.17
```

图 1.27：Gcloud 版本

现在，要安装 google cloud sdk，请点击以下链接：

[https://cloud.google.com/sdk/docs/downloads-versioned-archives](https://cloud.google.com/sdk/docs/downloads-versioned-archives)

### 1.6.3 从 Cloud IAP 设置 OAuth

在本节中，我们将设置 Cloud IAP 的 OAuth 以获取密钥。因此，OAuth 设置需要几个步骤。

首先从 GCP 中的 APIs and Service 创建 OAuth 同意屏幕，并完成以下步骤：

在 **应用程序名称** 框中，输入应用程序的名称。以下示例使用名称

在 **支持** 下选择您希望显示为公开联系人的电子邮件地址。您必须使用您自己的电子邮件地址或您拥有的 Google 群组。

如果您看到 **已授权**，请输入以下内容：

** .cloud.goog**

这里，是您的 GCP 项目 ID。

如果您使用自己的域名，例如 您也应将其添加。

Authorized domains 选项仅在某些项目配置中出现。如果您看不到该选项，则无需

设置。

点击

请前往以下链接并执行相同的操作： https://v1-o-branch.Kubeflow.org/docs/gke/deploy/oauth-setup/

步骤：前往 APIs & Service | OAuth consent screen | Credentials

![](img/8f8a671916d96b455297952d0f37b96c_78_0.png)

图 1.28：GCP APIs 和 Service

请注意：在前面的步骤之后复制几个重要点，这将在以后的 Kubeflow 部署中需要。

为此，完成以下步骤：

将 **客户端 ID** 和 **客户端密钥** 复制到笔记中以备将来使用。

|  |  |
|---|---|
| 客户端 ID | 449053263861-j66phntgagp35hl190bqc38o1rojs k04.apps.googleusercontent.com |
| 客户端密钥 | 2y7tNtbbH_SJZ_irWP2_jPo |

*图 1.29：OAuth ID 和 密钥*

在 OAuth 同意屏幕中更改 Authorized redirect URIs。

https://iap.googleapis.com/v1/oauth/clientIds/:handleRedirect

将 CLIENT_ID 粘贴到此 URL 中并粘贴到 OAuth 同意屏幕中的 Authorized redirect URIs。

请点击以下链接以详细了解：

https://www.Kubeflow.org/docs/gke/deploy/oauth-setup/

### 1.6.4 设置 Docker

现在，我们将设置 Docker，这对于构建容器映像很重要。

您应该拥有 Docker Hub 账户 [https://hub.docker.com/](https://hub.docker.com/)

![](img/8f8a671916d96b455297952d0f37b96c_80_0.png)

图 1.30：Docker Hub 登录页面

一旦您为 MacOS、Linux 或 Windows 安装 Docker，您必须使用 Docker hub 的相同凭据使用 DOCKER_ID 和 PASSWORD 登录到应用程序。

请点击以下链接进行 Docker 安装：

[https://docs.docker.com/docker-for-mac/install/](https://docs.docker.com/docker-for-mac/install/)

### 1.6.5 在 GCP 中的 Kubernetes 集群中设置 Kubeflow

要在 Kubernetes 集群中设置 Kubeflow，您可以使用 Google cloud shell 或系统的 Microsoft Visual Studio Terminal。在这里，我们将使用 Google cloud shell。

![](img/8f8a671916d96b455297952d0f37b96c_82_0.png)

图 1.31：激活 cloud shell

现在，我们将激活 boost shell。

![](img/8f8a671916d96b455297952d0f37b96c_82_1.png)

## 图 1.32：激活 cloud shell Boost 模式

请在 cloud shell 中完成以下步骤。

我们唯一需要提供的是 **集群名称** 并根据 Kubeflow 发布 yaml 文件的版本更改 **配置 URI**。

您在 GitHub 中有以下代码 yaml 文件。请在完成本章的所有活动后运行步骤 5 以在 google cloud 中产生费用。

**使用部署** 本指南描述了如何使用 **kfctl 命令行界面** 在 GCP 上部署 Kubeflow。命令行部署为您提供了对部署过程的更多控制。

## 在 Google Cloud Platform 上设置 Kubeflow

注意：使用可在 ** https://v1-o-branch.Kubeflow.org/docs/gke/deploy/deploy-cli/** 获取的最新官方 Kubeflow 文档来安装最新版本和配置文件。
最新版本可在以下位置获取
**https://github.com/Kubeflow/kfctl/releases**

### 第 1 步：设置 GCP

```bash
# login to gcloud for authentication : done once
gcloud auth login
# create application default credentials : done once
gcloud auth application-default login
```

```
# GCP Project ID
export PROJECT=
gcloud config set project ${PROJECT}
# GCP Zone (use us-east1-c)
export ZONE=
gcloud config set compute/zone ${ZONE}
```

### 第 2 步：根据您的操作系统下载发行版

```
# KFCTL file url : Get the latest file from
# https://github.com/Kubeflow/kfctl/releases based on the operating system

KFCTL_FILE_PATH="https://github.com/Kubeflow/kfctl/releases/download/v1.0.2/kfctl_v1.0.2-o-ga476281_linux.tar.gz"
KFCTL_FILE="kfctl.tar.gz"
# download KFCTL compressed file
wget $KFCTL_FILE_PATH -O $KFCTL_FILE
# extract KFCTL
tar -xvf ${KFCTL_FILE}
#mv kfctl-${PLATFORM} kfctl
# add kFCTL to path
PATH=${PATH}:$(pwd)
```

### 第 3 步：设置部署

复制并粘贴步骤 C（OAuth Setup Cloud）中的 Client ID 和 secret。

```bash
# Deployment Name e.g.
export KF_NAME=
# set client ID and client secret
export CLIENT_ID=
export CLIENT_SECRET=

# set the config URI : use the official documentation to use the
latest config file
# get latest config URI from official Kubeflow documentation :
https://v1-o-branch.Kubeflow.org/docs/gke/deploy/deploy-cli/
#export
CONFIG_URI=https://raw.githubusercontent.com/Kubeflow/manifests/
v1.o-branch/kfdef/kfctl_gcp_iap.v1.o.2.yaml
```

将前面的 URL 复制到 bash 中的以下命令中：

```bash
export CONFIG_URI=""
# set the base directory
BASE_DIR=$(pwd)
# set the directory for deployment
KF_DIR=${BASE_DIR}/${KF_NAME}
# create the directory
mkdir -p ${KF_DIR}
# navigate to the directory
cd ${KF_DIR}
# build deployment using the config file. Make changes in your
configuration if needed
kfctl build -V -f ${CONFIG_URI}
```



### 第 4 步：部署

```bash
# setup the config file
```

现在，在当前文件夹中运行以下命令以检查文件：

```bash
ls
```

![](img/8f8a671916d96b455297952d0f37b96c_86_0.png)

Figure 1.33: Kubeflow 安装 yaml 文件

现在，从前面的图中，我们可以复制 kfctl_gcp_iap.v1.0.2.yaml 并粘贴到以下位置以设置环境变量来部署该 yaml。

接下来，进入之前的 gcp_config 文件夹，运行 vim cluster-Kubeflow.yaml 并将 cluster-version 改为“1.19”，保存文件，然后返回 {KF_DIR} 的根文件夹。

```bash
export CONFIG_FILE=${KF_DIR}/
# apply changes
kfctl apply -V -f ${CONFIG_FILE}
gcloud container clusters get-credentials ${KF_NAME} --zone ${ZONE} --project ${PROJECT}
```

请在所有活动完成后运行第 5 步，以在项目结束时删除所有内容，避免在 Google Cloud 中产生费用。

### 第 5 步：删除

```bash
# If you want to delete all the resources, including storage:
kfctl delete -f ${CONFIG_FILE} --delete_storage
```

现在，请等待 15-20 分钟以使 Ingress 准备就绪。让我们打开 Ingress 进行检查；点击 **Kubernetes Engine | 服务与入口**，并在名称中查找以下示例作为托管 Kubeflow 的 URL；点击打开 Kubeflow 仪表板。

![](img/8f8a671916d96b455297952d0f37b96c_87_0.png)

Figure 1.34: Kubeflow 服务与入口 URL

点击前面图中显示的以下 URL：

https://.endpoints..cloud.google/

如果您想运行 Kubeflow 1.3，请查看下面的链接：

https://github.com/aniruddhachoudhury/mlopsworld

### 1.6.6 连接到集群并部署 Grafana

### 设置 knative-monitoring

```bash
##RUN THE COMMAND IN GOOGLE SHELL
# Connect to cluster
gcloud container clusters get-credentials <$ClusterName> --zone <$ZONE> --project <$PROJECTID>
#create namespace
kubectl create namespace knative-monitoring
#setup monitoring components
kubectl apply --filename https://github.com/knative/serving/releases/download/v0.17.2/monitoring-metrics-prometheus.yaml
```

### 1.6.7 在 Kubeflow 中设置 Jupyter Notebook 服务器

让我们为本书中的所有操作和项目创建一个自定义 Jupyter Lab 或 Notebook。

![](img/8f8a671916d96b455297952d0f37b96c_90_0.png)

Figure 1.35: 自定义 Docker 镜像 Jupyter NB

现在，我们将构建自定义 Docker 镜像；为此，请确保您启动 Docker。您会看到 Docker 在顶部处于激活状态，正如我们在下图中看到的第一个图标所示，表示 Docker 已启动：

![](img/8f8a671916d96b455297952d0f37b96c_90_1.png)

Figure 1.36: 系统中 Docker 的激活

```bash
PROJECT_ID=$(gcloud config get-value core/project)
IMAGE_NAME=custom-image-1
```

```bash
IMAGE_NAME=gcr.io/$PROJECT_ID/$IMAGE_NAME
IMAGE_TAG=latest

# build image
docker build -t $IMAGE_NAME:$IMAGE_TAG .
# run locally to test
docker run -it --rm -p 8888:8888 -p 6006:6006 -v $(pwd):/home/jovyan $IMAGE_NAME:$IMAGE_TAG
# authorize Docker
gcloud auth configure-docker --quiet
# push image

docker push $IMAGE_NAME:$IMAGE_TAG
```

因此，我们将在 Jupyter Notebook 中使用自定义 Docker 镜像。

gcr.io/custom-image-1:latest

完成以下步骤：

点击 Kubeflow UI 左侧面板上的 Notebook Servers，以访问随 Kubeflow 部署的 Jupyter notebook 服务：

![](img/8f8a671916d96b455297952d0f37b96c_91_0.png)

Figure 1.37: Kubeflow NB 仪表板

现在点击 NEW SERVER 创建一个新的 Jupyter Notebook。

![](img/8f8a671916d96b455297952d0f37b96c_92_0.png)

Figure 1.38: 点击新建服务器

为笔记本服务器输入您选择的名称。名称可以包含字母和数字，但不能包含空格。例如，

Kubeflow 会自动更新 namespace 字段的值，使其与您在上一步中选择的名称空间相同。这确保新的笔记本服务器位于您可以访问的名称空间中。

![](img/8f8a671916d96b455297952d0f37b96c_92_1.png)

Figure 1.39: 笔记本配置名称

为笔记本服务器的基础部署选择一个 Docker 镜像。您可以指定自定义镜像或从一系列标准镜像中选择。在这里，我们将使用 **自定义** 粘贴前面的 Docker 镜像：指定笔记本服务器应保留的总 CPU 量。默认值为 0.5。对于 CPU 密集型作业，您可以选择一个以上的 CPU（例如，1.5）。指定笔记本服务器应保留的总内存（RAM）量。默认值为 1.0Gi。

![](img/8f8a671916d96b455297952d0f37b96c_93_0.png)

Figure 1.40: 配置镜像和 CPU 与内存

指定一个工作区卷来保存此笔记本服务器的个人工作区。Kubeflow 为您的工作区卷配置 Kubernetes **持久卷**。PV 确保即使您销毁笔记本服务器，您也可以保留数据。

默认情况下，使用以下配置为工作区创建一个新卷：

卷名称与笔记本服务器名称同步，格式为 workspace-。当您开始输入笔记本服务器名称时，卷名称会出现。您可以编辑卷名称，但如果以后编辑笔记本服务器名称，卷名称会更改以匹配笔记本服务器名称。

10Gi

**访问** ReadWriteOnce。此设置意味着该卷可以由单个节点以读写方式挂载。

Mount /home/jovyan

或者，您可以通过指定现有卷的名称将笔记本服务器指向现有卷。

（可选）如果您想存储和访问此笔记本服务器上笔记本的数据，请指定一个或多个数据卷。您可以添加新卷或指定现有卷。Kubeflow 为每个数据卷配置 Kubernetes **持久卷**。

![](img/8f8a671916d96b455297952d0f37b96c_95_0.png)

Figure 1.41: 配置 PVC 与卷

从下拉菜单中选择添加 gcp 凭据。同样，要使用 GPU 镜像，我们必须提供一个自定义 GPU 镜像，该镜像将在 GitHub 上。但由于我们目前将在 CPU 上工作，因此现在不会提供任何 GPU。

![](img/8f8a671916d96b455297952d0f37b96c_95_1.png)

Figure 1.42: 配置/GPU/启动

点击 您应该在 Notebook Servers 页面上看到新笔记本服务器的条目，状态列中有一个旋转指示器。以下是我们创建的示例 Notebook：

![](img/8f8a671916d96b455297952d0f37b96c_96_0.png)

Figure 1.43: Notebook 已就绪

当笔记本服务器运行时，您应该会看到 Jupyter 仪表板界面。如果您请求了新的工作区，仪表板上不应有笔记本。

## 1.7 可选：Jupyter Notebook 的 PVC 设置

如果您想将 PVC 附加到文件存储，以便您可以将 Jupyter Notebook 中的数据或代码保存到外部存储中，那么我们可以完成以下步骤：

（1TB 存储将收取费用）

步骤 创建一个具有 1 TB 存储容量的 Filestore 实例。

```bash
FS=[NAME FOR THE FILESTORE YOU WILL CREATE]
gcloud beta filestore instances create ${FS} \
--project=${PROJECT} \
--zone=${ZONE} \
--tier=STANDARD \
--file-share=name="volumes",capacity=1TB \
--network=name="default"
```

步骤 检索 Filestore 实例的 IP 地址。

```bash
FSADDR=$(gcloud beta filestore instances describe ${FS} \
--project=${PROJECT} \
--zone=${ZONE} \
--format="value(networks.ipAddresses[0])")
```

步骤 连接到您创建的集群。

```bash
export ZONE=us-east1-c
export CLUSTER_NAME= {Your-cluster name}
gcloud container clusters get-credentials --zone --project
```

步骤 为自己授予 cluster-admin 权限。

```bash
ACCOUNT=$(gcloud config get-value core/account)
kubectl create clusterrolebinding core-cluster-admin-binding \
--user ${ACCOUNT} \
--clusterrole cluster-admin
```

步骤 下载 Helm。

```bash
wget https://storage.googleapis.com/kubernetes-helm/helm-v2.11.0-linux-amd64.tar.gz
tar xf helm-v2.11.0-linux-amd64.tar.gz
sudo ln -s $PWD/linux-amd64/helm /usr/local/bin/helm
```

步骤 创建一个名为 rbac-config.yaml 的文件，包含以下内容：

apiVersion: v1
kind: ServiceAccount
metadata:
name: tiller
namespace: kube-system
---
apiVersion: rbac.authorization.k8s.io/v1beta1
kind: ClusterRoleBinding
metadata:
name: tiller
roleRef:
apiGroup: rbac.authorization.k8s.io
kind: ClusterRole

name: cluster-admin
subjects:
- kind: ServiceAccount
name: tiller
namespace: kube-system

### Step Create the tiller service account and cluster-admin role binding.
### 步骤 创建 tiller 服务账号和 cluster-admin 角色绑定。

```bash
kubectl apply -f rbac-config.yaml
```

### Step Initialize Helm.
### 步骤 初始化 Helm。

```bash
helm init --service-account tiller
```

### Step Copy the namespace that you can find by either running the following command which will give a list of namespace, or from the UI.
### 步骤 复制命名空间，您可以通过运行以下命令找到该命名空间，该命令将列出命名空间，或从 UI 中找到。

```bash
kubectl get namespace
```

Otherwise, copy the drop down and paste in the Notepad example here: aniruddha-choudhury.
否则，复制下拉菜单并粘贴到记事本示例中：aniruddha-choudhury。

![](img/8f8a671916d96b455297952d0f37b96c_100_0.png)

Figure 1.44: Namespace
图 1.44：命名空间

### Step Deploy the NFS-Client Provisioner.
### 步骤 部署 NFS-Client Provisioner。

Create an instance of NFS-Client Provisioner connected to the Filestore instance that you created earlier via its IP address (${FSADDR}). The NFS-Client Provisioner creates a new storage class: nfs-client. Persistent volume claims against that storage class will be fulfilled by creating persistent volumes backed by directories under the /volumes directory on the Filestore instance's managed storage.
创建一个 NFS-Client Provisioner 实例，通过其 IP 地址 (${FSADDR}) 连接到您之前创建的 Filestore 实例。NFS-Client Provisioner 创建一个新的存储类：nfs-client。针对该存储类的持久卷声明将通过创建由 Filestore 实例托管存储上的 /volumes 目录下的目录支持的持久卷来满足。

```bash
helm install stable/nfs-client-provisioner --name nfs-cp --set nfs.server=${FSADDR} --set nfs.path=/volumes
watch kubectl get po -l app=nfs-client-provisioner
```

![](img/8f8a671916d96b455297952d0f37b96c_101_0.png)

Figure 1.45: FileStore
图 1.45：文件存储

### Step Make a Persistent Volume Claim.
### 步骤 创建持久卷声明。

Create a Kubernetes Persistent Volume Claim specification. This is a .yaml file that allows a Kubernetes pod to access the storage resources of a Persistent Volume. The specification looks similar to the following example:
创建一个 Kubernetes 持久卷声明规范。这是一个 .yaml 文件，允许 Kubernetes pod 访问持久卷的存储资源。该规范看起来类似于以下示例：

![](img/8f8a671916d96b455297952d0f37b96c_101_1.png)

Figure 1.46: PVC yaml
图 1.46：PVC yaml

Here, storage is the size of the Persistent Volume Claim that you want to make available to the Kubernetes objects.
这里，storage 是您希望提供给 Kubernetes 对象的持久卷声明的大小。

You must specify the storage value in one of the supported units described in the Resource quantities. The value you specify must be equal to or less than the storage you specified for the Persistent Volume.
您必须使用 Resource quantities 中描述的支持的单位之一指定 storage 值。您指定的值必须等于或小于您为持久卷指定的存储。

Deploy the Persistent Volume Claim specification:
部署持久卷声明规范：

```bash
kubectl create -f persistent-volume-claim-file-name.yaml
```

Here, persistent-volume-file-name is the name of the Kubernetes Persistent Volume specification file that you created in the previous step.
这里，persistent-volume-file-name 是您在上一步中创建的 Kubernetes 持久卷规范文件的名称。

### Step Copy the PVC name from above and paste it in the Jupyter Notebook in Kubeflow Workspace Volume Name.
### 步骤 从上面复制 PVC 名称并将其粘贴到 Jupyter Notebook 中的 Kubeflow 工作区卷名称。

```bash
## paste the namespace here to get the name
kubectl get pvc -n {namespace}
```

## 1.8 Conclusion
## 1.8 结论

In this chapter, we learned about the Kubernetes Orchestration concepts and architecture, and how it works in deployment level and scaling our application, alongside exposing to the outer world with the Network & Service; and how the Docker makes it easy for a developer to containerize applications.
在本章中，我们学习了 Kubernetes 编排概念和架构，以及它在部署级别和扩展我们的应用程序方面的工作方式，同时通过网络和服务向外部世界公开；以及 Docker 如何使开发人员轻松地将应用程序容器化。

Then, we saw how to set up the Jupyter Notebook with CPU and GPU with the PVC attached and how to setup the PVC to store our required data for lifetime. We also learned more about deployment, service, and the ingress framework structure in Google Cloud. Finally, we learned how to setup Kubeflow in Google Cloud Platform for our following chapters.
然后，我们了解了如何使用附加 PVC 设置 CPU 和 GPU 的 Jupyter Notebook，以及如何设置 PVC 以永久存储我们所需的数据。我们还进一步了解了 Google Cloud 中的部署、服务和 ingress 框架结构。最后，我们学习了如何为后续章节在 Google Cloud Platform 上设置 Kubeflow。

In this chapter, we have gained how to leverage the power of Google Cloud Platform, and how to use your Devops knowledge with Machine Learning to become a MLops.
在本章中，我们了解了如何利用 Google Cloud Platform 的强大功能，以及如何将您的 DevOps 知识与机器学习结合起来成为 MLOps。

## 1.9 Reference
## 1.9 参考

https://kubernetes.io/docs/tutorials/kubernetes-basics/

https://kubernetes.io/docs/reference/

https://github.com/kubernetes/kubernetes

https://kubernetes.io/docs/concepts/overview/what-is-kubernetes/

# Developing Kubeflow Pipeline in GCP
## 在 GCP 中开发 Kubeflow Pipeline

In this chapter, we will build an end-to-end TensorFlow classification Model deployment with Kubeflow Orchestration, which includes deploying Kubeflow in Kubernetes Cluster in GCP, building the pipeline components for the model with Docker and Kubeflow SDK, and then serving the Model with KF serving to have an endpoint for prediction. We will also track the monitoring and performance for our serving traffic endpoint in Grafana Dashboard.
在本章中，我们将使用 Kubeflow 编排构建端到端的 TensorFlow 分类模型部署，其中包括在 GCP 的 Kubernetes 集群中部署 Kubeflow，使用 Docker 和 Kubeflow SDK 为模型构建流水线组件，然后使用 KF serving 提供模型以获得预测端点。我们还将在 Grafana 仪表板中跟踪我们服务流量端点的监控和性能。

## Structure
## 结构

In this chapter, we will cover the following topics:
本章将涵盖以下主题：

- Problem statement
- 问题陈述
- Getting started in GCP Kubeflow and Docker setup
- 在 GCP Kubeflow 和 Docker 设置中入门
- Breakdown technique to build the production pipeline
- 构建生产流水线的分解技术
- Building the Kubeflow Pipeline components for TensorFlow model
- 为 TensorFlow 模型构建 Kubeflow Pipeline 组件
- Serving the Model with KF Serving
- 使用 KF Serving 提供模型
- Building the pipeline end to end
- 端到端构建流水线
- Monitoring the performance with Grafana dashboard
- 使用 Grafana 仪表板监控性能

## Objectives
## 目标

In this chapter, we will learn the following:
在本章中，我们将学习以下内容：

- How to use Docker and Kubernetes to build the Kubeflow Pipeline.
- 如何使用 Docker 和 Kubernetes 构建 Kubeflow Pipeline。
- How to build the individual pipeline components like the training and model evaluation.
- 如何构建单个流水线组件，如训练和模型评估。
- How to serve the Model with KF serving and predict the model request, and monitor with the Grafana Dashboard.
- 如何使用 KF serving 提供模型并预测模型请求，并使用 Grafana 仪表板进行监控。
- How to use Kubernetes, and many Google Cloud Platform to leverage the power of Machine learning with Devops Knowledge.
- 如何使用 Kubernetes 和许多 Google Cloud Platform 来利用 DevOps 知识的机器学习能力。

## 2.1 Problem statement
## 2.1 问题陈述

In this example, we have a classification dataset of breast cancer, and it will have 30 attributes. We have to classify the Malignant and Benign.
在此示例中，我们有一个乳腺癌分类数据集，它将有 30 个属性。我们需要对 Malignant 和 Benign 进行分类。

Benign. Benign. Benign. Benign. Benign. Benign. Benign. Benign.
Benign. Benign. Benign. Benign. Benign. Benign. Benign. Benign.
Benign. Benign. Benign. Benign. Benign. Benign. Benign. Benign.
Benign. Benign. Benign. Benign. Benign. Benign. Benign. Benign.
Benign.

Benign.

## 2.2 Getting started in GCP Kubeflow setup
## 2.2 在 GCP Kubeflow 设置中入门

So, before we begin, we must setup the Kubeflow Cluster in GCP; please refer to *Chapter 1: Introduction to Kubeflow & Kubernetes Cloud* section 1.6 (Getting Started in GCP Kubeflow setup).
因此，在开始之前，我们必须在 GCP 中设置 Kubeflow 集群；请参阅 *第 1 章：Kubeflow 和 Kubernetes 云简介* 第 1.6 节（在 GCP Kubeflow 设置中入门）。

## 2.3 Breakdown technique to build production pipeline
## 2.3 构建生产流水线的分解技术

In this section, we will see how to frame your business problem, so that we can break down the Machine learning life cycle components, and build each component, so that we can build the Kubeflow pipeline.
在本节中，我们将了解如何构建您的业务问题，以便我们可以分解机器学习生命周期组件并构建每个组件，从而构建 Kubeflow 流水线。

The following is the high level framework from the Jupyter Notebook code to the Pipeline components, and serving and hosting that in Cloud.
以下是从 Jupyter Notebook 代码到流水线组件的高级框架，以及在云中提供和托管该框架。

![](img/8f8a671916d96b455297952d0f37b96c_110_0.png)

Figure 2.1: Pipeline Components E2E Architecture
图 2.1：流水线组件 E2E 架构

We will Dockerize each and every component, and push to the container registry of any Cloud, like for AWS, GCP, Azure, so that we can use that in the Kubeflow pipeline.
我们将对每个组件进行 Docker 化，并推送到任何云的容器注册表中，例如 AWS、GCP、Azure，以便我们可以在 Kubeflow 流水线中使用它。

### Steps to perform:
### 执行步骤：

**Data Extraction or** Let's say we have our machine learning; the first component is to extract the data from any sources like S3 bucket, Cloud Storage, and so on. Now, we will write the single component of the Input data sources and connection between Kubeflow components to all the data sources in the Python code.

And a next a service account in json format will be used so that we can connect to external source. Then, we will Dockerize the component.
**Data Extraction or** 假设我们有机器学习；第一个组件是从任何来源（如 S3 存储桶、Cloud Storage 等）提取数据。现在，我们将在 Python 代码中编写输入数据源的单个组件以及 Kubeflow 组件与所有数据源之间的连接。

接下来将使用 json 格式的服务账号，以便我们可以连接到外部源。然后，我们将对组件进行 Docker 化。

![](img/8f8a671916d96b455297952d0f37b96c_111_0.png)

*Figure 2.2: Pipeline Component 1: Data Ingestion*
*图 2.2：流水线组件 1：数据摄取*

**Data** The next component in our machine learning project is to pre-process or feature the engineering step. Here, we will build or transform all the incoming data which will be required for the training, according to all the use case like Computer vision, NLP, Structured data with the respective business pre-processing logic, and we will save the artifacts or the transformed data back to the Storage bucket for future reference.
**Data** 我们机器学习项目中的下一个组件是预处理或特征工程步骤。在这里，我们将构建或转换所有传入的数据，这些数据将根据所有用例（如计算机视觉、NLP、结构化数据）以及相应的业务预处理逻辑用于训练，并将工件或转换后的数据保存回存储桶以供将来参考。

![](img/8f8a671916d96b455297952d0f37b96c_112_0.png)

Figure 2.3: Pipeline Component 2: Data Pre-processing
图 2.3：流水线组件 2：数据预处理

So, here we will train the model it can any TensorFlow or Sklearn, and so on with our pre-process data, and will save the model artifacts and logs in the external storage and internally in the native Kubernetes' Persistent Volume Claim
因此，在这里我们将使用预处理数据训练模型，可以是任何 TensorFlow 或 Sklearn 等，并将模型工件和日志保存到外部存储以及 Kubernetes 原生的持久卷声明中

![](img/8f8a671916d96b455297952d0f37b96c_112_1.png)

Figure 2.4: Pipeline Component 3: Training
图 2.4：流水线组件 3：训练

Similarly, like the preceding step, we will build the evaluator component for the Kubeflow pipeline and then we will serve the model by loading the model from any storage like S3, Cloud Bucket, and so on.
类似于前一步，我们将为 Kubeflow 流水线构建评估器组件，然后通过从任何存储（如 S3、Cloud Bucket 等）加载模型来提供模型。



接下来，我们将预处理逻辑保留在服务 Python 代码中，对传入的数据进行自动转换，然后再进行预测。然后，我们将加载保存在 S3、Bucket 等中的训练模型以进行预测。同时，如果我们有其他预处理模型，例如 Scikit-learn 中的 label-encoder，我们可以在数据预处理步骤 2 中保存的 artifacts 加载时加载它，以便它转换传入的数据，并使用我们加载的模型进行预测。

![](img/8f8a671916d96b455297952d0f37b96c_113_0.png)

图 2.5：Pipeline Component 4:serving

接下来，我们将从头开始构建 TensorFlow 模型管道。

## 2.4 为 TensorFlow 模型构建 Kubeflow Pipeline 组件

本节不会展示如何使用 TensorFlow 构建训练分类器；这里的主要重点是如何在 Kubeflow 中构建管道，将其结构化为端到端的管道。您可以使用 Microsoft Visual Studio 并安装 Docker 并在 Visual Studio 中进行配置。

因此，我们的管道文件夹结构将如下所示：

![](img/8f8a671916d96b455297952d0f37b96c_114_0.png)

图 2.6：Pipeline folder Structure

下面我们将看到我们管道的分解架构，以及构建端到端管道的每个组件包含的内容。

这里，我们有 KF-serving 已部署在 Kubernetes 中并正在运行，我们可以调用其端点进行预测。

与此步骤类似，所有其他步骤都可以在 pipeline/folder 中找到，并且都具有以下结构：

**Pipeline.py** 通过 CLI 暴露功能。

**requirements.txt** 指定运行所需的 Python 依赖项。

Dockerfile 使用 requirements 构建镜像，一行即可完成。

### 2.3.1 数据提取或摄取组件

让我们看看如何构建组件数据提取 Python 文件，如下所示：

**dataextraction.py:**

```
```python
from __future__ import absolute_import, division, print_function,
unicode_literals
import click, json, os, dill, argparse
import numpy as np
import pandas as pd
from sklearn.datasets import load_breast_cancer

@click.command()
@click.option('--data-file', default="/mnt/breast.data")
def get_data(data_file):
cancer = load_breast_cancer()
df_cancer = pd.DataFrame(np.c_[cancer['data'], cancer['target']],
columns = np.append(cancer['feature_names'], ['target']))
print(df_cancer.head(3))
print(df_cancer.describe())
with open(data_file,"wb") as f:
dill.dump(df_cancer,f)
return

if __name__ == "__main__":
get_data()
```
```

让我们按如下方式分解代码：

首先我们将从 Sklearn 数据集加载数据。然后，导入所有所需的数据集。

然后 **@click** 命令将参数传递给函数

然后 **dill** 命令将帮助将数据保存到 pvc 中。

因此，正如我们所见，“data-file”是“/mnt”，所以 mnt 是挂载点；我们每次都会使用 mnt；之后我们可以给出一个带有 **.data** 扩展名的文件名；它将以 csv、txt、numpy、dataframe 等任何格式保存数据。

因此，我们使用它保存的任何数据都将用于下一个管道数据预处理，其中我们将输入保存的数据。

接下来，让我们看看如何为数据提取构建组件 Dockerfile。以下屏幕截图显示了 requirements 文件，其中每个库将在 **pipeline.py** 内使用，我们需要将 **requirements.txt** 文件加载为环境，以便在 Docker 内运行 Python 函数：

![](img/8f8a671916d96b455297952d0f37b96c_118_0.png)

图 2.7：Pipeline Requirements.txt

### Docker:

```
FROM python:3.7-slim-stretch
ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update && \
apt-get -y install gcc mono-mcs g++ git curl && \
rm -rf /var/lib/apt/lists/*
RUN mkdir /app

WORKDIR /app
ADD requirements.txt /app/requirements.txt
RUN pip3 install -r requirements.txt
# copy python
ADD dataextract.py /app/dataextract.py
```

```
RUN chmod +x /app/dataextract.py
ENTRYPOINT ["python"]
CMD ["/app/dataextract.py"]
```

让我们按如下方式分解 Dockerfile 代码：

加载 Python 镜像作为基础镜像以运行 3.7 版本的管道代码。

RUN 函数将在 Docker 镜像启动时运行，并首先使用 mkdir 命令创建 /app 文件夹。

接下来，我们将把命令重定向到 WORKDIR，在那里安装所有文件和依赖项。

接下来，我们将在 /app 文件夹中添加 requirements 文件，然后运行 pip 命令安装 Python 库。

接下来，我们将复制 pipeline.py Python 代码并使用 chmod 命令授予管理权限，以便在 Docker 镜像运行时运行该文件。

接下来，我们将设置入口点为 Python，CMD 为首先运行此项。

现在，我们将构建 Docker 镜像；为此，请确保启动 Docker，之后您将在顶部看到 Docker 已激活。如以下屏幕截图所示，第一个图标是已启动的 Docker。

![](img/8f8a671916d96b455297952d0f37b96c_120_0.png)

图 2.8：Docker Activation

接下来，我们可以重定向到我们的 visual studio code，并通过在 dataextraction 文件夹内右键单击 Dockerfile 从 visual studio 打开终端：

![](img/8f8a671916d96b455297952d0f37b96c_120_1.png)

图 2.9：Open terminal from Visual Studio

通过本地连接 GCP 运行以下所有命令：

```
```bash
gcloud init
#Select the Email/Project associated with GCP
```
```

构建数据提取容器：

```
```bash
cd /pipeline/dataextraction
PROJECT_ID=$(gcloud config get-value core/project)
IMAGE_NAME=breast_cancer/step1_loadingdata
IMAGE_VERSION=v1
IMAGE_NAME=gcr.io/$PROJECT_ID/$IMAGE_NAME
```
```

构建 Docker 镜像：

```
```
docker build -t $IMAGE_NAME:$IMAGE_VERSION .
```
```

将训练镜像推送到 Google 容器注册表

```
```
docker push $IMAGE_NAME:$IMAGE_VERSION
```
```

以下是您的镜像将被存储的屏幕截图：

![](img/8f8a671916d96b455297952d0f37b96c_122_0.png)

图 2.10：Docker Container Registry in GCR

接下来，我们将了解如何构建训练组件，如前所述，我们将构建预处理。

### 2.3.2 数据预处理组件

现在，我们将构建预处理步骤，并假设输入将来自之前的数据摄取组件。因此，我们将首先加载使用 @dill 命令转储的任何数据，并执行必要的预处理步骤。

在这部分代码中，让我们导入所有依赖项，并创建实用相关性绘图函数。

```
from __future__ import absolute_import, division, print_function,
unicode_literals
import os, argparse, json, click, dill
from tensorflow.python.lib.io import file_io
import pandas as pd
from sklearn.model_selection import train_test_split
from google.cloud import storage
from plotly.subplots import make_subplots
import plotly.graph_objects as go
import numpy as np
os.environ['GOOGLE_APPLICATION_CREDENTIALS'] = "service_account_iam.json"
```

```
def correlation_plotting(data,s,correlation_plot):
correlation = data.corr()
matrix_cols = correlation.columns.tolist()
corr_array = np.array(correlation)
```

```
trace = go.Heatmap(z = corr_array, x = matrix_cols, y =
matrix_cols, xgap = 2, ygap = 2, colorscale='Viridis', colorbar =
dict()

layout = go.Layout(dict(title = 'Correlation Matrix' +s, autosize =
False, height = 720, width = 800, margin = dict(r = 0, l = 210, t
= 25,b = 210,), yaxis = dict(tickfont = dict(size = 9)), xaxis =
dict(tickfont = dict(size = 9)),))
fig = go.Figure(data = [trace],layout = layout)
fig.update_layout(title={'y':1, 'x':0.6, 'xanchor': 'center', 'yanchor':
'top'})
fig.write_image(correlation_plot)

@click.command()
@click.option('--data-file', default="/mnt/breast.data")
@click.option('--train-file', default="/mnt/training.data")
@click.option('--test-file', default="/mnt/test.data")
@click.option('--validation-file', default="/mnt/validation.data")
@click.option('--train-target', default="/mnt/trainingtarget.data")
@click.option('--test-target', default="/mnt/testtarget.data")
@click.option('--validation-target',
default="/mnt/validationtarget.data")
@click.option('--split-size', default=0.1)
@click.option('--bucket-data',
default="gs://kubeflowusecases/breast/data.csv")
@click.option('--bucket-name', default="gs://kubeflowusecases")
@click.option('--commit-sha', default="breast/visualize")
@click.option('--metrics-plot', default="/mnt/correlation.png")
def training_data_processing(data_file,train_file,test_file,metrics_plot,validation_file,split_size,train_target,test_target,validation_target,bucket_data,bucket_name,commit_sha):
```



```
with open(data_file, 'rb') as in_f:
    data = dill.load(in_f)

data = data.fillna(data.mean())

correlation_plotting(data, "for the Breast Cancer Dataset", metrics_plot)
```

在延续上一页的预处理代码后，这里我们将在以下部分上传使用 plotly 保存的相关性图像，以便于 Kubeflow Python 可视化。然后，我们将在运行时管道中转储图像和表格的元数据以进行可视化。

```
image_path = os.path.join(bucket_name, commit_sha, 'correlation.png')
image_url = os.path.join('https://storage.cloud.google.com', bucket_name.lstrip('gs://'), commit_sha, 'correlation.png?authuser=0')
html_path = os.path.join(bucket_name, commit_sha, 'correlation.html')
data.to_csv(bucket_data)
header = data.columns.tolist()
file_io.copy(metrics_plot, image_path)
rendered_template = """
src="{}"
""".format(image_url)
file_io.write_string_to_file(html_path, rendered_template)
```

```
metadata = {'outputs': [{'type': 'table', 'storage': 'gcs', 'format': 'csv', 'header': header, 'source': bucket_data}, {'type': 'web-app', 'storage': 'gcs', 'source': html_path,}]}
with open('/mlpipeline-ui-metadata.json', 'w') as f:
    json.dump(metadata, f)
target_name = 'target'
data_target = data[target_name]
data = data.drop([target_name], axis=1)

#%% split training set to validation set
train, test, target, target_test = train_test_split(data, data_target, test_size=split_size, random_state=0)
Xtrain, Xval, Ztrain, Zval = train_test_split(train, target, test_size=split_size, random_state=0)
with open(train_file, "wb") as f:
    dill.dump(Xtrain, f)
with open(test_file, "wb") as f:
    dill.dump(test, f)
with open(validation_file, "wb") as f:
    dill.dump(Xval, f)
with open(train_target, "wb") as f:
    dill.dump(Ztrain, f)

with open(test_target, "wb") as f:
    dill.dump(target_test, f)
with open(validation_target, "wb") as f:
    dill.dump(Zval, f)
return
```

让我们按如下方式分解预处理代码：

首先，我们将导入所有库，并创建用于保存绘图图像的 plotly 相关性实用函数。然后我们将其保存到 GCS 存储桶中，以便可以在 Kubeflow Dashboard 中以静态 HTML 格式可视化。

然后，我们将在环境中添加服务账号 **.json** 文件，以便它可以访问推送数据或工件到 GCP 存储桶。

接下来，**@click** 选项将输入我们在数据摄取步骤中完成的所有必需转储，以便我们可以在此处使用它，之后我们将先加载它们并将其用于训练数据的预处理步骤。

然后，我们将通过 TensorFlow **file_io** 函数授权并将工件图像推送到 GCS 存储桶中，之后我们将创建静态 HTML 以发布到 Kubeflow 仪表板中。它从存储桶位置提取图像，该图像我们之前保存在以下路径 **gs://Kubeflowusecase/breast/visualize/correlation.html** 中，并以 json 格式转储了元数据。我们已拆分数据并为下一步训练转储了数据。

在创建 Docker 文件之前，请确保我们拥有服务 **service_account_iam.json** 文件，该文件将用于云存储桶访问。

请点击以下链接下载 json 密钥，并将其粘贴到 **预处理** 文件夹中：

https://cloud.google.com/iam/docs/creating-managing-service-account-keys

JSON 文件将如下所示：

```
{"type": "service_account",
"project_id": "project-id",
"private_key_id": "key-id",

"private_key": "-----BEGIN PRIVATE KEY-----\nprivate-key\n-----END PRIVATE KEY-----\n",
"client_email": "service-account-email",
"client_id": "client-id",
"auth_uri": "https://accounts.google.com/o/oauth2/auth",
"token_uri": "https://accounts.google.com/o/oauth2/token",
"auth_provider_x509_cert_url":
"https://www.googleapis.com/oauth2/v1/certs",
"client_x509_cert_url":
"https://www.googleapis.com/robot/v1/metadata/x509/service-account-email"}
```

创建服务账号时，搜索 **云** 然后选择 **存储**

![](img/8f8a671916d96b455297952d0f37b96c_129_0.png)

### 图 2.11：服务账号云存储选择

前面的屏幕截图显示了我们将为服务账号授予的角色。

同样，我们将创建 Docker 镜像，并添加服务账号 json 密钥。

## Docker：

```
FROM python:3.7-slim-stretch
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && apt-get -y install gcc mono-mcs g++ git curl && \
rm -rf /var/lib/apt/lists/*
RUN mkdir /app
WORKDIR /app
COPY service_account_iam.json
```

```
ENV GOOGLE_APPLICATION_CREDENTIALS="service_account_iam.json"
ADD requirements.txt /app/requirements.txt
RUN pip3 install -r requirements.txt
ADD dataextract.py /app/preprocessing.py
RUN chmod +x /app/preprocessing.py
ENTRYPOINT ["python"]
CMD ["/app/processing.py"]
```

与前一步类似，在数据摄取步骤中，我们将构建 Docker 镜像。

现在，从 Dockerfile 位置构建 Docker 镜像，并将其推送到 GCS 容器注册表中。您可以在 GCP 存储桶中获取整个文件夹，您所需要做的就是重命名 Docker 镜像名称，并运行 Docker build 和 push 命令。

### 2.3.3 训练模型组件

在本节中，我们将构建一个 TensorFlow 模型，然后构建分布式模型策略，将模型保存到 GCP 存储桶中，并将 Tensorboard 日志推送到存储桶中以供 Kubeflow Dashboard Tensorboard 可视化使用。

让我们看看我们将如何构建组件 **pipeline.py** 文件。

### train.py：

```
from __future__ import absolute_import, division, print_function, unicode_literals
import click, dill, json, logging, os
import pandas as pd
import tensorflow as tf
from storage import Storage

def model_build(Xtrain):
    model = tf.keras.models.Sequential([
        tf.keras.layers.Dense(units=32,
                              kernel_initializer='glorot_uniform', activation='relu', input_shape=(len(Xtrain.columns),)),
        tf.keras.layers.Dense(units=64,
                              kernel_initializer='glorot_uniform', activation='relu'),
        tf.keras.layers.Dropout(0.5),
```

```
tf.keras.layers.Dense(units=64,
                      kernel_initializer='glorot_uniform', activation='relu'),
tf.keras.layers.Dropout(0.5),
tf.keras.layers.Dense(units=1, kernel_initializer='glorot_uniform',
                      activation='sigmoid')])
    return model

def get_callbacks(path):
    checkpointdir = path
    class customLog(tf.keras.callbacks.Callback):
        def on_epoch_end(self, epoch, logs={}):
            logging.info('epoch: {}'.format(epoch + 1))
            logging.info('loss={}'.format(logs['loss']))
            logging.info('accuracy={}'.format(logs['accuracy']))
            logging.info('val_loss={}'.format(logs['val_loss']))
            logging.info('val_accuracy={}'.format(logs['val_accuracy']))
    callbacks = [tf.keras.callbacks.ModelCheckpoint(filepath=checkpointdir), customLog()]
    return callbacks

@click.command()
@click.option('--epochs', default=100)
@click.option('--batch-size', default=4)
@click.option('--learning-rate', default=0.001)
@click.option('--tensorboard-logs', default='/mnt/logs/')
@click.option('--tensorboard-gcs-logs', default='gs://kubeflowusecases/breast/logs')
@click.option('--model-output-base-path', default="/mnt/saved_model")
```

```
@click.option('--gcs-path', default="gs://kubeflowusecases/breast/model")
@click.option('--mode', default="local")
def train_model(train_file, test_file, validation_file, train_target, test_target, validation_target,
                batch_size, learning_rate, tensorboard_logs, tensorboard_gcs_logs, model_output_base_path, gcs_path, mode, epochs):
    with open(train_file, 'rb') as in_f:
        train = dill.load(in_f)
```

所以，这是代码的延续，我们声明了用于回调和模型构建函数的实用函数，以及 @click 用于输入之前的管道输出，这些输出将在这里用作输入，同时还有这些管道参数如 epoch、学习率等的新的输入。

```
with open(test_file, 'rb') as in_f:
    test = dill.load(in_f)
with open(validation_file, 'rb') as in_f:
    validation = dill.load(in_f)
with open(train_target, 'rb') as in_f:
    train_tar = dill.load(in_f)
with open(test_target, 'rb') as in_f:
    test_tar = dill.load(in_f)
with open(validation_target, 'rb') as in_f:
    validation_tar = dill.load(in_f)

strategy = tf.distribute.experimental.MultiWorkerMirroredStrategy()
```

```python
logging.info("Number of devices:\n{o}".format(strategy.num_replicas_in_sync))
with strategy.scope():
    optimizer = tf.keras.optimizers.Adam(learning_rate)
    model = model_build(train)
    model.compile(optimizer=optimizer,
                  loss=tf.keras.losses.binary_crossentropy, metrics=['accuracy'])
    TF_STEPS_PER_EPOCHS = 5
    BATCH_SIZE = batch_size * strategy.num_replicas_in_sync
    tensorboard_callback = tf.keras.callbacks.TensorBoard(log_dir=tensorboard_logs,
                                                           histogram_freq=1)
    logging.info("Training starting...")

    model.fit(train, train_tar, epochs=epochs, batch_size=BATCH_SIZE,
              validation_data=(validation, validation_tar), callbacks=
              [tensorboard_callback])
    logging.info("Training completed.")
    model.save(model_output_base_path)
    new_model = tf.keras.models.load_model(model_output_base_path)
    # Check its architecture
    print(new_model.summary())
    Storage.upload(tensorboard_logs, tensorboard_gcs_logs)
    metadata = {
        'outputs': [{'type': 'tensorboard', 'source': tensorboard_gcs_logs,}]}
    with open("/mlpipeline-ui-metadata.json", 'w') as f:
        json.dump(metadata, f)
    if mode != 'local':
        print("uploading to {o}".format(gcs_path))
        Storage.upload(model_output_base_path, gcs_path)
    else:
        print("Model will not be uploaded")
```

```python
pass

if __name__ == "__main__":
    train_model()
```

所以，前面的内容是 **train.py** 文件；让我们按如下方式拆解管道代码：

首先我们导入所有所需的数据集。

然后 **@click** 命令会将参数传递给函数

然后 **dill** 命令将帮助从 PVC 保存或加载数据。

接下来，我们将从外部传入诸如 epochs 和 batch size、learning rate 等参数并训练我们的模型。

我们将把模型训练输出推送到 Google Storage Bucket。我们已导入 **Storage.py** 文件到 Storage 类以保存我们的模型产物。

接下来，我们将可视化 Tensorboard 并遵循相同的 metadata json 格式，并提供 GCS 存储桶路径，在该路径下保存你的模型产物。

对于 Python 可视化，你可以访问以下链接：

https://www.Kubeflow.org/docs/pipelines/sdk/output-viewer/

在创建 Docker 文件之前，请确保复制我们之前创建的服务 **service_account_iam.json** 文件，该文件将用于云存储桶访问，并且 **storage.py** Python 文件将用于将数据上传到 GCS 存储桶。

![](img/8f8a671916d96b455297952d0f37b96c_136_0.png)

## 图 2.12：训练文件夹结构

同样，我们将创建 Docker 镜像并添加服务账号 json 密钥。

## Docker:

```
FROM python:3.7-slim-stretch
ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update && \
apt-get -y install gcc mono-mcs g++ git curl && \
rm -rf /var/lib/apt/lists/*
RUN mkdir /app
WORKDIR /app
ADD requirements.txt /app/requirements.txt
RUN pip3 install -r requirements.txt
COPY service_account_iam.json /app/service_account_iam.json
ENV GOOGLE_APPLICATION_CREDENTIALS="service_account_iam.json"
ADD train.py /app/train.py
ADD storage.py /app/storage.py
RUN chmod +x /app/train.py
ENTRYPOINT ["python"]
CMD ["/app/train.py"]
```

接下来我们将创建 Docker 镜像并将其推送，方式与我们在数据提取部分上面所做的类似。

### 2.3.4 评估组件

同样，我们将创建评估组件。请查看 GitHub **steps.md** 文件。

以下是我们在评估组件中完成工作的几个重要要点：

我们已将混淆矩阵和 ROC 曲线以 csv 格式转储到 GCP 存储桶中，并在元数据中给出这些内容的存储位置路径，并将其转储为 json，以便 Kubeflow pipeline 可以获取并可视化 ROC & 混淆矩阵。

## 2.5 使用 KF Serving 提供模型服务

在本节中，我们将为我们的模型构建服务。在下面的截图中，我们可以看到模型服务 Dockerfile 的三个主要组件是模型文件夹、Dockerfile，

因此，这里我们将本地保存的训练模型保留在 Docker 文件的根目录或 Cloud Storage 存储桶中。

![](img/8f8a671916d96b455297952d0f37b96c_139_0.png)

## 图 2.13：KF – Serving 组件文件夹结构

## KF-Serving 架构：

InferenceService 数据平面架构由一个静态组件图组成，该图协调针对单个模型的请求。

![](img/8f8a671916d96b455297952d0f37b96c_140_0.png)

## 图 2.14：KF – Serving 架构

**Endpoint:** InferenceServers 被分为两个端点 – "default" 和 "canary"。端点允许用户使用 Pinned 和 Canary 滚动策略安全地进行更改。Canarying 完全是可选的，使用户能够仅在 "default" 端点上使用 BlueGreen 部署策略进行部署。

**Component:** 每个端点由多个组件组成 – "predictor"、"explainer" 和 "transformer"。唯一必需的组件是 predictor，它是系统的核心。随着 KFServing 的发展，我们计划增加支持的组件数量以实现诸如 Outlier Detection 之类的用例。

**Predictor:** predictor 组件是 InferenceService 的主力。它只是一个模型和一个模型服务器，使其在网络端点可用。

**Explainer:** 它启用了一个可选的替代数据平面，除了预测之外还提供我们的模型解释。因此，用户还可以定义自己的解释容器，KFServing 将使用相关的环境变量如 prediction endpoint 对其进行配置。对于常见场景，KFServing 提供了开箱即用的解释器如 Alibi。

**Transformer:** transformer 使用户能够在预测和解释工作流之前定义预处理和后处理步骤。与 explainer 类似，它也使用相关的环境变量进行配置。对于常见用例，KFServing 提供了开箱即用的 transformers 如 Feast。

这里，我们将使用自定义镜像服务，原因如下：

自定义镜像支持的目标是允许用户将自己的包装模型带入容器中并使用 KFServing 提供服务。在这里，在此示例中，位于 model-server 目录下扩展了 kfserving。KFModel 使用 tornado web server。

你可以使用 KFServing 执行以下操作：
- 为任意框架上的 ML 模型服务提供 Kubernetes Custom Resource Definition。
- 封装自动扩缩容、网络、健康检查和服务器配置的复杂性，将前沿服务功能如 GPU 自动扩缩容、缩容至零和金丝雀发布带入你的 ML 部署。
- 通过提供开箱即用的预测、预处理、后处理和可解释性，为你的生产 ML 推理服务器提供简单、可插拔且完整的解决方案。

让我们看看我们将如何构建服务组件 **Transformer.py** 文件。

```
Transformer.py:
import tensorflow as tf
import sys, os, json, kfserving
import numpy as np
import kfserving
from typing import List, Dict

os.environ['GOOGLE_APPLICATION_CREDENTIALS'] = "service_account_iam.json"
```

```
class KFServingSampleModel(kfserving.KFModel):

    def __init__(self, name: str):
        super().__init__(name)
        self.name = name
        self.ready = False
        self.model_output_base_path = "gs://kubeflowusecases/breast/model/"

    def load(self):
        model = tf.keras.models.load_model(self.model_output_base_path)
        self.model = model
        self.ready = True

    def predict(self, request: Dict) -> Dict:
        inputs = np.array(request["instances"])
        reshaped_to_2d = np.reshape(inputs, (-1, len(inputs)))
        results = self.model.predict(reshaped_to_2d)
        result = (results > 0.5) * 1
        if result == 1:
            result = "malignant"
        else:
            result = "Benign"
        print("result : {0}".format(result))
        return {"predictions": result}

if __name__ == "__main__":
    model = KFServingSampleModel("kfserving-breast-model")
    model.load()
    kfserving.KFServer(workers=1).start([model])
```

所以让我们按如下方式拆解 transformer predictor 代码：

我们将具有存储桶的服务账号保留在 Docker 根目录中，然后将其声明为环境变量到对象 **model_output_base_path**，用于 gcp 存储桶路径。

接下来，在 Load 函数中，我们从 TensorFlow 库加载了模型。

然后，在 predict 方法中，传入的数据将以 json 格式出现，我们需要将其提取为键值对并进行必要的预测并作为字典返回。

因此，在 “main” 函数中，**KFServingSampleModel** 类接收该部署的名称；请注意这一点并应用到 yaml 文件中；这里是 "kfserving-breast-model"

接下来，我们将为我们的服务模型构建 Docker 镜像。

## Docker:

```
FROM python:3.7-slim-stretch
ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update && \
apt-get -y install gcc mono-mcs g++ git curl bash && \
rm -rf /var/lib/apt/lists/*
RUN mkdir /app
```

```
WORKDIR /app
ADD requirements.txt /app/requirements.txt
RUN pip install -r /app/requirements.txt
ADD servebreast.py /app/servebreast.py
COPY service.json
ENV GOOGLE_APPLICATION_CREDENTIALS="service.json"
CMD ["python","servebreast.py"]
```

现在，在前面的 Docker 代码中，我们已复制用于存储桶访问的服务账号并将其保存到 然后，我们在同一位置复制了 Python 服务文件并将工作目录保持为 然后，我们使用以下代码构建了镜像。同样，我们创建了 Docker 镜像；请查看 GitHub steps.md 文件。

要使用 kubectl 命令行或使用 KF Serving 客户端 SDK 部署模型服务器，请完成以下步骤：

- 使用命令行部署。
- 使用 KF Serving 客户端 SDK 部署。

## 使用命令行部署：

现在，让我们使用命令行部署它，但首先让我们填充 yaml 文件。

## Custom_KFServing.yaml:

```
apiVersion: serving.kubeflow.org/v1alpha2
kind: InferenceService
```

```
metadata:
annotations:
sidecar.istio.io/inject: "false"

name: kfserving-breast-model
namespace: kubeflow
spec:
default:
predictor:
custom:
container:
image: gcr.io//breast_cancer/custom_serving:v1
```

这里，在前面的 yaml 文件中，我们将使用在 Transformer.py 文件中提供的相同名称，其中包含模型名称，然后我们将提供命名空间“Kubeflow”，它将在其中部署。接下来，我们将为我们创建的 Transformer 模型提供一个 Docker 镜像名称。

![](img/8f8a671916d96b455297952d0f37b96c_146_0.png)

## 图 2.15：KF – Serving 模型名称匹配

正如我们在前面的截图中看到的，左侧图像中的第 38 行和右侧的第 6 行应始终相同。

接下来，从 Visual Studio 中保存文件的位置在 bash 中运行以下命令。

使用以下命令连接到 GCP 集群：

```
gcloud container clusters get-credentials <$ClusterName> --zone <$ZONE> --project <$PROJECTID>
```

通过在集群中部署它来创建推理服务：

```
kubectl apply -f custom_breast_model.yaml
```

检查推理服务。间隔一段时间后尝试检查是否已创建：

```
kubectl get inferenceservice -n Kubeflow
```

![](img/8f8a671916d96b455297952d0f37b96c_147_0.png)

## 图 2.16：KF – Serving 推理输出

## 示例预测：

从 serving 文件夹在 Bash 中运行以下命令：

```
```bash
MODEL_NAME=kfserving-braintumor
HOST=$(kubectl get inferenceservice -n Kubeflow $MODEL_NAME -o jsonpath='{.status.url}' | cut -d "/" -f 3)
INPUT_PATH=@./data.json
CLUSTER_IP=$(kubectl -n istio-system get service kfserving-ingressgateway -o jsonpath='{.status.loadBalancer.ingress[0].ip}')
curl -v -H "Host: ${HOST}"
http://${CLUSTER_IP}/v1/models/${MODEL_NAME}:predict -d $INPUT_PATH
```
```

现在，以下是响应预测请求：

```
* Trying [redacted].
* TCP_NODELAY set
* Connected to [redacted] ([redacted] port 80 (#0)
> POST /v1/models/kfserving-breast-model:predict HTTP/1.1
> Host: kfserving-breast-model.kubeflow.example.com
> User-Agent: curl/7.64.1
> Accept: */*
> Content-Length: 256
> Content-Type: application/x-www-form-urlencoded
>
* upload completely sent off: 256 out of 256 bytes
< HTTP/1.1 200 OK
< content-length: 28
< content-type: application/json; charset=UTF-8
< date: Fri, 24 Jul 2020 05:40:42 GMT
< server: istio-envoy
< x-envoy-upstream-service-time: 11796
<
* Connection #0 to host [redacted] left intact
{"predictions": "malignant"}* Closing connection 0
```

图 2.17：KF – Serving 预测输出

从 serving 文件夹在 Python 中运行以下命令：

现在，我们将创建一些示例数据以从前面的 URL 预测结果。以下是创建示例数据的代码：

```
import base64,json,requests
from sklearn.datasets import load_breast_cancer
import pandas as pd
import numpy as np
from sklearn.model_selection import train_test_split
cancer = load_breast_cancer()
```

```
df_cancer = pd.DataFrame(np.c_[cancer['data'], cancer['target']],
columns = np.append(cancer['feature_names'], ['target']))

X = df_cancer.drop(['target'],axis=1)
y = df_cancer['target']
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size =
0.1, random_state = 0)
data = json.dumps({"instances": X_test.iloc[7].to_list()})
data
```

![](img/8f8a671916d96b455297952d0f37b96c_150_0.png)

图 2.18：示例数据

```
MODEL_NAME="kfserving-breast-model"
cluster_ip = YOUR CLUSTER IP HERE
headers={"Host": "{0}.Kubeflow.example.com".format(MODEL_NAME)}
response =
requests.post("http://{0}/v1/models/{1}:predict".format(cluster_ip,
MODEL_NAME), data = data,headers = headers)
response.json()
```

![](img/8f8a671916d96b455297952d0f37b96c_150_1.png)

图 2.19：预测输出

正如我们在前面的截图中看到的，我们的预测输出为恶性。

## 2.6 端到端构建管道

现在，让我们看看如何构建 Pipeline，并将在 Kubeflow Notebook 服务器中运行此平台。

打开 URL：GCP Kubernetes > Service & ingress > 点击 URL。

![](img/8f8a671916d96b455297952d0f37b96c_152_0.png)

图 2.20：Ingress URL

如第 1 章《Kubeflow 和 Kubernetes 云架构简介》第 1.6 节所述，我们已创建了一个 Jupyter notebook，我们将使用它。

![](img/8f8a671916d96b455297952d0f37b96c_152_1.png)

图 2.21：Notebook Server 输出

现在，粘贴以下代码并运行管道；在之前请将以下代码中的 PROJECT_ID 和存储桶名称替换掉，它将转储一个 zip 文件：

```
```
import kfp.dsl as dsl
import yaml
from kubernetes import client as k8s
import kfp.gcp as gcp
from kfp import components
from string import Template
import json
from kubernetes import client as k8s_client

@dsl.pipeline(

name='breast cancer pipeline',
description='End to End pipeline for Tensorflow Breast Cancer')
def breast_cancer_tensorflow_pipeline(
dataextraction_step_image="gcr.io/<$PROJECT_ID>/breast_cancer/step1_loadingdata",
dataprocessing_step_image="gcr.io/<$PROJECT_ID>/breast_cancer/step2_dataprocessing",
trainmodel_step_image="gcr.io/<$PROJECT_ID>/breast_cancer/step3_training_model",
evaluator_step_image="gcr.io/<$PROJECT_ID>/breast_cancer/step4_evaluation_model",
train_file='/mnt/training.data',
data_file="/mnt/breast.data",
test_file='/mnt/test.data',
validation_file="/mnt/validation.data",
split_size=0.2,
train_target="/mnt/trainingtarget.data",
test_target="/mnt/testtarget.data",
```

```
validation_target="/mnt/validationtarget.data",
epochs=5,
learning_rate=.001,
batch_size=64,
shuffle_size=1000,
tensorboard_logs="/mnt/logs/",
tensorboard_gcs_logs="gs://<$YOUR_BUCKET>/breast/logs",
model_output_base_path="/mnt/saved_model",
gcs_path="gs://<$YOUR_BUCKET>/breast/model",

gcs_path_confusion="gs://<$YOUR_BUCKET>/breast",
mode="gcs",
probability=0.5,
serving_name="kfserving-breast-model",
serving_namespace="Kubeflow",
image="gcr.io/<$PROJECT_ID>/breast_cancer/custom_serving_nermodel"):
"""
Pipeline
"""

# PVC : PersistentVolumeClaim volume
vop = dsl.VolumeOp(
name='my-pvc',
resource_name="my-pvc",
modes=dsl.VOLUME_MODE_RWO,
size="1Gi"
)
# data extraction
data_extraction_step = dsl.ContainerOp(
name='data_extraction',
image=dataextraction_step_image,
command="python",
```

```
```python
arguments=[
"/app/dataextract.py",
"--data-file", data_file],
pvolumes={"/mnt": vop.volume})

# processing
data_processing_step = dsl.ContainerOp(
name='data_processing',

image=dataprocessing_step_image,
command="python",
arguments=[
"/app/preprocessing.py",
"--train-file", train_file,
"--test-file", test_file,
"--validation-file", validation_file,
"--data-file",data_file,
"--split-size",split_size,
"--train-target",train_target,
"--test-target",test_target,
"--validation-target",validation_target],
pvolumes={"/mnt": data_extraction_step.pvolume})
#trainmodel
train_model_step = dsl.ContainerOp(
name='train_model',
image=trainmodel_step_image,
command="python",
arguments=[
"/app/train.py",
"--train-file", train_file,
"--test-file", test_file,
"--validation-file", validation_file,
```
```



```
"--train-target", train_target,
"--test-target", test_target,
"--validation-target", validation_target,
"--epochs", epochs,
"--batch-size", batch_size,
"--learning-rate", learning_rate,

"--tensorboard-logs", tensorboard_logs,
"--tensorboard-gcs-logs", tensorboard_gcs_logs,
"--model-output-base-path", model_output_base_path,
"--gcs-path", gcs_path,
"--mode", mode],
pvolumes={"/mnt": data_processing_step.pvolume})
```

# evaluation_model
evaluation_model_step = dsl.ContainerOp(
name='evaluation_model',
image=evaluator_step_image,
command="python",
arguments=[
"/app/evaluator.py",
"--test-file", test_file,
"--test-target", test_target,
"--probability", probability,
"--model-output-base-path", model_output_base_path,
"--gcs-path", gcs_path,
"--gcs-path-confusion", gcs_path_confusion],
pvolumes={"/mnt": train_model_step.pvolume})

kfserving_template = Template("""{
"apiVersion": "serving.Kubeflow.org/v1alpha2",
```
"kind": "InferenceService",
"metadata": {
"labels": {
"controller-tools.k8s.io": "1.0"},
"name": "$name",
"namespace": "$namespace"},
"spec": {

"default": {
"predictor": {
"custom": {
"container": {
"image": "$image"}}}}})""")
kfservingjson = kfserving_template.substitute({'name':
str(serving_name),
'namespace': str(serving_namespace),
'image': str(image)})
kfservingdeployment = json.loads(kfservingjson)
serve = dsl.ResourceOp(
name="serve",
k8s_resource=kfservingdeployment,
action="apply",
success_condition="status.url")
serve.after(evaluation_model_step)

if __name__ == '__main__':
import kfp.compiler as compiler
pipeline_func = breast_cancer_tensorflow_pipeline
pipeline_filename = pipeline_func.__name__ + '.pipeline.zip'
compiler.Compiler().compile(pipeline_func,pipeline_filename)
```

现在，让我们按如下方式拆解管道代码：

Pipelines are expected to include a **@dsl.pipeline** decorator to provide the metadata about the pipeline.

The pipeline is defined in the **breast_cancer_tensorflow_pipeline** function. It includes a number of arguments, which are exposed in the Kubeflow Pipelines UI when creating a new Run. Although passed as strings, these arguments are of type

Each individual block defines one component like ‘train’, ‘evaluation’, and so on. A component is made up of a **kfp.dsl.ContainerOp** object with the container path and a specified name. The container image used is defined as the Docker file which we have created.

After defining the train component, we also set a number of environment variables for the training script.

At the bottom of the script is the main function. This is used to compile the pipeline when the script is run; next, the **.after** method will trigger the pipeline one after the other.

When you run the preceding code, it will dump a zip like the following:

![](img/8f8a671916d96b455297952d0f37b96c_159_0.png)

图 2.22：管道 zip

Next, we will create an experiment; under that, we can create multiple runs of a pipeline. The following code is for creating the experiment:

```
import kfp
from kfp import compiler
import kfp.components as comp
import kfp.dsl as dsl
from kfp import gcp
EXPERIMENT_NAME = 'Breast'
client = kfp.Client()
```

try:

```
experiment =
client.get_experiment(experiment_name=EXPERIMENT_NAME)
except:
experiment = client.create_experiment(EXPERIMENT_NAME)
print(experiment)
```

The following snippet will create a run for the zip that we have dumped in that location:

```
arguments = {}
run_name = pipeline_func.__name__ + 'breast_run'
run_result = client.run_pipeline(experiment.id, run_name,
pipeline_filename, arguments)
```

```
print(experiment.id)
print(run_name)
print(pipeline_filename)
print(arguments)
```

Click on the run link, once the pipeline is ready. The following is how our pipeline training looks:

![](img/8f8a671916d96b455297952d0f37b96c_161_0.png)

图 2.23：训练管道输出

The following is how our pipeline Serving looks:

![](img/8f8a671916d96b455297952d0f37b96c_161_1.png)

图 2.24：服务管道输出

The following screenshot is of the pipeline which we have created and the Python visualizations, tables and static HTML plots:

![](img/8f8a671916d96b455297952d0f37b96c_162_0.png)

图 2.25：服务管道输出

Next, let’s find out how to Monitor an endpoint in Grafana.

## 2.7 使用 Grafana 仪表板监控性能

Run the command in the Google Cloud shell after connecting the Cluster and then Create Namespace.

```bash
gcloud container clusters get-credentials <$ClusterName> --zone <$ZONE> --project <$PROJECTID>
#create namespace
kubectl create namespace knative-monitoring
#setup monitoring components
kubectl apply --filename https://github.com/knative/serving/releases/download/v0.177.20/monitoring-metrics-prometheus.yaml
```

![](img/8f8a671916d96b455297952d0f37b96c_163_0.png)

图 2.26：Prometheus 部署

Next, run from the Local Terminal and open the `grafana` dashboard by using `localhost:8080` on the browser. Explore the different components of the grafana dashboard.

```bash
kubectl port-forward --namespace knative-monitoring $(kubectl get pod --namespace knative-monitoring --selector="app=grafana" --output jsonpath='{.items[0].metadata.name}') 8080:3000
```

Hit the Curl request from bash and see the output in the Dashboard.

```
curl -v -H "Host: ${HOST}"
http://${CLUSTER_IP}/v1/models/${MODEL_NAME}:predict -d $INPUT_PATH
```

![](img/8f8a671916d96b455297952d0f37b96c_165_0.png)

图 2.27：Grafana 仪表板内容

The preceding dashboard is for the contents of Grafana; we can click on the individual section and see the reports there.

The following Dashboard talks about the HTTP requests for Knative Serving Visualization which we serve per/sec request.

![](img/8f8a671916d96b455297952d0f37b96c_165_1.png)

图 2.28：Grafana 仪表板 HTTP 请求

So, the following is the Dashboard for the Control Plane which shows the CPU Usage and memory usage efficiency.

![](img/8f8a671916d96b455297952d0f37b96c_166_0.png)

图 2.29：Prometheus 仪表板

## 2.8 结论

In this chapter, we learned how to build end-to-end Kubeflow Orchestrator Pipeline for a TensorFlow Model and how to Dockerize each component and build it in Google Platform.

Then, we learned how to build the pipeline with the kfp library package and triggered the pipeline from the Kubeflow Dashboard. We have now deployed the Kubeflow on the Kubernetes Platform and learned how to trigger the pipeline from the Notebook. We have also deployed the model in the Kubernetes cluster with the KF serving and monitored our prediction results in the Grafana Dashboard.

We have also learned how to leverage the power of Google Cloud Platform, and use our Devops knowledge with Machine Learning to become an MLops.

## 2.9 参考

https://knative.dev/docs/serving/autoscaling/autoscaling-concepts/

https://v1-1-branch.Kubeflow.org/docs/

https://v1-1-branch.Kubeflow.org/docs/gke/

https://v1-1-branch.Kubeflow.org/docs/gke/monitoring/

# 在 Kubeflow 中设计计算机视觉模型

In this chapter, we will build an end-to-end TensorFlow Computer Vision Model with OpenCV operation and deploy that with the Kubeflow Orchestration, which includes deploying Kubeflow in Kubernetes Cluster in GCP, building the pipeline components for the model with Docker and Kubeflow SDK, and then serving the Model with KF serving to have an endpoint for prediction. We will then perform the monitor and performance in Grafana Dashboard.

## 结构

In this chapter, we will cover the following topics:

- 问题陈述
- 在 GCP Kubeflow 和 Docker 设置中入门
- 问题陈述背后的分析
- 为计算机视觉（CNN）TensorFlow 模型构建 Kubeflow Pipeline 组件
- 使用 KF Serving 提供模型
- 端到端构建管道
- 服务端点的自动扩缩容




## 目标

在本章中，我们将学习以下内容：

- 如何设置 Docker 和 Kubernetes 以构建 Kubeflow Pipeline。
- 如何使用 OpenCV 库预处理图像，并为训练模型构建数据，以及它将如何用于 Kubeflow pipeline。
- 如何从 Kaggle 等外部来源进行数据摄取以及如何进行批量预测。
- 如何构建单个流水线组件，如训练和模型评估。
- 如何使用 KF serving 提供模型服务，并预测模型请求并通过 Grafana Dashboard 监控。
- 如何使用 Kubernetes 和多个 Google Cloud Platform 来利用 Devops 知识下的机器学习能力。
- 如何使用 TensorFlow 的预训练模型权重并将其用于模型构建。

## 如何根据并发请求和目标并发数自动扩缩 kf-serving 推理服务。

## 3.1 问题陈述

这里，我们有一个脑癌 X 射线图像的分类数据集，它有两个类别的文件夹，一个包含 Brain Tumor，另一个不包含；我们将从 Kaggle 发布数据并构建端到端的分类模型；之后我们需要部署它。

No tumor, encoded as 0

Tumor, encoded as 1

| 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 |
|---|
| 1 |

## 3.2 在 GCP 上开始 Kubeflow 设置

在开始本章之前，我们必须在 GCP 中设置 Kubeflow 集群；请参阅 _第 1 章，Kubeflow 和 Kubernetes 云简介_ 第 1.6 节（在 GCP 上开始 Kubeflow 设置）。

## 3.3 问题陈述背后的分析

该项目的主要目的是构建一个 CNN 模型，该模型将根据 MRI 扫描判断受试者是否患有肿瘤。我们使用了 **VGG-16** 模型架构和权重来为此二分类问题训练模型。我们使用准确率作为指标来证明模型性能，可定义如下：

### 什么是脑肿瘤？

脑部癌性或非癌性的异常细胞团块或生长。肿瘤可能起源于大脑，或身体其他部位的癌症可能扩散到大脑。这些症状可能包括头痛、癫痫发作、视力问题、呕吐和精神变化。头痛通常在早上更严重，呕吐后会消失。其他症状可能包括行走、说话困难或其他感觉困难。随着疾病进展，可能出现意识丧失。

在这里，我们的目标是计算图像中脑扫描轮廓上的极值点；沿给定轮廓找到极北、极南、极东和极西的 (x, y) 坐标。此方法可用于原始轮廓和旋转边界框。

让我们导入所需的库。

```
from IPython.display import clear_output
!pip install imutils
clear_output()
import numpy as np
from tqdm import tqdm
import cv2,os, shutil, itertools, imutils
```

```
import plotly.express as px
from skimage import io
import plotly.graph_objs as go
from plotly.offline import init_notebook_mode, iplot
from plotly import tools
from plotly.subplots import make_subplots
```

以下函数对图像进行阈值处理并执行一系列腐蚀和膨胀以去除任何小的噪声区域；接下来它在阈值图像中查找轮廓，然后抓取最大的一个。最后，它找到极值点以裁剪图像，并返回所有步骤数组，以便我们可以绘制它们。

```
def analytics(filepath):
    IMG_SIZE = (224,224)
    img = cv2.imread(filepath)
    img = cv2.resize(img, dsize=IMG_SIZE,
    interpolation=cv2.INTER_CUBIC)
    gray = cv2.cvtColor(img, cv2.COLOR_RGB2GRAY)
    gray = cv2.GaussianBlur(gray, (5, 5), 0)
    # threshold the image, then perform a series of erosions +
    # dilations to remove any small regions of noise
    thresh = cv2.threshold(gray, 45, 255, cv2.THRESH_BINARY)[1]
```

```
```python
thresh = cv2.erode(thresh, None, iterations=2)
thresh = cv2.dilate(thresh, None, iterations=2)
# find contours in thresholded image, then grab the largest one
cnts = cv2.findContours(thresh.copy(), cv2.RETR_EXTERNAL,
cv2.CHAIN_APPROX_SIMPLE)
cnts = imutils.grab_contours(cnts)

c = max(cnts, key=cv2.contourArea)
# find the extreme points
extLeft = tuple(c[c[:, :, 0].argmin()][0])
extRight = tuple(c[c[:, :, 0].argmax()][0])
extTop = tuple(c[c[:, :, 1].argmin()][0])
extBot = tuple(c[c[:, :, 1].argmax()][0])
# add contour on the image
img_cnt = cv2.drawContours(img.copy(), [c], -1, (0, 255, 255), 4)
# add extreme points
img_pnt = cv2.circle(img_cnt.copy(), extLeft, 8, (0, 0, 255), -1)
img_pnt = cv2.circle(img_pnt, extRight, 8, (0, 255, 0), -1)
img_pnt = cv2.circle(img_pnt, extTop, 8, (255, 0, 0), -1)
img_pnt = cv2.circle(img_pnt, extBot, 8, (255, 255, 0), -1)
# crop
ADD_PIXELS = 0
new_img = img[extTop[1]-ADD_PIXELS:extBot[1]+ADD_PIXELS,
extLeft[0]-ADD_PIXELS:extRight[0]+ADD_PIXELS].copy()
return img,img_cnt,img_pnt,new_img
```
```

这里，我们可以通过从 GitHub 链接下载示例数据文件夹来调用该函数。

```
```python
img,img_cnt,img_pnt,new_img=analytics('//Sample_Tumor_Data/Y2.jpg')
```
```

接下来，我们将创建一个实用的 plotly 函数，利用 plotly 绘制原始图像和裁剪后图像的极值点。

```
def make_subplots_image(img,img_cnt,img_pnt,new_img):
fig = make_subplots(1, 4, horizontal_spacing=0.08)

fig.add_trace(go.Image(z=img), 1, 1)
fig.add_trace(go.Image(z=img_cnt), 1, 2)
fig.add_trace(go.Image(z=img_pnt), 1, 3)
fig.add_trace(go.Image(z=new_img), 1, 4)
fig['layout']['xaxis1'].update(showgrid=False, title= 'Original image')
fig['layout']['xaxis2'].update(showgrid=False, title='Find the biggest contour')
fig['layout']['xaxis3'].update(showgrid=False, title='Find the extreme points')
fig['layout']['xaxis4'].update(showgrid=False, title='Crop the image')
fig.update_layout(height=400, width=1500)
fig.show()
```

调用前述函数：

**make_subplots_image(img,img_cnt,img_pnt,new_img)**

![](img/8f8a671916d96b455297952d0f37b96c_178_0.png)

### 图 3.1：脑扫描的极值点

现在，我们将在流水线构建阶段对训练数据的所有图像应用此转换。

## 3.4. 构建用于计算机视觉（CNN）TensorFlow 模型的 Kubeflow 流水线组件

在本节中，我们将看到构建各个组件时将使用的完整架构。

![](img/8f8a671916d96b455297952d0f37b96c_180_0.png)

图 3.2：CNN Kubeflow Pipeline 架构

从上图来看，让我们按如下方式分解组件概述：

数据摄取将由 Kaggle connector API 提供，我们将在 PVC 中下载它。它将用于后续的流水线组件。

接下来，我们将训练我们的 CNN TensorFlow 模型，并将其保存在 GCP 存储桶中。

之后，我们将评估模型性能，并在 Kubeflow Dashboard 中使用 ROC 和混淆矩阵可视化该实验运行。

最后，我们将部署模型以提供服务并从训练阶段保存的存储桶中加载该模型，然后在 Grafana 仪表板中检查模型端点性能流量。

我们将了解如何根据并发请求和目标并发数自动扩缩 kf-serving InferenceService，并且在这里我们将构建 KF serving 的批量预测。

### 3.4.1 数据提取或摄取组件

现在，让我们构建数据摄取组件；在这里我们将从 Kaggle 获取数据，并借助 Kaggle API 进行提取。

### dataextraction.py:

```
```python
from __future__ import absolute_import, division, print_function, unicode_literals
import click,json,os,dill,argparse,logging,shutil,itertools,Kaggle

@click.command()
@click.option('--data-file', default="/mnt/BrainScan_Data/")
@click.option('--root',default="/mnt/")
@click.option('--kaggle-api-data',default="navoneel/brain-mri-images-for-brain-tumor-detection")
def download_data(root,data_file,kaggle_api_data):
logging.info(kaggle.api.authenticate())
kaggle.api.dataset_download_files(kaggle_api_data, path=data_file, unzip=True)
logging.info("Downloaded Data")
print(len(os.listdir(data_file +"brain_tumor_dataset/no")))
print(len(os.listdir(data_file +"brain_tumor_dataset/yes")))
directory=["TRAIN", "TEST", "VAL", "TRAIN/YES", "TRAIN/NO", "TEST/YES", "TEST/NO", "VAL/YES", "VAL/NO"]
for i in directory:
```




```
path = os.path.join(root, i)
try:
    os.mkdir(path)
except OSError as error:
    print(error)

for CLASS in os.listdir(data_file):

logging.info(CLASS)
print(CLASS)
if not CLASS.startswith('.'):
    IMG_NUM = len(os.listdir(data_file + CLASS))
    logging.info(IMG_NUM)
    print(IMG_NUM)
    for (n, FILE_NAME) in enumerate(os.listdir(data_file + CLASS)):
        img = data_file + CLASS + '/' + FILE_NAME
        if n < 5:
            try:
                shutil.copy(img, '/mnt/TEST/' + CLASS.upper() + '/' + FILE_NAME)
            except OSError as error:
                print(error)
        elif n < 0.8*IMG_NUM:
            try:
                shutil.copy(img, '/mnt/TRAIN/'+ CLASS.upper() + '/' + FILE_NAME)
            except OSError as error:
                print(error)
        else:
            try:
                shutil.copy(img, '/mnt/VAL/'+ CLASS.upper() + '/' + FILE_NAME)
            except OSError as error:
```

```python
print(error)
return
if __name__ == "__main__":

download_data()
```

让我们按如下方式分解代码：

使用 Kaggle API 从 Kaggle DB 加载数据，并为其指定特定的项目名称。

导入所有所需的数据集。

**@click** 命令是在函数中传递参数

接下来，我们将为 Train、Test、Validation 创建单独的文件夹，并将原始数据随机混洗以填充 Tumour Yes 或 No Tumour 子文件夹中的所有文件夹。

所有文件夹都保存在 PVC 中，并在管道之后使用。

接下来，看看我们将如何为数据摄取构建组件 Dockerfile，我们将在 dockerfile 的根目录中保留 **requirements.txt** 文件，我们需要它作为在 Docker 内部运行 Python 函数的环境。然后，我们将在 Docker 根目录中放置 kaggle api json 文件，以便对 Kaggle 进行身份验证，从 Kaggle 项目下载数据。

要获取 Kaggle API json 文件，请参阅第 6 章《构建 Weights & Biases Pipeline》第 6.2.2 节（Kaggle API 设置）。

![](img/8f8a671916d96b455297952d0f37b96c_185_0.png)

图 3.3：dataextraction 文件夹

现在，我们将构建 Docker 镜像；为此请确保启动 Docker，您将在顶部看到 Docker 已激活。如我们所见，第一个图标 Docker 已启动。

## Docker：

```
FROM python:3.7-slim-stretch
ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update && \
apt-get -y install gcc mono-mcs g++ git curl && \
rm -rf /var/lib/apt/lists/*
RUN mkdir /app
RUN mkdir ~/.kaggle
WORKDIR /app
ADD requirements.txt /app/requirements.txt
RUN pip3 install -r requirements.txt
```

```
ADD dataextract.py /app/dataextract.py
ADD kaggle.json /app/kaggle.json
RUN chmod +x /app/dataextract.py

RUN cp /app/kaggle.json ~/.kaggle
RUN chmod 600 ~/.kaggle/kaggle.json
ENTRYPOINT ["python"]
CMD ["/app/dataextract.py"]
```

所以让我们按如下方式分解 Docker 文件代码：

加载 Python 镜像作为基础镜像以运行 3.7 版本的管道代码。

RUN 函数将在 Docker 镜像启动时运行，并首先使用 mkdir 命令创建 /app 文件夹，并为存储 kaggle API json 文件创建 ~/.kaggle 文件夹。

接下来，我们将把命令重定向到 WORKDIR，在那里安装所有文件和依赖项。

接下来，我们将在 /app 文件夹中 ADD requirements 文件，并运行 pip 命令安装 Python 库。

然后我们将复制我们的 dataextract.py Python 代码和 kaggle.json，并使用 chmod 命令授予管理权限，以便在 Docker 镜像运行时运行该文件。

接下来，我们将设置入口点为 Python，CMD 为首先运行此项。

现在，我们将构建 Docker 镜像；为此，请确保启动 Docker，您将在顶部看到 Docker 已激活。如我们所见，第一个图标 Docker 已启动。

通过本地连接 GCP 运行以下所有命令：

```bash
gcloud init

#Select the Email/Project associated with GCP
```

构建数据提取容器。

```bash
cd $WORKDIR/pipeline/dataextraction
PROJECT_ID=$(gcloud config get-value core/project)
IMAGE_NAME=brain_tumor_scan/step1_download_data
IMAGE_VERSION=v1
IMAGE_NAME=gcr.io/$PROJECT_ID/$IMAGE_NAME
```

构建 Docker 镜像：

```
docker build -t $IMAGE_NAME:$IMAGE_VERSION .
```

## 将训练镜像推送到 **Google 容器注册表**

```
docker push $IMAGE_NAME:$IMAGE_VERSION
```

接下来，我们将了解如何构建训练组件，与上面类似，之后我们将为我们的 Kubeflow 管道构建预处理步骤。

### 3.4.2 数据预处理组件

现在，我们将构建预处理步骤，假设输入将来自之前的数据摄取组件。因此，我们将首先加载使用 @dill 命令转储的任何数据，并执行必要的预处理步骤。

在这部分代码中，让我们导入所有依赖项并创建实用相关性绘图函数。

### Preprocessing.py

```
from __future__ import absolute_import, division, print_function, unicode_literals
import click,json,os,argparse,dill,cv2,imutils
from tqdm import tqdm
import numpy as np
import tensorflow as tf
def load_data_array(dir_path, img_size=(100,100)):
X = []
y = []
i = 0
labels = dict()
for path in tqdm(sorted(os.listdir(dir_path))):
if not path.startswith('.'):
labels[i] = path
for file in os.listdir(dir_path + path):
```

```
if not file.startswith('.'):
img = cv2.imread(dir_path + path + '/' + file)
X.append(img)
y.append(i)
i += 1
X = np.array(X)

y = np.array(y)
print(f'{len(X)} images loaded from {dir_path} directory.')
return X, y, labels

def crop_imgs(set_name, add_pixels_value=0):
set_new = []
for img in set_name:
gray = cv2.cvtColor(img, cv2.COLOR_RGB2GRAY)
gray = cv2.GaussianBlur(gray, (5, 5), 0)
thresh = cv2.threshold(gray, 45, 255, cv2.THRESH_BINARY)[1]
thresh = cv2.erode(thresh, None, iterations=2)
thresh = cv2.dilate(thresh, None, iterations=2)
cnts = cv2.findContours(thresh.copy(), cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_SIMPLE)
cnts = imutils.grab_contours(cnts)
c = max(cnts, key=cv2.contourArea)
extLeft = tuple(c[c[:, :, 0].argmin()][0])
extRight = tuple(c[c[:, :, 0].argmax()][0])
extTop = tuple(c[c[:, :, 1].argmin()][0])
extBot = tuple(c[c[:, :, 1].argmax()][0])
ADD_PIXELS = add_pixels_value
new_img = img[extTop[1]-ADD_PIXELS:extBot[1]+ADD_PIXELS, extLeft[0]-ADD_PIXELS:extRight[0]+ADD_PIXELS].copy()
set_new.append(new_img)
return np.array(set_new)
```

代码在此处继续到下一页；在前面的代码中，我们已导入所需的库并构建了一些实用函数，如 **crop_img()** 和

继续，预处理代码如下：

```
def save_new_images(x_set, y_set, folder_name):
i = 0
for (img, imclass) in zip(x_set, y_set):
if imclass == 0:
cv2.imwrite(folder_name+'NO/'+str(i)+'.jpg', img)
else:
cv2.imwrite(folder_name+'YES/'+str(i)+'.jpg', img)
i += 1

def preprocess_images(set_name, img_size):
set_new = []
for img in set_name:
img = cv2.resize(img,dsize=img_size,
interpolation=cv2.INTER_CUBIC)
set_new.append(tf.keras.applications.vgg16.preprocess_input(img))
return np.array(set_new)
@click.command()
@click.option('--root',default="/mnt/")
@click.option('--train-file', default="/mnt/training.data")
@click.option('--test-file', default="/mnt/test.data")
@click.option('--validation-file', default="/mnt/validation.data")
@click.option('--train-target', default="/mnt/trainingtarget.data")
@click.option('--test-target', default="/mnt/testtarget.data")
```

```
@click.option('--validation-target',
default="/mnt/validationtarget.data")
@click.option('--label', default="/mnt/labels.data")
@click.option('--image-size', default=224)

def training_data_processing(root,train_file,label,test_file,validation_file,
image_size,train_target,test_target,validation_target):
TRAIN_DIR = root + 'TRAIN/'
TEST_DIR = root + 'TEST/'
VAL_DIR = root + 'VAL/'
IMG_SIZE = (image_size,image_size)
X_train, y_train, labels = load_data_array(TRAIN_DIR, IMG_SIZE)
X_test, y_test, _ = load_data_array(TEST_DIR, IMG_SIZE)
X_val, y_val, _ = load_data_array(VAL_DIR, IMG_SIZE)

X_train_crop = crop_imgs(set_name=X_train)
X_val_crop = crop_imgs(set_name=X_val)
X_test_crop = crop_imgs(set_name=X_test)
directory=["TRAIN_CROP", "TEST_CROP", "VAL_CROP",
"TRAIN_CROP/YES", "TRAIN_CROP/NO", "TEST_CROP/YES",
"TEST_CROP/NO", "VAL_CROP/YES", "VAL_CROP/NO"]
for i in directory:
path = os.path.join(root, i)
try:
os.mkdir(path)
except OSError as error:
print(error)
save_new_images(X_train_crop, y_train,
folder_name='/mnt/TRAIN_CROP/')



```
save_new_images(X_val_crop, y_val,
folder_name='/mnt/VAL_CROP/')
save_new_images(X_test_crop, y_test,
folder_name='/mnt/TEST_CROP/')
```

代码继续到下一页；在前面的代码部分，我们正在输入来自前一个管道组件的文件，之后我们将把图像转换为数组，并裁剪这些图像；之后我们将为这些裁剪后的图像创建一些新文件夹并保存这些图像。

```
with open(label,"wb") as f:
dill.dump(labels,f)
with open(train_file,"wb") as f:
dill.dump(X_train_prep,f)
with open(test_file,"wb") as f:
dill.dump(X_test_prep,f)
with open(validation_file,"wb") as f:
dill.dump(X_val_prep,f)
with open(train_target,"wb") as f:
dill.dump(y_train,f)
with open(test_target,"wb") as f:
dill.dump(y_test,f)
with open(validation_target,"wb") as f:
dill.dump(y_val,f)
return
if __name__ == "__main__":
training_data_processing()
```

让我们按如下方式分解预处理代码：

首先，我们将导入所有库并创建实用函数，如 **crop_img()**，它将裁剪原始图像，而 **load_data_array()** 将有助于将图像转换为数组 X、y 和 labels。

接下来，**save_new_images()** 将把这些裁剪后的图像保存到新文件夹中，而 **pre_process_images()** 函数将借助 keras 的 vgg16 应用对这些裁剪后的图像进行预处理并将其保存到新的数组集合中。

接下来，**@click.option** 将输入我们在数据摄取步骤中完成的所有必需转储，以便我们可以在此处使用，并先加载它们，然后将它们用于训练数据的预处理步骤。

然后，**dill.dump** 将为下一个管道组件转储用于训练的预处理数组。

## Docker:

```
FROM python:3.7-slim-stretch
ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update && \
apt-get -y install gcc mono-mcs g++ git curl && \
rm -rf /var/lib/apt/lists/*
RUN mkdir /app
WORKDIR /app
RUN curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
```

```
RUN python get-pip.py
RUN rm get-pip.py
RUN pip install --upgrade pip
RUN apt-get update && yes | apt-get upgrade
RUN apt-get install -y libsm6 libxext6 libxrender-dev
RUN apt-get install -y protobuf-compiler python-pil python-lxml python-pip python-dev git
RUN apt-get update && apt-get install -y protobuf-compiler python-pil python-lxml
ADD requirements.txt /app/requirements.txt
```

```
RUN pip3 install -r requirements.txt
ADD preprocessing.py /app/preprocessing.py
RUN chmod +x /app/preprocessing.py
ENTRYPOINT ["python"]
CMD ["/app/preprocessing.py"]
```

与前面的数据摄取步骤类似，我们将构建 Docker 镜像。正如我们在前面的 Docker 镜像中所看到的，我们已安装运行任何计算机视觉 Docker 镜像所需的库。

```bash
PROJECT_ID=$(gcloud config get-value core/project)
IMAGE_NAME=brain_tumor_scan/step2_dataprocessing
IMAGE_VERSION=v1
IMAGE_NAME=gcr.io/$PROJECT_ID/$IMAGE_NAME
```

构建 Docker 镜像。

```
docker build -t $IMAGE_NAME:$IMAGE_VERSION .
```

将训练镜像推送到 GCR。

```
docker push $IMAGE_NAME:$IMAGE_VERSION
```

### 3.4.3 训练模型组件

在本节中，我们将构建一个 TensorFlow CNN 模型，并下载预训练的 VGG-16 权重并将其保存在 train 文件夹的路径中。因此，请访问以下链接并下载文件：

https://www.kaggle.com/gaborfodor/keras-pretrained-models?select=vgg16_weights_tf_dim_ordering_tf_kernels_notop.h5

![](img/8f8a671916d96b455297952d0f37b96c_197_0.png)

图 3.4：VGG16 下载位置

这就是我们的 train 文件夹的样貌，我们将保留存储桶服务账号和 **Storage.py** 以上传到存储桶。

![](img/8f8a671916d96b455297952d0f37b96c_198_0.png)

图 3.5：train 文件夹

接下来，我们将了解如何构建 Train 组件。

### Train.py

```
from __future__ import absolute_import, division, print_function, unicode_literals
import click,dill,json,logging,os,PIL
import pandas as pd
import tensorflow as tf
from storage import Storage
from sklearn.metrics import accuracy_score

def model_build(base_model,NUM_CLASSES,activation):
model =
tf.keras.models.Sequential([base_model,tf.keras.layers.Flatten(),
tf.keras.layers.Dropout(0.5),
tf.keras.layers.Dense(NUM_CLASSES,activation=activation)])
model.layers[0].trainable = False
```

```
return model

@click.command()
@click.option('--train-file', default="/mnt/training.data")
@click.option('--test-file', default="/mnt/test.data")
@click.option('--validation-file', default="/mnt/validation.data")
@click.option('--train-target', default="/mnt/trainingtarget.data")
@click.option('--test-target', default="/mnt/testtarget.data")
@click.option('--validation-target',
default="/mnt/validationtarget.data")
@click.option('--epochs', default=100)
@click.option('--activation', default="sigmoid")
@click.option('--learning-rate', default=0.001)
@click.option('--tensorboard-logs', default='/mnt/logs/')
@click.option('--tensorboard-gcs-logs',
default='gs://kubeflowusecases/brain/logs')

@click.option('--model-output-base-path',
default="/mnt/saved_model")
@click.option('--gcs-path',
default="gs://kubeflowusecases/brain/model")
@click.option('--mode', default="local")
@click.option('--image-size', default=224)
@click.option('--label', default="/mnt/labels.data")
def train_model(train_file,test_file,validation_file,train_target,test_target,
validation_target,
label,epochs,activation,image_size,learning_rate,tensorboard_logs,tensorboard_gcs_logs,model_output_base_path,gcs_path,mode):
with open(label, 'rb') as in_f:
labels= dill.load(in_f)
with open(train_file, 'rb') as in_f:
train= dill.load(in_f)
with open(test_file, 'rb') as in_f:
test= dill.load(in_f)
with open(validation_file, 'rb') as in_f:
validation= dill.load(in_f)
with open(train_target, 'rb') as in_f:
train_tar= dill.load(in_f)
with open(test_target, 'rb') as in_f:
test_tar= dill.load(in_f)
with open(validation_target, 'rb') as in_f:
validation_tar= dill.load(in_f)
```

代码继续到下一页，这里在前面的部分，我们已导入所需的库，并且我们拥有来自前一个管道的所有输入；我们已使用 dill.load 将它们导入。并且我们创建了一个实用函数 **model_build()** 用于构建 TensorFlow 模型的层。

在前一个代码片段的延续中，**train.py** Python 文件包含以下部分：

```
IMG_SIZE = (image_size,image_size)
RANDOM_SEED = 123
TRAIN_DIR = '/mnt/TRAIN_CROP/'
VAL_DIR = '/mnt/VAL_CROP/'
```

```
train_datagen = tf.keras.preprocessing.image.ImageDataGenerator(
rotation_range=15,width_shift_range=0.1,height_shift_range=0.1,shear_range=0.1,brightness_range=[0.5, 1.5],
horizontal_flip=True,vertical_flip=True,
preprocessing_function=tf.keras.applications.vgg16.preprocess_input)
```

```
train_generator =
train_datagen.flow_from_directory(TRAIN_DIR,color_mode='rgb',
target_size=IMG_SIZE,batch_size=32,class_mode='binary',
seed=RANDOM_SEED)
val_datagen = tf.keras.preprocessing.image.ImageDataGenerator(
preprocessing_function=tf.keras.applications.vgg16.preprocess_input)
validation_generator = val_datagen.flow_from_directory(
VAL_DIR,color_mode='rgb',target_size=IMG_SIZE,
batch_size=16,class_mode='binary',seed=RANDOM_SEED)

vgg16_weight_path="/app/vgg16_weights_tf_dim_ordering_tf_kernels_notop.h5"
base_model=tf.keras.applications.VGG16(
include_top=False, weights=vgg16_weight_path,
input_shape=IMG_SIZE + (3,))
NUM_CLASSES=1
model=model_build(base_model,NUM_CLASSES,activation)
optimizer=tf.keras.optimizers.RMSprop(learning_rate=learning_rate)
model.compile(loss=tf.keras.losses.binary_crossentropy,optimizer=optimizer, metrics=['accuracy'])
tensorboard_callback =
tf.keras.callbacks.TensorBoard(log_dir=tensorboard_logs,
histogram_freq=1)
earlystopping = tf.keras.callbacks.EarlyStopping(monitor='val_loss',
mode='max',patience=6)
logging.info("Training starting...")
model.fit_generator(train_generator,epochs=epochs,
validation_data=validation_generator,validation_steps=25, callbacks=
[earlystopping,tensorboard_callback])
logging.info("Training completed.")
model.save(model_output_base_path)
new_model = tf.keras.models.load_model(model_output_base_path)
```



```
print(new_model.summary())
predictions = new_model.predict(validation)
predictions = [1 if x>0.5 else 0 for x in predictions]
```

```
accuracy = accuracy_score(validation_tar, predictions)
print('Val Accuracy = %.2f' % accuracy)
logging.info(('Val Accuracy = %.2f' % accuracy))
Storage.upload(tensorboard_logs,tensorboard_gcs_logs)
metadata = {'outputs': [{'type': 'tensorboard',
'source': tensorboard_gcs_logs,}]}
```

所以，前面的代码包含使用 Image Data Generator 进行训练和预处理，之后我们使用预处理后的图像在 pipeline 中训练模型，并且训练好的产物作为 TensorFlow 模型保存在 GCP Bucket 中。

```
with open("/mlpipeline-ui-metadata.json", 'w') as f:
json.dump(metadata,f)
if mode!= 'local':
print("uploading to {0}".format(gcs_path))
Storage.upload(model_output_base_path,gcs_path)
else:
print("Model will not be uploaded")
pass
```

```
if __name__ == "__main__":
train_model()
```

所以，前面的代码是 **train.py** 文件；让我们按如下方式拆解 pipeline 代码：

导入所有所需的数据集。

**@click** 命令将参数传递给函数

这里，我们在 train Python 代码中从 Docker 根目录加载 VGG16 模型，以便我们可以用 TensorFlow 导入它进行模型训练，然后，**dill** 命令将帮助从 pvc 保存或加载数据。接下来，我们将从外部传入 epochs 和 batch size、learning rate 等所有参数并训练我们的模型。

然后，我们将把模型训练输出推送到 Google Storage Bucket。然后，我们将导入 **Storage.py** 文件到导入的 storage 类以保存我们的模型产物。

并且为了可视化，Tensorboard 将遵循相同的 metadata json 格式，并给出您保存模型产物所在的 gcs bucket 路径。

同样，我们将创建 Docker 镜像，并添加 service account json 密钥。请查看 GitHub **steps.md** 文件。

### 3.3.4 评估组件

同样，我们将创建评估组件。请查看 GitHub steps.md 文件。我们已将混淆矩阵和 ROC 曲线作为 csv 导出到 GCP bucket 中，并在 metadata 中给出这些内容的存储位置路径，并将其导出为 json。

![](img/8f8a671916d96b455297952d0f37b96c_204_0.png)

图 3.6：评估器组件

## 3.5. 使用 KF Serving 提供模型服务

本节中，我们将构建我们的服务模型。如以下部分所示，服务账户与存储桶访问 json 文件、Dockerfile 有三个主要组件，

我们将构建自定义端点服务，并将看到如何对多个测试输入图像进行批量预测。

### brainserving.py

```python
import kfserving, argparse, json, cv2, logging,os,base64,io,imutils
from typing import List, Dict
import numpy as np
from PIL import Image
import tensorflow as tf
os.environ['GOOGLE_APPLICATION_CREDENTIALS'] = "service_account_iam.json"

def crop_imgs(set_name, add_pixels_value=0):
set_new = []
for img in set_name:
gray = cv2.cvtColor(img, cv2.COLOR_RGB2GRAY)
gray = cv2.GaussianBlur(gray, (5, 5), 0)
thresh = cv2.threshold(gray, 45, 255, cv2.THRESH_BINARY)[1]
thresh = cv2.erode(thresh, None, iterations=2)
thresh = cv2.dilate(thresh, None, iterations=2)
```

```
cnts = cv2.findContours(thresh.copy(), cv2.RETR_EXTERNAL,
 cv2.CHAIN_APPROX_SIMPLE)
cnts = imutils.grab_contours(cnts)
c = max(cnts, key=cv2.contourArea)

extLeft = tuple(c[c[:, :, 0].argmin()][0])
extRight = tuple(c[c[:, :, 0].argmax()][0])
extTop = tuple(c[c[:, :, 1].argmin()][0])
extBot = tuple(c[c[:, :, 1].argmax()][0])
ADD_PIXELS = add_pixels_value
new_img = img[extTop[1]-ADD_PIXELS:extBot[1]+ADD_PIXELS,
extLeft[0]-ADD_PIXELS:extRight[0]+ADD_PIXELS].copy()
set_new.append(new_img)
return np.array(set_new)

def preprocess_imgs(set_name, img_size):
set_new = []
for img in set_name:
img = cv2.resize(img,dsize=img_size,interpolation=cv2.INTER_CUBIC)
set_new.append(tf.keras.applications.vgg16.preprocess_input(img))
return np.array(set_new)

def image_transform(instance):
logging.info("Inside Image Transform")
originalimage = base64.b64decode(instance)
jpg_as_np = np.frombuffer(originalimage, dtype=np.uint8)
img = cv2.imdecode(jpg_as_np, flags=1)
image_expanded = np.expand_dims(img, axis=0)
crop_image = crop_imgs(set_name=image_expanded)
IMG_SIZE=(224,224)
```

```
prep_image = preprocess_imgs(set_name=crop_image,
img_size=IMG_SIZE)
return prep_image

class Transformer(kfserving.KFModel):
def __init__(self, name: str):
super().__init__(name)
self.name = name
self.ready = False
self.model_output_base_path='gs://kubeflowusecases/brain/model/'

def load(self):
self.model = tf.keras.models.load_model(self.model_output_base_path)
self.ready = True
def predict(self, request: Dict) -> Dict:
data={'instances': [image_transform(request['instances'][i]) for i in range(len(request['instances']))]}
transformdata=[]
for i in data['instances']:
logging.info("Inside transform data")
arraydata=self.model.predict(i)
logging.info(self.model.predict(i))
transformdata.append(arraydata)
result=[]
Predict=0
predictions = [1 if x>0.5 else 0 for x in transformdata]
for i in predictions:
if i == Predict:
result.append("No tumor inside Brain")
```

```
else:
result.append("Tumor inside Brain")
return json.dumps({"predictions" : result})
```

```
if __name__ == "__main__":
model = Transformer("kfserving-braintumor")
model.load()
kfserving.KFServer(workers=1).start([model])
```

所以，让我们按如下方式拆解 transformer 预测器代码：

我们保留了具有存储桶的 service account 在 Docker 根目录中，并且在这里我们将该文件夹声明为环境变量到对象 model_output_base_path 以用于 gcp bucket 路径。

接下来，在 load 函数中，我们从 TensorFlow 库加载了模型。

这里，传入的数据是图像的编码字符串；然后我们使用以下函数转换图像，这些函数会将编码字符串更改为解码后的字符串；接下来，我们将使用 crop_imgs() 函数裁剪图像，之后，我们将使用 preprocess_image() 预处理图像数组并返回该数组。

然后，在 predict 方法中，传入的数据将以 json 格式到来，我们需要将其提取为键值对并进行必要的预测并作为字典返回。

所以，在“main”函数中，KFServingSampleModel 类将采用该部署的名称；请注意这一点并应用到 yaml 文件中；这里是 "kfserving-breast-model"。

### Docker:

```docker
FROM python:3.7-slim-stretch
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && apt-get -y install gcc mono-mcs g++ git curl bash && \
rm -rf /var/lib/apt/lists/*
RUN mkdir /app
WORKDIR /app
RUN curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
RUN python get-pip.py && rm get-pip.py && pip install --upgrade pip
RUN apt-get update && yes | apt-get upgrade
RUN apt-get install -y libsm6 libxext6 libxrender-dev protobuf-compiler python-pil python-lxml python-pip python-dev git protobuf-compiler python-pil python-lxml
ADD requirements.txt /app/requirements.txt
RUN pip3 install -r requirements.txt
ADD brainserving.py /app/brainserving.py
COPY service_account_iam.json service_account_iam.json
ENV GOOGLE_APPLICATION_CREDENTIALS="service_account_iam.json"
CMD ["python","brainserving.py"]
```

现在，在前面的 Docker 代码中，我们已复制用于存储桶访问的 service account，并将其保存到 然后，我们将 Python serving 文件复制到同一位置并将工作目录保持为 然后，我们使用上述代码构建镜像。同样，我们创建了 Docker 镜像；请查看 GitHub **steps.md** 文件。

要使用 **kubectl** 命令行或使用 KF Serving 客户端 SDK 部署模型服务器，您可以执行以下任一操作：

- 使用命令行部署
- 使用 KF Serving 客户端 SDK 部署

### 使用命令行部署：

现在，让我们使用命令行部署它，首先让我们填写 yaml 文件：

```yaml
apiVersion: serving.kubeflow.org/v1alpha2
kind: InferenceService
metadata:
annotations:
sidecar.istio.io/inject: "false"
name: kfserving-braintumor
namespace: kubeflow
spec:
```

```
default:
predictor:
custom:
container:
image: gcr.io/brain_tumor_scan/kf_serving_braintest:v1
```

这里，在前面的 yaml 文件中，我们将使用与 serving.py 文件中提供的模型名称（“kfserving-braintumor”）相同的名称，然后提供部署的命名空间“kubeflow”。接下来，我们将提供 Docker 镜像名称。

![](img/8f8a671916d96b455297952d0f37b96c_211_0.png)

图 3.7：KF – Serving 模型名称匹配

如图所示，左侧图像中的行号与右侧的第 6 行始终应相同。

接下来，从 Visual Studio 中保存文件的 bash 中运行以下命令：

使用以下命令连接到 GCP 集群：

```
gcloud container clusters get-credentials <$ClusterName> --zone <$ZONE> --project <$PROJECTID>
```

通过在集群中部署它来创建推理服务：

```
kubectl apply -f custom_brain_model.yaml
```

检查推理服务。间隔一段时间后尝试检查它是否已创建：

```
kubectl get inferenceservice -n kubeflow
```

![](img/8f8a671916d96b455297952d0f37b96c_212_0.png)

图 3.8：KF – Serving 推理服务就绪

## 示例预测：

从 serving 文件夹在 Bash 中运行以下命令：

```bash
MODEL_NAME=kfserving-breast-model
HOST=$(kubectl get inferenceservice -n kubeflow $MODEL_NAME -o jsonpath='{.status.url}' | cut -d "/" -f 3)
INPUT_PATH=@./breast.json

CLUSTER_IP=$(kubectl -n istio-system get service kfserving-ingressgateway -o jsonpath='{.status.loadBalancer.ingress[0].ip}')
```

```
curl -v -H "Host: ${HOST}" http://${CLUSTER_IP}/v1/models/${MODEL_NAME}:predict -d $INPUT_PATH
```

现在，以下是响应预测请求：

![](img/8f8a671916d96b455297952d0f37b96c_213_0.png)

图 3.9：KF – Serving 预测输出

从 serving 文件夹在 Python 中运行以下命令。

现在我们创建一些示例数据以预测前面 URL 的结果。创建示例数据的代码如下：

```
import json
import base64
import requests
samples=[]
NUM_SAMPLES=4
for index in range(NUM_SAMPLES):
with open("Brain_{0}.jpg".format(index + 1), "rb") as image_file:
encoded_bytes = base64.b64encode(image_file.read())
```

```
# result: string (in utf-8)
encoded_string = encoded_bytes.decode('utf-8')
samples.append(encoded_string)
```

```
# prepare test data
data = json.dumps({"instances": samples})
data_read = json.loads(data)
with open('data.json','w') as out:
json.dump(data_read, out)
```

```
%%bash
gcloud container clusters get-credentials --zone us-east1-d --project
CLUSTER_IP=$(kubectl -n istio-system get service kfserving-ingressgateway -o jsonpath='{.status.loadBalancer.ingress[0].ip}')
echo $CLUSTER_IP
MODEL_NAME="kfserving-braintumor"
#Replace the cluster IP
cluster_ip = "COPY YOUR IP FROM ABOVE"
headers={"Host": "{0}.kubeflow.example.com".format(MODEL_NAME),"Content-Type": "application/json"}
response = requests.post("http://{0}/v1/models/{1}:predict".format(cluster_ip, MODEL_NAME), data = data,headers = headers)
print(response.json())
```

```
{'predictions': ['No tumor inside Brain', 'Tumor inside Brain', 'Tumor inside Brain', 'Tumor inside Brain']}
```

图 3.10：预测输出

在前面的屏幕截图中，我们可以看到批量预测的输出结果。

## 3.6 端到端构建管道

现在，让我们看看如何构建 Pipeline，并在 Kubeflow Notebook 服务器中运行此平台。

打开 URL：GCP Kubernetes > Service & ingress > 点击 URL

如第 1 章《Kubeflow & Kubernetes Cloud 简介》中所述，我们已经创建了一个 Jupyter notebook，我们将使用它。

现在，粘贴以下代码并运行管道；在执行之前，请将以下代码中的 PROJECT_ID 和存储桶名称替换掉，它将转储一个 zip 文件：

```
import kfp.dsl as dsl
import yaml
from kubernetes import client as k8s
import kfp.gcp as gcp
from kfp import components
from string import Template
import json
from kubernetes import client as k8s_client
```

```
@dsl.pipeline(
name="brain_tensorflow_pipeline",
description='End to End pipeline for Tensorflow Brain MRI '
)
```

def brain_tensorflow_pipeline(
dataextraction_step_image="gcr.io/brain_tumor_scan1/step1_download_data:v1",
dataprocessing_step_image="gcr.io/brain_tumor_scan4/step2_dataprocessing:v1",

trainmodel_step_image="gcr.io/brain_tumor_scan1/step3_training_model:v1",
evaluator_step_image="gcr.io/brain_tumor_scan1/step4_evaluation_model:v1",
root="/mnt/",data_file="/mnt/BrainScan_Data/",
kaggle_api_data="navoneel/brain-mri-images-for-brain-tumor-detection",
train_file='/mnt/training.data',test_file='/mnt/test.data',
validation_file="/mnt/validation.data",label="/mnt/labels.data",
activation="sigmoid",image_size=224,train_target="/mnt/trainingtarget.data",
test_target="/mnt/testtarget.data",validation_target="/mnt/validationtarget.data",
epochs=10,learning_rate=.001,shuffle_size=1000,tensorboard_logs="/mnt/logs/",
tensorboard_gcs_logs="gs://brain/logs",
model_output_base_path="/mnt/saved_model",gcs_path="gs://brain/model",
gcs_path_confusion="gs://brain", mode="gcs",probability=0.5,
serving_name="kfserving-braintumor",serving_namespace="kubeflow",
image="gcr.io/brain_tumor_scan/kf_serving_braintest:v1"):
"""
Pipeline
"""

'''

# PVC : PersistentVolumeClaim volume
vop = dsl.VolumeOp(
name='my-pvc', resource_name="my-pvc",modes=dsl.VOLUME_MODE_RWO,size="1Gi")
# data extraction
data_extraction_step = dsl.ContainerOp(
name='data_extraction',image=dataextraction_step_image,command="python",
arguments=[
"/app/dataextract.py",
"--root",root,
"--data-file", data_file,
"--kaggle-api-data", kaggle_api_data,
],pvolumes={"/mnt": vop.volume}).apply(gcp.use_gcp_secret("user-gcp-sa"))
# processing
data_processing_step = dsl.ContainerOp(
name='data_processing',image=dataprocessing_step_image,command="python",
arguments=[
"/app/preprocessing.py",
"--train-file", train_file,
"--test-file", test_file,
"--validation-file", validation_file,
"--root",root,
"--image-size",image_size,
"--train-target",train_target,
"--test-target",test_target,
"--validation-target",validation_target,
"--label",label],pvolumes={"/mnt": data_extraction_step.pvolume}
).apply(gcp.use_gcp_secret("user-gcp-sa"))
#trainmodel
train_model_step = dsl.ContainerOp(
name='train_model', image=trainmodel_step_image,
command="python",
arguments=[
"/app/train.py",
"--train-file", train_file,
"--test-file", test_file,
"--label",label,
"--activation",activation,
"--validation-file", validation_file,
"--train-target",train_target,
"--test-target",test_target,
"--validation-target",validation_target,
"--epochs",epochs,
"--image-size",image_size,
"--learning-rate",learning_rate,
"--tensorboard-logs",tensorboard_logs,
"--tensorboard-gcs-logs",tensorboard_gcs_logs,
"--model-output-base-path",model_output_base_path,
"--gcs-path", gcs_path,
"--mode", mode,
],file_outputs={"mlpipeline-ui-metadata": "/mlpipeline-ui-metadata.json"},
pvolumes={"/mnt": data_processing_step.pvolume}).apply(gcp.use_gcp_secret("user-gcp-sa"))

#evaluation
evaluation_model_step = dsl.ContainerOp(
name='evaluation_model',image=evaluator_step_image,command="python",
arguments=[
"/app/evaluator.py",
"--test-file", test_file,
"--test-target",test_target,
"--probability",probability,
"--model-output-base-path",model_output_base_path,
"--gcs-path", gcs_path,
"--label",label,
"--gcs-path-confusion", gcs_path_confusion,
],file_outputs={"mlpipeline-metrics": "/mlpipeline-metrics.json","mlpipeline-ui-metadata": "/mlpipeline-ui-metadata.json"},
pvolumes={"/mnt": train_model_step.pvolume}).apply(gcp.use_gcp_secret("user-gcp-sa"))
kfserving_template = Template("""{
"apiVersion": "serving.kubeflow.org/v1alpha2",
"kind": "InferenceService",
"metadata": {
"labels": {
"controller-tools.k8s.io": "1.0"
},
"name": "$name",
"namespace": "$namespace"
},
"spec": {
"default": {
"predictor": {
"custom": {
"container": {

```
"image": "$image"
}
}
}
}
}
}"""
kfservingjson = kfserving_template.substitute({'name':
str(serving_name),
'namespace': str(serving_namespace),
'image': str(image)})
kfservingdeployment = json.loads(kfservingjson)
serve = dsl.ResourceOp(
name="serve",k8s_resource=kfservingdeployment,
action="apply",success_condition="status.url")
serve.after(evaluation_model_step)
```

```
if __name__ == '__main__':
import kfp.compiler as compiler
pipeline_func = brain_tensorflow_pipeline
pipeline_filename = pipeline_func.__name__ + '.pipeline.yaml'
compiler.Compiler().compile(pipeline_func,pipeline_filename)
```

因此，让我们按如下方式拆分流水线代码：

预计流水线应包含一个 @dsl.pipeline 装饰器以提供有关流水线的元数据。

流水线在 brain_tensorflow_pipeline 函数中定义。它包含多个参数，这些参数在创建新的 Run 时会在 Kubeflow Pipelines UI 中公开。尽管以字符串形式传递，这些参数的类型为

每个单独的块定义一个组件，如‘train’、‘evaluation’等。组件由一个带有指定容器路径和名称的 **kfp.dsl.ContainerOp** 对象组成。使用的容器镜像定义为我们已创建的 Dockerfile。

在定义 train 组件之后，我们还为训练脚本设置了一些环境变量。

脚本底部是 main 函数。它用于在运行脚本时编译流水线；然后 **.after** 方法将依次触发流水线。

接下来，我们将创建一个实验；在该实验下，我们可以创建流水线的多次运行。以下代码用于创建实验：

```
EXPERIMENT_NAME = 'Brain_experiment'
client = kfp.Client()
try:
experiment =
client.get_experiment(experiment_name=EXPERIMENT_NAME)
except:
experiment = client.create_experiment(EXPERIMENT_NAME)

print(experiment)
```

以下代码片段将为我们已转储到该位置的 zip 创建一次运行：

```
arguments = {}
run_name = pipeline_func.__name__ + 'heart_run'
run_result = client.run_pipeline(experiment.id, run_name, pipeline_filename,arguments)
print(experiment.id)
print(run_name)
print(pipeline_filename)
print(arguments)
```

流水线准备就绪后，点击运行链接。以下是我们的流水线训练情况：

![](img/8f8a671916d96b455297952d0f37b96c_223_0.png)

图 3.11：Kubeflow 端到端流水线

下图是我们创建的流水线，以及 Python 可视化、ROC 曲线、混淆矩阵和 Tensorboard：

![](img/8f8a671916d96b455297952d0f37b96c_224_0.png)

图 3.12：流水线可视化

从 UI 运行流水线的另一种方式如下：

点击创建新实验按钮后，它将重定向到实验创建页面的新屏幕。

![](img/8f8a671916d96b455297952d0f37b96c_225_0.png)

图 3.13：创建实验

提供一个实验名称。

![](img/8f8a671916d96b455297952d0f37b96c_225_1.png)

图 3.14：创建实验并提供名称

点击跳过此项

![](img/8f8a671916d96b455297952d0f37b96c_225_2.png)

参数将在您选择流水线后出现

开始  跳过此步骤  必须选择流水线版本

图 3.15：创建实验跳过步骤

现在，实验已准备就绪；现在点击

![](img/8f8a671916d96b455297952d0f37b96c_226_0.png)

图 3.16：创建运行

接下来，上传我们在之前构建流水线期间创建的 zip 文件。

![](img/8f8a671916d96b455297952d0f37b96c_227_0.png)

图 3.17：上传流水线 tar 或 yaml 文件

现在，创建您已上传的该流水线的运行，并选择我们之前创建的实验。

![](img/8f8a671916d96b455297952d0f37b96c_228_0.png)

图 3.18：选择实验开始运行

接下来，让我们看看如何自动扩缩 KF-Serving 端点并在 Grafana 仪表板中监控它。

## 3.7. 服务端点的自动扩缩容

Knative 的主要功能之一是对应用程序的副本进行自动扩缩，以紧密匹配传入需求，包括在没有流量接收时将应用程序缩减为零。Knative Serving 默认使用 **Knative Pod Autoscaler** 启用此功能。Autoscaler 组件监视流向应用程序的流量，并根据配置的指标对副本进行向上或向下扩缩。

部署 kf-serving Knative 服务：

### Custom_auto_scale.yaml:

```yaml
apiVersion: serving.kubeflow.org/v1alpha2
kind: InferenceService
metadata:
annotations:
sidecar.istio.io/inject: "false"
autoscaling.knative.dev/target: "10"
labels:
controller-tools.k8s.io: "1.0"
name:
namespace: kubeflow
spec:
default:
predictor:
```

```
minReplicas: 1
custom:
container:
image: gcr.io//brain_tumor_scan/kf_serving_braintest:v1
imagePullPolicy: Always
```

```
name: user-container
imagePullSecrets:
- name: user-gcp-sa
```

使用以下命令连接到 GCP 集群：

```
gcloud container clusters get-credentials <$ClusterName> --zone <$ZONE> --project <$PROJECTID>
```

通过在集群中部署它来创建推理服务：

```
kubectl apply -f custom_autoscale.yaml
```

检查推理服务。间隔一段时间后尝试检查是否已创建：

```
kubectl get inferenceservice -n kubeflow
```

![](img/8f8a671916d96b455297952d0f37b96c_230_0.png)

图 3.19：KF – Serving 自动扩缩推理服务就绪

我们可以使用任何负载测试工具来模拟负载。在这里，我们将使用 Hey 工具来测试自动扩缩：

```bash
# on macOS
brew install hey
```

我们已在第 1 章《Kubeflow 和 Kubernetes 云简介》部分安装了 Prometheus，如果您尚未安装，请参阅该章节。

发送 30 秒的流量，保持 50 个并发请求：

```bash
MODEL_NAME=kfserving-braintumor
HOST=$(kubectl get inferenceservice -n kubeflow $MODEL_NAME -o jsonpath='{.status.url}' | cut -d \"\/\" -f 3)
INPUT_PATH=@./data.json
CLUSTER_IP=$(kubectl -n istio-system get service kfserving-ingressgateway -o jsonpath='{.status.loadBalancer.ingress[0].ip}')
hey -z 30s -c 100 -m POST -H \"Host: ${HOST}\" -d $INPUT_PATH
```

摘要：
  总计：30.9381 secs
  最慢：2.4160 secs
  最快：0.3205 secs
  平均：0.6304 secs
  请求/秒：155.6978

响应时间直方图：
  0.321 [1]
  0.530 [928]
  0.740 [3435]
  0.949 [326]
  1.159 [45]
  1.368 [25]
  1.578 [0]
  1.787 [30]
  1.997 [21]
  2.206 [4]
  2.416 [2]

延迟分布：
  10% in 0.4698 secs
  25% in 0.5516 secs
  50% in 0.6244 secs
  75% in 0.6655 secs
  90% in 0.7328 secs
  95% in 0.8477 secs
  99% in 1.6786 secs

详情（平均、最快、最慢）：
  DNS+dialup: 0.0184 secs, 0.3205 secs, 2.4160 secs
  DNS-lookup: 0.0000 secs, 0.0000 secs, 0.0000 secs
  req write: 0.0000 secs, 0.0000 secs, 0.0004 secs
  resp wait: 0.3716 secs, 0.3189 secs, 2.2550 secs
  resp read: 0.0000 secs, 0.0000 secs, 0.0012 secs

状态码分布：
  [404] 4817 responses

图 3.20：Hey 流量报告

查看正在运行的 Pod。

```bash
kubectl get pods -n kubeflow | grep kfserving-braintumor
```

kfserving-braintumor-predictor-default-xk9np-deployment-582ct7n 1/2 Running 0 53s
kfserving-braintumor-predictor-default-xk9np-deployment-588lp7k 1/2 Running 0 33s
kfserving-braintumor-predictor-default-xk9np-deployment-589mw7n 1/2 Running 0 53s
kfserving-braintumor-predictor-default-xk9np-deployment-58kc4jv 1/2 Running 0 54s
kfserving-braintumor-predictor-default-xk9np-deployment-58qtt6m 1/2 Running 0 31s
kfserving-braintumor-predictor-default-xk9np-deployment-58rq4qz 1/2 Running 0 50s
kfserving-braintumor-predictor-default-xk9np-deployment-58szgg6 1/2 Running 0 27s
kfserving-braintumor-predictor-default-xk9np-deployment-58vk4jm 1/2 Running 0 50s
kfserving-braintumor-predictor-default-xk9np-deployment-58vnbj5 1/2 Running 0 28s
kfserving-braintumor-predictor-default-xk9np-deployment-58wx6cw 1/2 Running 0 31s

图 3.21：自动扩缩的 Pod

打开 Grafana 仪表板。

查看 Knative Serving 扩缩仪表板：

```bash
# use port-forwarding
kubectl port-forward --namespace knative-monitoring $(kubectl get pod --namespace knative-monitoring --selector="app=grafana" --output jsonpath='{.items[0].metadata.name}') 8080:3000
```




![](img/8f8a671916d96b455297952d0f37b96c_234_0.png)

Figure 3.22: Grafana Knative Dashboard 自动扩缩容

正如我们所见，当我们发送持续 30 秒的 100 个并发请求的流量时，它创建了 10 个 Pod。

## 自动扩缩容说明：它是如何工作的？

![](img/8f8a671916d96b455297952d0f37b96c_234_1.png)

Figure 3.23: 自动扩缩容工作概念

### 算法

Knative Serving 自动扩缩容基于每个 Pod 的平均并发请求数（并发）。系统默认的目标并发数为 100（搜索 container-concurrency-target-default），但我们为服务使用了 10。

我们用 100 个并发请求加载服务，因此自动扩缩容器创建了 5 个 Pod。

（100 个并发请求 / 目标 10 = 10 个 Pod）

### 恐慌

自动扩缩容器在 60 秒窗口上计算平均并发，因此系统需要一分钟才能在期望的并发水平上稳定下来。然而，自动扩缩容器还计算 6 秒的恐慌窗口，如果该窗口达到目标并发的 2 倍，则会进入恐慌模式。在恐慌模式下，自动扩缩容器在更短、更敏感的恐慌窗口上运行。一旦恐慌条件在 60 秒内不再满足，自动扩缩容器将返回初始的 60 秒稳定窗口。

## 3.8 结论

在本章中，我们学习了如何为 TensorFlow CNN 模型构建端到端的 Kubeflow Orchestrator Pipeline，以及如何 Docker 化每个组件并在 Google 平台上构建它。

然后，我们看到了如何使用 kfp 库包构建管道，并从 Kubeflow Dashboard 触发管道并构建批量预测服务。现在，我们已在 Kubernetes 平台上部署了 Kubeflow，并学习了如何从 Notebook 触发管道。我们还使用 KF serving 在 Kubernetes 集群中部署了模型，并在 Grafana Dashboard 中监控了自动扩缩容。

在本章中，我们学习了如何利用 Google Cloud Platform 的强大功能，并将我们的 DevOps 知识与机器学习相结合，成为 MLOps。

## 3.9 参考

https://knative.dev/docs/serving/autoscaling/autoscaling-concepts/

https://v1-1-branch.kubeflow.org/docs/

https://v1-1-branch.kubeflow.org/docs/gke/

https://v1-1-branch.kubeflow.org/docs/gke/monitoring/

https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale/

# 构建 TFX Pipeline

在本章中，我们将使用 TFX 的帮助构建端到端的结构化数据分类模型并使其准备好投入生产，并使用 TF serving 提供模型输出以获得预测。我们还将构建 TensorFlow 生态系统建模，并使用 Tensorboard 和 Fairness 可视化评估。然后，我们将学习各种 TFX 组件，如 TFT、TFMA、TFDV 等。之后，我们将在 Google 云中创建一个 Kubeflow Pipeline。

## 结构

在本章中，我们将涵盖以下主题：

- 问题陈述
- TFX 组件架构
- TFX 环境设置
- TFX 管道
- 使用 TF serving 提供模型
- 构建 Kubeflow Pipeline Orchestrator

## 目标

学习本章后，我们将能够做到以下几点：

- 了解完整的 BERT 架构模型及其分词和预处理。
- 评估 BERT Base 模型并创建用于情感分析的框架。
- 构建 TFX Pipeline 组件，它提供配置框架和共享库，以集成定义、启动和监控机器学习系统所需的通用组件。
- 对 BERT 模型训练和验证的训练数据进行预处理。
- 分析和审查训练和调优的模型，部署最佳模型，该模型将由 pusher 组件推送。

## 4.1 问题陈述

在本章中，我们将使用 Taxi Trips 数据集。这是一个用于二元情感分类的数据集，包含比以前的基准数据集多得多的數據。此外，我们还将预测小费。在这里，我们将使用各种组件在 TFX 中构建分类模型和 Kubeflow pipeline，以便它准备好投入生产。我们还将使用 TF-Serving。

| TF-Serving. TF-Serving. TF-Serving. TF-Serving. TF-Serving. TF-Serving. TF-Serving. TF-Serving. TF-Serving. TF-Serving. TF-Serving. TF-Serving. TF-Serving. TF-Serving. TF-Serving. TF-Serving. TF-Serving. TF-Serving. TF-Serving. TF-Serving. TF-Serving. TF-Serving. TF-Serving. TF-Serving. TF-Serving. |
|---|
| TF-Serving. |

## 4.2 TFX 组件架构

机器学习管道可能变得非常复杂，并且需要大量开销来管理任务依赖关系。同时，机器学习管道可以包括各种任务，包括数据验证、预处理、模型训练和任何训练后任务。任务之间的连接通常很脆弱，并且可能导致管道失败。具有脆弱连接最终意味着生产模型将很少更新；数据科学家或机器学习工程师厌恶更新陈旧的模型。管道还需要良好管理的分布式处理，这就是 TFX 利用 Apache Beam 的原因。这对于大型工作负载尤其正确。

![](img/8f8a671916d96b455297952d0f37b96c_242_0.png)

Figure 4.1: TFX 架构

TFX pipeline 是组件序列，它实现机器学习管道，专门为可扩展、高性能的机器学习任务而设计。

**ExampleGen** 是管道的初始输入组件，它摄取并可选地拆分输入数据集。

**StatisticsGen** 计算数据集的统计信息。

**SchemaGen** 检查统计信息并创建数据模式。

**ExampleValidator** 在数据集中查找异常和缺失值。

**Transform** 对数据集执行特征工程。

**Trainer** 训练模型。

**Tuner** 调整模型的超参数。

**Evaluator** 对训练结果进行深入分析，帮助您验证导出的模型，确保它们可以推送到生产环境。

**Pusher** 在服务基础设施上部署模型。

**TFX 组件简述：** 组件处理比单个任务执行更复杂的过程。所有机器学习管道组件都从 Channel 读取以从元数据存储中获取输入工件。然后从元数据存储提供的路径加载数据并进行处理。组件的输出，即处理后的数据，然后提供给下一个管道组件。组件的通用内部结构始终如下：

- 接收一些输入
- 执行操作
- 存储最终结果

TFX 组件功能

![](img/8f8a671916d96b455297952d0f37b96c_244_0.png)

*图 4.2:* TFX 组件功能

在 TFX 术语中，组件的三个内部部分称为 Driver、Executor 和 Publisher。驱动程序处理元数据存储的查询；执行器执行组件的操作；发布者管理在 MetadataStore 中保存输出元数据。驱动程序和发布者不移动任何数据，而是从 MetadataStore 读取和写入引用。

## 4.3 TFX 环境设置

现在，我们将根据项目安装每个依赖项。

```
try:
import colab
!pip install --upgrade pip
except:
pass
!pip install -q -U --use-feature=2020-resolver tfx
```

接下来，我们必须重新启动内核，我们将导入每个依赖项。

```
from tfx.components.base import executor_spec
from tfx.components.trainer.executor import GenericExecutor
from tfx.dsl.experimental import latest_blessed_model_resolver
from tfx.proto import evaluator_pb2, example_gen_pb2, pusher_pb2, trainer_pb2
from tfx.types import Channel
from tfx.types.standard_artifacts import Model, ModelBlessing
from tfx.utils.dsl_utils import external_input
from tfx.components import (Evaluator, ExampleValidator, ImportExampleGen,ModelValidator, Pusher, ResolverNode, SchemaGen,StatisticsGen, Trainer, Transform,Tuner)
from tfx.orchestration import (metadata, pipeline)
```


```
from tfx.orchestration.experimental.interactive.interactive_context
import InteractiveContext
from tfx.proto import (pusher_pb2, trainer_pb2)
from tfx.proto.evaluator_pb2 import SingleSlicingSpec
from tfx.utils.dsl_utils import external_input
```
```
from tfx.types.standard_artifacts import (Model, ModelBlessing)
tf.get_logger().propagate = False
pp = pprint.PrettyPrinter()
%load_ext tfx.orchestration.experimental.interactive.notebook_extensions.skip
```

## 设置目录并下载数据

设置根目录的步骤如下：

- 步骤 1：这是您的 TFX pip 包安装的根目录。
- 步骤 2：这是包含 TFX 芝加哥出租车管道示例的目录。
- 步骤 3：这是模型将被推送用于服务的路径。
- 步骤 4：设置日志记录。

```
def setting_directory():
#step1
_tfx_root = tfx.__path__[0]
```
```
print(_tfx_root)
#step2
_taxi_root = os.path.join(_tfx_root, 'examples/chicago_taxi_pipeline')
print(_taxi_root)
#step3
_serving_model_dir = os.path.join(tempfile.mkdtemp(),
'serving_model/taxi_simple')
print(_serving_model_dir)
#step4
absl.logging.set_verbosity(absl.logging.INFO)
return _tfx_root,_taxi_root,_serving_model_dir
```

现在，我们调用前面的函数来设置目录：

```
_tfx_root,_taxi_root,_serving_model_dir=setting_directory()
```

```
def download_data():
_data_root = tempfile.mkdtemp(prefix='tfx-data')
DATA_PATH = 'https://raw.githubusercontent.com/tensorflow/tfx/master/tfx/examples/chicago_taxi_pipeline/data/simple/data.csv'
_data_filepath = os.path.join(_data_root, "data.csv")
urllib.request.urlretrieve(DATA_PATH, _data_filepath)
return _data_root,_data_filepath
```

现在让我们调用前面的函数在目录中下载数据：

```
_data_root,_data_filepath = download_data()
```

让我们预览一下我们的数据集：

![](img/8f8a671916d96b455297952d0f37b96c_249_0.png)

Figure 4.3: 芝加哥数据集

在前面的截图中，我们可以看到数据集中包含的特征；我们将使用它与 TensorFlow 构建分类模型。

## 4.4 TFX 管道组件

TFX 提供了多个 Python 包库，这里将使用它们来创建管道组件。

在本节中，我们使用默认参数创建了 Interactive Context，这将有助于创建临时的 ML Metadata 数据库实例。

```
context = InteractiveContext()
```

```
WARNING:absl:InteractiveContext pipeline_root argument not provided: using temporary directory /tmp/tfx-interactive-2(
WARNING:absl:InteractiveContext metadata_connection_config not provided: using SQLite ML Metadata database at /tmp/tf
```

Figure 4.4: 初始化交互式上下文

接下来，我们将构建管道。

### 4.4.1 ExampleGen

ExampleGen 组件通常位于 TFX 管道的开始处。TFX examplegen 将自定义训练/评估拆分比例，ExampleGen 将输出并设置 **output_config**；例如，Gen 组件。Span 中的每个 Version 都可以进一步细分为多个 Splits。将 Span 分割的最常见用例是将其拆分为训练和评估数据。

本示例中设置了 **hash_buckets**。

![](img/8f8a671916d96b455297952d0f37b96c_251_0.png)

Figure 4.5: Example Gen

前面的图表是 example gen 组件，它将以这种方式拆分数据集。所以，这是 ExampleGen 的架构。

### 组件：ExampleGen

![](img/8f8a671916d96b455297952d0f37b96c_252_0.png)

Figure 4.6: Example Gen 架构

ExampleGen TFX Pipeline 组件将数据摄取到 TFX 管道中。

```
def examplegen(_data_root):
example_gen = CsvExampleGen(input=external_input(_data_root))
return example_gen
```

定义我们下载数据的路径：

```
example_gen= examplegen(_data_root)
context.run(example_gen)
```

![](img/8f8a671916d96b455297952d0f37b96c_253_0.png)

Figure 4.7: Example Gen 输出

前面的截图是 ExampleGen 的输出，我们在其中将数据拆分为训练和评估，并将路径存储如图所示。

### 4.4.2 StatisticsGen

StatisticsGen 组件计算您数据集的统计信息，用于数据分析以及下游组件使用。它使用 TensorFlow Data Validation 库。

### 组件：StatisticsGen

![](img/8f8a671916d96b455297952d0f37b96c_254_0.png)

Figure 4.8: Statistics Gen 架构

StatisticsGen 的输入是我们刚刚使用 ExampleGen 摄取的数据集：

```
def statisticsgen(example_gen):
statistics_gen =
StatisticsGen(examples=example_gen.outputs['examples'])
return statistics_gen
```

```
statistics_gen=statisticsgen(example_gen)
context.run(statistics_gen)
```

![](img/8f8a671916d96b455297952d0f37b96c_255_0.png)

Figure 4.9: Statistics Gen 输出

可视化我们训练数据和评估数据的输出统计信息：

```
%%skip_for_export
context.show(statistics_gen.outputs['statistics'])
```

StatisticsGen 将为我们提供所有特征的分布以及分类和数值列的统计信息，从中我们可以分析偏度和缺失值分析。

![](img/8f8a671916d96b455297952d0f37b96c_255_1.png)

Figure 4.10: Statistics Gen 输出可视化

StatisticsGen TFX 管道组件生成训练数据和服务数据的特征统计信息，可供其他管道组件使用。StatisticsGen 使用 Beam 来扩展到大型数据集。

### 4.4.3 SchemaGen

SchemaGen 组件基于您的数据统计信息生成模式。（模式定义了数据集中特征的预期边界、类型和属性。）它也使用 TensorFlow Data Validation 库。

### 组件：SchemaGen

![](img/8f8a671916d96b455297952d0f37b96c_257_0.png)

Figure 4.11: Schema Gen 架构

SchemaGen 将以我们使用 StatisticsGen 生成的统计信息作为输入，默认情况下查看训练拆分。

```
def schemagen(statistics_gen):
schema_gen =
SchemaGen(statistics=statistics_gen.outputs['statistics'],infer_feature_shape=False)
return schema_gen
```

让我们生成模式表：

```
schema_gen=schemagen(statistics_gen)
%%skip_for_export
context.show(schema_gen.outputs['schema'])
```

输入张量的数据类型模式如下：

| 特征名称 | 类型 | 存在性 | 价数 | 域 |
|---|---|---|---|---|
| 'company' | STRING | 必需 |  | 'company' |
| 'dropoff_census_tract' | INT | 必需 |  | - |
| 'dropoff_community_area' | INT | 必需 |  | - |
| 'dropoff_latitude' | FLOAT | 必需 |  | - |
| 'dropoff_longitude' | FLOAT | 必需 |  | - |
| 'fare' | FLOAT | 必需 | single | - |
| 'payment_type' | STRING | 必需 | single | 'payment_type' |
| 'pickup_census_tract' | INT | 必需 |  | - |
| 'pickup_community_area' | INT | 必需 |  | - |
| 'pickup_latitude' | FLOAT | 必需 |  | - |
| 'pickup_longitude' | FLOAT | 必需 |  | - |
| 'tips' | FLOAT | 必需 | single | - |
| 'trip_miles' | FLOAT | 必需 | single | - |
| 'trip_seconds' | INT | 必需 |  | - |
| 'trip_start_day' | INT | 必需 | single | - |
| 'trip_start_hour' | INT | 必需 | single | - |
| 'trip_start_month' | INT | 必需 | single | - |
| 'trip_start_timestamp' | INT | 必需 | single | - |

Figure 4.12: Schema Gen 输出可视化

所以，schema 是 It 将指定特征值的... The SchemaGen 组件将通过从训练数据自动推断类型、类别和范围来生成该模式。

### 4.4.4 ExampleValidator

**ExampleValidator** 组件根据模式定义的期望检测数据中的异常。它也使用 **TensorFlow Data Validation** 库。

### 组件：ExampleValidator

![](img/8f8a671916d96b455297952d0f37b96c_260_0.png)

Figure 4.13: ExampleValidator 架构

**ExampleValidator** 将以来自 StatisticsGen 的统计信息和来自 SchemaGen 的模式作为输入。默认情况下，它将评估拆分的统计信息与训练拆分的模式进行比较。

```
def examplevalidator(statistics_gen,schema_gen):
 example_validator =
 ExampleValidator(statistics=statistics_gen.outputs['statistics'],schema=
 schema_gen.outputs['schema'])
 return example_validator
```

让我们调用该函数来检查异常报告。



```
example_validator = ExampleValidator(statistics_gen,schema_gen)
context.run(example_validator)
```

可视化异常表：

```
%%skip_for_export
context.show(example_validator.outputs['anomalies'])
```

工件位于 /tmp/tfx-interactive-2020-10-30T18_40_25.173616-vnjm_j02/ExampleValidator/anomalies/4

'train' 分割：

未发现异常。
'eval' 分割：

未发现异常。
导出到管道时，此单元格将被跳过。

## 图 4.14：ExampleValidator 异常表

因此，ExampleValidator 管道组件会在训练和服务数据中查找异常。它有助于检测我们数据中的不同异常类别。请看以下内容：

它执行有效性检查，将数据统计信息与模式进行比较，该模式将规范化用户的期望。

接下来，它通过检查训练数据和服务数据之间的比较来帮助检测训练-服务偏差。

它通过查看一系列数据来帮助检测数据漂移。

## 4.4.5 转换

Transform 组件为训练和服务执行特征工程。Transform 组件处理我们摄取到管道中的数据，以及之前生成的数据集模式，并输出以下两个工件：

TFRecords 格式的预处理训练和评估数据集。生成的数据集可在管道的 Trainer 组件中下游使用。

导出的预处理图（带资源），将在导出机器学习模型时使用。

![](img/8f8a671916d96b455297952d0f37b96c_263_0.png)

图 4.15：Transform 架构

**步骤** Transform 用于通过完成以下步骤来转换数值和分类独热编码特征、分桶特征以及原始字符串表示数据：

**步骤** 假设分类特征在数据集中各有一个最大值和密集浮点特征，并且分类特征分布在列表中。

**步骤** **tf.transform** 用于编码每个特征的桶数。

**步骤** **tf.transform** 用于编码 **VOCAB_FEATURES** 的词汇项数。

**步骤** 未识别的 **VOCAB_FEATURES** 被哈希的超出词汇表桶的数量。

**步骤** 指定目标特征列。

**步骤** 最佳做法是通过在特征名称后附加后缀（例如，_xf）来重命名特征。后缀有助于区分错误是源自输入特征还是输出特征，并防止我们在实际模型中意外使用未转换的特征。

```
%%skip_for_export
%%writefile {_taxi_constants_module_file}
```

```
# Step1
MAX_CATEGORICAL_FEATURE_VALUES = [24, 31, 12]
CATEGORICAL_FEATURE_KEYS = ['trip_start_hour', 'trip_start_day',
'trip_start_month',
'pickup_census_tract', 'dropoff_census_tract',
'pickup_community_area', 'dropoff_community_area']
DENSE_FLOAT_FEATURE_KEYS = ['trip_miles', 'fare', 'trip_seconds']

# Step2
FEATURE_BUCKET_COUNT = 10
BUCKET_FEATURE_KEYS = ['pickup_latitude', 'pickup_longitude',
'dropoff_latitude', 'dropoff_longitude']

# Step3
VOCAB_SIZE = 1000

# Step4

OOV_SIZE = 10
VOCAB_FEATURE_KEYS = ['payment_type','company']

# Step5
LABEL_KEY = 'tips'
FARE_KEY = 'fare'

#Step6
def transformed_name(key):
return key + '_xf'
```

我们管道中的 TFX Transform 组件期望转换代码提供在单独的 Python 文件中。模块文件的名称可以由用户设置（例如，在我们的例子中，但入口点 **preprocessing_fn()** 必须包含在模块文件中，并且函数不能重命名。将前面的 Python 代码导入到以下 transform 文件中：

预处理步骤和填充缺失值的转换代码如下：

**步骤** 从 Python 文件导入特征。

**步骤** tf.transform 用于预处理训练工件数据输入的回调函数。

**步骤** TensorFlow Transform 期望转换输出为密集的，因此我们使用以下辅助函数将稀疏特征转换为密集特征：

```
%%skip_for_export
%%writefile {_taxi_transform_module_file}
```

```
#Step1
import tensorflow as tf
import tensorflow_transform as tft
import taxi_constants
```

```
_DENSE_FLOAT_FEATURE_KEYS =
taxi_constants.DENSE_FLOAT_FEATURE_KEYS
```

```
_VOCAB_FEATURE_KEYS = taxi_constants.VOCAB_FEATURE_KEYS
_VOCAB_SIZE = taxi_constants.VOCAB_SIZE
_OOV_SIZE = taxi_constants.OOV_SIZE
_FEATURE_BUCKET_COUNT =
taxi_constants.FEATURE_BUCKET_COUNT
_BUCKET_FEATURE_KEYS = taxi_constants.BUCKET_FEATURE_KEYS
_CATEGORICAL_FEATURE_KEYS =
taxi_constants.CATEGORICAL_FEATURE_KEYS
_FARE_KEY = taxi_constants.FARE_KEY
_LABEL_KEY = taxi_constants.LABEL_KEY
_transformed_name = taxi_constants.transformed_name

#Step2
def preprocessing_fn(inputs):
outputs = {}
for key in _DENSE_FLOAT_FEATURE_KEYS:
# Preserve this feature as a dense float, setting nan's to the
mean.
outputs[_transformed_name(key)] =
tft.scale_to_z_score(_fill_in_missing(inputs[key]))

for key in _VOCAB_FEATURE_KEYS:
# Build a vocabulary for this feature.
outputs[_transformed_name(key)] =
tft.compute_and_apply_vocabulary(
_fill_in_missing(inputs[key]),top_k=_VOCAB_SIZE,num_oov_buckets=_OOV_SIZE)

for key in _BUCKET_FEATURE_KEYS:
```

```
outputs[_transformed_name(key)] =
tft.bucketize(_fill_in_missing(inputs[key]),
_FEATURE_BUCKET_COUNT,always_return_num_quantiles=False)
for key in _CATEGORICAL_FEATURE_KEYS:
outputs[_transformed_name(key)] = _fill_in_missing(inputs[key])

# Was this passenger a big tipper?
taxi_fare = _fill_in_missing(inputs[_FARE_KEY])
tips = _fill_in_missing(inputs[_LABEL_KEY])
outputs[_transformed_name(_LABEL_KEY)] =
tf.where(tf.math.is_nan(taxi_fare),
tf.cast(tf.zeros_like(taxi_fare), tf.int64),
# Test if the tip was > 20% of the fare.
tf.cast(tf.greater(tips, tf.multiply(taxi_fare, tf.constant(0.2))), tf.int64))
return outputs
```

```
#step3
def _fill_in_missing(x):
default_value = "" if x.dtype == tf.string else 0
return tf.squeeze(tf.sparse.to_dense(tf.SparseTensor(x.indices,
x.values, [x.dense_shape[0], 1]),default_value),axis=1)
```

以下函数是我们 Transform 函数针对所有特征的转换函数：

```
def transformation(example_gen,schema_gen):
transform =
Transform(examples=example_gen.outputs['examples'],schema=schema_gen.outputs['schema'],module_file=os.path.abspath(_taxi_transform_module_file))
```

```
return transform
```

当我们执行 transform 组件时，TensorFlow Extended 将应用在我们的 taxi_transform.py 模块文件中定义的转换，并将其应用于在数据摄取步骤期间加载到 TFRecords 的加载输入数据。然后组件将输出我们的转换数据、转换图和所需的元数据。

```
transform=transformation(example_gen,schema_gen)
context.run(transform)
```

![](img/8f8a671916d96b455297952d0f37b96c_269_0.png)

图 4.16：Transform 输出

前述屏幕截图显示了转换结构的输出数据结构。

```
}
feature {
  key: "pickup_longitude_xf"
  value {
    int64_list {
      value: 9
    }
  }
}
feature {
  key: "tips_xf"
  value {
    int64_list {
      value: 0
    }
  }
}
feature {
  key: "trip_miles_xf"
  value {
    float_list {
      value: -0.15886740386486053
    }
  }
}
```

图 4.17：Transform 序列化 json 输出

preprocessing_fn 函数，如前述函数所示，定义了我们希望应用于原始数据的所有转换。当我们执行 transform 组件时，preprocessing_fn 函数将接收原始数据，应用转换并返回处理后的数据。

## 4.4.6 调优器和训练器

Trainer 组件将训练你在 TensorFlow 中定义的模型（使用 Estimator API 或 Keras API）

现在，首先模型将使用超参数进行训练，然后它将使用 Trainer 组件训练模型，该组件将转换数据的模式和来自训练参数的图作为输入，以及包含用户定义模型代码的模块。

### 组件：Trainer

![](img/8f8a671916d96b455297952d0f37b96c_271_0.png)

图 4.18：Trainer 架构

Trainer 组件需要以下输入：

先前生成的数据模式，由数据验证生成。



转换后的数据及其预处理图。

训练参数（例如，训练步数）。

包含 run_fn() 函数的模块文件，该函数定义了训练过程。

![](img/8f8a671916d96b455297952d0f37b96c_272_0.png)

### 图 4.19：转换特征

## 预处理函数()

- 1. 如果你想将特征标准化为均值为 0、标准差为 1，可以使用这个有用的 TFT 函数。
- 2. 这个有用的函数让我们可以将特征分桶到区间中。它返回区间或桶的索引。你可以指定参数 **num_buckets** 来设置桶的数量。TFT 然后会将等大小的桶进行划分。
- 3. 这是 TensorFlow Transform 最令人惊叹的函数之一。它计算特征列的所有唯一值，然后将最频繁的值映射到索引。此索引映射随后用于将特征转换为数值表示。该函数在幕后为你的图生成所有资源。

Trainer 文件将通过完成以下步骤来训练估计器模型：

- **步骤** 在列表中导入特征。
- **步骤** 后缀有助于区分错误是源自输入特征还是输出特征，并且防止我们在实际模型中意外使用未转换的特征。
- **步骤** **Tf.Transform** 将这些特征视为“原始”。
- **步骤** 一个小型实用工具，返回可以读取 gzip 压缩文件的记录读取器。
- **步骤** **_build_estimator()** 函数将使用 estimator 创建 Wide 和 Deep 模型架构。
- 步骤 构建服务输入。
- 步骤 构建 tf-model-analysis 以运行模型。
- 步骤 通过数据生成器生成训练或评估的特征和标签。
- 步骤 TFX 将调用此函数作为主函数来执行所有实用函数。

```
%%skip_for_export
%%writefile {_taxi_trainer_module_file}
#Step1
import tensorflow as tf
import tensorflow_model_analysis as tfma
import tensorflow_transform as tft
from tensorflow_transform.tf_metadata import schema_utils
import taxi_constants

_DENSE_FLOAT_FEATURE_KEYS =
taxi_constants.DENSE_FLOAT_FEATURE_KEYS
_VOCAB_FEATURE_KEYS = taxi_constants.VOCAB_FEATURE_KEYS
_VOCAB_SIZE = taxi_constants.VOCAB_SIZE
_OOV_SIZE = taxi_constants.OOV_SIZE

_FEATURE_BUCKET_COUNT =
taxi_constants.FEATURE_BUCKET_COUNT
_BUCKET_FEATURE_KEYS = taxi_constants.BUCKET_FEATURE_KEYS
_CATEGORICAL_FEATURE_KEYS =
taxi_constants.CATEGORICAL_FEATURE_KEYS
```

```
_MAX_CATEGORICAL_FEATURE_VALUES =
taxi_constants.MAX_CATEGORICAL_FEATURE_VALUES
_LABEL_KEY = taxi_constants.LABEL_KEY
_transformed_name = taxi_constants.transformed_name

#Step2
def _transformed_names(keys):
return [_transformed_name(key) for key in keys]

#Step3
def _get_raw_feature_spec(schema):
return schema_utils.schema_as_feature_spec(schema).feature_spec

#Step4
def _gzip_reader_fn(filenames):
return tf.data.TFRecordDataset(filenames,compression_type='GZIP')

#Step5
def _build_estimator(config, hidden_units=None,
warm_start_from=None):
real_valued_columns = [tf.feature_column.numeric_column(key,
shape=())
for key in _transformed_names(_DENSE_FLOAT_FEATURE_KEYS)]
categorical_columns =
[tf.feature_column.categorical_column_with_identity(
key, num_buckets=_VOCAB_SIZE + _OOV_SIZE, default_value=0)
for key in _transformed_names(_VOCAB_FEATURE_KEYS)]
categorical_columns +=
[tf.feature_column.categorical_column_with_identity(
key, num_buckets=_FEATURE_BUCKET_COUNT, default_value=0)
```

```
for key in _transformed_names(_BUCKET_FEATURE_KEYS)]
categorical_columns +=
[tf.feature_column.categorical_column_with_identity(key,
num_buckets=num_buckets,default_value=0) for key, num_buckets
in zip(
_transformed_names(_CATEGORICAL_FEATURE_KEYS),_MAX_CATEGORICAL_FEATURE_VALUES)]
return tf.estimator.DNNLinearCombinedClassifier(config=config,
linear_feature_columns=categorical_columns,dnn_feature_columns=real_valued_columns,
dnn_hidden_units=hidden_units or [100, 70, 50,
25],warm_start_from=warm_start_from)

#Step6
def _example_serving_receiver_fn(tf_transform_graph, schema):
raw_feature_spec = _get_raw_feature_spec(schema)
raw_feature_spec.pop(_LABEL_KEY)
raw_input_fn =
tf.estimator.export.build_parsing_serving_input_receiver_fn(
raw_feature_spec, default_batch_size=None)
serving_input_receiver = raw_input_fn()
transformed_features = tf_transform_graph.transform_raw_features(
serving_input_receiver.features)
return tf.estimator.export.ServingInputReceiver(
transformed_features, serving_input_receiver.receiver_tensors)

#Step7
def _eval_input_receiver_fn(tf_transform_graph, schema):
# Notice that the inputs are raw features, not transformed
features here.
```

```
raw_feature_spec = _get_raw_feature_spec(schema)
serialized_tf_example = tf.compat.v1.placeholder(
dtype=tf.string, shape=[None], name='input_example_tensor')
# Add a parse_example operator to the tensorflow graph, which
will parse raw, untransformed, tf examples.
features = tf.io.parse_example(serialized_tf_example,
raw_feature_spec)
# Now that we have our raw examples, process them through the
tf-transform function computed during the preprocessing step.
transformed_features = tf_transform_graph.transform_raw_features(
features)
# The key name MUST be 'examples'.
receiver_tensors = {'examples': serialized_tf_example}

# NOTE: Model is driven by transformed features (since training
works on the materialized output of TFT, but slicing will happen
on raw features.
features.update(transformed_features)
return tfma.export.EvalInputReceiver(features=features,receiver_tensors=receiver_tensors,
labels=transformed_features[_transformed_name(_LABEL_KEY)])
```

```
#Step8
def _input_fn(filenames, tf_transform_graph, batch_size=200):
transformed_feature_spec =
(tf_transform_graph.transformed_feature_spec().copy())
dataset = tf.data.experimental.make_batched_features_dataset(
filenames, batch_size, transformed_feature_spec,
reader=_gzip_reader_fn)
transformed_features =
(tf.compat.v1.data.make_one_shot_iterator(dataset).get_next())

# We pop the label because we do not want to use it as a feature while we're training.
return transformed_features,
transformed_features.pop(_transformed_name(_LABEL_KEY))
```

```
#Step9
def trainer_fn(trainer_fn_args, schema):
# Number of nodes in the first layer of the DNN
first_dnn_layer_size = 100
num_dnn_layers = 4
dnn_decay_factor = 0.7
train_batch_size = 40
eval_batch_size = 40

tf_transform_graph =
tft.TFTransformOutput(trainer_fn_args.transform_output)
train_input_fn = lambda:
_input_fn(trainer_fn_args.train_files,tf_transform_graph,
batch_size=train_batch_size)
eval_input_fn = lambda:
_input_fn(trainer_fn_args.eval_files,tf_transform_graph,
batch_size=eval_batch_size)
train_spec =
tf.estimator.TrainSpec(train_input_fn,max_steps=trainer_fn_args.train_steps)
serving_receiver_fn = lambda:
_example_serving_receiver_fn(tf_transform_graph, schema)
exporter = tf.estimator.FinalExporter('chicago-taxi',
serving_receiver_fn)
eval_spec =
tf.estimator.EvalSpec(eval_input_fn,steps=trainer_fn_args.eval_steps,
exporters=[exporter],name='chicago-taxi-eval')
```

```
run_config = tf.estimator.RunConfig(save_checkpoints_steps=999,
keep_checkpoint_max=1)
run_config =
run_config.replace(model_dir=trainer_fn_args.serving_model_dir)
estimator = _build_estimator(hidden_units=[max(2,
int(first_dnn_layer_size * dnn_decay_factor**i))for i in
range(num_dnn_layers)],config=run_config,
warm_start_from=trainer_fn_args.base_model)
# Create an input receiver for TFMA processing
receiver_fn = lambda: _eval_input_receiver_fn(# pylint: disable=g-long-lambda
tf_transform_graph, schema)

return {'estimator': estimator,'train_spec': train_spec,'eval_spec':
eval_spec,
'eval_input_receiver_fn': receiver_fn}
```

让我们使用训练和评估参数步骤构建 Tuner 函数：

```
def tuner_model(transform):
tuner =
Tuner(module_file=os.path.abspath(_taxi_trainer_module_file),
examples=transform.outputs['transformed_examples'],
transform_graph=transform.outputs['transform_graph'],
train_args=trainer_pb2.TrainArgs(num_steps=20),
eval_args=trainer_pb2.EvalArgs(num_steps=50))
return tuner
```

接下来，我们将创建一个 Trainer 函数，该函数将以 Tuner、Transform、Schema 作为模型训练的输入：

```
def trainer_model(transform,schema_gen,tuner):
 trainer =
 Trainer(module_file=os.path.abspath(_taxi_trainer_module_file),
 transformed_examples=transform.outputs['transformed_examples'],
 schema=schema_gen.outputs['schema'],
 transform_graph=transform.outputs['transform_graph'],
 hyperparameters=tuner.outputs['best_hyperparameters'],
 train_args=trainer_pb2.TrainArgs(num_steps=10000),
 eval_args=trainer_pb2.EvalArgs(num_steps=5000))
 return trainer
```

让我们调用 Tuner 组件并将其传递给训练器函数：

```
tuner=tuner_model(transform)
trainer=trainer_model(transform,schema_gen)
```

context.run(trainer)

![](img/8f8a671916d96b455297952d0f37b96c_280_0.png)

图 4.20：训练器输出

## 使用 TensorBoard 分析训练

可选地，我们可以将 TensorBoard 连接到训练器以分析我们模型的训练曲线。获取表示训练日志的输出工件的 URI，它是一个目录：

```
model_dir = trainer.outputs['model'].get()[0].uri
%load_ext tensorboard
%tensorboard --logdir {model_dir}
```

![](img/8f8a671916d96b455297952d0f37b96c_281_0.png)

图 4.21：Tensorboard 输出

在这里，我们将在 TensorBoard 中可视化 Batch Accuracy 和 Batch loss 以及 Epoch Loss 和 epoch accuracy。

## 4.4.7 评估器

评估器组件计算评估集上的模型性能指标。因此，评估器组件会自动将情感评估为概率。

### 组件：评估器

![](img/8f8a671916d96b455297952d0f37b96c_282_0.png)

图 4.22：评估器架构

让我们构建评估组件以评估模型性能：

```
def evaluation_configuration():
    eval_config = tfma.EvalConfig(
        model_specs=[tfma.ModelSpec(signature_name='eval')],
        metrics_specs=tfma.MetricsSpec(metrics=
            [tfma.MetricConfig(class_name='ExampleCount')],
            thresholds = {'accuracy': tfma.MetricThreshold(
                value_threshold=tfma.GenericValueThreshold(lower_bound={'value':
                0.5}),
change_threshold=tfma.GenericChangeThreshold(
 direction=tfma.MetricDirection.HIGHER_IS_BETTER,absolute={'value':
-1e-10}))],
 slicing_specs=[tfma.SlicingSpec(),tfma.SlicingSpec(feature_keys=
['trip_start_hour'])]
 return eval_config
```

在这里，我们将返回为评估器模型定义的指标：

```
eval_config = evaluation_configuration()
```

如果我们想将新模型与之前模型进行比较，则需要 Resolver 组件。它检查最后一个被祝福的模型并将其作为基线返回，以便可以将其与新的候选模型一起传递给评估器组件。

```
model_resolver =
ResolverNode(instance_name='latest_blessed_model_resolver',
resolver_class=latest_blessed_model_resolver.LatestBlessedModelResolver,
model=Channel(type=Model),model_blessing=Channel(type=ModelBlessing))
```

评估器组件使用 TFMA 库在验证数据集上评估模型的预测。它以来自 ExampleGen 组件的数据、来自训练器组件的训练模型以及 TFMA 的 EvalConfig 作为输入。

```
def evaluator_component(model_resolver):
evaluator =
Evaluator(examples=example_gen.outputs['examples'],model=trainer.outputs['model'],
baseline_model=model_resolver.outputs['model'],eval_config=eval_config)
return evaluator
evaluator=evaluator_component(model_resolver)
```

评估器有助于验证我们导出的模型，确认它们可以推送到生产环境。

### 4.4.7.1 公平性与 TFMA 可视化

**TensorFlow 模型分析** 有助于获取比模型训练期间使用的指标更详细的指标。TFMA 将指标可视化为模型版本之间的时间序列，并使我们能够在数据集的切片上查看指标。由于 Apache Beam，它也很容易扩展到大型评估集。

```
%%skip_for_export
context.show(evaluator.outputs['evaluation'])
```

![](img/8f8a671916d96b455297952d0f37b96c_285_0.png)

*图 4.23：TFMA 指标可视化*

TFMA 有助于在 EvalConfig 的 **metrics_specs** 参数中将它们可视化。

```
evaluation_uri = evaluator.outputs['output'].get()[0].uri
eval_result = tfma.load_eval_result(evaluation_uri)
```

```
tfma.addons.fairness.view.widget_view.render_fairness_indicator(eval_result)
```

Fairness Indicators 是一个库，可实现对二元和多类分类器的常用识别公平性指标的轻松计算。使用 Fairness Indicators 工具套件，您可以执行以下操作：

- 为分类模型计算常用识别的公平性指标。
- 将各子组之间的模型性能与基线或其它模型进行比较。
- 使用置信区间来揭示统计上显著的差异。
- 在多个阈值上执行评估。

![](img/8f8a671916d96b455297952d0f37b96c_286_0.png)

## 图 4.24：公平性指标可视化

Fairness Indicators 是模型分析的极其有用的工具。它与 TFMA 具有一些重叠的功能，但它特别有用的一个功能是能够在各种决策阈值下查看按特征切片的指标。

## 4.4.8 推送器

推送器组件通常位于 TFX 管道的末尾。它检查模型是否通过了验证，如果是，则将模型导出到

它以保存的模型、评估器组件的输出以及模型将存储供服务的文件路径作为输入。

### 组件：推送器

![](img/8f8a671916d96b455297952d0f37b96c_288_0.png)

图 4.25：推送器架构

让我们构建推送器组件，模型将自动推送以供服务。

```
def pusher_model(trainer,evaluator):
pusher = Pusher(model=trainer.outputs['model'],
model_blessing=evaluator.outputs['blessing'],
push_destination=pusher_pb2.PushDestination(
filesystem=pusher_pb2.PushDestination.Filesystem(base_directory=_serving_model_dir))
return pusher
```

接下来，调用推送器模型以将模型推送到可服务状态。

```
pusher=pusher_model(trainer,evaluator)
context.run(pusher)
```

![](img/8f8a671916d96b455297952d0f37b96c_289_0.png)

*图 4.26：推送器输出*

推送器组件提供了模型评估器输出和服务目标。它依赖于来自其它验证组件的一个或多个祝福模型来决定是否推送该模型。如果新训练的模型适合推送到生产环境，评估器就会祝福该模型。

## 4.5 使用 TF Serving 提供模型服务

现在我们有一个经过 ModelValidator 祝福并由 Pusher 推送到部署目标的训练模型，我们可以将其加载到 TensorFlow Serving 中并开始提供推理请求。

### 安装

我们正在准备使用 Aptitude 安装 TensorFlow Serving，因为此 Colab 在 Debian 环境中运行。我们将 tensorflow-model-server 包添加到 Aptitude 已知的包列表中。请注意，我们是以 root 身份运行的。此示例本机运行 TensorFlow Serving，但您也可以在 Docker 容器中运行它，这是开始使用 TensorFlow Serving 的最简单方法之一。

### 步骤

```bash
!echo "deb http://storage.googleapis.com/tensorflow-serving-apt stable tensorflow-model-server tensorflow-model-server-universal" | tee /etc/apt/sources.list.d/tensorflow-serving.list && \
curl https://storage.googleapis.com/tensorflow-serving-apt/tensorflow-serving.release.pub.gpg | apt-key add -
!apt update
```

### 步骤

## 在 Docker 容器中运行 TensorFlow Serving：

```
!apt-get install tensorflow-model-server
```

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
tensorflow-model-server
0 upgraded, 1 newly installed, 0 to remove and 13 not upgraded.
Need to get 210 MB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://storage.googleapis.com/tensorflow-serving-apt stable/tensorflow-model-server amd64 tensorflow-model
Fetched 210 MB in 3s (73.7 MB/s)
Selecting previously unselected package tensorflow-model-server.
(Reading database ... 144628 files and directories currently installed.)
Preparing to unpack .../tensorflow-model-server_2.3.0_all.deb ...
Unpacking tensorflow-model-server (2.3.0) ...
Setting up tensorflow-model-server (2.3.0) ...
```

图 4.27：安装输出

下一步是加载 Pusher，它将以 SavedModel 格式导出您的模型并加载路径。

```
latest_pushed_model = os.path.join(_serving_model_dir,
max(os.listdir(_serving_model_dir)))
!saved_model_cli show --dir {latest_pushed_model} --all
```

```
MetaGraphDef with tag-set: 'serve' contains the following SignatureDefs:

signature_def['classification']:
  The given SavedModel SignatureDef contains the following input(s):
    inputs['inputs'] tensor_info:
      dtype: DT_STRING
      shape: (-1)
```

图 4.28：显示图




## 开始运行 TensorFlow Serving

这里我们开始运行 TensorFlow Serving 并加载我们的模型。一旦加载完成，我们就可以使用 REST 开始进行推理请求。以下是一些重要参数：

- 用于 REST 请求的端口。你将在 REST 请求的 URL 中使用它。可以是任意值。
- 这是保存模型所在的目录的路径。请注意，此 **base_path** 不应包含模型版本目录，这就是我们将其拆分的原因，如下所示：

```
os.environ["MODEL_DIR"] = os.path.split(latest_pushed_model)[0]
%%bash --bg
nohup tensorflow_model_server \
--rest_api_port=8501 \
--model_name=online_news_simple \
--model_base_path="${MODEL_DIR}" >server.log 2>&1
!tail server.log
```

## 在示例数据上执行推理

让我们从 eval 数据集中加载一些示例，移除它们的标签（因为服务模型不期望标签），并通过一次 REST API 调用将它们发送到 Tensorflow Serving。

请注意，这将包含标签，但服务器会忽略它们。

```
eval_uri = example_gen.outputs['examples'].get()[0].uri
eval_tfrecord_paths = [os.path.join(eval_uri, name)for name in os.listdir(eval_uri)]
```

```
def strip_label(serialized_example):
example = tf.train.Example.FromString(serialized_example.numpy())
return example.SerializeToString()
```

```
dataset =
tf.data.TFRecordDataset(eval_tfrecord_paths,compression_type="GZIP")
serialized_examples = [strip_label(serialized_example)for serialized_example in dataset.take(3)]
```

在这里，我们对用于评估的转换后的数据进行了序列化，并制作了一个数据集 TFRecord。

向模型发送请求，并按如下方式打印结果：

- 模型服务器的网络地址，采用 "host:port" 格式。
- 模型服务器所理解的模型名称。
- 用于进行推理的数据的序列化示例。

```python
def do_inference(server_addr, model_name, serialized_examples):
parsed_server_addr = server_addr.split(':')
host=parsed_server_addr[0]
port=parsed_server_addr[1]
json_examples = []
for serialized_example in serialized_examples:
example_bytes = base64.b64encode(serialized_example).decode('utf-8')
predict_request = '{"b64": "%s"}' % example_bytes
json_examples.append(predict_request)

json_request = '{"instances": [' + ','.join(map(str, json_examples)) + '] }'
server_url = 'http://' + host + ':' + port + '/v1/models/' + 
model_name + ':predict'
response = requests.post(server_url, data=json_request, 
timeout=5.0)
response.raise_for_status()
prediction = response.json()
print(json.dumps(prediction, indent=4))
```

让我们为我们的样本数据集的预测调用推理函数：

```python
do_inference(server_addr='127.0.0.1:8501',
model_name='online_news_simple',
serialized_examples=serialized_examples)
```

```json
{
  "predictions": [
    {
      "scores": [
        0.775838792,
        0.224161178
      ],
      "classes": [
        "0",
        "1"
      ]
    },
    {
      "scores": [
        0.775838792,
        0.224161178
      ],
      "classes": [
        "0",
        "1"
      ]
    },
    {
      "scores": [
        0.775838792,
        0.224161178
      ],
      "classes": [
        "0",
        "1"
      ]
    }
  ]
}
```

### 图 4.29：测试模型预测

在前面的屏幕截图中，我们可以看到 3 条记录批次的分类输出，以及小费是否大于车费 20% 的概率得分。

## 4.6 构建 Kubeflow Pipeline 编排器

因此，在开始本章之前，我们必须在 GCP 中设置 Kubeflow 集群，我们已经创建了一个 Jupyter notebook；我们将使用它。

从 Kubeflow Dashboard 连接到 Jupyter Notebook 后打开终端一次并安装 TFX SDK。

```bash
!pip install tfx==0.22.0
```

如果出现以下错误，请运行以下命令：

![](img/8f8a671916d96b455297952d0f37b96c_296_0.png)

### 图 4.30：错误

运行以下命令：

```bash
PROTOC_ZIP=protoc-3.7.1-osx-x86_64.zip
```

```
curl -OL
https://github.com/protocolbuffers/protobuf/releases/download/v3.7.1/
$PROTOC_ZIP
sudo unzip -o $PROTOC_ZIP -d /usr/local bin/protoc
sudo unzip -o $PROTOC_ZIP -d /usr/local 'include/*'
rm -f $PROTOC_ZIP
pip install --upgrade protobuf
```

现在，请前往该项目的 GitHub 下载这些文件夹并将这些文件保存到你的 GCP Bucket 中，如以下屏幕截图所示：

![](img/8f8a671916d96b455297952d0f37b96c_297_0.png)

### 图 4.31：Kubeflow Pipeline 文件夹数据和文件

现在，让我们看看管道代码以及如何为 TFX 生成构造性管道。

完成以下步骤：

- 定义用于管道执行的管道参数。
- 模块文件的路径应为 GCS 路径，或烘焙在管道使用的 Docker 镜像中的模块文件。
- CSV 数据文件的路径，其下应有一个 **data.csv** 文件。
- 管道根路径应为 GCS 路径。
- 创建一个基于 Kubeflow 的简单 Chicago Taxi TFX 管道。
- 管道输出的根目录。
- 输入数据目录的位置。
- Transform/Trainer 模块文件的位置。
- 是否启用缓存。

管道是一个 **有向无环图**，每个节点上都有一个容器化进程，该进程运行在 argo 之上。

一个逻辑 TFX 管道对象。之后我们将构建 KubeflowDagRunner，它将转储一个 yaml 文件，该文件将用于在 Kubeflow 中部署以运行管道。

```
import os
from typing import Text
import kfp
import tensorflow_model_analysis as tfma
from tfx.components.evaluator.component import Evaluator
from tfx.components.example_gen.csv_example_gen.component import CsvExampleGen
from tfx.components.example_validator.component import ExampleValidator
from tfx.components.pusher.component import Pusher
from tfx.components.schema_gen.component import SchemaGen
from tfx.components.statistics_gen.component import StatisticsGen
from tfx.components.trainer.component import Trainer
from tfx.components.transform.component import Transform
from tfx.orchestration import data_types
from tfx.orchestration import pipeline
from tfx.orchestration.kubeflow import kubeflow_dag_runner
from tfx.utils.dsl_utils import external_input
from tfx.proto import pusher_pb2, trainer_pb2
```

### 步骤 1：

```
_taxi_module_file_param =
data_types.RuntimeParameter(name='module-file',
default='gs://tfx_taxi_simple/modules/taxi_utils.py',ptype=Text)
```

### 步骤 2：

```
_data_root_param = data_types.RuntimeParameter(name='data-root',
ptype=Text
default='gs:///tfx_taxi_simple/data')
```

### 步骤 3：

```
pipeline_root = os.path.join('gs://{{kfp-default-bucket}}',
'tfx_taxi_simple', kfp.dsl.RUN_ID_PLACEHOLDER)
```

### 步骤 4：

```
def _create_pipeline(pipeline_root: Text, csv_input_location:
data_types.RuntimeParameter,
taxi_module_file: data_types.RuntimeParameter, enable_cache: bool):
examples = external_input(csv_input_location)
example_gen = CsvExampleGen(input=examples)
statistics_gen =
StatisticsGen(examples=example_gen.outputs['examples'])
infer_schema =
SchemaGen(statistics=statistics_gen.outputs['statistics'],
infer_feature_shape=False)
validate_stats =
ExampleValidator(statistics=statistics_gen.outputs['statistics'],
schema=infer_schema.outputs['schema'],)
transform = Transform(examples=example_gen.outputs['examples'],
schema=infer_schema.outputs['schema'],module_file=taxi_module_file)
trainer = Trainer(module_file=taxi_module_file,
transformed_examples=transform.outputs['transformed_examples'],
schema=infer_schema.outputs['schema'],
transform_graph=transform.outputs['transform_graph'],
train_args=trainer_pb2.TrainArgs(num_steps=10),
eval_args=trainer_pb2.EvalArgs(num_steps=5))
```

```
eval_config = tfma.EvalConfig(model_specs=
[tfma.ModelSpec(signature_name='eval')], metrics_specs=
[tfma.MetricsSpec(metrics=
[tfma.MetricConfig(class_name='ExampleCount')], thresholds=
{'binary_accuracy':tfma.MetricThreshold(
value_threshold=tfma.GenericValueThreshold(lower_bound={'value':
0.5}), change_threshold=tfma.GenericChangeThreshold(
direction=tfma.MetricDirection.HIGHER_IS_BETTER,absolute={'value':
-1e-10})})], slicing_specs=
[tfma.SlicingSpec(),tfma.SlicingSpec(feature_keys=['trip_start_hour'])]
model_analyzer =
Evaluator(examples=example_gen.outputs['examples'],
model=trainer.outputs['model'],eval_config=eval_config)
pusher = Pusher(model=trainer.outputs['model'],
model_blessing=model_analyzer.outputs['blessing'],
push_destination=pusher_pb2.PushDestination(
filesystem=pusher_pb2.PushDestination.Filesystem(
base_directory=os.path.join(str(pipeline.ROOT_PARAMETER),
'model_serving'))),)

return
pipeline.Pipeline(pipeline_name='parameterized_tfx_oss',pipeline_root
=pipeline_root, components=[example_gen, statistics_gen,
infer_schema, validate_stats, transform, trainer, model_analyzer,
pusher],enable_cache=enable_cache)
if __name__ == '__main__':
enable_cache = True
pipeline =
_create_pipeline(pipeline_root,_data_root_param,_taxi_module_file_param, enable_cache=enable_cache)
metadata_config =
kubeflow_dag_runner.get_default_kubeflow_metadata_config()
```



```
config = kubeflow_dag_runner.KubeflowDagRunnerConfig(
 kubeflow_metadata_config=metadata_config, tfx_image='gcr.io/tfx-oss-public/tfx:0.22.0')
 kfp_runner =
 kubeflow_dag_runner.KubeflowDagRunner(output_filename='pipe9' +
 '.yaml', config=config)
 kfp_runner.run(pipeline)
```

运行上述代码后，它将转储一个 yaml，如以下屏幕截图所示。在运行文件之前，请在此处步骤1/2中替换存储桶名称。

![](img/8f8a671916d96b455297952d0f37b96c_302_0.png)

图 4.32: Kubeflow Pipeline yaml

一旦我们转储了 yaml，请完成以下步骤以在 Kubeflow 中运行管道：

在 Kubeflow pipeline 中上传 pipeline.yaml 文件，然后单击

![](img/8f8a671916d96b455297952d0f37b96c_303_0.png)

图 4.33: Upload pipeline.yaml

接下来，如果尚未创建，请创建一个实验；我们在之前的章节中已经完成了此操作。之后，单击 Run 并选择该管道。

![](img/8f8a671916d96b455297952d0f37b96c_303_1.png)

图 4.34: Create Run

在启动管道之前，运行‘choose an experiment’然后更改以下参数，例如替换您的存储桶名称；例如：tfx-pipeline 是我的存储桶名称，tfx 是我的实验名称。

单击

![](img/8f8a671916d96b455297952d0f37b96c_304_0.png)

图 4.35: Pipeline parameters

之后，管道将准备就绪，如以下屏幕截图所示：

![](img/8f8a671916d96b455297952d0f37b96c_305_0.png)

图 4.36: Pipeline of TFX

每个管道组件以块的形式表示，是一个自包含的代码片段，打包为 Docker 镜像。它包含输入（参数）和输出，并在管道中执行一个步骤。在前面显示的示例管道中，transform_data 步骤需要作为 extract_data 和 generate_schema 步骤的输出而产生的参数，其输出是依赖项

您的 ML 代码被封装到组件中，您可以在其中执行以下操作：

指定 **parameters** – 这些参数可在仪表板中编辑，并且可为每次运行配置。

附加 **persistent volumes** – 如果不添加持久卷，当我们的笔记本因任何原因终止时，我们将丢失所有数据。

指定 **artifacts** 要生成的 – 图表、表格、选定的图像、模型 – 这些最终会方便地存储在 Kubeflow 仪表板内的 Artifact Store 中。

最后，当您运行管道时，每个容器将根据 Kubernetes 调度在整个集群中执行，同时考虑依赖关系。这种容器化架构使得在工作流程发生变化时（这种情况往往会发生）轻松重用、共享或替换组件。

![](img/8f8a671916d96b455297952d0f37b96c_307_0.png)

图 4.37: Kubeflow pipeline visualization

运行管道后，您将能够在 **pipelines** 调试中探索结果，调整参数，并通过使用不同的参数或数据源执行管道来运行实验。

现在，在管道完成后，运行转储在 GCS 存储桶内的模型工件。在以下屏幕截图中，我们可以看到服务模型目录：

存储桶详情

tfx-pipeline

Buckets > [redacted] > tfx_taxi_simple > 6d011835-562c-49d0-bea2-a06048a601ce

对象  配置  权限  保留  生命周期

上传文件  上传文件夹  创建文件夹  管理保留  删除

过滤  按对象或文件夹名称前缀过滤

| 名称 | 大小 | 类型 | 创建时间 | 存储类别 | 最后修改 | 公共访问 |
|---|---|---|---|---|---|---|
| CsvExampleG | - | 文件夹 | - | - | - | - |
| Evaluator/ | - | 文件夹 | - | - | - | - |
| ExampleValidi | - | 文件夹 | - | - | - | - |
| Pusher/ | - | 文件夹 | - | - | - | - |
| SchemaGen/ | - | 文件夹 | - | - | - | - |
| StatisticsGen/ | - | 文件夹 | - | - | - | - |
| Trainer/ | - | 文件夹 | - | - | - | - |
| Transform/ | - | 文件夹 | - | - | - | - |
| model_servin | - | 文件夹 | - | - | - | - |

图 4.38: Kubeflow pipeline Artifacts & Model in GCS

## 4.7 结论

在本章中，我们学习了如何为 BERT 模型构建 TFX 管道以实现生产就绪，并集成可视化工具，如 Fairness、Tensorboard、TFMA。

我们还学习了如何从 TF-HUB 加载 BERT 模型以及如何使用它。然后，我们学习了在训练模型之前的数据转换管道。我们还学习了如何使用分布式 GPU 节点策略训练我们的 BERT 模型。然后，我们使用 TFX 组件创建了一个管道，并使用公平性指标和指标可视化和评估了被祝福的模型。然后，我们加载了服务器模型并使用示例电影评论进行测试并检查其情感概率。

## 4.8 参考

https://www.tensorflow.org/tfx/tutorials

https://www.tensorflow.org/responsible_ai/fairness_indicators/tutorials/Fairness_Indicators_Example_Colab

# 第 5 章

# ML Model Explainability & Interpretability

在本章中，我们将针对酒店预订数据集的分类模型进行工作，训练 TensorFlow 和 boosting 模型，并使用 Tensorboard、Shap 和 What-if 产品可视化我们模型结果的高级解释。

### 结构

在本章中，我们将涵盖以下主题：

- 问题陈述
- 在 Colab 中开始 Python 库安装和数据加载
- 用于训练模型的特征转换
- LightGBM 模型训练
- 使用 Shap 工具进行高级可视化的模型分析
- TensorFlow Estimator 模型构建框架
- 使用 Tensorboard、What-IF 工具和公平性进行 TensorFlow 模型的高级可视化

### 目标

学习本章后，我们将能够理解以下内容：

Shapely Additive explanations 的实现以及如何使用其在模型评估上的不同方法。

如何从头开始构建 LightGBM 模型。

用于模型分析的不同高级 Shap 图。

如何端到端构建 TensorFlow Estimator 框架。

如何使用 What-if 工具以及公平性指标评估模型性能。

## 5.1 问题

此数据集的问题陈述包含城市酒店和度假村酒店的预订信息，其中包括一些信息，例如预订时间、入住时长、成人、儿童或婴儿的人数以及可用停车位数量等。

你有没有想过一年中预订酒店房间的最佳时间是什么时候？或者想过为了获得最佳日费率，最佳入住时长是多少？或者，如果你想预测酒店是否熟悉收到不成比例的高数量的特殊请求怎么办？

请求？ 请求？ 请求？ 请求？ 请求？ 请求？
请求？ 请求？ 请求？ 请求？ 请求？ 请求？
请求？ 请求？ 请求？ 请求？ 请求？ 请求？
请求？ 请求？ 请求？ 请求？ 请求？ 请求？
请求？ 请求？ 请求？ 请求？ 请求？ 请求？
请求？

请求？

## 5.2 General idea and concept behind Shap

SHAP 的目标是通过计算每个特征对预测的贡献来解释实例 x 的预测。从联盟博弈论来看，shapely 值是从 SHAP 解释方法计算得出的。每个特征值实例充当联盟中的玩家。如何公平地将预测分配给特征，Shapley 值告诉我们这一点。玩家是一个单独的特征值，例如来自表格数据。特征值的组也可以是一个玩家。

例如，图像像素之间的预测分布也可以分组为超像素。SHAP 带来的创新之一是加性特征归因方法，一种解释 Shapley 值的线性模型。

SHAP 将解释指定如下：

g(z') = ∅ₒ + ∑_{j=0}^{M} ∅_j Z'_j

SHAP 描述了以下三个理想属性：

### Local accuracy



f(x) = g(x') = φ₀ + ∑_{j=1}^{M} φ_J X'_J

对于 x' 全部设为 1，它是 Shapley 的效率性质；只是名称不同并且使用了联盟向量。

f(x̂) = φ₀ + ∑_{j=1}^{M} φ_J X'_J = E_x (f̂(x)) + ∑_{j=1}^{M} φ_J

## 缺失性

= 0 => 0

它说明缺失的特征获得的归因值为零。请注意这指的是联盟，其中值 0 表示特征值的缺失。在联盟表示法中，待解释实例的所有特征值都应为 '1'。出现 0 表示该特征值缺失。

## 一致性

设 (z')) 和 z(j') 表示 zj' = 0。对于满足以下条件的任意两个模型 f 和 f'：

(z') - >= (z') -

对于所有输入 z' ∈ 则：

(f,x)

一致性性质说明，如果模型发生变化使得特征值的边际贡献无论其他特征如何都增加或保持不变，则 Shapley 值也会增加或保持不变。

![](img/8f8a671916d96b455297952d0f37b96c_317_0.png)

## 图 5.1：Shap 解释示例

例如，对于向量 (1,0,1,0)，它表示第一个和第三个特征具有联盟。回归模型的数据集变为 K 个采样的联盟。因此，对于回归模型，目标变为对联盟的预测。

我们需要一个函数 (z') = z where → 来获取从特征值的联盟中有效的数据实例。因此，映射到 1 的相应值到实例 x，我们将在此

解释。现在，对于表格形式的数据，它将 0 映射到我们从样本数据中获得的另一个实例值。这说明接下来我们将把“缺失的特征值”与“特征值”相等，并用来自数据的随机特征值集合替换它。

现在，从 figure_functions 将有效实例映射到联盟。接下来，映射 x 的特征值 (1) 到存在的特征。

对于缺失的特征 (0)，映射随机采样数据实例的值。对于表格数据，将特征视为独立并在边际分布上积分：

(z') = [f(x)]

在博弈论中，SHAP 具有 **坚实的理论** 特征值之间的公平分配预测将预测与平均预测进行比较以获得 **对比性解释。**

## 5.3 使用 Python 库在 Colab 中开始安装和数据加载

现在，我们将开始安装 Shap 和 Witwidget 库。

```
!pip install shap
```

```
Successfully built shap
Installing collected packages: shap
Successfully installed shap-0.35.0
```

## 图 5.2：Shap 的安装

```
try:
import google.colab
!pip install --upgrade witwidget
except:
pass
```

```
Requirement already satisfied, skipping upgrade: pyparsing>=2.0.2 i
Installing collected packages: witwidget
Successfully installed witwidget-1.6.0
```

## 图 5.3：wit-widget 的安装

我们已成功安装了 wit-widget 和 Shap 可视化工具。

现在我们将导入所需的库。

```
import numpy as np
import tensorflow as tf
from pprint import pprint
import lightgbm as lgb
import shap, warnings, functools
from sklearn.model_selection import train_test_split, StratifiedKFold
from sklearn.preprocessing import LabelEncoder
```

```
data=pd.read_csv("hotel_bookings.csv")
data.head()
```

![](img/8f8a671916d96b455297952d0f37b96c_320_0.png)

图 5.4：酒店预订数据集表

```
data.is_canceled.value_counts()
```

![](img/8f8a671916d96b455297952d0f37b96c_320_1.png)

图 5.5：目标列分布

在前面的屏幕截图中，我们可以看到目标预测列的值计数分布。

现在，根据我们的领域知识和理解，我们手动选择了一些列。

```
features =
["lead_time","arrival_date_week_number","arrival_date_day_of_month",
"stays_in_weekend_nights","stays_in_week_nights","adults","children",
"babies","is_repeated_guest", "previous_cancellations",
"previous_bookings_not_canceled","agent","company",
"required_car_parking_spaces", "total_of_special_requests",
"adr","hotel","arrival_date_month","meal","market_segment",
"distribution_channel","reserved_room_type","deposit_type","customer_type","is_canceled"]

Raw_Data=data[features]
```

## 5.4 训练模型的特征转换

现在我们将为数据框创建一些副本并且不更改原始数据框，这样我们就可以在不干预任何更改的情况下将其用于进一步分析。

```
X = Raw_Data.drop(["is_canceled"], axis=1)
y = Raw_Data["is_canceled"]
X_display =X.copy()
y_display = y.copy()
X_new=X.copy()
```

接下来，我们将检查数据集的数据类型并对分类特征进行必要的转换。

## X.dtypes

| 特征 | 数据类型 |
|---|---|
| lead_time | int64 |
| arrival_date_week_number | int64 |
| arrival_date_day_of_month | int64 |
| stays_in_weekend_nights | int64 |
| stays_in_week_nights | int64 |
| adults | int64 |
| children | float64 |
| babies | int64 |
| is_repeated_guest | int64 |
| previous_cancellations | int64 |
| previous_bookings_not_canceled | int64 |
| agent | float64 |
| company | float64 |
| required_car_parking_spaces | int64 |
| total_of_special_requests | int64 |
| adr | float64 |
| hotel | object |
| arrival_date_month | object |
| meal | object |
| market_segment | object |
| distribution_channel | object |
| reserved_room_type | object |
| deposit_type | object |
| customer_type | object |
| dtype | object |

## 图 5.6：特征的数据类型

在前面的屏幕截图中，我们可以看到需要转换的数据类型对象，因为该数据集中没有缺失值。因此，我们将处理所有分类列，如 deposit_type、meal、customer_type 等。

以下是转换的函数，因为我们将在对象数据类型列中使用标签编码器并遍历它们并替换数据集列。

```
def transform_categorical():
s = (X.dtypes == 'object')
```

```
object_cols = list(s[s].index)
print(object_cols)
for i in object_cols:
    lb_make = LabelEncoder()
    X[i] = lb_make.fit_transform(X[i])
#for i in object_cols:
# X[i] = X[i].astype(float)
return X
X=transform_categorical()
X.head()
```

![](img/8f8a671916d96b455297952d0f37b96c_324_0.png)

## 图 5.7：转换表

现在，我们已经转换了数据集；接下来，我们将拆分数据集用于训练并训练我们的模型。

```
def data_split():
    random_state = 7
    X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2,
    random_state=random_state)
    return X_train, X_test, y_train, y_test
X_train, X_test, y_train, y_test=data_split()
```

现在，我们已准备好训练模型。

## 5.5 LightGBM 模型训练

LightGBM 使用基于直方图算法将连续特征（属性）值分桶到离散 bin 中。这加快了训练速度并减少了内存使用。有关进一步阅读，请访问以下链接：

https://lightgbm.readthedocs.io/en/latest/Features.html

现在，我们将为 LightGBM 模型创建数据准备。

```
d_train = lgb.Dataset(X_train, label=y_train)
d_test = lgb.Dataset(X_test, label=y_test)
```

```
random_state=7
params = {
"max_bin": 512, "learning_rate": 0.05,"boosting_type": "gbdt",
"objective": "binary","metric": "binary_logloss", "num_leaves": 10,
"verbose": -1, "min_data": 100, "boost_from_average": True,
"random_state": random_state
}
```

让我们对模型参数做一个简要总结：

**max_bin default = type = constraints: max_bin > 1** 因此，特征值将被分桶的最大 bin 数，较小的 bin 数会降低训练精度但可能增加泛化能力（处理过拟合）。

**boosting_type** 是选择算法技术传统梯度提升决策树。

**Num_leaves** 它是一个树中叶子的最大数量。

因此，有许多参数我们可以从以下链接详细学习：

https://lightgbm.readthedocs.io/en/latest/Parameters.html

接下来，我们将训练我们的模型。

```
model = lgb.train(params, d_train, 10000, valid_sets=[d_test],
early_stopping_rounds=50, verbose_eval=1000)
```

```
Training until validation scores don't improve for 50 rounds.
[1000]  valid_0's binary_logloss: 0.344903
[2000]  valid_0's binary_logloss: 0.334606
[3000]  valid_0's binary_logloss: 0.32872
[4000]  valid_0's binary_logloss: 0.325002
[5000]  valid_0's binary_logloss: 0.322382
Early stopping, best iteration is:
[5889]  valid_0's binary_logloss: 0.320531
```

*图 5.8：LightGBM 模型输出*



接下来，我们将借助 SHAP 这一先进的 AI 技术可视化我们的结果，以获得更好的可见性。

## 5.6 使用 SHAP 工具进行高级可视化的模型分析

在本节中，我们将可视化模型结果的不同模式和分析。现在，我们将计算前 20 个测试观测值的 SHAP 值和 SHAP 交互值。

```
explainer = shap.TreeExplainer(model)
expected_value = explainer.expected_value
if isinstance(expected_value, list):
expected_value = expected_value[1]
print(f"Explainer expected value: {expected_value}")
```

```
select = range(20)
features = X_test.iloc[select]
features_display = X_display.loc[features.index]
```

```
with warnings.catch_warnings():
warnings.simplefilter("ignore")
shap_values = explainer.shap_values(features)[1]
shap_interaction_values = explainer.shap_interaction_values(features)
if isinstance(shap_interaction_values, list):
shap_interaction_values = shap_interaction_values[1]
```

由于未提供背景数据，因此将 feature_perturbation 设置为 "tree_path_dependent"。
Explainer expected value: [-0.22869578]

图 5.9：SHAP 计算值

所以，现在解释器值为 -0.22；接下来，我们查看模式和关系分析。

### 5.6.1 基本决策图特征

请参考以下 20 个测试观测值的决策图；请注意，该图本身并无信息性；我们仅将其用于说明主要概念：

x 轴表示模型的输出。在本例中，单位为对数几率。

该图在 x 轴上以期望值为中心。所有 SHAP 值都相对于模型的期望值，就像线性模型的效应相对于截距一样。

y 轴列出模型的特征。默认情况下，特征按其重要性降序排列。重要性是根据绘制的观测值计算的。这通常与整个数据集的重要性排序不同。除了特征重要性排序外，决策图还支持分层聚类特征排序和用户定义的特征排序。

每个观测值的预测由一条彩色线表示。在图的顶部，每条线在其对应观测值的预测值处与 x 轴相交。该值决定了线条在光谱上的颜色。

从图的底部向上移动，每个特征的 SHAP 值会加到模型的基础值上。这显示了每个特征如何对整体预测做出贡献。

在图的底部，观测值趋于收敛

```
shap.decision_plot(expected_value, shap_values, features_display)
```

![](img/8f8a671916d96b455297952d0f37b96c_331_0.png)

图 5.10：SHAP 模型输出值

现在，我们可以从前面的屏幕截图中看到，期望值在 -0.22，且在图的底部，观测值趋于收敛。

与力图类似，决策图支持 link='logit' 将对数几率转换为概率。

```
shap.decision_plot(expected_value, shap_values, features_display, link='logit')
```

![](img/8f8a671916d96b455297952d0f37b96c_332_0.png)

图 5.11：SHAP 模型对数转换输出

### 交互的累积效应：

决策图支持 SHAP 交互值。因此，从基于树的模型中估计了二阶交互。SHAP 依赖图提供了个体的交互可视化，其中绘制决策图以显示主要效应和数据中某个观测值与其他观测值之间的交互的累积效应。

### 5.6.2 力图分析

可以使用虚线样式突出显示观测值。
在这里，我们突出显示了一个被错误分类的观测值。我们的朴素截止点是对数几率为零（概率 0.5）。

```
y_pred = (shap_values.sum(1) + expected_value) > 0
misclassified = y_pred != y_test[:20]
shap.decision_plot(expected_value, shap_values, features_display,
link='logit', highlight=misclassified)
```

![](img/8f8a671916d96b455297952d0f37b96c_334_0.png)

图 5.12：SHAP 模型朴素截断阈值图

让我们单独绘制该被错误分类的观测值进行检查。当单独绘制一个观测值时，其对应的特征值会显示出来。请注意线的形状已发生变化。为什么？y 轴上的特征顺序已根据该行观测值的重要性而改变。*order and scale between* 部分展示了如何为多个图使用相同的特征顺序。

```
shap.decision_plot(expected_value, shap_values[misclassified],
features_display[misclassified],link='logit', highlight=o)
```

![](img/8f8a671916d96b455297952d0f37b96c_336_0.png)

图 5.13：SHAP 错误分类输出

以下是被错误分类观测值的力图。在这种情况下，决策图和力图都有效地显示了模型如何得出其决策。

```
%matplotlib inline
shap.initjs()
shap.force_plot(expected_value, shap_values[misclassified],
features_display[misclassified],
link='logit', matplotlib=False,show=True)
```

![](img/8f8a671916d96b455297952d0f37b96c_337_0.png)

图 5.14：SHAP 力图决策错误分类

从前面的 JavaScript 动态可视化中进行错误分类分析，我们可以通过查看这些结果来推断手动解释。本节的重点是构建架构以及如何使用我们的数据集。

## 5.7 TensorFlow Estimator 模型框架构建

在本节中，我们将着手构建 TensorFlow Estimator 模型，然后使用 Tensorboard 和 what-if 工具分析模型分析。接下来，我们将通过拆分数据集来构建训练数据集。

```
X = Raw_Data.drop(["is_canceled"], axis=1)
y = Raw_Data["is_canceled"]
from sklearn.model_selection import train_test_split
xTrain, xTest, yTrain, yTest = train_test_split(X, y, test_size = 0.2, random_state = 0)
xTrain['is_canceled']=yTrain
xTrain.reset_index(inplace=True,drop=True)
xTrain.head()
```

![](img/8f8a671916d96b455297952d0f37b96c_338_0.png)

*图 5.15：房屋预订数据集表*

接下来，我们将创建一些实用函数，我们将在 TensorFlow Estimator 模型构建中使用它们。

这里，它将从指定的数据框和列创建 **tf** 特征规范。

```
def create_feature_spec(df, columns=None):
feature_spec = {}
if columns == None:
columns = df.columns.values.tolist()
for f in columns:
if df[f].dtype is np.dtype(np.int64):

feature_spec[f] = tf.io.FixedLenFeature(shape=(), dtype=tf.int64)
elif df[f].dtype is np.dtype(np.float64):
feature_spec[f] = tf.io.FixedLenFeature(shape=(), dtype=tf.float32)
else:
feature_spec[f] = tf.io.FixedLenFeature(shape=(), dtype=tf.string)
return feature_spec
```

从特征规范和该规范中要使用的列列表创建简单的数值和分类特征列。模型可能通过一些特征工程表现更好，例如用于分类特征的分桶数值列和哈希桶/嵌入列。

```
def create_feature_columns(columns, feature_spec):
ret = []
for col in columns:
if feature_spec[col].dtype is tf.int64 or feature_spec[col].dtype is tf.float32:
ret.append(tf.feature_column.numeric_column(col))
else:
ret.append(tf.feature_column.indicator_column(
tf.feature_column.categorical_column_with_vocabulary_list(col,
list(xTrain[col].unique()))) 
return ret
```

下列是用于向模型提供输入的输入函数

```
def tfexamples_input_fn(examples, feature_spec, label,
mode=tf.estimator.ModeKeys.EVAL,
num_epochs=None, batch_size=64):
def ex_generator():
for i in range(len(examples)):
yield examples[i].SerializeToString()
dataset = tf.data.Dataset.from_generator(
ex_generator, tf.dtypes.string, tf.TensorShape([]))
if mode == tf.estimator.ModeKeys.TRAIN:
dataset = dataset.shuffle(buffer_size=2 * batch_size + 1)
dataset = dataset.batch(batch_size)
dataset = dataset.map(lambda tf_example:
parse_tf_example(tf_example, label, feature_spec))
dataset = dataset.repeat(num_epochs)
return dataset
```

接下来，我们将解析 Tf.Example 原型以获取输入函数的特征。

```
def parse_tf_example(example_proto, label, feature_spec):
parsed_features = tf.io.parse_example(serialized=example_proto,
features=feature_spec)
target = parsed_features.pop(label)
```

```
return parsed_features, target
```

在这里，它会将一个 dataframe 转换为 tf.Example protos 的列表。

```
def df_to_examples(df, columns=None):
examples = []
if columns == None:
columns = df.columns.values.tolist()
for index, row in df.iterrows():
example = tf.train.Example()
for col in columns:

if df[col].dtype is np.dtype(np.int64):
example.features.feature[col].int64_list.value.append(int(row[col]))
elif df[col].dtype is np.dtype(np.float64):
example.features.feature[col].float_list.value.append(row[col])
elif row[col] == row[col]:
example.features.feature[col].bytes_list.value.append(row[col].encode('utf-8'))
examples.append(example)
return examples
```

接下来，此函数会根据提供的测试将 dataframe 列转换为 0 和 1 的列。它用于强制标签列在用于二元分类的 TF 估计器中为数值型。

```
def make_label_column_numeric(df, label_column, test):
df[label_column] = np.where(test(df[label_column]), 1, 0)
```

以下是我们在训练之前将执行的步骤：

指定输入列和目标预测器，并设置数据集中希望模型预测的列：

```
label_column = 'is_canceled'
input_features = ['lead_time', 'arrival_date_week_number', 'arrival_date_day_of_month',
'stays_in_weekend_nights', 'stays_in_week_nights', 'adults',
'children','babies', 'is_repeated_guest',
'previous_cancellations','previous_bookings_not_canceled', 'agent',
'company', 'required_car_parking_spaces', 'total_of_special_requests',
'adr','hotel', 'arrival_date_month', 'meal',
'market_segment','distribution_channel', 'reserved_room_type',
'deposit_type', 'customer_type']
```

```
# Create a list containing all input features and the label column
features_and_labels = input_features + [label_column]
```

将数据集转换为 tf.Example protos：

```
examples = df_to_examples(xTrain)
```

创建并训练线性分类器以及分类器的特征规范：

```
num_steps = 2000
feature_spec = create_feature_spec(xTrain, features_and_labels)
```

feature_spec

```
{'adr': FixedLenFeature(shape=(), dtype=tf.float32, default_value=None),
'adults': FixedLenFeature(shape=(), dtype=tf.int64, default_value=None),
'agent': FixedLenFeature(shape=(), dtype=tf.float32, default_value=None),
'arrival_date_day_of_month': FixedLenFeature(shape=(), dtype=tf.int64, default_value=None),
'arrival_date_month': FixedLenFeature(shape=(), dtype=tf.string, default_value=None),
'arrival_date_week_number': FixedLenFeature(shape=(), dtype=tf.int64, default_value=None),
'babies': FixedLenFeature(shape=(), dtype=tf.int64, default_value=None),
'children': FixedLenFeature(shape=(), dtype=tf.float32, default_value=None),
'company': FixedLenFeature(shape=(), dtype=tf.float32, default_value=None),
'customer_type': FixedLenFeature(shape=(), dtype=tf.string, default_value=None),
'deposit_type': FixedLenFeature(shape=(), dtype=tf.string, default_value=None),
'distribution_channel': FixedLenFeature(shape=(), dtype=tf.string, default_value=None),
'hotel': FixedLenFeature(shape=(), dtype=tf.string, default_value=None),
'is_canceled': FixedLenFeature(shape=(), dtype=tf.int64, default_value=None),
'is_repeated_guest': FixedLenFeature(shape=(), dtype=tf.int64, default_value=None),
'lead_time': FixedLenFeature(shape=(), dtype=tf.int64, default_value=None),
'market_segment': FixedLenFeature(shape=(), dtype=tf.string, default_value=None),
'meal': FixedLenFeature(shape=(), dtype=tf.string, default_value=None),
'previous_bookings_not_canceled': FixedLenFeature(shape=(), dtype=tf.int64, default_value=None),
'previous_cancellations': FixedLenFeature(shape=(), dtype=tf.int64, default_value=None),
'required_car_parking_spaces': FixedLenFeature(shape=(), dtype=tf.int64, default_value=None),
'reserved_room_type': FixedLenFeature(shape=(), dtype=tf.string, default_value=None),
'stays_in_week_nights': FixedLenFeature(shape=(), dtype=tf.int64, default_value=None),
'stays_in_weekend_nights': FixedLenFeature(shape=(), dtype=tf.int64, default_value=None),
'total_of_special_requests': FixedLenFeature(shape=(), dtype=tf.int64, default_value=None)}
```

图 5.16：特征列张量和数据类型

```
train_inpf = functools.partial(tfexamples_input_fn, examples,
feature_spec, label_column)
```

## 5.7.1 TensorFlow Estimator 模型

在这里，我们将使用两个估计器构建模型，即线性分类器模型和 DNN 分类器模型。欲进一步阅读，请查看以下链接：

https://www.tensorflow.org/api_docs/python/tf/estimator

现在，我们首先使用线性模型分类器估计器训练模型。

```
classifier = tf.estimator.LinearClassifier(
feature_columns=create_feature_columns(input_features,
feature_spec))
classifier.train(train_inpf, steps=num_steps)
```

![](img/8f8a671916d96b455297952d0f37b96c_344_0.png)

图 5.17：线性分类器的估计器输出结果

接下来，我们将按如下方式训练第二个模型 DNN 分类器：

```
#title Create and train the DNN classifier {display-mode: "form"}
num_steps_2 = 2000
classifier1 = tf.estimator.DNNClassifier(
feature_columns=create_feature_columns(input_features,
feature_spec),
hidden_units=[128, 64, 32])
classifier1.train(train_inpf, steps=num_steps_2)
```

![](img/8f8a671916d96b455297952d0f37b96c_345_0.png)

图 5.18：DNN 分类器的估计器输出结果

在前面的示例中，我们训练了 TensorFlow Estimator 模型线性分类器和 DNN 分类器；接下来，我们将查看一些很棒的模型评估产品来分析我们的结果。

## 5.8 使用 TensorBoard 和 What-IF 工具对 TensorFlow 模型进行高级可视化

在本节中，我们将使用 what-if 和 TensorBoard 工具进行 TensorFlow 模型评估。

### 5.8.1 TensorBoard

现在，我们将在 TensorBoard 中可视化 DNN 分类器的模型结果和日志。

```
%load_ext tensorboard
%tensorboard --logdir=/tmp/
```

![](img/8f8a671916d96b455297952d0f37b96c_347_0.png)

图 5.19：DNN 估计器模型评估缩放器结果

在这里，此缩放器标签页将告诉我们模型评估结果，如准确率、偏差、全局步长、损失等。

![](img/8f8a671916d96b455297952d0f37b96c_348_0.png)

图 5.20：DNN 估计器模型评估图表

前面的屏幕截图向我们展示了模型图表以及张量中矩阵乘法的计算图形可视化。

![](img/8f8a671916d96b455297952d0f37b96c_348_1.png)

图 5.21：DNN 估计器模型层权重

在此前述模型中，层激活函数和权重在分布标签页的密集图中投影。

![](img/8f8a671916d96b455297952d0f37b96c_349_0.png)

图 5.22：DNN 估计器模型直方图

在这里，激活在各层模型上计算直方图的 epoch 频率显示在直方图标签页中。

### 5.8.2 What-If 工具

现在，我们将在部署之前准备测试数据集，以评估模型表现。

```
xTest['is_canceled']=yTest
xTest.reset_index(inplace=True,drop=True)
```

接下来，我们将导入我们的库，并借助 util 函数转换或预处理测试数据集，并设置动态可视化的像素和高度。

```
# title Invoke What-If Tool for test data and the trained models
{display-mode: "form"}
num_datapoints = 2000
tool_height_in_px = 1000
```

```
from witwidget.notebook.visualization import WitConfigBuilder
from witwidget.notebook.visualization import WitWidget
```

```
# Load up the test dataset
test_examples = df_to_examples(xTest[:2000])
```

接下来，使用测试示例和训练好的分类器设置 what-if 可视化的工具。

```
config_builder =
WitConfigBuilder(test_examples).set_estimator_and_feature_spec(
classifier, feature_spec).set_compare_estimator_and_feature_spec(
classifier1, feature_spec).set_label_vocab(['Check-Out','Canceled'])
a = WitWidget(config_builder, height=tool_height_in_px)
```

![](img/8f8a671916d96b455297952d0f37b96c_351_0.png)

图 5.23：预测数据集的动态数据点编辑器

现在，前面的屏幕截图显示了动态数据点编辑器及其所有信息，我们可以随意操作以检查数据分析。



![](img/8f8a671916d96b455297952d0f37b96c_352_0.png)

## 图 5.24：所有特征的性能和公平性

接下来，从性能和公平性标签页中，我们可以查看模型评估并比较两个分类器模型之间的研究及其 PR 曲线和 ROC 与混淆矩阵。

![](img/8f8a671916d96b455297952d0f37b96c_352_1.png)

## 图 5.25：两个特征的多切片 ROC/PR 曲线

我们可以对数据点进行切片并创建一些桶，以查看相互依赖特征的评估。在前面的屏幕截图中，我们使用了多切片策略，对两个特征进行了分析，并在混淆矩阵和公平性研究上进行了定义。

![](img/8f8a671916d96b455297952d0f37b96c_353_0.png)

## 图 5.26：分类和数值特征的统计信息

最后，在前面的屏幕截图中，我们可以看到数值和分类值的特征分布及其统计性质和行为。

## 5.9 结论

在本章中，我们学习了使用 Tensorboard 和 what-if 等各种工具对我们的 TensorFlow 模型评估进行端到端高级可视化。

我们还学习了如何构建高级 Boosting 算法 LightGBM 并使用模型端点，利用高级可视化技术对模型进行特征分析，以解释决策图，如特征图、汇总图、期望 Shap 图和误分类图等。此外，我们还构建了 TensorFlow 估计器模型，如 DNN 分类器，并可视化了我们的 Dense 层，并使用 Tensorboard 评估了直方图和日志。我们还学习了如何使用 what-if 工具在测试数据部署之前对两个 TensorFlow 模型进行动态比较研究，其中包括数据点编辑器、性能与公平性（ROC 曲线、混淆矩阵等），最后是特征分布分析标签页。

## 5.10 参考文献

https://shap.readthedocs.io/en/latest/example_notebooks/plots/decision_plot.html

https://christophm.github.io/interpretable-ml-book/preface-by-the-author.html

https://www.tensorflow.org/tutorials/estimator/premade

https://pair-code.github.io/what-if-tool/

https://www.tensorflow.org/tensorboard/get_started

https://lightgbm.readthedocs.io/en/latest/Features.html

# 构建 Weights & Biases 流水线开发

在本章中，我们将构建一个端到端的 LightGBM 模型框架，并在 Weights & Biases（Wandb）工具中监控模型性能。在 Weights & Biases 中，我们将看到每个迭代的实时模型 RMSE 图和并行坐标超参数性能图。接下来，我们将使用 KF Serving 在 Google Cloud Platform 中的 Kubernetes 集群中部署模型。然后，我们将提供模型端点，该端点将用于预测并在 Grafana 仪表板中进行监控，例如模型请求速率随时间变化以及 CPU 和 GPU 消耗。

## 结构

在本章中，我们将涵盖以下主题：

- 问题陈述
- 在 GCP 和 Wandb 中设置项目需求
- Weight & Biases 用法的介绍
- 为股票数据建模和训练 LightGBM 模型
- 使用 KF Serving 在 Kubernetes 集群中提供模型
- 使用 Grafana 仪表板监控性能

## 目标

学习本章后，我们将能够理解以下内容：

如何设置 Docker 和 Kubernetes。

如何在 Weights & Biases 工具中构建单个流水线组件，如训练和带超参数的模型评估。

如何使用 KF Serving 提供模型并预测模型请求并使用 Grafana 仪表板进行监控。

如何使用 Kubernetes 和许多其他 Google Cloud Platform 来利用 DevOps 知识发挥机器学习的强大功能。

## 6.1 问题陈述

数据已在全球股票数据中清理、规范化并加密。前 21 列（feature1 - feature21）是特征，target 是你试图预测的二分类。

在提供的数据中，每个 id 对应一个股票及其一组混淆特征。目标代表未来表现。行按时代分组，表示不同的时间点。你的目标是训练一个机器学习模型，根据新特征预测目标，并判断该股票是好是坏。让我们看一下数据集：

![](img/8f8a671916d96b455297952d0f37b96c_359_0.png)

图 6.1：股票特征数据

data data data data data data data data data data data data data
data data data data data data data data data data data data data data
data data data data data data data
data

## 6.2 在 GCP 和 Wandb 中设置项目需求

你必须拥有一个活跃的 GCP 账户，在练习本章时，运行 Kubernetes 集群可能会产生费用。我所有的代码都在 MacOS 上运行。

我认为具备基本的 Kubernetes 和 Docker 知识是必须的。

### 6.2.1 GCP 中的 Kubeflow 集群和 Docker 设置

我们已经在 Google Cloud Platform 中的 Kubernetes 集群中部署了 Kubeflow，并在之前的章节中在本地安装了 Docker。

### 6.2.2 Kaggle API 设置用于下载数据

在本节中，我们将了解如何获取 Kaggle API，并使用它直接从 Kaggle 网站下载数据。因此，用户必须拥有 Kaggle 账户；如果没有，请点击以下链接创建账户：

https://www.kaggle.com/

![](img/8f8a671916d96b455297952d0f37b96c_362_0.png)

图 6.2：Kaggle 网站

安装 Kaggle API：

你可以运行 pip install Kaggle 来安装 API。如果你在使用 Linux 或 Mac 时遇到安装问题，可能需要运行 pip install --user Kaggle。

https://github.com/Kaggle/kaggle-api

设置 API 密钥：

现在，前往你的 Kaggle 账户标签 https://www.kaggle.com//account 并点击 API。名为 kaggle.json 的文件将被下载。

接下来，将文件移动到 Mac 或 Linux 中的 ~/.kaggle/ 文件夹，或 Windows 中的 C:\Users\.kaggle\。

或者，你可以使用 kaggle.json 中的值填充 KAGGLE_USERNAME 和 KAGGLE_KEY 环境变量以使 API 进行身份验证。在这里，我们将使用 Google Colab 来训练模型；现在我们将 Kaggle.json 上传到那里。

![](img/8f8a671916d96b455297952d0f37b96c_363_0.png)

图 6.3：Kaggle 账户 API

在前面的屏幕截图中，你可以看到登录后可以点击 **Create New API Token**，它将下载一个文件，如以下屏幕截图所示：

![](img/8f8a671916d96b455297952d0f37b96c_364_0.png)

图 6.4：Kaggle Json API 密钥

保留此 json 文件，我们稍后会用到。

### 6.2.3 Weights & Biases API 密钥

Weights & Biases 将帮助你跟踪机器学习项目。你可以使用此工具记录运行的超参数和输出指标，然后可视化和比较结果，并快速与同事分享研究成果。以下是 Weights & Biases 的网站：

![](img/8f8a671916d96b455297952d0f37b96c_365_0.png)

图 6.5：Weights & Biases 网站

它在本地部署和云端设置中提供以下框架和集成：

## 模块化工具

- 实验跟踪
  仪表板
- 数据集版本控制
  Artifacts
- 模型优化
  Sweeps
- 协作 + 可重复性
  报告
- 生产监控
  即将推出

## 框架无关

- Jupyter
- PyTorch
- TensorFlow
- Keras
- Scikit
- fast.ai
- LightGBM
- XGBoost

## 环境无关

- 本地 + 私有云
- AWS
- Azure
- Google Cloud
- Kubernetes

## 图 6.6：框架和云支持

接下来，让我们看看如何创建 API；因此用户必须拥有账户或可以通过点击以下链接创建账户：https://docs.wandb.com/

接下来，前往用户设置并创建 API，然后将其复制并粘贴到笔记中的某个位置。




![](img/8f8a671916d96b455297952d0f37b96c_367_0.png)

## 图 6.7：Wandb 用户设置 API

前面的截图显示了 API Key，我们稍后将使用它来进行机器学习训练日志和评估图的集成。

## 6.3 如何使用 Weights & Biases 的介绍

所以，What-if 提供了一些功能，如下所示：

Dashboard：它有助于跟踪实验并可视化我们的训练结果。

它保存并分享可复现的研究成果。

它通过超参数调优来优化模型。

数据集和模型版本控制、管道跟踪。

现在，在使用 Python 3 的环境中安装我们的库，运行以下命令 pip install 然后运行命令 wandb

```
wandb: You can find your API key in your browser here: https://app.wandb.ai/authorize
wandb: Paste an API key from your profile and hit enter:
```

图 6.8：来自 CLI 的 Wandb 登录

修改你的训练。我们可以在脚本中添加几行代码来记录超参数和评估指标。

初始化。接下来，在脚本开头、导入之后立即初始化 Wandb。

```
# Inside my model training code
import wandb
wandb.init(project="my-project")
```

前面的命令如果在 Home 中不存在，将自动为你创建一个项目。它将捕获前面训练脚本的每次运行，并同步到该项目，命名为

### 声明超参数：

在这里，使用 wandb.config 对象保存超参数非常容易。

```
wandb.config.learningrate = 0.2
```

```
wandb.config.hidden_layer_size = 64
```

### 记录指标：

Wandb 提供了在模型训练时记录我们的训练损失或准确率等指标的功能（在许多情况下，我们提供框架特定的默认值）。它使用以下方式记录更复杂的输出或结果，如直方图、图表或图像与

```
def train_logs():
for epoch in range(20):
loss = 0
wandb.log({'epoch': epoch, 'loss': loss})
```

### 保存文件：

保存到 **wandb.run.dir** 目录中的任何内容都将被上传到 Weights & Biases，并在训练完成后与我们的运行一起保存，这对于保存我们训练好的模型的字面 Weights & Biases 非常方便。默认情况下，这将保存到为你的运行相关文件创建的新子文件夹中，位于 **wandb.run.dir**（默认为 **./wandb**）。

```
wandb.save("mymodel.h5")
```

我们可以传递到 Keras 或 Tensorflow 模型 API 的完整路径。

```
model.save(os.path.join(wandb.run.dir, "mymodel.h5"))
```

太棒了！接下来，正常运行你的脚本，它将在后台进程中同步日志。这将是你的终端输出、指标、日志和文件，并将与云同步，如果我们从 git 仓库运行，还会连同我们的 git 状态记录一起同步。

![](img/8f8a671916d96b455297952d0f37b96c_370_0.png)

### 图 6.9：训练日志的示例捕获

在前面的截图中，你可以看到一个训练和验证准确率的示例图。

## 6.4 为股票数据建模和训练 LightGBM 模型

股票数据集有 21 个与时间相关的特征。我们有 96320 行数据结构，将用于你的模型评估。你的目标是预测测试数据和实时数据。在这里，数据集中的特征是正则化的；没有分类特征。

特征和目标变量谈论的是加密的股票市场数据，目标变量被转换为对冲基金的正趋势与负趋势。无需领域金融知识。

### 6.4.1 获取最新版本的 Weights & Biases 依赖项和 Kaggle 设置

在这里，我们将在 Colab 中运行整个平台。

![](img/8f8a671916d96b455297952d0f37b96c_373_0.png)

图 6.10：Colab Logo

现在，在 Colab 中运行以下命令：

```
from tqdm import tqdm
for i in tqdm(range(2)):
!pip install -q -r requirements.txt --upgrade
```

![](img/8f8a671916d96b455297952d0f37b96c_373_1.png)

图 6.11：库安装输出

以下内容用于运行包含库的 requirements.txt：

![](img/8f8a671916d96b455297952d0f37b96c_374_0.png)

### 图 6.12：Python 库名称

接下来，为 Notebook 导入以下库：

```
import wandb
import logging
import kaggle
import os
import numpy as np

import random as rn
import pandas as pd
import seaborn as sns
import lightgbm as lgb
import matplotlib.pyplot as plt
from scipy.stats import spearmanr
from sklearn.metrics import mean_absolute_error,
mean_squared_error
from wandb.lightgbm import wandb_callback
from sklearn.model_selection import train_test_split
import warnings
warnings.filterwarnings("ignore");
import plotly.offline as py
py.init_notebook_mode(connected=True)
import plotly.graph_objs as go
import plotly.tools as tls
import plotly.figure_factory as ff
```

```
# Set seed for reproducibility
seed = 1234
rn.seed(seed)
np.random.seed(seed)
os.environ['PYTHONHASHSEED'] = str(seed)
# Suppress Pandas warnings
pd.set_option('chained_assignment', None)
```

现在，我们已经导入了所需的库；接下来，让我们看看如何设置我们之前创建的 Wandb API，以便我们可以将运行保存到 Wandb 项目中。

### 6.4.2 Weights & Biases 依赖项和 Kaggle API 设置

复制密钥并将其粘贴到 Notebook 中，将对象存储为字符串 WANDB_KEY 并使用 API 运行 Wandb 登录。

### Weights and Biases

```
# Obfuscated WANDB API Key
WANDB_KEY = "aboab83e47545b9007e5f77eeb681ae53oc0376c"
!wandb login aboab83e47545b9007e5f77eeb681ae53oc0376c
```

```
wandb: Appending key for api.wandb.ai to your netrc file: /root/.netrc
Successfully logged in to Weights & Biases!
```

图 6.13：Wandb 配置消息

以下内容是 Wandb 的成功消息，并且它配置了我们的连接。

### Kaggle API

现在，在 Colab 中上传 Kaggle.json 文件，默认情况下它将被保存到 Colab 中的 contents 文件夹中。以下是 Colab 中文件夹的截图。

![](img/8f8a671916d96b455297952d0f37b96c_377_0.png)

图 6.14：Colab 中的文件夹结构

将此文件移动到环境中根文件夹内部。这是为了身份验证所需，Chmod 将提供所需的权限，以便该密钥可在 Notebook 中的任何地方使用。

```
!mkdir ~/.kaggle
!touch ~/.kaggle/kaggle.json
import json
api=json.load(open("/content/kaggle.json"))
with open('/root/.kaggle/kaggle.json', 'w') as file:
json.dump(api, file)
```

```
!chmod 600 ~/.kaggle/kaggle.json
```

在前面的命令中，我们在 **root./kaggle** 内部创建了一个空的 json 文件 **Kaggle.json**，并从 **/content/kaggle.json** 复制了内容，并使用 **chmod** 授予了所需的访问权限并更改了文件系统对象的访问权限。

接下来，我们将从 Kaggle 下载数据。以下是我们将使用的数据的截图：

![](img/8f8a671916d96b455297952d0f37b96c_378_0.png)

图 6.15：Kaggle 数据集 URL

点击右侧，复制 API 命令并将其粘贴到单元格中复制 **numerai/encrypted-stock-market-data-from-numerai**

```
kaggle datasets download -d numerai/encrypted-stock-market-data-from-numerai
```

### 图 6.16：数据的 API

以下内容是 Kaggle API 的格式；运行以下命令将该文件解压为 **numerai_training.csv** 文件：

```
Signature: filename: [owner]/[dataset-name]
dataset_download_file(dataset, file_name, path=None, force=False, quiet=True)
```

```
logging.info(kaggle.api.authenticate())
```

```
kaggle.api.dataset_download_files('numerai/encrypted-stock-market-data-from-numerai', path='/content', unzip=True)
logging.info("Downloaded Data")
```

### 6.4.3 加载和提取数据

现在，我们将使用 Pandas 库加载数据。

```
data=pd.read_csv("/content/numerai_training_data.csv")
import numpy as np
data['target']=np.random.uniform(0,1,size=data.shape[0])
data.head(5)
```

![](img/8f8a671916d96b455297952d0f37b96c_380_0.png)

图 6.17：特征表

接下来，我们将准备训练数据；让我们按 60/20/20 的比例分别将数据拆分为训练、验证和测试。

```
train, test = train_test_split(data, test_size=0.2)
train, val = train_test_split(train, test_size=0.2)
print(len(train), 'train examples')
print(len(val), 'validation examples')
print(len(test), 'test examples')
```

61644 训练示例
15412 验证示例
19264 测试示例



## 图 6.18：训练-测试拆分大小

现在我们已经拆分了数据，让我们进行一些探索性数据分析。

## 6.4.4 探索性数据分析

让我们查看加密数据相对于目标列的相关性矩阵。正相关一词表示两个特征会朝同一方向移动，而负相关表示当一个变量的值增加时，另一个变量的值会减少。因此，接近/为零的相关性表示变量之间没有关系。

```
def correlation_plot(data):
correlation = data.corr()
matrix_cols = correlation.columns.tolist()
corr_array = np.array(correlation)
trace = go.Heatmap(z = corr_array,x = matrix_cols,y = matrix_cols,xgap = 2,ygap = 2, colorscale='Plasma',colorbar = dict())
layout = go.Layout(dict(title = 'Correlation Matrix for variables', autosize = False, height = 900,width = 1000,margin = dict(r = 0, l = 210, t = 25,b = 210), yaxis = dict(tickfont = dict(size = 9)),xaxis = dict(tickfont = dict(size = 9))))
fig = go.Figure(data = [trace],layout = layout)
py.iplot(fig)
```

现在，让我们在下一页查看图表。

![](img/8f8a671916d96b455297952d0f37b96c_383_0.png)

## 图 6.19：相关性图

因此，这里特征与目标变量的相关性非常低。即使相关性最高的特征，与目标变量的相关性也只有约 1.5%。

接下来，我们注意到特征的重要性可能会随时间变化。因此，通过选择最少的特征数量，我们可能会面临高方差的风险。因此，特征暴露可以量化为所有预测与每个特征的相关性的标准差。我们可以通过使用降维技术，如主成分分析，将几乎所有特征整合到模型中来降低风险。

接下来，让我们查看训练集、测试集和验证集数据的分布。

```
feats = [f for f in train.columns if "feature" in f]
plt.figure(figsize=(16, 5))
sns.distplot(pd.DataFrame(train[feats].std()), bins=50)
sns.distplot(pd.DataFrame(val[feats].std()), bins=50)
sns.distplot(pd.DataFrame(test[feats].std()), bins=50)
plt.legend(["Train", "Val", "Test"], fontsize=20)
plt.title("Standard deviations over all features in the data", fontsize=20);
```

![](img/8f8a671916d96b455297952d0f37b96c_384_0.png)

图 6.20：分布图

现在，我们可以看到训练集、验证集和测试集中特征的标准差在其正态分布中广泛分布，范围在 0.275 到 0.295 之间。

```
feature_list = list(train.columns)
```

```
feature_list.remove("target")
```

现在，将特征列名称绘制到列表 **feature_list** 中以进行进一步操作。

## 6.4.4 效用指标函数

我们将使用以下三个指标评估我们的训练 LightGBM 回归器：

**Spearman** 统计上，该方法将量化由单调函数关联的变量的排序程度，表示为递增或递减的关系行为。该方法进行假设检验，并说明样本不相关（未能拒绝 Ho）。该函数接下来将两个实值数据作为参数，并返回介于 -1 和 1 之间的相关系数，以及用于解释系数显著性的 p 值。

对于大小为 n 的样本，n 个原始分数 X_i、Y_i 转换为秩 rg_Xi、rg_Yi，且 r_s 计算为

r_s = ρ_{rgX, rgY} = cov(rg_X, rg_Y) / (σ_{rgX} σ_{rgY}),

其中
ρ 表示通常的 Pearson 相关系数，但应用于秩变量，
cov(rg_X, rg_Y) 是秩变量的协方差，
σ_{rgX} 和 σ_{rgY} 是秩变量的标准差。

只有当所有 n 个秩都是不同的整数时，才可以使用流行公式计算

r_s = 1 - 6 Σ d_i² / [n(n² - 1)],

其中
d_i = rg(X_i) - rg(Y_i) 是每个观测值的两个秩之间的差异，
n 是观测值的数量。

图 6.21：Spearman 相关性（来源：维基）

**Mean Absolute** 实际值与预测值之间绝对差异的平均值。它说明预测有多错误。它还衡量误差幅度，并给出方向概念，因此值为 0 表示无误差或预测完美。

**Root Mean Square** R^2（或 R 平方）指标谈论的是我们的预测相对于原始值的拟合优度指标。在统计术语中，它也被称为决定系数。其值介于 0 和 1 之间，分别表示无拟合和完美拟合。

```
def evaluate(df: pd.DataFrame) -> tuple:
def _score(sub_df: pd.DataFrame) -> np.float32:
"""Calculates Spearman correlation"""
return spearmanr(sub_df["target"], sub_df["prediction"])[0]

mae = mean_absolute_error(df["target"], df["prediction"]).round(4)
RMSE=mean_squared_error(df["target"], df["prediction"])** 0.5
spearman=spearmanr(df["target"], df["prediction"])[0]
# Display metrics
print(f"Spearman Correlation: {spearman}")
print(f"RMSE Score: {RMSE}")
print(f"Mean Absolute Error (MAE): {mae}")
return spearman,RMSE, mae
```

因此，我们将在 LightGBM 模型中使用前述函数。

## 6.4.5 使用 Weights & Biases 训练模型（使用 LightGBM 框架）

在本节中，让我们看看如何使用 Weights & Biases 构建我们的 LightGBM 框架。

LightGBM 如何工作？

LightGBM 使用基于直方图的算法，将连续特征（属性）值划分为离散的 bin。这加快了训练速度并减少了内存使用。

![](img/8f8a671916d96b455297952d0f37b96c_388_0.png)

图 6.22：LightGBM 架构

LightGBM 以最佳优先的方式以叶式方式生长树。接下来，它取具有最大增量损失的叶进行生长。叶式算法通过固定叶节点，往往比层式算法实现更低的损失。

叶式算法在数据量较少时可能导致过拟合，因此 LightGBM 包含一个用于限制树深度的参数，即 max_depth。然而，即使指定了 **max_depth**，叶式树仍会继续生长。

基于直方图的算法的优点包括以下内容：

- 计算每次分割增益的成本降低。
- 使用直方图减法以进一步加速。
- 减少内存使用。
- 降低并行学习的通信成本。

如需进一步阅读，请访问以下链接：

[https://lightgbm.readthedocs.io/en/latest/Features.html](https://lightgbm.readthedocs.io/en/latest/Features.html)

## **Sweeps：**

我们将训练 LightGBM 模型以获得第一个不错的模型，然后我们将使用 Weights & Biases 进行超参数扫描。在此示例中，我们将对 LightGBM 框架算法的一些最重要的

超参数进行网格搜索。首先，我们将定义扫描的配置。

常见用例如下：

它有效地发现超参数组合的有希望区域的样本空间；接下来，它建立了对模型的直觉。

它有助于找到我们模型超参数的最优性能集合。

**K-fold cross** 以下是使用 W&B Sweeps 进行 k 折交叉验证的简要示例。

## 方法：

**Add** 在我们的 Python 脚本中编写几行代码以记录超参数和评估输出指标。

**Write** 接下来，对于扫描，我们还将定义变量和范围。我们将选择一种搜索策略——它支持随机、网格和贝叶斯搜索，以及提前停止。

**Initialize** 现在，启动扫描服务器。它托管中央控制器，并将在执行扫描的多个代理之间进行协调。

WANDB BACKEND MACHINES

![](img/8f8a671916d96b455297952d0f37b96c_391_0.png)

YOUR MACHINES

*图 6.23：Wandb 扫描架构*

**Launch** 要在扫描中使用训练模型，请在每台机器上运行命令，然后代理会询问后端中央扫描服务器下一步尝试哪些超参数，并将执行运行。

**Visualize** 点击生成的链接，打开我们的实时仪表板，在一个中央位置查看所有结果。有关配置，请查看以下链接：
https://docs.wandb.com/sweeps/configuration

在我们的笔记本中运行以下配置：

```
# Configuration for hyperparameter sweep
sweep_config = {
'method': 'grid',
```



```
'metric': {
'name': 'mse',
'goal': 'minimize'},
'parameters': {

"num_leaves": {'values': [30, 40, 50]},
"max_depth": {'values': [4, 5, 6, 7]},
"learning_rate": {'values': [0.1, 0.05, 0.01]},
"bagging_freq": {'values': [7]},
"bagging_fraction": {'values': [0.6, 0.7, 0.8]},
"feature_fraction": {'values': [0.85, 0.75, 0.65]}},)
sweep_id = wandb.sweep(sweep_config,
project="simpletransformers")
```

创建 sweep，ID 为：d3b061m9
Sweep 网址：https://app.wandb.ai/aniruddha/simpletransformers/sweeps/d3b061m9

### 图 6.24：Sweep 配置链接

让我们分解前面的 sweep metric 方法的配置，并同时讨论 LightGBM 参数。

## 指标：

在这里，指定要优化的指标。此指标将在我们的训练脚本中明确记录到 Wandb。在此示例中，我们希望最小化 LightGBM 模型的验证损失：

- name: 要优化的指标名称 goal: minimize 或 maximize（默认为 minimize）

## 方法：

接下来，我们将从 grid、random search 和 bayes 中指定搜索策略：

它会遍历所有可能的组合以找到参数值。

它选择随机的值集合。

它使用高斯过程来建模我们的函数，然后选择能够优化模型改进概率的参数。它也被称为 *贝叶斯*

## 参数：

接下来，请查看以下链接以了解参数的描述：

https://lightgbm.readthedocs.io/en/latest/Parameters.html

前面的 **sweep_id** 中的最后一行代码将存储项目名称和配置设置，我们将在 LightGBM 模型训练期间提供这些设置。

## 为 LightGBM 准备数据：

现在，我们将为 LightGBM 模型创建数据准备。

```
dtrain = lgb.Dataset(train[feature_list], label=train["target"])
dvalid = lgb.Dataset(val[feature_list], label=val["target"])
watchlist = [dtrain, dvalid]
```

## 训练模型集成 Wandb：

接下来，让我们看看如何构建 LightGBM 回归器并构建一个 **train()** 方法作为实用函数：

```
def _train():
# Configure and train model
wandb.init(name="LightGBM_sweep")
lgbm_config = {"num_leaves": wandb.config.num_leaves,
"max_depth": wandb.config.max_depth, "learning_rate":
wandb.config.learning_rate, "bagging_freq":
wandb.config.bagging_freq, "bagging_fraction":
wandb.config.bagging_fraction, "feature_fraction":
wandb.config.feature_fraction, "metric": 'mse', "random_state": seed}

lgbm_model = lgb.train(lgbm_config, train_set=dtrain,
num_boost_round=750, valid_sets=watchlist, callbacks=
[wandb_callback()], verbose_eval=100, early_stopping_rounds=50)

# Create predictions for evaluation
val_preds = lgbm_model.predict(val[feature_list],
num_iteration=lgbm_model.best_iteration)
print(val_preds)
```

```
print(type(val_preds))
val.loc[:, "prediction"] = val_preds
# W&B log metrics
spearman,RMSE, mae = evaluate(val)
wandb.log({"Spearman": spearman, "RMSE": RMSE, "Mean Absolute Error": mae})
#lgb_path = '/content/'
save_to = "/content/lgb_classifier.txt"
lgbm_model.save_model(save_to)
```

现在，让我们分解前面的 **train()** 方法：

我们将在 Wandb 中以名称 **LightGBM_sweep** 启动模型的训练，所有运行都将保存在该名称下。

![](img/8f8a671916d96b455297952d0f37b96c_396_0.png)

### 图 6.25：Wandb 中的运行名称

所以，在这里我们将在脚本中设置 wandb.config 以保存我们的训练配置、超参数，并输入诸如数据集名称或模型类型之类的设置，以及 LightGBM 模型实验的任何其他独立变量或参数，例如学习率、最大深度等。这对于分析我们的实验并在未来重现我们的工作非常有用。我们可以在 Web 界面中按配置值进行分组，比较不同的运行并查看它们如何影响输出。让我们设置对象

格式：**wandb.config.[PARAMETER]**

接下来，我们将使用 **early_stopping_rounds** 训练我们的 LightGBM 模型，如果某个验证数据的某个指标最终没有改善，则会停止训练。然后，我们创建的训练和验证数据都将通过，我们之前创建了这些数据。

然后，我们将使用测试数据集评估我们的模型，并使用原始数据集评估预测以计算 MAE、RMSE 和相关性。

输出指标或因变量 RMSE、MAE 和 Spearman 应改用 **wandb.log** 保存。我们已将 LightGBM 模型与最佳迭代一起保存在 **/content/lgb_classifier.txt** 文件夹中，我们将在 Google Cloud Platform 中的 Kubeflow Kubernetes 集群中使用它进行 KF Serving 生产。

现在，使用我们之前完成的 **sweep_id** 配置运行以下命令，并传递前面的 **train()** 函数。

```
# Run hyperparameter sweep (grid search)

wandb.agent(sweep_id, function=_train)
```

```
INFO:wandb.wandb_agent:Running runs: ['u5n9ep55']
INFO:wandb.wandb_agent:Cleaning up finished run: u5n9ep55
INFO:wandb.wandb_agent:Agent received command: run
INFO:wandb.wandb_agent:Agent starting run with config:
    bagging_fraction: 0.6
    bagging_freq: 7
    feature_fraction: 0.85
    learning_rate: 0.1
    max_depth: 4
    num_leaves: 40
wandb: Agent Starting Run: b9ml3fz3 with config:
    bagging_fraction: 0.6
    bagging_freq: 7
    feature_fraction: 0.85
    learning_rate: 0.1
    max_depth: 4
    num_leaves: 40
wandb: Agent Started Run: b9ml3fz3
Logging results to Weights & Biases (Documentation).
Project page: https://app.wandb.ai/aniruddha/simpletransformers
Sweep page: https://app.wandb.ai/aniruddha/simpletransformers/sweeps/03edx2p8
Run page: https://app.wandb.ai/aniruddha/simpletransformers/runs/b9ml3fz3
Training until validation scores don't improve for 50 rounds.
Early stopping, best iteration is:
[3]        training's 12: 0.0835953            valid_l's 12: 0.0827124
[0.5026042 0.5016406 0.5016406 ... 0.5016406 0.5026042 0.5016406]
<class 'numpy.ndarray'>
Spearman Correlation: 0.004787618906806593
RMSE Score: 0.2875976805060863
Mean Absolute Error (MAE): 0.2481
wandb: Agent Finished Run: b9ml3fz3
```

### 图 6.26：每次运行的输出

前面的示例是 Notebook 中的一次运行输出日志；它讨论了模型的性能，每个运行都保存在蓝色超链接 URL 中，我们可以在其中导航并查看性能和模型超参数的平行坐标。例如，查看以下链接：

http://app.wandb.ai/aniruddha/simpletransformers/sweeps/03edx2p8

## Wandb 仪表板

在前面的训练日志中，我们得到了 3 个 URL。让我们导航到 PROJECT URL 并检查一个示例运行的性能。

![](img/8f8a671916d96b455297952d0f37b96c_399_0.png)

### 图 6.27：一次运行的仪表板

现在，在前面的截图中，我们可以看到总共有 311 次运行，如左上角所述，接下来，仪表板由 RMSE、Spearman、训练损失和验证损失以及每个运行的平均绝对误差组成，显示在单个轴上，并通过相互比较告诉哪个运行最好；让我们以 Spearman 和训练/验证损失为例。

![](img/8f8a671916d96b455297952d0f37b96c_399_1.png)

### 图 6.28：多次运行比较

现在，在前面的截图中，在第一个条形图中，我们可以看到 3 个相关性最高的运行的紫色、绿色和浅粉色条形。同样，我们可以分析每个运行在训练和测试中的多个分数，这些分数是在步数或 epoch 数中训练的，我们可以为模型部署选择最佳运行。接下来，单击 **RUN URL；** 在单个运行中，您将获得以下报告图表：

![](img/8f8a671916d96b455297952d0f37b96c_400_0.png)

### 图 6.29：多次运行比较

所以，前面的截图谈到了单个运行，正如我们所见，验证损失相对于训练损失较低。

接下来，我们可以看到相对于各种参数的 GPU 或 CPU 消耗：

![](img/8f8a671916d96b455297952d0f37b96c_401_0.png)

### 图 6.30：模型机器性能

前面的屏幕截图讨论了在训练模型时每次运行的内存利用率、推送日志所消耗的网络流量（以字节为单位），以及各种运行的 CPU 消耗情况。

让我们导航到 SWEEP URL 以可视化 sweep 结果：

![](img/8f8a671916d96b455297952d0f37b96c_401_1.png)

### 图 6.31：超参数重要性图

所以，超参数重要性图表面显示了哪些超参数是最好的预测因子，并且与数据框中那些理想值高度相关。

这里，相关性表示超参数与所选指标之间的线性相关性，在本例中为 Validation Loss。因此，这里较高的相关性表明超参数的值较高，指标的值也较高，反之亦然。接下来，相关性也是一个很棒的指标可以查看，但它无法捕捉输入之间的二阶交互，并且在比较具有不同范围指标的输入时可能会变得混乱。

让我们向下查看一点以检查超参数的平行坐标来了解指标的性能。它将超参数值映射到模型指标，这对于确定导致最佳模型性能的超参数组合非常有用。

![](img/8f8a671916d96b455297952d0f37b96c_402_0.png)

### 图 6.32：超参数平行坐标

在前面的屏幕截图中，每个轴代表不同的参数范围值，在本例中，我们有 7 个垂直轴，例如等等。接下来，可视化不同超参数与我模型的最终均方误差之间的关系，我们将对其进行最小化。

**Axes:** 它表示来自 **wandb.config** 的不同超参数，我之前提到过，以及所有指标从

**Lines:** 这里，一条线代表一次运行。将鼠标悬停在线上即可查看包含每次运行所有详细信息的工具提示。

## 6.5 使用 KF Serving 提供模型服务

在本节中，我们将构建我们的服务模型。在下面的屏幕截图中，我们可以看到模型服务下面屏幕截图的三个主要组件。

因此，这里我们将保存的训练模型从本地保留到 Docker 文件的根目录，或者我们可以从 Cloud Storage 存储桶中调用它。

![](img/8f8a671916d96b455297952d0f37b96c_404_0.png)

### 图 6.33：文件夹结构

在之前的章节中，我们已经介绍了 KF Serving Architecture；因此您可以参考

让我们看看我们将如何构建服务组件 **lightgbm_wandb.py** 文件：

```python
import os
import sys
import json
import numpy as np
import kfserving
import lightgbm as lgb
from typing import List, Dict
class KFServingSampleModel(kfserving.KFModel):
def __init__(self, name: str):
super().__init__(name)
self.name = name
self.ready = False
self.model_output_base_path = "lgb_classifier.txt"
def load(self):
model = lgb.Booster(model_file=self.model_output_base_path)
self.model = model
self.ready = True
def predict(self, request: Dict) -> Dict:
inputs = np.array(request["instances"])
reshaped_to_2d = np.reshape(inputs, (-1, len(inputs)))
results = self.model.predict(reshaped_to_2d)
result = (results > 0.5)*1
```

```python
if result==1:
result="Positive Equity"
else:

result="Negative Equity"
print("result : {0}".format(result))
return {"predictions": result}
```

```python
if __name__ == "__main__":
model = KFServingSampleModel("kfserving-wandb-lightgbm-model")
model.load()
kfserving.KFServer(workers=1).start([model])
```

那么，让我们按如下方式分解 transformer 预测器代码：

我们将保存的模型文件 lgb_classifier.txt 保留在 Docker 根目录中，并且在这里我们将该文件声明为对象的环境变量

接下来，在 Load 函数中，我们从 LightGBM 库加载了模型。

然后，在 predict 方法中，传入的数据以 json 格式出现，我们需要将其提取为键值对并进行必要的预测并作为字典返回。

因此，在“main”函数中，KFServingSampleModel 类采用了该部署的名称；请注意这一点并将其应用到 yaml 文件中；如下所示

![](img/8f8a671916d96b455297952d0f37b96c_407_0.png)

### 图 6.34：kf Serving Python 代码左侧 & 部署 yaml 右侧

假设在构建镜像后，名称为 **gcr.io/ /：**

现在，让我们在这里了解 KF serving transformer 代码。从上面屏幕截图中 Python 文件的左侧，**KFServingSampleModel** 类将始终有一个 **Load()** 方法，我们可以在其中从 docker 路径或从 Google Bucket 加载训练好的模型；然后我们可以加载到那里进行预测和 **predict()** 方法，该方法将用于接收传入的 json 请求作为输入。然后，我们可以在模型预测文本或图像数据的情况下进行必要的操作。

让我们看看我们将如何构建服务组件 Dockerfile：

```
FROM python:3.7-slim-stretch
ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update && \
apt-get -y install gcc mono-mcs g++ git curl bash && \

rm -rf /var/lib/apt/lists/*
ADD requirements.txt /app/requirements.txt
RUN pip install -r /app/requirements.txt
ADD lightgbm_wandb.py /app/lightgbm_wandb.py
ADD lgb_classifier.txt /app/lgb_classifier.txt
# COPY . /app
WORKDIR /app
CMD ["python","lightgbm_wandb.py"]
```

因此，从上面的 dockerfile 我们有以下步骤：

我们的 Dockerfile 的第一行以 FROM 开始。这里是我们导入操作系统或编程语言的地方。

接下来的两行涉及设置环境并在服务器上执行。ADD 行使本地文件在 Docker 容器中可用。RUN 命令可以跟随您希望执行的任何 bash 代码。

我们使用 RUN 安装依赖项。然后 ENV 设置我们的环境变量。

WORKDIR 行将工作目录设置为 app。然后，ADD 行使剩余的本地文件在 Docker 容器中可用。接下来，CMD 将在 Docker 文件每次执行时运行命令。

现在，让我们使用命令行部署它；首先让我们填写 yaml 文件：

```
apiVersion: serving.kubeflow.org/v1alpha2
kind: InferenceService
metadata:

labels:
controller-tools.k8s.io: "1.0"
name: kfserving-wandb-lightgbm-model
namespace: kubeflow
spec:
default:
predictor:
custom:
container:
image: gcr.io//<_TAG>
imagePullPolicy: Always
name: user-container
```

这里，在前面的 yaml 文件中，我们给出了与在 lightgbm_wandb.py 文件中提供的相同名称；它将是 然后我们提供了部署的命名空间“kubeflow”。接下来，我们为我们创建的 Transformer 模型提供了 Docker 镜像名称。

接下来，从 Visual Studio 中保存文件的位置在 bash 中运行以下命令：

使用以下命令连接到 GCP 集群：

```
gcloud container clusters get-credentials <$ClusterName> --zone <$ZONE> --project <$PROJECTID>
```

通过在集群中部署它来创建推理服务：

```
kubectl apply -f wandb.yaml
```

检查推理服务。间隔一段时间后尝试检查是否已创建：

```
kubectl get inferenceservice -n kubeflow
```

![](img/8f8a671916d96b455297952d0f37b96c_410_0.png)

### 图 6.35：KF Serving 推理

示例预测：

从 serving 文件夹在 Bash 中运行以下命令：

```
MODEL_NAME=kfserving-wandb-lightgbm-model
HOST=$(kubectl get inferenceservice -n kubeflow $MODEL_NAME -o jsonpath='{.status.url}' | cut -d "/" -f 3)
INPUT_PATH=@./input.json
```

```
CLUSTER_IP=$(kubectl -n istio-system get service kfserving-ingressgateway -o jsonpath='{.status.loadBalancer.ingress[0].ip}')
curl -v -H "Host: ${HOST}"
http://${CLUSTER_IP}/v1/models/${MODEL_NAME}:predict -d
$INPUT_PATH
```

```
* Trying ...
* TCP_NODELAY set
* Connected to ... (...) port 80 (#0)
> POST /v1/models/kfserving-wandb-lightgbm-model:predict HTTP/1.1
> Host: kfserving-wandb-lightgbm-model.default.example.com
> User-Agent: curl/7.64.1
> Accept: */*
> Cookie: authservice_session=MTUS0TkxsQT0NXx0d3bTKzM1Z6UTB0a3RCV2taYVdWTTFSa3BTVH pKU1dGUKlUMEi
> Content-Length: 490
> Content-Type: application/x-www-form-urlencoded
>
* upload completely sent off: 490 out of 490 bytes
< HTTP/1.1 200 OK
< content-length: 34
< content-type: application/json; charset=UTF-8
< date: Sat, 12 Sep 2020 14:09:49 GMT
< server: istio-envoy
< x-envoy-upstream-service-time: 22
<
* Connection #0 to host ... left intact
{"predictions": "Negative Equity"}* Closing connection 0
```

### 图 6.36：KF Serving 预测输出

从 Colab 笔记本运行以下命令：

现在，我们将创建一些示例数据以从前面的下方 URL 预测结果。要创建示例数据，代码如下：

```
import requests
MODEL_NAME="kfserving-wandb-lightgbm-model"
cluster_ip = YOUR CLUSTER IP HERE
```



```
headers={"Host": "
{0}.kubeflow.example.com".format(MODEL_NAME)}
response =
requests.post("http://{0}/v1/models/{1}:predict".format(cluster_ip,
MODEL_NAME), data = data1,headers = headers)
response.json()
```

```
{'predictions': 'Negative Equity'}
```

图 6.37: KF serving Prediction O/P Python

## 6.6 使用 Grafana 仪表板监控性能

Grafana 包含对 Prometheus 的内置支持。本主题解释了 Prometheus 数据源特定的选项、变量、查询以及其他选项。启动 Grafana 仪表板。如第 4 章《Building TFX Pipeline》第 4.7 节所示，我们已经安装了 Grafana。

接下来，从本地终端运行并使用浏览器上的 `localhost:8080` 打开 `grafana` 仪表板。探索 Grafana 仪表板的各个组件。

```bash
kubectl port-forward --namespace knative-monitoring $(kubectl get pod --namespace knative-monitoring --selector="app=grafana" --output jsonpath='{.items[0].metadata.name}') 8080:3000
```

以下仪表板讨论了 Knative Serving 可视化的 HTTP 请求，我们将按每秒请求进行服务。

![](img/8f8a671916d96b455297952d0f37b96c_414_0.png)

图 6.38: Grafana Dashboard HTTP Request

因此，以下是控制平面的仪表板，显示 CPU 消耗和内存使用效率。

![](img/8f8a671916d96b455297952d0f37b96c_414_1.png)

图 6.39: Grafana CPU/Memory Dashboard

## 6.7 结论

在本章中，我们学习了如何在 Weights & Biases 中构建端到端的 LightGBM 框架，该框架在每次运行中捕获我们的模型并输出指标。我们为 LightGBM 算法参数构建了 sweep 和 Wandb 配置，同时为超参数搜索构建了平行坐标图。

我们还在 Kubernetes 平台上部署了 Kubeflow，并在 Kubernetes 集群中使用 KF serving 部署了模型，并在 Grafana 仪表板中监控了我们的预测结果。

在本章中，我们还获得了如何利用 Google Cloud Platform 的强大功能，并将 DevOps 知识与机器学习结合以成为 MLops 的知识。

## 6.8 参考文献

https://plotly.com/python/builtin-colorscales/

https://technowhisp.com/kaggle-api-python-documentation/

https://www.kaggle.com/numerai/encrypted-stock-market-data-from-numerai

https://github.com/Kaggle/kaggle-api

https://lightgbm.readthedocs.io/en/latest/Parameters.html

https://www.wandb.com/

https://github.com/kubeflow/kfserving

# 使用 AWS SageMaker 的应用机器学习

在本章中，我们将开展 Housing Price Sales Dataset 项目，在 Amazon SageMaker 云环境中完整运行、评估和部署模型，并使用 S3 进行数据存储。我们还将使用内置容器算法 XG-Boost 进行模型构建，以便能够从头到尾理解 SageMaker 模型构建框架的架构。

## 结构

本章将涵盖以下主题：

- 问题陈述
- AWS SageMaker 设置入门
- JupyterLab Notebook 实例、SDK 和 S3 存储桶入门
- 启动笔记本并将数据加载到 S3 入门
- 加载、分析和转换训练数据
- Amazon SageMaker 训练模型
- Amazon SageMaker 模型部署

## 目标

学习本章后，您将能够理解以下内容：

如何将数据加载并推送到用于数据存储的 Amazon S3 中。

离群值分析、特征转换以及分类和数值列的插补。

如何在 Amazon SageMaker 中创建笔记本、构建模型并部署它。在这里，我们将使用 XG-Boost 内置算法。

我们在 Amazon CloudWatch 中部署的模型的指标和性能。

## 7.1 问题

这里，一位购房者描述了他们的梦想房屋，他们可能不会从地下室天花板的高度或靠近东西向铁路开始。

因此，我们有 79 个变量描述了爱荷华州埃姆斯市住宅房屋几乎各方面的情况；这挑战了预测每栋房屋的最终价格。

房屋。 房屋。 房屋。 房屋。 房屋。 房屋。 房屋。 房屋。 房屋。
房屋。 房屋。 房屋。 房屋。 房屋。 房屋。 房屋。 房屋。 房屋。
房屋。 房屋。 房屋。 房屋。 房屋。 房屋。 房屋。 房屋。 房屋。
房屋。 房屋。 房屋。
---
房屋。

## 7.2 AWS SageMaker 设置入门

因此，我们将从 AWS 账户设置开始我们的旅程。要完成设置，请完成以下步骤：

创建 AWS 账户电子邮件地址和密码以作为 AWS 账户根用户登录，并导航到 IAM 控制台，链接如下：

![](img/8f8a671916d96b455297952d0f37b96c_421_0.png)

图 7.1: AWS Sign-in Console

接下来，为您将创建的 IAM 管理员用户启用计费数据的访问权限：

在您账户名称的导航栏中选择 **My Account**。

在 **IAM User and Role Access to Billing** 旁边选择 Edit Next

接下来，选择复选框以 **Activate IAM Access** 并选择

![](img/8f8a671916d96b455297952d0f37b96c_422_0.png)

*图 7.2: AWS My account. Dashboard*

从导航栏中选择 **Services**，然后选择 IAM 进入 IAM 仪表板。

![](img/8f8a671916d96b455297952d0f37b96c_423_0.png)

图 7.3: AWS IAM Dashboard

您可以在 IAM 中的访问管理控制台中自定义下方给出的控制台登录链接，其中有自定义选项可更改。

单击 **Users** 并添加新用户：

类型

现在，选择 AWS Management Console access 旁边的复选框；然后选择自定义密码；接下来，在文本框中输入您自己的新密码。因此，默认情况下，AWS 会强制新用户在首次登录 AWS 时创建新密码。因此，我们可以 optionally 取消选中 User 旁边的框，因为用户必须在下次登录时创建新密码，以便新用户在登录后重置其密码。

![](img/8f8a671916d96b455297952d0f37b96c_424_0.png)

图 7.4: AWS Add User Screen

选择下一步：

在设置权限页面，选择直接附加现有策略。

单击下一步：

单击创建用户。

下载 csv 文件。

![](img/8f8a671916d96b455297952d0f37b96c_425_0.png)

图 7.5: AWS User Creation Last Step Screen

接下来，打开 csv 文件并复制链接到您的浏览器，以 myrole 用户名和您的自定义密码登录。可选：您可以在 IAM 的访问管理控制台中自定义下方的控制台登录链接，其中有自定义选项可更改。

以下是我们已下载的 csv 文件的屏幕截图：

![](img/8f8a671916d96b455297952d0f37b96c_425_1.png)

图 7.6: AWS IAM Role Creation csv file credentials

接下来，以 IAM 用户身份登录并搜索

![](img/8f8a671916d96b455297952d0f37b96c_426_0.png)

图 7.7: AWS Service search dashboard

这里，我们将搜索 **AmazonSagemaker**

## 7.3 JupyterLab Notebook 实例和 SDK 及 S3 存储桶入门

### 7.3.1 创建 S3 存储桶

现在，模型的训练将产生以下内容：

转换后的模型训练数据存储在 S₃ 中。

模型工件，即 Amazon SageMaker 在模型训练期间生成的。

我们可以将所有这些内容保存在 **Amazon Simple Storage Service** 存储桶中；我们可以将训练数据期间使用的数据集和训练作业输出的模型工件存储在单个存储桶或两个单独的存储桶中。

登录后，屏幕将如下所示的屏幕截图：

![](img/8f8a671916d96b455297952d0f37b96c_429_0.png)

图 7.8: AWS S3 Create Bucket Screen

现在，您的存储桶已创建。

![](img/8f8a671916d96b455297952d0f37b96c_429_1.png)

图 7.9: AWS S3 Bucket Dashboard

### 7.3.2 创建 Amazon SageMaker 笔记本实例

导航到 Amazon SageMaker 控制台 > 笔记本实例 > 创建笔记本实例。步骤如下：

在创建笔记本实例页面，提供以下信息（如果未提及某个字段，请保留默认值）：

在笔记本实例名称部分，为您的笔记本实例输入名称。

然后，对于实例类型，选择 这是最便宜的实例类型，也是笔记本实例支持的推荐类型。

![](img/8f8a671916d96b455297952d0f37b96c_430_0.png)



## 图 7.10：AWS SageMaker 创建笔记本屏幕

对于 IAM 角色，选择 创建新角色，然后选择 创建角色。

选择 创建笔记本实例。

![](img/8f8a671916d96b455297952d0f37b96c_431_0.png)

## 图 7.11：创建 IAM 角色屏幕

![](img/8f8a671916d96b455297952d0f37b96c_432_0.png)

## 图 7.12：创建笔记本屏幕

请等待几分钟，Amazon SageMaker 将启动一个 ML 计算实例——在本例中为笔记本实例——并为其附加一个 ML 存储卷。笔记本实例具有预配置的 Jupyter notebook 服务器 /JupyterLab 以及一套 Anaconda 库。

启动 JupyterLab。以下屏幕截图显示了屏幕的显示方式：

![](img/8f8a671916d96b455297952d0f37b96c_433_0.png)

图 7.13：AWS 笔记本实例仪表板

接下来，我们需要添加一些 IAM 策略，因此请点击以下屏幕截图中所示的笔记本实例名称：

![](img/8f8a671916d96b455297952d0f37b96c_433_1.png)

图 7.14：我们创建的 AWS 笔记本仪表板

然后点击带有 ARN 的 IAM 角色；它将重定向到新页面。现在，如果以下策略不存在，则点击附加策略，并搜索这些策略名称然后点击复选框。

![](img/8f8a671916d96b455297952d0f37b96c_434_0.png)

## 图 7.15：AWS 笔记本 IAM 角色策略仪表板

确保所有红色框中的策略都已附加到我们的 IAM 中，否则请搜索并附加这些策略。

## 7.4 通过启动笔记本并将数据加载到 S3 开始使用

要启动 Jupyter Notebook 服务器，请完成以下步骤：

现在，我们将创建一个笔记本。

当我们在 JupyterLab 经典视图中打开笔记本时，在 **Files** 选项卡上，选择并且 这里，预安装的环境包括默认的 Anaconda 安装和 Python 3。

在 Jupyter notebook 中，选择 **File** 和 **Save** 并为笔记本命名。

接下来，我们将查看笔记本选项，点击后会出现这些选项。

![](img/8f8a671916d96b455297952d0f37b96c_436_0.png)

图 7.16：JupyterLab 默认屏幕

通过创建文件夹将数据加载到 S3 Bucket，然后在另一个文件夹中上传 train.csv 文件。

Amazon S3> /mysagemakerbucket

![](img/8f8a671916d96b455297952d0f37b96c_436_1.png)

图 7.17：Amazon S3 Bucket 文件路径

因此，前面的示例是 S3 存储桶位置和文件。

## 7.5 加载、分析和转换训练数据

在这里我们将完成以下部分步骤：

从 S3 和 Python 库加载数据。

原始数据的特征工程，如插补和异常值检测。

然后，对目标特征进行对数转换并检查相关性和正态分布图。

使用标签编码和哑变量转换分类特征。

### 7.5.1 从 S3 和库加载数据

现在我们将加载构建和部署模型所需的所有 Python 库。

```
import numpy as np
import pandas as pd
import boto3
import re
import sagemaker
from sagemaker import get_execution_role
import matplotlib.pyplot as plt
import seaborn as sns
from scipy import stats
from sklearn.preprocessing import LabelEncoder, StandardScaler
from sklearn.base import TransformerMixin
from warnings import filterwarnings
filterwarnings('ignore')
from sklearn.base import BaseEstimator, TransformerMixin,
RegressorMixin, clone
from sklearn.neighbors import LocalOutlierFactor
```

加载在笔记本实例期间创建的 IAM 角色。

```
role = get_execution_role()
role
```

```
2]: 'arn:aws:iam: Account ID role/service-role/AmazonSageMaker-ExecutionRole-20200223T004685'
```

## 图 7.18：AWS-ARN-IAM 路径

现在，从 S3 存储桶加载原始数据，并提供其位于 houseprice 文件夹中的地址。

```
bucket_name = 'mysagemakerbucket' # Your Bucket name
```

```
raw_folder=r'houseprice/rawdata/train.csv'
s3_raw_file_location =r's3://{0}/{1}'.format(bucket_name,raw_folder)
```

现在，将文件作为 pandas 数据框加载；它将访问 S3 位置。

```
raw_data=pd.read_csv(s3_raw_file_location)
raw_data.head()
```

![](img/8f8a671916d96b455297952d0f37b96c_440_0.png)

## 图 7.19：原始数据框

### 7.5.2 特征工程

现在，我们将在模型训练过程之前完成特征工程步骤。

### 7.5.2.1 查找分类与数值列

在这里，我们将通过对象类型找出数值和分类列，包括并排除所有特征。

```
num_cols = raw_data.select_dtypes(exclude='object').columns
print('{} Numeric columns \n{}'.format(len(num_cols), num_cols))
categ_cols = raw_data.select_dtypes(include='object').columns
print('\n{} Categorical columns \n{}'.format(len(categ_cols), categ_cols))
```

```
38 Numeric columns
Index(['Id', 'MSSubClass', 'LotFrontage', 'LotArea', 'OverallQual',
       'OverallCond', 'YearBuilt', 'YearRemodAdd', 'MasVnrArea', 'BsmtFinSF1',
       'BsmtFinSF2', 'BsmtUnfSF', 'TotalBsmtSF', '1stFlrSF', '2ndFlrSF',
       'LowQualFinSF', 'GrLivArea', 'BsmtFullBath', 'BsmtHalfBath', 'FullBath',
       'HalfBath', 'BedroomAbvGr', 'KitchenAbvGr', 'TotRmsAbvGrd',
       'Fireplaces', 'GarageYrBlt', 'GarageCars', 'GarageArea', 'WoodDeckSF',
       'OpenPorchSF', 'EnclosedPorch', '3SsnPorch', 'ScreenPorch', 'PoolArea',
       'MiscVal', 'MoSold', 'YrSold', 'SalePrice'],
      dtype='object')

43 Categorical columns
Index(['MSZoning', 'Street', 'Alley', 'LotShape', 'LandContour', 'Utilities',
       'LotConfig', 'LandSlope', 'Neighborhood', 'Condition1', 'Condition2',
       'BldgType', 'HouseStyle', 'RoofStyle', 'RoofMatl', 'Exterior1st',
       'Exterior2nd', 'MasVnrType', 'ExterQual', 'ExterCond', 'Foundation',
       'BsmtQual', 'BsmtCond', 'BsmtExposure', 'BsmtFinType1', 'BsmtFinType2',
       'Heating', 'HeatingQC', 'CentralAir', 'Electrical', 'KitchenQual',
       'Functional', 'FireplaceQu', 'GarageType', 'GarageFinish', 'GarageQual',
       'GarageCond', 'PavedDrive', 'PoolQC', 'Fence', 'MiscFeature',
       'SaleType', 'SaleCondition'],
      dtype='object')
```

图 7.20：输出数值与分类特征

现在，我们总共有 81 列中的 38 个数值列和 43 个分类列。

### 7.5.2.2 检查缺失值总和

现在，我们将从表中检查缺失值，然后为不同的插补技术做准备。

```
df_na = (raw_data.isnull().sum()) / len(raw_data) * 100
df_na =
df_na.drop(df_na[df_na==0].index).sort_values(ascending=False)
```

我们将在条形图中绘制缺失值的计数或总和。

```
with plt.rc_context(rc={'font.size':14}):
fig, ax = plt.subplots(figsize=(16, 6))
sns.barplot(df_na.index, df_na, palette="pastel", ax=ax)
ax.set(xlabel='Features', ylabel='Missing values percentages')
ax.tick_params(axis='x', rotation=55)
```

![](img/8f8a671916d96b455297952d0f37b96c_444_0.png)

## 图 7.21：特征的缺失值条形图

在前面的屏幕截图中，我们可以看到从缺失值最多的顺序开始，PoolQC、Alley 等；现在我们需要为模型构建填充这些列。

### 7.5.2.3 因变量的对数转换

现在，我们将转换模型因变量列以减少偏度并在均值上保持正态分布。

```
def skew_distribution(data, col='SalePrice'):
fig, ax1 = plt.subplots()
sns.distplot(data[col], ax=ax1, fit=stats.norm)
(mu, sigma) = stats.norm.fit(data[col])
ax1.set(title='Normal distribution ($\mu=$ {:.2f} and $\sigma=$ {:.2f})'.format(mu, sigma))
fig, ax2 = plt.subplots()
stats.probplot(data[col], plot=plt)
print('The {} skewness is {:.2f}'.format(col, stats.skew(data[col])))
```

价格的分布及正态分布拟合：

```
skew_distribution(raw_data, 'SalePrice')
```

因此，分布图将如下所示：

SalePrice 偏度为 1.88

![](img/8f8a671916d96b455297952d0f37b96c_447_0.png)

图 7.22：正态分布图

![](img/8f8a671916d96b455297952d0f37b96c_447_1.png)

图 7.23：概率图

因此，我们需要将其转换为更正态的分布，因为线性模型将表现更好。因此，在对数变换后，正态分布和 P-P 图如下：

```
raw_data['SalePrice']=np.log1p(raw_data['SalePrice'])
```

```
skew_distribution(raw_data, 'SalePrice')
```

SalePrice 偏度为 0.12

![](img/8f8a671916d96b455297952d0f37b96c_448_0.png)

图 7.24：正态分布图

![](img/8f8a671916d96b455297952d0f37b96c_448_1.png)

图 7.25：概率图

SalePrice 现在更符合高斯分布，且第二个代表概率图的图显示分布几乎遵循正态分布。

## 7.5.2.4 相关性与散点图

在这里，我们将绘制相关性以检查变量之间的关系，并绘制散点图以检查相对于因变量房屋价格的异常值分析。

```
corr = raw_data.corr()
top_correlation = corr['SalePrice'].sort_values(ascending=False)[:25]
threshold = 0.51
top_corr = corr.index[np.abs(corr["SalePrice"]) > threshold]
```

```
plt.figure(figsize=(10,8))
sns.heatmap(raw_data[top_corr].corr(),annot=True,cmap="RdBu_r")
```

因此，相关性图将如下所示：

<matplotlib.axes._subplots.AxesSubplot at 0x7f29c57b0c88>

![](img/8f8a671916d96b455297952d0f37b96c_451_0.png)

## 图 7.26：顶部相关性图

现在，在前面的截图中，我们可以看到我们使用 0.51 的阈值绘制了相关性最高的特征，并确定了一些相对于因变量列非常重要的列。

我们将找到顶部数值相关特征的平均相关性。

```
for col in top_correlation.index[:15]:
```

```
```python
print('{} - unique values: {} - mean: {:.2f}'.format(col, raw_data[col].unique()[:5], np.mean(raw_data[col])))
```
```

```
```
SalePrice - unique values: [12.24769912 12.10901644 12.31717117 11.84940484 12.4292202 ] - mean: 12.02
OverallQual - unique values: [7 6 8 5 9] - mean: 6.10
GrLivArea - unique values: [1710 1262 1786 1717 2198] - mean: 1515.46
GarageCars - unique values: [2 3 1 0 4] - mean: 1.77
GarageArea - unique values: [548 460 608 642 836] - mean: 472.98
TotalBsmtSF - unique values: [ 856 1262  920  756 1145] - mean: 1057.43
1stFlrSF - unique values: [ 856 1262  920  961 1145] - mean: 1162.63
FullBath - unique values: [2 1 3 0] - mean: 1.57
YearBuilt - unique values: [2003 1976 2001 1915 2000] - mean: 1971.27
YearRemodAdd - unique values: [2003 1976 2002 1970 2000] - mean: 1984.87
GarageYrBlt - unique values: [2003. 1976. 2001. 1998. 2000.] - mean: 1978.51
TotRmsAbvGrd - unique values: [8 6 7 9 5] - mean: 6.52
Fireplaces - unique values: [0 1 2 3] - mean: 0.61
MasVnrArea - unique values: [196. 0. 162. 350. 186.] - mean: 103.69
BsmtFinSF1 - unique values: [706 978 486 216 655] - mean: 443.64
```
```

## 图 7.27：相对于目标特征的相关均值

因此，以下列是通过散点图确定的用于进一步分析的重要列。

```
```python
cols = 'SalePrice GrLivArea GarageArea TotalBsmtSF YearBuilt 1stFlrSF MasVnrArea TotRmsAbvGrd'.split()
with plt.rc_context(rc={'font.size':14}):
fig, ax = plt.subplots(figsize=(16,13), tight_layout=True)
pd.plotting.scatter_matrix(raw_data[cols], ax=ax, diagonal='kde', alpha=0.8)
```
```

![](img/8f8a671916d96b455297952d0f37b96c_453_0.png)

## 图 7.28：散点图

这些散点图将为我们提供一些关于少数异常值的见解，即那些类似于不连贯/巨大的值，将会影响模型。因此，我们只会删除其中一些，因为它们确实很重要。我们将在 (GrLivArea - GarageArea - TotalBsmtSF - 1stFlrSF - MasVnrArea - TotRmsAbvGrd) 与 SalePrice 的散点图中删除主要异常值。

## 7.5.2.5 异常值检测

现在，我们将使用 Scikit-Learn 的 LocalOutlierFactor 方法从数据集中删除异常值。

```
def detect_outliers_plots(x, y,name,top=5, plot=True):
lof = LocalOutlierFactor(n_neighbors=40, contamination=0.1)
x_ =np.array(x).reshape(-1,1)
preds = lof.fit_predict(x_)
lof_scr = lof.negative_outlier_factor_
out_idx = pd.Series(lof_scr).sort_values()[:top].index
if plot:
f, ax = plt.subplots(figsize=(9, 6))
plt.scatter(x=x, y=y, c=np.exp(lof_scr), cmap='RdBu')
ax.set(ylabel='SalePrice', xlabel=name)
return out_idx
```

提取 8 列到单独的表中并列出并删除空值。

```
outlier_ana_data=raw_data[['SalePrice','GarageArea','TotalBsmtSF',
'YearBuilt','1stFlrSF','MasVnrArea', 'TotRmsAbvGrd', 'GrLivArea']]
outlier_ana_data.dropna(inplace=True)
cols_out = ['GarageArea','TotalBsmtSF',
'YearBuilt','1stFlrSF','MasVnrArea', 'TotRmsAbvGrd', 'GrLivArea']
for i in cols_out:
```

```
outs = detect_outliers_plots(outlier_ana_data[i],
 outlier_ana_data['SalePrice'],i,top=5) #got 1298,523
print(outs)
```

```
Int64Index([540, 515, 1364, 318, 1158], dtype='int64')
Int64Index([1290, 331, 495, 522, 439], dtype='int64')
Int64Index([1429, 802, 800, 282, 762], dtype='int64')
Int64Index([1290, 495, 522, 1018, 1365], dtype='int64')
Int64Index([1017, 1353, 976, 378, 384], dtype='int64')
Int64Index([531, 633, 203, 1094, 612], dtype='int64')
Int64Index([1290, 522, 1176, 688, 531], dtype='int64')
```

## 图 7.29：索引异常值输出

因此，它将返回这些 7 列中所有异常值的索引。

![](img/8f8a671916d96b455297952d0f37b96c_455_0.png)

## 图 7.30：正态分布图

![](img/8f8a671916d96b455297952d0f37b96c_456_0.png)

## 图 7.31：概率图

我们创建了一个函数并在此调用以检测异常值；你可以在 GitHub 上找到代码，因此如果在以下部分看到此方法，请不要感到困惑。

我们从数据集中提取了最常见的异常值并找到了异常值。

```
outliers = [30, 88, 462, 523, 632, 1298, 1324]
from collections import Counter
all_outliers=[]
```

```
numeric_features = raw_data.dtypes[raw_data.dtypes != 'object'].index
for feature in numeric_features:
try:
outs = detect_outliers(raw_data[feature], raw_data['SalePrice'],top=5,
plot=False)
except:
continue
all_outliers.extend(outs)
```

```
print(Counter(all_outliers).most_common())
for i in outliers:
if i in all_outliers:
print(i)
```

![](img/8f8a671916d96b455297952d0f37b96c_457_0.png)

## *图 7.32：异常值索引计数字典*

```
Outliers_table=raw_data.loc[outliers]
Outliers_table=Outliers_table[cols_out]
Outliers_table
```

|  | GarageArea | TotalBsmtSF | YearBuilt | 1stFlrSF | MasVnrArea | TotRmsAbvGrd | GrLivArea |
|---|---|---|---|---|---|---|---|
| 30 | 250 | 649 | 1920 | 649 | 0.0 | 6 | 1317 |
| 88 | 0 | 1013 | 1915 | 1013 | 0.0 | 6 | 1526 |
| 462 | 360 | 864 | 1965 | 864 | 0.0 | 5 | 864 |
| 523 | 884 | 3138 | 2007 | 3138 | 762.0 | 11 | 4676 |
| 632 | 544 | 1386 | 1977 | 1411 | 209.0 | 6 | 1411 |
| 1298 | 1418 | 6110 | 2008 | 4692 | 796.0 | 12 | 5642 |
| 1324 | 895 | 1795 | 2006 | 1795 | 428.0 | 7 | 1795 |

## 图 7.33：异常值表

现在我们将通过索引列表删除异常值。

```
raw_data = raw_data.drop(raw_data.index[outliers])
raw_data.reset_index(drop=True, inplace=True)
raw_data.shape()
```

[23]: (1453, 81)

## 图 7.34：新数据形状

因此，我们已删除了 7 行最常见的异常值。

## 7.5.3 特征转换

在这里，将列分组为数值型、类别型、标签编码器列，并更改列的数据类型。

```
N= ['GarageYrBlt', 'MasVnrArea','GarageArea',
'GarageCars','BsmtFinSF1', 'BsmtFinSF2', 'BsmtUnfSF','TotalBsmtSF',
'BsmtFullBath', 'BsmtHalfBath','MasVnrArea']
M= ['MSZoning','Electrical','KitchenQual','Exterior1st',
'Exterior2nd','SaleType']
S=['OverallCond','YrSold','MoSold','MSSubClass','GarageCars',
'Fireplaces', 'HalfBath','OverallQual']
L= ['PoolQC','MSSubClass','MasVnrType','Alley','MiscFeature',
'Fence','FireplaceQu','BsmtQual', 'BsmtCond',
'BsmtExposure','BsmtFinType1', 'BsmtFinType2','GarageType',
'GarageFinish', 'GarageQual', 'GarageCond']
cols= ['BsmtExposure', 'BsmtFinType1', 'BsmtFinType2', 'BsmtQual',
'BsmtCond', 'GarageQual', 'GarageCond', 'GarageFinish',
'GarageType',
'FireplaceQu', 'ExterQual', 'ExterCond',
'HeatingQC', 'PoolQC', 'KitchenQual',
'Functional', 'Fence', 'LandSlope',
'LotShape', 'PavedDrive', 'Street', 'Alley', 'CentralAir',
'MSSubClass', 'OverallCond', 'GarageCars', 'YrSold', 'MoSold',
'Fireplaces', 'HalfBath']
```

因此，以下 **transformation()** 函数用于数值列的插补：

```
def transformation(data) -> pd.DataFrame:
for i in N:
data[i] = data[i].fillna(0)
for i in M:

data[i] = data[i].fillna(data[i].mode()[0])
for i in L:
data[i] = data[i].fillna("None")
for i in S:
data[i] = data[i].astype(str)
data["LotFrontage"] = data.groupby("Neighborhood")
["LotFrontage"].transform(lambda x: x.fillna(x.median()))
data["Functional"] = data["Functional"].fillna("Typ")
data = data.drop(['Utilities'], axis=1)
return data
```

这里 **cat_transform()** 用于分类标签编码和哑变量转换：

```
def cat_transform(data) -> pd.DataFrame:
le = LabelEncoder()
for col in cols:
data[col] = le.fit_transform(data[col])
data = pd.get_dummies(data)
return data
```

这里，**add_features()** 将添加一些重要的特征，这将有助于我们的预测：

```
def add_features(data) -> pd.DataFrame():
```

```
data['TotalSF'] = data['TotalBsmtSF'] + data['1stFlrSF'] +
 data['2ndFlrSF'] + data['GrLivArea'] + data['GarageArea']
# Combine the bathrooms
data['Bathrooms'] = data['FullBath'] + data['HalfBath']* 0.5
# Combine Year built, Garage Year Built and Year Remod
# (with a coeff 0.5 since it's less correlated to Year Built than the
Garage year built).
```

```
data['YearMean'] = data['YearBuilt'] + data['YearRemodAdd'] * 0.5 +
data['GarageYrBlt']
return data
```

现在，我们已加载没有目标列的测试数据集，并在其中与训练数据一起进行了预处理。

```
# We don't need the Id column so we save it
df_train_id = raw_data['Id']
df_test_id = test_data['Id']
raw_data.drop("Id", axis=1, inplace=True)
test_data.drop("Id", axis=1, inplace=True)
```

```
# same transformation to the train / test datasets to avoid irregularities
size_train = len(raw_data.index)
size_test = len(test_data.index)
print((size_train),(size_test))
```

(1453, 81) (1459, 80)

图 7.35：原始数据/测试数据形状

现在，我们合并了原始数据和测试数据并为数据转换做好了准备。

```
df_tot = pd.concat([raw_data, test_data],
sort=False).reset_index(drop=True)
df_tot.drop(['SalePrice'], axis=1, inplace=True)
print(df_tot.shape)
df_tot.head()
```

![](img/8f8a671916d96b455297952d0f37b96c_462_0.png)

图 7.36：合并表

让我们打印表的形状。

```
print (df_tot.shape)
df_tot = transformation(df_tot)
print(df_tot.shape)
df_tot = cat_transform(df_tot)
print(df_tot.shape)
```

现在，我们将转换分类变量并对训练集和测试集中的缺失值进行插补；之后，我们将仅从合并数据中分离出训练数据，然后添加特征。以下是训练数据的处理过程：

```
x = df_tot[:size_train]
x=add_features(x)
print (x.shape)
x.head()
```

![](img/8f8a671916d96b455297952d0f37b96c_463_0.png)

图 7.37：转换后从合并数据中分离的原始训练数据

在前面的截图中，您可以看到转换后训练数据的形状变为 (1453,225)。之后，我们检查了训练数据中的空值，所有列均为零。

```
logSalesPrice=raw_data['SalePrice']
x.reset_index(drop=True, inplace=True)
x.insert(loc=0, column='SalePrice', value=logSalesPrice)
x.head()
```

```
[48]:
SalePrice MSSubClass LotFrontage LotArea Street Alley LotShape LandSlope OverallCond YearBuilt ... SaleType_WD SaleCondition_Abnormal Su
0 12.247699 10 65.0 8450 1 1 3 0 4 2003 ... 1 0
1 12.109016 5 80.0 9600 1 1 3 0 7 1976 ... 1 0
2 12.317171 10 68.0 11250 1 1 0 0 4 2001 ... 1 0
3 11.849405 11 60.0 9550 1 1 0 0 4 1915 ... 1 1
4 12.429220 10 84.0 14260 1 1 0 0 4 2000 ... 1 0
5 rows × 226 columns
```

# 图 7.38：现在最终表格，目标列在最前面

现在，我们将在第一列添加独立特征，因为我们将使用内置的 SageMaker 算法 XG-boost，它会自动将第一列作为目标列，其余作为独立特征。

## 7.6 Amazon SageMaker 训练模型

现在，就我们的考虑而言，我们转换后的原始数据到 Dataframe (x)/ train.csv 文件是我们的主表，我们将将其拆分为 Train/Validation 文件。我们将在验证数据集中进行评估，并对我们将预测目标特征销售价格的测试数据进行预测。

![](img/8f8a671916d96b455297952d0f37b96c_465_0.png)

图 7.39：Amazon SageMaker 训练与部署（来源：AWS Docs）

### 7.6.1 将数据拆分为训练/验证并推送到 S3

我们将指定您的存储桶名称，然后为路径和文件夹命名，我们将在 S3 中创建它们。

```
bucket_name = 'mysagemakerbucket' # your bucket name

training_folder = r'houseprice/training/'
validation_folder = r'houseprice/validation/'
test_folder = r'houseprice/test/'

s3_model_output_location =
r's3://{0}/houseprice/model'.format(bucket_name)
s3_training_file_location =
r's3://{0}/{1}'.format(bucket_name,training_folder)
s3_validation_file_location =
r's3://{0}/{1}'.format(bucket_name,validation_folder)
s3_test_file_location = r's3://{0}/{1}'.format(bucket_name,test_folder)
```

因此，模型输出和工件将存储在模型输出位置，模型的训练将存储在训练位置，模型的评估将从验证数据中进行，我们将从测试文件位置预测测试数据。

![](img/8f8a671916d96b455297952d0f37b96c_467_0.png)

图 7.40：Amazon S3 文件夹结构

结构将在您的 S3 存储桶中看起来像前面的截图。以下函数将用于通过转换为二进制将数据推送到 S3：

```
def write_to_s3(filename, bucket, key):
with open(filename,'rb') as f: # Read in binary mode
return
boto3.Session().resource('s3').Bucket(bucket).Object(key).upload_fileobj(f)
```

我们将随机将训练数据按 80-20 的比例拆分为训练集和验证集。

```
df=x.copy()
np.random.seed(5)
l = list(df.index)
np.random.shuffle(l)
df = df.loc[l]
```

```
rows = df.shape[0]
train = int(.20 * rows)
test = rows-train
```

保存训练/验证/测试数据集本地路径：

```
# Write Training Set
df.iloc[:train].to_csv('house_train_final.csv',index=False,header=False)
```

```
# Write Validation Set
df.iloc[train:].to_csv('house_validation_final.csv',index=False,header=False)
```

```
# Write test Set
test_csv.to_csv('house_test_final.csv')
```

在这里，我们将通过调用 write_to_s3 函数将训练/验证/测试数据集推送到 S3：

```
write_to_s3('house_train_final.csv', bucket_name, training_folder + 'train.csv')
write_to_s3('house_validation_final.csv',bucket_name, validation_folder + 'validation.csv')
write_to_s3('house_test_final.csv',bucket_name, test_folder + 'test_tran.csv')
```

因此，我们已将数据推送到 S3。

### 7.6.2 使用维护算法容器的 SageMaker API XG-Boost 进行训练

现在，我们将通过从 SageMaker SDK 调用会话来与 AWS 建立会话。

```
sess = sagemaker.Session()
```

在这里，我们将导入 Amazon SageMaker Python SDK 并获取 XGBoost 容器的默认版本。现在，SageMaker API 为我们维护算法容器映射，指定区域、算法和版本。

```
container = sagemaker.amazon.amazon_estimator.get_image_uri(
sess.boto_region_name,
"xgboost")
print('Using SageMaker XGBoost container:\n{}\n({})'.format(container, sess.boto_region_name))
```

![](img/8f8a671916d96b455297952d0f37b96c_470_0.png)

图 7.41：AWS 云中 XG-Boost 容器位置和版本

接下来，我们将配置训练作业，然后指定要使用的实例类型和数量；然后指定最终工件需要存储的 S3 位置。我们将创建 sagemaker.estimator.Estimator 类的一个实例。

## 参考：

http://sagemaker.readthedocs.io/en/latest/estimators.html

```
estimator = sagemaker.estimator.Estimator(
container,
role,
train_instance_count=1,
train_instance_type='ml.m4.xlarge',

output_path=s3_model_output_location,
sagemaker_session=sess,
base_job_name ='xgboost-Model')
```

在构造函数中，您可以指定以下参数：

AWS **身份和访问管理** 角色，Amazon SageMaker 可以假定该角色代表我们执行任务（例如：它可以读取训练结果，它可以从我们的 S3 存储桶调用模型工件，并且可以将训练结果写入 Amazon S3）。这是我们在创建 Notebook 实例期间获得的角色。

**train_instance_count** 和 因此，请考虑我们用于模型训练的 ML 计算实例的类型和数量；在这里，我们只能使用单个训练实例。

这是附加到训练实例的 **Amazon Elastic Block Store** 存储卷的大小（以 GB 为单位）。如果您使用文件模式（即默认模式），它必须足够大以存储我们的训练数据。



This is the path to the S3 bucket where the Amazon SageMaker stores our training results as a default extension file.

This is the session object that will manage the interactions with SageMaker APIs and for any other AWS service that our training job will use.

So, we will set the hyperparameter values for our XGBoost training job by calling the **sdk** method **set_hyperparameters** method of the estimator class.

```
estimator.set_hyperparameters(base_score=0.5,
colsample_bylevel=1,num_round=150,
colsample_bynode=1, colsample_bytree=0.5,
learning_rate=0.02, gamma=0.025,
max_depth=4, n_estimators=1500, min_child_weight=2,
nthread=1, reg_alpha=0., reg_lambda=1, subsample=0.5,
objective='reg:linear', random_state=28)
```

Here, we have to create the training channels which will be used for the training job. We use both the train and the validation channels.

```
# content type can be libsvm or csv for XGBoost
training_input_config = sagemaker.session.s3_input(
s3_data=s3_training_file_location,
content_type='csv',
s3_data_type='S3Prefix')
```

```
validation_input_config = sagemaker.session.s3_input(
 s3_data=s3_validation_file_location,
 content_type='csv',
 s3_data_type='S3Prefix'
 )
 data_channels = {'train': training_input_config, 'validation':
 validation_input_config}
```

Now, to start the model training, we will call the estimator's fit method. XGBoost supports "train", "validation" channels.

### Reference: Supported channels by algorithm
https://docs.aws.amazon.com/sagemaker/latest/dg/sagemaker-algo-docker-registry-paths.html

```
estimator.fit(data_channels)
```

```
2020-04-05 16:42:08 Starting – Starting the training job...
2020-04-05 16:42:09 Starting – Launching requested ML instances.....
2020-04-05 16:43:12 Starting – Preparing the instances for training...
2020-04-05 16:44:06 Downloading – Downloading input data...
2020-04-05 16:44:37 Training – Downloading the training image...
2020-04-05 16:45:09 Uploading – Uploading generated training model
2020-04-05 16:45:09 Completed – Training job completed
Arguments: train
[2020-04-05:16:44:58:INFO] Running standalone xgboost training.
[2020-04-05:16:44:58:INFO] File size need to be processed in the node: 0.74mb. Available memory size in the node: 8508.11mb
[2020-04-05:16:44:58:INFO] Determined delimiter of CSV input is ','
[16:44:58] S3DistributionType set as FullyReplicated
[16:44:58] 1235x225 matrix with 277875 entries loaded from /opt/ml/input/data/train?format=csv&label_column=&delimiter=,
[2020-04-05:16:44:58:INFO] Determined delimiter of CSV input is ','
[16:44:58] S3DistributionType set as FullyReplicated
[16:44:58] 218x225 matrix with 49050 entries loaded from /opt/ml/input/data/validation?format=csv&label_column=&delimiter=,
[16:44:58] src/tree/updater_prune.cc:74: tree pruning end, 1 roots, 18 extra nodes, 0 pruned nodes, max_depth=4
[0]#011train-rmse:5.41071#011validation-rmse:5.58529
[16:44:58] src/tree/updater_prune.cc:74: tree pruning end, 1 roots, 22 extra nodes, 0 pruned nodes, max_depth=4
[1]#011train-rmse:4.03268#011validation-rmse:4.23648
[16:44:58] src/tree/updater_prune.cc:74: tree pruning end, 1 roots, 22 extra nodes, 0 pruned nodes, max_depth=4
[2]#011train-rmse:2.98134#011validation-rmse:3.15959
[16:44:58] src/tree/updater_prune.cc:74: tree pruning end, 1 roots, 18 extra nodes, 2 pruned nodes, max_depth=4
[3]#011train-rmse:2.26828#011validation-rmse:2.4225
[16:44:58] src/tree/updater_prune.cc:74: tree pruning end, 1 roots, 22 extra nodes, 0 pruned nodes, max_depth=4
[4]#011train-rmse:1.67801#011validation-rmse:1.83374
[16:44:58] src/tree/updater_prune.cc:74: tree pruning end, 1 roots, 20 extra nodes, 0 pruned nodes, max_depth=4
[5]#011train-rmse:1.33205#011validation-rmse:1.48437
[16:44:58] src/tree/updater_prune.cc:74: tree pruning end, 1 roots, 12 extra nodes, 0 pruned nodes, max_depth=4
[6]#011train-rmse:1.10017#011validation-rmse:1.23461
[16:44:58] src/tree/updater_prune.cc:74: tree pruning end, 1 roots, 24 extra nodes, 0 pruned nodes, max_depth=4
[16:44:59] src/tree/updater_prune.cc:74: tree pruning end, 1 roots, 22 extra nodes, 6 pruned nodes, max_depth=4
[148]#011train-rmse:0.095235#011validation-rmse:0.693852
[16:44:59] src/tree/updater_prune.cc:74: tree pruning end, 1 roots, 18 extra nodes, 4 pruned nodes, max_depth=4
[149]#011train-rmse:0.094575#011validation-rmse:0.694274
Training seconds: 63
Billable seconds: 63
```

### Figure 7.42: XG-Boost Model Fit Logs of RMSE of 0.6942 which is minimum

It is a synchronous operation. The method will display the progress logs and it waits until the training completes before returning.

Go to the training Jobs and Model in Amazon SageMaker service and you can check all the details of the model hyperparameter and the output artifacts location.

![](img/8f8a671916d96b455297952d0f37b96c_474_0.png)

### Figure 7.43: XG-Boost Model Training Job Dashboard

Now, the preceding screenshot is of the dashboard of the model which we have fitted; we will get all the output location and instance type and required information in the dashboard.

## 7.7 Amazon SageMaker model deployment

Now, we will deploy from the training job which was fitted earlier and give an endpoint name and instance type.

### Ref: http://sagemaker.readthedocs.io/en/latest/estimators.html

```
predictor = estimator.deploy(initial_instance_count=1,
instance_type='ml.m4.xlarge',endpoint_name = 'xgboost-house-v1')
```

Here, we will deploy the model that we have trained in create and run a Training Job by calling the deploy method of the **sagemaker.estimator.Estimator** object from SDK. So, now it is the same object which we have used to train our model. When we call the deploy method, it will specify the number and type of the ML instances that we want to use to host the endpoint for deployment.

If an error comes, please use **instance_type='ml.t2.medium'**.

![](img/8f8a671916d96b455297952d0f37b96c_476_0.png)

### Figure 7.44: XG-Boost Model Deployment Endpoint

In the preceding screenshot, we can see the endpoint deployment name and below that, we can call the endpoint, with **RealTimePredictor** API by passing the name.

```
endpoint_name = 'xgboost-house-v1'
predictor = 
sagemaker.predictor.RealTimePredictor(endpoint=endpoint_name)
```

![](img/8f8a671916d96b455297952d0f37b96c_477_0.png)

### Figure 7.45: XG-Boost Model End-Point Cloud-Watch Metrics

Now, the preceding screenshot shows the model CPU Utilization and its performance with respect to time and we can see those in CloudWatch and Cloud logs to track all the model performance.

```
class sagemaker.predictor.RealTimePredictor(endpoint, sagemaker_session=None, serializer=None, deserializer=None, content_type=None, accept=None)
```

Bases: object

Make prediction requests to an Amazon SageMaker endpoint.

Initialize a `RealTimePredictor`.

Behavior for serialization of input data and deserialization of result data can be configured through initializer arguments. If not specified, a sequence of bytes is expected and the API sends it in the request body without modifications. In response, the API returns the sequence of bytes from the prediction result without any modifications.

- Parameters:
  - endpoint (str) – Name of the Amazon SageMaker endpoint to which requests are sent.
  - sagemaker_session (sagemaker.session.Session) – A SageMaker Session object, used for SageMaker interactions (default: None). If not specified, one is created using the default AWS configuration chain.
  - serializer (callable) – Accepts a single argument, the input data, and returns a sequence of bytes. It may provide a content_type attribute that defines the endpoint request content type. If not specified, a sequence of bytes is expected for the data.
  - deserializer (callable) – Accepts two arguments, the result data and the response content type, and returns a sequence of bytes. It may provide a content_type attribute that defines the endpoint response's "Accept" content type. If not specified, a sequence of bytes is expected for the data.
  - content_type (str) – The invocation's "ContentType", overriding any content_type from the serializer (default: None).
  - accept (str) – The invocation's "Accept", overriding any accept from the deserializer (default: None).

```
predict(data, initial_args=None, target_model=None)
```

### Figure 7.46: SageMaker API Notes AWS SageMaker SDK)

Now we will set the environment variables.

```
from sagemaker.predictor import csv_serializer, json_deserializer
predictor.content_type = 'text/csv'
predictor.serializer = csv_serializer
predictor.deserializer = None
```

We need to pass an array; so the prediction can pass a numpy array or a list of values [[19,1],[20,1]]. Here, we will load the test

数据并转换 **add_features** 函数，然后我们将进行预测。

```
t=pd.read_csv("house_test_final.csv")
t=add_features(t)
t.shape
arr_test = t[t.columns[1:]].values
```

对于大量预测，我们可以拆分输入数据并查询预测服务。**array_split** 方便指定需要的拆分数量。

```
predictions = []
for arr in np.array_split(arr_test,50):
result = predictor.predict(arr)
result = result.decode("utf-8")
result = result.split(',')
print (arr.shape)
predictions += [float(r) for r in result]
```

现在，我们将反向转换我们的日志值。我们也可以评估验证数据集。

```
pred=np.expm1(predictions)
sub=pd.DataFrame()
sub['id']=df_test_id.values
sub['SalePrice']=pred
sub.head()
```

[130]:

|   | id | SalePrice |
|---|----|-----------|
| 0 | 1461 | 10.459867 |
| 1 | 1462 | 7.723757 |
| 2 | 1463 | 51.396668 |
| 3 | 1464 | 68.385400 |
| 4 | 1465 | 133.739232 |

Figure 7.47: 预测结果

因此，前面的表格是我们从已部署的端点预测的预测输出。

以下为已部署的端点：

![](img/8f8a671916d96b455297952d0f37b96c_481_0.png)

Figure 7.48: 模型端点仪表板，删除端点

为避免产生不必要的费用，请使用如前图所示的 AWS 管理控制台删除资源，或按如下方式从 Notebook 中删除：

```
sagemaker.Session().delete_endpoint(predictor.endpoint)
```

## 7.8 结论

我们已接近本章的结尾，您可以安心地在云中运行和部署自己的模型，并使用云的强大功能。

在本章中，我们学习了异常值分析、特征转换以及分类和数值列的插补。然后，我们学习了如何在 Amazon SageMaker 中创建笔记本并构建模型和部署它。我们还学习了如何使用内置的 XG-Boost 算法。然后，我们在 Amazon CloudWatch 中检查了已部署模型的指标和性能。

## 7.9 参考文献

https://docs.aws.amazon.com/sagemaker/latest/dg/studio-jumpstart.html

https://docs.aws.amazon.com/sagemaker/index.html

https://github.com/awslabs/sagemaker-churn-prediction-text

# 使用 Streamlit 和 Heroku 进行 Web 应用开发

在本章中，我们将为计算机视觉模型构建端到端的 Web 应用程序，并使用 Streamlit 构建该 UI。我们将学习有关图像的许多 Open CV 模型，例如裁剪、更改像素等。接下来，我们将使用 Heroku 容器注册表或作为 Google 云中的服务应用程序的 Kubernetes 集群托管 Web 应用程序。

## 结构

本章将涵盖以下主题：

- 问题陈述
- GCP 和 Heroku 中项目要求的设置
- Streamlit 组件简介
- 为 OpenCV 模型构建 Streamlit 框架
- 创建 Heroku 部署的组件
- 通过在 Kubernetes 集群中容器化部署 Streamlit 代码

## 目标

学习本章后，您将能够理解以下内容：

- 如何使用 Docker 和 Kubernetes。
- 如何在没有任何 JavaScript 知识的情况下使用 Python Streamlit 构建 Web 应用程序。
- 各种计算机视觉 OpenCV 模型。
- 如何为 Streamlit 构建框架并将其托管到 Heroku。
- 如何使用 Kubernetes 和许多 Google Cloud Platform 来利用其强大的功能部署和托管应用程序。

## 8.1 问题陈述

在本章中，我们将使用 OpenCV 模型的各种图像处理技术应用，为此我们将使用 Streamlit 库构建 UI 框架。因此，我们将构建 OpenCV 模型，如铅笔素描、裁剪图像、锐化图像和颜色更改图像，然后我们将添加漫画阅读器。然后，我们将把应用程序托管在 Heroku 或 GCP 中的 Kubernetes 集群中。

| GCP. GCP. GCP. GCP. GCP. GCP. GCP. GCP. GCP. GCP. GCP. |
| GCP. GCP. GCP. GCP. GCP. GCP. GCP. GCP. GCP. GCP. GCP. |
| GCP. GCP. GCP. GCP. GCP. GCP. GCP. GCP. GCP. GCP. GCP. |
| GCP. |

## 8.2 GCP 和 Heroku 中项目要求的设置

Google Cloud Platform：使用您的电子邮件 ID 创建一个帐户，您将被重定向到云帐户的主页。

您必须拥有一个活跃的 GCP 帐户，并且在练习本章时，运行 Kubernetes 集群可能会产生费用，因为我运行的所有代码都在 MacOS 上。我建议必须具备一些基本的 Kubernetes 和 Docker 知识。

![](img/8f8a671916d96b455297952d0f37b96c_488_0.png)

Figure 8.1: Google Cloud Platform

使用您的电子邮件 ID 创建一个帐户。

![](img/8f8a671916d96b455297952d0f37b96c_489_0.png)

Figure 8.2: Heroku 平台

让我们在下一节中构建 Streamlit 组件。

## 8.3 Streamlit 组件简介

Streamlit 是一个开源应用框架，是数据科学家和机器学习工程师在几个小时内创建漂亮、高性能应用的最简单方法。Streamlit 的目标是为我们的数据或模型创建交互式应用，并在过程中使用 Streamlit 检查、调试、完善和分享我们的代码。

设置您的虚拟环境：`pip install streamlit==0.71.0`

### 功能：

我们可以用几行代码构建一个应用并利用 Streamlit 简单的 API，我们可以保存源 Python 文件并自动更新。

![](img/8f8a671916d96b455297952d0f37b96c_490_0.png)

Figure 8.3: Streamlit 功能 1

我们可以添加各种小部件用于 Python 中的变量声明，如复选框、滑块、文本框等。无需从后端硬编码变量并定义路由来处理 HTTP 请求等。

![](img/8f8a671916d96b455297952d0f37b96c_491_0.png)

Figure 8.4: Streamlit 功能 2

即时在本地或云端托管您的应用程序，无需太多努力和维护。

![](img/8f8a671916d96b455297952d0f37b96c_491_1.png)

Figure 8.5: Streamlit 功能 3

所以，这些是 Streamlit 最重要的功能。

### 8.3.1 主要概念

首先，让我们在 Python 脚本中编写一些 Streamlit 命令，然后使用 Streamlit run 运行它。将在默认浏览器中打开一个新标签页。现在它会是空白的。没关系。

```bash
streamlit run your_script.py
```

![](img/8f8a671916d96b455297952d0f37b96c_493_0.png)

*Figure 8.6: Streamlit 本地主机 URL*

### 使用文本：

```
streamlit.write(*args, **kwargs)
```

“瑞士军刀”。您可以将几乎任何内容传递给文本、数据、Matplotlib 图形、Altair 图表等。使用特定的文本函数向您的应用添加内容。

```
streamlit.title(body)
```

它以标题格式显示文本。

```
streamlit.subheader(body)
```

此 API 以副标题格式显示文本。

```
streamlit.code(body, language='python')
```

它显示一个代码块，可选语法高亮。

```
streamlit.latex(body)
```

这个显示格式化为 LaTeX 的数学表达式。

```
import streamlit as st
```

```
import pandas as pd
```

```
import numpy as np
```

```
st.title('My first Web Application')
```

```
st.subheader("This is Subheader for Maths Equation")
```

```
st.markdown('Streamlit is **_really_ cool*.')
```

```
st.latex(r'''f(x)=a_0 +\sum_{n=1}^{\infty}(a_n + b_n)\left(\frac{1-r^{n}}{1-r}\right)
cos\left(\frac{n\pi x/L}{1-r}\right)sin\left(\frac{n\pi x/L}{1-r}\right)''')
```

```
st.write('Hello, *World!* :sunglasses:')
```

```
code = """def python():
print("Hello, Streamlit!")"""
st.code(code)
```

现在，打开 Bash 或终端，无论代码在哪里，然后运行 **streamlit run Basics.py：**

![](img/8f8a671916d96b455297952d0f37b96c_495_0.png)

Figure 8.7: Streamlit 文本组件

因此，前面的屏幕截图显示了 Streamlit 工具的文本组件的输出。

### 使用媒体：

```
streamlit.audio(data, format='audio/wav', start_time=0)
```

此 API 显示音频播放器。



```
streamlit.image(image, caption=None, width=None,
use_column_width=False, clamp=False, channels='RGB',
output_format='auto', **kwargs)
```

很容易将图像、视频和音频文件直接嵌入到你的 Streamlit 应用中。

```
streamlit.video(data, format='video/mp4', start_time=0)
```

这里，此 API 显示一个视频播放器。

现在，打开 Bash 或 Terminal，无论代码在哪里，然后运行 **Streamlit run**

![](img/8f8a671916d96b455297952d0f37b96c_496_0.png)

图 8.8：Streamlit 媒体组件

因此，以上是 Streamlit 媒体组件的输出。

## 使用媒体

```
streamlit.button(label, key=None)
```

它用于显示按钮小部件。

```
streamlit.checkbox(label, value=False, key=None)
```

此 API 显示一个复选框小部件。

```
streamlit.selectbox(label, options, index=0, format_func='str',
key=None)
```

它显示一个选择小部件。

```
streamlit.radio(label, options, index=0, format_func='str',
key=None)
```

它用于显示单选按钮小部件。

```
streamlit.multiselect(label, options, default=None, format_func='str',
key=None)
```

此 API 显示一个多选小部件。多选小部件初始为空。

```
streamlit.slider(label, min_value=None, max_value=None,
value=None, step=None, format=None)
```

它显示一个滑块小部件。这支持 int、float、date、time 和 datetime 类型。

```
streamlit.text_input(label, value="", max_chars=None, key=None,
type='default')
```

此 API 显示一个单行文本输入小部件。

```
streamlit.number_input(label, min_value=None, max_value=None,
value=None, step=None, format=None, key=None)
```

显示一个数字输入小部件。

让我们在 Python 脚本中构建上述 API：

```
import streamlit as st
import pandas as pd
import numpy as np
from PIL import Image
import datetime
```

```
st.title('My first Web Application for Widget')
# Button
if st.button('HIT ME'):
st.write('Hello welcome to my world :sunglasses:')
else:
st.write("It's time for GoodBye")
```

### 复选框

```
condition = st.checkbox('Do you want?')
if condition:
    st.write('Welcome to my checkbox world!')
```

### RadioButton

```
sport = st.radio(
"What's your favorite sport?",
('Cricket', 'Football', 'Hockey'))
if sport == 'Cricket':
    st.write('You selected Cricket. 🏏')
elif sport == 'Football':
    st.write('You selected Football. ⚽')
elif sport == 'Hockey':
    st.write('You selected Hockey. 🏑')
else:
    st.write("You didn't select anything.")
```

### SelectBox

```
option = st.selectbox(
'Which movie type you want to see?',
('Romantic', 'Action', 'Horror'))
st.write('You selected:', option)
```

### Multiselect

```
options = st.multiselect(
'What are your favorite colors',
['Green', 'Yellow', 'Red', 'Blue'],
['Yellow', 'Red'])
st.write('You selected:', options)
```

```
# Slider
age = st.slider('How old are you?', 0, 130, 25)
st.write("I'm ", age, 'years old')
```

```
# Text Input
title = st.text_input('Movie title', 'Dark night Rises')
st.write('The current movie title is', title)
```

```
# Number Input
number = st.number_input('Insert a number')
st.write('The current number is ', number)
```

```
#File Upload
uploaded_file = st.file_uploader("Choose a CSV file", type="csv")
st.set_option('deprecation.showfileUploaderEncoding', False)
if uploaded_file:
text_io = io.TextIOWrapper(uploaded_file)
if text_io is not None:
data = pd.read_csv(text_io)
st.write(data)
```

```
# Input Date
d = st.date_input(
"When's your birthday",
datetime.date(2019, 7, 6))
st.write('Your birthday is:', d)
```

现在，打开 Bash 或 Terminal，无论代码在哪里，然后运行 Streamlit run 并在浏览器中打开链接。

![](img/8f8a671916d96b455297952d0f37b96c_501_0.png)

图 8.9：Streamlit 媒体组件

因此，以上是 Streamlit 媒体组件的输出。

## 使用数据和图表

```
streamlit.dataframe(data=None, width=None, height=None)
```

它将数据框显示为交互式表格。

```
streamlit.line_chart(data=None, width=0, height=0,
use_container_width=True)
```

它显示折线图。同样，我们可以绘制条形图和面积图。

```
streamlit.plotly_chart(figure_or_data, width=0, height=0,
use_container_width=False, sharing='streamlit', **kwargs)
```

它显示一个交互式 Plotly 图表。Plotly 是 Python 的图表库。

```
import streamlit as st
import pandas as pd
import numpy as np
```

```
st.title('My first Web Application for Data & Chart')
# Data Table
df = pd.DataFrame(np.random.randn(4, 2),columns=('col %d' % i
for i in range(2)))
st.dataframe(df) # Same as st.write(df)
```

```
# Line Chart
chart_data = pd.DataFrame(np.random.randn(20, 3),columns=['a', 'b',
'c'])
st.line_chart(chart_data)
```

```
# plotly
import plotly.express as px
df = px.data.gapminder().query("year == 2007")
fig = px.sunburst(df, path=['continent', 'country'], values='pop',
color='lifeExp', hover_data=
['iso_alpha'],color_continuous_scale='RdBu',
color_continuous_midpoint=np.average(df['lifeExp'],
weights=df['pop']))
st.plotly_chart(fig, use_container_width=True)
```

现在，打开 Bash 或 Terminal，无论代码在哪里，然后运行 **Streamlit run** 然后，在浏览器中打开以下链接： **http://Localhost:8051**

![](img/8f8a671916d96b455297952d0f37b96c_503_0.png)

图 8.10：Streamlit 数据和图表组件

如需进一步学习 API，请访问以下链接：

## 8.4 为 Streamlit 构建 OpenCV 模型的框架

要为 Streamlit 构建 OpenCV 模型的框架，请完成以下步骤：

### STEP 1：加载计算机视觉模型和 Streamlit 的所有依赖项。

```
import streamlit as st
import cv2
import numpy as np
from PIL import Image
from matplotlib import pyplot as plt
import io
import cv2 as cv
import os
import glob
import requests
from bs4 import BeautifulSoup
import urllib.request
import random
import pandas as pd
from io import BytesIO
import ssl
ssl._create_default_https_context = ssl._create_unverified_context
```

### STEP 2：现在我们将为我们的应用程序设置一些 Logo 和标题。然后，我们可以从下拉菜单中选择 OpenCV 模型。然后，st.sidebar.selectbox() 将把小部件添加到 UI 的右侧。

```
st.markdown("![Alt Text]
(https://raw.githubusercontent.com/aniruddhachoudhury/AR-RL-/master/CoMPUTER%20VISION.gif)")
```

```
st.title("Computer Vision Use Case")
st.sidebar.subheader("Choose Computer Vision Model")
model = st.sidebar.selectbox("Model", ("Pencil Sketch","Crop Image","Sharp Image","Color Spacer","Comic Reader"))
```

![](img/8f8a671916d96b455297952d0f37b96c_506_0.png)

图 8.11：Streamlit 模型下拉菜单

### STEP 3：在此步骤中，我们将使用 st.write() 函数写一个标题，并设置一些弃用选项。接下来，我们将上传任何格式的图像，如 jpg、png 等，因此 st.file_uploader() 对象将被存储在内部

```
st.write("This Web App is to help convert your photos to realistic images")
st.set_option('deprecation.showfileUploaderEncoding', False)
file_image = st.sidebar.file_uploader("Upload your Photos", type=['jpeg','jpg','png'])
st.set_option('deprecation.showfileUploaderEncoding', False)
```

![](img/8f8a671916d96b455297952d0f37b96c_507_0.png)

图 8.12：Streamlit st.file_uploader()

### STEP 4：现在，让我们为 OpenCV 铅笔素描构建第一个模型。如果我们在此处给出条件，即如果您想从步骤 2 中选择模型，它将是铅笔素描，那么 dodgeV2() 和 pencilsketch() 函数将执行必要的预处理，如转换和缩放图像，并返回输出。st.image() 函数将在浏览器中显示输入和输出图像。st.write() 函数在浏览器中显示您想要的文本。st.file_uploader() 函数将返回一个 BytesIO 对象。然而，Image.open() 接受一个字符串来读取图像。

```
def dodgeV2(x, y):
return cv2.divide(x, 255 - y, scale=256)
def pencilsketch(inp_img):
img_gray = cv2.cvtColor(inp_img, cv2.COLOR_BGR2GRAY)
img_invert = cv2.bitwise_not(img_gray)
img_smoothing = cv2.GaussianBlur(img_invert, (21, 21),sigmaX=0,
sigmaY=0)
final_img = dodgeV2(img_gray, img_smoothing)
return(final_img)
if model == "Pencil Sketch":
st.subheader("PencilSketcher app to Cartoon Image")
if file_image is None:
st.write("You haven't uploaded any image file")
else:
input_img = Image.open(file_image)
final_sketch = pencilsketch(np.array(input_img))
st.write("**Input Photo**")


```
st.image(input_img, use_column_width=True)
st.write("**Output Pencil Sketch**")
```

```
st.image(final_sketch, use_column_width=True)
```

现在，打开 Bash 或 Terminal，无论代码在哪里，然后运行 Streamlit run 然后，在浏览器中打开以下链接：

![](img/8f8a671916d96b455297952d0f37b96c_509_0.png)

图 8.13：OpenCV 铅笔素描输出

### 第 5 步：现在，让我们构建用于 OpenCV 裁剪和更改像素的第二个模型。如果我们给出条件，即如果您想在此处从第 2 步选择模型，那么它将是裁剪图像。st.file_uploader() 函数将返回一个 BytesIO 对象。然而，Image.open() 接受一个字符串来读取图像。接下来，我们将使用 st.sidebar.slider() 函数从滑块中选择所有坐标的像素坐标。我们添加了一个 if 条件——是否想要裁剪。之后，我们将执行必要的 OpenCV 图像裁剪操作和像素更改。st.image() 将输出图像并在浏览器中显示输入和输出图像。

```
if model == "Crop Image":
st.subheader("Crop your Image app to your size")
if file_image is None:
st.write("You haven't uploaded any image file")
else:
input_img = Image.open(file_image)
image = np.array(input_img)
x, y = image.shape[:2]
height, width = image.shape[:2]
print(height,width)
st.sidebar.subheader("Choose Pixel for image")
# Let's get the starting pixel coordinates (top left of cropping rectangle)
startrowper=st.sidebar.slider("Start Row", min_value=0., max_value=1.0)
startcolper=st.sidebar.slider("Start Column", min_value=0., max_value=1.0)
endrowper=st.sidebar.slider("End Row", min_value=0., max_value=1.0)
endcolper=st.sidebar.slider("End Column", min_value=0., max_value=1.0)
Crop = st.sidebar.selectbox("You want to Crop", ("Yes", "No"))
if Crop=='Yes':
```

```
start_row, start_col = int(height * startrowper), int(width *
startcolper)
# Let's get the ending pixel coordinates (bottom right)
end_row, end_col = int(height * endrowper), int(width * endcolper)

# Simply use indexing to crop out the rectangle we desire
cropped = image[start_row:end_row, start_col:end_col]
row, col = 1, 2
fig, axs = plt.subplots(row, col, figsize=(15, 10))
fig.tight_layout()
axs[0].imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
axs[0].set_title('Original Image')
cv2.imwrite('original_image.png', image)
st.image('original_image.png', use_column_width=True)
axs[1].imshow(cv2.cvtColor(cropped, cv2.COLOR_BGR2RGB))
axs[1].set_title('Cropped Image')
cv2.imwrite('cropped_image.png', cropped)
st.image('cropped_image.png', use_column_width=True)
else:
st.write("You don't want to crop")
```

现在，打开 Bash 或 Terminal，无论代码在哪里，然后运行 **Streamlit run** 然后，在浏览器中打开以下链接：

![](img/8f8a671916d96b455297952d0f37b96c_512_0.png)

图 8.14：OpenCV 像素更改输出

因此，以上是 Streamlit 应用中 OpenCV 像素更改模型的输出。

### 第 6 步：现在让我们构建用于 OpenCV 锐化图像的第三个模型。如果我们给出条件，即如果您想在此处从第 2 步选择模型，它将是裁剪图像。st.file_uploader() 函数将返回一个 BytesIO 对象。然而，Image.open() 接受一个字符串来读取图像。

接下来，我们将使用 st.sidebar.slider() 函数从滑块中选择所有坐标的像素坐标。之后，我们将使用 cv2.filter2d 内核和归一化应用执行必要的 OpenCV 图像锐化。st.image() 将输出图像并在浏览器中显示输入和输出图像。

```
if model == "Sharp Image":
 st.subheader("Sharpen your Image")

if st.sidebar.button('Changer'):
 showpred = 1
 if file_image is None:
  st.write("You haven't uploaded any image file")
 else:
  input_img = Image.open(file_image)
  image = np.array(input_img)
  row, col = 1, 2
  fig, axs = plt.subplots(row, col, figsize=(15, 10))
  #fig.tight_layout()
  axs[0].imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
  axs[0].set_title('Original Image')
  # Create our sharpening kernel, we don't normalize since the
  # the values in the matrix sum to 1
  kernel_sharpening = np.array([[-1,-1,-1],[-1,9,-1], [-1,-1,-1]])
  # applying different kernels to the input image
  sharpened = cv2.filter2D(image, -1, kernel_sharpening)
  axs[1].imshow(cv2.cvtColor(sharpened, cv2.COLOR_BGR2RGB))
  axs[1].set_title('Image Sharpening')
  st.image(input_img, use_column_width=True)
  cv2.imwrite('sharpen_image.jpg', sharpened)
  st.image('sharpen_image.jpg', use_column_width=True)
```

现在，打开 Bash 或 Terminal，无论代码在哪里，然后运行 **Streamlit run** 然后，在浏览器中打开以下链接：

![](img/8f8a671916d96b455297952d0f37b96c_514_0.png)

图 8.15：OpenCV 锐化输出

### 第 7 步：现在，让我们构建用于 OpenCV 颜色空间更改的第四个模型。如果我们给出条件，即如果您想在此处从第 2 步选择模型，它将是裁剪图像。**st.file_uploader()** 函数将返回一个 BytesIO 对象。然而，**Image.open()** 接受一个字符串来读取图像。接下来，我们在侧边栏上添加了 **st.sidebar.selectbox()** 函数用于 UI；这里我们有不同的 OpenCV 颜色更改选项，如“bw”、“hsv”等。然后，如果条件与我们选择的选项匹配，它将执行必要的操作，最后 **st.image()** 将在浏览器中显示图像。

```
if model == "Color Spacer":
st.subheader("Sharpen your Image")
cs = ["bw","hsv","yuv","lab"]
color_space = st.sidebar.selectbox("Pick a space.", cs)

if st.sidebar.button('Changer'):
showpred = 1
if file_image is None:
st.write("You haven't uploaded any image file")
else:
input_img = Image.open(file_image)
st.write("**Input Photo**")
st.image(input_img, use_column_width=True)
src = np.array(input_img)
if color_space == "bw":
image = cv2.cvtColor(src, cv2.COLOR_BGR2GRAY)
if color_space == "hsv":
image = cv2.cvtColor(src, cv2.COLOR_BGR2HSV)
if color_space == "yuv":
image = cv2.cvtColor(src, cv2.COLOR_BGR2YUV)
if color_space == "lab":
image = cv2.cvtColor(src, cv2.COLOR_BGR2LAB)
st.write("**Output Pencil Sketch**")
st.image(image,use_column_width=True)
```

现在，打开 Bash 或 Terminal，无论代码在哪里，然后运行 **Streamlit run** 然后，在浏览器中打开以下链接：

![](img/8f8a671916d96b455297952d0f37b96c_516_0.png)

图 8.16：OpenCV 颜色更改器输出

因此，以上是 Streamlit 中 OpenCV 模型组件的输出。

我们将所有模型组合在如下函数之下：

```
def main():
{
CODE
}
```

```
if __name__ == '__main__':
main()
```

为了本地调试测试，我们运行命令 Streamlit run

```
You can now view your Streamlit app in your browser.

Local URL: http://localhost:8501
Network URL: http://192.168.29.199:8501
```

图 8.17：应用的本地主机 URL

## 8.5 为 Heroku 部署创建组件

![](img/8f8a671916d96b455297952d0f37b96c_518_0.png)

![](img/8f8a671916d96b455297952d0f37b96c_518_1.png)

构建阶段是一个转换，它通过获取和供应商化依赖项并编译二进制文件和资源，将代码仓库转换为称为 slug 的可执行包。

发布阶段然后获取构建并将其与部署的当前配置组合。 resulting release 包含构建和配置，并可立即执行。

图 8.18：Heroku 架构

现在，创建应用程序的 Python 脚本，使用 Docker 容器化整个框架，将构建发布到 Heroku 内的 App，然后在其中托管应用程序并部署它，这将生成一个主机 URL。

现在，我们将构建 Docker 镜像；为此，请确保启动 Docker，之后您将在顶部看到 Docker 已激活。在以下截图中，我们可以看到第一个图标 Docker 已启动。您可以从该图标停止或重新启动。



### 图 8.19：Docker 激活

Heroku 提供三种部署 Docker 化应用的方式。我们将使用容器注册表。

![](img/8f8a671916d96b455297952d0f37b96c_519_0.png)

![](img/8f8a671916d96b455297952d0f37b96c_519_1.png)

### 图 8.20：Heroku 部署方法

Heroku 部署文件夹包含以下文件：

![](img/8f8a671916d96b455297952d0f37b96c_519_2.png)

### 图 8.21：Heroku 部署文件夹

现在，让我们为 Heroku 部署创建 Dockerfile。

Dockerfile:

```
FROM ubuntu:18.04
# streamlit-specific commands for config
ENV LC_ALL=C.UTF-8
ENV LANG=C.UTF-8
RUN mkdir -p /root/.streamlit

RUN bash -c 'echo -e "\
[general]\n\
email = \"\"\n\
" > /root/.streamlit/credentials.toml'
RUN bash -c 'echo -e "\
[server]\n\
enableCORS = false\n\
" > /root/.streamlit/config.toml'

RUN apt-get update && \
apt-get install -y \
python3.7 python3-pip \
libsm6 libxext6 libxrender-dev
EXPOSE 8501
# make app directory
WORKDIR /streamlit-docker
```

- 1. streamlit
- 2. black
- 3. altair
- 4. pandas
- 5. pydeck
- 6. matplotlib
- 7. numpy
- 8. Pillow
- 9. bs4
- 10. pipenv
- 11. xlrd
- 12. opencv-python==4.2.0.34
- 13. gdown

### 图 8.22：Heroku Docker requirements 文件

```
COPY requirements.txt ./requirements.txt
RUN pip3 install -r requirements.txt
COPY . .
```

### 图 8.22：Heroku Docker requirements 文件

```
RUN chmod +x ./heroku_startup.sh
ENTRYPOINT "./heroku_startup.sh"
```

下面对 Docker 进行如下分解：

获取基础镜像。就像你的应用程序需要一个操作系统作为基础一样。

显示此镜像作者的消息。

将环境变量设置为特定值。

执行包含 Python 库的 requirements 文件命令。

让容器在运行时监听特定端口。

**WORKDIR/** 设置工作目录，复制新文件/目录。

执行容器时提供默认操作。

更改 **heroku_startup.sh** 的权限，否则在执行时你会收到权限被拒绝错误

**ENTRYPOINT** 告诉 Docker 在启动容器时执行 heroku_startup.sh。

前一行中第二个和第三个 RUN 命令的目的是让 OpenCV 在 Docker 中正常运行，以缓解一个问题：如果我们在构建 Docker 镜像时未安装 libSM.so.6 并导入 OpenCV，我们的容器在执行时会静默崩溃，并出现以下消息：segmentation fault (core dumped) when executing。

## Heroku.yml：

```
build:
docker:
web: heroku.Dockerfile
run:
web: ./heroku_startup.sh
```

Heroku 需要 heroku.yml 来构建和部署 Docker 镜像，因此我们将为此创建一个。显然，build 和 run 部分分别表示我们在 Heroku 上的构建和运行阶段想要执行的操作。

## Heroku_startup.sh：

```
echo PORT $PORT
streamlit run --server.port $PORT Master.py
```

Heroku 使用 $PORT 环境变量进行端口暴露。我们必须将 $PORT 变量设置为 Streamlit，否则你的应用将不会出现。在这种情况下，我们将在 8501 上暴露。

## 安装：

现在下载 Heroku CLI :
https://devcenter.heroku.com/articles/heroku-cli#download-and-install

安装 Brew: https://brew.sh/

```
brew tap heroku/brew && brew install heroku
```

```
sudo snap install --classic heroku
```

## 组件步骤如下：

首先登录你的 Heroku 账户并按照提示创建新的 SSH 公钥。

```
$ heroku login
```

登录容器注册表：

```
$ heroku container:login
```

![](img/8f8a671916d96b455297952d0f37b96c_524_0.png)

### 图 8.23：Heroku CLI 登录

导航到应用目录并创建 Heroku 应用：

```
$ heroku create
```

```
Creating app... done, hidden-river-78993
https://hidden-river-78993.herokuapp.com/ | https://git.heroku.com/hidden-river-78993.git
```

### 图 8.24：Heroku 应用创建

构建镜像并在一行命令中推送到容器注册表。确保你已启动 Docker。并且确保你将下面的应用名称更改为你的情况，该名称将在上面创建。

```
$ heroku container:push web -a hidden-river-78993
```

```
(base) .Heroku $ heroku container:push web -a hidden-river-78993
=== Building web (/Users//Downloads/Streamlit/ComputerVision/Heroku/Dockerfile)
Sending build context to Docker daemon 16.38kB
Step 1/14 : FROM ubuntu:18.04
18.04: Pulling from library/ubuntu
5d9821c94847: Downloading 25.57MB/26.7MB
a610eae58dfc: Download complete
a40e0eb9f140: Download complete
Successfully built 68a10f4d1819
Successfully tagged registry.heroku.com/hidden-river-78993/web:latest
```

### 图 8.25：Heroku 容器构建并推送消息

然后将镜像发布到我们创建的应用；这里是 hidden-river-78993。

```
$ heroku container:release web -a hidden-river-78993
```

Releasing images web to hidden-river-78993... done

### 图 8.26：Heroku 容器已发布到应用

现在，在浏览器中打开应用，或我们可以导航到网站并点击右上角的 Open app。

```
$ heroku open -a hidden-river-78993
```

![](img/8f8a671916d96b455297952d0f37b96c_526_0.png)

### 图 8.27：Heroku 网站点击打开应用

现在，我们可以看到托管在 Heroku 上的 Web 应用。

## 选择计算机视觉模型

模型

Pencil Sketch

上传你的照片

将文件拖放到此处上传

浏览文件

## 计算机视觉用例

此 Web 应用旨在帮助将你的照片转换为逼真图像

### 图 8.28：托管在 Heroku 上的计算机视觉应用

![](img/8f8a671916d96b455297952d0f37b96c_527_0.png)

## 8.6 通过在 Kubernetes 集群中容器化部署 Streamlit 代码

![](img/8f8a671916d96b455297952d0f37b96c_528_0.png)

![](img/8f8a671916d96b455297952d0f37b96c_528_1.png)

### 图 8.29：GCP Kubernetes 部署架构

现在，创建应用程序的 Python 脚本，使用 Docker 将整个框架容器化，并在 Kubernetes 集群中作为部署服务部署应用程序，Docker 镜像将作为负载均衡器部署公开，这将在端口 8501 上生成主机 URL：

容器是一种软件类型，它将应用程序及其所有依赖项打包在一起，以便应用程序能够从一个计算环境可靠地运行到另一个计算环境。

Docker 是一种用于构建和管理容器的软件。

Kubernetes 是一个用于在集群环境中管理容器化应用程序的开源系统。

Google Kubernetes Engine 是在 Google Cloud Platform 上对开源 Kubernetes 框架的实现。

让我们构建 Docker 镜像，保持与之前相同，只是从之前的 Heroku Dockerfile 中删除最后两行，并添加一行 CMD 来运行 Streamlit Python 脚本：

```
FROM ubuntu:18.04
ENV LC_ALL=C.UTF-8
ENV LANG=C.UTF-8
RUN mkdir -p /root/.streamlit

RUN bash -c 'echo -e "\
[general]\n\
email = \"\"\n\
" > /root/.streamlit/credentials.toml'

RUN bash -c 'echo -e "\
[server]\n\
enableCORS = false\n\
" > /root/.streamlit/config.toml'

RUN apt-get update && \
apt-get install -y \
python3.7 python3-pip \
libsm6 libxext6 libxrender-dev

EXPOSE 8501
WORKDIR /streamlit-docker
COPY requirements.txt ./requirements.txt
RUN pip3 install -r requirements.txt
COPY . .
CMD streamlit run Master.py
```

现在，在 Bash 中运行以下命令来为你的 GCP 部署构建 Docker 镜像，假设你已将 GCP 项目作为先决条件：

```bash
gcloud init
gcloud auth configure-docker
PROJECT_ID=$(gcloud config get-value core/project)
IMAGE_NAME=opencv-streamlit
IMAGE_NAME=gcr.io/$PROJECT_ID/$IMAGE_NAME
IMAGE_TAG=v1

# build image

docker build --no-cache -t $IMAGE_NAME:$IMAGE_TAG .
docker push $IMAGE_NAME:$IMAGE_TAG
```

假设我们的 Docker 镜像将如下所示：
**gcr.io//opencv-streamlit:v1**

确保你安装了 kubectl，我们已在第 1 章《Kubeflow & Kubernetes 云简介》中安装过。此外，请访问以下链接：https://kubernetes.io/docs/tasks/tools/install-kubectl/

## 创建集群：

要设置 Kubernetes 集群，你可以使用 Google Cloud Shell 或系统的 Microsoft Visual Studio 终端。导航到 Google Cloud Platform > Kubernetes > Cluster。

![](img/8f8a671916d96b455297952d0f37b96c_531_0.png)

### 图 8.30：GCP Cloud Shell

现在，完成以下步骤：

为 gcloud 工具设置你的项目 ID 和 Compute Engine 区域选项。

```
PROJECT_ID=$(gcloud config get-value core/project)
gcloud config set project $PROJECT_ID
```

```
gcloud config set compute/zone us-central1
```

创建集群，请执行以下代码：

```
gcloud container clusters create streamlit-computer-vision --num-nodes=2
```

![](img/8f8a671916d96b455297952d0f37b96c_532_0.png)

图 8.31：集群创建

通过点击 Connect 按钮连接到集群。

```
gcloud container clusters get-credentials streamlit-computer-vision --region us-central1 --project
```

![](img/8f8a671916d96b455297952d0f37b96c_532_1.png)

图 8.32：集群连接

要在 GKE 集群上部署和管理应用程序，您必须与 Kubernetes 集群管理系统进行通信。执行以下命令部署应用程序：

```
kubectl create deployment computervision-streamlit --image=gcr.io/opencv-streamlit:v1
```

![](img/8f8a671916d96b455297952d0f37b96c_533_0.png)

图 8.33：成功部署消息

您在 GKE 上运行的容器无法从互联网访问，因为它们没有外部 IP 地址。执行以下代码将应用程序公开到互联网：

```
kubectl expose deployment computervision-streamlit --type=LoadBalancer --port 80 --target-port 8501
```

![](img/8f8a671916d96b455297952d0f37b96c_533_1.png)

图 8.34：成功 LoadBalancer 服务消息

执行以下代码以获取服务的状态。EXTERNAL-IP 是您可以在浏览器中使用的网络地址，用于查看已发布的应用程序。

```
kubectl get service
```

![](img/8f8a671916d96b455297952d0f37b96c_533_2.png)

图 8.35：成功服务消息

复制 External IP 并粘贴到浏览器中。我们将获得我们的应用程序 http://34.71.219.0

现在，我们可以看到托管在 Google Cloud Platform 上的网络应用程序：

![](img/8f8a671916d96b455297952d0f37b96c_534_0.png)

图 8.36：托管在 Google Kubernetes Engine 上的计算机视觉应用程序

## 8.7 摘要

本章中，我们学习了如何在没有其他语言先验知识的情况下，使用 Python 中的 Streamlit 工具构建网络应用程序。然后，我们将应用程序托管在 Heroku 平台和 Google Kubernetes Engine 上。

接下来，我们学习了各种 Streamlit 组件，用于显示文本、图像、图表等。此外，我们为各种计算机视觉 OpenCV 模型（如 Sharpening、Cropping Image 等）构建了网络应用程序的框架。之后，我们看到了构建 Heroku 部署的架构，它是可与 Google Kubernetes Engine 一起用于所有 Skeleton 机器学习网络应用程序部署的通用骨架。

在本章中，我们获得了如何利用 Google Cloud Platform 的强大功能以及如何将 DevOps 知识与机器学习结合以成为 MLOps 的知识。此外，我们还学习了如何使用 Streamlit 在 Heroku 和云中仅用几个小时构建 Skeleton Web 应用程序。

## 8.8 参考文献

https://devcenter.heroku.com/categories/reference
https://technowhisp.com/kaggle-api-python-documentation/

https://docs.streamlit.io/en/stable/api.html

https://kubernetes.io/docs/tutorials/kubernetes-basics/

https://cloud.google.com/kubernetes-engine/docs/quickstart

https://www.pyimagesearch.com/start-here/

https://docs.docker.com/get-started/overview/

https://devcenter.heroku.com/articles/container-registry-and-runtime#unsupported-dockerfile-commands

## 索引

### A

Amazon SageMaker Notebook Instance
创建
Amazon SageMaker Training model 261
数据，拆分为训练/验证 262
部署
使用 SageMaker API XG-Boost
训练数据，推送到 S3 263
验证数据，推送到 S3 263
自动扩缩容
算法 129
恐慌 129
工作概念 129
AWS S3 Bucket
创建 241
AWS SageMaker
问题陈述 236
设置

### B

脑肿瘤 87.
分解技术
用于构建生产管道 46

### C

Cloud IAP
OAuth，从 Cloud IAP 设置 27.
集群 10
CNN Kubeflow Pipeline

架构 91
构建 90
数据提取或摄取组件，构建
数据预处理组件，构建
评估组件，构建 106
GCP Kubeflow 设置 86
模型，使用 KF Serving 提供服务
问题陈述 86
问题陈述分析 87
训练模型组件，构建
组件，KF Serving
端点 66
解释器 66
预测器 66
转换器 66
组件，Kubeflow 20
中央 UI 21
仪表板 24
Jupyter Notebook 服务器 23
Katib 24
元数据 23
注册流程 22
容器 3
特性 3
容器隔离 3

对比解释 178
交互的累积效应 186
自定义 Docker 镜像
构建 35

在 Jupyter Notebook 中使用 36

### D

决策图
特性
默认命名空间 18
部署 12
使用 13
SHAP 的期望属性
一致性 178
局部准确性 177
缺失性 177
Docker 2
安装参考链接 29
设置 29
Docker 架构
镜像 3
VM 容器 3
Dockerfile 5
Docker Hub
URL 29
Docker 镜像 3

### F

公平性指标 159
公平性指标可视化 159
特征暴露 215
强制图分析

### G

gcloud sdk

安装 26
设置 27.
GCP Kubeflow 设置
集群，连接到 34.
Docker，设置 29
gcloud sdk，安装 26
gcloud sdk，设置 27.
Grafana，部署 34.
kubectl，安装 26
kubectl，设置 26
Kubeflow，设置
OAuth，从 Cloud IAP 设置 28
执行 26
先决条件 24
参考链接 24.
Google Cloud Platform (GCP) 24.
Google Kubernetes Engine (GKE) 8
Grafana 仪表板
使用...监控服务流量端点性能

### H

Heroku 部署
组件，创建用于
高可用性
健康检查 7.
负载均衡 7.
流量路由 7.
基于直方图的算法
优点 218

### I

Ingress 15

架构 17.

### J

Jupyter Notebook
相关性和散点图
使用自定义 Docker 镜像
数据，从 Python 库加载 247.
数据，从 S3 加载 248
特征工程 248
特征转换
启动 246
缺失值总和，检查 250
模型依赖列转换 251
数值和分类列，查找 249.
异常值检测
PVC 设置
服务器 23

服务器，在 Kubeflow 中设置 35

### K

Kaggle API
API Key，设置 204
安装 203
URL 203
Katib
参考链接 24
kfctl 命令行界面 (CLI)
使用 31

KF Serving
架构 66
组件 66
LightGBM 模型，使用...提供服务
用于提供 TensorFlow 模型服务 65
使用 67
Knative 124
Knative Pod Autoscaler (KPA) 125
Knative Serving 124
kubectl
安装 26
设置 26
Kubeflow 18
架构 19
组件 20
特性 20
Jupyter Notebook 服务器，设置 35
在 Kubernetes 集群中设置

Kubeflow 中央 UI
URL 21
Kubeflow 编排，用于 ML 部署 18
Kubeflow pipeline
构建 47.
构建，用于 TensorFlow 模型 49
数据提取 47.
数据摄取 47.
数据预处理 48
GCP Kubeflow 设置 46
问题陈述 46

提供服务 48
训练 48
Kubeflow Pipeline Orchestrator
构建
kube-node-lease 命名空间 18
kube-public 命名空间 18
Kubernetes
优点 6
能力 6
集群编排系统 8
组件 9
特性 6
主节点 8
节点 9
目的 6
从节点 9
工作方式 8
Kubernetes 组件
集群 10
部署 12

网络 11
节点 10
Pod 11
服务 14
存储 12
Kubernetes，特性
自动化发布和回滚 7
金丝雀部署 7
为部署而设计 7

高可用性 7
开源 6
可移植 6
编程语言和框架支持 7
有状态容器 7
工作负载可扩展性 6
kube-system 命名空间 18

### L

LightGBM 182
架构 217
工作方式 217
LightGBM 模型
数据提取 213
数据加载 213
探索性数据分析
Kaggle API 密钥设置 212
Kaggle 设置，获取 209
库，安装 209
建模，用于股票数据 208

性能，使用 Grafana 仪表板监控 232
使用 KF Serving 提供服务
训练 183
训练，用于股票数据 208
训练，使用 Weights & Biases
效用指标函数 215
Wandb API 密钥设置 210
Wandb 依赖，获取 209
LightGBM 参数
参考链接 220

### M

机器学习 (ML) 22
主节点，Kubernetes
API 服务器 8
控制管理器 9
调度器 9
平均绝对误差 216
元数据，Kubeflow
管理 23
模型分析
使用 SHAP 工具进行高级可视化 184

### N

命名空间
默认 18
kube-node-lease 18
kube-public 18

kube-system 18

多个命名空间，使用 18

网络 11

节点 10

节点

容器引擎 9

Kubelet 9

Kube Proxy 9

Pod 9

## O

OAuth

设置，从 Cloud IAP 28

## P

持久卷 (PV) 38

管道，CNN TensorFlow 模型构建

管道，TensorFlow 模型构建

pod 11

主成分分析 (PCA) 215

配置文件设置，Kubeflow 22

项目要求，GCP & Heroku 设置 275

项目要求，GCP & Wandb Kaggle API 设置 204

Kubeflow 集群 203

设置 202
Weights & Biases API 密钥
PVC
设置，用于 Jupyter Notebook

## R

均方根误差 216

## S

服务 14.
目的 14.
类型 15
serving 组件，TensorFlow 模型管道构建
serving 端点，CNN TensorFlow 模型自动扩缩容，使用 Knative
serving 流量端点，TensorFlow 模型性能，使用 Grafana 监控
SHAP
理想属性 177.
解释示例 178
目标 176
安装 179
Python 库，安装 179
坚实的理论基础 178
Spearman 相关性 216
有状态容器
临时存储卷 7.
持久存储 8
卷 7.
存储 12
Streamlit 275
代码部署，通过在 Kubernetes 集群中容器化
命令，写入 Python 脚本 277.
数据和图表，操作 285
特性 277.
框架，构建用于 OpenCV 模型
媒体，操作
文本，操作 278
Streamlit 组件
构建 276

## T

Tensorboard
高级可视化，用于 TensorFlow 模型

TensorFlow Estimator 模型
构建
构建，使用 DNN 分类器 194.
构建，使用线性模型分类器估计器 194.
构建，使用两个估计器 193

TensorFlow 模型
评估，使用 Tensorboard
评估，使用 What-If 工具
TensorFlow 模型分析 (TFMA) 158
TensorFlow 模型管道
构建 50
数据提取或摄取组件，构建
数据预处理组件，构建
Docker 镜像，构建用于数据提取 53
评估组件，构建 65
训练模型组件，构建
TensorFlow Serving
推理，在示例数据上执行
安装 161
模型，提供服务 161
运行 162
TFMA 指标可视化 158
TFX 组件
Evaluator 133
ExampleGen 133
ExampleValidator 133
功能 134
Pusher 133
SchemaGen 133
StatisticsGen 133
Trainer 133
Transform 133
TFX 环境设置 134
根目录，设置 136
TFX Pipeline
架构 132
问题陈述 132
TFX pipeline 组件 137
Evaluator，构建 158
ExampleGen，构建 138
ExampleValidator，构建 143
Pusher，构建 160
SchemaGen，构建
StatisticsGen，构建 140
Trainer，构建
训练，使用 TensorBoard 分析 156
Transform，构建
Tuner，构建 156
训练模型
特征转换
类型，Services
ClusterIP (默认) 15
ExternalName 15
Headless 15
LoadBalancer 15
NodePort 15

## U

实用指标函数

平均绝对误差 216
均方根误差 216
Spearman 相关性 216

## W

Wandb sweep 架构 219
Weights & Biases
API，创建 206
API 密钥 204
特性 206
框架和云支持 205
使用 208

- What-If 工具
- 高级可视化，用于 TensorFlow 模型
- wit-widget
- 安装 179.
- Python 库，安装 180
- 工作负载可扩展性
- 自动扩缩容 6
- 水平基础设施扩展 6
- 手动扩展 6
- 复制控制器 7.


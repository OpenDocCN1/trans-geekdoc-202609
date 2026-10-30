
## Continuous
Machine Learning
with
Kubeflow

利用 TFX、Sagemaker 和 Kubernetes 的能力进行可靠的 MLOps

ANIRUDDHA CHOUDHURY

![](img/8f8a671916d96b455297952d0f37b96c_0_0.png)

![](img/8f8a671916d96b455297952d0f37b96c_0_1.png)

## Continuous
Machine Learning with
Kubeflow

*利用以下能力进行可靠的 MLOps*
*TFX、Sagemaker 和 Kubernetes*

Aniruddha Choudhury

![](img/8f8a671916d96b455297952d0f37b96c_1_0.png)

www.bpbonline.com

首版 2022

版权 © BPB Publications，印度

ISBN: 978-93-89898-507

保留所有权利。未经出版者事先书面许可，本出版物的任何部分不得以任何形式或任何方式复制、分发或传播，或存储在数据库或检索系统中，但程序列表除外，程序列表可以输入、存储并在计算机系统中执行，但不得通过出版、影印、录音或任何电子和机械方式复制。

## 责任限制和免责声明

本书所载信息在作者和出版商所知范围内真实正确。作者已尽最大努力确保这些出版物的准确性，但出版商不对因本书中的任何信息而产生的任何损失或损害负责。

本书中提及的所有商标均被承认为其各自所有者的财产，但 BPB Publications 不能保证此信息的准确性。

查看完整
BPB Publications 目录
扫描二维码：

![](img/8f8a671916d96b455297952d0f37b96c_3_0.png)

[www.bpbonline.com](http://www.bpbonline.com)

## 致敬

*我深爱的父母和家人*

## *关于作者*

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

## 第 1 章：

在本章中，我们将学习 Kubeflow 的完整功能、其工作原理及其需求。我们还将学习 Kubernetes 的架构功能，例如服务、Pod、Ingress 等。我们将学习构建 Docker 镜像并了解其工作原理。在这里，我们将看到 Kubeflow 的组件优势，我们将在接下来的章节中使用。然后，我们将继续在 Google Cloud 平台上完成 Kubeflow 的完整设置和 Jupyter Notebook 设置。我们有一个可选项目——如何创建持久卷声明并将其附加到文件存储以保存您的代码和数据。

## 第 2 章：

在本章中，我们将构建一个端到端的 TensorFlow 分类模型部署，使用 Kubeflow 编排，其中包括在 GCP 的 Kubernetes 集群中部署 Kubeflow，使用 Docker 和 Kubeflow SDK 为模型构建管道组件，然后使用 KF serving 为预测提供服务以获得端点。我们还将在 Grafana 仪表板中跟踪我们服务流量的端点的监控和性能。

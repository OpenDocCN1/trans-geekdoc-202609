
# 章节概览

## [第 3 章：AutoML 图像、文本和预构建模型](#ch03.xhtml)
本章将处理非结构化数据。如何从非结构化数据（图像和文本数据）创建数据集？如何为图片和文本分类任务训练 AutoML 模型？如何使用训练好的模型进行批量和实时预测。我们将开始了解如何使用 GCP 的预训练模型来解决问题。

## [第 4 章：Vertex AI Workbench 和自定义模型训练](#ch04.xhtml)
我们将开始学习如何使用 Vertex AI 进行自定义模型训练。从基础模型训练示例入手，然后进阶到更复杂的示例。我们将使用 Vertex AI Workbench 组件，评估其各种可能性，并开发一个用于自定义模型训练的单一 Workbench。在深入讲解自定义 Vertex AI 模型之前，我们将向您介绍 `Container`、`Docker` 和 `Kubernetes` 的原理。

## [第 5 章：Vertex AI 自定义模型超参数和部署](#ch05.xhtml)
我们从 Vertex AI 上的一个基础模型训练练习开始，以了解自定义模型训练。在本章中，我们将研究一项更困难的任务：带有超参数调整的模型训练。我们将讨论模型训练完成后如何部署自定义模型以提供预测服务。

## [第 6 章：流水线和 Kubeflow 简介](#ch06.xhtml)
本章将向您介绍 MLOPS 的概念。理解机器学习生命周期。我们将通过示例展示如何使用 Vertex AI 的 AutoML 构建流水线。

## [第 7 章：使用 Kubeflow 为自定义模型构建流水线](#ch07.xhtml)
本章从 Kubeflow 简介开始。如何使用 Kubeflow 组件构建流水线？如何使用 `Container` 创建模型训练作业？Kubeflow 流水线的 CI/CD。

## [第 8 章：使用 TensorFlow Extended 构建流水线](#ch08.xhtml)
TFX 简介是本章的第一部分。如何使用 TFX 组件构建流水线？如何使用 `Container` 构建模型训练作业。TFX 流水线使用 CI/CD。

## [第 9 章：Vertex AI Feature Store](#ch09.xhtml)
本章基于 Vertex AI Feature Store。我们将从 Feature Store 概览开始。Feature Store 的用途是什么？首先介绍 Feature Store 的基础知识，随后是 Feature Store 的实战部分。

## [第 10 章：可解释 AI](#ch10.xhtml)
在本章中，我们将借助 Explainable AI 开始研究机器学习模型。如何使用 Explainable AI 更好地理解图像分类的 ML 模型？如何使用 Explainable AI 更好地识别 ML 模型中的偏差？

# 代码包和彩色图片

请访问以下链接下载本书的 **代码包** 和 **彩色图片**：

[https://rebrand.ly/of74aa7](https://rebrand.ly/of74aa7)

本书的代码包也托管在 GitHub 上：**[https://github.com/bpbpublications/Learning-Google-Cloud-Vertex-AI](https://github.com/bpbpublications/Learning-Google-Cloud-Vertex-AI)**。如果代码有更新，将在现有的 GitHub 仓库中更新。

我们在 **[https://github.com/bpbpublications](https://github.com/bpbpublications)** 上拥有丰富图书和视频目录的代码包。欢迎查看！

# 勘误表

我们在 BPB Publications 为我们的工作感到无比自豪，并遵循最佳实践以确保内容的准确性，为订阅者提供沉浸式的阅读体验。我们的读者是我们的镜子，我们利用他们的反馈来反思和改进出版过程中可能发生的人为错误。为了让我们保持质量并帮助我们联系到可能因不可预见的错误而遇到困难的读者，请写信给我们：

**[errata@bpbonline.com](mailto:errata@bpbonline.com)**

BPB Publications 全家高度赞赏您的支持、建议和反馈。

# 加入我们的 Discord 社区

加入本书的 Discord 工作区，获取最新动态、优惠、全球科技资讯、新版本发布和作者见面会：

**[https://discord.bpbonline.com](https://discord.bpbonline.com)**

![](images/fm1.png)

# [第 1 章 Google Cloud Platform 基础](#contents.xhtml#ch01a)

## [简介](#contents.xhtml#sc2_1a)

本章将介绍 Google Cloud Platform、其优势及其在当今数字化革命中的作用。内容涵盖云计算基础知识，包括云服务模型、GCP 账号创建、覆盖范围、服务范围和 GCP 层级结构。本章还将介绍几项关键的 GCP 服务，包括存储、计算、Google BigQuery 和身份与访问管理。

## [结构](#contents.xhtml#sc2_2a)

本章将涵盖以下主题：

*   云平台简介和基础知识
*   云的优势
*   云对数据科学家的重要性
*   云的类型
*   Google Cloud Platform 简介
*   Google Cloud 的覆盖范围
*   云服务模型
*   GCP 服务
*   GCP 层级结构
*   与 GCP 服务交互
*   GCP 中的存储
*   GCP 中的计算
*   BigQuery
*   身份与访问管理

## [目标](#contents.xhtml#sc2_3a)

在深入了解 Google Cloud Platform 的 Vertex AI 之前，掌握云平台的几个重要原则和关键服务至关重要。读完本章后，用户将对 GCP 组件和服务有扎实的理解。书中包含使用 GCP 存储、计算和 BigQuery 服务的详细说明。

## [云简介](#contents.xhtml#sc2_4a)

**云** 一词描述的是运行在可通过互联网访问的服务器上的应用程序和数据库。全球各地的数据中心托管着云服务器。组织可以通过使用云计算，避免管理物理服务器或在自己的计算机上运行软件。因为计算和存储发生在数据中心的服务器上，而不是用户设备本地，所以云使用户能够从几乎任何设备访问相同的文件和应用程序。

对于企业而言，转向云计算可以消除一些 IT 成本和开销：例如，它们不再需要更新和维护自己的服务器，因为所使用的云供应商会负责这些工作。

## [云的优势](#contents.xhtml#sc2_5a)

云的各种优势如 [图 1.1](#ch01.xhtml#fig1-1) 所示，具体如下：

![](images/Figure_1.1.png)

图 1.1：云平台的优势

*   **成本效益**：在 IT 基础设施管理方面，云计算无疑是最具成本效益的选择。得益于各种即用即付和其他可扩展选项，各种规模的组织从本地硬件迁移到云都非常经济实惠。使用云资源代替购买昂贵的服务器设备和 PC，后者需要大量时间进行设置和维护（如漫长的设置和维护工时）。云还有助于减少在计算、存储、网络、运营和升级方面的支出。

*   **可扩展性和弹性**：总体而言，云托管比本地机器托管更灵活。如果您需要更多带宽，无需对 IT 基础设施进行昂贵（且耗时）的升级。这种更高的自由度和适应性可能对生产力产生重大影响。

    弹性仅在短时间内用于应对工作负载的快速变化。这是一种用于满足需求高峰的短期策略，无论这些高峰是意外的还是季节性的。静态工作负载的增加通过可扩展性来满足。为了应对预期的需求增长，会采用长期的可扩展性策略。


# 机器学习生产环境：MLOps 交付健壮机器学习解决方案指南

## 献词

致我的父母：

我非常感激你们对我的信任，以及你们一生中为我所做的许多牺牲。你们的爱和支持对我来说意义重大。

## 关于作者

**苏哈斯·波特** 在数据科学领域拥有超过八年的多学科经验，曾在众多项目中担任技术负责人和数据科学家等核心角色，为包括南美洲、欧洲和美国在内的大型公司交付了使用开源技术的项目，其中包括许多成功的项目。他有丰富的客户合作经验，并能与不同团队协作工作。目前，他任职于 Eclrx 担任流程经理，是一位成就卓越的研究生，完成了数据科学、商业分析和大数据学位。他拥有电子与通信工程专业的学士学位。与此同时，他成功获得了许多数据科学及相关工具的认证。此外，作者还作为演讲者参加数据科学会议，并就机器学习及相关主题撰写技术文章。他还为全球技术社区（如 Stack Overflow）做出贡献。

## 关于审稿人

卡兰·维杰·辛格是一位充满热情的大数据/机器学习工程师，在云成本优化领域拥有丰富的专业经验。凭借其优化技能，他为当前组织每年节省了 50 万美元的成本。他还于 2019 年在云计算领域共同撰写了一篇研究论文，该论文在全球范围内被引用超过 270 次。

卡兰在加拿大滑铁卢大学获得数学（计算机科学）硕士学位。他目前在加拿大 Lightspeed Commerce 担任数据工程师。

## 致谢

我要向我的家人和朋友表达我最深切的感谢，感谢他们在本书撰写过程中一如既往的支持与鼓励，尤其是我的妻子 Archana 博士和我的儿子 Eshansh。

我也感谢 BPB 出版社在将本书付梓过程中提供的指导和专业知识。这是一段漫长的修订旅程，审稿人、技术专家和编辑都作出了宝贵的参与和协作。

我也要感谢我的同事和合作者多年来在科技行业的工作，他们教会了我许多东西，并对我工作的宝贵反馈。

最后，我要感谢所有对我书籍感兴趣的读者，感谢他们支持本书成为现实。你们的鼓励是无价的。

## 序言

将机器学习模型投入生产是一项复杂的任务，需要全面了解最新技术和 CI/CD 流水线。MLOps 在数据科学领域变得越来越流行。

本书旨在提供使用 MLOps 构建和部署 ML 应用程序的全面指南。它涵盖了广泛的主题，包括 Python 编程基础、Git、机器学习生命周期、Docker，以及打包用于 ML 模型的 Python 代码、监控、模型安全、Kubernetes、使用 pytest 进行测试，以及使用 CI/CD 流水线在包括 Azure、GCP 和 AWS 在内的云平台上构建和部署强大且可扩展的 ML 应用程序等高级概念。

在本书中，您将了解 MLOps、各种工具和部署 ML 模型的技术。您还将学习如何使用它们来投入生产高效、可扩展且易于维护的 ML 模型和应用程序。此外，您还将了解 MLOps 的最佳实践和设计模式。

本书面向数据科学家、软件开发人员、数据工程师、数据分析师以及初次接触 MLOps 的经理，旨在帮助他们学习如何将 ML 模型投入生产。它也对希望扩展这些技术知识并提高在生产环境中部署 ML 模型技能的资深数据科学家和 ML 工程师有所帮助。

通过本书，您将获得在 MLOps 领域熟练掌握所需的知识和技能。希望您会发现本书内容丰富且有所帮助。

**第 1 章：Python 入门** – 解释读者掌握本书所需先决条件的 Python 基础概念，包括 Python 安装、数据结构、控制语句、循环、函数以及使用 pandas 进行数据操作。这是为那些使用过 Python 的人提供的快速复习。如果您是初学者，本章将介绍构建和部署生产环境 ML 模型所需的最常见 Python 命令。它使读者能够使用 Python 学习面向对象编程范式相关的基础概念。

**第 2 章：Git 和 GitHub 基础** – 提供 Git 工作流程的详细概述，包括带有实际示例的常见 Git 命令。这是整本书的重要内容，因为本章涵盖了 Git 和 GitHub 的基本方面，这些方面会影响构建 CI/CD 流水线以在生产环境中部署 ML 模型的技术决策。

**第 3 章：ML 模型部署中的挑战** – 涵盖 ML 生命周期的各个阶段，包括每个阶段挑战的详细信息。它还涵盖了在生产环境中部署模型的常见挑战以及 MLOps 如何帮助克服这些挑战。此外，本章还讨论了在生产环境中部署 ML 模型的不同方法。

**第 4 章：打包 ML 模型** – 使读者能够学习使用 Python 语言进行模块化编程的基础概念，包括 Python 打包、依赖项管理以及开发稳定、可读和可扩展代码的软件开发良好实践，以用于稳健的企业级应用程序。此外，本章还解释了虚拟环境、使用 pytest 测试代码、ML 模型的序列化和反序列化。它涵盖了打包 ML 模型、代码和依赖项，以便该包可以在另一台机器或服务器上安装和使用。

**第 5 章：MLflow – 管理 ML 生命周期的平台** – 特别关注简化机器学习开发，包括跟踪实验、将代码打包为可复现的运行、共享和部署模型。它通过基于用例的实际示例演示如何使用 MLflow 训练、部署和重用 ML 模型。本章解释了 MLflow 在 ML 生命周期中的作用。

**第 6 章：适用于 ML 的 Docker** – 展示 Docker 的基本概念，并为读者提供带有用例的常见 Docker 命令的实际示例。学习这些命令使读者能够将 ML 代码及其依赖项打包并在 Docker 容器中运行应用程序。本章包括 Docker 对象（如 Docker 镜像和容器）的实际示例。

**第 7 章：使用 API 构建 ML Web 应用** – 详细解释了使用 Python 语言构建基于 Web 的 ML 应用程序最常用的框架，包括 FastAPI、Streamlit 和 Flask。它还使读者能够学习 Gunicorn、NGINX 和 API 的基础知识，包括对 REST API 的解释，以及更多内容。





## 第8章：构建原生 ML 应用
致力于使用 Python 构建原生 ML 应用程序，使读者更熟悉将 Python 应用转换为 Windows 和 Android 应用的方法以及如何使用它们。本章介绍了使用 Tkinter、kivy、kivyMD、pyinstaller 和 buildozer 的实际示例。

## 第9章：ML 的 CI/CD
允许读者学习并使用 GitHub 和 Jenkins 实现 CI/CD 流水线的不同阶段，包括提交、构建、测试和部署。本章解释了如何集成 GitHub 和 Jenkins，使用 Python 和 Docker 构建用于部署 ML 应用的自动化 CI/CD 流水线。

## 第10章：在 Heroku 上部署 ML 模型
将指导读者配置并使用 GitHub Actions 构建 CI/CD 流水线，在 Heroku 平台上部署基于 Web 的 ML 应用程序。本章还解释了在 Heroku 上部署 Web 应用的三种方法：Heroku Git、GitHub 集成和容器注册表。它涵盖了为 GitHub Actions 创建工作流（YAML）文件的实际示例，包括使用 tox 和 pytest 测试代码，以及一个用于加快部署的自动化 Heroku 流水线。

## 第11章：在 Microsoft Azure 上部署 ML 模型
解释了使用 GitHub Actions 构建 CI/CD 流水线的逐步方法，将基于 Web 的 ML 应用部署到 Azure 云服务。在另一种方法中，读者将学习构建 CI/CD 流水线，并使用 Azure DevOps 和 Azure Machine Learning (AML) 服务将基于 Web 的可扩展 ML 应用部署到 Azure 容器实例 (ACI) 和 Azure Kubernetes 服务 (AKS)。

## 第12章：在 Google Cloud Platform 上部署 ML 模型
展示了如何构建自动化 CI/CD 流水线以在 Google Kubernetes Engine (GKE) 上部署 ML 模型，无需集成任何外部工具、服务或平台。本章使读者能够学习并实现 Kubernetes 功能，使用 Google Kubernetes Engine (GKE) 运行可扩展的 ML 应用。

## 第13章：在 Amazon Web Services 上部署 ML 模型
介绍了 Amazon Web Services (AWS) 提供的各种云计算服务的概览。本章使读者能够学习并实现带有持续训练 (CT) 的自动化 CI/CD 流水线，在 Amazon Elastic Container Service (ECS) 上部署可扩展的企业级 ML 应用。此外，它还涵盖了将应用负载均衡器 (ALB)、Amazon 虚拟私有云 (Amazon VPC) 和安全组集成到 Amazon Elastic Container Service (ECS) 中，以构建强大且安全的企业级 ML 应用。

## 第14章：监控与调试
专注于监控 ML 和运营指标，包括服务器、服务成本、ML 漂移、输入数据、ML 模型等更多内容。本章展示了 ML 生命周期中监控的重要性和基本概念。它还涵盖了使用 whylogs 和 WhyLabs 进行 ML 模型监控，以及使用 Prometheus 和 Grafana 进行运营监控的实际示例。

## 第15章：ML 模型生产后管理
详细概述了对抗机器学习，包括不同类型的对抗攻击及其缓解方法。它还涵盖了 A/B 测试的基本概念以及 MLOps 在行业中的未来前景。

## 代码包和彩色图片

请访问链接以下载本书的代码包和彩色图片：

https://rebrand.ly/vlv0nzp

本书的代码包也托管在 GitHub 上 https://github.com/bppublications/Machine-Learning-in-Production。如果代码有更新，将在现有的 GitHub 仓库中更新。

我们丰富的图书和视频目录的代码包可在 https://github.com/bppublications 上获取。请查看！

## 勘误

我们对 BPB Publications 的工作深感自豪，并遵循最佳实践以确保内容的准确性，为订阅者提供引人入胜的阅读体验。我们的读者是我们的镜子，我们会利用读者的反馈，反思并改进在出版过程中可能发生的人为错误（如有）。为了保持质量，并帮助我们联系到因任何不可预见的错误而遇到困难的读者，请写信至：

errata@bpbonline.com

BPB Publications 团队高度感谢您的支持、建议和反馈。

> 您知道吗？BPB 为每本出版的图书提供电子书版本，可供下载 PDF 和 ePub 文件。您可以在 www.bpbonline.com 升级到电子书版本，作为印刷书客户，您有权享受电子书副本的折扣。如需了解更多详情，请与我们联系：
> business@bpbonline.com
>
> 在 www.bpbonline.com 上，您还可以阅读一系列免费技术文章，订阅多种免费通讯，并获取 BPB 图书和电子书的独家折扣和优惠。

## 盗版

如果您在互联网上以任何形式发现我们作品的非法副本，我们将不胜感激，如果您能向我们提供位置地址或网站名称。请通过 business@bpbonline.com 联系我们，并附上材料的链接。

## 如果您有兴趣成为作者

如果您在某个主题上有专长，并有兴趣撰写或参与编写图书，请访问 www.bpbonline.com。我们已与成千上万的开发者和技术专业人士（如您一样）合作，帮助他们将见解分享给全球技术社区。您可以提交一般性申请，申请我们正在招募作者的特定热门主题，或提交您自己的创意。

## 评论

请留下评论。读完并使用本书后，为什么不在您购买该书的网站上留下评论呢？潜在读者随后可以查看并使用您公正的意见来做出购买决定。我们 BPB 可以了解您对我们产品的看法，我们的作者可以看到您对其书籍的反馈。谢谢！

如需了解有关 BPB 的更多信息，请访问 www.bpbonline.com。

## 加入本书的 Discord 空间

加入本书的 Discord 工作区，获取最新动态、优惠、全球技术动态、新版本发布以及与作者的交流会：

https://discord.bpbonline.com

![](img/cc4299656808e62a294f1843a1e18e72_12_0.png)

## Git + Hub = GitHub

## 常用 Git 工作流

## 安装 Git 并创建 GitHub 账户

### Linux (Debian/Ubuntu)

## Git 适用于所有平台

## GUI 客户端

## 创建 GitHub 账户

## 常用 Git 命令

### 设置

### 新建仓库

### 更新

### 更改

### 撤销

### 让我们开始使用 Git

### 配置

### 初始化 Git 仓库

### 检查 Git 状态

### 添加新文件

## 结论

## 要点回顾

## 选择题

## 答案

## 3. ML 模型部署中的挑战

### 简介

### 结构

### 目标

### ML 生命周期

### 业务影响

### 数据收集

### 数据准备

### 特征工程

### 构建和训练模型

### 测试和评估

### 模型部署

### 监控和优化

### 模型部署类型

### 批量预测

### Web 服务/REST API

### 移动端和边缘设备

### 实时

### 在生产环境中部署模型的挑战

### 团队协调

### 数据相关挑战

### 可移植性

### 可扩展性

### 鲁棒性

### 安全性

### MLOps

### MLOps 的优势

### ML 生命周期的高效管理

### 可重现性

### 自动化

### 跟踪与反馈循环

### 结论

### 要点回顾

### 选择题

### 答案

### 问题

### 关键术语

## 4. ML 模型打包

### 简介

### 结构

### 目标

### 虚拟环境

### 依赖文件

### ML 模型的序列化与反序列化

### 使用 pytest 测试 Python 代码

### pytest 测试夹具

### Python 打包与依赖管理

### 模块化编程

### 模块

### 包

### 开发、构建和部署 ML 包

### 业务问题

### 数据

### 构建 ML 模型

### 开发包

### 设置环境变量和路径

### 构建包

### 安装包

### 包的使用示例

### 结论

### 要点回顾

### 选择题

### 答案

### 问题

### 关键术语

## 5. MLflow：管理 ML 生命周期的平台

### 简介

### 结构

### 目标

### MLflow 简介

### 设置环境并安装 MLflow

### Miniconda 安装

### MLflow 组件

### MLflow 追踪

- 将数据记录到运行中

- MLflow 项目

- MLflow 模型

- MLflow 注册表

- 为 MLflow 设置 MySQL 服务器

- 启动 MLflow 服务器

### 结论

### 要点回顾

### 选择题

### 答案

### 问题

## 6. 适用于 ML 的 Docker

- 简介

- 结构

- 目标

- Docker 简介

- 它在我的机器上可以运行！

- 冗长的设置

- 设置环境并安装 Docker

- Docker 安装

- 卸载旧版本

- 安装 Docker Engine

- Docker Compose

- 使用 Docker 的 Hello World

- Docker 对象

- Dockerfile

- Docker 镜像

- Docker 容器

- Docker 容器网络

- 创建 Dockerfile

- 构建 Docker 镜像

- 运行 Docker 容器




- Docker 化并部署 ML 模型 122
- 常用 Docker 命令 127
- 总结 127
- 要点回顾 127
- 选择题 128
- 答案 128
- 问题 128

## 7. 使用 API 构建 ML Web 应用 129

- 简介 129
- 结构 129
- 目标 130
- REST API 130
- FastAPI 131
- Streamlit 139
- Flask 143
- Gunicorn 150
- NGINX 150
- 总结 154
- 要点回顾 154
- 选择题 155
- 答案 155

## 8. 构建原生 ML 应用 157

- 简介 157
- 结构 157
- 目标 158
- Tkinter 简介 158
- 使用 Tkinter 构建 Hello World 应用 159
- 使用 Tkinter 构建基于 ML 的应用 160
- Tkinter 应用 163
- 将 Python 应用转换为 Windows EXE 文件 167
- 使用 kivy 和 kivyMD 构建基于 ML 的应用 170
- KivyMD 应用 173
- 将 Python 应用转换为 Android 应用 179
- 总结 180
- 要点回顾 181
- 选择题 181
- 答案 181
- 问题 181

## 9. ML 的 CI/CD 183

- 简介 183
- 结构 183
- 目标 184
- ML 的 CI/CD 流水线 184
- 持续集成 (CI) 185
- 持续交付/部署 (CD) 186
- 持续训练 (CT) 186
- Jenkins 简介 187
- 安装 187
- 使用 GitHub、Docker 和 Jenkins 构建 CI/CD 流水线 189
- 开发代码库 189
- 在 GitHub 上创建个人访问令牌 (PAT) 196
- 在 GitHub 仓库上创建 Webhook 197
- 配置 Jenkins 199
- 使用 Jenkins 创建 CI/CD 流水线 202
- 阶段 1: 1-GitHub-to-container 203
- 阶段 2: 2-training 205
- 阶段 3: 3-testing 207
- 阶段 4: 4-deployment-status-email 210
- 总结 217
- 要点回顾 217
- 选择题 218
- 答案 218
- 问题 218

## 10. 在 Heroku 上部署 ML 模型 219

- 简介 219
- 结构 219
- 目标 220
- Heroku 220
- 设置 Heroku 221
- 使用 Heroku Git 部署 222
- 使用 GitHub 仓库集成进行部署 222
- 预览应用 223
- 预发布环境 223
- 生产环境 224
- Heroku 流水线流程 224
- 使用容器注册表进行部署 225
- GitHub Actions 225
- 配置 226
- 使用 GitHub Actions 和 Heroku 构建 CI/CD 流水线 227
- 总结 246
- 要点回顾 246
- 选择题 247
- 答案 247
- 问题 247

## 11. 在 Microsoft Azure 上部署 ML 模型 249

- 简介 249
- 结构 249
- 目标 250
- Azure 250
- 设置 Azure 账户 251
- 使用 GitHub Actions 进行部署 251
- 基础设施设置 263
- Azure 容器注册表 263
- Azure 应用服务 267
- GitHub Actions 270
- 服务主体 273
- 配置 Azure 应用服务以使用 GitHub Actions 进行 CD 274
- 使用 Azure DevOps 和 Azure ML 进行部署 278
- Azure 机器学习 (AML) 服务 279
- 工作区 280
- 实验 280
- 运行 280
- 配置 CI 流水线 290
- 配置 CD 流水线 292
- 总结 299
- 要点回顾 299
- 选择题 299
- 答案 300
- 问题 300

## 12. 在 Google Cloud Platform 上部署 ML 模型 301

- 简介 301
- 结构 301
- 目标 302
- Google Cloud Platform (GCP) 302
- 设置 GCP 账户 303
- Cloud Source Repositories 304
- Cloud Build 309
- 容器注册表 311
- Kubernetes 312
- Google Kubernetes Engine (GKE) 313
- 使用 Cloud Shell 进行部署 – 手动触发 316
- 使用 Cloud Build 构建 CI/CD 流水线 317
- 在 Cloud Build 中创建触发器 318
- 总结 323
- 要点回顾 323
- 选择题 323
- 答案 324




### 问题 324

## 13. 在 Amazon Web Services 上部署 ML 模型 325

### 简介 325

### 结构 325

### 目标 326

### Amazon Web Services (AWS) 简介 326

### AWS 计算服务 326

### Amazon Elastic Compute Cloud (EC2) 327

### Amazon Elastic Container Service (ECS) 327

### Amazon Elastic Kubernetes Service (EKS) 327

### Amazon Elastic Container Registry (ECR) 327

### AWS Fargate 328

### AWS Lambda 328

### Amazon SageMaker 328

### 设置 AWS 账户 329

### AWS CodeCommit 331

### 持续训练 336

### Amazon Elastic Container Registry (ECR) 336

### Docker Hub 速率限制 337

### AWS CodeBuild 339

### 将容器注册表访问权限附加到 CodeBuild 的服务角色 345

### Amazon Elastic Container Service (ECS) 346

### AWS ECS 部署模型 347

### EC2 实例 347

### Fargate 348

### 任务定义 349

### 使用任务定义运行任务 350

### Amazon VPC 和子网 351

### 负载均衡 352

### 目标组 353

### 安全组 356

### 应用负载均衡器 (ALB) 358

### 服务 363

### 使用 CodePipeline 的 CI/CD 管道 369

### AWS CodePipeline 371

### 监控 378

### 结论 379

### 要点 379

### 选择题 380

### 答案 380

### 问题 380

## 14. 监控和调试 381

### 简介 381

### 结构 381

### 目标 382

### 监控的重要性 382

### ML 监控基础 383

### 监控 ML 系统的指标 385

### ML 中的漂移 386

### ML 中的漂移类型 386

### 检测 ML 中漂移的技术 388

### 解决 ML 中的漂移 389

### 使用 Prometheus 和 Grafana 进行运营监控 390

### 使用 whylogs 和 WhyLabs 进行 ML 模型监控 402

### whylogs 403

### 数据质量验证的约束 404

### WhyLabs 407

### 结论 416

### 要点 416

### 选择题 417

### 答案 417

### 问题 417

## 15. 部署后的 ML 模型

### 简介

### 结构

### 目标

### 连接 ML 模型与业务价值创造之间的差距

### 模型安全

### 对抗攻击

### 数据投毒攻击

### 分布式拒绝服务攻击 (DDoS)

### 数据隐私攻击

### 降低模型攻击风险

### A/B 测试

### MLOps 是未来

### 结论

### 要点

### 选择题

### 答案

### 问题

### 索引

## 第 1 章 Python 101

### 简介

Python 101 将指导你从 Python 安装到 Pandas DataFrame 中的数据操作。简而言之，本章旨在为你提供本书所需的先决条件。对于曾使用过 Python 的人来说，这是一个快速复习。如果你是初学者，本章将涵盖构建和部署机器学习模型所需的最常用 Python 命令。

### 结构

- 本章涵盖以下主题：
- Python 安装
- Hello World!
- 数据结构
- 控制语句和循环
- 函数
- 面向对象编程
- NumPy
- Pandas

### 目标

学习本章后，你应该能够在自己的机器上安装 Python，并使用 Python 中的常见数据结构来存储和管理数据。你应该能够使用 Python 的数据处理包进行数据操作，并且还应该知道如何创建类、方法和对象。

### 安装 Python

确保你安装的 Python 版本与你将要使用的库和应用程序兼容。此外，在整个项目中保持相同的 Python 版本，以避免任何错误或异常。在此，你将安装 Python 3.6.10 版本。

### 在 Windows 和 Mac OS 上

这是安装 Python 3.6.10 的链接：

https://www.python.org/downloads/release/python-3610/

### 在 Linux 上

Ubuntu 16.10 和 17.04：

```
sudo apt update
```

```
sudo apt install python3.6
```

Ubuntu 17.10、18.04（Bionic）及更高版本：

Ubuntu 17.10 和 18.04 已默认自带 Python 3.6。只需在终端中运行 python3 即可调用它。

### 安装 Anaconda

Anaconda 个人版包含 conda 和 Anaconda Navigator，以及 Python 和数百个科学软件包。安装 Anaconda 时，所有这些也会随之安装。

https://docs.anaconda.com/anaconda/install/

> 注意：在安装 Anaconda 个人版之前，请查看网站上列出的系统要求。





## 安装代码编辑器

可以选择以下任意一种代码编辑器；不过，首选的是 Visual Studio Code：

Visual Studio Code (https://code.visualstudio.com)

Sublime Text (https://www.sublimetext.com)

Notepad++ (https://notepad-plus-plus.org/downloads/)

## Hello World！

Python 是一种具有动态语义的解释型、面向对象的高级编程语言。其简单易学的语法强调可读性，从而降低了程序维护成本。Python 支持模块和包，鼓励模块化编程和代码重用。它是在 OSI 批准的开源许可证下开发的，可免费用于分发，甚至可用于商业用途。Python 软件包索引 (PyPI) 为 Python 托管了数千个第三方模块。

打开终端并键入 python 以打开 Python 控制台。

现在你已在 Python 控制台中。

### 示例：1.1 Python 中的 Hello world

```
1. print("Hello World")
2. Hello World
```

要退出控制台，可以使用：

```
1. exit()
```

## 执行 Python 文件

让我们创建一个名为 hello_world.py 的文件，并将 print("Hello World") 添加到其中。

现在，在终端中运行该文件：

```
python hello_world.py
```

你应得到以下输出：

Hello World

## 数据结构

数据结构无非是将数据以特定方式存储在内存中并进行管理，以便以后能够轻松访问和修改。Python 自带一套全面的数据结构，它们在编程中起着重要作用，因为这些结构可重用、易于访问且易于管理。

### 常见数据结构

本节将学习一些常见的数据结构。

### 数组

数组是同类项的集合。在单个数组中可以使用相同的数据类型。

### 示例：1.2 数组数据类型

```
1. import array as arr
2.
3. my_array = arr.array("i", (1, 2, 3, 4, 5))
4.
5. print(my_array)
6. array('i', [1, 2, 3, 4, 5])
7.
8. print(my_array[1])
9. 2
```

### 字典

字典定义为用逗号分隔的 **键:值** 对，并用花括号括起来。

### 示例：1.3 字典数据类型

```
1. my_dict = {'name': 'Adam', 'emp_id': 3521, 'dept': 'Marketing'}
2. print(my_dict['name'])
3. Adam
```

### 列表

它是用方括号括起来的异构项集合。在列表中可以使用相同或不同的数据类型。

### 示例：1.4 列表数据类型

```
1. my_list=['apple', 4, 'banana', 6]
2. print(my_list[0])
3. apple
```

### 集合

集合是用花括号括起来的唯一（非重复）元素集合。集合可以包含异构元素。

### 示例：1.5 集合数据类型

```
1. my_set = {3,5,6}
2. print(my_set)
3. {3, 5, 6}
```

```
1. my_set = {1, 2.0, (3,5,6), 'Test'}
2. print(my_set)
3. {1, 2.0, 'Test', (3, 5, 6)}
```

### 字符串

字符串用于存储文本数据。它可以用单引号 ('') 或双引号 ("") 表示。

### 示例：1.6 字符串数据类型

```
1. print('The cat was chasing the mouse')
2. The cat was chasing the mouse
```

### 元组

元组是用圆括号（可选）包围的元素集合，且是不可变的，即无法更改。

### 示例：1.7 元组数据类型

```
1. my_tuple_1 = ('apple', 4, 'banana', 6)
2. print(my_tuple_1[0])
3. apple
```

元组可以在没有圆括号的情况下声明，如下所示：

```
1. my_tuple_2 = 1, 2.0, (3,5,6), 'Test'
2. print(my_tuple_2[0])
3. 1
```

## 控制语句和循环

Python 有几种控制语句和循环。让我们来看看它们。

### if...else

if 语句在指定条件为真时执行一段代码。而 else 语句在指定条件为假时执行一段代码。此外，如果第一个条件为假，可以使用 elif（else if）语句来检查新条件。

语法：

```
if condition1:
    Code to be executed
elif condition2:
    Code to be executed
else:
    Code to be executed
```

### 示例：1.8 if...else 控制语句

```
1. x = 26
2. y = 17
3.
4. if(x > y):
5.     print('x is greater than y')
6. elif(x == y):
7.     print('x and y are equal')
8. else:
9.     print('y is greater than x')
10.
11.x is greater than y
```

### for 循环

当你想遍历字符串、列表、字典或元组等序列或可迭代对象时使用它。它会执行一定次数的代码块。

语法：

```
for val in sequence:
Code to be executed
```

### 示例：1.9 for 循环

```
1. num = 2
2. for i in range(1, 11):
3.     print(num, 'X', i, '=', num*i)
4.
5. 2 X 1 = 2
6. 2 X 2 = 4
7. 2 X 3 = 6
8. 2 X 4 = 8
9. 2 X 5 = 10
10. 2 X 6 = 12
11. 2 X 7 = 14
12. 2 X 8 = 16
13. 2 X 9 = 18
14. 2 X 10 = 20
```

在前面的示例中，range() 函数使用 start、stop 和 step 参数生成一组连续的数字。

### while 循环

当你想无限期执行一段代码直到满足指定条件时使用它。此外，如果第一个条件为假，可以使用 else 语句执行一次代码块。

语法：

```
while condition:
Code to be executed
```

### 示例：1.10 while 循环

```
1. num = 1
2. while num <= 10:
3.     if num % 2 == 0:
4.         print(num)
5.     num = num + 1
6.
7. 2
8. 4
9. 6
10. 8
11. 10
```

## pass 语句

在 Python 中，pass 语句充当占位符。如果你计划在循环、函数定义、类定义或 if 语句中稍后添加代码，可以编写 pass 以避免任何错误，因为它什么也不做。它允许开发人员稍后编写逻辑或条件，并继续执行剩余代码。

语法：

```
if condition:
pass
```

### 示例：1.11 pass 语句

```
1. num = 10
2. if num % 2 == 0:
3.     pass
```

## 函数

开发人员使用函数来多次执行相同的任务。函数是一段可以接受参数、执行某些操作并返回值的代码。Python 使开发人员能够使用预定义或内置函数，也可以编写用户定义的函数来执行特定任务。

### 示例：1.12 预定义或内置函数

```
1. print("Hello World")
2. Hello World # Output
```

### 示例：1.13 用户定义函数

```
1. a = 5
2. b = 2
3.
4. # Function definition
5. def add():
6.     print(a+b)
7.
8. # Calling a function
9. add()
10.
11. # Output
12. 7
```

## 面向对象编程 (OOP)

Python 是一门面向对象的语言，因此 Python 中的一切都是对象。让我们来理解其关键概念及其重要性：

**类：** 类充当对象的模板。它使用 **class** 关键字定义，就像在创建新函数时使用 **def** 关键字一样。Python 类包含对象和方法，可以使用句点 (.) 访问它们。

**对象：** 对象是类的实例。它描述了类的结构，包含类变量、实例变量和方法。

**方法：** 简单来说，它是在创建类时定义的函数。

**__init__：** 为了通过赋值自动初始化数据成员，在创建类的实例时应使用 **__init__** 方法。每次创建类的对象时都会调用它。其用法等同于 C++ 和 Java 中的构造函数。

**self：** 它帮助我们访问类的方法和属性。你可以随意命名；但根据惯例和可读性，最好将其声明为 self。

### 示例：1.14 类定义

```
1. class Multiply:
2.     def mul(self):
3.         result = self.num1 * self.num2       Class definition
4.         return result
5.
6.     def __init__(self,num1,num2):
7.         self.num1 = num1
8.         self.num2 = num2
9.
10.   a = Multiply(5,6)
11.             Passing parameters to class
12.   a.mul()            Calling method of class
13.   30
```

> 注意：遵循变量、函数和方法的标准命名约定。例如：
> * 对于变量、函数、方法、包和模块：my_variable
> * 对于类和异常：MyClass
> * 对于常量：MY_CONSTANT

## 数值 Python (NumPy)

简单来说，它是一个数组处理包。NumPy 是 Numerical Python 的缩写。默认情况下，NumPy 数组的数据类型由其元素定义。在 NumPy 中，数组的维度称为秩；例如，2-D 数组表示秩为 2 的数组。

NumPy 因其速度而广受欢迎。在处理大型数据集时，使用 NumPy 会体会到其中的差别。

你可以使用 pip 安装 NumPy 包：

```
pip install numpy
```

### 示例：1.15 NumPy 数组

```
1. import numpy as np
2. # Rank 0 Array (scalar)
3. my_narray = np.array(42)
4. print(my_narray)
5. 42
6.
7. print("Dimension: ", my_narray.ndim)
8. Dimension: 0
9.
10.   print("Shape: ", my_narray.shape)
11.   Shape: ()
12.
```




```python
13.     print("Size: ", my_narray.size)
14.     Size: 1
```

```python
1. # Rank 1 Array (vector)
2. my_narray = np.array([4,5,6])
3. print(my_narray)
4. [4 5 6]
5. print("Dimension: ", my_narray.ndim)
6. Dimension: 1
7. print("Shape: ", my_narray.shape)
8. Shape: (3,)
9. print("Size: ", my_narray.size)
10.     Size: 3
```

```python
1. # Rank 2 Array (matrix)
2. my_narray = np.array([[1,2,3],[4,5,6]])
3. print(my_narray)
4. [[1 2 3]
5.  [4 5 6]]
6. print("Dimension: ", my_narray.ndim)
7. Dimension: 2
8. print("Shape: ", my_narray.shape)
9. Shape: (2, 3)
10.     print("Size: ", my_narray.size)
11.     Size: 6
```

```python
1. # Rank 3 Array
2. my_narray = np.array([[[1,2,3],[4,5,6]],[[7,8,9],[10,11,12]]])
3. print(my_narray)
4. [[[ 1 2 3]
5.   [ 4 5 6]]
6.  [[ 7 8 9]
7.  [10 11 12]]]
8. print("Dimension: ", my_narray.ndim)
9. Dimension: 3
10.     print("Shape: ", my_narray.shape)
11.     Shape: (2, 2, 3)
12. print("Size: ", my_narray.size)
13. Size: 12
```

## 重塑数组

假设你想在不丢失数据的情况下更改 ndarray（N 维数组）的形状，可以使用 reshape() 或 flatten() 方法来完成。

### 示例：1.16 重塑 NumPy 数组

```python
1. # Rank 1 Array
2. my_1array = np.array([1,2,3,4,5,6])
3. print(my_1array)
4. [1 2 3 4 5 6]
```

```python
1. # converting Rank 1 array to Rank 2 array
2. my_2array = my_1array.reshape(2, 3)
3. print(my_2array)
4. [[1 2 3]
5. [4 5 6]]
```

```python
1. #converting Rank 2 array to Rank 1 array
2. my_1array = my_2array.flatten()
3. print(my_1array)
4. [1 2 3 4 5 6]
```

> 注意：在此，你可以使用 my_2array.reshape(6) 代替 flatten()。

## Pandas

Pandas 是一个开源的、BSD 许可的库，为 Python 编程语言提供高性能、易于使用的数据结构和数据分析工具。DataFrame 是一个二维标记数据结构，其列可能具有不同的类型。

你可以使用 pip 安装 Pandas 包：

```bash
pip install pandas
```

### 示例：1.17 Pandas DataFrame 用法

```python
1. import pandas as pd
2. df = pd.DataFrame(data={'fruit': ['apple', 'banana', 'orange',
3.       'mango',
4.       'size': ['large', 'medium', 'small',
5.       'medium']],
6.       'quantity': [5,4,8, 6]})
7.
8. print(df)
```

| 水果    | 大小    | 数量     |
|---------|---------|----------|
| 苹果    | 大      | 5        |
| 香蕉    | 中等    | 4        |
| 橙子    | 小      | 8        |
| 芒果    | 中等    | 6        |

在以下示例中，head() 检索 Pandas DataFrame 的顶部行。

### 示例：1.18 获取 DataFrame 的前 n 行

```python
1. df.head(2)
```

| 水果    | 大小    | 数量     |
|---------|---------|----------|
| 苹果    | 大      | 5        |
| 香蕉    | 中等    | 4        |

而 tail() 检索 Pandas DataFrame 的底部行。

### 示例：1.19 获取 DataFrame 的最后 n 行

```python
1. df.tail(2)
```

| 水果    | 大小    | 数量     |
|---------|---------|----------|
| 橙子    | 小      | 8        |
| 芒果    | 中等    | 6        |

在以下示例中，describe() 显示 DataFrame 数值列的快速统计摘要。

### 示例：1.20 获取基本统计信息

```python
1. df.describe()
```

| | 数量 |
|---|----------|
| 计数 | 4.000000 |
| 平均值 | 5.750000 |
| 标准差 | 1.707825 |
| 最小值 | 4.000000 |
| 25% | 4.750000 |
| 50% | 5.500000 |
| 75% | 6.500000 |
| 最大值 | 8.000000 |

```python
1. df['fruit']
2. 0 apple
3. 1 banana
4. 2 orange
5. 3 mango
6. Name: fruit, dtype: object
```

## loc - 按标签选择

loc 用于获取具有特定标签的行（和/或列）。要获取所有水果大小为中等的行，loc 的写法如下：

### 示例：1.21 按位置获取数据

```python
1. df.loc[df['size'] == 'medium']
```

| 水果    | 大小    | 数量     |
|---------|---------|----------|
| 香蕉    | 中等    | 4        |
| 芒果    | 中等    | 6        |

## iloc - 按位置选择

iloc 用于获取索引位置处的行（和/或列）。要获取索引为 2 的行，iloc 的写法如下：

### 示例：1.22 按位置获取数据

```python
1. df.iloc[2]
2. fruit orange
3. size small
4. quantity 8
5. Name: 2, dtype: object
```

要检索从索引 2 到 3 和列 0 到 1 的行，iloc 的写法如下：

```python
1. df.iloc[2:4, 0:2]
```

| 水果    | 大小    |
|---------|---------|
| 橙子    | 小      |
| 芒果    | 中等    |

你可以调用 groupby() 并传递 size，即要对其进行分组的列，然后使用 sum() 聚合方法。

### 示例：1.23 对数据分组，然后使用聚合函数

```python
1. df.groupby(['size'])['quantity'].sum()
```

| 大小   | 数量 |
|--------|------|
| 大     | 5    |
| 中等   | 10   |
| 小     | 8    |

名称：数量，数据类型：int64

## 保存和加载 CSV 文件

### 示例：1.24 保存和加载 CSV 文件

```python
1. df.to_csv("fruit.csv")
2. df = pd.read_csv("fruit.csv")
```

## 保存和加载 Excel 文件

### 示例：1.25 保存和加载 Excel 文件

```python
1. df.to_excel("fruit.xlsx", sheet_name="Sheet1")
2. df = pd.read_excel("fruit.xlsx", "Sheet1", index_col=None)
```

有关更多信息，可以参考 https://pandas.pydata.org/docs/ 上的官方文档。

## 结论

本章通过示例讨论了 Python 语言的基本概念。在本章开头，你学习了如何在系统中安装 Python。随后，你通过示例学习了 Python 中的常见数据结构和面向对象编程概念。接着，使用 NumPy 和 Pandas 等包介绍了数据预处理命令，这些命令在开发机器学习模型中将发挥重要作用。

在下一章中，你将通过示例学习 git 和 GitHub。

## 要点

- 确保在整个机器学习项目中使用相同的 Python 版本。
- 类中的 __init__() 方法用于自动初始化数据成员和方法。但是，这不是强制性的。
- 元组是不可变的，即它们不可更改，但如果它们包含类似列表的元素，那么列表是可变的，而整个元组则不是。

## 选择题

- 1. np.array([[1,2,3],[4,5,6]]) 的输出是什么？
- a) 秩 1 数组
- b) 秩 2 数组
- c) 秩 3 数组
- d) 以上皆是

- 2. 集合可以包含 _______ 元素。
- a) 异质
- b) 同质
- c) 仅整数
- d) 仅字符串

## 答案

- 1. b
- 2. a

## 问题

- 1. 列表和元组有什么区别？
- 2. __init__() 的用途是什么？
- 3. 何时应该使用 pass 语句？

## 关键术语

**面向对象编程**：它是一种基于对象概念的编程范式，对象可以包含数据和方法。

## 加入我们的图书 Discord 空间

加入图书的 Discord 工作区，获取最新动态、优惠、全球技术动态、新版本发布以及与作者的交流会议：

https://discord.bpbonline.com

![](img/cc4299656808e62a294f1843a1e18e72_40_0.png)

## 第 2 章 Git 和 GitHub 基础

### 简介

在团队中工作时，维护文件的多个版本很困难。Git 通过允许开发人员与其他团队成员协作和共享文件来解决这个问题。本章介绍了构成本书基础的最基本 Git 和 GitHub 概念。它解释了 Git 配置、分叉 Git 仓库、将代码库推送到 GitHub 以及克隆过程。此外，还介绍了 GitHub Actions、常用 Git 命令及其语法和示例。在团队中工作时，维护文件的多个版本可能很困难，但 Git 是解决方案。

### 结构

本章将涵盖以下主题：

- Git 概念
- 常用 Git 工作流
- 安装 Git 并创建 GitHub 帐户
- 常用 Git 命令
- 让我们开始使用 Git

### 目标

学习本章后，你应该知道如何执行 Git 命令并连接到远程 GitHub 仓库。理解并执行 Git 流程。你应该知道如何将更改推送、获取和恢复到远程 Git 仓库，并且你应该熟悉如何在你的计算机或服务器上安装和执行 Git 的基本配置。

### Git 概念

Git 是一种开源的分布式版本控制系统（DVCS）。版本控制系统允许你记录一段时间内对文件的更改。

Git 用于维护源代码的历史版本和当前版本。在项目中，开发人员拥有存储在中央服务器上的所有代码版本的副本。

Git 允许开发人员执行以下操作：

- 跟踪更改、谁进行了更改以及何时进行更改
- 回滚/恢复更改
- 允许多个开发人员协调并在同一文件上工作
- 在远程和本地级别维护文件副本

下图描绘了 Git 作为团队中的 VCS，开发人员可以同时在同一文件上工作并跟踪谁进行了更改。这里，F1、F2 和 F3 是文件名。

![](img/cc4299656808e62a294f1843a1e18e72_42_0.png)

图 2.1：团队中的 Git 场景





## Git + Hub = GitHub

Git 和 GitHub 是两个独立的实体。Git 是命令行工具，而 GitHub 是协作平台。你可以在 GitHub 上存储文件和文件夹，并对现有项目进行更改。通过创建独立分支，可以将这些更改与现有项目文件隔离开来。

GitHub Actions 可让你使用持续集成/持续部署轻松自动化所有软件工作流。你可以直接从 GitHub 构建、测试和部署代码。

## 常见 Git 工作流

下图描绘了通用 Git 工作流。它涵盖创建或克隆 Git 仓库、从远程仓库拉取文件以更新本地仓库，以及将本地更改推送到远程仓库等操作。

![](img/cc4299656808e62a294f1843a1e18e72_43_0.png)

图 2.2：Git 工作流

## 安装 Git 并创建 GitHub 账号

首先，你需要安装 Git，然后在 GitHub 上创建账号。要在你的机器上安装 Git，请按照给定的说明操作。

### Linux (Debian/Ubuntu)

在 Ubuntu 中，打开终端并使用以下命令安装 Git：

```
$ sudo apt-get update
$ sudo apt-get install git
```

### 适用于所有平台的 Git

从官方网站下载适用于你机器的 Git：

https://git-scm.com/downloads

### GUI 客户端

Git 自带内置 GUI 工具；不过，你可以在 https://git-scm.com/downloads/guis 上探索其他第三方 GUI 工具。

点击适用于你操作系统的下载链接，然后按照安装步骤操作。

安装后，启动终端并输入 `git --version` 以验证 Git 安装情况。

如果一切顺利，你将看到 Git 已成功安装。

### 创建 GitHub 账号

如果你是 GitHub 新手，可以在 https://github.com/join 加入 GitHub。

如果你是现有用户，请登录你的账号。

点击右上角的加号 + 来创建新仓库：

![](img/cc4299656808e62a294f1843a1e18e72_44_0.png)

图 2.3：在 GitHub 上创建新仓库

点击**创建仓库**按钮。填写必填字段，你的 Git 仓库将被创建。

你可以从 https://desktop.github.com/ 下载并安装 GitHub 桌面版。

## 常见 Git 命令

本节将讨论一些常见的 Git 命令。

### 设置

设置一个在审查版本历史记录时可用于归属的识别名称：

```
git config --global user.name "[firstname lastname]"
```

设置一个将与每个历史记录标记关联的电子邮件地址：

```
git config --global user.email "[valid-email-id]"
```

### 新建仓库

将现有目录初始化为 Git 仓库：

```
git init
```

通过 URL 从托管位置检索整个仓库：

```
git clone [url]
```

### 更新

获取并合并来自远程分支的任何提交：

```
git pull
```

获取远程 Git 仓库中的所有分支：

```
git fetch [alias]
```

### 更改

查看工作目录中为下一次提交暂存的已修改文件：

```
git status
```

将文件添加到下一次提交中（暂存）：

```
git add [file]
```

将你暂存的内容作为新的提交快照进行提交：

```
git commit -m "[descriptive message]"
```

将本地分支提交传输到远程仓库分支：

```
git push [alias] [branch]
```

## 回退

查看当前分支历史记录中的所有提交：

```
git log
```

切换到另一个分支：

```
git checkout [branch_name]
```

## 让我们开始使用 Git

创建一个名为 code 的新目录并切换到 code 目录：

```
suhas@test:~/code$ sudo chmod -R 777 /home/suhas/code
```

### 配置

提供用户名和用户的电子邮件：

```
suhas@test:~/code$ git config --global user.name "Suhas"
```

```
suhas@test:~/code$ git config --global user.email "suhasp.ds@gmail.com"
```

> 注意：始终阅读命令的输出，以了解后台发生了什么。

### 初始化 Git 仓库

```
suhas@test:~/code$ git init
```

```
Initialized empty Git repository in /home/suhas/code/.git/
```

### 检查 Git 状态

```
suhas@test:~/code$ git status
```

在 master 分支上

暂无提交

无需提交（创建/复制文件并使用 "git add" 进行跟踪）

### 添加新文件

已使用 touch 命令添加了新文件 hello.py：

```
suhas@test:~/code$ touch hello.py
```

你可以在 git status 的输出中注意到变化：

```
suhas@test:~/code$ git status
On branch master
No commits yet
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        hello.py
nothing added to commit but untracked files present (use "git add" to track)
```

将 hello.py 文件添加到暂存区：

```
suhas@test:~/code$ git add hello.py
```

再次检查 Git 状态的输出：

```
suhas@test:~/code$ git status
On branch master
No commits yet
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   hello.py
```

使用消息 "New file" 进行提交：

```
suhas@test:~/code$ git commit -m "New file"
[master (root-commit) bd49a5e] New file
1 file changed, 0 insertions(+), 0 deletions(-)
create mode 100755 hello.py
```

检查 Git 状态的输出：

```
suhas@test:~/code$ git status
On branch master
nothing to commit, working tree clean
```

使用 nano 命令更新 hello.py 文件：

```
suhas@test:~/code$ sudo nano hello.py
```

现在，将 print ("Hello World!") 添加到 hello.py 文件中。

你可以在 git status 的输出中看到更改：

```
suhas@test:~/code$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)
        modified:   hello.py
no changes added to commit (use "git add" and/or "git commit -a")
```

将 hello.py 文件添加到暂存区：

```
suhas@test:~/code$ git add hello.py
```

随消息 "added print text" 一起提交：

```
suhas@test:~/code$ git commit -m "added print text"
[master af7cfeb] added print text
 1 file changed, 1 insertion(+)
```

使用 git log 命令查看日志：

```
suhas@test:~/code$ git log
commit af7cfeb53ff6dc49126d24aedb20a065c54ef4a0 (HEAD -> master)
Author: "Suhas Pote" <"suhasp.ds@gmail.com">
Date:   Sun Jul 5 21:34:15 2020 +0530
    added print text
commit bd49a5e5280de35811848a80299d900e6e6509ce
Author: "Suhas Pote" <"suhasp.ds@gmail.com">
Date:   Sun Jul 5 21:26:12 2020 +0530
    New file
```

Git 使用基于提交文件内容的 SHA1 哈希函数唯一标识每个提交。因此，每个提交都由一个 40 字符长的十六进制字符串标识。

```
suhas@test:~/code$ git checkout af7cfeb53ff6dc49126d24aedb20a065c54ef4a0
Note: checking out 'bd49a5e5280de35811848a80299d900e6e6509ce'.
```

你处于“分离的 HEAD”状态。你可以四处查看、进行实验性更改并提交它们，并且可以通过再次执行 checkout 来丢弃在此状态下所做的任何提交，而不会影响任何分支。

如果你想创建新分支以保留所创建的提交，可以立即或稍后再次使用 checkout 命令的 -b 选项。示例：

```
git checkout -b <new-branch-name>
```

```
HEAD is now at bd49a5e New file
```

如果你注意到，hello.py 文件已回到之前的状态，即一个空白文件。这就像一台时光机！

现在，让我们回到 hello.py 的最新版本。

```
suhas@test:~/code$ git reset --hard af7cfeb53ff6dc49126d24aaedb20a065c54ef4a0
HEAD is now at af7cfeb added print text
```

是时候将文件推送到 GitHub 仓库了。

```
suhas@test:~/code$ git remote add origin https://github.com/suhas-ds/myrepo.git
suhas@test:~/code$ git push -u origin master
Username for 'https://github.com': suhas-ds
Password for 'https://suhas-ds@github.com':
Counting objects: 6, done.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (6/6), 477 bytes | 477.00 KiB/s, done.
Total 6 (delta 0), reused 0 (delta 0)
To https://github.com/suhas-ds/myrepo
* [new branch]      master -> master
Branch 'master' is set up to track remote branch 'master' from 'origin'.
```

> 注意：在这里，origin 作为 URL 的别名或标签，而 master 是分支名称。

要拉取文件的最新版本，请执行以下命令。

```
suhas@test:~/code$ git pull origin master
From https://github.com/suhas-ds/myrepo
* branch            master    -> FETCH_HEAD
Already up to date.
```



如果你想从另一个 GitHub 仓库加载文件，或者你正在另一个系统上工作并想从自己的 GitHub 仓库加载文件，可以通过克隆它来实现。

```
suhas@test:~/myrepo$ git clone https://github.com/suhas-ds/myrepo.git
Cloning into 'myrepo'...
remote: Enumerating objects: 6, done.
remote: Counting objects: 100% (6/6), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 6 (delta 0), reused 6 (delta 0), pack-reused 0
Unpacking objects: 100% (6/6), done.
```

你可以使用更多文件和 Git 仓库来练习常用的 Git 命令。

## 结论

在本章中，你探索了 Git 和 GitHub，并学习了基本的 Git 命令，例如 `git commit` 和 `git push`。随后，你安装并配置了 Git，并从远程 GitHub 仓库推送和克隆了文件。要使用 GitHub 平台，了解 Git 工作流至关重要。

在下一章中，你将了解在生产环境中部署机器学习模型时面临的挑战，并了解如何克服这些挑战。

## 要点总结

- Git 使用 SHA1 哈希函数根据提交文件的内容唯一标识每个提交。
- Git 是一个命令行工具，而 GitHub 是一个协作平台。
- Git 用于维护源代码的历史版本和当前版本。

## 选择题

- 1. ____ 命令显示当前分支历史中的所有提交。
  - a) git checkout
  - b) git push [alias] [branch]
  - c) git log
  - d) git pull

- 2. 以下哪项陈述不适用于 Git？
  - a) 追踪谁创建/做了哪些更改以及何时更改
  - b) 回滚/恢复更改
  - c) 允许多个开发者协调并在同一文件上工作
  - d) 不在远程和本地仓库中保存文件副本

## 答案

- 1. c
- 2. d

## 问题

- 1. 什么是 Git？什么是 GitHub？
- 2. 上传更改到远程仓库的命令是什么？
- 3. 如何回滚/恢复更改？
- 4. 如何初始化一个新仓库？
- 5. Git status 命令的用途是什么？

## 加入本书的 Discord 空间

加入本书的 Discord 工作区，获取最新动态、优惠、全球技术动态、新版本发布以及与作者的会议：

https://discord.bpbonline.com

![](img/cc4299656808e62a294f1843a1e18e72_51_0.png)

## 第 3 章 机器学习模型部署中的挑战

### 引言

一项研究发现，87% 的数据科学和机器学习项目从未投入生产。在本章中，你将研究在部署机器学习模型时可能面临的常见问题。

部署 ML 模型完全取决于你的最终目标，例如预测频率、延迟、用户数量、单次或批量预测以及可访问性。

### 结构

- 本章涵盖以下主题：
- ML 生命周期
- 模型部署类型
- 部署模型时的挑战
- MLOps
- MLOps 的优势

### 目标

本章将介绍在生产环境中部署 ML 模型的各种方法。学习本章后，你应该能够使用 MLOps 克服手动部署 ML 模型中的挑战。你还将在本章中学习 ML 生命周期的不同阶段。

### ML 生命周期

机器学习生命周期是一个周期性过程。它从业务问题开始，最后一个阶段是监控和优化。然而，这并不那么简单直接。例如，如果业务需求发生变更，你可能需要重新执行 ML 生命周期的所有阶段。在某些场景中，你可能需要回到 ML 生命周期的先前阶段，以满足特定阶段的标准。例如，如果模型准确率低于阈值，你需要重新审视先前阶段以提高准确率。这可以通过添加新特性、优化模型参数等方式实现。

下图展示了 ML 生命周期的不同阶段。

![](img/cc4299656808e62a294f1843a1e18e72_54_0.png)

图 3.1: ML 生命周期

### 业务影响

第一个也是最重要的阶段是定义一个想法及其对项目的影响。在不考虑业务影响、复杂性、预期结果和所需时间的情况下启动项目，可能导致交付延迟、重复工作以及资源利用率低下。

业务影响可以是任何事情，例如收入增加、支出减少或减少人为错误。需要了解业务痛点，并尝试评估拥有一个可解决多个业务问题的 ML 解决方案的可能性。在某些场景中，快速获得结果更为重要。

### 数据收集

数据收集是从一个或多个来源收集数据的过程。虽然看起来容易，但实际上并非如此。在收集数据之前，你需要回答以下问题：

- 需要收集什么数据？
- 数据的不同来源有哪些？
- 数据类型是什么？
- 数据大小是多少？

在现实世界中，你可能需要从不同来源收集数据，例如关系型数据库、NoSQL 数据库、网络等。为了避免任何故障或延迟，你必须构建数据收集管道。

为了获得更好的结果，你可以将可用数据与外部数据结合，例如社交媒体网站、天气数据和公共数据。

以下是几种收集数据的方式：

- 电子调查
- 授权的网络爬虫工具
- 点击数据
- 社交媒体平台
- 网站追踪
- 订阅/注册数据
- 图像数据 - CCTV/摄像头
- 语音数据 - 客户服务

与客户/利益相关者和领域专家安排会议以了解数据。他们将帮助你理解数据，以便你可以决定哪些数据需要用于模型构建。

### 挑战：

- 数据分散在不同位置
- 数据缺乏一致性
- 结合来自不同来源的数据
- 3Vs：数据量、速度、多样性
- 数据存储

### 数据准备

收集的数据通常是原始格式。需要对其进行处理，以便可用于进一步分析和模型开发。这种清洗、重构和标准化的过程称为数据准备。

大约 70%-80% 的时间用于 ML 项目的这一阶段。这是一项乏味的任务，但无法避免。当需要处理大量数据时，会使用数据缩减技术。

数据准备旨在将原始数据转换为一种格式，以便可以高效地执行 EDA（即探索性数据分析）以获得洞察。

### 挑战：

- 缺失值
- 异常值
- 不同的数据格式
- 数据标准化
- 数据中的噪声

### 特征工程

在此阶段，你准备可以输入模型的数据，这通过推导有意义的特征、数据转换等方式，使机器学习模型更容易处理。

假设你正在组合特征以创建一个新特征，这可以帮助 ML 模型更好地理解数据并识别隐藏模式。例如，你将糖、水和柠檬汁混合制作柠檬水，而不是单独食用。

以下是几种特征工程技术：

- 标签编码
- 组合特征以创建新特征
- 独热编码
- 填充
- 缩放
- 删除不需要的特征
- 对数变换

### 挑战：

- 缺乏领域知识
- 从现有特征集中创建新特征
- 从一组特征中选择有用的特征

### 构建和训练模型

ML 模型构建要求先前的阶段已成功完成。首先，你应该准备好训练集、测试集和验证集（针对监督学习算法）。在创建基准模型后，可以将其与新模型进行比较。

此过程涉及开发多个模型，以查看哪个更高效且效果更好。你必须考虑此阶段的计算资源需求。

一旦最终模型在训练数据上构建完成，下一步是检查其在未见数据（即测试数据）上的性能。

### 挑战：

- 模型复杂性
- 计算能力
- 识别合适的模型
- 模型训练时间





## 测试与评估

这里，你将构建测试用例，并检查模型在新数据上的表现。预生产或预部署活动在此阶段完成。性能结果将被分析，如果需要，你必须回到前面的阶段修复问题。

通过该阶段后，你可以将 ML 模型推入生产阶段。

### Challenges:

- 测试数据不足
- 反复迭代流程，直到输出满足要求
- 确定用于在真实数据上评估模型性能的平台
- 决定使用哪种测试
- 记录和分析测试结果

## 模型部署

这指的是将训练好的 ML 模型暴露给真实世界用户。你的模型在测试集和验证集上表现良好，但如果其他系统或用户无法使用它，那么它就未能达到目的。

例如，你构建了一个预测可能流失客户的模型，但直到你部署一个开始在真实数据上提供预测的模型，工作才算完成。

模型部署至关重要，因为你必须考虑以下因素：

- 预测交付次数
- 预测延迟
- ML 系统架构
- ML 模型部署和维护成本
- 基础设施复杂度
- 这将在后续章节中详细介绍。

### Challenges:

- 可移植性问题
- 可扩展性问题
- 数据相关挑战
- 安全威胁

## 监控与优化

最后但同样重要的是，监控和优化是需要观察和跟踪的阶段。你需要检查模型性能，因为性能会随时间下降。

如果模型指标（如准确率）低于预定义阈值，则需要进行跟踪，并且需要重新训练模型，可以是自动或手动方式。同样，输入数据也需要监控，因为可能出现输入数据架构不匹配或包含缺失值的情况。

除此之外，还需要跟踪基础设施指标，如 RAM、可用空间和系统问题。

维护指标、中间输出、警告和错误的日志记录是个好主意。

### Challenges:

- 数据漂移
- 为不同指标确定阈值
- 异常
- 确定需要跟踪的模型评估指标

## 机器学习模型部署类型

将 ML 模型部署到生产环境有多种方式；然而，并没有一种通用的方法。本节将介绍部署 ML 模型的流行方式。

## 批量预测

这是最简单的方法。在这里，ML 模型在静态数据上进行训练以进行预测，预测结果保存在数据库中，如 MS-SQL，并可集成到现有应用程序中或由商业智能团队访问。

通常，使用 ML 模型工件进行预测，因为这可以节省时间。模型工件需要在新数据上更新以进行更好的预测。

此方法非常适合小型组织和初学者。你可以安排 cron 定时任务，在一定时间间隔后进行预测。

### Pros:

- 价格实惠
- 复杂度低
- 易于实现

### Cons:

- 中等延迟
- 不适合以 ML 为中心的组织

## Web 服务/REST API

Web 服务/REST API 是部署模型的流行方法。与批量预测不同，它不处理一批记录；它一次处理单条记录。在近乎实时的情况下，它从用户或现有应用程序获取参数并进行预测。

它可以接受输入并以 JSON 格式返回输出。JSON 是一种流行且兼容的格式，使软件或网站开发人员能够轻松将其集成到现有应用程序中。

当事件触发时，REST API 将输入参数传递给 ML 模型并返回预测结果。

### Pros:

- 易于集成
- 灵活
- 经济实惠（按需付费计划）
- 近乎实时预测

### Cons:

- 可扩展性问题
- 易受安全威胁

## 移动设备和边缘设备

当存在需要立即采取行动/做出决策的情况，或者没有互联网连接时，ML 模型需要部署在这些设备上。

边缘设备包括安装在机器人上的传感器、智能手表和摄像头。

这种部署方式与前面的方法不同。在此方式中，输入数据可能不会发送到远程服务器进行预测。有云服务提供商，例如 Microsoft Azure，为这种方式提供所需的基础设施。Tiny Machine Learning（TinyML）是另一种此类替代方案，能够以极低功耗执行设备端传感器数据分析。

部署在移动设备上的 ML 模型很有用。开发基于 ML 的 Android/iOS 应用程序，例如语音助手或基于摄像头图像的考勤，都是部署在移动设备上的 ML 模型的用例。

### Pros:

- 功耗要求低
- 成本效益高
- 尺寸小

### Cons:

- 硬件资源有限
- 过程复杂且繁琐

## 实时

在这里，需要对流式数据进行分析。在这种方法中，用户传递输入数据进行预测，并期望（近）实时预测。与你之前学习过的方法相比，这是一种相当具有挑战性的方法。

你可以通过小型模型、缓存预测、No-SQL 数据库等方式降低预测延迟。

### Pros:

- 极低或无延迟
- 可以处理流式数据

### Cons:

- 复杂架构要求
- 计算开销大

## 生产环境中部署模型面临的挑战

在生产环境中部署机器学习模型至关重要。在部署 ML 模型时，技术挑战并非唯一的挑战。以下是你可能遇到的常见挑战。

### 团队协调

如果你在小型组织或小型数据科学团队工作，你可能需要承担不同角色，并负责端到端的模型开发。

然而，在大型组织中，不同阶段有独立的团队。这些团队相互交互以完成整个过程。大部分时间，生产团队或后续团队不了解前序阶段。缺乏协调和沟通不畅可能导致 ML 生命周期失败。

### 数据相关挑战

通常，数据科学家在实验阶段使用有限数据开发模型，但在将模型部署到生产环境时可能面临挑战，因为大规模数据可能影响模型性能。

新数据会不断改变其行为，但数据准备/预处理阶段可能无法处理这些新问题。例如，数字列中存在字符串记录。有时，需要通过修复问题重新运行实验才能获得可靠结果。

### 可移植性

可移植性问题在将代码库从本地机器移动到服务器以及反之亦然时出现。例如，假设你开发了一个模型并想将代码移动到服务器以重新运行模型。但是，你可能会遇到问题，例如库与当前操作系统版本不兼容，以及与 Python x 版本配合使用的代码行无法在当前安装的版本上工作。

在这种情况下，需要创建虚拟环境并重新安装软件包。

### 可扩展性

假设你使用 Web 服务部署了模型，且有 100 倍更多的用户尝试访问相同的 API。REST API 可能停止响应或延迟可能增加。

与大型组织相比，小规模管理 ML 模型相对容易，大型组织中多个模型正在大规模提供服务。对许多组织来说，大规模部署模型仍是一件新鲜事。

### 鲁棒性

简而言之，ML 模型的鲁棒性通过在输入数据出现变化的情况下仍能提供可靠输出来衡量。在现实世界中，提供 100% 的准确率几乎是不可能的。因此，可以说未见数据上的预测误差应接近训练误差。





用户行为可能难以预测。例如，假设模型需要一个字符串值，但用户提供了一个字母数字值。在这种情况下，模型输出可能不可靠。

## 安全性

机器学习系统容易受到安全漏洞的影响。攻击者可能通过故意提供恶意数据或向数据中添加噪声，迫使模型做出错误预测。模型在使用新数据训练时表现更好。但是，个人或一群人可以故意将恶意数据传递给模型，意图改变模型预测。

随着模型不断在新数据上进行训练，数据安全面临风险。在训练模型期间，攻击者可以窃取敏感信息。

## MLOps

MLOps将机器学习流程与DevOps最佳实践相结合，通过自动化流水线和管理来交付一致的输出。MLOps在过去几年中已成为行业新兴领域。

下图显示了MLOps随时间的流行度不断提升。

![](img/cc4299656808e62a294f1843a1e18e72_63_0.png)

图3.2：MLOps的兴起。来源：Google趋势

MLOps弥合了机器学习实验与生产环境中模型部署之间的差距。如今，许多数据科学家被迫手动执行MLOps流程。

MLOps流程涉及多个专业人员，数据科学家扮演关键角色。学科专家了解并收集客户的需求。然后，数据工程师从多个来源收集数据并执行ETL作业。完成此步骤后，数据科学家构建模型，DevOps团队构建CI/CD流水线并对其进行监控。最后，反馈会发送给数据科学家或相关团队进行验证。

MLOps简化并自动化此流程，以加快交付速度并构建高效的产品/服务。

MLOps是三个学科的结合，如下图所示。

![](img/cc4299656808e62a294f1843a1e18e72_64_0.png)

*图3.3：机器学习运维*

MLOps与DevOps不同，因为在DevOps中代码通常是静态的，但在MLOps中并非如此。

在MLOps中，模型不断在新数据上进行训练，因此会反复生成新的模型版本。如果满足要求，可以将其推送到生产环境。这就是为什么MLOps需要**持续训练**（CT）以及**持续集成**（CI）和**持续交付/部署**（CD）。

在DevOps中，开发人员根据需求编写代码，然后将其发布到生产环境，但在机器学习的情况下，开发人员首先需要收集数据并对其进行清理。他们编写模型构建代码，然后构建ML模型。最后，他们将其发布到生产环境。

## MLOps的优势

MLOps流程不仅加快了从实验到生产的ML进程，还减少了错误数量。MLOps在生产环境中自动化机器学习和深度学习模型部署。此外，它通过简化流程减少了对其他团队的依赖。

## 高效管理ML生命周期

MLOps通过遵循机器学习项目的基本原则来管理ML生命周期。它基于敏捷方法论。自动化CI/CD流水线有助于加快在新数据上重新训练模型、部署前测试、监控和反馈循环的过程。当前阶段取决于前一阶段的输出，因此部署过程中出现问题的可能性较小。

如果已部署模型的流量或请求数量增加，所需资源也会增加；同样，当流量或请求数量减少时，所需资源也会减少。

市场上有许多平台（例如GitHub Actions）可帮助您设置MLOps工作流。

## 可重复性

> 开发者：在我机器上可以运行。
> 经理：那么，我们将把你的机器发给客户。

- 可重复性在ML生命周期中起着至关重要的作用。在将代码文件传输到另一台机器或服务器时，可重复性可减少调试时间。MLOps基于**DRY（不要重复自己）**原则，可让您获得一致的输出。

- 给定相同的输入，复制的工作流应该产生相同的输出。为此，开发人员使用Docker等容器编排工具，以便在另一台机器或服务器上创建和设置具有依赖项的相同环境，从而获得一致的输出。

## 自动化

在最终部署之前，开发人员通常会多次部署模型，以确保一切就绪且输出符合预期。没有自动化，这将是一个耗时且乏味的过程。自动化提高了生产力，因为您不太可能手动测试、部署、扩展和监控ML模型。

在每个阶段，都会实施某些规则和条件，模型仅在满足这些条件时才会进入下一阶段。这减少了在计划将其部署到生产环境时其他团队的积极参与。

由于减少了一个跨团队依赖，因此测试时部署延迟很少或没有延迟。

在对代码进行所需更改后，以自动化方式进行快速部署（如果通过测试用例并满足条件）。这提高了团队的整体生产力。

## 跟踪与反馈循环

如果正确设置MLOps工作流，跟踪模型性能、指标、测试结果和输出将变得容易。模型性能可能会随时间下降，因此可能需要在新数据上重新训练模型。

得益于跟踪和反馈循环，它会发送有关模型性能、指标等方面的警报。

例如，如果反馈循环发送信息说模型准确率已降至68%以下，则需要重新训练模型。随后，它会再次检查模型性能。如果性能高于阈值，则会进入下一阶段；否则，需要使用最新数据对模型进行重新校准。

## 结论

在本章中，您学习了在生产环境中部署ML模型时面临的主要挑战。在本章开始时，您了解了ML生命周期的工作原理，并理解了其不同阶段及其挑战。接下来，您接触了不同类型的模型服务技术，并了解了它们的优缺点。然后，您分析了在生产环境中部署ML模型时可能面临的挑战。最后，您了解了MLOps的优势。

在下一章中，您将学习使用一个用例来开发、构建和安装用于ML模型的自定义Python包。

## 要点

- MLOps弥合了机器学习实验阶段与其在生产环境中的模型部署之间的差距。
- 模型部署策略取决于业务需求、用户和应用程序。
- MLOps将机器学习流程与DevOps最佳实践相结合，通过自动化流水线和管理来交付一致的输出。

## 选择题

- 1. 收集ML问题数据的不同方式有哪些？
- a) 电子调查
- b) 网页抓取
- c) 点击数据
- d) 以上全部

- 2. 如果向复制的工作流提供与原始工作流相似的输入，它应产生相同的输出，这被称为：
- a) 可移植性
- b) 可重复性
- c) 可扩展性
- d) 标签编码

## 答案

- 1. d
- 2. b

## 问题

- 1. 部署ML模型的不同方式有哪些？
- 2. MLOps与DevOps有何不同？
- 3. 部署ML模型时面临哪些挑战？
- 4. MLOps的优势是什么？

## 关键术语

- **容器**：容器是软件的标准单元，它将代码及其所有依赖项打包在一起，以便应用程序无论在何种计算环境下都能快速可靠地运行。
- **持续集成（CI）**：这是一个自动化流程，用于构建、测试和执行不同的代码片段。
- **持续交付/部署（CD）**：这是一个自动化流程，用于频繁构建经过测试的代码并将其部署到生产环境。




## 加入本书的 Discord 空间

加入本书的 Discord 工作区，获取最新动态、优惠、全球技术动态、新版本发布以及与作者的互动会议：

https://discord.bpbonline.com

![](img/cc4299656808e62a294f1843a1e18e72_68_0.png)

## 第 4 章 封装 ML 模型

### 简介

本章将教你如何将 Python 代码模块化，并构建可在另一台机器或服务器上安装和使用的 ML 包。模块化程序简化了代码调试、可重用性和可维护性。你将从创建虚拟环境开始，然后进行数据预处理，接着构建 ML 模型，最后为包创建测试用例。

### 结构

本章涵盖以下主题：

- 虚拟环境
- 要求文件
- 序列化和反序列化 ML 模型
- 使用 pytest 测试 Python 代码
- Python 打包和依赖管理
- 开发、构建和部署 ML 包
- 设置环境变量和路径

### 目标

完成本章后，你应该能够创建虚拟环境并在其中安装所需的依赖项。你还应该能够封装构建 ML 模型所需的模块和依赖项，以便在本地机器或远程服务器上安装。此外，你应该能够通过 pickle 保存训练好的 ML 模型。本章还将帮助你学习如何模块化代码并使用 pytest 构建测试用例，以检查完整性和功能。

### 虚拟环境

在处理多个项目时，**项目A** 需要 **PackageY_version2.6**，而 **项目B** 需要 **PackageY_version2.8**。在这种情况下，你无法在全局保留同一包的两个版本。

虚拟环境是解决方案。它允许你为每个项目隔离依赖项。你可以在任何位置创建虚拟环境，并在其中安装所需的包。

没有虚拟环境时，包会安装在默认 Python 位置的全局目录下：

```
/home/suhas/.local/lib/python3.6/site-packages
```

使用虚拟环境时，包会安装在虚拟环境的 Python 位置内：

```
/home/suhas/code/packages/venv_package/lib/python3.6/site-packages
```

可以为不同项目在不同虚拟环境中安装同一包的不同版本。你可以在 **venv1** 中拥有五个包，在 **venv2** 中拥有九个包。

下图最能描述以下场景：三个不同的项目拥有各自独立的虚拟环境，其中安装了不同版本的 Python 和包。

![](img/cc4299656808e62a294f1843a1e18e72_71_0.png)

图 4.1: 虚拟环境

### 虚拟环境安装：

```
pip install virtualenv
```

### 创建虚拟环境：

```
virtualenv venv_package
```

### 激活虚拟环境：

```
source venv_package/bin/activate
```

```
(venv_package) suhas@suhasVM:~/code/packages/prediction_model$
```

### 停用虚拟环境：

```
deactivate
```

要查看虚拟环境中安装的包列表：

```
pip list
```

或者

```
pip freeze
```

### 要求文件

要求文件中保存了可使用 pip 安装的包列表。

要创建要求文件：

```
pip freeze > requirements.txt
```

要从要求文件安装包列表，可以使用以下命令：

```
pip install -r requirements.txt
```

其中 -r 指的是 --requirement。它指示 pip 安装给定要求文件中的所有包。

### 序列化和反序列化 ML 模型

序列化是将 Python 对象层次结构转换为字节流的过程，而反序列化是逆运算，即将字节流（来自二进制文件或类字节对象）转换回对象层次结构。在 Python 中，序列化和反序列化分别指 pickling 和 unpickling。

此处，`joblib.dump()` 和 `joblib.load()` 将分别用作 `pickle.dump()` 和 `pickle.load` 的替代方案，以高效处理包含大数据的任意 Python 对象（尤其是大型 NumPy 数组），如下所示。

导入 joblib 库：

```
import joblib
```

然后创建要持久化的对象：

```
joblib.dump(ML_model_object, filename)
```

对象可以重新加载：

```
joblib.load(filename)
```

> 注意：如果在 Python 版本之间切换，可能需要为每个 Python 版本保存不同的 joblib 转储文件。

### 使用 pytest 测试 Python 代码

测试你的代码可以确保其产出预期结果且功能无缺陷。pytest 工具让你轻松构建和运行测试。它拥有简洁语法和多种特性。

pytest 可使用 pip 安装：

```
pip install pytest
```

要运行 **pytest**，只需切换到包目录并运行以下命令：

```
pytest
```

它会查找 test*.py 或 *_test.py 文件。

**pytest** 输出可以是以下之一：

- 一个点（.）表示测试已通过。
- 一个 F 表示测试失败。
- 一个 E 表示测试引发了意外异常。

```
pytest -v
```

-v 或 --verbose 标志允许你查看各个测试是通过还是失败。

### pytest fixture

pytest fixture 是基本函数，在测试函数执行前运行。当使用相同的函数返回值运行多个测试用例时，pytest fixture 非常有用。

它可以通过 @pytest.fixture 标记进行声明。以下是示例：

```
@pytest.fixture
def xyz_func():
    return "ABC"
```

当 pytest 运行测试用例时，它会查看该测试函数签名中的参数，然后查找名称与这些参数相同的 fixture。找到后，pytest 会运行这些 fixture，捕获它们返回的内容（如果有），并将这些对象作为参数传递给测试函数。

可以使用 pytest.ini 文件配置 **pytest**。

### Python 打包和依赖管理

假设你已在 Python 笔记本中创建了最终 ML 模型。此 Python 笔记本包含从加载数据到预测测试数据的所有步骤。

然而，出于以下原因，此笔记本不应在生产环境中使用：

- 调试困难
- 需在多处进行更改
- 依赖项繁多
- 代码缺乏模块化
- 变量和函数冲突
- 重复的代码片段

### 模块化编程

Python 是一门模块化编程语言。模块化编程是一种设计方法，将代码分割到独立文件中，每个文件包含执行特定逻辑所需的一切内容，并且可被其他作为输入的文件导入后返回预期输出。这些独立文件称为模块。

### 模块

模块是一个可包含类、函数和变量的 Python 文件。例如，load.py 是一个模块，其名为 load。

### 包

包包含一个或多个（相关）模块，这些模块彼此相互关联。包可以包含存放模块的子包。它使用内置目录层次结构以便于访问。如果目录包含 __init__.py 文件，则带有子目录的目录可称为包。

包将作为部署的一部分安装在生产环境中，因此在打包任何内容之前，你需要对以下部署问题有答案：

- 你的应用用户是谁？你的应用是由从事软件开发的其他开发人员、数据中心的运维人员，还是不太精通软件的群体安装的？
- 你的应用是用于在服务器、桌面、移动客户端（手机、平板电脑等）上运行，还是嵌入专用设备中？
- 你的应用是单独安装，还是大规模部署批量安装？

下图展示了 Python 包的示例结构，其中 f1、f2、f3、f4 和 f5 是包的模块。




![](img/cc4299656808e62a294f1843a1e18e72_75_0.png)

图 4.2: Python 包结构

## 导入模块语法

```
import <module_name>
import <module_name> as <alt_name>
```

## 导入 f4 模块

- 1. from My_Package import f4
- 2. from My_Package import f4 as load

## 导入 f1 模块以使用 x()

- 1. from My_Package.Sub_PackageA import f1
- 2. f1.func()

或者您可以使用以下方法导入模块：

- 1. from My_Package.Sub_PackageA.f1 import func
- 2. func()

## 开发、构建和部署 ML 包

在本节中，您将研究一个用例，该用例将从定义业务问题开始，最终以安装和使用 ML 包结束。您将学习为 ML 模型开发和构建自定义 Python 包。自定义包具有可移植性，可用于给定项目。您将能够像安装其他 Python 包一样安装自定义包，并对新数据进行预测。

### 业务问题

一家公司希望根据客户通过在线申请表格提供的详细信息来自动化贷款资格流程。这是一个分类问题，您需要预测贷款是否会被批准。

### 数据

数据对应与个人相关的一组财务交易。数据已标准化、去趋势化并匿名化。有关数据列的详细信息，请参阅以下表格：

| Variable | Description |
|---|---|
| Loan_ID | 唯一贷款 ID |
| Gender | 男性 / 女性 |
| Married | 申请人的婚姻状态 (Y / N) |
| Dependents | 受赡养人数量 |
| Education | 申请人的教育程度 (Graduate/Under Graduate) |
| Self_Employed | 自雇 (Y / N) |
| ApplicantIncome | 申请人的收入 |
| CoapplicantIncome | 联合申请人的收入 |
| LoanAmount | 贷款金额（以千为单位） |
| Loan_Amount_Term | 贷款期限（以月为单位） |
| Credit_History | 信用记录是否符合指南 (Y / N) |
| Property_Area | 城市 / 半城市 / 农村 |
| Loan_Status | 贷款是否批准 (Y / N) |

*表 4.1: 数据描述*

## 构建 ML 模型

此时，您可以使用 Jupyter 笔记本构建和比较不同的 ML 算法。

识别表现优于其他模型的模型，并为模型确定最佳参数（和超参数）。在此实验阶段，您应准备好所需的信息，例如需要转换的变量、缺失值填充、数值变量列表以及数据路径。

当您完成实验阶段后，可以开始构建包。打包的目的是可重用性、可移植性、减少错误以及机器学习流程的自动化。

首先，为构建包创建一个单独的目录。为不同阶段和操作维护单独的模块（Python 文件），例如，为数据预处理维护单独的模块。这将模块化代码并使代码调试变得容易。

构建测试用例，这些测试用例将运行代码文件并验证文件和预期输出的完整性。

本章不专注于优化 ML 模型，因此您可以通过微调来进一步提高模型性能。此包仅限于当前项目，即您不应在不同项目中使用同一个包。

## 开发包

以下是包的目录结构：

```
prediction_model
|— MANIFEST.in
|— prediction_model
|   |— config
|   |   |— config.py
|   |   |— __init__.py
|   |— datasets
|   |   |— __init__.py
|   |   |— test.csv
|   |   |— train.csv
|   |— __init__.py
|   |— pipeline.py
|   |— predict.py
|   |__ processing
|   |   |__ data_management.py
|   |   |__ __init__.py
|   |   |__ preprocessors.py
|   |__ trained_models
|   |   |__ classification_v1.pkl
|   |   |__ __init__.py
|   |__ train_pipeline.py
|   |__ VERSION
|__ README.md
|__ requirements.txt
|__ setup.py
|__ tests
|   |__ pytest.ini
|   |__ test_predict.py
```

### __init__.py

__init__.py 模块通常为空。但是，它有助于导入其他 Python 模块。

此文件指示该目录应被视为一个包。

### MANIFEST.in

MANIFEST.in 文件由命令组成，每行一个，指示 setuptools 将一组文件添加到或从 sdist（源发行版）中删除。在 Python 中，发行版是指允许打包、构建和分发模块的一组文件。sdist 包含文件存档，例如源文件、数据文件和 setup.py 文件，存储在 Unix 上的压缩 tar 文件 (.tar.gz) 中。

以下表格列出了命令及其描述。但是，本章将仅介绍其中几个命令。

您可以根据项目要求更新 MANIFEST.in。有关清单文件中常用命令，请参阅以下表格。

| Command | Description |
|---|---|
| include pat1 pat2 ... | 添加匹配任何列出模式的所有文件。 |
| exclude pat1 pat2 ... | 移除匹配任何列出模式的所有文件。 |
| recursive-include dir-pattern pat1 pat2 ... | 添加与 dir-pattern 匹配且符合任何列出模式的目录下的所有文件。 |
| recursive-exclude dir-pattern pat1 pat2 ... | 移除与 dir-pattern 匹配且符合任何列出模式的目录下的所有文件。 |
| global-include pat1 pat2 ... | 添加源树中任何位置匹配任何列出模式的所有文件。 |
| global-exclude pat1 pat2 ... | 移除源树中任何位置匹配任何列出模式的所有文件。 |
| graft dir-pattern | 添加与 dir-pattern 匹配的目录下的所有文件。 |
| prune dir-pattern | 移除与 dir-pattern 匹配的目录下的所有文件。 |

表 4.2: 清单文件的命令

让我们将命令添加到清单文件中以包含或排除文件：

- 1. include *.txt
- 2. include *.md
- 3. include *.cfg
- 4. include *.pkl
- 5. recursive-include ./prediction_model/*
- 6.
- 7. include prediction_model/datasets/train.csv
- 8. include prediction_model/datasets/test.csv
- 9. include prediction_model/trained_models/*.pkl
- 10. include prediction_model/VERSION
- 11. include ./requirements.txt
- 12. exclude *.log
- 13. recursive-exclude * __pycache__
- 14. recursive-exclude * *.py[co]

### config.py

配置模块包含常量变量、目录路径和初始设置。可以通过将此模块导入到其他模块中来访问变量和函数。例如，TARGET 变量存储因变量列名 Loan_Status。

在此，指定包的根目录、数据目录、训练文件名、测试文件名、特征以及其他文件和目录的路径。

```
1. #Import Libraries
2. import pathlib
3. import os
4. import prediction_model
5.
6. PACKAGE_ROOT = pathlib.Path(prediction_model.__file__).resolve().parent
7.
8. DATAPATH=os.path.join(PACKAGE_ROOT, 'datasets')
9. SAVED_MODEL_PATH=os.path.join(PACKAGE_ROOT, 'trained_models')
10.
11. TRAIN_FILE='train.csv'
12. TEST_FILE='test.csv'
13.
14. TARGET='Loan_Status'
15.
16. #Features to keep
17. FEATURES=['Gender', 'Married', 'Dependents',
18.     'Education', 'Self_Employed', 'ApplicantIncome',
19.     'CoapplicantIncome','LoanAmount','Loan_Amount_Term',
20.     'Credit_History','Property_Area'] # Final feature to keep in data
21.
22. NUMERICAL_FEATURES=['ApplicantIncome', 'LoanAmount', 'Loan_Amount_Term']
23.
24. CATEGORICAL_FEATURES=['Gender', 'Married', 'Dependents',
25.     'Education', 'Self_Employed', 'Credit_History',
26.     'Property_Area'] #Categorical
27.
28. FEATURES_TO_ENCODE=['Gender', 'Married', 'Dependents',
29.     'Education', 'Self_Employed','Credit_History',
30.     'Property_Area'] #Features to Encode
31.
32. TEMPORAL_FEATURES=['ApplicantIncome']
33. TEMPORAL_ADDITION='CoapplicantIncome'
34. LOG_FEATURES=['ApplicantIncome', 'LoanAmount'] #Features for Log Transformation
35. DROP_FEATURES=['CoapplicantIncome'] #Features to Drop
```

### data_management.py

此模块包含加载数据、使用 joblib 保存序列化的 ML 模型以及加载反序列化的 ML 模型所需的函数。

```
1. #Import Libraries
2. import os
3. import pandas as pd
4. import joblib
5.
6. #Import other files/modules
7. from prediction_model.config import config
8.
9. def load_dataset(file_name):
10. """Read Data"""
11. file_path = os.path.join(config.DATAPATH,file_name)
12. _data = pd.read_csv(file_path)
13. return _data
15. def save_pipeline(pipeline_to_save):
16. """Store Output Of Pipeline
17. Exporting pickle file of trained Model """
18. save_file_name = 'classification_v1.pkl'
19. save_path = os.path.join(config.SAVED_MODEL_PATH, save_file_name)
```





```
joblib.dump(pipeline_to_save, save_path)
print("Saved Pipeline : ", save_file_name)

def load_pipeline(pipeline_to_load):
    """Importing pickle file of trained Model"""
    save_path = os.path.join(config.SAVED_MODEL_PATH, pipeline_to_load)
    trained_model = joblib.load(save_path)
    return trained_model
```

## preprocessors.py

此模块包含 sklearn 管道所需的所有拟合和转换函数：

```
# Import Libraries
import pandas as pd
import numpy as np
from sklearn.base import BaseEstimator, TransformerMixin
from sklearn.preprocessing import LabelEncoder

# Import other files/modules
from prediction_model.config import config
```

使用特征的均值来填补缺失的数值。但是，你也可以使用其他缺失值填补技术，例如随机回归填补、插值和冷卡填补。

```
# Numerical Imputer
class NumericalImputer(BaseEstimator, TransformerMixin):
    """Numerical Data Missing Value Imputer"""
    def __init__(self, variables=None):
        self.variables = variables

    def fit(self, X, y=None):
        self.imputer_dict_ = {}
        for feature in self.variables:
            self.imputer_dict_[feature] = X[feature].mean()
        return self

    def transform(self, X):
        X = X.copy()
        for feature in self.variables:
            X[feature].fillna(self.imputer_dict_[feature], inplace=True)
        return X
```

使用特征的最频繁值来填补缺失的类别值，但你也可以使用其他缺失值填补技术，例如缺失指示器填补、**多元连锁方程插补 (MICE)** 算法和系统随机抽样填补。

```
# Categorical Imputer
class CategoricalImputer(BaseEstimator, TransformerMixin):
    """Categorical Data Missing Value Imputer"""
    def __init__(self, variables=None):
        self.variables = variables

    def fit(self, X, y=None):
        self.imputer_dict_ = {}
        for feature in self.variables:
            self.imputer_dict_[feature] = X[feature].mode()[0]
        return self

    def transform(self, X):
        X = X.copy()
        for feature in self.variables:
            X[feature].fillna(self.imputer_dict_[feature], inplace=True)
        return X
```

随后，对类别特征进行编码以用于模型训练。

```
# Categorical Encoder
class CategoricalEncoder(BaseEstimator, TransformerMixin):
    """Categorical Data Encoder"""
    def __init__(self, variables=None):
        self.variables = variables

    def fit(self, X, y):
        self.encoder_dict_ = {}
        for var in self.variables:
            t = X[var].value_counts().sort_values(ascending=True).index
            self.encoder_dict_[var] = {k: i for i, k in enumerate(t, 0)}
        return self

    def transform(self, X):
        X = X.copy()
        # This part assumes that the encoder does not introduce a NANs
        # In that case, a check needs to be done and the code should break
        for feature in self.variables:
            X[feature] = X[feature].map(self.encoder_dict_[feature])
        return X
```

以下代码片段用于创建新特征：

```
# Temporal Variables
class TemporalVariableEstimator(BaseEstimator, TransformerMixin):
    """Feature Engineering"""
    def __init__(self, variables=None, reference_variable=None):
        self.variables = variables
        self.reference_variable = reference_variable

    def fit(self, X, y=None):
        # No need to put anything, needed for Sklearn Pipeline
        return self

    def transform(self, X):
        X = X.copy()
        for var in self.variables:
            X[var] = X[var] + X[self.reference_variable]
        return X
```

对变量应用对数变换，使数据中的模式更具可解释性。

```
# Log Transformations
class LogTransformation(BaseEstimator, TransformerMixin):
    """Transforming variables using Log Transformations"""
    def __init__(self, variables=None):
        self.variables = variables

    def fit(self, X, y):
        return self

    # Need to check in advance if the features are <= 0
    # If yes, needs to be transformed properly (E.g., np.log1p(X[var]))
    def transform(self, X):
        X = X.copy()
        for var in self.variables:
            X[var] = np.log(X[var])
        return X
```

以下代码片段用于删除对模型不重要的特征：

```
# Drop Features
class DropFeatures(BaseEstimator, TransformerMixin):
    """Dropping Features Which Are Less Significant"""
    def __init__(self, variables_to_drop=None):
        self.variables_to_drop = variables_to_drop

    def fit(self, X, y=None):
        return self

    def transform(self, X):
        X = X.copy()
        X = X.drop(self.variables_to_drop, axis=1)
        return X
```

## _pipeline.py_

本模块中使用了 sklearn 管道。模型可以在没有 sklearn 管道的情况下部署，但建议构建 sklearn 管道。管道的目的是组装多个步骤，以便在设置不同参数的同时一起进行交叉验证。

```
# Import Libraries
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import MinMaxScaler
from sklearn.linear_model import LogisticRegression

# Import other files/modules
from prediction_model.config import config
import prediction_model.processing.preprocessors as pp

loan_pipe = Pipeline([
    ('Numerical Imputer', pp.NumericalImputer(variables=config.NUMERICAL_FEATURES)),
    ('Categorical Imputer', pp.CategoricalImputer(variables=config.CATEGORICAL_FEATURES)),
    ('Temporal Features',
     pp.TemporalVariableEstimator(variables=config.TEMPORAL_FEATURES,
                                  reference_variable=config.TEMPORAL_ADDITION)),
    ('Categorical Encoder',
     pp.CategoricalEncoder(variables=config.FEATURES_TO_ENCODE)),
    ('Log Transform', pp.LogTransformation(variables=config.LOG_FEATURES)),
    ('Drop Features', pp.DropFeatures(variables_to_drop=config.DROP_FEATURES)),
    ('Scaler Transform', MinMaxScaler())),
    ('Linear Model', LogisticRegression(random_state=1))
])
```

## predict.py

一个 `predict.py` 模块加载保存的 ML 模型 (`.pkl`) 并对新数据进行预测。

```
# Import Libraries
import pandas as pd
import numpy as np
import joblib

# Import other files/modules
from prediction_model.config import config
from prediction_model.processing.data_management import load_pipeline

pipeline_file_name = 'classification_v1.pkl'

_loan_pipe = load_pipeline(pipeline_file_name)


def make_prediction(input_data):
    """Predicting the output"""

    # Read Data
    data = pd.DataFrame(input_data)

    # prediction
    prediction = _loan_pipe.predict(data[config.FEATURES])
    output = np.where(prediction == 1, 'Y', 'N').tolist()
    results = {'prediction': output}
    return results
```

## requirements.txt

本文件包含以下库：

```
# Model Building Requirements
joblib==0.16.0
numpy==1.19.0
pandas==1.0.5
scikit-learn==0.23.1
scipy==1.5.1
sklearn==0.0

# testing requirements
pytest<5.0.0,>=4.6.6

# packaging
setuptools==40.6.3
wheel==0.32.3
```

## classification_v1.pkl

这是来自训练模型的 pickle 文件。

## train_pipeline.py

此模块加载训练数据并将其传递给管道，然后将模型的 pickle 文件保存到本地目录。

```
# Import Libraries
import pandas as pd
import numpy as np

# Import other files/modules
from prediction_model.config import config
from prediction_model.processing.data_management import load_dataset, save_pipeline
import prediction_model.processing.preprocessors as pp
import prediction_model.pipeline as pl
from prediction_model.predict import make_prediction


def run_training():
    """Train the model"""
    # Read Data
    train = load_dataset(config.TRAIN_FILE)

    # separating Loan_status in y
    y = train[config.TARGET].map({'N': 0, 'Y': 1})
    pl.loan_pipe.fit(train[config.FEATURES], y)
    save_pipeline(pipeline_to_save=pl.loan_pipe)
```





21. if __name__ == '__main__':
22.     run_training()

## setup.py

要从源目录配置和安装软件包，请创建 setup.py 文件。该文件特定于软件包。PIP 将使用 setup.py 文件安装软件包。进入 setup.py 文件所在的目录，使用 pip install .（句号）命令安装软件包。

```python
import io
import os
from pathlib import Path

from setuptools import find_packages, setup

# Package meta-data
NAME = 'prediction_model'
DESCRIPTION = 'Train and deploy prediction model.'
URL = 'https://github.com/suhas-ds/prediction_model'
EMAIL = 'suhasp.ds@gmail.com'
AUTHOR = 'Suhas Pote'
REQUIRES_PYTHON = '3.6'

here = os.path.abspath(os.path.dirname(__file__))

# What packages are required for this module to be executed?
def list_reqs(fname='requirements.txt'):
    with io.open(os.path.join(here, fname), encoding='utf-8') as fd:
        return fd.read().splitlines()
try:
    with io.open(os.path.join(here, 'README.md'),
                 encoding='utf-8') as f:
    long_description = '\n' + f.read()
except FileNotFoundError:
    long_description = DESCRIPTION

# Load the package's __version__.py module as a dictionary.
ROOT_DIR = Path(__file__).resolve().parent
PACKAGE_DIR = ROOT_DIR / NAME
about = {}
with open(PACKAGE_DIR / 'VERSION') as f:
    _version = f.read().strip()
about['__version__'] = _version

setup(
    name=NAME,
    version=about['__version__'],
    description=DESCRIPTION,
    long_description=long_description,
    long_description_content_type='text/markdown',
    author=AUTHOR,
    author_email=EMAIL,
    python_requires=REQUIRES_PYTHON,
    url=URL,
    packages=find_packages(exclude=('tests',)),
    package_data={'prediction_model': ['VERSION']},
    install_requires=list_reqs(),
    extras_require={},
include_package_data=True,
license='MIT',
classifiers=[
    'License :: OSI Approved :: MIT License',
    'Programming Language :: Python',
    'Programming Language :: Python :: 3',
    'Programming Language :: Python :: 3.6',
    'Programming Language :: Python :: Implementation :: CPython',
    'Programming Language :: Python :: Implementation :: PyPy'
]
)
```

## VERSION

此文件保存软件包的版本。此处使用 **主版本号.次版本号.修订版本号** 方案。

```
0.1.0
```

## pytest.ini

要在运行 pytest 时禁用警告，需要配置 pytest.ini 文件。

```
[pytest]
addopts = -p no:warnings
```

## test_predict.py

它从验证数据中获取一条记录，并使用 **断言** 语句验证输出。

它验证以下检查：

- 输出不为空。
- 输出数据类型为 **str**。
- 对于给定数据（固定），输出为 **Y**。

这些检查通过 pytest 运行。

```python
# Import libraries
import pytest
# Import files/modules
from prediction_model.config import config
from prediction_model.processing.data_management import load_dataset
from prediction_model.predict import make_prediction

@pytest.fixture
def single_prediction():
    ''' This function will predict the result for a single record'''
    test_data = load_dataset(file_name=config.TEST_FILE)
    single_test = test_data[0:1]
    result = make_prediction(single_test)
    return result

# Test Prediction
def test_single_prediction_not_none(single_prediction):
    ''' This function will check if the result of prediction is not None'''
    assert single_prediction is not None

def test_single_prediction_dtype(single_prediction):
    ''' This function will check if the data type of the result of the prediction is str i.e. string'''
    assert isinstance(single_prediction.get('prediction')[0], str)

def test_single_prediction_output(single_prediction):
    ''' This function will check if the result of the prediction is Y'''
    assert single_prediction.get('prediction')[0] == 'Y'
```

设置环境变量 PYTHONPATH 并进入软件包目录，然后运行以下命令：

```
pytest -v
```

如果一切正常，应得到如下输出：

![](img/cc4299656808e62a294f1843a1e18e72_94_0.png)

图 4.3：pytest 输出

## sdist

Python 的 sdist 是压缩归档文件（.tar.gz 文件），包含一个或多个软件包或模块。

这会创建一个 dist 目录，其中包含软件包的压缩归档文件（例如，Linux 中的 <PACKAGE_NAME>-<VERSION>.tar.gz）。

## wheel

这是二进制分发版（bdist），支持 Windows、Mac 和 Linux。

如果你有已编译的代码扩展，Wheels 将加快安装速度，因为不需要构建步骤。wheel 分发版是当前平台的已构建分发版。可安装的 wheel 将在 dist 目录下创建，同时也会创建包含已构建代码的 build 目录。

## 设置环境变量和路径

你可能需要将路径添加到环境变量中。这允许你导入模块和函数：

使用终端打开 .bashrc 文件

```
sudo nano ~/.bashrc
```

将软件包目录的路径添加到环境变量。示例如下：

```
PYTHONPATH=/home/suhas/code/packages/prediction_model:$PYTHONPATH
```

```
export PYTHONPATH
```

然后运行 source ~/.bashrc。
重新打开终端并使用以下命令进行测试：
echo $PYTHONPATH

## 构建包

- 1. 进入项目目录并安装依赖项：
  pip install -r requirements.txt
- 2. 创建 pickle 文件：
  python prediction_model/train_pipeline.py
- 3. 创建源分发版和 wheel：
  python setup.py sdist bdist_wheel

## 安装包

进入 setup.py 文件所在的项目目录，并使用 pip 命令安装此项目：

要以可编辑或开发者模式安装软件包：

```
pip install -e .
```

- . 指的是当前目录。
- -e 指的是 --editable 模式。

软件包的普通安装：

```
pip install .
```

- . 指的是当前目录。

你可以将整个软件包推送到 GitHub 仓库。

要从 GitHub 仓库安装。

使用 git：

```
pip install git+https://github.com/suhas-ds/prediction_model.git
```

不使用 git：

```
pip install https://github.com/suhas-ds/prediction_model/tarball/master
```

或：

```
pip install https://github.com/suhas-ds/prediction_model/zipball/master
```

或：

```
pip install https://github.com/suhas-ds/prediction_model/archive/master.zip
```

构建软件包后，目录结构应如下所示：

```
prediction_model
|-- build
|   |-- bdist.linux-x86_64
|   |-- lib
|       |-- prediction_model
|-- dist
|   |-- prediction_model-0.1.0-py3-none-any.whl
|   |-- prediction_model-0.1.0.tar.gz
|-- MANIFEST.in
|-- prediction_model
|   |-- config
|   |   |-- config.py
|   |   |-- __init__.py
|   |-- datasets
|   |   |-- __init__.py
|   |   |-- test.csv
|   |   |-- train.csv
|   |-- __init__.py
|   |-- pipeline.py
|   |-- predict.py
|   |-- processing
|   |   |-- data_management.py
|   |   |-- __init__.py
|   |   |-- preprocessors.py
|   |-- trained_models
|       |-- classification_v1.pkl
|   |-- __init__.py
|   |-- train_pipeline.py
|   |-- VERSION
|   |-- prediction_model.egg-info
|   |   |-- dependency_links.txt
|   |   |-- PKG-INFO
|   |   |-- requires.txt
|   |   |-- SOURCES.txt
|   |   |-- top_level.txt
|-- README.md
|-- requirements.txt
|-- setup.py
|-- tests
|   |-- pytest.ini
|   |-- test_predict.py
```

## 包使用示例

启动 Python 控制台（在虚拟环境中）：

```
(venv_package) suhas@ds:~/code/packages$ python
```

```
Python 3.6.9

[GCC 8.4.0] on linux

Type "help", "copyright", "credits" or "license" for more information.
```

导入 prediction_model 软件包并进行预测：

```python
import prediction_model

from prediction_model import train_pipeline

from prediction_model.predict import make_prediction

import pandas as pd

train_pipeline.run_training() # Save the pickle object of the trained model
```





保存的管道：classification_v1.pkl # 输出
7. test_data = pd.read_csv("/home/suhas/code/test.csv") # 加载数据
8. result = make_prediction(test_data[0:1])# 对第一行进行预测
9. print(result)

{'prediction': ['Y']}

针对给定的输入数据，您应得到的输出为 Y（即“Yes”）。

## 结论

本章讨论了生产环境中模块化编程的重要性；当您同时处理多个项目时，虚拟环境发挥着至关重要的作用。之后，您探索了创建和激活虚拟环境的步骤。您可以在 requirements.txt 文件中列出要在虚拟环境内安装的包，以便一次性安装所有所需的包。编写测试用例能增强对包、函数及整体完整性的信心。包具有可移植性和可重用性，并且可以轻松调试。

在下一章中，您将学习如何利用 MLflow 来跟踪机器学习实验并保存序列化模型。

## 要点总结

- Python 包包含多个模块，每个模块包含函数、类和变量。
- MANIFEST.in 文件包含要包含和排除的文件列表。
- requirements.txt 文件包含使用 pip 安装的包列表。
- Python 分别使用 pickling 和 unpickling 术语来指代序列化和反序列化。
- __init__.py 文件指示该目录应被视为一个包。

## 选择题

- 1. 识别一个 Python 模块。
  a) load.py
  b) requirements.txt
  c) transform.ccm
  d) MANIFEST.in

- 2. Python fixture 可以通过以下哪项声明？
  a) fixture
  b) pytest.fixture
  c) @pytest.fixture
  d) fixture.pytest

## 答案

- 1. a
- 2. c

## 问题

- 1. 什么是 Python 模块？
- 2. 如何解读 pytest 命令的输出？
- 3. 如何以可编辑模式安装 Python 包？

## 关键术语

- PYTHONPATH：它扩展了模块的默认搜索路径。PYTHONPATH 变量包含一个目录列表，其中的模块将在 Python 环境中被访问。
- Joblib：Joblib 是一组用于在 Python 中提供轻量级流水线的工具。它用于将模型持久化以供将来使用，具体包括以下方面：
  - 函数的透明磁盘缓存和惰性重新计算（记忆模式）。
  - 简单的并行计算。

加入我们书籍的 Discord 空间

加入本书的 Discord 工作区，获取最新动态、优惠、全球技术动态、新版本发布以及与作者的交流会议：

https://discord.bpbonline.com

![](img/cc4299656808e62a294f1843a1e18e72_99_0.png)

## 第 5 章

### MLflow - 管理机器学习生命周期的平台

### 简介

机器学习生命周期涉及许多挑战。例如，数据科学家需要尝试包含多个参数和超参数的不同模型。他们需要跟踪表现良好的模型及其参数。接下来，他们需要保存序列化模型以供重用。本章解释了 MLflow 在机器学习生命周期中的作用。MLflow 是一个用于简化机器学习开发的平台，包括跟踪实验、将代码打包为可复现的运行以及共享和部署模型。它可以管理完整的机器学习生命周期。

### 结构

本章讨论以下主题：

- MLflow 简介
- MLflow 跟踪
- MLflow 项目
- MLflow 模型
- MLflow 模型注册表

### 目标

学习本章后，您应该能够使用 MLflow 训练、重用和部署机器学习模型。您还应该能够跟踪模型评估指标和模型参数，对训练好的模型进行 pickling 处理，并在 MLflow UI 上比较两个模型的结果。在部署方面，MLflow 支持许多下游工具。您应该能够选出任何优于其他迭代的版本（通过运行 ID），并通过 Python 代码、终端或 Postman 来使用它。

### MLflow 简介

MLflow 是一个用于管理端到端机器学习生命周期的开源平台。

MLflow 允许数据科学家在将模型部署到生产环境之前运行任意数量的实验；但是，它会跟踪模型评估指标，例如 RMSE 和 AUC。它还会跟踪构建模型时使用的超参数。它使您可以将训练好的模型及其最佳超参数保存在一起。最后，它允许您将机器学习模型部署到生产服务器或云端。您甚至可以跟踪暂存和生产环境中正在使用的模型，以便其他团队成员了解此信息。

MLflow 与库无关，也就是说，您可以将其与任何流行的机器学习库一起使用。此外，您可以使用任何流行的编程语言，因为 MLflow 函数可以通过 REST API 和命令行界面 (CLI) 访问。

将 MLflow 与现有代码集成非常简单，因为只需进行最小更改。如果您在本地系统上工作，它会自动创建一个 mlrun 目录，用于存储输出、工件和元数据。它为每个运行创建一个单独的目录。但是，您可以指定创建 mlrun 目录的路径。MLflow 允许您将每个运行的信息存储在数据库中，例如 MySQL 或 PostgreSQL。

MLflow 在以下场景中更有用：

- 比较不同的模型：MLflow 提供一个 UI，允许用户比较不同的模型。您可以并排比较随机森林与逻辑回归，以及它们的模型指标和所用参数。MLflow 支持多种模型框架。
- 循环模型部署：在生产环境中，每次数据变更、出现新需求或构建出比当前模型更好的模型后，都需要推送新版本的模型。在这些场景中，MLflow 有助于跟踪处于暂存（预生产）环境中的模型和处于生产环境中的模型，并附带版本和简要描述。
- **多个依赖项**：如果您正在处理不同的项目或不同的框架，每个项目或框架都会有一组不同的依赖项。MLflow 可帮助您随模型一起维护依赖项。
- **与大型数据科学团队协作**：MLflow 存储模型指标、参数、创建时间、版本、用户等信息。这些信息可供在同一项目上工作的其他团队成员访问。他们可以使用 MLflow UI 或 SQL 表（如果将其存储在数据库中）来跟踪所有元数据。

### 设置环境并安装 MLflow

在本节中，您将安装 miniconda，然后在 conda 环境中安装 mlflow。但是，如果您已经安装了 anaconda 或 miniconda，可以创建 conda 环境并使用 PIP 安装 mlflow。

### Miniconda 安装

如果您的机器上已安装 anaconda，则可以跳过下一步，即安装和设置 Miniconda。

您可以从以下链接下载 Miniconda：

```
https://docs.conda.io/en/latest/miniconda.html#linux-installers
```

或者，您可以在终端（针对 Linux）直接执行以下命令：

```
wget https://repo.anaconda.com/miniconda/Miniconda3-py37_4.10.3-Linux-x86_64.sh
```

运行安装：

```
bash Miniconda3-latest-Linux-x86_64.sh
```

阅读并按照安装程序屏幕上的提示操作。miniconda 安装完成后重启终端。

在终端中，您会看到 base conda 环境已自动激活。您可以通过在终端中运行以下命令来禁用 base 环境的自动激活：

```
conda config --set auto_activate_base false
```

使用以下命令验证 conda 安装：

```
conda list
```

运行以下命令更新 conda（可选）：

```
conda update conda
```


让我们创建一个虚拟环境：

```
conda create -n venv python=3.7
```

- `-n` 是指虚拟环境的名称。
- `venv` 是虚拟环境的名称。

上述命令将创建 Python 版本为 3.7 的虚拟环境。

创建 conda 环境后，需要运行以下命令将其激活：

```
conda activate venv
```

最后，使用 pip 安装 MLflow：

```
pip install mlflow
```

> 注意：默认情况下，MLflow 项目使用 conda 安装依赖项；但是，您可以通过使用 `--no-conda` 选项在不使用 conda 的情况下继续，例如，mlflow run . --no-conda。

安装 MLflow 后，在终端中键入 `mlflow` 并回车以查看其用法、选项和命令。以下图显示了 `mlflow` 的用法和选项：

![](img/cc4299656808e62a294f1843a1e18e72_104_0.png)

图 5.1: MLflow 的用法、选项和命令

要打开 MLflow 的 Web UI，请在终端中运行以下命令（请参阅图 5.2）：

```
mlflow ui
```

```
(mlflow_venv) suhas@suhasVN:~/test$ mlflow ui
[2021-09-23 20:02:36 +0530] [23435] [INFO] Starting gunicorn 20.1.0
[2021-09-23 20:02:36 +0530] [23435] [INFO] Listening at: http://127.0.0.1:5000 (
23435)
[2021-09-23 20:02:36 +0530] [23435] [INFO] Using worker: sync
[2021-09-23 20:02:36 +0530] [23438] [INFO] Booting worker with pid: 23438
```

图 5.2: 启动 MLflow UI

打开浏览器；您应该会看到 MLflow 的 Web UI，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_105_0.png)

图 5.3: MLflow UI

您可以执行一系列实验并捕获实验的多个运行。每个实验可以包含多个运行。您还可以为实验捕获注释。除此之外，还有许多可用的自定义选项，例如按列排序、显示或隐藏列以及更改表格视图。

注意：假设您中断了正在运行的 MLflow UI 服务并重新运行 `mlflow ui` 命令；在这种情况下，您可能会遇到如下图所示的错误：

```
(mlflow_venv) suhas@suhasVM:~/test$ mlflow ui
[2021-09-24 22:58:02 +0530] [23736] [INFO] Starting gunicorn 20.1.0
[2021-09-24 22:58:02 +0530] [23736] [ERROR] Connection in use: ('127.0.0.1', 5000)
[2021-09-24 22:58:02 +0530] [23736] [ERROR] Retrying in 1 second.
[2021-09-24 22:58:03 +0530] [23736] [ERROR] Connection in use: ('127.0.0.1', 5000)
[2021-09-24 22:58:03 +0530] [23736] [ERROR] Retrying in 1 second.
[2021-09-24 22:58:04 +0530] [23736] [ERROR] Connection in use: ('127.0.0.1', 5000)
[2021-09-24 22:58:04 +0530] [23736] [ERROR] Retrying in 1 second.
[2021-09-24 22:58:05 +0530] [23736] [ERROR] Connection in use: ('127.0.0.1', 5000)
[2021-09-24 22:58:05 +0530] [23736] [ERROR] Retrying in 1 second.
[2021-09-24 22:58:06 +0530] [23736] [ERROR] Connection in use: ('127.0.0.1', 5000)
[2021-09-24 22:58:06 +0530] [23736] [ERROR] Retrying in 1 second.
[2021-09-24 22:58:07 +0530] [23736] [ERROR] Can't connect to ('127.0.0.1', 5000)
Running the mlflow server failed. Please see the logs above for details.
```

图 5.4: MLflow UI 错误

这是因为地址端口已被占用；因此，您必须先释放它，然后才能重新运行 `mlflow ui`。可以使用以下命令完成：

```
sudo fuser -k 5000/tcp
```

## MLflow 组件

MLflow 分为四个组件：

- MLflow 跟踪
- MLflow 项目
- MLflow 模型
- MLflow 注册表

这些组件的设计旨在无缝协同工作；但是，您可以根据需要自由使用单个组件。例如，您可以使用 MLflow 提供模型而无需使用跟踪组件。

以下图显示了 MLflow 的组件及其主要作用：

![](img/cc4299656808e62a294f1843a1e18e72_107_0.png)

图 5.5: MLflow 组件

本章将通过示例介绍每个组件的功能。

## MLflow 跟踪

MLflow 跟踪是一种 API 和 UI，用于在运行机器学习代码时记录参数、代码版本、指标和工件，并可视化结果。

MLflow 以运行的形式捕获以下信息，其中每个运行意味着执行一段代码：

- **开始和结束时间：**它记录实验的开始和结束时间。
- **源：**它可以是启动运行的文件名或 MLproject 名称。
- **参数：**它们包含键值对中的数据。这些只不过是您想要捕获的模型输入参数，例如随机森林算法中使用的树的数量。例如，`n_estimators` 是键，其值为 100。您需要调用 MLflow 的 `log_param()` 来存储参数。
- **指标：**指标用于衡量模型的性能，例如模型的准确性。它以键值对的形式保存数据；但是，值应仅为数值。您需要调用 MLflow 的 `log_metric()` 来存储指标。

工件：当您想要存储文件或对象（例如训练好的模型的 pickle 文件）时，工件功能可提供帮助。您可以使用此功能存储序列化的训练模型、图表或 CSV 文件，并可以使用 `log_artifacts()` 调用它。

首先，您必须将文件或对象存储在本地目录中，然后可以通过提供该目录的路径来保存文件或对象。

### 将数据记录到运行中

### mlflow.set_tracking_uri()

它连接到 MLflow 跟踪统一资源标识符 (URI)。默认情况下，跟踪 URI 设置为 mlruns 目录；但是，您可以将其设置为远程服务器 (HTTP/HTTPS)、本地目录路径或 MySQL 等数据库。

```python
1. import mlflow

2. mlflow.set_tracking_uri('http://localhost:5000')
```

### mlflow.tracking.get_tracking_uri()

此函数将返回 MLflow 的当前跟踪 URI。

### mlflow.create_experiment()

它将创建一个新实验。您可以在执行 `mlflow.start_run` 时通过提供实验 ID 来捕获运行。实验名称应为唯一名称。

```python
1. exp_id = mlflow.create_experiment("Loan_Prediction")
```

### mlflow.set_experiment()

此方法激活实验，以便运行将在提供的实验下捕获。如果提到的实验不存在，则会创建一个新实验。默认情况下，实验设置为 'Default'，如图 5.3 所示。

### mlflow.start_run()

它启动一个新运行或返回当前活动的运行。您可以传递当前运行下需要跟踪的运行名称、运行 ID 和实验名称。

```python
1. # For single iteration
2. run = mlflow.start_run()
3.
4. # For multiple iterations
5. with mlflow.start_run(run_name="test_ololo") as run:
```

### mlflow.end_run()

它结束当前活动的运行（如果有）。

### mlflow.log_param()

它在当前活动的运行中记录单个键值参数。键和值均为字符串。使用 `mlflow.log_params()` 一次记录多个参数。

```
1. n_estimators = 100
2. mlflow.log_param("n_estimators:", n_estimators)
```

### mlflow.log_metric()

此 MLflow 函数将跟踪模型指标，例如模型的准确性。要跟踪多个指标，请使用 `mlflow.log_metrics()`。

```
1. accuracy = 0.8
2. mlflow.log_metric("accuracy", accuracy)
```

### mlflow.set_tag()

它以键值对的形式存储数据。在此，您可以设置用于识别或要跟踪的任何特定指标的标签。要设置多个标签，请使用 `mlflow.set_tags()`。

```
1. import mlflow
2. with mlflow.start_run():
3.     mlflow.set_tag("model_version", "0.1.0")
```

### mlflow.log_artifact()

此函数将文件或对象记录或存储在工件目录中；但是，您需要先将其存储在本地目录中，然后才能拉取文件或对象。

```
1. import pandas as pd
2. import mlflow
3.
4. dir_name = 'data_dir'
5. file_name = 'data_dir/cust_sale.csv'
6. data = pd.DataFrame({'Cust_id': [461,462,463], 'Sales': [2631,8462,4837]})
7. data.to_csv(file_name, index=False)
8. mlflow.log_artifacts(dir_name)
```

### mlflow.get_artifact_uri()


它将返回工件根目录的路径，工件存储于此。

```
1. import mlflow
2. mlflow.get_artifact_uri()
3. './mlruns/0/be1cd88ebd704e9ab7629fd364747e1e/artifacts'
```

让我们考虑贷款预测的场景，其目标是预测客户是否符合贷款资格。首先，导入所需的库。

```
1. # Importing required packages
2. import pandas as pd
3. import numpy as np
4.
5. from sklearn.linear_model import LogisticRegression
6. from sklearn.ensemble import RandomForestClassifier
7. from sklearn.tree import DecisionTreeClassifier
8.
9. from matplotlib import pyplot as plt
10.
11. from sklearn import preprocessing
12. from sklearn.model_selection import train_test_split, GridSearchCV
13. from sklearn import metrics
14.
15. import mlflow
```

下一步是加载数据集，并将数值列和类别列的名称分别捕获到独立变量中：

```
1. # Reading the data
2. data = pd.read_csv("loan_dataset.csv")
3. num_col = data.select_dtypes(include=['int64','float64']).columns.tolist()
4. cat_col = data.select_dtypes(include=['object']).columns.tolist()
5. cat_col.remove('Loan_Status')
6. cat_col.remove('Loan_ID')
```

处理类别列和数值列中的缺失值：

```
1. # Creating a list of categorical and numerical variables
2. for col in cat_col:
3.     data[col].fillna(data[col].mode()[0], inplace=True)
4.
5. for col in num_col:
6.     data[col].fillna(data[col].median(), inplace=True)
```

对数值数据将极端值限制在第 5 和第 95 百分位数。

```
1. # Clipping extreme values
2. data[num_col] = data[num_col].apply(lambda x: x.clip(*x.quantile([0.05, 0.95])))
```

创建一个名为 **总收入** 的新特征，它是申请人收入和共同申请人收入之和。

```
1. # creating a new feature as Total Income
2. data['LoanAmount'] = np.log(data['LoanAmount']).copy()
3. data['TotalIncome'] = data['ApplicantIncome'] + data['CoapplicantIncome']
4. data['TotalIncome'] = np.log(data['TotalIncome']).copy()
```

删除申请人收入和共同申请人收入列。

```
1. # Dropping ApplicantIncome and CoapplicantIncome
2. data = data.drop(['ApplicantIncome', 'CoapplicantIncome'], axis=1)
```

使用标签编码技术将类别列转换为数值列。

```
1. # Label encoding categorical variables
2. for col in cat_col:
3.     le = preprocessing.LabelEncoder()
4.     data[col] = le.fit_transform(data[col])
5.
6. data['Loan_Status'] = le.fit_transform(data['Loan_Status'])
```

将数据拆分为训练集和测试集（70:30）。

```
1. # Train test split
2. X = data.drop(['Loan_Status', 'Loan_ID'], 1)
3. y = data.Loan_Status
4.
5. SEED = 1
6.
7. X_train, X_test, y_train, y_test = train_test_split(X,y, test_size = 0.3, random_state = SEED)
```

使用网格搜索交叉验证方法构建逻辑回归模型。

```
1. # Logistic Regression #
2.
3. lr = LogisticRegression(random_state=SEED)
4. lr_param_grid = {
5.     'C': [100, 10, 1.0, 0.1, 0.01],
6.     'penalty': ['l1','l2'],
7.     'solver':['liblinear']
8. }
9.
10. lr_gs = GridSearchCV(
11.     estimator=lr,
12.     param_grid=lr_param_grid,
13.     cv=5,
14.     n_jobs=-1,
15.     scoring='accuracy',
16.     verbose=0
17. )
18. lr_model = lr_gs.fit(X_train, y_train)
```

使用网格搜索交叉验证方法构建决策树模型。

```
1. # Decision Tree #
2.
3. dt = DecisionTreeClassifier(
4.     random_state=SEED
5. )
6.
7. dt_param_grid = {
8.     "max_depth": [3, 5, 7, 9, 11, 13],
9.     'criterion' : ["gini", "entropy"],
10. }
11.
12. dt_gs = GridSearchCV(
13.     estimator=dt,
14.     param_grid=dt_param_grid,
15.     cv=5,
16.     n_jobs=-1,
17.     scoring='accuracy',
18.     verbose=0
19. )
20. dt_model = dt_gs.fit(X_train, y_train)
```

使用网格搜索交叉验证方法构建随机森林模型。

```
1. #___________ Random Forest ___________#
2.
3. rf = RandomForestClassifier(random_state=SEED)
4. rf_param_grid = {
5.     'n_estimators': [400, 700],
6.     'max_depth': [15,20,25],
7.     'criterion' : ["gini", "entropy"],
8.     'max_leaf_nodes': [50, 100]
9. }
10.
11. rf_gs = GridSearchCV(
12.     estimator=rf,
13.     param_grid=rf_param_grid,
14.     cv=5,
15.     n_jobs=-1,
16.     scoring='accuracy',
17.     verbose=0
18. )
19. rf_model = rf_gs.fit(X_train, y_train)
```

创建一个用于评估模型指标的函数。

```
1. # Model evaluation metrics
2. def model_metrics(actual, pred):
3.     accuracy = metrics.accuracy_score(y_test, pred)
4.     f1 = metrics.f1_score(actual, pred, pos_label=1)
5.     fpr, tpr, thresholds1 = metrics.roc_curve(y_test, pred)
6.     auc = metrics.auc(fpr, tpr)
7.     plt.figure(figsize=(8,8))
8.     # plot auc
9.     plt.plot(fpr, tpr, color='blue', label='ROC curve area = %0.2f'%auc)
10.    plt.plot([0,1],[0,1], 'r--')
11.    plt.xlim([-0.1, 1.1])
12.    plt.ylim([-0.1, 1.1])
13.    plt.xlabel('False Positive Rate', size=14)
14.    plt.ylabel('True Positive Rate', size=14)
15.    plt.legend(loc='lower right')
16.
17.    # Save plot
18.    plt.savefig("plots/ROC_curve.png")
19.
20.    # Close plot
21.    plt.close()
22.
23.    return(accuracy, f1, auc)
```

创建一个使用 MLflow 捕获模型参数和模型指标等信息的函数。

```
1. # MLflow's logging functions
2. def mlflow_logs(model, X, y, name):
3.
4. with mlflow.start_run(run_name = name) as run:
5.
6. # Run id
7. run_id = run.info.run_id
8. mlflow.set_tag("run_id", run_id)
9.
10. # Make predictions
11. pred = model.predict(X)
12.
13. # Generate performance metrics
14. (accuracy, f1, auc) = model_metrics(y, pred)
15.
16. # Logging best parameters
17. mlflow.log_params(model.best_params_)
18.
19. # Logging model metric
20. mlflow.log_metric("Mean cv score", model.best_score_)
21. mlflow.log_metric("Accuracy", accuracy)
22. mlflow.log_metric("f1-score", f1)
23. mlflow.log_metric("AUC", auc)
24.
25. # Logging artifacts and model
26. mlflow.log_artifact("plots/ROC_curve.png")
27. mlflow.sklearn.log_model(model, name)
28.
29. mlflow.end_run()
```

对测试数据进行预测，并使用前述函数捕获模型指标和参数。

```
1. # Make predictions using ML models
2.
3. mlflow_logs(dt_model, X_test, y_test, "DecisionTreeClassifier")
4. mlflow_logs(lr_model, X_test, y_test, "LogisticRegression")
5. mlflow_logs(rf_model, X_test, y_test, "RandomForestClassifier")
```

激活虚拟环境：

```
conda activate venv
```

下图显示了在成功创建 conda 环境后的激活和停用命令。

![](img/cc4299656808e62a294f1843a1e18e72_116_0.png)

运行 train.py 文件，它将捕获参数和指标并将工件存储在指定位置。

启动 MLflow UI，然后运行 train.py 文件，如下图所示。

![](img/cc4299656808e62a294f1843a1e18e72_116_1.png)

```
python train.py
```

这不会打印任何内容，因此可以在 MLflow UI 上检查输出。

为演示目的，实现了三种不同的分类器，即逻辑回归、决策树和随机森林，以比较其性能。

下图显示已捕获模型指标、参数、模型名称和运行 ID。总体而言，逻辑回归的准确率为 78.9%，略好于其他模型。

![](img/cc4299656808e62a294f1843a1e18e72_117_0.png)

## 图 5.8：train.py 输出的 MLflow UI

在 **贷款预测** 实验下捕获 MLflow 日志，而不是在 **默认** 实验下。

```
1. # Make predictions using ML models
2. mlflow.set_experiment("Loan_prediction")
3. mlflow_logs(dt_model, X_test, y_test, "DecisionTreeClassifier")
4. mlflow_logs(lr_model, X_test, y_test, "LogisticRegression")
5. mlflow_logs(rf_model, X_test, y_test, "RandomForestClassifier")
```

默认情况下，MLflow 会在名为 **默认** 的实验下捕获信息。但是，你可以直接在命令中指定实验名称，如下所示：

```
python train.py --experiment-name Loan_prediction
```

由于 `train.py` 文件中没有打印语句，此命令不会在终端打印任何输出。





现在，信息正在 **Loan_prediction** 实验下被捕获，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_118_0.png)

图 5.9: 新实验的 Mlflow UI

您可以使用以下命令停用虚拟环境：

```
conda deactivate
```

## MLflow 项目

完成实验阶段后，您的下一步是将所有代码及其依赖项打包为一个项目。假设您想将代码库和依赖项迁移到服务器或另一台机器上；MLflow 将为您完成这项工作。

MLflow 允许您打包代码库及其依赖项，使其可重现且可复用。MLflow 项目提供 API 和 CLI 功能，可帮助您将模型集成到 MLOps 中。

您可以直接从远程 git 仓库运行 MLflow 项目（前提是该仓库应包含所有必要文件）；或者，您也可以从本地 CLI 运行它。

MLproject 文件包含以下字段：

- **名称：** 它是项目名称，可以是任何文本。
- **环境：** 这是执行入口点命令时将使用的环境。它将包含入口点或 MLflow 项目所需的依赖项/包。
- **入口点：** 入口点部分包含在 MLflow 项目环境中要执行的命令。该命令可以接受参数；它是必填字段，不能留空。
- **参数：** 此部分包含入口点命令将使用的一个或多个参数，但它是可选的。

创建 conda.yaml 文件：

```
1. name: Loan_prediction
2.
3. channels:
4.   - defaults
5.
6. dependencies:
7.   - python=3.7
8.   - pip
9.   - pip:
10.    - mlflow
11.    - numpy==1.19.5
12.    - pandas==1.1.5
13.    - matplotlib==3.3.4
14.    - scikit-learn==0.24.2
```

然后，创建 MLproject 文件：

```
1. name: Loan_prediction
2.
3. conda_env: conda.yaml
4.
5. entry_points:
6.   main:
7.     command: “python train.py”
```

切换到 MLproject 文件和 conda 环境所在的目录。找到 YAML 文件并运行：

```
mlflow run .
```

您可以使用 CLI 创建并设置实验名称，如下图所示。

```
mlflow.set_experiment("Loan_prediction")
```

```
(venv) suhas@ds:~/mlb/mlflow$ mlflow experiments create --experiment-name Loan_prediction
Created experiment 'Loan_prediction' with id 1
```

图 5.10: 使用命令创建新实验

```
mlflow run . --experiment-name Loan_prediction
```

下图显示了前面命令的输出：

```
(venv) suhas@ds:~/mlb/mlflow$ mlflow run . --experiment-name Loan_prediction
2021/11/20 00:18:14 INFO mlflow.projects.utils: === Created directory /tmp/tmpkv82_lo6 for downloading remote URIs passed to arguments of type 'path' ===
2021/11/20 00:18:14 INFO mlflow.projects.backend.local: === Running command 'source /home/suhas/miniconda3/bin/../etc/profile.d/conda.sh && conda activate mlflow-b5055c7e7fba84943972ce6c6cd0d8f32c893b5ce 1>&2 && python train.py' in run with ID '40c8762545204d6ca12e726d091876cd' ===
2021/11/20 00:19:23 INFO mlflow.projects: === Run (ID '40c8762545204d6ca12e726d091876cd') succeeded ===
```

图 5.11: ML 项目运行命令的输出

在终端中运行以下命令，从 GitHub 仓库运行 MLproject：

```
mlflow run https://github.com/suhas-ds/mlflow_loan_prediction --experiment-name Loan_prediction
```

下图显示了前面命令的输出：

```
(venv) suhas@ds:~/mlb/mlflow$ mlflow run https://github.com/suhas-ds/mlflow_loan_prediction --experiment-name Loan_prediction
2021/11/20 00:08:47 INFO mlflow.projects.utils: === Fetching project from https://github.com/suhas-ds/mlflow_loan_prediction into /tmp/tmpsre4t5yp ===
Username for 'https://github.com': suhas-ds
Password for 'https://suhas-ds@github.com':
2021/11/20 00:09:20 INFO mlflow.projects.utils: === Created directory /tmp/tmpnb2xuisb for downloading remote URIs passed to arguments of type 'path' ===
2021/11/20 00:09:20 INFO mlflow.projects.backend.local: === Running command 'source /home/suhas/miniconda3/bin/../etc/profile.d/conda.sh && conda activate mlflow-b5055c7e7fba84943972ce6c6cd0d8f32c893b5ce 1>&2 && python train.py' in run with ID '2315c9aba4eb4e43836d83c19355d33e' ===
2021/11/20 00:10:32 INFO mlflow.projects: === Run (ID '2315c9aba4eb4e43836d83c19355d33e') succeeded ===
```

图 5.12: 从 GitHub 运行 ML 项目

您可以看到已创建新实验 **Loan_prediction**，其中捕获了相关信息。

当您打开 **LogisticRegression** 模型的详细信息时，可以看到 Git 提交记录，因为这是直接从 GitHub 运行的。

下图显示了从 GitHub 仓库运行 MLflow 项目后的逻辑回归输出。

![](img/cc4299656808e62a294f1843a1e18e72_121_0.png)

*图 5.13: 逻辑回归结果*

## MLflow 模型

MLflow 模型模块允许您以多种方式打包模型，例如 Python 函数、Scikit-learn (sklearn) 和 Spark MLlib (spark)。这种灵活性帮助您轻松连接相关的下游工具。

当您使用 `mlflow.sklearn.log_model(model, name)` 记录模型时，会创建一个模型目录，用于存储与模型关联的文件和元数据。您将看到以下目录结构：

```
LogisticRegression/
|—— conda.yaml
|—— MLmodel
|—— model.pkl
|—— requirements.txt
```

下图显示了逻辑回归模型的 MLmodel 详细信息：

![](img/cc4299656808e62a294f1843a1e18e72_122_0.png)

图 5.14: MLmodel

现在，让我们按照 **在 Pandas DataFrame 上进行预测** 下的说明进行操作，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_122_1.png)

图 5.15: MLflow 模型

现在，在终端中键入 **python** 打开 Python 控制台。这里的目标是创建一个 pandas DataFrame 并将其传递给 **predict** 函数。您可以从本地目录加载 DataFrame。

下图中，使用 pandas DataFrame 通过 MLflow 模型进行预测。

```
>>> import mlflow
>>> logged_model = 'runs:/ed8ccafef0de642b4ba484d805f0c69ea/LogisticRegression'
>>> loaded_model = mlflow.pyfunc.load_model(logged_model)
>>> import pandas as pd
>>>
>>> # Predict on a Pandas DataFrame
>>> loaded_model.predict(pd.DataFrame([[1.0,0.0,0.0,0.0,0.0,0.0,0.4,0.85203026,360.0,1.0,0.2,0.8,0.67402599]]))
array([[1]])
>>>
```

图 5.16: 使用 MLflow 模型对 pandas DataFrame 进行预测

现在，使用 MLmodel 部署本地 REST 服务器来提供预测服务。

默认情况下，服务器在端口 5000 上运行。如果端口已被占用，您可以使用 --port 或 -p 选项指定不同的端口。

例如，mlflow models serve -m runs:/<RUN_ID>/model --port 1234。

要部署到服务器，请运行以下命令：

```
mlflow models serve -m /home/suhas/mlb/mlflow/mlruns/0cc5b1a8r2a724f4e818b4e92776ca21b73/0/artifacts/LogisticRegression/ -p 1234
```

在前面的命令中，将模型路径替换为您计算机上使用的模型路径，并提供端口 1234 以供运行。

下图中，使用逻辑回归生成的 MLflow 模型已部署：

```
(venv) suhas@ds:~/mlb/mlflow$ mlflow models serve -m /home/suhas/mlb/mlflow/mlruns/0/0cc5b1a8724f4e818b4e92776ca21b73/artifacts/LogisticRegression/ -p 1234
2021/11/19 21:55:17 INFO mlflow.models.cli: Selected backend for flavor 'python_function'
2021/11/19 21:55:16 INFO mlflow.pyfunc.backend: === Running command 'source /home/suhas/mlb/miniconda/bin/... ./etc/profile.d/conda.sh && conda activate mlflow-cpF9596e179ab5335a829b6f7ebebb0275583927d 1>&2 & gunicorn --timeout=60 -b 127.0.0.1:1234 -w 1 ${GUNICORN_CMD_ARGS} -- mlflow.pyfunc.scoring_server.wsgi:app'
[2021-11-19 21:55:17 +0530] [5695] [INFO] Starting gunicorn 20.1.0
[2021-11-19 21:55:17 +0530] [5695] [INFO] Listening at: http://127.0.0.1:1234 (5695)
[2021-11-19 21:55:17 +0530] [5695] [INFO] Using worker: sync
[2021-11-19 21:56:17 +0530] [5705] [INFO] Booting worker with pid: 5705
[2021-11-19 21:56:17 +0530] [5695] [INFO] Handling signal: winch
```

图 5.17: 部署 MLflow 模型

前面的图说明服务器正在 http://127.0.0.1:1234/ 上监听。

使用以下 curl 命令调用 REST API：

```
curl -X POST -H "Content-Type:application/json; format=pandas-split" -d '{"columns":["Gender","Married","Dependents","Education","Self_Employed","LoanAmount","Loan_Amount_Term","Credit_History","Property_Area","TotalIncome"],"data":[[1.0,0.0,0.0,0.0,0.0,0.0,0.4,0.85203026,360.0,1.0,0.2,0.8,0.67402599]]}' http://127.0.0.1:1234/invocations
```



下图显示使用 curl 命令调用已部署模型的 REST API：

```
(venv) suhas@ds:~/mlb/mlflow$ curl -X POST -H "Content-Type:application/json; format=pandas-split" --data '{"columns":["Gender", "Married", "Dependents", "Education", "Self_Employed", "LoanAmount", "Loan_Amount_Term", "Credit_History", "Property_Area", "TotalIncome"],"data":[[1.0,0.0,0.0,0.0,0.0,0.0,4.85203026,360.0,1.0,2.0,8.67402599]]}' http://127.0.0.1:1234/invocations
[1](venv) suhas@ds:~/mlb/mlflow$ 
```

图 5.18：Curl 命令输出

可选，您还可以使用 curl 命令调用已部署模型的 REST API，如下图所示：

```
(venv) ~/mlb/mlflow $ curl http://127.0.0.1:1234/invocations -H "Content-Type:application/json" -d '{
> "columns":["Gender", "Married", "Dependents", "Education", "Self_Employed", "LoanAmount", "Loan_Amount_Term", "Credit_History", "Property_Area", "TotalIncome"],
> "data":[[1.0,0.0,0.0,0.0,0.0,0.0,4.85203026,360.0,1.0,2.0,8.67402599]]}'
```

图 5.19：Curl 命令输出

下图显示不同输入数据集的输出：

```
suhas@suhasVM:~$ curl -X POST -H "Content-Type:application/json; format=pandas-split" --data '{"columns":["Gender", "Married", "Dependents", "Education", "Self_Employed", "LoanAmount", "Loan_Amount_Term", "Credit_History", "Property_Area", "TotalIncome"], "data":[[1.,1.,0.,0.,0.,5.5387689,360.,1.,8.25556865]]}' http://127.0.0.1:1234/invocations
[1]suhas@suhasVM:~$ curl -X POST -H "Content-Type:application/json; format=pandas-split" --data '{"columns":["Gender", "Married", "Dependents", "Education", "Self_Employed", "LoanAmount", "Loan_Amount_Term", "Credit_History", "Property_Area", "TotalIncome"], "data":[[1.,1.,3.,0.,0.,5.06,360.,0.,1.,8.62]]}' http://127.0.0.1:1234/invocations
[0]suhas@suhasVM:~$ suhas@suhasVM:~$ 
```

图 5.20：Curl 命令输出

服务器应返回类似于 [0] 或 [1] 的输出。

此处，[0] 标记为 No，[1] 标记为 Yes。

## MLflow 注册表

MLflow 注册表是一个通过 UI 和一组 API 来存储和管理 ML 模型的平台。

它跟踪模型血统、不同版本以及模型从一种状态到另一种状态的转换（例如，从预发布环境到生产环境）。每个授权的团队成员都可以跟踪上述所有信息。

要探索此组件，需要将数据库连接到 MLflow。之前探索过的 MLflow 组件可以连接到数据库以存储信息。

使用以下命令设置 MLflow 的跟踪 URI：

```
export MLFLOW_TRACKING_URI=http://localhost:5000
```

## 为 MLflow 设置 MySQL 服务器

如果尚未安装 MySQL 服务器，可以自行安装。为此，您也可以参考 https://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en/ 上的官方文档。

首先，使用以下命令在 MySQL 中创建 mlflow_user：

```
mysql -u mlflow_user
CREATE USER 'mlflow_user'@'localhost' IDENTIFIED BY 'mlflow'
GRANT ALL ON db_mlflow.* TO 'mlflow_user'@'localhost';
FLUSH PRIVILEGES;
```

出现提示时输入密码。

创建并选择数据库：

```
CREATE DATABASE IF NOT EXISTS db_mlflow;
use db_mlflow;
```

要了解哪些用户可以访问 db_mlflow 数据库及其权限，可以执行以下命令：

```
SELECT * FROM mysql.db WHERE Db = 'db_mlflow'\G;
```

下图显示与 db_mlflow 数据库关联的 mlflow_user 的权限：

![](img/cc4299656808e62a294f1843a1e18e72_126_0.png)

图 5.21：MLflow_user 的权限

安装 MySQLdb 模块：

```
sudo apt-get install python3-mysqldb
```

为 Python 安装 MySQL 客户端：

```
pip install mysqlclient
```

以下是模型注册表的概念和主要功能：

- **已注册模型**：使用 MLflow 的 UI 或 API 注册模型后，该模型即被视为已注册模型。MLflow 的模型注册表会捕获模型版本，并跟踪模型的阶段（例如，生产环境和预发布环境）以及其他元数据。
- **模型版本**：注册模型后，MLflow 的模型注册表会维护每个模型的版本。例如，如果您使用分类模型保存了一个模型名称，则默认会将其分配给版本 1。但是，如果再次使用相同的名称保存该模型，它将被保存为版本 2。
- **模型阶段**：对于每个模型版本，您可以分配不同的阶段，例如预发布、生产环境和存档。但是，不能为同一模型版本分配两个阶段。
- **注释和描述**：您可以为模型添加注释、简短描述和说明。团队成员将通过您添加的描述了解模型。

## 启动 MLflow 服务器

使用 MySQL 作为数据库启动 MLflow 服务器所需的所有步骤均已完成。

要启动 MLflow 服务器，可以使用以下命令：

```
mlflow server --host 0.0.0.0 --port 5000 --backend-store-uri mysql://mlflow_user:mlflow@localhost/db_mlflow --default-artifact-root $PWD/mlruns
```

启动 MLflow 服务器的语法为 mlflow server <args>。在上述命令中，MLflow 将后端存储用作 MySQL 服务器（提供 MLflow 用户名和数据库名称），并将默认工件存储用作 mlruns 目录。

您可以运行 MLproject 并将实验名称作为参数传递（可选）。

```
mlflow run . --experiment-name 'Loan_prediction'
```

在 MLflow UI 中，您可以看到版本列显示字母数字值。模型的指标参数在 Loan_prediction 实验下显示。

下图显示了使用 MySQL 作为后端存储的 Loan_prediction 实验的输出：

![](img/cc4299656808e62a294f1843a1e18e72_127_0.png)

图 5.22：MLflow UI 上的 ML 项目输出

使用 show tables; 命令，您可以看到已创建新表，例如 metrics 和 experiments。请参阅图 5.23 以查看命令的输出：

| db_mlflow 中的表 |
|---------------------|
| alembic_version |
| experiment_tags |
| experiments |
| latest_metrics |
| metrics |
| model_version_tags |
| model_versions |
| params |
| registered_model_tags |
| registered_models |
| runs |
| tags |

图 5.23：MySQL 数据库中的 MLflow 表

让我们使用图 5.24 中显示的命令检查 experiments 表。目前，正在显示的两个实验是 Default 和 Loan_prediction。

| 实验 ID | 名称 | 工件位置 | 生命周期阶段 |
|---|---|---|---|
| 0 | Default | /home/suhas/mlb/mlflow/mlruns/0 | active |
| 1 | Loan_prediction | /home/suhas/mlb/mlflow/mlruns/1 | active |

图 5.24：MySQL 数据库中 MLflow 的实验列表

如果单击顶部的 Models 选项卡，您应该会看到下图。由于模型未注册，该表不包含任何模型信息。

![](img/cc4299656808e62a294f1843a1e18e72_128_0.png)

图 5.25：MLflow 模型的初始 UI

现在，转到 **实验** 选项卡上的运行 ID 并向下滚动；然后，在 UI 中单击模型目录。

如下图所示，**注册模型** 按钮将出现：

![](img/cc4299656808e62a294f1843a1e18e72_129_0.png)

图 5.26：注册模型 按钮

单击 **注册模型** 按钮，将出现一个弹出窗口，如下图所示。在当前情况下，从下拉菜单中选择了 **创建新模型** 选项，并指定了模型名称；不过，您可以为其指定任何可读的名称。最后，单击 **注册** 按钮。

![](img/cc4299656808e62a294f1843a1e18e72_129_1.png)

图 5.27：注册模型窗口

如下图所示，**注册模型** 按钮将更改为模型名称（带超链接）。

![](img/cc4299656808e62a294f1843a1e18e72_129_2.png)

图 5.28：已注册模型

现在，您应该在 **模型** 选项卡上看到已注册模型。默认情况下，它将被标记为版本 1。由于未分配状态，您应该在预发布和生产环境列中看到 –（短横线）。





下图显示了已注册模型的列表：

![](img/cc4299656808e62a294f1843a1e18e72_130_0.png)

### 图 5.29: MLflow Models UI 中的已注册模型

可以使用 MLflow UI 或终端更改模型的状态。这里，状态正在使用 MLflow 的 UI 被更改为暂存。

如下图所示，模型的状态正在从 **无** 更改为 **暂存**：

![](img/cc4299656808e62a294f1843a1e18e72_130_1.png)

### 图 5.30: 已注册模型的状态转换

如下图所示，您可以看到它在已注册模型的暂存列中显示 **版本 1**。

![](img/cc4299656808e62a294f1843a1e18e72_131_0.png)

### 图 5.31: 已注册模型的状态已过渡到暂存

已注册模型的信息可以在 MySQL 的 **registered_models** 表中找到，如下图所示：

| name | creation_time | last_updated_time | description |
|------|---------------|-------------------|-------------|
| Prediction_model_LR | 1633282534977 | 1633282535089 | |

### 图 5.32: MySQL 表中的已注册模型列表

在团队中工作时，可以为已注册模型添加描述和标签。这有助于其他团队成员了解更多有关模型的信息。

## 现在，为 **Prediction_Model_LR** 添加描述和标签。

![](img/cc4299656808e62a294f1843a1e18e72_131_1.png)

### 图 5.33: 已注册模型的标签和描述

您已学习如何在 MLflow 中注册模型，现在您将学习如何为给定数据提供模型以进行预测。

使用以下命令从 MLflow 注册表中部署模型：

```
mlflow models serve -m "models:/Prediction_model_LR/Staging"
```

- 1. import mlflow.pyfunc
- 2.
- 3. model_name = "Prediction_model_LR"
- 4. stage = 'Staging'
- 5. model=mlflow.pyfunc.load_model(model_uri=f"models:/{model_name}/{stage}")
- 6.
- 7. model.predict([[1.,1.,0.,1.,0.,4.55387689,360.,1.,2.,8.25556865]])
- 8. array([1])

注意：您可以使用 Postman 调用模型的 REST API，如下图所示。

![](img/cc4299656808e62a294f1843a1e18e72_132_0.png)

### 图 5.34: 使用 Postman 调用已部署模型的 REST API

您可以从以下链接获取 Postman：

https://www.postman.com/downloads/

有多种方式可以使用已部署模型的 REST API。您也可以在其他应用程序中使用此 REST API。

## 结论

本章解释了 MLflow 在 ML 生命周期和生产环境中的重要性。您探索了 MLflow 的角色、功能和用法，并举例说明了 MLflow 的四个组件。然后，您学习了 MLflow 如何在 ML 生命周期的各个阶段帮助数据科学开发人员。MLflow 追踪允许通过跟踪模型指标、使用的超参数和其他有用信息来选择最佳模型。MLflow 项目组件帮助您管理依赖项，并且可以从 GitHub 仓库运行。MLflow 注册表充当已注册模型的中心位置，并用于更改状态，例如暂存和生产。

在下一章中，您将学习如何使用 Docker 在一台机器到另一台机器或服务器之间传输 ML 项目时实现可移植性。

## 要点

- MLflow 可帮助您从 ML 项目的实验阶段一直到部署阶段。
- 除了模型注册表之外，所有组件都可以在不与类似 MYSQL 的数据库集成的情况下使用；但是，将它们与类似 MYSQL 的数据库集成是一种良好实践。
- 默认情况下，MLflow 项目使用 conda 安装依赖项；但是，您可以使用 –no-conda 选项在不使用 conda 的情况下继续。
- 每个 MLflow 组件都可以单独访问；但是，您可以将它们连接起来以创建工作流。

## 多项选择题

- 1. 以下哪一项不是 MLflow 组件？
- a) MLflow 追踪
- b) MLflow develop
- c) MLflow 模型
- d) MLflow 注册表

- 2. 在 MLflow 注册表中，模型状态从暂存到生产可以使用以下哪项更改？
- a) MLflow 命令
- b) MLflow UI
- c) a 和 b 都是
- d) 模型状态无法从暂存更改为生产

## 答案

- 1. b
- 2. c

## 问题

- 1. 什么是 MLflow？
- 2. `conda.yaml` 文件的作用是什么？
- 3. 提供模型的命令是什么？

## 第 6 章 Docker 与机器学习

## 简介

容器是应用层的一种抽象，可将代码和依赖项打包在一起。多个容器可以在同一台机器上运行并共享 OS 内核。每个运行中的容器在用户空间被视为一个隔离进程。

Docker 自动化了重复且耗时的配置任务，为开发人员节省了时间和精力。Docker 是一个一站式解决方案，包含 UI、API、CLI，最后但同样重要的是，安全性。Docker 运行在 Linux、Windows 和 Mac OS 上。

## 结构

本章讨论以下主题：

- Docker 在机器学习中的作用
- 使用 Docker 的 Hello World
- 创建 Dockerfile
- 构建 Docker 镜像
- 运行 Docker 容器
- Docker 化和部署 ML 模型

## 目标

学习本章后，您应该能够使用 Docker 将 ML 模型构建并部署到生产环境中作为容器或编排服务。您应该能够创建 Dockerfile，其中包含要执行的所有命令。使用 Dockerfile，您应该能够构建和运行 Docker 镜像。您还应该能够使用分离模式在后台运行容器服务。最后，您可以使用 Docker 部署 ML 模型。

## Docker 简介

Docker 是一个容器化平台，用于将应用程序及其依赖项以容器形式打包。它确保所有所需的库和依赖项都包装在隔离环境中，以便应用程序在开发、测试和生产环境中平稳运行。Docker 在开发人员中很受欢迎，因为它轻量、快速、可移植、安全，并且比虚拟机更高效。容器化应用程序在运行 Docker 容器后将立即开始运行。

Docker 有自己的 Docker 注册表，称为 Docker Hub。Docker Hub 允许开发人员通过互联网存储和分发容器镜像。镜像标签使开发人员能够区分镜像。Docker 注册表具有公共和私有仓库。开发人员可以使用 push 命令将容器镜像存储在 Docker Hub 上，并使用 pull 命令检索镜像。

## 它在我的机器上可以运行！

很多时候，代码在您的机器上运行完美，但在另一台机器上运行时会抛出错误。开发人员和数据科学家也会遇到这种情况。原因可能从不同的操作系统到不同的操作系统版本、不同的 Python 版本或依赖项问题不等。因此，当他们面临这个问题时，可能最终会花费大量时间来修复它。使用 Docker，您不应该遇到这些问题，因为 Docker 会打包文件、配置和命令以实现无缝流程。

## 漫长的设置

在生产环境中部署的传统方法需要花费大量时间，因为它需要移动必要的文件、安装依赖项、配置并手动保存输出。很多时候，开发人员需要先设置环境。当您需要为项目的不同阶段重复此过程时，例如开发、预生产和生产，这会更加耗时。手动部署脚本难以管理。

使用 Docker，您可以将所有所需文件放在目录中，并在 Dockerfile 中按顺序写下要执行的配置、操作系统版本和命令。您还可以使用相同的网络连接两个 Docker 容器。此外，您可以使用同一个 Dockerfile 用于开发、预生产和生产。

Docker 确保可重现性、可移植性、易于部署、细粒度更新、轻量级和简单性。

## 设置环境并安装 Docker

您可以参考 https://docs.docker.com/installation 中的说明，在首选操作系统上安装最新的 Docker 维护包，并查看官方 Docker 引擎安装指南 https://docs.docker.com/engine/install/ubuntu/。

## Docker 安装

以下是您可以遵循的在 Ubuntu 机器上安装 Docker 的一般步骤。Docker 引擎安装需要以下 64 位 Ubuntu 版本之一：

- Ubuntu Kinetic 22.10
- Ubuntu Jammy 22.04 (LTS)
- Ubuntu Focal 20.04 (LTS)
- Ubuntu Bionic 18.04 (LTS)

## 卸载旧版本

首先，卸载 Docker 的旧版本（如果有）：

```
sudo apt-get remove docker docker-engine docker.io containerd runc
```

设置存储库：

```
$ sudo apt-get update
$ sudo apt-get install \
ca-certificates \
curl \
gnupg \
lsb-release
```




添加 Docker 的官方 GPG 密钥。

GNU 隐私保护（GPG 或 GnuPG）是一个命令行工具，用于实现公钥加密和验证服务。GPG 在 Linux 中常用于对文件进行数字签名，从而确保软件项目文件的真实性。

```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

使用以下命令设置存储库：

```
$ echo \
"deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/
docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
$(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

## 安装 Docker 引擎

```
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
sudo docker --version
```

以下图显示当前 Docker 版本：

![](img/cc4299656808e62a294f1843a1e18e72_138_0.png)

图 6.1: Docker 版本

在终端中运行以下命令以检查 Docker 服务的状态：

```
sudo systemctl status docker
```

以下图显示前一命令的输出：

![](img/cc4299656808e62a294f1843a1e18e72_138_1.png)

图 6.2: Docker 状态检查

## Docker Compose

Docker Compose 使开发者能够配置并运行多个容器。它从 docker-compose.yml 文件中读取配置。单个 docker-compose up 命令可以启动服务并运行多容器应用程序。另一方面，你可以使用 docker-compose down 命令销毁所有内容。你也可以通过添加 --volumes 标志来删除卷。

你可以使用以下命令安装 Docker Compose：

```
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

以下图显示 Docker Compose 的安装过程：

![](img/cc4299656808e62a294f1843a1e18e72_139_0.png)

授权 docker-compose 执行文件：

```
sudo chmod +x /usr/local/bin/docker-compose
```

最后，验证安装：

```
docker-compose --version
```

以下图显示当前 Docker Compose 版本：

![](img/cc4299656808e62a294f1843a1e18e72_139_1.png)

安装提供以下内容：

- Docker 引擎
- Docker CLI 客户端
- Docker Compose

## 使用 Docker 的 Hello World

这是一个示例 Docker 镜像，用于测试 Docker 是否正常工作。通过运行以下命令，你将创建第一个 Docker 容器：

```
sudo docker run hello-world
```

以下图显示前一命令的执行情况：

![](img/cc4299656808e62a294f1843a1e18e72_140_0.png)

图 6.5: Docker 镜像 - hello-world

它还会生成以下输出，告诉你幕后发生了什么：

生成此消息时，Docker 执行了以下步骤：

- 1. Docker 客户端联系了 Docker 守护进程。
- 2. Docker 守护进程从 Docker Hub 拉取了 "hello-world" 镜像。
  - (amd64)
- 3. Docker 守护进程从该镜像创建了一个新容器，该容器运行生成你当前正在阅读的输出的可执行文件。
- 4. Docker 守护进程将该输出流式传输到 Docker 客户端，然后由客户端将其发送到你的终端。

你执行了 docker run 命令，后跟镜像名称。系统中不存在所需镜像，因此它没有停止后续执行，而是从 Docker Hub 拉取了该镜像。

以下图显示系统中的 Docker 结构。如你所见，Docker 可以在共享相同基础架构的隔离环境中运行多个容器。

![](img/cc4299656808e62a294f1843a1e18e72_141_0.png)

图 6.6: Docker 堆栈

## Docker 对象

使用 Docker 时，你可以创建和使用 Docker 对象，例如镜像、容器、卷和网络。在本章中，你将学习其中一些对象。

## Dockerfile

Dockerfile 可以被视为一组命令或指令，使开发者能够构建 Docker 镜像。这些命令或指令会按顺序执行。它是一个没有扩展名的纯文本文档。

## Docker 镜像

要创建 Docker 容器，需要先创建 Docker 镜像。它存储了运行应用程序所需的所有代码和依赖项，并充当运行容器实例的模板。Docker 镜像可以上传到 Docker Hub，从此处可以将其拉取到服务器或系统中以运行容器。

要查看可用 Docker 镜像的列表，请在终端中执行以下命令：

```
docker images
```

## Docker 容器

当你运行 Docker 镜像时，会创建一个容器实例。你可以使用同一个 Docker 镜像运行任意数量的容器。它是 Docker 生态系统的重要组成部分。Docker 在隔离环境中运行容器。

当开发者运行容器时，一个名为容器层的额外层会自动创建在现有镜像层之上。Docker 容器有自己的读写层，允许开发者对该容器进行特定更改。假设你使用同一个 Docker 镜像运行三个容器，并在其中一个运行中的容器内安装了另一个版本的 Python 包。这不会影响其他容器中 Python 包的现有版本。Docker 使用 Docker 卷来管理 Docker 容器内的数据。

你在镜像或容器中创建的所有文件都是联合文件系统的一部分。但是，数据卷是 Docker 主机文件系统的一部分，并简单地挂载到容器内部。

它在容器创建时初始化。默认情况下，当容器停止时，它不会被删除。数据卷也可以跨容器共享，并且可以以只读模式挂载。

检查所有运行中容器的命令是 `docker ps`。

检查所有运行中和已停止容器的命令是 `docker ps -a`。

### 分离模式

要在后台运行 Docker，请以分离模式运行容器。你可以使用 `-d` 标志以分离模式运行容器。

## Docker 容器网络

通常，Docker 主机包含多个 Docker 容器。Docker 容器还需要与本地和远程容器进行交互和协作，以构建分布式应用程序。桥接网络是 Docker 引擎分配给容器的默认网络接口。

```
docker network ls
```

此命令将显示网络列表及其范围。输出包含以下表头：

NETWORK ID、NAME、DRIVER、SCOPE

要检查任何 Docker 容器的网络详细信息，请使用以下命令，后跟网络 ID：

```
docker network inspect <NETWORK ID>
```

## 端口映射

-p 标志用于将容器端口映射到主机端口。请参考以下示例：

```
docker run -p <myport>:<containerport> nginx
```

> 注意：要观察输出，请使用 docker logs [container_id]。

## 创建 Dockerfile

Dockerfile 遵循简单易懂的结构，即 # 注释，后跟一条指令和一个参数。通常将指令写为大写，以区分指令和参数。

### FROM

- FROM 指令为后续指令设置基础镜像。
- 有效的 Dockerfile 必须包含 FROM 指令。
- FROM 可以在 Dockerfile 中出现多次。

### CMD

- CMD 定义在创建容器时要执行的默认命令。
- CMD 在构建镜像时不会执行。
- 可以在运行时被覆盖。

### RUN

它在当前镜像之上的新层中执行一个命令，并提交结果。

### COPY

COPY 指令从 <src> 复制新文件或目录，并将它们添加到容器文件系统中的 <dest> 路径。

### ENTRYPOINT

这可帮助你将容器配置为可执行文件；它类似于 CMD。ENTRYPOINT 指令最多只能有一条；如果指定了多条，则只有最后一条会被采纳。




## WORKDIR <path>

这将为其后的 RUN、CMD 和 ENTRYPOINT 指令设置工作目录。

## EXPOSE

这将公开容器上的网络端口，容器在运行时将监听这些端口。

## ENV

这将在容器内将环境变量 <key> 设置为 <value>。当从生成的镜像运行容器时，它会将所有信息传递并持久化到容器内运行的应用程序中。

## 构建 Docker 镜像

使用 docker build 命令，用户可以自动化 Docker 构建过程，该过程依次执行多条命令行指令。

docker build 命令从 Dockerfile 和上下文构建镜像：

```
docker build -t ImageName:TagName dir
```

其中：

- -t: 镜像标签
- ImageName: 您想为镜像指定的名称
- TagName: 您想为镜像指定的标签
- dir: Dockerfile 所在的目录

对于当前目录，只需使用 .（句点）：

```
sudo docker build -t myimage:v1 .
```

使用 docker images 命令检查新创建的镜像。

下一步是从新创建的镜像构建容器。

> 注意：要查看针对该镜像运行的所有命令，请执行以下命令 docker history [Image_id]

## 运行 Docker 容器

Docker 容器是 Docker 镜像的运行时实例。docker run 命令可以按如下方式运行 Docker 镜像：

```
docker run --name test -it myimage:v1
```

其中：

- -it: 用于指示您希望以交互模式运行容器。
- --name: 用于为容器命名。
- myimage: 即将运行的镜像名称。
- v1: 镜像的标签。

docker inspect [container_id] 命令将以 JSON 格式填充容器的完整信息。

docker top [container_id] 命令将显示容器内的顶级进程。

以下图示展示了 Docker 容器的生命周期和流程：

![](img/cc4299656808e62a294f1843a1e18e72_145_0.png)

图 6.7: Docker 容器生命周期

## Docker 化并部署机器学习模型

让我们考虑贷款预测的场景，您需要预测客户的贷款是否会被批准。

```
# Importing the required packages
import pandas as pd
import numpy as np
import warnings
warnings.filterwarnings('ignore')
from sklearn.linear_model import LogisticRegression
from sklearn import preprocessing
from sklearn.model_selection import train_test_split
from sklearn import metrics
import joblib
```

之后，加载数据集，并将数值列和类别列的名称分别捕获到单独的变量中，以供下一步使用：

```
# Loading the data
data = pd.read_csv("loan_dataset.csv")
# Missing value treatment (if found)
num_col = data.select_dtypes(include=['int64','float64']).columns.tolist()
cat_col = data.select_dtypes(include=['object']).columns.tolist()
cat_col.remove('Loan_Status')
```

处理类别列和数值列的缺失值：

```
for col in cat_col:
    data[col].fillna(data[col].mode()[0], inplace=True)
for col in num_col:
    data[col].fillna(data[col].median(), inplace=True)
```

### 为数值数据裁剪极端值：

```
# Outlier treatment (if found)
data[num_col] = data[num_col].apply(
    lambda x: x.clip(*x.quantile([0.05, 0.95])))
```

创建一个名为 **TotalIncome** 的新特征，它是申请人收入和共同申请人收入之和：

```
# Creating a new variable
data['TotalIncome'] = data['ApplicantIncome'] +
   data['CoapplicantIncome']
data = data.drop(['ApplicantIncome','CoapplicantIncome'], axis=1)
```

使用标签编码技术将类别列转换为数值列：

```
cat_col.remove('Loan_ID')

# Encoding categorical features
for col in cat_col:
    le = preprocessing.LabelEncoder()
    data[col] = le.fit_transform(data[col])

data['Loan_Status'] = le.fit_transform(data['Loan_Status'])

# Model building
X = data.drop(['Loan_Status', 'Loan_ID'], 1)
y = data.Loan_Status
features = X.columns.tolist()

model = LogisticRegression(solver='lbfgs', max_iter=1000, random_state=1)
model.fit(X, y)

joblib.dump(model, 'LR_model.pkl')
```

现在，在 while 循环中创建一个菜单驱动的预测功能，它将获取用户输入并进行预测：

```
# Menu driven

print("Type 'exit' to terminate.....\n")
print("'''Gender: Female = 0, Male=1
Married: No = 0, Yes = 1
Education: Graduate = 0 , Under-graduate = 1
Self_Employed: No = 0, Yes = 1
Property_Area: Urban = 2, Semiurban = 1, Rural = 0
Loan_Status: No = 0, Yes = 1\n''')

print("'''Pass the data in following sequence separated by comma
Gender, Married, Dependents,Education,Self_Employed,LoanAmount,Loan_Amount_Term,Credit_History,Property_Area,TotalIncome\n''')

# model = joblib.load('LR_model.pkl')

while True:
    user_data=input("Enter your data: ")

    if(user_data=="exit"):
        break

    data = list(map(float, user_data.split(',')))

    # exception handling
    if(len(data)<10):
        print("Incomplete data provided!!")
    else:
        # predicting the value
        predicted_value=model.predict([data])
        print("/___________________/")
        if (predicted_value[0]):
            print("\tCongratulations! your loan approval request is processed")
        else:
            print("\tSorry! your loan approval request is rejected")
        print("/___________________/")
```

接下来，创建一个依赖项的 requirements.txt 文件。

- 1. numpy==1.19.5
- 2. pandas==1.1.5
- 3. scikit-learn==0.24.2
- 4. joblib==1.0.1

现在，为前面的应用程序及其依赖项创建一个 Dockerfile。

```
# STEP 1: Install base image. Optimized for Python
FROM python:3.7-slim-buster

# STEP 2: Upgrading pip
RUN pip install --upgrade pip

# STEP 3: Copying all the files to the app directory
COPY . /app

# STEP 4: Set the working directory to the previously added app directory
WORKDIR /app

# STEP 5: Giving permissions to python file
RUN chmod +x train.py

# STEP 6: Install required python dependencies from the requirements file
RUN pip install -r requirements.txt

# STEP 7: Run the train.py file
ENTRYPOINT ["python"]

CMD ["train.py"]
```

当所有文件都在同一位置时，您可以使用 docker build 命令开始构建 Docker 镜像，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_150_0.png)

图 6.8: Docker 镜像构建已启动

这可能需要几分钟才能完成。完成后，您应该会看到最后一条消息，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_150_1.png)

图 6.9: Docker 镜像已构建

下一步是使用 docker run 命令运行镜像以启动 Docker 容器实例。最后，是时候进行预测了。在从用户处获取输入之前，添加简要说明，在此情况下，输入数据需要按照说明中给出的顺序传递。

使用 -it 标志执行 docker run 命令以交互模式运行镜像，如下图所示：

```
~/docker $
sudo docker run -it loan-pred:v1
Type 'exit' to terminate.....

Gender: Female = 0 , Male=1
Married: No = 0 , Yes = 1
Education: Graduate = 0 , Under-graduate = 1
Self_Employed: No = 0, Yes = 1
Property_Area: Urban = 2, Semiurban = 1, Rural = 0
Loan_Status: No = 0, Yes = 1

Pass the data in following sequence separated by comma
Gender, Married, Dependents,Education,Self_Employed,LoanAmount,Loan_Amount_Term,
Credit_History,Property_Area,TotalIncome
Enter your data: 1.0,0.0,0.0,0.0,0.0,0.0,273,360.0,1.0,2.0,5429
/_______________________________________________/
/   Congratulations! your loan approval request is processed   /
/_______________________________________________/
Enter your data: exit
~/docker $
```

图 6.10: Docker 容器 - 机器学习模型预测

要退出应用程序，用户可以传递 **exit**；这将中断 **while** 循环。

## 常见 Docker 命令

只需在终端中运行 **docker** 命令，您就会获得常用 Docker 命令的列表。您还可以参考 https://docs.docker.com/engine/reference/commandline/docker/ 中的 Docker CLI 命令完整列表。

## 结论

Docker 容器在隔离环境中运行。您了解了 Docker 框架在机器学习生命周期和生产环境中的重要性。在本章中，您探索了 Docker 组件的角色、功能和用法，并附有示例。您还学习了如何创建 Dockerfile 以及在容器中构建和运行镜像。您学习了如何在交互模式下使用 Docker 创建和部署机器学习模型。

下一章将从 REST APIs 开始，并说明如何使用 API 部署机器学习模型。然后，它将介绍 Web 框架，最后，您将学习如何为机器学习模型 API 构建 UI。

## 要点总结

- Docker 是一个容器化平台，用于将应用程序及其依赖项以容器形式打包。





- Docker 确保可重现性、可移植性、易于部署、细粒度更新、轻量和简单性。
- Docker 使用 Docker 卷在 Docker 容器中管理数据。
- 当你运行 Docker 镜像时，会创建一个容器实例。

## 选择题

### 1. 检查 Docker 镜像历史记录的命令是什么？

- a) docker history [Image_id]
- b) docker all commands [Image_id]
- c) docker hist [Image_id]
- d) history [Image_id]

### 2. 以下哪句话是不正确的？

- a) Docker 主机包含多个 Docker 容器。
- b) Docker 容器是 Docker 镜像的运行时实例。
- c) 检查运行中容器的命令是 **docker ps**。
- d) 不能使用 Docker 镜像创建 Docker 容器实例。

## 答案

- 1. a
- 2. d

## 问题

- 1. 什么是 Docker？
- 2. *Dockerfile* 的作用是什么？
- 3. 从 *Dockerfile* 构建 *Docker 镜像* 的命令是什么？

## 加入我们书籍的 Discord 空间

加入本书的 Discord 工作区，获取最新动态、优惠、全球技术动态、新版本发布以及与作者的交流会议：

https://discord.bpbonline.com

![](img/cc4299656808e62a294f1843a1e18e72_152_0.png)

## 第 7 章

## 使用 API 构建 ML Web 应用

### 简介

在使用 Python 开发 Web 应用时，你很可能会使用一个框架。框架是一个库，它在构建可扩展、标准且可投入生产的 Web 应用程序时，能简化开发者的工作。

本章将从 REST API 开始，介绍如何使用 API 部署 ML 模型。接着，它将涵盖不同的 Web 框架，最后说明构建 ML 模型 API UI 的步骤。在本部分结束时，你应该知道如何部署 ML Web 应用。

### 本章内容

本章将讨论以下主题：

- REST API
- FastAPI
- Streamlit
- Flask
- 构建 ML Web 应用

### 学习目标

学完本章后，你应该能够构建和部署基于 ML 的 Web 应用。你还应该能够为 ML 模型创建 API，并通过传递参数来调用它。此外，本章将教你如何使用 FastAPI、Streamlit 和 Flask 框架创建 Web 应用程序。它将介绍如何将 NGINX 和 Gunicorn 与 Flask 集成，以创建自动化的基于 ML 的 Web 应用程序，并且你应该能够熟练使用三种最常用的框架中的任何一种来开发 Web 应用：FastAPI、Streamlit 和 Flask。

### REST API

REST 是 Representational State Transfer（表述性状态转移）的缩写。REST 是一种主要为指导万维网（WWW）架构的开发和设计而创建的架构风格。简单来说，遵循 REST 架构的 Web 服务或 Web API 就是 REST API。

REST 是一种用于创建 API 的模式，这些 API 可用于访问托管在服务器上的图像、视频、文本、JSON 和 XML 等资源。RESTful API 为不同编程语言构建的应用程序之间的通信提供了一个共同平台。请参阅图 7.1：

![](img/cc4299656808e62a294f1843a1e18e72_154_0.png)

图 7.1：REST API

关于 API 有趣的是，客户端不需要知道服务器端执行的内部操作，反之亦然。REST API 将用户请求/处理的任何数据都视为资源；它可以是文本、图像、视频等等。

REST API 是无状态的；这意味着每次调用 API 时，客户端都应在请求中提供所有参数。服务器不会存储客户端随请求传递的先前参数。

### FastAPI

FastAPI 是一个用于在 Python 中开发 RESTful API 的 Web 框架。FastAPI 是一个轻量级（与 Django 相比）、易于安装、易于编码且高性能的框架。它使得用最少的代码即可开发 REST API。FastAPI 自带标准且交互式的文档。开发并运行 API 后，你可以在 {API endpoint}/docs 或 {API endpoint}/redoc 处访问应用程序的文档。

注意：FastAPI 要求 Python 3.6 及以上版本

让我们安装 FastAPI 和 uvicorn（一个用于生产环境的 Asynchronous Server Gateway Interface (ASGI) 服务器）。

```
pip install fastapi uvicorn
```

让我们考虑一个贷款预测场景，其目标是预测客户的贷款是否会被批准。重点不在于超参数调优和模型优化。不过，你可以优化模型以提高其整体性能。

```
1. # Importing the required packages
2. import pandas as pd
3. import numpy as np
4. import warnings
5. warnings.filterwarnings('ignore')
6. from sklearn.ensemble import RandomForestClassifier
7.
8. from sklearn import preprocessing
9. from sklearn.model_selection import train_test_split
10. from sklearn import metrics
11. import pickle
```

加载数据集，并将数值列和分类列的名称分别捕获到单独的变量中，以便下一步使用：

```
1. # Loading the data
2. data = pd.read_csv("loan_dataset.csv")
3. # Capturing numerical and categorical column names
4. num_col = data.select_dtypes(include=['int64','float64']).columns.tolist()
5. cat_col = data.select_dtypes(include=['object']).columns.tolist()
6. cat_col.remove('Loan_Status')
```

要处理缺失值，可以用众数替换分类缺失值，用中位数替换数值缺失值。

```
1. # Missing value treatment (if found)
2. for col in cat_col:
3.     data[col].fillna(data[col].mode()[0], inplace=True)
4.
5. for col in num_col:
6.     data[col].fillna(data[col].median(), inplace=True)
```

与其从数值数据中删除极端值（异常值），不如将它们下限封顶在 5%、上限封顶在 95%。

换句话说，低于 5% 分位数的数据点将被 5% 分位数处的值替换，而高于 95% 分位数的数据点将被 95% 分位数处的值替换。

```
1. # Outlier treatment (if found)
2. data[num_col] = data[num_col].apply(
3.     lambda x: x.clip(*x.quantile([0.05, 0.95])))
```

创建一个新特征 TotalIncome，即申请人收入和共同申请人收入之和。

```
1. # Creating a new variable
2. data['TotalIncome'] = data['ApplicantIncome'] +
data['CoapplicantIncome']
3. data = data.drop(['ApplicantIncome','CoapplicantIncome'], axis=1)
```

使用标签编码技术将分类列转换为数值列。目标列 Loan Status 将被编码为数值。

```
1. cat_col.remove('Loan_ID')
2.
3. # Encoding categorical features
4. for col in cat_col:
5.     le = preprocessing.LabelEncoder()
6.     data[col] = le.fit_transform(data[col])
7.
8. data['Loan_Status'] = le.fit_transform(data['Loan_Status'])
```

现在，你将使用随机森林分类器构建一个 ML 模型，并将训练好的模型存储在 pickle 对象中。在这里，你可以使用其他 ML 算法和不同的 ML 技术（如 GridSearchCV）来提高准确率。在这里，你将构建一个基准 ML 模型。

```
1. # Model building
2. X = data[['Gender', 'Married', 'TotalIncome', 'LoanAmount','Credit_History']]
3. y = data['Loan_Status']
4. features = X.columns.tolist()
5.
6. model = RandomForestClassifier(max_depth=4, random_state = 10)
7. model.fit(X, y)
8.
9. # saving the model
10. pickle_model = open("trained_model/model_rf.pkl", mode = "wb")
11. pickle.dump(model, pickle_model)
12. pickle_model.close()
13.
14. # loading the trained model
15. pickle_model = open('trained_model/model_rf.pkl', 'rb')
16. model_rf = pickle.load(pickle_model)
17.
18. prediction = model_rf.predict([[1, 1, 6000, 150, 0]])
19. print(prediction)
```

接下来，为依赖项创建一个 requirements.txt 文件。

- 1. numpy==1.19.5
- 2. pandas==1.1.5
- 3. scikit-learn==0.24.2

现在，创建一个 loan_pred_app.py 文件。首先，加载依赖项并 pickle 训练好的模型对象。此外，创建一个 FastAPI 实例并将其分配给 app。这将使 app 成为创建 API 时的交互点。

```
1. # Importing Dependencies
2. from fastapi import FastAPI
3. from pydantic import BaseModel
4. import uvicorn
5. import pickle
6. import numpy as np
7. import pandas as pd
8.
9. app = FastAPI()
10. # Loading the trained model
11. trained_model = 'trained_model/model_rf.pkl'
12. model = pickle.load(open(trained_model, 'rb'))
```

创建一个名为 LoanPred 的类，用于定义客户端预期的输入数据类型。

你将使用 LoanPred 类作为数据模型，用于定义从用户那里预期的数据类型。它继承自 BaseModel。然后添加根视图，该函数在主页上返回 'message': 'Loan Prediction App'。

```
1. class LoanPred(BaseModel):
2. Gender: float
3. Married: float
4. ApplicantIncome: float
5. LoanAmount: float
6. Credit_History: float
7.
```



```python
@app.get('/')
def index():
    return {'message': 'Loan Prediction App'}
```

以下函数将创建用于用户输入的 UI。这里，**/predict** 类作为端点（也称为路由）创建。然后，将数据模型（即 **LoanPred** 类）作为参数传递给 **predict_loan_status()** 函数。

```python
# Define the function, which will make the prediction using the input data provided by the user
@app.post('/predict')
def predict_loan_status(loan_details: LoanPred):
    data = loan_details.dict()
    gender = data['Gender']
    married = data['Married']
    income = data['ApplicantIncome']
    loan_amt = data['LoanAmount']
    credit_hist = data['Credit_History']

# Make predictions
prediction = model.predict([[gender,married,income,loan_amt,credit_hist]])

if prediction == 0:
    pred = 'Rejected'
else:
    pred = 'Approved'

return {'status':pred}

if __name__ == '__main__':
    uvicorn.run(app, host='127.0.0.1', port=8000)
```

现在，是时候运行应用并查看 FastAPI 自动生成的标准 UI 了，它使用 Swagger，现在称为 OpenAPI。

```bash
uvicorn loan_pred_app:app --reload
```

上述命令可解释如下：

- loan_pred_app 是创建 API 的文件名。
- app 是其中定义的实例。
- --reload 会在每次对 app 文件进行更改时重新启动 FastAPI 服务器。

下图显示了运行上述命令后的终端输出：

![](img/cc4299656808e62a294f1843a1e18e72_160_0.png)

图 7.2: 在终端中运行 FastAPI 应用

当终端上显示“Application startup complete”时，打开浏览器并访问终端中提到的路径。在此示例中，路径为 127.0.0.1:8000。

下图显示了浏览器中 FastAPI 应用的 UI。此处显示的文本消息为“Loan Prediction App”。

![](img/cc4299656808e62a294f1843a1e18e72_160_1.png)

图 7.3: 终端中的 FastAPI 应用

下图显示了浏览器中 FastAPI 应用的 Swagger（OpenAPI）UI。只需在 URL 末尾添加 /docs，即可查看应用的自动生成文档。

![](img/cc4299656808e62a294f1843a1e18e72_161_0.png)

图 7.4: FastAPI 应用的文档

FastAPI 提供数据类型验证功能。它在运行时检测无效的数据类型，并将错误输入返回给客户端，从而最终减少开发人员端的异常管理负担。

下图显示了客户端预期数据的架构和数据类型。由于上述模型中有五个变量，它们连同各自的数据类型都可以在图中看到。

![](img/cc4299656808e62a294f1843a1e18e72_161_1.png)

图 7.5: FastAPI 应用的架构

下图探索了应用的 **predict()**。此处输入了客户端预期的示例 JSON 输入。默认情况下，架构中所有变量的值均为零。为预先测试应用，您需要单击 **试试看** 按钮。

![](img/cc4299656808e62a294f1843a1e18e72_162_0.png)

图 7.6: FastAPI 应用的 Predict()

单击 **试试看** 按钮后，您可以以 JSON 格式传递变量值或数据。*图 7.7* 显示了用户为给定变量提供的数据。最后，单击底部的 **执行** 按钮，即可查看 API 返回的预测结果。

![](img/cc4299656808e62a294f1843a1e18e72_162_1.png)

图 7.7: predict 函数中的参数传递

下图显示了以 JSON 格式显示在 **响应正文** 下的预测结果。根据提供的数据，贷款的预测状态将作为 'Approved' 返回。您还可以运行 **curl** 命令在终端中获取输出。响应代码 **200** 表示请求已成功且无任何错误。

![](img/cc4299656808e62a294f1843a1e18e72_163_0.png)

图 7.8: FastAPI 的预测结果

## Streamlit

Streamlit 是一个 Python 开源库，使用户能够为机器学习模型构建和共享吸引人的 UI。它附带了丰富的文档，用于学习和探索。使用 Streamlit，您只需几行代码即可添加精美的交互式小部件来获取用户输入，例如下拉选择框和用于更改值的滑块。

根据其开发者的说法，Streamlit 是构建 ML 应用并将其部署到云上的最快方式。它是使用 Python 部署 ML 应用的绝佳框架。在 Streamlit 中，一切都可以使用 Python 编码，无需任何 JavaScript 等前端技能即可为应用开发惊艳的 UI。Streamlit 是一个将 Python 代码转换为交互式应用的框架，使数据科学家能够快速构建基于数据和模型的应用。

让我们使用以下命令安装 Streamlit：

```bash
pip install streamlit
```

使用以下命令验证 Streamlit 安装：

```bash
streamlit hello
```

现在，为基于 ML 的 Streamlit 应用创建 streamlit_app.py 文件：

```python
import pickle

import streamlit as st

# Loading the trained model
trained_model = 'trained_model/model_rf.pkl'
model = pickle.load(open(trained_model, 'rb'))

@st.cache()
```

以下函数将基于前端接收到的输入进行预测：

```python
# The following function will make the prediction based on data provided by the user

def prediction(Gender, Married, ApplicantIncome, LoanAmount, Credit_History):

    # Pre-processing user input
    if Gender == "Male":
        Gender = 1
    else:
        Gender = 0

    if Married == "Unmarried":
        Married = 1
    else:
        Married = 0

    if Credit_History == "Unclear Debts":
        Credit_History = 1
    else:
        Credit_History = 0

    # Making predictions
    prediction = model.predict([[Gender, Married, ApplicantIncome, LoanAmount, Credit_History]])

    if prediction == 0:
        pred = 'Rejected'
    else:
        pred = 'Approved'
    return pred
```

以下是一个包含 Streamlit 代码的函数，它负责从用户处获取输入数据并显示模型的预测结果：

```python
# The Following function is to define the home page of the streamlit application

def main():

    # Front-end view for the app
    html_temp = """
    <div style ="background-color:green;padding:1px">
    <h1 style ="color:black;text-align:center;">
    Loan Prediction App
    </h1>
    </div>
    """

    # display the front-end aspect
    st.markdown(html_temp, unsafe_allow_html = True)

    # Following code is to create a box field to get user data
    Gender = st.selectbox('Gender',("Male","Female"))
    Married = st.selectbox('Marital Status',("Unmarried","Married"))
    ApplicantIncome = st.number_input("Applicants monthly income")
    LoanAmount = st.number_input("Total loan amount")
    Credit_History = st.selectbox('Credit_History',("Unclear Debts", "No Unclear Debts"))
    result = ""

    # When Predict button is clicked it will make the prediction and display it
    if st.button("Predict"):
        result = prediction(Gender, Married, ApplicantIncome, LoanAmount, Credit_History)
        st.success('Your loan is {}'.format(result))

    if __name__=='__main__':
        main()
```

打开终端，在 streamlit_app.py 文件所在位置运行以下命令：

```bash
streamlit run streamlit_app.py
```

或

```bash
streamlit run streamlit_app.py &>/dev/null&
```

图 7.9 显示了 Streamlit 应用的前端。此处，预测基于用户提供的数据。

![](img/cc4299656808e62a294f1843a1e18e72_167_0.png)

图 7.9: Streamlit 应用

要将 Streamlit 应用部署到 Streamlit Cloud，可以使用 Streamlit Sharing。将包含 requirements.txt 文件的文件上传到 GitHub。在其网站 https://streamlit.io/cloud 上创建帐户，然后提供 GitHub 链接和 Streamlit 应用文件。这将把您的应用部署到 Streamlit Cloud 上。

## Flask

Flask 是一个 Web 框架，允许您使用 Python 构建 Web 应用程序。与 Django 相比，它是一个轻量级框架。它遵循 REST 架构。您可以使用 Flask 开发简单的 Web 应用程序，因为它需要较少的基础代码。Flask 基于 Web 服务器网关接口 (WSGI) 和 Jinja2 引擎。





要启动 Flask 应用程序，需要使用 **run()** 函数。如果在 **run()** 函数中设置 **debug=True**，则可以轻松跟踪错误。启用调试模式后，每次在应用文件中进行更改并保存时，服务器都会重新启动。如果发生错误，浏览器本身会显示原因。但是，在生产环境中部署模型时不应使用此功能。

在 Flask 中，可以调用 CSS 或 JavaScript 等静态文件来渲染应用的网页。**route()** 函数指导 Flask 访问函数调用的 URL。

```
pip install Flask
```

要在终端中运行 Flask 应用程序，请转到 *app.py* 和其他所需文件所在的目录：

```
python app.py
```

创建一个 *index.html* 文件，使用以下 HTML 代码为用户构建前端。这将使用户能够通过 UI 提供输入数据。

```
<html>
<head>
<title>LOAN PREDICTION</title>
</head>
<body>
<h2 align="center">LOAN PREDICTION</h2>
<br/>
<form action="/predict" method="POST">
<table align="center" cellpadding = "10">
<!----- First Name ------------------------------->
<tr>
<td>FIRST NAME</td>
<td>
<input type="text" name="First_Name" maxlength="30"
placeholder="characters a-z A-Z"/>
</td>
</tr>
<!----- Last Name ------------------------------->
<tr>
<td>LAST NAME</td>
<td>
    <input type="text" name="Last_Name" maxlength="30"
placeholder="characters a-z A-Z" />
</td>
</tr>
<!---- Gender -------------------------------------------------------->
<tr>
<td>GENDER</td>
<td>
    <input type="radio" name="gender" id="gender"
    value="1">Male</input>
</td>
</tr>
<!---- Marital Status -------------------------------------------------------->
<tr>
<td>MARRIED</td>
<td>
    <input type="radio" name="married" id="married" value="1">
Yes </input>
</td>
</tr>
<!------ Income ---------------------------------------------------------------->
<tr>
<td>TOTAL INCOME</td>
<td>
    <input type="text" name="total_income" maxlength="30"
    placeholder="$(thousands)" />
</td>
</tr>
<!----- Loan Amount ------->
<tr>
<td>LOAN AMOUNT</td>
<td>
    <input type="text" name="loan_amt" maxlength="30"
    placeholder="$(thousands)" />
</td>
</tr>
<!----- Credit History ------->
<tr>
<td>CREDIT HISTORY</td>
<td>
    <input type="radio" name="credit_history" id="credit_history"
    value="1"> Yes </input>
    <input type="radio" name="credit_history" id="credit_history"
    value="0"> No </input>
</td>
</tr>
<!----- Submit and Reset ------->
<tr>
    <td colspan="2" align="center">
        <input type="submit" value="Submit">
        &nbsp;&nbsp; <!---- to add extra space ---->
        <input type="reset" value="Reset" onclick="location.href='/';">
    </td>
</tr>
</table>
</form>
<h3 align="center"> {{ prediction }} </h3>
</body>
</html>
```

在此，result.html 文件将向用户显示预测输出：

```
<!doctype html>
<html>
<body>
<h1>{{ prediction }}</h1>
</body>
</html>
```

现在，为 Flask 应用程序创建 app.py 文件：

```
# Importing Dependencies
from flask import Flask,render_template,url_for,request
import pandas as pd
from sklearn.ensemble import RandomForestClassifier
import numpy as np
import pickle
import os
```

下一步是加载序列化模型对象以进行预测：

```
app = Flask(__name__)
port = int(os.environ.get("PORT", 80))
# Loading the trained model
pickle_in = open('trained_model/model_rf.pkl', 'rb')
model = pickle.load(pickle_in)
```

现在，为 Flask 应用程序创建视图。以下代码将渲染 HTML 模板，该模板将是 Flask 应用程序的主页。app.route('/') 将路由到主页 URL；尾随斜杠 '/' 通常用作主页的惯例。

```
# Views
@app.route('/')
def home():
    return render_template('index.html')
```

现在，为 predict() 函数创建视图。app.route('/predict') 将路由到主页 URL。POST 方法类型允许您向服务器发送数据以更新或创建目标资源。

```
@app.route('/predict', methods=['POST'])
def predict():
    if request.method == 'POST':
        # Fetch Value for Gender
        gender = request.form['gender']
        if gender == "Female":
            gender = int(0.0)
        if gender == "Male":
            gender = int(1.0)

        # Fetch Value for Married
        married = request.form['married']
        if married == "No":
            married = int(0.0)
        if married == "Yes":
            married = int(1.0)

        # Fetch value for LoanAmount
        loan_amt = float(request.form['loan_amt'])

        # Fetch value for Total_Income
        total_income = float(request.form['total_income'])

        # Fetch value for Prior Credit_Score
        credit_history = request.form['credit_history']
        if credit_history == "No":
            credit_history = int(0.0)
        if credit_history == "Yes":
            credit_history = int(1.0)

        to_predict_list = [gender, married, total_income, loan_amt, credit_history]
        prediction_array = np.array(to_predict_list, dtype=np.float32).reshape(1, 5)

        # Making Predictions using the trained model
        prediction = model.predict(prediction_array)
        prediction_value = prediction[0]

        if int(prediction_value) == 1:
            status="Congratulations! your loan approval request is processed"
        if int(prediction_value) == 0:
            status="Sorry! your loan approval request is rejected"

        return render_template('index.html',prediction = status)
```

添加错误处理功能，如下所示：

```
@app.errorhandler(500)
def internal_error(error):
    return "500: Something went wrong"

@app.errorhandler(404)
def not_found(error):
    return "404: Page not found",404
```

最后，您将按如下所示定义主函数：

```
if __name__ == '__main__':
    app.run(host='0.0.0.0', port=port)
```

## Gunicorn

Gunicorn 是用于运行 Python 应用的应用服务器。Gunicorn 兼容 WSGI，因此可以与多个 WSGI 应用程序进行通信。在当前情况下，Gunicorn 将从 Nginx 接收的请求转译给 Flask 应用，反之亦然。

要安装 Gunicorn，请执行以下命令：

```
sudo apt-get install gunicorn3
```

转到 app.py 文件所在的目录并运行：

```
gunicorn3 app:app
```

此命令有助于了解 Gunicorn 使用的 IP 和端口。在此情况下，端口为 8000，IP 可以是 0.0.0.0 或 127.0.0.1。

## NGINX

NGINX 是一款高性能、高度可扩展的开源反向代理 Web 服务器。它可以对应用程序实例进行负载平衡和缓存。它接受传入连接并决定它们接下来应去往何处。在当前情况下，它位于 Gunicorn 之上。

要安装 NGINX，请执行以下命令：

```
sudo apt-get install nginx
```

您可以使用以下命令检查 NGINX 的状态：

```
sudo service nginx status
```

现在，转到以下路径：

```
cd /etc/nginx/sites-enabled/
```

> 注意：NGINX 配置文件没有任何扩展名，每行都应使用分号 (;) 结尾。

为 Flask 应用创建新配置文件：

```
sudo nano flask_app
```

然后，添加以下代码片段并保存文件：

```
server{
    listen 80;
    server_name 0.0.0.0;

    location / {
        proxy_pass http://unix:/home/suhas/webapi/flask/flaskapp.sock;
    }
}
```

在此，您正在指示 NGINX 监听端口 **80**。在 location 块中，使用 **proxy_pass** 将请求传递到套接字。更改 NGINX 文件后，使用以下命令重新启动 NGINX 服务：

```
sudo service nginx restart or sudo systemctl restart nginx
```

您可以使用以下命令检查 NGINX 的状态：

```
sudo service nginx status
```

转到 _app.py_ 文件所在的目录，并运行以下命令以启动 Gunicorn 服务器：

```
gunicorn3 app:app
```

在浏览器中打开新选项卡，在地址栏中输入 IP。您应该能看到 Flask 应用已启动并运行。





## 在后台创建并运行服务：

创建一个 **systemd** 单元文件，使 Ubuntu 启动系统在每次服务器启动时自动启动 Gunicorn 并提供 Flask 应用程序。

首先，使用以下命令进入系统目录：

```
cd /etc/systemd/system
```

接下来，你需要为 Flask 应用创建一个服务

```
sudo nano flaskapp.service
```

然后，将以下命令添加到其中并保存：

```
[Unit]
Description=Flaskapp Gunicorn Service
After=network.target

[Service]
User=suhas
Group=www-data
WorkingDirectory=/home/suhas/webapi/flask

ExecStart=/usr/bin/gunicorn3 --workers 3 --bind unix:flaskapp.sock -m 007 app:app
Restart=on-failure
RestartSec=10

[Install]
WantedBy=multi-user.target
```

在上述服务中，你指示 Gunicorn 启动三个工作进程，之后可以进行更新。然后，创建并链接 UNIX 套接字文件。在当前场景中，**007** 用于访问，以便套接字文件允许所有者和组访问并限制其他人。然后，传递应用程序的文件名。

```
sudo systemctl daemon-reload
```

```
sudo service flaskapp restart
```

运行上述命令重启 **flaskapp** 服务，你应该会看到应用程序目录中创建了 *flaskapp.sock* 文件。

以下图示显示客户端发送的请求首先到达 NGINX。接下来，它传递到 Gunicorn 服务器；Gunicorn 将其翻译并传递给 Flask 应用，然后再返回给客户端。

![](img/cc4299656808e62a294f1843a1e18e72_177_0.png)

图 7.10：客户端-服务器交互

如果一切顺利，打开浏览器并在地址栏中输入 IP。你应该能看到应用程序正在运行。

以下图示显示浏览器中运行的贷款预测应用程序。提供用户数据。

## 贷款预测

| 名字 | Sam |
| 姓氏 | Potter |
| 性别 | 男 女 |
| 已婚 | 是 否 |
| 总收入 | 6000 |
| 贷款金额 | 150 |
| 信用记录 | 是 否 |
| | 提交 重置 |

图 7.11：在 Flask 应用中传递参数

以下图示显示在提供用户数据并点击 **提交** 按钮后的预测结果。

![](img/cc4299656808e62a294f1843a1e18e72_178_0.png)

**图 7.12：预测结果**

## 结论

本章演示了如何使用最常用的框架（即 FastAPI、Streamlit 和 Flask，以及 NGINX 和 Gunicorn）开发基于机器学习的 Web 应用程序。你创建了一个用户友好且简单的 UI 以接收用户输入数据，并学习了 REST API；它在客户端和服务器之间工作。本章还简要介绍了每个框架的突出特点。

下一章将讨论为 PC 和 Android 设备构建原生应用程序。

## 要点总结

- RESTful API 为与使用不同编程语言构建的应用程序进行通信提供了一个共同平台。
- FastAPI 要求 Python 3.6 及以上版本。
- Streamlit 是一个 Python 开源库，使用户能够为机器学习模型构建和共享吸引人的 UI。
- FastAPI 自带标准且交互式的文档。
- NGINX 配置文件没有扩展名，每一行都应使用分号（;）结束。

## 选择题

- 1. 如何验证 streamlit 的安装？
  - a) streamlit hello
  - b) streamlit hello world
  - c) streamlit run test
  - d) streamlit --

- 2. 可以使用以下哪项在浏览器中查看 FastAPI 应用程序的文档？
  - a) /docs
  - b) /redoc
  - c) 两者都是
  - d) 无法访问

## 答案

- 1. a
- 2. c

## 问题

- 1. 什么是 NGINX？
- 2. Gunicorn 的作用是什么？
- 3. 运行 streamlit 应用程序的命令是什么？

## 加入我们书籍的 Discord 空间

加入本书的 Discord 工作区，获取最新动态、优惠、全球技术动态、新版本发布以及与作者的会话：

https://discord.bpbonline.com

![](img/cc4299656808e62a294f1843a1e18e72_179_0.png)

## 第 8 章
构建原生机器学习应用

## 简介

为了以原生应用程序的形式使用机器学习模型，应为用户构建 GUI。在本章中，你将学习使用 Tkinter 和 Kivy 包构建原生应用程序，这些应用程序可以分别转换为 Windows 和 Android 设备的桌面应用程序。

Python 提供多种构建 **图形用户界面（GUI）** 的方式，GUI 是包含主窗口、按钮、小部件、输入字段等的应用程序。最终用户可以与其交互，并根据其操作和输入查看响应。Python 有多种 GUI 框架或工具包可供使用。

## 结构

本章讨论以下主题：

- Tkinter 简介
- 使用 Tkinter 构建基于机器学习的应用程序
- 使用 Pyinstaller 将 Python 应用程序转换为 Windows EXE 文件
- kivy 简介
- 使用 kivy 和 kivyMD 构建基于机器学习的应用程序
- 使用 Buildozer 将 Python 应用程序转换为 Android 应用程序

## 目标

学习本章后，你应该能够构建和部署基于机器学习的原生应用程序，例如 Windows 和 Android 应用程序。本章分为两个部分。在第一部分结束时，你应该能够熟练使用 Tkinter 开发基于机器学习的 Windows 应用程序。你也可以将 Python 应用程序转换为独立的 Windows 可执行文件。在第二部分结束时，你应该能够开发基于 kivy 的机器学习应用程序，并使用 Buildozer 包将其转换为 Android 应用程序。

## Tkinter 简介

Tkinter 是在 Python 许可证下发布的免费软件。

Tkinter 是 Tk GUI 库的 Python 接口。Tk 源自 **工具命令语言（TCL）**，它是一种脚本语言。最棒的是，你不需要显式安装 Tkinter，因为自 1994 年起它已随 Python 一起提供。

Tkinter 使开发人员能够轻松创建小部件（GUI 元素），这些小部件包装在 Tk 工具包中。使用小部件，开发人员可以创建按钮、菜单和输入字段以获取用户数据。这些小部件可以链接到 Python 功能、方法、数据或其他小部件。

例如，按钮小部件可用于在单击事件时执行某个操作，或者它可以调用函数并将用户数据作为参数传递。

> 注意：通过安装 Python 3.7 或更高版本获取最新版本的 Tkinter。

你可以使用以下命令验证 Tkinter 的安装：

```
python -m tkinter
```

将出现一个弹出窗口，如下所示，其中包含 TCL/Tk 版本和文本“This should be a cedilla: ç”。

![](img/cc4299656808e62a294f1843a1e18e72_182_0.png)

图 8.1：Tkinter

注意：音节符是书写在字母 'ç' 下方的符号，用于法语、葡萄牙语和其他一些语言中，表示发音类似于字母 's'。

## 使用 Tkinter 构建 Hello World 应用程序

让我们创建一个基本的 Tkinter 应用程序，以了解 Tkinter 功能。以下代码创建一个简单的应用程序，显示 Hello World 文本，并带有用于关闭应用程序的 Exit 按钮。

```
from tkinter import *
win = Tk()

a = Label(win, text = "Hello World")
a.pack()

b=Button(win, text='Exit', command=tk.destroy)
b.pack()

win.mainloop()
```

在上述代码中，首先导入 tkinter 包，并使用 Tk() 为应用程序创建主窗口，其中 win 是使用 Tk() 创建的主窗口对象的名称。Label() 小部件用于显示文本或图像，win 参数用于表示应用程序的父窗口。

pack() 将小部件组织在块中（例如按钮和标签）。如果你不组织小部件，你的应用程序仍会运行，但该小部件将不可见。Button() 小部件用于添加按钮，这里用于关闭 Tkinter 应用程序。当用户单击 Exit 按钮时，Tkinter 应用程序窗口将关闭。最后，mainloop() 用于保持应用程序运行并执行用户命令。

以下图示显示上述代码的输出。它是一个带有标签和按钮的简单 Tkinter 应用程序。

![](img/cc4299656808e62a294f1843a1e18e72_183_0.png)

图 8.2：使用 Tkinter 构建的 Hello World 应用程序





- Tkinter 易于使用，可快速开发桌面应用程序。
- Tkinter 及其小部件的语法易于理解。
- Tkinter 随 Python 一起提供，因此您无需显式安装它。
- Tkinter 是开源的且可免费使用。

## 使用 Tkinter 构建基于 ML 的应用

这里，您需要开发用于数据加载、数据清洗、特征工程、模型构建，最后将训练好的模型保存为 pickle 等序列化对象的 Python 代码。然后，您可以使用训练好的模型在 Tkinter 应用上获得预测。

让我们考虑一个贷款预测场景，目标是预测客户的贷款是否会被批准。重点不在于超参数调整和模型优化。但是，您可以优化模型以提高其整体性能。首先，按如下方式创建 train.py 文件：

```
# Import the required packages
import pandas as pd
import numpy as np
import warnings
warnings.filterwarnings('ignore')
from sklearn.ensemble import RandomForestClassifier

from sklearn import preprocessing
from sklearn.model_selection import train_test_split
from sklearn import metrics
import pickle
```

接下来的步骤，加载数据集并将数值列和分类列的名称分别捕获到单独的变量中。

```
# Load the data
data = pd.read_csv("loan_dataset.csv")
# Missing value treatment (if found)

4. num_col = data.select_dtypes(include=['int64','float64']).columns.tolist()

5. cat_col = data.select_dtypes(include=['object']).columns.tolist()

6. cat_col.remove('Loan_Status')
```

为处理缺失值，您可以使用众数替换分类缺失值，使用中位数替换数值缺失值。

```
1. # Missing value treatment (if found)

2. for col in cat_col:

3. 	data[col].fillna(data[col].mode()[0], inplace=True)

4.

5. for col in num_col:

6. 	data[col].fillna(data[col].median(), inplace=True)
```

与其从数值数据中删除极端值（异常值），不如将其下限限制在 5%，上限限制在 95%。

换句话说，低于 5% 分位数的数据点将被替换为 5% 分位数的值，而另一方面，高于 95% 分位数的数据点将被替换为 95% 分位数的值。

```
1. # Outlier treatment (if found)

2. data[num_col] = data[num_col].apply(

3. 		lambda x: x.clip(*x.quantile([0.05, 0.95])))
```

在许多情况下，联合申请人收入不可用。创建一个名为 TotalIncome 的新特征，它是申请人收入和联合申请人收入的总和。

```
1. # Create a new variable

2. data['TotalIncome'] = data['ApplicantIncome'] + data['CoapplicantIncome']

3. data = data.drop(['ApplicantIncome', 'CoapplicantIncome'], axis=1)
```

您应避免将 Gender 和 Married（婚姻状态）等文本数据传递给模型。使用标签编码技术将分类特征转换为数值特征。目标列 Loan Status 将被编码为数值。

```
1. cat_col.remove('Loan_ID')

2.

3. # Encode categorical features

4. for col in cat_col:

5.     le = preprocessing.LabelEncoder()

6.     data[col] = le.fit_transform(data[col])

7.

8. data['Loan_Status'] = le.fit_transform(data['Loan_Status'])
```

现在，您将使用随机森林分类器构建 ML 模型，并将训练好的模型存储在 pickle 对象中。在这里，您可以使用其他 ML 算法和不同的 ML 技术，例如 GridSearchCV，来提高准确性。在这里，您将构建一个基准 ML 模型。

```
1. # Model building

2. X = data[['Gender', 'Married', 'TotalIncome', 'LoanAmount','Credit_History']]

3. y = data['Loan_Status']

4. features = X.columns.tolist()

5.

6. model = RandomForestClassifier(max_depth=4, random_state = 10)

7.

8. model.fit(X, y)

9.

10. # save the model

11. pickle_model = open("trained_model/model_rf.pkl", mode = "wb")

12. pickle.dump(model, pickle_model)

13. pickle_model.close()

14.

15. # Load the trained model

16. pickle_model = open('trained_model/model_rf.pkl', 'rb')

17. model_rf = pickle.load(pickle_model)

18.

19. prediction = model_rf.predict([[1, 1, 6000, 150, 0]])

20. print(prediction)
```

## Tkinter 应用

完成前面的部分后，您应该有一个训练好的模型的 pickle 对象，它将由 Tkinter 应用使用。在这里，您需要导入两个包，即 **tkinter** 用于构建 GUI，以及 **joblib** 用于加载 pickle ML 模型对象。

创建一个 Python 文件并将其命名为 ml_app.py。

导入 **tkinter** 模块以创建 Tkinter 桌面应用程序。

```
1. from tkinter import *

2.

3. import joblib

4.

5. trained_model = 'E:/tkinter_ml_app/trained_model/model.pkl'

6. model = joblib.load(trained_model)
```

为 ML 应用定义 **MyWindow** 类。在此类中，添加 Tkinter 小部件用于 GUI，并添加 **predict()** 函数以根据用户输入进行预测。在以下代码中，输入字段的标签已使用 **Label()** 小部件创建。

```
1. class MyWindow:

2. def __init__(self, win):

3. # Create a text Label

4. self.lbl0=Label(win, text="Loan Prediction App", font=(25))

5. self.lbl0.pack(pady=10)

6. self.lbl1=Label(win, text='Gender')

7. self.lbl2=Label(win, text='Married')

8. self.lbl3=Label(win, text='Total Income')

9. self.lbl4=Label(win, text='Loan Amount')

10.     self.lbl5=Label(win, text='Credit History')

11.     self.lbl6=Label(win, text='Loan Status')
```

下一步是使用 **Entry()** 小部件为前述字段声明输入框。在此，声明可选参数 **bd**，即输入框 **Entry()** 小部件内部的边框。

**insert()** 小部件在给定位置插入文本。**0**（零）是第一个字符，因此它在开头插入默认文本。

**bind()** 的语法如下：
**widget.bind(event, handler)**

在当前情况下，一个输入小部件通过 **bind()** 链接到 **FocusIn** 事件。这意味着特定的输入小部件已获得焦点，即当给定输入小部件中光标处于活动状态时，它应该执行 **bind()** 内部定义的 lambda 函数。lambda 函数用于在用户单击输入小部件时立即删除其内容。

使用 **Button()** 创建 **Predict** 按钮。

```
1.     # Create an entry widget to accept the user input

2.     self.t1=Entry(bd=2)

3.     self.t1.insert(0, "0:F, 1:M")

4.     self.t1.bind("<FocusIn>", lambda args: self.t1.delete('0', 'end'))

5.

6.     self.t2=Entry(bd=2)

7.     self.t2.insert(0, "0:No, 1:Yes")

8.     self.t2.bind("<FocusIn>", lambda args: self.t2.delete('0', 'end'))

9.

10.    self.t3=Entry(bd=2)

11.    self.t3.insert(0, "E.g. 6000")

12.    self.t3.bind("<FocusIn>", lambda args: self.t3.delete('0', 'end'))

13.

14.   self.t4=Entry(bd=2)

15.   self.t4.insert(0, "E.g. 150")

16.   self.t4.bind("<FocusIn>", lambda args: self.t4.delete('0', 'end'))

17.

18.   self.t5=Entry(bd=2)

19.   self.t5.insert(0, "0:Clear Debts, 1:Unclear Debts")

20.   self.t5.bind("<FocusIn>", lambda args: self.t5.delete('0', 'end'))

21.

22.   self.t6=Entry(bd=2)

23.

24.   # Create a Predict button

25.   self.btn1 = Button(win, text='Predict')
```

Tkinter 带有三个几何管理器：grid、place 和 pack。几何管理器的作用是将小部件排列在特定位置。与其他两个几何管理器相比，place 几何管理器为您提供了更大的灵活性。您可以声明小部件的垂直和水平位置。以下代码提及了每个小部件（包括 **Predict** 按钮）的垂直和水平位置。

```
1.    # Organize widgets appropriately

2.    self.lbl1.place(x=100, y=50)

3.    self.t1.place(x=200, y=50)

4.

5.    self.lbl2.place(x=100, y=100)

6.    self.t2.place(x=200, y=100)

7.

8.    self.lbl3.place(x=100, y=150)

9.    self.t3.place(x=200, y=150)

10.

11.   self.lbl4.place(x=100, y=200)

12.   self.t4.place(x=200, y=200)
```





14. self.lbl5.place(x=100, y=250)
15. self.t5.place(x=200, y=250, width=165)
17. self.b1=Button(win, text='Predict', command=self.predict, fg='blue')
18. self.b1.place(x=170, y=300)
20. self.lbl6.place(x=100, y=350)
21. self.t6.place(x=200, y=350)

最后，定义 **predict()** 以使用基于用户输入的 ML 模型进行预测。

```
1. # For making predictions
2. def predict(self):
3. self.t6.delete(0, 'end')
4. gender = float(self.t1.get())
5. married = float(self.t2.get())
6. income = float(self.t3.get())
7. loan_amt = float(self.t4.get())
8. credit_hist = float(self.t5.get())
9. prediction = model.predict([[gender, married, income, loan_amt, credit_hist]])[0]
10. if prediction == 0:
11. pred = 'Rejected'
12. else:
13. pred = 'Approved'
15. self.t6.insert(END, str(pred))
```

类声明至此完成。

使用 Tk 类创建主窗口并调用 mainloop() 以保持窗口显示。

此外，在调用 mainloop() 之前，应用程序窗口不会出现在屏幕上，因为它会获取所有对象和小部件并将其呈现在屏幕上。

```
1. window=Tk()
2.
3. mywin=MyWindow(window)
4.
5. # Create a title
6. window.title('ML App')
7.
8. # Define the size of the window
9. window.geometry("400x400+10+10")
10.
11. window.mainloop() #Keep the window displaying
```

为 Tkinter 应用创建 ml_app.py 文件并运行它。它应根据给定输入进行预测。

## 将 Python 应用转换为 Windows EXE 文件

现在，您可以按照以下步骤使用 PyInstaller 将此 Tkinter - ML 应用转换为 Windows 可执行应用程序。PyInstaller 将 Python 应用程序及其依赖项打包为单个包，无需安装 Python 解释器即可独立运行。

让我们创建虚拟环境并安装所有必需的依赖项。

此处，使用 conda 创建了 Python 3.7 版本的虚拟环境，如下所示：

```
conda create -n envv_tkinter python=3.7 -y
```

创建后，使用以下命令激活它：

```
source activate envv_tkinter
```

> 注意：要删除 conda 环境，可以执行以下命令 conda env remove -n envv_tkinter：

```
pyinstaller --noconfirm --onefile --windowed --icon "E:/tkinter_ml_app/python_104451.ico" --add-data "E:/tkinter_ml_app/trained_model/model.pkl;." --hidden-import "sklearn" --hidden-import "sklearn.ensemble._forest" --hidden-import "sklearn.neighbors._typedefs" --hidden-import "sklearn.utils._weight_vector" --hidden-import "sklearn.neighbors._quad_tree" "E:/tkinter_ml_app/ml_app.py"
```

前面的命令将基于 Python 的 Tkinter 应用转换为可用于预测的 Windows 可执行文件。

其中：

- -y, --noconfirm：在不询问确认的情况下替换输出目录
- -F, --onefile：创建单文件捆绑可执行文件
- -D, --onedir：创建包含 Windows 可执行文件的单文件夹捆绑包
- --add-data：要添加到可执行文件的其他非二进制文件或文件夹
- -c, --console, --nowindowed：为标准 I/O 打开控制台窗口（默认）
- -w, --windowed, --noconsole：用于不为标准 I/O 提供控制台窗口
- --hidden-import MODULENAME：用于命名脚本代码中不可见的导入；此选项可多次使用

有关更多详细信息，请参阅：
https://pyinstaller.org/en/stable/usage.html

执行前面的命令后，以下图显示状态消息。它显示 EXE 文件创建成功消息。

![](img/cc4299656808e62a294f1843a1e18e72_192_0.png)

图 8.3：将 Python 应用转换为 Windows 应用

现在，打开 dist 文件夹中位于 ml_app.exe 文件。

以下图显示基于 ML 的 Tkinter 应用的文件和文件夹：

```
__pycache__
build
data
dist
trained_model
ml_app
ml_app.spec
python_104451
Readme
requirements
train
```

图 8.4：Tkinter ML 应用

打开应用；您应该会看到 Tkinter 应用的窗口。它应根据用户输入显示预测。

以下图显示基于用户提供数据的预测：

![](img/cc4299656808e62a294f1843a1e18e72_193_0.png)

图 8.5：Tkinter ML 应用

## 使用 kivy 和 kivyMD 构建基于 ML 的应用

在本节中，使用本章前面生成的训练模型的 pickle 对象，让我们在远程服务器（即 Heroku）上开发和部署 FastAPI 端点。您将在即将到来的章节中学习如何在带有 CI / CD 管道的 Heroku 平台上部署 ML 模型。

此外，您还可以使用任何其他托管服务（例如 PythonAnywhere 或 Amazon EC2）部署此 FastAPI 应用。在当前场景中，远程端点用于在 Kivy 应用中进行预测。

因此，每当用户在 kivy 应用中传递数据并按下 **Predict** 按钮时，它会将参数发送到 API 端点，该端点会将接收到的参数传递给模型对象，并反过来将预测发送到 API。Kivy 应用将获取 API 提供的输出（预测）。

让我们按如下所示安装 FastAPI 和 uvicorn（用于生产的 **ASGI（异步服务器网关接口）**服务器）：

```
pip install fastapi uvicorn
```

注意：FastAPI 要求 Python 3.6+

现在，创建一个 `app.py` 文件。首先，加载依赖项并对训练模型的对象进行 pickle 处理。另外，创建一个 FastAPI 实例并将其分配给 app。因此，在创建 API 时，app 将是交互点。

```
1. # Import dependencies
2. from fastapi import FastAPI
3. from pydantic import BaseModel
4. import uvicorn
5. import pickle
6. from fastapi.middleware.cors import CORSMiddleware
7.
8. app = FastAPI()
9.
10.origins = ["*"]
11.
```

```
12. app.add_middleware(
13.     CORSMiddleware,
14.     allow_origins=origins,
15.     allow_credentials=True,
16.     allow_methods=["*"],
17.     allow_headers=["*"],)
18.
19. # Load the trained model
20. trained_model = 'trained_model/model_rf.pkl'
21. # pickle_in = open(trained_model, 'rb')
22. model = pickle.load(open(trained_model, 'rb'))
```

定义类 **LoanPred**，用于定义客户端预期的数据类型。

**LoanPred** 类用于从 **BaseModel** 继承的数据模型。为主页添加一个根视图函数，返回 **'message': '贷款预测应用'**。

```
1. class LoanPred(BaseModel):
2.     Gender: float
3.     Married: float
4.     ApplicantIncome: float
5.     LoanAmount: float
6.     Credit_History: float
7.
8. @app.get('/')
9. def index():
10.     return {'message': 'Loan Prediction App'}
```

以下函数将为用户输入创建 UI。在此，创建 **/predict** 作为端点（也称为路由）。然后，添加所创建数据模型类型的参数，即 **LoanPred**。

```
1. # Defining the function which will make the prediction using the data which the user inputs
2. @app.post('/predict_status')
3. def predict_loan_status(loan_details: LoanPred):
4.     data = loan_details.dict()
5.     gender = data['Gender']
6.     married = data['Married']
7.     income = data['ApplicantIncome']
8.     loan_amt = data['LoanAmount']
9.     credit_hist = data['Credit_History']
10.
11.     # Making predictions
12.     prediction=model.predict([[[gender, married, income, loan_amt, credit_hist]]])
13.
14.     if prediction == 0:
15.         pred = 'Rejected'
16.     else:
17.         pred = 'Approved'
18.
19.     return {'status':pred}
20.
21. @app.get('/predict')
22. def get_loan_details(gender: float, married: float, income: float,
23.                     loan_amt: float, credit_hist: float):
24.     prediction = model.predict([[[gender, married, income, loan_amt, credit_hist]]]).tolist()[0]
25.     print(prediction)
26.     if prediction == 0:
27.         pred = 'Rejected'
28.     else:
```

```
29. pred = 'Approved'
30.
31. return {'status':pred}
32.
33. if __name__ == '__main__':
34. uvicorn.run(app, host='0.0.0.0', port=4000)
```

现在是运行应用并查看 FastAPI 自动生成的标准 UI 的时候了，它使用 swagger（现称为 openAPI）。

```
uvicorn app:app --reload
```

前面的命令可解释如下：

- The app 是创建 API 的文件名。
- The app 是其中定义的实例或文件。
- --reload 会在 app 文件发生更改时简单地重新启动 FastAPI 服务器。

## KivyMD 应用

Kivy 是一个用于快速开发带有简单 GUI 的应用的开源软件库。Kivy 用 Python 编写，因此要使用它，系统中应已安装 Python。与 Tkinter 不同，它未随 Python 预安装；您需要单独安装。

KivyMD 是 kivy 框架的扩展。它是 Material Design (MD) 小部件的集合，主要与 kivy 一起用于 GUI 构建。首先创建虚拟环境是个好主意，因为它有助于轻松维护不同的包。您可以使用以下命令安装 kivy 和 KivyMD：

```
pip install kivy
pip install kivymd
```

使用远程服务器上部署的端点。暂时保持简单。首先导入所需的依赖项。此处，导入 MDApp（一个基础应用）。在此基础应用之上构建应用，因为它负责初始化和启动应用。

然后，为应用的前端导入 Builder 函数。

现在，创建一个名为 main.py 的文件并向其中添加以下代码。首先，将所需的依赖项导入其中。





from kivymd.app import MDApp
from kivy.lang.builder import Builder
from kivy.uix.screenmanager import Screen, ScreenManager
from kivy.core.window import Window
from kivy.network.urlrequest import UrlRequest
import certifi as cf

屏幕是基础，其他组件将放置在其上。它类似于网页。在这里，你可以为屏幕指定一个名称。如下面的代码所示，正在维护一个层次结构。

屏幕管理器主要管理不同的屏幕。让我们来了解每个组件。MDLabel 用于显示文本，具有水平对齐、字体样式等属性。

MDTextField 用于获取用户输入。在此过程中，hint_text 用于在用户向应用输入数据时提供指导。它有一个 id 参数，用于获取用户输入的数据。

MDButton 用于执行操作。在此过程中，它被用来通过 on_press 参数调用 predict() 来完成操作。

```
Builder_string = '''
ScreenManager:
    Main:
<Main>:
    name: 'main'
    MDLabel:
        text: 'Loan Prediction App'
        halign: 'center'
        pos_hint: {'center_y':0.9}
        font_style: 'H4'

    MDLabel:
        text: 'Gender'
        pos_hint: {'center_y':0.75}

    MDTextField:
        id: input_1
        hint_text: '0:Female, 1:Male'
        width: 100
        size_hint_x: None
        pos_hint: {'center_y':0.75, 'center_x':0.50}

    MDLabel:
        text: 'Marital Status'
        pos_hint: {'center_y':0.68}

    MDTextField:
        id: input_2
        hint_text: '0:No, 1:Yes'
        width: 100
        size_hint_x: None
        pos_hint: {'center_y':0.68, 'center_x':0.50}

    MDLabel:
        text: 'Applicant Income'
        pos_hint: {'center_y':0.61}

    MDTextField:
        id: input_3
        hint_text: '6000'
        width: 100
        size_hint_x: None
        pos_hint: {'center_y':0.61, 'center_x':0.50}

MDLabel:
    text: 'Loan Amount'
    pos_hint: {'center_y':0.54}

MDTextField:
    id: input_4
    hint_text: '150'
    width: 100
    size_hint_x: None
    pos_hint: {'center_y':0.54, 'center_x':0.50}

MDLabel:
    text: 'Credit History'
    pos_hint: {'center_y':0.47}

MDTextField:
    id: input_5
    hint_text: '0:Clear Debts, 1:Unclear Debts'
    width: 100
    size_hint_x: None
    pos_hint: {'center_y':0.47, 'center_x':0.50}

MDLabel:
    pos_hint: {'center_y':0.2}
    halign: 'center'
    text: ''
    id: output_text
    theme_text_color: 'Custom'
    text_color: 0, 1, 1, 1

MDRaisedButton:
    pos_hint: {'center_y':0.1, 'center_x':0.5}
    text: 'Predict'
    on_press: app.predict()
'''
```

首先将 **ScreenManager()** 存储到 **sm** 对象中以便访问，然后添加主屏幕小部件。之后，定义 **MainApp** 类（将 **MDApp** 作为基类导入其中），该类保存应用的核心逻辑。定义 **build()** 用于添加文本和输入小部件。**predict()** 将直接从代码中所示的 **id** 获取用户数据。

将这些输入参数提供给远程 API 端点，它将返回其预测结果。

在 Kivy 中，你可以使用 **UrlRequest()** 解析 URL，并使用 **on_success** 参数在请求完成时触发。在当前情况下，使用 **UrlRequest()** 在 API 请求完成时调用 **res()**，它将替换之前定义的 **MDLabel** 的空白文本：**MDRaisedButton**。

```
class Main(Screen):
    pass

sm = ScreenManager()
sm.add_widget(Main(name='main'))

class MainApp(MDApp):
    def build(self):
        self.help_string = Builder.load_string(Builder_string)
        return self.help_string

    def predict(self):
        Gender = self.help_string.get_screen('main').ids.input_1.text
        Married = self.help_string.get_screen('main').ids.input_2.text
        ApplicantIncome = self.help_string.get_screen('main').ids.input_3.text
        LoanAmount = self.help_string.get_screen('main').ids.input_4.text
        Credit_History = self.help_string.get_screen('main').ids.input_5.text
        url = f'https://fastapi-herokuapp.com/predict?gender={Gender}&married={Married}&income={ApplicantIncome}&loan_amt={LoanAmount}&credit_hist={Credit_History}'
        self.request = UrlRequest(url=url, on_success=self.res, ca_file=cf.where(), verify=True)

    def res(self, *args):
        self.data = self.request.result
        ans = self.data
        self.help_string.get_screen('main').ids.output_text.text = ans['status']

MainApp().run()
```

使用 `python main.py` 运行应用，如果一切正常，你应该能看到应用已启动并运行。

下图显示 Kivy 应用已成功运行。

![](img/cc4299656808e62a294f1843a1e18e72_202_0.png)

**图 8.6：** Kivy ML 应用

## 将 Python 应用转换为 Android 应用

现在，你将学习如何使用 Buildozer 包将此应用转换为 Android 应用。在此步骤中，请确保你的 Kivy 文件名为 main.py。你需要先安装 Buildozer 包（如果尚未安装）。

```
pip install buildozer
```

按以下方式安装所需的依赖项：

```
pip install cython==0.29.19
```

```
sudo apt-get install -y \
python3-pip \
build-essential \
git \
python3 \
python3-dev \
ffmpeg \
libsdl2-dev \
libsdl2-image-dev \
libsdl2-mixer-dev \
libsdl2-ttf-dev \
libportmidi-dev \
libswscale-dev \
libavformat-dev \
libavcodec-dev \
zlib1g-dev
```

```
sudo apt-get install -y \
libgstreamer1.0 \
gstreamer1.0-plugins-base \
gstreamer1.0-plugins-good
```

```
sudo apt-get install build-essential libsqlite3-dev sqlite3 bzip2 libbz2-dev zlib1g-dev libssl-dev openssl libgdbm-dev libgdbm-compat-dev liblzma-dev libreadline-dev libncursesw5-dev libffi-dev uuid-dev libbz2-dev
```

```
sudo apt-get install libffi-dev
```

根据系统要求，你可能需要安装其他依赖项。

现在，通过运行以下命令创建 buildozer.spec 文件：

```
buildozer init
```

上述命令将创建一个标准的 buildozer.spec 文件。不过，你需要根据要求对其进行修改。例如，在 **应用程序要求** 部分中，在 requirements 旁边提供依赖项；提供包名、标题和域；在 **权限** 部分中提供互联网权限，等等。

最后，使用以下命令构建并打包 Android 应用：

```
buildozer -v android debug
```

或者，你可以使用 Google Colab 笔记本。

下图显示了 KivyML 应用的文件和目录：

![](img/cc4299656808e62a294f1843a1e18e72_204_0.png)

*图 8.7：Kivy ML 应用*

你已成功构建并运行基于 ML 的 Tkinter 和 Kivy 应用。此外，你还学会了将它们打包为原生应用程序。

## 结论

在本章中，你学习了如何使用最开源的框架：Tkinter、kivy 和 KivyMD 开发 ML 应用程序。你创建了一个用户友好且简单的 UI，用于接收用户输入数据并显示响应。你探索了 Tkinter 和 kivy 的功能，并使用 Pyinstaller 将 Tkinter 应用转换为带有 Windows 可执行文件的桌面应用，使用 Buildozer 将 kivyMD 应用转换为 Android 应用。

在下一章中，你将学习如何为 ML 构建 CI/CD 流水线。

## 要点总结

- Tkinter 预安装随 Python 一起提供。获取最新版本 Tkinter 的最佳方式是安装 Python 3.7 或更高版本。
- KivyMD 是 Kivy 框架的扩展。
- Tkinter 和 Kivy 都是开源且免费使用的。
- MDLabel 用于在 KivyMD 中显示文本。

## 选择题

- 1. 在 Tkinter 中，几何管理器是什么/有哪些？
  - a) Grid
  - b) Place
  - c) Pack
  - d) 以上都是

- 2. Tkinter 中 mainloop() 的用途是
  - a) 保持应用运行
  - b) 执行定义的任何循环
  - c) 两者皆是
  - d) 都不是

## 答案

- 1. a
- 2. d

## 问题

- 1. 什么是 Tkinter？
- 2. pack() 在 Tkinter 中的作用是什么？
- 3. 如何在 Kivy 应用中定义按钮？





## 加入本书的 Discord 空间

加入本书的 Discord 工作区，获取最新动态、优惠、全球技术动态、新版本发布以及与作者的交流活动：

https://discord.bpbonline.com

![](img/cc4299656808e62a294f1843a1e18e72_206_0.png)

## 第 9 章 机器学习的 CI/CD

### 简介

当今，自动化无处不在。通过自动化手动流程，您可以节省时间、精力和成本。自动化的最佳之处在于它能减少人为错误。您可以自动化大部分部分，同时在应用程序中纳入新的更改或更新。

CI/CD 流水线可让您以自动化方式将更新部署到应用程序中。本章将介绍 CI/CD 流水线的要素以及如何为 ML 应用程序利用它。在本章中，您将了解 CI/CD 流水线的不同阶段、它们在 MLOps 中的重要性以及如何构建一个流水线。

### 结构

本章讨论以下主题：

- 机器学习的 CI/CD 流水线
  - 持续集成 (CI)
  - 持续交付/部署 (CD)
  - 持续训练 (CT)
- 构建 CI/CD 流水线的工具和平台
  - Jenkins 简介
  - 使用 GitHub、Docker 和 Jenkins 构建 CI/CD 流水线

## 目标

学习本章后，您应该能够构建 CI/CD 流水线以在生产环境中部署 ML 模型、将 GitHub 与 Jenkins 集成、使用 Jenkins 的作业运行测试并在 Jenkins 中生成测试摘要、构建 Docker 镜像以及使用 Jenkins 运行 Docker 容器。最后，您应该能够将 Jenkins 与电子邮件帐户集成以获取构建和部署状态。

## 机器学习的 CI/CD 流水线

CI/CD 是 **持续集成/持续交付/部署 (CI/CD)** 的缩写。CI/CD 流水线的目的是自动化部署应用程序或发布新软件版本所需的一系列相互关联的步骤。

当向应用程序添加新功能时，任何改进都需要与应用程序集成。然而，这涉及不同的团队，它们执行多项任务并在进入生产阶段之前对其进行验证。大部分情况下，这是一个手动且耗时的过程，可能导致新版本的发布延迟。

CI/CD 流水线有助于自动化测试、为应用程序运行无错误代码、加快部署速度、为开发者节省时间和成本、提高可靠性等等。

CI/CD 流水线可让您快速将更改从开发推送到部署，通常包含四个阶段：

- **提交代码更改**：对文件或代码进行更改后，开发者将更新推送到源代码仓库。这项活动通常由团队完成。CI/CD 流水线使任何团队成员都能检查代码的完整性。因此，代码通过测试后，您可以自动将更改推送到仓库。
- **构建**：在此阶段，它从仓库获取更改以进行构建。它会监视源代码仓库的任何更改。一旦检测到更改，即启动构建过程，并在构建完成后验证构建结果。
- **测试**：测试阶段会在构建之上运行自动化测试，例如单元测试、pytest 和 API 测试。这是 CI/CD 流水线的关键阶段。这可确保代码的整体完整性，并防止任何损坏的代码进入下一阶段。
- 部署：此阶段将更改部署到生产环境。

下图显示了 CI/CD 流水线的不同阶段。但是，组织可以根据其目标进行修改。

![](img/cc4299656808e62a294f1843a1e18e72_209_0.png)

图 9.1: CI/CD 流水线

以下是一些用于 CI/CD 流水线的流行工具：

- Jenkins
- GitHub Actions
- Bamboo
- CircleCI
- GitLab CI/CD
- Travis CI

## 持续集成 (CI)

在持续集成 (CI) 中，开发者团队会先在本地环境中构建、运行和测试代码。如果一切顺利，他们将更新推送到仓库。此后，一系列步骤开始运行，涉及构建、运行和测试阶段。项目成员会在每个步骤中收到通知，并及时获得更新，例如构建结果和测试结果。最后，构件会被存储，当前状态的报告会通过电子邮件发送或通过 Slack 通知。

当开发者团队在同一应用程序上工作时，他们将代码更改推送到仓库。但是，由于环境变化（例如生产环境），代码可能会中断或抛出错误。另一方面，当多个开发者尝试将应用程序的更新推送到中央代码仓库时，更新之间可能会发生冲突。CI 阶段解决了此问题，开发者可以推送将通过定义阶段（如构建、运行和测试）的更改，以确保代码正常运行且无任何问题。但是，如果任何 CI 阶段失败，您将收到通知，且后续流程停止。这样，您可以避免将任何损坏的代码集成到生产环境中。开发者可以频繁推送并检查代码、流程以及代码或应用程序的完整性，然后再将其推送到下一阶段进行部署。

## 持续交付/部署 (CD)

CD 是指持续交付或持续部署（这些术语根据您计划实施的自动化级别互换使用）。CD 阶段取决于 CI 阶段。CI 阶段完成后，它会在流水线中触发 CD 阶段。持续交付 (CD) 阶段的目的是将无错误的代码库或构件交付到预生产环境。在此阶段，您可以添加一系列测试用例（在需要的地方），以确保构建稳定且应用程序功能正常。它会将测试状态报告发送给团队或开发者，然后应用程序会被手动推送到生产环境。如果任何步骤失败，您可能需要根据所需更新重新执行整个流程。

另一方面，持续部署更进一步，能够快速将应用程序从预生产环境部署到生产环境。这消除了将应用程序手动部署到生产环境的步骤。但是，这是可选的，因为它取决于开发者和运维团队根据业务和应用程序的性质选择要实施的自动化级别。

## 持续训练 (CT)

传统 CI/CD 流水线中引入的一个新阶段是持续训练 (CT)。在此阶段，您期望模型在新数据输入或发生任何事件（例如模型准确率降至可接受阈值以下）时持续训练。这可能会给 CI/CD 流水线增加轻微的复杂性，但对于机器学习部署来说至关重要。

在 CI/CD 中，持续训练 (CT) 在 MLOps 中同样重要。模型重新训练取决于场景以及各种其他因素，例如数据变化的频率和输入数据的架构。它还取决于事件，例如准确率降至可接受阈值以下、特定时期（如每周结束）或手动触发。

### Jenkins 简介

Jenkins 是一个用 Java 编写的开源、模块化 CI/CD 自动化工具，带有多个插件。Jenkins 可使用最近更新或开发的代码库，实现构建、测试和部署应用程序的平稳连续流程。它拥有庞大的社区支持，深受开发者欢迎。

如果构建成功，Jenkins 会自动从代码仓库执行一系列步骤，如果一切顺利，它会将应用程序部署到服务器。

以下是 Jenkins 的一些显著特性：

- Jenkins 是一个开源、免费且模块化的工具。
- 它由开发者创建，专为开发者而设。
- Jenkins 安装和配置简单，可安装在 Linux、MacOS 和 Windows 上。
- 大量 Jenkins 插件可用于主流云平台。
- Jenkins 的主节点可以将负载分发到多个从节点，实现更快的处理。

### 安装

Jenkins 可以安装在任何支持 Java 的服务器上，因为它是用 Java 编写的。此处介绍了带有各种选项的 Jenkins 安装。

https://www.jenkins.io/doc/book/

- Docker
- Kubernetes
- Linux
- MacOS
- WAR 文件
- Windows
- 其他系统
- 离线安装
- 初始设置





在 Ubuntu 上安装 Jenkins 时，您可以参考以下链接获取分步安装指南。

https://www.jenkins.io/doc/book/installing/linux/#debianubuntu

## 步骤 1：安装 Jenkins

添加存储库密钥：

```
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
```

将 Debian 软件包存储库地址追加到服务器的 sources.list 中：

```
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
```

执行以下命令，以便 apt 使用最新的存储库：

```
sudo apt update
```

最后，连同其依赖项一起安装 Jenkins：

```
sudo apt install Jenkins
```

## 步骤 2：启动 Jenkins 服务

现在，使用以下命令启动 Jenkins 服务：

```
sudo systemctl start Jenkins
```

要检查 Jenkins 的状态，请使用以下命令：

```
sudo systemctl status Jenkins
```

## 步骤 3：在防火墙中允许 Jenkins 的默认端口

默认情况下，Jenkins 将在其默认端口（即 8080）上运行。因此，需要在防火墙中允许端口 8080。为此，请在终端中运行以下命令：

```
sudo ufw allow 8080
```

然后，要确认此设置，请使用以下命令：

```
sudo ufw status
```

## 步骤 4：设置 Jenkins

您可以使用 Jenkins 的基于 Web 的 UI 服务器 IP 或域名访问 Jenkins：

```
http://<server_ip_or_domain>:8080
```

初始时，您将看到要求输入管理员密码的屏幕；您可以使用以下命令获取该密码：

```
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

从终端复制字母数字密码，并将其粘贴到 **管理员** 密码字段中。

在下一个窗口中，您可以以管理员身份继续，或通过填写表单创建第一个管理员用户。

现在，使用以下命令将 Jenkins 用户添加到 Docker 组中：

```
sudo usermod -aG docker jenkins
```

## 使用 GitHub、Docker 和 Jenkins 构建 CI/CD 管道

此处，Jenkins 用于自动化 ML 工作流。首先，您需要在本地计算机上创建代码库，并在本地运行 ML 应用，以确保其在本地计算机上正常工作。接下来，您将更改推送到 GitHub 仓库。然后，通过 Webhook 将 GitHub 仓库与 Jenkins 集成。Jenkins 将安装在预生产或生产服务器上。Jenkins 将从关联的 GitHub 仓库拉取最新代码库，并在服务器上部署 ML 应用。

### 开发代码库

让我们考虑贷款预测场景，您需要预测客户的贷款是否会被批准。重点不在于超参数调优和模型优化。但是，您可以优化模型以提高其整体性能。

在本章中，您将使用先前开发的机器学习包。

您可以通过以下链接访问代码仓库：

https://github.com/suhas-ds/docker_pkg_jenkins

以下是代码库的目录结构：

```
.
|   Dockerfile
|   main.py
|   requirements.txt
\---src
    |   MANIFEST.in
    |   README.md
requirements.txt
setup.py
tox.ini
+--prediction_model
|   |   pipeline.py
|   |   predict.py
|   |   train_pipeline.py
|   |   VERSION
|   |   __init__.py
|   +---config
|   |   |   config.py
|   |   __init__.py
|   +---datasets
|   |   |   test.csv
|   |   |   train.csv
|   |   __init__.py
|   +---processing
|   |   |   data_management.py
|   |   |   preprocessors.py
|   |   __init__.py
|   \---trained_models
|       classification_v1.pkl
|       __init__.py
\---tests
    pytest.ini
    test_predict.py
```

### main.py

FastAPI 是一种用于在 Python 中开发 RESTful API 的 Web 框架。创建 main.py 文件以运行 FastAPI 应用。

> 注意：FastAPI 需要 Python 3.6+。

```
1. # Importing Dependencies
2. from fastapi import FastAPI
3. from pydantic import BaseModel
4. import uvicorn
5. import pickle
6. import numpy as np
7. import pandas as pd
8. from fastapi.middleware.cors import CORSMiddleware
9. from prediction_model.predict import make_prediction
10. import pandas as pd
```

创建一个 FastAPI 实例并将其分配给 **app**，以便在创建 API 时，**app** 将作为交互点。

```
1. app = FastAPI(
2. 
3.     title="Loan Prediction Model API",
4. 
5.     description="A simple API that uses ML model to predict the Loan application status",
6. 
7.     version="0.1",
8. 
9.     )
```

**CORS（跨源资源共享）** 是指浏览器中运行的前端具有与后端通信的 JavaScript 代码，而后端与前端的来源不同的情况。但是，是否使用它取决于您的应用程序和要求。

```
1. origins = ["*"]
2. 
3. app.add_middleware(
4.     CORSMiddleware,
5.     allow_origins=origins,
6.     allow_credentials=True,
7.     allow_methods=["*"],
8.     allow_headers=["*"],
9.     )
```

定义 **LoanPred** 类，该类定义了客户端预期的数据类型。

您可以使用继承自 `BaseModel` 的 `LoanPred` 类作为数据模型。然后，为主页添加返回 'message': 'Loan Prediction App' 的根视图函数。

```
1. class LoanPred(BaseModel):
2.     Gender: str
3.     Married: str
4.     Dependents: str
5.     Education: str
6.     Self_Employed: str
7.     ApplicantIncome: float
8.     CoapplicantIncome: float
9.     LoanAmount: float
10.    Loan_Amount_Term: float
11.    Credit_History: float
12.    Property_Area: str
13.
14. @app.get('/')
15. def index():
16.     return {'message': 'Loan Prediction App'}
```

此处，创建 `/predict_status` 作为端点（也称为路由）。然后，添加 `predict_loan_status()`，其参数为您创建的 `LoanPred` 类型的数据模型。

```
1.    #Defining the function which will make the prediction using the data
    which the user inputs
2. @app.post('/predict_status')
3. def predict_loan_status(loan_details: LoanPred):
4. data = loan_details.dict()
5. Gender = data['Gender']
6. Married = data['Married']
7. Dependents = data['Dependents']
8. Education = data['Education']
9. Self_Employed = data['Self_Employed']
10. ApplicantIncome = data['ApplicantIncome']
11. CoapplicantIncome = data['CoapplicantIncome']
12. LoanAmount = data['LoanAmount']
13. Loan_Amount_Term = data['Loan_Amount_Term']
14. Credit_History = data['Credit_History']
15. Property_Area = data['Property_Area']
16.
17. # Making predictions
18. input_data = [Gender, Married, Dependents, Education,
19. Self_Employed, ApplicantIncome, CoapplicantIncome,
20. LoanAmount, Loan_Amount_Term, Credit_History, Property_Area]
21. cols = ['Gender','Married','Dependents',
22. 'Education','Self_Employed','ApplicantIncome',
23. 'CoapplicantIncome','LoanAmount','Loan_Amount_Term',
24. 'Credit_History','Property_Area']
25. data_dict = dict(zip(cols,input_data))
26. prediction = make_prediction([data_dict])['prediction'][0]
27.
28. if prediction == 'Y':
29. pred = 'Approved'
30. else:
31. pred = 'Rejected'
32.
33. return {'status':pred}
```

以下函数将创建用户输入的 UI。此处，创建 **/predict** 作为端点（也称为路由），并声明用户预期的输入数据类型。

```
1. @app.post('/predict')
2. def get_loan_details(Gender: str, Married: str, Dependents: str,
3.  Education: str, Self_Employed: str, ApplicantIncome: float,
4.  CoapplicantIncome: float, LoanAmount: float, Loan_Amount_Term: float,
5.  Credit_History: float, Property_Area: str):
6.
7.  input_data = [Gender, Married, Dependents, Education,
8.    Self_Employed, ApplicantIncome, CoapplicantIncome,
9.    LoanAmount, Loan_Amount_Term, Credit_History, Property_Area]
10. cols = ['Gender','Married','Dependents',
11.   'Education','Self_Employed','ApplicantIncome',
12.   'CoapplicantIncome','LoanAmount','Loan_Amount_Term',
13.   'Credit_History','Property_Area']
14.
15. data_dict = dict(zip(cols,input_data))
16. prediction = make_prediction([data_dict])['prediction'][0]
17. if prediction == 'Y':
18.   pred = 'Approved'
19. else:
20.   pred = 'Rejected'
21.
22. return {'status':pred}
23.
24. if __name__ == '__main__':
25. uvicorn.run(app)
```

FastAPI 应用程序文件已完成。

## requirements.txt

现在，按如下方式创建 requirements.txt 文件。在此文件中，模型要求、测试要求和 FastAPI 要求分别定义，以便更好地理解和易于管理。

- 1. # 模型构建要求
- 2. joblib==0.16.0





- 3. numpy==1.19.0
- 4. pandas==1.0.5
- 5. scikit-learn==0.23.1
- 6. scipy==1.5.1
- 7. sklearn==0.0
- 8.
- 9. # testing requirements
- 10. pytest<5.0.0,>=4.6.6
- 11.
- 12. # packaging
- 13. setuptools==40.6.3
- 14. wheel==0.32.3
- 15.
- 16. # FastAPI app requirements
- 17. fastapi>=0.68.0,<0.69.0
- 18. pydantic>=1.8.0,<2.0.0
- 19. uvicorn>=0.15.0,<0.16.0
- 20. gunicorn>=20.1.0

## Dockerfile

创建一个 `Dockerfile`，将其命名为 Dockerfile（不带任何文件扩展名），并向其中添加以下命令。

```
1. FROM python:3.7-slim-buster
2.
3. RUN apt-get update && apt-get install -y \
4.   build-essential \
5.   libpq-dev \
6.   && rm -rf /var/lib/apt/lists/*
7.
8. RUN pip install --upgrade pip
9.
10. COPY . /code
11.
12. RUN chmod +x /code/src
13.
14. RUN pip install --no-cache-dir --upgrade -r /code/requirements.txt
15.
16. EXPOSE 8005
17.
18. WORKDIR /code/src
19.
20. ENV PYTHONPATH "${PYTHONPATH}:/code/src"
21.
22. CMD pip install -e .
```

在前述 Dockerfile 中，它首先会拉取基础镜像，即 Python 3.7 slim buster，并安装必要的软件包。之后，将从要求文件安装软件包，并公开 **8005** 端口，以便可以在 Docker 容器外部访问。最后，它将在 **ENV** 指令中分配 **PYTHONPATH**，并执行 CMD 指令中提到的命令，以可编辑模式安装 Python 包。

## 在 GitHub 上创建个人访问令牌 (PAT)

如果使用 `git cli` 命令执行拉取、推送或克隆等任何操作，则 GitHub 密码将不再可用。事实上，GitHub 已移除密码身份验证。相反，您必须使用 **个人访问令牌 (PAT)**。

PAT 是使用 GitHub API 或命令行进行 GitHub Enterprise Server 身份验证时密码的替代方案。

首先，您需要创建一个 PAT。此过程在以下链接中描述：

https://docs.github.com/en/enterprise-server@3.4/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token

要生成或重新生成 PAT，您可以转到 Settings | Tokens（需要登录）：

https://github.com/settings/tokens

如果系统未提示您输入用户名和密码，您的凭据可能已缓存在本地计算机中。

## 在 GitHub 仓库上创建 Webhook

Webhook 可视为一种轻量级 API，在由特定事件触发后可实现单向数据共享。在 GitHub 中，当对仓库执行推送和拉取等操作时，可以触发 Webhook。借助 GitHub Webhook，您可以在远程服务器上触发 CI 阶段。

转到您的 GitHub 仓库 | Settings | Webhooks。

或者，您可以使用以下 URL 直接跳转到该页面：

```
https://github.com/<username>/<your-repo-name>/settings/hooks
```

在当前情况下，如下所示：

```
https://github.com/suhas-ds/docker_pkg_jenkins/settings/hooks
```

您不能在 GitHub Webhook 的负载 URL 中使用 https://localhost:8080/github-webhook/，因为 localhost URL 需要暴露到互联网上。您可以使用 ngrok 将 localhost URL 暴露到互联网。有关更多详细信息，请参阅 ngrok 官方网站 https://ngrok.com/。

在此，ngrok 仅用于演示目的；但是，在部署阶段可以使用远程服务器的 IP 或域名。

使用命令 ngrok http 8080 将 8080 端口公开暴露。

![](img/cc4299656808e62a294f1843a1e18e72_221_0.png)

图 9.2：ngrok

如下图所示提供负载 URL。负载 URL 格式已在本章前面讨论过。将 **内容类型** 选择为 **application/json** 格式。**密钥** 字段为可选项。目前请留空。

## Webhooks / 管理 Webhook

![](img/cc4299656808e62a294f1843a1e18e72_222_0.png)

图 9.3：GitHub Webhook

如下图所示，选择 **启用 SSL 验证** 和 **仅推送事件** 选项，这样只有在有人向仓库推送更新时才会发送数据。但是，您也可以选择单个事件，即 **让我选择单个事件**。

现在，单击 **添加 Webhook** 按钮以保存 Jenkins GitHub Webhook。

![](img/cc4299656808e62a294f1843a1e18e72_222_1.png)

图 9.4：GitHub Webhook

## 配置 Jenkins

在当前场景中，主要需要配置两个部分：GitHub Webhook 集成和扩展电子邮件集成。

- 1. 转到 Jenkins 控制面板。
- 2. 转到 **管理 Jenkins | 管理插件**。
- 3. 安装 Git、GitHub 和电子邮件插件，无需重启。

如果上述插件已被选中，您可以继续下一步。

现在，让我们在 Jenkins 中配置 GitHub Webhook。

转到 **管理 Jenkins | 配置系统**。

向下滚动并在 **GitHub** 部分中更新 **API URL**，如下所示：

```
https://api.github.com
```

在 **凭据** 部分中，添加上一步生成的 GitHub PAT。您可以将 **名称** 字段留空。

最后，单击 **保存** 按钮。

下图显示了 Jenkins 中的 GitHub Webhook 集成：

![](img/cc4299656808e62a294f1843a1e18e72_223_0.png)

图 9.5：Jenkins 中的 GitHub 配置

现在，每当开发者向仓库推送更新时，Jenkins 都会检测到更改并开始逐个执行一系列命令。

接下来，配置电子邮件以用于反馈循环或状态更新，例如成功或失败。

转到 **管理 Jenkins | 配置系统**。

向下滚动并更新 **GitHub** 部分中的字段。

如下图所示，**默认主题** 字段在开头添加了 **状态**。此外，在 **默认内容** 字段中添加了电子邮件正文。它高度可自定义，因此您可以根据要求进行更新。

![](img/cc4299656808e62a294f1843a1e18e72_224_0.png)

图 9.6：电子邮件配置

在 **默认触发器** 部分中，选择 **始终** 复选框，以便 Jenkins 在成功和失败场景下都发送状态电子邮件，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_224_1.png)

图 9.7：电子邮件配置 - 触发器

现在，在 **默认内容类型** 字段的下拉列表中选择 **HTML (text/html)**，并在 **默认收件人** 中添加您的电子邮件 ID，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_225_0.png)

## 图 9.8：电子邮件配置 – 内容类型和收件人

在扩展电子邮件通知部分中，提供电子邮件通知的详细信息。在当前场景中，提供了 Gmail 详细信息，如下所示：

- smtp.gmail.com 用于 SMTP 服务器
- 465 用于 SMTP 端口
- 添加电子邮件登录凭据
- 选中 **使用 SSL** 复选框
- 单击 **保存** 按钮

如下图所示提供您的电子邮件详细信息：

![](img/cc4299656808e62a294f1843a1e18e72_225_1.png)

## 图 9.9：扩展电子邮件通知

向下滚动并单击 **应用** 和 **保存** 按钮以保存更改，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_226_0.png)

## 图 9.10：扩展电子邮件通知

如果您要为电子邮件通知集成 Gmail 帐户，则需要在 Gmail 帐户设置中允许不够安全的应用。如果处于关闭状态，可以访问以下 URL 将其打开。

https://myaccount.google.com/lesssecureapps

有关更多详细信息，请访问 https://support.google.com/accounts/answer/6010255?hl=en。

Jenkins 所需的配置已完成。

## 使用 Jenkins 创建 CI/CD 管道

现在，您将使用 GitHub 和 Jenkins 构建一个简单的 CI/CD 管道。当开发者向 GitHub 仓库推送更新时，GitHub Webhook 会检测到更改并将通知发送到 Jenkins。Jenkins 从 GitHub 仓库拉取最新代码，构建 Docker 镜像，并使用该镜像运行容器。接下来，它训练模型并从训练好的模型中导出 pickle 对象。在下一步中，pytest 结果会被导出并在 Jenkins 中显示。所有测试通过后，它将运行 ML Web 应用。最后，它将通过电子邮件向开发者或相关团队发送反馈。

![](img/cc4299656808e62a294f1843a1e18e72_226_1.png)

## 图 9.11：使用 Jenkins 构建的 CI/CD 管道





## 阶段 1：1-GitHub-to-container

在此阶段，一旦开发者将更新推送到关联的 GitHub 仓库，Jenkins 将立即从 GitHub 拉取最新代码和文件。让我们逐步了解此过程。

当开发者将更新推送到 GitHub 仓库时，Webhook 检测到变化并被触发。GitHub Webhook 向 Jenkins 发送消息，告知已检测到新更新，随后 Jenkins 拉取最新代码文件以开始构建 Docker 镜像。

如下图所示，从 Jenkins 仪表板左侧面板选择 **新建任务**。

![](img/cc4299656808e62a294f1843a1e18e72_227_0.png)

图 9.12：Jenkins 仪表板 – 新建任务

如下图所示，在 **输入项目名称** 字段中提供作业名称，并选择 **自由风格项目**。在本例中，其名为 1-GitHub-to-docker-container。

![](img/cc4299656808e62a294f1843a1e18e72_227_1.png)

图 9.13：Jenkins 仪表板 – 自由风格项目

如下图所示，在 **源代码管理** 选项卡下选择 **Git** 单选按钮并提供 GitHub 仓库 URL。默认情况下，它将是 **master** 分支，但你可以将其更新。如果你的仓库是私有的，则可能需要为其传递凭据。

![](img/cc4299656808e62a294f1843a1e18e72_228_0.png)

图 9.14：1-GitHub-to-docker-container

如下图所示，在 **构建触发器** 选项卡下选择 **GitHub 钩子触发 GITScm 轮询**，以从 GitHub 仓库拉取最新更新。

![](img/cc4299656808e62a294f1843a1e18e72_228_1.png)

图 9.15：1-GitHub-to-docker-container - 构建触发器

在下图中，正在执行 Docker 命令，以使用 GitHub 仓库的最新更改构建和运行 Docker 镜像。

![](img/cc4299656808e62a294f1843a1e18e72_229_0.png)

图 9.16：1-GitHub-to-container - 构建

如下图所示，一旦更新推送到 GitHub 仓库，Jenkins 便开始构建 Docker 镜像。输出的第一行显示 "Started by GitHub push by suhas-ds"，指明是谁将更新推送到 GitHub 仓库。

### 控制台输出

```
Started by GitHub push by suhas-ds
Running as SYSTEM
Building in workspace /var/lib/jenkins/workspace/1-GitHub-to-docker-container
The recommended git tool is: NONE
No credentials specified
> git rev-parse --resolve-git-dir /var/lib/jenkins/workspace/1-GitHub-to-docker-container/.git # timeout=10
Fetching changes from the remote Git repository
> git config remote.origin.url https://github.com/suhas-ds/docker_pkg_jenkins # timeout=10
Fetching upstream changes from https://github.com/suhas-ds/docker_pkg_jenkins
> git --version # timeout=10
> git --version # 'git' version 2.17.1
> git fetch --tags --progress -- https://github.com/suhas-ds/docker_pkg_jenkins +refs/heads/*:refs/remotes/origin/* # timeout=10
> git rev-parse refs/remotes/origin/master^{commit} # timeout=10
Checking out Revision 70a4d59968d3f499d4fe38e8d180ff3a33650fc8 (refs/remotes/origin/master)
> git config core.sparsecheckout # timeout=10
> git checkout -f 70a4d59968d3f499d4fe38e8d180ff3a33650fc8 # timeout=10
Commit message: "Update"
> git rev-list --no-walk b5635257b0e9c6e43ee0e4b08e2da368110b745 # timeout=10
[1-GitHub-to-docker-container] $ /bin/sh -xe /tmp/jenkins9986791013263554543.sh
+ echo Stage 1
Stage 1
> sudo -S docker build -t loan-pred:v1 .
Sending build context to Docker daemon 241.7kB
```

图 9.17：1-GitHub-to-container - 控制台输出

## 阶段 2：2-training

在此阶段，模型将通过在 Docker 容器内运行 train_pipeline.py 文件在训练数据上进行训练。如下图所示，在 **源代码管理** 选项卡下选择 **无** 单选按钮，因为这是下一阶段，无需再次拉取源代码。

![](img/cc4299656808e62a294f1843a1e18e72_230_0.png)

图 9.18：2-training – 源代码管理

如下图所示，在 **构建触发器** 选项卡下选择 **其他项目构建完成后构建** 选项。接下来，在 **监视的项目** 字段中提供上一阶段的名称。然后，选择第一个单选按钮，即 **仅在构建稳定时触发**，这意味着阶段 2 将仅在上一阶段成功完成后开始执行。

![](img/cc4299656808e62a294f1843a1e18e72_230_1.png)

图 9.19：2-training – 构建触发器

如下图所示，在 **构建** 选项卡下编写用于训练模型管道并导出训练模型最新 pickle 对象的 Docker 命令。

![](img/cc4299656808e62a294f1843a1e18e72_231_0.png)

图 9.20：2-training - 构建

下图显示了阶段 2 的控制台输出。它告诉你是什么触发了阶段 2 以及阶段 2 的状态。之后，Jenkins 在阶段 2 成功完成时触发阶段 3。

### 控制台输出

```
Started by upstream project "1-GitHub-to-docker-container" build number 20
originally caused by:
Started by GitHub push by suhas-ds
Running as SYSTEM
Building in workspace /var/lib/jenkins/workspace/2-training
[2-training] $ /bin/sh -xe /tmp/jenkins5775494677148366096.sh
+ echo Stage 2 --------------------------->
Stage 2 ----------------------------------->
+ sudo docker exec modell python prediction_model/train_pipeline.py
Saved Pipeline : classification_v1.pkl
+ echo Model training completed
Model training completed
Triggering a new build of 3-testing
Finished: SUCCESS
```

图 9.21：2-training - 控制台输出

## 阶段 3：3-testing

在此阶段，Jenkins 正在运行 pytest 并使用 **JUnit** 发布测试结果。Jenkins 理解 XML 格式的 JUnit 测试报告。JUnit 使 Jenkins 能够提供测试结果，包括历史测试结果趋势、失败跟踪（如果有）以及用于查看测试报告的简洁 Web UI。在 **源代码管理** 选项卡下选择 **无** 单选按钮。

如下图所示，在 **构建触发器** 下选择 **其他项目构建完成后构建** 和 **仅在构建稳定时触发**，这表示这是下一阶段，将在上一阶段完成后开始执行。

![](img/cc4299656808e62a294f1843a1e18e72_232_0.png)

图 9.22：3-testing – 构建触发器

如下图所示，在 **构建** 选项卡下，Jenkins 正在使用 Docker 命令在运行中的 Docker 容器内执行测试。接下来，Docker 命令将 pytest 结果导出为 .xml 文件。然后，**mkdir** 命令将创建名为 **reports** 的新目录并将测试结果复制到其中。

![](img/cc4299656808e62a294f1843a1e18e72_232_1.png)

图 9.23：3-testing – 构建

最后，它正在使用 JUnit 插件发布测试结果。

如下图所示，在 **构建后操作** 下选择 **发布 JUnit 测试结果报告**。

![](img/cc4299656808e62a294f1843a1e18e72_233_0.png)

图 9.24：3-testing – 构建后操作

如下图所示，提供你想要存储测试结果的路径。Jenkins 将从提到的路径获取测试结果并发布测试结果。

![](img/cc4299656808e62a294f1843a1e18e72_233_1.png)

图 9.25：3-testing – JUnit 测试结果报告

在下图中，你可以看到阶段 1 和阶段 2 的构建编号。然后，它运行 pytest 并使用 JUnit 将测试结果导出为 .xml 文件。

![](img/cc4299656808e62a294f1843a1e18e72_233_2.png)

图 9.26：3-testing – 控制台输出

### 测试结果：test_predict

| 测试名称 | 持续时间 | 状态 |
|---|---|---|
| test_single_prediction_dtype | 32 ms | 已通过 |
| test_single_prediction_not_none | 37 ms | 已通过 |
| test_single_prediction_output | 36 ms | 已通过 |

### 所有测试

图 9.27：3-testing – 测试结果

在下图中，你可以看到以图形格式显示的测试结果状态。

### 测试结果趋势

![](img/cc4299656808e62a294f1843a1e18e72_234_0.png)

图 9.28：3-testing – 测试结果趋势

## 阶段 4：4-deployment-status-email

在此阶段，Jenkins 正在使用 FastAPI 和训练好的模型部署 ML Web 应用。





如下图所示，在**构建触发器**（Build Triggers）下选择**其他项目构建后构建**（Build after other projects are built），并选择**仅在构建稳定时触发**（Trigger only if build is stable），这意味着此阶段是下一个阶段，并在上一阶段完成后开始执行。

![](img/cc4299656808e62a294f1843a1e18e72_235_0.png)

图 9.29: 4-deployment-status-email – 构建触发器

如下图所示，在**构建**（Build）选项卡下，从**添加构建步骤**（Add build step）下拉菜单中选择**执行 Shell**（Execute shell），因为它将执行来自 Shell 的命令。

![](img/cc4299656808e62a294f1843a1e18e72_235_1.png)

图 9.30: 4-deployment-status-email – 执行 Shell

在下图中，Jenkins 正在名为 **model11** 的运行中 Docker 容器内执行 **FastAPI** 命令，命令中的 **-d** 用于指示 Docker 容器以分离模式运行该命令。**-w /code** 表示将工作目录更改为 /code。最后，--host 和 --port 分别是 FastAPI Web 应用将要运行的地址和端口。

## 构建

![](img/cc4299656808e62a294f1843a1e18e72_236_0.png)

图 9.31: 4-deployment-status-email – 构建

如下图所示，从**添加构建后操作**（Add post-build action）下拉菜单中选择**扩展电子邮件通知**（Extended Email Notification）。

![](img/cc4299656808e62a294f1843a1e18e72_236_1.png)

图 9.32: 4-deployment-status-email – 构建后操作

如下图所示，将内容类型（Content Type）选择为 HTML (text/html)，以便可以在正文中使用 HTML 标签；不过，这是可选的。

![](img/cc4299656808e62a294f1843a1e18e72_236_2.png)

图 9.33: 4-deployment-status-email – 内容类型

如下图所示，在**触发器**（Triggers）部分下选择**始终**（Always）选项。这样可让 Jenkins 无论构建状态（成功或失败）如何都发送电子邮件。它将向指定的人员发送电子邮件。

![](img/cc4299656808e62a294f1843a1e18e72_237_0.png)

图 9.34: 4-deployment-status-email – 触发器

如下图所示，从**附加构建日志**（Attach Build Log）下拉菜单中选择**压缩并附加构建日志**（Compress and Attach Build Log）选项。启用此选项后，人员将获得当前阶段的控制台输出，从而无需访问 Jenkins 作业即可了解作业中发生的情况；不过，这是可选的。

![](img/cc4299656808e62a294f1843a1e18e72_237_1.png)

图 9.35: 4-deployment-status-email – 附加构建日志

如下图所示，一封电子邮件显示了阶段 4 的结果。如果作业因任何原因失败，则会触发此电子邮件，因为你在扩展电子邮件插件中选择了**始终**（Always）选项。此电子邮件包含作业名称、构建编号和作业状态。此处，未选择**附加构建日志**（Attach Build Log）选项。

![](img/cc4299656808e62a294f1843a1e18e72_238_0.png)

图 9.36: 4-deployment-status-email – 失败邮件

下图包含阶段 4 的输出。如你所见，它显示了带有构建编号的前几个阶段的状态。最后，它还显示了发送电子邮件的过程。

## 控制台输出

```
Started by upstream project "3-testing" build number 11
originally caused by:
Started by upstream project "2-training" build number 10
originally caused by:
Started by upstream project "1-GitHub-to-docker-container" build number 20
originally caused by:
Started by GitHub push by suhas-ds
Running as SYSTEM
Building in workspace /var/lib/jenkins/workspace/4-deployment-status-email
No emails were triggered.
[4-deployment-status-email] $ /bin/sh -xe /tmp/jenkins292211547470220823.sh
+ echo Stage 4
+--------------------->>>>>
echo Stage 4 <<<<<---------------------
+ sudo docker exec -d -w /code model11 unicorn main:app -proxy-headers --host 0.0.0.0 --port 8005
+ echo Successfully Deployed
Successfully Deployed
Email was triggered for: Always
Sending email for trigger: Always
Request made to compress build log
Sending email to: suhas.ds@gmail.com
Finished: SUCCESS
```

图 9.37: 4-deployment-status-email – 控制台输出

如下图所示，收到的电子邮件是阶段 4 成功完成的结果。作业在没有任何错误的情况下完成后，由于在扩展电子邮件插件中选择了**始终**（Always）选项，因此会触发此电子邮件。此电子邮件包含作业名称、构建编号和作业状态。你可以查看作业的构建输出。

![](img/cc4299656808e62a294f1843a1e18e72_239_0.png)

图 9.38: 4-deployment-status-email – 成功邮件

下图显示了所有作业的状态，包括上次成功、上次失败状态以及完成作业所需的持续时间。你可以在 Jenkins 仪表板上查看此状态。

| S | W | 名称 | 上次成功 | 上次失败 | 上次持续时间 |
|---|---|---|---|---|---|
| ✔ | ⚙️ | 1-GitHub-to-docker-container | 1 小时 59 分 | #20 N/A | 1 分 44 秒 |
| ✔ | ⚙️ | 2-training | 1 小时 57 分 | #10 2 天 17 小时 | #2 2.6 秒 |
| ✔ | ⚙️ | 3-testing | 1 小时 57 分 | #11 20 小时 | #6 2.4 秒 |
| ✔ | 👤 | 4-deployment-status-email | 1 小时 57 分 | #12 18 小时 | #8 0.26 秒 |

图 9.39: Jenkins 仪表板 – 作业概览

是时候检查已部署的贷款预测 Web 应用了。该 Web 应用运行在 **8005** 端口上，因此你可以通过服务器 IP 地址（或域名）后跟端口 **8005** 来访问它。当链接的 GitHub 仓库中有任何更改提交时，Jenkins 将一个接一个地触发第一个及后续阶段，最新的 Web 应用将再次部署。简而言之，在将更新推送到 GitHub 仓库后，你可以坐下来观察每个阶段的状态，或只是等待电子邮件。

提供用户数据并点击**执行**（Execute）按钮，如下图所示。

![](img/cc4299656808e62a294f1843a1e18e72_240_0.png)

图 9.40: FastAPI – ML 应用

下图是上述操作的结果。你可以在响应体中看到状态为**已批准**（Approved）。你还可以将此 API 端点集成到其他应用程序中。

![](img/cc4299656808e62a294f1843a1e18e72_241_0.png)

图 9.41: FastAPI - 响应

因此，你学会了如何使用开源工具 Jenkins 创建一个简单的 CI/CD 流水线。你可以根据业务和应用程序要求对其进行修改。

## 结论

在本章中，你探索了 CI/CD 流水线中持续集成（CI）、持续交付（CD）、持续部署（CD）和持续训练（CT）的过程。此外，你还学会了如何使用流行的开源工具 Jenkins 创建一个简单的 CI/CD 流水线。接下来，你使用 GitHub Webhook 集成了 GitHub 和 Jenkins，并构建了 Docker 镜像，将容器作为 Jenkins 作业运行。你还使用 JUnit 插件执行并导出了 pytest 结果。在最后一个阶段，ML Web 应用被部署在端口 8005 上。最后，它触发了带有构建状态、作业名称和构建日志的电子邮件。

在下一章中，你将学习如何使用 GitHub Actions 构建将 ML 应用部署到 Heroku 平台的 CI/CD 流水线。

## 要点

- CD 根据你计划实施的自动化程度，可指持续交付或持续部署（两者互换使用）。
- Jenkins 是一个用 Java 编写的开源、模块化 CI/CD 自动化工具，附带大量插件。
- FastAPI 需要 Python 3.6 及以上版本。
- Jenkins 理解 JUnit 测试报告 XML 格式。

## 选择题

- 1. 哪个插件用于在 Jenkins 中显示测试输出？
  - a) pytest
  - b) Selenium
  - c) JUnit
  - d) GitHub

- 2. CD 指的是以下哪项？
  - a) 持续交付
  - b) 持续部署
  - c) 创建字典
  - d) a 和 b

## 答案

- 1. c
- 2. d

## 问题

- 1. CI/CD 流水线中的 CT 是什么？
- 2. 流行的 CI/CD 工具/平台有哪些？
- 3. 在 Jenkins 中显示测试结果需要哪个插件？

## 加入我们的图书 Discord 空间

加入图书的 Discord 工作区，获取最新动态、优惠、全球技术动态、新版本发布以及与作者的交流会议：

https://discord.bpbonline.com

![](img/cc4299656808e62a294f1843a1e18e72_242_0.png)





## CHAPTER 10

## 在 Heroku 上部署 ML 模型

### 简介

Heroku 是一个 **平台即服务 (PaaS)** 平台，使开发者能够完全在云端构建、运行和操作应用程序。您可以将 Docker 容器推送到 Heroku，或提供 GitHub 仓库详细信息（例如分支名称），以便在将模型的新更改推送后自动部署 Web 应用。这样，您可以使 ML 模型在 Web 上可访问，随时准备进行预测。

如果您是初学者，那么 GitHub CI/CD 是构建端到端 CI/CD 流水线的最简单平台。由于所有内容都在 GitHub 上，因此易于管理。您只需要一个 GitHub 仓库即可创建和运行 GitHub Actions 工作流。

有关讨论的概念（例如打包 ML 模型、FastAPI、docker 和 CI/CD 流水线），请参考前面的章节。

### 结构

本章讨论以下主题：

- 创建 Heroku 账户并安装 Heroku CLI
- 创建 Heroku 应用
- 使用 Heroku CLI 将 Web 应用部署到 Heroku
- 使用 GitHub Actions 构建 CI/CD 流水线

### 目标

学习本章后，您应该能够将 ML 模型部署到 Heroku - 平台即服务 (PaaS)，并将 GitHub 仓库集成到 Heroku 中以实现自动部署。从 Heroku Web UI 和终端创建 Heroku 应用。您将学习使用 GitHub Actions 和 Heroku 构建和运行 CI/CD 流水线。您还将学习如何在 GitHub Actions 上使用 pytest 和 tox 执行多个测试。为 GitHub Actions 创建 YAML 文件以运行工作流。

### Heroku

Heroku 是一个基于容器的云平台即服务 (PaaS) 平台。开发者使用 Heroku 来部署、管理和扩展现代应用程序。它拥有一个非常简便的应用程序部署流程。

Heroku 通过消除维护服务器、硬件或基础设施的困难来为您节省时间。它支持最流行的语言，例如 Node、Ruby、Java、Clojure、Scala、Go、Python 和 PHP。

简单来说，Heroku 允许您将应用程序在互联网上发布供他人访问，就像网站一样。只需几个步骤，它就能让您的应用程序供他人访问。您可以专注于应用程序开发，无需担心基础设施、服务器等事项。

它支持与 GitHub 轻松集成，以便轻松将 GitHub 仓库中可用的代码部署到运行在 Heroku 上的应用程序。为 Heroku 应用配置 GitHub 集成后，当更新推送到指定仓库时，Heroku 可以自动构建并发布（如果构建成功）这些更新。

Heroku 应用可以扩展到多个 dyno（运行 Heroku 应用程序代码的容器）上同时运行（免费或爱好者 dyno 除外），只需简单的步骤即可避免任何停机时间。Heroku 提供 dyno 的手动和自动扩展。您可以通过添加更多 dyno 来水平扩展，以处理大量请求流量。另一方面，您可以根据需要增加内存和 CPU 等资源来垂直扩展。

Heroku 提供持续集成和持续部署。它具有内置测试设施以实现持续部署。共享相同代码库的 Heroku 应用可以组织成部署流水线，轻松从一个阶段提升到下一个阶段，并通过可视化界面进行管理。

在 Heroku 平台上部署 Web 应用有三种方法：

- 使用 Heroku Git 部署
- 使用 GitHub 仓库集成部署
- 使用容器注册表部署

现在您应该已经掌握了要点，接下来将部署一个机器学习模型到 Heroku。学习本章后，您将能够更好地在 Heroku 上进行 ML 部署。

### 设置 Heroku

您需要创建一个 Heroku 账户。这是一次性操作。访问 Heroku 平台 https://www.heroku.com/

**步骤 1：**
创建 Heroku 账户（如果您没有的话）并登录。

将主要开发语言选择为 **Python** 并创建免费账户。

**步骤 2：**
登录账户后，创建一个新应用，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_245_0.png)

*图 10.1：创建新应用*

点击 **创建新应用** 按钮并添加应用名称。在此示例中，它是 **docker-ml-cicd**。

点击 **创建应用** 按钮完成流程。

> 注意：两个或更多 Heroku 应用不能具有相同的名称。

**步骤 3：**
您可以点击 **打开应用** 按钮查看应用。在当前场景中，它是 https://docker-ml-cicd.herokuapp.com/

它将显示以下文本：

**Heroku | 欢迎使用您的新应用！**

现在，返回您的 Heroku 应用控制面板并安装 Heroku **命令行界面 (CLI)**，以便通过终端轻松访问。Heroku CLI 的安装步骤在 https://devcenter.heroku.com/articles/heroku-cli 中说明。您可以通过本地终端执行 Heroku 命令。此时，为生产环境再创建一个应用，并命名为 docker-ml-cicd-prod。此时，您的 Heroku 账户应该已准备好您创建的应用。

### 使用 Heroku Git 部署

此方法非常简单直接。此方法需要 Heroku CLI。添加 Heroku 的 Git 远程仓库并直接推送更改到它。

从 Heroku 应用控制面板，进入 **部署** 选项卡。您将看到三种部署方法：

- Heroku Git
- GitHub
- 容器注册表

下图显示了 Heroku 平台上可用的部署方法：

![](img/cc4299656808e62a294f1843a1e18e72_246_0.png)

图 10.2：部署方法

从上述方法中，您需要选择第一种方法，即 Heroku Git 方法，并按照该选项下方给出的步骤操作。

### 使用 GitHub 仓库集成部署

Heroku 自带 GitHub 集成方法，使您能够自动化部署流程。在 GitHub 与 Heroku 集成后，推送到仓库的任何更改都将触发部署 Heroku 应用的流程。

在 Heroku 上，您可以创建一个流水线并将两个应用添加到其中。Heroku 允许您在部署暂存应用之前创建审核（临时）应用。此额外选项使您在将应用推送到暂存或预部署阶段之前，可以查看应用的运行情况。

流水线已分为三个阶段：

- 审核应用
- 暂存
- 生产

#### 审核应用

这将为未合并的拉取请求创建审核应用。每个审核应用都有一个唯一 URL，可共享用于测试。为了标准化，您可以设置审核应用的 URL 模式。

当存在未合并的拉取请求时，它会自动创建用于审核，在拉取请求合并后，审核应用会被删除。这意味着该应用不再可访问。

注意：您应该为 Heroku 应用同时启用 Heroku 流水线和 GitHub 集成，以使用审核应用。

在 审核应用 下，点击 启用审核应用 按钮。

之后，在弹出窗口中，为以下选项选中复选框：

- 自动为新拉取请求创建新审核应用：启用后，每个新打开的拉取请求都会自动创建审核应用，关闭的拉取请求会删除该审核应用。
- 自动销毁过期的审核应用：您可以从下拉菜单中选择应用的生命周期，例如 1 天后、2 天后、5 天后或 30 天后。默认值为 5 天。

点击 启用审核应用。

#### 暂存

暂存应用可用于在部署到生产环境之前预览代码更改和功能，这被称为预生产阶段。不建议跳过暂存部署直接部署到生产环境。可能会出现一种情况：在您的本地机器上运行良好的应用在 Heroku（云端）上可能无法运行。您可能会花费大量时间查找和修复问题，并在客户面前丢脸。一旦您验证了在暂存环境中运行正常的应用，就应该使用 提升到生产 按钮将其推送到生产环境。

在 暂存 下，添加暂存应用。





## 生产环境

生产应用运行面向客户的代码。建议仅在代码经过测试后，才从预发布应用推送代码到生产环境。

在 **生产环境** 下，应为生产环境创建一个新应用。

## Heroku Pipeline 流程

当有人将更改推送到分支（master 分支除外）时，在 GitHub 仓库中点击 **对比与拉取请求** 按钮，然后点击 **创建拉取请求** 按钮。在 GitHub 上发起拉取请求后，您应该能看到一个新应用正在构建（在 **预览应用** 下）。应用就绪后，即可看到预览应用已运行。

如果一切顺利，主开发人员可以返回 GitHub，将拉取请求合并到 GitHub 仓库的 master 分支。几秒钟内，预发布应用应开始构建。部署完成后，可以打开并验证预发布应用。不过，如果直接将更改推送到 master 分支，预发布应用将开始构建，并会跳过 **预览应用** 阶段。

可以将预发布应用交给测试人员或 QA 团队，如果一切顺利，最终可以将其推送到 **生产环境**。

在 Heroku 上点击 **提升到生产环境** 按钮后，生产应用将上线。

下图展示了在 Heroku 上与 GitHub 仓库集成时，自动化 Heroku 流水线的工作流。

![](img/cc4299656808e62a294f1843a1e18e72_248_0.png)

图 10.3: Heroku 自动化流水线

## 使用容器注册表进行部署

Heroku 容器注册表允许您将 Docker 镜像部署到 Heroku。

请确保已安装可正常工作的 Docker，并使用以下命令登录 Heroku：

```
heroku login
```

系统将提示您按任意键打开浏览器以完成登录过程。

将打开一个新浏览器窗口并要求您登录。可以添加 `-i` 或 `--interactive` 选项，以留在终端并在出现提示时传递登录信息。

请确保您位于包含 `Dockerfile` 的项目目录中。

现在，登录 Heroku 容器注册表：

```
heroku container:login
```

使用以下语法构建镜像并将其推送到 Heroku 的容器注册表：

```
heroku container:push <process-type> --app [app name]
```

在此示例中，它是 Web 进程，`--app` 参数保存 Heroku 的应用名称。

最后，将镜像发布到您的应用：

```
heroku container:release <process-type> --app [app name]
```

运行以下命令在浏览器中查看运行中的应用：

```
heroku open --app [app name]
```

> 注：容器注册表方法不支持流水线提升。

## GitHub Actions

GitHub Actions 是一个持续集成与持续交付（CI/CD）平台，可帮助您在代码所在的同一位置（即 GitHub 仓库）自动化开发工作流，并协作处理拉取请求和议题。您可以编写名为“动作”的单个可配置任务，并将它们组合以创建自定义工作流。工作流是 GitHub 内的自定义自动化流程。

下图展示了为当前用例创建的工作流：

![](img/cc4299656808e62a294f1843a1e18e72_250_0.png)

与 Jenkins 不同，GitHub Actions 自带运行器（GitHub 拥有的服务器，适用于 Windows、Linux 和 macOS 等常见操作系统），用于构建、测试和部署工作。GitHub 支持多种语言，例如 Node.js、Python、Java、Ruby、PHP、Go、Rust 和 .NET。

GitHub Actions 自动化通过工作流来管理。工作流本质上是您放置在同一项目仓库中 `.github/workflows` 目录下的 yml 或 YAML 文件。

GitHub Actions 可免费使用，但对其设置了一些限制。

您可以访问 https://docs.github.com/en/actions 了解有关 GitHub Actions 的更多信息。

### 配置

GitHub Actions 需要最小程度的 GitHub 配置。首先，前往包含代码库和所需文件的 GitHub 仓库。接下来，默认情况下，您将被重定向到“代码”选项卡；切换到“设置”选项卡，然后从左侧面板中，在“安全性”部分下选择“密码”选项。之后，在“密码”菜单下选择“操作”。最后，使用“新建仓库密码”按钮添加以下密码：

- HEROKU_API_KEY: 可在 Heroku 平台的以下路径获取 Heroku API 密钥。
  Heroku 登录 | 账户设置 | 账户 | API 密钥 | 显示/重新生成 API 密钥

- HEROKU_APP_NAME: 这是 Heroku 应用名称。此处，请提供为预发布环境创建的应用名称，即 docker-ml-cicd。

- HEROKU_PROD_APP_NAME: 这是另一个需为生产环境创建的应用。在此示例中，它是 docker-ml-cicd-prod。

下图展示了仓库密码。您可以更新或删除密码，但无法查看它们。

![](img/cc4299656808e62a294f1843a1e18e72_251_0.png)

图 10.5: GitHub – 仓库密码

## 使用 GitHub Actions 和 Heroku 构建 CI/CD 流水线

假设存在贷款预测场景，您需要预测客户的贷款是否会获批。重点不在于超参数调优和模型优化。不过，您可以优化模型以提升整体性能。

在本章中，将使用之前开发的机器学习包（参见第 4 章：打包机器学习模型）。

首先，创建 ML 代码包并使用 FastAPI 构建 Web 应用。随后，创建测试用例和依赖文件，以及 Dockerfile 和 docker-compose.yml 文件。最后，为 GitHub Actions 创建 GitHub 工作流文件（.yml）。

您可以通过以下链接访问代码仓库：https://github.com/suhas-ds/heroku-docker-cicd

下目录结构展示了 CI/CD 流水线文件：

```
.
|__ .github/
   |__ workflows/
      |__ production.yml
      |__ workflow.yml
|__ src/
   |__ prediction_model/
      |__ config/
         |__ __init__.py
         |__ config.py
```

```
datasets/
    __init__.py
    test.csv
    train.csv
processing/
    __init__.py
    data_management.py
    preprocessors.py
trained_models/
    __init__.py
    classification_v1.pkl
VERSION
__init__.py
pipeline.py
predict.py
train_pipeline.py
tests/
    pytest.ini
    test_predict.py
MANIFEST.in
README.md
requirements.txt
setup.py
tox.ini
.gitignore
Dockerfile
README.md
docker-compose.yml
main.py
pytest.ini
requirements.txt
runtime.txt
start.sh
test.py
tox.ini
```

在 src 目录中，使用了第 4 章：打包机器学习模型中的文件。

### .gitignore

此文件包含 Git 应忽略的文件。

- venv/
- __pycache__/
- .pytest_cache
- .tox

### main.py

首先，从 **prediction_model** 加载依赖项和模块：

```
# Importing Dependencies
from fastapi import FastAPI
from pydantic import BaseModel
import uvicorn
import pickle
import os
import numpy as np
import pandas as pd
from fastapi.middleware.cors import CORSMiddleware
from prediction_model.predict import make_prediction
import pandas as pd
```

创建 FastAPI 实例并将其分配给 **app**，以便 **app** 在创建 API 时成为交互点。

```
app = FastAPI(
    title="Loan Prediction Model API",
    description="A simple API that uses ML model to predict the Loan application status",
    version="0.1",
)
```

CORS（跨源资源共享）是指在浏览器上运行的前端具有与后端通信的 JavaScript 代码，而后端与前端源不同。但是，是否使用它取决于您的应用程序和需求。

```
1. origins = [
2.     "*"
3. ]
4.
5. app.add_middleware(
6.     CORSMiddleware,
7.     allow_origins=origins,
8.     allow_credentials=True,
9.     allow_methods=["*"],
10.    allow_headers=["*"],
11. )

```

定义 LoanPred 类，该类定义了客户端预期的数据类型。

LoanPred 类的数据模型继承自 BaseModel。然后，添加带有函数的根视图，该函数为主页返回 'message': 'Loan Prediction App'。

```
class LoanPred(BaseModel):
    Gender: str
    Married: str
    Dependents: str
    Education: str
    Self_Employed: str
    ApplicantIncome: float
    CoapplicantIncome: float
    LoanAmount: float
    Loan_Amount_Term: float
    Credit_History: float
    Property_Area: str

@app.get('/')
```





def index():
    return {'message': 'Loan Prediction App'}

@app.get('/health')
def healthcheck():
    return {'status':'ok'}

在这里，创建 **/predict_status** 作为端点，也称为路由。然后，添加 **predict_loan_status()**，其参数类型为数据模型，即 **LoanPred**。

```python
# Defining the function which will make the prediction using the data
# which the user inputs
@app.post('/predict_status')
def predict_loan_status(loan_details: LoanPred):
    data = loan_details.dict()
    Gender = data['Gender']
    Married = data['Married']
    Dependents = data['Dependents']
    Education = data['Education']
    Self_Employed = data['Self_Employed']
    ApplicantIncome = data['ApplicantIncome']
    CoapplicantIncome = data['CoapplicantIncome']
    LoanAmount = data['LoanAmount']
    Loan_Amount_Term = data['Loan_Amount_Term']
    Credit_History = data['Credit_History']
    Property_Area = data['Property_Area']

    # Making predictions
    input_data = [Gender, Married, Dependents, Education,
                 Self_Employed, ApplicantIncome, CoapplicantIncome,
                 LoanAmount, Loan_Amount_Term, Credit_History, Property_Area]
    cols = ['Gender','Married','Dependents',
           'Education','Self_Employed','ApplicantIncome',
           'CoapplicantIncome','LoanAmount','Loan_Amount_Term',
           'Credit_History','Property_Area']
    data_dict = dict(zip(cols,input_data))
    prediction = make_prediction([data_dict])['prediction'][0]

    if prediction == 'Y':
        pred = 'Approved'
    else:
        pred = 'Rejected'

    return {'status':pred}
```

以下函数将为用户输入创建 UI。在这里，创建 /predict 作为端点，也称为路由，并声明用户预期的输入数据类型。

```python
@app.post('/predict')
def get_loan_details(Gender: str, Married: str, Dependents: str,
Education: str, Self_Employed: str, ApplicantIncome: float,
CoapplicantIncome: float, LoanAmount: float, Loan_Amount_Term: float,
Credit_History: float, Property_Area: str):

    input_data = [Gender, Married, Dependents, Education,
Self_Employed, ApplicantIncome, CoapplicantIncome,
LoanAmount, Loan_Amount_Term, Credit_History, Property_Area]
    cols = ['Gender','Married','Dependents',
           'Education','Self_Employed','ApplicantIncome',
           'CoapplicantIncome','LoanAmount','Loan_Amount_Term',
           'Credit_History','Property_Area']

    data_dict = dict(zip(cols,input_data))
    prediction = make_prediction([data_dict])['prediction'][0]
    if prediction == 'Y':
        pred = 'Approved'
    else:
        pred = 'Rejected'

    return {'status':pred}

if __name__ == '__main__':
    pass
```

FastAPI 文件已完成。

## requirements.txt

现在，按如下方式创建 requirements.txt 文件。在此文件中，您可以分别定义模型要求、测试要求和 FastAPI 要求，以便更好地理解和管理。

```
# Model building requirements
joblib==0.16.0
numpy==1.19.0
pandas==1.0.5
scikit-learn==0.23.1
scipy==1.5.1
sklearn==0.0

# testing requirements
pytest<5.0.0,>=4.6.6
requests

# packaging
setuptools==40.6.3
wheel==0.32.3

# FastAPI app requirements
fastapi>=0.68.0,<0.69.0
pydantic>=1.8.0,<2.0.0
uvicorn>=0.15.0,<0.16.0
gunicorn>=20.1.0
```

## Dockerfile

Dockerfile 包含在构建 Docker 镜像时要执行的一系列命令或指令。Docker 使用此文件来构建 Docker 镜像。

```
FROM python:3.7-slim-buster

COPY ./start.sh /start.sh

RUN chmod +x /start.sh

ENV PYTHONPATH "${PYTHONPATH}:/app/src/"

COPY . /app

RUN chmod +x /app

RUN pip install --no-cache-dir --upgrade -r app/requirements.txt

CMD ["./start.sh"]
```

## docker-compose.yml

Web 服务从当前目录中的 Dockerfile 构建，并将主机上的 app 目录挂载到容器内的 /app。

```
version: "3.9" # optional since v1.27.0
services:
web:
build: .
volumes:
- ./app:/app
```

## pytest.ini

Pytest 允许您使用一个全局配置文件，即 *pytest.ini*，您可以在其中保存运行命令时要传递的设置和其他参数。将 **-p no:warnings** 添加到 **addopts** 选项中，这将禁止警告。pytest 运行时将执行此部分中的参数。

```
[pytest]

addopts = -p no:warnings
```

## runtime.txt

在此文件中声明要使用的 Python 版本。

```
python-3.7
```

## start.sh

这是一个 shell 脚本，包含一系列由 bash shell 执行的命令。此文件的第一行告诉应使用哪个解释器来执行此脚本。

它将从 `app/` 文件夹中的 `src/` 安装 **prediction_model** 包，并在下一命令中运行 FastAPI 应用。在此过程中，它将从 Heroku 环境中获取 PORT，因此您无需显式声明它。Heroku 将在任何可用端口上运行该应用。**main** 是位于 `app` 目录中的文件名，后跟 `:app`，这是要调用的 FastAPI 对象。

```
#!/bin/sh

pip install app/src/

uvicorn app.main:app --host 0.0.0.0 --port $PORT
```

如果您正在使用 **--reload** 选项，请务必将其删除。**--reload** 选项会消耗更多资源；此外，它不稳定。您可以在开发期间使用它，但不应在生产环境中使用它。

## test.py

此文件可让您使用 **TestClient** 测试 FastAPI 应用。FastAPI 提供的 **starlette.testclient** 与 **fastapi.testclient** 相同；不过，它直接来自 Starlette。借此，您可以在不显式运行应用的情况下检查应用的路由。

此文件将通过传递数据来测试应用的根路径和示例预测。

```
# Importing dependencies

from main import app

from fastapi.testclient import TestClient

import pytest
import requests
import json
```

通过将 FastAPI 应用作为参数传递来创建 TestClient()：

```
client = TestClient(app)
```

按照标准 pytest 约定，定义以 test_ 开头的函数：

```
def test_read_main():
    response = client.get("/")
    assert response.status_code == 200
    assert response.json() == {'message': 'Loan Prediction App'}
```

编写简单的 assert 语句以检查输出：

```
def test_pred():
    data = {
        "Gender": "Male",
        "Married": "Yes",
        "Dependents": "0",
        "Education": "Graduate",
        "Self_Employed": "No",
        "ApplicantIncome":5720,
        "CoapplicantIncome":0,
        "LoanAmount":110,
        "Loan_Amount_Term":360,
        "Credit_History":1,
        "Property_Area": "Urban"
    }

    response = client.post("/predict_status", json=data)
    assert response.json()["status"] != ""
    assert response.json() == {"status": "Approved"}
```

## tox.ini

这是 tox 配置文件。tox 可自动化并标准化 Python 中的测试。它是一个虚拟环境管理和测试命令行工具，用于检查您的包是否与不同的 Python 版本兼容。tox 将首先根据提供的配置创建虚拟环境，安装依赖项，最后执行配置中提供的命令。

**tox-gh-actions** 是一个插件，可使 tox 在 GitHub Actions 上运行。因此，您需要在运行 tox 命令之前在 GitHub Actions 工作流中安装 **tox-gh-actions**。

此文件旨在检查包与 Python-3.7 的功能。它将安装所需的依赖项并运行 pytest 命令。

```
[tox]
envlist = py37
skipsdist=True

[gh-actions]
python =
    3.7: py37

[testenv]
install_command = pip install {opts} {packages}
deps =
   -r requirements.txt

setenv =
   PYTHONPATH=src/

commands=
   pip install requests
   pytest -v test.py
   pytest -v src/tests/
```

## workflow.yml





GitHub Actions 会查找此文件以执行工作流。此工作流用于在 Heroku 上进行暂存或预生产应用部署。它在推送事件时触发，这意味着任何推送到 GitHub 仓库项目 master 分支的更新都会触发此工作流运行。在 jobs 下，你应声明其应运行的操作系统和 Python 版本。然后，它将使用 tox 运行 pytest。通过所有测试后，它将开始在 Heroku 上部署。为此，它将使用在 GitHub 仓库设置中定义的密钥。

```yaml
name: Docker-ml-cicd-Heroku

on:
  push:
    branches:
      - master

jobs:
  build:
    runs-on: ubuntu-18.04
    strategy:
      matrix:
        python-version: ['3.7']

    steps:
      - uses: actions/checkout@v2
      - name: Permissions
        run: chmod +x start.sh
      - name: Set up Python ${{ matrix.python-version }}
        uses: actions/setup-python@v2
        with:
          python-version: ${{ matrix.python-version }}
      - name: Install dependencies
        run: |
          python -m pip install --upgrade pip
          python -m pip install tox tox-gh-actions
      - name: Test with tox
        run: tox
      - name: Log in to Heroku Container registry
        env:
          HEROKU_API_KEY: ${{ secrets.HEROKU_API_KEY }}
        run: heroku container:login
      - name: Build and push
        env:
          HEROKU_API_KEY: ${{ secrets.HEROKU_API_KEY }}
        run: heroku container:push web --app ${{ secrets.HEROKU_APP_NAME }}
      - name: Release
        env:
          HEROKU_API_KEY: ${{ secrets.HEROKU_API_KEY }}
        run: heroku container:release web --app ${{ secrets.HEROKU_APP_NAME }}
```

*production.yml*

在 *workflow.yml* 用于暂存成功完成后，*production.yml* 工作流将运行。此工作流将简单地使用最新更新在 Heroku 上部署生产应用，假设一切正常。

```yaml
name: Production

on:
  workflow_run:
    workflows: [Docker-ml-cicd-Heroku]
    types:
      - completed

jobs:
  build:
    runs-on: ubuntu-18.04
    steps:
      - uses: actions/checkout@v2
      - name: Log in to Heroku Container registry
        env:
          HEROKU_API_KEY: ${{ secrets.HEROKU_API_KEY }}
        run: heroku container:login
      - name: Build and push
        env:
          HEROKU_API_KEY: ${{ secrets.HEROKU_API_KEY }}
        run: heroku container:push web --app ${{ secrets.HEROKU_PROD_APP_NAME }}
      - name: Release
        env:
          HEROKU_API_KEY: ${{ secrets.HEROKU_API_KEY }}
        run: heroku container:release web --app ${{ secrets.HEROKU_PROD_APP_NAME }}
```

一旦所有文件和代码库就绪，在本地计算机上运行应用。如果应用在本地计算机上运行，则将应用部署到 Heroku 容器注册表。为此，你可以参考本章前面讨论的“使用容器注册表部署”部分。如果一切顺利，部署后应用应在 Heroku 平台上运行。

接下来，为当前场景在 GitHub 上创建仓库（如果尚未创建）并将代码文件推送到其中。进入 GitHub 上的 **Actions** 选项卡；你会看到 GitHub 已经开始执行用于暂存或预部署应用的 workflow.yml 文件。

如下图所示，更新已被推送，注释为 Staging。

![](img/cc4299656808e62a294f1843a1e18e72_265_0.png)

图 10.6：GitHub 工作流运行

单击 Staging；它将带你进入此工作流的摘要。你将看到你在工作流中定义的作业状态。还会提及其他执行详细信息，例如完成此工作流所用的时间，用户名是指谁将更新推送到 master 分支，以及工作流文件的名称。

如下图所示，你可以看到暂存阶段的摘要：

![](img/cc4299656808e62a294f1843a1e18e72_266_0.png)

图 10.7：GitHub 工作流 - 暂存

下图显示了工作流中执行的步骤及其输出。要查看步骤的输出，请单击步骤左侧的 > 图标。

## 暂存
Docker-ml-cicd-Heroku #17

- 摘要
- 作业
- build (3.7)

![](img/cc4299656808e62a294f1843a1e18e72_267_0.png)

图 10.8：GitHub 工作流 – 暂存步骤

下图显示了 tox 命令的输出，该命令使用 py37 环境执行了 pytest 命令。

![](img/cc4299656808e62a294f1843a1e18e72_267_1.png)

图 10.9：GitHub 工作流 – tox

下图显示了在 _workflow.yml_ 工作流成功完成后，应用在 Heroku 平台上运行的情况。

_图 10.10：Heroku 应用 – docker-ml-cicd_

单击 **Production**；它将带你进入此工作流的摘要。你将看到你在工作流中定义的作业状态。还会提及其他执行详细信息，例如完成工作流所用的时间、将更新推送到 master 分支的用户名、工作流文件名称以及构建编号，在此示例中为 #2。

如下图所示，你可以看到生产阶段的摘要和状态：

![](img/cc4299656808e62a294f1843a1e18e72_269_0.png)

图 10.11：GitHub 工作流 – 生产步骤

下图显示了工作流中执行的步骤及其输出。要查看步骤的输出，请单击步骤左侧的 > 图标。

![](img/cc4299656808e62a294f1843a1e18e72_269_1.png)

图 10.12：GitHub 工作流 – 生产步骤

下图显示了在 production.yml 工作流成功完成后，应用在 Heroku 平台上运行的情况。

![](img/cc4299656808e62a294f1843a1e18e72_270_0.png)

图 10.13：Heroku 应用 – docker-ml-cicd-prod

因此，你现在已学会如何使用 GitHub 创建一个简单的 CI/CD 管道，以在 Heroku 平台上部署 ML 应用。此外，你可以根据业务和应用要求对其进行修改。

## 结论

在本章中，你了解了在 Heroku 平台（PaaS）上部署 ML 应用，使用 GitHub Actions 构建了自动化 CI/CD 管道，并使用 GitHub CI/CD 管道在 Heroku 平台上部署了暂存或预部署应用和生产应用。最后，你将 tox 与 GitHub Actions 集成，以在将暂存应用部署到 Heroku 之前作为 CI/CD 管道的一部分运行测试。

在下一章中，你将探索用于部署 ML 应用的 Azure 平台。

## 要点

- GitHub Actions 自带运行器（GitHub 拥有的用于 Windows、Linux 和 macOS 等主要操作系统的服务器），用于构建、测试和部署工作流。
- Heroku 应用必须同时启用 Heroku Pipelines 和 GitHub 集成才能使用评审应用。
- 你可以更新或删除 GitHub 密钥，但无法查看它们。
- GitHub Actions 免费使用；但是，对其设置了一些限制。

## 选择题

- 1. ______ 是一个插件，可实现 tox 在 GitHub Actions 上运行。
  - a) JUnit
  - b) tox-gh-actions
  - c) GitHub
  - d) tox-github

- 2. GitHub Actions 自动化使用 ______ 进行管理。
  - a) .git
  - b) tox
  - c) Workflow
  - d) 以上全部

## 答案

- 1. b
- 2. c

## 问题

- 1. GitHub Actions 工作流的文件格式是什么？
- 2. 在 Heroku 平台上部署应用的三种方法是什么？
- 3. 解释 Heroku 管道的工作阶段。

## 加入我们书籍的 Discord 空间

加入本书的 Discord 工作区，获取最新动态、优惠、全球技术动态、新版本发布以及与作者的会话：

https://discord.bpbonline.com

![](img/cc4299656808e62a294f1843a1e18e72_272_0.png)

## 第 11 章

## 在 Microsoft Azure 上部署 ML 模型

### 简介

Microsoft Azure 是开发者中广受欢迎的云平台，因为它提供了多种多样的服务，帮助开发者和组织在安全环境中以更少的努力和更少的时间向客户交付高质量解决方案。

在本章中，你将了解由 Microsoft Azure 提供的 MLaaS，即机器学习即服务。本章主要分为两部分。在第一部分中，将在 CI/CD 管道中使用 GitHub Actions 和 Azure Web 应用容器来在 Azure 云上部署 ML 应用。在第二部分中，将使用 Azure DevOps 和 **Azure 机器学习 (AML)** 服务在 Azure 云上部署 ML 应用。

### 结构

本章将讨论以下主题：

- 创建 Azure 帐户并安装 Azure CLI
- 使用 Docker 容器在本地运行 ML 应用
- 使用 Azure 容器将应用部署到 Azure Web 服务






- 使用 GitHub Actions 构建 CI/CD 流水线
- Azure Machine Learning (AML) 服务
- 使用 Azure Machine Learning (AML) 服务和 Azure DevOps 构建 CI/CD 流水线

## 目标

本章学习结束后，你应当能够将 ML 模型部署到 平台即服务 (PaaS) 和 机器学习即服务 (MLaaS) 上。你还应当能够将 GitHub 仓库集成到 Azure，以实现应用的自动化部署。你应当知道如何创建 Web 应用及其容器。此外，你将熟悉如何使用 GitHub Actions 和 Azure 构建并运行 CI/CD 流水线，以及在 GitHub Actions 上使用 pytest 和 tox 执行多个测试用例。在本章后续部分，你将学习如何为 GitHub Actions 创建 YAML 文件以运行工作流。到本章结束时，你还应当能够使用 Azure DevOps 构建并运行 CI/CD 流水线。

## Azure

Microsoft Azure（又称 Azure）是微软提供的云计算服务。Azure 提供多种形式的云计算选项，例如软件即服务 (SaaS)、平台即服务 (PaaS)、机器学习即服务 (MLaaS) 和基础设施即服务 (IaaS)，用于在 Azure 上部署应用程序和服务。

微软于 2008 年首次以 Windows Azure 名称推出其云计算服务，但商业上是在 2010 年推出的。之后，在 2014 年，他们扩展了服务并将其重新推出为 Microsoft Azure。

Azure 是一个即用型、资源丰富、灵活、快速且经济的云平台。它附带 200 多种产品和云服务；不过，在开发者中运行虚拟机 (VM) 或容器很受欢迎。它与 Docker、Jenkins 和 Kubernetes 等开源技术兼容。Azure 内置了持续集成和持续部署流水线。

Azure 支持与 GitHub 集成，以便轻松将 GitHub 仓库中的代码部署到运行在 Azure 上的应用程序。当为 Azure 应用配置 GitHub 集成后，Azure 可以自动构建并发布（如果该阶段成功完成）并将其推送到 Azure。

Azure 应用服务可以使用 Azure Kubernetes 服务 (AKS) 进行缩放。你可以选择不同的层级，每个层级附带一组计算能力，并设置自动缩放限制。在需要时，它会创建服务的副本以无缝处理请求。

在 Azure 平台上部署应用有许多方式，但你将在本章中探索两种方法：

- 使用 GitHub Actions 进行部署
- 使用 Azure DevOps 和 Azure ML 进行部署

Azure 主要采用按需付费定价计划，允许你仅为所使用的服务付费。如果某个应用程序使用多个服务，则每个服务将根据其获得的计划/层级计费。如果用户或组织寻求长期承诺，微软会提供折扣价格。

Azure 是一项付费服务，但允许新用户使用免费积分在有限时长内免费探索其功能和服务。之后，你需要激活按需付费定价计划。

## 设置 Azure 账户

你需要设置一个 Azure 账户。这是一次性操作，完成后即可使用。访问 Azure 平台 https://azure.microsoft.com/。

创建 Azure 账户（如果你还没有），然后登录。

> 注：你可以免费探索 Azure；但是，你需要提供信用卡/借记卡信息。如果需要付款，Azure 会发送通知。此外，你可以免费使用热门服务 12 个月，并额外获得 30 天的 $200 额度。

本章将使用 Azure DevOps。为此，你需要登录 Azure DevOps。

https://azure.microsoft.com/en-us/services/devops/

要连接并与 Azure 通信，需要 Azure 命令行工具，即 azure-cli 和 azureml-sdk。

使用本地终端安装 Azure CLI：

```
pip install azure-cli==2.37.0
pip install --upgrade azureml-sdk[cli]
```

你可以创建资源组。它是一个容器，用于保存 Azure 项目的相关资源。你可以根据需要将资源分配给此资源组。

## 使用 GitHub Actions 进行部署

在本部分中，将使用 Docker 在 Azure Web 服务中部署一个 ML 应用。GitHub Actions 将用于构建、测试和部署 Azure 上的 ML 应用。首先，GitHub Actions 会构建 Docker 镜像并将其推送到 **Azure 容器注册表 (ACR)**，然后将其拉取到 Azure 应用服务。

首先，为此实现准备所需的代码库。接下来，创建一个 ACR，然后构建 Docker 镜像并将其推送到 ACR。在下一步中，在 Azure 应用服务中创建 Web 应用，它将从 ACR 拉取容器镜像以部署基于 Web 的 ML 应用。

下图显示了使用 GitHub Actions 在 Azure 应用服务 (Web 应用) 上进行部署的工作流：

![](img/cc4299656808e62a294f1843a1e18e72_276_0.png)

图 11.1：GitHub Actions 和 Web 应用工作流

你可以在以下 GitHub 仓库中访问代码：

https://github.com/suhas-ds/mlapp-cd

以下目录结构显示了将用于 CI/CD 流水线的文件：

```
.
|-- .github
|   |-- workflows
|       |-- prod.workflow.yml
|-- src
|   |-- prediction_model
|       |-- config
|           |-- __init__.py
|           |-- config.py
|       |-- datasets
|           |-- __init__.py
|           |-- test.csv
|           |-- train.csv
|       |-- processing
|           |-- __init__.py
|           |-- data_management.py
|           └ preprocessors.py
|       |-- trained_models
|           |-- __init__.py
|           └ classification_v1.pkl
|       |-- VERSION
|       |-- __init__.py
|       |-- pipeline.py
|       |-- predict.py
|       └ train_pipeline.py
|       |-- tests
|           |-- pytest.ini
|           └ test_predict.py
|   |-- MANIFEST.in
|   |-- README.md
|   |-- requirements.txt
|   |-- setup.py
|   └ tox.ini
|-- Dockerfile
|-- docker-compose.yml
|-- main.py
|-- pytest.ini
|-- requirements.txt
|-- runtime.txt
|-- start.sh
|-- test.py
└─ tox.ini
```

让我们讨论前面文件中的代码和概念。在 `src` 目录中，将使用 *第 4 章：打包 ML 模型* 中的文件。

## .gitignore

此文件包含 Git 应忽略的文件和目录的名称。

- venv/
- __pycache__/
- .pytest_cache
- .tox

## main.py

此文件将加载模型的 pickle 对象并运行 FastAPI 应用。首先，从 **预测模型** 加载依赖项和模块：

```
1. # Importing Dependencies
2. from fastapi import FastAPI
3. from pydantic import BaseModel
4. import uvicorn
5. import pickle
6. import os
7. import numpy as np
8. import pandas as pd
9. from fastapi.middleware.cors import CORSMiddleware
10. from prediction_model.predict import make_prediction
11. import pandas as pd
```

创建一个 FastAPI 实例并将其分配给 **应用**，以便在创建 API 时 **应用** 成为交互点。

```
1. app = FastAPI(
2.     title="Loan Prediction Model API",
3.     description="A simple API that uses ML model to predict the Loan application status",
4.     version="0.1",
5. )
```

**跨源资源共享 (CORS)** 是指当在浏览器中运行的前端具有与后端通信的 JavaScript 代码，而后端与前端来源不同的情况。但是，是否使用它取决于你的应用程序和要求。

```
1. origins = [
2.       "*"
3.     ]
4.
5. app.add_middleware(
6.     CORSMiddleware,
7.     allow_origins=origins,
8.     allow_credentials=True,
9.     allow_methods=["*"],
10.    allow_headers=["*"],
11. )
```

定义 LoanPred 类，该类定义客户端预期的数据类型。

用于数据模型的 LoanPred 类继承自 BaseModel。然后，添加一个带有函数的根视图，该函数为主页返回 'message': 'Loan Prediction App'。

```
1. class LoanPred(BaseModel):
2.     Gender: str
3.     Married: str
4.     Dependents: str
5.     Education: str
6.     Self_Employed: str
7.     ApplicantIncome: float
8.     CoapplicantIncome: float
9.     LoanAmount: float
10.    Loan_Amount_Term: float
11.    Credit_History: float
12.    Property_Area: str
13.
14. @app.get('/')
15. def index():
16.     return {'message': 'Loan Prediction App'}
17.
```



@app.get('/health')
def healthcheck():
    return {'status':'ok'}

在此，创建`/predict_status`作为端点，也称为路由。然后，添加`predict_loan_status()`，其参数为数据模型类型，即`LoanPred`。

```
# Defining the function which will make the prediction using the data which the user inputs
@app.post('/predict_status')
def predict_loan_status(loan_details: LoanPred):
    data = loan_details.dict()
    Gender = data['Gender']
    Married = data['Married']
    Dependents = data['Dependents']
    Education = data['Education']
    Self_Employed = data['Self_Employed']
    ApplicantIncome = data['ApplicantIncome']
    CoapplicantIncome = data['CoapplicantIncome']
    LoanAmount = data['LoanAmount']
    Loan_Amount_Term = data['Loan_Amount_Term']
    Credit_History = data['Credit_History']
    Property_Area = data['Property_Area']

    # Making predictions
    input_data = [Gender, Married, Dependents, Education,
        Self_Employed, ApplicantIncome, CoapplicantIncome,
        LoanAmount, Loan_Amount_Term, Credit_History, Property_Area]
    cols = ['Gender','Married','Dependents',
        'Education','Self_Employed','ApplicantIncome',
        'CoapplicantIncome','LoanAmount','Loan_Amount_Term',
        'Credit_History','Property_Area']
    data_dict = dict(zip(cols,input_data))
    prediction = make_prediction([data_dict])['prediction'][0]

    if prediction == 'Y':
        pred = 'Approved'
    else:
        pred = 'Rejected'

    return {'status':pred}
```

以下函数将创建用于用户输入的 UI。在此，创建 /predict 作为端点，也称为路由，并声明用户预期的输入数据类型。

```
@app.post('/predict')
def get_loan_details(Gender: str, Married: str, Dependents: str,
                     Education: str, Self_Employed: str, ApplicantIncome: float,
                     CoapplicantIncome: float, LoanAmount: float, Loan_Amount_Term: float,
                     Credit_History: float, Property_Area: str):

    input_data = [Gender, Married, Dependents, Education,
                  Self_Employed, ApplicantIncome, CoapplicantIncome,
                  LoanAmount, Loan_Amount_Term, Credit_History, Property_Area]
    cols = ['Gender','Married','Dependents',
            'Education','Self_Employed','ApplicantIncome',
            'CoapplicantIncome','LoanAmount','Loan_Amount_Term',
            'Credit_History','Property_Area']

    data_dict = dict(zip(cols,input_data))
    prediction = make_prediction([data_dict])['prediction'][0]
    if prediction == 'Y':
        pred = 'Approved'
    else:
        pred = 'Rejected'

    return {'status':pred}

if __name__ == '__main__':
    uvicorn.run("main:app", host="0.0.0.0", port=port, reload=False)
```

FastAPI 文件已完成。

## requirements.txt

现在，让我们按如下方式创建 requirements.txt 文件。在此文件中，模型要求、测试要求和 FastAPI 要求分别定义，以便更好地理解和易于管理。

```
# Model building requirements
joblib==0.16.0
numpy==1.19.0
pandas==1.0.5
scikit-learn==0.23.1
scipy==1.5.1
sklearn==0.0

# testing requirements
pytest<5.0.0,>=4.6.6
requests

# packaging
setuptools==40.6.3
wheel==0.32.3

# FastAPI app requirements
fastapi>=0.68.0,<0.69.0
pydantic>=1.8.0,<2.0.0
uvicorn>=0.15.0,<0.16.0
gunicorn>=20.1.0
```

## Dockerfile

Dockerfile 包含在构建 Docker 镜像时要执行的一系列命令或指令。

```
FROM python:3.7-slim-buster

COPY ./start.sh /start.sh

RUN chmod +x /start.sh

ENV PYTHONPATH "${PYTHONPATH}:app/src/"

COPY . /app

RUN chmod +x /app

# expose the port that uvicorn will run the app on
ENV PORT=8000
EXPOSE 8000

RUN pip install --no-cache-dir --upgrade -r app/requirements.txt

CMD ["./start.sh"]
```

## docker-compose.yml

这将从当前目录中的 Dockerfile 构建 Web 服务，并将主机上的 app 目录挂载到容器内的 /app。

```
version: "3.9"  # optional since v1.27.0
services:
  web:
    build: .
    volumes:
      - ./app:/app
```

## pytest.ini

Pytest 允许您使用全局配置文件，即 *pytest.ini*，您可以在其中保存运行命令时传递的设置和其他参数。您可以将 **-p no:warnings** 添加到 **addopts** 字段中，这将禁止显示警告。pytest 运行时，此部分**将执行**这些参数。

```
[pytest]
addopts = -p no:warnings
```

## runtime.txt

此文件为可选文件。在此文件中，您可以声明要使用的 Python 版本。

```
python-3.7
```

## start.sh

这是一个 shell 脚本，包含一系列由 bash shell 执行的命令。此文件的第一行决定了应使用哪个解释器来执行此脚本。

它将从 **app/** 中的 **src/** 安装 **prediction_model** 包，并在下一条命令中运行 FastAPI 应用。*main.py* 是位于 *app* 目录中的文件名。

```
#!/bin/bash
pip install app/src/
python app/main.py
```

如果您正在使用，请确保删除 **--reload** 选项。**--reload** 选项消耗更多资源，且不稳定。您可以在开发期间使用它，但不应在生产环境中使用。

## test.py

此测试文件将使用 **testclient** 来启用对 FastAPI 应用的测试。FastAPI 提供与 **fastapi.testclient** 相同的 **starlette.testclient**，但它直接来自 Starlette。借助此功能，您可以在不从应用显式运行的情况下检查应用的路由。

此文件将通过传递数据来测试应用的根路径和模型预测。

```
# Importing dependencies
from main import app
from fastapi.testclient import TestClient
import pytest
import requests
import json
```

创建 **TestClient()** 并将 FastAPI 应用程序传递给它。

```
client = TestClient(app)
```

按照 pytest 的标准命名约定，定义以 **test_** 开头的测试函数：

```
def test_read_main():
    response = client.get("/")
    assert response.status_code == 200
    assert response.json() == {'message': 'Loan Prediction App'}
```

在测试函数中编写简单的 assert 语句以检查输出。

```
def test_pred():
    data = {
        "Gender":"Male",
        "Married":"Yes",
        "Dependents":"0",
        "Education":"Graduate",
        "Self_Employed":"No",
        "ApplicantIncome":5720,
        "CoapplicantIncome":0,
        "LoanAmount":110,
        "Loan_Amount_Term":360,
        "Credit_History":1,
        "Property_Area":"Urban"
    }

    response = client.post("/predict_status", json=data)
    assert response.json()["status"] != ''
    assert response.json() == {"status": "Approved"}
```

## tox.ini

这是 tox 配置文件。tox 可自动化并标准化 Python 中的测试。它是一个 virtualenv 管理和测试命令行工具，用于检查您的包是否与不同的 Python 版本兼容。tox 首先将根据提供的配置创建虚拟环境，然后安装依赖项。最后，它将执行配置中提供的命令。

**tox-gh-actions** 是一个插件，可使 tox 在 GitHub Actions 上运行。因此，在运行 tox 命令之前，您需要在 GitHub Actions 工作流中安装 **tox-gh-actions**。

此文件将检查包与 Python-3.7 的兼容性。首先，它将安装所需的依赖项，然后运行 pytest 命令。

```
[tox]
envlist = py37
skipsdist=True

[gh-actions]
python =
  3.7: py37

[testenv]
install_command = pip install {opts} {packages}
deps =
  -r requirements.txt

setenv =
  PYTHONPATH=src/

commands=
  pip install requests
  pytest -v test.py
  pytest -v src/tests/
```

当所有文件和代码库准备就绪后，在本地计算机上运行应用。如果应用在本地计算机上运行，则将应用部署到 Azure 容器注册表。

使用以下命令在本地计算机上构建 Docker 镜像：

```
sudo docker build . -t mlappcd.azurecr.io/mlapp-cd:v1
```

然后，使用以下命令运行 Docker 镜像：

```
sudo docker push mlappcd.azurecr.io/mlapp-cd:v1
```

至此，您应该可以看到 ML 应用在本地计算机上正在运行。

## 基础架构设置

首先，在 Azure 云上设置基础架构。在本节中，您将学习如何设置 Azure 容器注册表 (ACR) 并使用 Azure 应用服务创建 Web 应用容器。

## Azure Container Registry

首先，从本地计算机将 Docker 镜像推送到 Azure 容器注册表，此后 GitHub Actions 将推送该镜像。Azure 应用服务将拉取此 Docker 镜像以运行 Web 应用容器。





创建 Azure 容器注册表，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_288_0.png)

图 11.2: Azure 容器注册表

在字段中提供值后，单击 **评审 + 创建** 按钮完成流程。

完成上述流程后，可以检查容器注册表以查看状态。下图显示容器注册表的状态为 OK：

![](img/cc4299656808e62a294f1843a1e18e72_289_0.png)

图 11.3: Azure 容器注册表的部署状态

接下来，在 **访问密钥** 中启用 **管理用户** 选项。下图显示在 **设置** 下启用了管理用户访问：

![](img/cc4299656808e62a294f1843a1e18e72_289_1.png)

图 11.4: 容器注册表的访问密钥

完成上述流程后，返回本地终端。使用 Azure CLI 登录到 Azure，如下所示：

```
az login
```

在本地终端执行上述命令后，将打开一个浏览器窗口，你需要在其中登录。然后，可以关闭浏览器窗口并在终端中继续。下图显示了上述命令的输出：

![](img/cc4299656808e62a294f1843a1e18e72_290_0.png)

图 11.5: Azure 登录

之后，在终端中使用以下命令登录到 Azure 容器注册表：

```
sudo az acr login --name mlappcd
```

下图显示了在终端中执行上述命令的情况：

![](img/cc4299656808e62a294f1843a1e18e72_290_1.png)

图 11.6: Azure 容器注册表登录

首先，在本地计算机上构建 Docker 映像：

```
sudo docker build . -t mlappcd.azurecr.io/mlapp-cd:v1
```

在下图中，你可以看到映像已成功构建并打上标记：

![](img/cc4299656808e62a294f1843a1e18e72_290_2.png)

图 11.7: 在本地计算机上构建并标记 Docker 映像

现在，将该映像推送到 Azure 容器注册表：

```
sudo docker push mlappcd.azurecr.io/mlapp-cd:v1
```

如下图所示，映像已推送到 Azure 容器注册表：

```
sudo docker push mlappcd.azurecr.io/mlapp-cd:v1
The push refers to repository [mlappcd.azurecr.io/mlapp-cd]
3b6d870fb83d: Pushed
8f1f0492f672: Pushed
887b37cec3fa: Pushed
b53d06fba293: Pushed
5fb14adc05b1: Pushed
fa8a2adf7020: Pushed
1286c8c60b62: Pushed
3c97f5d9ffd6: Pushed
832439eadb07: Pushed
0ad3ddf4a4ce: Pushed
v1: digest: sha256:41546d3a93f60b03d1b3a8e202eb65e412c19426
```

图 11.8: Docker 映像已推送到 ACR

如下图所示，验证已推送到仓库的映像在 Azure 容器注册表中可用。在此示例中，你可以看到映像 mlapp-cd 在仓库中可用。

![](img/cc4299656808e62a294f1843a1e18e72_291_0.png)

图 11.9: Azure 容器注册表

## Azure 应用服务

现在，创建 Azure 应用服务资源。使用 Azure 应用服务，你可以创建基于容器的 Web 应用。这将从 ACR 拉取映像。Azure 应用服务可让你快速构建 Web、移动和 API 应用，并可根据要求进行缩放。

如下图所示，在“基础”选项卡下选择订阅和服务组。然后，将实例名称提供为 mlapp-cd。选择 Docker 容器单选按钮，因为 ML 应用基于 Docker 容器。

主页 > 应用服务 >

创建 Web 应用 ...

+   基础 Docker 网络 (预览) 监视 标记 评审 + 创建

应用服务 Web 应用可让你在任何平台上快速构建、部署和缩放企业级 Web、移动和 API 应用。在使用完全托管平台执行基础设施维护的同时，满足严格的性能、可缩放性、安全性和合规性要求。了解更多

项目详细信息

选择订阅以管理已部署资源和成本。使用资源组（如文件夹）来组织和管理所有资源。

订阅 * 免费试用

资源组 * mlapp-cd 创建新

实例详细信息

需要数据库？试用全新的 Web + 数据库体验。

名称 * mlapp-cd.azurewebsites.net

发布 * 代码 Docker 容器 静态 Web 应用

操作系统 * Linux Windows

图 11.10: Azure 服务

接下来，选择操作系统 Linux，并选择需要部署 Web 应用的区域。最后，从计划中选择 SKU 和大小。你可以根据应用程序和业务要求更改应用服务计划。

主页 > 应用服务 >
创建 Web 应用

操作系统 *
⚫ Linux ⚪ Windows

区域 *
美国东部
ⓘ 找不到你的应用服务计划？尝试不同的区域或选择你的应用服务环境。

应用服务计划
应用服务计划定价层确定与你的应用关联的位置、功能、成本和计算资源。
了解更多 ⓘ

Linux 计划 (美国东部) * ⓘ
(新) ASP-mlappcd-856c
创建新

SKU 和大小 *
基本 B1
100 总 ACU，1.75 GB 内存
更改大小

区域冗余
应用服务计划可以在支持该功能的区域部署为区域冗余服务。这仅是部署时的决定。应用服务计划部署后无法将其设置为区域冗余 了解更多 ⓘ

区域冗余
⚪ 已启用：你的应用服务计划及其中的应用将是区域

评审 + 创建 < 上一步 下一步：Docker >

图 11.11: Azure 服务

在下一个选项卡（即 Docker 配置）中，确保选择了来自 Azure 容器注册表的映像。如下图所示，将 映像源 选择为 Azure 容器注册表，然后从 Azure 容器注册表选项部分选择注册表、映像和标记。

主页 > 应用服务 >
创建 Web 应用 ...

基础 Docker 网络 (预览) 监视 标记 评审 + 创建

从 Azure 容器注册表、Docker Hub 或私有 Docker 仓库拉取容器映像。应用服务会使用你首选的依赖项在几秒钟内将容器化应用部署到生产环境。

选项
单个容器

映像源
Azure 容器注册表

Azure 容器注册表选项
注册表 *
mlappcd

映像 *
mlapp-cd

标记 *
v1

启动命令 ⓘ

评审 + 创建 < 上一步 下一步：网络 (预览) >

图 11.12: Azure 服务-Docker 配置

在字段中提供值后，单击 **评审 + 创建** 按钮完成流程。你应该能在新创建的资源中看到 Web 应用的状态。下图显示了 Azure 应用服务资源的状态：

![](img/cc4299656808e62a294f1843a1e18e72_294_0.png)

图 11.13: Azure 服务资源-状态

完成上述流程后，你的应用应该已部署。你可以通过互联网从任何位置访问 ML Web 应用。

## GitHub Actions

GitHub Actions 将自动化 Azure 上的部署。要自动化 ML 应用的部署，将使用工作流 (.yml) 文件，如下所示：

```
prod.workflow.yml
```

GitHub Actions 将查找此文件以执行工作流。此工作流用于在 Azure 上部署应用。它由推送事件触发，这意味着推送到 GitHub 仓库的 master 分支的任何更改都将触发此工作流运行。在 jobs 下，声明了要使用的操作系统和 Python 版本。然后，它将使用 tox 运行 pytest。通过所有测试后，它将开始在 Azure 上进行部署。为此，它将使用 GitHub 仓库设置中定义的密码。首先，登录到 Azure 容器注册表，然后构建并推送 Docker 映像到注册表。最后，此工作流将应用部署到 Azure Web 应用服务并从 Azure 登出。

```
1. name: Build and deploy to production
2.
3. on:
4.   push:
5.     branches:
6.       - master
7.
8. jobs:
9.   build-and-deploy:
10.     runs-on: ubuntu-18.04
11.     strategy:
12.       matrix:
13.         python-version: ['3.7']
14.
15.     steps:
16.     - name: Checkout GitHub Actions
17.       uses: actions/checkout@master
18.
19.     - name: Set up Python ${{ matrix.python-version }}
20.       uses: actions/setup-python@v2
21.       with:
22.         python-version: ${{ matrix.python-version }}
23.
24.     - name: Install dependencies
25.       run: |
26.         python -m pip install --upgrade pip
27.         python -m pip install tox tox-gh-actions
28.
29.     - name: Test with tox
```





run: |
  tox

- name: Login via Azure CLI
  uses: azure/login@v1
  with:
    creds: ${{ secrets.AZURE_CREDENTIALS }}

- name: Login to Azure Container Registry
  uses: azure/docker-login@v1
  with:
    login-server: mlappcd.azurecr.io
    username: ${{ secrets.REGISTRY_USERNAME }}
    password: ${{ secrets.REGISTRY_PASSWORD }}

- name: Build and push container image to the registry
  run: |
    docker build . -t mlappcd.azurecr.io/mlapp-cd:${{ github.sha }}
    docker push mlappcd.azurecr.io/mlapp-cd:${{ github.sha }}

- name: Deploy to App Service
  uses: azure/webapps-deploy@v2
  with:
    app-name: 'mlapp-cd'
    images: 'mlappcd.azurecr.io/mlapp-cd:${{ github.sha }}'

- name: Azure logout
  run: |
    az logout

Next, create the repository on GitHub for this (if not created already) and push the codebase into that repo.

## 服务主体

你需要在 GitHub Actions 工作流中提供服务主体，用于 Azure 身份验证和应用部署。要获取凭据，请在终端中使用你的订阅 ID 执行以下命令。

```
az ad sp create-for-rbac --name "github-actions" --role contributor --scopes /subscriptions/<Subscription ID>/resourceGroups/mlapp-cd --sdk-auth
```

With the preceding command, you will create an Azure Role Based Access Control (RBAC) named github-actions with a contributor role and scope.

Note: You can get the subscription ID from the subscription you have used while creating a resource group.

Azure RBAC is an authorization system built on Azure Resource Manager that provides access management of Azure resources.

You should get the following output:

```
{
    "clientId": "",
    "clientSecret": "",
    "subscriptionId": "",
    "tenantId": "",
    "activeDirectoryEndpointUrl": "https://login.microsoftonline.com",
    "resourceManagerEndpointUrl": "https://management.azure.com/",
    "activeDirectoryGraphResourceId": "https://graph.windows.net/",
    "sqlManagementEndpointUrl": "https://management.core.windows.net:8443/",
    "galleryEndpointUrl": "https://gallery.azure.com/",
    "managementEndpointUrl": "https://management.core.windows.net/"
}
```

In the preceding response, clientId, clientSecret, subscription, and tenantId are unique for the individual account. Copy and save the response of the preceding command for future use.

Now, go to GitHub repo settings and create three GitHub secrets:

- AZURE CREDENTIALS: Entire JSON response from preceding
- REGISTRY_USERNAME: clientId value from JSON response
- REGISTRY_PASSWORD: clientSecret value from JSON response

## 配置 Azure 应用服务以使用 GitHub Actions 进行持续部署

你需要配置 Azure 应用服务，以便使用 GitHub Actions 进行自动化。前往 Azure 应用服务 | 部署中心，并链接 GitHub 仓库主分支，如下图所示。

![](img/cc4299656808e62a294f1843a1e18e72_298_0.png)

图 11.14: Azure 服务-GitHub 配置

你需要授权 GitHub Actions 以实现持续部署自动化并提供所需详细信息。你可以添加部署槽位，例如暂存或预生产。当你不希望将更新后的 Azure 应用服务直接暴露到生产环境时，这非常有用。你需要按照上述步骤为部署中心执行相同的配置。

After completing the configuration in the app service, place the `prod.workflow.yml` workflow file in the linked GitHub repository. The path would be `.github/workflows/prod.workflow.yml`. When you push any changes to the GitHub repo, it will trigger the GitHub Actions workflow. After completing all the stages, the ML app will be deployed on Azure.

Go to the Actions tab in the GitHub repository, and you will see that GitHub has already started running the `prod.workflow.yml` workflow for app deployment on Azure.

Push the changes with a **部署** text as a comment, as you can see in the following figure.

![](img/cc4299656808e62a294f1843a1e18e72_299_0.png)

图 11.15: GitHub Actions-工作流运行

Click on **部署**, and it will take you to the summary of this workflow. You will see the status of the jobs you have defined in the workflow. Other execution details are also mentioned, such as the time taken to complete this workflow, the username that pushed the updates to the **主分支** branch, and the name of the workflow file.

**部署**
Build and deploy to production #5

![](img/cc4299656808e62a294f1843a1e18e72_300_0.png)

Figure 11.16: GitHub Actions-workflow steps

The following figure shows the output of app deployment to the Azure step from GitHub Actions. You can see that the app is successfully deployed and running on Azure. An app service application URL is printed at the end.

![](img/cc4299656808e62a294f1843a1e18e72_300_1.png)

Figure 11.17: GitHub Actions-deployment status

Head over to the Azure App Service; you should see container logs in the Azure App Service, as shown in the following figure. This helps you debug the issue while deploying the app.

![](img/cc4299656808e62a294f1843a1e18e72_301_0.png)

Figure 11.18: App service-container logs

If everything goes well, the app should work on Azure post deployment.

The following figure shows the app running on the Azure platform on successful completion of the prod.workflow.yml workflow.

![](img/cc4299656808e62a294f1843a1e18e72_301_1.png)

Figure 11.19: App service-ML web app running

Azure provides a monitoring service to track the usage of the Azure app. You can select metrics from the dropdown.

The following figure shows the monitoring service of the Azure app.

![](img/cc4299656808e62a294f1843a1e18e72_302_0.png)

Figure 11.20: App service-monitoring service

Thus, you have learned to create a simple CI/CD pipeline using GitHub to deploy the ML app on the Azure platform. However, you can modify it as per business and application requirements.

## 使用 Azure DevOps 和 Azure ML 进行部署

In this part, you will use Azure DevOps and AML to deploy an ML app on the Azure cloud. Unlike the previous part, the CI pipeline and CD pipeline are in the Azure cloud. This approach requires parallelism to be enabled. If you are using free credits, then by default, parallelism is not enabled; however, you can activate it by sending the request via email. You can use Azure Git repo or other sources, such as GitHub. This approach gives more flexibility, such as integration with other platforms, manual approval before deploying to the production, auto redeploy triggers, and such.

The following figure shows the automated ML workflow:

![](img/cc4299656808e62a294f1843a1e18e72_303_0.png)

Figure 11.21: Azure DevOps pipeline for ML

## Azure 机器学习 (AML) 服务

Azure Machine Learning (AML) service enable the creation of a reproducible CI/CD pipeline for ML. It is an Azure cloud-hosted environment that allows developers and organizations to deploy ML models quickly in the production environment with minimal code. In Azure Machine Learning Studio, you can run the notebooks on the cloud, use Automated ML for automated training and tuning the ML model using a metric, or use a designer to deploy a model from data preparation using a drag-and-drop interface.

The following are the salient features of Azure Machine Learning Studio:

- Storage provision to store your data and artifacts
- MLFlow to track your experiments and log the run details like timestamp, model metrics, and so on
- Model registry to store trained ML models for reusability
- Key vault to store credentials and variables
- Supports open-source libraries and frameworks
- Compute instance, which enables building and training in a secure VM
- Pipelines and CI/CD for faster training and deployment

- Endpoints for ML model
- Data drift functionality to deliver consistent accuracy and predictions
- Monitoring service to track the model, logs, and resources

### 工作区

A machine learning workspace is the main resource of AML. It contains experiments, models, endpoints, datasets, and such. It also includes other Azure resources, such as Azure Container Registry (ACR), which registers Docker containers at the time of Docker image deployment, storage, application insights, and key vault.

### 实验

An experiment consists of several runs initiated from the script. Run details and metadata are stored under the experiment. When you run the script, the experiment name needs to be provided to store the run information. However, it will create a new experiment if the name provided in the script does not exist in the given workspace.

### 运行

A run can be defined as a single iteration of the training script. Multiple runs are recorded under an experiment. A run logs model metrics and metadata, such as timestamps.

The best thing about AML is that you do not need to create a separate web service API using frameworks like Flask, Django, and FastAPI. AML creates endpoints for trained ML models and tracks the web service.

In this section, you will be using the Azure Machine Learning template and modifying it as per your requirements. You can build your codebase from the scratch; however, this template saves time as it has reusable and required steps already defined. The Azure DevOps demo generator can be accessed at the following link:

https://azuredevopsdemogenerator.azurewebsites.net/environment/createproject

Go to DevOps Labs, select the Azure Machine Learning template and add it to your project by providing the project name and organization in the next step.

Alternatively, you can directly go to the following URL:

https://azuredevopsdemogenerator.azurewebsites.net/?name=machinelearning





![](img/cc4299656808e62a294f1843a1e18e72_305_0.png)

图 11.22: Azure DevOps 演示生成器

您可以看到，代码库已与模板一起导入。此模板包含机器学习项目的代码和管道定义，用于演示如何自动化端到端的 ML/AI 项目。在此过程中，大多数步骤可在需要的地方进行小幅修改后重复使用。代码库位于 Azure Git 仓库中；不过，您也可以从 GitHub 仓库导入代码库。请注意，此模板是为回归算法构建的，并使用糖尿病数据集。不过，您需要更新分类算法的文件，并将使用贷款数据集。

![](img/cc4299656808e62a294f1843a1e18e72_306_0.png)

图 11.23: Azure 代码仓库

接下来，从左侧菜单进入管道部分。您可以看到，步骤已在模板中定义。如果您想从头开始创建所有步骤，请不要担心。首先，创建一个新项目，然后在该项目中，从左侧菜单进入管道部分。接下来，从可用的源选项中选择一个代码库，例如 GitHub、Azure Repos 和 Git。然后，从 YAML 文件创建一个新管道，或使用经典编辑器创建无需 YAML 的管道。

接下来，转到新建项目的设置，如果尚未创建服务连接，则创建一个新的服务连接。选择 **服务主体 (自动)**，然后从下拉列表中选择订阅和资源组，并在下一个窗口中提供服务连接名称。请确保已选中 **授予所有管道的访问权限** 复选框。

以下图片展示了讨论的步骤：

![](img/cc4299656808e62a294f1843a1e18e72_307_0.png)

图 11.24: 新 Azure 服务连接

现在，您需要更新将在 Azure CI/CD 管道中使用的文件。您可以参考以下代码来修改相应的脚本。此处仅讨论代码修改，因为您可以保留原始脚本中其余代码的原样。

```
code/training/train.py
```

此文件将使用逻辑回归构建分类模型。模型训练后，它将记录交叉验证 (CV) 分数和准确率以供后续使用。然后，它将模型保存为 pickle 对象。此脚本将由 aml_service/10-TrainOnLocal.py 脚本调用。

以下代码更新已合并到现有脚本中：

- `import pickle`
- `from azureml.core import Workspace`
- `from azureml.core.run import Run`
- `import os`
- `from sklearn.linear_model import LogisticRegression`
- `from sklearn.model_selection import train_test_split, cross_val_score`
- `from sklearn.metrics import accuracy_score`
- `from sklearn.preprocessing import LabelEncoder`
- `from sklearn.externals import joblib`

```
import pandas as pd
import numpy as np
import json
import subprocess
from typing import Tuple, List

run = Run.get_submitted_run()

url = "https://gist.githubusercontent.com/suhas-ds/a318d2b1dda8d8cbf2d6990a8f0b7e8a/raw/9b548fab0952dd12b8fdf057188038c8950428f1/loan_dataset.csv"
df = pd.read_csv(url)

# fill the missing values for numerical cols with the median
num_col = ['LoanAmount','Loan_Amount_Term','Credit_History']
for col in num_col:

    df[col].fillna(df[col].median(), inplace=True)

# fill the missing values for categorical cols with mode
cat_col = ['Gender','Married','Dependents','Self_Employed']
for col in cat_col:

    df[col].fillna(df[col].mode()[0], inplace=True)

# Total Income = Applicant Income + Coapplicant Income
df['Total_Income'] = df['ApplicantIncome'] + df['CoapplicantIncome']

# drop unnecessary columns
cols = ['ApplicantIncome', 'CoapplicantIncome', "LoanAmount",
"Loan_Amount_Term", 'Loan_ID']
df = df.drop(columns=cols, axis=1)

# Label encoding
cols = ['Gender',"Married","Education",'Self_Employed',"Property_Area","Loan_Status","Dependents"]

le = LabelEncoder()
for col in cols:
    df[col] = le.fit_transform(df[col])

# Train test data preparation
target = 'Loan_Status'

X = df.drop(columns=['Loan_Status'], axis=1)
y = df['Loan_Status']
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.30, random_state=42)

print("Running train.py")

model = LogisticRegression()
model.fit(X_train, y_train)
print("Accuracy is", model.score(X_test, y_test)*100)
# cross validation - it is used for better validation of the model
# eg: cv-5, train-4, test-1
cv_score = cross_val_score(model, X, y, cv=5)
print("Cross-validation is", np.mean(cv_score)*100)
run.log("CV_score", np.mean(cv_score)*100)
y_pred = model.predict(X_test)
print("Accuracy = " , accuracy_score(y_test, y_pred))
run.log("accuracy", accuracy_score(y_test, y_pred))

# Save the model as part of the run history
model_name = "sklearn_classification_model.pkl"
# model_name = "."

with open(model_name, "wb") as file:
    joblib.dump(value=model, filename=model_name)
```

### code/score/score.py

此脚本将用于测试 Web 服务。此处，更新已保存模型的路径，然后更新要使用 Web 服务进行预测的输入测试数据。

以下代码更新已合并到现有脚本中：

```
1. model_path = Model.get_model_path(model_name="sklearn_classification_model.pkl")
```

根据 ML 模型要求更新测试数据：

```
1. test_row = '{"data":[[1,1,0,1,0,1,2,3849],[1,1,3,0,0,0,1,5540]]}'
```

### aml_config/config.json

此处，您需要从 Azure 门户更新详细信息。其他脚本将使用此脚本中声明的变量。

以下代码更新已合并到现有脚本中：

```
{
  "subscription_id": "**********",
  "resource_group": "mlops",
  "workspace_name": "mlops_ws",
  "location": "centralus"
}
```

### environment_setup/install_requirements.sh

此 Bash 脚本负责使用 pip 安装 Python 包。

以下代码更新已合并到现有脚本中：

```
python --version
pip install azure-cli==2.37.0 #==2.0.69
pip install --upgrade azureml-sdk[cli]
pip install -r requirements.txt
```

### aml_service/00-WorkSpace.py

此文件将获取现有工作区的详细信息；不过，如果未找到，它将创建一个新工作区。

### aml_service/10-TrainOnLocal.py

此脚本触发 code/training/train.py 脚本在本地计算（生成管道的情况下为主机代理）上运行。如果您在远程 VM 上进行训练，则不需要在生成管道中使用此脚本。所有训练脚本都会生成一个输出文件 aml_config/run_id.json，用于记录训练运行的 run_id 和运行历史记录名称。run_id.json 由 20-RegisterModel.py 用于获取训练好的模型。将实验名称更新为 mlops-classification。

以下代码更新已合并到现有脚本中：

```
experiment_name = "mlops-classification"
```

### aml_service/15-EvaluateModel.py

在此步骤中，您将获取生产模型和新训练模型的运行历史记录以比较准确率。如果新模型的准确率优于现有模型，则新模型将被提升到生产环境；否则，现有模型将保持不变。不过，第一次时没有可比较的模型，因此它将进入 except 块并提升新模型。您可以更改需要比较的指标以及决定是否将新模型提升到生产环境的条件。在脚本末尾，如果新模型被提升到生产环境，它将在 aml_config/run_id.json 文件中记录新模型的实验名称和运行 ID。

以下代码更新已合并到现有脚本中：

```
production_model_acc = production_model_run.get_metrics().get("accuracy")
new_model_acc = new_model_run.get_metrics().get("accuracy")
print(
"Current Production model accuracy: {}, New trained model accuracy: {}".format(
production_model_acc, new_model_acc
)
)

promote_new_model = False
if new_model_acc > production_model_acc:
promote_new_model = True
print("New trained model performs better, thus it will be registered")
```

### aml_service/20-RegisterModel.py

此脚本负责注册新模型。它将查找 aml_config/run_id.json；如果未找到 run_id，它将打印消息 No new model to



register as production model perform better written inside the **except** block and exit from the code.

将模型注册为生产模型，最好在 **except** 块中编写，并从代码中退出。

If the run id is found in `aml_config/run_id.json`, it will register the model. Finally, it will write the registered model details to `/aml_config/model.json`.

如果在 `aml_config/run_id.json` 中找到运行 ID，则会注册该模型。最后，它会将已注册模型的详细信息写入 `/aml_config/model.json`。

The following code update is incorporated into the existing script:

以下代码更新已合并到现有脚本中：

```
# Download Model to Project root directory

model_name = "sklearn_classification_model.pkl"

run.download_file(
    name="./outputs/" + model_name, output_file_path="./model/" + model_name
)

print("Downloaded model {} to Project root directory".format(model_name))

os.chdir("./model")

model = Model.register(
    model_path=model_name, # This points to a local file
    model_name=model_name, # This is the name the model is registered as
    tags={"area": "loan", "type": "classification", "run_id": run_id},
    description="Classification model for loan dataset",
    workspace=ws,
)
```

### aml_service/30-CreateScoringImage.py

In the beginning, it will look for the `aml_config/model.json` file generated from the previous step. If it is not found, the script will be terminated with the message **No new model to register thus no need to create new scoring image**.

开始时，它会查找上一步生成的 `aml_config/model.json` 文件。如果找不到，脚本将显示消息 **没有新模型可注册，因此无需创建新的评分镜像** 后终止。

The following code update is incorporated into the existing script:

以下代码更新已合并到现有脚本中：

```
image_name = "loan-model-score"

image_config = ContainerImage.image_configuration(
    execution_script="score.py",
    runtime="python-slim",
    conda_file="conda_dependencies.yml",
    description="Image with logistic regression model",
    tags={"area": "loan", "type": "classification"},
)
```

This will create the image for the model, and at the end, capture the image details, such as name, version, creation_state, image_location, and image_build_log_uri in the /aml_config/image.json.

这将为模型创建镜像，最后在 /aml_config/image.json 中捕获镜像详细信息，如名称、版本、创建状态、镜像位置和镜像构建日志 URI。

### aml_service/50-deployOnAci.py

**Azure Container Instances (ACI)** is an Azure service that enables users to run a container on the Azure cloud without demanding the use of a **Virtual Machine (VM)**。

**Azure 容器实例 (ACI)** 是一项 Azure 服务，使用户能够在 Azure 云上运行容器，而无需使用 **虚拟机 (VM)**。

In the beginning, it will look for the _aml_config/image.json_ file generated from the previous step. If it is not found, the script will be terminated with the message **No new model, thus no deployment on ACI.**

开始时，它会查找上一步生成的 _aml_config/image.json_ 文件。如果找不到，脚本将显示消息 **没有新模型，因此不在 ACI 上部署。** 后终止。

The following code update is incorporated into the existing script:

以下代码更新已合并到现有脚本中：

```
aciconfig = AciWebservice.deploy_configuration(
    cpu_cores=1,
    memory_gb=1,
    tags={"area": "loan", "type": "classification"},
    description="A loan prediction app",
)
```

This script will create a web service and capture the ACI details in /aml_config/aci_webservice.json at the end of the script.

此脚本将创建 Web 服务，并在脚本结束时将 ACI 详细信息捕获到 /aml_config/aci_webservice.json 中。

### aml_service/60-AciWebserviceTest.py

In the beginning, it will look for the _aml_config/aci_webservice.json_ file generated from the previous step. If it is not found, the script will be terminated with the message **No new model, thus no deployment on ACI.**

开始时，它会查找上一步生成的 _aml_config/aci_webservice.json_ 文件。如果找不到，脚本将显示消息 **没有新模型，因此不在 ACI 上部署。** 后终止。

The following code update is incorporated into the existing script:

以下代码更新已合并到现有脚本中：

```
# Input for Model with all features
input_j = [[[1,1,0,1,0,1,2,3849],[1,1,3,0,0,0,1,5540]]]
```

## Configure CI pipeline

## 配置 CI 管道

At this stage, you will configure the CI pipeline. This pipeline will execute the following tasks:

此阶段，您将配置 CI 管道。该管道将执行以下任务：

- Set up Python version 3.6.
- Install required dependencies.
- Create or get Azure Machine Learning (AML) workspace.
- Build and train the ML model.
- Evaluate newly trained model performance against the existing model to decide whether the model is to be promoted to production.
- Register model in Azure Machine Learning (AML) service.
- Create a scoring Docker image with the required dependencies.
- Publish the artifacts (all files) to the repo.

- 设置 Python 3.6 版本。
- 安装所需的依赖项。
- 创建或获取 Azure 机器学习 (AML) 工作区。
- 构建并训练 ML 模型。
- 评估新训练模型与现有模型的性能，以决定是否将模型提升到生产环境。
- 在 Azure 机器学习 (AML) 服务中注册模型。
- 使用所需的依赖项创建评分 Docker 镜像。
- 将构件（所有文件）发布到仓库。

The following figure shows the steps of the CI pipeline:

以下图显示了 CI 管道的步骤：

![](img/cc4299656808e62a294f1843a1e18e72_314_0.png)

Figure 11.25: CI pipeline for ML

图 11.25: 机器学习的 CI 管道

Note: You need to select Azure service connection from the Azure subscription dropdown wherever necessary.

注意：在需要的地方，请从 Azure 订阅下拉列表中选择 Azure 服务连接。

Next, in the **Triggers** tab, select **Enable continuous integration** checkbox. This enables the CI pipeline to run as soon as any changes are pushed to the code repository.

接下来，在 **触发器** 选项卡中，选择 **启用持续集成** 复选框。这样可启用 CI 管道，以便在将任何更改推送到代码仓库时立即运行。

You can trigger the CI pipeline by pushing any changes to the repository. The Azure CI pipeline detects the changes in the repo and starts building the pipeline. To see the progress of the CI pipeline, switch to the **Summary** tab.

您可以通过向仓库推送任何更改来触发 CI 管道。Azure CI 管道会检测仓库中的更改并开始生成管道。要查看 CI 管道的进度，请切换到 **摘要** 选项卡。

The following figure displays the **Summary** tab. You can see the commit message on the top, followed by the summary and the jobs. The job status and progress of steps can be seen by clicking on **Phase 1**.

以下图显示了 **摘要** 选项卡。您可以在顶部看到提交消息，接着是摘要和作业。单击 **阶段 1** 可以查看作业状态和步骤进度。

![](img/cc4299656808e62a294f1843a1e18e72_315_0.png)

Figure 11.26: CI pipeline for ML-Jobs summary

图 11.26: 机器学习的 CI 管道 - 作业摘要

After clicking on Phase 1 under the Jobs section, you should see the progress of the CI pipeline. The following figure shows the terminal output of each CI pipeline step:

在作业部分单击阶段 1 后，您应该能看到 CI 管道的进度。以下图显示了每个 CI 管道步骤的终端输出：

![](img/cc4299656808e62a294f1843a1e18e72_316_0.png)

Figure 11.27: CI pipeline for ML-logs

图 11.27: 机器学习的 CI 管道 - 日志

## Configure CD pipeline

## 配置 CD 管道

Now that you have completed the CI pipeline configuration, it's time to configure the CD pipeline. The CD pipeline will deploy the image generated through the CI pipeline to the Azure Container Instance (ACI) and Azure Kubernetes Service (AKS). In the current case, the scope of the project is limited to ACI. However, you can deploy it on AKS to handle large amounts of traffic and make it scalable.

完成 CI 管道配置后，现在是配置 CD 管道的时候了。CD 管道将通过 CI 管道生成的镜像部署到 Azure 容器实例 (ACI) 和 Azure Kubernetes 服务 (AKS)。在当前情况下，项目范围仅限于 ACI。但是，您可以将其部署到 AKS 以处理大量流量并实现可扩展性。

This pipeline executes the following tasks:

此管道将执行以下任务：

- Set up Python version 3.6.
- Install the required dependencies.
- Deploy a web service on the Azure container instance (ACI).
- Test the ACI web service by passing data that needs to be tested.
- Deploy a web service on Azure container instance (AKS).
- Test the AKS service by passing the data to be tested.

- 设置 Python 3.6 版本。
- 安装所需的依赖项。
- 在 Azure 容器实例 (ACI) 上部署 Web 服务。
- 通过传递需要测试的数据来测试 ACI Web 服务。
- 在 Azure 容器实例 (AKS) 上部署 Web 服务。
- 通过传递要测试的数据来测试 AKS 服务。

The following figure shows the CD pipeline:

以下图显示了 CD 管道：

![](img/cc4299656808e62a294f1843a1e18e72_317_0.png)

Figure 11.28: CD pipeline for ML

图 11.28: 机器学习的 CD 管道

Now, navigate to Pipeline | Releases, select Deploy Web service and click on Edit pipeline.

现在，导航到 Pipeline | 发布版本，选择部署 Web 服务，然后单击编辑管道。

The following figure shows the QA – Deploy on ACI stage of the CD pipeline when switched to the Tasks tab.

切换到任务选项卡时，以下图显示了 CD 管道中 QA – 部署到 ACI 阶段。

![](img/cc4299656808e62a294f1843a1e18e72_317_1.png)

Figure 11.29: CD pipeline for ML-QA stage

图 11.29: 机器学习的 CD 管道 - QA 阶段

Note: You need to select Azure service connection from the Azure subscription dropdown wherever necessary.

注意：在需要的地方，请从 Azure 订阅下拉列表中选择 Azure 服务连接。

In the following figure, you can see the entire file path provided by the artifacts that are retrieved from the CI pipeline:

在以下图中，您可以看到从 CI 管道检索的构件提供的完整文件路径：

![](img/cc4299656808e62a294f1843a1e18e72_318_0.png)

Figure 11.30: CD pipeline for ML-QA stage requirement step

图 11.30: 机器学习的 CD 管道 - QA 阶段要求步骤

When you update the CD pipeline, you can run the CD pipeline manually by hitting the **Create Release** button or setting the auto trigger, which means that the CD pipeline starts executing upon completion of the CI pipeline. You need to make sure that continuous deployment triggers are enabled in the **Artifacts** stage and the **QA -Deploy on ACI** stage of the CD pipeline.

更新 CD 管道时，您可以通过单击 **创建发布版本** 按钮或设置自动触发器手动运行 CD 管道，这意味着 CD 管道将在 CI 管道完成后开始执行。您需要确保在 CD 管道的 **构件** 阶段和 **QA - 部署到 ACI** 阶段中启用了持续部署触发器。

In the following figure, you can see the CD pipeline triggers upon completion of the CI pipeline, which caused the **QA -Deploy on ACI** stage to start executing:

在以下图中，您可以看到 CD 管道在 CI 管道完成后触发，这导致 **QA - 部署到 ACI** 阶段开始执行：

![](img/cc4299656808e62a294f1843a1e18e72_319_0.png)

Figure 11.31: CD pipeline for ML-triggered after CI pipeline

图 11.31: 机器学习的 CD 管道 - CI 管道完成后触发

It takes a few minutes to execute all the steps. You should see the number of tasks completed and the status of the stage. If you want to see the details of each step, click on the Logs option.

执行所有步骤需要几分钟。您应该能看到完成的任务数量和阶段状态。如果要查看每个步骤的详细信息，请单击日志选项。

The following figure shows the status of each step with logs.

以下图显示了带日志的每个步骤的状态。

![](img/cc4299656808e62a294f1843a1e18e72_319_1.png)

Figure 11.32: CD pipeline for ML-QA stage logs

图 11.32: 机器学习的 CD 管道 - QA 阶段日志

When ACI deployment is completed, it waits for manual approval from the developer but for a limited time. You can update the time from the options. After approval, it will deploy to the AKS. If you want to automate this step, you can remove the manual approval or set auto approval. However, it is recommended to keep manual approval before deploying it on AKS.

ACI 部署完成后，它会等待开发者的手动批准，但仅限有限时间。您可以从选项中更新时间。批准后，它将部署到 AKS。如果要自动执行此步骤，可以删除手动批准或设置自动批准。但是，建议在部署到 AKS 之前保留手动批准。

In the following figure, you can see that the QA – Deploy on ACI stage is completed, and it is pending approval for deploying it on AKS. You can set the time for approval requests to be active. After approval, the pipeline will deploy the app using AKS.

在以下图中，您可以看到 QA – 部署到 ACI 阶段已完成，并且正在等待批准以部署到 AKS。您可以设置批准请求的有效时间。批准后，管道将使用 AKS 部署应用。

![](img/cc4299656808e62a294f1843a1e18e72_320_0.png)

Figure 11.33: Azure pipeline for ML-completed

图 11.33: 机器学习的 Azure 管道 - 已完成

Now, head over to the Azure Machine Learning studio, and go to Jobs from the left panel. You should see the experiment with the name provided in the training script, that is, **mlops-classification**. On the right side, you can see the details like the experiment name, the date of creation, and the last submission. When you go to the experiment, you will see the run information with status and other metadata. On the top, you can see metrics details with graphs. In the current case, accuracy and CV score are being logged. You can assess each job’s details by clicking on it.

现在，请转到 Azure 机器学习工作室，然后从左侧面板进入作业。您应该能看到训练脚本中提供的名称的实验，即 **mlops-classification**。在右侧，您可以看到实验名称、创建日期和上次提交等详细信息。进入实验后，您将看到带有状态和其他元数据的运行信息。在顶部，您可以看到带图表的指标详细信息。在当前情况下，正在记录准确率和 CV 分数。您可以单击每个作业来评估其详细信息。

The following figure shows the model metrics, that is, accuracy and CV score, along with run information and other details. In the graphs, you can see the value of each metric logged in the runs separately.

以下图显示了模型指标（即准确率和 CV 分数），以及运行信息和其他详细信息。在图表中，您可以看到各个运行中分别记录的每个指标的值。




## mlops-classification

图 11.34：Azure 机器学习-模型指标

当模型部署在 Azure 容器实例 (ACI) 中时，您将获得评分 URI，后续应用程序可以使用它。

以下图显示了 CI/CD 管道脚本创建的终结点：

## 终结点

| 名称 | 创建者 | 评分 URI | 标记 | 位置 |
|---|---|---|---|---|
| aciwebservice061314 | 服务主体 | http://81930dc4-23d3-4541-... | 区域：贷款 类型：分类 | 美国中部 |

图 11.35：AML 实时终结点

您可以通过传递输入数据后评估结果来评估模型终结点。此外，您可以使用 C#、Python 和 R 等其他语言来使用终结点。

在以下图中，您可以在传递测试数据后，在测试结果下看到模型终结点生成的输出：

默认目录 > mlops_ws > 终结点 > aciwebservice061314

## aciwebservice061314

![](img/cc4299656808e62a294f1843a1e18e72_322_0.png)

图 11.36：AML 实时终结点测试

您也可以在 Postman 中评估相同的终结点。以下图显示了在 Postman 中测试评分 URI：

![](img/cc4299656808e62a294f1843a1e18e72_322_1.png)

图 11.37：在 Postman 中测试 AML 实时终结点

至此，您已学习如何使用 Azure DevOps 和 Azure 机器学习服务自动化 CI/CD 工作流。您已探索 GitHub Actions 和 Azure DevOps 方法来构建自动化工作流，以在生产环境中部署模型。到现在，您应该已熟悉 Azure 云及其提供的服务及其实现。

## 结论

在本章中，您学习如何在 Azure 平台 (PaaS) 上部署应用。您还使用 GitHub Actions 构建了自动化 CI/CD 管道。使用 Azure 容器注册表 (ACR) 在 Azure 应用服务中部署了 ML Web 应用。此外，您将 tox 与 GitHub Actions 集成，在将 ML Web 应用部署到 Azure 之前，将测试用例作为 CI/CD 管道的一部分来运行。

之后，您学习如何使用 Azure DevOps 和 Azure 机器学习服务 (AML) 部署 ML 应用，该服务提供机器学习即服务 (MLaaS)。您分析了 Azure 机器学习工作室中运行记录的指标，并将示例数据传递给终结点并评估了结果。

在下一章中，您将探索 GCP 平台以部署 ML 应用。

## 要点总结

- 您需要授权 GitHub Actions 以自动化管道的 CD 部分并提供所需详细信息。
- Azure 基于角色的访问控制 (RBAC) 是构建在 Azure 资源管理器之上的授权系统，可对 Azure 资源提供精细的访问管理。
- 实验由从脚本启动的多个运行组成。
- 在 Azure DevOps 模板中，aml_service/15-EvaluateModel.py 脚本将在部署阶段之前将最新模型的性能指标与已部署模型进行比较。这意味着该脚本中编写了一组规则，用于决定模型是否可以提升到下一步。

## 选择题

- 1. ______ 可定义为训练脚本的单次迭代。
  - a) 一个运行
  - b) 一个实验
  - c) 一个工作区
  - d) ACR

- 2. Azure 主要使用 ______ 定价计划。
  - a) 无限（适用于所有 Azure 服务）
  - b) 季度
  - c) 月度
  - d) 按量付费

## 答案

- 1. a
- 2. d

## 问题

- 1. Azure 机器学习 (AML) 服务的用途是什么？
- 2. 如何从本地终端登录 Azure？
- 3. 解释 Azure 管道阶段的工作原理。

## 第 12 章：在 Google Cloud Platform 上部署 ML 模型

## 简介

云计算是按需交付计算机系统资源（例如服务器、数据库、分析、存储和网络）。这些资源和服务在本地之外可用；然而，它们可以根据需求通过云（互联网）访问。这意味着您无需在本地构建大型基础架构。这对企业和个人有利，因为他们可以在按量付费计划下立即获得所需的系统资源和服务。资源和服务可以快速添加或删除，这使您能够高效地花钱。

请参阅前面的章节，了解打包 ML 模型、FastAPI、Docker 和 CI/CD 管道等概念，因为它们是本章的先决条件。

## 结构

本章将涵盖以下主题：

- 在 Google Cloud Platform (GCP) 上创建并设置帐户
- Cloud Source Repositories
- Cloud Build
- Container Registry
- 使用手动触发器将基于 Web 的 ML 应用部署到 Google Kubernetes Engine (GKE)
- 构建自动化 CI/CD 管道以在 Google Kubernetes Engine (GKE) 上部署基于 Web 的 ML 应用

## 目标

学完本章后，您应该能够在 Google Kubernetes Engine (GKE) 上部署 ML 模型。您可以通过简单步骤创建完全自动化的 CI/CD 管道，无需集成任何外部工具、服务或平台。您将使用 Cloud Source Repository 和 Kubernetes 集群在 GCP 上创建远程 Git 存储库，以构建可扩展的 ML 应用。您还将学习在本章中为 Kubernetes 创建清单文件。到最后，您应该能够在 Cloud Build 中创建触发器，以自动部署 ML 应用。

## Google Cloud Platform (GCP)

**Google Cloud Platform** (**GCP**) 包含 Google 提供的云计算服务，该服务使用与 YouTube、Gmail 和其他 Google 平台或服务相同的基础架构。

该平台为计算、机器学习和 AI、网络、IoT 和 BigData 提供一系列服务。以下是 GCP 提供的几项服务：

- Google 的计算引擎提供 VM 实例来运行代码和部署应用。
- AI 和机器学习服务，例如 Vertex AI，它是端到端 ML 生命周期管理和统一平台。数据科学家可以轻松上传数据、构建、训练和测试 ML 模型。
- AI 构建块，例如 Vision AI，可帮助使用 AutoML 从图像中获取洞察。
- 容器服务，例如 Container Registry 和 **Google Kubernetes Engine** (**GKE**)，管理 Docker 镜像并允许开发人员构建可扩展的应用程序。
- BigQuery 和 Data Proc 用于处理和分析大量数据。
- 数据库，例如 Cloud SQL 和 Cloud Bigtable，在云上存储数据。
- 开发者工具，例如 Cloud Build、Cloud Source Repositories 和 Google Cloud Deploy，用于自动化 CI/CD 过程。
- 管理工具，例如 Deployment Manager 和 Cost Management，帮助您跟踪项目中使用的工具或服务的部署和成本。
- 网络服务，例如 **虚拟私有云 (VPC)**，允许您在公有云内创建虚拟私有云环境。在不同区域创建的多个项目可以相互通信，而无需通过公共互联网公开通信。
- 安全服务，例如云密钥管理、防火墙和安全中心。
- 存储服务，例如 Cloud Storage，允许您存储构件。
- 无服务器计算，例如 Cloud Function，是一种事件驱动的无服务器计算平台。这种功能即服务 (FaaS) 允许您在无服务器或容器的情况下运行代码。
- 运营服务，例如 Cloud Logging 和 Cloud Monitoring，可让您跟踪已部署模型或应用程序的性能、延迟等。
- 它还提供其他服务，例如迁移、IoT、事件管理、身份和访问、混合和多云、备份和恢复。

您应该已经了解了 GCP 及其服务的要点；现在，您将学习如何在 GCP 上部署机器学习模型。完成本章后，您将能更好地在 GCP 上开展 ML 模型部署工作。

GCP 提供为期 90 天、包含 300 美元信用额度的免费试用帐户。这将为新客户提供实践经验，以便他们探索 GCP 提供的服务。

## 设置 GCP 帐户

首先，设置 GCP 帐户；但是，这是一次性活动。登录后应立即可用：

### 步骤 1：

创建 GCP 帐户（如果您没有）并登录。免费试用帐户可以在 GCP 平台 https://cloud.google.com/free 上创建。首先，使用您的 Gmail ID 登录；然后它将重定向到 GCP 免费试用页面。从下拉列表中选择您的国家/地区，接受服务条款，然后单击 **继续**。接下来，选择 **个人**（个人使用）或 **商业**（如果是商业帐户）。之后，提供姓名、地址和城市等个人详细信息。最后，提供付款方式详细信息并完成流程。




## 步骤 2：

登录账户后，创建新项目，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_328_0.png)

图 12.1：创建新项目

点击 **新建项目** 按钮并提供项目名称。在此示例中，项目名称为 MLOps，项目 ID 将自动生成；不过，它可以编辑。在此示例中，项目 ID 为 mlops-54321。位置可预先选择或更改。

单击 **创建** 按钮以完成此过程。

> 注：项目 ID 对每个项目都是唯一的。

## Cloud Source Repositories

在此示例中，使用的是 Git 仓库，即 Cloud Source Repository；不过，也可以使用其他远程 Git 仓库，例如 GitHub。Cloud Source Repositories 是托管在 GCP 上的私有 Git 仓库。可在单个项目中创建多个 Git 仓库。它支持标准的 Git 命令集，例如 push、pull、clone 和 log。Cloud Source Repositories 可添加为本地 Git 仓库的远程仓库。它支持协作并提供安全性。不过，建议不要在其中存储任何个人或机密数据。好处是，GCP 的 Cloud Source Repositories 允许您每月免费存储最多 50 GB 的数据。

现在，搜索并启用 Cloud Source Repositories API，该 API 允许访问由 Google 托管的源代码仓库。

接下来，在 Cloud Source Repositories 中创建新仓库，并提供仓库名称和项目 ID，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_329_0.png)

图 12.2：在 Cloud Source Repositories 中创建新仓库

创建 Cloud Source Repository 后，它将为空。因此，请选择 **将仓库克隆到本地 Git 仓库** 选项。接下来，前往 **手动生成的凭据**，并按照链接 **生成并存储 Git 凭据** 中的说明生成凭据。只需复制命令并在本地终端中运行即可。在下图中，已创建空的 Cloud Source Repository 并选择了选项，如讨论所示：

![](img/cc4299656808e62a294f1843a1e18e72_329_1.png)

图 12.3：将仓库克隆到本地 Git 仓库

此后，仓库应可从本地终端访问。现在，创建新目录并将 Cloud Source Repository 克隆到本地计算机，将代码文件包含在其中，并从本地计算机将其推送到 Cloud Source Repository。

让我们考虑贷款预测场景，问题陈述是预测客户的贷款是否会获批。请随意实现超参数调优并优化模型。

首先，创建 ML 代码包，并使用 FastAPI 构建 Web 应用。然后，创建测试用例和依赖文件、Dockerfile 以及 docker-compose 文件。最后，为 GCP 部署创建配置文件，即 cloudbuild.yaml、deployment.yaml 和 service.yaml。

注意：`src` 目录中的代码文件，请参考第 4 章：打包 ML 模型中开发的 ML 模型包；其余代码文件，请参考第 11 章：在 Microsoft Azure 上部署 ML 模型。新增的代码文件为 cloudbuild.yaml、deployment.yaml 和 service.yaml。删除 workflow 目录 .github。此外，tox.ini 文件已针对本场景进行更新。

代码仓库也可在 GitHub 上找到，网址为 https://github.com/suhas-ds/GCP。

以下目录结构显示了 CI/CD 管道文件：

```
.
|-- k8s
|   |-- deployment.yaml
|   |-- service.yaml
|-- src
|   |-- build
|   |   |-- bdist.linux-x86_64
|   |   |-- lib
|   |-- prediction_model
|   |   |-- config
|   |   |-- datasets
|   |   |-- processing
|   |   |-- __pycache__
|   |   |-- trained_models
|   |   |-- __init__.py
|   |   |-- pipeline.py
|   |   |-- predict.py
|   |   |   |___ train_pipeline.py
|   |   |   |___ VERSION
|   |   |___ prediction_model.egg-info
|   |   |   |___ dependency_links.txt
|   |   |   |___ PKG-INFO
|   |   |   |___ requires.txt
|   |   |   |___ SOURCES.txt
|   |   |   |___ top_level.txt
|   |   |___ tests
|   |   |   |___ pytest.ini
|   |   |   |___ test_predict.py
|   |   |___ MANIFEST.in
|   |   |___ README.md
|   |   |___ requirements.txt
|   |   |___ setup.py
|   |   |___ tox.ini
|___ cloudbuild.yaml
|___ docker-compose.yml
|___ Dockerfile
|___ main.py
|___ pytest.ini
|___ requirements.txt
|___ runtime.txt
|___ start.sh
|___ test.py
|___ tox.ini
```

13 个目录，31 个文件

## tox.ini

tox 是一种免费开源工具，用于测试 Python 包或应用程序。它会创建虚拟环境并在其中安装所需的依赖项。最后，它会针对 Python 包 prediction_model 运行测试用例。如下所示更新 tox.ini 文件：

```
1. [tox]
2. envlist = my_env
3. skipdist=True
4.
5. [testenv]
6. install_command = pip install {opts} {packages}
7. deps =
8.   -r requirements.txt
9.
10. setenv =
11. PYTHONPATH=src/
12.
13. commands=
14.   pip install requests
15.   pytest -v test.py --junitxml=test_log.xml
16.   pytest -v src/tests/ --junitxml=src_test_log.xml
```

**skipdist=True** 标志表示不执行打包操作。这意味着在执行任何测试之前，包不会安装到虚拟环境中。将 **PYTHONPATH** 设置为 `src` 目录，Python 包文件位于该目录。在 commands 下，将执行 pytest 命令，测试结果将导出为 `.xml` 文件。

从本地终端成功推送后，代码文件将显示在 Cloud Source Repository 中，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_333_0.png)

图 12.4：代码文件已推送到 Cloud Source Repository

## Cloud Build

Cloud Build 是一种无服务器平台，允许用户在云中快速自动化构建、测试和部署容器。Cloud Build 与 App Engine、Kubernetes Engine、Cloud Run、Cloud Functions 和 Firebase 的部署环境协同工作。如果使用量超出 GCP 分配的免费配额，将按使用的构建分钟数收费。

Cloud Build 配置文件类型可以是 YAML 或 JSON。该文件包含开发者指定的一系列步骤和命令来执行构建。每个构建步骤在其自己的 Docker 容器中运行。不过，这些容器通过与 Cloud Build 的本地 Docker 网络相互连接。这允许构建步骤进行通信和共享信息。

在 API 和服务中搜索并启用 Cloud Build API。Cloud Build 使用特殊的服务帐户代表您执行构建。Cloud Build 服务帐户的电子邮件格式为 [PROJECT_NUMBER]@cloudbuild.gserviceaccount.com。它拥有执行从仓库获取代码、获取项目详细信息以及将对象写入与项目关联的存储空间等任务的权限。不过，可以将此默认服务帐户更改为开发者自己的服务帐户，以代表开发者执行构建，且开发者可以设置特定权限。

## cloudbuild.yaml

Cloud Build 构建工具是预安装了常用语言和工具的容器镜像。Cloud Build 提供可在配置文件中用于执行命令的预构建 Docker 镜像。这些预构建镜像可在 Container Registry 的 gcr.io/cloud-builders/ 中找到。

在此示例中，cloudbuild.yaml 文件将使用 tox 和 pytest 运行测试。接下来，它将带有 latest 标签构建 Docker 容器镜像。随后，它将把镜像推送到 Container Registry，并运行 bash 命令以检查当前目录中的文件列表。最后，它将从 Docker 容器中拉取镜像以将其部署到 Google Kubernetes Engine (GKE)。

```
1. steps:
2. # Run test
3. - name: 'python:3.7-slim'
4.   id: Test
5.   entrypoint: /bin/sh
6.   args:
7.   - -c
8.   - 'python -m pip install tox && tox'
9.
10. # Build the image
11. - name: 'gcr.io/cloud-builders/docker'
12.   id: Build
13.   args: ['build', '-t', 'gcr.io/$PROJECT_ID/mlapp:latest', '.']
14.   timeout: 200s
15.
16. # Push the image
17. - name: 'gcr.io/cloud-builders/docker'
18.   id: Push
19.   args: ['push', 'gcr.io/$PROJECT_ID/mlapp:latest']
20.
21. - name: 'gcr.io/cloud-builders/gcloud'
22.   id: Bash
23.   entrypoint: /bin/sh
```





```
24. args:
25. - -c
26. - |
27. echo "List of files and directories within the current working directory"
28. ls -l
29.
30.# Deploy container image to GKE
31.- name: "gcr.io/cloud-builders/gke-deploy"
32. id: Deploy on GKE
33. args:
34. - run
35. - --filename=k8s/
36. - --image=gcr.io/$PROJECT_ID/mlapp:latest
37. - --location=us-west1-b
38. - --cluster=mlkube
```

在前面的文件中，主要使用了三个（受支持的）构建器镜像：

- **gcr.io/cloud-builders/docker**: 构建并将 Docker 容器镜像推送到容器注册表
- **gcr.io/cloud-builders/gcloud**: 运行内联 Bash 脚本
- **gcr.io/cloud-builders/gke-deploy**: 在 GKE 中部署容器化应用

此外，python:3.7-slim 是用于使用 tox 测试代码的公开可用镜像。如果要从 Docker Hub 使用任何镜像，只需在单引号中提供镜像名称即可。但是，如果镜像来自其他注册表，则需要在单引号中指定完整的注册表路径。构建步骤的 args 字段接受参数列表，并将其传递给由 name 字段引用的镜像。

## 容器注册表

容器注册表是 GCP 提供的一种用于管理和存储私有容器镜像的服务。它允许用户安全地推送和拉取容器镜像。在此示例中，Docker 容器镜像将被推送到容器注册表。Kubernetes 引擎将拉取该镜像以在云端部署 ML 应用。

容器注册表使用主机名、项目 ID、镜像以及标签或镜像摘要来访问镜像，其中镜像摘要是镜像内容的 sha256 哈希值。格式如下：

```
HOSTNAME/PROJECT-ID/IMAGE : TAG
```

Or

```
HOSTNAME/PROJECT-ID/IMAGE : @IMAGE-DIGEST
```

启用容器注册表 API 后，下图显示了 GCP 容器注册表，其中 mlapp 是应用名称，gcr.io 是主机名。目前，gcr.io 在美国托管镜像。

![](img/cc4299656808e62a294f1843a1e18e72_336_0.png)

图 12.5：容器注册表

## Kubernetes

容器编排是运行容器化工作负载和服务所需操作流程的自动化。它可以自动化部署、扩容/缩容、生命周期管理、负载均衡、配置、安全、资源分配、健康监控以及容器网络等任务。

Kubernetes（也称为 K8s 或 Kube）是一个用于容器编排的开源平台。它允许应用在不中断生产环境中运行的应用的情况下随时扩缩容。它可以快速创建多个容器化应用副本以应对流量增加，并在流量减少时自动减少副本数量。

在 Kubernetes 上部署会创建包含容器的 Pod。Pod 是 Kubernetes 环境中的最小单元。一个 Pod 可以包含一个或多个容器。它始终在节点上运行，但一个节点可以拥有多个 Pod。节点只是 Kubernetes 环境中的一个工作节点（VM 或物理机）。所有节点均由控制平面管理。

每个节点都运行 Kubelet 和容器运行时（例如 Docker）。Kubelet 是控制平面与节点之间的通信媒介。它还管理节点中的 Pod 和运行中的容器。Docker 等容器运行时会从注册表拉取镜像，并运行容器化应用。

## Google Kubernetes Engine (GKE)

Google Kubernetes Engine (GKE) 提供用于管理、部署和扩缩容容器化应用的基础架构。GKE 的底层架构由一组组装成集群的 Compute Engine 实例组成。

清单是一个包含要部署的所有组件描述的文件（JSON 或 YAML）。这些清单文件指导 Kubernetes 在容器之间进行网络通信。Kubernetes 将容器部署到集群中，并为容器识别最佳主机。在决定主机后，它会根据预先规划的规格管理容器的生命周期。

在 GCP 控制台中搜索并启用 Kubernetes Engine API，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_337_0.png)

图 12.6：Kubernetes Engine API

接下来，单击 GCP 账户右上角的“Activate Cloud Shell”图标。它将打开一个基于云的终端：

```
gcloud container clusters create mlkube --zone "us-west1-b" --machine-type "n1-standard-1" --num-nodes "1" --project mlops-54321
```

```
Created [https://container.googleapis.com/v1/projects/mlops-54321/zones/us-west1-b/clusters/mlkube]
To inspect the contents of your cluster, go to: https://console.cloud.google.com/kubernetes/workload/_/gcloud/us-west1-b/mlkube?project=mlops-54321
Kubeconfig entry generated for mlkube.
NAME: mlkube
LOCATION: us-west1-b
MASTER_VERSION: 1.22.8-gke.202
MASTER_IP: 34.168.38.219
MACHINE_TYPE: n1-standard-1
NODE_VERSION: 1.22.8-gke.202
NUM_NODES: 1
STATUS: RUNNING
```

图 12.7：使用 Cloud Shell 创建 Kubernetes 集群

Kubernetes 集群成功创建后，可以使用 GKE 服务查看其详细信息，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_338_0.png)

图 12.8：Kubernetes 集群

所有清单文件都包含 apiVersion 字段。每个 Kubernetes 配置文件都有三个部分：metadata、specification 和 status。metadata 和 specification 由开发人员在配置文件中提供；然而，status 部分由 Kubernetes 管理。例如，如果声明了 2 个副本但只有一个副本正在运行，那么 Kubernetes 会检查状态并创建另一个副本，以使所需状态与实际状态一致。如下所示，Kubernetes 配置文件位于 k8s 目录中。labels 和 selectors 负责连接服务和部署文件。service.yaml 和 deployment.yaml 文件中应使用相同的标签，以便服务和部署之间成功通信。

```
k8s
|-- deployment.yaml
|-- service.yaml
```

## deployment.yaml

此文件包含 Kubernetes 部署的配置，例如要创建的副本数和要部署的容器镜像。deployment.yaml 的作用是启动带有容器化应用的 Pod，并确保 Kubernetes 集群中始终运行所需数量的副本。在以下文件中，template 是 Pod 的蓝图。它有自己的 metadata 和 specification。在此示例中，replicas 字段设置为 2，这意味着它将创建两个 Pod 副本。

```
1. apiVersion: apps/v1
2. kind: Deployment
3. metadata:
4. name: loan-prediction
5. spec:
6. replicas: 2
7. selector:
8. matchLabels:
9. app: mlapp
10. template:
11. metadata:
12. labels:
13. app: mlapp
14. spec:
15. containers:
16. - name: loan-prediction-app
17. image: gcr.io/mlops-54321/mlapp:latest
18. ports:
19. - containerPort: 8000
```

## service.yaml

此文件将容器化应用连接到最终用户。service.yaml 的作用是向由 deployment.yaml 创建的 Pod 公开一个接口，从而实现集群与服务之间的网络访问。它将部署的应用公开到外部世界。容器化应用的端口 8000 与端口 80 映射。在 ports 中，可以指定多个端口。在此示例中，服务类型为 LoadBalancer，它将通过 GCP（云提供商）的负载均衡器公开服务。标签选择器有助于定位 Pod。在此示例中，mlapp 是一个标签。

```
1. apiVersion: v1
2. kind: Service
3. metadata:
4. name: mlapp
5. spec:
6. type: LoadBalancer
7. selector:
8. app: mlapp
9. ports:
10. - port: 80
11. targetPort: 8000
```

注意：在 targetPort 字段中，使用大写字母 'P'，因为它是一个键值对。在键值对中，第二个单词的首字符应为大写。

## 使用 Cloud Shell 进行部署 – 手动触发

首先，打开 Cloud Shell 并使用 `git clone` 命令克隆远程 Git 仓库。现在，代码文件在 GCP Cloud Shell 终端中可用。使用以下命令手动运行 `cloudbuild.yaml` 文件：

```
gcloud builds submit --config cloudbuild.yaml --project=mlops-54321
```

此命令执行需要几分钟。在此场景中，流水线被手动触发，一系列步骤将从 `cloudbuild.yaml` 文件依次执行。

下图显示了前面命令的输出，其中给出了使用 Kubernetes 部署的应用的详细信息，例如部署的 ML 应用的 IP 地址、源、持续时间、状态，以及工作负载、服务、配置和存储的 GKE URL。

![](img/cc4299656808e62a294f1843a1e18e72_340_0.png)

图 12.9：使用手动触发在 GKE 上部署 ML 应用





## 使用 Cloud Build 构建 CI/CD 流水线

GCP 提供了一组用于 CI/CD 流水线的服务。在上一节中，构建是通过 Cloud Shell 终端手动触发的。为了自动化手动流程，需要使用自动触发器构建 CI/CD 流水线。以下图示了 GCP 提供的 CI/CD 服务列表：

### CI/CD

### 持续集成与持续交付

| 名称 | 描述 |
| :--- | :--- |
| Cloud Build | 持续集成交付平台 |
| Container registry | 私有容器镜像仓库存储 |
| Source Repositories | 托管的私有 Git 代码库 |
| Artifact Registry | 通用构建制品管理 |
| Cloud Deploy | 面向 GKE 的托管式持续交付 |

图 12.10：GCP 提供的 CI/CD 服务

当有更新推送到 Cloud Source Repository (CSR) 时，将触发 CI/CD 流水线。Cloud Build 配置文件首先运行测试，然后构建并将容器镜像推送到 Container Registry。同时，它会读取 Kubernetes 清单并将其部署到 Kubernetes 引擎上。Kubernetes 引擎将拉取 Cloud Build 推送的容器镜像，并最终运行面向最终用户的容器化 ML 应用。

以下图示了在 GKE 上部署容器化应用的自动化 CI/CD 流水线：

![](img/cc4299656808e62a294f1843a1e18e72_342_0.png)

图 12.11：在 GKE 上部署 ML 应用的 CI/CD 流水线

## 在 Cloud Build 中创建触发器

在本节中，将在 Cloud Build 中创建一个触发器，用于查找 Cloud Build 配置文件（即 YAML 文件），构建并将 Docker 镜像推送到 Container Registry。它还负责在 Kubernetes 引擎中应用 Kubernetes 清单。

首先，从 Cloud Build 左侧面板进入“触发器”部分。第一次时，将显示“全局中未找到触发器”，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_342_1.png)

图 12.12：在 Cloud Build 中创建触发器

使用“创建触发器”按钮创建新触发器。接下来，为触发器在项目区域内提供唯一名称，并从下拉菜单中选择区域。描述和标签为可选项。

在此示例中，Name 为 AutoDeploy，Region 为 global（非区域），Description 为 Mlapp，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_343_0.png)

图 12.13：在 Cloud Build 中创建触发器 – 提供名称并选择区域

接下来，选择将触发流水线的仓库事件。它提供多个选项；但是，已选择 **推送到分支**。因此，推送到仓库 **主分支** 的任何更改都将触发流水线。触发器被调用时，这将查找仓库中的更改并克隆仓库。

在下图中，已选择 **推送到分支** 选项，并以 Cloud Source Repository 和主分支作为源：

![](img/cc4299656808e62a294f1843a1e18e72_343_1.png)

图 12.14：在 Cloud Build 中创建触发器 – 选择事件和源

最后，通过选择配置文件类型和位置来完成流程。在此示例中，配置类型选择了 Cloud Build 配置文件（YAML 或 JSON）选项，并提供了仓库中的 cloudbuild.yaml 文件位置，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_344_0.png)

图 12.15：在 Cloud Build 中创建触发器 – 选择配置文件类型及其位置

现在，推送到 Cloud Source Repository 的任何更新都将触发流水线。要查看构建历史记录，请从侧边栏进入 **历史记录** 部分，或通过仪表板中的链接查看。

以下图示了构建历史记录，包含 **状态**、**构建 ID**、**源 - loan_pred**（在此示例中即 Cloud Source Repository）以及该仓库的 **Ref - 主分支**。它还显示 **触发器类型**、**触发器名称** 和 **持续时间**，即完成构建所需的时间。

![](img/cc4299656808e62a294f1843a1e18e72_344_1.png)

图 12.16：构建历史

你可以查看每个步骤的实时构建日志。这有助于你调试构建过程中发生的错误。在最后一步，你应该能看到 GKE 部署详情，例如状态、名称以及访问应用的 URL。

以下图示了构建摘要，包含构建 ID 以及每个步骤的持续时间或耗时：

![](img/cc4299656808e62a294f1843a1e18e72_345_0.png)

图 12.17：构建详情 – 构建日志

Cloud Build 仪表板汇总了详细信息，例如最新构建的状态、持续时间、通过/失败构建的历史记录、构建的平均持续时间以及通过/失败百分比，如下图所示：

仪表板

![](img/cc4299656808e62a294f1843a1e18e72_345_1.png)

图 12.18：仪表板 - Cloud Build

部署成功后，你应该能在 GKE 中看到 ML 应用正在运行，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_346_0.png)

图 12.19：在 GKE 中运行的 ML 应用

Google Kubernetes 还提供应用监控服务。前往 GKE 中的服务入口 URL。这包括资源使用情况、详情、事件和日志。以下图示了已部署应用的监控概览：

![](img/cc4299656808e62a294f1843a1e18e72_346_1.png)

图 12.20：mlapp 监控

你现在已经学习如何使用 GitHub 创建一个简单的 CI/CD 流水线来在 GCP 平台上部署 ML 应用。不过，你可以根据业务和应用需求对其进行修改。

## 结论

本章中，带有 CI/CD 流水线的 ML 应用已部署到 Google Kubernetes Engine (GKE)。首先，你创建了 GCP 账号并创建了代码文件，包括用于 GCP 部署的 cloudbuild.yaml 和 Kubernetes 清单文件，并将它们推送到 Cloud Source Repositories (CSR)。接着，你创建了一个 Container Registry 用于推送和拉取 Docker 容器镜像，以及一个 Kubernetes 集群 ml-kube 来部署 ML 应用。最后，你启用了 Cloud Build API，并通过集成 Cloud Source Repositories (CSR) 创建了 AutoDeploy 触发器，以实现 ML 应用部署的自动化。

在下一章中，你将学习如何在 Amazon Web Services (AWS) 上部署 ML 应用。

## 要点总结

- Kubernetes 集群可在多个项目中共享。
- 创建 GCP 账号需要 Gmail 电子邮件地址。
- Cloud Build 是一个无服务器平台，可让你快速自动化构建、测试和部署容器。
- Cloud builders 是预装常用语言和工具的容器镜像。
- service.yaml 和 deployment.yaml 文件中应使用相同的标签，以确保服务和部署之间成功通信。

## 选择题

- 1. ________ 是 Google 提供的 CI/CD 服务。
- a) Cloud Build
- b) BigQuery
- c) 虚拟私有云 (VPC)
- d) Pub/Sub

- 2. 清单文件的推荐文件格式是 _______。
- a) .git
- b) YAML
- c) Python
- d) Shell 脚本

## 答案

- 1. a
- 2. b

## 问题

- 1. Cloud builders 预构建容器镜像的位置是什么？
- 2. Container Registry 的作用是什么？
- 3. 什么是容器编排？

## 加入本书的 Discord 空间

加入本书的 Discord 工作区，获取最新动态、优惠、全球技术动态、新版本发布以及与作者的会话：

https://discord.bpbonline.com

![](img/cc4299656808e62a294f1843a1e18e72_348_0.png)

## 第 13 章 在 Amazon Web Services 上部署 ML 模型

## 简介

云计算是指通过互联网存储和访问数据和应用程序。通常，数据存储在远程服务器上。简单来说，你可以从互联网上的任何位置访问数据和应用程序，无需担心物理或本地基础架构，这使得云计算在组织中越来越流行。

Amazon Web Services (AWS) 有助于解决本地基础架构问题。AWS 可以在几分钟内启动 100 到 1000 台服务器，多余或未使用的服务器将被删除。使用 AWS 可以轻松扩展应用程序。你可以为应用程序或数据添加更多存储空间。AWS 可帮助你专注于在云端构建和部署应用程序，无需担心从零开始搭建基础架构。

如果你需要学习所讨论的概念（例如封装 ML 模型、FastAPI、Docker 和 CI/CD 流水线），请参考前面的章节。

## 结构

本章将涵盖以下主题：

- Amazon Web Services (AWS) 简介





- AWS Elastic Container Registry (ECR)
- AWS CodeCommit
- Amazon Elastic Container Service (ECS)
- AWS CodeBuild
- Application Load Balancer (ALB)
- 将基于Web的机器学习应用与服务和Application Load Balancer (ALB)一起部署到Elastic Container Service (ECS)
- AWS CodePipeline
- 构建自动化CI/CD CodePipeline以在Amazon Web Services (AWS)上部署基于Web的机器学习应用

## 目标

本章学习完成后，您将能够在Amazon Elastic Container Service (ECS)上部署机器学习模型，而无需集成AWS以外的任何外部工具、服务或平台。您将使用AWS CodeCommit在AWS上创建远程Git仓库，并使用Amazon Elastic Container Service (ECS)集群运行可扩展的机器学习应用。您还将学习如何将Application Load Balancer (ALB)与Amazon Elastic Container Service (ECS)集成，以路由来自外部的请求。接下来，您将通过端口映射将服务端口与Docker端口集成，为Application Load Balancer (ALB)创建安全组，并学习将Docker容器镜像推送到AWS Elastic Container Registry (ECR)。完成本章后，您将能够使用AWS CodePipeline、AWS CodeBuild、AWS Elastic Container Registry (ECR)、Application Load Balancer (ALB)和Amazon Elastic Container Service (ECS)创建完全自动化的CI/CD流水线。

## Amazon Web Services (AWS)简介

Amazon Web Services (AWS)是一个可用于托管应用程序的云基础设施。2006年，AWS开始以Web服务的形式向市场提供IT服务。AWS是领先的云服务提供商之一。

## AWS计算服务

Amazon Web Services (AWS)提供计算服务，用于管理包含许多服务器或实例的工作负载。

以下是AWS提供的一些广泛使用的计算服务，可根据业务或应用程序需求使用。这些服务将在本章后面讨论。

## Amazon Elastic Compute Cloud (EC2)

Amazon EC2是一个代表远程服务器的虚拟机。Amazon EC2服务归类于**基础设施即服务（Infrastructure-as-a-Service，IaaS）**。Amazon EC2为应用程序提供可调整的计算能力，这些EC2机器称为实例。您可以创建具有不同计算大小的多个实例。创建后，您甚至可以升级RAM、vCPU等，因此无需重新创建新实例并再次配置。这就是使用“弹性”一词的原因。

## Amazon Elastic Container Service (ECS)

Amazon **Elastic Container Service** (**ECS**)可让您部署、扩展和管理容器化应用程序。它管理容器，并使开发人员能够在EC2实例集群上运行容器化应用程序。但是，它不基于Kubernetes。Amazon ECS是免费的，这意味着您无需为ECS集群付费。但是，需要为在ECS任务中运行的EC2实例支付额外费用。启动ECS集群主要有两种方式：

- Fargate启动
- EC2启动

Amazon ECS是AWS独有的技术。ECS可以轻松与AWS **Application Load Balancer (ALB)** 和 **Network Load Balancer (NLB)** 集成。

## Amazon Elastic Kubernetes Service (EKS)

Amazon **Elastic Kubernetes Service** (**EKS**) 是一项由AWS支持的Kubernetes服务，可让您在无需在EC2上手动安装Kubernetes的情况下在AWS上构建Kubernetes集群。Amazon Elastic Kubernetes Service (EKS)允许您在Kubernetes环境中管理或编排容器。您需要为EKS集群付费，并在Kubernetes pod中运行的EC2实例产生额外费用。Amazon EKS服务会为您设置和管理Kubernetes控制平面。

如果您需要多云功能以及与Amazon **Elastic Container Service** (**ECS**) 相比的其他功能，这是一个不错的选择。

## Amazon Elastic Container Registry (ECR)

Amazon **Elastic Container Registry** (**ECR**)允许开发人员在Amazon ECS上存储、共享和部署Docker镜像。它为其中存储的镜像提供安全性。Amazon Elastic Container Registry (ECR)与Amazon ECS集成。它类似于Docker Hub容器注册表，但由AWS管理。它允许您在其中存储私有Docker容器镜像。

## AWS Fargate

简单来说，AWS Fargate是面向容器的无服务器计算。您按分钟为容器使用的资源（如虚拟CPU（vCPU）和内存）付费。AWS Fargate与Amazon Elastic Container Service (ECS)和Amazon Elastic Kubernetes Service (EKS)兼容。

## AWS Lambda

AWS Lambda简单且成本较低。它是一种无服务器且事件驱动的计算服务；它是一种功能即服务（FaaS）。这意味着您无需管理服务器或集群。事件可以是任何简单的活动，例如用户单击链接以获取最新新闻。Lambda一词据说来源于λ演算和编程中的函数。它主要由三个组件组成：

- 函数：它是执行任务的实际代码。
- 配置：它决定函数的执行。
- 事件源：这是触发函数的事件。但是，此组件是可选的。

AWS Lambda是事件驱动编程的不错选择，或者在您需要访问多个服务时使用。

## Amazon SageMaker

AWS还提供一种名为Amazon SageMaker的机器学习平台即服务。它消除了手动管理和维护服务器的开销。它还降低了在AWS云上部署机器学习模型的时间和成本。

Amazon SageMaker是一个基于云的机器学习平台，使数据科学家和开发人员能够在生产环境中构建、训练、调整和部署机器学习模型。它使用Amazon Simple Storage Service (S3)存储数据，并带有超过15种最常用的内置机器学习算法用于训练数据。它将ML模型部署到SageMaker端点。Amazon SageMaker使用Amazon Elastic Container Registry (ECR)来存储容器镜像。

您现在应该已经了解了AWS及其服务的要点。您即将在Amazon Elastic Kubernetes Service (EKS)上部署机器学习模型。学完本章后，您将能够熟练使用AWS进行机器学习模型部署。

## 设置AWS账户

首先，设置一个AWS账户；但是，这是一次性活动。登录后即可立即使用。

AWS免费套餐为客户提供免费探索和试用AWS服务的功能，每项服务都有指定的使用限额。免费套餐包含三种不同类型的产品：12个月免费套餐、永久免费产品和短期试用。

### 步骤1：创建或登录现有AWS账户

创建AWS账户（如果您还没有账户）并登录。可以在AWS平台上创建免费试用账户，网址为 https://aws.amazon.com/free。

首先，单击Create a Free Account按钮。接下来，提供登录详细信息，例如电子邮件ID、密码和AWS账户名称。然后，选择账户类型（专业版或个人版）并提供联系信息。之后，提供PAN和付款详细信息。最后，在身份验证页面上完成验证流程。

几分钟后，账户将被激活并可以使用。根据您的要求选择一个计划。

### 步骤2：创建IAM用户并提供所需权限

登录AWS管理控制台后，打开IAM控制台 - https://console.aws.amazon.com/iam/。IAM代表身份和访问管理。接下来，在导航窗格中单击Users并选择Add users。然后，为该用户提供用户名并选择访问类型。之后，从附加的现有策略中选择现有策略，或为该用户创建新策略。在此场景中，IAM用户被授予管理员访问权限。标签是可选的。最后，检查并完成流程。不要忘记保存用户详细信息，如Access key ID、Secret access key和用户名。在此示例中，将使用IAM用户执行所有任务。单击Create user按钮并完成流程。




下图显示 IAM 用户已创建：

## 添加用户

![](img/cc4299656808e62a294f1843a1e18e72_354_0.png)

图 13.1: AWS IAM 用户

秘密访问密钥仅在创建时可用，因此您需要下载并保存它。如果丢失，则必须创建另一个。

不建议为 AWS 账户根用户创建访问密钥，除非必要。相反，应创建一个或多个具有所需权限的 IAM 用户来执行任务。

## 步骤 3：在本地机器上安装和配置 AWS CLI

AWS 命令行界面 (CLI) 是一款允许管理多个 AWS 服务的工具。它是一个开源工具，可让您通过命令与 AWS 服务交互。首先，下载并安装它，然后使用 AWS 凭证对其进行配置。要开始使用 AWS CLI，请访问此链接 https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html。

对于 Linux，使用 curl 命令下载安装文件，其中 -o 选项指定下载包写入的文件名：

```
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
```

按以下方式解压缩安装程序：

```
unzip awscliv2.zip
```

安装命令使用从解压的 aws 目录中获取的文件名 install：

```
sudo ./aws/install
```

通过检查 AWS CLI 版本来验证安装，使用以下命令：

```
aws --version
```

如果找不到 aws 命令，请重启终端。

接下来，使用 AWS IAM 凭证配置 AWS CLI，如下图所示：

```
aws configure
AWS Access Key ID [None]: AKI
AWS Secret Access Key [None]: CPDHawC5
Default region name [None]: us-west-2
Default output format [None]:
```

图 13.2: AWS CLI 配置

## AWS CodeCommit

在此示例中，使用 Git 仓库，即 AWS CodeCommit；但是，也可以使用其他远程 Git 仓库，如 GitHub。AWS CodeCommit 是托管在 AWS 上的私有 Git 仓库。它允许您创建多个 Git 仓库，并支持一组标准的 Git 命令，例如 push、pull、clone 和 log。AWS CodeCommit 可以作为远程仓库添加到本地 Git 仓库中。它允许协作并提供安全性；但是，通常不应在其中存储任何个人或敏感数据。好处是，AWS CodeCommit 对新用户和现有用户均可免费使用，最高可达一定限额。即使在免费套餐使用期满 12 个月后，它也不会过期。前 5 名活跃用户可免费使用，其中包括每个账户 1,000 个仓库、每月 50 GB 存储空间和每月 10,000 次 Git 请求。

从服务中进入 CodeCommit：

| 服务 | 所有服务 | 开发者工具 | CodeCommit |
|---|---|---|---|

在 CodeCommit 中创建新仓库，然后提供仓库名称；描述为可选。仓库名称包含在该仓库的 URL 中。

创建仓库后，需要提供特定权限；然后，创建 Git 凭证以便从本地机器访问 CodeCommit 仓库。进入 IAM 控制台，从导航窗格中选择 Users，然后选择要配置 CodeCommit 的用户。接着，从策略列表中附加 AWSCodeCommitPowerUser 策略并完成流程。在此示例中，IAM 用户具有管理员权限，因此无需将上述策略附加到 IAM 用户。

选择相同的 IAM 用户，定位 AWS CodeCommit 的 HTTPS Git 凭证。接着，选择该用户并单击 Generate credentials 按钮。它将填充 Git 凭证，即用户名和密码。可以查看并下载密码，保存以备将来使用。此后无法恢复该密码；但是，可以重新生成。

![](img/cc4299656808e62a294f1843a1e18e72_356_0.png)

图 13.3: CodeCommit–Git 凭证

创建 CodeCommit 仓库后，将其克隆到本地机器。将项目代码文件复制到本地机器上的目录中。使用 git init 命令重新初始化 Git 仓库。最后，从本地机器将更改提交并推送到 CodeCommit 仓库。

让我们考虑贷款预测的场景，问题陈述是预测客户的贷款是否会被批准。请随意实现超参数调整并调整模型。

首先，创建 ML 代码的可安装包，然后使用 FastAPI 构建 Web 应用；接着，创建测试和依赖文件。之后，创建 Dockerfile 和 docker-compose.yml 文件。最后，创建用于 AWS 部署的配置文件 buildspec.yml。

> 注意：对于代码文件，请参考前面的章节。您应该为当前场景创建 buildspec.yaml 文件并更新 tox.ini 文件。您需要更新 src\tests\test_predict.py、src\prediction_model\predict.py 和 start.sh 以用于持续训练。

您可以在 https://github.com/suhas-ds/AWS-CICD 访问代码仓库。

以下目录结构显示了 CI/CD 管道的代码文件：

```
.
|-- src
    |-- prediction_model
        |-- config
            |-- __init__.py
            |-- config.py
        |-- datasets
            |-- __init__.py
            |-- test.csv
            |-- train.csv
        |-- processing
            |-- __init__.py
            |-- data_management.py
            |-- preprocessors.py
        |-- trained_models
            |-- __init__.py
            |-- classification_v1.pkl
        |-- VERSION
        |-- __init__.py
        |-- pipeline.py
        |-- predict.py
        |-- train_pipeline.py
|-- tests
    |-- pytest.ini
    |-- test_predict.py
|-- MANIFEST.in
|-- README.md
|-- requirements.txt
|-- setup.py
|-- tox.ini
|-- .gitignore
|-- Dockerfile
```

```
|__ README.md
|__ buildspec.yaml
|__ docker-compose.yml
|__ main.py
|-- pytest.ini
|-- requirements.txt
|-- runtime.txt
|-- start.sh
|-- test.py
└── tox.ini
```

## tox.ini

tox 是一款免费开源工具，用于测试 Python 包或应用程序。它创建虚拟环境并在其中安装所需的依赖项；最后，它运行该 Python 包的测试。您需要按照以下代码所示更新 tox.ini 文件。

```
1. [tox]
2. envlist = my_env
3. skipsdist=True
4.
5. [testenv]
6. install_command = pip install {opts} {packages}
7. deps =
8.   -r requirements.txt
9.
10. setenv =
11.   PYTHONPATH=src/
12.
13. commands=
14.   pip install requests
15.   pytest -v src/tests/ --junitxml=pytest_reports/Prediction_test_report.xml
16.   pytest -v test.py --junitxml=pytest_reports/API_test_report.xml
```

**skipsdist=True** 标志表示不执行打包操作。这意味着在执行任何测试之前，包不会安装到虚拟环境中。将 **PYTHONPATH** 设置为存放 Python 包文件的 **src/** 目录。在 commands 部分，将执行 pytest 命令，测试结果将导出为 **pytest_reports** 目录中的 `.xml` 文件。

### .\src\prediction_model\predict.py

在此，向 _predict.py_ 文件添加 **train_accuracy** 函数，该函数将返回准确率得分。

```
1. def train_accuracy(input_data):
2.     """ Checking accuracy score of training data """
3.
4.     # Read Data
5.     data = pd.DataFrame(input_data)
6.     y_train = np.where(data['Loan_Status']=='Y', 1, 0).tolist()
7.
8.     # Prediction
9.     prediction = _loan_pipe.predict(data[config.FEATURES])
10.    y_pred = prediction.tolist()
11.    score = accuracy_score(y_train,y_pred)*100
12.    return score
```

### .\src\tests\test_predict.py

现在，向 _test_predict.py_ 文件添加 **test_score** 函数，用于测试训练准确率得分是否在 70 到 95 之间。您可以更改此范围。

```
1. from prediction_model.predict import train_accuracy
2.
3. def test_score():
4.     """ This function will check the accuracy score of training data
...
5.     data = load_dataset(file_name=config.TRAIN_FILE)
6.     score = train_accuracy(data)
7.     assert 70 <= score <= 95
```

从本地终端成功推送后，代码文件将显示在云端源代码仓库中。




## 持续训练

通过 CI/CD 流水线，您可以添加 **持续训练（CT）** 阶段。因此，当运行 CI/CD 流水线时，它还将根据配置设置在最新可用数据上训练模型。

_start.sh_

要在最新数据上训练模型，需要将以下命令添加到 _start.sh_ 文件中：

```
python app/src/prediction_model/train_pipeline.py
```

这将运行 train_pipeline.py 文件并生成训练模型的最新 pickle 文件。该文件将先安装包，然后训练模型，最后运行 FastAPI 应用。

```
1. #!/bin/bash
2.
3. pip install app/src/
4. python app/src/prediction_model/train_pipeline.py
5. python app/main.py
```

## Amazon Elastic Container Registry (ECR)

Amazon Elastic Container Registry (ECR) 是由 AWS 托管的容器镜像仓库服务。它可存储、管理并为私有容器镜像提供安全性。如果需要通过代码或其他服务（例如 **CodeBuild**）来访问这些容器镜像，则需要向指定的服务角色提供容器镜像仓库访问权限。

从服务中进入 Elastic Container Registry：

**服务 | 所有服务 | 容器 | Elastic Container Registry**

创建名为 `mlapp-cicd` 的仓库。默认情况下，仓库的可见性为私有，这意味着访问将由 IAM 管理，并且预定义权限将授予仓库策略。仓库名称应当简洁且有意义，即应基于仓库的内容。名称必须以字母开头，且只能包含小写字母、数字、连字符、下划线、句点和正斜杠。

然后，进入仓库并点击右上角的 **查看推送命令** 按钮。它将显示使用 AWS CLI 从本地机器推送 Docker 容器镜像时需要遵循的推送命令和说明。首先，需要使用弹出窗口中给出的命令登录到 AWS ECR。接下来，在本地机器上使用 docker build 命令构建 Docker 镜像。如果 Docker 镜像已构建，则可以跳过 Docker 构建步骤。然后，使用弹出窗口中给出的命令为 Docker 镜像打标签并将镜像推送到 AWS ECR 仓库。

以下图显示了 `mlapp-cicd` 仓库的推送命令：

![](img/cc4299656808e62a294f1843a1e18e72_361_0.png)

图 13.4：Amazon ECR – 推送命令

> 注：建议在本地机器上安装并配置最新版本的 AWS CLI 和 Docker。

## Docker Hub 速率限制

从 2020 年 11 月 20 日开始，匿名用户和免费用户每 6 小时分别被限制为 100 和 200 次容器镜像拉取请求。超过指定限制后，将抛出包含 ERROR: toomanyrequests: Too Many Requests. 或 You have reached your pull rate limit. 的错误。您可以通过身份验证和升级来提高限制：https://www.docker.com/increase-rate-limits。要提高拉取速率限制，可以将帐户升级为 Docker Pro 或 Team 订阅。Docker Pro 和 Docker Team 帐户每 24 小时可从 Docker Hub 拉取 5,000 次。

为避免此错误，请针对当前场景在 AWS ECR 上创建新仓库。接下来，将 Docker Hub 中的基础 Python 3.7 镜像拉取到本地机器或虚拟机中。然后，将该基础 Python 3.7 镜像推送到新创建的 AWS ECR 仓库。在当前场景中，基础镜像在单独的仓库中维护，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_362_0.png)

图 13.5：Amazon ECR–仓库

在 Dockerfile 中使用此镜像路径，以便在针对 Dockerfile 运行 docker build 命令时，它将从 AWS 拉取基础 Python 3.7 镜像。为此，需要按如下方式更新 Dockerfile：

```
1. # Pull base Python:3.7 image from AWS ECR repository
2. ARG REPO=692601447418.dkr.ecr.us-west-2.amazonaws.com
3.
4. FROM ${REPO}/python:3.7
5.
6. COPY ./start.sh /start.sh
7.
8. RUN chmod +x /start.sh
9.
10. ENV PYTHONPATH "${PYTHONPATH}:app/src/"
11.
```

```
12. COPY . /app

13.

14. RUN chmod +x /app

15.

16. # Exposing the port that uvicorn will run the app on

17. ENV PORT=8000

18. EXPOSE 8000

19.

20. RUN pip install --upgrade pip

21.

22. RUN pip install --no-cache-dir --upgrade -r app/requirements.txt

23.

24. CMD ["./start.sh"]
```

在当前场景中，python:3.7-slim-buster 镜像被构建并打标签为 3.7，然后推送到 AWS ECR 以实现重用。这样，每次都会从 AWS ECR 而不是 Docker Hub 拉取 python:3.7-slim-buster 镜像，以避免任何速率限制错误。

## AWS CodeBuild

CodeBuild 是一种由 AWS 基础设施支持的完全托管型持续集成（CI）服务，可让开发者快速自动化构建、测试和部署容器或软件包。它采用按需或按使用量付费的模式，即根据用户使用的计算资源按分钟计费。

CodeBuild 配置文件类型为 YAML。该文件包含一系列阶段和命令，以执行开发者指定的构建。

*buildspec.yaml*

在这种情况下，buildspec.yaml 文件在 install 阶段中先安装 tox 包。接下来，它将使用 tox 运行测试并在 pre_build 阶段中登录 AWS ECR。然后，buildspec.yaml 文件在 build 阶段构建带 latest 标签的 Docker 容器镜像，并在 post_build 阶段将镜像推送到 AWS ECR 仓库。最后，指定 pytest 报告的详细信息，例如文件、基目录和文件格式。此外，提供要作为项目存储到 S3 存储桶中的文件名。

```
1. version: 0.2
2.
3. phases:
4. install:
5. runtime-versions:
6. python: 3.7
7. commands:
8. - pip install tox
9. pre_build:
10. commands:
11. - echo Running test...
12. - tox
13. - echo Logging into Amazon ECR...
14. - aws --version
15. - aws ecr get-login-password --region us-west-2 | docker login --username AWS --password-stdin 692601447418.dkr.ecr.us-west-2.amazonaws.com
16. - REPOSITORY_URI=692601447418.dkr.ecr.us-west-2.amazonaws.com/mlapp-cicd
17. - COMMIT_HASH=$(echo $CODEBUILD_RESOLVED_SOURCE_VERSION | cut -c 1-7)
18. - IMAGE_TAG=${COMMIT_HASH:=latest}
19. build:
20. commands:
21. - echo Build started on `date`
22. - echo Building the Docker image...
23. - docker build -t $REPOSITORY_URI:latest .
24. - docker tag $REPOSITORY_URI:latest $REPOSITORY_URI:$IMAGE_TAG
25. post_build:
26. commands:
27. - echo Build completed on `date`
28. - docker push $REPOSITORY_URI:latest
29. - docker push $REPOSITORY_URI:$IMAGE_TAG
30. - echo Writing container image definitions file...
31. - printf '[{"name":"mlapp-cicd","imageUri":"%s"}]' $REPOSITORY_URI:$IMAGE_TAG > imagedefinitions.json
```

```
33. reports:
34.   pytest_reports:
35.     files:
36.       - Prediction_test_report.xml
37.       - API_test_report.xml
38.     base-directory: pytest_reports/
39.     file-format: JUNITXML
40. artifacts:
41.     files: imagedefinitions.json
```

在前面的文件中，主要使用了三种受支持的构建器镜像。

可以看到，python:3.7 是用于使用 tox 测试代码的公开可用镜像。如果需要从 Docker Hub 使用任何镜像，则只需在单引号中提供镜像名称即可。但是，如果镜像来自其他注册表，则需要在单引号中指定完整的注册表路径。构建阶段的 args 字段接受参数列表，并将它们传递给由 name 字段引用的镜像。

要创建构建，请使用 CodeBuild。在开发者工具中搜索并选择 CodeBuild，然后在构建部分中选择构建项目。点击“创建构建项目”按钮来创建新项目。首先，在“项目配置”下，提供项目名称。

在此情况下，提供了项目名称 mlapp-cicd，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_366_0.png)

图 13.6：CodeBuild–项目配置

接下来，在源部分中，从下拉列表中选择源提供商，并选择后续详细信息，例如仓库和分支。源提供商包含用作构建项目输入源代码的详细信息和代码文件。在当前场景中，选择 AWS CodeCommit 作为源提供商，如下图所示。但是，也可以选择其他源提供商而非 AWS CodeCommit，例如 BitBucket、GitHub 和 S3。





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




保持任务执行角色为默认值，即 ecsTaskExecutionRole。在“任务大小”部分，根据应用程序要求或用例，为任务分配所需的内存和 CPU。对于当前场景，选择了任务内存 (GB) 为 1GB，任务 CPU (vCPU) 为 0.25 vCPU，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_374_0.png)

图 13.15: 任务定义–任务大小

最后，添加容器详细信息，例如容器名称、从 AWS ECR 获取的镜像 URI 以及容器的内存限制 (以 MiB 为单位)。硬限制和软限制分别对应任务定义中的 memory 和 memoryReservation 参数。端口映射参数非常重要。在这里，您需要提供容器用于运行应用程序并在 Dockerfile 中公开的端口。在当前场景中，容器端口为 8000。您可以保留其余配置不变并添加容器。

最后，单击“Create”以完成任务定义的步骤 2。

## 使用任务定义运行任务

可以使用先前创建的任务定义独立运行任务。

以下图显示了任务定义可用的各种选项。现在，要运行任务，请选择第一个选项，即 Run Task。

![](img/cc4299656808e62a294f1843a1e18e72_374_1.png)

图 13.16: 运行独立任务

接下来，选择启动类型。在当前场景中，选择了 FARGATE。从 Cluster 下拉列表中选择 mlapp-cluster。

### Amazon VPC 和子网

Amazon 虚拟私有云 (Amazon VPC) 使您能够将 AWS 资源启动到您定义的虚拟网络中。这些虚拟网络与数据中心中使用的传统网络类似。虚拟网络的优势在于它附带了由 AWS 管理的可扩展基础设施。每个 VPC 网络由一个或多个称为子网的 IP 地址范围组成。

接下来，在 VPC 和安全组下，选择集群 VPC 并选择子网。在当前场景中，选择 2a 和 2b；但是，剩余的 2c 和 2d 也可以选择。确保 Auto-assign public IP 已启用。这将允许您自动分配可用的公有 IP，以便从任何位置访问 ML 应用程序。

然后，编辑默认安全组，安全组窗口将显示。在这里，创建一个将在后续阶段使用的新安全组。从“Assigned security groups”中选择“Create new security group”，并为安全组提供名称为 mlapp-sg，其中 sg 代表安全组。之后，允许两个端口，即端口 80 和端口 8000，用于容器化应用程序与外部世界的通信。

之后，添加 HTTP 端口 80 和自定义 TCP 端口 8000，容器化应用程序正在该端口上运行。对于两个端口，在源选项中选择 Anywhere。

最后，在右下角单击“Run Task”按钮。任务启动并运行需要一些时间。任务的状态将在“Tasks”选项卡中显示为 RUNNING，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_375_0.png)

图 13.17: 运行独立任务 - 任务已创建

任务的公有 IP 为 54.191.99.95。这意味着可以从互联网上的任何位置使用此公有 IP 访问 ML 应用程序。

独立运行任务的问题是，如果任务因任何原因失败或停止，应用程序也会停止；这会导致应用程序对外部世界不可访问。为解决此问题，可以使用 ECS 服务。不要忘记停止正在运行的任务。使用 ECS 服务，可以创建多个任务。

## 负载均衡

在并行计算中，负载均衡是将应用程序流量分布到不同可用计算资源或资源上的过程，以使整体请求处理更高效。该技术的主要目标是避免最终用户或客户出现任何停机时间。

以下图示了应用程序负载均衡器 (ALB) 的高级架构：

![](img/cc4299656808e62a294f1843a1e18e72_376_0.png)

图 13.18: 应用程序负载均衡器 (ALB)

应用程序负载均衡器只能在创建服务时添加到服务中。接下来，进入负载均衡部分并创建目标组，目标组负责动态添加创建任务时生成的 IP 地址。

从服务转到负载均衡器：

服务 | 所有服务 | 开发者工具 | 负载均衡

以下图显示了负载均衡的组件：

![](img/cc4299656808e62a294f1843a1e18e72_377_0.png)

图 13.19: AWS-负载均衡

让我们了解负载均衡两个组件的角色和配置。

### 目标组

使用负载均衡器，单个 DNS 名称即可访问容器化应用程序。负载均衡器将在端口 **80** 上接收用户请求，并通过服务将其路由到具有动态 IP 的任务。目标组将确保负载均衡器与通过服务的具有动态 IP 的任务之间的连接。

转到目标组，并通过单击 **创建目标组** 按钮创建新目标组。

创建目标是一个三步过程：

- 指定组详细信息
- 注册目标
- 审查要包含在组中的 IP 目标

### 步骤 1：指定组详细信息

创建目标组后无法更改配置设置。在此步骤中，目标类型是 **IP 地址**；其功能在以下图中列出：

![](img/cc4299656808e62a294f1843a1e18e72_377_1.png)

图 13.20: 目标组 - 指定组详细信息

接下来，将 **目标组名称** 提供为 `mlapp-tg`。目标组名称不应以连字符 (-) 开头或结尾。然后，提供端口 `8000`，HTTP 类型 **协议** 为，因为应用程序公开到端口 `8000`。保留其余选择不变。此配置如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_378_0.png)

图 13.21: 目标组 - 基本配置

在运行状况检查部分下，默认情况下，目标组将检查根路径或索引路径 (`/`)，或者如果您愿意，可以指定自定义路径。目标组将定期向应用程序的此端点发送请求，以检查其是否运行正常。

### 步骤 2：注册目标

在此步骤中，可以从所选网络手动指定 IP 地址和端口。默认情况下，将选择 VPC 网络。删除预选的 IP，因为此部分是可选的。以后可以配置此部分。以下图显示此步骤：

EC2 > 目标组 > 创建目标组

### 注册目标

步骤 2，共 2 步

这是创建目标组的一个可选步骤。但是，为确保负载均衡器将流量路由到此目标组，您必须注册您的目标。

### IP 地址

### 步骤 1：选择网络

您可以从为目标组选择的 VPC 或 VPC 外部添加 IP 地址。请注意，您可以返回此步骤并选择另一个网络，从多个网络源组合目标。

**网络**

vpc-0794b5f3d52feed4
IPv4: 172.31.0.0/16

### 步骤 2：指定 IP 地址并定义端口

您可以手动输入所选网络中的 IP 地址。

输入来自 VPC 子网的 IPv4 地址。

**添加 IPv4 地址**

图 13.22: 目标组 - 注册目标

之后，指定路由到此目标的端口。在当前情况下，指定了应用程序的端口 **8000**，如下图所示：

### 端口

路由到此目标的端口。

8000

1-65535 (用逗号分隔多个端口)

**将其包含在下方的待处理项中**

### 审查目标

### 步骤 3：审查要包含在组中的 IP 目标

确认要包含在目标组中的 IP 目标。通过在本页面上重复步骤 1 和 2 添加更多 IP 目标。您也可以在创建目标组后注册其他目标。

### 目标 (0)

全部

按属性或值筛选资源

| 移除 IPv4 地址 | 运行状态 | IP 地址 | 端口 | 区域 |
| :--- | :--- | :--- | :--- | :--- |

尚未包含任何 IP 地址
指定上述 IP 地址并将其添加到列表。

图 13.23: 目标组 - 审查目标和路由到目标的端口





## 步骤 3：检查要包含在组中的 IP 目标

此时，如果要添加其他 IP 目标，可以重复步骤 1 和步骤 2。但是，您在步骤 2 中未指定任何 IP 地址，因此请直接点击底部的“创建目标组”按钮。这将带您返回目标组的主页面并显示成功消息，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_380_0.png)

图 13.24：目标组–mlapp-tg

亚马逊资源名称 (ARN) 是 AWS 资源的唯一标识符。AWS ARN 格式可以是以下任一格式：

- arn:partition:service:region:account-id:resource-id
- arn:partition:service:region:account-id:resource-type/resource-id
- arn:partition:service:region:account-id:resource-type:resource-id

分区是一组 AWS 区域，每个账户的范围有限：一个分区。

## 安全组

安全组是一组防火墙规则，用于控制流向负载均衡器的流量。它尚未创建，因此请继续创建一个新安全组。执行以下步骤：

服务 | 所有服务 | EC2 | 网络与安全 | 安全组

首先，为安全组指定基本信息，例如名称和描述，如下图所示。安全组名称为 mlapp-lb-sg，其中 lb 代表负载均衡器，sg 代表安全组。

### 创建安全组

安全组充当实例的虚拟防火墙，用于控制入站和出站流量。要创建新安全组，请完成以下字段。

### 基本信息

图 13.25：负载均衡器的安全组—创建安全组

接下来，为安全组配置入站规则。点击“添加规则”按钮。负载均衡器应能够从任何位置访问端口 80，因此请在“端口范围”下指定端口 80，并将“源类型”选择为“任何位置”，如下图所示。可通过“添加规则”按钮添加更多规则。

### 入站规则

图 13.26：负载均衡器的安全组—入站规则

然后，在页面右下角点击“创建安全组”按钮并完成过程。下图显示了创建后的安全组详细信息：

![](img/cc4299656808e62a294f1843a1e18e72_382_0.png)

图 13.27：负载均衡器的安全组–mlapp-lb-sg

此安全组 mlapp-lb-sg 将用于负载均衡器。

## 应用程序负载均衡器 (ALB)

应用程序负载均衡器 (ALB) 接收传入请求并将其路由到已注册目标，例如 EC2 实例。它还会检查已注册目标的运行状况（默认情况下，根路径设置为 '/'；但是，可以将其更改为应用程序的其他路径）。应用程序负载均衡器 (ALB) 面向客户端。它仅将流量路由到运行正常的目标。它可以轻松与 Amazon Elastic Container Service (Amazon ECS)、Amazon Elastic Container Service for Kubernetes (Amazon EKS)、AWS Fargate 和 AWS Lambda 集成。

创建安全组和目标组后，创建负载均衡器。再次进入负载均衡部分并选择负载均衡器。

服务 | 所有服务 | EC2 | 负载均衡 | 负载均衡器

然后，点击“创建负载均衡器”按钮。下图显示了负载均衡器的主页面：

![](img/cc4299656808e62a294f1843a1e18e72_383_0.png)

图 13.28：应用程序负载均衡器—创建负载均衡器

单击“创建负载均衡器”按钮后，将显示三个带有简要描述和架构的选项供选择，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_383_1.png)

图 13.29：应用程序负载均衡器—选择负载均衡器类型

应用程序负载均衡器会根据请求将传入请求分发到目标（例如容器、微服务和 EC2 实例）。在将传入请求传递给目标之前，它会评估是否已配置侦听器规则。

在当前场景中，选择第一种类型，即应用程序负载均衡器，方法是点击“创建”按钮。

现在，配置负载均衡器。首先，为负载均衡器指定名称 mlapp-lb，其中 lb 代表负载均衡器。接下来，选择方案为“面向互联网的”。面向互联网的方案与内部方案的主要区别在于互联网。面向互联网的负载均衡器将来自客户端通过互联网的请求路由到指定目标。另一方面，内部负载均衡器仅将来自拥有私有 IP 的客户端的请求路由到指定目标。选择 IP 地址类型为 IPv4，该类型由指定子网使用。下图显示了应用程序负载均衡器的基本配置：

EC2 > 负载均衡器 > 创建应用程序负载均衡器

### 创建应用程序负载均衡器

应用程序负载均衡器会根据请求属性将传入的 HTTP 和 HTTPS 流量分发到多个目标（例如 Amazon EC2 实例、微服务和容器）。当负载均衡器接收到连接请求时，它会按优先级顺序评估侦听器规则以确定应用哪条规则，如果适用，则为规则操作从目标组中选择一个目标。

### 应用程序负载均衡器的工作原理

### 基本配置

负载均衡器名称
名称在您的 AWS 账户中必须唯一，且创建负载均衡器后无法更改。
mlapp-lb
最多允许 32 个字母数字字符（包括连字符），但名称不能以连字符开头或结尾。

创建负载均衡器后，方案无法更改。

| 方案 | 信息 |
|--------|------|
| 面向互联网的 | 面向互联网的负载均衡器将来自客户端通过互联网的请求路由到目标。需要公有子网。了解更多 |
| 内部 | 内部负载均衡器使用私有 IP 地址将来自客户端的请求路由到目标。 |

图 13.30：应用程序负载均衡器—基本配置

然后，配置网络映射。网络映射使负载均衡器能够将传入请求路由到特定子网和 IP 地址。对于映射，请选择至少两个可用区和每个区的一个子网，负载均衡器可以将流量路由到这些子网。默认情况下，将显示可用区供选择。负载均衡器仅将请求路由到这些可用区中的目标。从下拉菜单中选择默认 VPC 和两个子网 (2a 和 2b)，如下图所示：

### 网络映射信息

负载均衡器将流量路由到选定子网中的目标，并遵循您的 IP 地址设置。

### VPC 信息

为目标选择虚拟私有云 (VPC)。仅启用了互联网网关的 VPC 才可供选择。创建负载均衡器后，所选 VPC 无法更改。要确认目标的 VPC，请查看您的目标组。

```
vpc-0794b53ffdc52faed4
IPv4: 172.31.0.0/16
```

### 映射信息

至少选择两个可用区和每个区的一个子网。负载均衡器仅将流量路由到这些可用区中的目标。不受负载均衡器或 VPC 支持的可用区不可供选择。

- us-west-2a
  - 子网：subnet-08c67a67021afa335
  - IPv4 设置：由 AWS 分配
- us-west-2b

图 13.31：应用程序负载均衡器—网络映射

之后，移除默认安全组，并从上一部分创建的下拉菜单中选择安全组。也可以通过“创建新安全组”链接创建安全组。这将带您进入仅显示安全组的主页面，如上一部分所示。下图显示了为负载均衡器选择的安全组 mlapp-lb-sg：

### 安全组信息

安全组是一组防火墙规则，用于控制流向负载均衡器的流量。

- 最多选择 5 个安全组
- mlapp-lb-sg sg-0615e0e759807c03f
- VPC：vpc-0794b53ffdc52faed4

图 13.32：应用程序负载均衡器—安全组





最后，选择您之前创建的目标组，即带有端口 80 的 mlapp-tg，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_386_0.png)

图 13.33：应用负载均衡器–监听器和路由

向下滚动并点击右下角的“创建负载均衡器”按钮。下图显示了负载均衡器的主页面，显示新创建的负载均衡器已创建：

![](img/cc4299656808e62a294f1843a1e18e72_386_1.png)

图 13.34：应用负载均衡器–mlapp-lb

## 服务

AWS ECS 服务允许您在 AWS ECS 集群中同时运行指定数量的任务定义实例。如果任务因任何原因失败或停止，ECS 服务将启动另一个任务定义实例，以确保所需数量的任务正在运行。这样做的好处是，即使某个任务失败，应用程序也将保持运行。

转到 mlapp-cluster 页面的“服务”选项卡，然后点击“创建”按钮以创建新服务。

服务创建包含四个步骤，如下图所示。每个步骤的配置和设置将在下图中讨论：

![](img/cc4299656808e62a294f1843a1e18e72_387_0.png)

图 13.35：ECS 服务创建步骤

### 步骤 1：配置服务

在此步骤中，选择启动类型。由于 ECS 集群已配置为 FARGATE，请将启动类型选择为 FARGATE。操作系统系列将为 Linux。

如下图所示，从下拉菜单中将**任务定义**选择为**mlapp**，将**集群**选择为**mlapp-cluster**：

![](img/cc4299656808e62a294f1843a1e18e72_388_0.png)

图 13.36：ECS 服务–配置服务

接下来，在同一步骤中，为服务命名；在此场景中，名称为**mlapp-cicd**，并将**任务数量**设置为 2，这指的是将受服务影响的所需任务数量。不过，此计数可以根据要求进行更新（1 及以上）。其余选项可保持不变。下图是步骤 1 的延续：

![](img/cc4299656808e62a294f1843a1e18e72_388_1.png)

图 13.37：ECS 服务–配置服务

### 步骤 2：配置网络

在此步骤中，首先从下拉菜单中选择集群 VPC 及其关联的子网。再次选择两个子网，即 2a 和 2b，类似于独立任务但带有附加配置，如下图所示。请确保“自动分配公有 IP”为“已启用”。这将允许您分配可用的公有 IP 以从任何位置访问 ML 应用。

#### 配置网络

#### VPC 和安全组

当任务定义使用 awsvpc 网络模式时，可以配置 VPC 和安全组。

![](img/cc4299656808e62a294f1843a1e18e72_389_0.png)

图 13.38：ECS 服务—配置网络

接下来，点击安全组中的“编辑”按钮。这将打开一个窗口以配置安全组。在此处，选择的是您为运行独立任务而创建的现有安全组。它为端口 80 和 8000 定义了入站规则，如下图所示。保存安全组的此配置。

![](img/cc4299656808e62a294f1843a1e18e72_390_0.png)

图 13.39：ECS 服务—配置安全组

然后，选择应用负载均衡器作为负载均衡器类型。这使其能够跨服务中运行的任务进行分发，而无需让最终用户知晓。应用负载均衡器类型的负载均衡器允许容器使用动态主机端口映射，即每个容器实例允许运行多个任务。多个服务可以在单个负载均衡器上使用相同的监听器端口，并基于规则的路径进行路由。

#### 负载均衡

弹性负载均衡负载均衡器将传入流量分发到服务中运行的任务。选择现有负载均衡器，或在 Amazon EC2 控制台中创建一个新负载均衡器。

![](img/cc4299656808e62a294f1843a1e18e72_390_1.png)

图 13.40：ECS 服务 – 负载均衡器类型

随后，如下图所示，从下拉菜单中选择**负载均衡器名称**。负载均衡器将监听 HTTP 端口 **80**。从下拉菜单中将**目标组名称**选择为**mlapp-tg**，即您在负载均衡器部分中创建和配置的目标组。

服务 IAM 角色
使用 awsvpc 网络模式的任务定义使用 AWSServiceRoleForECS 服务相关角色，该角色会为您自动创建。了解更多。

![](img/cc4299656808e62a294f1843a1e18e72_391_0.png)

图 13.41：ECS 服务–目标和端口

### 步骤 3：设置自动扩展（可选）

自动扩展是可选的。这将根据 CloudWatch 警报在指定范围内自动更新服务的所需计数。在当前场景中，使用默认值，即**不调整服务的所需计数**。点击**下一步**。

### 步骤 4：审核

在此步骤中，查看服务的配置。在此处，您可以返回上一步以更新配置。如果看起来没问题，请点击**创建服务**按钮来创建服务，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_391_1.png)

图 13.42：ECS 服务–审核

步骤 4 完成后，服务将被创建；不过，创建该服务所需数量的任务需要几分钟时间。任务创建进度可以在“事件和日志”选项卡下查看。几分钟后，任务状态将变为 RUNNING，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_392_0.png)

图 13.43：ECS 服务–mlapp-cicd

现在，点击第一个任务，复制其公有 IP，并在浏览器中输入该公有 IP，后跟端口 8000。它应该显示一条消息，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_392_1.png)

```
{"message":"Loan Prediction App"}
```

图 13.44：ECS 服务–使用第一个任务的公有 IP 访问 ML 应用

返回并点击第二个任务，复制其公有 IP，并在浏览器中输入该公有 IP 后跟端口 8000。它应该显示一条消息，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_392_2.png)

```
{"message":"Loan Prediction App"}
```

图 13.45：ECS 服务–使用第二个任务的公有 IP 访问 ML 应用

服务相对于独立任务的好处是，如果任务因任何原因失败或关闭，服务将用新任务替换它，以维持所需数量的任务正在运行。没有负载均衡器的服务的问题在于，当它替换任务或创建新任务时，公有 IP 会发生更改，这使得跟踪该服务的最新或运行中的任务变得有些困难。

这些公有 IP 可以通过互联网被外部世界访问。但是，您可以通过更新服务 mlapp-sg 的安全组中的入站规则来限制对任务公有 IP 的访问。转到 mlapp-sg 安全组，删除入站规则（如果存在），添加一条新规则并指定容器端口，即在端口范围中指定 8000，并在源中选择负载均衡器的安全组，即 mlapp-lb-sg，而不是 0.0.0.0/0 或任何位置。最后，您可以保存规则。这将限制外部世界通过互联网直接访问任务的公有 IP。

让我们使用应用负载均衡器来检查已部署的容器化应用。转到负载均衡器页面，复制其 DNS 名称，并在浏览器中运行（粘贴并回车）。它应该显示一条文本消息。这是应用程序的根页面。

然后，在 <ALB DNS 名称>/docs 中传递输入数据并检查预测输出，如下图所示。在此处，您不需要传递端口和 IP 地址，因为负载均衡器已配置端口和目标组，将处理任务的动态 IP。

![](img/cc4299656808e62a294f1843a1e18e72_393_0.png)

图 13.46：应用负载均衡器–ML 应用预测响应

> 注：负载均衡设置只能在服务创建时进行设置。

## 使用 CodePipeline 的 CI/CD 管道

AWS 提供了一组用于 CI/CD 管道的工具和服务。在上一节中，构建是使用 CodeBuild 手动触发的。为了实现手动流程的自动化，您必须构建带有自动触发器的 CI/CD 管道。





为了实现此目标，将使用 AWS CodePipeline。在创建 CI/CD 管道之前，请确保之前的服务和主题已在 AWS 云上学习并实现。AWS CodePipeline 将连接这些服务以创建自动化管道。如 CodeCommit、ALB、ECS FARGATE 集群等 AWS 服务需要创建并配置。请确保在适用的地方为服务提供必要的权限。在当前场景中，未使用任何外部服务（例如 GitHub）。但是，您可以将外部服务或第三方服务集成到此过程中。在这里，利用 AWS 服务部署应用程序。

当有任何更新推送到 CodeCommit 时，将触发 CI/CD 管道。CodeBuild 配置文件 buildspec.yaml 将首先运行测试。接下来，登录到 Amazon ECR，然后构建并推送 Docker 容器镜像到 Elastic Container Registry (ECR)。它还将写入容器镜像定义文件 imagedefinitions.json，其中会捕获仓库，后跟一个镜像标签。此容器镜像定义文件将作为构件存储在 Amazon S3 存储桶中。CodeBuild 将导出 pytest_reports/ 目录中的测试报告 (.xml)。这些测试结果可以在 CodeBuild 页面上查看。之后，在部署阶段，指定 ECS 集群详细信息。ECS 集群将从 Elastic Container Registry (ECR) 拉取最新的容器镜像。最后，容器化应用将部署到 ECS 集群中。日志将在 CloudWatch 中捕获。

当客户端或最终用户通过域名系统 (DNS) 名称访问此机器学习应用时，DNS 将把人类可读的名称翻译成机器可理解的数字 IP 地址。此请求将发送到应用程序负载均衡器 (ALB)。接下来，应用程序负载均衡器 (ALB) 将检查指定的监听器规则，例如端口号和 IP 地址。然后，它将传入请求发送到特定目标组，该目标组会将请求路由到位于 Elastic Container Service (ECS) FARGATE 集群中运行的任务。应用程序将处理请求，并将预测结果发送到客户端或最终用户。

以下图显示了将容器化应用部署到 Elastic Container Service (ECS) 的自动化 CI/CD 管道架构：

![](img/cc4299656808e62a294f1843a1e18e72_395_0.png)

图 13.47: 带有 ECS 参考架构的 CI/CD 管道

## AWS CodePipeline

管道是负责自动化部署或发布应用程序的工作流。CodePipeline 是 AWS 云中的完全托管持续交付 (CD) 服务。它能更快、更轻松地部署应用程序。它自动化了 CI/CD 过程中的不同阶段，例如构建、测试和部署。每个阶段包含一系列要执行的操作。AWS CodePipeline 可以轻松与 GitHub 等第三方服务集成。

以下图显示了创建 CI/CD 管道所使用的 CodePipeline 和 AWS 服务的流程。

![](img/cc4299656808e62a294f1843a1e18e72_396_0.png)

图 13.48: 使用 CodePipeline 的 CI/CD 管道

从“服务”中进入 CodePipeline。

服务 | 所有服务 | 开发者工具 | CodePipeline

让我们从创建管道开始。点击“创建管道”按钮。它包含 5 个步骤，即：

- 选择管道设置
- 添加源阶段
- 添加构建阶段
- 添加部署阶段
- 审查

### 步骤 1：选择管道设置

在此步骤中，您需要将管道名称指定为 mlapp-cicd。管道名称创建后无法更改。为 CodePipeline 选择新的服务角色。选中“允许 AWS CodePipeline 创建可与此新管道一起使用的服务角色”复选框。角色名称应自动填充。

![](img/cc4299656808e62a294f1843a1e18e72_397_0.png)

图 13.49: CodePipeline – 选择管道设置

### 步骤 2：添加源阶段

在此步骤中，您需要指定要拉取最新代码和更新的源的详细信息。将 AWS CodeCommit 选为源提供程序。接下来，将仓库名称选择为 loan_pred。然后，选择要拉取最新代码和更新的 main 分支。从更改检测选项中，选择 Amazon CloudWatch Events（推荐），如下图所示。这将在检测到源存储库分支中的更改时立即触发管道。

![](img/cc4299656808e62a294f1843a1e18e72_398_0.png)

图 13.50: CodePipeline-添加源阶段

### 步骤 3：添加构建阶段

首先，您需要将 AWS CodeBuild 选为构建提供程序。或者，也可以选择 Jenkins 作为构建提供程序。已选择美国西部（俄勒冈）区域。接下来，选择您在 CodeBuild 控制台中已创建的构建项目名称，或在 CodeBuild 控制台中创建构建项目。“创建项目”链接将重定向您到 CodeBuild 控制台。在构建类型部分，您需要选择单次构建，因为预计将触发一次构建。

![](img/cc4299656808e62a294f1843a1e18e72_399_0.png)

图 13.51: CodePipeline–添加构建阶段

### 步骤 4：添加部署阶段

在此步骤中，提供应用程序需要部署到的部署详细信息。此步骤取决于上一步。一旦构建完成，此步骤将把应用程序部署到 Elastic Container Service (ECS) 集群。

首先，将部署提供程序选为 Amazon ECS。区域是美国西部（俄勒冈）。然后，选择您在 Amazon ECS 控制台中已创建的集群名称，或在 Amazon ECS 控制台中创建集群并完成此步骤。之后，指定前一部分中创建的集群和服务名称。请参阅下图了解步骤 4 的配置。

![](img/cc4299656808e62a294f1843a1e18e72_400_0.png)

图 13.52: CodePipeline–添加部署阶段

### 步骤 5：审查

在此步骤中，查看前几步的配置。

如果配置正确，点击“创建管道”。

### 运行 CodePipeline

默认情况下，它将在创建后很快首次开始构建管道。当任何更新推送到源（即 AWS CodeCommit）时，管道执行将开始。您可以在 CodePipeline 主页上查看管道的进度和状态。进入管道 mlapp-cicd，您可以查看每个阶段的状态。它显示指向该服务的链接。例如，可以通过构建步骤下的链接查看构建进度。

转到构建部分的详细信息；您可以查看源和提交者详细信息。在以下图中，显示了谁启动了构建作业以及源版本。在第一行中，构建作业由 CodePipeline 启动，而在下一行中，构建作业由 IAM 用户手动启动。

| 构建运行 | 状态 | 构建编号 | 源版本 | 提交者 | 持续时间 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| mlapp-cicd:5c3b12c-aeda-45a7-a479-2ff667b0922b | 成功 | 11 | arn:aws:s3:::codepipeline-us-west-2-945654230632/mlapp-pc-cid/SourceArtl/VxxO13G | codepipeline/mlapp-cicd | 2 分钟 49 秒 |
| mlapp-cicd:cbe2999b-8a00-4f7d-bab5-8c8dd875afc8 | 成功 | 8 | refs/heads/main | suhas | 3 分钟 0 秒 |

图 13.53: CodePipeline–构建状态

以下图显示了 CodePipeline 主页。它显示管道的最新状态和最新源修订等详细信息。

![](img/cc4299656808e62a294f1843a1e18e72_401_0.png)

图 13.54: 运行 CodePipeline–成功

要访问应用，可以使用负载均衡器主页上显示的 DNS 名称。即使创建了新任务或任务的公共 IP 发生更改，DNS 名称也不会更改。以下图显示了使用 FastAPI UI 传递输入数据后的预测结果。

![](img/cc4299656808e62a294f1843a1e18e72_402_0.png)

图 13.55: 运行 CodePipeline–使用 ALB 的 DNS 进行 ML 应用预测

## 监控

监控是部署的重要组成部分。建议监控 ECS 集群和其他集成服务，以确保应用程序的高可用性。这使您可以检查 ECS 容器的整体运行状况。首先，制定需要监控的资源和服务的计划。接下来，决定检测到指定事件时应采取的操作。决定应通知谁事件或错误，在哪里监控指标和事件，等等。

ECS 提供集群级统计信息，例如：

- CPU 利用率——ECS 集群当前利用的 CPU 百分比
- 内存利用率——ECS 集群当前利用的内存百分比

Amazon ECS 指标数据会自动以 1 分钟为周期发送到 CloudWatch，并保留 2 周。**Amazon CloudWatch 容器洞察**允许您聚集和分析容器化应用程序的指标和日志。它有助于监控 CPU、内存、磁盘和网络等利用率指标。它还提供关于容器重启失败的诊断信息。

您可以创建一个 AWS Lambda 函数，在检测到指定事件时触发，并将警报发送到 Slack 频道。这样，团队成员和开发人员将收到有关警报的通知。

因此，您已学会如何使用 CodePipeline 创建一个简单的 CI/CD 管道，以将 ML 应用部署到 Amazon ECS Fargate 集群。但是，您可以根据业务和应用程序要求对其进行修改。本章中的参考图片来自经典 UI。如果您看到用于创建和管理服务的新 UI，可以切换回经典 UI，也可以继续使用新 UI。对于新 UI，底层流程和服务将保持不变，但您可能会看到选择



更改。或者，你可以使用 AWS CloudFormation 或 Terraform 来自动化创建基础设施或服务。

## 结论

在本章中，你使用 Fargate 创建了一个 Amazon Elastic Container Service (ECS) 集群来部署 ML 应用。首先，你创建了一个 AWS 账户，并创建了一个包含用于 Amazon Elastic Container Service (ECS) 部署的 buildspec.yml 文件的代码库。你在 CI/CD 管道中添加了持续训练阶段，并在 pytest 文件中添加了准确性测试用例。接下来，你将代码库和依赖项推送到 AWS CodeCommit。之后，你创建了 AWS Elastic Container Registry (ECR) 来存储和管理 Docker 容器镜像，并使用 AWS CodeBuild 通过 buildspec.yml 构建并将 Docker 镜像推送到 AWS Elastic Container Registry (ECR)。你创建了一个带有安全组和目标组的 Application Load Balancer (ALB) 来分发传入流量到 Fargate 任务，创建了带有安全组的 ECS 服务，并将 Application Load Balancer (ALB) 添加到其中。最后，你创建了 AWS CodePipeline 并集成了这些服务来自动化 ML 应用部署。

在下一章中，你将学习 ML 模型的漂移以及已部署模型的监控过程。

### 要点

- Amazon Elastic Container Service (ECS) 提供部署模型：EC2 和 Fargate。
- Application Load Balancer (ALB) 只能在服务创建时指定。
- Application Load Balancer (ALB) 检查其注册目标的健康状况（默认情况下，根路径设置为 '/'；但是，可以更改为应用程序的不同路径），并且仅将流量路由到健康目标。
- 建议在本地计算机上安装并配置最新版本的 AWS CLI 和 Docker。
- Amazon ECS 集群是任务或服务的逻辑分组。
- 创建一个或多个具有所需权限的 IAM 用户来运行服务，并避免直接使用 root 用户运行服务。

### 选择题

- 1. __________ 是面向容器的无服务器按需付费计算。
  - a) EC2
  - b) Fargate
  - c) CloudWatch
  - d) Amazon Lightsail

- 2. 用于负载平衡的目标组 __________
  - a) 接收来自 Application Load Balancer (ALB) 的请求
  - b) 将请求路由到指定目标
  - c) 处理任务的动态 IP
  - d) 以上全部

### 答案

- 1. b
- 2. d

### 问题

- Amazon ECS 集群中的任务是什么？
- Application Load Balancer (ALB) 的用途是什么？
- 什么是 ECS 服务及其作用？

### 加入我们图书的 Discord 空间

加入图书的 Discord 工作区，获取最新更新、优惠、全球技术动态、新版本发布以及与作者的会议：

https://discord.bpbonline.com

![](img/cc4299656808e62a294f1843a1e18e72_404_0.png)

## 第 14 章

### 简介

到目前为止，你已学习了多种在生产环境中部署 ML 模型的技术。然而，将模型部署到生产环境并非终点；监控是下一个重要步骤。本章讨论模型监控的概念和技术。模型监控不仅限于部署模型的最终端点；你还应根据需要将其集成到中间阶段。静态 ML 模型是在历史数据上离线训练的。然而，该模型可能无法永远提供一致的性能。主要原因可能包括输入数据、业务需求的变化以及模型随时间的降级。

### 结构

本章将涵盖以下主题：

- 监控的重要性
- ML 监控基础
- 用于监控 ML 系统的指标
- ML 中的漂移 - 类型和检测技术
- 使用 Prometheus 和 Grafana 进行运营监控
- 使用 whylogs 和 WhyLabs 进行 ML 模型监控

### 目标

学习本章后，你可以开始监控 ML 模型。你应该能够理解监控的重要性和基础，决定为项目监控哪些指标，并理解 ML 中漂移的概念、其类型以及检测漂移的技术。你还应该能够使用 whylogs（一个开源的轻量级库）和 WhyLabs（一个可观测性平台）监控数据中的漂移。你还应该能够将 Prometheus 和 Grafana 与 FastAPI 集成，并使用开源工具（即 Prometheus 和 Grafana）进行运营监控。

### 监控的重要性

一旦 ML 模型在生产环境中部署，就必须对其进行监控，以确保模型性能保持达标，并继续无缝提供可靠的输出。事实上，ML 应用或服务失败的原因有很多，例如管道故障、模型随时间的降级、模型输入数据的变化、系统或服务器故障以及架构的变更。

将模型部署到生产环境时通常涉及多个团队，包括数据科学家、数据工程师和 DevOps 团队。如果预测错误增加，谁将承担责任？生产环境中模型的所有者是谁？

由于 COVID-19，银行的 ML 模型性能受到严重影响。模型的预测与实际数字相去甚远。这是输入数据偏移的一个案例。这应让你了解将模型部署到生产环境后面临的挑战以及监控 ML 模型的必要性。

在比较新旧模型性能及其随时间的预测时，监控至关重要。可能存在延迟问题，即输出延迟。为了跟踪和调查延迟问题，需要高效的监控。你需要监控输入数据，以确保生产输入数据的处理方式与训练数据相同。在将数据传递给模型之前，为了跟踪和处理极端值、超出范围的值或特殊情况，需要监控。最后但同样重要的是模型安全性，即需要监控来跟踪对模型或系统的任何外部攻击。

ML 监控的目标如下：

- 在早期阶段检测问题或故障，以便采取必要措施
- 跟踪资源使用情况和模型预测，以评估生产环境中的模型和系统性能
- 检测输入数据中可能导致预测出错的分布、架构和异常变化
- 确保模型预测的可用性，并且这些预测是可解释的
- 跟踪并在指定存储或数据库中存储指标

模型监控帮助数据科学家减少模型故障、避免停机，并确保为用户提供可靠的结果。

### ML 监控基础

ML 监控是指跟踪已部署模型的性能、错误、指标等，并在需要时发送警报，以确保模型持续在可接受的阈值之上运行。它不仅限于跟踪输入数据或模型降级。但是，它应考虑所有可能直接或间接影响模型性能的因素。ML 监控有助于决定现有模型是否需要更新。

以下是需要考虑的基本步骤：

- **监控是关键**：一旦模型在生产环境中部署，监控就至关重要。监控使你能够更快地跟踪和修复问题或错误。监控大致可分为两类：
  - **功能监控**：在 ML 中，功能监控是指跟踪与 ML 模型相关的指标、错误和性能，例如准确率和异常值。
  - **运营监控**：运营监控是指跟踪系统特定指标，例如 CPU 和 RAM 利用率、正常运行时间和吞吐量。

- **可扩展集成**：监控应易于与现有基础设施和工作流集成。监控系统应无缝且易于扩展集成。如果存在多个模型，它应该能够跟踪多个模型。监控解决方案应与平台无关，以便可用于不同类型的部署，具有不同的技术栈。

- **指标跟踪**：仅跟踪准确率是不够的。监控系统应能够跟踪所有随时间可能影响模型和系统性能的指标。集中式监控系统应使用多个性能指标来提供解决方案的整体状态。对不同类型的功能使用不同的指标。例如，最小值（min）、最大值（max）、平均值（mean）、标准差（standard deviation）和异常值（outliers）可用于数值数据。指标记录和日志需要存储在数据库中，以便以后分析。





- **针对重要事件的警报系统**：您无法全天候手动跟踪 100+ 个指标；因此，警报系统应作为监控解决方案的一部分。并非所有内容都需要警报。您可能正在跟踪 20+ 个指标；然而，只有少数指标需要高度关注。例如，如果输入数据漂移超过阈值，则警报系统应将通知发送给负责团队或数据科学家。警报系统的整个目的是通知相关团队或个人，以便尽早避免或解决问题或错误，确保 ML 模型性能的一致性。

- **根本原因分析与调试**：收到警报后，您可能需要采取行动。可以开始根本原因分析以确定问题并通过调试进行修复。例如，如果模型准确率低于阈值，可能是由于输入数据分布的变化或异常所致。

要设计高效的监控系统，您需要考虑现有的管道和基础设施。监控主要有三大支柱：

- **处理与存储**：它会将关键指标连同时间戳处理并存储在数据库或数据源中。您可在需要时查询这些指标。

- **图表与仪表板**：它会从连接的数据库或数据源查询或获取监控指标。您可根据指标类型选择可视化方式。在此，您需要决定要显示的指标。它应通过直观图表总结整体监控情况。

- **警报**：最后，如有需要，它应向相关团队或数据科学家发送警报，以便立即采取行动。这有助于防止未来故障或减轻影响。

以下图表展示了用于有效监控的监控系统三大支柱：

## 监控系统支柱

![](img/cc4299656808e62a294f1843a1e18e72_408_0.png)

图 14.1：监控系统支柱

在设置任何监控系统之前，以下是需要回答的问题列表：

- 您计划监控什么？
- 您使用什么工具和语言？
- 监控将使用什么平台或库？
- 您计划如何将监控设置与现有环境和工具集成？
- 警报将使用什么阈值？
- 检测到问题或故障后应采取什么措施？

最后，根据模型生命周期，监控应完成反馈回路，即在检测到问题或故障后，应向相关团队或数据科学家发送通知，以便他们采取必要措施，例如重新训练 ML 模型。

## 监控 ML 系统的指标

您需要决定监控哪类指标。运营指标将使开发人员能够跟踪系统或服务器相关的故障或警告，例如可能增加延迟并影响最终用户体验的高资源使用情况。跟踪运营指标至关重要，因为服务器应保持良好状态以运行 ML 模型和其他任务。另一个因素是成本。运营团队需要设定成本上限，并跟踪哪些资源或服务导致了更高的成本。

以下是几个重要的运营指标：

- 系统或服务器
  - 资源使用情况
  - 可用性
  - 延迟
  - 吞吐量
- 成本
  - 基础设施成本
  - 存储成本
  - 其他服务（如有）

服务器在无任何问题的情况下运行正常后，您可以专注于功能或 ML 模型指标。您将在本章中学习模型监控指标的检测及应对方法。

以下是几个重要的模型指标：

- 输入数据
  - 模型版本
  - 数据漂移
  - 异常值
- ML 模型
  - 模型版本
  - 模型超参数
  - 元数据
  - 预测或输出
  - 分类模型评估指标
    - 准确率
    - 混淆矩阵
    - ROC-AUC 分数
    - 精确率和召回率分数
    - F1 分数
  - 回归模型评估指标
    - 均方根误差 (RMSE)
    - R 平方和调整 R 平方
    - 平均绝对误差 (MAE)
    - 平均绝对百分比误差 (MAPE)
- 预测漂移

您可以决定密切跟踪哪些指标以及哪些指标需要警报。

## ML 中的漂移

模型漂移是指 ML 模型行为的改变，或模型未按预期或服务等级协议 (SLA) 运行。模型部署到生产环境后，其性能可能会下降，因为模型可能接收到在模型训练期间未引入的数据。

### ML 中的漂移类型

ML 中主要有三种漂移：

- 数据漂移
- 预测漂移
- 概念漂移

### 数据漂移

数据漂移是指相对于训练数据，输入特征的分布或特征发生变化。它也称为特征漂移、总体漂移或协变量转移。如果输入数据的分布发生变化，则其预测可能会受到影响，因为模型对此没有准备。

如果在部署后向特征添加了新类别，则在进行预测时可能会导致错误，因为模型训练时不存在该类别。

另一个示例是，假设训练数据中有一个名为**信用评级**的特征，且其权重较高，这意味着该特征的变化可能会导致模型输出发生重大变化。现在，企业决定使用穆迪信用评级而非标准普尔。这将导致输入数据发生变化。例如，标准普尔的 AA- 相当于穆迪的 Aa3 评级。

以下公式显示训练数据的分布与参考（生产）数据的分布不匹配。

从数学上定义，数据漂移可表示如下：

```
P(X) ≠ Pref(X)
```

其中 P(X) 表示输入数据概率分布。

### 预测漂移

随着数据漂移导致输入数据发生变化，这可能会导致目标或预测变量发生变化。它是指随时间推移预测结果的变化。它也被称为先验概率偏移、标签漂移或无条件类别偏移。这也可能由于类别的删除或添加而发生。重新训练模型有助于缓解因预测漂移导致的模型性能下降。

从数学上定义，预测漂移可表示如下：

```
P(Y) ≠ Pref(Y)
```

其中 P(Y) 表示目标标签的先验概率分布。

### 概念漂移

当自变量与因变量或目标变量之间的关系发生变化时，会发生概念漂移。它也被称为后验类别偏移、条件变化或真实概念漂移。它是指输入变量与目标变量之间关系的变化。如果检测到任何显著的概念漂移，那么模型的预测很可能不可靠。概念漂移中的**概念**是指自变量与因变量之间的关系。

例如，一家汽车保险公司更改其赔偿政策，规定对汽车特定部件的索赔将被拒绝。假设汽车的该部件在事故中损坏，客户的索赔将被拒绝。在此场景中，即使输入数据的分布保持不变，输入特征与目标特征之间的映射也会发生变化。

从数学上定义，概念漂移可表示如下：

$P(Y|X) \neq Pref(Y|X)$

其中 $P(Y|X)$ 表示目标标签的后验概率分布。

概念漂移的模式如下：

- 突发或突然
- 渐进
- 循环或周期性
- 增量
- 临时

![](img/cc4299656808e62a294f1843a1e18e72_412_0.png)

图 14.2：概念漂移的不同模式

## 检测 ML 中漂移的技术

使用两个分布之间的距离指标进行统计距离测量对于检测 ML 中的漂移很有用。

如果数据集中有许多自变量，则可以使用降维技术，例如 PCA。跟踪许多特征会增加监控系统的负载，并且有时通过针对特定特征来减轻漂移会变得困难。

基本统计指标，例如均值、标准差、相关性以及最小值和最大值比较，可用于计算训练数据与当前自变量之间的漂移。

可用于连续特征的距离度量包括总体稳定性指数 (PSI)、特征稳定性指数 (CSI)、Kullback–Leibler 差异 (KL-Divergence)、Jensen–Shannon 差异 (JS-Divergence) 和 Kolmogorov–Smirnov (KS) 统计量。





## 解决 ML 中的漂移问题

Once you detect the drift in the ML model, it can be addressed in the following ways:

### 数据质量问题

If there is an issue with input data, then it can be easily fixed. For instance, high-resolution images were provided for training face recognition models; however, low-resolution images were passed to the deployed model.

### 重新训练模型

After detecting the data or concept shift, retraining the model with recent data can improve its performance. Sometimes production data is not sufficient to train the model. In that case, you can combine historical data with recent production data and give more weight to recent data.

Here are four strategies for retraining the model:

- **定期重新训练**: Scheduling it at a fixed time, for instance, every Monday at 10 PM
- **数据或事件驱动**: When new data is available
- **模型或指标驱动**: When accuracy is lower than a threshold or SLA
- **在线学习**: Where the model continuously learns in real-time or near real-time on the latest data

### 重建或调优模型

If retraining the model doesn’t work, then you may need to consider rebuilding it or tuning it on recent data. You can automate this using a pipeline.

## 使用 Prometheus 和 Grafana 进行运营监控

Prometheus is an open-source system used for event monitoring and alerting. It scrapes the real-time data instrumented jobs and stores it with a timestamp in the database. The word **instrument** refers to the use of a client library that allows Prometheus to track and scrape its metrics and store them locally. Prometheus offers client libraries that can be used to instrument your application. In this scenario, you will be using the Prometheus Python client in the FastAPI application to expose its metrics that need to be tracked.

A Prometheus server scrapes and stores metrics from instrumented jobs in time series format. This data can be fetched using PromQL - query language, and it can be used to visualize the metrics. It comes with an alert manager to handle alerts.

According to GrafanaLabs, Grafana is an open-source interactive visualization and monitoring platform that enables users to visualize metrics, logs, and traces collected from deployed applications. Grafana is easy to integrate with most common databases, such as Prometheus, Influx DB, ElasticSearch, MySQL, and PostgreSQL.

As Grafana is an open source tool, hence you can write an integration plugin from scratch to connect with multiple data sources. The Grafana dashboard fetches the data from connected data sources and allows you to pick up the visualization type from plenty of visualization options, such as heat maps, bar charts, and line graphs. You can easily run the query, visualize metrics, and set up alerts for critical events.

In this scenario, you will be using Grafana and Prometheus. Both Prometheus and Grafana are open-source tools. As a matter of fact, Prometheus and Grafana are popular combinations in the industry for monitoring systems. Grafana dashboard will be used for visualization and alert management. It will fetch the data from the Prometheus database for querying metrics and will display the intuitive visualization on the dashboard.

Prometheus and Grafana can be separately installed and configured on a local machine or a remote server. However, you will be using docker images of Prometheus and Grafana by executing the docker-compose.yaml file.

To maintain consistency, similar files from the previous chapters with minor modifications will be used. The files required for Prometheus and Grafana dashboards are added as shown in the following file structure:

- .gitignore
- config.monitoring
- datasource.yml

```
|-- docker-compose.yml
|-- Dockerfile
|-- fastapi-dashboard.json
|-- LICENSE
|-- main.py
|-- prometheus.yml
|-- pytest.ini
|-- README.md
|-- requirements.txt
|-- runtime.txt
|-- start.sh
|-- test.py
|-- tox.ini
|-- app
|   |-- MANIFEST.in
|   |-- README.md
|   |-- requirements.txt
|   |-- setup.py
|   |-- tox.ini
|   └-- prediction_model/
        |-- pipeline.py
        |-- predict.py
        |-- train_pipeline.py
        |-- VERSION
        |-- __init__.py
        |-- config/
        |   |-- config.py
        |   └-- __init__.py
        |-- datasets/
        |   |-- test.csv
        |   |-- train.csv
        |   └-- __init__.py
```

```
|-- processing/
|   |-- data_management.py
|   |-- preprocessors.py
|   |-- __init__.py
|-- trained_models/
|   |-- classification_v1.pkl
|   |-- __init__.py
|-- tests/
|   |-- pytest.ini/
|   |-- test_predict.py
```

### config.monitoring

The extension of this file is .monitoring. In this file, configure the admin password and user permission for sign up.

```
1. GF_SECURITY_ADMIN_PASSWORD=pass@123
2. GF_USERS_ALLOW_SIGN_UP=false
```

The Docker container currently allows new Grafana users to sign up, so anyone can create an account and view the dashboard. Therefore, for security purposes, the admin password and allowing new users to sign up should be set to false.

### prometheus.yml

This file contains Prometheus configurations, such as `scrape_configs` and `scrape_intervals`.

```
1. # Global config
2. global:
3.   scrape_interval: 15s
4.   evaluation_interval: 15s
5.   external_labels:
6.     monitor: "app"
7.
8.   rule_files:
9.
10. scrape_configs:
11.   - job_name: "prometheus"
12.
13. static_configs:
14.   - targets: ["localhost:9090"]
15.
16.   - job_name: "app"
17. dns_sd_configs:
18.   - names: ["app"]
19.   port: 8000
20.   type: A
21.   refresh_interval: 5s
```

In this file, the scrape interval is set to 15 seconds (**15s**) in the global config, which means it will scrape the metrics data after every 15 seconds. It is targeting an app, that is, the FastAPI app here. Port is the app’s port, that is, **8000**, and the refresh interval is set to 5 seconds (**5s**).

### Dockerfile

This Dockerfile will install the dependencies, set the working directory, expose ports, and finally, run the ML app.

```
1. FROM python:3.7-slim-buster
2.
3. ENV PYTHONPATH "${PYTHONPATH}:src/"
4.
5. WORKDIR /app/
6.
7. COPY . .
8.
9. RUN chmod +x /app
10.
11. COPY ./start.sh /start.sh
12.
13. RUN chmod +x /start.sh
14.
15. # Expose the port that uvicorn will run the app on
16. ENV PORT=8000
17. EXPOSE 8000
18.
19. RUN pip install --upgrade pip
20.
21. RUN pip install --upgrade -r requirements.txt --no-cache-dir
22.
23. CMD ["/start.sh"]
```

### docker-compose.yaml

This docker-compose file will set up and run three services:

- The app, that is, FastAPI app: For the ML model. It will run on port **8000**.
- Prometheus server: It will run on port **9090**.
- Grafana dashboard: It will run on port **3000**.

In the following file, you can see that the Grafana service depends on the Prometheus service:

```
1. version: "2.2"
2.
3. services:
4.   app:
5.     build: .
6.     restart: unless-stopped
7.     container_name: app
8.     ports:
9.     - 8000:8000
10.    networks:
11.      example-network:
12.        ipv4_address: 172.16.238.10
13.
14.   prometheus:
15.     image: prom/prometheus:latest
16.     restart: unless-stopped
17. container_name: prometheus
18. ports:
19.   - 9090:9090
20. volumes:
21.   - ./prometheus.yml:/etc/prometheus/prometheus.yml
22. command:
23.   - "--config.file=/etc/prometheus/prometheus.yml"
24. networks:
25.   example-network:
26.     ipv4_address: 172.16.238.11
27.
28. grafana:
29. image: grafana/grafana:latest
30. restart: unless-stopped
31. user: "472"
32. container_name: grafana
33. depends_on:
34.   - prometheus
35. ports:
36.   - 3000:3000
37. volumes:
38.   - ./datasource.yml:/etc/grafana/provisioning/datasource.yml
39. env_file:
40.   - ./config.monitoring
41. networks:
42.   example-network:
43.     ipv4_address: 172.16.238.12
44.
45. networks:
46.   example-network:
47.     # name: example-network
```



driver: bridge
ipam:
driver: default
config:
- subnet: 172.16.238.0/24

## main.py

此文件包含 FastAPI 应用的代码。在此代码中，添加以下两行代码以对 FastAPI 应用进行插桩。在 Prometheus 中，插桩是指在应用程序代码（在此场景中为 FastAPI）中使用库，以便 Prometheus 可以抓取应用公开的指标。

首先，将版本为 **5.7.1** 的 `prometheus-fastapi-instrumentator` 添加到 `requirements.txt` 文件中。然后，按如下方式导入 Prometheus FastAPI 插桩器：

```
from prometheus_fastapi_instrumentator import Instrumentator
```

然后，在文件末尾添加以下行，以将 FastAPI 应用插桩到 Prometheus FastAPI 插桩器：

```
Instrumentator().instrument(app).expose(app)
```

通过这一行代码，FastAPI 将被插桩，FastAPI 应用中使用的所有 Prometheus 指标均可通过添加的 **/metrics** 端点进行抓取。

您在前面的章节中已经学习了其余文件。有关前面目录结构中提到的文件，请参阅前面的章节。

您需要在终端中运行以下 docker-compose 命令来启动 docker 容器：

```
docker-compose up
```

现在您可以访问三个容器及其各自的端口：

- FastAPI: 运行于 http://localhost:8000/
- Prometheus: 运行于 http://localhost:9090/
- Grafana 仪表板: 运行于 http://localhost:3000/

在 FastAPI 应用上，您可以访问 `/metrics` 端点以查看 Prometheus 从中抓取的数据，如下图所示：

```
# HELP python_gc_objects_collected_total Objects collected during gc
# TYPE python_gc_objects_collected_total counter
python_gc_objects_collected_total{generation="0"} 27968.0
python_gc_objects_collected_total{generation="1"} 5156.0
python_gc_objects_collected_total{generation="2"} 92.0
# HELP python_gc_objects_uncollectable_total Uncollectable object found during GC
# TYPE python_gc_objects_uncollectable_total counter
python_gc_objects_uncollectable_total{generation="0"} 0.0
python_gc_objects_uncollectable_total{generation="1"} 0.0
python_gc_objects_uncollectable_total{generation="2"} 0.0
# HELP python_gc_collections_total Number of times this generation was collected
# TYPE python_gc_collections_total counter
python_gc_collections_total{generation="0"} 325.0
python_gc_collections_total{generation="1"} 29.0
python_gc_collections_total{generation="2"} 2.0
```

### 图 14.3：FastAPI 指标

您可以在端口 9090 上访问 Prometheus UI 并运行 PromQL 查询。要获取请求总数，请执行 **prometheus_http_requests_total**。您将获得 HTTP 状态码、处理程序、实例、作业名称和计数，如下图所示：

使用本地时间 启用查询历史 启用自动补全 启用高亮显示 启用 linter prometheus_http_requests_total 执行

| 系列 | 值 |
| :--- | :--- |
| prometheus_http_requests_total{code="200", handler="/api/v1/label/name/values", instance="localhost:9090", job="prometheus"} | 55 |
| prometheus_http_requests_total{code="200", handler="/api/v1/labels", instance="localhost:9090", job="prometheus"} | 54 |
| prometheus_http_requests_total{code="200", handler="/api/v1/metadata", instance="localhost:9090", job="prometheus"} | 58 |
| prometheus_http_requests_total{code="200", handler="/api/v1/query", instance="localhost:9090", job="prometheus"} | 28 |
| prometheus_http_requests_total{code="200", handler="/api/v1/query_range", instance="localhost:9090", job="prometheus"} | 5023 |
| prometheus_http_requests_total{code="200", handler="/api/v1/rules", instance="localhost:9090", job="prometheus"} | 19 |
| prometheus_http_requests_total{code="200", handler="/api/v1/series", instance="localhost:9090", job="prometheus"} | 2 |
| prometheus_http_requests_total{code="200", handler="/api/v1/status/buildinfo", instance="localhost:9090", job="prometheus"} | 3 |
| prometheus_http_requests_total{code="200", handler="/metrics", instance="localhost:9090", job="prometheus"} | 592 |
| prometheus_http_requests_total{code="200", handler="/static/filepath", instance="localhost:9090", job="prometheus"} | 1 |
| prometheus_http_requests_total{code="400", handler="/api/v1/query_range", instance="localhost:9090", job="prometheus"} | 2 |

### 图 14.4：Prometheus UI—查询执行

Prometheus 允许您通过切换到 Prometheus Web UI 中的 Graph 选项卡以图形格式查看这些查询结果。

您已经见识了 Prometheus Web UI，PromQL 也在获取指标数据。现在，在下一部分中，您将把 Prometheus 作为数据源连接到 Grafana 仪表板。从 Prometheus 服务器获取的指标数据将在 Grafana 仪表板上可视化。转到 Grafana 仪表板 Web UI 并单击“添加您的第一个数据源”选项，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_422_0.png)

### 图 14.5：Grafana–添加数据源

接下来，从时间序列数据库中选择 Prometheus 数据库，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_422_1.png)

### 图 14.6：Grafana–Prometheus 数据源

在设置中，在 Name 字段中提供 Prometheus 作为名称。然后，在 URL 字段中输入 http://prometheus:9090，如下图所示，因为 Prometheus 服务正在端口 9090 上运行：

![](img/cc4299656808e62a294f1843a1e18e72_423_0.png)

### 图 14.7：Grafana–Prometheus 配置

最后，继续进行基本配置；不过，您也可以配置其他字段。滚动到页面底部并单击 **Save & test** 按钮，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_423_1.png)

### 图 14.8：Grafana–保存并测试 Prometheus 配置

如果配置正确，保存并测试配置后，您应该会看到集成状态成功消息。

Prometheus 集成完成后，在 Grafana Web UI 中使用 **New Dashboard** 选项创建新仪表板，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_423_2.png)

### 图 14.9：Grafana–创建新仪表板

Grafana 仪表板可以从头开始创建，也可以通过从存储中导入 JSON 文件来创建。Grafana 还允许您通过 Grafana.com 导入仪表板，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_424_0.png)

### 图 14.10：Grafana–上传 JSON 文件

在此场景中，从目录导入 JSON 文件。您可以参考由 Grafana Labs 托管的原始公共 Grafana 实例之一，使用以下链接：https://play.grafana.org/d/000000012/grafana-play-home?orgId=1

有关各种仪表板可视化和数据源，请参阅以下链接 https://grafana.com/grafana/dashboards/。

接下来，提供仪表板名称和 Prometheus 数据源，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_424_1.png)

### 图 14.11：Grafana–作为数据源的 Prometheus

最后，从 Web UI 打开新创建的仪表板。从 JSON 文件导入仪表板后，您可以通过更改图表类型来自定义仪表板，如下图所示。

![](img/cc4299656808e62a294f1843a1e18e72_425_0.png)

### 图 14.12：Grafana-仪表板

下一步是针对关键事件发送警报。Grafana 内置了对 Prometheus Alertmanager 的支持。Grafana 主要提供三种设置警报的策略：

- **Cloud Alertmanager**：Cloud Alertmanager 运行在 Grafana Cloud 中。它支持来自 Grafana、Mimir 和 Loki 的警报。
- **Grafana Alertmanager**：Grafana Alertmanager 是一个内置的 Alertmanager。它已预配置并支持来自 Grafana 的警报；但是，它无法接收 Grafana 外部的警报。
- **外部 Alertmanager**：您可以配置 Grafana 以使用外部 Alertmanager。当您需要一个能够接收来自不同来源警报的集中式 Alertmanager 时，这很有用。





可以在 Grafana 中添加告警规则、标签和通知策略。下图显示了 Grafana 中的 Alert UI：

![](img/cc4299656808e62a294f1843a1e18e72_426_0.png)

图 14.13：Grafana—告警 UI

## 使用 whylogs 和 WhyLabs 进行 ML 模型监控

WhyLabs 是一个模型监控和可观测性平台，用于监控数据漂移、模型性能下降、数据质量、模型评估指标，并向团队或个人发送告警。它建立在开源包 **whylogs** 之上。你可以使用 WhyLabs Observability Platform 持续监控 whylogs 配置文件。

WhyLabs 的主要特性如下：

- **设置时间短**：你可以先安装轻量级开源库 whylogs，使用 **pip install whylogs**。片刻之后，即可生成数据集的摘要，即 whylogs 配置文件，这可帮助你完成以下操作：
  - 跟踪数据集的变化
  - 可视化数据集的汇总统计信息
  - 通过定义数据约束来检查数据质量

- **无缝集成**：它可以轻松与现有的数据管道、模型生命周期、模型框架和 MLOps 生态系统集成。

- **数据隐私**：WhyLabs 使用 whylogs 代理创建的数据统计摘要，因此你的实际数据不会被传输或存储在 WhyLabs 平台上。

- **可扩展性**：它可以轻松扩展以处理大量数据和多个项目。

- **集中监控**：使用 WhyLabs 平台，你可以在单一框架下监控多个项目。它允许你在单个帐户中创建多个隔离项目，并且还会跟踪输入和输出数据、模型性能等。

## whylogs

废话不多说，让我们开始使用 whylogs 的日志记录功能。首先，如果尚未安装 whylogs，请使用 **pip install whylogs** 进行安装。接着，导入贷款预测数据集并使用 whylogs 开始记录它。

```
1. # Import packages
2. import numpy as np
3. import pandas as pd
4. from sklearn.model_selection import train_test_split
5. pd.set_option("display.max_columns", None) #To show all columns in DataFrame
6. import whylogs as why
7.
8. df = pd.read_csv("https://gist.githubusercontent.com/suhas-ds/a318d2b1dda8d8cbf2d6990a8f0b7e8a/raw/9b548fab0952dd12b8fdf057188038c8950428f1/loan_dataset.csv")
9.
10. profile1 = why.log(df)
11. profile_view1 = profile1.view()
12. profile_view1.to_pandas()
```

要查看统计摘要，即 whylogs 配置文件，请将其转换为 pandas DataFrame。配置文件的 pandas DataFrame 包含以下指标：

- cardinality/est
- cardinality/lower_1
- cardinality/upper_1
- counts/n
- counts/null
- distribution/max
- distribution/mean
- distribution/median
- distribution/min
- distribution/n
- distribution/q_01
- distribution/q_05
- distribution/q_10
- distribution/q_25
- distribution/q_75
- distribution/q_90
- distribution/q_95
- distribution/q_99
- distribution/stddev
- frequent_items/frequent_strings
- ints/max
- ints/min
- type
- types/boolean
- types/fractional
- types/integral
- types/object
- types/string

这涵盖了关于输入数据的几乎所有所需信息，例如基数、类型、频繁项、分布和计数。

### 用于数据质量验证的约束

使用 whylogs，你可以使用约束来执行数据验证。此功能可用于单元测试或 CI/CD 管道，以便避免进一步的错误。你可以对配置文件指标设置约束，例如计数、分布和类型。whylogs 还支持用户定义的自定义指标。你需要一个 whylogs 配置文件来在数据上设置约束。

设置新约束很简单；你需要为以下内容赋值：

- name：可以是任何字符串，用于描述约束。
- condition：它是 lambda 表达式。
- metric_selector：它是要测量或验证的指标类型。

```
from whylogs.core.constraints import (Constraints,
ConstraintsBuilder,
```

```
3. MetricsSelector,
4. MetricConstraint)
5.
6. # Function with Constraints for Data Quality Validation
7. def validate_feat(profile_view, verbose=False, viz=False):
8. builder = ConstraintsBuilder(profile_view)
9. # Define a constraint for data validation
10. builder.add_constraint(MetricConstraint(
11. name="Credit_History == 0 or == 1",
12. condition=lambda x: x.min == 0 or x.max == 1,
13. metric_selector=MetricsSelector(metric_name='distribution',
14. column_name='Credit_History')
15. ))
16.
17. # Build the constraints and return the report
18. constraints: Constraints = builder.build()
19.
20. if verbose:
21. print(constraints.report())
22.
23. # return constraints.report()
24. return constraints
25.
26. const = validate_feat(profile_view1, True)
```

在当前场景中，约束设置为确保 **Credit_History** 特性应仅包含 **0** 或 **1**。如果接收到 **0** 或 **1** 之外的任何值，将验证失败。你可以添加多个约束来一次性验证多个条件。以下是前面代码的输出：

```
[('Credit_History == 0 or == 1', 1, 0)]
```

这可以理解为 [('约束名称', 通过, 失败)]。可以在笔记本中使用 whylogs 的可视化功能对其进行可视化。

```
1. from whylogs.viz import NotebookProfileVisualizer
2. visualization = NotebookProfileVisualizer()
3. visualization.constraints_report(const, cell_height=300)
```

图 14.14 描绘了约束报告，即前面代码的输出，用于可视化约束的结果：

![](img/cc4299656808e62a294f1843a1e18e72_430_0.png)

图 14.14：whylogs-约束报告

为了一次性验证所有约束，你可以直接在约束的结果上使用 **validate()**。

```
1. # check all constraints for passing:
2. constraints_valid = const.validate()
3. print(constraints_valid)
```

由于它仅验证一个条件，将检查该条件是否为 true。由于 **Credit_History** 特性中的数据包含 **0** 或 **1**，测试通过并打印 **True**。

**True**

接下来，使用少量代码，你可以生成漂移报告。为此，你需要数据的两个 whylogs 配置文件：目标配置文件和参考配置文件。

```
1. from whylogs.viz import NotebookProfileVisualizer
2.
3. visualization = NotebookProfileVisualizer()
4. visualization.set_profiles(target_profile_view=profile_view1, reference_profile_view=profile_view2)
5.
6. visualization.profile_summary()
7.
8. visualization.summary_drift_report()
```

使用 summary_drift_report()，你可以获取易于阅读的漂移报告。它是两个配置文件之间按功能进行的交互式比较。此报告包含以下内容：

- Target：目标配置文件的直方图
- Reference：参考配置文件的直方图
- p-value：范围从 0 到 1
- Total count：数据集中记录或实例的计数
- Mean：数值特征的平均值

## WhyLabs

下一步是开始将这些配置文件上传到 WhyLabs 平台。

第一步是在 https://whylabs.ai/whylabs-free-sign-up 注册帐户。如果已经完成此步骤，请登录帐户。接着，在项目管理部分创建新项目。根据要求，有不同类型的项目可供选择，例如 ML 模型和数据管道。在此场景中，选择分类（即 ML 项目），以便你可以分析模型的性能和输入输出数据。

如下图所示，将项目名称提供为 ML_monitor（稍后可以更新），类型提供为 Classification：

![](img/cc4299656808e62a294f1843a1e18e72_431_0.png)

图 14.15：WhyLabs—项目管理





然后，您需要以下三项才能开始将 whylogs 配置文件上传到 WhyLabs 平台：

- 一个 WhyLabs API 密钥
- 组织 ID
- 每个项目一个不同的数据集或模型 ID

从“访问令牌”选项卡创建新的访问令牌，如下图所示。保存访问令牌和组织 ID，因为访问 WhyLabs 中的项目时可以多次使用。

![](img/cc4299656808e62a294f1843a1e18e72_432_0.png)

WhyLabs 允许您通过以下方式设置重要事件的通知工作流：

- 电子邮件
- Slack
- PagerDuty

下图显示了 WhyLabs 在“通知”页面下提供的通知选项：

![](img/cc4299656808e62a294f1843a1e18e72_432_1.png)

在 **用户管理** 选项卡中，您可以查看团队成员及其角色。您还可以控制用户的权限和访问权限。在此场景中，下图显示了一个具有 **管理员** 角色的用户：

![](img/cc4299656808e62a294f1843a1e18e72_433_0.png)

图 14.18：WhyLabs–用户管理

接下来，确保从“选择 **项目**”下拉菜单中选择了目标项目。您可以更新监视器的默认值和选择。您还可以设置阈值、滚动窗口、操作、严重级别等，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_433_1.png)

图 14.19：WhyLabs–监视器管理器

WhyLabs 提供预设监视器来针对常见检测。您可以为项目使用这些易于使用的预设监视器，而无需从头开始设置。配置后，您可以单击启用。WhyLabs 提供以下预设监视器：

- 漂移
  - 与滚动 7 天基线相比，所有离散模型输入的数据漂移
  - 与滚动 7 天基线相比，所有非离散模型输入的数据漂移
- 数据质量
  - 缺失值
  - 唯一值
  - 数据类型
  - 百分比变化
- 模型性能
  - F1 分数
  - 精确率
  - 召回率
  - 准确率
- 集成健康
  - 数据可用性

下图显示了 WhyLabs 中可用于检查输入数据质量的预设：

![](img/cc4299656808e62a294f1843a1e18e72_434_0.png)

图 14.20：WhyLabs–数据质量预设

现在，如果尚未安装 whylogs，请使用以下命令进行安装，或直接使用 pip 安装 whylogs：

```
pip install -q "whylogs[whylabs]"
```

首先，使用组织 ID、访问密钥和项目 ID 声明变量。接下来，加载数据并构建模型。

```
whylabs_org = 'org-ELqbpF'
whylabs_key = '0Ji9w2gC7qlQQ4pxgQBEUdx********************D0vvDrL'
whylabs_project = 'model-5'

# Importing the required packages
import numpy as np
import pandas as pd
from sklearn.linear_model import LogisticRegression

from sklearn import preprocessing
from sklearn.model_selection import train_test_split, GridSearchCV
from sklearn import metrics
import whylogs as why
import os
from whylogs.api.writer.whylabs import WhyLabsWriter
import datetime as dt
writer = WhyLabsWriter()
os.environ["WHYLABS_DEFAULT_ORG_ID"] = whylabs_org # ORG-ID is case sensitive
os.environ["WHYLABS_API_KEY"] = whylabs_key
os.environ["WHYLABS_DEFAULT_DATASET_ID"] = whylabs_project

# Read the data
data = pd.read_csv("https://gist.githubusercontent.com/suhas-ds/a318d2b1dda8d8cbf2d6990a8f0b7e8a/raw/9b548fab0952dd12b8fdf057188038c8950428f1/loan_dataset.csv")
```

此处，由于重点在于模型监控，因此构建了基线模型。构建模型后，其在测试数据上实现了 80.9% 的准确率。现在，在现有 DataFrame 中创建其他列以存储模型预测和分数。

```
# Make Prediction
y_pred = lr_model.predict(X)
# Predict probability
y_pred_prob = lr_model.predict_proba(X)

# Get a maximum probability value of class
y_pred_prob_max = [max(p) for p in y_pred_prob]

# Output column name should contain the 'output' word
data.rename(columns={'Loan_Status':'output_loan_status'}, inplace=True)
data['output_prediction'] = y_pred
data['output_score'] = y_pred_prob_max
```

这样，您应该拥有一个包含输入数据和预测输出的 DataFrame。此处，请考虑模型预测的类别概率。为了显示每日批次的输出，将该 DataFrame 分为四个 DataFrames。在每个 for 循环迭代中减去 1 天，并将该时间戳分配给给定的数据集。

```
# Splitting the final DataFrame into four
df1, df2, df3, df4 = np.array_split(data, 4)

daily_batches = [df1, df2, df3, df4]

for i, data_frame in enumerate(daily_batches):
    date_time = dt.datetime.now(tz=dt.timezone.utc) - dt.timedelta(days=i)

    df = data_frame
    print("logging data for date {}".format(date_time))
    results = why.log_classification_metrics(
df,
target_column = "output_loan_status",
prediction_column = "output_prediction",
score_column="output_score"
)

profile = results.profile()
profile.set_dataset_timestamp(date_time)

print("writing profiles to whylabs...")
results.writer("whylabs").write()
```

由于这是一个分类示例，请使用 log_classification_metrics() 记录分类模型指标，并向 why.log_classification_metrics 传递以下四个参数。

### log_classification_metrics()

- 输入 DataFrame: 整个 DataFrame df
- target_column: 实际目标列
- prediction_column: 预测目标列
- score_column: 分数

如果列标题中包含“output”文本，WhyLabs 会将数据中的某一列识别为输出列。

WhyLabsWriter() 将在 WhyLabs 平台上发布摘要。转到 WhyLabs 中的“摘要”选项卡。它为多个小部件（如数据配置文件、输入运行状况、模型运行状况、模型性能和警报）提供紧凑的单一视图，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_437_0.png)

图 14.21：WhyLabs–摘要

在 **配置文件** 选项卡下，将显示总体数据摘要。它包括直方图、特征计数、特征类型、项目频率和空值等指标，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_438_0.png)

图 14.22：WhyLabs-配置文件

同样，您可以在 **输入** 选项卡中查看输入特征指标，如数据类型、项目总异常数和漂移距离，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_438_1.png)

图 14.23：WhyLabs-输入

此处，您可以查看随时间变化的总计数，因此显示折线图。

在 **输出** 选项卡下，您可以查看类似的指标，但针对输出列。

![](img/cc4299656808e62a294f1843a1e18e72_439_0.png)

图 14.24：WhyLabs-输出

最后，在 **性能** 选项卡中，您可以查看不同时间段的模型指标。在当前场景中，您每天传递一次数据。因此，您可以看到准确率每天都在变化。它还显示分类模型的其他模型评估指标，例如 ROC、精确率-召回率、混淆矩阵和 F1 分数。

在下图中，您可以查看带有时间戳以及准确率、ROC、精确率-召回率和混淆矩阵图表的最近模型准确率：

![](img/cc4299656808e62a294f1843a1e18e72_439_1.png)

图 14.25：WhyLabs-性能

**性能** 选项卡还每天显示输入和输出数据的总计数，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_440_0.png)

图 14.26：WhyLabs–总输入和输出计数

您可以参考以下链接中的 Google Colab 笔记本中的 whylogs 代码：
https://colab.research.google.com/gist/suhas-ds/8bc0c895b7aa95839eaa5a5df5492a42/whylogs-and-whylabs.ipynb

总体而言，WhyLabs 支持与 MLOps 环境中现有管道和工具的集成。由于它以最小配置运行，因此维护需求低或为零，并且它是动态的，这意味着它可以处理数据属性和特征的变化。

## 结论

在本章中，您学习了 ML 中监控的重要性及 ML 监控的基础知识。您还研究了检测和解决 ML 中漂移的各种技术，并探索了用于运营监控和功能监控的不同指标。接下来，您学习了如何将 Prometheus 和 Grafana 与 FastAPI 集成以进行运营监控。在本章后面，您使用 whylogs 和 WhyLabs 实现了 ML 模型监控解决方案。最后，您介绍了警报系统以完成 ML 生命周期的反馈循环。

在下一章中，您将学习在生产环境中部署 ML 模型后应遵循的步骤。您还将学习不同类型的 ML 攻击和模型安全性。

## 要点

确保列名包含单词 **output**，以便在 WhyLabs 平台的 **输出** 选项卡下显示输出或预测数据。





- ML监控是指跟踪已部署模型的性能、错误、指标等，并在必要时发送警报，以确保模型继续保持在可接受阈值以上。
- 一旦ML模型部署到生产环境，就必须对其进行监控，以确保其性能达标，并能持续无缝地提供可靠的输出。
- 当自变量与因变量或目标变量之间的关系发生变化时，就会发生概念漂移（Concept shift）。
- 监控应完成反馈回路，即在检测到问题或故障后，应向相关团队或数据科学家发送通知，以便他们采取必要措施。

## 多项选择题

1. 当自变量与因变量或目标变量之间的关系发生变化时，会发生______。

   - a) 概念漂移
   - b) 数据漂移
   - c) 协变量偏移
   - d) 标签漂移

2. 监控基础设施成本属于______类型。

   - a) 模型监控
   - b) 经常性监控
   - c) 运营监控
   - d) 经常性监控

## 答案

1. a
2. c

## 问题

1. 什么是概念漂移？
2. 监控在ML生命周期中的作用是什么？
3. ML中检测漂移的不同技术有哪些？

## 加入本书的Discord空间

加入本书的Discord工作区，获取最新动态、优惠、全球技术动态、新版本以及与作者的交流：
https://discord.bpbonline.com

![](img/cc4299656808e62a294f1843a1e18e72_442_0.png)

## 第 15 章

## 将ML模型投入生产后的处理

## 介绍

到目前为止，你已学习了ML生命周期的不同阶段，以及打包、部署和监控ML模型的方法。你还学习了如何实施测试以确保模块的完整性和正常运行。你已从ML模型创建出可在Windows和Android设备上运行的本地应用；在Microsoft Azure、GCP和AWS等流行的云平台上部署模型；并为运营监控和ML模型监控构建了监控解决方案。

然而，接下来的部分是从中获取商业价值。部署后，当新模型准备就绪时，你需要决定新模型是否优于现有模型，以便提供可靠的预测。将模型部署到生产环境后，模型安全性也至关重要。

## 本章结构

在本章中，将涵盖以下主题：

- ML模型与商业价值创造之间的差距
- 模型安全性
- A/B测试
- MLOps是未来

## 学习目标

学习本章后，你应能够降低ML生命周期中不同类型攻击的风险。在本章中，你将学习将MLOps解决方案转化为商业价值的重要性，并通过A/B测试和多臂老虎机（MAB）测试比较两个或多个ML模型，在部署ML模型时做出更好的决策。你还将研究MLOps在行业中的未来前景。

## 弥合ML模型与商业价值创造之间的差距

业务用户利用ML模型预测来制定业务策略和做出决策。获得良好的准确性并不意味着有良好的商业影响。有时，准确性较低的模型会增加公司的收入。你需要在构建ML解决方案与从中创造商业价值之间填补差距。数据科学家应能够将模型预测转化为易于理解的行动。例如，使用分类模型时，你可以根据类别的概率分数创建五个桶，然后对其进行排名，使最高概率获得最高排名。

在将ML模型连同监控系统部署到生产环境后，下一步是确保MLOps解决方案将使业务用户受益。你可以从利益相关者、业务用户或客户那里获取反馈，因为他们正在消费模型输出。例如，你可以询问业务用户，在部署模型后是否有某个特征比其他特征更重要，以便你可以给该特征赋予更高的权重。这样，你可以调整模型，以提供对业务用户更有用的预测。

数据科学家应能够向业务用户解释模型的工作原理（高层次），因为这将有助于他们信任模型输出，因为其中许多人不熟悉ML术语。业务用户或客户偏好以可读形式消费输出，例如交互式仪表板或聊天机器人。你也可以使用商业智能（BI）工具，例如Tableau或Power BI，来创建仪表板。

## 模型安全性

模型安全性是MLOps的重要组成部分。在处理数据时，可能需要保护其中可能包含的敏感信息。攻击可能发生在模型训练阶段或生产阶段。在本章中，你将熟悉不同类型的攻击，以便实施适当的解决方案来防止它们。

以下是与模型安全性相关的术语：

- **中毒攻击**：向训练过程传递恶意数据，旨在改变模型输出
- **模型提取**：从目标模型重建一个新模型，该新模型将与目标模型具有相同的功能
- **规避攻击**：通过对输入进行微小变化，试图将标签更改为特定类别
- **推理攻击**：判断特定数据集是否是训练数据的一部分
- **模型反演**：通过逆向工程，从训练好的模型获取关于训练数据的信息

## 对抗性攻击

这是一种生成敌对数据输入的方法。攻击者故意向模型发送恶意数据，使模型做出错误预测。随着模型学习新的数据模式，这种攻击会导致模型预测出错。这种恶意输入数据对人类来说可能看起来正常；然而，输入数据的微小变化可能对模型预测产生重大影响。

根据攻击者的目标，对抗性攻击可分为两大类：

- **目标攻击**：攻击者试图将标签更改为特定目标。为此，他们可以将输入数据源更改为特定目标。这需要更多的时间和精力。
- **非目标攻击**：攻击者没有模型应该预测的任何特定目标。然而，他们在没有任何特定目标的情况下更改标签。这需要较少的时间和精力。

攻击者可以使用以下方法进行对抗性攻击：

- **黑盒方法**：在此方法中，攻击者可以将输入数据发送到模型，并根据其获得输出。
- **白盒方法**：在此方法中，攻击者了解ML模型的几乎所有信息，例如训练数据和分配给特征的权重。

## 数据中毒攻击

在数据中毒攻击中，攻击者可以访问输入或源数据。他们以这种方式更改输入数据，使模型会做出错误的预测，这些预测不可靠，无法用于做出任何业务决策或采取任何行动。攻击者可以向原始数据添加一些噪声，以导致模型预测的变化。这种攻击针对训练数据并智能地修改它。

## 分布式拒绝服务攻击（DDoS）

它是指向模型传递复杂数据，导致模型花费更多时间进行预测。这种类型的攻击限制了用户对模型的使用。为此，攻击者可以注入一些恶意软件来控制系统或服务器。

## 数据隐私攻击

数据隐私是指个人可识别信息（PII）和个人健康信息（PHI）的保密性。攻击者试图通过这种类型的攻击了解这类敏感信息。可能是关于模型或训练数据的信息。支持向量机器（SVMs）等ML模型可能会泄露信息，因为支持向量是训练数据中的数据点。

数据隐私攻击可大致分为以下类别：

- 成员推断攻击：此攻击的目标是确定输入X是否是训练数据的一部分。大多数此类隐私攻击使用影子模型。影子模型训练使用影子数据集来模仿目标模型。影子模型的输出随后作为输入传递给元模型。最后，元模型的输出用于外推训练数据或模型的属性。过拟合模型容易受到数据隐私攻击。

- 输入推断攻击：也称为模型反演或数据提取攻击。这是最常见的攻击类型。此攻击的目标是通过逆向工程模型，从训练数据集中提取信息。它还可以针对学习输入数据的统计属性，例如概率分布。攻击者可以尝试学习在训练模型时未明确编码的特征。

- 模型提取攻击：也称为参数推断攻击。此攻击的目标是学习模型的超参数，然后重建表现与目标模型相同的模型。有趣的是，由于基于测试数据的预测错误较高，过拟合模型难以提取。





## 降低模型攻击风险

ML 管道大致可分为两个阶段：训练阶段和测试阶段。您可以根据这些阶段解决各种 ML 模型攻击。

## 训练阶段

数据科学家执行数据收集、数据清洗、特征工程、选择合适算法、超参数调优和模型构建等活动。攻击者通过数据中毒等攻击瞄准此阶段。如果模型是在受毒数据上训练的，您就不能依赖其预测结果。

您可以实施以下技术来降低训练阶段的攻击风险：

- 数据加密
- 保护训练数据的完整性
- 鲁棒统计
- 数据净化

## 测试阶段

在这个阶段，攻击者针对 ML 模型。模型提取攻击在攻击者中很常见。他们试图确定输入 X 是否属于训练数据的一部分，或试图窃取训练阶段定义的模型参数。

可以实施以下技术来降低测试阶段的风险：

- 对抗训练
- 自动编码器
- 蒸馏
- 集成技术
- 限制每个用户的请求数量

您可以使用 Python 库 Adversarial Robustness Toolbox (ART) 和命令行工具 Counterfit 来保障 ML 模型安全。该库将防御最常见的 ML 攻击类型。它还支持流行的 ML 框架、库和数据类型。

## A/B 测试

A/B 测试广泛应用于营销、网站设计和电子邮件活动中，以了解和掌握用户偏好。A/B 测试的目标是提高转化率、成功率、收入等。

A/B 测试涉及将总体中的受众或客户分成相等的集合。这些集合将路由到对照版本和实验版本。对照版本是现有版本，而实验版本是新版本或挑战者版本。首先，定义 A/B 测试的问题陈述、原假设和针对问题陈述的备择假设。接下来，设计实验以跟踪和分析指标，然后运行并验证实验。之后，比较输出的统计信息。最后，根据结果做出决策。如果 A/B 测试未正确执行，则其输出将不可靠。

数据科学家通过将数据分为训练集和验证集来对 ML 模型进行离线评估。然而，A/B 测试允许您通过衡量业务指标或成功率来对 ML 模型进行在线评估。当您在模型构建过程中对训练数据执行操作（例如缩放和归一化，或应用不同的算法和超参数）时，可以实施 A/B 测试。MLOps 工程师或数据科学家可以同时部署多个模型以在生产环境中测试模型。Google Cloud (GCP) 和 Amazon SageMaker 允许将多个模型部署到同一端点后面的生产环境中，以决定从业务角度来看哪个模型表现更好。

多臂老虎机 (MAB) 是 A/B 测试的高级版本。它比 A/B 测试更复杂，因为它使用 ML 算法，根据数据动态地将更多流量分配给表现更好的版本，将较少流量分配给表现不佳的版本。

## MLOps 是未来

机器学习领域正在蓬勃发展。各行业正将 ML 纳入业务开发流程的关键部分，ML 系统正在解决许多新挑战。

MLOps 可以处理 ML 模型的复杂性和可扩展性。因此，各行业对 MLOps 的需求正在增加。由于 MLOps 是机器学习与软件开发的交叉领域，行业内 MLOps 工程师短缺。公司需要为 MLOps 工程师设立独立团队，或者可以提升数据科学家的技能以执行 MLOps 任务。MLOps 可以降低成本并减少整个 ML 生命周期的手动工作量。这使得数据科学家和 ML 工程师能够专注于其他有价值的任务。

MLOps 正在比 DevOps 更受欢迎。您的模型在本地环境中可能表现良好；但是，如果它无法触达最终用户或客户，那么其业务影响就很低。超过 85% 的 ML 模型未部署到生产环境。MLOps 工程师可以填补研究环境与生产环境之间的差距。这是一个需求量很大的领域，因为仅靠数据科学家不足以将 ML 模型转化为业务价值。

## 结论

在本章中，您了解了模型安全的重要性，并研究了 ML 生命周期中的各种攻击。构建 ML 模型和 MLOps 解决方案还不够；数据科学家应致力于从中提供业务价值。在将现有模型与较新模型进行比较以改善整体结果和业务指标时，A/B 测试和多臂老虎机 (MAB) 起着至关重要的作用。最后，您了解了行业对 MLOps 需求的增加。

## 关键点

- 模型安全是 MLOps 的重要组成部分。
- A/B 测试使您能够对 ML 模型进行在线评估。
- 攻击者在尝试对抗性攻击时可以使用黑盒方法或白盒方法。
- 可以使用 Python 库 Adversarial Robustness Toolbox (ART) 和命令行工具 Counterfit 来保障 ML 模型安全。
- 多臂老虎机 (MAB) 是 A/B 测试的高级版本。它足够智能，可以通过评估多个模型来决定哪个模型应获得更多流量。

## 选择题

- 1. 在 ______ 中，攻击者故意向模型发送恶意数据，使模型做出错误预测。
  - a) 网络钓鱼
  - b) 对抗性攻击
  - c) 偷窥
  - d) 尾随

- 2. __________ 是指通过逆向工程从训练好的模型中获取训练数据信息的行为。
  - a) 提取
  - b) 规避
  - c) 反演
  - d) 监控

## 答案

- 1. b
- 2. c

## 问题

- 1. 什么是数据中毒攻击？
- 2. 什么是 A/B 测试？
- 3. 可以实施哪些不同的技术来降低训练阶段的模型安全风险？

## 加入我们书籍的 Discord 空间

加入本书的 Discord 工作区，获取最新动态、优惠、全球技术动态、新版本发布以及与作者的会议：

https://discord.bpbonline.com

![](img/cc4299656808e62a294f1843a1e18e72_450_0.png)

## 索引

### 符号

__init__ 方法 9

### A

- A/B 测试 423, 424
- 激活 Cloud Shell 图标 313
- Adversarial Robustness Toolbox (ART) 423
- Amazon CloudWatch 容器详细监控 378
- Amazon Elastic Compute Cloud (EC2) 327
- Amazon Elastic Container Registry (ECR) 327, 336, 337
- Amazon Elastic Container Service (ECS) 327, 346
  - 集群 347
  - 容器 347
  - 服务 347
  - 任务 346
  - 任务定义 346, 349
- Amazon Elastic Kubernetes Service (EKS) 327
- Amazon SageMaker 328
- Amazon Simple Storage Service (S3) 328
- Amazon Virtual Private Cloud (Amazon VPC) 351, 352
- Amazon Web Services (AWS) 326
- Anaconda 安装 2
- 应用负载均衡器 (ALB) 352, 358-362
- 数组 4
- AWS 账户设置 329, 330
- AWS 应用负载均衡器 (ALB) 327
- AWS CodeBuild 339-344
  - 容器仓库访问权限，附加到服务角色 345, 346
- AWS CodeCommit 331-335
- AWS CodePipeline 371, 372
  - 生成阶段，添加 374
  - 部署阶段，添加 375, 376
  - 监控 378
  - 运行 376-378
  - 设置 372
  - 源阶段，添加 373, 374
- AWS 命令行界面 (CLI) 330
- AWS 计算服务 326, 327
- AWS ECS 部署模型 347
  - EC2 实例 347, 348
  - Fargate 348, 349
- AWS Fargate 328
- AWS Lambda 328
- Azure 250, 251
  - 部署，使用 GitHub Actions 251-253
  - 基础设施设置 263
- Azure 账户
  - 设置 251
- Azure 应用服务
  - 配置，用于使用 GitHub Actions 进行持续交付 274-278
  - 创建 267-270
- Azure 容器实例 (ACI) 289, 292, 297
- Azure 容器注册表 (ACR) 252, 263
  - 创建 264-267
- Azure Kubernetes 服务 (AKS) 250, 292
- Azure 机器学习 (AML) 服务 249, 279
- Azure 机器学习 Studio
  - 实验 280
  - 功能 279
  - 运行 280-289
  - 工作区 280

### C

- CD 管道
  - 配置 292-298
- CI/CD 管道
  - 构建 189
  - 代码库，开发 189-196
  - 使用 Jenkins 创建 202
  - 用于 ML 184, 185
  - 使用 GitHub Actions 和 Heroku 227
  - 个人访问令牌 (PAT)，在 GitHub 上创建 196
  - 使用 Cloud Build 317, 318
  - 使用 CodePipeline 369, 370
  - Webhook，在 GitHub 仓库中创建 197, 198
- CI/CD 管道，使用 Jenkins 202
  - 部署状态电子邮件 210-217
  - GitHub 到容器 203-205
  - 测试 207-210
  - 训练 205-207
- CI 管道
  - 配置 290-292
- 类 9
- Cloud Alert 管理器 401
- Cloud Build 309-311
  - 触发器，创建 318-322
- Cloud Source 代码库 304-308, 317
- CloudWatch 日志 345





### D
- CodeBuild 339
- 代码编辑器
  - 安装 3
- 容器注册表 311, 312
- 持续交付 (CD) 186
- 持续部署 186
- 持续集成 (CI) 185, 186, 339
- 持续训练 (CT) 186, 336
- 控制语句和循环
  - for 循环 6, 7
  - if...else 6
  - pass 语句 8
  - while 循环 7
- 跨源资源共享 (CORS) 191, 229, 254
- CSV 文件
  - 加载 15
  - 保存 15
- 数据隐私攻击
  - 输入推断攻击 422
  - 成员推断攻击 422
  - 模型提取攻击 422
- 数据结构 4
  - 数组 4
  - 字典 4
  - 列表 4
  - 集合 5
  - 字符串 5
  - 元组 5
- 字典 4
- 分布式版本控制系统 (DVCS) 18
- Docker 112
  - 分离模式 118
  - 环境，设置 113
  - Hello World 示例 116
  - 安装 113
  - 旧版本，卸载 113, 114
- Docker 命令 127
- Docker Compose 115
- Docker 容器
  - ML 模型，部署 122-127
  - 运行 120, 121
- Docker 引擎
  - 安装 114
- Dockerfile
  - 创建 119, 120
- Docker Hub 速率限制 337-339
- Docker 镜像
  - 构建 120
- Docker 对象
  - Docker 容器网络 118
  - Docker 容器 118
- Dockerfile 117
- Docker 镜像 117
- 域名系统 (DNS) 370
- 漂移，在机器学习中 386
  - 应对 389
  - 概念漂移 387, 388
  - 数据漂移 387
  - 数据质量问题 389
  - 检测技术 388, 389
  - 模型，重建 389
  - 模型，重新训练 389
  - 模型，调优 389
  - 类型 386
- DRY (不要重复自己) 原则 41

### E
- EC2 (弹性计算云) 347
- ECS 服务
  - 自动伸缩 367
  - 配置，审查 367-369
  - 配置 363, 364
  - 创建 363
  - 网络，配置 365-367
- 弹性容器注册表 (ECR) 370
- 环境变量
  - 包，构建 71
  - 包，安装 71, 72
  - 包用法，示例 73, 74
  - 路径，添加 70
  - 设置 70
- Excel 文件
  - 加载 15
  - 保存 15
- 外部 Alert Manager 401

### F
- FastAPI 131-139
- Flask 143-150
- for 循环 6, 7
- 函数即服务 (FaaS) 328
- 函数 8

### G
- GCP 账户
  - 设置 303, 304
- GCP Cloud Shell
  - 使用，用于部署 316
- GCP 平台
  - URL 303
- Git 17, 18
  - 配置 22
  - 文件，添加 23-26
  - GUI 客户端 20
  - 安装 20
  - 安装，适用于所有平台 20
  - 安装，在 Linux 中 20
  - 状态，检查 22
  - 工作流 19
- Git 命令
  - 更改 21, 22
  - 新仓库 21
  - 撤销 22
  - 设置 21
  - 更新 21
- GitHub 17, 19
  - GitHub 账户
    - 创建 20, 21
  - GitHub Actions 225-270
    - 配置 226
    - 服务主体 273
  - Git 仓库
    - 初始化 22
- GNU 隐私保护 (GPG) 114
- Google Cloud Platform (GCP) 302
  - 服务 302, 303
- Google Kubernetes Engine
  - (GKE) 302, 313, 314
    - deployment.yaml 314
    - service.yaml 315
- Grafana 390
- Grafana Alert Manager 401
- 图形用户界面 (GUI) 157
- Gunicorn 150

### H
- Hello World! 示例 3
- Heroku 219-221
  - 部署，使用容器注册表 225
  - 部署，使用 GitHub 仓库集成 222
  - 流水线流程 224
  - 设置 221
- Heroku 部署
  - 生产环境 224
  - 评审应用 223
  - 预发布 223
- Heroku Git
  - 使用部署 222

### I
- IAM 管理控制台 345
- if...else 语句 6
- iloc 14, 15
- 监控项 390

### J
- Jenkins 187
  - 配置 199-202
  - 安装 187-189

### K
- KivyMD 应用 173-178
- Kubernetes 312
- Kubernetes Engine API 313

### L
- 列表 4
- 负载均衡 352
  - 应用负载均衡器
    - (ALB) 358-362
  - 安全组 356-358
  - 目标组 353-356
- loc 14

### M
- 方法 9
- MICE 算法 59
- Microsoft Azure 250
- 机器学习即服务 (MLaaS) 250
- ML 应用
  - 构建，使用 Kivy 和 KivyMD 170-173
  - 构建，使用 Tkinter 160-162
- MLflow 78
  - 组件 82
  - 环境，设置 79
  - 安装 79
  - Miniconda 安装 79-81
  - 场景 78, 79
- MLflow 项目 94-97
- MLflow 模型 97-100
- MLflow 注册表 100, 101
  - 功能 102, 103
- MLflow 服务器，启动 103-108
- MySQLdb 模块，安装 102
- MySQL 服务器，设置 101
- MLflow 跟踪 83
  - 制品 84
  - 记录数据，到运行中 84-94
  - 指标 83
  - 参数 83
  - 源 83
  - 开始和结束时间 83
- ML 生命周期 30
  - 业务影响 31
  - 数据收集 31, 32
  - 数据准备 32
  - 特征工程 32, 33
  - 模型构建 33
  - 模型部署 34
  - 模型评估 34
  - 模型测试 34
  - 模型训练 33
  - 监控 35
  - 优化 35

- ML 模型
  - 部署，使用 Azure DevOps 和 Azure ML 278, 279
  - 反序列化 48
  - 弥合与业务价值创造之间的差距 420
  - 生产化后 419
  - 需求文件 47, 48
  - 序列化 48
  - 虚拟环境 46, 47
- ML 模型攻击
  - 风险缓解 423
- ML 监控
  - 约束，用于数据质量验证 404-407
  - 功能监控 383
  - 基础 383-385
  - 指标 385, 386
  - 指标跟踪 383, 384
  - 运营监控 383
  - 可扩展集成 383
  - 使用 whylogs 和 WhyLabs 402
- MLOps 39, 40
  - 自动化 41
  - 优势 40
  - 高效管理 41
  - 功能 424
  - 可重复性 41
  - 跟踪和反馈循环 42
- ML 包
  - 业务问题 52
  - classification_v1.pkl 65
  - 配置模块 55, 56
  - 数据 52
  - data_management.py 57
  - 开发 51, 53
  - __init__.py 模块 54
  - MANIFEST.in 文件 54, 55
  - ML 模型，构建 53
  - pipeline.py 62
  - predict.py 模块 63
  - preprocessors.py 58-62
  - pytest.ini 68
  - requirements.txt 64
  - sdist 70
  - setup.py 66
  - test_predict.py 68-70
  - train_pipeline.py 65
  - 版本 68
  - wheel 70
- 模型部署 35
  - 批量预测 35
  - 移动和边缘设备 36, 37
  - 实时预测 37
  - Web 服务/REST API 36
- 模型部署挑战，在生产环境中
  - 数据相关挑战 38
  - 可移植性 38
  - 鲁棒性 38, 39
  - 可扩展性 38
  - 安全性 39
  - 团队协调 37, 38
- 模型安全 420, 421
  - 对抗攻击 421
  - 数据投毒攻击 422, 423
  - 数据隐私攻击 422
  - 分布式拒绝服务攻击 (DDoS) 422
  - 监控 382, 383
  - 多臂老虎机 (MAB) 424

### N
- 网络负载均衡器 (NLB) 327
- NGINX 150-154
- NumPy 10
  - NumPy 数组 10
    - 重塑 12

### O
- 对象 9
- 面向对象编程 (OOP) 9
  - 类 9
  - __init__ 方法 9
  - 方法 9
  - 对象 9
  - self 9
- 运营监控
  - 使用 Prometheus 和 Grafana 390-401

### P
- Pandas 12
  - Pandas DataFrame
    - 使用 12, 13
- pass 语句 8
- 个人访问令牌 (PAT) 196
- 个人健康信息 (PHI) 422
- 个人身份信息 (PII) 422
- 平台即服务 (PaaS) 219, 250
- prod.workflow.yml 270-272
- Prometheus 390
- pytest fixtures 49
- Python
  - 安装 2
  - 安装，在 Mac OS 上 2
  - 安装，在 Linux 上 2
  - 安装，在 Windows 上 2
  - Python 101 1
  - Python 应用
    - 转换，为 Android 应用 179, 180
  - 基于 Python 的 Tkinter 应用
    - 转换，为 Windows EXE 文件 167-169
  - Python 代码
    - 测试，使用 pytest 48, 49
  - Python 文件
    - 执行 3
  - Python 包索引 (PyPI) 3
  - Python 打包
    - 和依赖管理 49
    - 模块化编程 50
    - 模块 50
    - 包 50, 51

### R
- 表述性状态转移 (REST) 130
- REST API 130
- 机器学习模型攻击的风险缓解
  - 测试阶段 423
  - 训练阶段 423

### S
- 服务主体 (自动) 282
- 集合 5
- src 目录
  - docker-compose.yml 234, 259
  - Dockerfile 234, 259
  - .gitignore 229, 253
  - main.py 229-232, 254-257
  - production.yml 239-243
  - pytest.ini 235, 260
  - requirements.txt 258
  - requirements.txt 文件 233
  - runtime.txt 235, 260
  - start.sh 235, 260
  - test.py 235, 236, 260, 261
  - tox.ini 237, 262, 263
  - workflow.yml 238
  - workflow.yml 工作流 244-246
- 预发布 241
- Streamlit 139-143
- 字符串 5

### T
- 任务定义 349, 350
- 任务，运行 350
- 微型机器学习 (TinyML) 36
- Tkinter 158
  - 功能 160
  - Hello World 应用 159
  - ML 应用，构建 160-162
- Tkinter 应用 163-167
- 工具命令语言 (TCL) 158
- 元组 5

### V
- 虚拟机 (VM) 250
- 虚拟私有云 (VPC) 303

### W
- Web 服务器网关接口 (WSGI) 143
- while 循环 7
- WhyLabs 402, 407
  - 访问令牌 408
  - 功能 402
  - 通知页面 408
  - 输出选项卡 415, 416
  - 配置文件选项卡 414
  - 项目管理 407, 408
  - 用户管理 409-413
- whylogs 403, 404





## 机器学习生产环境部署

### 描述

《机器学习生产环境部署》是一本试图破解在 MLOps 领域开辟非凡职业生涯之路的著作。它是一本管理从开发到部署的机器学习生命周期的全面指南，阐述了如何在生产环境中部署 ML 模型的方法。

它从基础概念、ML 生命周期和 MLOps 介绍开始，随后提供从零开始开发可使用 pip 安装的 ML 代码包的全面分步说明。接着介绍了用于 ML 生命周期管理的 MLflow、CI/CD 流水线，并演示了如何在 Azure、GCP 和 AWS 上部署 ML 应用程序。此外，它还提供了如何将 Python 应用转换为 Android 和 Windows 应用，以及如何开发 ML Web 应用的指导。最后，它涵盖了监控、机器学习攻击这一关键主题以及 A/B 测试。

有了这本书，你可以轻松构建并部署生产环境的机器学习解决方案。

### 主要特性

- 探索使用自动化 CI/CD 流水线在生产环境中构建和部署 ML 模型的多种方式。
- 开发并将 ML 应用转换为 Android 和 Windows 应用。
- 了解如何在 Azure、GCP 和 AWS 等流行的云平台上实现 ML 模型部署。

### 你将学到的内容

- 掌握使用 MLOps 管理机器学习生命周期。
- 了解大规模管理 ML 模型的最佳实践。
- 使用 MLflow 简化 ML 工作流。
- 使用 whylogs、WhyLabs、Grafana 和 Prometheus 实现监控解决方案。
- 使用 Docker 和 Kubernetes 进行 ML 部署。

### 本书适合人群

无论你是数据科学家、ML 工程师、DevOps 专业人员、软件工程师还是云架构师，这本书都能帮助你快速高效地将机器学习模型投入生产。


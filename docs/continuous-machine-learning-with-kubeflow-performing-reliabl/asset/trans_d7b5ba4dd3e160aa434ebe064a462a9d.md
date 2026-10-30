
## 5. 机器学习模型可解释性与可解释性
## 结构
## 目标
### 5.1 问题
### 5.2 Shap 背后的总体思路和概念
### 5.3 在 Colab 中开始使用 Python 库安装和数据加载
### 5.4 用于训练模型的特征转换
### 5.5 LightGBM 模型训练
### 5.6 使用 Shap 工具进行高级可视化的模型分析
### 5.6.1 基本决策图特征
### 5.6.2 强制图分析
### 5.7 TensorFlow Estimator 模型框架构建
### 5.7.1 TensorFlow Estimator 模型
### 5.8 使用 Tensorboard 和 What-IF 工具对 TensorFlow 模型进行高级可视化
### 5.8.1 Tensorboard
### 5.8.2 What-If 工具
### 5.9 结论
### 5.10 参考文献
## 6. 构建 Weights & Biases 管道开发
## 结构
## 目标
### 6.1 问题陈述
### 6.2 在 GCP 和 Wandb 中设置项目需求
### 6.2.1 GCP 中的 Kubeflow 集群和 Docker 设置
### 6.2.2 用于下载数据的 Kaggle API 设置
### 6.2.3 Weights & Biases API 密钥
### 6.3 如何使用 Weights & Biases 的介绍
### 6.4 为股票数据建模和训练 LightGBM 模型
### 6.4.1 获取最新版本的 Weights & Biases 依赖项和 Kaggle 设置
### 6.4.2 Weights & Biases 依赖项和 Kaggle API 设置
### 6.4.3 数据加载和提取
### 6.4.4 探索性数据分析
### 6.4.4 实用指标函数
### 6.4.5 使用 LightGBM 框架训练模型（使用 Weights & Biases）
### 6.5 使用 KF Serving 提供模型服务
### 6.6 使用 Grafana 仪表板监控性能
### 6.7 结论
### 6.8 参考文献
## 7. 使用 AWS SageMaker 的应用机器学习
## 结构
## 目标
### 7.1 问题
### 7.2 开始 AWS SageMaker 设置
### 7.3 开始使用 JupyterLab Notebook 实例和 SDK 及 S3 存储桶
### 7.3.1 创建一个 S3 存储桶
### 7.3.2 创建 Amazon SageMaker Notebook 实例
### 7.4 通过启动 Notebook 并将数据加载到 S3 开始
### 7.5 加载、分析和转换训练数据
### 7.5.1 从 S3 和库加载数据
### 7.5.2 特征工程
### 7.5.2.1 查找分类和数值列
### 7.5.2.2 检查缺失值总和
### 7.5.2.3 因变量的对数转换
### 7.5.2.4 相关性与散点图
### 7.5.2.5 异常值检测
### 7.5.3 特征转换
### 7.6 Amazon SageMaker 训练模型
### 7.6.1 将数据拆分为训练/验证集并推送到 S3
### 7.6.2 使用维护算法容器的 SageMaker API XG-Boost 进行训练
### 7.7 Amazon SageMaker 模型部署
### 7.8 结论
### 7.9 参考文献
## 8. 使用 Streamlit 和 Heroku 进行 Web 应用开发
## 结构
## 目标
### 8.1 问题陈述
### 8.2 在 GCP 和 Heroku 中设置项目需求
### 8.3 Streamlit 组件介绍
### 8.3.1 主要概念
### 8.4 为 OpenCV 模型构建 Streamlit 框架
### 8.5 创建 Heroku 部署的组件
### 8.6 通过在 Kubernetes 集群中容器化部署 Streamlit 代码
### 8.7 摘要
### 8.8 参考文献
## 索引
## Kubeflow 和 Kubernetes 云架构介绍

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

### 1.1 Docker 理解

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


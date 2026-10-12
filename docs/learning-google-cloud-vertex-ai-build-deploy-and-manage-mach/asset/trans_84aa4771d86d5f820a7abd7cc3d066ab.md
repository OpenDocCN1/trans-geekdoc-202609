

# 章节总结

在本章中，我们学习了流水线、Kubeflow 及其组件。我们介绍了如何使用 Kubeflow SDK 构建流水线，以及如何使用 GCP 的 AutoML 组件进行模型训练。我们还介绍了如何提交流水线以供运行，并通过可视化方式理解流水线和检查结果。

在下一章中，我们将使用 Kubeflow SDK 为自定义模型训练构建流水线。

## 问题

1.  基于什么构建的流水线可以在 Vertex AI 上执行？
2.  为什么代码中仅在自定义模型评估函数中提到了基础镜像信息？
3.  为什么我们需要在提交流水线之前对其进行编译？
4.  如果在排查错误后执行流水线，所有组件是否都将从头开始执行？

## 加入我们书籍的 Discord 空间

加入书籍的 Discord 工作区，获取最新动态、优惠、全球科技动态、新版本发布以及与作者的交流会议：

[https://discord.bpbonline.com](https://discord.bpbonline.com)

![Discord](images/fm1.png)

# 第 7 章：使用 Kubeflow 针对自定义模型的流水线

## 简介

在上一章中，我们使用 Kubeflow 处理了 GCP 的流水线。我们使用平台的 AutoML 构建了第一个用于模型训练的流水线。在本章中，我们将了解如何为自定义模型构建流水线并比较不同流水线的结果。我们还将了解 Vertex AI 流水线和 Kubeflow 流水线之间的一些差异。

## 结构

在本章中，我们将涵盖以下主题：

*   模型训练数据
*   额外权限
*   使用 Cloud Shell 创建 Workbench
*   流水线代码演练
*   流水线
*   流水线比较
*   资源删除

## 目标

在本章结束时，用户将能够使用 Kubeflow 为自定义模型构建流水线并比较不同流水线的结果。

## 模型训练数据

对于本练习，数据从 Kaggle 下载（链接如下），该数据集列在 CC0：公共领域许可下。在前几章中，我们使用 Cloud Storage 上传数据以训练模型；在本章中，数据被上传到 GCP 的 BigQuery，机器学习模型在其上进行训练。

[https://www.kaggle.com/datasets/arashnic/hr-ana](https://www.kaggle.com/datasets/arashnic/hr-ana)

请参阅[第 1 章](#ch01.xhtml) *Google Cloud Platform 基础* 中的 BigQuery 部分以上传数据。[图 1.43](#ch01.xhtml#fig1-43) 至 [1.47](#ch01.xhtml#fig1-47) 将帮助您将数据上传到 BigQuery。请参阅 [图 1.48](#ch01.xhtml#fig1-48) 运行一个小查询以检查数据上传是否成功。

要将数据上传到 BigQuery，请创建一个名为 `employee_data` 的数据集。在该数据集下，创建一个名为 `employee_promotion_data` 的表。在查询部分，使用查询 `select * from 'vertex-ai-gcp-1.employee_data.employee_promotion_data' limit 10` 来检查数据上传。[图 7.1](#ch07.xhtml#fig7-1) 显示了上传到 BigQuery 的数据：

![图 7.1：加载到 BigQuery 表中的数据](images/Figure_7.1.png)

在本章中，我们将使用 Kubeflow SDK 在 GCP 的 Vertex AI 组件上创建流水线。在流水线中，我们将使用 GCP 的 AutoML 组件进行模型训练。

## 额外权限

由于我们要从 BigQuery 获取数据，因此还需要向与 GCP Compute Engine 关联的服务账户授予额外权限。请按照以下步骤授予所需权限。

### 步骤 1：打开 IAM 和管理部分

按照 [图 7.2](#ch07.xhtml#fig7-2) 中提到的步骤，向与 GCP Compute Engine 关联的服务账户添加角色：

![图 7.2：GCP 的 IAM](images/Figure_7.2.png)

1.  点击 **IAM**。
2.  选择与项目关联的服务账户。
3.  点击 **修改主体**。

### 步骤 2：额外角色

按照 [图 7.3](#ch07.xhtml#fig7-3)、[7.4](#ch07.xhtml#fig7-4) 和 [7.5](#ch07.xhtml#fig7-5) 中提到的步骤，编辑 Compute Engine 服务账户的角色：

![图 7.3：编辑服务账户的角色](images/Figure_7.3.png)

1.  点击 **+ 添加其他角色** 并按照 [图 7.4](#ch07.xhtml#fig7-4) 中提到的步骤操作：

    ![图 7.4：添加 BigQuery 管理员角色](images/Figure_7.4.png)

2.  在 BigQuery 产品/服务下选择 **BigQuery 管理员** 角色。
3.  点击 **保存**。新角色将添加到服务账户，如下图所示：

    ![图 7.5：IAM 中可见添加到服务账户的新角色](images/Figure_7.5.png)

4.  与 Compute Engine 关联的服务账户将显示新角色。

## 创建 Workbench

在之前的所有章节中，我们都在 Workbench 上工作。《Vertex AI Workbench》和《自定义模型训练》指导了使用 GUI 方法创建 Workbench。请按照以下步骤从 Cloud Shell 创建 Vertex AI Workbench：

### 步骤 1：激活 Cloud Shell

按照 [图 7.6](#ch07.xhtml#fig7-6) 中所示的步骤激活 Cloud Shell 并输入以下命令：

![图 7.6：激活 Cloud Shell](images/Figure_7.6.png)

1.  点击 **Cloud Shell** 以激活它。
2.  在 Cloud Shell 中输入以下命令以创建 Workbench：

```
gcloud notebooks instances create kubeflow-custom-ml \
  --vm-image-project=deeplearning-platform-release \
  --vm-image-family=common-cpu-notebooks \
  --machine-type=n1-standard-4 \
  --location=us-central1-a
```

### 步骤 2：创建的 Workbench

创建的 Workbench 将列在 Vertex AI 的 Workbench 部分下，如 [图 7.7](#ch07.xhtml#fig7-7) 所示：

![图 7.7：Workbench 创建完成](images/Figure_7.7.png)

1.  新创建的 Workbench。
2.  点击 **打开 JUPYTERLAB**。

## 流水线代码演练

我们将使用 Python 3 笔记本文件来输入命令、创建流水线、编译和运行它。请按照以下步骤创建 Python 文件并输入本节给出的 Python 代码。

### 步骤 1：创建 Python 笔记本文件

Workbench 创建完成后，打开 JupyterLab 并按照 [图 7.8](#ch07.xhtml#fig7-8) 中提到的步骤创建 Python 笔记本文件：

![图 7.8：新启动器窗口](images/Figure_7.8.png)

1.  点击 **新启动器**。
2.  双击 **Python 3** 笔记本文件以创建一个。

从步骤 2 开始，在单独的单元格中运行给定的代码。

### 步骤 2：软件包安装

运行以下命令以安装 Kubeflow、Google Cloud Pipeline 和 Google Cloud AI Platform 软件包。（安装软件包需要几分钟）：

```
USER_FLAG = "--user"

!pip3 install {USER_FLAG} google-cloud-aiplatform==1.3.0 --upgrade
!pip3 install {USER_FLAG} kfp --upgrade
!pip install google_cloud_pipeline_components
```

### 步骤 3：内核重启

在下一个单元格中输入以下命令以重启内核。（用户也可以从 GUI 重启内核）：

```
import os

if not os.getenv("IS_TESTING"):
    import IPython
    app = IPython.Application.instance()
    app.kernel.do_shutdown(True)
```

### 步骤 4：启用 API

运行以下代码行以启用 API。我们过去常从 Cloud Shell 启用 API。这是从 Python 笔记本启用 API 的另一种方式（除 Cloud Resource Manager 外，所有其他 API 在前几章中已启用）：

```
!gcloud services enable compute.googleapis.com \
  containerregistry.googleapis.com \
  aiplatform.googleapis.com \
  cloudbuild.googleapis.com \
  cloudfunctions.googleapis.com \
  cloudresourcemanager.googleapis.com
```

如果所有 API 都成功启用，将打印成功消息，如 [图 7.9](#ch07.xhtml#fig7-9) 所示：

![图 7.9：API 成功启用](images/Figure_7.9.png)


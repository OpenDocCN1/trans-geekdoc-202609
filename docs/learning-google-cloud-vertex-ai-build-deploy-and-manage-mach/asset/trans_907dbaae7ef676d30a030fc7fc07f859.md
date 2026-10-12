

```python
os.environ['GOOGLE_APPLICATION_CREDENTIALS'] = r"E:\service_account_json\vertex-ai-gcp-1-a3973ca6a1fe.json"

project_ID = "vertex-ai-gcp-1"

endpoint_ID = "5530565477945835520"

location = "us-central1"

api_endpoint = "us-central1-aiplatform.googleapis.com"
```

# 调用函数

```python
inputs = [4287.69, 3997.44, 4260, 4121.03, 4333.33, 4616.41, 4088.72, 4638.46, 4212.31, 4226.67, 4167.69, 4274.36, 4597.95, 4350.77]

online_custom_models(project_ID, endpoint_ID, inputs, location, api_endpoint)
```

输出：

![](images/Figure_5.31.png)

图 5.31：已部署模型的预测

## 使用 Python SDK 提交训练作业

在前几章涵盖的所有练习中，我们主要在平台的图形用户界面上工作。现在让我们看看如何使用 Python 代码提交训练作业。

### 步骤 1：在 Jupyter Lab 上创建新的 Python 笔记本

按照以下步骤创建一个新的 Python 笔记本文件，如下图所示：

![](images/Figure_5.32.png)

图 5.32：Python 笔记本的创建

遵循对应的要点：

1.  点击新启动器，即 `+` 号。
2.  点击 Python 笔记本以创建一个。

### 步骤 2：用于启动训练作业的 Python 代码

#### 单元格 1

```bash
!pip3 install google-cloud-aiplatform --upgrade --user
```

```python
from google.cloud import aiplatform
from google.cloud.aiplatform import hyperparameter_tuning as hpt
```

#### 单元格 2

```python
worker_pool_details = [{
    "machine_spec": {
        "machine_type": "n1-standard-4"
    },
    "replica_count": 1,
    "container_spec": {
        "image_url": "gcr.io/vertex-ai-gcp-1/eye:v1"
    }
}]

metric_spec = {'accuracy': 'maximize'}  # 待优化的指标

# 需要优化的超参数
parameter_spec_list = {
    "n_estimators": hpt.DiscreteParameterSpec(values=[100, 125], scale=None),
    "max_depth": hpt.DiscreteParameterSpec(values=[5, 10, 15, 20], scale=None),
    "min_samples_split": hpt.DiscreteParameterSpec(values=[5, 10], scale=None),
    "min_samples_leaf": hpt.DiscreteParameterSpec(values=[5, 10], scale=None),
    "max_features": hpt.CategoricalParameterSpec(values=["auto", "sqrt"])
}
```

#### 单元格 3

```python
my_custom_job = aiplatform.CustomJob(
    display_name='eye_classification-sdk-job',
    worker_pool_specs=worker_pool_details,
    staging_bucket='gs://hpo_vertex-ai'
)
```

#### 单元格 4

```python
job_hyperparameter = aiplatform.HyperparameterTuningJob(
    display_name='eye_classification-sdk-job',
    custom_job=my_custom_job,
    metric_spec=metric_spec,
    parameter_spec=parameter_spec_list,
    max_trial_count=2,
    parallel_trial_count=1
)

job_hyperparameter.run()  # 启动超参数调优作业
```

在不同的单元格中输入前面给出的代码，如 [图 5.33](#ch05.xhtml#fig5-33) 所示：

![](images/Figure_5.33.png)

图 5.33：用于提交训练作业的 Python 代码

请参考对应的要点，以更好地理解每个单元格中代码的作用：

1.  安装并导入所需的包。即使我们在 GCP 上使用笔记本，`google-cloud-aiplatform` 也不会预装。
2.  定义硬件配置、待优化的指标和超参数列表。
3.  使用显示名称和其他详细信息定义自定义作业（如果需要在没有超参数优化的情况下启动自定义作业，则添加 `my_custom_job.run()` 以启动自定义模型训练）。
4.  将超参数步骤添加到上一步中定义的自定义作业训练中。
5.  点击链接。它将转到训练页面，如 [图 5.34](#ch05.xhtml#fig5-34) 所示：

    ![](images/Figure_5.34.png)

    图 5.34：训练成功完成

## 资源删除

所有计算资源都很昂贵。请遵循 [第 2 章](#ch02.xhtml) “模型取消部署和删除端点”下提到的步骤，以取消部署模型和删除端点。请遵循 [第 2 章](#ch02.xhtml) “模型删除”下提到的步骤，从注册表中删除模型。请遵循 [第 4 章](#ch04.xhtml) “资源删除”下提到的步骤，删除 Workbench 实例。

## 结论

在本章中，我们详细了解了自定义模型以及超参数调优。我们还介绍了如何使用 GUI 和 SDK 方法提交自定义模型进行训练，以及如何将训练好的模型导入模型注册表。

在下一章中，我们将开始使用 GCP 的管道。

## 问题

1.  如何在自定义作业中传递用于调优的参数？
2.  从 Python SDK 启动包含超参数调优的训练作业时，为什么需要定义自定义训练作业？
3.  如果我们使用 PyTorch 包训练模型，可以使用预构建容器进行训练吗？

## 加入我们书籍的 Discord 空间

加入书籍的 Discord 工作区，获取最新动态、优惠、全球科技动态、新版本发布和作者专场：

[https://discord.bpbonline.com](https://discord.bpbonline.com)

![](images/fm1.png)

# 第 6 章：管道和 Kubeflow 简介

## 简介

在前几章中，我们使用 Vertex AI 的 Workbench 通过 Vizer 训练了包含超参数调优的自定义模型。在本章中，我们将开始使用 Vertex AI 的管道。我们将了解什么是管道、什么是 Kubeflow、管道的组成部分，以及如何使用 Kubeflow 配置和运行 Vertex AI 管道。

## 结构

在本章中，我们将讨论以下主题：

*   什么是机器学习管道
*   机器学习管道的优势
*   Kubeflow 简介
*   Kubeflow 的组件
*   Kubeflow 的任务
*   模型训练数据
*   API 启用和额外权限
*   管道代码演练
*   Vertex AI 管道
*   资源删除

## 目标

在本章结束时，您将对机器学习 (ML) 管道、Kubeflow 及其组件有很好的理解。读者还将学习如何在 Vertex AI 上使用 Kubeflow 构建管道。

## 什么是机器学习管道

机器学习管道是一个用于管理 ML 模型（或多个模型集合）输入和输出的综合框架。它包含原始数据、特征和输出作为输入，以及机器学习模型及其参数和预测作为输出。

理解 ML 管道的另一种方式是：将大型机器学习操作分解为较小的、可重用的模块，这些模块可用于管道中以生成模型，这也是一种 ML 管道。通过消除不必要的步骤，ML 管道加快并简化了模型构建过程。

## Vertex AI 管道

Vertex AI 管道通过以无服务器方式编排 ML 工作流，并将该过程的工件存储在 Vertex ML Metadata 中，使自动化、监控和管理 ML 系统变得更加容易。通过在 Vertex ML Metadata 中跟踪 ML 工作流的输出，用户可以追溯制作每个工件（如 ML 模型的训练数据、超参数和代码）所经历的步骤。

管道用于应用 MLOps 方法来简化并跟踪您最常执行的任务。通过尝试超参数、训练步骤、迭代等的各种配置，试验您的机器学习过程。重用管道组件或整个管道来训练新模型。使用 Kubeflow SDK 或 TensorFlow Extended 构建的管道可以使用 Vertex AI 管道执行。

## 机器学习管道的优势

机器学习管道有多种优势：

### 执行


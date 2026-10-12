

# 用于模型检查的 What-If Tool (WIT)

您可以在笔记本环境中使用 What-If Tool (WIT)，通过交互式信息中心检查 AI Platform Prediction 模型。What-If Tool 可与 TensorBoard、Jupyter Notebook、Colab Notebook 和 JupyterHub 集成。它也预装在 Vertex AI Workbench 用户管理的笔记本和 TensorFlow 实例中。

要使用 WIT，您需要安装 `witwidget` 库，该库已预装在 Vertex AI Workbench 中。然后配置 `WitConfigBuilder` 以检查模型或比较两个模型。以下是用于检查模型的一些示例代码：

```
PROJECT_ID = 'YOUR_PROJECT_ID'
MODEL_NAME = 'YOUR_MODEL_NAME'
VERSION_NAME = 'YOUR_VERSION_NAME'
TARGET_FEATURE = 'mortgage_status'
LABEL_VOCAB = ['denied', 'approved']
config_builder = (WitConfigBuilder(test_examples.tolist(), features.columns.tolist() + ['mortgage_status'])
  .set_ai_platform_model(PROJECT_ID, MODEL_NAME, VERSION_NAME, adjust_prediction=adjust_prediction)
  .set_target_feature(TARGET_FEATURE)
  .set_label_vocab(LABEL_VOCAB)
```

然后将配置构建器传递给 `WitWidget`，并设置显示高度。

```
WitWidget(config_builder, height=800)
```

What-If Tool 会在您的笔记本中显示交互式可视化界面。请尝试此 Colab Notebook 以探索 What-If Tool 的工作原理：

`https://colab.research.google.com/github/pair-code/what-if-tool/blob/master/What_If_Tool_Notebook_Usage.ipynb`

## 重新训练/重新部署评估

模型在真实世界中训练并部署后，随着时间的推移，模型性能会发生变化；由于用户行为和训练数据随时间不断变化，您的模型对变化很敏感。尽管所有机器学习模型都会衰退，但衰退的速度随时间而异。这主要是由数据漂移、概念漂移或两者共同导致的。让我们来了解这些术语。

### 数据漂移

**数据漂移**是指生产数据的统计分布与用于训练或构建模型的基准数据的统计分布发生了变化。如果模型的特征归因发生变化，或者数据本身发生变化，则可以检测到数据漂移。例如，假设您使用从 IoT 传感器收集的华氏度温度数据构建了一个模型，但单位变成了摄氏度。这意味着输入数据发生了变化，因此数据发生了漂移。您可以通过检查特征分布或特征间的相关性，或使用监控系统检查相对于基准的数据架构来检测数据漂移。

### 概念漂移

**概念漂移**是一种现象，即您试图预测的目标变量的统计特性随时间发生变化。例如，假设您构建了一个模型来对围绕特定主题的 Reddit 信息流的正面和负面情绪进行分类。随着时间的推移，人们对这些主题的情绪会发生变化。属于正面情绪的推文可能会随着时间演变为负面情绪。

为了检测漂移，您需要监控已部署的模型，这可以通过 Vertex AI Model Monitoring 来完成。我们将在 [第 12 章](#c12.xhtml) “模型监控、跟踪和审核元数据” 中详细介绍此主题。

### 何时应重新训练模型？

根据 [表 8.7](#c08.xhtml#c08-tbl-0006) 确定重新训练策略。我们将在 [第 12 章](#c12.xhtml) 中讨论如何使用 Vertex AI Pipelines 和 Vertex AI Model Monitoring 设置重新训练。

**表 8.7** 重新训练策略

| 策略 | 说明 |
| :--- | :--- |
| 定期训练 | 您可以选择每周、每月或每年等间隔来重新训练模型。这取决于您的训练数据更新的频率。仅当基于间隔的模型重新训练与您的业务用例一致时才有意义。为模型重新训练选择随机周期可能会导致模型比之前的模型更差。 |
| 基于性能的触发器 | 如果模型性能低于您设定的阈值（即真实情况或基准数据），这将自动触发重新训练流水线。此方法假设您已在生产环境中实施了复杂的监控系统。 |
| 数据变更触发器 | 如果发生数据漂移，则应触发模型重新训练的构建。通常，生产环境中的模型性能变化会导致数据漂移。 |
| 按需重新训练 | 这是一种手动且传统的模型重新训练方式，采用传统技术。 |

## 模型训练和服务的单元测试

测试机器学习系统很难，因为代码、模型和数据都控制着系统的行为。测试 ML 模型意味着测试模型代码，以及测试数据和模型。单元测试允许我们测试代码单元是否按预期运行。

模型测试涉及对我们期望模型遵循的行为进行显式检查。测试使我们能够尽早发现一些 Bug。我们可以在不需要训练参数的情况下运行一些测试。这些测试包括以下内容：

*   检查模型输出的形状，并确保其与数据集中的标签一致。
*   检查输出范围，并确保其符合预期（例如，分类模型的输出应该是一个分布，其类别概率之和为 1）。
*   确保在一批数据上进行单步梯度下降会导致损失减少。
*   对数据集进行断言。
*   检查训练数据集和验证数据集之间是否存在标签泄露。

### 测试 API 调用的更新

您可以通过重新训练模型来测试 API 调用的更新，但这会消耗大量资源。相反，您可以编写一个单元测试来生成随机输入数据，并运行单步梯度下降以在无运行时错误的情况下完成。

### 测试算法正确性

要检查模型的算法正确性，请执行以下步骤：

1.  训练模型几次迭代，并验证损失是否减少。
2.  在没有正则化的情况下训练算法。如果模型足够复杂，它将记住训练数据，训练损失将接近 0。
3.  测试算法的特定子计算。例如，您可以测试 CNN 的某一部分是否针对输入数据的每个元素运行一次。

## 摘要

在本章中，我们讨论了各种文件类型，如结构化、非结构化和半结构化，以及它们如何在 GCP 中存储和摄取以用于 AI/ML 工作负载。我们将文件摄取到 Google Cloud Platform 的过程分为收集、处理、存储和分析等阶段，并讨论了每个阶段可提供帮助的服务。我们介绍了用于收集实时数据的 Pub/Sub 和 Pub/Sub Lite，以及用于将数据从第三方来源和数据库迁移到 Google Cloud 的 BigQuery Data Transfer Service 和 Datastream。在处理阶段，我们介绍了如何使用 Cloud Dataflow、Cloud Data Fusion、Cloud Dataproc、Cloud Composer 和 Cloud Dataprep 等服务转换数据。

然后我们讨论了如何使用 Vertex AI Training 训练模型。Vertex AI Training 支持 scikit-learn、TensorFlow、PyTorch 和 XGBoost 等框架。我们讨论了如何使用预构建容器和自定义容器训练模型。

我们还介绍了为什么以及如何对机器学习的数据和模型进行单元测试。

然后我们介绍了超参数调优以及 Google Cloud 中可用的各种超参数调优搜索算法，以及 Vertex AI Vizier 及其与超参数调优的区别。

您了解了如何使用 Vertex AI 交互式 Shell、TensorFlow Profiler 和 What-If Tool，通过 Vertex AI 指标跟踪和调试训练模型。

您还了解了数据漂移和概念漂移，以及何时应重新训练模型以避免漂移。

## 考试要点


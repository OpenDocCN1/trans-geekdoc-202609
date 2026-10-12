

# BigQuery Omni 和混合云

BigQuery Omni 允许您对存储在 Amazon S3 或 Azure Blob Storage 中的数据运行 BigQuery 分析。如果您想将 AWS 或 Azure 中的数据与 Google Cloud 区域中的数据进行关联，或者想利用 BigQuery ML 功能，请使用 `LOAD DATA` SQL 语句。此 SQL 语句可让您将数据从 BigQuery Omni 可访问的 S3 存储桶传输到 BigQuery 原生表中。

要在 Vertex AI 上训练自定义 ML 模型，Vertex AI 与 BigQuery 集成，您可以从 BigQuery Omni（S3、Azure 中的数据）访问数据，以使用 Vertex AI Training 训练 AutoML 或自定义 ML 模型。您也可以在数据上使用 BigQuery ML。

**混合云** 是指将私有计算环境（通常是现有的本地数据中心）和公共云计算环境相结合。

Anthos 是混合和多云的云现代化平台。以下列表包含 Anthos 支持混合 ML 开发的一些功能：

*   BigQuery Omni 由 Anthos 提供支持，您无需管理底层基础架构即可查询数据。
*   混合 AI 产品是 Speech-to-Text On-Prem，现已通过 Google Cloud Marketplace 在 Anthos 上正式发布。
*   您可以在本地运行 GKE，这意味着您可以使用 Anthos 为您的 ML 工作流设置 Kubeflow Pipelines。
*   您还可以通过 Anthos 在本地运行 Cloud Run 服务，这使您能够设置基于 API 的预训练 AI 服务。

## 摘要

在本章中，我们介绍了使用 Kubeflow、Vertex AI Pipelines、Apache Airflow 和 Cloud Composer 等工具对 ML 流水线进行编排。我们还介绍了所有这些工具之间的区别，以及何时为 ML 工作流自动化使用每一种工具。您了解到 Vertex AI Pipelines 是一种托管的无服务器方式来运行 Kubeflow 和 TFX 工作流，而您可以在 Google Kubernetes Engine 上的 GCP 上运行 Kubeflow。

然后我们介绍了使用 Kubeflow 和 Vertex AI Pipelines 调度 ML 工作流的方法。对于 Kubeflow，您将使用 Cloud Build 触发部署；而对于 Vertex AI Pipelines，您可以使用 Cloud Function 事件触发器来调度流水线。您也可以手动运行这些流水线。

我们介绍了使用 Kubeflow 和 TensorFlow 进行系统设计。在 Kubeflow Pipelines 中，您将每个任务创建为一个组件并编排这些组件。Kubeflow 自带 UI 和 TensorBoard 来可视化这些组件。您可以在 Kubeflow 上运行 TFX 流水线。对于 TFX，我们介绍了三个 TFX 组件和 TFX 库来定义 ML 流水线。要编排 ML 流水线，TFX 支持自带编排器或运行时。您可以使用 Cloud Composer、Kubeflow 或 Vertex AI Pipelines 来运行 TFX ML 工作流。

最后，我们介绍了*混合*和*多云*的高层定义。您了解了如何使用 BigQuery Omni 和 Anthos 在 GCP 上设置混合和多云环境。您可以使用 BigQuery Omni 连接器从 AWS S3 和 Azure 存储获取数据。您可以使用 Anthos 在 GKE 本地设置 Kubeflow Pipelines。

## 考试重点

*   **了解不同的编排框架。** 知道什么是编排框架以及为什么需要它。您应该知道什么是 Kubeflow Pipelines 以及如何在 GCP 上运行 Kubeflow Pipelines。您还应该了解 Vertex AI Pipelines 以及如何在 Vertex AI Pipelines 上运行 Kubeflow 和 TFX。还要了解 Apache Airflow 和 Cloud Composer。最后，对比所有四种用于自动化 ML 工作流的编排方法。

*   **识别这些框架上的组件、参数、触发器和计算需求。** 了解使用 Kubeflow 和 Vertex AI Pipelines 调度 ML 工作流的方法。对于 Kubeflow，了解如何使用 Cloud Build 触发部署。对于 Vertex AI Pipelines，了解如何使用 Cloud Function 事件触发器来调度流水线。

*   **了解 TFX/Kubeflow 的系统设计。** 了解使用 Kubeflow 和 TensorFlow 进行系统设计。理解在 Kubeflow Pipelines 中，您将每个任务创建为一个组件并编排这些组件。了解如何在 Kubeflow 上运行 TFX 流水线，以及如何使用 TFX 组件和 TFX 库来定义 ML 流水线。理解要使用 TFX 编排 ML 流水线，您可以使用任何运行时或编排器，如 Kubeflow 或 Apache Airflow。您也可以使用 Vertex AI Pipelines 在 GCP 上运行 TFX。

## 复习题

1.  您是一名数据科学家，正在构建一个包含 100 多个输入特征的 TensorFlow 模型，所有特征的值均在 -1 和 1 之间。您希望提供基于所有可用数据训练的模型，但在推向生产环境前，跟踪其在特定数据子集上的性能。执行此验证的最高效且最可靠的方法是什么？

    1.  使用 TFX ModelValidator 组件指定生产就绪的性能指标。
    2.  使用整个数据集，并将接收者操作特征曲线下面积 (AUC ROC) 作为主要指标。
    3.  使用 L1 正则化将无信息量特征的系数降为 0。
    4.  使用 k 折交叉验证作为验证策略，以确保模型已准备好投入生产。

2.  您的团队已使用 Kubeflow 开发了一个 ML 流水线来清理数据集并将其保存在 Google Cloud Storage 存储桶中。您创建了一个 ML 模型，并希望在新数据可用时立即使用该数据刷新模型。作为 CI/CD 工作流的一部分，您希望以最少的工作量和最托管的方式在 GCP 上自动运行 Kubeflow Pipelines 作业。您应如何设计此工作流？

    1.  配置 Cloud Storage 触发器，在存储桶中有新文件可用时向 Pub/Sub 主题发送消息。使用由 Pub/Sub 触发的 Cloud Function 启动 Vertex AI Pipelines。
    2.  使用 Cloud Scheduler 按固定时间间隔调度作业。对于作业的第一步，检查 Cloud Storage 存储桶中对象的时间戳。如果自上次运行以来没有新文件，则中止作业。
    3.  使用 App Engine 创建一个轻量级 Python 客户端，持续轮询 Cloud Storage 以查找新文件。文件一到达，即在 GKE 上启动 Kubeflow Pipelines 作业。
    4.  使用 Dataflow 配置您的流水线，将文件保存到 Cloud Storage。文件保存后，在 GKE 上启动作业。

3.  您创建了一个 ML 模型，并希望在 Google Cloud Storage 存储桶中有新数据可用时立即使用该数据刷新模型。作为 CI/CD 工作流的一部分，您希望以最少的工作量和最托管的方式在 GKE 上自动运行 Kubeflow Pipelines 训练作业。您应如何设计此工作流？

    1.  配置 Cloud Storage 触发器，在存储桶中有新文件可用时向 Pub/Sub 主题发送消息。使用由 Pub/Sub 触发的 Cloud Function 在 GKE 上启动训练作业。
    2.  使用 Cloud Scheduler 按固定时间间隔调度作业。对于作业的第一步，检查 Cloud Storage 存储桶中对象的时间戳，查看自上次运行以来是否有新文件。
    3.  使用 App Engine 创建一个轻量级 Python 客户端，持续轮询 Cloud Storage 以查找新文件。文件一到达，即在 GKE 上启动 Kubeflow Pipelines 作业。
    4.  使用 Dataflow 配置您的流水线，将文件保存到 Cloud Storage。文件保存后，您可以在 GKE 上启动作业。

4.  您是一家全球零售公司的 ML 工程师。您正在 Google Kubernetes Engine 上为推荐系统开发一个 Kubeflow 流水线。流水线的第一步是针对 BigQuery 发出查询。您计划将该查询的结果作为流水线中下一步的输入。选择两种创建此流水线的方法。


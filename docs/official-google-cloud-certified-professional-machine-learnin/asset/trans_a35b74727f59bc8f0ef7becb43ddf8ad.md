

# 机器学习工作流与流水线编排

机器学习工作流定义了在机器学习项目期间实施的各个阶段。典型阶段包括数据收集、数据预处理、构建数据集、模型训练与优化、评估以及部署到生产环境。要在生产环境中集成 ML 系统，您需要编排 ML 流水线中的各个步骤。此外，您还需要实现流水线的自动化执行，以便对模型进行持续训练。

ML 流水线用于连接 ML 解决方案的各个步骤。`Kubeflow` 是一个机器学习工具包，它提供了一个名为 `Kubeflow Pipelines` 的流水线解决方案，构建在 `Kubernetes` 之上。Google 推出了 `Vertex AI Pipelines`，因为维护 `Kubernetes` 可能具有挑战性且耗时。它是一个用于运行流水线的无服务器产品，因此您的机器学习团队可以专注于他们的本职工作：ML。

## 使用 Vertex AI Pipelines 编排 ML 工作流

`Vertex AI Pipelines` 是一项托管服务，它通过以无服务器方式编排您的 ML 工作流并使用 `Vertex ML Metadata` 存储工作流的工件，帮助您自动化、监控和治理 ML 系统。通过将 ML 工作流的工件存储在 `Vertex ML Metadata` 中，您可以分析工作流工件的血缘关系，例如用于创建模型的训练数据、超参数和代码。`Vertex AI Pipelines` 可以运行使用 `Kubeflow Pipelines SDK` v1.8.9 或更高版本或 `TensorFlow Extended` v0.30.0 或更高版本构建的流水线。

对于 `TensorFlow`，请使用 `TensorFlow Extended` 来定义您的流水线及每个步骤的操作，然后在 `Vertex AI` 的无服务器流水线系统上执行它。

对于所有其他框架，请将 `Kubeflow Pipelines` 与 `Vertex AI Pipelines` 结合使用。使用 `Vertex AI` 来启动平台并与其交互。

这会产生两个结果：

*   您可以使用流水线，而无论您选择哪种 ML 环境。
*   您只需要少量配置适度 CPU 和内存的节点，因为大部分工作将在托管服务中完成。

## 使用 Kubeflow Pipelines 进行灵活的流水线构建

`Kubeflow` 是一个开源 `Kubernetes` 框架，用于开发和运行可移植的 ML 工作负载。`Kubeflow Pipelines` 是一项 `Kubeflow` 服务，可让您组合、编排和自动化 ML 系统。您可以选择在本地、本地部署或云环境（如 `Google Cloud` 或其他云平台）中部署 `Kubernetes` 工作负载。`Kubeflow Pipelines SDK` 推荐给大多数想要编写托管流水线的用户。`Kubeflow Pipelines` 灵活多变，让您可以使用简单的代码构建流水线，并提供 `Google Cloud Pipeline Components`，允许您在流水线中包含 `AutoML` 等 `Vertex AI` 功能。

`Kubeflow Pipelines` 通过执行所需的 `Google Cloud` 服务，让您能够编排和自动化生产级 ML 流水线。在[图 5.2](#c05.xhtml#c05-fig-0002) 中，`Cloud SQL` 作为 `Kubeflow Pipelines` 的 ML 元数据存储。

![FIGURE 5.2 Kubeflow Pipelines and Google Cloud managed services](images/c05f002.png)

[**图 5.2**](#c05.xhtml#R_c05-fig-0002) Kubeflow Pipelines 和 Google Cloud 托管服务

`Kubeflow Pipelines` 组件不仅限于在 `Google Cloud` 上执行 `TensorFlow Extended (TFX)` 相关服务。这些组件可以执行用于 `Spark` ML 作业的 `Dataproc`、`AutoML` 和其他计算工作负载。

## 使用 TensorFlow Extended SDK 利用预构建组件处理常见步骤

`TensorFlow` 为 `Vertex AI` 工作流中的常见步骤（如数据摄取、数据验证和训练）提供预构建组件。`TFX` 提供了一系列框架、库和组件，用于在生产环境中定义、启动和监控机器学习模型。如果满足以下任一条件，建议使用 `TensorFlow Extended SDK`：

*   您已经在使用 `TensorFlow`。
*   您使用结构化数据和文本数据。
*   您处理大量数据。

我们在[第 3 章](#c03.xhtml)“特征工程”中介绍了 `TFX` 流水线的 `Google Cloud` 实现。另请参阅此页面：

`https://neptune.ai/blog/deep-dive-into-ml-models-in-production-using-tfx-and-kubeflow`

## 何时使用哪种流水线

`Vertex AI Pipelines` 可以运行使用 `Kubeflow Pipelines SDK` v1.8.9 或更高版本或 `TensorFlow Extended` v0.30.0 或更高版本构建的流水线。

如果您在处理 TB 级结构化数据或文本数据的 ML 工作流中使用 `TensorFlow`，我们建议您使用 `TFX` 构建流水线。默认情况下，`TFX` 会创建 ML 流水线的有向无环图 (DAG)。它在底层使用 `Apache Beam` 来管理和实现流水线，并且可以轻松地在 `Apache Spark`、`Google Cloud Dataflow` 和 `Apache Flink` 等分布式处理后端上执行。

虽然在 `Cloud Dataflow` 上运行 `Apache Beam` 的 `TFX` 很酷，但配置、监控和维护已定义的流水线和工作流却很困难。这催生了我们称为*编排器*的工具。

像 `Kubeflow` 这样的编排器使配置、操作、监控和维护 ML 流水线变得容易。它们大多附带易于理解的 GUI。您可以使用 `Kubeflow Pipelines` 来调度和编排 `TFX` 流水线。

对于其他用例，我们建议您使用 `Kubeflow Pipelines SDK` 构建流水线。

虽然您可以考虑其他编排器，如 `Cloud Composer`（请参阅 Apache `Airflow`），但 `Vertex AI Pipelines` 是更好的选择，因为它内置了对常见 ML 操作的支持，并跟踪特定于 ML 的元数据和血缘关系。血缘关系对于验证流水线在生产环境中是否正常运行尤为重要。

# 服务

在训练、评估和调优机器学习 (ML) 模型后，该模型将被部署到生产环境以进行预测。ML 模型可以通过两种方式提供预测：离线预测和在线预测。

## 离线或批量预测

当您以批次形式获取数据并运行指向已训练模型的批处理作业以进行离线预测时，您执行的是离线或批量预测。离线或批量处理的一些用例包括推荐、需求预测、细分分析，以及对大批量文本进行分类以确定其所属主题。您可以使用 `Vertex AI batch prediction` 为存储在 `BigQuery` 或 `Google Cloud Storage` 中的数据运行批量预测作业。

[图 5.3](#c05.xhtml#c05-fig-0003) 展示了在 `Google Cloud` 上执行离线批量预测的典型高层架构。

![FIGURE 5.3 Google Cloud architecture for performing offline batch prediction](images/c05f003.png)

[**图 5.3**](#c05.xhtml#R_c05-fig-0003) 用于执行离线批量预测的 Google Cloud 架构

## 在线预测

当您向已部署的模型端点发送请求并获得预测响应时，这种预测会近乎实时地发生。这可以是一个部署到 HTTPS 端点的模型，您可以使用微服务架构从 Web 应用程序或移动应用程序调用此端点。在进行 ML 预测时需要近乎实时响应的用例包括实时竞价和对 Twitter 源的实时情感分析。

有两种方式可以进行在线预测，具体说明如下：

*   **同步** 在这种方式中，调用者会等待，直到从 ML 服务接收到预测，然后再执行后续步骤。您可以使用 `Vertex AI online predictions` 将模型部署为实时 HTTPS 端点。您还可以使用 `App Engine` 或 `GKE` (`Google Kubernetes Engine`) 作为 ML 网关，在从客户端应用程序发送请求之前执行一些特征预处理，如[图 5.4](#c05.xhtml#c05-fig-0004) 所示。

    ![FIGURE 5.4 Google Cloud architecture for online prediction](images/c05f004.png)

    [**图 5.4**](#c05.xhtml#R_c05-fig-0004) 用于在线预测的 Google Cloud 架构


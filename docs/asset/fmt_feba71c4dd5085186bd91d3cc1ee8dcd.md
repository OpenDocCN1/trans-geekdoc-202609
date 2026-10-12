
```python
pipeline_run_rf = pipeline_jobs.PipelineJob(
    display_name="employee_promotion_ml_pipeline_rf",
    template_path="employee_promotion_prediction_rf.json",
    enable_caching=True,
    location=REGION,
)
```

### 步骤 14：提交流水线作业

运行以下代码以提交流水线作业。代码执行后将提供链接，用于查看流水线，如图 7.10 所示：

```python
pipeline_run_rf.run()
```

![](img/Figure_7.10.png)

**图 7.10：** 笔记本文件中的流水线链接

1. 提交流水线作业后，将提供一个链接以检查流水线的状态。点击它。

## 流水线

请遵循以下步骤来分析流水线作业、工件、谱系和输出的状态：

### 步骤 1：自定义模型的流水线

打开图 7.10 中所示的链接，导航至 Vertex AI 的流水线。流水线将开始执行，大约需要 5 到 10 分钟。练习中的所有四个任务将按顺序执行。流水线完全执行完毕后，您将看到所有组件上都有绿色的勾号，如图 7.11 所示：

![](img/Figure_7.11.png)

**图 7.11：** 流水线创建并成功执行

1. 表示流水线中的所有步骤均已成功执行。

2. 点击流水线的 `SUMMARY（摘要）` 部分。

3. 基本信息提供流水线运行、区域、查看日志的链接等信息。

4. 运行参数提供流水线所用参数的相关信息。向下滚动可在摘要部分获取运行指标。

5. 点击切换按钮以展开工件。

### 步骤 2：展开工件

工件将在流水线中展开，如图 7.12 所示：

![](img/Figure_7.12.png)

**图 7.12：** 流水线的组件和工件

1. 带有勾号的方框表示流水线的组件。其他的则是流水线的工件。点击它们。

2. 点击 `NODE INFO（节点信息）`。

3. 存储工件的云存储位置。

4. 点击 `VIEW LINEAGE（查看谱系）`。

### 步骤 3：流水线的谱系

当您使用 Vertex AI Pipelines 执行流水线时，流水线运行的工件和参数会记录在 Vertex ML Metadata 中。Vertex ML Metadata 通过免除用户维护流水线信息的负担，便于分析项目的来源。制作工件所用的一切，以及任何衍生对象或信息，都是其谱系的一部分。

流水线的谱系将在单独的标签页中打开，如图 7.13 所示：

![](img/Figure_7.13.png)

**图 7.13：** 流水线的谱系

### 步骤 4：流水线中记录的指标和 KPI

训练模型的指标将在工件中提供，如图 7.14 所示：

![](img/Figure_7.14.png)

**图 7.14：** 模型的指标

1. 点击流水线的指标工件。

2. 在流水线的最后一个组件中，我们记录了混淆矩阵和 ROC 曲线（向下滚动查看）。

训练模型的 KPI 将在工件中提供，如图 7.15 所示：

![](img/Figure_7.15.png)

**图 7.15：** 模型的 KPI

1. 点击流水线的 KPI 工件。

2. 在流水线的最后一个组件中，我们记录了模型的准确率和其他 KPI，这些指标将显示出来。

### 步骤 5：存储在云存储中的流水线工件

流水线工件存储在云存储中，如下图所示。为流水线不同组件的工件创建了单独的文件夹：

![](img/Figure_7.16.png)

**图 7.16：** 存储在云存储中的工件

## 流水线对比

用户可能会使用不同的模型或不同的数据样本运行多个流水线。GCP 为用户提供了对比不同流水线性能的选项。

在本练习中，我们构建了一个用于训练随机森林分类器模型的流水线。将随机森林更改为您选择的任何其他模型并运行流水线（决策树分类器可用于此场景，只需对代码进行最少的更改）。导入所需的包并在代码中进行必要的更改（流水线的第三和第四个组件）。更改 JSON 文件的名称和流水线名称。编译并提交流水线作业以执行。

流水线成功执行后，请遵循以下步骤对比流水线。

### 步骤 1：Vertex AI 的流水线模块

所有执行过的流水线都将列在流水线部分下，如图 7.17 所示：

![](img/Figure_7.17.png)

**图 7.17：** Vertex AI 的流水线模块

1. 转到 Vertex AI 的流水线模块。

2. 选择要对比的流水线。

3. 点击 `COMPARE（对比）`。

### 步骤 2：流水线对比

使用流水线对比，用户可以对比所用的流水线参数、流水线的输出指标和 KPI，如图 7.18 所示：

![](img/Figure_7.18.png)

**图 7.18：** 流水线对比

## 资源删除

我们使用了 Workbench、BigQuery 来存储数据，以及云存储来存储流水线的工件。请确保删除 Workbench，清除云存储和 BigQuery 中存储的数据。

## Vertex AI 与 Kubeflow 流水线的区别

下面列出了 Vertex AI 流水线与 Kubeflow 流水线之间的一些重要区别：

*   **领域特定语言 (DSL) 版本：** 使用 TFX v0.30.0 或更高版本以及 `Kubeflow Pipelines SDK v2` 领域特定语言 (DSL) 创建的流水线可以在 Vertex AI 流水线上执行。只有 `Kubeflow Pipelines SDK` 可用于 Kubeflow 流水线执行。

*   **存储：** Kubeflow Pipelines 可以使用持久卷声明等 Kubernetes 资源，而 Vertex AI 使用云存储进行数据存储（使用 Cloud Storage FUSE 挂载到组件）。

*   **递归：** Vertex AI 不支持递归调用的流水线组件，而 Kubeflow 支持。

## 结论

## 章节总结

我们学习了如何使用 Kubeflow SDK 构建使用自定义模型的流水线，编译并提交流水线作业。本章还涵盖了流水线中谱系的使用、不同流水线的对比及其用途。

在下一章中，我们将使用 TensorFlow Extended (TFX) 为自定义模型训练构建流水线。

## 问题

1. 如果我们必须使用 xgboost/pytorch/TensorFlow 来执行流水线，需要做哪些更改？

2. 为什么流水线对比很有帮助？

3. 流水线的工件和参数是如何被追踪的？

## 加入我们书籍的 Discord 空间

加入书籍的 Discord 工作区，获取最新动态、优惠、全球科技动态、新版本发布以及与作者的交流会议：

[`discord.bpbonline.com`](https://discord.bpbonline.com)

---

# 第 8 章：使用 TensorFlow Extended 的流水线

## 简介

在上一章中，我们使用 Kubeflow 处理了 GCP 的流水线，并为自定义模型训练构建了第一条流水线。在本章中，我们将开始了解 TFX 及其组件，以及如何使用这些组件进行自定义模型训练。

## 结构

在本章中，我们将讨论以下主题：

*   什么是 TensorFlow Extended (TFX)
*   TFX 流水线
*   TFX 的组件
*   用于构建流水线的数据
*   流水线代码演示
*   资源的删除

## 目标

在本章结束时，用户将能够使用标准组件构建 TFX 流水线，并使用 Kubeflow 执行流水线。

## 什么是 TensorFlow Extended

毫无疑问，将机器学习和深度学习模型投入生产极具挑战性。即使它为企业创造了额外价值，但相比建模本身，它更加耗时且容易失败。模型部署后必须进行维护。我们必须评估其功能、新生成数据的质量以及支持基础设施的适用性。必须根据需要对模型进行重新训练。为了长期可行，整个过程必须尽可能减少人工干预并实现自动化。此外，我们必须确保所使用的模型是可靠的、一致的、安全的，并且可能具备可扩展性。Google 于 2019 年初正式推出了其内部平台 TensorFlow Extended，以帮助企业实施工业级的端到端生产系统。

TFX 旨在成为一个强大且通用的端到端机器学习平台。它构建在 TensorFlow (TF) 包之上，这些包允许 Python 程序员创建自定义函数。TFX 封装了整个 TensorFlow 生态系统（从 Keras 到数据验证再到服务），使用户能够构建和运行可扩展且高效的机器学习流水线，而不仅仅是允许他们以高性能方式服务模型。它被构建为一系列可调整的组件，要求用户编写更少的代码。

## TFX 流水线

TFX 流水线是机器学习过程的一种实现，具有可移植性，可以在各种编排器上运行，例如 `Kubeflow Pipelines`、`Apache Beam` 和 `Apache Airflow`。流水线的构建块称为组件和输入参数。

组件实例的输出是工件，而组件实例的输入通常由上游组件实例生成的工件组成。有向无环图 (DAG) 是使用工件创建的，它决定了流水线的执行顺序。

## TFX 的组件

流水线将机器学习工作流分解为一系列组件，每个组件负责机器学习过程中的某个特定阶段。TFX 将标准组件和自定义组件作为单独的类别提供。用户也可以仅使用少数标准组件来构建流水线。

借助自定义组件，机器学习过程可以得到扩展。构建组件是根据用户需求定制的，例如从闭源系统吸收数据、应用数据增强、采样、将用 Python 以外语言开发的工具集成到您的机器学习过程中（如使用 R 进行数据分析）等。

TFX 中的组件由组件规范和执行器类组成，两者都包含在组件接口类中。组件的规范定义了组件的输入和输出契约。该契约概述了组件的输入和输出工件，以及执行组件过程中应用的参数。组件的执行器类负责实现组件负责执行的任务。规范和执行器被组合到一个接口类中，以便在 TFX 流水线中使用该组件。

组件的执行分三个步骤进行：

1.  **驱动程序**：根据元数据决定需要做什么，并协调作业执行
2.  **执行器**：执行完成用户贡献的当前项目作业代码的实际工作
3.  **发布器**：负责收集执行器的结果并更新元数据库。

如果只需要标准功能，则无需更改构成驱动程序或发布器的代码。我们只需扩展执行器，即可在保持相同输入、输出和执行属性的前提下修改执行器。也可以编写一个完全定制的执行器，以实现完全不同的一组功能。

## 自定义组件的类型

有三种自定义组件：基于 Python 函数、基于容器，以及完全自定义的组件：

*   **Python 函数**：构建基于函数的 Python 组件比构建基于容器的组件或从头构建的组件更容易。类型注解显示参数是输入工件、输出工件还是参数。这些注解位于 Python 函数的参数中。

*   **基于容器**：基于容器的组件允许您将用任何语言编写的代码添加到流水线中，只要该代码可以在 Docker 容器中运行。

*   **完全自定义**：您可以通过定义组件规范、组件执行器和组件接口的类来构建完全自定义的组件。

TFX 中有库和流水线组件。下图展示了 TFX 库和流水线组件之间的关系：

![](img/Figure_8.1.png)

**图 8.1：** TFX 的库和组件 1

1 图片来源：[`www.tensorflow.org/tfx/guide`](https://www.tensorflow.org/tfx/guide)

## 自定义组件的功能

让我们了解这些组件的功能。

*   **ExampleGen**：TFX 流水线组件 `ExampleGen` 作为入口点并摄取数据。当作为输入使用时，`ExampleGen` 会自动扫描并使用外部数据源，包括 CSV、TF Records、Avro 和 Parquet。`ExampleGen` 生成 TF 示例（也称为 TF 序列示例）作为输出。这些示例在执行数据集表示方面特别有效，并且可以被后续组件可靠地读取。

*   **StatisticsGen**：其他流水线组件可以使用 `StatisticsGen` TFX 流水线组件生成的统计信息。这些统计信息可以针对训练数据和服务数据生成。

## TFX 组件概述

### SchemaGen

`SchemaGen` 使用数据描述（称为 Schema，即 `schema.proto` 类的实例）来供 TFX 组件使用。它可以指定特征值的数据类型、可接受值的范围、特征是否必须存在于所有样本中以及其他特性。此外，`SchemaGen` 流水线组件会通过从训练数据推断类型、类别和范围来自动构建 Schema。

### ExampleValidator

`ExampleValidator` 是流水线组件，用于查找用于训练和服务的数据中的异常。它可以识别数据中的几类异常。此外，它还可以：

- 通过将数据统计信息与详述用户期望的 Schema 进行比较，执行有效性检查。
- 对比训练数据和服务数据，以查找两者之间的任何差异。
- 检查数据系列，以识别任何数据漂移实例。

### Transform

`ExampleGen` 组件负责输出数据工件，而 `Transform` TFX 流水线组件负责对这些工件执行特征工程。`Transform` 组件从外部来源导入数据 Schema 工件，或使用由 `SchemaGen` 生成的数据 Schema 工件。

### Trainer

`Trainer` TFX 是流水线组件，负责训练 TensorFlow 模型。`Trainer` 组件为推理生成至少一个模型，并以兼容 TensorFlow SavedModel 的格式存储。一个可信的模型将包含完整的 TensorFlow 程序，包括所有权重和计算。

### Tuner

`Tuner` 组件负责微调模型的超参数。`Tuner` 是 TFX 组件家族中最新加入的成员，严重依赖 Python Keras Tuner API 来调整超参数。转换后的数据以 Transform 图工件的形式提供，供 `Tuner` 组件作为输入，`Tuner` 组件输出超参数工件。

### Evaluator

由 `Trainer` 开发的模型将被 `Evaluator` 组件使用，该组件将使用原始输入数据工件。此外，它将利用 TensorFlow Model Analysis 库进行综合分析。

### InfraValidator

在将模型发送到生产环境之前，作为 TFX 组件的 `InfraValidator` 作为早期预警层，用于捕获任何潜在问题。模型验证发生在实际为模型提供服务的基础设施中，因此得名 `InfraValidator`。如果 `Evaluator` 保证模型将按预期执行，则 `InfraValidator` 也将保证模型不会有任何机械问题。

### Pusher

在模型训练或重新训练过程中，`Pusher` 组件用于将已验证的模型发送到部署目标。

## 流水线构建数据

对于此练习，数据从 Kaggle 下载（链接如下），数据集列在 CC0：公共领域许可证下。数据包含来自 EEG 的各种测量值，眼睛状态通过摄像头捕获。1 表示闭眼，0 表示睁眼。

[`www.kaggle.com/datasets/robikscube/eye-state-classification-eeg-dataset`](https://www.kaggle.com/datasets/robikscube/eye-state-classification-eeg-dataset)

在 us-centra1（单区域）下创建了 `tfx_pipeline_input_data` 存储桶，并将 csv 文件上传到该存储桶，如图 8.2 所示：

![](img/Figure_8.2.png)

**图 8.2：** 用于流水线构建的 GCS 中的数据

## 流水线代码演练

需要创建 Workbench 来运行流水线代码。请按照章节 "Vertex AI workbench & custom model training" 中提到的步骤创建 Workbench（选择 TensorFlow enterprise | TensorFlow Enterprise 2.9 | Without GPUs，参考图 8.3。所有其他步骤将与 Vertex AI workbench 和自定义模型训练中提到的相同）。

![](img/Figure_8.3.png)

**图 8.3：** 使用 TensorFlow Enterprise 创建 Workbench

### 步骤 1：创建 Python Notebook 文件

创建 Workbench 后，打开 JupyterLab 并按照图 8.4 中提到的步骤创建 Python Notebook 文件：

![](img/Figure_8.4.png)

**图 8.4：** 新启动器窗口

1. 点击 New launcher。
2. 双击 Python3 Notebook 文件以创建一个。

### 步骤 2：包安装

运行以下命令安装 Kubeflow、Google Cloud Pipeline 和 Google Cloud AI Platform 包（安装包需要几分钟）：

```bash
USER_FLAG = "--user"

!pip install {USER_FLAG} --upgrade "tfx[kfp]<2"

!pip install {USER_FLAG} apache-beam[interactive]

!pip install python-snappy
```

### 步骤 3：内核重启

在下一个单元格中输入以下命令以重启内核（用户也可以从 GUI 重启内核）：

```python
import os
import IPython

if not os.getenv(""):
    IPython.Application.instance().kernel.do_shutdown(True)
```

### 步骤 4：验证包是否安装

运行以下代码行以检查包是否已安装（如果包安装正确，请尝试在安装 tfx 和 kfp 包之前升级 pip 包）：

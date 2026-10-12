
```
gcloud ai endpoints deploy-model 1234567890 \
  --region=us-central1 \
  --model=model_id_12345 \
  --display-name=image_classification \
  --machine-type=a2-highgpu-2g \
  --accelerator=count=2,type=nvidia-tesla-t4 \
  --disable-container-logging \
  --enable-access-logging
```

### 模型监控和日志记录

模型监控和请求-响应日志记录在后端使用相同的基础设施（BigQuery 表）。因此，当这两项服务同时涉及时，存在一些限制：

* 如果端点上已启用模型监控，则无法启用请求-响应日志记录。
* 如果先启用了请求-响应日志记录，然后启用模型监控，则无法修改请求-响应日志记录。

## 模型和数据集谱系

当你尝试不同类型的模型时，需要一种有条理的方法来记录实验的参数和相应的观察结果。机器学习实验的参数、工件和指标称为实验的*元数据*。元数据可帮助你执行以下操作：

* 检测部署后的模型性能下降。
* 比较不同超参数集的有效性。
* 跟踪机器学习工件（包括数据集和模型）的谱系。谱系有助于查找所有工件的来源，也能从给定的模型/数据集找到派生工件。
* 使用相同的参数重新运行机器学习工作流。
* 为审计目的跟踪工件的下游使用情况。这也可用于了解给定工件影响了什么。

### Vertex ML Metadata

使用 Vertex ML Metadata，你可以记录工件的元数据，并查询元数据以进行分析、调试或审计。Vertex ML Metadata 基于 Google TensorFlow Extended 团队开发的开源 ML Metadata (MLMD) 库。

Vertex ML Metadata 使用以下数据模型和相关术语：

* **元数据存储区：** 这是所有元数据资源的顶级容器。它是区域级的，且在 Google Cloud 项目范围内。通常，一个元数据存储区由整个组织共享。
* **元数据资源：** Vertex ML Metadata 使用类图数据模型来表示资源之间的关系。这些资源如下：
    * **工件：** 工件是由机器学习工作流创建或可被其使用的实体或数据片段。示例包括数据集、模型、输入文件、训练日志和指标。
    * **上下文：** 上下文是一组可供查询的工件和执行。假设你正在优化超参数；每个实验将是一个具有自己参数和指标集的不同执行。你可以将这些实验分组到一个上下文中，然后比较该上下文中的指标以确定最佳模型。
    * **执行：** 这代表机器学习工作流中的一个步骤，并可附带运行时参数进行标注。示例可以是一个“训练”操作，附带关于耗时和使用的 GPU 数量的标注。
    * **事件：** 事件连接工件和执行。诸如工件作为执行的输出和下一个执行的输入等详细信息，可使用事件来捕获。当你试图追踪谱系时，它有助于确定工件的来源。[图 12.3](#c12.xhtml#c12-fig-0003) 显示了一个包含事件、工件、执行和上下文的简单图。

![图 12.3 Vertex Metadata 数据模型](images/c12f003.png)

[**图 12.3**](#c12.xhtml#R_c12-fig-0003) Vertex Metadata 数据模型

* **元数据架构：** 元数据架构指定工件或执行等特定类型数据所使用的架构。类型架构使用 YAML 格式的 OpenAPI 架构对象表示。

#### 管理 ML 元数据架构

存储在 Vertex ML Metadata 中的每个元数据资源都遵循一个称为 `MetaDataSchema` 的架构。对于存储的最常见资源类型，有称为*系统架构*的预定义架构。系统架构位于 `system` 命名空间下。以下是 YAML 格式的预定义模型系统类型示例：

```yaml
title: system.Model
type: object
properties:
  framework:
    type: string
    description: "The ML framework used, eg: 'TensorFlow' or 'PyTorch'."
  framework_version:
    type: string
    description: "The version used, eg: '1.16' or '2.5'"
  payload_format:
    type: string
    description: "The format of the model stored: eg: 'SavedModel' or 'pkl'"
```

让我们看看两个重要操作：创建工件和查找工件。其他操作（此处未显示）包括删除工件、创建执行和上下文管理。你可以使用 REST、命令行或 Python 来执行这些操作，我们将展示 Python 示例。以下是在 Python 中创建工件的方法：

```python
def create_artifact_sample(
    project: str,
    location: str,
    uri: Optional[str] = None,
    artifact_id: Optional[str] = None,
    display_name: Optional[str] = None,
    schema_version: Optional[str] = None,
    description: Optional[str] = None,
    metadata: Optional[Dict] = None,
):
    system_artifact_schema = artifact_schema.Artifact(
        uri=uri,
        artifact_id=artifact_id,
        display_name=display_name,
        schema_version=schema_version,
        description=description,
        metadata=metadata,
    )
    return system_artifact_schema.create(project=project, location=location)
```

在此示例中，我们定义了一个新函数，接收 URI、工件 ID、位置、显示名称、架构版本、描述和元数据（定义元数据本身的属性）等详细信息。在函数内部，我们调用 `artifact_schema.Artifact` 函数创建一个系统工件实例，第二步调用 `create()` 函数在元数据存储区中创建它。

在下一个示例中，我们将看到如何查询或查找数据集或模型等工件：

```python
def list_artifact_sample(
    project: str,
    location: str,
    display_name_fitler: Optional[str] = "display_name=\"my_model_*\"",
    create_date_filter: Optional[str] = "create_time>\"2022-06-11\"",
):
    aiplatform.init(
        project=project,
        location=location)
  
    combined_filters = f"{display_name_fitler} AND {create_date_filter}"
    return aiplatform.Artifact.list(filter=combined_filters)
```

我们在这里使用类似的方法，定义一个名为 `list_artifact_sample` 的函数来完成这项工作。这也只有三行代码，第一行是 `init()` 函数，第二行创建一个 `combined_filters` 查询。第三行我们使用 `combined_filters` 字符串作为参数调用 `aiplatform.Artifact.list()` 函数。这些代码块和更多信息可以在 `https://cloud.google.com/vertex-ai/docs/ml-metadata/managing-metadata` 的文档中找到。

#### Vertex AI Pipelines

当你使用 Vertex AI Pipelines 时，模型元数据和工件会自动存储在元数据存储区中，用于*谱系跟踪*。每当你运行一个流水线，它都会生成一系列工件。这些可能包括数据集摘要、模型评估指标、特定流水线执行的元数据等。Vertex AI Pipelines 还提供谱系的可视化表示，如[图 12.4](#c12.xhtml#c12-fig-0004)所示。你可以用它来了解模型基于哪些数据构建、部署了哪个模型版本，并按数据架构和日期排序。

![图 12.4 显示谱系的 Vertex AI Pipelines](images/c12f004.png)

[**图 12.4**](#c12.xhtml#R_c12-fig-0004) 显示谱系的 Vertex AI Pipelines

## Vertex AI Experiments

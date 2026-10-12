
在本节中，我们介绍了用户管理笔记本和托管笔记本之间的一些功能差异。我们还介绍了如何创建它们。

在下一节中，您将学习如何使用 Vertex AI Training 训练模型。

## 在不同环境中将模型训练作为作业运行

Vertex AI 支持两种类型的训练：

*   **AutoML：** AutoML 让您能够以极少的技术工作量创建和训练模型。我们在 [第 4 章](#c04.xhtml)“选择合适的 ML 基础设施”中详细介绍了 AutoML。
*   **自定义训练：** 自定义训练让您能够创建针对目标结果进行优化的训练应用。您可以完全控制训练应用的功能。具体而言，您可以以任何目标为对象，使用任何算法，开发自己的损失函数或指标，或进行任何其他自定义。在以下章节中，我们将重点介绍使用 Vertex AI 进行自定义训练。

### Vertex AI 训练工作流

使用 Vertex AI，您可以使用以下选项为 AutoML 或自定义模型创建训练作业或训练资源：

*   **训练流水线：** 训练流水线是 Vertex AI 中主要的模型训练工作流。您可以使用训练流水线创建 AutoML 训练的模型或自定义训练的模型。对于自定义训练模型，训练流水线可编排自定义训练作业和超参数调优，并包含添加数据集或将模型上传到 Vertex AI 以用于预测服务等额外步骤。[图 8.17](#c08.xhtml#c08-fig-0004) 显示了 Vertex AI 控制台中的训练流水线。

    ![FIGURE 8.17 Vertex AI 控制台中的训练 ¶ 来源：Google LLC.](images/c08f017.png)

    [**图 8.17**](#c08.xhtml#R_c08-fig-0004) Vertex AI 控制台中的训练 ¶ 来源：Google LLC。

*   **自定义作业：** 自定义作业指定 Vertex AI 如何运行您的自定义训练代码，包括工作器池、机器类型以及与您的 Python 训练应用和自定义容器相关的设置。自定义作业仅用于自定义训练模型，而非 AutoML 模型。当您创建自定义作业时，您需要指定 Vertex AI 运行训练代码所需的设置。
*   **超参数调优作业：** 超参数调优通过在一系列试验中优化指标值，搜索超参数值的最佳组合。超参数调优仅用于自定义训练模型，而非 AutoML 模型。我们将在本章后面的“超参数调优”部分介绍这一点。

### Vertex AI 中的训练数据集选项

训练始于数据集。在 Vertex AI 中，您有两种存储和管理数据集的选择：

*   **非托管数据集：** 您可以使用存储在 Google Cloud Storage 中的数据或存储在 BigQuery 中的数据进行训练。Vertex AI 托管笔记本与 Cloud Storage 和 BigQuery 集成。因此，您可以直接使用来自这些来源的数据进行训练，您可以在 Vertex AI Workbench 中使用 Google Cloud Storage FUSE 为非托管数据集选项指定 GCS 存储桶中的数据集。GCS FUSE 为应用程序提供了一种使用标准文件系统语义上传和下载 Cloud Storage 对象的方式。
*   **托管数据集：** 这是在 Vertex AI 上训练机器学习模型的首选方式。以下是使用托管数据集在 Vertex AI 上进行训练的一些优势：
    *   在中心位置管理您的数据集。
    *   轻松创建标签和多个注释集。
    *   使用集成的数据标注创建人工标记任务。
    *   跟踪到模型的血缘，用于治理和迭代开发。
    *   通过使用相同的数据集训练 AutoML 和自定义模型来比较模型性能。
    *   生成数据统计信息和可视化。
    *   自动将数据拆分为训练集、测试集和验证集。

Vertex AI 训练为训练提供了两种选择：预构建容器和自定义容器。让我们详细了解一下每一种。

### 预构建容器

Vertex AI 支持容器注册表上托管的 scikit-learn、TensorFlow、PyTorch 和 XGBoost 容器，用于预构建训练。Google 管理所有容器镜像及其版本。要使用预构建容器设置训练，请遵循以下步骤：

1.  您需要按照 [图 8.18](#c08.xhtml#c08-fig-0005) 所示的应用结构组织代码。您应该有一个包含 `setup.py` 的根文件夹和一个包含 `task.py`（训练代码）的 trainer 文件夹，后者是 Vertex AI 训练作业的入口点。您可以通过在 `setup.py` 中指定，使用标准依赖项或预构建容器中不包含的库。
2.  在使用预构建容器开始训练之前，您需要将训练代码作为 Python 源代码分发包上传到 Cloud Storage 存储桶。您可以使用 `sdist` 命令创建源代码分发包——例如 `python setup.py sdist ‐‐formats=gztar,zip`。[图 8.18](#c08.xhtml#c08-fig-0005) 显示了预构建容器的文件夹结构和架构。

![FIGURE 8.18 预构建容器的 Vertex AI 训练架构](images/c08f018.png)

[**图 8.18**](#c08.xhtml#R_c08-fig-0005) 预构建容器的 Vertex AI 训练架构

[图 8.19](#c08.xhtml#c08-fig-0006) 显示了 GCP 控制台为预构建容器设置 Vertex AI 训练流水线的样子。

选择训练容器后，您可以选择要用于训练的计算实例类型。

以下命令基于预构建训练容器镜像和您的本地 Python 代码构建 Docker 镜像，将镜像推送到 Container Registry，并创建自定义作业。

```
gcloud ai custom-jobs create \
  --region=LOCATION \
  --display-name=JOB_NAME \
  --worker-pool-spec=machine-type=MACHINE_TYPE,replica-count=REPLICA_COUNT,executor-image-uri=EXECUTOR_IMAGE_URI,local-package-path=WORKING_DIRECTORY,script=SCRIPT_PATH

LOCATION: 容器或 Python 包将在其中运行的区域。
JOB_NAME: 必需。CustomJob 的显示名称。
MACHINE_TYPE: 机器类型。请参阅可用于训练的机器类型。
REPLICA_COUNT: 要使用的工作器副本数量。在大多数情况下，对于第一个工作器池，将其设置为 1。
EXECUTOR_IMAGE_URI: 运行所提供代码的容器镜像的 URI。请参阅可用于训练的预构建容器。
此镜像充当您使用此命令构建的新 Docker 镜像的基础镜像。
WORKING_DIRECTORY: 本地文件系统中包含运行训练代码的入口点脚本的目录（请参阅下一个列表项）。

相对于本地文件系统上 WORKING_DIRECTORY 的路径，指向作为训练代码入口点的脚本。例如，如果您想运行 /custom job/trainer/task.py 且 WORKING_DIRECTORY 是 /custom job，则对此值使用 trainer/task.py。
```

![FIGURE 8.19 预构建容器的 Vertex AI 训练控制台 来源：Google LLC.](images/c08f019.png)

[**图 8.19**](#c08.xhtml#R_c08-fig-0006) 预构建容器的 Vertex AI 训练控制台 来源：Google LLC。

### 自定义容器

自定义容器是您创建用于运行训练应用的 Docker 镜像。以下是使用自定义容器相较于预构建容器的一些优势：

*   **更快的启动时间。** 如果您使用预装了依赖项的自定义容器，可以节省训练应用在启动时原本需要安装依赖项的时间。
*   **使用您选择的 ML 框架。** 如果您找不到包含您想要使用的 ML 框架的 Vertex AI 预构建容器，您可以构建一个包含您所选框架的自定义容器，并使用它在 Vertex AI 上运行作业。例如，您可以使用自定义容器通过 PyTorch 进行训练。
*   **对分布式训练的扩展支持。** 使用自定义容器，您可以使用任何 ML 框架进行分布式训练。


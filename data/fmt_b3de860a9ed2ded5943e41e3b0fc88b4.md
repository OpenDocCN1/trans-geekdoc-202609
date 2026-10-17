
## 非托管数据集与托管数据集

### 非托管数据集

您可以使用存储在 Google Cloud Storage 中的数据或存储在 BigQuery 中的数据进行训练。Vertex AI 托管笔记本与 Cloud Storage 和 BigQuery 集成。因此，您可以直接使用来自这些来源的数据进行训练。您可以在 Vertex AI Workbench 中使用 Google Cloud Storage FUSE 为非托管数据集选项指定 GCS 存储桶中的数据集。GCS FUSE 为应用程序提供了一种使用标准文件系统语义上传和下载 Cloud Storage 对象的方式。

### 托管数据集

这是在 Vertex AI 上训练机器学习模型的首选方式。以下是使用托管数据集在 Vertex AI 上进行训练的一些优势：

*   在中心位置管理您的数据集。
*   轻松创建标签和多个注释集。
*   使用集成的数据标注创建人工标记任务。
*   跟踪到模型的血缘，用于治理和迭代开发。
*   通过使用相同的数据集训练 AutoML 和自定义模型来比较模型性能。
*   生成数据统计信息和可视化。
*   自动将数据拆分为训练集、测试集和验证集。

## Vertex AI 训练选项

Vertex AI 训练为训练提供了两种选择：预构建容器和自定义容器。

### 预构建容器

Vertex AI 支持容器注册表上托管的 scikit-learn、TensorFlow、PyTorch 和 XGBoost 容器，用于预构建训练。Google 管理所有容器镜像及其版本。要使用预构建容器设置训练，请遵循以下步骤：

1.  您需要按照图 8.18 所示的应用结构组织代码。您应该有一个包含 `setup.py` 的根文件夹和一个包含 `task.py`（训练代码）的 trainer 文件夹，后者是 Vertex AI 训练作业的入口点。您可以通过在 `setup.py` 中指定，使用标准依赖项或预构建容器中不包含的库。
2.  在使用预构建容器开始训练之前，您需要将训练代码作为 Python 源代码分发包上传到 Cloud Storage 存储桶。您可以使用 `sdist` 命令创建源代码分发包——例如 `python setup.py sdist --formats=gztar,zip`。图 8.18 显示了预构建容器的文件夹结构和架构。

![FIGURE 8.18 预构建容器的 Vertex AI 训练架构](img/c08f018.png)

**图 8.18** 预构建容器的 Vertex AI 训练架构

图 8.19 显示了 GCP 控制台为预构建容器设置 Vertex AI 训练流水线的样子。

![FIGURE 8.19 预构建容器的 Vertex AI 训练控制台 来源：Google LLC.](img/c08f019.png)

**图 8.19** 预构建容器的 Vertex AI 训练控制台 来源：Google LLC。

选择训练容器后，您可以选择要用于训练的计算实例类型。

以下命令基于预构建训练容器镜像和您的本地 Python 代码构建 Docker 镜像，将镜像推送到 Container Registry，并创建自定义作业：

```
gcloud ai custom-jobs create \
  --region=LOCATION \
  --display-name=JOB_NAME \
  --worker-pool-spec=machine-type=MACHINE_TYPE,replica-count=REPLICA_COUNT,executor-image-uri=EXECUTOR_IMAGE_URI,local-package-path=WORKING_DIRECTORY,script=SCRIPT_PATH
```

参数说明：

*   `LOCATION`: 容器或 Python 包将在其中运行的区域。
*   `JOB_NAME`: 必需。CustomJob 的显示名称。
*   `MACHINE_TYPE`: 机器类型。请参阅可用于训练的机器类型。
*   `REPLICA_COUNT`: 要使用的工作器副本数量。在大多数情况下，对于第一个工作器池，将其设置为 1。
*   `EXECUTOR_IMAGE_URI`: 运行所提供代码的容器镜像的 URI。请参阅可用于训练的预构建容器。此镜像充当您使用此命令构建的新 Docker 镜像的基础镜像。
*   `WORKING_DIRECTORY`: 本地文件系统中包含运行训练代码的入口点脚本的目录。
*   `SCRIPT_PATH`: 相对于本地文件系统上 `WORKING_DIRECTORY` 的路径，指向作为训练代码入口点的脚本。例如，如果您想运行 `/custom job/trainer/task.py` 且 `WORKING_DIRECTORY` 是 `/custom job`，则对此值使用 `trainer/task.py`。

### 自定义容器

自定义容器是您创建用于运行训练应用的 Docker 镜像。以下是使用自定义容器相较于预构建容器的一些优势：

*   **更快的启动时间。** 如果您使用预装了依赖项的自定义容器，可以节省训练应用在启动时原本需要安装依赖项的时间。
*   **使用您选择的 ML 框架。** 如果您找不到包含您想要使用的 ML 框架的 Vertex AI 预构建容器，您可以构建一个包含您所选框架的自定义容器，并使用它在 Vertex AI 上运行作业。例如，您可以使用自定义容器通过 PyTorch 进行训练。
*   **对分布式训练的扩展支持。** 使用自定义容器，您可以使用任何 ML 框架进行分布式训练。

#### 使用最新版本

您还可以使用 ML 框架的最新构建版本或次要版本。例如，您可以构建一个自定义容器，以使用 `tf-nightly` 进行训练。

图 8.20 展示了自定义容器训练在 Google Cloud 上的工作架构。您需要使用 `Dockerfile` 和采用推荐文件夹结构的训练文件来构建容器。您构建 `Dockerfile` 并将其推送到 Artifact Registry。对于使用自定义容器的 Vertex AI 训练，您需要指定数据集（托管模式）、您推送到代码库的自定义容器镜像 URI，以及用于训练的计算（VM）实例。

![图 8.20 用于自定义容器的 Vertex AI 训练架构](img/c08f020.png)

**图 8.20** 用于自定义容器的 Vertex AI 训练架构

要为 Vertex AI 训练创建自定义容器，您需要创建 `Dockerfile`、构建 `Dockerfile` 并将其推送到 Artifact Registry。步骤如下：

#### 1. 创建自定义容器和训练文件

##### 1.1 按照要求的文件夹结构设置文件

您需要创建一个根文件夹。然后创建一个 `Dockerfile` 和一个名为 `trainer/` 的文件夹。在该 `trainer` 文件夹中，您需要创建 `task.py`（您的训练代码）。此 `task.py` 文件是入口点文件。

##### 1.2 创建 Dockerfile

您的 `Dockerfile` 需要包含如下代码所示的命令，这些命令包括选择基础镜像、安装额外依赖项、将训练代码复制到镜像中，以及配置入口点以调用训练代码等任务。

```
####### 指定基础镜像和标签
FROM image:tag
WORKDIR /root

####### 安装额外的软件包
RUN pip install pkg1 pkg2 pkg3

####### 下载训练数据
RUN curl https://example-url/path-to-data/data-filename --output /root/data-filename

####### 将训练器代码复制到 Docker 镜像中
COPY your-path-to/model.py /root/model.py
COPY your-path-to/task.py /root/task.py

####### 设置入口点以调用训练器
ENTRYPOINT ["python", "task.py"]
```

#### 2. 构建并运行您的 Docker 容器

您可以使用以下代码构建 Docker 镜像：

```
export PROJECT_ID=$(gcloud config list project --format "value(core.project)")
export REPO_NAME=REPOSITORY_NAME
export IMAGE_NAME=IMAGE_NAME
export IMAGE_TAG=IMAGE_TAG
export IMAGE_URI=us-central1-docker.pkg.dev/${PROJECT_ID}/${REPO_NAME}/${IMAGE_NAME}:${IMAGE_TAG}

docker build -f Dockerfile -t ${IMAGE_URI} ./
```

对于本地运行，请使用以下命令：

```
docker run ${IMAGE_URI}
```

#### 3. 将容器镜像推送到 Artifact Registry

如果 Docker 构建成功，您可以通过运行以下命令将容器推送到 Artifact Registry。

```
docker push ${IMAGE_URI}
```

#### 4. 开始训练

将镜像推送到代码库后，您可以通过使用以下命令创建自定义作业来开始训练：

```
gcloud ai custom-jobs create \
  --region=LOCATION \
  --display-name=JOB_NAME \
  --worker-pool-spec=machine-type=MACHINE_TYPE,replica-count=REPLICA_COUNT,container-image-uri=CUSTOM_CONTAINER_IMAGE_URI
```

## 分布式训练

为了使用 Vertex 运行分布式训练作业，您需要在训练集群中指定多台机器（节点）。训练服务会为您指定的机器类型分配资源。在给定节点上运行的作业称为 **副本**。具有相同配置的一组副本称为工作池。您可以通过定义多个工作池，将任何自定义训练作业配置为分布式训练作业。您还可以在训练流水线或超参数调优作业中运行分布式训练。请使用支持分布式训练的 ML 框架。在您的训练代码中，您可以使用 `CLUSTER_SPEC` 或 `TF_CONFIG` 环境变量来引用训练集群的特定部分。请参阅表 8.4 以了解分布式训练中的工作池任务。

### 表 8.4 分布式训练中的工作池任务

| `workerPoolSpecs[]` 中的位置 | 在集群中执行的任务 |
| --- | --- |
| 第一 (`workerPoolSpecs[0]`) | 主节点、控制器、调度器或 "master"。恰好有一个副本被指定为 *主副本*。此任务管理其他副本并报告整个作业的状态。 |
| 第二 (`workerPoolSpecs[1]`) | 次要节点、副本、工作器。一个或多个副本可被指定为 *工作器*。这些副本按照您在作业配置中指定的方式完成其份额的工作。 |
| 第三 (`workerPoolSpecs[2]`) | 参数服务器和 Reduction Server<br>• **参数服务器：** 如果您的 ML 框架支持，一个或多个副本可被指定为参数服务器。这些副本存储模型参数，以协调工作器之间的共享模型状态。<br>• **Reduction Server** 是一种全归约算法，可提高分布式训练的吞吐量并降低延迟。如果您使用 GPU 工作器进行分布式训练，可以使用此选项。您的训练代码使用 TensorFlow 或 PyTorch，并配置为使用 NCCL 全归约进行多主机数据并行 GPU 训练。<br>对于 TensorFlow，您还可以使用 Horovod，它支持 Tensor Fusion 以将小张量批量处理进行全归约。 |
| 第四 (`workerPoolSpecs[3]`) | 评估器：这些副本可用于评估您的模型。如果您使用 TensorFlow，请注意 TensorFlow 通常预期您使用不超过一个评估器。 |

### 设置 Vertex AI Reduction Server 分布式训练

Vertex AI 以 Docker 容器镜像的形式提供 Reduction Server，您可以在分布式训练期间将其用于其中一个工作池。在设置 `workerpoolspec[2]` 中的 Reduction Server 容器之前，您需要遵循此链接中提到的先决条件：`https://cloud.google.com/vertex-ai/docs/training/distributed-training`。以下命令提供了一个示例，展示如何通过设置工作池创建一个使用 Reduction Server 进行分布式训练的 `CustomJob` 资源：

```
gcloud ai custom-jobs create \
  --region=LOCATION \
  --display-name=JOB_NAME \
  --worker-pool-spec=machine-type=n1-highmem-96,replica-count=1,accelerator-type=NVIDIA_TESLA_V100,accelerator-count=8,container-image-uri=CUSTOM_CONTAINER_IMAGE_URI \
  --worker-pool-spec=machine-type=n1-highmem-96,replica-count=4,accelerator-type=NVIDIA_TESLA_V100,accelerator-count=8,container-image-uri=CUSTOM_CONTAINER_IMAGE_URI \
  --worker-pool-spec=machine-type=n1-highcpu-16,replica-count=16,container-image-uri=us-docker.pkg.dev/vertex-ai-restricted/training/reductionserver:latest
```

我们在 第 7 章 "模型构建" 中介绍了使用 TensorFlow 的分布式训练策略。要深入了解 Reduction Server 的工作原理，请参阅此深度解析博客：`https://cloud.google.com/blog/topics/developers-practitioners/optimize-training-performance-reduction-server-vertex-ai`

## 超参数调优

超参数是训练算法本身的参数，不会直接从训练过程中学习。让我们看一个使用梯度下降训练的简单前馈神经网络 DNN 模型的示例。梯度下降中的超参数之一是学习率，我们在 第 7 章 中已介绍过。学习率必须在任何学习开始之前预先设置。因此，寻找合适的学习率涉及选择一个值、训练模型、评估它，然后再次尝试。

### 图 8.21：ML 模型参数和超参数

图 8.21 总结了参数和超参数之间的区别。

![图 8.21 ML 模型参数和超参数](img/c08f021.png)

**图 8.21** ML 模型参数和超参数

### 为什么超参数很重要

超参数的选择对神经网络架构的成功至关重要，因为超参数会严重影响所学习模型的行为。例如，如果学习率设置得太低，模型将错过数据中的重要模式；但如果设置得太大，模型将过于容易地在偶然的巧合中发现模式。寻找良好的超参数涉及解决两个问题：

*   **如何高效地搜索可能的超参数空间：** 有一些算法可帮助进行超参数搜索空间优化。Vertex AI 默认算法应用贝叶斯优化以得出最优解。表 8.5 总结了 Vertex AI 超参数调优支持的搜索算法。
*   **如何管理大量用于超参数调优的实验：** 如果没有像 Vertex AI 超参数调优这样的自动化技术，您将需要在许多训练运行过程中手动调整超参数，以得出最优值。超参数调优使确定最佳超参数设置的过程更轻松、不那么繁琐。超参数调优利用 Google Cloud 的计算基础设施，在训练模型时测试不同的超参数配置。它可以为您提供超参数的优化值，从而最大化模型的预测准确性。

### 表 8.5：GCP 上超参数调优的搜索算法选项

**表 8.5** GCP 上超参数调优的搜索算法选项

| 网格搜索 | 随机搜索 | 贝叶斯搜索 |
| --- | --- | --- |
| 网格搜索本质上是对手动指定的一组超参数进行详尽搜索。例如，一个具有超参数 `learning_rate` 和 `num_layers` 的模型。<br>`learning_rate = [0.1, 0.5, 1]`<br>`num_layers = [5, 10, 20]`<br>网格搜索将在每次训练中对每一对 `[learning_rate, num_layers]` 进行训练，例如 `[0.1, 5]`，并使用训练集上的交叉验证或单独的验证集来衡量性能。得分最高的超参数设置即为最终输出。 | 随机搜索是一种使用超参数的随机组合来为构建的模型寻找最佳解决方案的技术。这在并非所有超参数都同等重要的假设下效果最好。在这种搜索模式中，每次迭代都会考虑参数的随机组合。 | 这是 Vertex AI 的默认搜索算法。贝叶斯优化在选择下一个要评估的超参数集时，会考虑过去的评估结果。 |
| 网格搜索的缺点之一是，就维度而言，当超参数的数量呈指数级增长时，其评估会变得困难。 | 然而，随机搜索的缺点是它不利用先前实验的信息来选择下一个设置。 | 它使用过去的评估结果。 |
| 要使用网格搜索，所有参数必须属于 `INTEGER`、`CATEGORICAL` 或 `DISCRETE` 类型。 | 由于随机搜索模式的随机性，模型可能最终在没有任何混叠的情况下在优化参数上进行训练，因此随机搜索找到最优参数的几率比网格搜索高。 | 超参数调优使用一种称为 `Gaussian Process Bandits`（高斯过程老虎机）的算法，这是一种贝叶斯优化形式。 |

### 加速超参数优化的技术

有几种技术可以加速超参数优化：



在此命令中，`--package-path` 表示 `trainer` 目录代表一个包，而 `--module-name` 表示该包的模块名称为 `trainer.task`。`--job-dir` 标志告诉应用程序将其结果存储在名为 `output` 的目录中。

两个破折号（`--`）将 `--job-dir` 与 `--data_dir` 分开。这表示 `--data_dir` 及之后的所有标志均由用户定义。

### 运行本地预测任务

训练完成后，您可以通过执行 `gcloud ml-engine local predict` 启动本地预测任务。 [表 13-8](#19_9788126592555-ch13.xhtml#c13-tbl-0008) 列出了您可以设置的各种标志。

[TABLE 13-8](#19_9788126592555-ch13.xhtml#rc13-tbl-0008) 本地预测标志

| **Flag** || **Description** |

| --- | --- |

| `--model-dir=MODEL_DIR` || 模型的路径 |

| --- | --- |

| `--json-instances=JSON_INSTANCES` || 包含 JSON 格式预测数据的本地文件路径 |

| `--text-instances=TEXT_INSTANCES` || 包含纯文本预测数据的本地文件路径 |

您应将 `--model-dir` 标志分配给包含训练操作输出的目录。此外，您需要使用 `--json-instances` 或 `--text-instances` 标志来标识预测参数。

## 部署到云端

如果您已成功在本地启动任务，将应用程序部署到云端不应有任何困难。但请注意两个问题：

*   您需要将训练/评估数据上传到 Cloud Storage。
*   ML Engine 可能不支持您需要的软件包版本。

在执行 `ch13` 目录中的任一应用程序之前，您需要将 `mnist_test.tfrecords` 和 `mnist_train.tfrecords` 文件上传到 Cloud Storage 存储桶中。例如，如果您的项目 ID 为 `$(PROJECT_ID)`，您可以使用以下命令在美国中部创建一个名为 `$(PROJECT_ID)_mnist` 的存储桶：

```
gsutil mb -c regional -l us-central1 gs://$(PROJECT_ID)_mnist
```

创建存储桶后，您可以使用以下命令将两个 `MNIST` 文件上传到存储桶中：

```
gsutil cp mnist_test.tfrecords mnist_train.tfrecords gs://$(PROJECT_ID)_mnist
```

命令执行后，最好检查 Cloud Storage 是否为这两个文件创建了对象。您可以通过运行命令 `gsutil ls gs://$(PROJECT_ID)_mnist` 来验证这一点。

### 运行远程训练任务

上传测试/评估数据后，您可以使用以下命令启动训练任务：

```
gcloud ml-engine jobs submit training $(JOB_ID)
```

`$(JOB_ID)` 为训练任务提供唯一标识符。启动任务后，您可以使用此 ID 检查任务的状态。

除了标识任务之外，您还需要告诉 ML Engine 在何处查找您的软件包和输入数据。您还需要告诉引擎应将输出文件存储在何处。您可以通过在命令后跟随标志来提供此信息，而 [表 13-9](#19_9788126592555-ch13.xhtml#c13-tbl-0009) 列出了其中的每一个。

[TABLE 13-9](#19_9788126592555-ch13.xhtml#rc13-tbl-0009) 云训练任务标志

| **Flag** || **Description** |

| --- | --- |

| `--module-name=MODULE_NAME` || 标识要执行的模块 |

| --- | --- |

| `--package-path=PACKAGE_PATH` || 包含要执行模块的 Python 软件包的路径 |

| `--job-dir=JOB_DIR` || 存储输出文件的路径 |

| `--staging-bucket=STAGING_BUCKET` || 操作期间保存软件包的存储桶 |

| `--region=REGION` || 机器学习任务的区域 |

| `--runtime-version=RUNTIME_VERSION` || 任务的 ML Engine 版本 |

| `--stream-logs` || 阻塞直到任务完成并流式传输日志 |

| `--scale-tier=SCALE_TIER` || 任务的运行环境 |

| `--config=CONFIG` || 任务配置文件路径 |

`--module-name`、`--package-path` 和 `--job-dir` 标志的作用与本地训练任务中同名标志相同。`--staging-bucket` 标志标识保存已部署软件包的存储桶。`--region` 标志接受 [表 13-3](#19_9788126592555-ch13.xhtml#c13-tbl-0003) 中列出的区域之一。

默认情况下，已部署的应用程序在 ML Engine 的最新稳定版本上运行。您可以通过设置 `--runtime-version` 标志来配置此项。您可以在 `cloud.google.com/ml-engine/docs/runtime-version-list` 获取版本列表。

我更喜欢设置 `--stream-logs` 标志，因为它会强制命令阻塞直到任务完成。随着任务的运行，控制台会打印远程日志中的消息。中止命令（`Ctrl-C`）不会影响远程任务。

默认情况下，上传到 ML Engine 的应用程序只能在单个 CPU 上运行。您可以通过将 `--scale-tier` 标志设置为 [表 13-10](#19_9788126592555-ch13.xhtml#c13-tbl-0010) 中列出的值之一来配置执行环境。

[TABLE 13-10](#19_9788126592555-ch13.xhtml#rc13-tbl-0010) 规模层级值

| **Value** || **Description** |

| --- | --- |

| `basic` || CPU 上的单个工作器 |

| --- | --- |

| `basic-gpu` || 带有 GPU 的单个工作器 |

| `basic-tpu` || 带有 Cloud TPU 的单个工作器实例 |

| `standard-1` || 多个工作器和少数参数服务器 |

| `premium-1` || 大量工作器和许多参数服务器 |

| `custom` || 定义集群 |

如果您将 `--scale-tier` 设置为 `basic-gpu`，您可以在 Nvidia Tesla K80 GPU 上执行代码。该 GPU 具有 4,992 个 CUDA 核心和 24 GB GDDR5 内存。如果您将 `--scale-tier` 设置为 `basic-tpu`，您可以在一个或多个 Google 的张量处理单元（`TPUs`）上执行代码。截至本文撰写时，Google 将 TPU 访问限制在其 Cloud TPU 计划的开发人员，您可以在 [`http://cloud.google.com/tpu`](http://cloud.google.com/tpu) 了解有关该计划的更多信息。

如果您将 `--scale-tier` 设置为 `standard-1` 或 `premium-1`，您可以在处理器集群上运行任务。如果您将 `--scale-tier` 设置为 `custom`，您可以通过将 `--config` 标志分配给配置文件名称来配置集群。

### 运行远程预测任务

[第 5 章](#09_9788126592555-ch05.xhtml) 介绍了 `SavedModel`，如果您将 `SavedModel` 上传到 Cloud Storage 存储桶，您可以使用以下命令启动预测任务：

```
gcloud ml-engine jobs submit prediction $(JOB_ID)
```

此命令接受指定预测任务应读取输入和写入输出位置的标志。 [表 13-11](#19_9788126592555-ch13.xhtml#c13-tbl-0011) 列出了这些标志中的每一个。

[TABLE 13-11](#19_9788126592555-ch13.xhtml#rc13-tbl-0011) 云预测任务标志

| **Flag** || **Description** |

| --- | --- |

| `--model-dir=MODEL_DIR` || 包含已保存模型的存储桶路径 |

| --- | --- |

| `--model=MODEL` || 用于预测的模型名称 |

| `--input-paths=INPUT_PATH, [INPUT_PATH,…]` || 用于预测的输入数据路径 |

| `--data-format=DATA_FORMAT` || 输入数据的格式 |

| `--output-path=OUTPUT_PATH` || 存储预测结果的路径 |

| `--region=REGION` || 机器学习任务的区域 |

| `--batch-size=BATCH_SIZE` || 每批记录数 |

| `--max-worker-count=MAX_WORKER_COUNT` || 用于并行处理的最多工作器数 |

| `--runtime-version=RUNTIME_VERSION` || 任务的 ML Engine 版本 |

| `--version=VERSION` || 要使用的模型版本 |

当您启动远程预测任务时，您必须使用 `--model` 标识模型名称或使用 `--model-dir` 标识包含模型文件的存储桶。您还需要使用 `--input-paths` 标识输入文件的位置。

ML Engine 接受三种格式的预测输入数据。您可以通过将 `--data-format` 设置为以下值之一来标识您的数据格式：

*   `text`: 每行一个实例的文本文件
*   `tf-record`: TFRecord 文件


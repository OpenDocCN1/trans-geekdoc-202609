
让我们创建一个虚拟环境：

```
conda create -n venv python=3.7
```

- `-n` 是指虚拟环境的名称。
- `venv` 是虚拟环境的名称。

上述命令将创建 Python 版本为 3.7 的虚拟环境。

创建 conda 环境后，需要运行以下命令将其激活：

```
conda activate venv
```

最后，使用 pip 安装 MLflow：

```
pip install mlflow
```

> 注意：默认情况下，MLflow 项目使用 conda 安装依赖项；但是，您可以通过使用 `--no-conda` 选项在不使用 conda 的情况下继续，例如，mlflow run . --no-conda。

安装 MLflow 后，在终端中键入 `mlflow` 并回车以查看其用法、选项和命令。以下图显示了 `mlflow` 的用法和选项：

![](img/cc4299656808e62a294f1843a1e18e72_104_0.png)

图 5.1: MLflow 的用法、选项和命令

要打开 MLflow 的 Web UI，请在终端中运行以下命令（请参阅图 5.2）：

```
mlflow ui
```

```
(mlflow_venv) suhas@suhasVN:~/test$ mlflow ui
[2021-09-23 20:02:36 +0530] [23435] [INFO] Starting gunicorn 20.1.0
[2021-09-23 20:02:36 +0530] [23435] [INFO] Listening at: http://127.0.0.1:5000 (
23435)
[2021-09-23 20:02:36 +0530] [23435] [INFO] Using worker: sync
[2021-09-23 20:02:36 +0530] [23438] [INFO] Booting worker with pid: 23438
```

图 5.2: 启动 MLflow UI

打开浏览器；您应该会看到 MLflow 的 Web UI，如下图所示：

![](img/cc4299656808e62a294f1843a1e18e72_105_0.png)

图 5.3: MLflow UI

您可以执行一系列实验并捕获实验的多个运行。每个实验可以包含多个运行。您还可以为实验捕获注释。除此之外，还有许多可用的自定义选项，例如按列排序、显示或隐藏列以及更改表格视图。

注意：假设您中断了正在运行的 MLflow UI 服务并重新运行 `mlflow ui` 命令；在这种情况下，您可能会遇到如下图所示的错误：

```
(mlflow_venv) suhas@suhasVM:~/test$ mlflow ui
[2021-09-24 22:58:02 +0530] [23736] [INFO] Starting gunicorn 20.1.0
[2021-09-24 22:58:02 +0530] [23736] [ERROR] Connection in use: ('127.0.0.1', 5000)
[2021-09-24 22:58:02 +0530] [23736] [ERROR] Retrying in 1 second.
[2021-09-24 22:58:03 +0530] [23736] [ERROR] Connection in use: ('127.0.0.1', 5000)
[2021-09-24 22:58:03 +0530] [23736] [ERROR] Retrying in 1 second.
[2021-09-24 22:58:04 +0530] [23736] [ERROR] Connection in use: ('127.0.0.1', 5000)
[2021-09-24 22:58:04 +0530] [23736] [ERROR] Retrying in 1 second.
[2021-09-24 22:58:05 +0530] [23736] [ERROR] Connection in use: ('127.0.0.1', 5000)
[2021-09-24 22:58:05 +0530] [23736] [ERROR] Retrying in 1 second.
[2021-09-24 22:58:06 +0530] [23736] [ERROR] Connection in use: ('127.0.0.1', 5000)
[2021-09-24 22:58:06 +0530] [23736] [ERROR] Retrying in 1 second.
[2021-09-24 22:58:07 +0530] [23736] [ERROR] Can't connect to ('127.0.0.1', 5000)
Running the mlflow server failed. Please see the logs above for details.
```

图 5.4: MLflow UI 错误

这是因为地址端口已被占用；因此，您必须先释放它，然后才能重新运行 `mlflow ui`。可以使用以下命令完成：

```
sudo fuser -k 5000/tcp
```

## MLflow 组件

MLflow 分为四个组件：

- MLflow 跟踪
- MLflow 项目
- MLflow 模型
- MLflow 注册表

这些组件的设计旨在无缝协同工作；但是，您可以根据需要自由使用单个组件。例如，您可以使用 MLflow 提供模型而无需使用跟踪组件。

以下图显示了 MLflow 的组件及其主要作用：

![](img/cc4299656808e62a294f1843a1e18e72_107_0.png)

图 5.5: MLflow 组件

本章将通过示例介绍每个组件的功能。

## MLflow 跟踪

MLflow 跟踪是一种 API 和 UI，用于在运行机器学习代码时记录参数、代码版本、指标和工件，并可视化结果。

MLflow 以运行的形式捕获以下信息，其中每个运行意味着执行一段代码：

- **开始和结束时间：**它记录实验的开始和结束时间。
- **源：**它可以是启动运行的文件名或 MLproject 名称。
- **参数：**它们包含键值对中的数据。这些只不过是您想要捕获的模型输入参数，例如随机森林算法中使用的树的数量。例如，`n_estimators` 是键，其值为 100。您需要调用 MLflow 的 `log_param()` 来存储参数。
- **指标：**指标用于衡量模型的性能，例如模型的准确性。它以键值对的形式保存数据；但是，值应仅为数值。您需要调用 MLflow 的 `log_metric()` 来存储指标。

工件：当您想要存储文件或对象（例如训练好的模型的 pickle 文件）时，工件功能可提供帮助。您可以使用此功能存储序列化的训练模型、图表或 CSV 文件，并可以使用 `log_artifacts()` 调用它。

首先，您必须将文件或对象存储在本地目录中，然后可以通过提供该目录的路径来保存文件或对象。

### 将数据记录到运行中

### mlflow.set_tracking_uri()

它连接到 MLflow 跟踪统一资源标识符 (URI)。默认情况下，跟踪 URI 设置为 mlruns 目录；但是，您可以将其设置为远程服务器 (HTTP/HTTPS)、本地目录路径或 MySQL 等数据库。

```python
1. import mlflow

2. mlflow.set_tracking_uri('http://localhost:5000')
```

### mlflow.tracking.get_tracking_uri()

此函数将返回 MLflow 的当前跟踪 URI。

### mlflow.create_experiment()

它将创建一个新实验。您可以在执行 `mlflow.start_run` 时通过提供实验 ID 来捕获运行。实验名称应为唯一名称。

```python
1. exp_id = mlflow.create_experiment("Loan_Prediction")
```

### mlflow.set_experiment()

此方法激活实验，以便运行将在提供的实验下捕获。如果提到的实验不存在，则会创建一个新实验。默认情况下，实验设置为 'Default'，如图 5.3 所示。

### mlflow.start_run()

它启动一个新运行或返回当前活动的运行。您可以传递当前运行下需要跟踪的运行名称、运行 ID 和实验名称。

```python
1. # For single iteration
2. run = mlflow.start_run()
3.
4. # For multiple iterations
5. with mlflow.start_run(run_name="test_ololo") as run:
```

### mlflow.end_run()

它结束当前活动的运行（如果有）。

### mlflow.log_param()

它在当前活动的运行中记录单个键值参数。键和值均为字符串。使用 `mlflow.log_params()` 一次记录多个参数。

```
1. n_estimators = 100
2. mlflow.log_param("n_estimators:", n_estimators)
```

### mlflow.log_metric()

此 MLflow 函数将跟踪模型指标，例如模型的准确性。要跟踪多个指标，请使用 `mlflow.log_metrics()`。

```
1. accuracy = 0.8
2. mlflow.log_metric("accuracy", accuracy)
```

### mlflow.set_tag()

它以键值对的形式存储数据。在此，您可以设置用于识别或要跟踪的任何特定指标的标签。要设置多个标签，请使用 `mlflow.set_tags()`。

```
1. import mlflow
2. with mlflow.start_run():
3.     mlflow.set_tag("model_version", "0.1.0")
```

### mlflow.log_artifact()

此函数将文件或对象记录或存储在工件目录中；但是，您需要先将其存储在本地目录中，然后才能拉取文件或对象。

```
1. import pandas as pd
2. import mlflow
3.
4. dir_name = 'data_dir'
5. file_name = 'data_dir/cust_sale.csv'
6. data = pd.DataFrame({'Cust_id': [461,462,463], 'Sales': [2631,8462,4837]})
7. data.to_csv(file_name, index=False)
8. mlflow.log_artifacts(dir_name)
```

### mlflow.get_artifact_uri()

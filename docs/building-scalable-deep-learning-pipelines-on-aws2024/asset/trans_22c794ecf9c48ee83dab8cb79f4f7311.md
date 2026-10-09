

- `calculate_average_price_task` 将输出塔可（tacos）的平均价格，该价格会被打印到任务日志中，并可在 Apache Airflow 界面中查看。

**执行元数据：**

- Apache Airflow 维护每次 DAG 运行的元数据，包括开始时间、结束时间、持续时间以及与每个任务执行相关的任何相关元数据等详细信息。
- 您可以在 Apache Airflow 界面或通过 Airflow 的后端数据库访问这些元数据。

利用 Apache Airflow 提供了更具可扩展性和可管理性的工作流编排方法，这是通过用 Airflow DAG 定义替换独立脚本中的 `main()` 函数来实现的。

让我们讨论一下这种替换是如何进行的：

- **任务函数：** 在 `main()` 函数内执行的每个逻辑步骤或操作都会成为 Airflow DAG 中的一个独立任务。例如，`create_taco_dataframe` 函数和 `calculate_average_price` 函数将成为 DAG 中的独立任务。
- **DAG 定义：** 我们不再使用 `main()` 函数，而是在 Airflow 中定义一个 DAG 对象。该 DAG 对象封装了工作流，包括任务依赖关系、调度以及其他参数。DAG 定义提供了一种结构化表示和管理工作流的方式。
- **任务依赖关系：** 在独立脚本中，`main()` 函数内的函数调用顺序决定了执行顺序。在 Airflow DAG 中，任务依赖关系通过使用 `>>` 等操作符显式定义，以指示哪些任务依赖于其他任务。这确保了任务按正确的顺序执行。
- **执行上下文：** 在独立脚本中，函数在 `main()` 函数的上下文中顺序执行。在 Airflow 中，每个任务在 DAG 运行的上下文中独立执行。Airflow 根据 DAG 定义自动管理任务执行、调度、重试和错误处理。
- **触发执行：** 虽然 `main()` 函数通常通过直接运行脚本来触发，但 Airflow DAG 的执行可以手动触发、基于调度触发，或对外部事件做出响应。这种触发是使用 Airflow 的命令行界面 (CLI)、Web 界面或通过网络接口通过其 API 以编程方式完成的。

上述内容表明，用 Airflow DAG 替换 `main()` 函数提供了更具可扩展性和可管理性的工作流编排方法。Airflow 的基于 DAG 的方法允许对复杂工作流进行更好的监控、调度和管理，特别是在数据处理管道和 ETL（提取、转换、加载）任务中。

总体而言，整个管道（从使用 S3 进行数据摄取的第一步开始，到在 Apache Airflow 上调度模型运行结束）具有几个优势：

- 首先，它利用了 PySpark 在大规模数据处理方面的可扩展性以及 EC2 实例在模型训练方面的计算能力，确保高效利用资源。
- 其次，基于云的方法提供了灵活性，允许根据工作负载需求扩展资源并轻松配置资源。
- 第三，PySpark 和 Apache Airflow 凭借其分布式计算能力简化了数据处理任务，实现了高效预处理、转换和工作流编排。
- 第四，Amazon S3 的大容量存储促进了不间断的数据存储和检索，支持大规模数据集的处理。
- 最后，在预处理（PySpark）、模型开发、训练和评估（PyTorch、TensorFlow）、模型编排（Apache Airflow）、存储（S3）和计算（EC2）之间关注点的分离简化了架构并增强了模块化，从而促进简化的工作流管理。

## 项目目录结构

在开始一个新项目时，首先需要考虑的事项之一是如何组织构成该项目的文件和目录。精心设计的 项目目录结构 提供了多项好处，包括组织性、协作性、可复现性和文档化：

- **组织性：** 清晰且合乎逻辑的结构有助于跟踪所有项目文件，使查找所需内容更容易，并避免杂乱。
- **协作性：** 在与团队合作时，标准化的目录布局确保了贡献者之间的一致性，并减少了关于在哪里查找特定文件的困惑。
- **可复现性：** 组织良好的项目目录更易于复现实验或分析，因为所有必要的数据、代码和输出都整齐地组织并记录在案。
- **文档化：** 目录结构本身作为一种形式的文档，提供了对项目架构、组件和工作流的洞察。

理想的目录结构应具备以下属性：

- 直观且易于导航。
- 避免不必要的目录嵌套或过于复杂的层级结构。
- 应根据内容类型划分为逻辑部分。
- 使用有意义的目录和文件名称，以反映其内容和目的。
- 在目录中包含 README 文件或文档，以提供关于如何使用其中包含的文件的其他上下文和指导。

图 1-2 是一个预测特斯拉股价的项目可能如何结构的示例。

# 第 1 章    AWS 上可扩展深度学习管道概述

```
项目目录结构
├── data
│   └── TSLA_stock.csv
├── logs
├── output
│   ├── TSLA_stock.parquet
│   │   ├── _SUCCESS
│   │   └── part-00000-2c717885-1e92-4091-b73e-c07fb2f42ba8-c000.snappy.parquet
│   └── TSLA_stock_train.parquet
│       ├── _SUCCESS
│       └── part-00000-3931d223-097a-4b7f-a6df-6ddc8abfbc5c-c000.snappy.parquet
├── src
│   ├── pyspark_code
│   │   └── data_preprocessing.py
│   ├── pytorch_code
│   │   ├── model.py
│   │   └── model_training.py
│   └── main.py
├── tests
│   └── test.py
├── visualizations
│   └── plot.png
├── README.md
├── config.yaml
└── requirements.txt
```

**图 1-2.** *预测特斯拉股价的项目目录结构*

为了理解特斯拉股价预测项目的组织方式，让我们详细检查目录结构：

- `data`: 此目录包含项目的输入数据。在这种情况下，它是一个名为 `TSLA_stock.csv` 的 CSV 文件，包含特斯拉的历史股票数据。
- `logs`: 此目录可能包含项目执行期间生成的日志文件。将日志与其他项目文件分开是常见的做法，以便于管理。
- `output`: 此目录存储项目生成的输出文件。它包含两个子目录：
    - `TSLA_stock.parquet`: 此目录保存 Parquet 文件，代表与特斯拉股票相关的处理数据。
    - `TSLA_stock_train.parquet`: 与前面的目录类似，此目录包含代表机器学习模型训练数据的 Parquet 文件。
- `src`: 此目录包含项目的源代码。它进一步组织到子目录中：
    - `pyspark_code`: 包含与用于数据清理或转换的 PySpark 数据预处理相关的 Python 文件。
    - `pytorch_code`: 包含用于 PyTorch 模型开发和训练的 Python 文件。
    - `main.py`: 这是项目的主入口点，项目的不同组件在此进行编排。
- `tests`: 此目录保存项目的测试文件。在这种情况下，有一个名为 `test.py` 的 Python 文件，其中包含项目组件的单元测试。
- `visualizations`: 此目录存储项目生成的可视化输出。它包含一个名为 `plot.png` 的 PNG 文件，这是与特斯拉股票分析相关的图表或绘图。
- `README.md`: 这是一个提供项目信息的 markdown 文件。它通常包括设置项目的说明、其用途概览以及其他相关详细信息。
- `requirements.txt`: 此文件列出了运行项目所需的依赖项。它通常包括项目执行所需的 Python 包及其版本。
- `config.yaml`: 此文件包含项目的配置设置。它可能包括数据预处理、模型训练或项目其他方面的参数。下面是一个基本的 `config.yaml` 文件示例，可以添加到特斯拉项目中，用于表示和概述结构：

```yaml
project:
  name: Tesla Stock Prediction
  version: 1.0
  author: Abdelaziz Testas

data:
  input_path: data/TSLA_stock.csv
  output_path: output/TSLA_stock.parquet
  train_output_path: output/TSLA_stock_train.parquet

preprocessing:
  missing_values_strategy: fillna
  fillna_value: 0
  scaling_method: standard_scaler

training:
```


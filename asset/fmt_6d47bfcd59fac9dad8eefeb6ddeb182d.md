
流水线编排了多个步骤，每个步骤都可能产生或消耗数据资产。在我们的训练流水线示例中，我们看到可以将数据资产作为作业的输入和输出。生产流水线中的一个常见需求是在步骤之间传递数据。有很多模式可以在流水线的步骤之间传递数据，但在 Azure Machine Learning 中我们遵循以下步骤：

1. 将数据集传递给脚本：决定使用什么类型的数据：`TabularDataset` 或 `FileDataset`。使用 `Dataset` 对象的 `as_named_input()` 方法将数据集路径传递给脚本，创建一个 `DatasetConsumptionConfig` 对象。

2. 选择访问模式（仅限 `FileDataset`）：如果脚本访问数据集的子集，或者数据集超过了计算资源的磁盘容量，请使用 `as_mount()`，因为该模式在运行时流传输数据。如果脚本处理数据集中的所有文件，且计算资源的磁盘足够大，请使用 `as_download()`，因为该模式会将数据集下载到计算资源中，避免流传输的开销。

## 将数据集传递给你的流水线步骤

使用 `TabularDataset.as_named_input()` 或 `FileDataset.as_named_input()` 来创建一个 `DatasetConfig` 对象，对于 `FileDataset`，使用 `as_mount()` 或 `as_download()` 设置访问模式。通过参数或输入将数据集传递到流水线步骤。

以下是一个使用 Python SDK 操作此内容的示例：点击此处查看图像

```python
train_step = PythonScriptStep(
    name="creditcard",
    script_name="train.py",
    compute_target=cluster,
    inputs=[iris_dataset.as_named_input('iris')]
)
```

你还可以使用 `random_split()` 和 `take_sample()` 等方法创建多个输入，或减少传递给流水线步骤的数据量。这里是该技术的另一个示例：点击此处查看图像

```python
seed = 42 # PRNG
smaller_dataset = default_dataset.take_sample(0.1, seed=seed) # 10%
train, test = smaller_dataset.random_split(percentage=0.8, seed=seed)

train_step = PythonScriptStep(
    name="train_job",
    script_name="train.py",
    compute_target=cluster,
    inputs=[train.as_named_input('train'), test.as_named_input('test')]
)
```

我们可以用你自己的数据替换所有这些参数的值（例如 `train_job`、`train.py`、`cluster`、`iris_dataset`）。上面的代码仅展示了调用形式，并不是示例的一部分。我们可以在设计器中执行相同的流程，如图 3-5 所示。

![图 3-5 在步骤之间传递数据](img/03fig05.jpg)

### 图 3-5 在步骤之间传递数据

我们现在可以构建 Azure Machine Learning 流水线，并在流水线的步骤之间传递数据，甚至可以使用方法减少传递的数据量。在下一节中，我们将查看如何运行和调度流水线。

### 运行和调度流水线

训练和部署机器学习模型过程的一个关键方面是调度流水线作业的能力，这可以自动化常规任务，例如重新训练模型和批量预测。在本指南中，我们将探索如何通过编程在 Azure 上调度流水线运行，并有效地管理这些调度。

假设你正在从事一个机器学习项目，涉及预测订阅制服务的客户流失率。为了让你的模型与最新数据保持同步，你需要定期重新训练它。与其每周都手动触发重新训练过程，不如你决定通过在 Azure Machine Learning 中调度流水线作业来自动化此任务。

要调度流水线作业，你需要创建一个将作业与触发器关联的计划。触发器可以基于 cron 表达式或周期性模式。以下是如何使用 Azure CLI 使用周期性模式创建基于时间的计划：点击此处查看图像

```yaml
$schema: https://azuremlschemas.azureedge.net/latest/schedule.json
name: weekly_retraining_schedule
display_name: Weekly Retraining Schedule
description: Retrain the churn prediction model every week

trigger:
  type: recurrence
  frequency: week
  interval: 1
  schedule:
    days: [sunday]
    hours: [3]
    minutes: [0]
  start_time: "2024-04-07T03:00:00"
  time_zone: "Pacific Standard Time"

create_job: ./retrain_pipeline_job.yml
```

在这个示例中，流水线作业被调度为每周日太平洋标准时间凌晨 3:00 运行。你可能会问有哪些类型的计划可用以及它如何映射到你的特定用例——例如，如果你决定你的训练流水线需要按照特定计划运行以重新训练模型，这通过标准计划是可以实现的。

### 计划类型

在 YAML 中定义你的机器学习流水线只是创建高效且可扩展工作流的开始。一旦建立了流水线，下一步是确保它在适当的时间持续性地运行。在业务背景下，在调度器上进行调度和运行流水线至关重要，因为它们确保了你的机器学习模型定期进行训练、验证和更新，而无需人工干预。这种自动化方法提高了生产力，减少了错误风险，并确保你的模型能够保持准确并与最新数据同步。

Azure Machine Learning 支持各种类型的计划来触发你的流水线作业，允许你量定制执行以满足你特定的业务需求。周期性计划特别有用，因为它们根据指定的频率（例如每天、每周或每月间隔）触发作业。此外，你还可以定义详细的计划，指定具体的小时、分钟和星期几，以便对流水线的运行时间进行更精确的控制。

另一方面，cron 使用 cron 表达式来描述计划。例如，“0 3 * * 0” 将在每周日凌晨 3:00 触发作业。

创建计划后，你可以使用 Azure CLI 或 SDK 对进行管理。表 3-5 总结了一些常用任务及其示例。

#### 表 3-5 管理机器学习计划的命令

| 示例命令 | 任务 |
| --- | --- |
| `az ml schedule list` | 列出计划 |
| `az ml schedule show -n weekly_retraining_schedule` | 查看 `weekly_retraining_schedule` 详情 |
| `az ml schedule update -n weekly_retraining_schedule --set description="Updated description"` | 更新 `weekly_retraining_schedule` 的描述 |
| `az ml schedule disable -n weekly_retraining_schedule` | 禁用 `weekly_retraining_schedule` |
| `az ml schedule enable -n weekly_retraining_schedule` | 启用 `weekly_retraining_schedule` |
| `az ml schedule delete -n weekly_retraining_schedule` | 删除 `weekly_retraining_schedule` |

首先，导航到 Azure 门户并选择“创建资源”（Create A Resource）。搜索 Application Insights 并按照提示设置新实例。创建实例后，从 Application Insights 资源的“概览”（Overview）或“属性”（Properties）部分获取连接字符串。该连接字符串将您的 Azure Machine Learning 工作区与 Application Insights 关联，从而实现两个服务之间的无缝集成和数据流。

通过将您的 Azure Machine Learning 实验配置为将遥测数据发送到 Application Insights，可以提供极具价值的信息，包括实时性能指标、错误日志和自定义事件。例如，您可以跟踪模型预测的延迟和吞吐量，识别流水线中的瓶颈，并监控资源利用率。这些洞察允许您对数据科学解决方案进行主动管理，确保运行的高效有效，最终获得更可靠、更准确的机器学习结果。

## 在您的流水线中配置日志记录

在流水线中记录日志是管理和调试机器学习工作流的一个基本方面，特别是在像 Azure Machine Learning 这样的云环境中。有效的日志记录可以提供流水线各个阶段的可视性，允许您跟踪任务进度、捕获错误并记录关键指标。在数据科学的背景下，这种详尽程度对于理解模型性能、识别问题以及确保工作流顺畅运行是无价之宝。

在您的 Azure Machine Learning 流水线中设置全面的日志记录涉及配置每个步骤以输出相关日志。这些日志可以捕获广泛的信息，从简单的打印语句到详细的系统指标和错误消息。通过将将这些日志重定向到集中位置，例如 Azure Log Analytics 或 Application Insights（Azure Log Analytics 用于集中式日志管理和分析，而 Azure Application Insights 侧重于监控性能、可用性和使用情况），您可以获得流水线性能的统一视图。这种集中日志记录方法在云环境中特别有用，因为资源是分布式的，任务通常是异步执行的。

在云环境中记录日志至关重要，原因有几个：首先，它实现了实时监控和告警，允许您在问题出现时迅速响应。这种能力对于维护数据科学解决方案的可靠性和性能至关重要。其次，日志提供了流水线执行的历史记录，可用于审计、合性和追溯分析。这些历史数据有助于识别模式、诊断反复出现的问题，并对优化和改进做出明智决策。在 Azure Machine Learning 的背景下，有效的日志记录实践确保您的机器学习工作流是透明、可追溯且具有韧性的，最终带来更稳健、更可信的数据科学结果。

我们需要使用 Python 脚本步骤进行日志记录。您可以将该步骤添加到流水线并按如下所示配置连接字符串：

1. 向您的 Azure Machine Learning 流水线添加一个 `PythonScriptStep`；我们将使用它进行日志记录。

2. 配置您的 `RunConfiguration`，添加对 `opencensus-ext-azure` 的依赖。

3. 在您的 `RunConfiguration` 中设置 `APPLICATIONINSIGHTS_CONNECTION_STRING` 环境变量。

以下是此脚本步骤的 Python 代码示例：

点击此处查看代码图像

```python
from azureml.core.runconfig import RunConfiguration
from azureml.pipeline.steps import PythonScriptStep
from azureml.core.conda_dependencies import CondaDependencies
dependencies = CondaDependencies()
dependencies.add_pip_package("opencensus-ext-azure>=1.0.1")

run_config = RunConfiguration(conda_dependencies=dependencies)
run_config.environment.environment_variables = {
 "APPLICATIONINSIGHTS_CONNECTION_STRING": 'InstrumentationKey=your_instrumentation_key'
}

sample_step = PythonScriptStep(
 script_name="sample_step.py",
 compute_target=compute_target,
runconfig=run_config
)
```

一旦我们有了脚本步骤，就需要在脚本步骤中实现日志记录。您可以通过导入 `AzureLogHandler`（用于写入日志）并将此日志处理器添加到 Python 日志器来实现这一点。以下代码块显示了如何使用 `logging` 模块创建日志对象并配置处理器：

点击此处查看代码图像

```python
from opencensus.ext.azure.log_exporter import AzureLogHandler
import logging
logger = logging.getLogger(__name__)
logger.setLevel(logging.DEBUG)
logger.addHandler(logging.StreamHandler())
logger.addHandler(AzureLogHandler())
logger.warning("This log will be sent to Application Insights")
```

## 使用自定义维度记录日志

使用自定义维度创建结构化日志如何？为了给您的日志消息提供上下文，您可以添加自定义维度，例如 `parent_run_id`、`step_id`、`step_name`、`experiment_name` 和 `run_url`。

点击此处查看代码图像

```python
from azureml.core import Run
run = Run.get_context(allow_offline=False)
custom_dimensions = {
 "parent_run_id": run.parent.id,
 "step_id": run.id,
 "step_name": run.name,
 "experiment_name": run.experiment.name,
"run_url": run.parent.get_portal_url(),
"run_type": "training"
}
logger.info("Log with Custom Dimensions", extra={"custom_dimensions":
custom_dimensions})
```

自定义维度是 Azure Machine Learning 中创建结构化日志的一项强大功能，为您的日志消息添加了有价值的上下文。通过结合 `parent_run_id`、`step_id`、`step_name`、`experiment_name` 和 `run_url` 等自定义维度，您可以用详细的元数据丰富您的日志，使其更易于搜索、过滤和分析。这些自定义维度帮助您理解生成每个日志条目的广泛上下文，提供有关流水线特定部分及其如何与整体工作流相关的洞察。

例如，在日志中包含 `parent_run_id` 允许您将所有活动追溯到主流水线运行，提供执行流的完整视图。`step_id` 和 `step_name` 维度有助于精确定位流水线中的哪个步骤生成了日志条目，这对于识别错误或性能瓶颈发生的位置特别有用。通过用 `experiment_name` 为每条日志标记，可以轻松地分组和比较不同实验的日志，便于跨实验分析和调试。

此外，`run_url` 维度提供了指向 Azure Machine Learning Studio 的直接链接，您可以在那里查看有关运行的更详细信息。这种集成增强了调试过程的效率，允许您从日志项快速导航到 Azure ML 界面中的相应运行详细。通过利用这些自定义维度，您创建了一个结构化日志记录框架，这不仅提高了日志的粒度和清晰度，还显著增强了您在云环境中管理和优化机器学习工作流的能力。

带有自定义维度的结构化日志在云环境中尤为重要，原因有以下几点：首先，它通过支持更复杂的查询和分析，提升了日志的可管理性。在处理海量日志数据时，能够根据 `experiment_name` 或 `step_name` 等特定维度过滤日志，可以节省大量的时间和精力。其次，结构化日志有助于与监控和告警系统更好地集成。例如，你可以根据特定的日志维度设置告警，以便通知你与特定步骤或实验相关的问题。这种主动的监控方法有助于确保你的数据科学解决方案的可靠性和性能。

在日志策略中引入自定义维度还支持合规性和审计要求。通过维护详尽且结构化的日志，你可以为你的机器学习工作流提供清晰、全面的审计追踪。这种透明度对于监管合规以及与依赖你的数据科学解决方案的利益相关者建立信任至关重要。在 Azure Machine Learning 的背景下，带有自定义维度的结构化日志不仅增强了工作流的技术稳健性，还有助于其整体信度和可责性。

## 在 Application Insights 中查询日志

一旦你的流水线运行被记录到 Application Insights 中，你就获得了查询和分析日志的强大能力。Application Insights 提供了在 `'traces'` 和 `'exceptions'` 等类别下访问日志的功能，允许你高效地过滤和剖析日志数据。这种细粒度在数据科学背景下特别有用，因为理解机器学习工作流的复杂性会显著影响模型的性能和可靠性。通过利用这些功能，你可以跟踪流水线运行的行为，定位问题，并收集见解以优化你的流程。

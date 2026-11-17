

可以在 Grafana 中添加告警规则、标签和通知策略。下图显示了 Grafana 中的 Alert UI：

![](img/cc4299656808e62a294f1843a1e18e72_426_0.png)

图 14.13：Grafana—告警 UI

## 使用 whylogs 和 WhyLabs 进行 ML 模型监控

WhyLabs 是一个模型监控和可观测性平台，用于监控数据漂移、模型性能下降、数据质量、模型评估指标，并向团队或个人发送告警。它建立在开源包 **whylogs** 之上。你可以使用 WhyLabs Observability Platform 持续监控 whylogs 配置文件。

WhyLabs 的主要特性如下：

- **设置时间短**：你可以先安装轻量级开源库 whylogs，使用 **pip install whylogs**。片刻之后，即可生成数据集的摘要，即 whylogs 配置文件，这可帮助你完成以下操作：
  - 跟踪数据集的变化
  - 可视化数据集的汇总统计信息
  - 通过定义数据约束来检查数据质量

- **无缝集成**：它可以轻松与现有的数据管道、模型生命周期、模型框架和 MLOps 生态系统集成。

- **数据隐私**：WhyLabs 使用 whylogs 代理创建的数据统计摘要，因此你的实际数据不会被传输或存储在 WhyLabs 平台上。

- **可扩展性**：它可以轻松扩展以处理大量数据和多个项目。

- **集中监控**：使用 WhyLabs 平台，你可以在单一框架下监控多个项目。它允许你在单个帐户中创建多个隔离项目，并且还会跟踪输入和输出数据、模型性能等。

## whylogs

废话不多说，让我们开始使用 whylogs 的日志记录功能。首先，如果尚未安装 whylogs，请使用 **pip install whylogs** 进行安装。接着，导入贷款预测数据集并使用 whylogs 开始记录它。

```
1. # Import packages
2. import numpy as np
3. import pandas as pd
4. from sklearn.model_selection import train_test_split
5. pd.set_option("display.max_columns", None) #To show all columns in DataFrame
6. import whylogs as why
7.
8. df = pd.read_csv("https://gist.githubusercontent.com/suhas-ds/a318d2b1dda8d8cbf2d6990a8f0b7e8a/raw/9b548fab0952dd12b8fdf057188038c8950428f1/loan_dataset.csv")
9.
10. profile1 = why.log(df)
11. profile_view1 = profile1.view()
12. profile_view1.to_pandas()
```

要查看统计摘要，即 whylogs 配置文件，请将其转换为 pandas DataFrame。配置文件的 pandas DataFrame 包含以下指标：

- cardinality/est
- cardinality/lower_1
- cardinality/upper_1
- counts/n
- counts/null
- distribution/max
- distribution/mean
- distribution/median
- distribution/min
- distribution/n
- distribution/q_01
- distribution/q_05
- distribution/q_10
- distribution/q_25
- distribution/q_75
- distribution/q_90
- distribution/q_95
- distribution/q_99
- distribution/stddev
- frequent_items/frequent_strings
- ints/max
- ints/min
- type
- types/boolean
- types/fractional
- types/integral
- types/object
- types/string

这涵盖了关于输入数据的几乎所有所需信息，例如基数、类型、频繁项、分布和计数。

### 用于数据质量验证的约束

使用 whylogs，你可以使用约束来执行数据验证。此功能可用于单元测试或 CI/CD 管道，以便避免进一步的错误。你可以对配置文件指标设置约束，例如计数、分布和类型。whylogs 还支持用户定义的自定义指标。你需要一个 whylogs 配置文件来在数据上设置约束。

设置新约束很简单；你需要为以下内容赋值：

- name：可以是任何字符串，用于描述约束。
- condition：它是 lambda 表达式。
- metric_selector：它是要测量或验证的指标类型。

```
from whylogs.core.constraints import (Constraints,
ConstraintsBuilder,
```

```
3. MetricsSelector,
4. MetricConstraint)
5.
6. # Function with Constraints for Data Quality Validation
7. def validate_feat(profile_view, verbose=False, viz=False):
8. builder = ConstraintsBuilder(profile_view)
9. # Define a constraint for data validation
10. builder.add_constraint(MetricConstraint(
11. name="Credit_History == 0 or == 1",
12. condition=lambda x: x.min == 0 or x.max == 1,
13. metric_selector=MetricsSelector(metric_name='distribution',
14. column_name='Credit_History')
15. ))
16.
17. # Build the constraints and return the report
18. constraints: Constraints = builder.build()
19.
20. if verbose:
21. print(constraints.report())
22.
23. # return constraints.report()
24. return constraints
25.
26. const = validate_feat(profile_view1, True)
```

在当前场景中，约束设置为确保 **Credit_History** 特性应仅包含 **0** 或 **1**。如果接收到 **0** 或 **1** 之外的任何值，将验证失败。你可以添加多个约束来一次性验证多个条件。以下是前面代码的输出：

```
[('Credit_History == 0 or == 1', 1, 0)]
```

这可以理解为 [('约束名称', 通过, 失败)]。可以在笔记本中使用 whylogs 的可视化功能对其进行可视化。

```
1. from whylogs.viz import NotebookProfileVisualizer
2. visualization = NotebookProfileVisualizer()
3. visualization.constraints_report(const, cell_height=300)
```

图 14.14 描绘了约束报告，即前面代码的输出，用于可视化约束的结果：

![](img/cc4299656808e62a294f1843a1e18e72_430_0.png)

图 14.14：whylogs-约束报告

为了一次性验证所有约束，你可以直接在约束的结果上使用 **validate()**。

```
1. # check all constraints for passing:
2. constraints_valid = const.validate()
3. print(constraints_valid)
```

由于它仅验证一个条件，将检查该条件是否为 true。由于 **Credit_History** 特性中的数据包含 **0** 或 **1**，测试通过并打印 **True**。

**True**

接下来，使用少量代码，你可以生成漂移报告。为此，你需要数据的两个 whylogs 配置文件：目标配置文件和参考配置文件。

```
1. from whylogs.viz import NotebookProfileVisualizer
2.
3. visualization = NotebookProfileVisualizer()
4. visualization.set_profiles(target_profile_view=profile_view1, reference_profile_view=profile_view2)
5.
6. visualization.profile_summary()
7.
8. visualization.summary_drift_report()
```

使用 summary_drift_report()，你可以获取易于阅读的漂移报告。它是两个配置文件之间按功能进行的交互式比较。此报告包含以下内容：

- Target：目标配置文件的直方图
- Reference：参考配置文件的直方图
- p-value：范围从 0 到 1
- Total count：数据集中记录或实例的计数
- Mean：数值特征的平均值

## WhyLabs

下一步是开始将这些配置文件上传到 WhyLabs 平台。

第一步是在 https://whylabs.ai/whylabs-free-sign-up 注册帐户。如果已经完成此步骤，请登录帐户。接着，在项目管理部分创建新项目。根据要求，有不同类型的项目可供选择，例如 ML 模型和数据管道。在此场景中，选择分类（即 ML 项目），以便你可以分析模型的性能和输入输出数据。

如下图所示，将项目名称提供为 ML_monitor（稍后可以更新），类型提供为 Classification：

![](img/cc4299656808e62a294f1843a1e18e72_431_0.png)

图 14.15：WhyLabs—项目管理


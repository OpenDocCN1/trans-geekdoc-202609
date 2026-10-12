

## 函数 `fetch_eval_info`

函数 `fetch_eval_info` 将从训练好的模型工件中获取评估数据，这些数据将被传递给 `metrics_log_check` 函数，以检查模型性能是否高于阈值，并返回值为 `true`（如果模型性能优于阈值）或 `false`（否则）。

```python
@dsl.pipeline(
    # 默认流水线根目录。提交流水线时可覆盖它。
    pipeline_root=PIPELINE_ROOT,
    # 流水线的名称。用于确定流水线上下文。
    name="employee-pipeline-rf",
)
def pipeline(
    bq_table: str = "vertex-ai-gcp-1.employee_data.employee_promotion_data",
    project: str = PROJECT_ID,
    region: str = REGION,
    display_name: str = 'pipeline-employeepromotion-rf-job{}'.format(datetime.now().strftime("%Y%m%d%H%M%S")),
):
    data = get_data(bq_table)
    data_transformed = data_transformation(data.outputs["output_data_path"])
    train_model = emp_promotion_training(data_transformed.outputs["dataset_train"])
    model_evaluation_op = model_evaluation(
        test_set=data_transformed.outputs["dataset_test"],
        trained_model=train_model.outputs["model"],
    )
```

## 步骤 12：使用 Kubeflow 编译

运行以下代码以编译流水线代码。Kubeflow Pipelines SDK v2 编译器会验证流水线中正确的数据类型用法，以及避免将来自参数的输入用作来自工件的输出，反之亦然：

```python
compiler.Compiler().compile(pipeline_func=pipeline, package_path='employee_promotion_prediction_rf.json')
```

## 步骤 13：创建流水线

运行以下代码以创建流水线：

```python
pipeline_run_rf = pipeline_jobs.PipelineJob(
    display_name="employee_promotion_ml_pipeline_rf",
    template_path="employee_promotion_prediction_rf.json",
    enable_caching=True,
    location=REGION,
)
```

## 步骤 14：提交流水线作业

运行以下代码以提交流水线作业。代码执行后将提供链接，用于查看流水线，如 [图 7.10](#ch07.xhtml#fig7-10) 所示：

```python
pipeline_run_rf.run()
```

![](images/Figure_7.10.png)

**图 7.10：** 笔记本文件中的流水线链接

1.  提交流水线作业后，将提供一个链接以检查流水线的状态。点击它。

## 流水线

请遵循以下步骤来分析流水线作业、工件、谱系和输出的状态：

### 步骤 1：自定义模型的流水线

打开 [图 7.10](#ch07.xhtml#fig7-10) 中所示的链接，导航至 Vertex AI 的流水线。流水线将开始执行，大约需要 5 到 10 分钟。练习中的所有四个任务将按顺序执行。流水线完全执行完毕后，您将看到所有组件上都有绿色的勾号，如 [图 7.11](#ch07.xhtml#fig7-11) 所示：

![](images/Figure_7.11.png)

**图 7.11：** 流水线创建并成功执行

1.  表示流水线中的所有步骤均已成功执行。
2.  点击流水线的 **SUMMARY（摘要）** 部分。
3.  基本信息提供流水线运行、区域、查看日志的链接等信息。
4.  运行参数提供流水线所用参数的相关信息。向下滚动可在摘要部分获取运行指标。
5.  点击切换按钮以展开工件。

### 步骤 2：展开工件

工件将在流水线中展开，如 [图 7.12](#ch07.xhtml#fig7-12) 所示：

![](images/Figure_7.12.png)

**图 7.12：** 流水线的组件和工件

1.  带有勾号的方框表示流水线的组件。其他的则是流水线的工件。点击它们。
2.  点击 **NODE INFO（节点信息）**。
3.  存储工件的云存储位置。
4.  点击 **VIEW LINEAGE（查看谱系）**。

### 步骤 3：流水线的谱系

当您使用 Vertex AI Pipelines 执行流水线时，流水线运行的工件和参数会记录在 Vertex ML Metadata 中。Vertex ML Metadata 通过免除用户维护流水线信息的负担，便于分析项目的来源。制作工件所用的一切，以及任何衍生对象或信息，都是其谱系的一部分。

流水线的谱系将在单独的标签页中打开，如 [图 7.13](#ch07.xhtml#fig7-13) 所示：

![](images/Figure_7.13.png)

**图 7.13：** 流水线的谱系

### 步骤 4：流水线中记录的指标和 KPI

训练模型的指标将在工件中提供，如 [图 7.14](#ch07.xhtml#fig7-14) 所示：

![](images/Figure_7.14.png)

**图 7.14：** 模型的指标

1.  点击流水线的指标工件。
2.  在流水线的最后一个组件中，我们记录了混淆矩阵和 ROC 曲线（向下滚动查看）。

训练模型的 KPI 将在工件中提供，如 [图 7.15](#ch07.xhtml#fig7-15) 所示：

![](images/Figure_7.15.png)

**图 7.15：** 模型的 KPI

1.  点击流水线的 KPI 工件。
2.  在流水线的最后一个组件中，我们记录了模型的准确率和其他 KPI，这些指标将显示出来。

### 步骤 5：存储在云存储中的流水线工件

流水线工件存储在云存储中，如下图所示。为流水线不同组件的工件创建了单独的文件夹：

![](images/Figure_7.16.png)

**图 7.16：** 存储在云存储中的工件

## 流水线对比

用户可能会使用不同的模型或不同的数据样本运行多个流水线。GCP 为用户提供了对比不同流水线性能的选项。

在本练习中，我们构建了一个用于训练随机森林分类器模型的流水线。将随机森林更改为您选择的任何其他模型并运行流水线（决策树分类器可用于此场景，只需对代码进行最少的更改）。导入所需的包并在代码中进行必要的更改（流水线的第三和第四个组件）。更改 JSON 文件的名称和流水线名称。编译并提交流水线作业以执行。

流水线成功执行后，请遵循以下步骤对比流水线。

### 步骤 1：Vertex AI 的流水线模块

所有执行过的流水线都将列在流水线部分下，如 [图 7.17](#ch07.xhtml#fig7-17) 所示：

![](images/Figure_7.17.png)

**图 7.17：** Vertex AI 的流水线模块

1.  转到 Vertex AI 的流水线模块。
2.  选择要对比的流水线。
3.  点击 **COMPARE（对比）**。

### 步骤 2：流水线对比

使用流水线对比，用户可以对比所用的流水线参数、流水线的输出指标和 KPI，如 [图 7.18](#ch07.xhtml#fig7-18) 所示：

![](images/Figure_7.18.png)

**图 7.18：** 流水线对比

## 资源删除

我们使用了 Workbench、BigQuery 来存储数据，以及云存储来存储流水线的工件。请确保删除 Workbench，清除云存储和 BigQuery 中存储的数据。

## Vertex AI 与 Kubeflow 流水线的区别

下面列出了 Vertex AI 流水线与 Kubeflow 流水线之间的一些重要区别：

*   **领域特定语言 (DSL) 版本：** 使用 TFX v0.30.0 或更高版本以及 Kubeflow Pipelines SDK v2 领域特定语言 (DSL) 创建的流水线可以在 Vertex AI 流水线上执行。只有 Kubeflow Pipelines SDK 可用于 Kubeflow 流水线执行。
*   **存储：** Kubeflow Pipelines 可以使用持久卷声明等 Kubernetes 资源，而 Vertex AI 使用云存储进行数据存储（使用 Cloud Storage FUSE 挂载到组件）。
*   **递归：** Vertex AI 不支持递归调用的流水线组件，而 Kubeflow 支持。

## 结论


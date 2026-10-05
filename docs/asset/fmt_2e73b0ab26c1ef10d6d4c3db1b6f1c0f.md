
## 9.3 游览开源工作流编排系统

### 核心特性

`Argo Workflows` 提供了以下功能：

- 低安装维护成本 —— `Argo Flows` 原生运行在 `Kubernetes` 上，安装非常简单；通过几个 `kubectl` 命令即可让 `Argo Flows` 运行。
- 健壮的工作流执行 —— `Kubernetes` pod 创建了良好的隔离。`Argo Flows` 还支持定时工作流和任务重试。
- 模板化和组合 —— `Argo Flows` 模板类似于函数。在构建工作流时，`Argo` 支持组合模板。这种组合性鼓励跨团队共享工作，极大提高了生产力。
- 功能全 UI —— `Argo Flows` 提供了方便的 UI 来管理工作流的整个生命周期，例如提交/停止工作流、列出所有工作流以及工作流定义。
- 高灵活适用 —— `Argo Flows` 定义了 `REST API` 来管理系统并添加新功能（插件），工作流通过 `Docker` 镜像定义。这些功能使得 `Argo Flows` 高度定制并广泛应用于许多领域，如 `ML`、`ETL`、批处理和 `CI/CD`。
- 生产级 —— `Argo Flows` 设计用于在严肃的生产环境中运行。`Kubernetes` pipeline 和 `Argo CD` 是 `Argo Flows` 生产化的优秀范例。

### 局限性

在深度学习系统中使用 `Argo` 的缺点如下：

- 每个人都要编写和维护 `YAML` 文件 —— `Argo Flows` 要求工作流定义为 `YAML` 文件中的 `Kubernetes` CRD。单个项目的短 `YAML` 文件尚可管理，但随着工作流数量增加和工作流逻辑变得复杂，`YAML` 文件可能会变得冗长且混乱。虽然 `Argo Flows` 提供模板来保持工作流定义的简单，但除非习惯操作 `Kubernetes` `YAML` 配置，否则并不直观。
- 必须是 `Kubernetes` 专家 —— 如果你是 `Kubernetes` 专家，你会觉得它非常自然。新手可能需要花时间学习 `Kubernetes` 的概念和实践。
- 执行延迟 —— 在 `Argo Flows` 中，对于每个新任务，`Argo` 会启动一个新的 `Kubernetes` pod 来执行。Pod 的启动会每个任务执行引入几秒到几分钟的延迟，这限制了 `Argo` 支持时间敏感型工作流的能力。例如，`Argo` 不适合实时模型预测工作流（该流需要毫秒级 SLA 的模型预测请求）。

## 9.3.3 Metaflow

`Metaflow` 是一个专注于 `MLOps` 的易用型 `Python` 库。它最初由 `Netflix` 开发，并于 2019 年开源。`Metaflow` 的特殊之处在于它遵循了以人为中心的设计；它不仅为自动化工作流而构建，还旨在减少深度学习项目开发中花费的人工时间（运营成本）。

在第 9.1.3 节中，我们指出了从原型到生产工作流的转换在 `ML` 开发中产生了大量的摩擦。数据科学家必须为每次模型开发迭代构建并测试新版本的工作流。为了弥补原型与生产之间的差距，`Metaflow` 做了两个改进：首先，它简化了工作流的构建；其次，它使用了本地与生产环境之间的工作流执行体验（见图 9.7）。

![](img/9dbecddeac1b6cad2e240ace2b0d4b22_286_0.png)

图 9.7 `Metaflow` 在原型和生产之间提供了统一的开发体验。

在 9.7 中，我们可以看到 `Metaflow` 将原型环境和生产环境都视为一等执行环境。因为 `Metaflow` 库提供了一套统一的 API 来抽象底层基础设施，无论工作流运行在哪个环境中，都可以以相同的方式执行。例如，工作流可以由本地调度器运行也可以由生产调度器运行，而无需任何更改。本地调度器在本地执行工作流，而生产调度器则集成到其他生产编排系统中，例如 `AWS Step Functions` 或 `Argo Workflows`。

# 第 9 章 工作流编排

`Metaflow` 允许通过标记 `Python` 代码（一个 DAG `Python` 类）来定义工作流。`Metaflow` 库随后根据 `Python` 注解自动创建工作流。通过 `Metaflow` 注解，`Vena` 可以在不改变任何原型代码的情况下构建工作流。

除了工作流的创建和测试外，`Metaflow` 还提供了其他模型可复现性的关键功能，如工作流步骤的版本控制以及输入保存。要了解更多关于 `Metaflow` 的信息，你可以查看 `Metaflow` 官方网站（https://docs.metaflow.org/）以及 `Ville Tuuos` 写的佳作《Effective Data Science Infrastructure》（Manning, 2022; https://www.manning.com/books/effective-data-science-infrastructure）。

### 典型案例

让我们使用 `Metaflow` 自动化处理我们在 9.3.1 节和 9.3.2 节中处理相同的数据。请参考下面的伪代码。

+ 列表 9.3 一个示例 `Metaflow` 工作流

```python
# python 类中的工作流 DAG
class DataProcessWorkflow(FlowSpec):

    @parameter("source") 作为工作流的输入参数
    datasource = Parameter(
        "datasource_path", help="数据处理的数据存储位置",
        required=True
    )

    @step
    def start(self):
        # 参数 "self.data_source" 在所有步骤中均可用。
        self.newdata_path = dataUtil.fetch_new_data(self.data_source)
        self.next(self.transform_data)

    @step
    def transform_data(self):
        self.new_data = dataUtil.convert(self.newdata_path)
        # 数据传输后输出到两个并行分支。
        self.next(self.save_to_db, self.notify_data_science_team)

    @step
    def save_to_db(self):
        dataUtil.store_data(self.new_data)
        self.next(self.join)

    @step
    def notify_data_science_team(self):
        slackUtil.send_notification(messageUtil.build_message(self.new_data))
        self.next(self.join)

# 合并两个并行分支步骤
# notify_data_science_team 和 save_to_db
```

上传自 >> dr-notes.com

```python
@step
def join(self, inputs):
    self.next(self.end)

@step
def end(self, inputs):
    # 结束流程。
    pass

if __name__ == "__main__":
    DataProcessWorkflow()
```

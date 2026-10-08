

```python
s_customer_churn = s_customer_churn.coalesce(1)
s_customer_churn.write.option("header", "true")
format("csv").mode('overwrite').save(output_dir)
logger.info("output_dir: " + output_dir)
```

作业完成后，请检查 S3 中的 `s3://MLSA-DataLake-Serving-<your initials>/ml-customer-churn/<date>/<guid>/` 路径，查看是否生成了新的 csv 文件。打开该文件，查看在文件中是否看到了处理后的数据集。

你现在已成功构建了一个 AWS Glue 作业，用于用于机器学习的数据处理和特征工程。现在，通过创建一个爬虫（crawler）来爬取 `MLSA-DataLake-Serving-<your initials>` 存储桶中新处理的数据，使其在 Glue 目录中可用，并对其运行一些查询。你应该能看到创建一个新表，其中包含多个分区（例如 `ml-customer-churn`、`date` 和 `GUID`），对应不同的训练数据集。你可以使用 GUID 分区作为查询条件查询数据。

# 使用 Glue 工作流构建数据流水线

现在，创建一个流水线，它将运行一个数据摄取作业，然后为数据创建数据库目录，并运行数据处理作业以生成训练数据集：

- 首先，点击 Glue 管理控制台左侧面板中的“Workflows”（工作流）链接。

- 点击“Add Workflow”（添加工作流），并在下一个屏幕上为你的工作流输入名称。然后，点击“Add Workflow”按钮。

- 选择你创建的工作流并点击“Add Trigger”（添加触发器）。选择“Add New”（新建）选项卡，然后为触发器输入名称，并选择“on-demand”（按需）触发器类型。

- 在 UI 设计器中，你将看到出现一个新的“Add Node”（添加节点）图标。点击“Add Node”图标，选择“Crawler”（爬虫）选项卡，并选择 `bank_customer_db_crawler`，然后点击“Add”（添加）。

- 在 UI 设计器中，点击爬虫图标，你将看到出现了一个新的“Add Trigger”（添加触发器）图标。点击“Add Trigger”图标，选择“Add new”选项卡，选择“After ANY event”（任何事件发生后）作为触发器逻辑，然后点击“Add”（添加）。

- 在 UI 设计器中，点击“Add Node”图标，选择“jobs”（作业）选项卡，并选择 `customer_churn_process` 作业。

7. 在工作流 UI 设计器上，最终的工作流应该看起来所示所示：

![](img/bd21298357d8484151447cff0b2f138b_140_0.png)

图 4.7 - Glue 数据流设计

8. 现在，你已准备好运行工作流。选择该工作流，并在“Actions”（操作）下拉列表中选择“Run”（运行）。你可以通过选择 Run ID 并点击“View run details”（查看运行详情）来监控运行状态。你应该能看到类似于下面的截图：

![](img/bd21298357d8484151447cff0b2f138b_140_1.png)

图 4.8 - Glue 工作流执行

9. 尝试删除 `customer_data` 和 `churn_list` 表并重新运行工作流。查看是否创建了新表。检查 `s3://MLSA-DataLake-Serving-<your initials>/ml-customer-churn/<date>/` S3 位置，验证是否创建了带有新数据集的新文件夹。

恭喜！你已经完成了实验，并学习了如何构建一个简单的数据湖及其支持组件，以实现数据目录、数据查询和数据处理。

# 总结

在本章中，我们涵盖了机器学习的数据管理考虑因素，以及企业级数据管理平台对于机器学习的形态。现在，你应该了解数据管理与机器学习生命周期的交点，以及如何在 AWS 上设计数据湖架构。为了将所学付实践，你还使用 Lake Formation 构建了数据湖。你练习了用于数据发现、查询和下游机器学习任务的数据摄取、处理和数据建模。你还培养了使用 AWS 数据管理工具的实战技能。


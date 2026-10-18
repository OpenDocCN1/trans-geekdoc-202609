

1. 单击 `Save`，然后单击 `Run job` 按钮以运行作业。通过单击 Glue 控制台中的 `ETL jobs` 链接来检查作业运行状态，然后单击 `Job run monitoring`。

2. 作业完成后，检查 S3 中的 `s3://MLSA-DataLake-Serving-<your initials>/ml-customer-churn/<date>/<guid>/` 位置，查看是否生成了新的 CSV 文件。打开文件，查看文件中是否包含新的处理后的数据集。

您现在已成功构建用于数据处理和机器学习特征工程的 AWS Glue 作业。借助此作业，您可以自动化数据处理和特征工程，这对于实现可重复性和治理至关重要。尝试创建一个爬虫来爬取 `MLSA-DataLake-Serving-<your initials>` 存储桶中新处理的数据，以便将其提供到 Glue 目录中并针对其运行一些查询。您应该会看到为不同训练数据集创建了带有多个分区（例如 `ml-customer-churn`、`date` 和 `GUID`）的新表。您可以使用 `GUID` 分区作为查询条件来查询数据。

## 使用 Glue 工作流构建数据管道

接下来，我们将构建一个执行数据摄取作业，然后创建数据的数据库目录的管道。最后，将启动一个数据处理作业以生成训练数据集。该管道将自动化数据从源到所需格式的流动，确保机器学习模型训练的数据处理无缝且高效：

1. 首先，单击 Glue 管理控制台左侧窗格中的 `Workflows (orchestration)` 链接。

2. 单击 `Add workflow`，并在下一屏幕为您的工作流输入名称。然后，单击 `Create workflow` 按钮。

3. 选择您刚刚创建的工作流，然后单击 `Add trigger`。选择 `Add New` 选项卡，然后为触发器输入名称并选择 `on-demand` 触发器类型。

4. 在工作流 UI 设计器中，您将看到一个新的 `Add Node` 图标出现。单击 `Add Node` 图标，选择 `Crawler` 选项卡，然后选择 `bank_customer_db_crawler`，接着单击 `Add`。

5. 在工作流 UI 设计器中，单击 `Crawler` 图标，您将看到一个新的 `Add Trigger` 图标出现。单击 `Add Trigger` 图标，选择 `Add new` 选项卡，并选择 `Start after ANY event` 作为触发逻辑，然后单击 `Add`。

6. 在工作流 UI 设计器中，单击 `Add Node` 图标，选择 `Jobs` 选项卡，然后选择 `customer_churn_process` 作业。

7. 在工作流 UI 设计器中，最终工作流应如下图所示：

![](OEBPS/Images/B20836_04_08.png)

图 4.8: Glue 数据流设计

1. 现在，您已准备好运行工作流。选择工作流，然后从 `Actions` 下拉菜单中选择 `Run`。您可以通过选择 `Run ID` 并单击 `View run details` 来监控运行状态。您应该会看到类似于以下屏幕截图的内容：

![](OEBPS/Images/Image2513.jpg)

图 4.9: Glue 工作流执行

1. 尝试删除 `customer_data` 和 `churn_list` 表，然后重新运行工作流。查看是否重新创建了新表。检查 `s3://MLSA-DataLake-Serving-<your initials>/ml-customer-churn/<date>/` S3 位置，以验证是否创建了包含新数据集的新文件夹。

恭喜！您已完成实操实验，并学习了如何构建简单的数据湖及其支持组件，以实现数据目录编目、数据查询和数据处理。您现在应该能够将所学的一些技能应用于 AWS 上数据管理平台的实际设计和实施，以支持机器学习开发生命周期。

# Summary

在本章中，我们深入探讨了在机器学习背景下管理数据的注意事项，并探索了用于机器学习的企业数据管理平台的架构。我们研究了数据管理与机器学习生命周期的交叉点，并学习了如何在 AWS 上设计数据湖架构。为了应用这些概念，我们经历了使用 AWS Lake Formation 构建数据湖的过程。

通过实操经验，我们练习了用于数据发现、查询和机器学习任务的数据摄取、处理和目录编目。此外，我们还熟练掌握了使用 AWS 数据管理工具，例如 `AWS Glue`、`AWS Lambda` 和 `Amazon Athena`。在下一章中，我们的重点将转移到使用开源工具构建数据科学环境所涉及的架构和技术。

# Leave a review!

喜欢这本书吗？通过留下 Amazon 评论来帮助像您一样的读者。扫描下方的二维码，获取您选择的免费电子书。

![](OEBPS/Images/Review_Copy.png)

`*Limited Offer*`

# 5

# 探索开源机器学习库

有大量的 `machine learning` (`ML`) 和数据科学技术可供选择，涵盖开源和商业产品。不同组织在构建其机器学习平台时采用了不同的方法。有些组织选择了内部团队，利用开源技术栈，从而实现更大的灵活性和定制性。其他组织则选择了商业产品，以专注于解决特定的业务和数据挑战。此外，一些组织采用了混合架构，结合开源和商业工具，以发挥两者的优势。作为机器学习解决方案架构师，了解可用的开源机器学习技术及其在构建强大机器学习解决方案中的应用至关重要。

在即将到来的章节中，我们将重点探讨用于实验、模型构建和机器学习平台开发的不同开源技术。在本章中，我们将深入探讨流行的机器学习库，包括 `scikit-learn`、`Spark`、`TensorFlow` 和 `PyTorch`。我们将研究这些库的核心功能，并演示如何在机器学习项目生命周期的各个阶段有效地利用它们，涵盖数据处理、模型开发和模型评估等任务。此外，您将有机会参与实操练习，获得这些机器学习库及其在模型训练中应用的实践经验。

具体来说，我们将涵盖以下主要主题：

* 开源机器学习库的核心功能

* 了解 `scikit-learn` 机器学习库

* 了解 `Apache Spark` 机器学习库

* 了解 `TensorFlow` 机器学习库和实操实验

* 了解 `PyTorch` 机器学习库和实操实验

* 如何在 `TensorFlow` 和 `PyTorch` 之间进行选择

# 技术要求

在本章中，您需要访问本地计算机，其中已安装来自 `Chapter 3`、`Exploring ML Algorithms` 的 `Jupyter` 环境。

您可以在 [https://github.com/PacktPublishing/The-Machine-Learning-Solutions-Architect-and-Risk-Management-Handbook-Second-Edition/tree/main/Chapter05](https://github.com/PacktPublishing/The-Machine-Learning-Solutions-Architect-and-Risk-Management-Handbook-Second-Edition/tree/main/Chapter05) 找到本章使用的代码示例。

# 开源机器学习库的核心功能

机器学习库是旨在促进机器学习算法和技术实现的软件库。虽然它们与其他软件库有相似之处，但使它们与众不同的是其对各种机器学习功能的专门支持。这些库通常通过不同的子包提供一系列功能，包括：

* 数据操作和处理：这包括对不同数据任务的支持，例如加载不同格式的数据、数据操作、数据分析、数据可视化、数据转换和特征提取。


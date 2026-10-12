
# 7. 您正在使用 TensorFlow 训练一个模型，该模型基于一个包含 5000 亿条记录的结构化数据集，数据存储在多个 CSV 文件中。您需要提高输入/输出执行性能。应该怎么做？

1.  将数据加载到 HDFS 中。
2.  将数据加载到 Cloud Bigtable，并使用 TF Bigtable 连接器从 Bigtable 读取数据。
3.  将 CSV 文件转换为 TFRecords 分片，并将数据存储在 Cloud Storage 中。
4.  使用 Dataflow 作业将数据加载到 BigQuery 中。

# 8. 您是一家游戏公司的高级解决方案架构师。您必须为手机游戏设计一个流式传输管道，以摄取玩家交互数据。您想对流式数据执行机器学习。为了构建开销最小的管道，应该怎么做？

1.  使用 Pub/Sub 配合 Cloud Dataflow 流式传输管道来摄取数据。
2.  使用 Apache Kafka 配合 Cloud Dataflow 流式传输管道来摄取数据。
3.  使用 Apache Kafka 配合 Cloud Dataproc 来摄取数据。
4.  使用 Pub/Sub Lite 流式传输连接器配合 Cloud Data Fusion。

# 9. 您是一名数据科学家，正在从事智慧城市项目，构建一个机器学习模型以检测实时传感器数据中的异常。您将使用 Pub/Sub 处理传入请求。您希望存储结果以供分析和可视化。应如何配置以下管道：

使用 Pub/Sub 摄取数据 → 1. 预处理 → 2. 机器学习训练 → 3. 存储 → 在 Data Studio 中可视化

1.  1. Dataflow，2. Vertex AI Training，3. BigQuery
2.  1. Dataflow，2. Vertex AI AutoML，3. Bigtable
3.  1. BigQuery，2. Vertex AI Platform，3. Cloud Storage
4.  1. Dataflow，2. Vertex AI AutoML，3. Cloud Storage

# 10. 您是一家金融科技公司的数据科学家。您想了解公司针对某金融产品的最新广告活动的效果如何。您已将 900 MB 的广告活动数据流式传输到 BigQuery。您想查询该表，然后在 Vertex AI 平台笔记本中使用 pandas DataFrame 操作查询结果。完成此操作所需的最少步骤数是多少？

1.  从 BigQuery 下载表作为本地 CSV 文件，并将其上传到您的 AI 平台笔记本实例。使用 pandas `read_csv` 将文件作为 pandas DataFrame 摄取。
2.  将表从 BigQuery 导出为 CSV 文件到 Google Drive，并使用 Google Drive API 将文件摄取到您的笔记本实例中。
3.  使用 Vertex AI 平台笔记本的 BigQuery 单元格魔术命令查询数据，并使用 pandas BigQuery 客户端将结果作为 pandas DataFrame 摄取。
4.  使用 `bq extract` 命令将表导出为 CSV 文件到 Cloud Storage，然后使用 `gsutil cp` 将数据复制到笔记本中。使用 pandas `read_csv` 摄取文件。

# 11. 您是一名正在研究欺诈检测模型的数据科学家。您将使用 Pub/Sub 处理传入请求。您希望存储结果以供分析和可视化。应如何配置以下管道：1. 摄取数据 → 2. 预处理 → 3. 机器学习训练并在 Data/Looker Studio 中可视化

1.  1. Dataflow，2. Vertex AI Training，3. BigQuery
2.  1. Pub/Sub，2. Dataflow，3. BigQuery ML
3.  1. Pub/Sub，2. Dataflow，3. Vertex AI Training
4.  1. Dataflow，2. Vertex AI AutoML，3. Cloud Storage

# 12. 您是一名为公共卫生团队工作的机器学习工程师，旨在创建一个管道来对 Google Cloud 上的支持工单进行分类。您分析了需求，决定使用 TensorFlow 构建分类器，以便完全控制模型的代码、服务和部署。您将使用 Kubeflow Pipelines 作为机器学习平台。为了节省时间，您希望利用现有资源并使用托管服务，而不是构建一个全新的模型。应如何构建分类器？

1.  使用成熟的文本分类模型，并按原样使用 Vertex AI Training 进行训练以对支持请求进行分类。
2.  使用成熟的文本分类模型，并使用 Vertex AI Training 进行训练以执行迁移学习。
3.  使用 AutoML Natural Language 构建支持请求分类器。
4.  使用 Natural Language API 对支持请求进行分类。

# 13. 您正在使用 Vertex AI 自定义作业训练一个具有大量分类特征的二元分类 TensorFlow 模型。您正在寻找 UI 工具来跟踪模型的指标，例如训练期间的 CPU 利用率、网络 I/O 和使用的特征。您会选择哪些工具？（选择两项。）

1.  交互式 Shell
2.  TensorFlow Profiler
3.  Jupyter Notebooks
4.  Looker Studio
5.  Looker

# 14. 您正在使用 Vertex AI 自定义作业训练一个 TensorFlow 模型以识别半成品。您想监控模型的性能。可以使用以下哪项？

1.  TensorFlow Profiler
2.  TensorFlow Debugger
3.  TensorFlow Trace
4.  TensorFlow Checkpoint

# 15. 您是一家初创公司的数据科学家，正在使用 TensorFlow 进行多个项目。您的数据采用 Parquet 格式，您需要管理输入和输出。您正在寻找在 Google Cloud 上训练 TensorFlow 模型时管理输入的最具成本效益的解决方案。应该使用以下哪项？

1.  TensorFlow I/O
2.  Cloud Dataproc
3.  Cloud Dataflow
4.  BigQuery 转 TFRecords

# 16. 您正在使用 Vertex AI 自定义作业训练一个具有许多分类特征的二元分类 TensorFlow 模型。您的经理询问了分类指标，并要求解释推理过程。您想向他们展示一个带有可视化图表的交互式演示。应该使用哪个工具？

1.  TensorBoard
2.  What-If Tool
3.  Looker
4.  语言可解释性工具 (LIT)

# 第 9 章：Vertex AI 上的模型可解释性

在本章中，我们将介绍什么是可解释性 AI 以及它在机器学习中为什么重要。我们将详细讨论 Vertex AI 平台上的模型可解释性技术以及应用用例。

## Vertex AI 上的模型可解释性

对于开发机器学习模型的团队来说，随着预测对业务结果的影响增加，解释模型预测的责任也随之增加。例如，消费者可能会毫无保留地接受来自机器学习模型的电影推荐，而不需要解释。消费者可能同意也可能不同意该推荐，但模型开发人员证明预测合理性的需求相对较低。

相反，如果机器学习模型预测信贷申请是否获批或患者的药物剂量是否正确，模型开发人员就有责任解释该预测。他们需要回答诸如“为什么我的贷款被拒？”或“为什么我应该服用 10 毫克这种药？”等问题。因此，深入了解训练过程并开发人类可解释的机器学习模型非常重要。

### 可解释性 AI

*可解释性* 是指您能够用人类语言解释机器学习或深度学习系统内部机制的程度。这与“黑箱”概念形成对比，在黑箱中，即使是设计者也无法解释为什么 AI 做出特定决策。

可解释性分为两种类型：全局和局部：

*   *全局可解释性* 旨在使整体机器学习模型透明且易于理解。
*   *局部可解释性* 侧重于解释模型的单个预测。

解释机器学习模型及其预测的能力可以建立信任并提高机器学习的采用率。模型不再是黑箱。这增加了模型预测消费者的舒适度。对于模型所有者来说，了解机器学习模型固有的不确定性有助于在出现问题时调试模型，并改进模型以获得更好的业务成果。

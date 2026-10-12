

## 使用 TFX 组件或 Kubeflow DSL 进行系统设计

*   使用 TFX 组件或 Kubeflow DSL（例如 Dataflow）进行系统设计 [11](#c11.xhtml)

## 5.2 自动化模型重新训练

考虑因素包括：[13](#c13.xhtml)

*   确定合适的重新训练策略 [13](#c13.xhtml)
*   持续集成和持续交付 (CI/CD) 模型部署（例如 Cloud Build、Jenkins） [13](#c13.xhtml)

## 5.3 跟踪和审核元数据

考虑因素包括：[12](#c12.xhtml)

*   跟踪和比较模型工件及版本（例如 Vertex AI Experiments、Vertex ML Metadata） [12](#c12.xhtml)
*   对接模型和数据集版本控制 [12](#c12.xhtml)
*   模型和数据血缘 [12](#c12.xhtml)

## 第 6 部分：监控机器学习解决方案

### 6.1 识别机器学习解决方案的风险

考虑因素包括：[6](#c06.xhtml)、[9](#c09.xhtml)

*   构建安全的机器学习系统（例如防止无意的数据或模型利用、黑客攻击） [6](#c06.xhtml)、[9](#c09.xhtml)
*   遵循 Google 的负责任 AI 实践（例如偏见） [9](#c09.xhtml)
*   评估机器学习解决方案的就绪情况（例如数据偏差、公平性） [9](#c09.xhtml)
*   Vertex AI 上的模型可解释性（例如 Vertex AI Prediction） [9](#c09.xhtml)

### 6.2 监控、测试和排查机器学习解决方案故障

考虑因素包括：[12](#c12.xhtml)、[13](#c13.xhtml)

*   建立持续评估指标（例如 Vertex AI Model Monitoring、Explainable AI） [12](#c12.xhtml)、[13](#c13.xhtml)
*   监控训练-服务偏差 [12](#c12.xhtml)
*   监控特征归因漂移 [12](#c12.xhtml)
*   监控模型性能与基线、更简单模型的对比，以及随时间维度的表现 [12](#c12.xhtml)
*   常见的训练和服务错误 [13](#c13.xhtml)

## 如何联系出版商

如果您认为在本书中发现了错误，请告知我们。在 John Wiley & Sons，我们深知为客户提供准确内容的重要性，但即使尽了最大努力，错误仍可能发生。

为了提交可能的勘误，请发送邮件至我们的客户服务团队 [wileysupport@wiley.com](mailto:wileysupport@wiley.com)，邮件主题为“Possible Book Errata Submission”。

## 评估测试

1.  在在线推荐系统中，为了预测未来 30 天内的用户生命周期价值 (LTV)，您会如何拆分数据以避免数据和标签泄露？（选择三项。）

    1.  执行 30 天的数据收集。
    2.  使用第 1 天到第 29 天的数据创建训练集。
    3.  使用第 30 天的数据创建验证集。
    4.  创建随机数据拆分为训练集、验证集和测试集。

2.  您拥有一个高度不平衡的数据集，并且希望在分类问题中关注正类。您会选择哪些指标？

    1.  精确率-召回率曲线下面积 (AUC PR)
    2.  ROC 曲线下面积 (AUC ROC)
    3.  召回率
    4.  精确率

3.  特征组合是通过 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ 两个或更多特征来创建的。

    1.  交换
    2.  相乘
    3.  相加
    4.  相除

4.  您可以使用 Cloud Pub/Sub 在 GCP 中流式传输数据，并使用 Cloud Dataflow 转换数据。

    1.  正确
    2.  错误

5.  您有训练数据，正在编写模型训练代码。您有一支数据工程师团队，他们更喜欢用 SQL 编码。您会推荐哪种服务？

    1.  BigQuery ML
    2.  Vertex AI 自定义训练
    3.  Vertex AI AutoML
    4.  Vertex AI 预训练 API

6.  使用 Vertex AI 托管数据集有哪些好处？（选择三项。）

    1.  使用 Vertex 数据标记，为未标记的非结构化数据（如视频、文本和图像）提供集成的数据标记功能。
    2.  跟踪模型血缘，以实现治理和迭代开发。
    3.  自动将数据拆分为训练集、测试集和验证集。
    4.  手动将数据拆分为训练集、测试集和验证集。

7.  掩码、加密和分桶是使用 Cloud Data Loss Prevention API 对 PII 数据进行去标识化以使其模糊不清的技术。

    1.  正确
    2.  错误

8.  您会选择哪种策略来处理图像、视频、音频和非结构化自由格式数据中存在的敏感数据？

    1.  使用 NLP API、Cloud Speech API、Vision AI 和 Video Intelligence AI 开箱即用地识别电子邮件、位置等敏感数据，然后对其进行编辑或移除。
    2.  使用 Cloud DLP 处理此类数据。
    3.  使用 Healthcare API 隐藏敏感数据。
    4.  创建一个不提供对相关列访问权限的视图。数据工程师无法查看数据，但同时数据是实时的，不需要人工干预即可对其进行去标识化以用于持续训练。

9.  当您试图在解决大型模型过拟合问题的同时减少特征时，您会使用 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_。

    1.  L1 正则化
    2.  L2 正则化
    3.  A 和 B 都是
    4.  梯度消失

10. 如果网络中的权重非常大，那么较低层的梯度将涉及许多大项的乘积，导致梯度爆炸，变得太大而无法收敛。有哪些方法可以避免这种情况？（选择两项。）

    1.  批量归一化
    2.  降低学习率
    3.  ReLU 激活函数
    4.  Sigmoid 激活函数

11. 您在本地拥有 Spark 和 Hadoop 环境，并计划将数据迁移到 Google Cloud。您的摄入管道既是实时的也是批处理的。您的 ML 客户工程师建议使用 Cloud Dataproc 以可扩展的方式将数据移动到 BigQuery。您会*不*推荐以下哪个 Dataproc 连接器？

    1.  Pub/Sub Lite Spark 连接器
    2.  BigQuery Spark 连接器
    3.  BigQuery 连接器
    4.  Cloud Storage 连接器

12. 您已将 Spark 和 Hadoop 环境迁移至 Google Cloud，数据存储在 Google Cloud Storage 中。您的摄入管道既是实时的也是批处理的。您的 ML 客户工程师建议以可扩展的方式直接在 Google Cloud Storage 中的数据上运行 Apache Hadoop 或 Apache Spark 作业。您会推荐以下哪个 Dataproc 连接器？

    1.  Pub/Sub Lite Spark 连接器
    2.  BigQuery Spark 连接器
    3.  BigQuery 连接器
    4.  Cloud Storage 连接器

13. 以下哪项*不是*加速超参数优化的技术？

    1.  通过使用带有超参数优化的分布式训练，将问题并行化到多台机器上。
    2.  通过预计算或缓存可在后续模型拟合中重用的计算结果，避免冗余计算。
    3.  使用网格搜索而不是随机搜索。
    4.  如果您有大型数据集，请使用简单的验证集而不是交叉验证。

14. Vertex AI Vizier 是一项用于优化具有许多参数的复杂模型的独立服务。它*只能*用于非机器学习用例。

    1.  正确
    2.  错误

15. 以下哪项*不是*训练神经网络时用于跟踪指标的工具？

    1.  Vertex AI 交互式 Shell
    2.  What-If Tool
    3.  Vertex AI TensorBoard Profiler
    4.  Vertex AI 超参数调优

16. 您是一名数据科学家，正在使用结构化数据集选择特征。以下哪种技术会有所帮助？

    1.  Sampled Shapley（采样 Shapley 值）
    2.  Integrated Gradients（积分梯度）
    3.  XRAI (eXplanation with Ranked Area Integrals)
    4.  Gradient Descent（梯度下降）

17. 变量选择和避免目标泄露是特征重要性的好处。

    1.  正确
    2.  错误


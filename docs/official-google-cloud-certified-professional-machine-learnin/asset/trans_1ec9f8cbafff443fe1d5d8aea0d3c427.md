

## 配置触发器和流水线计划

了解在 Google Cloud 上设置触发器以调用已训练模型或部署模型进行预测的方法。了解如何安排触发器，例如使用 `Cloud Scheduler` 和 Vertex AI 托管笔记本调度程序。此外，学习如何使用 `Workflows`、`Vertex AI Pipelines` 和 `Cloud Composer` 自动化流水线。

## 复习题

1.  您是一家在线旅行社的数据科学家。您被要求预测用户接下来应看到的最相关网页横幅，要求近实时完成。模型延迟要求为 300ms@p99，库存包含数千个网页横幅。您希望在 Google Cloud 上实现最简单的解决方案。应如何配置预测流水线？

    1.  在网站上嵌入客户端，并通过创建指向数据仓库的批量预测作业将预测结果缓存在数据存储中。在 `App Engine` 上部署网关，然后使用 `Vertex AI Prediction` 部署模型。
    2.  使用 `TF Serving` 部署模型。
    3.  使用 `Google Kubernetes Engine` 部署模型。
    4.  在网站上嵌入客户端，在 `App Engine` 上部署网关，在 `Cloud Bigtable` 上部署数据库以写入和读取用户的导航上下文，然后在 `Vertex AI` 上部署模型。

2.  您是一名数据科学家，正在使用 `Vertex AI` 平台通过 `TensorFlow` 训练文本分类模型。您希望对存储在 `BigQuery` 中的文本数据使用训练好的模型进行批量预测，同时将计算开销降至最低。您应该怎么做？

    1.  在 `Vertex AI` 上提交批量预测作业，将输入数据指向存储文本数据的 `BigQuery` 表。
    2.  在 `Vertex AI` 平台上部署并版本化模型。
    3.  使用带有 `SavedModel` 的 `Dataflow` 从 `BigQuery` 读取数据。
    4.  将模型导出到 `BigQuery ML`。

3.  您是一家全球性银行的 CTO，您任命了一名 ML 工程师为银行构建一个将被数百万客户使用的应用程序。您的团队构建了一个预测模型，用于预测客户未来三天的账户余额。您的团队将在一项新功能中使用该结果，当账户余额可能低于特定金额时通知用户。您应该如何提供预测服务？

    1.  为每个用户创建一个 `Pub/Sub` 主题。部署一个 `Cloud Function`，当模型预测用户的账户余额将低于阈值时发送通知。
    2.  为每个用户创建一个 `Pub/Sub` 主题。在 `App Engine` 环境中部署一个应用，当模型预测用户的账户余额将低于阈值时发送通知。
    3.  在 `Firebase` 上构建通知系统。在 `Firebase Cloud Messaging` 服务器上使用用户 ID 注册每个用户，当所有账户余额预测的平均值低于阈值时发送通知。
    4.  在 `Docker` 容器上构建通知系统。设置 `Cloud Functions` 和 `Pub/Sub`，当所有账户余额预测的平均值低于阈值时发送通知。

4.  您是一名数据科学家，使用 `TensorFlow` 训练了一个文本分类模型。您已下载用于 `TF Serving` 的 SavedModel。该模型具有以下 `SignatureDefs`：

    ```
    input ['text'] tensor_info:
    dtype: String
    shape: (-1, 2)
    name: dnn/head/predictions/textclassifier
    SignatureDefs for output.
    output ['text'] tensor_info:
    dtype: String
    shape: (-1, 2)
    name: tfserving/predict
    ```

    编写预测请求的正确方式是什么？

    1.  `json.dumps({'signature_name': 'serving_default', 'instances': ['fab', 'be1', 'cd']})`
    2.  `json.dumps({'signature_name': 'serving_default', 'instances': [['a', 'b', 'c', 'd', 'e', 'f']]})`
    3.  `json.dumps({'signature_name': 'serving_default', 'instances': [['a', 'b', 'c'], ['d', 'e', 'f']]})`
    4.  `json.dumps({'signature_name': 'serving_default', 'instances': [['a', 'b'], ['c', 'd'], ['e', 'f']]})`

5.  您是一名 ML 工程师，在一个需要计算成本高昂的预处理操作的数据集上训练了模型。您需要在预测时执行相同的预处理。您已在 `Vertex AI` 平台上部署模型以进行高吞吐量在线预测。您应该使用哪种架构？

    1.  将传入的预测请求发送到 `Pub/Sub` 主题。设置一个由发布到 `Pub/Sub` 主题的消息触发的 `Cloud Function`。在 `Cloud Function` 中实现预处理逻辑。使用转换后的数据向 `Vertex AI` 平台提交预测请求。将预测结果写入出站 `Pub/Sub` 队列。
    2.  将传入的预测请求数据流式传输到 `Cloud Spanner`。创建一个视图来抽象预处理逻辑。每秒查询一次视图以获取新记录。使用转换后的数据向 `Vertex AI` 平台提交预测请求。将预测结果写入出站 `Pub/Sub` 队列。
    3.  将传入的预测请求发送到 `Pub/Sub` 主题。使用 `Dataflow` 作业转换传入数据。使用转换后的数据向 `Vertex AI` 平台提交预测请求。将预测结果写入出站 `Pub/Sub` 队列。
    4.  验证在预处理数据上训练的模型的准确性。创建一个使用原始数据且可实时使用的新模型。将新模型部署到 `Vertex AI` 平台以进行在线预测。

6.  作为公司的首席数据科学家，您负责构建 ML 模型以数字化扫描的客户表单。您开发了一个 `TensorFlow` 模型，可将扫描图像转换为文本并存储在 `Cloud Storage` 中。您需要在每天结束时对聚合数据使用 ML 模型，且尽量减少人工干预。您应该怎么做？

    1.  使用 `Vertex AI` 平台的批量预测功能。
    2.  在 `Compute Engine` 中创建用于预测的服务流水线。
    3.  每次摄入新数据点时使用 `Cloud Functions` 进行预测。
    4.  在 `Vertex AI` 平台上部署模型并创建一个版本用于在线推理。

7.  作为公司的首席数据科学家，您需要创建一个计划，以便在每天结束时使用 `Jupyter Notebook` 运行批量作业，且尽量减少人工干预。您应该怎么做？

    1.  使用 `Vertex AI 托管笔记本` 中的调度功能。
    2.  在 `Compute Engine` 中创建用于预测的服务流水线。
    3.  每次摄入新数据点时使用 `Cloud Functions` 进行预测。
    4.  使用 `Cloud Workflow` 通过 `Cloud Function` 调度批量预测 `Vertex AI` 作业。

8.  您是一家在线旅行社的数据科学家。管理层要求您预测用户接下来应看到的最相关新闻文章，要求近实时完成。库存位于数据仓库中，包含数千篇新闻文章。您希望在 Google Cloud 上实现最简单的解决方案，并在服务模型时延迟最低。应如何配置预测流水线？

    1.  在网站上嵌入客户端，在 `App Engine` 上部署网关，然后使用 `Vertex AI Prediction` 部署模型。
    2.  使用 `TF Serving` 部署模型。
    3.  使用 `Google Kubernetes Engine` 部署模型。
    4.  在网站上嵌入客户端，在 `App Engine` 上部署网关，在 `Cloud Bigtable` 上部署数据库以写入和读取用户的导航上下文，然后在 `Vertex AI` 上部署模型。

# 第 11 章：设计 ML 训练流水线




## 2. 使用 TensorFlow 训练并保存模型。

## 3. 使用 TensorFlow Serving 服务已保存的模型。

更多信息请参阅 `www.tensorflow.org/tfx/serving/api_rest`。

### 使用 TensorFlow Serving 服务已保存的模型

运行在 host:port 上的 TensorFlow ModelServer 接受以下 REST API 请求：

```
POST http://host:port/<URI>:<VERB>

URI: /v1/models/${MODEL_NAME}[/versions/${MODEL_VERSION}]
VERB: classify|regress|predict
```

要调用 `predict()` REST 端点，您需要定义一个 JSON 数据载荷，因为 TF Serving 期望数据为 JSON 格式，如下所示：

```
data = json.dumps({"signature_name": "serving_default",
 "instances": instances.tolist()})
headers = {"content-type": "application/json"}
json_response = requests.post(url, data=data, headers=headers)
predictions = json.loads(json_response.text)['predictions']
```

`signature_name` 指定输入/输出数据类型。`instances` 是您想要预测的数据/输入/实例。您应该将其作为列表传递。

TF Serving 为您处理所有模型和 API 基础设施，以便您专注于模型优化。在考试中，可能会给您一个 TF Serving JSON 负载的实例和签名，并要求您提供 `predict()` 函数的输出。

以下是一个张量实例的示例：

```
{
 // 两个形状均为 [1, 2] 的张量列表
 "instances": [ [[1, 2]], [[3, 4]] ]
}
```

要了解您的 `predict()` 响应格式，您需要查看 SavedModel 的 SignatureDef（更多信息请参阅 `www.tensorflow.org/tfx/serving/signature_defs`）。您可以使用 SignatureDef CLI 来检查已保存的模型。给定的 SavedModel SignatureDef 包含以下输出：

```
outputs['class_ids'] tensor_info:
dtype: DT_INT64
shape: (-1, 1)
name: dnn/head/predictions/ExpandDims:0
outputs['classes'] tensor_info:
dtype: DT_STRING
shape: (-1, 1)
name: dnn/head/predictions/str_classes:0
outputs['logits'] tensor_info:
dtype: DT_FLOAT
shape: (-1, 3)
name: dnn/logits/BiasAdd:0
outputs['probabilities'] tensor_info:
dtype: DT_FLOAT
shape: (-1, 3)
name: dnn/head/predictions/probabilities:0
Method name is: tensorflow/serving/predict
```

根据前面的 SignatureDef，`predict()` 请求会在响应体中返回一个 JSON 对象，如下面的代码所示：

```
{
 "predictions": [
 {
 "class_ids": [3],
 "probabilities": [2.0495e-7, 0.0243, 0.9756],
 "classes": ["2"],
 "logits": [-5.74621, 5.94074, 9.62958]
 }
 ]
}
```

前面的示例具有形状为 (−1,1) 的类别 ID 整数、形状为 (−1,1) 的字符串类别、形状为 (−1,3) 的浮点数 logits 以及形状为 (−1,3) 的浮点数概率。

由于类别 ID 和类别的形状均为 (−1,1)，因此它们在预测中将只有一个值。同样，对于概率和 logit，形状 (−1,3) 将在响应中给出三个张量值。−1 意味着我们可以向已保存的模型传递任意大小。

一旦模型在模型目录或文件夹中可用，TF Serving 会自动加载新模型。此外，当新模型版本可用时，TF Serving 会自动卸载旧模型并加载更新的版本。此技术非常高效，且可以轻松添加到 MLOps 流水线中。这有助于您更专注于模型优化，而不是模型服务基础设施。我们将在 [第 11 章](#c11.xhtml) "设计 ML 训练流水线" 中介绍使用 TFX/Kubeflow 进行系统设计的主题。

更多信息请参阅 `https://neptune.ai/blog/how-to-serve-machine-learning-models-with-tensorflow-serving-and-docker`。

# 服务（在线、批量和缓存）

在 [第 5 章](#c05.xhtml) "ML 解决方案架构设计" 中，我们介绍了 ML 系统中的两种服务选项：批量预测（或离线服务）和在线预测，以及它们推荐的架构。在本章中，我们将介绍一些关于您的服务和缓存策略的最佳实践。

## 实时静态和动态参考特征

有两类输入特征是实时获取以调用模型进行预测的：静态参考特征和动态参考特征。让我们看 [表 10.1](#c10.xhtml#c10-tbl-0001) 以了解它们的区别。

### **表 10.1** 静态特征与动态特征

| 静态参考特征 | 动态实时特征 |
| --- | --- |
| 它们的值不会实时变化。相反，这些值通常通过批量方式更新。 | 实时特征是在事件流处理流水线中即时计算的。 |
| 这些类型的特征通常在数据仓库中可用——例如，客户 ID 和电影 ID。 | 对于实时特征，您需要特定时间段内特定窗口（固定、滑动或会话）的聚合值列表，而不是该时间段内值的总体聚合。 |
| 用例包括根据房屋位置估算房价，或根据客户当前正在查看的产品属性推荐相似产品。 | 用例可以是根据实时传感器数据预测发动机在未来一小时内是否会故障。另一个用例可以是根据用户在当前会话期间查看的最后 N 篇文章列表，推荐下一篇要阅读的新闻文章。 |
| 这些类型的静态参考特征存储在针对单点查找操作进行了优化的 NoSQL 数据库中，例如 Firestore。BigQuery 未针对单点读取进行优化，例如，查询“为特定客户 ID 从多个表中选择 100 列”，结果是一行包含多列的数据。 | 您可以使用 Dataflow 流式流水线来实现动态特征读取的用例。对于动态特征创建，流水线实时捕获并聚合（求和、平均等）事件，并将它们存储在低延迟读/写数据库中。Cloud Bigtable 是用于特征值的低延迟读/写数据库的一个不错选择。 |
| 静态参考架构（请参阅 [图 10.2](#c10.xhtml#c10-fig-0002)）。 | 动态参考架构（请参阅 [图 10.3](#c10.xhtml#c10-fig-0003)）。 |

![图 10.2 静态参考架构](images/c10f002.png)

**图 10.2** 静态参考架构

![图 10.3 动态参考架构](images/c10f003.png)

**图 10.3** 动态参考架构

## 预计算和缓存预测

改善在线预测延迟的另一种方法是在离线批量评分作业中预计算预测，并将它们存储在像 Memorystore 或 Datastore 这样的低延迟读取数据存储中，以便在线服务。在这些情况下，客户端（移动端、Web、数据流水线工作器、后端或前端 API）不会调用模型进行在线预测。相反，假设预测存在，客户端会从数据存储中获取预计算的预测。该过程如下：

1.  数据被摄取、处理并存储在键值存储中。
2.  一个训练并部署好的模型在准备好的数据上运行批量预测作业，为输入数据生成预测。每个预测由一个键标识。
3.  数据流水线将按键引用的预测导出到针对单点读取进行了优化的低延迟数据存储中。
4.  客户端发送一个由唯一键引用的预测请求。
5.  ML 网关使用条目键从数据存储中读取并返回相应的预测。

客户端接收预测响应。[图 10.4](#c10.xhtml#c10-fig-0004) 展示了该流程。

![图 10.4 缓存架构](images/c10f004.png)

**图 10.4** 缓存架构

预测请求可用于两类查找键：


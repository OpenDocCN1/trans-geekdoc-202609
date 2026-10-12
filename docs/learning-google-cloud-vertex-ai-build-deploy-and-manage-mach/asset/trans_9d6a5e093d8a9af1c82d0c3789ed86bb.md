

## 2. 模型 ID

`Model ID`，模型的唯一标识符（将用于在线预测）。

## 步骤 7：模型版本选择

模型版本列在模型注册表下，如[图 3.39](#ch03.xhtml#fig3-39)所示：

![](images/Figure_3.39.png)

**图 3.39：模型注册表上的模型版本**

1.  选择模型版本（因为我们训练了一个新模型，所以有一个可用版本）。点击 `1`。

> **注意：** 训练好的模型也会在 Vertex AI 的训练模块下作为训练流水线列出。

## 模型评估

任何训练好的模型在进行预测之前都需要经过评估。请按照以下步骤评估模型：

### 步骤 1：训练模型在测试数据上的性能

训练模型在测试数据上的性能如[图 3.40](#ch03.xhtml#fig3-40)所示：

![](images/Figure_3.40.png)

**图 3.40：基于文本数据集训练的模型评估**

1.  模型训练完成后，将成为该模型的第一个版本。当训练多个模型时，提供选择特定模型版本的选项。
2.  `EVALUATE` 提供关于情感值类别信息的详情，用户可以选择特定值以分别查看每个类别的评估指标。
3.  列出了不同的评估指标，并提供了部分指标的可视化信息。可以调整置信度阈值，以在不同置信度水平下检查图表。
4.  `DEPLOY AND TEST` 提供在线预测选项。
5.  `BATCH PREDICT` 提供批量预测选项。
6.  `VERSION DETAILS` 提供模型版本的各种详细信息。

> **注意：** 对比文本、图像和表格数据的评估，查看评估指标的差异。

## 批量预测

与表格和图像的训练模型非常相似，文本模型也可以在不部署的情况下用于批量预测。请按照以下步骤进行批量预测：

### 步骤 1：准备批量预测的输入

需要按照[图 3.41](#ch03.xhtml#fig3-41)所示的格式，准备用于批量预测的图像详细信息和图像的完整路径。文件需采用 `JSONL` 格式。

![](images/Figure_3.41.png)

**图 3.41：包含用于批量预测的文本数据的 JSONL 文件**

`JSONL` 文件中的每一行代表一个待预测的文件。`JSONL` 文件连同用于批量预测的文本文件一起上传到同一存储桶下的 `Batch_prediction` 文件夹中，如[图 3.42](#ch03.xhtml#fig3-42)所示：

![](images/Figure_3.42.png)

**图 3.42：上传到云存储的 JSONL 文件**

### 步骤 2：初始化批量预测

按照[图 3.43](#ch03.xhtml#fig3-43)所示步骤启动批量预测：

![](images/Figure_3.43.png)

**图 3.43：文本数据的批量预测**

1.  点击 `CREATE BATCH PREDICTION`。
2.  为预测任务提供名称。
3.  选择用于预测的模型。
4.  选择 `JSONL` 文件。
5.  选择输出格式为 `JSONL`。
6.  选择用于存储批量预测输出的云存储存储桶。
7.  点击 `CREATE`。

批量预测可能需要几分钟到几小时，具体取决于文本文件的数量（以及文本文件的大小）。

### 步骤 3：批量预测的输出

批量预测的输出将在云存储上可用，如[图 3.44](#ch03.xhtml#fig3-44)所示：

![](images/Figure_3.44.png)

**图 3.44：存储回云存储的批量预测输出**

1.  包含 `JSONL` 文件的文件夹将在云存储存储桶下创建。

可以使用记事本访问 `JSONL` 输出，它包含关于输入文件的信息以及每个类别的预测置信度分数，如下所示：

```
{"instance":{"content":"gs://AutoML_text_sentiment_analysis/Batch_prediction/228_1.txt","mimeType":"text/plain"},"prediction":{"sentiment":1}}
{"instance":{"content":"gs://AutoML_text_sentiment_analysis/Batch_prediction/227_1.txt","mimeType":"text/plain"},"prediction":{"sentiment":1}}
{"instance":{"content":"gs://AutoML_text_sentiment_analysis/Batch_prediction/182_10.txt","mimeType":"text/plain"},"prediction":{"sentiment":1}}
{"instance":{"content":"gs://AutoML_text_sentiment_analysis/Batch_prediction/180_9.txt","mimeType":"text/plain"},"prediction":{"sentiment":0}}
```

> **注意：** 与图像分类不同，在情感分析的情况下，概率分数将不包含在输出中。

## 用于在线预测的模型部署

部署模型以获取在线预测。请按照以下步骤将模型部署到端点。

### 步骤 1：模型部署

模型部署的着陆页如[图 3.45](#ch03.xhtml#fig3-45)所示：

![](images/Figure_3.45.png)

**图 3.45：文本模型的模型部署页面**

1.  转到 `DEPLOY AND TEST` 标签页。
2.  选择 `DEPLOY TO ENDPOINT`。

### 步骤 2：端点定义

按照[图 3.46](#ch03.xhtml#fig3-46)所示步骤创建端点：

![](images/Figure_3.46.png)

**图 3.46：情感模型部署的端点创建**

1.  选择 `Create new endpoint`，如果模型需要部署到现有端点，则提供 `Add to existing endpoints` 选项。
2.  点击 `CONTINUE`。

### 步骤 3：模型设置

继续进行模型设置以完成模型部署，如[图 3.47](#ch03.xhtml#fig3-47)所示：

![](images/Figure_3.47.png)

**图 3.47：部署设置**

1.  在流量分配中填入 `100`，因为我们将仅在 1 个节点上部署模型。
2.  为端点启用日志记录。
3.  点击 `DONE`。
4.  点击 `DEPLOY`。

### 步骤 4：测试已部署的模型

按照[图 3.48](#ch03.xhtml#fig3-48)中的以下步骤检查已部署的模型，然后再进行在线预测：

![](images/Figure_3.48.png)

**图 3.48：情感分析模型部署完成**

1.  模型部署后，状态将变为 `active`。
2.  在框中输入文本以检查预测。
3.  点击 `PREDICT`。
4.  将显示预测分数。

## 提供在线预测服务

模型已部署到 GCP 端点。用户可以使用本地机器上的 Python 从已部署的模型获取预测。使用上一章中创建的相同服务账号和密钥。

通过以下命令安装 `google-cloud-aiplatform` Python 包：

```
pip install google-cloud-aiplatform
```

更多关于该包的信息可从以下链接获取：

[https://pypi.org/project/google-cloud-aiplatform/](https://pypi.org/project/google-cloud-aiplatform/)

### 用于预测的 Python 代码

```
import base64
from google.cloud import aiplatform
from google.cloud.aiplatform.gapic.schema import predict
from google.protobuf import json_format
from google.protobuf.struct_pb2 import Value
import os

os.environ['GOOGLE_APPLICATION_CREDENTIALS'] = r""  # Full path of the service account key (Json file)
project_ID = "vertex-ai-gcp"
endpoint_id = "5207489379286646784"
content_path = r"E:\Publication\CHAPTERS\CHAPTER 3\DATA\Sentiment analysis\Test"
location = "us-central1"
api_endpoint = "us-central1-aiplatform.googleapis.com"

def predict_text_sentiment_analysis_sample(
    project_ID: str,
    endpoint_id: str,
    content_path: str,
    location: str = "us-central1",
    api_endpoint: str = "us-central1-aiplatform.googleapis.com"
):
    client_options = {"api_endpoint": api_endpoint}
    client = aiplatform.gapic.PredictionServiceClient(client_options=client_options)
    for path in os.listdir(content_path):
        with open(os.path.join(content_path, path)) as f:
            content1 = f.readlines()
        instance = predict.instance.TextSentimentPredictionInstance(content=str(content1[0])).to_value()
        instances = [instance]
        parameters_dict = {}
        parameters = json_format.ParseDict(parameters_dict, Value())
```


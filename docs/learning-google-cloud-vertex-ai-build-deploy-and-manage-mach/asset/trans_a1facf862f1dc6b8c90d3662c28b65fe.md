

## 模型版本与评估

1.  当模型训练完成时，它将成为该模型的第一个版本。当训练多个模型时，系统提供选项以选择特定的模型版本。

2.  **EVALUATE** 提供关于目标变量类别信息的详细情况，用户可以选择任意特定类别，分别查看每个类别的评估指标。

3.  列出了不同的评估指标，并附带部分指标的可视化信息。置信度阈值可调整，以便在不同置信度水平下检查图表。

4.  评估指标的图形化表示（随置信度阈值变化而变化）。

5.  **BATCH PREDICT** 提供批量预测选项。

6.  **DEPLOY AND TEST** 提供在线预测选项。

7.  **VERSION DETAILS** 提供模型版本的各种详细信息。

## Step 2: 混淆矩阵

向下滚动以获取混淆矩阵，如 [Figure 3.17](#ch03.xhtml#fig3-17) 所示：

![](images/Figure_3.17.png)

**Figure 3.17: Confusion matrix of the trained model**

1.  混淆矩阵。

2.  **VERSION DETAILS**（训练时间、训练和测试项目详情可在版本详情下查看）。

[Batch Predictions image](#contents.xhtml#sc2_60a)

无需将模型部署到部署环境即可发起异步预测请求。

### Step 1: 准备批量预测的输入

需要按照 [Figure 3.18](#ch03.xhtml#fig3-18) 所示的格式准备用于批量预测的图像详情和图像完整路径。该文件需采用 JSONL 格式。

![](images/Figure_3.18.png)

**Figure 3.18: JSONL file containing image data for batch prediction**

如 [Figure 3.19](#ch03.xhtml#fig3-19) 所示，JSONL 文件连同用于批量预测的图像一起上传到同一存储桶下的 `Data_for_batch_pred` 文件夹中：

![](images/Figure_3.19.png)

**Figure 3.19: JSONL file uploaded to cloud storage**

### Step 2: 初始化批量预测

按照 [Figure 3.20](#ch03.xhtml#fig3-20) 所示步骤开始批量预测：

![](images/Figure_3.20.png)

**Figure 3.20: Batch prediction for image data**

1.  点击 **CREATE BATCH PREDICTION**。
2.  为预测任务提供名称。
3.  选择用于预测的模型。
4.  选择 JSONL 文件。
5.  选择输出格式为 JSONL。
6.  选择用于存储批量预测输出的 Cloud Storage 存储桶。
7.  点击 **CREATE**。

批量预测可能需要几分钟到几小时不等，具体取决于图像数量。重要的是，用户无需部署模型即可进行批量预测。

### Step 3: 批量预测的输出

批量预测的输出将在 Cloud Storage 中可用，如 [Figure 3.21](#ch03.xhtml#fig3-21) 所示：

![](images/Figure_3.21.png)

**Figure 3.21: Output for batch predictions stored back to cloud storage**

1.  包含 JSONL 文件的文件夹将在 Cloud Storage 存储桶下创建。

可使用记事本访问 JSONL 输出，其中包含关于输入文件的信息以及每个类别的预测置信度分数，如下所示。每行包含输入文件信息、类别名称和概率分数：

```
{"instance":{"content":"gs://AutoML_image_data/Data_for_batch_pred/FB.jpg","mimeType":"image/jpeg"},"prediction":{"ids":["4888950415359475712","2583107406145781760","7194793424573169664"],"displayNames":["Ferry_boat","Kayak","Cruise_ships"],"confidences":[0.9992281,7.1564014E-4,5.6237353E-5]}}
```

```
{"instance":{"content":"gs://AutoML_image_data/Data_for_batch_pred/kayak.jpg","mimeType":"image/jpeg"},"prediction":{"ids":["2583107406145781760","4888950415359475712","7194793424573169664"],"displayNames":["Kayak","Ferry_boat","Cruise_ships"],"confidences":[0.9999988,1.2133818E-6,5.55904E-9]}}
```

```
{"instance":{"content":"gs://AutoML_image_data/Data_for_batch_pred/CS.jpg","mimeType":"image/jpeg"},"prediction":{"ids":["4888950415359475712","7194793424573169664","2583107406145781760"],"displayNames":["Ferry_boat","Cruise_ships","Kayak"],"confidences":[0.9019485,0.09799572,5.580726E-5]}}
```

[Model deployment for online predictions image](#contents.xhtml#sc2_61a)

与 AutoML 表格模型非常相似，AutoML 图像模型也可以部署到端点以提供在线预测服务。请按照以下步骤进行在线预测：

### Step 1: 模型部署

模型部署的着陆页如 [Figure 3.22](#ch03.xhtml#fig3-22) 所示：

![](images/Figure_3.22.png)

**Figure 3.22: Model deployment page**

1.  转到 **DEPLOY AND TEST** 标签页。
2.  选择 **DEPLOY TO ENDPOINT**。

### Step 2: 端点定义

按照 [Figure 3.23](#ch03.xhtml#fig3-23) 所示步骤创建端点：

![](images/Figure_3.23.png)

**Figure 3.23: Endpoint creation for image classification model deployment**

1.  如果模型需要部署在现有端点上，选择 **Create new endpoint**，用户可选择 **Add to existing endpoints**。
2.  点击 **CONTINUE**。

### Step 3: 模型设置

继续进行模型设置以完成模型部署，如 [Figure 3.24](#ch03.xhtml#fig3-24) 所示：

![](images/Figure_3.24.png)

**Figure 3.24: Deployment settings**

1.  在 **Traffic Split** 中填入 `100`，因为我们将仅在 1 个节点上部署模型。
2.  预测所需的节点数量 – 填入 `1`。
3.  为端点启用日志记录。
4.  点击 **DONE**。

向下滚动以选择日志记录选项，然后点击 **CONTINUE**。

### Step 4: 测试已部署的模型

按照以下步骤在进行在线预测前检查已部署的模型：

![](images/Figure_3.25.png)

**Figure 3.25: Image classification model deployment complete**

1.  端点创建完成后，将在 Model Registry 中列出，状态为 active。
2.  用户可上传图像以测试输出。上传的图像将连同每个类别的概率分数一起显示，如 [Figure 3.26](#ch03.xhtml#fig3-26) 所示：

![](images/Figure_3.26.png)

**Figure 3.26: Testing online prediction for image classification model**

[Serving online predictions image](#contents.xhtml#sc2_62a)

模型已部署到 GCP 端点。用户可以使用 Python 本地机器从已部署的模型获取预测。使用上一章中创建的相同服务账号和密钥。

通过以下命令安装 `google-cloud-aiplatform` Python 包：

```
pip install google-cloud-aiplatform
```

更多关于该包的信息可从以下链接获取：

<https://pypi.org/project/google-cloud-aiplatform/>

### 用于预测的 Python 代码

```python
# Install google-cloud-aiplatform
import base64
from google.cloud import aiplatform
from google.cloud.aiplatform.gapic.schema import predict
import os

os.environ['GOOGLE_APPLICATION_CREDENTIALS'] = r"E:\service_account_json\vertex-ai-gcp-0a71505b3eae.json"

project_ID = "vertex-ai-gcp"
model_ID = "4810468924636266496"
filename = r"E:\Publication\CHAPTERS\CHAPTER 3\DATA\Batch Pred\FB.jpg"
location = "us-central1"
api_endpoint = "us-central1-aiplatform.googleapis.com"

def predict_image_classification(
    project_ID=project_ID,
    model_ID=model_ID,
    filename=filename,
    location=location,
    api_endpoint=api_endpoint):

    client_options = {"api_endpoint": api_endpoint}
    client = aiplatform.gapic.PredictionServiceClient(client_options=client_options)

    with open(filename, "rb") as f:
        file_content = f.read()

    content_encoded = base64.b64encode(file_content).decode("utf-8")
    instance = predict.instance.ImageClassificationPredictionInstance(content=content_encoded).to_value()
    instances = [instance]
    params = predict.params.ImageClassificationPredictionParams(confidence_threshold=0.5, max_predictions=1).to_value()
    endpoint = client.endpoint_path(project=project_ID, location=location, endpoint=model_ID)
```


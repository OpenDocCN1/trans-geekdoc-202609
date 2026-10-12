

```python
response = client.predict(endpoint=endpoint, instances=instances, parameters=params)

predictions = response.predictions

for prediction in predictions:
    print("prediction:", dict(prediction))
```

# 调用函数

```python
predict_image_classification(project_ID, model_ID, filename, location, api_endpoint)
```

Python 代码的输出：

输出可在 [图 3.27](#ch03.xhtml#fig3-27) 中查看：

![](images/Figure_3.27.png)

图 3.27：图像分类模型 Python 代码输出

输出包含每个类别的概率得分。

注意：

*   项目 ID 和其他详细信息可从平台获取，具体请参阅 [第 2 章](#ch02.xhtml)。
*   部署模型会产生费用，请确保从部署中删除该模型。
*   用户可按 [第 2 章](#ch02.xhtml)“Vertex AI 和 AutoML 结构简介”中所述删除模型和数据集。

## 用于文本数据的 Vertex AI AutoML

文本 AutoML 可处理单标签、多标签分类、文本实体提取和文本情感分析任务。对于实际示例，我们使用情感分析数据，可从以下链接下载：

[https://www.kaggle.com/datasets/revanthrex/stanford-imdb-sentiment-analysis](https://www.kaggle.com/datasets/revanthrex/stanford-imdb-sentiment-analysis)

该数据集遵循 CC0：公共领域许可，包含约 25K 条电影评论。评论分为正面和负面评论。

在 `us-centra1`（单一区域）下创建了 `AutoML_text_sentiment_analysis` 存储桶，并上传了两个分别包含 50 条正面和负面评论的文件夹。在存储桶中创建了一个名为 `Batch_prediction` 的额外文件夹，其中包含随机选取的文本评论。云存储的快照如 [图 3.28](#ch03.xhtml#fig3-28) 所示：

![](images/Figure_3.28.png)

图 3.28：上传至云存储的文本数据

与图像数据集创建非常相似，即使对于情感分析数据集，我们也需要创建一个 CSV 文件，其中包含有关文本属于训练/验证/测试集的信息、文本的完整路径以及其所属的类别：

```bash
for f in $(gsutil ls gs://AutoML_text_sentiment_analysis/Positive/); do echo UNASSIGNED,$f,1,1;done>>text_sentiment_label.csv

for f in $(gsutil ls gs://AutoML_text_sentiment_analysis/Negative/); do echo UNASSIGNED,$f,0,1;done>>text_sentiment_label.csv
```

这些命令将创建一个包含三列的 CSV 文件：

*   设置文本文件用于训练/验证/测试。在本例中，我们使用了“UNASSIGNED”，由平台选择用于训练、验证和测试的图像。
*   文本文件的完整路径。
*   其所属的类别。

使用以下命令将 CSV 文件推送到云存储存储桶。

```bash
gsutil cp text_sentiment_label.csv gs://AutoML_text_sentiment_analysis/text_sentiment_label.csv
```

打开命令 Shell 并输入 [图 3.29](#ch03.xhtml#fig3-29) 中所示的命令：

![](images/Figure_3.29.png)

图 3.29：CSV 创建的 gs 命令（文本数据）

1.  点击图标以打开 Cloud Shell。
2.  输入命令（输入一条命令并按 Enter 键）。
3.  新的 CSV 文件已创建并可在云存储中使用。

创建的 CSV 文件快照如 [图 3.30](#ch03.xhtml#fig3-30) 所示：

![](images/Figure_3.30.png)

图 3.30：创建的 CSV 快照（用于文本数据）

C 列包含值 0 或 1。1 表示正面情感，0 表示负面情感。在 AutoML 的情感分析中，C 列可以是 0 到 10 之间的整数值（最大情感值由用户选择，在本例中 1 为最大值）。如果用户想要捕捉更细粒度的情感，例如 10 个层级，用户可以将文档标记为从 0（最负面）到 9（最正面）。

## 文本数据集创建

只有创建数据集后，才能启动情感分析的 AutoML 模型训练。请按照以下步骤为图像分类创建图像数据集：

### 步骤 1：数据集创建

导航至 Vertex AI 的数据集模块，如 [图 3.31](#ch03.xhtml#fig3-31) 所示：

![](images/Figure_3.31.png)

图 3.31：数据集着陆页

1.  点击创建。

### 步骤 2：目标选择

数据集创建标签页将显示，如 [图 3.32](#ch03.xhtml#fig3-32) 所示：

![](images/Figure_3.32.png)

图 3.32：文本数据集选择

1.  选择文本标签页。
2.  选择情感分析。
3.  为数据集提供名称。
4.  点击创建。

### 步骤 3：数据选择

数据可从云存储或本地系统中选择。按照 [图 3.33](#ch03.xhtml#fig3-33) 中提到的步骤从云存储上传图像：

![](images/Figure_3.33.png)

图 3.33：文本数据的数据选择

1.  标签存储在与模型目标关联的注释集中，将自动填充。
2.  选择从云存储导入文件。
3.  点击浏览。
4.  选择创建的 CSV 文件（参考 [图 3.29](#ch03.xhtml#fig3-29)）。
5.  点击选择。
6.  点击继续。

### 步骤 4：数据导入完成

数据导入完成后，数据（图像）将显示如 [图 3.34](#ch03.xhtml#fig3-34) 所示：

![](images/Figure_3.34.png)

图 3.34：文本数据集数据导入完成

1.  导航至浏览标签页。
2.  上传的图像根据输入的 CSV 文件进行分类。
3.  点击训练新模型以开始模型训练。

数据集创建完成后，将列在 Vertex AI 的数据集模块中。

注意：

*   至少需要提供 10 个且不超过 100,000 个训练文档总数。建议每个情感值至少有 100 个文档。
*   情感得分值必须是从零开始的连续整数。
*   每个情感得分的文档比例相等

## 文本模型训练

数据集创建完成且数据上传到数据集后，我们可以开始训练 AutoML 模型。请按照以下步骤启动模型训练：

### 步骤 1：模型训练方法

点击训练新模型后，用户将导航至如 [图 3.35](#ch03.xhtml#fig3-35) 所示的页面：

![](images/Figure_3.35.png)

图 3.35：文本数据集的训练方法选择

1.  创建的数据集将自动填充。
2.  注释集也将自动选择。
3.  创建数据集时选择的目标将自动选择。
4.  选择 AutoML 进行训练。
5.  点击继续。

### 步骤 2：模型详情

模型训练的下一步是用户提供模型详情，请按照 [图 3.36](#ch03.xhtml#fig3-36) 所示步骤操作：

![](images/Figure_3.36.png)

图 3.36：文本数据模型训练的模型详情

1.  选择训练新模型（如果要训练现有模型的新版本，请选择下面的选项）。
2.  提供模型名称。
3.  提供模型描述。
4.  选择随机分配（因为我们在创建 CSV 文件时给出了 unassigned）。默认情况下，80% 的数据将用于训练，10% 分别用于验证和测试。但是，用户可以根据要求进行更改。
5.  点击开始训练。

### 步骤 3：模型训练完成

模型训练完成后，数据集页面将更新，如 [图 3.37](#ch03.xhtml#fig3-37) 所示：

![](images/Figure_3.37.png)

图 3.37：数据集页面上的模型训练状态

1.  绿色对勾表示模型训练完成。
2.  点击模型注册表。

### 步骤 4：模型注册表

训练好的模型将列在模型注册表中，如 [图 3.38](#ch03.xhtml#fig3-38) 所示：

![](images/Figure_3.38.png)

图 3.38：模型注册表中列出的训练模型

1.  训练好的模型以用户提供的模型名称列出。点击模型名称。


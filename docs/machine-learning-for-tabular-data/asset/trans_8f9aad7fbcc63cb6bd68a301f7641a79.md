

# 第 11 章 构建机器学习流水线

`gsutil` 统一资源标识符 (URI) 值所示：`gs://first-project-ml-tabular-bucket/processed_dataset/ki_real_estate_output.csv`

现在，我们已经将清理后的数据集上传到 Google Cloud Storage 存储桶中，可以使用它来创建一个 Vertex AI 数据集。

## 11.2.7 创建 Vertex AI 托管数据集

ML 流水线调用 Vertex AI SDK 来训练模型；它将用于训练模型的数据集识别为 Vertex AI 托管数据集。要了解更多关于 Vertex AI 托管数据集的信息，请参阅文档：https://mng.bz/VVRP。

Vertex AI SDK 会自动执行以下操作，以使训练脚本可以使用该托管数据集：

- 将数据集的内容复制到 Google Cloud Storage。
- 将数据集划分为训练、验证和测试子集。每个子集的划分比例在流水线配置文件 `pipeline_config.yaml` 中设置，如图 11.2 所示。

```
# training_specs - 这里的设置将覆盖模型训练配置中的划分
training_fraction_split : 0.8
validation_fraction_split : 0.1
test_fraction_split : 0.1
```

![](img/def89cc476fa39f4c54bd34e78d91674_434_0.png)

将子集划分为多个 CSV 文件。图 11.22 显示了 Cloud Storage 中数据集 CSV 文件的示例。

| 名称 | 大小 | 类型 |
| :--- | :--- | :--- |
| test-00000-of-0004.csv | 155.3 KB | text/plain |
| test-00001-of-0004.csv | 143.4 KB | text/plain |
| test-00002-of-0004.csv | 146.1 KB | text/plain |
| test-00003-of-0004.csv | 141 KB | text/plain |
| training-00000-of-0004.csv | 1.1 MB | text/plain |
| training-00001-of-0004.csv | 1.1 MB | text/plain |
| training-00002-of-0004.csv | 1.1 MB | text/plain |
| training-00003-of-0004.csv | 1.1 MB | text/plain |
| validation-00000-of-0004.csv | 140.8 KB | text/plain |
| validation-00001-of-0004.csv | 139.3 KB | text/plain |
| validation-00002-of-0004.csv | 143.3 KB | text/plain |
| validation-00003-of-0004.csv | 138.8 KB | text/plain |

![](img/def89cc476fa39f4c54bd34e78d916744_43_1.png)

现在我们已经看到了数据集是如何进入 Cloud Storage 的，让我们通过以下步骤为训练数据创建一个 Vertex AI 数据集。

## ML 流水线准备工作步骤

1. 在 Vertex AI 中，选择“数据集 (Datasets)”。在数据集页面，点击“创建 (Create)”，如图 11.23 所示。

![](img/def89cc476fa39f4c54bd34e78d91674_435_0.png)

### 托管数据集包含用于训练机器学习模型的数据。了解更多

图 11.23
创建数据集

2. 在“创建数据集”页面上，将 `kuala-lumpur-real-estate` 设置为数据集名称，选择“表格 (Tabular)”标签页，选择“回归/分类 (Regression/Classification)”，并点击“创建 (Create)”，如图 11.24 所示。

![](img/def89cc476fa39f4c54bd34e78d91674_435_1.png)

选择数据类型和目标
首先选择你将包含的数据类型。选择一个目标，即你想要得到的结果

图 11.24
指定数据集详情

3. 在“源 (Source)”选择器中，选择“来自 Cloud Storage 的 CSV 文件”。在“导入文件路径 (Import file path)”中，点击“浏览 (Browse)”，选择你在上一节中上传处理后的训练文件的 Cloud Storage 位置，并点击“继续 (Continue)”，如图 11.25 所示。

![](img/def89cc476fa39f4c54bd34e78d91674_436_0.png)

图 11.25
指定数据集的源

4. 注意你刚刚创建的数据集的 ID 值，如图 11.26 所示。

数据集
用于训练机器学习模型的托管数据集。了解更多

![](img/def89cc476fa39f4c54bd34e78d91674_436_1.png)

图 11.26 Google Cloud Console 中的数据集 ID

## 定义 ML 流水线

这是在流水线配置文件 `pipeline_config.yaml` 中需要设置的值，如图 11.27 所示。

```python
ENDPOINT_NAME = 'klrealestate'
# 来自 cloud.google.com/vertex-ai/docs/training/pre-built-containers
train_image = 'us-docker.pkg.dev/vertex-ai/training/tf-cpu.2.9'
# 来自 cloud.google.com/vertex-ai/docs/pre-built-containers
deploy_image = 'us-docker.pkg.dev/vertex-ai/prediction/tf2-2.9'
config_path = "model_training.yml"
# 包含训练设置的 文件
```

```python
script_path = 'model_training_preprocessing.py'
machine_type = 'n1-standard-4'
# 项目详情
project_id = 'first-project-ml-tabular'
region = 'us-central1'
dataset_id = '290141542631119872'
# 11.27 流线配置文件中的 dataset_id
```

恭喜！你已经为模型训练部分将使用的数据集设置了 Vertex AI 托管数据集。

## 11.3 定义 ML 流水线

到本章为止，我们已经完成了流水线的以下准备工作：

- 1. 创建了服务账户和服务密钥
- 2. 将服务账户密钥上传到我们将运行流水线脚本的目录
- 3. 将清理后的数据集上传到 Cloud Storage
- 4. 从清理后的数据集创建了 Vertex AI 托管数据集

在本节中，我们将实现上一节中准备的元素，并创建一个 ML 流水线，该流水线在端接收预处理的数据集，另一端生成部署到 Vertex AI 终端训练模型。

## 11.3.1 本地实现与流水线对比

在定义流水线之前，让我们对比一下 ML 流水线与训练吉隆坡房地产预测模型的本地设置。图 11.28 显示了这种对比并突出了某些差异。

| 在本地系统上训练 | 使用 ML 流水线训练 |
| :--- | :--- |
| 输入 CSV | 输入 CSV |
| --- | --- |
| 数据清理笔记本 | 数据清理笔记本 |
| 清理后的 pickle 文件 | 清理后的 CSV 文件 |
| 训练 CSV  | 验证 CSV 、测试 CSV 文件 |
| 训练配置文件 | 训练配置文件 |
| 流水线脚本 | 流水线脚本 |
| Cloud Shell 实例 | 云存储 |
| 训练好的模型 | 模型库 |
| 部署到终端的模型 | 部署到终端的模型 |

图 11.28 本地系统与 ML 流水线的对比


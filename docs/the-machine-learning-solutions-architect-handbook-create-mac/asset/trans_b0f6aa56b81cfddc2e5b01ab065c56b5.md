

# 动手练习 – 使用开源技术构建数据科学架构 213

要访问 MLflow 跟踪服务器站点，请查找 EC2 的公共 DNS 名称并将其输入浏览器。该地址看起来应该像示例所示：

```
http://<EC2 public url>:5000.
```

请注意，MLflow 跟踪服务器没有内置安全机制，因此该跟踪服务器是公开访问的。在不使用时，您应该停止/终止跟踪服务器。若要安全地访问跟踪服务器，您可以在跟踪服务器前面设置一个安全代理服务器，这超出了本书的讨论范围。

- 6 从 Kubeflow notebook 中使用 MLflow 跟踪：现在我们已经准备好使用跟踪服务器来跟踪实验了，请从您的 Kubeflow 仪表板启动之前创建的 Jupyter notebook，并在屏幕上的 `New` 下拉菜单中选择 `Terminal` 以打开终端控制台。在终端窗口中，运行以下代码块以安装 AWS 命令行界面 (CLI) 并配置 AWS CLI 环境变量。在运行 `aws configure` 命令提示时，提供 AWS 访问密钥对值。MLflow 将使用这些凭据将制品上传到 S3 存储桶以供 MLflow 跟踪服务器使用：

```
pip3 install awscli
aws configure
```

接下来，通过选择 file->new notebook 创建新 notebook，并插入此处显示的代码块。将 `<<tracking server uri>>` 替换为您的跟踪服务器资源标识符 (URI)，并运行代码。此代码块将在 Jupyter notebook 中安装 mlflow 客户端库，使用 `mlflow.set_experiment()` 函数设置实验跟踪，使用 `mlflow.sklearn.autolog()` 函数开启自动跟踪，最后使用 `mlflow.sklearn.log_model()` 函数注册训练好的模型：

```python
! pip3 install mlflow
```

```python
import pandas as pd
import mlflow
from sklearn.ensemble import RandomForestClassifier
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import OrdinalEncoder
```

```python
churn_data = pd.read_csv("churn.csv")
```

```python
encoder = OrdinalEncoder()
churn_data['Geography_code'] = encoder.fit_transform(churn_data['Geography'])
churn_data['Gender_code'] = encoder.fit_transform(churn_data['Gender'])
churn_data.drop(columns=['Geography', 'Gender', 'RowNumber', 'Surname'], inplace=True)
```

```python
# 将数据集划分为训练集 (80%) 和测试集 (20%)
churn_train, churn_test = train_test_split(churn_data, test_size=0.2)
```

```python
# 将特征与目标变量 "Exited"分离，因为模型训练需要
churn_train_X = churn_train.loc[:, churn_train.columns != 'Exited']
churn_train_y = churn_train['Exited']
```

```python
churn_test_X = churn_test.loc[:, churn_test.columns != 'Exited']
churn_test_y = churn_test['Exited']
```

```python
# 设置 mlflow 跟踪服务器
tracking_uri = <tracking server uri>
mlflow.set_tracking_uri(tracking_uri)
```

```python
mlflow.set_experiment('customer churn')
mlflow.sklearn.autolog()
```

```python
with mlflow.start_run():
    bank_churn_clf = RandomForestClassifier(max_depth=2, random_state=0)
    bank_churn_clf.fit(churn_train_X, churn_train_y)
    mlflow.sklearn.log_model(sk_model=bank_churn_clf, artifact_path="sklearn-model", registered_model_name="churn-model")
```

# 动手练习 – 使用开源技术构建数据科学架构 215

现在返回跟踪服务器站点并刷新页面。在 `Experiment` 标签下，你将看到一个名为 `customer churn` 的新实验。点击 customer 链接查看运行详情，然后点击 `Model` 标签。你将看到一个名为 `churn` 的新模型。

现在，在 Jupyter notebook 中运行相同的代码。你现在将看到一个新的运行，并创建一个新的模型版本。

- **将模型部署到 Seldon Core：** 你已成功训练了一个 ML 模型并在 MLflow 模型注册表中注册了该模型。接下来，让我们使用 Seldon Core 服务框架部署此模型。

让我们从模型注册中心下载模型制品并将其保存到 S3 中的部署存储桶中。要做到这一点，首先创建一个名为 `model-deployment-<your initial>` 的新 S3 桶。我们将使用 Seldon Core 的 sklearn 服务程序包来托管模型，它期望模型名称为 `model.joblib`。运行以下代码块从模型注册中心下载模型制品，将 `model.pkl` 文件复制到另一个目录并将其命名为 `model.joblib`：

```python
import mlflow.sklearn
import shutil
model_name = "churn-model"
model_version = <version>
```

```python
sk_model = mlflow.sklearn.load_model(f"models:{model_name}/{model_version}")
mlflow.sklearn.save_model(sk_model, f"{model_name}_{model_version}")
```

```python
src = f"{model_name}_{model_version}/model.pkl"
des = f"skserver_{model_name}_{model_version}/model.joblib"
```

```python
shutil.copy(src, des)
```

接下来，运行以下代码将模型上传到 S3：

```python
import boto3
import os

s3 = boto3.client('s3')
bucket_name = "model-deployment-<your initial>"
s3.upload_file(des, bucket_name, os.path.basename(des))
```

跟踪服务器现在已就绪，存储桶中包含 `model.joblib` 文件。我们现在可以进行 Seldon Core 部署了。


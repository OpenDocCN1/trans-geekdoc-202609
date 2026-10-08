

## 实践练习 – 使用开源技术构建数据科学架构 225

```python
output: str ) -> str :
import os

import boto3
import mlflow
import pandas as pd
from sklearn.ensemble import RandomForestClassifier
from sklearn.model_selection import train_test_split
```

```python
s3 = boto3.client('s3', region_name=region)
response = s3.list_objects(Bucket=bucket, Prefix=key)

key = response['Contents'][0]['Key']
s3.download_file('datalake-demo-dyping', key, 'churn.csv')
```

```python
churn_data = pd.read_csv('churn.csv')
```

```python
# 将数据集分为训练集 (80%) 和测试集 (20%)
churn_train, churn_test = train_test_split(churn_data, test_size=0.2)
```

```python
churn_train_X = churn_train.loc[:, churn_train.columns != 'exited']
churn_train_y = churn_train['exited']
```

```python
churn_test_X = churn_test.loc[:, churn_test.columns != 'exited']
churn_test_y = churn_test['exited']
```

```python
tracking_uri = <<your mlflow tracking server url>>
```

```python
mlflow.set_tracking_uri(tracking_uri)
mlflow.set_experiment('Churn Experiment 3')
```

```python
with mlflow.start_run(run_name="churn_run 2") as run:
    bank_churn_clf = RandomForestClassifier(max_depth=2, random_state=0)
```

```python
mlflow.sklearn.autolog()
bank_churn_clf.fit(churn_train_X, churn_train_y)
mlflow.sklearn.log_model(sk_model=bank_churn_clf,
artifact_path="sklearn-model", registered_model_name="churn-model")
```

```python
print(f"MLflow run id: {run.info.run_id}")
return f"MLflow run_id: {run.info.run_id}"
```

```python
train_model_op = components.func_to_container_op(
train_model,
base_image=BASE_IMAGE,
packages_to_install=('boto3', 'mlflow', 'scikit-learn', 'matplotlib'),
)
```

前面的训练步骤将把模型注册到 MLflow 模型注册表中。我们需要下载目标模型版本并将其上传到 S3 存储桶，以便进行部署步骤。在 notebook 中添加以下代码块，这将创建一个 `download_model_op` 组件。请记住将 `model-deployment-<your initials>` 替换为自己的存储桶名称，并将 `<<your mlflow server>>` 替换为自己的跟踪服务器地址：

```python
@dsl.python_component(
name='model_download_op',
description='model training step',
base_image=BASE_IMAGE # 你可以在此处定义基础镜像，
或者在下一步构建时进行定义。
)
```

```python
def download_model(model_version: int, previous_output: str)
-> str :
    import mlflow
    import os
    import shutil
    import boto3
```

```python
model_name = "churn-model"
model_version = model_version
```

## 实践练习 – 使用开源技术构建数据科学架构 227

```python
tracking_uri = <<your mlflow tracking server>>
```

```python
mlflow.set_tracking_uri(tracking_uri)
mlflow.set_experiment('Churn Experiment 3')
```

```python
sk_model = mlflow.sklearn.load_model(f"models:/{model_name}/{model_version}")
```

```python
mlflow.sklearn.save_model(sk_model, f"{model_name}_{model_version}")
```

```python
os.makedirs(f"sksver_{model_name}_release")
```

```python
src = f"{model_name}_{model_version}/model.pkl"
des = f"sksver_{model_name}_release/model.joblib"
```

```python
shutil.copyfile(src, des)
```

```python
targetbucket = "model-deployment-<your initials>"
prefix = f"mlflow-models/{model_name}_release"
```

```python
def upload_objects(src_path, bucketname):
    s3 = boto3.resource('s3')
    my_bucket = s3.Bucket(bucketname)
```

```python
for path, dirs, files in os.walk(src_path):
    dirs[:] = [d for d in dirs if not d.startswith('.')]
```

```python
    path = path.replace("\\", "//")
    directory_name = prefix + path.replace(src_path, "")
    for file in files:
        my_bucket.upload_file(os.path.join(path, file), 
            directory_name + "/" + file)
```

```python
upload_objects(des, targetbucket)
```

```python
print(f"target bucket: {targetbucket}, prefix: {prefix}")
return f"target bucket: {targetbucket}, prefix: {prefix}")
```

```python
model_download_op = components.func_to_container_op(
download_model,
base_image=BASE_IMAGE,
packages_to_install=['boto3', 'mlflow', 'scikit-learn'],
)
```

现在我们准备好构建流水线定义了。通过使用 `@dsl.pipeline` 装饰器定义函数来构建流水线。为了运行流水线并将模型部署到集群，我们需要为与流水线相关的服务账户（default-editor）添加权限。正确的方法创建一个具有适当权限的角色。为了简单起见，我们将重用现有的 `cluster-admin` 角色。在 CloudShell 环境中运行以下代码块，为集群创建 `.yaml` 文件，然后运行 `kubectl apply -f sa-binding.yaml` 来建立绑定：

```yaml
cat << EOF > sa-binding.yaml
apiVersion: rbac.authorization.k8s.io
kind: ClusterBinding
metadata:
  name: default-editor-binding
  namespace: admin
subjects:
  - kind: ServiceAccount
    name: default-editor
    namespace: admin
roleRef:
  kind: ClusterRole
  name: cluster-admin
  apiGroup: rbac.authorization.k8s.io
EOF
```

接下来，我们需要为流水线创建一个 Seldon 部署文件。在你的 Jupyter 环境中创建一个名为 `bank_churn_deployment.yaml` 的新文件，将代码复制并保存。在保存文件之前，确保替换 `<<S3 uri of model file>>`：

```yaml
apiVersion: machinelearning.seldon.io
kind: SeldonDeployment
metadata:
  name: bank-churn
spec:
  name: bank-churn
  predictors:
    name: classifier
    name: default
    replicas: 1
    implementation: <<S3 uri of model file>>
    envSecretName: aws-secret
EOF
```

好了，现在准备好运行以下代码块来构建流水线。注意我们将在某些步骤中使用 AWS 凭据。为了安全地管理 AWS 凭据并将其传递给组件，我们需要在构建流水线之前在 admin 命名空间创建一个新的 secret。在 CloudShell 终端运行以下脚本，然后运行 `kubectl apply -f aws_secret.yaml`。请将 `<<your AWS access key>>` 和 `<<your AWS secret key>>` 替换为你自己的密钥：

```yaml
cat << EOF > aws_secret.yaml
apiVersion: v1
kind: Secret
metadata:
  name: aws-secret
  namespace: admin
type: Opaque
data:
  AWS_ACCESS_KEY_ID:<<your AWS access key>>
  AWS_SECRET_ACCESS_KEY: <<your AWS secret key>>
EOF
```

现在在 Jupyter 单元格中运行以下代码块构建流水线定义。此工作流中有四个步骤：

- preprocess_data_task
- model_training_task
- model_download_task
- seldondeploy

为了简单起见，我们在流水线中添加了默认值。请将 `<<aws region>>` 替换为你的区域：

```python
@dsl.pipeline(
name='bank churn pipeline',
description='Train bank churn model'
)
def preprocess_train_deploy(
    bucket: str = 'datalake-demo-dyping',
    glue_job_name: str = 'customer-churn-processing',
    region: str = <<aws region>>,
    tag: str = '4',
    model: str = 'bank_churn_model',
    model_version: int = 1
):
    preprocess_data_task = process_data_op(glue_job_name, region).apply(use_aws_secret('aws-secret', 'AWS_ACCESS_KEY_ID', 'AWS_SECRET_ACCESS_KEY', 'us-west-1'))

    model_training_task = train_model_op(bucket, 'ml-customer-churn/data/', region, preprocess_data_task.output).apply(use_aws_secret())

    model_download_task = model_download_op(model_version, model_training_task.output).apply(use_aws_secret())
```

```python
seldon_config = yaml.load(open("bank_churn_deployment.yaml"))
deploy_op = dsl.ResourceOp(
name="seldondeploy",
k8s_resource=seldon_config,
action="apply",
attribute_outputs={"name": "{.metadata.name}"})
```

```python
deploy_op.after(model_download_task)
```

流水线定义需要注册到 Kubeflow Pipelines 服务。为了做到，我们需要编译前面的定义并将其保存为。在新单元格中运行以下代码块将流水线编译为文件：

```python
import kfp.compiler as compiler
```

```python
pipeline_filename = 'bank_churn_pipeline.tar.gz'
compiler.Compiler().compile(preprocess_train_deploy, pipeline_filename)
```

我们准备好注册并运行流水线，方法是创建一个实验（用于组织不同实验的所有端到端工作流运行），并使用 `run_pipeline()` 函数运行流水线。注意，我们还在使用 MLflow 来跟踪工作流中模型训练步骤细节：

```python
client = kfp.Client()
experiment = client.create_experiment(name='data_experiment',
namespace='admin')
```

```python
arguments = {'model_version':1}
pipeline_func = preprocess_train_deploy
run_name = pipeline_func.name + ' run'
run_result = client.run_pipeline(experiment.id, run_name,
pipeline_filename, arguments)
```


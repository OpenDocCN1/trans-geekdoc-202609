
```
WORKDIR /app
ADD requirements.txt /app/requirements.txt
RUN pip install -r /app/requirements.txt
ADD servebreast.py /app/servebreast.py
COPY service.json
ENV GOOGLE_APPLICATION_CREDENTIALS="service.json"
CMD ["python","servebreast.py"]
```

现在，在前面的 Docker 代码中，我们已复制用于存储桶访问的服务账号并将其保存到 然后，我们在同一位置复制了 Python 服务文件并将工作目录保持为 然后，我们使用以下代码构建了镜像。同样，我们创建了 Docker 镜像；请查看 GitHub steps.md 文件。

要使用 kubectl 命令行或使用 KF Serving 客户端 SDK 部署模型服务器，请完成以下步骤：

- 使用命令行部署。
- 使用 KF Serving 客户端 SDK 部署。

## 使用命令行部署：

现在，让我们使用命令行部署它，但首先让我们填充 yaml 文件。

## Custom_KFServing.yaml:

```
apiVersion: serving.kubeflow.org/v1alpha2
kind: InferenceService
```

```
metadata:
annotations:
sidecar.istio.io/inject: "false"

name: kfserving-breast-model
namespace: kubeflow
spec:
default:
predictor:
custom:
container:
image: gcr.io//breast_cancer/custom_serving:v1
```

这里，在前面的 yaml 文件中，我们将使用在 Transformer.py 文件中提供的相同名称，其中包含模型名称，然后我们将提供命名空间“Kubeflow”，它将在其中部署。接下来，我们将为我们创建的 Transformer 模型提供一个 Docker 镜像名称。

![](img/8f8a671916d96b455297952d0f37b96c_146_0.png)

## 图 2.15：KF – Serving 模型名称匹配

正如我们在前面的截图中看到的，左侧图像中的第 38 行和右侧的第 6 行应始终相同。

接下来，从 Visual Studio 中保存文件的位置在 bash 中运行以下命令。

使用以下命令连接到 GCP 集群：

```
gcloud container clusters get-credentials <$ClusterName> --zone <$ZONE> --project <$PROJECTID>
```

通过在集群中部署它来创建推理服务：

```
kubectl apply -f custom_breast_model.yaml
```

检查推理服务。间隔一段时间后尝试检查是否已创建：

```
kubectl get inferenceservice -n Kubeflow
```

![](img/8f8a671916d96b455297952d0f37b96c_147_0.png)

## 图 2.16：KF – Serving 推理输出

## 示例预测：

从 serving 文件夹在 Bash 中运行以下命令：

```
```bash
MODEL_NAME=kfserving-braintumor
HOST=$(kubectl get inferenceservice -n Kubeflow $MODEL_NAME -o jsonpath='{.status.url}' | cut -d "/" -f 3)
INPUT_PATH=@./data.json
CLUSTER_IP=$(kubectl -n istio-system get service kfserving-ingressgateway -o jsonpath='{.status.loadBalancer.ingress[0].ip}')
curl -v -H "Host: ${HOST}"
http://${CLUSTER_IP}/v1/models/${MODEL_NAME}:predict -d $INPUT_PATH
```
```

现在，以下是响应预测请求：

```
* Trying [redacted].
* TCP_NODELAY set
* Connected to [redacted] ([redacted] port 80 (#0)
> POST /v1/models/kfserving-breast-model:predict HTTP/1.1
> Host: kfserving-breast-model.kubeflow.example.com
> User-Agent: curl/7.64.1
> Accept: */*
> Content-Length: 256
> Content-Type: application/x-www-form-urlencoded
>
* upload completely sent off: 256 out of 256 bytes
< HTTP/1.1 200 OK
< content-length: 28
< content-type: application/json; charset=UTF-8
< date: Fri, 24 Jul 2020 05:40:42 GMT
< server: istio-envoy
< x-envoy-upstream-service-time: 11796
<
* Connection #0 to host [redacted] left intact
{"predictions": "malignant"}* Closing connection 0
```

图 2.17：KF – Serving 预测输出

从 serving 文件夹在 Python 中运行以下命令：

现在，我们将创建一些示例数据以从前面的 URL 预测结果。以下是创建示例数据的代码：

```
import base64,json,requests
from sklearn.datasets import load_breast_cancer
import pandas as pd
import numpy as np
from sklearn.model_selection import train_test_split
cancer = load_breast_cancer()
```

```
df_cancer = pd.DataFrame(np.c_[cancer['data'], cancer['target']],
columns = np.append(cancer['feature_names'], ['target']))

X = df_cancer.drop(['target'],axis=1)
y = df_cancer['target']
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size =
0.1, random_state = 0)
data = json.dumps({"instances": X_test.iloc[7].to_list()})
data
```

![](img/8f8a671916d96b455297952d0f37b96c_150_0.png)

图 2.18：示例数据

```
MODEL_NAME="kfserving-breast-model"
cluster_ip = YOUR CLUSTER IP HERE
headers={"Host": "{0}.Kubeflow.example.com".format(MODEL_NAME)}
response =
requests.post("http://{0}/v1/models/{1}:predict".format(cluster_ip,
MODEL_NAME), data = data,headers = headers)
response.json()
```

![](img/8f8a671916d96b455297952d0f37b96c_150_1.png)

图 2.19：预测输出

正如我们在前面的截图中看到的，我们的预测输出为恶性。

## 2.6 端到端构建管道

现在，让我们看看如何构建 Pipeline，并将在 Kubeflow Notebook 服务器中运行此平台。

打开 URL：GCP Kubernetes > Service & ingress > 点击 URL。

![](img/8f8a671916d96b455297952d0f37b96c_152_0.png)

图 2.20：Ingress URL

如第 1 章《Kubeflow 和 Kubernetes 云架构简介》第 1.6 节所述，我们已创建了一个 Jupyter notebook，我们将使用它。

![](img/8f8a671916d96b455297952d0f37b96c_152_1.png)

图 2.21：Notebook Server 输出

现在，粘贴以下代码并运行管道；在之前请将以下代码中的 PROJECT_ID 和存储桶名称替换掉，它将转储一个 zip 文件：

```
```
import kfp.dsl as dsl
import yaml
from kubernetes import client as k8s
import kfp.gcp as gcp
from kfp import components
from string import Template
import json
from kubernetes import client as k8s_client

@dsl.pipeline(

name='breast cancer pipeline',
description='End to End pipeline for Tensorflow Breast Cancer')
def breast_cancer_tensorflow_pipeline(
dataextraction_step_image="gcr.io/<$PROJECT_ID>/breast_cancer/step1_loadingdata",
dataprocessing_step_image="gcr.io/<$PROJECT_ID>/breast_cancer/step2_dataprocessing",
trainmodel_step_image="gcr.io/<$PROJECT_ID>/breast_cancer/step3_training_model",
evaluator_step_image="gcr.io/<$PROJECT_ID>/breast_cancer/step4_evaluation_model",
train_file='/mnt/training.data',
data_file="/mnt/breast.data",
test_file='/mnt/test.data',
validation_file="/mnt/validation.data",
split_size=0.2,
train_target="/mnt/trainingtarget.data",
test_target="/mnt/testtarget.data",
```

```
validation_target="/mnt/validationtarget.data",
epochs=5,
learning_rate=.001,
batch_size=64,
shuffle_size=1000,
tensorboard_logs="/mnt/logs/",
tensorboard_gcs_logs="gs://<$YOUR_BUCKET>/breast/logs",
model_output_base_path="/mnt/saved_model",
gcs_path="gs://<$YOUR_BUCKET>/breast/model",

gcs_path_confusion="gs://<$YOUR_BUCKET>/breast",
mode="gcs",
probability=0.5,
serving_name="kfserving-breast-model",
serving_namespace="Kubeflow",
image="gcr.io/<$PROJECT_ID>/breast_cancer/custom_serving_nermodel"):
"""
Pipeline
"""

# PVC : PersistentVolumeClaim volume
vop = dsl.VolumeOp(
name='my-pvc',
resource_name="my-pvc",
modes=dsl.VOLUME_MODE_RWO,
size="1Gi"
)
# data extraction
data_extraction_step = dsl.ContainerOp(
name='data_extraction',
image=dataextraction_step_image,
command="python",
```

```
```python
arguments=[
"/app/dataextract.py",
"--data-file", data_file],
pvolumes={"/mnt": vop.volume})

# processing
data_processing_step = dsl.ContainerOp(
name='data_processing',

image=dataprocessing_step_image,
command="python",
arguments=[
"/app/preprocessing.py",
"--train-file", train_file,
"--test-file", test_file,
"--validation-file", validation_file,
"--data-file",data_file,
"--split-size",split_size,
"--train-target",train_target,
"--test-target",test_target,
"--validation-target",validation_target],
pvolumes={"/mnt": data_extraction_step.pvolume})
#trainmodel
train_model_step = dsl.ContainerOp(
name='train_model',
image=trainmodel_step_image,
command="python",
arguments=[
"/app/train.py",
"--train-file", train_file,
"--test-file", test_file,
"--validation-file", validation_file,
```
```

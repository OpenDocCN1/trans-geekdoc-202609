
## 开始运行 TensorFlow Serving

这里我们开始运行 TensorFlow Serving 并加载我们的模型。一旦加载完成，我们就可以使用 REST 开始进行推理请求。以下是一些重要参数：

- 用于 REST 请求的端口。你将在 REST 请求的 URL 中使用它。可以是任意值。
- 这是保存模型所在的目录的路径。请注意，此 **base_path** 不应包含模型版本目录，这就是我们将其拆分的原因，如下所示：

```
os.environ["MODEL_DIR"] = os.path.split(latest_pushed_model)[0]
%%bash --bg
nohup tensorflow_model_server \
--rest_api_port=8501 \
--model_name=online_news_simple \
--model_base_path="${MODEL_DIR}" >server.log 2>&1
!tail server.log
```

## 在示例数据上执行推理

让我们从 eval 数据集中加载一些示例，移除它们的标签（因为服务模型不期望标签），并通过一次 REST API 调用将它们发送到 Tensorflow Serving。

请注意，这将包含标签，但服务器会忽略它们。

```
eval_uri = example_gen.outputs['examples'].get()[0].uri
eval_tfrecord_paths = [os.path.join(eval_uri, name)for name in os.listdir(eval_uri)]
```

```
def strip_label(serialized_example):
example = tf.train.Example.FromString(serialized_example.numpy())
return example.SerializeToString()
```

```
dataset =
tf.data.TFRecordDataset(eval_tfrecord_paths,compression_type="GZIP")
serialized_examples = [strip_label(serialized_example)for serialized_example in dataset.take(3)]
```

在这里，我们对用于评估的转换后的数据进行了序列化，并制作了一个数据集 TFRecord。

向模型发送请求，并按如下方式打印结果：

- 模型服务器的网络地址，采用 "host:port" 格式。
- 模型服务器所理解的模型名称。
- 用于进行推理的数据的序列化示例。

```python
def do_inference(server_addr, model_name, serialized_examples):
parsed_server_addr = server_addr.split(':')
host=parsed_server_addr[0]
port=parsed_server_addr[1]
json_examples = []
for serialized_example in serialized_examples:
example_bytes = base64.b64encode(serialized_example).decode('utf-8')
predict_request = '{"b64": "%s"}' % example_bytes
json_examples.append(predict_request)

json_request = '{"instances": [' + ','.join(map(str, json_examples)) + '] }'
server_url = 'http://' + host + ':' + port + '/v1/models/' + 
model_name + ':predict'
response = requests.post(server_url, data=json_request, 
timeout=5.0)
response.raise_for_status()
prediction = response.json()
print(json.dumps(prediction, indent=4))
```

让我们为我们的样本数据集的预测调用推理函数：

```python
do_inference(server_addr='127.0.0.1:8501',
model_name='online_news_simple',
serialized_examples=serialized_examples)
```

```json
{
  "predictions": [
    {
      "scores": [
        0.775838792,
        0.224161178
      ],
      "classes": [
        "0",
        "1"
      ]
    },
    {
      "scores": [
        0.775838792,
        0.224161178
      ],
      "classes": [
        "0",
        "1"
      ]
    },
    {
      "scores": [
        0.775838792,
        0.224161178
      ],
      "classes": [
        "0",
        "1"
      ]
    }
  ]
}
```

### 图 4.29：测试模型预测

在前面的屏幕截图中，我们可以看到 3 条记录批次的分类输出，以及小费是否大于车费 20% 的概率得分。

## 4.6 构建 Kubeflow Pipeline 编排器

因此，在开始本章之前，我们必须在 GCP 中设置 Kubeflow 集群，我们已经创建了一个 Jupyter notebook；我们将使用它。

从 Kubeflow Dashboard 连接到 Jupyter Notebook 后打开终端一次并安装 TFX SDK。

```bash
!pip install tfx==0.22.0
```

如果出现以下错误，请运行以下命令：

![](img/8f8a671916d96b455297952d0f37b96c_296_0.png)

### 图 4.30：错误

运行以下命令：

```bash
PROTOC_ZIP=protoc-3.7.1-osx-x86_64.zip
```

```
curl -OL
https://github.com/protocolbuffers/protobuf/releases/download/v3.7.1/
$PROTOC_ZIP
sudo unzip -o $PROTOC_ZIP -d /usr/local bin/protoc
sudo unzip -o $PROTOC_ZIP -d /usr/local 'include/*'
rm -f $PROTOC_ZIP
pip install --upgrade protobuf
```

现在，请前往该项目的 GitHub 下载这些文件夹并将这些文件保存到你的 GCP Bucket 中，如以下屏幕截图所示：

![](img/8f8a671916d96b455297952d0f37b96c_297_0.png)

### 图 4.31：Kubeflow Pipeline 文件夹数据和文件

现在，让我们看看管道代码以及如何为 TFX 生成构造性管道。

完成以下步骤：

- 定义用于管道执行的管道参数。
- 模块文件的路径应为 GCS 路径，或烘焙在管道使用的 Docker 镜像中的模块文件。
- CSV 数据文件的路径，其下应有一个 **data.csv** 文件。
- 管道根路径应为 GCS 路径。
- 创建一个基于 Kubeflow 的简单 Chicago Taxi TFX 管道。
- 管道输出的根目录。
- 输入数据目录的位置。
- Transform/Trainer 模块文件的位置。
- 是否启用缓存。

管道是一个 **有向无环图**，每个节点上都有一个容器化进程，该进程运行在 argo 之上。

一个逻辑 TFX 管道对象。之后我们将构建 KubeflowDagRunner，它将转储一个 yaml 文件，该文件将用于在 Kubeflow 中部署以运行管道。

```
import os
from typing import Text
import kfp
import tensorflow_model_analysis as tfma
from tfx.components.evaluator.component import Evaluator
from tfx.components.example_gen.csv_example_gen.component import CsvExampleGen
from tfx.components.example_validator.component import ExampleValidator
from tfx.components.pusher.component import Pusher
from tfx.components.schema_gen.component import SchemaGen
from tfx.components.statistics_gen.component import StatisticsGen
from tfx.components.trainer.component import Trainer
from tfx.components.transform.component import Transform
from tfx.orchestration import data_types
from tfx.orchestration import pipeline
from tfx.orchestration.kubeflow import kubeflow_dag_runner
from tfx.utils.dsl_utils import external_input
from tfx.proto import pusher_pb2, trainer_pb2
```

### 步骤 1：

```
_taxi_module_file_param =
data_types.RuntimeParameter(name='module-file',
default='gs://tfx_taxi_simple/modules/taxi_utils.py',ptype=Text)
```

### 步骤 2：

```
_data_root_param = data_types.RuntimeParameter(name='data-root',
ptype=Text
default='gs:///tfx_taxi_simple/data')
```

### 步骤 3：

```
pipeline_root = os.path.join('gs://{{kfp-default-bucket}}',
'tfx_taxi_simple', kfp.dsl.RUN_ID_PLACEHOLDER)
```

### 步骤 4：

```
def _create_pipeline(pipeline_root: Text, csv_input_location:
data_types.RuntimeParameter,
taxi_module_file: data_types.RuntimeParameter, enable_cache: bool):
examples = external_input(csv_input_location)
example_gen = CsvExampleGen(input=examples)
statistics_gen =
StatisticsGen(examples=example_gen.outputs['examples'])
infer_schema =
SchemaGen(statistics=statistics_gen.outputs['statistics'],
infer_feature_shape=False)
validate_stats =
ExampleValidator(statistics=statistics_gen.outputs['statistics'],
schema=infer_schema.outputs['schema'],)
transform = Transform(examples=example_gen.outputs['examples'],
schema=infer_schema.outputs['schema'],module_file=taxi_module_file)
trainer = Trainer(module_file=taxi_module_file,
transformed_examples=transform.outputs['transformed_examples'],
schema=infer_schema.outputs['schema'],
transform_graph=transform.outputs['transform_graph'],
train_args=trainer_pb2.TrainArgs(num_steps=10),
eval_args=trainer_pb2.EvalArgs(num_steps=5))
```

```
eval_config = tfma.EvalConfig(model_specs=
[tfma.ModelSpec(signature_name='eval')], metrics_specs=
[tfma.MetricsSpec(metrics=
[tfma.MetricConfig(class_name='ExampleCount')], thresholds=
{'binary_accuracy':tfma.MetricThreshold(
value_threshold=tfma.GenericValueThreshold(lower_bound={'value':
0.5}), change_threshold=tfma.GenericChangeThreshold(
direction=tfma.MetricDirection.HIGHER_IS_BETTER,absolute={'value':
-1e-10})})], slicing_specs=
[tfma.SlicingSpec(),tfma.SlicingSpec(feature_keys=['trip_start_hour'])]
model_analyzer =
Evaluator(examples=example_gen.outputs['examples'],
model=trainer.outputs['model'],eval_config=eval_config)
pusher = Pusher(model=trainer.outputs['model'],
model_blessing=model_analyzer.outputs['blessing'],
push_destination=pusher_pb2.PushDestination(
filesystem=pusher_pb2.PushDestination.Filesystem(
base_directory=os.path.join(str(pipeline.ROOT_PARAMETER),
'model_serving'))),)

return
pipeline.Pipeline(pipeline_name='parameterized_tfx_oss',pipeline_root
=pipeline_root, components=[example_gen, statistics_gen,
infer_schema, validate_stats, transform, trainer, model_analyzer,
pusher],enable_cache=enable_cache)
if __name__ == '__main__':
enable_cache = True
pipeline =
_create_pipeline(pipeline_root,_data_root_param,_taxi_module_file_param, enable_cache=enable_cache)
metadata_config =
kubeflow_dag_runner.get_default_kubeflow_metadata_config()
```

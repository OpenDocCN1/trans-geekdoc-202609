
```
from tfx.orchestration.experimental.interactive.interactive_context
import InteractiveContext
from tfx.proto import (pusher_pb2, trainer_pb2)
from tfx.proto.evaluator_pb2 import SingleSlicingSpec
from tfx.utils.dsl_utils import external_input
```
```
from tfx.types.standard_artifacts import (Model, ModelBlessing)
tf.get_logger().propagate = False
pp = pprint.PrettyPrinter()
%load_ext tfx.orchestration.experimental.interactive.notebook_extensions.skip
```

## 设置目录并下载数据

设置根目录的步骤如下：

- 步骤 1：这是您的 TFX pip 包安装的根目录。
- 步骤 2：这是包含 TFX 芝加哥出租车管道示例的目录。
- 步骤 3：这是模型将被推送用于服务的路径。
- 步骤 4：设置日志记录。

```
def setting_directory():
#step1
_tfx_root = tfx.__path__[0]
```
```
print(_tfx_root)
#step2
_taxi_root = os.path.join(_tfx_root, 'examples/chicago_taxi_pipeline')
print(_taxi_root)
#step3
_serving_model_dir = os.path.join(tempfile.mkdtemp(),
'serving_model/taxi_simple')
print(_serving_model_dir)
#step4
absl.logging.set_verbosity(absl.logging.INFO)
return _tfx_root,_taxi_root,_serving_model_dir
```

现在，我们调用前面的函数来设置目录：

```
_tfx_root,_taxi_root,_serving_model_dir=setting_directory()
```

```
def download_data():
_data_root = tempfile.mkdtemp(prefix='tfx-data')
DATA_PATH = 'https://raw.githubusercontent.com/tensorflow/tfx/master/tfx/examples/chicago_taxi_pipeline/data/simple/data.csv'
_data_filepath = os.path.join(_data_root, "data.csv")
urllib.request.urlretrieve(DATA_PATH, _data_filepath)
return _data_root,_data_filepath
```

现在让我们调用前面的函数在目录中下载数据：

```
_data_root,_data_filepath = download_data()
```

让我们预览一下我们的数据集：

![](img/8f8a671916d96b455297952d0f37b96c_249_0.png)

Figure 4.3: 芝加哥数据集

在前面的截图中，我们可以看到数据集中包含的特征；我们将使用它与 TensorFlow 构建分类模型。

## 4.4 TFX 管道组件

TFX 提供了多个 Python 包库，这里将使用它们来创建管道组件。

在本节中，我们使用默认参数创建了 Interactive Context，这将有助于创建临时的 ML Metadata 数据库实例。

```
context = InteractiveContext()
```

```
WARNING:absl:InteractiveContext pipeline_root argument not provided: using temporary directory /tmp/tfx-interactive-2(
WARNING:absl:InteractiveContext metadata_connection_config not provided: using SQLite ML Metadata database at /tmp/tf
```

Figure 4.4: 初始化交互式上下文

接下来，我们将构建管道。

### 4.4.1 ExampleGen

ExampleGen 组件通常位于 TFX 管道的开始处。TFX examplegen 将自定义训练/评估拆分比例，ExampleGen 将输出并设置 **output_config**；例如，Gen 组件。Span 中的每个 Version 都可以进一步细分为多个 Splits。将 Span 分割的最常见用例是将其拆分为训练和评估数据。

本示例中设置了 **hash_buckets**。

![](img/8f8a671916d96b455297952d0f37b96c_251_0.png)

Figure 4.5: Example Gen

前面的图表是 example gen 组件，它将以这种方式拆分数据集。所以，这是 ExampleGen 的架构。

### 组件：ExampleGen

![](img/8f8a671916d96b455297952d0f37b96c_252_0.png)

Figure 4.6: Example Gen 架构

ExampleGen TFX Pipeline 组件将数据摄取到 TFX 管道中。

```
def examplegen(_data_root):
example_gen = CsvExampleGen(input=external_input(_data_root))
return example_gen
```

定义我们下载数据的路径：

```
example_gen= examplegen(_data_root)
context.run(example_gen)
```

![](img/8f8a671916d96b455297952d0f37b96c_253_0.png)

Figure 4.7: Example Gen 输出

前面的截图是 ExampleGen 的输出，我们在其中将数据拆分为训练和评估，并将路径存储如图所示。

### 4.4.2 StatisticsGen

StatisticsGen 组件计算您数据集的统计信息，用于数据分析以及下游组件使用。它使用 TensorFlow Data Validation 库。

### 组件：StatisticsGen

![](img/8f8a671916d96b455297952d0f37b96c_254_0.png)

Figure 4.8: Statistics Gen 架构

StatisticsGen 的输入是我们刚刚使用 ExampleGen 摄取的数据集：

```
def statisticsgen(example_gen):
statistics_gen =
StatisticsGen(examples=example_gen.outputs['examples'])
return statistics_gen
```

```
statistics_gen=statisticsgen(example_gen)
context.run(statistics_gen)
```

![](img/8f8a671916d96b455297952d0f37b96c_255_0.png)

Figure 4.9: Statistics Gen 输出

可视化我们训练数据和评估数据的输出统计信息：

```
%%skip_for_export
context.show(statistics_gen.outputs['statistics'])
```

StatisticsGen 将为我们提供所有特征的分布以及分类和数值列的统计信息，从中我们可以分析偏度和缺失值分析。

![](img/8f8a671916d96b455297952d0f37b96c_255_1.png)

Figure 4.10: Statistics Gen 输出可视化

StatisticsGen TFX 管道组件生成训练数据和服务数据的特征统计信息，可供其他管道组件使用。StatisticsGen 使用 Beam 来扩展到大型数据集。

### 4.4.3 SchemaGen

SchemaGen 组件基于您的数据统计信息生成模式。（模式定义了数据集中特征的预期边界、类型和属性。）它也使用 TensorFlow Data Validation 库。

### 组件：SchemaGen

![](img/8f8a671916d96b455297952d0f37b96c_257_0.png)

Figure 4.11: Schema Gen 架构

SchemaGen 将以我们使用 StatisticsGen 生成的统计信息作为输入，默认情况下查看训练拆分。

```
def schemagen(statistics_gen):
schema_gen =
SchemaGen(statistics=statistics_gen.outputs['statistics'],infer_feature_shape=False)
return schema_gen
```

让我们生成模式表：

```
schema_gen=schemagen(statistics_gen)
%%skip_for_export
context.show(schema_gen.outputs['schema'])
```

输入张量的数据类型模式如下：

| 特征名称 | 类型 | 存在性 | 价数 | 域 |
|---|---|---|---|---|
| 'company' | STRING | 必需 |  | 'company' |
| 'dropoff_census_tract' | INT | 必需 |  | - |
| 'dropoff_community_area' | INT | 必需 |  | - |
| 'dropoff_latitude' | FLOAT | 必需 |  | - |
| 'dropoff_longitude' | FLOAT | 必需 |  | - |
| 'fare' | FLOAT | 必需 | single | - |
| 'payment_type' | STRING | 必需 | single | 'payment_type' |
| 'pickup_census_tract' | INT | 必需 |  | - |
| 'pickup_community_area' | INT | 必需 |  | - |
| 'pickup_latitude' | FLOAT | 必需 |  | - |
| 'pickup_longitude' | FLOAT | 必需 |  | - |
| 'tips' | FLOAT | 必需 | single | - |
| 'trip_miles' | FLOAT | 必需 | single | - |
| 'trip_seconds' | INT | 必需 |  | - |
| 'trip_start_day' | INT | 必需 | single | - |
| 'trip_start_hour' | INT | 必需 | single | - |
| 'trip_start_month' | INT | 必需 | single | - |
| 'trip_start_timestamp' | INT | 必需 | single | - |

Figure 4.12: Schema Gen 输出可视化

所以，schema 是 It 将指定特征值的... The SchemaGen 组件将通过从训练数据自动推断类型、类别和范围来生成该模式。

### 4.4.4 ExampleValidator

**ExampleValidator** 组件根据模式定义的期望检测数据中的异常。它也使用 **TensorFlow Data Validation** 库。

### 组件：ExampleValidator

![](img/8f8a671916d96b455297952d0f37b96c_260_0.png)

Figure 4.13: ExampleValidator 架构

**ExampleValidator** 将以来自 StatisticsGen 的统计信息和来自 SchemaGen 的模式作为输入。默认情况下，它将评估拆分的统计信息与训练拆分的模式进行比较。

```
def examplevalidator(statistics_gen,schema_gen):
 example_validator =
 ExampleValidator(statistics=statistics_gen.outputs['statistics'],schema=
 schema_gen.outputs['schema'])
 return example_validator
```

让我们调用该函数来检查异常报告。

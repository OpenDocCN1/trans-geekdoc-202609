
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

## SETTING DIRECTORY AND DOWNLOAD DATA

Steps for Setting the Root directory are as follows:

- Step 1: This is the root directory for your TFX pip package installation.
- Step 2: This is the directory containing the TFX Chicago Taxi Pipeline example.
- Step 3: This is the path where your model will be pushed for serving.
- Step 4: Set up logging.

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

Now, we call the preceding function to set the directory:

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

Now let’s call the preceding function to download the data in the directory:

```
_data_root,_data_filepath = download_data()
```

Let’s check a glimpse on our dataset:

![](img/8f8a671916d96b455297952d0f37b96c_249_0.png)

Figure 4.3: Chicago Dataset

In the preceding screenshot, we can see the features in our dataset; we will be using that for the classification model building with TensorFlow.

## 4.4 TFX pipeline components

TFX provides several Python package libraries which will be used here to create the pipeline components.

In this section, we have created the Interactive Context using the default parameters, which will help to create the ephemeral ML Metadata database instance.

```
context = InteractiveContext()
```

```
WARNING:absl:InteractiveContext pipeline_root argument not provided: using temporary directory /tmp/tfx-interactive-2(
WARNING:absl:InteractiveContext metadata_connection_config not provided: using SQLite ML Metadata database at /tmp/tf
```

Figure 4.4: Initializing interactive Context

Next, we will build the pipeline.

### 4.4.1 ExampleGen

The ExampleGen component is usually at the start of a TFX pipeline. TFX examplegen will customize the train/eval split ratio, which the ExampleGen will output, set the **output_config**; for example, Gen component. Each Version within a Span can further be subdivided into multiple Splits. The most common use-case for splitting a Span is to split it into the training and eval data.

The **hash_buckets** were set in this example.

![](img/8f8a671916d96b455297952d0f37b96c_251_0.png)

Figure 4.5: Example Gen

The preceding diagram is the example gen component, which will split the dataset in that manner. So, this is the architecture of the ExampleGen.

### Component: ExampleGen

![](img/8f8a671916d96b455297952d0f37b96c_252_0.png)

Figure 4.6: Example Gen Architecture

The ExampleGen TFX Pipeline component ingests the data into TFX pipelines.

```
def examplegen(_data_root):
example_gen = CsvExampleGen(input=external_input(_data_root))
return example_gen
```

Define the path where we downloaded the data:

```
example_gen= examplegen(_data_root)
context.run(example_gen)
```

![](img/8f8a671916d96b455297952d0f37b96c_253_0.png)

Figure 4.7: Example Gen Output

The preceding screenshot is the output for the ExampleGen where we split the data into train and evaluation and stored the path as shown.

### 4.4.2 StatisticsGen

The StatisticsGen component computes the statistics over your dataset for the data analysis, as well as for use in the downstream components. It uses the TensorFlow Data Validation library.

### Component: StatisticsGen

![](img/8f8a671916d96b455297952d0f37b96c_254_0.png)

Figure 4.8: Statistics Gen Architecture

StatisticsGen takes as input, the dataset that we just ingested using ExampleGen:

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

Figure 4.9: Statistics Gen Output

Visualize the outputted statistics of our training data and evaluation data:

```
%%skip_for_export
context.show(statistics_gen.outputs['statistics'])
```

The StatisticsGen will give us the distribution of all the features and stats of the categorical and numerical columns, from which we can analyse the skewness and missing value analysis.

![](img/8f8a671916d96b455297952d0f37b96c_255_1.png)

Figure 4.10: Statistics Gen Output Visualization

The StatisticsGen TFX pipeline component generates the feature statistics over both the training and the serving data, which can be used by the other pipeline components. StatisticsGen uses Beam to scale to large datasets.

### 4.4.3 SchemaGen

The SchemaGen component generates a schema based on your data statistics. (A schema defines the expected bounds, types, and properties of the features in your dataset.) It also uses the TensorFlow Data Validation library.

### Component: SchemaGen

![](img/8f8a671916d96b455297952d0f37b96c_257_0.png)

Figure 4.11: Schema Gen Architecture

SchemaGen will take as input, the statistics that we generated with StatisticsGen, looking at the training split by default.

```
def schemagen(statistics_gen):
schema_gen =
SchemaGen(statistics=statistics_gen.outputs['statistics'],infer_feature_shape=False)
return schema_gen
```

Let’s generate the schema table:

```
schema_gen=schemagen(statistics_gen)
%%skip_for_export
context.show(schema_gen.outputs['schema'])
```

Data schema for the type of input tensors is as follows:

| Feature name | Type | Presence | Valency | Domain |
|---|---|---|---|---|
| 'company' | STRING | required |  | 'company' |
| 'dropoff_census_tract' | INT | required |  | - |
| 'dropoff_community_area' | INT | required |  | - |
| 'dropoff_latitude' | FLOAT | required |  | - |
| 'dropoff_longitude' | FLOAT | required |  | - |
| 'fare' | FLOAT | required | single | - |
| 'payment_type' | STRING | required | single | 'payment_type' |
| 'pickup_census_tract' | INT | required |  | - |
| 'pickup_community_area' | INT | required |  | - |
| 'pickup_latitude' | FLOAT | required |  | - |
| 'pickup_longitude' | FLOAT | required |  | - |
| 'tips' | FLOAT | required | single | - |
| 'trip_miles' | FLOAT | required | single | - |
| 'trip_seconds' | INT | required |  | - |
| 'trip_start_day' | INT | required | single | - |
| 'trip_start_hour' | INT | required | single | - |
| 'trip_start_month' | INT | required | single | - |
| 'trip_start_timestamp' | INT | required | single | - |

Figure 4.12: Schema Gen Output Visualization

So, schema is a part of It will specify the data types for the feature values, whether that feature has to be present in all the examples, value ranges, and other properties. The SchemaGen

component will generate that schema by inferring the types, categories, and ranges from the training data automatically.

### 4.4.4 ExampleValidator

The **ExampleValidator** component detects the anomalies in your data, based on the expectations defined by the schema. It also uses the **TensorFlow Data Validation** library.

### Component: ExampleValidator

![](img/8f8a671916d96b455297952d0f37b96c_260_0.png)

Figure 4.13: ExampleValidator Architecture

**ExampleValidator** will take as input, the statistics from StatisticsGen, and the schema from SchemaGen. By default, it compares the statistics from the evaluation split to the schema from the training split.

```
def examplevalidator(statistics_gen,schema_gen):
 example_validator =
 ExampleValidator(statistics=statistics_gen.outputs['statistics'],schema=
 schema_gen.outputs['schema'])
 return example_validator
```

Let’s call the function to check the anomaly report.

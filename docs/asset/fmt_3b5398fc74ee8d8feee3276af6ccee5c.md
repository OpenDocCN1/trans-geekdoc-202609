
```python
from sagemaker.estimator import SKLearn
sklearn_estimator = SKLearn(
    entry_point="<Training script name>",
    hyperparameters=<List of hyperparameters>,
    role=AWS IAM role,
    instance_count=Number of instances,
    instance_type="<Instance type>",
    framework_version="<sklearn version>"
)
sklearn_estimator.fit("training data")
```

```python
from sagemaker.estimator import Estimator
custom_estimator = Estimator (
    Custom_training_img,
    role=AWS IAM role,
    instance_count=Number of instances,
    instance_type="<Instance type>"
)
custom_estimator.fit("training data location")
```

除了使用 SageMaker Python SDK 启动训练外，您还可以使用 `boto3` 库和 SageMaker CLI 命令启动训练作业。

# 自动化支持

SageMaker 训练服务通过一组 API 暴露，可以通过集成外部应用程序或工作流工具（如 `Airflow` 和 `AWS Step Functions`）来实现自动化。例如，它可以作为基于 `Airflow` 的端到端 ML 工作流中的步骤之一。某些工作流工具（如 `Airflow` 和 `AWS Step Functions`）提供了 SageMaker 特有的连接器，以便更无缝地与 SageMaker 训练服务交互。SageMaker 训练服务还提供了 Kubernetes 运算符，因此它可以作为 Kubernetes 工作流的一部分进行集成和自动化。示例代码显示了如何通过 AWS `boto3` SDK 使用底层 API 启动训练作业：

```python
import boto3
client = boto3.client('sagemaker')
response = client.create_training_job(
    TrainingJobName='job name',
    HyperParameters={list of parameters and value},
    AlgorithmSpecification={...},
    RoleArn='AWS IAM Role',
    InputDataConfig=[...],
    OutputDataConfig={...},
    ResourceConfig={...},
    ....
)
```

关于使用 `Airflow` 作为工作流工具，以下示例展示了如何将 `Airflow` SageMaker operator 作为工作流定义的一部分。这里，`train_config` 包含了训练配置细节，例如训练估计器、训练实例类型和数量以及训练数据位置：

```python
import airflow
from airflow import DAG
from airflow.contrib.operators.sagemaker_training_operator
import SageMakerTrainingOperator
default_args = {
    'owner': 'myflow',
    'start_date': '2021-01-01'
}
dag = DAG('tensorflow_training', default_args=default_args,
    schedule_interval='@once')
```

```python
train_op = SageMakerTrainingOperator(
  task_id='tf_training',
  config=train_config,
  wait_for_completion=True,
  dag=dag)
```

SageMaker 还有一个一个名为 `SageMakerPipelines` 的内置工作流自动化工具。可以使用 `SageMaker TrainingStep` API 创建训练步骤，并成为更大的 SageMaker Pipelines 工作流的一部分。

# 模型训练生命周期管理

SageMaker 训练管理模型训练过程的生命周期。它使用 `AWS IAM` 作为对其功能进行身份验证和授权的机制。一旦授权，它将提供所需的设施，为不同的模型训练需求部署软件栈，将数据从源端移动到训练节点，并启动训练作业。训练作业完成后，模型产物将保存到 S3 输出桶中，并拆毁基础设施。对于血缘追踪，会捕获训练元数据，例如源数据集、模型训练容器、超参数和模型输出。作业运行中的任何日志都会保存在 `CloudWatch Logs` 中，而 CPU 和 GPU 利用率等系统指标会被采集到 `CloudWatch` 指标中。

取决于整体端到端 ML 平台架构，训练环境还可以托管数据预处理、模型验证和模型训练后处理的服务，因为这些是端到端 ML 流中的重要步骤。对于这些有多种技术选项可用，例如 SageMaker 处理服务和 `AWS Lambda`。

# 模型托管环境深度解析

企业级模型托管环境需要以安全、高效且可扩展的方式支持广泛的 ML 框架。它应该配备一组预构建的推理引擎，能够通过 RESTful API 或 `grpc` 协议开箱即用提供模型服务。它还需要提供灵活性，以托管满足独特需求的自定义构建的推理引擎。用户还应该能够访问不同的硬件设备，例如 CPU、GPU 和专用芯片。

某些推理模式需要更复杂的推理图，例如流量分 `own`、请求转换或模型集成支持。模型托管环境可以作为开箱功能提供这种能力，或者为构建推理图提供技术选项。其他常见的模型托管能力包括概念漂移检测和模型性能检测。当生产数据的统计特征偏离用于训练的数据时，就会发生概念漂移。概念漂移的一个示例是特征在生产环境中的均值和标准差与训练环境相比发生了变化。

模型托管环境中的组件可以通过其 API、脚本或 IaC 部署（如 `AWS CloudFormation`）参与工作流。例如，可以使用 `CloudFormation` 模板部署 RESTful 端点，或者作为自动化工作流的一部分调用其 API。

从安全角度来看，模型托管环境需要提供身份验证和授权控制，以管理对控制平面（管理功能）和数据平面（模型端点）的访问。针对托管环境执行的访问和操作应该记录审计。为了操作支持，托管环境需要启用状态日志和系统监控，以支持系统观测性和问题排查。

SageMaker 托管服务是一个全托管的模型托管服务。与我们在书中之前回顾的 `KFServing` 和 `Seldon Core` 类似，SageMaker 托管服务也是多框架模型服务服务。接下来，让我们仔细查看其企业级模型托管的能力。

# 推理引擎

SageMaker 为多个 ML 框架提供了内置的推理引擎，包括 `scikit-learn`、`XGBoost`、`TensorFlow`、`PyTorch` 和 `Spark ML`。SageMaker 以 Docker 容器的形式提供这些内置推理引擎。要建立 API 端点来服务模型，您只需要提供模型产物基础设施配置。以下是模型服务的选项列表：

- *提供 TensorFlow 模型：SageMaker 使用 `TensorFlow Serving` 作为 TensorFlow 模型的推理引擎。以下代码示例展示了如何使用 SageMaker 托管服务部署 TensorFlow Serving 模型：

```python
from sagemaker.tensorflow.serving import Model
tensorflow_model = Model(
    model_data=<S3 location of the ML model artifacts>,
    role=<AWS IAM role>
)
```

| framework_version=<tensorflow version |

| ) tensorflow_model.deploy( initial_instance_count=<instance count>, instance_type=<instance type> ) |

- 部署 PyTorch 模型：SageMaker 托管在底层使用 `TorchServe` 来部署 PyTorch 模型。以下代码示例展示了如何部署 PyTorch 模型：

```python
from sagemaker.pytorch.model import PyTorchModel
```

```python
pytorch_model = PyTorchModel( model_data=<S3 location of the PyTorch model artifacts>, role=<AWS IAM role>, framework_version=<PyTorch version> )
pyorch_model.deploy( initial_instance_count=<instance count>, instance_type=<instance type> )
```

- 部署 Spark ML 模型：对于基于 Spark ML 模型，SageMaker 使用 `MLEap` 作为后端来部署 Spark ML 模型。这些 Spark ML 模型需要序列化为 MLeap 格式。以下代码示例展示了如何使用 SageMaker 托管服务部署 Spark ML 模型：

```python
import sagemaker
from sagemaker.sparkml.model import SparkML
sparkml_model = SparkMLModel( model_data=<S3 location of the Spark ML model artifacts>, role=<AWS IAM role>, sagemaker_session=sagemaker.Session(), name=<Model name>, env={"SAGEMAKER_SPARKML_SCHEMA": <schema_json> } )
```

```python
sparkml_model.deploy(
    initial_instance_count=<instance count>,
    instance_type=<instance type>
)
```

- 部署 XGBoost 模型：SageMaker 提供了一个 XGBoost 模型服务器用于部署训练好的 XGBoost 模型。在底层，它使用 Nginx、Gunicorn 和 Flask 作为模型推理架构的一部分。入口 Python 脚本加载训练好的 XGBoost 模型，并可以可选地执行数据的预处理和后处理：

```python
from sagemaker.xgboost.model import XGBoostModel
xboost_model = XGBoostModel(
model_data=<S3 location of the XGBoost ML artifacts,
role=<AWS IAM role>,
entry_point=<entry python script,
framework_version=<xgboost version>
)
xboost_model.deploy(
instance_type=<instance type>,
initial_instance_count=<instance count>
)
```

- 部署 scikit-learn 模型：SageMaker 提供了一个内置的部署容器用于部署基于 scikit-learn 的模型。其技术栈与 XGBoost 模型服务器类似：

```python
from sagemaker.sklearn.model import SKLearnModel
sklearn_model = SKLearnModel(
model_data=<S3 location of the XGBoost ML artifacts,
role=<AWS IAM role>,
entry_point=<entry python script,
framework_version=<scikit-learn version>
)
sklearn_model.deploy(instance_type=<instance type>,
initial_instance_count=<instance count>)
```

- 使用自定义容器部署模型：对于自定义创建的推理容器，您可以遵循类似的语法来部署模型。主要的区别在于需要提供自定义推理容器镜像的 uri。您可以在 `https://docs.aws.amazon.com/sagemaker/latest/dg/adapt-inference-container.html` 找到构建自定义推理容器的详细文档。

```python
from sagemaker.model import Model
custom_model = Model(
    Image_uri = <custom inference container image uri>,
    model_data=<S3 location of the ML model artifacts,
    role=<AWS IAM role,
    framework_version=<scikit-learn version>
)
custom_model.deploy(instance_type=<instance type>,
initial_instance_count=<instance count>)
```

SageMaker 托管提供推理流水线功能，允许您创建一个线性序列的容器（最多 15 个），以便在调用模型进行预测前后执行数据处理。SageMaker 托管可以支持多个版本模型之间的流量划分，以进行 A/B 测试。

SageMaker 托管可以使用 `AWS CloudFormation` 模板进行配置。还支持使用 `AWS CLI` 进行脚本自动化，并可以通过其 API 集成到自定义应用程序中。以下是不同端点自动化方法的代码示例：

- 以下是一个用于 SageMaker 端点部署的 CloudFormation 代码示例。您可以在 `https://github.com/PacktPublishing/The-Machine-Learning-Solutions-Architect-Handbook/blob/main/Chapter09/sagemaker_hosting.yaml` 找到完整代码。

| Description: "Model hosting cloudformation template" |

| :--- |

| Resources: |

| Endpoint: |

| Type: "AWS::SageMaker::Endpoint" |

| Properties: |

| EndpointConfig: | !GetAtt EndpointConfig.EndpointConfigName |

| EndpointConfig:| |

| Type: "AWS::SageMaker::EndpointConfig" |

| Properties: |

| ProductionVariants: |

| - InitialInstanceCount: 1 |

| InitialVariantWeight: 1.0 |

| InstanceType: ml_t2.large |

| ModelName: !GetAtt Model.ModelName |

| VariantName: !GetAtt Model.ModelName |

| Model: |

| Type: "AWS::SageMaker::Model" |

| Properties: |

| PrimaryContainer: |

| Image: <container uri> |

| ExecutionRoleArn: !GetAtt ExecutionRole.Arn |

| ... |

- * 以下是一个用于 SageMaker 端点部署的 `AWS CLI` 示例：

```bash
aws sagemaker create-model --model-name <value>
--execution-role-arn <value>
aws sagemaker create-endpoint-config --endpoint-config-name <value> --production-variants <value>
aws sagemaker create-endpoint --endpoint-name <value>
```

## 身份验证与安全

SageMaker 托管服务使用 `AWS IAM` 作为控制控制平面 API（例如，创建端点）和数据平面 API（例如，调用托管端点）访问的机制。如果您需要为数据平面支持其他身份验证方法（如 OpenID Connect `OIDC`），可以使用代理服务作为前端来管理用户身份验证，以及流量限制等 API 管理功能。

## 监控与日志

SageMaker 提供开箱即用的监控和日志功能以协助运维。它监控系统资源指标（例如 CPU/GPU 利用率）以及模型调用指标（例如调用次数、模型延迟和失败）。这些监控指标和任何模型处理日志都会被 `CloudWatch` 指标和 `CloudWatch Logs` 。

## 在 ML 工作中引入 MLOps

类似于适用于传统软件开发和部署的 DevOps 实践，`MLOps` 实践旨在简化 ML 流水线的构建和部署过程，并改进数据科学家/机器学习工程师、数据工程师和运维团队之间的协作。具体而言，`MLOps` 实践旨在端到端的 ML 生命周期中带来以下主要收益：

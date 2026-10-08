

# 模型训练引擎

SageMaker 训练服务为一系列 ML/DL 库提供了内置的模型训练能力。此外，您也可以携带自己的 Docker 容器来满足定制化的模型训练需求。以下是 SageMaker Python SDK 支持的选项子集：

- *训练 TensorFlow 模型：SageMaker 为 TensorFlow 模型提供了一个内置的训练容器。以下代码示例展示了如何使用 TensorFlow 估计器 API 通过内置容器训练 TensorFlow 模型：

```python
from sagemaker.tensorflow import TensorFlow
tf = TensorFlow(
    entry_point="<Training script name>",
    role="<AWS IAM role>",
    instance_count=<Number of instances>,
    instance_type="<Instance type>",
    framework_version="<TensorFlow version>",
    py_version="<Python version>",
)
tf.fit("<Training data location>")
```

- *训练 PyTorch 模型：SageMaker 为 PyTorch 模型提供一个内置的训练容器。以下代码示例展示了如何使用 PyTorch 估计器训练 PyTorch 模型：

```python
from sagemaker.pytorch import PyTorch
pytorch_estimator = PyTorch(
    entry_point="<Training script name>",
    role="<AWS IAM role>",
    instance_count=<Number of instances>,
    instance_type="<Instance type>",
    framework_version="<PyTorch version>",
    py_version="<Python version>",
)
pytorch_estimator.fit("<Training data location>")
```

- *训练 XGBoost 模型：通过内置容器也支持 XGBoost 训练。以下代码示例展示了使用 XGBoost 估计器训练 XGBoost 模型的语法：

```python
from sagemaker.xgboost.estimator import XGBoost
xgb_estimator = XGBoost (
    entry_point="<Training script name>",
    hyperparameters=<List of hyperparameters>,
    role=AWS IAM role,
    instance_count=Number of instances,
    instance_type="<Instance type>",
    framework_version="<Xgboost version>"
)
xgb_estimator.fit("train data location")
```

- *训练 scikit-learn 模型：以下代码示例展示了如何使用内置容器训练 scikit-learn 模型：

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

除了使用 SageMaker Python SDK 启动训练外，您还可以使用 boto3 库和 SageMaker CLI 命令启动训练作业。

# 自动化支持

SageMaker 训练服务通过一组 API 暴露，可以通过集成外部应用程序或工作流工具（如 Airflow 和 AWS Step Functions）来实现自动化。例如，它可以作为基于 Airflow 的端到端 ML 工作流中的步骤之一。某些工作流工具（如 Airflow 和 AWS Step Functions）提供了 SageMaker 特有的连接器，以便更无缝地与 SageMaker 训练服务交互。SageMaker 训练服务还提供了 Kubernetes 运算符，因此它可以作为 Kubernetes 工作流的一部分进行集成和自动化。示例代码显示了如何通过 AWS boto3 SDK 使用底层 API 启动训练作业：

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

关于使用 Airflow 作为工作流工具，以下示例展示了如何将 Airflow SageMaker operator 作为工作流定义的一部分。这里，train_config 包含了训练配置细节，例如训练估计器、训练实例类型和数量以及训练数据位置：

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

SageMaker 还有一个一个名为 SageMakerPipelines 的内置工作流自动化工具。可以使用 SageMaker TrainingStep API 创建训练步骤，并成为更大的 SageMaker Pipelines 工作流的一部分。

# 模型训练生命周期管理

SageMaker 训练管理模型训练过程的生命周期。它使用 AWS IAM 作为对其功能进行身份验证和授权的机制。一旦授权，它将提供所需的设施，为不同的模型训练需求部署软件栈，将数据从源端移动到训练节点，并启动训练作业。训练作业完成后，模型产物将保存到 S3 输出桶中，并拆毁基础设施。对于血缘追踪，会捕获训练元数据，例如源数据集、模型训练容器、超参数和模型输出。作业运行中的任何日志都会保存在 CloudWatch Logs 中，而 CPU 和 GPU 利用率等系统指标会被采集到 CloudWatch 指标中。

取决于整体端到端 ML 平台架构，训练环境还可以托管数据预处理、模型验证和模型训练后处理的服务，因为这些是端到端 ML 流中的重要步骤。对于这些有多种技术选项可用，例如 SageMaker 处理服务和 AWS Lambda。

# 模型托管环境深度解析

企业级模型托管环境需要以安全、高效且可扩展的方式支持广泛的 ML 框架。它应该配备一组预构建的推理引擎，能够通过 RESTful API 或 grpc 协议开箱即用提供模型服务。它还需要提供灵活性，以托管满足独特需求的自定义构建的推理引擎。用户还应该能够访问不同的硬件设备，例如 CPU、GPU 和专用芯片。

某些推理模式需要更复杂的推理图，例如流量分 own、请求转换或模型集成支持。模型托管环境可以作为开箱功能提供这种能力，或者为构建推理图提供技术选项。其他常见的模型托管能力包括概念漂移检测和模型性能检测。当生产数据的统计特征偏离用于训练的数据时，就会发生概念漂移。概念漂移的一个示例是特征在生产环境中的均值和标准差与训练环境相比发生了变化。

模型托管环境中的组件可以通过其 API、脚本或 IaC 部署（如 AWS CloudFormation）参与工作流。例如，可以使用 CloudFormation 模板部署 RESTful 端点，或者作为自动化工作流的一部分调用其 API。

从安全角度来看，模型托管环境需要提供身份验证和授权控制，以管理对控制平面（管理功能）和数据平面（模型端点）的访问。针对托管环境执行的访问和操作应该记录审计。为了操作支持，托管环境需要启用状态日志和系统监控，以支持系统观测性和问题排查。

SageMaker 托管服务是一个全托管的模型托管服务。与我们在书中之前回顾的 KFServing 和 Seldon Core 类似，SageMaker 托管服务也是多框架模型服务服务。接下来，让我们仔细查看其企业级模型托管的能力。

# 推理引擎

SageMaker 为多个 ML 框架提供了内置的推理引擎，包括 scikit-learn、XGBoost、TensorFlow、PyTorch 和 Spark ML。SageMaker 以 Docker 容器的形式提供这些内置推理引擎。要建立 API 端点来服务模型，您只需要提供模型产物基础设施配置。以下是模型服务的选项列表：

- *提供 TensorFlow 模型：SageMaker 使用 TensorFlow Serving 作为 TensorFlow 模型的推理引擎。以下代码示例展示了如何使用 SageMaker 托管服务部署 TensorFlow Serving 模型：

```python
from sagemaker.tensorflow.serving import Model
tensorflow_model = Model(
    model_data=<S3 location of the ML model artifacts>,
    role=<AWS IAM role>
)
```

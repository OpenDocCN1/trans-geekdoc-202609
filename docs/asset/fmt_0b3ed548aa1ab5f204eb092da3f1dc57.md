
# Amazon Elastic Kubernetes Service (Amazon EKS)

Amazon Elastic Kubernetes Service (Amazon EKS) 利用 Kubernetes（一个领先的开源容器编排平台）的强大功能进行非托管模型部署。通过使用 Amazon EKS，您可以使用 Kubernetes 原生工具和 API 高效地部署、管理和扩展容器化 ML 模型。Amazon EKS 自动执行设置和维护 Kubernetes 控制平面的关键方面，提供高可用性、安全性和性能，使您能够专注于运行 ML 工作负载。此外，Amazon EKS 还与其他 AWS 服务无缝集成，例如用于数据存储的 `Amazon S3`、用于安全访问控制的 `AWS IAM`，以及用于监控和日志记录的 `Amazon CloudWatch`。

此外，Amazon EKS 提供了无与伦比的灵活性和控制力，让您能够充分利用 Kubernetes 的全部功能进行 ML 部署。通过支持 Kubernetes 插件和第三方工具，您可以使用服务网格、日志记录和监控解决方案等高级功能来增强部署环境。Amazon EKS 让您能够利用 Kubernetes 的基本功能，如自动扩缩容、滚动更新和自我修复，确保您的模型始终处于最佳运行状态。这种灵活性对于拥有现有 Kubernetes 基础设施或专业知识的组织非常有益，因为无论是在本地还是在云端运行，它都能提供一致的部署体验。总体而言，Amazon EKS 为部署和管理 ML 模型提供了一个强大且可扩展的平台，使其成为希望充分发挥 Kubernetes 潜力的组织的另一个宝贵选择。

# AWS Lambda

AWS Lambda 提供了一种无服务器计算模型，非常适合部署 ML 模型，尤其是当您需要大规模运行推理而无需管理底层基础设施时。借助 `AWS Lambda`，您可以将 ML 模型打包为 `Lambda` 函数并进行部署，以便根据传入的请求自动扩缩容。这种按需付费模式确保您仅为模型消耗的计算时间付费，使其成为运行推理任务的一种具有成本效益的解决方案。`Lambda` 函数可由各种 AWS 服务触发，例如 `API Gateway`、`S3` 或 `DynamoDB`，从而允许您为 ML 应用程序构建无缝且集成的部署管道。

使用 `AWS Lambda` 进行非托管模型部署的一个显著优势是其能够轻松处理高度可变的工作负载。`Lambda` 会根据请求数量自动扩缩容，确保您的模型无需人工干预即可应对需求的突然激增。这对于流量模式不可预测或存在季节性变化的应用程序特别有益。此外，`Lambda` 与 `Amazon CloudWatch` 的集成提供了强大的监控和日志记录功能，使您能够跟踪已部署模型的性能和运行状况。您可以设置警报和通知，以便随时了解任何问题或异常，确保您的模型始终处于最佳运行状态。

最后，`AWS Lambda` 支持多种编程语言，包括广泛用于 ML 的 `Python`。这种灵活性使您能够使用熟悉的工具和框架来开发和部署模型。您还可以利用 `AWS Lambda Layers` 来管理依赖项并在多个函数之间共享通用代码，从而简化部署流程。`Lambda` 的无状态特性意味着函数的每次调用都是独立的，确保了性能和可靠性的一致性。通过将 `AWS Lambda` 与其他 AWS 服务（如用于模型存储的 `S3` 和用于创建 RESTful API 的 `API Gateway`）相结合，您可以为 ML 模型构建一个可扩展、具有成本效益且完全托管的部署解决方案。

# 为边缘设备优化 ML 模型

为边缘设备优化 ML 模型涉及多种策略，以确保高效的性能和资源利用。`Amazon SageMaker Neo` 是一项专为此目的设计的强大服务，使开发人员能够轻松地在各种边缘设备上优化和部署 ML 模型。`Amazon SageMaker Neo` 会编译和调优模型，使其在特定的硬件和软件配置上高效运行，这使其成为边缘部署的理想选择。

借助 `Amazon SageMaker Neo`，您可以为各种边缘设备优化模型，包括由 `ARM`、`Intel`、`Nvidia` 和其他处理器驱动的设备。该服务支持流行的框架，如 `TensorFlow`、`TensorFlow-Lite`、`PyTorch` 和 `Open Neural Network Exchange (ONNX)` 标准格式，为不同的开发工作流提供了灵活性和兼容性。`Amazon SageMaker Neo` 会自动应用量化、压缩和剪枝等技术，以减小 ML 模型的大小和复杂性，确保它们在资源受限的设备上高效运行。

该流程始于训练您的 ML 模型（在云端使用 `Amazon SageMaker` 或其他地方）。模型训练完成后，您可以使用 `Amazon SageMaker Neo` 对其进行编译和优化，以适配您的目标边缘设备。`Amazon SageMaker Neo` 会创建一个针对目标硬件高度优化的二进制文件，从而实现更快、更高效的推理。这种方法不仅降低了延迟，还节省了能源，使其适用于低功耗边缘设备。

为了持续监控和更新部署在边缘设备上的 ML 模型，`Amazon SageMaker Neo` 提供了空中下载技术（OTA）更新工具。这确保了模型保持最新状态，并且无需物理接触设备即可长期保持高准确性。借助 `Amazon SageMaker Neo`，您可以创建响应迅速、安全且稳健的 AI 应用程序，在边缘设备上提供卓越的用户体验。

您可以通过访问 `https://docs.aws.amazon.com/sagemaker/latest/dg/neo-supported-devices-edge.html` 查看支持的边缘设备、云实例和框架版本列表。

以下代码片段展示了导出预训练 `TensorFlow` 模型、将其上传到 `S3` 并创建 `Amazon SageMaker Neo` 编译作业以针对使用 `Apple Core ML` 的 iPhone 进行优化的示例：

```python
import tensorflow as tf
import boto3
from sagemaker import get_execution_role, Session

# Step 1: Export the Pre-trained Model
# Load your pre-trained model
model = tf.keras.models.load_model('path_to_your_model.h5')

# Save the model in the SavedModel format
model.save('saved_model_path')

# Step 2: Upload the Model to S3
s3 = boto3.client('s3')
s3.upload_file('saved_model_path', 'your-bucket', 'saved_model_path')

# Step 3: Create a SageMaker Neo Compilation Job
# Initialize SageMaker session
sagemaker_session = Session()

# Get the execution role
role = get_execution_role()

# Define the S3 bucket paths
input_model_path = 's3://your-bucket/saved_model_path'
output_model_path = 's3://your-bucket/compiled-model'

# Create a Neo compilation job
sagemaker_client = boto3.client('sagemaker')

response = sagemaker_client.create_compilation_job(
    CompilationJobName='MyCompilationJob',
    RoleArn=role,
    InputConfig={
        'S3Uri': input_model_path,
        'DataInputConfig': '{"input": [1, 224, 224, 3]}',
        'Framework': 'TENSORFLOW'
    },
    OutputConfig={
        'S3OutputLocation': output_model_path,
        'TargetDevice': 'ml_coreml'  # Target device for iPhone
    },
    StoppingCondition={
        'MaxRuntimeInSeconds': 3600
    }
)

# Wait for the compilation job to complete
sagemaker_client.get_waiter('compilation_job_completed_or_stopped').wait(
    CompilationJobName='MyCompilationJob'
)

# Check the status of the compilation job
status = sagemaker_client.describe_compilation_job(
    CompilationJobName='MyCompilationJob'
)['CompilationJobStatus']
print(f'Compilation job status: {status}')
```

# 高级模型部署技术

`Amazon SageMaker AI` 提供了高级部署技术，以确保您的 ML 模型在生产环境中实现最佳且可靠的性能。借助 `Amazon Application Auto Scaling`，您可以根据预定义指标自动扩缩容 `SageMaker` 终端节点，从而在可变流量负载期间确保高效的资源利用和成本管理。蓝/绿部署等部署策略，以及金丝雀测试、影子测试和 A/B 测试等测试策略，可实现向新模型版本的无缝可靠过渡，并将中断降至最低。这些技术将在以下章节中介绍，为使用 `Amazon SageMaker AI` 有效部署 ML 模型提供一个全面的框架。

## 自动扩缩容终端节点

### Amazon SageMaker AI 端点自动扩缩容

Amazon SageMaker AI 端点自动扩缩容通过水平扩缩（缩容、扩容）负责处理传入推理请求的实例，确保您部署的 ML 模型能够高效应对不同级别的流量。Amazon Application Auto Scaling 允许您根据预定义指标（如 CPU 利用率或请求数）自动调整 Amazon SageMaker AI 端点的实例副本数量。这有助于在控制成本的同时保持最佳性能。首先，您需要使用 `application-autoscaling boto3` 客户端为端点配置自动扩缩容策略。

#### 为实时端点创建自动扩缩容策略

首先，让我们为实时端点创建一个自动扩缩容策略。为此，您需要定义两个组件：

*   **扩缩容目标**：设置扩缩容的边界（例如，最小 1 个实例，最大 10 个实例）
*   **扩缩容策略**：指定要监控的指标（例如 `SageMakerVariantInvocationsPerInstance` 或 `CPUUtilization`）、该指标的目标值，以及扩容或缩容的条件

以下是一个简单的 Python 示例来说明这一点：

```python
import boto3

client = boto3.client('application-autoscaling')

# 注册可扩缩容目标
response = client.register_scalable_target(
    ServiceNamespace='sagemaker',
    ResourceId='endpoint/your-endpoint-name/variant/AllTraffic',
    ScalableDimension='sagemaker:variant:DesiredInstanceCount',
    MinCapacity=1,
    MaxCapacity=10
)

# 创建扩缩容策略
response = client.put_scaling_policy(
    PolicyName='ScalingPolicy',
    ServiceNamespace='sagemaker',
    ResourceId='endpoint/your-endpoint-name/variant/AllTraffic',
    ScalableDimension='sagemaker:variant:DesiredInstanceCount',
    PolicyType='TargetTrackingScaling',
    TargetTrackingScalingPolicyConfiguration={
        'TargetValue': 70.0,  # 每个实例的目标端点调用次数
        'PredefinedMetricSpecification': {
            'PredefinedMetricType': 'SageMakerVariantInvocationsPerInstance',
        },
        'ScaleInCooldown': 300,
        'ScaleOutCooldown': 300
    }
)
```

在本示例中，自动扩缩容是根据 Amazon SageMaker AI 端点每个实例的调用次数（请求数）触发的。具体而言，扩缩容策略设定为维持每个实例平均 70 次调用。如果每个实例的平均调用次数超过 70，策略将自动增加更多实例（扩容）以处理增加的负载。反之，如果每个实例的平均调用次数降至 70 以下，策略将减少实例数量（缩容）以优化资源使用。这种“弹性”行为确保您的实时推理端点能够动态适应不断变化的流量水平，保持性能和效率。

`ScaleInCooldown` 和 `ScaleOutCooldown` 参数分别定义了缩容和扩容操作的冷却期（以秒为单位）。在本例中，两者均设置为 300 秒（5 分钟）。当触发扩缩容操作（如增加实例（扩容）或减少实例（缩容））时，冷却期确保在冷却期结束前不会采取同类型的进一步扩缩容操作。这有助于防止因短期流量波动而触发快速且过度的扩缩容操作，确保系统有足够时间稳定下来，然后再考虑下一次扩缩容调整。

#### 基于 CPU 利用率进行扩缩容

让我们看另一个基于 CPU 利用率进行扩缩容的示例。我们可以修改扩缩容策略以使用自定义指标，例如平均 CPU 利用率。具体操作如下：

```python
import boto3

client = boto3.client('application-autoscaling')

# 注册可扩缩容目标
response = client.register_scalable_target(
    ServiceNamespace='sagemaker',
    ResourceId='endpoint/your-endpoint-name/variant/AllTraffic',
    ScalableDimension='sagemaker:variant:DesiredInstanceCount',
    MinCapacity=1,
    MaxCapacity=10
)

# 创建扩缩容策略
response = client.put_scaling_policy(
    PolicyName='CPUScalingPolicy',
    ServiceNamespace='sagemaker',
    ResourceId='endpoint/your-endpoint-name/variant/AllTraffic',
    ScalableDimension='sagemaker:variant:DesiredInstanceCount',
    PolicyType='TargetTrackingScaling',
    TargetTrackingScalingPolicyConfiguration={
        'TargetValue': 50.0,  # 目标平均 CPU 利用率
        'CustomizedMetricSpecification': {
            'MetricName': 'CPUUtilization',
            'Namespace': 'AWS/SageMaker',
            'Dimensions': [{'Name': 'EndpointName', 'Value': 'your-endpoint-name'}],
            'Statistic': 'Average',
            'Unit': 'Percent'
        },
        'ScaleInCooldown': 300,
        'ScaleOutCooldown': 300
    }
)
```

在第二个示例中，自动扩缩容是根据运行 Amazon SageMaker AI 端点的实例的平均 CPU 利用率触发的。扩缩容策略设定为维持 50% 的平均 CPU 利用率。如果实例的平均 CPU 使用率超过 50%，策略将自动增加更多实例（扩容）以处理增加的负载。反之，如果平均 CPU 使用率降至 50% 以下，策略将减少实例数量（缩容）以优化资源使用。冷却期确保这些扩缩容操作不会过于频繁地触发，从而在进行进一步调整之前让系统有时间稳定下来。

这两个程序演示了如何使用 Amazon Application Auto Scaling——具体来说是**目标跟踪**自动扩缩容——来“弹性”调整 Amazon SageMaker AI 端点的实例数量，确保最佳性能、可靠性和成本效益。

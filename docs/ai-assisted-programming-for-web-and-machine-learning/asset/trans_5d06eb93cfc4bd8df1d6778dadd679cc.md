
通过提供可扩展的基础设施、高可用性、内置的可观测性、强大的安全性以及与 DevOps 和 MLOps 工作流的无缝集成，来交付机器学习模型：

-   **弹性扩展性：** 云服务根据实时需求自动分配或减少计算资源。这确保了空闲期间的成本效益以及用量高峰期间的性能不中断。

-   **高可用性：** 部署在云端的模型由多区域和多可用区冗的支持，提供了容错能力，即使在基础设施故障时也能最大限地减少停机时间。

-   **集成监控：** 云平台内置仪表板、日志和告警系统，允许团队实时跟踪模型延迟、吞吐量、使用模式和错误。

-   **安全性与合规性：** 细粒度访问控制、数据加密、审计跟踪和预配置合规性标准等功能，使云平台适用于医疗、金融和政府等受监管行业。

-   **DevOps 和 MLOps 集成：** 与 CI/CD 工具的无缝集成实现了自动化部署、持续模型重训练和全生命周期管理，为稳健的 MLOps 流水线奠定了基础。

简而言之，云部署将 ML 模型交付从手动的、基础设施密集型的任务转变为与企业软件实践一致的可扩展、安全且自动的过程。

## 使用 AWS SageMaker 部署 PyTorch 模型

AWS SageMaker 通过其 Python SDK 为 PyTorch 模型提供了无缝的部署体验。通过抽象基础设施管理的复杂性，允许开发者以极配置快速从开发笔记本迁移到实时、可扩展的端点。

图9.3概述了使用 Amazon SageMaker 的部署流水，从模型打包和上传到 S3，到端点创建和推理执行：

![](img/036cc5d5719121241c605ad59a82949c_617_0.png)

**图 9.3：** 用于 PyTorch 模型的 AWS SageMaker 部署流水

## 部署步骤

以下是使用 SageMaker 部署 PyTorch 模型的步骤：

1. **保存并打包模型**：将您的模型和推理逻辑压缩为 .tar.gz 归包。该包通常包含：
   a. **model.pt**：序列化的 PyTorch 模型。
   b. **inference.py**：定义 `model_fn()` 和 `predict_fn()` 的脚本。
   c. **(可选) requirements.txt**：额外依赖项列表。
2. **将归包上传到 Amazon S3**

```
import boto3
s3 = boto3.client('s3')
s3.upload_file("model.tar.gz", "your-bucket", "model/model.tar.gz")
```

3. **在 SageMaker 中创建 PyTorchModel 对象**：

```python
from sagemaker.pytorch import PyTorchModel
pytorch_model = PyTorchModel(
    model_data="s3://your-bucket/model/model.tar.gz",
    entry_point="inference.py",
    role="arn:aws:iam::123456789012:role/SageMakerExecutionRole",
    framework_version="1.12",
    py_version="py38"
)
```

4. **将模型部署为实时端点**：

```python
predictor = pytorch_model.deploy(
    initial_instance_count=1,
    instance_type="ml.m5.large"
)
```

5. **调用已部署的端点**：
```python
response = predictor.predict({"input": [1.2, 3.4, 5.6]})
print(response)
```

## AI 工具支持

GitHub Copilot 和 ChatGPT 通过自动化 SDK 配置、管理权限以及解决 AWS SageMaker 环境中的部署挑战，简化了云端部署：

-   **GitHub Copilot：**
    - 自动补全 SageMaker SDK 的函数签名。
    - 建议最佳的 `instance_type` 和 `entry_point` 配置。

-   **ChatGPT：**
    - 提供 IAM 角色配置、S3 策略和端点测试指导。
    - 帮助调试部署错误并优化内存和计算设置。

这些工具通过减少手动脚本编写、提高配置准确性以及简化端点验证，显著加速了云端部署。

## 在 SageMaker 上使用 Docker 部署自定义容器

虽然 SageMaker 为 PyTorch 等流行框架提供了广泛预构建容器，但某些情况需要更大的灵活性——例如使用特定版本的库、安装冷门包或实现自定义运行时逻辑。在这种情况下，SageMaker 支持“自备容器”（BYOC）方法。

BYOC 允许您定义自己的容器镜像，根据项目需求进行完全定制，并将其部署为 SageMaker 推理端点。

## BYOC 部署工作流

SageMaker 中的 BYOC 方法通过允许开发者构建、推送和部署针对特定 ML 部署定制的自定义 Docker 镜像，实现了运行时环境的完全自定义：

1. 创建包含 PyTorch 和所有所需依赖项的 Dockerfile。
2. 构建并将容器推送到 Amazon Elastic Container Registry (ECR)。
3. 配置 SageMaker 引用来自 ECR 的自定义容器镜像。
4. 使用 SageMaker SDK 将模型部署到实时托管端点。

**示例：** 用于 SageMaker 的 Dockerfile

以下 Dockerfile 为 SageMaker BYOC 部署设置了自定义容器，符合平台的目录和环境变量命名约定，以确保推理脚本的顺畅执行：

```dockerfile
FROM pytorch/pytorch:1.12-cuda11.3-cudnn8-runtime
COPY inference.py /opt/ml/code/
RUN pip install sagemaker-inference
ENV SAGEMAKER_PROGRAM inference.py
```

此设置使用了 SageMaker 预期的目录结构和环境变量（SAGEMAKER_PROGRAM）来正确定位并执行推理入口。

## AI 工具支持

通过自动化 Dockerfile 的创建、优化容器设置以及通过智能建议解决配置问题，简化了 BYOC 部署过程：

-   **ChatGPT：**
    - 生成针对 SageMaker 兼容性优化的完整 Dockerfile。
    - 协助设置环境变量、卷和工作目录。
    - 故障排除与 BYOC 相关的构建错误和配置问题。
-   **GitHub Copilot：**
    - 自动填充所需的 Docker 命令序列。
    - 建议所需的 Python 包和 pip 安装命令。
    - 协助优化容器镜像的大小和性能。

使用 BYOC 为高级 ML 应用提供了无与伦比的灵活性，而 SageMaker 则负责部署、缩缩和端点管理。

## SageMaker 中的监控与管理

有效的部署并不结束于模型上线——持续的监控和管理对于确保可靠性、性能和合规性至关重要。Amazon SageMaker 通过提供用于记录、健康检查、流量缩缩和治理的内置工具，简化了这一过程。

## 关键监控与管理功能

监控和管理对于在生产环境中维护可靠的 ML 服务至关重要。下表概述了 AWS SageMaker 支持的可观测性、合规性和扩展性的核心功能：

| 功能 | 目的 |
| --- | --- |
| CloudWatch 日志 | 跟踪推理延迟、错误消息和服务器运行时间 |
| 模型监控 | 自动检测数据漂移、模式违反或异常模式 |
| 自动扩展 | 根据入流量动态调整实例数量 |
| 审计跟踪 | 记录 API 调用和用户操作，以实现追溯性和合规性 |

**表 9.3：** AWS SageMaker 部署中的关键监控与管理功能

这些工具有助于确保您的 ML 端点保持健康、响应敏捷并与真实的数据趋势保持。

## AI 工具支持

GitHub Copilot 和 ChatGPT 通过自动化设置任务、减少手动工作和加速部署，简化了 SageMaker 操作。这些工具支持监控和管理工作流，帮助团队在云端构建更可靠、高效的 ML 系统。

以下强调了 AI 工具如何协助简化云监控和管理任务：

- **GitHub Copilot：**
    - 建议用于将 CloudWatch 指标集成到自定义仪表板的代码。
- 帮助使用 AWS Lambda 或 SNS 自动化日志摄取和告警设置。


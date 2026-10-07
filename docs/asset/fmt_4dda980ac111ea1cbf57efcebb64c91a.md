
| 蒸馏 | 60-80% | 快 2 倍 | ~95-97% |

以及部署的便利性同样重要。

图 9.2 展示了基于 FastAPI 部署的典型推理流程，从客户端请求到模型推理以及响应交付：

![](img/036cc5d5719121241c605ad59a82949c_608_0.png)

**图 9.2**: 基于 FastAPI 的模型服务工作流

**示例**: 基于 FastAPI 的模型服务

以下代码演示了如何使用 FastAPI 将 TorchScript 模型部署为 RESTful API，实现客户端应用程序的实时预测：

```
from fastapi import FastAPI
import torch
from pydantic import BaseModel
class Input(BaseModel):
    features: list

app = FastAPI()
model = torch.jit.load("model_scripted.pt")

@app.post("/predict")
def predict(input: Input):
    input_tensor = torch.tensor([input.features])
    output = model(input_tensor)
    return {"prediction": output.tolist()}
```

## 核心优势

这种部署方法提供了轻量级、实时的接口，是快速开发、测试以及与客户端应用程序无缝集的理想选择：

- 开发环境和本地测试的快速轻量级部署。
- 支持低延迟的实时推理。
- 通过 REST APIs 与前端客户端和后端服务无缝集成。

## AI 工具辅助

AI 编程助手通过自动化路由逻辑、改进模式验证以及解决常见的实现问题，增强了 FastAPI 的部署工作流：

- GitHub Copilot:
    - 自动补全 API 路由和请求/响应逻辑。
    - 使用 `pydantic` 模型验证输入模式。
    - 为常见的边缘情况建议异常处理。
- ChatGPT:
    - 辅助设计异步端点和兼容 JSON 的响应。
    - 推荐输入验证模式并帮助排查 API 错误。
    - 为基于 FastAPI 的部署流水线生成完整的脚架。

> 注意：本地 API 部署是概念验证 (POC)、内部工具以及在扩展到云端或容器环境之前集成演示的理想选择。

## 使用 Docker 进行容器化部署

随着机器学习解决方案从开发转向生产，一致性、可移植性和可复现性成为重中之重。Docker 提供了一种强大且标准的方法，可以将整个应用程序（包括模型、依赖项和服务逻辑）封装成轻量级、可移植的容器镜像。

这确保了模型在开发人员笔记本电脑、云虚拟机或 Kubernetes 等大规模编排平台上的具有完全一致的行为。

### 示例：用于模型部署的 Dockerfile

以下 Dockerfile 演示了如何对基于 FastAPI 的 ML 模型服务器进行容器化，确保跨不同环境的部署一致性。

```
FROM python:3.10-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY .
CMD ["uvicorn", "app:app", "-host", "0.0.0.0", "-port", "8000"]
```

### 构建并运行容器

使用以下命令构建 Docker 镜像并在本地或云环境中启动容器化的 ML API：

```bash
docker build -t ml-api .
docker run -p 8000:8000 ml-api
```

### 部署目标

这种容器化设置具有多功能性，适用于部署在本地服务器、云虚拟机和可扩展的 Kubernetes 环境中：

- 具有固定基础设施的本地服务器。
- 云虚拟机，如 AWS EC2、Google Compute Engine 或 Azure VMs。
- 用于生产环境中可扩展编排部署的 Kubernetes 集群。

## AI 工具辅助

AI 驱动的助手通过生成优化的 Dockerfile、解决构建问题以及自动化环境配置步骤，简化了基于 Docker 的部署：

- GitHub Copilot:
    - 提供编写高效 Dockerfile 的最佳实践。
    - 推荐最小基础镜像（例如 `python:3.10-slim`）和缓存策略。
    - 自动完成环境设置和 `CMD` 指令。
- ChatGPT:
    - 生成多阶段 Dockerfile 以减小镜像尺寸。
    - 帮助编写多容器设置的 `docker-compose.yml` 文件。
    - 诊断构建失败、版本不匹配和依赖问题。

> 注意：Docker 增强了可复现性，简化了 CI/CD 集成，并实现了云端和本地平台的无缝迁移。

## 模型服务

模型服务增强了可复现性，简化了 CI/CD 集成，并实现了云端和本地平台的无缝迁移。TorchServe 是一个为生产环境机器学习模型提供的灵活、可扩展且就绪的工具。

以下步骤演示了使用 TorchServe 的工作流：

1. 归档模型：
   使用 `torch-archiver` 创建模型归档文件。
2. 启动服务器：
   使用 `torchserve` 启动模型服务器。
3. 发起请求：
   使用 `curl` 或客户端向模型发送数据。

通过提供可扩展的基础设施、高可用性、内置的可观测性、强大的安全性以及与 DevOps 和 MLOps 工作流的无缝集成，来交付机器学习模型：

- **弹性扩展性：** 云服务根据实时需求自动分配或减少计算资源。这确保了空闲期间的成本效益以及用量高峰期间的性能不中断。
- **高可用性：** 部署在云端的模型由多区域和多可用区的支持，提供了容错能力，即使在基础设施故障时也能最大限地减少停机时间。
- **集成监控：** 云平台内置仪表板、日志和告警系统，允许团队实时跟踪模型延迟、吞吐量、使用模式和错误。
- **安全性与合规性：** 细粒度访问控制、数据加密、审计跟踪和预配置合规性标准等功能，使云平台适用于医疗、金融和政府等受监管行业。
- **DevOps 和 MLOps 集成：** 与 CI/CD 工具的无缝集成实现了自动化部署、持续模型重训练和全生命周期管理，为稳健的 MLOps 流水线奠定了基础。

简而言之，云部署将 ML 模型交付从手动的、基础设施密集型的任务转变为与企业软件实践一致的可扩展、安全且自动的过程。

## 使用 AWS SageMaker 部署 PyTorch 模型

AWS SageMaker 通过其 Python SDK 为 PyTorch 模型提供了无缝的部署体验。通过抽象基础设施管理的复杂性，允许开发者以极配置快速从开发笔记本迁移到实时、可扩展的端点。

图9.3概述了使用 Amazon SageMaker 的部署流水，从模型打包和上传到 S3，到端点创建和推理执行：

![](img/036cc5d5719121241c605ad59a82949c_617_0.png)

**图 9.3：** 用于 PyTorch 模型的 AWS SageMaker 部署流水

### 部署步骤

以下是使用 SageMaker 部署 PyTorch 模型的步骤：

1. **保存并打包模型**：将您的模型和推理逻辑压缩为 `.tar.gz` 归包。该包通常包含：
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

### AI 工具支持

GitHub Copilot 和 ChatGPT 通过自动化 SDK 配置、管理权限以及解决 AWS SageMaker 环境中的部署挑战，简化了云端部署：

- **GitHub Copilot：**
    - 自动补全 SageMaker SDK 的函数签名。
    - 建议最佳的 `instance_type` 和 `entry_point` 配置。
- **ChatGPT：**
    - 提供 IAM 角色配置、S3 策略和端点测试指导。
    - 帮助调试部署错误并优化内存和计算设置。

这些工具通过减少手动脚本编写、提高配置准确性以及简化端点验证，显著加速了云端部署。

## 在 SageMaker 上使用 Docker 部署自定义容器

虽然 SageMaker 为 PyTorch 等流行框架提供了广泛预构建容器，但某些情况需要更大的灵活性——例如使用特定版本的库、安装冷门包或实现自定义运行时逻辑。在这种情况下，SageMaker 支持“自备容器”（BYOC）方法。

BYOC 允许您定义自己的容器镜像，根据项目需求进行完全定制，并将其部署为 SageMaker 推理端点。

### BYOC 部署工作流

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

此设置使用了 SageMaker 预期的目录结构和环境变量（`SAGEMAKER_PROGRAM`）来正确定位并执行推理入口。

### AI 工具支持

通过自动化 Dockerfile 的创建、优化容器设置以及通过智能建议解决配置问题，简化了 BYOC 部署过程：

- **ChatGPT：**
    - 生成针对 SageMaker 兼容性优化的完整 Dockerfile。
    - 协助设置环境变量、卷和工作目录。
    - 故障排除与 BYOC 相关的构建错误和配置问题。
- **GitHub Copilot：**
    - 自动填充所需的 Docker 命令序列。
    - 建议所需的 Python 包和 pip 安装命令。
    - 协助优化容器镜像的大小和性能。

使用 BYOC 为高级 ML 应用提供了无与伦比的灵活性，而 SageMaker 则负责部署、缩缩和端点管理。

## SageMaker 中的监控与管理

有效的部署并不结束于模型上线——持续的监控和管理对于确保可靠性、性能和合规性至关重要。Amazon SageMaker 通过提供用于记录、健康检查、流量缩缩和治理的内置工具，简化了这一过程。

### 关键监控与管理功能

监控和管理对于在生产环境中维护可靠的 ML 服务至关重要。下表概述了 AWS SageMaker 支持的可观测性、合规性和扩展性的核心功能：

| 功能 | 目的 |
| --- | --- |
| CloudWatch 日志 | 跟踪推理延迟、错误消息和服务器运行时间 |
| 模型监控 | 自动检测数据漂移、模式违反或异常模式 |
| 自动扩展 | 根据入流量动态调整实例数量 |
| 审计跟踪 | 记录 API 调用和用户操作，以实现追溯性和合规性 |

**表 9.3：** AWS SageMaker 部署中的关键监控与管理功能

这些工具有助于确保您的 ML 端点保持健康、响应敏捷并与真实的数据趋势保持。

### AI 工具支持

GitHub Copilot 和 ChatGPT 通过自动化设置任务、减少手动工作和加速部署，简化了 SageMaker 操作。这些工具支持监控和管理工作流，帮助团队在云端构建更可靠、高效的 ML 系统。

以下强调了 AI 工具如何协助简化云监控和管理任务：

- **GitHub Copilot：**
    - 建议用于将 CloudWatch 指标集成到自定义仪表板的代码。
    - 帮助使用 AWS Lambda 或 SNS 自动化日志摄取和告警设置。
- ChatGPT:
    - 引导 Model Monitor 进行计划基线分析的配置。
    - 协助设置审核规则、通知阈值和失败告警。

SageMaker 的操作层在通过 AI 助手实现智能自动化时，可以创建一个具有实时可见性和自适应性能调优的弹性机器学习（ML）部署流水线。

## 云端部署的 AI 工具支持

在云环境中部署机器学习模型通常涉及多个部分——从身份和访问管理 (IAM) 配置、存储权限到 SDK 使用和端点故障排除。AI 编码助手，尤其是 ChatGPT 和 GitHub Copilot，在简化这些任务方面发挥着关键作用。

这些工具帮助开发者跳过冗长的文档和重复的脚本编写，实现更快速、更可靠的云部署。

### 工具用例

下表总结了 ChatGPT 和 GitHub Copilot 如何协助开发者完成云端 ML 部署和管理的不同阶段：

| 工具 | 关键用例 |
|---|---|
| ChatGPT | - 生成 IAM 策略和 Docker 模板<br>- 编写 S3 CLI 上传脚本<br>- 诊断常见的部署错误（例如 HTTP 502、IAM 角色问题） |
| GitHub Copilot | - 补全 SageMaker SDK 方法调用<br>- 协助编写端点逻辑和负载格式<br>- 建议日志和监控设置 |

**表 9.4：** AI 工具针对云端 ML 部署和监控的特定支持

### ChatGPT 提示示例

这些提示说明了开发者如何利用 ChatGPT 简化云部署、排除错误并生成基础设施配置：

- **生成一个允许 SageMaker 访问 S3 和 ECR 的 IAM 策略。**
- **“为什么我在 SageMaker 上部署 PyTorch 模型时会遇到 502 Bad Gateway 错误？”**
- **“创建一个用于 SageMaker BYOC 部署 PyTorch 模型的 Dockerfile。”**

这些提示可以在几秒内生成可用的解决方案或可操作的解释，极大地加速了开发周期。

AI 工具弥补了平台文档与生产级解决方案之间的知识差距，使开发者能够专注于创新而非基础设施障碍。

## 端端 AI 部署的实际示例

为了桥接理论与现实应用，本节介绍了两个 ML 模型部署的实践示例——从训练和 API 开发到容器化和云伸缩——由 FastAPI、Docker 和 AWS SageMaker 等工具驱动。GitHub Copilot 和 ChatGPT 在加速开发和解决常见挑战方面至关重要。

### 使用 FastAPI 和 Docker 部署情感分析模型

使用在 IMDB 数据集上训练的 PyTorch BiLSTM 模型构建并部署情感分析 API。该服务应通过 REST 访问，以便集成到网络和移动平台。

### 技术栈

以下工具构成了情感分析部署流水线的骨干，实现了高效的模型训练、服务和容器化部署：

- **PyTorch**: 用于模型训练和序列化 (TorchScript)。
- **FastAPI**: 用于创建 RESTful API。
- **Docker**: 用于容器化和平台无关性。
- **GitHub Copilot**: 用于简化编码和 API 骨架搭建。
- **ChatGPT**: 用于调试错误和优化推理逻辑。

### 工作流概述

以下步骤概述了使用 FastAPI 和 Docker 训练、提供和部署基于 PyTorch 的情感分析模型的完整过程：

1. **模型训练和序列化**：`scripted_model = torch.jit.script(model)` `torch.jit.save(scripted_model, "sentiment_model.pt")`
2. **使用 FastAPI 开发 API**：
